<!-- source_url: https://wiki.php.net/rfc/pdo_driver_specific_parsers?rev=1717399473&do=export_raw -->
<!-- revision: 1718026107 -->
<!-- status: ready -->

# Analisadores SQL específicos do _driver_ PDO

* Versão: 1.0
* Data: 11/04/2024
* Pessoas autoras: Matteo Beccati, mbeccati@php.net
* Situação: Em votação
* Discussão:
  [https://externals.io/message/123141](https://externals.io/message/123141)
* Publicada pela primeira vez em:
  [https://wiki.php.net/rfc/pdo_driver_specific_parsers](https://wiki.php.net/rfc/pdo_driver_specific_parsers)
* Implementação:
  [https://github.com/php/php-src/pull/14035](https://github.com/php/php-src/pull/14035)

## Introdução

A extensão PDO contém um analisador SQL, cujo objetivo principal é reconhecer
espaços reservados para parâmetros dentro de consultas (ou seja, `?` e
`:paramName`), para saber quantos e quais parâmetros esperar para uma consulta,
e passar as informações para o driver PDO em uso.

Este analisador foi historicamente modelado para funcionar com o SQL padrão de
fato no ecossistema PHP da época: MySQL.
No entanto, o dialeto SQL usado pelo MySQL lida com literais de _string_ de
forma diferente do SQL padrão, seguido por outros fornecedores de banco de
dados, como PostgreSQL e SQLite.

Especificamente, o MySQL trata o caractere de barra invertida como um caractere
de escape:

```mysql
'This \'word\' is a single quoted'
```

Ao passo que o SQL padrão usa aspas simples duplas:

```sql
'This ''word'' is a single quoted'
```

Ao usar bancos de dados diferentes do MySQL com PDO, consultas válidas com
literais de _string_ terminando com uma barra invertida estão prejudicando o
analisador e causando falhas aparentemente inexplicáveis.

Por exemplo:

```sql
SELECT 'foo\' AS a, '?' AS b
```

fará com que o PDO considere `'foo\' AS a, '` como uma _string_ literal e
analise o `?` seguinte como um espaço reservado para parâmetro posicional.
Na verdade, se você prestar bastante atenção, até mesmo o formatador de código
SQL do DocuWiki fica confuso com este exemplo.

Temos vários relatos de falhas semelhantes
<sup>
[[1]](https://bugs.php.net/bug.php?id=78534),
[[2]](https://bugs.php.net/bug.php?id=79276),
[[3]](https://bugs.php.net/bug.php?id=80340)</sup>, e possivelmente outras
duplicatas<sup>[[7]](https://github.com/php/php-src/issues/13958)</sup>.

Resumindo, a função _scanner_ SQL do PDO não precisa analisar completamente o
dialeto SQL em uso.
**É suficiente reconhecer adequadamente literais de _string_ entre aspas,
literais de identificadores entre aspas e comentários para ignorar a detecção de
espaço reservado dentro deles**.

### Melhoria de bônus

A limitação de um analisador SQL global no PDO significava que minha
[RFC anterior para suportar o operador `?` somente do PostgreSQL](https://wiki.php.net/rfc/pdo_escape_placeholders)<sup>[4]</sup>
teve que aplicar a alteração do analisador a todos os tipos de banco de dados.
A mudança não teve efeitos colaterais conhecidos, mas sinto que esta RFC poderia
melhorar mantendo essa peculiaridade apenas dentro do _scanner_ `pdo_pgsql`.

## Proposta

Após uma pesquisa detalhada (veja abaixo) para cada um dos bancos de dados
atualmente suportados pelo PDO no núcleo, a proposta é permitir que os _drivers_
forneçam opcionalmente uma função _scanner_ personalizada para lidar com seu
dialeto SQL específico e:

1. Alterar o
   [
   _scanner_ PDO padrão](https://github.com/php/php-src/blob/ab589e4481f0cf35c8773e0c64dccc35b8870ae1/ext/pdo/pdo_sql_parser.re#L42)
   para esperar apenas SQL padrão:
    1. literais entre aspas simples e duplas, com duplicação como mecanismo de
       escape
    2. comentários com dois traços e no estilo C (não aninhados, pois parece ser
       o formato mais comum, já implementado no PDO)
2. Adicionar uma função _scanner_ específica do MySQL:
    1. literais entre aspas simples e duplas com duplicação e barra invertida
       como mecanismos de escape (padrão do MySQL)
    2. literais de crase com duplicação como mecanismo de escape (eu também
       testei e parece que o MySQL não aceita barras invertidas como escapes)
    3. dois traços (se seguidos por 1 espaço em branco), comentários no estilo C
       e comentários com cerquilha
    4. testes, conforme necessário
3. Adicionar uma função _scanner_ específica do PgSQL:
    1. literais entre aspas simples e duplas, com duplicação como mecanismo de
       escape
    2. literais de _string_ de escape no estilo C
    3. literais de _string_ delimitadas por cifrão
    4. comentários de dois traços e no estilo C (não aninhados, pois o
       aninhamento exigiria alterações indesejadas na funcionalidade comum do
       analisador)
    5. suporte para `??` como sequência de escape para o operador `?`
    6. testes, conforme necessário
4. Adicionar uma função _scanner_ específica do SQLite:
    1. literais entre aspas simples, duplas e crase, com duplicação como
       mecanismo de escape
    2. colchetes para delimitar identificadores
    3. comentários de dois traços e no estilo C (não aninhados)
    4. testes, conforme necessário

Para manter a mudança o mais simples possível, a proposta tenta cobrir a sintaxe
SQL padrão para cada banco de dados o mais próximo possível, sem grandes
alterações no código do analisador comum.

Uma coisa importante a mencionar é que as alterações propostas visam apenas a
parte do PDO que examina a consulta SQL em busca de espaços reservados para
parâmetros.
A notação de literais ou o uso de parâmetros em consultas **não serão
afetados**.

## Proposta Detalhada

Para executar o plano, um novo membro será anexado a:

```c
struct pdo_dbh_methods {
	pdo_dbh_close_func		closer;
	pdo_dbh_prepare_func	preparer;
	pdo_dbh_do_func			doer;
	pdo_dbh_quote_func		quoter;
	// ...
	pdo_dbh_sql_scanner		scanner;
}
```

Cada _driver_ PDO já define
[sua estrutura](https://github.com/search?q=repo%3Aphp/php-src%20pdo_dbh_methods&type=code).
Deixar o novo membro como `NULL` fará com que o _driver_ use a função _scanner_
PDO padrão.
Caso contrário, um ponteiro para uma função _scanner_ personalizada substituirá
a função padrão ao analisar consultas.
É realmente simples assim.

O resto da implementação é o próprio código do _scanner_ re2c, `config.*`,
alterações no `Makefile`, etc., necessárias para incorporar o _scanner_
específico do _driver_ na compilação.

Para oferecer suporte a _strings_ delimitadas por cifrão no Postgres, a
funcionalidade de delimitação personalizada foi adicionada à função comum do
analisador PDO.
A alteração não tem efeitos colaterais para outros _drivers_ de banco de dados.

Uma pequena quebra potencial de compatibilidade com versões anteriores foi
relatada durante a pesquisa da falha
[#14244](https://github.com/php/php-src/issues/14244), que basicamente descreve
a falta de suporte para delimitação por cifrão no `pdo_pgsql`.
Uma das soluções alternativas atualmente viáveis é usar pontos de interrogação
com escape dentro de _strings_ delimitadas por cifrão para evitar a detecção
inesperada de espaços reservados.
A última versão da implementação ainda permite isso, embora gere o seguinte
aviso de descontinuação:

```text
Escaping question marks inside dollar quoted strings is not required anymore
and is deprecated.
```

Essa compatibilidade com versões anteriores pode ser removida na próxima versão
principal.

## Pesquisa Sobre Literais de _String_, Identificadores e Comentários

### MySQL

O MySQL, por padrão, aceita aspas com escape de barra invertida e o padrão SQL.
Literais de _string_ podem usar aspas simples ou duplas.
Veja [a documentação](https://dev.mysql.com/doc/refman/8.0/en/string-literals.html)
(a versão 8.0 está listada aqui, mas a 5.7 e a 8.3 se comportam da mesma forma).

O modo SQL
[`NO_BACKSLASH_ESCAPES`](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html#sqlmode_no_backslash_escapes)
desabilitará o reconhecimento da barra invertida como caractere de escape.
Se definido, interromperá a análise do SQL, independentemente desta RFC.

O modo SQL
[`ANSI_QUOTES`](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html#sqlmode_ansi_quotes)
muda o uso de crase para aspas duplas do padrão SQL para os literais de
identificadores.

Vários
[tipos de comentários](https://dev.mysql.com/doc/refman/8.0/en/comments.html)
suportados: `-- `, `#` e `/* */` (não aninhado).

A RFC visa oferecer suporte a todos os tipos de literais de _string_ acima com
variáveis de configuração que afetam _strings_ definidas com seus padrões.
Todos os tipos de comentários serão suportados.

### PostgreSQL

O escape evoluiu ao longo dos anos.
Historicamente, foi aceito `\'`, mas começou mudar gradualmente para o padrão
SQL por volta de 2005, saindo da memória.
Desde a versão 9.1 (2011+), ele aceita apenas literais de _string_ entre aspas
simples por padrão, conforme o padrão SQL.
Consulte
[a documentação](https://www.postgresql.org/docs/16/sql-syntax-lexical.html#SQL-SYNTAX-STRINGS).

O Postgres também suporta
[constantes de
_string_ com escapes Unicode](https://www.postgresql.org/docs/16/sql-syntax-lexical.html#SQL-SYNTAX-STRINGS-UESCAPE),
que seguem as mesmas convenções das _strings_ padrão sendo analisadas pelo PDO
como _strings_ regulares.

Ele também aceita
[constantes de
_string_ de "escape"](https://www.postgresql.org/docs/16/sql-syntax-lexical.html#SQL-SYNTAX-STRINGS-ESCAPE),
por exemplo.

```php
E'This \'word\' is a single quoted'
```

Por último,
[constantes de
_string_ delimitadas por cifrão](https://www.postgresql.org/docs/16/sql-syntax-lexical.html#SQL-SYNTAX-DOLLAR-QUOTING)
são muito comuns, especialmente ao definir funções.

O comportamento das _strings_ também pode ser manipulado de diversas maneiras
usando variáveis de configuração, como:
[`standard_conforming_strings`](https://www.postgresql.org/docs/16/runtime-config-compatible.html#GUC-STANDARD-CONFORMING-STRINGS),
[`backslash_quote`](https://www.postgresql.org/docs/16/runtime-config-compatible.html#GUC-BACKSLASH-QUOTE)
e
[`escape_string_warning`](https://www.postgresql.org/docs/16/runtime-config-compatible.html#GUC-ESCAPE-STRING-WARNING).

Sobre
[comentários](https://www.postgresql.org/docs/16/sql-syntax-lexical.html#SQL-SYNTAX-COMMENTS),
segue o padrão com `--` e `/* */` (com comentários aninhados permitidos).

A RFC visa oferecer suporte a todos os tipos de literais de _string_ acima com
variáveis de configuração que afetam _strings_ definidas com seus padrões.
O suporte à delimitação por cifrão requer alterações mínimas na função comum do
analisador PDO.
Todos os tipos de comentários já são suportados, embora o suporte para
comentários aninhados não seja introduzido.

### SQLite

Segue o padrão SQL e requer aspas simples duplas para representar as aspas
simples em uma _string_ literal.
Consulte a
[documentação](https://www.sqlite.org/lang_expr.html#literal_values_constants_).

No entanto, ele aceitará _strings_ entre aspas duplas como literais de _string_
em
[certas circunstâncias](https://www.sqlite.org/quirks.html#double_quoted_string_literals_are_accepted).

Identificadores entre aspas duplas, mas também
[crases e colchetes](https://sqlite.org/lang_keywords.html).

[Comentários](https://www.sqlite.org/lang_comment.html) quase padrão SQL: `--` e
`/* */` (não aninhado).

A RFC visa oferecer suporte a literais entre aspas simples, aspas duplas, crases
e colchetes.
Todos os tipos de comentários já são suportados.

### SQL Server

Literais de _string_ do padrão SQL, conforme a
[documentação](https://learn.microsoft.com/en-us/sql/t-sql/data-types/constants-transact-sql?view=sql-server-ver16#character-string-constants).

Dependendo da configuração `QUOTED_IDENTIFIER`, aspas duplas são usadas para
_strings_ ou identificadores.

[Comentários](https://learn.microsoft.com/en-us/sql/t-sql/language-elements/comment-transact-sql?view=sql-server-ver16)
quase padrão SQL: `--` e `/* */` (não aninhados).

Nenhum analisador personalizado está planejado nesta RFC: o _scanner_ padrão
será usado por padrão, trazendo compatibilidade para literais de _string_,
identificadores e comentários do padrão SQL.

### Firebird

Literais de _string_ do padrão SQL, conforme a
[documentação](https://firebirdsql.org/file/documentation/chunk/en/refdocs/fblangref40/fblangref40-commons.html#fblangref40-commons-constants).
Ele também oferece suporte a _strings_ hexadecimais (binárias), por exemplo,
`x'50444F'` e, semelhantemente ao Oracle, _strings_ entre aspas (fora do
escopo).

A documentação menciona "Aspas duplas NÃO SÃO VÁLIDAS para delimitar strings.
O padrão SQL reserva aspas duplas para uma finalidade diferente: delimitar
identificadores."

[Comentários](https://firebirdsql.org/file/documentation/chunk/en/refdocs/fblangref25/fblangref25-structure-comments.html)
quase padrão SQL: `--` e `/* */` (não aninhados).

Nenhum analisador personalizado está planejado nesta RFC: o _scanner_ padrão
será usado por padrão, trazendo compatibilidade para literais de _string_,
identificadores e comentários do padrão SQL.

### ODBC

Como o ODBC pode se conectar a vários tipos de bancos de dados, esperamos que o
analisador do padrão SQL seja suficiente.

### Oracle

Literais de _string_ do padrão SQL, conforme a
[documentação](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/Literals.html).
Ele também suporta delimitações alternativas, por exemplo, `q'<literal>'` e
muitas outras variantes, o que está fora do escopo desta RFC.

[Identificadores com aspas duplas](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/Database-Object-Names-and-Qualifiers.html#SQLRF-GUID-75337742-67FD-4EC0-985F-741C93D918DA).

[Comentários](https://docs.oracle.com/en/database/oracle/oracle-database/12.2/sqlrf/Comments.html#SQLRF-GUID-5C84C344-CEB3-4DBF-B748-337DE11CCE2A)
quase padrão SQL: `--` e `/* */` (não aninhados).

O _driver_ OCI pode ser encontrado no PECL: o _scanner_ padrão será usado por
padrão, trazendo compatibilidade para literais de _string_, identificadores e
comentários do padrão SQL.

## Contexto Histórico

Alguns anos atrás, tentei consertar uma falha e criei uma
[pull request](https://github.com/php/php-src/pull/6852) que poderia ser
considerada uma prova de conceito para esta RFC.
O mesmo tópico também foi levantado por
[outras pessoas na lista _internals_](https://externals.io/message/114016), mas
ninguém teve tempo de seguir com uma RFC adequada.

## Alterações incompatíveis com versões anteriores

Não há quebras de compatibilidade com versões anteriores, mas um aviso de
descontinuação será gerado ao usar a solução alternativa "pontos de interrogação
com escape dentro de _strings_ delimitadas por cifrão" descrita anteriormente.

As pessoas usuárias que possuem aplicações que podem trabalhar com vários
motores de banco de dados ainda devem ter muito cuidado e escrever consultas
portáteis, possivelmente usando o método `PDO::quote()` quando necessário, em
vez de codificar _strings_ contendo caracteres de escape.

## Versões propostas do PHP

Próximo PHP 8.x, esperançosamente, 8.4.

## Impacto da RFC

### Para SAPIs

Sem impacto.

### Para extensões existentes

_Drivers_ fora do `php-src` podem precisar ser modificados se fizerem suposições
sobre a estrutura da _enum_ `pdo_param_type`.
Eles teriam que ser reconstruídos já que a macro `PDO_DRIVER_API` seria
atualizada.

Isso tem sido historicamente permitido/esperado em versões menores.
A última vez que isso aconteceu foi no PHP 7.2 com a RFC
[Tipos de
_String_ Estendidos para o PDO](https://wiki.php.net/rfc/extended-string-types-for-pdo).

### Para Opcache

Nenhum impacto no opcache.

### Novas Constantes

Nenhuma nova constante.

### Padrões do `php.ini`

Nenhuma alteração no `php.ini`.

## _Issues_ Abertas

Nenhuma _issue_ aberta no momento.

## Funcionalidade PHP Não Afetada

Qualquer coisa não relacionada ao PDO analisando a consulta SQL em busca de
espaços reservados para parâmetros.

## Fora do Escopo

### Mudanças dinâmicas no _scanner_

Os scanners são gerados quando o PHP é compilado e, atualmente, não podem ser
modificados em tempo de execução.
Entretanto, alguns bancos de dados permitem que diretivas de configuração ou
consultas `SET` alterem a sintaxe aceita para literais, identificadores, etc.

Conseguir compreender todas as combinações possíveis exigiria rastrear quais
diretivas são diferentes do padrão esperado e ter vários _scanners_ dentro de
cada _driver_ para cada permutação possível de tais diretivas de configuração.

## Escopo Futuro

Validar o suporte a sintaxes "exóticas" nos _scanners_ existentes e/ou adicionar
outras funcionalidades personalizadas do _scanner_.

## Votação

A votação estará aberta até segunda-feira, 17 de junho de 2024 às 15h00 UTC.
Como habitualmente, é necessária uma maioria de 2/3 para que esta proposta seja
aceita.

<!--
TODO: Add doodle.
<doodle title="Implement PDO Driver specific SQL parsers?" auth="mbeccati" voteType="single" closed="false" closeon="2024-06-17T15:00:00Z">
   * Yes
   * No
</doodle>
-->

## _Patches_ e Testes

[Pull request da implementação](https://github.com/php/php-src/pull/14035).

## Referências

* [1] [https://bugs.php.net/bug.php?id=78534](https://bugs.php.net/bug.php?id=78534)
* [2] [https://bugs.php.net/bug.php?id=79276](https://bugs.php.net/bug.php?id=79276)
* [3] [https://bugs.php.net/bug.php?id=80340](https://bugs.php.net/bug.php?id=80340)
* [4] [RFC PHP: Escapar o espaço reservado para parâmetro `?` no PDO](https://wiki.php.net/rfc/pdo_escape_placeholders)
* [5] [Implementação prova de conceito de um
  _scanner_ `pdo_pgsql` personalizado](https://github.com/php/php-src/pull/6852)
* [6] [Discussão anterior do tópico na lista
  _internals_](https://externals.io/message/114016)
* [7] [Falha mais recente](https://github.com/php/php-src/issues/13958)
