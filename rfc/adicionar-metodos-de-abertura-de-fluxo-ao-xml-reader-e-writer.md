---
source_url: https://wiki.php.net/rfc/xmlreader_writer_streams
revision: 1718313707
status: ready
license: https://www.php.net/copyright
---

# Adicionar Métodos de Abertura de Fluxo ao XML{Reader,Writer}

* Versão: 0.11.0
* Data: 21/04/2024
* Pessoas autoras: Niels Dossche <nielsdos@php.net>
* Situação: Em votação
* Publicada pela primeira vez em:
  [https://wiki.php.net/rfc/xmlreader_writer_streams](https://wiki.php.net/rfc/xmlreader_writer_streams)

## Introdução

As classes `XMLReader` e `XMLWriter` lidam com XML de maneira orientada a fluxo.
O primeiro implementa um analisador _pull_ XML.
Isso significa que, em vez de manter os dados na memória ou construir uma árvore
do documento, o documento é transmitido e a pessoa desenvolvedora pode instruir
o `XMLReader` a analisar fragmentos no cursor atual e processar ou ignorar os
dados.
A vantagem é que pessoas desenvolvedoras podem processar e filtrar documentos
grandes exigindo poucos recursos.
Ele é mais frequentemente usado como um bloco de construção de baixo nível para
manipulação mais complexa de grandes documentos XML.
Da mesma forma, o `XMLWriter` grava um documento XML em um fluxo ou na memória
usando métodos como `startElement` e `writeElement`.

Há, no entanto, uma estranha limitação para estas classes: elas não podem operar
em um fluxo já aberto!
Isso é bizarro, pois as APIs (tanto internas quanto voltadas para a pessoa
desenvolvedora) são orientadas a fluxo.
Fluxos que já estão abertos são comuns ao trabalhar, por exemplo, com
requisições HTTP, dados passados de um _framework_ ou apenas dados XML
incorporados em um fluxo existente.
A falta de uma API que funcione com fluxos já abertos faz com que as pessoas
desenvolvedoras dependam de soluções alternativas, por exemplo, lendo o fluxo
inteiramente para a memória e depois usando as APIs do `XMLReader`, ou
escrevendo um arquivo XML usando o `XMLWriter` e tendo que passá-lo para um
fluxo já aberto.
Isso é um desperdício e desnecessariamente difícil.
Esta RFC visa corrigir esse problema e também corrigir algumas outras
inconsistências.

## Proposta

### Proposta Principal

Proponho adicionar dois novos métodos, um ao `XMLReader` e outro ao `XMLWriter`,
para criar uma instância a partir de um fluxo.
Aqui está como eles seriam:

```php
class XMLReader {
    /** @param resource $stream */
    public static function fromStream($stream, ?string $encoding = null, int $flags = 0, ?string $documentUri = null): static {}
}

class XMLWriter {
/** @param resource $stream */
public static function toStream($stream): static {}
}
```

As assinaturas são fortemente inspiradas no método existente
`public static XMLReader::open(string $uri, ?string $encoding = null, int $flags = 0): bool|XMLReader`
que opera em arquivos.
No entanto, uma grande diferença é que `XMLReader::fromStream()` é somente
estático, enquanto os outros métodos de abertura do `XMLReader` podem ser
chamados estaticamente ou não estaticamente e alterar o comportamento do valor
de retorno dependendo disso.
A desvantagem dos métodos estáticos existentes é que eles só podem retornar uma
instância de `XMLReader`, portanto quando `XMLReader` é herdado por uma
subclasse da pessoa desenvolvedora, nos deparamos com o problema de ele não
retornar um objeto do tipo correto.
Resolvemos isso escolhendo `static` como tipo de retorno e deixando o método
chamar internamente o construtor do tipo estático (sem argumentos).
Como parece que estamos nos afastando dos métodos sobrecarregados, decidi
disponibilizar apenas a variante do método estático.

O parâmetro `$documentUri` é usado principalmente quando a `libxml` gera
mensagens de erro, de modo que você pode colocar um nome de origem lá.

A assinatura do método `XMLWriter::toStream()` deve ser autoexplicativa.
Ele também foi modelado como os outros métodos de abertura, mas é
consideravelmente mais simples.
Você também notará a ausência de um argumento de codificação, porque isso já é
tratado pelo método `XMLWriter::startDocument()`.

Ao implementar essa RFC, encontrei alguns comportamentos estranhos em relação ao
parâmetro `?string $encoding` dos métodos existentes `XMLReader::open()` e
`XMLReader::XML()`.
O primeiro comportamento estranho é que eles emitem um alerta em vez de lançar
um `ValueError` quando a codificação contém _bytes_ `NULL`.
Isso é inconsistente com como outros métodos lidam com isso.
Proponho promover este alerta para `ValueError`.
O segundo comportamento estranho é que nomes de codificação inválidos são
totalmente ignorados.
Isso significa que eles não emitirão um alerta nem nada, apenas silenciosamente
não definirão a codificação.
Isso pode esconder bugs.
Proponho também lançar um `ValueError` neste caso informando
`Argument #X ($encoding) must be a valid character encoding`.

Uma versão anterior desta RFC propunha adicionar métodos `openStream()` a ambas
as classes, mas a nomenclatura não era ideal e o comportamento de ser um método
de instância não era apreciado.
Portanto, isso foi alterado para métodos somente estáticos que retornam uma
instância da respectiva classe.

### Consistência

Estamos adicionando novos construtores nomeados estáticos às classes `XMLWriter`
e `XMLReader`.
No entanto, `XMLWriter` ainda não possui construtores estáticos e `XMLReader`
possui esses métodos híbridos estáticos e de instância de que falamos
anteriormente.
Esses métodos existentes também não podem ser usados em subclasses porque
retornam `XMLWriter` ou `XMLReader` em vez de `static`.

A ideia é adicionar os seguintes construtores nomeados estáticos para
consistência com os novos métodos propostos, com os mesmos argumentos de sua
contraparte existente:

- `XMLReader::fromUrl(string $url, ?string $encoding = null, int $flags = 0): static`
  como uma nova versão de `XMLReader::open(...)`
- `XMLReader::fromString(string $source, ?string $encoding = null, int $flags = 0): static`
  como uma nova versão de `XMLReader::XML(...)`
- `XMLWriter::toMemory(): static` como uma nova versão de
  `XMLWriter::openMemory(...)`
- `XMLWriter::toUrl(string $url): static` como uma nova versão de
  `XMLWriter::openUri(...)`

Observe que usei `Url` aqui em vez de `Uri` porque esse é o termo mais preciso:
ele realmente localiza o recurso em vez de apenas identificá-lo.

Isso não visa descontinuar nenhum método existente.
Iremos apenas atualizar a documentação para direcionar as pessoas
desenvolvedoras aos novos construtores.

## Alterações Incompatíveis com Versões Anteriores

Existem três quebras menores de compatibilidade com versões anteriores.

A primeira é o fato de estarmos adicionando novos métodos.
Se uma pessoa desenvolvedora estender a classe `XMLReader` ou `XMLWriter` e sua
classe implementar um método com o mesmo nome, mas com uma assinatura
incompatível, ocorrerá um erro de compilação.
Analisei os 2.500 principais pacotes do Composer e nenhum usou nenhum dos nomes
de métodos propostos nas subclasses das classes XML.
Isso significa que os 2.500 principais pacotes não sofrem quebra de
compatibilidade com versões anteriores por causa disso.
Isso não significa que não haverá nenhum, mas dá uma boa indicação.

A segunda quebra de compatibilidade com versões anteriores é causada pelo
lançamento de um `ValueError` ao usar codificações inválidas, em vez de
ignorá-las silenciosamente.
Se não sinalizarmos a codificação inválida de alguma forma para a pessoa
desenvolvedora, isso poderá ocultar falhas sutilmente.
Por exemplo, isso pode ocultar erros de digitação ou passar silenciosamente
entradas inválidas da pessoa desenvolvedora para os respectivos métodos.
Forçar as pessoas desenvolvedoras a lidar explicitamente com esse erro resultará
em um código mais robusto no final.

A terceira quebra de compatibilidade com versões anteriores é a promoção do
alerta de _byte_ `NULL` para um `ValueError`.
Isso torna as classes `XMLReader` e `XMLWriter` mais consistentes com outras
extensões que lançam erros em vez de emitir um alerta.
A migração para pessoas desenvolvedoras deve ser bastante simples: em vez de
silenciar o alerta e/ou verificar o valor de retorno do método, elas devem usar
uma construção `try-catch` para tratar o erro.

## Exemplos de Uso

### Exemplo Mínimo com `XMLReader`

```php
// Poderia ser qualquer fluxo, mas isso é para simplificar.
$h = fopen("php://memory", "w+");
fwrite($h, "<root><!--meu comentário--><child/></root>");
fseek($h, 0);

$reader = XMLReader::fromStream($h);

while ($reader->read()) {
    switch ($reader->nodeType) {
    case XMLReader::ELEMENT:
        echo "Elemento: ", $reader->name, "\n";
        break;
    case XMLReader::COMMENT:
        echo "Comentário: ", $reader->value, "\n";
        break;
    }
}
```

### Exemplo Mínimo com `XMLWriter`

```php
// Poderia ser qualquer fluxo, mas isso é para simplificar.
$h = fopen("php://output", "w");

$writer = XMLWriter::toStream($h);

$writer->startElement("root");
$writer->writeAttribute("align", "left");
$writer->writeComment("olá");
$writer->endElement();
$amount = $writer->flush();
echo "\nQuantidade de bytes gravados: ";
var_dump($amount);
```

## Versões Propostas do PHP

Próximo PHP 8.x, é o PHP 8.4 no momento em que esta RFC foi escrita.

## Impacto da RFC

### Para Extensões Existentes

Somente `ext/xmlreader` e `ext/xmlwriter` serão afetadas.

## _Issues_ Abertas

Nenhuma ainda.

## Funcionalidade PHP Não Afetada

O resto, por que temos esta seção?

## Escopo Futuro

Nenhum ainda.

## Escolhas de Votação Propostas

Duas votações primárias, cada uma exigindo maioria de 2/3: uma para a proposta
principal e outra para a proposta de consistência.

A votação começou em 13/06/2024 e terminará em 28/06/2024.

### Aceita adicionar os métodos da seção Proposta Principal?

| Nome                                                         | Sim | Não |
|--------------------------------------------------------------|:---:|:---:|
| [adiel](https://people.php.net/adiel) (adiel)                |  X  |     |
| [ashnazg](https://people.php.net/ashnazg) (ashnazg)          |  X  |     |
| [crell](https://people.php.net/crell) (crell)                |  X  |     |
| [girgias](https://people.php.net/girgias) (girgias)          |  X  |     |
| [jimw](https://people.php.net/jimw) (jimw)                   |  X  |     |
| [kguest](https://people.php.net/kguest) (kguest)             |  X  |     |
| [mbeccati](https://people.php.net/mbeccati) (mbeccati)       |  X  |     |
| [nielsdos](https://people.php.net/nielsdos) (nielsdos)       |  X  |     |
| [ocramius](https://people.php.net/ocramius) (ocramius)       |  X  |     |
| [theodorejb](https://people.php.net/theodorejb) (theodorejb) |  X  |     |
| **Total**                                                    | 10  |  0  |

### Aceita adicionar os métodos da seção Consistência?

| Nome                                                         | Sim | Não |
|--------------------------------------------------------------|:---:|:---:|
| [adiel](https://people.php.net/adiel) (adiel)                |  X  |     |
| [ashnazg](https://people.php.net/ashnazg) (ashnazg)          |  X  |     |
| [crell](https://people.php.net/crell) (crell)                |  X  |     |
| [galvao](https://people.php.net/galvao) (galvao)             |  X  |     |
| [girgias](https://people.php.net/girgias) (girgias)          |  X  |     |
| [jimw](https://people.php.net/jimw) (jimw)                   |  X  |     |
| [kguest](https://people.php.net/kguest) (kguest)             |  X  |     |
| [mbeccati](https://people.php.net/mbeccati) (mbeccati)       |  X  |     |
| [nielsdos](https://people.php.net/nielsdos) (nielsdos)       |  X  |     |
| [ocramius](https://people.php.net/ocramius) (ocramius)       |  X  |     |
| [theodorejb](https://people.php.net/theodorejb) (theodorejb) |  X  |     |
| **Total**                                                    | 11  |  0  |

## _Patches_ e Testes

PR da implementação:
[https://github.com/php/php-src/pull/14030](https://github.com/php/php-src/pull/14030)

## Implementação

Depois que o projeto for implementado, esta seção deverá conter:

- as versões nas quais foi feito o _merge_
- um link para os _commits_ do git
- um link para a entrada no manual do PHP para o recurso
- um link para a seção de especificação da linguagem (se houver)

## Referências

- [https://bugs.php.net/bug.php?id=63506](https://github.com/php/php-src/pull/14030)
- [https://bugs.php.net/bug.php?id=46146](https://github.com/php/php-src/pull/14030)

## Recursos Rejeitados

Nenhum ainda.

## _Changelog_

- 0.11.0: Incorporou feedback sobre métodos estáticos.
- 0.10.1: Correções de linguagem.
- 0.10.0: Estático novamente.
- 0.9.2: Adicionou exemplos de uso das novas APIs.
- 0.9.1: Tornou `XMLReader::openStream()` não estático, para que funcione com
  classes sobrescritas.
- 0.9: Versão inicial em discussão.
