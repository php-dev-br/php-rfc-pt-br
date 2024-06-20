---
source_url: https://wiki.php.net/rfc/xmlreader_writer_streams
revision: 1718313707
status: wip
license: https://www.php.net/copyright
---

# Novos Recursos da `ext-dom` no PHP 8.4

* Versão: 0.1
* Data: 12/04/2024
* Pessoas autoras: Niels Dossche, <nielsdos@php.net>
* Situação: Em votação
* Publicada pela primeira vez em:
  [https://wiki.php.net/rfc/dom_additions_84](https://wiki.php.net/rfc/dom_additions_84)

## Introdução

O ciclo de desenvolvimento do PHP 8.4 já viu duas melhorias importantes na
extensão `ext-dom`:
[suporte ao HTML 5](https://wiki.php.net/rfc/domdocument_html5_parser) e
[conformidade opcional com a especificação DOM](https://wiki.php.net/rfc/opt_in_dom_spec_compliance).
Esta RFC é (provavelmente) a última melhoria da `ext-dom` para o PHP 8.4: ela
propõe adicionar novos recursos à extensão.
Em particular, focaremos no suporte ao seletor CSS, preenchendo recursos
ausentes, mas comuns, e adicionando novas propriedades.
Essas melhorias e alterações se aplicam apenas às novas classes no namespace
`Dom`.

## Proposal

The RFC consists of multiple sub-proposals bundled together under one RFC to
minimize overhead.
In this section, we'll discuss each proposal separately.

### CSS selectors

There exist multiple ways to query nodes in an XML or HTML document.
The one that's already implemented since the existence of the DOM extension is
using XPath.
Another popular way, that people are likely more familiar with, is CSS
selectors.
In theory, every query you can write with CSS selectors can also be written with
XPath.
However, XPath is much more cumbersome to use in a lot of cases.
For example, a simple query like ''p:contains("hello") + span'' is equivalent
to ''./​/p[contains(normalize-space(),"hello")]/following-sibling::*[1]/self::
span''.
Things can get much more complicated when you use pseudo-functions like '':
disabled'' which are a real pain to express in XPath.

The DOM spec defines the following CSS selector functions:
<PHP>
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
</PHP>

This is what the methods do:

* querySelector: Returns the first descendant element that matches the CSS
  selectors
* querySelectorAll: Returns a NodeList containing all descendant elements that
  match the CSS selectors
* closest: Finds the closest ancestor of the element that matches the CSS
  selectors
* matches: Returns true if the element matches the CSS selectors, false
  otherwise

It's worth noting that CSS selectors can contain pseudo-classes that only make
sense when something is rendered on screen.
Like for example '':hover'', which matches when a user hovers over an element.
Because in the context of PHP this is nonsensical, a CSS selector that uses such
a pseudo-class will match nothing.

While it's possible to implement ''closest'' and ''matches'' using XPath, it
cannot be done performance-efficiently (as far as I know).

The underlying library we use for the HTML5 parsing also contains the CSS
functionality necessary to implement these methods.
Therefore, we can get the functionality relatively easily.
I only had to adapt the node data structures to match PHP's data structures.

There exist workarounds in userland that implement a CSS selector to XPath
translation, but based on what I've seen:

* They will take a performance hit because translation isn't "free"
* They don't provide an efficient way to implement ''closest'' and ''matches''
* Because they are implemented around the old DOM classes, and the old DOM
  classes didn't take into account the different HTML namespaces properly, they
  also don't take into account the namespaces properly.

=== Examples ===

**Example 1: querySelector**

<PHP>
$dom = Dom\XMLDocument::createFromString(<<<XML
<root>
  <span>1</span>
  <p>hi</p>
  <span>2</span>
</root>
XML);

var_dump($dom->querySelector('p ~ span')->textContent); // string(1) "2"
</PHP>

**Example 2: closest**

<PHP>
$dom = Dom\XMLDocument::createFromString(<<<XML
<root>
  <div class="foo" xml:id="div1">
    <div xml:id="div2">
      <div class="bar" xml:id="div3"/>
    </div>
  </div>
</root>
XML);

var_dump($dom->getElementById('div3')->closest('div')->getAttribute("xml:
id")); // string(4) "div3"
var_dump($dom->getElementById('div3')->closest(':not(div[class])')->
getAttribute("xml:id")); // string(4) "div2"
</PHP>

**Example 3: matches**

<PHP>
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
</PHP>

### Element::$innerHTML

This is a property on the Element class defined in the DOM
spec: https://html.spec.whatwg.org/#the-innerhtml-property

<PHP>
namespace Dom {
  class Element /* ...
*/ {
    public string $innerHTML;
  }
}
</PHP>

Reading from this field will get the serialization of the inner content of the
element, writing to it will parse a string into a subtree and replace the
contents of the element with the new subtree.
If the document is an HTML document, the HTML parser / serializer will be used.
If the document is an XML document, the XML parser / serializer will be used.
Yes, that means that inner**HTML** can set **XML** content, and this is as
defined by spec.
This naming oopsie is legacy baggage from the spec that stems from the fact that
the Element class is shared between XML and HTML documents for interopability.

If the serialization is not well-formed for XML, then a DOMException with <php>
$code</php> DOM_SYNTAX_ERR will be thrown, as defined by the spec.

Parsing documents (or fragments) can cause hard/soft errors.
The soft errors are reported via warnings, or if the internal error handling
mechanism is used then the errors are stored inside an array.
Unless LIBXML_NOERROR is provided, in which case those soft errors are silenced.
Note that we don't have a way to provide a parsing option to the innerHTML
property, and so we cannot provide a way to silence the errors cleanly.
I asked about this on the mailing list (https://externals.io/message/123224) but
got no response.
This probably means that people are uncertain or don't care, and so I choose to
not implement the error reporting because it's easier to omit something and add
it later than it is to remove something later.

### New properties for Document

I propose the additional of several new properties to the Document class to make
developing a bit easier:

<PHP>
namespace Dom {
  class HTMLElement extends Element {
    /* There's an opportunity to add useful HTML-spec properties here for the future.
*/
  }

class Document /* ...
*/ {
public ?HTMLElement $body;
/** @readonly */
public ?HTMLElement $head;
public string $title;
}
}
</PHP>

These additions are described in the HTML addendum for the DOM specification
in https://html.spec.whatwg.org/#document.

The properties should be relatively self-explanatory.
<php>$body</php> refers to the body element (if there is one), <php>$head</php>
to the head element (if there is one), and <php>$title</php> to the text inside
the title element (which in turn is inside the head element).
You can read about all the details using the link above, because it's a bit more
complicated when SVG is involved for example, but you should be familiar with
these properties from Javascript.

As you can see, this requires adding the HTMLElement class as well.
This class extends the Element class.
In the future we may add properties on them too but this is left out of this RFC
for now.
Elements that are within the HTML namespace will now return an instance of
HTMLElement instead of Element.
For example, <php>$documentElement</php> is a property on the Document class of
type Element.
If this is an HTML element, we will get an instance of HTMLElement instead of
Element.
This is all as defined in the spec.

### TokenList

I propose to add the TokenList class from the DOM specification to
PHP (https://dom.spec.whatwg.org/#interface-domtokenlist):

<PHP>
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
</PHP>

An instance of TokenList can be obtained via the <php>Element::$classList</php>
property.
As of now, its purpose is limited to managing the class names of an element, but
the class is built in a way that it represents a set of tokens.
On the surface level, it might seem trivial to manage the class names in
documents, but that's not quite true.
TokenList will consider the classes as a set, handle whitespace normalization,
iteration, easy manipulations like toggling, ...
all for you in an easy-to-use API.

=== Examples ===

**Example 1: Basic operations**

<PHP>
$dom = Dom\XMLDocument::createFromString("<root class='first second\tthird'/>");
$root = $dom->documentElement;
$list = $root->classList;

var_dump($list);
/*
object(Dom\TokenList)#3 (2) {
["length"]=>
int(3)
["value"]=>
string(18) "first second third"
}
*/

var_dump($list->contains("second")); // bool(true)
var_dump($list->toggle("second")); // bool(false)
var_dump($root->className); // string(11) "first third"

$list->replace("third", "something-else");
var_dump($list->item(1)); // string(14) "something-else"
</PHP>

### PHP-specific additions

The DOM extension already implements some PHP-specific extensions to the DOM
classes, like normalization and canonicalization support.
To better support some workloads, I propose the following PHP-specific
additions:

<PHP>
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

class Attr /* ...
*/ {
public function rename(?string $namespace, string $qualifiedName): void {}
}

class Element /* ...
*/ {
public string $substitutedNodeValue;

    /** @return list<NamespaceInfo> */
    public function getInScopeNamespaces(): array {}

    /** @return list<NamespaceInfo> */
    public function getDescendantNamespaces(): array {}

    public function rename(?string $namespace, string $qualifiedName): void {}

}
}
</PHP>

Let's go over them one by one.

=== NamespaceInfo ===

This class is the modern replacement of the <php>DOMNamespaceNode</php> class.
<php>DOMNamespaceNode</php> is misdesigned in that it tries to be a Node, but it
actually isn't a node because it's not in the tree.
For example, in "old DOM", when using <php>getAttributeNode("xmlns")</php> it
may return a <php>DOMNamespaceNode</php> for the namespace declaration even
though there's not necessarily such an attribute.
The other way you could obtain a <php>DOMNamespaceNode</php> instance is via
XPath by using the ''namespace::*'' axis.

The reason we have the <php>DOMNamespaceNode</php> instance returned for XPath
is because of some peculiar rules laid out
by https://www.w3.org/TR/1999/REC-xpath-19991116/#namespace-nodes.
In particular, the namespace axis needs to return all in-scope namespaces for an
element.
However that spec link //also// states:

<blockquote>Elements never share namespace nodes: if one element node is not the same node as another element node, then none of the namespace nodes of the one element node will be the same node as the namespace nodes of another element node.</blockquote>

So we can't return the attribute node corresponding to the namespace
declaration (if there even is one) because we'd have to return the //same//
attribute node for //different// elements.
Hence, the <php>DOMNamespaceNode</php> is returned in "old DOM".
However, implementing this in "new DOM" is a problem because we'd be returning
something from an XPath query that //isn't// a node.
This is confusing for users and also for static analysis tools.

Because these APIs are also implemented by browsers, it's worth looking at how
they solve this problem and what the spec says.
Turns out this is all undocumented in the spec, and browsers don't implement the
namespace axis at all.

I propose to add two methods to "new DOM" that replace the namespace axis
functionality: <php>getInScopeNamespaces</php> that replaces ''./namespace::*''
and <php>getDescendantNamespaces</php> that replaces ''./​/namespace::*''.
When users would try to query namespace nodes from the namespace axis in <php>
Dom\XPath</php>, we'll throw a DOMException with <php>$code</php>
DOM_NOT_SUPPORTED_ERR, redirecting users to use one of these two methods.

To identify a namespace we only need to know the prefix, the uri, and the
element it is scoped upon.
Therefore, it has these three fields.
It can only be constructed by the DOM extension, not by users.
No node-specific properties will be implemented in <php>NamespaceInfo</php>.

The main advantages are:

* The guarantee that XPath queries for nodes will always return nodes
* Better static analysis results
* Less confusion for users

== Examples ==

<PHP>
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
</PHP>

**Example: getInscopeNamespaces() output**

<code>
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
</code>

**Example: getInscopeNamespaces() output**
<code>
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
</code>

=== $substitutedNodeValue ===

In "old DOM", the <php>$nodeValue</php> property performed entity substitution,
which goes against the spec and can
cause [[https://github.com/php/php-src/issues/8388|security issues]].
In "new DOM", <php>$nodeValue</php> does not substitute entities (as intended by
spec).
However, that means we can no longer substitute entities //on purpose//.
This isn't the most common use-case, but is sometimes necessary when dealing
with XML //that you trust//.
The <php>$substitutedNodeValue</php> property will be the node's value, but with
entity substitution explicitly enabled.

== Examples ==

**Example 1: Setting the substituted value to a built-in entity**

<PHP>
$dom = Dom\XMLDocument::createFromString('<root/>');
$root = $dom->documentElement;

$root->substitutedNodeValue = "&amp;";

var_dump($root->textContent); // string(1) "&"

// Note: this will escape the entity in accordance to the XML serialization
rules
echo $dom->saveXml(); // <root>&amp;</root>
</PHP>

=== rename method ===

This is only partially PHP-specific.
This method did kind of exist
in [[https://www.w3.org/TR/2004/REC-DOM-Level-3-Core-20040407/|DOM Core Level 3]],
but was never implemented in PHP.
It doesn't exist anymore in the living standard: the authors removed it to
simplify the API and I think also because the DOM spec is more HTML-centric
nowadays than XML-centric.
We propose something very similar to what once existed in spec, but slightly
improved.

Sometimes it's necessary to either change a namespace prefix for an
element/attribute, change an element/attribute's name, or change its namespace
URI.
This use-case occurs when combining different documents, or fixing up documents,
like for example with userland SOAP implementations.
You can //kinda// do this today by recreating the entire subtree under an
element with the new name, prefix, and namespace; but this is extremely annoying
and difficult to get right.
This approach also won't work if you have references to the same Element
instance as now one piece of code is working on a new node while other pieces of
code work on the old node.

It turns out that changing these properties is actually super easy to do
internally, so it makes sense to just expose this functionality to the user.

You'll see that the rename method follows the same signature as the <php>
createElementNS</php> method, and it also performs the same namespace-related
sanity checks.
These sanity checks ensure that the namespace-related rules are satisfied, and
if they're not, the method will throw a ''NAMESPACE_ERR'' (or ''
INVALID_CHARACTER_ERR'') type of <php>DOMException</php>.

<PHP>
public function createElementNS(?string $namespace, string $qualifiedName): Element {} // in Dom\Document
public function rename(?string $namespace, string $qualifiedName): void {} // In Dom\Element and Dom\Attr
</PHP>

The first argument of the rename method allows you to change the namespace URI
of the element/attribute, while the second one allows you to change the
qualified name.
The qualified name is the combination of the prefix and local name; or just the
local name if there is no prefix.
You may be wondering: "why not split this method up into multiple different
methods?".
The answer is that it's not possible to do: the namespace you choose has
implications on what qualified names are allowed.
Therefore, in some cases you have to change these two at the //same time//.
It is of course possible to just change one of the two while keeping the other
intact, but that must happen in accordance to the namespace-related rules.

We have previously seen how elements in the HTML namespace will create an
instance of ''HTMLElement'' instead of ''Element''.
This imposes a restriction on the rename API because otherwise it becomes
possible to create Elements in the HTML namespace or HTMLElements not in the
HTML namespace.
Therefore, if the element is in the HTML namespace, it must remain in that
namespace; and if it's not in the HTML namespace, it may not enter the HTML
namespace.
If you try to do this, a DOMException with <php>$code</php>
DOM_INVALID_MODIFICATION_ERR will be thrown.

== Examples ==

**Example 1: Basic operation on an element**

<PHP>
$dom = Dom\XMLDocument::createFromString('<root/>');
$root = $dom->documentElement;
$root->rename(NULL, 'document');

echo $dom->saveXml(); // <document/>

$root->rename('urn:test', 'document');

echo $root->namespaceURI; // urn:test
var_dump($root->prefix); // NULL
echo $dom->saveXml(); // <document xmlns="urn:test"/>

$root->rename('urn:test', 'prefix:document');

echo $root->namespaceURI; // urn:test
var_dump($root->prefix); // prefix
echo $dom->saveXml(); // <prefix:document xmlns:prefix="urn:test"/>
</PHP>

**Example 2: Changing an HTML element's name**

<PHP>
$dom = Dom\HTMLDocument::createFromString('<p>hello</p>', LIBXML_NOERROR);
$p = $dom->getElementsByTagName('p')[0];

$p->rename($p->namespaceURI, 'span');

echo $dom->saveHTML(); // <html><head></head><body><span>
hello</span></body></html>
</PHP>

**Example 3: Changing an attribute's name**

<PHP>
$dom = Dom\HTMLDocument::createFromString('<p align="center"></p>', LIBXML_NOERROR);
$p = $dom->getElementsByTagName('p')[0];
$attr = $p->getAttributeNode('align');

$attr->rename($attr->namespaceURI, 'title');

echo $dom->
saveHTML(); // <html><head></head><body><p title="center"></p></body></html>
</PHP>

**Example 4: Changing an element's prefix, keeping the rest intact (special-case
example)**

<PHP>
$dom = Dom\XMLDocument::createFromString('<prefix:root xmlns:prefix="urn:x"/>');
$root = $dom->documentElement;
$root->rename($root->namespaceURI, 'foo:' .
$root->localName);

// Prefix changed, but not in serialization due to the namespace urn:x being
bound to "prefix" by the attribute
var_dump($root->prefix); // string(3) "foo"
echo $dom->saveXML(); // <prefix:root xmlns:prefix="urn:x"/>

// We fix this by either renaming the attribute or removing it
$root->removeAttribute('xmlns:prefix');
echo $dom->saveXML(); // <foo:root xmlns:foo="urn:x"/>
</PHP>

### Allowing PHP-specific developer experience improvements

DOM functions like <php>Element::insertAdjacentElement(string $where, Element
$element)</php> and <php>Element::insertAdjacentText(string $where, string
$data)</php> have a first "where" argument.
There are only four valid values for "where": "beforebegin", "afterbegin", "
beforeend", "afterend".
So that's actually an enum in disguise.
I propose to make use of the PHP enum feature.
This would prevent programming mistakes and make IDE hints much nicer,
contributing to a better developer experience.
Strictly speaking, this deviates from the DOM spec, but we already model the DOM
classes in a way that fits PHP's OOP model anyway.
In fact, I'd propose to allow the use of enums where it makes sense in the
extension for new APIs.
Since the Element class didn't exist prior to the opt-in spec compliance RFC, we
can change the signature without affecting users as no releases of PHP 8.4 have
been made so far.

In particular, this will result in the following enum and function signatures:
<PHP>
namespace Dom {
enum AdjacentPosition : string {
case BeforeBegin = "beforebegin";
case AfterBegin = "afterbegin";
case BeforeEnd = "beforeend";
case AfterEnd = "afterend";
}

class Element /* ...
*/ {
public function insertAdjacentElement(AdjacentPosition $where, Element
$element): ?Element {}
public function insertAdjacentText(AdjacentPosition $where, string $data):
void {}
}
}
</PHP>

The <php>AdjacentPosition</php> enum is backed such that the literal values from
the DOM spec can still be used by using <php>AdjacentPosition::from("
beforebegin")</php> etc.

### API amendments

Initially, the [DOM spec-compliance RFC][rfc-opt-in-dom-spec-compliance] copied
the existing APIs from the old DOM classes without a deviation for most APIs.
Someone reported that the <php>(DOM)Document::xinclude()</php> has weird return
value behaviour.
In particular, quoting from the documentation:
<blockquote>Returns the number of XIncludes in the document, -1 if some processing failed, or false if there were no substitutions.
</blockquote>
This seems to be caused by an implementation mistake.
The more sensical behaviour would be to throw on failure (to avoid 0/false confusion), and return the number of substitutions on success.
If there were no substitutions the number 0 should be returned.

The new signature of this function would look like this:
<PHP>
final class XMLDocument extends Document {
public function xinclude(int $options = 0): int {}
}
</PHP>

The exception thrown will be DOMException with <php>$code</php> set to
INVALID_MODIFICATION_ERR.

## Backward Incompatible Changes

None because this RFC only affects classes added in 8.4.

## Proposed PHP Version(s)

PHP 8.4.

## RFC Impact

### To Existing Extensions

Only ext-dom is affected.

## Open Issues

None yet.

## Unaffected PHP Functionality

Everything outside ext-dom.

## Future Scope

I initially planned on including the outerHTML property too.
This is very feasible with all the internal DOM work that happened during the
PHP 8.4 development cycle.
However, given that I haven't seen demand for this, I think my time is better
spent with other features.
If someone really wants this in 8.4, feel free to make a PoC implementation,
should be fairly doable using Lexbor and the current ext-dom internal APIs.

The <php>HTMLElement</php> class can offer some useful properties but that's
left out of here because no one really asked for that feature so far, so
development time is better spent elsewhere.

## Proposed Voting Choices

One primary yes/no vote with 2/3 majority to accept this proposal as a whole.

Voting started on 2024-06-10 and will end on 2024-06-24.

<doodle title="Accept PHP 8.4 DOM additions RFC?" auth="nielsdos" voteType="single" closed="false" closeon="2024-06-24T21:00:00+02:00">
   * Yes
   * No
</doodle>

## Patches and Tests

- CSS selector implementation: https://github.com/php/php-src/pull/13819
- innerHTML implementation: https://github.com/nielsdos/php-src/pull/104
- TokenList implementation: https://github.com/php/php-src/pull/13664
- HTMLDocument properties
  implementation: https://github.com/php/php-src/pull/13791
- PHP-specific extensions
  implementation: https://github.com/nielsdos/php-src/pull/93

## Implementation

After the project is implemented, this section should contain

- the version(s) it was merged into
- a link to the git commit(s)
- a link to the PHP manual entry for the feature
- a link to the language specification section (if any)

## References

- innerHTML error handling: https://externals.io/message/123224
- DOM spec: https://dom.spec.whatwg.org/
- HTML spec that defines DOM addendums: https://html.spec.whatwg.org
- Old feature request for getting in scope
  namespaces: https://bugs.php.net/bug.php?id=63410
- Feature request for TokenList: https://github.com/php/php-src/issues/11688
- Discussion (externals.io): https://externals.io/message/123405

## Changelog

* 0.1: First version put under discussion and voting

## Acknowledgements

I'd like to thank [[https://github.com/veewee/|Toon Verwerft]] for his feedback
and early testing.

[rfc-domdocument-html5-parser-html-5-support-and-rfc-opt-in-dom-spec-compliance]: https://wiki.php.net/rfc/domdocument_html5_parser%7CHTML+5+support%5D%5D%2C+and+%5B%5Brfc%3Aopt_in_dom_spec_compliance

[rfc-opt-in-dom-spec-compliance]: https://wiki.php.net/rfc/opt_in_dom_spec_compliance

