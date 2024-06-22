---
source_url: https://wiki.php.net/rfc/dom_additions_84
revision: 1718313707
status: wip
license: https://www.php.net/copyright
---

# Novos Recursos da `ext-dom` no PHP 8.4

* Versão: 0.1
* Data: 12/04/2024
* Pessoas autoras: [Niels Dossche][email-nielsdos]
* Situação: Em votação
* Primeira publicação: [Wiki do PHP][rfc-dom-additions-84]

## Introdução

O ciclo de desenvolvimento do PHP 8.4 já viu duas melhorias importantes na
extensão [`ext-dom`][doc-dom]: [suporte ao HTML 5][rfc-html5-parser] e
[conformidade opcional com a especificação DOM][rfc-spec-compliance].
Esta RFC é (provavelmente) a última melhoria da [`ext-dom`][doc-dom] para o PHP
8.4: ela propõe adicionar novos recursos à extensão.
Em particular, focaremos no suporte ao seletor CSS, preenchendo recursos
ausentes, mas comuns, e adicionando novas propriedades.
Essas melhorias e alterações se aplicam apenas às novas classes no _namespace_
`Dom`.

## Proposta

A RFC consiste em várias subpropostas agrupadas em uma RFC para minimizar a
sobrecarga.
Nesta seção, discutiremos cada proposta separadamente.

### Seletores CSS

Existem várias maneiras de consultar nós em um documento XML ou HTML.
Aquela já implementada desde a existência da extensão DOM está usando XPath.
Outra forma popular, com a qual as pessoas provavelmente estão mais
familiarizadas, são os seletores CSS.
Em teoria, toda consulta que você pode escrever com seletores CSS também pode
ser escrita com XPath.
No entanto, em muitos casos, o XPath é muito mais complicado de usar.
Por exemplo, uma consulta simples como `p:contains("hello") + span` é
equivalente a
`.//p[contains(normalize-space(),"hello")]/following-sibling: :*[1]/self::span`.
As coisas podem ficar muito mais complicadas quando você usa pseudofunções
como `:disabled`, que são muito difíceis de expressar em XPath.

A especificação DOM define as seguintes funções de seletor CSS:

```php
namespace Dom {
    interface ParentNode {
        public function querySelector(string $selectors): ?Element {}
        public function querySelectorAll(string $selectors): NodeList {}
    }

    class Element extends Node implements ParentNode {
        public function closest(string $selectors): ?Element {}
        public function matches(string $selectors): bool {}
    }
}
```

Isso é o que os métodos fazem:

* `querySelector`: Retorna o primeiro elemento descendente que corresponde aos
  seletores CSS.
* `querySelectorAll`: Retorna uma [`NodeList`][doc-domnodelist] contendo todos
  os elementos descendentes que correspondem aos seletores CSS.
* `closest`: Encontra o ancestral mais próximo do elemento que corresponde aos
  seletores CSS.
* `matches`: Retorna `true` se o elemento corresponder aos seletores CSS, ou
  `false`, caso contrário.

Vale ressaltar que os seletores CSS podem conter pseudoclasses que só fazem
sentido quando algo é renderizado na tela.
Como, por exemplo, `:hover`, que corresponde quando uma pessoa usuária passa o
mouse sobre um elemento.
Como no contexto do PHP isso não faz sentido, um seletor CSS que usa tal
pseudoclasse não corresponderá a nada.

Embora seja possível implementar `closest` e `matches` usando XPath, isso não
pode ser feito com um bom desempenho (até onde eu sei).

A biblioteca fundamental que usamos para análise do HTML5 também contém a
funcionalidade CSS necessária para implementar esses métodos.
Portanto, podemos obter a funcionalidade com relativa facilidade.
Eu só tive que adaptar as estruturas de dados dos nós para corresponder às
estruturas de dados do PHP.

Existem soluções alternativas criadas por pessoas desenvolvedoras que
implementam uma tradução de seletores CSS para XPath, mas com base no que vi:

* Elas sofrerão um impacto no desempenho porque a tradução não é "gratuita".
* Elas não fornecem uma forma eficiente de implementar `closest` e `matches`.
* Como elas são implementadas em torno das antigas classes DOM, e as antigas
  classes DOM não consideram os diferentes _namespaces_ HTML adequadamente, elas
  também não consideram os _namespaces_ adequadamente.

#### Exemplos

**Exemplo 1: `querySelector`**

```php
$dom = Dom\XMLDocument::createFromString(<<<XML
<root>
  <span>1</span>
  <p>oi</p>
  <span>2</span>
</root>
XML);

var_dump($dom->querySelector('p ~ span')->textContent); // string(1) "2"
```

**Exemplo 2: `closest`**

```php
$dom = Dom\XMLDocument::createFromString(<<<XML
<root>
  <div class="foo" xml:id="div1">
    <div xml:id="div2">
      <div class="bar" xml:id="div3"/>
    </div>
  </div>
</root>
XML);

var_dump($dom->getElementById('div3')->closest('div')->getAttribute("xml:id")); // string(4) "div3"
var_dump($dom->getElementById('div3')->closest(':not(div[class])')->getAttribute("xml:id")); // string(4) "div2"
```

**Exemplo 3: `matches`**

```php
$dom = Dom\XMLDocument::createFromString(<<<XML
<root>
  <div xml:id="div1">
    <div xml:id="div2">
      <div xml:id="div3"/>
    </div>
  </div>
</root>
XML);

var_dump($dom->getElementById('div3')->matches('div > div')); // bool(true)
var_dump($dom->getElementById('div3')->matches('root > div')); // bool(false)
```

### `Element::$innerHTML`

Esta é uma propriedade da classe [`Element`][doc-domelement] definida na
[especificação DOM][spec-innerhtml]:

```php
namespace Dom {
    class Element /* ... */ {
        public string $innerHTML;
    }
}
```

A leitura deste campo obterá a serialização do conteúdo interno do elemento, a
gravação nele transformará uma _string_ em uma subárvore e substituirá o
conteúdo do elemento pela nova subárvore.
Se o documento for um documento HTML, o analisador/serializador HTML será usado.
Se o documento for um documento XML, o analisador/serializador XML será usado.
Sim, isso significa que inner**HTML** pode definir conteúdo **XML**, e isso foi
definido pelas especificações.
Esse erro na nomenclatura é uma bagagem herdada da especificação que decorre
do fato de que, por questões de interoperabilidade, a classe
[`Element`][doc-domelement] é compartilhada entre documentos XML e HTML.

Se a serialização não estiver bem formada para XML, uma
[`DOMException`][doc-domexception] com `$code`
[`DOM_SYNTAX_ERR`][doc-dom-syntax-err] será lançada, conforme definido pela
especificação.

A análise de documentos (ou fragmentos) pode causar erros _hard_/_soft_.
Os erros _soft_ são relatados por meio de alertas ou, se o mecanismo interno de
tratamento de erros for usado, os erros serão armazenados em um _array_.
A menos que [`LIBXML_NOERROR`][doc-libxml-noerror] seja fornecida, nesse caso
esses erros _soft_ serão silenciados.
Observe que não temos como fornecer uma opção de análise para a propriedade
`innerHTML` e, portanto, não podemos fornecer uma maneira de silenciar os erros
de maneira limpa.
Perguntei sobre isso na [lista de discussão][message-123224], mas não obtive
resposta.
Isso provavelmente significa que as pessoas estão inseguras ou não se importam
e, por isso, optei por não implementar o relatório de erros porque é mais fácil
omitir algo e adicioná-lo mais tarde do que remover algo mais tarde.

### Novas propriedades para `Document`

Proponho a adição de várias novas propriedades à classe
[`Document`][doc-domdocument] para tornar o desenvolvimento um pouco mais fácil:

```php
namespace Dom {
    class HTMLElement extends Element {
        /* Há uma oportunidade de adicionar propriedades úteis da especificação
           HTML aqui no futuro. */
    }

    class Document /* ... */ {
        public ?HTMLElement $body;
        /** @readonly */
        public ?HTMLElement $head;
        public string $title;
    }
}
```

Essas adições são descritas no
[adendo da especificação HTML para o DOM][spec-document].

As propriedades devem ser relativamente autoexplicativas.
`$body` refere-se ao elemento `body` (se houver), `$head` ao elemento `head`
(se houver) e `$title` ao texto dentro do elemento `title` (que por sua vez está
dentro do elemento `head`).
Você pode ler sobre todos os detalhes usando o _link_ acima, porque é um pouco
mais complicado quando SVG está envolvido, por exemplo, mas você deve estar
familiarizado com essas propriedades do Javascript.

Como você pode ver, isso também requer a adição da classe `HTMLElement`.
Esta classe estende a classe [`Element`][doc-domelement].
No futuro, poderemos adicionar propriedades a elas também, mas isso será deixado
de fora desta RFC por enquanto.
Os elementos que estão dentro do _namespace_ `HTML` agora retornarão uma
instância de `HTMLElement` em vez de [`Element`][doc-domelement].
Por exemplo, `$documentElement` é uma propriedade na classe
[`Document`][doc-domdocument] do tipo [`Element`][doc-domelement].
Se este for um elemento HTML, obteremos uma instância de `HTMLElement` em vez de
[`Element`][doc-domelement].
Tudo isso está definido nas especificações.

### `TokenList`

Proponho adicionar a
[classe `TokenList` da especificação DOM][spec-domtokenlist] ao PHP:

```php
namespace Dom {
    /**
    * @not-serializable
    * @strict-properties
    */
    final class TokenList implements \IteratorAggregate, \Countable {
        private function __construct() {}

        /** @readonly */
        public int $length;
        public function item(int $index): ?string {}
        public function contains(string $token): bool {}
        public function add(string ...$tokens): void {}
        public function remove(string ...$tokens): void {}
        public function toggle(string $token, ?bool $force = null): bool {}
        public function replace(string $token, string $newToken): bool {}
        public function supports(string $token): bool {}
        public string $value;

        public function count(): int {}

        public function getIterator(): \Iterator {}
    }
}
```

Uma instância de `TokenList` pode ser obtida através da propriedade
`Element::$classList`.
Por enquanto, seu propósito está limitado a gerenciar os nomes das classes de um
elemento, mas a classe é construída para representar um conjunto de tokens.
Superficialmente, pode parecer trivial gerenciar os nomes de classes em
documentos, mas isso não é bem verdade.
`TokenList` considerará as classes como um conjunto, lidará com normalização de
espaços em branco, iteração, manipulações fáceis como alternância, etc., tudo
disponível para você em uma API fácil de usar.

#### Exemplos

**Exemplo 1: Operações básicas**

```php
$dom = Dom\XMLDocument::createFromString("<root class='primeiro segundo\tterceiro'/>");
$root = $dom->documentElement;
$list = $root->classList;

var_dump($list);
/*
object(Dom\TokenList)#3 (2) {
["length"]=>
int(3)
["value"]=>
string(25) "primeiro segundo terceiro"
}
*/

var_dump($list->contains("segundo")); // bool(true)
var_dump($list->toggle("segundo")); // bool(false)
var_dump($root->className); // string(17) "primeiro terceiro"

$list->replace("terceiro", "outra-classe");
var_dump($list->item(1)); // string(12) "outra-classe"
```

### Adições Específicas do PHP

A extensão DOM já implementa algumas extensões específicas do PHP para as
classes DOM, como suporte à normalização e canonização.
Para melhor suportar algumas cargas de trabalho, proponho as seguintes adições
específicas do PHP:

```php
namespace Dom {
    /**
    * @not-serializable
    * @strict-properties
    */
    final class NamespaceInfo
    {
        public readonly ?string $prefix;
        public readonly ?string $namespaceURI;
        public readonly Element $element;

        private function __construct() {}
    }

class Attr /* ... */ {
    public function rename(?string $namespace, string $qualifiedName): void {}
}

class Element /* ... */ {
    public string $substitutedNodeValue;

        /** @return list<NamespaceInfo> */
        public function getInScopeNamespaces(): array {}

        /** @return list<NamespaceInfo> */
        public function getDescendantNamespaces(): array {}

        public function rename(?string $namespace, string $qualifiedName): void {}
    }
}
```

Vamos examiná-las uma por uma.

#### `NamespaceInfo`

Esta classe é a substituta moderna da classe
[`DOMNamespaceNode`][doc-domnamespacenode].
[`DOMNamespaceNode`][doc-domnamespacenode] foi mal projetada porque tenta ser um
[`Node`][doc-domnode], mas, na verdade, não é um nó porque não está na árvore.
Por exemplo, no "DOM antigo", ao usar `getAttributeNode("xmlns")`, ele pode
retornar um [`DOMNamespaceNode`][doc-domnamespacenode] para a declaração de
_namespace_, mesmo que não exista necessariamente tal atributo.
A outra maneira de obter uma instância
[`DOMNamespaceNode`][doc-domnamespacenode] é via XPath usando o eixo
`namespace::*`.

A razão pela qual retornamos a instância
[`DOMNamespaceNode`][doc-domnamespacenode]
para o XPath é devido a algumas regras peculiares estabelecidas pela
[Recomendação do XPath][rec-namespace-nodes].
Em particular, o eixo de _namespace_ precisa retornar todos os _namespaces_ em
escopo de um elemento.
No entanto, esse link da especificação _também_ afirma:

> Os elementos nunca compartilham nós de _namespace_: se um nó de elemento não
> for o mesmo nó que outro nó de elemento, então nenhum dos nós de _namespace_
> de um nó de elemento será o mesmo nó que os nós de _namespace_ de outro nó de
> elemento.

Por isso, não podemos retornar o nó de atributo correspondente à declaração do
_namespace_ (se houver) porque teríamos que retornar o _mesmo_ nó de atributo
para elementos _diferentes_.
Consequentemente, o [`DOMNamespaceNode`][doc-domnamespacenode] é retornado no
"DOM antigo".
No entanto, implementar isso no "novo DOM" é um problema porque estaríamos
retornando algo de uma consulta XPath que _não é_ um nó.
Isso é confuso para as pessoas usuárias e também para as ferramentas de análise
estática.

Como essas APIs também são implementadas por navegadores, vale a pena ver como
eles resolvem esse problema e o que diz a especificação.
Acontece que tudo isso não está documentado nas especificações e os navegadores
não implementam o eixo de _namespace_.

Proponho adicionar dois métodos ao "novo DOM" que substituem a funcionalidade do
eixo de _namespace_: `getInScopeNamespaces`, que substitui `./namespace::*` e
`getDescendantNamespaces`, que substitui `.//namespace::*`.
Quando as pessoas usuárias tentarem consultar nós de _namespace_ a partir do
eixo de namespace em `Dom\XPath`, lançaremos uma
[`DOMException`][doc-domexception] com `$code`
[`DOM_NOT_SUPPORTED_ERR`][doc-dom-not-supported-err], redirecionando as pessoas
usuárias para usar um desses dois métodos.

Para identificar um _namespace_, precisamos apenas saber o prefixo, o URI e o
elemento com escopo definido.
Portanto, ele possui esses três campos.
Só pode ser construído pela extensão DOM, não pelas pessoas usuárias.
Nenhuma propriedade específica do nó será implementada em `NamespaceInfo`.

As principais vantagens são:

* A garantia de que as consultas XPath para nós sempre retornarão nós.
* Melhores resultados de análise estática.
* Menos confusão para as pessoas usuárias.

##### Exemplos

```php
$dom = Dom\XMLDocument::createFromString(<<<XML
<root xmlns="urn:a">
    <b:sibling xmlns:b="urn:b" xmlns:d="urn:d" d:foo="bar">
        <d:child xmlns:d="urn:d2"/>
    </b:sibling>
</root>
XML);

$sibling = $dom->documentElement->firstElementChild;
var_dump($sibling->getInScopeNamespaces());
var_dump($sibling->getDescendantNamespaces());
```

**Exemplo: saída de `getInscopeNamespaces()`**

```text
array(3) {
    [0]=>
    object(Dom\NamespaceInfo)#2 (3) {
        ["prefix"]=>
        NULL
        ["namespaceURI"]=>
        string(5) "urn:a"
        ["element"]=> ...
        (<b:sibling>)
    }
    [1]=>
    object(Dom\NamespaceInfo)#4 (3) {
        ["prefix"]=>
        string(1) "b"
        ["namespaceURI"]=>
        string(5) "urn:b"
        ["element"]=> ...
        (<b:sibling>)
    }
    [2]=>
    object(Dom\NamespaceInfo)#5 (3) {
        ["prefix"]=>
        string(1) "d"
        ["namespaceURI"]=>
        string(5) "urn:d"
        ["element"]=> ...
        (<b:sibling>)
    }
}
```

**Exemplo: saída de `getInScopeNamespaces()`**

```text
array(6) {
    [0]=>
    object(Dom\NamespaceInfo)#5 (3) {
        ["prefix"]=>
        NULL
        ["namespaceURI"]=>
        string(5) "urn:a"
        ["element"]=> ...
        (<b:sibling>)
    }
    [1]=>
    object(Dom\NamespaceInfo)#4 (3) {
        ["prefix"]=>
        string(1) "b"
        ["namespaceURI"]=>
        string(5) "urn:b"
        ["element"]=> ...
        (<b:sibling>)
    }
    [2]=>
    object(Dom\NamespaceInfo)#2 (3) {
        ["prefix"]=>
        string(1) "d"
        ["namespaceURI"]=>
        string(5) "urn:d"
        ["element"]=> ...
        (<b:sibling>)
    }
    [3]=>
    object(Dom\NamespaceInfo)#6 (3) {
        ["prefix"]=>
        NULL
        ["namespaceURI"]=>
        string(5) "urn:a"
        ["element"]=> ...
        (<d:child>)
    }
    [4]=>
    object(Dom\NamespaceInfo)#8 (3) {
        ["prefix"]=>
        string(1) "b"
        ["namespaceURI"]=>
        string(5) "urn:b"
        ["element"]=> ...
        (<d:child>)
    }
    [5]=>
    object(Dom\NamespaceInfo)#9 (3) {
        ["prefix"]=>
        string(1) "d"
        ["namespaceURI"]=>
        string(6) "urn:d2"
        ["element"]=> ...
        (<d:child>)
    }
}
```

#### `$substitutedNodeValue`

No "DOM antigo", a propriedade [`$nodeValue`][doc-nodevalue] realizava a
substituição de entidade, o que vai contra as especificações e pode causar
[problemas de segurança][issue-8388].
No "novo DOM", [`$nodeValue`][doc-nodevalue] não substitui entidades (conforme
pretendido pelas especificações).
No entanto, isso significa que não podemos mais substituir entidades _de
propósito_.
Este não é o caso de uso mais comum, mas às vezes é necessário ao lidar com XML
_que você confia_.
A propriedade `$substitutedNodeValue` será o valor do nó, mas com a substituição
de entidade explicitamente habilitada.

##### Exemplos

**Exemplo 1: Definir o valor substituído em uma entidade nativa**

```php
$dom = Dom\XMLDocument::createFromString('<root/>');
$root = $dom->documentElement;

$root->substitutedNodeValue = "&amp;";

var_dump($root->textContent); // string(1) "&"

// Nota: isso irá escapar a entidade conforme as regras de serialização do XML.
echo $dom->saveXml(); // <root>&amp;</root>
```

#### Método `rename`

Esse método é apenas parcialmente específico do PHP.
Ele existia no [DOM Core Level 3][spec-dom-level-3], mas nunca foi implementado
no PHP.
Ele não existe mais no padrão atual: os autores o removeram para simplificar a
API e acho que também porque a especificação DOM é mais centrada em HTML hoje em
dia do que em XML.
Propomos algo muito semelhante ao que existia nas especificações, mas
ligeiramente melhorado.

Às vezes é necessário alterar um prefixo de _namespace_ para um
elemento/atributo, alterar o nome de um elemento/atributo ou alterar seu URI de
_namespace_.
Este caso de uso ocorre ao combinar diferentes documentos ou ao corrigir
documentos, como, por exemplo, com implementações SOAP criadas por pessoas
usuárias.
Isso pode ser feito hoje recriando toda a subárvore sob um elemento com o novo
nome, prefixo e _namespace_; mas isso é extremamente irritante e difícil de
acertar.
Essa abordagem também não funcionará se você tiver referências à mesma instância
de [`Element`][doc-domelement], pois agora um trecho de código está
funcionando em um novo nó enquanto outros trechos de código funcionam no nó
antigo.

Acontece que alterar essas propriedades é realmente muito fácil de fazer
internamente, então faz sentido apenas expor essa funcionalidade à pessoa
usuária.

Você verá que o método rename segue a mesma assinatura do método
[`createElementNS`][doc-createelementns] e também executa as mesmas verificações
de integridade relacionadas ao _namespace_.
Essas verificações de integridade garantem que as regras relacionadas ao
_namespace_ sejam atendidas e, se não forem, o método lançará uma
[`DOMException`][doc-domexception] do tipo
[`NAMESPACE_ERR`][doc-dom-namespace-err]
(ou [`INVALID_CHARACTER_ERR`][doc-dom-invalid-character-err]).

```php
public function createElementNS(?string $namespace, string $qualifiedName): Element {} // Em Dom\Document
public function rename(?string $namespace, string $qualifiedName): void {} // Em Dom\Element e Dom\Attr
```

O primeiro argumento do método `rename` permite alterar o URI do _namespace_ do
elemento/atributo, enquanto o segundo permite alterar o nome qualificado.
O nome qualificado é a combinação do prefixo e do nome local; ou apenas o nome
local se não houver nenhum prefixo.
Você pode estar se perguntando: "Por que não dividir esse método em vários
métodos diferentes?".
A resposta é que isso não é possível: o _namespace_ escolhido tem implicações
sobre quais nomes qualificados são permitidos.
Portanto, em alguns casos você terá que alterar esses dois _simultaneamente_.
É claro que é possível alterar apenas um dos dois enquanto mantém o outro
intacto, mas isso deve acontecer conforme as regras relacionadas ao _namespace_.

Vimos anteriormente como os elementos no _namespace_ `HTML` criarão uma
instância
de `HTMLElement` em vez de [`Element`][doc-domelement].
Isso impõe uma restrição à API `rename` porque, caso contrário, será possível
criar um [`Element`][doc-domelement] no _namespace_ `HTML` ou um `HTMLElement`
que não esteja no namespace `HTML`.
Portanto, se o elemento estiver no _namespace_ `HTML`, ele deverá permanecer
nesse _namespace_; e se não estiver no _namespace_ `HTML`, não poderá entrar no
_namespace_ `HTML`.
Se você tentar fazer isso, uma [`DOMException`][doc-domexception] com `$code`
[`DOM_INVALID_MODIFICATION_ERR`][doc-dom-invalid-modification-err] será lançada.

##### Exemplos

**Exemplo 1: Operação básica em um elemento**

```php
$dom = Dom\XMLDocument::createFromString('<root/>');
$root = $dom->documentElement;
$root->rename(NULL, 'documento');

echo $dom->saveXml(); // <documento/>

$root->rename('urn:teste', 'documento');

echo $root->namespaceURI; // urn:teste
var_dump($root->prefix); // NULL
echo $dom->saveXml(); // <documento xmlns="urn:teste"/>

$root->rename('urn:teste', 'prefixo:documento');

echo $root->namespaceURI; // urn:teste
var_dump($root->prefix); // prefixo
echo $dom->saveXml(); // <prefixo:documento xmlns:prefixo="urn:teste"/>
```

**Exemplo 2: Alterando o nome de um elemento HTML**

```php
$dom = Dom\HTMLDocument::createFromString('<p>olá</p>', LIBXML_NOERROR);
$p = $dom->getElementsByTagName('p')[0];

$p->rename($p->namespaceURI, 'span');

echo $dom->saveHTML(); // <html><head></head><body><span>olá</span></body></html>
```

**Exemplo 3: Alterando o nome de um atributo**

```php
$dom = Dom\HTMLDocument::createFromString('<p align="center"></p>', LIBXML_NOERROR);
$p = $dom->getElementsByTagName('p')[0];
$attr = $p->getAttributeNode('align');

$attr->rename($attr->namespaceURI, 'title');

echo $dom->saveHTML(); // <html><head></head><body><p title="center"></p></body></html>
```

**Exemplo 4: Alterar o prefixo de um elemento, mantendo o restante intacto
(exemplo de caso especial)**

```php
$dom = Dom\XMLDocument::createFromString('<prefixo:root xmlns:prefixo="urn:x"/>');
$root = $dom->documentElement;
$root->rename($root->namespaceURI, 'foo:' . $root->localName);

// Prefixo alterado, mas não na serialização devido ao namespace urn:x estar
// vinculado ao "prefixo" pelo atributo.
var_dump($root->prefix); // string(3) "foo"
echo $dom->saveXML(); // <prefixo:root xmlns:prefixo="urn:x"/>

// Corrigimos isso renomeando o atributo ou removendo-o.
$root->removeAttribute('xmlns:prefixo');
echo $dom->saveXML(); // <foo:root xmlns:foo="urn:x"/>
```

### Permitindo Melhorias Específicas do PHP na Experiência da Pessoa Desenvolvedora

Funções DOM como
[`Element::insertAdjacentElement(string $where, Element $element)`][doc-insertadjacentelement]
e
[`Element::insertAdjacentText(string $where, string $data)`][doc-insertadjacenttext]
têm um primeiro argumento `$where`.
Existem apenas quatro valores válidos para `$where`: `"beforebegin"`,
`"afterbegin"`, `"foreend"`, `"afterend"`.
Então, na verdade, isso é uma _enum_ disfarçada.
Proponho usar o recurso [`enum`][doc-enum] do PHP.
Isso evitaria erros de programação e tornaria as dicas do IDE muito mais
agradáveis, contribuindo para uma melhor experiência da pessoa desenvolvedora.
Estritamente falando, isso se desvia das especificações do DOM, mas, de qualquer
forma, já modelamos as classes DOM de uma forma que se ajusta ao modelo OOP do
PHP.
Na verdade, eu proporia permitir o uso de _enums_ onde fizer sentido na extensão
para novas APIs.
Como a classe `Element` não existia antes da
[RFC de conformidade opcional com a especificação DOM][rfc-spec-compliance],
podemos alterar a assinatura sem afetar os usuários, já que nenhuma versão do
PHP 8.4 foi feita até agora.

Em particular, isso resultará nas seguintes assinaturas de função e _enum_:

```php
namespace Dom {
    enum AdjacentPosition : string {
        case BeforeBegin = "beforebegin";
        case AfterBegin = "afterbegin";
        case BeforeEnd = "beforeend";
        case AfterEnd = "afterend";
    }

    class Element /* ... */ {
        public function insertAdjacentElement(AdjacentPosition $where, Element $element): ?Element {}
        public function insertAdjacentText(AdjacentPosition $where, string $data): void {}
    }
}
```

A _enum_ `AdjacentPosition` é apoiada de forma que os valores literais da
especificação DOM ainda possam ser usados usando
`AdjacentPosition::from("beforebegin")`, etc.

### Emendas de API

Inicialmente, a
[RFC de conformidade opcional com a especificação DOM][rfc-spec-compliance]
copiou as APIs existentes das antigas classes DOM sem mudanças para a maioria
das APIs.
Alguém relatou que `(DOM)Document::xinclude()` tem um comportamento estranho de
valor de retorno.
Em particular, citando a documentação:

> Retorna o número de `XIncludes` no documento, -1 se algum processamento falhou
> ou `false` se não houve substituições.

Isso parece ser causado por um erro de implementação.
O comportamento mais sensato seria lançar um erro em caso de falha (para evitar
confusão com `0`/`false`) e retornar o número de substituições em caso de
sucesso.
Se não houve substituições o número 0 deverá ser retornado.

A nova assinatura desta função ficaria assim:

```php
final class XMLDocument extends Document {
    public function xinclude(int $options = 0): int {}
}
```

A exceção lançada será [`DOMException`][doc-domexception] com `$code` definido
como [`DOM_INVALID_MODIFICATION_ERR`][doc-dom-invalid-modification-err].

## Alterações Incompatíveis com Versões Anteriores

Nenhum porque esta RFC afeta apenas as classes adicionadas na versão 8.4.

## Versões Propostas do PHP

PHP 8.4.

## Impacto da RFC

### Para Extensões Existentes

Apenas a [`ext-dom`][doc-dom] é afetada.

## _Issues_ Abertas

Nenhuma ainda.

## Funcionalidade PHP Não Afetada

Tudo fora da [`ext-dom`][doc-dom].

## Escopo Futuro

Inicialmente planejei incluir a propriedade `outerHTML` também.
Isso é muito viável com todo o trabalho interno do DOM que aconteceu durante o
ciclo de desenvolvimento do PHP 8.4.
Porém, como não tenho visto demanda por isso, acho que meu tempo será melhor
gasto com outros recursos.
Se alguém realmente quiser isso no PHP 8.4, sinta-se à vontade para fazer uma
implementação de PoC, deve ser bastante viável usando Lexbor e as atuais APIs
internas da [`ext-dom`][doc-dom].

A classe `HTMLElement` pode oferecer algumas propriedades úteis, mas isso foi
deixado de fora porque ninguém realmente solicitou esse recurso até agora, então
o tempo de desenvolvimento é melhor gasto em outro lugar.

## Escolhas de Votação Propostas

Uma votação primária sim/não com maioria de 2/3 para aceitar esta proposta na
totalidade.

A votação começou em 10/06/2024 e terminará em 24/06/2024.

### Aceita a RFC de Adições ao DOM no PHP 8.4?

| Nome                                                | Sim | Não |
|-----------------------------------------------------|:---:|:---:|
| [adiel][user-adiel] (adiel)                         |  X  |     |
| [ashnazg][user-ashnazg] (ashnazg)                   |  X  |     |
| [beberlei][user-beberlei] (beberlei)                |  X  |     |
| [crell][user-crell] (crell)                         |  X  |     |
| [devnexen][user-devnexen] (devnexen)                |  X  |     |
| [galvao][user-galvao] (galvao)                      |  X  |     |
| [girgias][user-girgias] (girgias)                   |  X  |     |
| [heiglandreas][user-heiglandreas] (heiglandreas)    |  X  |     |
| [jimw][user-jimw] (jimw)                            |  X  |     |
| [josh][user-josh] (josh)                            |  X  |     |
| [kguest][user-kguest] (kguest)                      |  X  |     |
| [kocsismate][user-kocsismate] (kocsismate)          |  X  |     |
| [levim][user-levim] (levim)                         |  X  |     |
| [mauricio][user-mauricio] (mauricio)                |  X  |     |
| [mbeccati][user-mbeccati] (mbeccati)                |  X  |     |
| [nicolasgrekas][user-nicolasgrekas] (nicolasgrekas) |  X  |     |
| [nielsdos][user-nielsdos] (nielsdos)                |  X  |     |
| [petk][user-petk] (petk)                            |  X  |     |
| [pierrick][user-pierrick] (pierrick)                |  X  |     |
| [ramsey][user-ramsey] (ramsey)                      |  X  |     |
| [sebastian][user-sebastian] (sebastian)             |  X  |     |
| [sergey][user-sergey] (sergey)                      |  X  |     |
| [theodorejb][user-theodorejb] (theodorejb)          |  X  |     |
| [timwolla][user-timwolla] (timwolla)                |  X  |     |
| [weierophinney][user-weierophinney] (weierophinney) |  X  |     |
| **Total**                                           | 25  |  0  |

## _Patches_ e Testes

- [Implementação do seletor CSS][pull-13819]
- [Implementação de `innerHTML`][pull-104]
- [Implementação de `TokenList`][pull-13664]
- [Implementação de propriedades de `HTMLDocument`][pull-13791]
- [Implementação de extensões específicas do PHP][pull-93]

## Implementação

Depois que o projeto for implementado, esta seção deverá conter:

- as versões nas quais foi feito o _merge_
- um link para os _commits_ do git
- um link para a entrada no manual do PHP para o recurso
- um link para a seção de especificação da linguagem (se houver)

## Referências

- [Tratamento de erros de `innerHTML`][message-123224]
- [Especificação DOM][spec-dom]
- [Especificação HTML que define adendos ao DOM][spec-html]
- [Antiga solicitação do recurso para obter _namespaces_ em escopo][bug-63410]
- [Solicitação de recurso para `TokenList`][issue-11688]
- [Discussão (externals.io)][message-123405]

## _Changelog_

* 0.1: Primeira versão colocada em discussão e votação

## Agradecimentos

Gostaria de agradecer a [Toon Verwerft][user-veewee] por seus comentários e
testes iniciais.

[bug-63410]:
https://bugs.php.net/bug.php?id=63410

[doc-createelementns]:
/docs/php/doc/8/domdocument.createelementns.html

[doc-dom]:
/docs/php/doc/8/book.dom.html

[doc-dom-invalid-character-err]:
/docs/php/doc/8/dom.constants.html#constant.dom-invalid-character-err

[doc-dom-invalid-modification-err]:
/docs/php/doc/8/dom.constants.html#constant.dom-invalid-modification-err

[doc-dom-namespace-err]:
/docs/php/doc/8/dom.constants.html#constant.dom-namespace-err

[doc-dom-not-supported-err]:
/docs/php/doc/8/dom.constants.html#constant.dom-not-supported-err

[doc-dom-syntax-err]:
/docs/php/doc/8/dom.constants.html#constant.dom-syntax-err

[doc-domdocument]:
/docs/php/doc/8/class.domdocument.html

[doc-domelement]:
/docs/php/doc/8/class.domelement.html

[doc-domexception]:
/docs/php/doc/8/class.domexception.html

[doc-domnamespacenode]:
/docs/php/doc/8/class.domnamespacenode.html

[doc-domnode]:
/docs/php/doc/8/class.domnode.html

[doc-domnodelist]:
/docs/php/doc/8/class.domnodelist.html

[doc-enum]:
/docs/php/doc/8/language.enumerations.html

[doc-insertadjacentelement]:
/docs/php/doc/8/domelement.insertadjacentelement.html

[doc-insertadjacenttext]:
build/docs/php/doc/8/domelement.insertadjacenttext.html

[doc-libxml-noerror]:
/docs/php/doc/8/libxml.constants.html#constant.libxml-noerror

[doc-nodevalue]:
/docs/php/doc/8/class.domnode.html#domnode.props.nodevalue

[email-nielsdos]:
mailto:nielsdos@php.net

[issue-8388]:
https://github.com/php/php-src/issues/8388

[issue-11688]:
https://github.com/php/php-src/issues/11688

[message-123224]:
https://externals.io/message/123224

[message-123405]:
https://externals.io/message/123405

[pull-93]:
https://github.com/nielsdos/php-src/pull/93

[pull-104]:
https://github.com/nielsdos/php-src/pull/104

[pull-13664]:
https://github.com/php/php-src/pull/13664

[pull-13791]:
https://github.com/php/php-src/pull/13791

[pull-13819]:
https://github.com/php/php-src/pull/13819

[rfc-dom-additions-84]:
https://wiki.php.net/rfc/dom_additions_84

[rfc-html5-parser]:
https://wiki.php.net/rfc/domdocument_html5_parser

[rfc-spec-compliance]:
https://wiki.php.net/rfc/opt_in_dom_spec_compliance

[rec-namespace-nodes]:
https://www.w3.org/TR/1999/REC-xpath-19991116/#namespace-nodes

[spec-document]:
https://html.spec.whatwg.org/#document

[spec-dom]:
https://dom.spec.whatwg.org/

[spec-dom-level-3]:
https://www.w3.org/TR/2004/REC-DOM-Level-3-Core-20040407/

[spec-domtokenlist]:
https://dom.spec.whatwg.org/#interface-domtokenlist

[spec-html]:
https://html.spec.whatwg.org

[spec-innerhtml]:
https://html.spec.whatwg.org/#the-innerhtml-property

[user-adiel]:
https://people.php.net/adiel

[user-ashnazg]:
https://people.php.net/ashnazg

[user-beberlei]:
https://people.php.net/beberlei

[user-crell]:
https://people.php.net/crell

[user-devnexen]:
https://people.php.net/devnexen

[user-galvao]:
https://people.php.net/galvao

[user-girgias]:
https://people.php.net/girgias

[user-heiglandreas]:
https://people.php.net/heiglandreas

[user-jimw]:
https://people.php.net/jimw

[user-josh]:
https://people.php.net/josh

[user-kguest]:
https://people.php.net/kguest

[user-kocsismate]:
https://people.php.net/kocsismate

[user-levim]:
https://people.php.net/levim

[user-mauricio]:
https://people.php.net/mauricio

[user-mbeccati]:
https://people.php.net/mbeccati

[user-nicolasgrekas]:
https://people.php.net/nicolasgrekas

[user-nielsdos]:
https://people.php.net/nielsdos

[user-petk]:
https://people.php.net/petk

[user-pierrick]:
https://people.php.net/pierrick

[user-ramsey]:
https://people.php.net/ramsey

[user-sebastian]:
https://people.php.net/sebastian

[user-sergey]:
https://people.php.net/sergey

[user-theodorejb]:
https://people.php.net/theodorejb

[user-timwolla]:
https://people.php.net/timwolla

[user-veewee]:
https://github.com/veewee/

[user-weierophinney]:
https://people.php.net/weierophinney
