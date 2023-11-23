<!-- source_url: https://wiki.php.net/rfc -->
<!-- revision: 1700677205 -->
<!-- status: wip -->

# RFC

Esta página fornece uma visão geral das RFCs atuais do PHP.

Para criar uma RFC, consulte [Como Criar uma RFC][rfc-howto].

**Nota:** Uma RFC é efetivamente "propriedade" da pessoa que a criou.
Se quiser fazer alterações, obtenha permissão do criador.
Se nenhum acordo for alcançado, o único curso de ação é criar uma RFC
concorrente.
Neste caso, a antiga página da RFC deve ser modificada para se tornar uma página
intermediária que aponta para todas as RFCs concorrentes.

Uma nova página no namespace RFC da wiki do PHP será automaticamente carregada
com um [modelo][rfc-template] de RFC. Personalize conforme necessário.

## Em Fase de Votação

Esta seção é para RFCs que estão sendo votadas atualmente.

  * [Unbundle the imap, pspell, and oci8 extensions][rfc-unbundle-imap-pspell-oci8] (Created 2023-08-27)
  * [New 4 rounding modes to round() function][rfc-new-rounding-modes-to-round-function] (Discussion started: 2023-09-31)
  * [Adding bcround, bcfloor and bcceil to BCMath][rfc-adding-bcround-bcfloor-bcceil-to-bcmath] (Created 2023-10-01)

## Em Discussão

Esta seção é para RFCs que foram anunciadas na lista de discussão "internals" do
PHP.

  * [Harmonise "untyped" and "typed" properties][rfc-mixed-vs-untyped-properties] (Created and discussion started: 2023-11-16)
  * [Change how JIT is disabled by default][rfc-jit-config-defaults] (Created 2023-11-15, Discussion started 2023-11-15)
  * [Final anonymous classes][rfc-final-anonymous-classes] (Created 2023-11-15, Discussion started 2023-11-15)
  * [Resource to object conversion][rfc-resource-to-object-conversion] (Created 2023-10-31, Discussion started: 2023-11-12)
  * [Release cycle update][rfc-release-cycle-update] (Created 2023-11-05, Discussion started: 2023-11-10)
  * [Improve callbacks in ext/dom and ext/xsl][rfc-improve-callbacks-dom-and-xsl] (Created 2023-11-05, Discussion started: 2023-11-07)
  * [Change the edge case of round()][rfc-change-the-edge-case-of-round] (Created 2023-10-23)
  * [RFC1867 for non-POST HTTP verbs][rfc-rfc1867-non-post] (Created 2023-10-06)
  * [Rounding Integers as int][rfc-integer-rounding] (Created 2023-09-26, Discussion started: 2023-09-26)
  * [Closure self-reference][rfc-closure-self-reference] (Discussion started: 2023-06-03)
  * [Allow getting the name of a variable during runtime][rfc-nameof] \\ Adds nameof() to get the name of variables, closures, and members during runtime. (Discussion started: 2023-05-13)
  * [Property access hooks][rfc-property-hooks] (Created 2022-12-01)
  * [Clone with][rfc-clone-with] (Discussion started: 2023-04-17)
  * [New core autoloading mechanism with support for function autoloading][rfc-core-autoloading] (Discussion started: 2023-04-10)
  * [Working With Substrings][rfc-working-with-substrings] (Discussion started: 2023-02-14)
  * [Add file_descriptor() function][rfc-file-descriptor-function] (Discussion started: 2023-01-16)
  * [Add SameSite cookie attribute parameter][rfc-same-site-parameter] (Discussion started: 2023-01-14)
  * [Unicode Text Processing][rfc-unicode-text-processing] (Created 2022-12-15)
  * [List\unique() and Assoc\unique()][rfc-list-assoc-unique] (Created 2022-12-01)
  * [shell_exec() $result_code parameter][rfc-shell-exec-result-code-param] (Created 2021-11-21)
  * [final class Deque][rfc-deque] (Created 2021-09-19)
  * [final class Vector][rfc-vector] (Created 2021-09-16)
  * [Default User-Agent for cURL][rfc-curl-user-agent]
  * [Deprecate boolean to string coercion][rfc-deprecate-boolean-string-coercion] (Created: 2021-06-22)
  * [Property Accessors][rfc-property-accessors] (Created 2021-05-04)
  * [Autoload Classmap][rfc-autoload-classmap] (Created: 2021-03-15)
  * [Concepts to improve mysqli extension][rfc-improve-mysqli] (Created 2020-12-30)
  * [Wall-Clock Time Based Execution Timeout][rfc-max-execution-wall-time] (Created 2020-12-12)
  * [Named parameters explicit opt in][rfc-renamed-parameters] (Created 2020-07-24)
  * [Objects can be declared falsifiable][rfc-objects-can-be-falsifiable] (Created 2020-07-14)
  * [Property write/set visibility][rfc-property-write-visibility] (Created 2020-06-29)
  * [Change terminology to ExcludeList][rfc-change-terminology-to-excludelist] (Created 2020-06-09)
  * [<<Deprecated>> Attribute][rfc-deprecated-attribute]\\ This RFC proposes an attribute to mark declarations as deprecated (Created 2020-05-07)
  * [Change var_export() array syntax to use shorthand arrays][rfc-var-export-array-syntax] (Created 2020-03-29)
  * [__toArray()][rfc-to-array] \\ Add a new <nowiki>__toArray()</nowiki> magic method (Created: 2019-08-28)
  * [Prevent disruptions of conversations][rfc-prevent-disruptions-of-conversations] \\ (Created: 2019-09-19)
  * [Normalize arrays' "auto-increment" value on copy on write][rfc-normalize-array-auto-increment-on-copy-on-write] \\ (Discussion started: 2019-06-20)
  * [Alternative "use" syntax for Closures][rfc-alternative-closure-use-syntax] \\ (Discussion started: 2019-06-15)
  * [Nullable Casting][rfc-nullable-casting] \\ Support nullable types in casting (Discussion started: 2019-04-06)

## Em Rascunho

Esta seção é para rascunhos iniciais de RFCs que NÃO foram anunciadas na lista
de discussão "internals" do PHP.

  * [Remove disable_classes INI setting][rfc-remove-disable-classes] (Created 2023-09-29)
  * [Deprecations for PHP 8.4][rfc-deprecations-php-8-4] (Created 2023-07-25)
  * [Introduce array_group and array_group_pair grouping functions][rfc-array-group] (Created 2023-06-01)
  * [Implicit Move Optimisation][rfc-implicit-move-optimisation] (Created: 2023-05-13)
  * [Access Scope from Magic Accessors][rfc-access-scope-from-magic-accessors] (Discussion started: 2023-01-19)
  * [Property Capture for Anonymous Classes][rfc-property-capture] (Created: 2022-04-13)
  * Function interfaces
      * [Closure::castTo][rfc-allow-casting-closures-into-single-method-interface-implementations]
      * [Explicit closure interfaces][rfc-allow-closures-to-declare-interfaces-they-implement]
      * [Structural Typing for Closures][rfc-structural-typing-for-closures]
  * [Types for Local Variables][rfc-local-variable-types] (Created 2023-02-08)
  * [Miscellaneous Variable Functions][rfc-misc-variable-functions] (Created 2023-01-28)
  * [is_valid_utf8()][rfc-is-valid-utf8] (Created 2023-01-27)
  * [2D Matrix Operations][rfc-2d-matrix-operations] (Created 2023-01-24)
  * [gd imageexportpixels() and imageimportpixels()][rfc-gd-image-export-import-pixels] (Created 2023-01-23)
  * [LiteralString][rfc-literal-string] (Created 2022-12-27)
  * [Random migration][rfc-random-migration] (Created 2022-12-22)
  * [Sorting Enum][rfc-sorting-enum] ( Created 2021-09-01 )
  * [Iterator chaining][rfc-iterator-chaining] (Created 2021-03-20)
  * [Algebraic data types (Meta RFC)][rfc-adts] (Created 2020-11-11)
     * [Tagged Unions (Enums)][rfc-tagged-unions] (Created 2020-09-19)
     * [Pattern matching ''is'' keyword][rfc-pattern-matching] (Created 2020-11-11)
     * ''isIdentical()'' method override (future scope)
     * Advanced pattern matching (future scope)
  * [Type declarations in array destructuring expressions][rfc-typehint-array-desctructuring] (Created 2020-04-16)
  * [Variable declarations before usage][rfc-declare-vars] \\ Optionally require variables to be declared before usage (Created: 2019-09-19)
  * [Unbundle unmaintained extensions in PHP 8][rfc-unbunle-unmaintained-extensions-php8] \\ Unbundle or assign the PHP Group as maintainer to unmaintained extensions (Created: 2019-07-15)
  * [Comprehensions (short generators)][rfc-comprehensions] \\ Generator Comprehensions for PHP (Created: 2019-03-10)
  * [Improved Error Callback Mechanism][rfc-improved-error-callback-mechanism] \\ This RFC aims to give extensions that intercept errors a better way to register their callbacks. (Created 2015-03-13)
  * [Add support for stream-wrapped URLs in opcode cache][rfc-url-opcode-cache] \\ Adds a generic way to opcode-cache code generated through a stream wrapper. (Created 2017/05/25)

## Aprovadas

  * [Multibyte for trim function mb_trim, mb_ltrim and mb_rtrim][rfc-mb-trim] (Created 2023-10-19)

### Processos e Políticas

  * [Namespaces in bundled PHP extensions][rfc-namespaces-in-bundled-extensions] (Created 2021-02-25)
  * [Abolish Short Votes][rfc-abolish-short-votes] \\ Proposal to abolish voting periods of less than two weeks (Created 2019-03-21, Voting ended: 2019-04-22)
  * [Abolish Narrow Margins][rfc-abolish-narrow-margins] \\ Proposal to abolish 50%+1 votes (Created 2016-11-17, Voting ended: 2019-02-22)
  * [Security Issue Classification][rfc-security-classification] \\ Ratify reformed security issue classification. (Accepted 2016-11-18)
  * [PHP 5 Support Timeline][rfc-php56timeline]\\ Determine the Active & Support timelines for PHP 5.
  * [Reserve Even More Types in PHP 7][rfc-reserve-even-more-types-in-php-7] \\ A proposal to reserve even more type names in PHP 7 (Created 2015-02-20)
  * [PHP 7.0 Timeline][rfc-php7timeline]\\ Define an agreed-upon timeline and milestones for PHP 7.0.
  * [Keeping the tests green][rfc-travis-ci] \\ This RFC proposes a policy for keeping PHP CI tests green.
  * [Define PHP 5.3 end of life][rfc-php53eol]\\ The purpose of this RFC is to define when the PHP 5.3 series will no longer be supported.
  * [Release Process][rfc-releaseprocess]\\ PHP release process.
  * [Voting Process][rfc-voting]\\ PHP voting process.
  * [Magic Quotes][rfc-magicquotes]\\ This RFC proposes how we deal with magic quotes from PHP 5.3.0 to 6.0.0.
  * [Choosing a distributed version control system for PHP][rfc-dvcs]\\ This RFC proposes to migrate the PHP SVN repo to a DVCS.
  * [PHP Version Control System][rfc-phpvcs]\\ This RFC discusses the switch from CVS to some other version tracking system
  * [Name of Next Release of PHP][rfc-php6]\\ To settle what the name of the next major release of PHP shall be. (Created 2014-07-05)
  * [MD5 Release Checksum][rfc-release-md5-deprecation] \\ Deprecate MD5 checksums from Release process (Created: 2017-05-30)
  * [Class Naming][rfc-class-naming] \\ Specify how to deal with abbreviations and acronyms in the coding standard (Created: 2017-06-03)
  * [Cleaning up unmaintained extensions][rfc-umaintained-extensions] \\ (Created: 2016-08-07; Accepted: 2018-06-26)
  * [Migrating to GitHub Issues][rfc-github-issues] (Created 2021-11-01)

### Implementação/Versão de Destino Pendente

  * [PDO driver specific sub-classes][rfc-pdo-driver-specific-subclasses] (Created 2022-06-20, Voting start: 2023-07-03, Voting closed: 2023-07-17)
  * [APXS LoadModule][rfc-apxs-loadmodule]\\ This RFC proposes the addition of an option to the configure script that allows the user to specify whether the main Apache .conf file should be appended with the LoadModule entry.
  * [DateTime and Daylight Saving Time Transitions][rfc-datetime-and-daylight-saving-time]\\ Defines expected behaviors and new features to improve how DateTime handles Daylight Saving Time transitions.
  * PHP 9.0: [Undefined Property Error Promotion][rfc-undefined-property-error-promotion] (Created: 2022-04-04)
  * PHP 9.0: [Undefined variables error promotion][rfc-undefined-variable-error-promotion] (Created: 2022-02-17)

## Implementadas

**Ordem nestas seções:** Mudanças na linguagem primeiro, mudanças na biblioteca
depois.

### PHP 8.4

  * [DOM HTML5 parsing and serialization][rfc-domdocument-html5-parser] (Created 2023-08-12, Discussion started: 2023-09-02, Voting started: 2023-10-02, Voting ended: 2023-10-16)
  * [A new JIT implementation based on IR Framework][rfc-jit-ir] (Created 2023-09-20, Discussion started: 2023-09-21, Voting ended: 2023-10-19)
  * [XML_OPTION_PARSE_HUGE][rfc-xml-option-parse-huge] (Created 2023-09-21, Discussion started: 2023-09-21, Voting started: 2023-10-07, Voting closed: 2023-10-21)
  * [Increasing the default BCrypt cost][rfc-bcrypt-cost-2023] (Created 2023-09-07)

### PHP 8.3

  * [Deprecations for PHP 8.3][rfc-deprecations-php-8-3] (Created 2022-08-01)
  * [Path to Saner Increment/Decrement operators][rfc-saner-inc-dec-operators] (Discussion started: 2023-01-17, Voting start: 2023-06-28, Voting end: 2023-07-12)
  * [Marking overridden methods (#[\Override])][rfc-marking-overriden-methods] (Created: 2023-05-06, Voting started: 2023-06-14)
  * [Arbitrary static variable initializers][rfc-arbitrary-static-variable-initializers] (Created 2022-11-06)
  * [Make unserialize() emit a warning for trailing data][rfc-unserialize-warn-on-trailing-data] (Discussion started: 2023-03-27)
  * [Dynamic class constant fetch][rfc-dynamic-class-constant-fetch] (Created 2022-11-04)
  * [Improve unserialize() error handling][rfc-improve-unserialize-error-handling] (Created 2022-09-01, Voting opened 2022-10-14, Voting closed 2022-10-28)
  * [Readonly amendments][rfc-readonly-amendments] (Created 2022-10-24)
  * [Typed Class Constants][rfc-typed-class-constants] (Discussion started: 2023-01-31, Voting started: 2023-02-27)
  * [Deprecate remains of string evaluated code assertions][rfc-assert-string-eval-cleanup] (Created: 2023-05-31, Voting start: 2023-06-28, Voting end: 2023-07-12)
  * [mb_str_pad][rfc-mb-str-pad] (Created: 2023-05-19, Discussion started: 2023-05-20, Voting started: 2023-06-05, Voting closed: 2023-06-19)
  * [product)()][rfc-saner-array-sum-product-saner-array-sum] (Discussion started: 2023-01-17, Voting opened 2023-02-20, Voting closed 2023-03-06, Implemented: 2023-03-07)
  * [Define proper semantics for range() function][rfc-proper-range-semantics] (Discussion started: 2023-03-27, Voting started: 2023-06-01, Voting ended: 2023-06-15)
  * [Randomizer Additions][rfc-randomizer-additions] (Created 2022-10-09)
  * [More Appropriate Date/Time Exceptions][rfc-datetime-exceptions] (Created 2022-11-29, Implemented: 2023-02-08)
  * [json_validate function][rfc-json-validate] (Created 2022-08-14, Voting closed: 2022-10-07)
  * [Use exceptions by default in SQLite3 extension][rfc-sqlite3-exceptions]
  * [Deprecate functions with overloaded signatures][rfc-deprecate-functions-with-overloaded-signatures] (Discussion started: 2023-04-27, Voting started: 2023-06-26, Voting ended: 2023-07-10)

### PHP 8.2

  * [Constants in Traits][rfc-constants-in-traits] (Created 2022-06-21, Voting closed: 2022-07-19)
  * [Random Extension 5.x][rfc-rng-extension] (Created 2021-05-19, Voting closed: 2022-06-28)
  * [Random Extension Improvement][rfc-random-extension-improvement] (Created 2022-06-16, Voting closed: 2022-07-16)
  * [Fetch properties of enums in const expressions][rfc-fetch-property-in-const-expressions] (Created 2022-05-27)
  * [Disjunctive Normal Form Types][rfc-dnf-types] (Created 2021-11-04, Voting opened: 2022-06-17, Voting closed: 2022-07-03)
  * [Add true type][rfc-true-type] (Created 2022-04-07, Voting opened: 2022-05-29, Voting closed: 2022-06-12)
  * [MySQLi Execute Query][rfc-mysqli-execute-query] (Created 2022-04-21, Voting opened: 2022-05-11, Voting closed: 2022-05-25)
  * [Readonly classes][rfc-readonly-classes] (Created 2021-08-04)
  * [Allow null and false as stand-alone types][rfc-null-false-standalone-types] (Created 2022-02-20, Voting start: 2022-03-12, Voting end: 2022-03-27)
  * [Locale-independent case conversion][rfc-strtolower-ascii] (Created 2021-09-22)
  * [Deprecate partially supported callables][rfc-deprecate-partially-supported-callables] (Created 2021-09-02)
  * [Expand deprecation notice scope for partially supported callables][rfc-partially-supported-callables-expand-deprecation-notices] (Created 2022-05-12, Voting opened: 2022-05-31)
  * [Deprecate dynamic properties][rfc-deprecate-dynamic-properties] (Created 2021-08-23)
  * [Redacting parameters in back traces][rfc-redact-parameters-in-back-traces] ( Created 2022-01-10 )
  * [Deprecate ${} string interpolation][rfc-deprecate-dollar-brace-string-interpolation] (Created on 2021-03-13)
  * [Remove support for libmysql from mysqli][rfc-mysqli-support-for-libmysql] ( Created 2022-01-06)
  * [Deprecate and remove utf8_decode() and utf8_encode()][rfc-remove-utf8-decode-and-utf8-encode]
  * [Make the iterator_*() family accept all iterables][rfc-iterator-xyz-accept-array] (Created 2022-06-21, Voting opened: 2022-07-05)

### PHP 8.1

  * [Disable autovivification on false][rfc-autovivification-false] (Created 2021-05-25)
  * [Pure intersection types][rfc-pure-intersection-types] (Created 2021-03-23, Voting started 2021-06-03, Voting ended 2021-06-17, Merged 2021-07-05)
  * [Add IntlDatePatternGenerator][rfc-intldatetimepatterngenerator] (Voting started 2021-05-14 and ended 2021-05-28)
  * [Deprecate implicit non-integer-compatible float to int conversions][rfc-implicit-float-int-deprecate] (Voting started 2021-04-01, Voting ended 2021-04-14)
  * [Enumerations][rfc-enumerations] (Created 2020-09-19)
  * [Deprecate passing null to non-nullable arguments of internal functions][rfc-deprecate-null-to-scalar-internal-arg] (Created 2020-12-01)
  * [Array unpacking with string keys][rfc-array-unpacking-string-keys] (Created 2021-01-07)
  * [Add array_is_list(array $array): bool][rfc-is-list] (Created 2020-12-19)
  * [Explicit octal integer literal notation][rfc-explicit-octal-notation] (Created: 2020-10-20, Voting Started: 2020-11-11, Voting Ended: 2020-11-25, Merged into master: 2021-01-04)
  * [Restrict $GLOBALS usage][rfc-restrict-globals-usage] (Created 2020-12-02)
  * [Change Default mysqli Error Mode][rfc-mysqli-default-errmode] (Created 2021-01-20)
  * [Add fetch_column method to mysqli][rfc-mysqli-fetch-column] (Created 2021-03-28)
  * [Mysqli bind in execute][rfc-mysqli-bind-in-execute] (Created 2021-02-11)
  * [fsync() Function][rfc-fsync-function] (Created 2021-01-30)
  * [noreturn type][rfc-noreturn-type] (Voting started 2021-03-30)
  * [Fibers][rfc-fibers] (Created 2020-12-04)
  * [Phasing out Serializable][rfc-phase-out-serializable] (Created 2020-12-07)
  * [Static variables in inherited methods][rfc-static-variable-inheritance] (Created 2021-02-23)
  * [Add return type declarations for internal methods][rfc-internal-method-return-types] (Created 2021-03-06)
  * [Final class constants][rfc-final-class-const] (Created 2021-05-04)
  * [Make reflection setAccessible() no-op][rfc-make-reflection-setaccessible-no-op] (Created 2021-06-13)
  * [New in initializers][rfc-new-in-initializers] (Created 2021-03-02)
  * [Deprecations for PHP 8.1][rfc-deprecations-php-8-1] (Created 2019-07-23)
  * [First-class callable syntax][rfc-first-class-callable-syntax] (Created 2021-05-20)
  * [Readonly properties 2.0][rfc-readonly-properties-v2] (Created 2021-06-02)

### PHP 8.0

  * [Shorter Attribute Syntax Change][rfc-shorter-attribute-syntax-change] (Created 2020-07-28)
  * [Don't automatically unserialize Phar metadata outside getMetadata()][rfc-phar-stop-autoloading-metadata] (Created 2020-07-07)
  * [Reclassifying engine warnings][rfc-engine-warnings] \\ Reevaluate the current level of various engine notices/warnings. (Created: 2019-08-27)
  * [Shorter Attribute Syntax][rfc-shorter-attribute-syntax] \\ Use ''@@'' instead of ''%%<<>>%%'' for attributes in PHP 8.0 (Created 2020-06-03)
  * [Ensure correct signatures of magic methods][rfc-magic-methods-signature] (Created 2020-04-05)
  * [Named Arguments][rfc-named-params]\\ This RFC proposes introducing named arguments. (Created 2013-09-06)
  * [Treat namespaced names as single token][rfc-namespaced-names-as-token] (Created 2020-06-16)
  * [Saner string to number comparison][rfc-string-to-number-comparison] \\ Proposes to change non-strict comparisons between strings and numbers to behave more reasonably. (Created: 2019-02-26)
  * [Saner numeric strings][rfc-saner-numeric-strings] (Created 2020-06-28)
  * [Nullsafe operator][rfc-nullsafe-operator] \\ Add new ?-> operator that skips null values (Created 2020-06-02)
  * [Allow trailing comma in closure use lists][rfc-trailing-comma-in-closure-use-list] (Created 2020-07-01)
  * [Configurable string length in getTraceAsString()][rfc-throwable-string-param-max-len] (Created 2020-06-27)
  * [Remove inappropriate inheritance signature checks on private methods][rfc-inheritance-private-methods] \\ Proposes that inappropriate inheritance checks are removed for private methods (Created: 2017-02-07)
  * [Match expression v2][rfc-match-expression-v2]\\ Introduce match expression (Created 2020-05-22)
  * [Attribute Amendments][rfc-attribute-amendments]\\ Group Syntax, Rename PhpAttribute, Target Validation, Repeatable (Created 2020-05-20)
  * [Make sorting stable][rfc-stable-sorting]\\ Make all sorts in PHP stable by default (Created 2020-05-12)
  * [Constructor Property Promotion][rfc-constructor-promotion] \\ Adds a short-hand syntax to combine declaration of properties and the constructor. (Created 2020-03-26)
  * [Attributes (v2)][rfc-attributes-v2] \\ Add structured metadata to declarations (classes, functions, properties, constants) for internal and userland use-cases. (Created 2020-03-09)
  * [Unbundle ext/xmlrpc][rfc-unbundle-xmlprc] \\ (Created 2020-04-25; Accepted 2020-05-26)
  * [Always available JSON extension][rfc-always-enable-json] \\ (Created 2020-04-29)
  * [Non-capturing catches][rfc-non-capturing-catches] \\ Allow catching exceptions without a variable (Created 2020-04-05)
  * [Mixed type v2][rfc-mixed-type-v2] \\ Add the mixed type (Created 2020-03-22)
  * [Locale-independent float to string cast][rfc-locale-independent-float-to-string] (Created 2020-03-11)
  * [Change default PDO error mode][rfc-pdo-default-errmode] (Created 2020-03-28)
  * [Stricter type checks for arithmetic/bitwise operators][rfc-arithmetic-operator-type-checks] (Created 2020-04-02)
  * [Add str_starts_with and str_ends_with to PHP][rfc-add-str-starts-with-and-ends-with-functions] (Created 2020-03-25)
  * [Allow trailing comma in parameter list][rfc-trailing-comma-in-parameter-list] (Created 2020-03-26)
  * [throw expression][rfc-throw-expression]\\ Convert throw statement into an expression (Created 2020-03-21)
  * [Object-based token_get_all() alternative][rfc-token-as-object]\\ Adds an object-based token_get_all() alternative, which is more ergonomic and uses less memory. (Created: 2020-02-13)
  * [Abstract trait method validation][rfc-abstract-trait-method-validation] \\ Enforce signature of abstract trait methods. (Created: 2020-02-07)
  * [Stringable][rfc-stringable] \\ Allow using ''string|Stringable'' to express ''string|object-with-%%__toString()%%''. (Created 2020-01-15)
  * [Allow ::class on objects][rfc-class-name-literal-on-object] \\ Adds support for ''$object::class''. (Created: 2020-01-09)
  * [Static return type][rfc-static-return-type] \\ Adds support for ''static'' as a return type. (Created: 2020-01-08)
  * [Variable Syntax Tweaks][rfc-variable-syntax-tweaks] \\ Fixes variable syntax edge cases. (Created: 2020-01-07)
  * [Union Types v2][rfc-union-types-v2] \\ A proposal to add union types (Created 2019-09-04)
  * [DOM Living Standard API][rfc-dom-living-standard-api] \\ Upgrade DOM API to latest standard version (Created: 2019-03-13)
  * [Always generate fatal error for incompatible method signatures][rfc-lsp-errors] \\ Resolve inconsistent handling of abstract and non-abstract methods during inheritance. (Created: 2019-04-08)
  * [Arrays starting with a negative index][rfc-negative-array-index] \\ Proposes to make implicit array keys consistent. (Created: 2017-04-20)
  * [Consistent type errors for internal functions][rfc-consistent-type-errors] \\ Consistently throw ''TypeError'' for parameter parsing failures of internal functions. (Created: 2019-02-05, Voting started: 2019-02-19)
  * [JIT][rfc-jit] \\ Just in Time Compiler. (Created: 2019-01-28)
  * [Weak maps][rfc-weak-maps] \\ Add a ''WeakMap'' class (Created: 2019-11-04)
  * [str_contains][rfc-str-contains] \\ Adds a new function to return whether or not a string is contained within another. (Created: 2020-02-17)
  * [get_debug_type][rfc-get-debug-type]\\ Adds a new function to return the true type name of a variable, automatically resolving class names. (Created: 2020-02-15)
  * [Add support for CMS][rfc-add-cms-support]\\ Exposes CMS API from OpenSSL (Created 2020-05-13)

### PHP 7.4

  * [Deprecations for PHP 7.4][rfc-deprecations-php-7-4] \\ Functionality to be deprecated in PHP 7.4. (Discussion started: 2019-06-21)
  * [Deprecate alternate access to array elements and chars in string][rfc-deprecate-curly-braces-array-access] \\ Deprecate curly braces array and string syntax access. (Created: 2019-03-12; Discussion started:2019-03-15; Voting started: 2019-07-03; Voting ends: 2019-07-17; Accepted: 2019-07-17)
  * [ E_WARNING for invalid containers][rfc-notice-for-non-valid-array-container] \\ Raise E_WARNING for array access on invalid containers (Created 2016-07-27)
  * [Base Convert improvements][rfc-base-convert-improvements] \\ Changes to base convert to warn the user when incorrect values are passed. Also allow negative numbers to be parsed. (Discussion started: 2019-05-18 | Accepted 2019-07-05)
  * [Numeric Literal Separator][rfc-numeric-literal-separator] \\ Enable improved code readability by supporting an underscore between digits in numeric literals. (Accepted: 2019-06-13)
  * [Covariant Returns and Contravariant Parameters][rfc-covariant-returns-and-contravariant-parameters] \\ (Announced: 2018-11-26; Voting began: 2018-12-19)
  * [Allow throwing exceptions from __toString()][rfc-tostring-exceptions] \\ Support throwing exceptions from %%__toString()%%. (Created: 2019-04-30)
  * [Spread Operator in Array Expression][rfc-spread-operator-for-array] \\ (Created: 2018-10-13)
  * [Deprecate left-associative ternary operator][rfc-ternary-associativity] \\ Deprecate nesting of ternaries without explicit use of parentheses. (Created: 2019-04-09)
  * [Arrow functions 2.0][rfc-arrow-functions-v2] \\ Adds short closures / arrow functions.
  * [Deprecate and remove ext/interbase][rfc-deprecate-and-remove-ext-interbase] \\ Deprecate and eventually remove the InterBase extension in the Core (Created 2019-03-22)
  * [weakrefs][rfc-weakrefs] \\ (Created: 2018-05-17, Voting started: 2019-02-22)
  * [FFI - Foreign Function Interface][rfc-ffi] \\ (Announced: 2018-12-06; Voting began: 2018-12-20; Accepted: 2019-01-09)
  * [Typed Properties 2.0][rfc-typed-properties-v2] \\ Add support for typed properties, including static properties and references to typed properties. (Created: 2018-06-15)
  * [Null Coalesce Equal Operator][rfc-null-coalesce-equal-operator] \\ Allow shorthand for self assigning null coalesce operator (Created 2016-03-09)
  * [Preloading][rfc-preload] \\ Preload PHP functions and classes once and use them in the context of any future request without overhead. (Created: 2018-10-18)
  * [Always available hash extension][rfc-permanent-hash-ext] \\ Proposes to make the hash extension available to every build of PHP. (Created: 04/09-2018)
  * [Password Hash Registry][rfc-password-registry] \\ Make the mechanisms used by password_hash/verify/etc... extensible by other modules. (Created: 2018-10-15)
  * [Improve openssl_random_pseudo_bytes()][rfc-improve-openssl-random-pseudo-bytes] \\ Proposes making ''openssl_random_pseudo_bytes()'' fail closed and deprecate the second parameter (Created: 2019-10-19)
  * [mb_str_split() Split multibyte string][rfc-mb-str-split] \\ (Announced: 2019-01-02; Voting began: 2019-01-10; Accepted: 2019-01-20; Implemented: 2019-02-12)
  * [Reflection for references][rfc-reference-reflection] \\ Introduces the ''ReflectionReference'' class to allow detecting references and determining reference equality. (Created: 2019-01-15; Voting began: 2019-01-30)
  * [Unbundle ext/wddx][rfc-deprecate-and-remove-ext-wddx] \\ (Announced: 2018-09-16; Voting began: 2019-01-17 Voting finished: 2019-01-31)
  * [New custom object serialization mechanism][rfc-custom-object-serialization] \\ Introduces new custom object serialization mechanism to replace ''Serializable''. (Created: 2019-01-24, Voting start: 2019-03-01)
  * [Change the precedence of the concatenation operator][rfc-concatenation-precedence] \\ Update the precedence of concatenation to be inferior to addition and subtraction (Created: 2019-03-28)
  * [Argon2 support from sodium][rfc-sodium-argon-hash] \\ Provide password_hash() support for argon2i/argon2id from ext/sodium if standard does not. (Created: 2019-04-05)
  * [Unbundle ext/recode][rfc-unbundle-recode] \\ (Discussion started: 2019-06-14; voting started: 2019-06-28; voting ends: 2019-07-12)
  * [Escape PDO "?" parameter placeholder][rfc-pdo-escape-placeholders] \\ Changes to PDO to allow using operators containing "?" with pdo_pgsql, most commonly the JSON key exists "?" operator. (Discussion started: 2019-05-31; Voting started: 2019-07-08; Accepted: 2019-07-22)

### PHP 7.3

  * [Flexible Heredoc and Nowdoc Syntaxes][rfc--flexible-heredoc-nowdoc-syntaxes]\\ Allow indentation of, and remove newline requirement after, Nowdoc/Heredoc closing markers  (Published: 2017-09-16, Accepted 2017-11-16)
  * [Allow a trailing comma in function calls][rfc-trailing-comma-function-calls] (Published 2017-10-07)
  * [JSON_THROW_ON_ERROR][rfc-json-throw-on-error] \\ Adds a flag to change the JSON extension's error-handling behaviour (Created: 2017-09-10)
  * [PCRE2 Migration][rfc-pcre2-migration] (Published 2017-10-16)
  * [list() Reference Assignment][rfc-list-reference-assignment]\\ This RFC proposes a new syntax to enable reference assignment with list(). (Created 2013/10/25, withdrawn 2014-05-15, Commandeered and Reopened: 2016-12-30, Accepted 2017-02-22)
  * [is_countable function][rfc-is-countable] (Created: 2018-01-21)
  * [array_key_first(), array_key_last()][rfc-array-key-first-last] \\ Add functions for handling the outer keys of an array (Created: 2018-06-11; Voting from 2018-07-09 to 2018-07-16)
  * [Make compact function reports undefined passed variables][rfc-compact] \\ (Created: 2018-05-24; Voting from 2018-06-06 to 2018-06-18)
  * [Argon2 Password Hash Enhancements][rfc-argon2-password-hash-enhancements] \\ (Created: 2018-01-11; Voting from 2018-06-06 to 2018-06-18)
  * [Deprecate and Remove image2wbmp()][rfc-image2wbmp] \\ (Created: 2018-05-11; Voting from 2018-05-26 to 2018-06-09)
  * [Deprecate and Remove Case-Insensitive Constants][rfc-case-insensitive-constant-deprecation] \\ Support for case-insensitive constants is deprecated and scheduled for removal in the next major version.
  * [Deprecations for PHP 7.3][rfc-deprecations-php-7-3] \\ Miscellaneous minor deprecations for PHP 7.3.
  * [Same Site Cookie][rfc-same-site-cookie] \\ Add same site flag to cookies created by core cookie functions (Created: 2017-07-16)

### PHP 7.2

  * [Allow loading extensions by name][rfc-load-ext-by-name] (Created: 2016-05-10)
  * [Allow abstract function override][rfc-allow-abstract-function-override] \\ Allow redefinition of "abstract functions" (Created: 2017-03-01)
  * [Prevent number_format() from returning negative zero][rfc-number-format-negative-zero] \\ Bring consistency to number_format() for negative zero. (Created: 2017-04-01)
  * [Convert numeric keys in object/array casts][rfc-convert-numeric-keys-in-object-array-casts] \\ Fix an edge case in casting objects to arrays and vice-versa. (Created: 2016-10-21)
  * [Deprecate and Remove Bareword (Unquoted) Strings][rfc-deprecate-bareword-strings] \\ Raises the severity of "undefined constant" to E_WARNING and deprecates the fallback to interpreting as a string. (Created: 2017-01-29)
  * [get_class() disallow null parameter][rfc-get-class-disallow-null-parameter] \\ Prevent get_class() having astonishing behaviour
  * [Counting of non-countable objects][rfc-counting-non-countables] \\ Raise a warning when counting invalid objects. (Created: 2016-10-04)
  * [Parameter Type Widening][rfc-parameter-no-type-variance] \\ Allow subclasses to omit a type entirely (Created: 2016-11-21)
  * [Trailing commas in list syntax][rfc-list-syntax-trailing-commas]\\ Allow for trailing commas in all list syntax (Created 2015-11-03)
  * [Deprecate png2wbmp() and jpeg2wbmp()][rfc-deprecate-png-jpeg-2wbmp] \\ Deprecate and later remove the png2wbmp() and jpeg2wbmp() functions. (Created: 2016-10-15)
  * [Implement socket_getaddrinfo()][rfc-socket-getaddrinfo] \\ Implement getaddrinfo() to socket extension. (Created: 2016-08-08)
  * [Argon2 in password hash][rfc-argon2-password-hash] \\ Introduce Argon2 hashing algorithm to password functions (Created: 2016-07-10)
  * [Debugging PDO Prepared Statement Emulation][rfc-debugging-pdo-prepared-statement-emulation] \\ Allow the output of this feature to be examined in userland. (Created: 2016-10-17)
  * [Debugging PDO Prepared Statement Emulation v2][rfc-debugging-pdo-prepared-statement-emulation-v2] \\ Another approach to allowing the output of this feature to be examined in userland. (Created: 2016-11-17)
  * [HashContext as Object][rfc-hash-context-as-resource] \\ Change Hash Contexts to use Objects instead of Resources
  * [Deprecate and remove INTL_IDNA_VARIANT_2003][rfc-deprecate-and-remove-intl-idna-variant-2003] (Created: 2017-01-07)
  * [Extended String Types For PDO][rfc-extended-string-types-for-pdo] \\ Types to handle "national character," i.e. Unicode, string parameters. (Created: 2017-02-16)
  * [Improve TLS constants to sane values][rfc-improved-tls-constants] (Created 2017-05-15)
  * [Object typehint][rfc-object-typehint] \\ Proposes adding ''object'' type-hint and return-type (Created: 2016-08-12)
  * [LDAP EXOP][rfc-ldap-exop] \\ Provide functions to use LDAP extended operations in php-ldap (Created: 2017-06-26)
  * [Libsodium][rfc-libsodium] \\ Make Libsodium a Core Extension (Created 2016-01-07)
  * [Deprecations for PHP 7.2][rfc-deprecations-php-7-2] \\ Functions and features to be deprecated in PHP 7.2 (Created 2015-12-28)

### PHP 7.1

  * [Session ID without hashing][rfc-session-id-without-hashing] \\ Remove hash usage from session ID generation. (Created 2016-04-06)
  * [Asynchronous Signal Handling][rfc-async-signals] \\ Asynchronous Signal Handling without TICKs and any additional overhead. (Created 2016-06-24)
  * [Fix inconsistent behavior of $this variable][rfc-this-var] \\ Fix all known inconsistencies related to special variable $this (Discussion began 2016-05-23)
  * [Replace "Missing argument" warning with "Too few arguments" exception][rfc-too-few-args] \\ (Created 2016-06-01)
  * [Nullable Types][rfc-nullable-types] \\ Allow a type check to be of some type or null (Discussion began 2016-04-13)
  * [Square bracket syntax for array destructuring assignment][rfc-short-list-syntax] \\ An alternative syntax to <php>list()</php> (Created 2016-04-07)
  * [Warn about invalid strings in arithmetic][rfc-invalid-strings-in-arithmetic] \\ Produce E_NOTICE or E_WARNING when using invalid numeric strings with arithmetic operators (Created 2016-01-08)
  * [Allow specifying keys in list()][rfc-list-keys] \\ Adds syntax to help unpacking associative arrays into variables (Created 2016-01-17)
  * [Iterable][rfc-iterable] \\ Iterable pseudo-type accepting arrays or objects implementing Traversable (Created 2016-06-10)
  * [Generalize support of negative string offsets][rfc--negative-string-offsets] \\ Add support for negative string offsets everywhere it makes sense (Created 2016-01-23)
  * [Closure from callable function][rfc-closurefromcallable] \\ Add a function to create closures from callables without reflection
  * [Deprecate mb_ereg_replace eval option][rfc--deprecate-mb-ereg-replace-eval-option] \\ This RFC aims at deprecating the e option that mb_ereg_replace and mb_eregi_replace provide.
  * [Deprecate (and remove) Mcrypt][rfc-mcrypt-viking-funeral] \\ Let's get rid of ext/mcrypt, which is abandonware and inhibits the growth of the language, as soon as humanly possible. (Created 2016-01-09)
  * [OpenSSL AEAD support][rfc--openssl-aead] \\ Adds support for AEAD cipher modes (GCM and CCM) to openssl_decrypt and openssl_encrypt.
  * [Void Return Type][rfc-void-return-type] \\ Adds a void return type to require that a function does not return a value. (Revived 2015-10-04, originally created 2015-02-14)
  * [Class constant visibility modifiers][rfc-class-const-visibility] \\ Introduce class constants visibility modifiers that mirror properties and methods. (Created 2015/09/13)
  * [Octal Overflow Protection][rfc-octal-overload-checking] \\ Stop quietly ignoring overflows in octal number parsing (Created: 2016-04-12)
   * [RNG fixes and changes][rfc-rng-fixes] \\ Fixes and improvements to the random number generation subsystems (Created 2016-06-14)
  * [Add HTTP/2 Server Push support to ext/curl][rfc-curl-http2-push] (Created 2015/10/01)
  * [TimeZone::getWindowsID][rfc-intl-timezone-get-windows-id] (Created (2016/03/15)
  * [Multi catch][rfc-multiple-catch] \\ Catching multiple exception types in a single catch statement (Created 2016/03/06)
  * [Forbid dynamic calls to scope introspection functions][rfc-forbid-dynamic-scope-introspection] (Created 2016-05-01)
  * [Add curl_multi_errno(), curl_share_errno() and curl_share_strerror()][rfc-new-curl-error-functions] (Created: 2016-04-29)
  * [Throw Error in Extensions][rfc-throw-error-in-extensions] \\ Convert E_ERROR and E_RECOVERABLE_ERROR to throw Error in extensions (Created 2016-06-14)
  * [More precise float value handling][rfc-precise-float-value] \\ This RFC proposes more precise float value handling.
  * [Additional Context in pcntl_signal Handler][rfc-additional-context-in-pcntl-signal-handler] \\ Adds a second array argument to ''pcntl_signal'' handler (Created 2016-06-14)
  * [Add session_create_id()][rfc-session-create-id] \\ Add session_create_id() function (Created 2016-04-07)
  * [Add session_gc()][rfc-session-gc] \\ Add session_gc() function (Created 2016-04-06)


### PHP 7.0

  * [Random Functions throwing Exceptions][rfc-random-function-exceptions] \\ This RFC proposes that the random_* functions should throw exceptions on failure.
  * [Throwable Interface][rfc-throwable-interface] \\ Proposes a modification to the exception hierarchy for PHP 7, introducing a Throwable interface and Error class.
  * [Context Sensitive Lexer][rfc-context-sensitive-lexer]\\ Proposal to have a context sensitive lexer for PHP with support for semi-reserved words (Created 2015-02-15)
  * [Add preg_replace_callback_array function][rfc-preg-replace-callback-array]\\ A RFC proposing each pattern can easily have a specific callback.
  * [Reliable User-land CSPRNG][rfc-easy-userland-csprng]\\ A proposal to add a reliable CSPRNG (Created 2015-02-20)
  * [Anonymous Class Support][rfc-anonymous-classes]\\ This RFC proposes support for anonymous classes.
  * [Generator Delegation][rfc-generator-delegation] \\ This RFC proposes new syntax to delegate generator function operations to sub-iterators/generators (Created 2015-03-01)
  * [Reserve More Type Names in PHP 7][rfc-reserve-more-types-in-php-7] \\ Reserves ''int'', ''float'', ''string'', ''bool'', ''true'', ''false'' and ''null'' in class names or namespaces. (Created 2015-02-18)
  * [Constructor behaviour of internal classes][rfc-internal-constructor-behaviour]\\ Cleanup undesirable behaviour of constructors internal classes. (Created 2015-03-01)
  * [Reclassify E_STRICT notices][rfc-reclassify-e-strict]\\ This RFC proposes to reclassify our few existing E_STRICT notices to different categories. (Created 2015-02-22)
  * [Remove PHP 4 Constructors][rfc-remove-php4-constructors]\\ Stop recognizing methods with the same name as the defining class as constructors. (Created 2014-11-17; Voting closed 2015-03-10)
  * [Remove the date.timezone warning][rfc-date-timezone-warning-removal] \\ (Created 2015-01-27)
  * [Combined Comparison (Spaceship) Operator][rfc-combined-comparison-operator] \\ Proposes a new comparison operator, ''%%<=>%%'' (Created 2014-02-12, revived 2015-01-19)
  * [Fix "foreach" behavior][rfc-php7-foreach] \\ The RFC defines foreach statement behavior for the cases where is wasn't defined before and implementation provided inconsistent results. (Created 2015-01-29)
  * [ Removal of dead SAPIs and extensions][rfc-removal-of-dead-sapis-and-exts]\\ Consideration about removing the unsupported SAPIs and extensions with unsupported dependencies.
  * [Remove deprecated functionality in PHP 7][rfc-remove-deprecated-functionality-in-php7]\\ Proposes to remove functionality that has been deprecated in the PHP 5.x cycle in PHP 7. (Created 2014-09-11)
  * [Jsond][rfc-jsond] \\ Whether jsond should replace the current json extension. (Created 2015-01-11)
  * [Preserve Fractional Part in JSON encode][rfc-json-preserve-fractional-part] \\ Adds a new option for JSON encode to preserve fractional part on float numbers.
  * [Return Type Declarations][rfc-return-types]\\ Adds return types to functions, methods and closures. (Created 2014-03-20)
  * [Fast Parameter Parsing API][rfc-fast-zpp]\\ Fast API in addition to zend_parse_parameters(). (Created 2014-05-23)
  * [Unicode Codepoint Escape Syntax][rfc-unicode-escape]\\ Adds an escape sequence syntax for Unicode codepoints to string literals. (Created 2014-11-24)
  * [Native TLS][rfc-native-tls]\\ Native TLS for internal globals in TS mode
  * [Null Coalesce Operator][rfc-isset-ternary]\\ Adds the coalesce operator, ''??''
  * [Integer Semantics][rfc-integer-semantics]\\ Improves cross-platform consistency in PHP for some operations dealing with integers
  * [ZPP Failure on Overflow][rfc-zpp-fail-on-overflow]\\ Make ''zend_parse_parameters'' fail if a float value out of bounds, or NaN, is passed where an integer is expected. (Created 2014-09-22)
  * [Move the phpng branch into master][rfc-phpng]\\ Embrace the phpng codebase as the basis for the future major version of PHP. (Created 2014-07-20)
  * [Abstract Syntax Tree][rfc-abstract-syntax-tree]\\ Proposes the introduction of an Abstract Syntax Tree (AST) as an intermediary structure in our compilation process.
  * [Uniform Variable Syntax][rfc-uniform-variable-syntax]\\ Introduces an internally consistent and complete variable syntax.
  * [64 bit platform improvements for string length and integer][rfc-size-t-and-int64-next]\\ Integer and String modifications for full 64 bit support
  * [Closure::call][rfc-closure-apply]\\ Proposes a new method on the ''Closure'' class to allow calling bound to an object without pre-binding
  * [Fix list() behavior inconsistency][rfc-fix-list-behavior-inconsistency]\\ Enable or disable string handling in list() operator
  * [Remove alternative PHP tags][rfc-remove-alternative-php-tags]\\ Removes ASP and script tags
  * [[rfc:switch.default.multiple]]\\ Disallow multiple defaults in switch statements
  * [Catchable "call to a member function of a non-object"][rfc-catchable-call-to-member-of-non-object]\\ Turns this fatal error into E_RECOVERABLE (Created 2014-04-26)
  * [Filtered unserialize()][rfc-secure-unserialize]\\ Add option to ignore all or some objects to unserialize() (Created 2013/03/30)
  * [ICU IntlChar class][rfc-intl-char]\\ Adds an IntlChar class an intl_char_*() functions to the Intl extension.
  * [Introduce session_start() INI options as array][rfc-session-lock-ini]\\ Introduce session_start() options
  * [Remove hex support in numeric strings][rfc-remove-hex-support-in-numeric-strings] \\ Removes support for hexadecimal numbers in numeric string conversions. (Created 2014-08-19)
  * [Expectations][rfc-expectations]\\ This RFC proposes adding BC zero-cost assertions. (Created 2013-11-01)
  * [Group Use Declarations][rfc-group-use-declarations] \\ The RFC adds improvements to current PHP namespace implementation by introducing group use declarations. (Created 2015-01-28)
  * [Exceptions in the engine][rfc-engine-exceptions-for-php7]\\ This RFC proposes to allow the use of exceptions in the engine. (Created 2014-09-30)
  * [Generator Return Expressions][rfc-generator-return-expressions] \\ This RFC proposes the ability to specify and access return values from Generator functions
  * [Scalar Type Hints v0.5][rfc-scalar-type-hints-v5] \\ This RFC proposes a mixed-mode scalar type system
  * [Continue output buffering][rfc-continue-ob] \\ Let the output buffer stack be usable despite an aborted connection
  * [intdiv()][rfc-intdiv]\\ This RFC proposes adding an intdiv() function for integer division. (Created 2014-07-15)
  * [Fix handling of custom session handler return values][rfc-session-user-return-value]\\ Make false actually mean failure, not success.
  * [Turn gc_collect_cycles into function pointer][rfc-gc-fn-pointer] \\ Proposes to turn gc_collect_cycles into function pointer for extensions to hook into. (Created 2012-12-11)

### PHP 5.6

  * [__debugInfo() magic method][rfc-debug-info]\\ Support get_debug_info hook for userspace classes
  * [Exponential operator][rfc-pow-operator]\\ Exponential operator
  * [Importing namespaced functions][rfc-use-function]\\ Proposes to allow importing namespaced functions through a new `use function` sequence.
  * [Constant Scalar Expressions (with constants)][rfc-const-scalar-exprs]\\ This RFC proposes adding support for Constant Scalar Expressions with support for constants being operands.
  * [Remove calls from incompatible context][rfc-incompat-ctx]\\ Calls from incompatible context deprecated in 5.6 (will be removed in next version).
  * [Dedicated syntax for variadic functions][rfc-variadics]\\ This RFC introduces a dedicated syntax for variadic functions.
  * [Argument unpacking][rfc-argument-unpacking]\\ This RFC proposes a syntax for argument unpacking.
  * [Internal operator overloading and GMP improvements][rfc-operator-overloading-gmp]\\ Add support for operator overloading in internal classes and improve GMP using it
  * [phpdbg][rfc-phpdbg]\\ Distribute phpdbg with PHP, a PHP debugger
  * [Slim POST data][rfc-slim-post-data]\\ Use a temp PHP stream for HTTP payload.
  * [Crypt() function salt][rfc-crypt-function-salt]\\ This RFC proposes changing crypt() function's salt parameter treatment.
  * [Apparmor change_hat functionality for php-fpm][rfc-fpm-change-hat]\\ Proposes to add the possibility to change to a different hat under the apparmor LSM
  * [TLS Peer Verification][rfc-tls-peer-verification]\\ Enable peer verification by default for encrypted client streams.
  * [Improved TLS Defaults][rfc-improved-tls-defaults]\\ Implement more secure defaults for encrypted stream transfers
  * [Default character encoding][rfc-default-encoding]\\ Default character encoding handling in PHP.
  * [64 bit format codes for pack() and unpack()][rfc-pack-unpack-64bit-formats]\\ Adds format codes for converting 64 bit integers to and from binary strings.
  * [Timing attack safe string comparison function][rfc-timing-attack]\\ New function to perform time-constant string comparison (Created 2013/12/22)

### PHP 5.5

  * [Generators][rfc-generators]\\ This RFC proposes adding generators as a simple and boilerplate-free way of defining iterators.
  * [support finally keyword][rfc-finally]\\ Add try catch finally supporting
  * [Resolve class names to scalars via class keyword][rfc-class-name-scalars]\\ A proposal to use ::class after type names to resolve FQ class names as scalar
  * [foreach_variable supporting T_LIST][rfc-foreachlist]\\ This extends PHP's language parser to support T_LIST in foreach_variable
  * [Const array/string dereference][rfc-constdereference] \\ A little improvement to make things consistent
  * [Allow arbitrary expression arguments to empty() and isset()][rfc-empty-isset-exprs]\\ Proposes to allow ''empty(getArray())'' etc.
  * [Integrating Optimizer+ into the PHP distribution][rfc-optimizerplus]\\ This RFC proposes to integrate the Zend Optimizer+ opcode cache into the PHP distribution
  * [Adding hash_pbkdf2 function][rfc-hash-pbkdf2]\\ This RFC proposes adding a hash_pbkdf2 function to the hash package
  * [Add Simplified Password Hashing][rfc-password-hash]\\ This RFC proposes adding 3 new functions to the core to expose a much simplified password hashing API.
  * [Remove preg_replace /e modifier][rfc-remove-preg-replace-eval-modifier]\\ This RFC aims at deprecating and subsequently removing the /e modifier (PREG_REPLACE_EVAL) that preg_replace provides.
  * [Add UConverter][rfc-uconverter]\\ A proposal to add ICU::UConverter functionality to ext/intl
  * [ext/mysql deprecation][rfc-mysql-deprecation]\\ Formally deprecating ext/mysql in PHP.
  * [Cookie Max-Age attribute][rfc-cookie-max-age]\\ Cookie Max-Age attribute
  * [Fix cURL file uploading API][rfc-curl-file-upload]\\ Fix insecure cURL file uploading API
  * [Add recvmsg() and sendmsg() to ext/sockets][rfc-sendrecvmsg]\\ Wrap sendmsg() and recvmsg(), with support for a limited number of message types
  * [PHP CLI changing process title support][rfc-cli-process-title]\\ Setting PHP CLI process titles for visibility in 'top' or 'ps'
  * [Allow non-scalar keys in foreach][rfc-foreach-non-scalar-keys]\\ This RFC proposes to remove the type restrictions on foreach iteration
  * [Add array_column() function][rfc-array-column]\\ This RFC proposes a new array function that returns the values of the specified column from a multi-dimensional array.
  * [Removal of curl-wrappers][rfc-curl-wrappers-removal-rfc]\\ This RFC is about removing the curl stream wrappers of the PHP as of 5.5 and to move it on PECL for any eventual improvements.
  * [Strict Sessions][rfc-strict-sessions]\\ This RFC proposes an additional security measure for preventing session fixation.

### PHP 5.4

**Nota:** Muitas RFCs nesta lista foram [votadas em massa][todo-php54-vote].

  * [Instantiating a class and calling methods/accessing properties on same command][rfc-instance-method-call]\\ A proposal to add support to instantiating a class and calling its methods or accessing its properties on same command.
  * [Traits][rfc-horizontalreuse]\\ Traits is a mechanism for code reuse in single inheritance languages such as PHP. A Trait is intended to reduce some limitations of single inheritance by enabling a developer to reuse sets of methods freely in several independent classes living in different class hierarchies. This RFC proposes a basic version of Traits.
  * [Closures: Object Extension][rfc-closures-object-extension]\\ How to extend closures to work with $this and objects.
  * [Short syntax for arrays][rfc-shortsyntaxforarrays]\\ This RFC will discuss an language enhancement for simple and easy array definition.
  * [Function array dereferencing][rfc-functionarraydereferencing]\\ You know, like foo()['bar']
  * [Short tags in templates][rfc-shortags]\\ This RFC discusses ways to enable short tags template syntax in a way that would be easy for users and compatible with XML users' requirements.
  * [Indirect method call by array variable][rfc-indirect-method-call-by-array-var]\\ $arr = array('Class', 'method'); $arr();
  * [Supporting Binary Notation for Integers][rfc-binnotation4ints]\\ This extends PHP's syntax to support binary notation for integers just as it already does for decimal, octal, and hexadecimal representations.
  * [Built-in web server][rfc-builtinwebserver]\\ This RFC discusses the web server that is built into PHP itself, for development purpose.
  * [Removal of deprecated features][rfc-removal-of-deprecated-features]\\ RFC about removing legacy features in the next version of PHP
  * [Improve parser error messages][rfc-improved-parser-error-message]\\ Improve parser error message readability.
  * [Session upload progress][rfc-session-upload-progress]\\ Using sessions to provide upload progress feedback to users.
  * [Object oriented session handlers][rfc-session-oo]\\ A proposal to allow session_set_save_handler() to accept an object, and expose the original session handler.
  * [Allow Multiple Simultaneous Syslog Connections][rfc-allow-multiple-simultaneous-syslog-connections]\\ This RFC propose enhancement to syslog function in order to allow multiple simultaneous connections by using resources.
  * [Stream meta-data][rfc-streammetadata]\\ RFC defines handler for setting metadata on stream URL.
  * [Error message formatting for development][rfc-error-formatting-for-developers]\\ This RFC discusses error message formatting to aid developers.
  * [Zend Engine Performance Improvements][rfc-performanceimprovements]\\ Proposes Zend Engine changes which together make up to 20% performance improvement on synthetic benchmarks and some real-life applications
  * [Run Time Cache][rfc-runtimecache]\\ offers an implementation of run-time caching technique which may improve performance of repeatable code
  * [Zend Signal Handling][rfc-zendsignals]\\ Improve stability and speed when running under any forking SAPI by adding deferred signal handling to the Zend Engine.
  * [DTrace Probes for PHP][rfc-dtrace]\\ Provide DTrace probes for PHP.
  * [New Output API][rfc-new-output-api]\\ An RFC about the New Output API
  * [Callable type hint][rfc-callable]\\ Callable type hint
  * [LDAP: Add ldap_modify_batch][rfc-ldap-modify-batch] \\ This RFC proposes adding a lower-level modification function to the LDAP extension.

### PHP 5.3

  * [Closures][rfc-closures]\\ This RFC proposes Closures and lambda functions for PHP.
  * [Namespace resolution order][rfc-namespaceresolution]
  * [RFC on what namespace separator to choose][rfc-namespaceseparator]
  * [HEREDOC with double quotes][rfc-heredoc-with-double-quotes]\\ This RFC is about allowing double quote syntax similar to single-quotes in NOWDOC as a HEREDOC syntax variant (in PHP 5.3)
  * [LSB parent::/self:: forwarding][rfc-lsb-parentself-forwarding]\\ Changes how parent:: and self:: work with LSB by making them forwarding.
  * [call_time_pass_by_reference][rfc-calltimebyref]\\ This RFC proposes that call_time_pass_by_reference be switched off by default in PHP 5.3.
  * [New error level E_USER_DEPRECATED][rfc-e-user-deprecated-warning] \\ This RFC proposes to introduce a new userspace error level similar to E_DEPRECATED for user level deprecation warnings
  * [Rounding in PHP][rfc-rounding]\\ Make round() produce predictable results on all platforms and fix some problems in the process.
  * [Alternative to include/require for autoloaders][rfc-autoload-include]\\ This RFC aims to offer an alternative solution to the well known fopen() “hack” used in autoloaders in order to verify the existence of files inside the include path
  * [FPM SAPI][rfc-fpm]\\ This RFC discusses FPM SAPI and its inclusion to the core PHP distribution.
  * [FPM INI syntax][rfc-fpm-ini-syntax]\\ This RDV discusses the replacement of FPM configuration file from XML to INI.
  * [New INI Files][rfc-newinis]\\ A proposal for two new INI files which will replace the current INI's packaged with PHP. One focused on production deployments and the other focused on development deployments.
  * [count_elements handler vs count()][rfc-array-count-handlers]\\ Internal change to allow some optimization and add consistency.

## Recusadas

  * [Support optional suffix parameter in tempnam][rfc-tempnam-suffix-v2] (Discussion started: 2023-08-08; Voting ends: 2023-09-10)
  * [Interface Default Methods][rfc-interface-default-methods] (Created 2022-06-27, Discussion started: 2023-06-14, Voting start: 2023-07-02)
  * [PHP Technical Committee][rfc-php-technical-committee] (Voting started: 2023-04-28)
  * [include cleanup][rfc-include-cleanup] (Created 2023-01-18)
  * [Asymmetric visibility][rfc-asymmetric-visibility] (Created 2022-08-05)
  * [Destructuring Coalesce][rfc-destructuring-coalesce] (Created 2022-10-16, Voting opened: 2022-11-07)
  * [New Curl URL API][rfc-curl-url-api] (Created 2022-06-21, Voting opened: 2022-07-04)
  * [json_encode indentation][rfc-json-encode-indentation] (Created 2021-06-03, Voting opened: 2022-07-04)
  * [Short Closures 2.0][rfc-auto-capture-closure] (Created 2021-03-22, Voting opened: 2022-07-01)
  * [Create a global login experience for PHP.net][rfc-global-login] (Created 2022-05-23)
  * [Stricter implicit boolean coercions][rfc-stricter-implicit-boolean-coercions] (Created 2022-05-16)
  * [Sealed Class][rfc-sealed-classes] ( Created 2021-04-24 )
  * [Move to RNG functions into ext/random][rfc-random-ext] (Created 2021-09-07)
  * [User-Defined Operator Overloads][rfc-user-defined-operator-overloads] (Created 2021-08-14)
  * [PHP RFC: Add array_group function][rfc-array-column-results-grouping] ( Created 2021-11-28 )
  * [Nullable intersection types][rfc-nullable-intersection-types] (Created 2021-07-22 )
  * [Is literal][rfc-is-literal] \\ Allow developers/frameworks to check if variable is safe (created by literals); ref SQL/Command/HTML Injection. (Created 2020-03-21)
  * [Pipe Operator V2][rfc-pipe-operator-v2] Syntax for creating native function pipelines (Created: 2020-04-20)
  * [Partial Function Application][rfc-partial-function-application] \\ Add syntax for partially applying functions
  * [ImmutableIterable (rewindable, iterable, memory-efficient, allows any key&repeating keys)][rfc-cachediterable] (Created 2021-02-06)
  * [Short functions][rfc-short-functions] (Created 2020-09-26)
  * [Allow static properties in enums][rfc-enum-allow-static-properties] (Created 2021-05-17)
  * [OPCache direct execution opcode file without php source code file][rfc-direct-execution-opcode] (Created 2020-11-13)
  * [Object scoped RNG Implementations][rfc-object-scope-prng] (Created 2020-12-20)
  * [PHP\iterable\any() and all() on iterables][rfc-any-all-on-iterable] (Created 2020-08-30)
  * [var_representation() : readable alternative to var_export()][rfc-readable-var-representation] (Created 2021-01-21)
  * [Dump results of expressions in `php -a`][rfc-readline-interactive-shell-result-function] (Created 2020-12-19)
  * [PHP Namespace Policy][rfc-php-namespace-policy] \\ Reserves the use of the \PHP and \Ext namespaces for zend and core extensions. (Created 2020-04-15)
  * [StackFrame class][rfc-stack-frame-class] \\ debug_backtrace alternative as an array of StackFrame objects (Created 2020-07-07)
  * [Make constructors and destructors return void][rfc-make-ctor-ret-void] (Created 2020-06-17)
  * [Rename T_PAAMAYIM_NEKUDOTAYIM to T_DOUBLE_COLON][rfc-rename-double-colon-token] (Created 2020-04-11)
  * [Opcache optimization without any caching][rfc-opcache-no-cache]\\ ini setting ''opcache.allow_cache=0'' for opcache optimization without any caching (Created 2020-05-16)
  * [PHP Namespace in core][rfc-php-namespace-in-core] \\ Allows the use of the \PHP namespace in core (Created 2020-03-25)
  * [Match expression][rfc-match-expression]\\ Introduce match expression to address shortcomings of switch (Created 2020-04-12)
  * [Type casting in array destructuring expressions][rfc-typecast-array-desctructuring] \\ Adds the possibility to cast values while using array or list destructuring expressions (Created 2020-03-25)
  * [Compact Object Property Assignment][rfc-compact-object-property-assignment] \\ Pseudo object literals (Created 2020-03-10)
  * [Userspace Operator overloading][rfc-userspace-operator-overloading]\\ Allow users to overload operators (+, -, etc.) in their own classes (Created 2020-02-01)
  * [Server-Side Request and Response Objects][rfc-request-response]\\ This RFC proposes request and response objects that are wrappers for existing global PHP variables and functions, with some limited additional convenience functionality. (Created: 2016-21-21, revised 2020-02-10)
  * [Write-Once Properties][rfc-write-once-properties] \\ Add support for a new property modifier that would allow properties to be initialized, but not modified afterwards. (Created: 2020-02-18)
  * [declare(function_and_const_lookup=global)][rfc-use-global-elements] \\ Support skipping checking for global functions/consts in the current namespace before the global namespace. (Discussion started: 2020-01-01)
  * [Deprecate Backtick Operator v2][rfc-deprecate-backtick-operator-v2] \\ (Created: 2019-10-04)
  * [Object initializer][rfc-object-initializer] \\ Add object initializer block to instantiate and initialize object in single expression (Created: 2019-09-03)
  * [PHP RFC: Deprecate short open tags, again][rfc-deprecate-php-short-tags-v2] \\ Deprecate PHP's short open tags once again (Created: 2019-07-23, Announced: 2019-07-23; Voting: 2019-08-06 until 2019-08-20;)
  * [Add str_starts_with(), str_ends_with() and related functions][rfc-add-str-begin-and-end-functions] \\ Add functions to check if a string starts with, or ends with, a given substring. (Created 2016-08-01)
  * [Making stdClass iterable][rfc-iterable-stdclass] \\ (Created: 2019-01-12; Voting began: 2019-02-04)
  * [iterable_to_array() and iterable_count()][rfc-iterable-to-array-and-iterable-count] \\ Add iterable_to_array() and iterable_count() functions (iterator_to_array() and iterator_count() siblings) that work with iterables (Created: 2018-06-20, Vote started: 2018-07-03)
  * [User-defined object comparison][rfc-object-comparison] \\ Object comparison using //%%__compareTo%%// and //%%__equals%%// (Created: 2018-06-26)
  * [Class Friendship][rfc-friend-classes] \\ A proposal to add class friendship (Created 2018-06-27)
  * [Implement SQLite "openBlob" in PDO][rfc-implement-sqlite-openblob-in-pdo] (Created: 2017-09-26)
  * [UUID][rfc-uuid] \\ Proposes to include a native immutable UUID value object (Created: 2017-05-25)
  * [Unary null coalescing operator][rfc-unary-null-coalescing-operator] \\ Proposes a unary form of the null coalescing operator. (Created: 2017-06-21)
  * [Doxygen][rfc-doxygen] \\ Start documenting the PHP C sources with Doxygen comments (Created: 2017-05-30)
  * [Binary String Deprecation][rfc-binary-string-deprecation] \\ Proposes the deprecation of the b prefix and binary cast (Created: 2016-12-11)
  * [Throwable code's type generalization][rfc-throwable-code-generalization] \\ Change Throwable::getCode() & co. so that they can be of any type (Created: 2016-12-18)
  * [User defined session serializer][rfc-user-defined-session-serializer] \\ Implement user defined session serializer interface (Created: 2016-11-17)
  * [Add PHP Engine Identifier Constant][rfc-php-engine-constant] (Created 2016/02/03)
  * [Add validation functions to filter module][rfc-add-validate-functions-to-filter] \\ Add functions suitable for input validations. (Created 2016-08-03)
  * [New operator for context-dependent escaping][rfc-escaping-operator] \\ New operator <?* ?> for HTML escaping and other contexts. (Created 2016-07-14)
  * [Enable session.use_strict_mode by default][rfc-session-use-strict-mode] \\ Enable session.use_strict_mode by default. (Created 2016-07-05)
  * ''[var_type()][rfc-var-type]'' \\ Successor for ''gettype()'' function (Created: 2016-06-25)
  * ''[var_info()][rfc-var-info]'' \\ Extended version of ''var_type()'' function (Created: 2016-06-26)
  * [[rfc:ReflectionTypeImprovements]] \\ Improve ReflectionType's support for nullable and named types.
  * [Typed Properties][rfc-typed-properties] \\ Allow class properties to be typed (Created 2016-03-16)
  * [Union Types][rfc-union-types]\\ A proposal to add union types (Discussion began 2016-04-13)
  * [Callable prototypes][rfc-callable-types] \\ Callable prototypes (Created 2015-08-27)
  * [Functional Interfaces][rfc-functional-interfaces] \\ Functional Interfaces (Created 2016-04-17)
  * [PHP Attributes][rfc-attributes] \\ Native support for annotation (Discussion began 2016-04-22)
  * [''var'' Deprecation][rfc-var-deprecation] \\ Deprecating ''var'' in favor of ''public'' (Created 2016-03-10)
  * [Introduce script only require/include ][rfc-script-only-include] \\ Introduce script only include/require to prevent script inclusion. (Created 2015-02-10)
  * [Precise Session Management][rfc-precise-session-management]\\ Make session management precise. (Created 2015/03/21 )
  * [Number Format Separator][rfc-number-format-separator] \\ Enable for numerical literals to be formatted for better readability (Created 2015-12-20)
  * [JSON numeric as string][rfc-json-numeric-as-string]\\ Proposes new options for dealing with the JSON number conversion problem by converting data to string.
  * [In Operator][rfc-in-operator] \\ This RFC proposes a new operator for contains checks.
  * [Coercive Scalar Type Hints][rfc-coercive-sth]\\ A proposal to add user-land coercive scalar type hints, and change internal function behavior to align with them (Created 2015-02-21)
  * [Make empty() a Variadic][rfc-variadic-empty]\\ A proposal to make empty() accept any number of arguments (Created 2015-02-20)
  * [Allow error_handler callback parameters to be passed by reference][rfc-error-handler-callback-parameters-passed-by-reference] \\ (Created 2015-01-26)
  * [pecl_http][rfc-pecl-http]\\ Whether to add pecl_http v2 to the core
  * [Skipping optional parameters][rfc-skipparams] \\ Skipping optional parameters in function calls (Created 2012-04-13)
  * [PHP 5.7][rfc-php57] \\ Proposes a final minor version of PHP 5, PHP 5.7, with no new features but added deprecation notices. (Created 2014-12-15)
  * [Using objects as keys][rfc-objkey]\\ Allows to use objects as keys for arrays. (Created 2014-10-26)
  * [Abstract final classes / Static classes][rfc-abstract-final-class]\\ Language enhancement to support "abstract final classes" or "static classes". (Created 2014-11-26)
  * [Access to aliases definition by reflection][rfc-aliases-by-reflection] \\ Extends reflection for a getDefinedAliases() methods. (Created 2014/10/09)
  * [Safe Casting Functions][rfc-safe-cast]\\ Adds a set of safe casting functions for scalar types (Created 2014-10-21)
  * [Loop + or control structure][rfc-loop-or]\\ Adds a default block to loops to be executed in the event that the loop is never entered.
  * [Bare Name Array Literal][rfc-bare-name-array-literal]\\ A shorter new syntax for array key-value pairs (Created 2014-06-01)
  * [Bare Name Array Dereference][rfc-bare-name-array-dereference]\\ A shorter new syntax for dereferencing arrays with string keys (Created 2014-06-01)
  * [Array Of][rfc-arrayof]\\ Proposed syntax for Type-Hinting against the contents or an array (Created 2014/01/15)
  * [Improve HTML escape][rfc-secure-html-escape]\\ This RFC proposes more secure HTML escape by escaping "/" (Vote period: 2014/02/16 - 2014/02/22) (Created 2014/02/02)
  * [Multibyte Char Handling][rfc-multibyte-char-handling]\\ This RFC proposes the way to handle multibyte chars. (Created 2014/01/16)
  * [Alternative mbstring implementation using ICU][rfc-altmbstring]\\ A proposal to completely rewrite mbstring extension with ICU. (Created 2011/04/06)
  * [64 bit platform improvements for string length and integer][rfc-size-t-and-int64]\\ Integer and String modifications for full 64 bit support
  * [Alphanumeric Decrement][rfc-alpanumeric-decrement]\\ This will add support for decrementing alphanumeric strings (“ab”, for example) to complement the existing incrementing behaviour. (Created 2013/12/16)
  * [Exceptions in the engine][rfc-engine-exceptions]\\ This RFC proposes to allow the use of exceptions in the engine. (Postponed to PHP 6.)
  * [Extended keyword support][rfc-keywords-as-identifiers]\\ This RFC proposes to widen keyword support.
  * [Class instances counter][rfc-instance-counter]\\ This RFC proposes a new function returning a list with class names and their instance counter.
  * [[rfc:trailing-comma-function-args]]\\ Allow a trailing comma in function calls, similar to array declarations
  * [Add an array_part() function][rfc-array-part]\\ Adds a function to extract multi-dimensional slices
  * [SplClassLoader][rfc-splclassloader]\\ Merge implementation of first proposal of PHP Standards Recommendation (PSR) into SPL core
  * [Annotations][rfc-annotations]\\ Class Metadata feature (aka Annotations) support in PHP
  * [ifsetor() Operator][rfc-ifsetor]\\ This RFC proposes an operator that efficiently implements (isset($foo) ? $foo : $bar) as ifsetor($foo, $bar)
  * [[http://marc.info/?l=php-internals&m=121397217528280&w=2|Method overloading]]
  * [Non-breakable Traits][rfc-nonbreakabletraits]\\ This RFC is a extension to the basic proposal. It includes the notion of trait-local methods and properties.
  * [Function getEntropy][rfc-functiongetentropy]\\ Feature request for a new userspace function providing a truly random value.
  * [Property Accessors Syntax][rfc-propertygetsetsyntax-v1-2]\\ RFC for the addition of C#-style get/set accessors to PHP
  * [Alternative typehinting syntax for accessors][rfc-propertygetsetsyntax-alternative-typehinting-syntax]\\ Proposes an improved typehinting syntax for the accessors proposal.
  * [Automatic Property Initialization][rfc-automatic-property-initialization]\\ This RFC proposes automatic assignments of constructor arguments to properties. (Created 2013/09/27)
  * [Default parent constructors][rfc-default-ctor] \\ The RFC proposes that the parent constructors, destructors and clone operations were always callable even if not defined in parent class. (Created 2014-11-05)

## Canceladas

  * [Access Scope from Magic Accessors][rfc-access-scope-from-magic-accessors] (Created: 2023-01-19)
  * [Clamp][rfc-clamp] \\ Add new function clamp, which clamps a value inside a bound. (Created: 2021-06-23)
  * [Code optimizations][rfc-code-optimizations] (Created 2023-03-01)
  * [Auto-implement Stringable for string backed enums][rfc-auto-implement-stringable-for-string-backed-enums] (Created 2022-06-21)
  * [Arbitrary string interpolation][rfc-arbitrary-string-interpolation] (Created 2022-03-17)
  * [NULL Coercion Consistency][rfc-null-coercion-consistency] ( Created 2022-04-05 )
  * [Add parse_query_string as an alternative to parse_str][rfc-parse-str-alternative] (Created 2021-06-23)
  * [instanceof improvements][rfc-instanceof-improvements] \\ Allow more ways to use ''instanceof'' (Created 2020-05-17)
  * [Increment/Decrement Fixes][rfc-increment-decrement-fixes] \\ Fix some inconsistent cases of ++ and -- behaviour (Created 2020-03-01)
  * [Unwrap reference after foreach][rfc-foreach-unwrap-ref] (Created: 2021-08-13)
  * [Consistent callables][rfc-consistent-callables]\\ Consistent Callables (Created 2015-09-28)
  * [Never for Parameter Types][rfc-never-for-parameter-types] (Created: 2021-08-14)
  * [Deprecate ticks][rfc-deprecate-ticks] (Created 2021-05-11)
  * [debug_backtrace_depth(int $limit=0): int][rfc-debug-backtrace-depth] (Created 2021-03-13)
  * [println(string $data=""): int][rfc-println] (Created 2021-03-13)
  * [Reserve keywords in PHP 8][rfc-reserve-keywords-in-php-8] (Created 2020-06-13)
  * [Locked Classes][rfc-locked-classes] \\ Allows classes to block dynamically adding and removing properties from their instances (Announced 2019-03-10)
  * [PHP RFC: Saner numeric strings][rfc-trailing-whitespace-numerics-trailing-whitespace-in-numeric-strings-proposes-to-permit-trailing-whitespace-in-numeric-strings-superseded-by-rfc-saner-numeric-strings])
  * [Switch Expression and Switch Statement Improvement][rfc-switch-expression-and-statement-improvement] \\ Extend switch statement and introduce switch expression (Created: 2019-09-26)
  * [Language Constructs Syntax Changes][rfc-language-constructs-syntax-changes] \\ Allow skip parentheses for declare and halt compiler (Created 2020-07-04)
  * [Strict operators directive][rfc-strict-operators] \\ Strict type-checking for operators (Created: 2019-05-25, Discussion started: 2019-06-25)
  * [Switch expression][rfc-switch-expression] (Created 2020-03-28)
  * [Allow function calls in constant expressions][rfc-calls-in-constant-expressions] \\ (Created 2020-02-20)
  * [Implement strrstr for consistency][rfc-implement-strrstr-for-consistency]\\ Add strrstr and strristr for consistency in standard library (Created: 2019-06-20; Discussion started: 2019-06-20; Withdrawn: 2019-07-03)
  * [PDO Float Type][rfc-pdo-float-type] \\ New parameter type to represent floating point values. (Created: 2017-04-05)
  * [array_change_keys()][rfc-array-change-keys] \\ Add method to simplify re-keying an array (Created 2016-05-29)
  * [Deprecate and remove continue targeting switch][rfc-continue-on-switch-deprecation] \\ Support for continue acting on switch is deprecated and scheduled for removal in the next major version.
  * [JSON failure warnings][rfc-json-encode-decode-errors] \\ Raise warnings for json_encode() and json_decode() issues (Created: 2017-07-28)
  * [Namespaces in Core][rfc-namespaces-in-core] \\ Proposal to allow namespaces in PHP core (Created: 2017-06-03)
  * [Deprecate class instance deserialization in WDDX][rfc-wddx-deprecate-class-instance-deserialization] \\ Proposal to deprecate the ability to deserialize class instances via ''wddx_deserialize()''.
  * [ArrayIterator improvements][rfc-arrayiterator-improvements] \\ Proposes adding ''ArrayIterator::seekKey()'' and ''ArrayIterator::prev()''  (Created: 2016-11-21)
  * [Use php_mt_rand() where php_rand() is used][rfc-use-php-mt-rand]\\ This RFC proposes replacing php_rand() function to php_mt_rand(). (Created 2014-07-17)
  * [Revisit trailing commas in function arguments][rfc-revisit-trailing-comma-function-args]\\ Revisit trailing commas in function arguments (Created 2015-10-07)
  * [Short Closures (''~>'' operator)][rfc-short-closures] \\ This RFC proposes an operator for shorter Closures.
  * [ ReflectionParameter::getClassName()][rfc-reflectionparameter-getclassname] \\ Add reflection method to access to a class name in a type hint (Created 2015-01-30)
  * [Big Integer Support][rfc-bigint]\\ Adds Big Integer support to PHP (Created 2014-06-20)
  * [Scalar Type Hints][rfc-scalar-type-hints] \\ Adds four type hints for scalar types. (Created 2014-12-14)
  * [Deprecate function that modify INI][rfc-deprecate-ini-functions]\\ There are number of functions that modify INI value. Let them deprecate and use ini_get()/ini_set(). (Other RFC is proposed)
  * [pecl_sync][rfc-sync]\\ Whether PHP should support locking mechanism on its core
  * [Function Referencing as Closures][rfc-function-referencing]\\ Proposes a new syntax to allow referencing functions and methods as closures
  * [Readonly Properties][rfc-readonly-properties]\\ Adds a ''readonly'' specifier to make properties writeable within a class, but only readable from outside (Created 2014-10-24)
  * [Strict Argument Count On Function Calls][rfc-strict-argcount] \\ This RFC proposes to sensibly add a strict argument count check for function calls on PHP7 (Created 2015-02-20)
  * [Add scalar type hinting with casts][rfc-scalar-type-hinting-with-cast]\\ This RFC proposes adding scalar type hinting with casting to provide more robust parameter hinting. (Re-opened 2014-07-13)
  * [Sessions: Improve original RFC about lazy_write]]\\ An attempt at redesigning the accepted solution from [[rfc:session-lock-ini][rfc-session-read-only-lazy-write].
  * [Make GMP number work like PHP number][rfc-gmp-number]\\ Make compatible PHP number
  * [Constant Scalar Expressions (re-opening)][rfc-const-scalar-expressions2]\\ This RFC proposes adding support for Constant Scalar Expressions.
  * [Function Autoloading][rfc-function-autoloading]\\ This RFC proposes to refactor the existing autoloading mechanism to support function and constant autoloading.
  * [Structural Type Hinting][rfc-protocol-type-hinting]\\ This RFC proposes a new type-hint format to allow run-time checking of Structural Types.
  * [Constant Scalar Expressions][rfc-const-scalar-expressions]\\ This RFC proposes adding support for Constant Scalar Expressions.
  * [Modify tempnam() to handle directories and auto-cleanup][rfc-request-tempnam]\\ Add TEMPNAM_DIR and TEMPNAM_REQUEST options to tempnam()
  * [Parameter Type Casting Hints][rfc-parameter-type-casting-hints]\\ This RFC proposes adding type casting hints to function declarations.
  * [Who can vote?][rfc-voting-who]\\ Define the participants of the voting process.
  * [Magic Quotes in PHP, the Finalé][rfc-magicquotes-finale]\\ A safe, orderly manner for getting rid of Magic Quotes.
  * [Return value type hint][rfc-returntypehint2]\\ Return type hinting
  * [Cast and Assign Magic Methods][rfc-object-cast-magic]\\ Feature request to expose object_cast, get and set to PHP land code via two new magic methods
  * [Add mysqlnd.localhost_override option][rfc-mysqlnd-localhost-override]\\ This RFC proposes to add mysqlnd.localhost_override to more easily override localhost when connecting to a MySQL database.
  * [Allow use T_AS in closure use statement][rfc-useas]\\ Allow user use a alias name for lexical variable of closure
  * [strn(case)cmp supporting a negative length as its third paramter][rfc-strncmpnegativelen]\\ This extends PHP's string function strn(case)cmp to support a negative length as parameter
  * [Nested Class Support][rfc-nested-classes]\\ This RFC proposes support for nested classes, following on from Anonymous Classes.
  * [ Extending the JsonSerializable interface][rfc-jsonserializable-] \\ This RFC aims to allow creation of an object through JSON (Created 2015-07-13)
  * [Improve array to string conversion][rfc-array-to-string] \\ Proposes alternative behaviors for array to string zval conversion. (Created 2015/01/10)
  * [IntlCharsetDetector][rfc-intl-charset-detector] \\ Wrap ICU's UCharsetDetector (Created: 2016-04-11)
  * [Kill proprietary CSV escaping mechanism][rfc-kill-csv-escaping] \\ (Created: 2018-09-27; Withdrawn: 2018-12-02)

## Inativas

Esta seção é para RFCs que estiveram em discussão, mas não houve nenhuma
atividade ou discussão sobre elas recentemente.
Pode ser porque foram adiadas, se tornaram obsoletas ou parecem ter sido
abandonadas, ou porque os autores precisam trabalhar mais nelas.
Se a sua RFC foi adicionada aqui e parece que ela ainda está ativa, mova-a de
volta para a seção apropriada.

  * [Short Match][rfc-short-match] (Created 2020-12-13)
  * [Conditional Return, Break, and Continue Statements][rfc-conditional-break-continue-return]\\ Conditional Return, Break, & Continues; aka "return early" (Created 2020-05-16)
  *  [Deprecate Inconsistent Cast Names][rfc-deprecate-inconsistent-cast-keywords] \\ Deprecate cast names that are not valid as type declarations
  * [Error backtraces][rfc-error-backtraces] \\ Add backtraces to error output (Created 2020-05-25)
  * [Namespace-scoped declares][rfc-namespace-scoped-declares] \\ Add ability to specify declare directives at the namespace level. (Created: 2016-09-20)
  * [Add PDO function: mysqlGetWarningCount][rfc-pdo-mysql-get-warning-count] (Created 2021-02-26)
  * [Session strict mode default ini settings][rfc-default-session-strict-mode] \\ More secure ini defaults for sessions (Created: 2018-02-13)
  * [Disallow multiple constructor calls][rfc-disallow-multiple-constructor-calls] \\ Raise an error on calling <nowiki>$obj->__construct</nowiki> (Created: 2017-01-17)
  * [Remove requirement for authority portion of user stream wrapper URIs][rfc-ommit-double-slash-in-user-stream-wrapper-uri] \\ Proposes additional flag allowing to use valid URI with StreamWrapper's (Created: 2017-01-23)
  * [Comparison Chains][rfc-chaining-comparison] \\ Implement arbitrary chaining of comparator operations
  * [Create URLParser and URLBuilder Classes][rfc-replace-parse-url] \\ Proposed improvement beyond what parse_url() allows Created: 2016-10-04)
  * [Comparator interface][rfc-comparator-interface] \\ Proposes introduction of Comparator interface (Created: 2016-09-27)
  * [Automatic CSRF protection][rfc-automatic-csrf-protection] \\ Extend session module to provide automatic CSRF protection (Created 2016-05-10)
  * [Extending Exception backtraces to provide 'object'][rfc-exception-bt-provide-object] \\ Extending Exception backtraces to provide 'object' (Created 11/04-2016)
  * [Add foreach iteration of keys without values][rfc-foreach-void] \\ Add new syntax to enable foreach iteration without retrieving values (Created 2016-01-09)
  * [Type Affinity][rfc-introduce-type-affinity] \\ This RFC proposes type affinity for inputs
  * [Parser Extension API][rfc-parser-extension-api] \\ This RFC proposes a userland API to fetch an AST for code and to provide parser extensions (Created 2015/02/17)
  * [Support linking in stream wrappers][rfc-linking-in-stream-wrappers]\\ Add support for links in stream wrappers by adding appropriate hooks
  * [Normalize string bitwise shifts][rfc-string-bitwise-shifts]\\ Bitwise shifts to operate on string bytes instead of casting to integer.
  * [Consistent names for legacy functions/classes][rfc-consistent-names]\\ This RFC proposes to use alias to provide both legacy and consistent names.
  * [Inconsistent behaviors][rfc-inconsistent-behaviors]\\ This RFC is to discuss/document inconsistent behaviors.
  * [Platform and extension-independent API to the system CSPRNG][rfc-csrandombytes]\\ Request for Comments: Platform and extension-independent API to the system CSPRNG.
  * [Loop+Else control structure][rfc-loop-else] \\ This RFC proposes an optional “else” clause that can be used after while, for, and foreach loops.
  * [Make the PHP core case-sensitive][rfc-case-sensitivity]
  * [Restrict parameter parsing rules][rfc-zpp-conversion-rules] \\ Restrict rules to accept and implicitely convert internal function input arguments.
  * [Sourcemaps][rfc-sourcemaps] \\ Add support for Source Maps Revision 3
  * [Static class constructor][rfc-static-class-constructor] \\ Introduce a class constructor to initialize class state
  * [Typesafe Callable][rfc-typesafe-callable] \\ Allow typesafe callables (Created 2016-04-04)
  * [Add cyclic string replace to str_[i]replace() functions][rfc-cyclic-replace] (Created 2015/01/05)
  * [PHP 8 Assertions][rfc-php8-assertions] (Created 2019-10-28)
  * [Allow void variance][rfc-allow-void-variance] \\ Allow void variance. (Created: 2019-02-04)
  * [Namespace Visiblity for Class, Interface and Trait][rfc-namespace-visibility] \\ Add support for public, protected and private classes, interfaces and traits. (Created: 2018-07-18)
  * [Fiber][rfc-fiber] \\ Primitives for implementing light weight cooperative concurrency (Created: 2017-09-13 2018-06-11 to 2018-06-22)
  * [Deprecate PEAR/PECL & Replace with composer/pickle][rfc-deprecate-pear-include-composer] \\ Proposes replacing pear/pecl with composer/pickle (Created: 2016-09-01)
  * [Callable constructors][rfc-callableconstructors] \\ Allow constructors to be called as a callable (Created 2015-02-25)
  * [Anonymous Class Lexical Scope][rfc-lexical-anon] \\ Anonymous Class Lexical Scope (Created 2016-04-19)
  * [Intersection Types][rfc-intersection-types] (Discussion began 2016-04-28)
  * [Exception on constant redefintion][rfc-constant-redefinition] \\ Throw Exception on Attempt of Constant Redefinition (Created 2016-06-10)
  * [Retry keyword][rfc-retry-keyword] \\ Proposes the implementation of the Retry keyword in Exceptions context. (Created: 2017-06-19)
  * [Enable strict_types checking for curl_setopt()][rfc-curl-setopt-strict-types] \\ Introduce strict type enforcement inside curl_setopt() when declare(strict_types=1) is being used. (Created: 2017-04-21)
  * [Deprecate PDO::PARAM_NULL][rfc-deprecate-pdo-null] (Created 2017-05-15)
  * [Deprecate uniqid()][rfc-deprecate-uniqid] \\ Proposes the deprecation of ''uniqid()'' (Created: 2017-05-24)
  * [Immutable classes and properties][rfc-immutability] \\ Proposes introduction of immutable classes and properties (Created: 2016-08-12, Reopened 2018-02-20)
  * [Deprecate backtick operator][rfc-deprecate-backtick-operator] (Created: 2018-02-11)
  * [Deprecation of fallback to root scope][rfc-fallback-to-root-scope-deprecation] \\ Deprecation of fallback to root scope (Created: 2018-02-03)
  * [Scalar Pseudo-type][rfc-scalar-pseudo-type] \\ Proposal to add ''scalar'' pseudo-type for parameter and return types (Created: 2017-12-24)
  * [Explicit call-site pass-by-reference][rfc-explicit-send-by-ref]\\ Allow explicitly annotating by-reference argument passing at the call-site. (Created: 2017-12-02)
  * [Operator functions][rfc-operator-functions] \\ Add counterpart functions for PHP's basic operators (Published: 2017-09-08)
  * [Traits with interfaces][rfc--traits-with-interfaces] \\ Allow traits to explicitly implement interfaces (Created 2016-02-17)
  * [Adopt Code of Conduct][rfc--adopt-code-of-conduct] \\ This RFC proposes that the PHP project should adopt a formal code of conduct for its members. (Re-created 2016-01-21)
  * [Normalize token_get_all() output][rfc--token-get-always-tokens] \\ Allows specifying flag to normalize output of token_get_all()
  * [On-demand Name Mangling][rfc-on-demand-name-mangling] \\ Replaces automatic super-global name mangling with an on-demand approach for those apps requiring it. (Updated 2016-01-08)
  * [index) functions][rfc-array-key-first-last-index-add-array-key-first-last] \\ Add functions to get the first/last/indexed array key and value. (Created 2016-01-01)
  * [Improve predictable PRNG random][rfc-improve-predictable-prng-random] \\ Fix predictable PRNG problems. (Created: 2017-02-01)
  * [SoapClient getLocation][rfc-soap-get-location] \\ Add getLocation method to SoapClient (Created: 2016-12-06)
  * [Distrust SHA-1 Certificates][rfc-distrust-sha1-certificates] \\ Distrust SHA-1 starting in PHP 7.2 (Created: 2016-11-25)
  * [Secure serialization by authentication code][rfc-secure-serialization] \\ Add authentication code protection to serialization.
  * [Default Value in List Assignment Syntax][rfc-list-default-value] \\ Allow set default values when using list assignment
  * [Automatic SQL injection protection][rfc-sql-injection-protection] \\ This RFC enables automatic detection of SQL queries that are issued with a non-constant query parameter-string, with configurable evasive action on detection (i.e. ignore/log/throw).
  * [Introduce consistent function names][rfc-consistent-function-names] \\ This RFC proposes to have consistent function names that accord CORDING_STANDARDS.
  * [Introduce Design by Contract][rfc-introduce-design-by-contract]\\ This RFC is vote only RFC for 2 Design by Contract introduction proposals.
  * [Native Design by Contract support as annotation][rfc-dbc] \\ This RFC proposes native Design by Contract support to PHP (Created 2015/02/04)
  * [Native Design by Contract support as definition][rfc-dbc2] \\ This RFC proposes native Design by Contract support to PHP (Created 2015/02/10)
  * [Precise URL include control][rfc-allow-url-include]\\ This RFC proposes precise URL include control.
  * [Comparable][rfc-comparable]\\ A proposal to add a Comparable interface for userspace object comparisons.
  * [ Deprecate INI set/get aliases][rfc-deprecate-ini-set-get-aliases] \\ This RFC proposes INI set/get alias function deprecation. (Created 2015-01-28)
  * [Additional splat operator usage][rfc-additional-splat-usage]\\ Allow splat operator to be used in array literals. (Created 2014-11-03)
  * [GitHub Pull Requests Triage Team][rfc-github-pr]\\ Define a process for triaging GitHub pull requests. (Created 2014-10-30)
  * [Change checkdnsrr() $type argument behavior][rfc-checkdnsrr-default-type]\\ This RFC proposes that the default behavior of the checkdnsrr() function be changed such that it no longer checks only for MX records by default. (Created 2014-09-19)
  * [Binary String Comparison][rfc-binary-string-comparison]\\ Non-strict binary string comparison
  * [password_hash function behavior][rfc-password-hash-spec]\\ Current password_hash()'s hash function has password length limitation. (Created 2014-07-23)
  * [ReflectionParameter Typehint accessors][rfc-reflectionparameter-typehint]\\ New API for accessing typehints on a reflection parameter.
  * [Secure Session Options][rfc-secure-session-options-by-default]\\ This RFC proposes secure options for session module as default (Vote period:  2014/02/14 - 2014/02/21) (Created: 2014/02/01)
  * [Unify crypto source INI setting][rfc-unified-crypto-source]\\ This RFC proposes unified crypto source settings. (Created 2014/02/13)
  * [Build OpenSSL module by default][rfc-build-openssl-by-default]\\ This RFC proposes building openssl module by default.
  * [gmp_number][rfc-gmp-floating-point-add-support-for-gmp-floating-point-numbers-separate-out-floating-point-change-from-rfc-gmp-number] (Created 2014/01/04)
  * [Add generic class and method support][rfc-generics] (Created 2015/04/28)
  * [Add resource typehint][rfc-resource-typehint] (Created 2015/11/11)
  * [Short Ternary Assignment Operator][rfc-short-ternary-equal-operator] \\ Allow shorthand for self assigning short ternary expressions (Created: 2016-03-10)
  * [Pipe Operator][rfc-pipe-operator] \\ Syntactic sugar for chaining expressions (Created: 2016-04-29)
  * [Simple Annotations][rfc-simple-annotations] (Created: 2016-05-13)
  * [Improve hash_hkdf() parameter order and handling][rfc-improve-hash-hkdf-parameter] \\ hash_hkdf() added to master(7.2) has non optimal parameter order and handling. (Created: 2017-02-05)
  * [Basic Scalar Types][rfc-basic-scalar-types]\\ A RFC proposing pure scalar types (Created 2015-03-11)
  * [PECL versioning][rfc-peclversioning]\\ This RFC, about tackling the versioning issues in PECL extensions, has been implemented across PECL for several months. But what should be done about extension versioning in the PHP core?
  * [Improve consistency of protected member lookups][rfc-protectedlookup]\\ This RFC proposes to eliminate an inconsistency in the way protected class members are resolved.
  * [Drop sql.safe_mode][rfc-drop-sql-safe-mode]\\ Dropping a php.ini setting affecting two extensions
  * [Get Random][rfc-get-random]\\ This RFC talks about how to get a (better) random string in PHP
  * [Error optimizations][rfc-error-optimizations]\\ A way to optimize the formatting of our errors
  * [Function autoloading through spl_autoload*][rfc-autofunc]\\ This RFC introduces a potential implementation for function autoloading which would be consistent with what we have for autoloading classes. (Created 2011/08/05)
  * [CLI options for strict and quiet modes][rfc-cli-strict]\\ This RFC proposes a ''-W'' option to turn on maximum error reporting, and a ''-Q'' option for no error reporting. (Created 2011/07/05)
  * [Add Logical Shift Operators][rfc-logicalshiftoperator]\\ Add logical shift operators for bitwise shifting of strings (Created 2011/07/18)
  * [Faster strtod algorithm][rfc-grisu3-strtod]\\ This RFC proposes to add the Grisu3 strtod algorithm as an optional feature to PHP. (Created 2011/07/15)
  * [Isset Set Operator][rfc-isset-set-operator]\\ This RFC proposes new operators for handling unset/falsey variables.
  * [Scalar Type Casting Magic Methods][rfc-object-cast-to-types]\\ This RFC proposes a set of new scalar type casting magic methods for classes.
  * [docBlock Parser][rfc-docblockparser]\\ Proposal to add docBlock parsing to the Reflection extension
  * [Annotations in doc block][rfc-annotations-in-docblock]\\ Class Metadata feature (aka Annotations) support in PHP through DocBlock
  * [Object and Array Literals][rfc-objectarrayliterals]\\ This RFC proposes first-class, inline object and array literals similar to JSON.
  * [Weak References][rfc-weakreferences]\\ This RFC proposes the introduction of Weak References in PHP via a new SPL class.
  * [PDO Version 1 Improvements][rfc-pdov1]\\ This RFC proposes a set of improvements to be made to PDO.
  * [Tainted variables][rfc-taint]\\ This RFC proposes an implementation of variable tainting in PHP.
  * [Static classes][rfc-static-classes]\\ This RFC proposes the introduction of static classes for PHP
  * [class casting to scalar][rfc-class-casting-to-scalar]\\ This RFC proposes a way to do like <nowiki>__</nowiki>toString(), for other scalar types
  * [Autodefinition][rfc-autodefine]\\ This RFC proposes the ability to define missing definitions (generalization of autoload).
  * [Line Markers in PHP][rfc-linecontrol]\\ This RFC proposes the introduction of line markers in PHP.
  * [Autoboxing][rfc-autoboxing]\\ Autoboxing feature in PHP
  * [Systemd socket activation][rfc-socketactivation]\\ Systemd socket activation support for PHP-FPM (Created 2012/10/18)
  * [Add a deprecated modifier for functions][rfc-deprecated-modifier]\\ Add a deprecated modifier for functions (Created 2012/12/25)
  * [Clarifying/Improving the prototype checks][rfc-prototype-checks]\\ This RFC discusses the current state of prototype checks, and gives some directions for discussion and improvement. (Created 2011/09/19)
  * [Introducing Jenkins][rfc-jenkins]\\ This RFC proposes using Jenkins as a Continuous Ingtegration environment for the php project. (Created 2011/11/01)
  * [Support for anonymous catch-statements][rfc-anonymous-catch]\\ This RFC proposes adding catch-statements without variables, and fully anonymous catches. (Created 2013/06/25)
  * [Errors as Exceptions][rfc-errors-as-exceptions]\\ This RFC discusses the conversion of errors to exceptions (Created 2011/04/06)
  * [Proposed modifications to traits][rfc-traitsmodifications]\\ This RFC proposes three modifications to traits: increasing separation and consistency of inheritance vs. trait composition, adding trait-local scope, and extending ''use'' syntax. (Created 2011/04/06)
  * [Add toString to DateTime][rfc-datetime-tostring]\\ A proposal to add toString to DateTime (Created 2012/09/01)
  * [Property get/set syntax][rfc-propertygetsetsyntax-as-implemented]\\ This RFC proposes to add a C# style property get/set syntax to PHP classes. (Created 2011-12-21 - document index)
  * [Make T_FUNCTION in method declarations optional.][rfc-optional-t-function]\\ A proposal for removing the requirement to use T_FUNCTION in method declarations. (Created 2011/04/06)
  * [Jsonable interface][rfc-jsonable]\\ Feature request to allow support json_(encode|decode) to handle Object instance conversions.
  * [Siberia][rfc-extensionsiberia]\\ This RFC proposes to create a cemetery for dead extensions (PECL or core).
  * [array_delete][rfc-array-delete]\\ This RFC proposes adding array_delete() as an intuitive API for array element deletion. (Created 2012/08/22)
  * [Enhanced Error Handling][rfc-enhanced-error-handling]\\ This offers a concept and implementation to let the user (php coder) choose between php_error, exception et al while retaining backwards compatibility (Created 2009/12/27)
  * [Parameter (and Return) value type hints/checks][rfc-typechecking]\\ Several RFC that propose to complete the actual parameter type hints/checks (and an implementation for return value type hints). (Created 2009/07/03)
  * [Better benchmarks for PHP][rfc-better-benchmarks]\\ A proposal for replacing current bench.php benchmarking script. (Created 2009/04/03)
  * [Remove reliance of Zend API][rfc-remove-zend-api]\\ A proposal to remove the use of the Zend API in PHP libraries. (Created 2009/03/29)
  * [PHP Native Interface][rfc-php-native-interface]\\ Provide complete alternative to writing libraries interfaces using the Zend API libraries. (Created 2009/04/05)
  * [Function call chaining][rfc-fcallfcall]\\ Function call chaining implementation. (Created 2010/01/30)
  * [Source files without opening tag][rfc-source-files-without-opening-tag]\\ This RFC proposes a way to support source code files without <?php at the top.
  * [New File Type for Pure-Code PHP Scripts][rfc-phpp]\\ This RFC proposes the creation of a new .phpp file type for scripts that contain only PHP code without a <?php or ?> tag.
  * [Named Parameters][rfc-namedparameters-named-parameters-obsolete-dummy-rfc-for-named-parameters-superseded-by-rfc-named-params].
  * [Lemon as a language parser][rfc-lemon]\\ This RFC discusses the switch from YACC/Bison to lemon for the main language parser
  * [Astract Syntax Tree RFC][rfc-ast-based-parsing-compilation-process-moving-to-an-ast-based-parsing-compilation-process-obsolete-proposal-for-ast-based-compilation-process-superseded-by-the-rfc-abstract-syntax-tree]. (Created 2012/09/04)
  * [Escaping RFC for PHP Core][rfc-escaper]\\ Implementing a core anti-XSS escaping class and possibly functions for the more procedurally inclined programmers. (Created 2012/09/18)
  * [Integrate voting polls in PHP.net][rfc-site-voting-poll]\\ This RFC talks about integration of voting polls into PHP.net (Created 2013/02/23)
  * [unset(): return bool if the variable has existed][rfc-unset-bool]\\ Add to unset a return value if the deletion was successful (Created 2013/03/06)
  * [Internal Serialize API][rfc-internal-serialize-api]\\ This RFC proposes API for internal generating of serialization. (Created 2013/07/27)
  * [Normalizing increment and decrement operators][rfc-normalize-inc-dec]\\ This RFC proposes to make ++ and -- operators to work more intuitively. (Created 2013-12-19)
  * [Make PHP open tag optional for better security][rfc-nophptags]\\ This RFC proposes option (php.ini and CLI opts) for removing PHP tags  (<?php and so forth) from PHP scripts.(Vote period: 2014/02/16 - 2014/02/22) (Created 2012/04/12)
  * [Module API introspection][rfc-moduleapi-inspection]\\ Developer/Operations command-line API for checking module versions (Created  2014/01/24)
  * [Improve uniqid() uniqueness.][rfc-uniqid] \\ Improve uniqid() uniqueness (Created: 2016-09-12)

## Obsoletas

  * [is_json function][rfc-is-json] ( Created 2022-08-14 )
  * [Allow null as standalone type][rfc-null-standalone-type] (Created 2021-10-02)
  * [Enumerated Types][rfc-enum]\\ A proposal to add enumerated types (Created 2015-04-08)
  * [Enumeration type (alternative proposal)][rfc-enum-v2] \\ Create enumeration type (Created 2020-05-16)
  * [Nullsafe calls][rfc-nullsafe-calls] \\ This RFC proposes a new operator for propagating forward failures in a computation composed of method calls without the need for lots of boilerplate. (Created 2014-12-09)
  * [https://wiki.php.net/rfc/mixed_type_v2][rfc-mixed-typehint-mixed-typehint-proposal-to-add-mixed-typehint-for-parameter-and-return-types-revived-2019-02-07-superseded-by-rfc-mixed-type-v2])
  * [Annotations 2.0][rfc-annotations-v2] \\ Annotations (Class Metadata) support in PHP (Created: 2019-02-05)
  * [Property Type-hints][rfc-property-type-hints] \\ Introduce optional static type-hints and type-checking for properties.
  * [PHP RFC: Deprecate short open tags, again][rfc-deprecate-php-short-tags-deprecate-php-s-short-open-tags-deprecate-php-s-short-open-tags-created-2019-03-20-announced-2019-03-25-voting-began-2019-04-10-accepted-2019-04-24-obsoleted-by-rfc-deprecate-php-short-tags-v2]: 2019-07-23)
  * [Deprecate MCRYPT_RAND][rfc-deprecate-mcrypt-rand] \\ This RFC proposes the deprecation of MCRYPT_RAND in favor of selecting cryptographically secure pseudo-random number generators.
  * [Zend Pause API][rfc-zend-vm-pause-api] \\ API to pause zend vm in extension (Created: 2017-11-01)
  * [Loosening heredoc/nowdoc scanner][rfc-heredoc-scanner-loosening]\\ More permissive scanner rules for heredoc/nowdoc (Created 2014-08-29)
  * [Arrow Functions][rfc-arrow-functions] \\ A short form of closures similar to ES6's arrow functions (Created: 2016-08-14; Discussion began 2017-01-30)
  * [Short Closures][rfc-short-closures] \\ Provide consistent syntax for creating closures from callable (Created: 2017-06-26)
  * [Native TLS in ZTS][rfc-tls]\\ Improving performance of ZTS builds by using native thread local storage. (Created 2008/08/24)
  * [Simplified Named Arguments][rfc-simplified-named-params] \\ Introduce syntax for named arguments

[rfc--adopt-code-of-conduct]: https://wiki.php.net/rfc/+adopt-code-of-conduct

[rfc--deprecate-mb-ereg-replace-eval-option]: https://wiki.php.net/rfc/+deprecate_mb_ereg_replace_eval_option

[rfc--flexible-heredoc-nowdoc-syntaxes]: https://wiki.php.net/rfc/+flexible_heredoc_nowdoc_syntaxes

[rfc--negative-string-offsets]: https://wiki.php.net/rfc/+negative-string-offsets

[rfc--openssl-aead]: https://wiki.php.net/rfc/+openssl_aead

[rfc--token-get-always-tokens]: https://wiki.php.net/rfc/+token-get-always-tokens

[rfc--traits-with-interfaces]: https://wiki.php.net/rfc/+traits-with-interfaces

[rfc-2d-matrix-operations]: https://wiki.php.net/rfc/2d_matrix_operations

[rfc-abolish-narrow-margins]: https://wiki.php.net/rfc/abolish-narrow-margins

[rfc-abolish-short-votes]: https://wiki.php.net/rfc/abolish-short-votes

[rfc-abstract-final-class]: https://wiki.php.net/rfc/abstract_final_class

[rfc-abstract-syntax-tree]: https://wiki.php.net/rfc/abstract_syntax_tree

[rfc-abstract-trait-method-validation]: https://wiki.php.net/rfc/abstract_trait_method_validation

[rfc-access-scope-from-magic-accessors]: https://wiki.php.net/rfc/access_scope_from_magic_accessors

[rfc-access-scope-from-magic-accessors]: https://wiki.php.net/rfc/access_scope_from_magic_accessors

[rfc-add-cms-support]: https://wiki.php.net/rfc/add-cms-support

[rfc-add-str-begin-and-end-functions]: https://wiki.php.net/rfc/add_str_begin_and_end_functions

[rfc-add-str-starts-with-and-ends-with-functions]: https://wiki.php.net/rfc/add_str_starts_with_and_ends_with_functions

[rfc-add-validate-functions-to-filter]: https://wiki.php.net/rfc/add_validate_functions_to_filter

[rfc-adding-bcround-bcfloor-bcceil-to-bcmath]: https://wiki.php.net/rfc/adding_bcround_bcfloor_bcceil_to_bcmath

[rfc-additional-context-in-pcntl-signal-handler]: https://wiki.php.net/rfc/additional-context-in-pcntl-signal-handler

[rfc-additional-splat-usage]: https://wiki.php.net/rfc/additional-splat-usage

[rfc-adts]: https://wiki.php.net/rfc/adts

[rfc-aliases-by-reflection]: https://wiki.php.net/rfc/aliases_by_reflection

[rfc-allow-abstract-function-override]: https://wiki.php.net/rfc/allow-abstract-function-override

[rfc-allow-casting-closures-into-single-method-interface-implementations]: https://wiki.php.net/rfc/allow_casting_closures_into_single-method_interface_implementations

[rfc-allow-closures-to-declare-interfaces-they-implement]: https://wiki.php.net/rfc/allow-closures-to-declare-interfaces-they-implement

[rfc-allow-multiple-simultaneous-syslog-connections]: https://wiki.php.net/rfc/allow_multiple_simultaneous_syslog_connections

[rfc-allow-url-include]: https://wiki.php.net/rfc/allow_url_include

[rfc-allow-void-variance]: https://wiki.php.net/rfc/allow-void-variance

[rfc-alpanumeric-decrement]: https://wiki.php.net/rfc/alpanumeric_decrement

[rfc-alternative-closure-use-syntax]: https://wiki.php.net/rfc/alternative-closure-use-syntax

[rfc-altmbstring]: https://wiki.php.net/rfc/altmbstring

[rfc-always-enable-json]: https://wiki.php.net/rfc/always_enable_json

[rfc-annotations-in-docblock]: https://wiki.php.net/rfc/annotations-in-docblock

[rfc-annotations-v2]: https://wiki.php.net/rfc/annotations_v2

[rfc-annotations]: https://wiki.php.net/rfc/annotations

[rfc-anonymous-catch]: https://wiki.php.net/rfc/anonymous_catch

[rfc-anonymous-classes]: https://wiki.php.net/rfc/anonymous_classes

[rfc-any-all-on-iterable]: https://wiki.php.net/rfc/any_all_on_iterable

[rfc-apxs-loadmodule]: https://wiki.php.net/rfc/apxs-loadmodule

[rfc-arbitrary-static-variable-initializers]: https://wiki.php.net/rfc/arbitrary_static_variable_initializers

[rfc-arbitrary-string-interpolation]: https://wiki.php.net/rfc/arbitrary_string_interpolation

[rfc-argon2-password-hash-enhancements]: https://wiki.php.net/rfc/argon2_password_hash_enhancements

[rfc-argon2-password-hash]: https://wiki.php.net/rfc/argon2_password_hash

[rfc-argument-unpacking]: https://wiki.php.net/rfc/argument_unpacking

[rfc-arithmetic-operator-type-checks]: https://wiki.php.net/rfc/arithmetic_operator_type_checks

[rfc-array-change-keys]: https://wiki.php.net/rfc/array_change_keys

[rfc-array-column-results-grouping]: https://wiki.php.net/rfc/array_column_results_grouping

[rfc-array-column]: https://wiki.php.net/rfc/array_column

[rfc-array-count-handlers]: https://wiki.php.net/rfc/array_count_handlers

[rfc-array-delete]: https://wiki.php.net/rfc/array_delete

[rfc-array-group]: https://wiki.php.net/rfc/array_group

[rfc-array-key-first-last-index-add-array-key-first-last]: https://wiki.php.net/rfc/array_key_first_last_index%7CAdd+array_key_%28first%7Clast

[rfc-array-key-first-last]: https://wiki.php.net/rfc/array_key_first_last

[rfc-array-part]: https://wiki.php.net/rfc/array_part

[rfc-array-to-string]: https://wiki.php.net/rfc/array-to-string

[rfc-array-unpacking-string-keys]: https://wiki.php.net/rfc/array_unpacking_string_keys

[rfc-arrayiterator-improvements]: https://wiki.php.net/rfc/arrayiterator-improvements

[rfc-arrayof]: https://wiki.php.net/rfc/arrayof

[rfc-arrow-functions-v2]: https://wiki.php.net/rfc/arrow_functions_v2

[rfc-arrow-functions]: https://wiki.php.net/rfc/arrow_functions

[rfc-assert-string-eval-cleanup]: https://wiki.php.net/rfc/assert-string-eval-cleanup

[rfc-ast-based-parsing-compilation-process-moving-to-an-ast-based-parsing-compilation-process-obsolete-proposal-for-ast-based-compilation-process-superseded-by-the-rfc-abstract-syntax-tree]: https://wiki.php.net/rfc/ast_based_parsing_compilation_process%7CMoving+to+an+AST-based+parsing%2Fcompilation+process+%28obsolete%29%5D%5D%5C%5C+Proposal+for+AST-based+compilation+process.+Superseded+by+the+%5B%5Brfc%3Aabstract_syntax_tree

[rfc-asymmetric-visibility]: https://wiki.php.net/rfc/asymmetric-visibility

[rfc-async-signals]: https://wiki.php.net/rfc/async_signals

[rfc-attribute-amendments]: https://wiki.php.net/rfc/attribute_amendments

[rfc-attributes-v2]: https://wiki.php.net/rfc/attributes_v2

[rfc-attributes]: https://wiki.php.net/rfc/attributes

[rfc-auto-capture-closure]: https://wiki.php.net/rfc/auto-capture-closure

[rfc-auto-implement-stringable-for-string-backed-enums]: https://wiki.php.net/rfc/auto-implement_stringable_for_string_backed_enums

[rfc-autoboxing]: https://wiki.php.net/rfc/autoboxing

[rfc-autodefine]: https://wiki.php.net/rfc/autodefine

[rfc-autofunc]: https://wiki.php.net/rfc/autofunc

[rfc-autoload-classmap]: https://wiki.php.net/rfc/autoload_classmap

[rfc-autoload-include]: https://wiki.php.net/rfc/autoload_include

[rfc-automatic-csrf-protection]: https://wiki.php.net/rfc/automatic_csrf_protection

[rfc-automatic-property-initialization]: https://wiki.php.net/rfc/automatic_property_initialization

[rfc-autovivification-false]: https://wiki.php.net/rfc/autovivification_false

[rfc-bare-name-array-dereference]: https://wiki.php.net/rfc/bare_name_array_dereference

[rfc-bare-name-array-literal]: https://wiki.php.net/rfc/bare_name_array_literal

[rfc-base-convert-improvements]: https://wiki.php.net/rfc/base_convert_improvements

[rfc-basic-scalar-types]: https://wiki.php.net/rfc/basic_scalar_types

[rfc-bcrypt-cost-2023]: https://wiki.php.net/rfc/bcrypt_cost_2023

[rfc-better-benchmarks]: https://wiki.php.net/rfc/better_benchmarks

[rfc-bigint]: https://wiki.php.net/rfc/bigint

[rfc-binary-string-comparison]: https://wiki.php.net/rfc/binary_string_comparison

[rfc-binary-string-deprecation]: https://wiki.php.net/rfc/binary_string_deprecation

[rfc-binnotation4ints]: https://wiki.php.net/rfc/binnotation4ints

[rfc-build-openssl-by-default]: https://wiki.php.net/rfc/build-openssl-by-default

[rfc-builtinwebserver]: https://wiki.php.net/rfc/builtinwebserver

[rfc-cachediterable]: https://wiki.php.net/rfc/cachediterable

[rfc-callable-types]: https://wiki.php.net/rfc/callable-types

[rfc-callable]: https://wiki.php.net/rfc/callable

[rfc-callableconstructors]: https://wiki.php.net/rfc/callableconstructors

[rfc-calls-in-constant-expressions]: https://wiki.php.net/rfc/calls_in_constant_expressions

[rfc-calltimebyref]: https://wiki.php.net/rfc/calltimebyref

[rfc-case-insensitive-constant-deprecation]: https://wiki.php.net/rfc/case_insensitive_constant_deprecation

[rfc-case-sensitivity]: https://wiki.php.net/rfc/case-sensitivity

[rfc-catchable-call-to-member-of-non-object]: https://wiki.php.net/rfc/catchable-call-to-member-of-non-object

[rfc-chaining-comparison]: https://wiki.php.net/rfc/chaining_comparison

[rfc-change-terminology-to-excludelist]: https://wiki.php.net/rfc/change-terminology-to-excludelist

[rfc-change-the-edge-case-of-round]: https://wiki.php.net/rfc/change_the_edge_case_of_round

[rfc-checkdnsrr-default-type]: https://wiki.php.net/rfc/checkdnsrr-default-type

[rfc-clamp]: https://wiki.php.net/rfc/clamp

[rfc-class-casting-to-scalar]: https://wiki.php.net/rfc/class_casting_to_scalar

[rfc-class-const-visibility]: https://wiki.php.net/rfc/class_const_visibility

[rfc-class-name-literal-on-object]: https://wiki.php.net/rfc/class_name_literal_on_object

[rfc-class-name-scalars]: https://wiki.php.net/rfc/class_name_scalars

[rfc-class-naming]: https://wiki.php.net/rfc/class-naming

[rfc-cli-process-title]: https://wiki.php.net/rfc/cli_process_title

[rfc-cli-strict]: https://wiki.php.net/rfc/cli-strict

[rfc-clone-with]: https://wiki.php.net/rfc/clone_with

[rfc-closure-apply]: https://wiki.php.net/rfc/closure_apply

[rfc-closure-self-reference]: https://wiki.php.net/rfc/closure_self_reference

[rfc-closurefromcallable]: https://wiki.php.net/rfc/closurefromcallable

[rfc-closures-object-extension]: https://wiki.php.net/rfc/closures%3Aobject-extension

[rfc-closures]: https://wiki.php.net/rfc/closures

[rfc-code-optimizations]: https://wiki.php.net/rfc/code_optimizations

[rfc-coercive-sth]: https://wiki.php.net/rfc/coercive_sth

[rfc-combined-comparison-operator]: https://wiki.php.net/rfc/combined-comparison-operator

[rfc-compact-object-property-assignment]: https://wiki.php.net/rfc/compact-object-property-assignment

[rfc-compact]: https://wiki.php.net/rfc/compact

[rfc-comparable]: https://wiki.php.net/rfc/comparable

[rfc-comparator-interface]: https://wiki.php.net/rfc/comparator_interface

[rfc-comprehensions]: https://wiki.php.net/rfc/comprehensions

[rfc-concatenation-precedence]: https://wiki.php.net/rfc/concatenation_precedence

[rfc-conditional-break-continue-return]: https://wiki.php.net/rfc/conditional_break_continue_return

[rfc-consistent-callables]: https://wiki.php.net/rfc/consistent_callables

[rfc-consistent-function-names]: https://wiki.php.net/rfc/consistent_function_names

[rfc-consistent-names]: https://wiki.php.net/rfc/consistent-names

[rfc-consistent-type-errors]: https://wiki.php.net/rfc/consistent_type_errors

[rfc-const-scalar-expressions2]: https://wiki.php.net/rfc/const_scalar_expressions2

[rfc-const-scalar-expressions]: https://wiki.php.net/rfc/const_scalar_expressions

[rfc-const-scalar-exprs]: https://wiki.php.net/rfc/const_scalar_exprs

[rfc-constant-redefinition]: https://wiki.php.net/rfc/constant_redefinition

[rfc-constants-in-traits]: https://wiki.php.net/rfc/constants_in_traits

[rfc-constdereference]: https://wiki.php.net/rfc/constdereference

[rfc-constructor-promotion]: https://wiki.php.net/rfc/constructor_promotion

[rfc-context-sensitive-lexer]: https://wiki.php.net/rfc/context_sensitive_lexer

[rfc-continue-ob]: https://wiki.php.net/rfc/continue_ob

[rfc-continue-on-switch-deprecation]: https://wiki.php.net/rfc/continue_on_switch_deprecation

[rfc-convert-numeric-keys-in-object-array-casts]: https://wiki.php.net/rfc/convert_numeric_keys_in_object_array_casts

[rfc-cookie-max-age]: https://wiki.php.net/rfc/cookie_max-age

[rfc-core-autoloading]: https://wiki.php.net/rfc/core-autoloading

[rfc-counting-non-countables]: https://wiki.php.net/rfc/counting_non_countables

[rfc-covariant-returns-and-contravariant-parameters]: https://wiki.php.net/rfc/covariant-returns-and-contravariant-parameters

[rfc-crypt-function-salt]: https://wiki.php.net/rfc/crypt_function_salt

[rfc-csrandombytes]: https://wiki.php.net/rfc/csrandombytes

[rfc-curl-file-upload]: https://wiki.php.net/rfc/curl-file-upload

[rfc-curl-http2-push]: https://wiki.php.net/rfc/curl_http2_push

[rfc-curl-setopt-strict-types]: https://wiki.php.net/rfc/curl_setopt_strict_types

[rfc-curl-url-api]: https://wiki.php.net/rfc/curl-url-api

[rfc-curl-user-agent]: https://wiki.php.net/rfc/curl_user_agent

[rfc-curl-wrappers-removal-rfc]: https://wiki.php.net/rfc/curl-wrappers-removal-rfc

[rfc-custom-object-serialization]: https://wiki.php.net/rfc/custom_object_serialization

[rfc-cyclic-replace]: https://wiki.php.net/rfc/cyclic-replace

[rfc-date-timezone-warning-removal]: https://wiki.php.net/rfc/date.timezone_warning_removal

[rfc-datetime-and-daylight-saving-time]: https://wiki.php.net/rfc/datetime_and_daylight_saving_time

[rfc-datetime-exceptions]: https://wiki.php.net/rfc/datetime-exceptions

[rfc-datetime-tostring]: https://wiki.php.net/rfc/datetime_tostring

[rfc-dbc2]: https://wiki.php.net/rfc/DbC2

[rfc-dbc]: https://wiki.php.net/rfc/DbC

[rfc-debug-backtrace-depth]: https://wiki.php.net/rfc/debug_backtrace_depth

[rfc-debug-info]: https://wiki.php.net/rfc/debug-info

[rfc-debugging-pdo-prepared-statement-emulation-v2]: https://wiki.php.net/rfc/debugging_pdo_prepared_statement_emulation_v2

[rfc-debugging-pdo-prepared-statement-emulation]: https://wiki.php.net/rfc/debugging_pdo_prepared_statement_emulation

[rfc-declare-vars]: https://wiki.php.net/rfc/declare_vars

[rfc-default-ctor]: https://wiki.php.net/rfc/default_ctor

[rfc-default-encoding]: https://wiki.php.net/rfc/default_encoding

[rfc-default-session-strict-mode]: https://wiki.php.net/rfc/default-session-strict-mode

[rfc-deprecate-and-remove-ext-interbase]: https://wiki.php.net/rfc/deprecate-and-remove-ext-interbase

[rfc-deprecate-and-remove-ext-wddx]: https://wiki.php.net/rfc/deprecate-and-remove-ext-wddx

[rfc-deprecate-and-remove-intl-idna-variant-2003]: https://wiki.php.net/rfc/deprecate-and-remove-intl_idna_variant_2003

[rfc-deprecate-backtick-operator-v2]: https://wiki.php.net/rfc/deprecate-backtick-operator-v2

[rfc-deprecate-backtick-operator]: https://wiki.php.net/rfc/deprecate-backtick-operator

[rfc-deprecate-bareword-strings]: https://wiki.php.net/rfc/deprecate-bareword-strings

[rfc-deprecate-boolean-string-coercion]: https://wiki.php.net/rfc/deprecate-boolean-string-coercion

[rfc-deprecate-curly-braces-array-access]: https://wiki.php.net/rfc/deprecate_curly_braces_array_access

[rfc-deprecate-dollar-brace-string-interpolation]: https://wiki.php.net/rfc/deprecate_dollar_brace_string_interpolation

[rfc-deprecate-dynamic-properties]: https://wiki.php.net/rfc/deprecate_dynamic_properties

[rfc-deprecate-functions-with-overloaded-signatures]: https://wiki.php.net/rfc/deprecate_functions_with_overloaded_signatures

[rfc-deprecate-inconsistent-cast-keywords]: https://wiki.php.net/rfc/deprecate-inconsistent-cast-keywords

[rfc-deprecate-ini-functions]: https://wiki.php.net/rfc/deprecate-ini-functions

[rfc-deprecate-ini-set-get-aliases]: https://wiki.php.net/rfc/deprecate_ini_set_get_aliases

[rfc-deprecate-mcrypt-rand]: https://wiki.php.net/rfc/deprecate_mcrypt_rand

[rfc-deprecate-null-to-scalar-internal-arg]: https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg

[rfc-deprecate-partially-supported-callables]: https://wiki.php.net/rfc/deprecate_partially_supported_callables

[rfc-deprecate-pdo-null]: https://wiki.php.net/rfc/deprecate_pdo_null

[rfc-deprecate-pear-include-composer]: https://wiki.php.net/rfc/deprecate-pear-include-composer

[rfc-deprecate-php-short-tags-deprecate-php-s-short-open-tags-deprecate-php-s-short-open-tags-created-2019-03-20-announced-2019-03-25-voting-began-2019-04-10-accepted-2019-04-24-obsoleted-by-rfc-deprecate-php-short-tags-v2]: https://wiki.php.net/rfc/deprecate_php_short_tags%7CDeprecate+PHP%27s+Short+Open+Tags%5D%5D+%5C%5C+Deprecate+PHP%27s+short+open+tags+%28Created%3A+2019-03-20%3B+Announced%3A+2019-03-25%3B+Voting+began%3A+2019-04-10%3B+Accepted%3A+2019-04-24%3B+Obsoleted+by+%5B%5Brfc%3Adeprecate_php_short_tags_v2

[rfc-deprecate-php-short-tags-v2]: https://wiki.php.net/rfc/deprecate_php_short_tags_v2

[rfc-deprecate-png-jpeg-2wbmp]: https://wiki.php.net/rfc/deprecate-png-jpeg-2wbmp

[rfc-deprecate-ticks]: https://wiki.php.net/rfc/deprecate_ticks

[rfc-deprecate-uniqid]: https://wiki.php.net/rfc/deprecate-uniqid

[rfc-deprecated-attribute]: https://wiki.php.net/rfc/deprecated_attribute

[rfc-deprecated-modifier]: https://wiki.php.net/rfc/deprecated-modifier

[rfc-deprecations-php-7-2]: https://wiki.php.net/rfc/deprecations_php_7_2

[rfc-deprecations-php-7-3]: https://wiki.php.net/rfc/deprecations_php_7_3

[rfc-deprecations-php-7-4]: https://wiki.php.net/rfc/deprecations_php_7_4

[rfc-deprecations-php-8-1]: https://wiki.php.net/rfc/deprecations_php_8_1

[rfc-deprecations-php-8-3]: https://wiki.php.net/rfc/deprecations_php_8_3

[rfc-deprecations-php-8-4]: https://wiki.php.net/rfc/deprecations_php_8_4

[rfc-deque]: https://wiki.php.net/rfc/deque

[rfc-destructuring-coalesce]: https://wiki.php.net/rfc/destructuring_coalesce

[rfc-direct-execution-opcode]: https://wiki.php.net/rfc/direct-execution-opcode

[rfc-disallow-multiple-constructor-calls]: https://wiki.php.net/rfc/disallow-multiple-constructor-calls

[rfc-distrust-sha1-certificates]: https://wiki.php.net/rfc/distrust-sha1-certificates

[rfc-dnf-types]: https://wiki.php.net/rfc/dnf_types

[rfc-docblockparser]: https://wiki.php.net/rfc/docblockparser

[rfc-dom-living-standard-api]: https://wiki.php.net/rfc/dom_living_standard_api

[rfc-domdocument-html5-parser]: https://wiki.php.net/rfc/domdocument_html5_parser

[rfc-doxygen]: https://wiki.php.net/rfc/doxygen

[rfc-drop-sql-safe-mode]: https://wiki.php.net/rfc/drop_sql.safe_mode

[rfc-dtrace]: https://wiki.php.net/rfc/dtrace

[rfc-dvcs]: https://wiki.php.net/rfc/dvcs

[rfc-dynamic-class-constant-fetch]: https://wiki.php.net/rfc/dynamic_class_constant_fetch

[rfc-e-user-deprecated-warning]: https://wiki.php.net/rfc/e-user-deprecated-warning

[rfc-easy-userland-csprng]: https://wiki.php.net/rfc/easy_userland_csprng

[rfc-empty-isset-exprs]: https://wiki.php.net/rfc/empty_isset_exprs

[rfc-engine-exceptions-for-php7]: https://wiki.php.net/rfc/engine_exceptions_for_php7

[rfc-engine-exceptions]: https://wiki.php.net/rfc/engine_exceptions

[rfc-engine-warnings]: https://wiki.php.net/rfc/engine_warnings

[rfc-enhanced-error-handling]: https://wiki.php.net/rfc/enhanced_error_handling

[rfc-enum-allow-static-properties]: https://wiki.php.net/rfc/enum_allow_static_properties

[rfc-enum-v2]: https://wiki.php.net/rfc/enum+v2

[rfc-enum]: https://wiki.php.net/rfc/enum

[rfc-enumerations]: https://wiki.php.net/rfc/enumerations

[rfc-error-backtraces]: https://wiki.php.net/rfc/error+backtraces

[rfc-error-formatting-for-developers]: https://wiki.php.net/rfc/error-formatting-for-developers

[rfc-error-handler-callback-parameters-passed-by-reference]: https://wiki.php.net/rfc/error_handler_callback_parameters_passed_by_reference

[rfc-error-optimizations]: https://wiki.php.net/rfc/error-optimizations

[rfc-errors-as-exceptions]: https://wiki.php.net/rfc/errors_as_exceptions

[rfc-escaper]: https://wiki.php.net/rfc/escaper

[rfc-escaping-operator]: https://wiki.php.net/rfc/escaping_operator

[rfc-exception-bt-provide-object]: https://wiki.php.net/rfc/exception_bt_provide_object

[rfc-expectations]: https://wiki.php.net/rfc/expectations

[rfc-explicit-octal-notation]: https://wiki.php.net/rfc/explicit_octal_notation

[rfc-explicit-send-by-ref]: https://wiki.php.net/rfc/explicit_send_by_ref

[rfc-extended-string-types-for-pdo]: https://wiki.php.net/rfc/extended-string-types-for-pdo

[rfc-extensionsiberia]: https://wiki.php.net/rfc/extensionsiberia

[rfc-fallback-to-root-scope-deprecation]: https://wiki.php.net/rfc/fallback-to-root-scope-deprecation

[rfc-fast-zpp]: https://wiki.php.net/rfc/fast_zpp

[rfc-fcallfcall]: https://wiki.php.net/rfc/fcallfcall

[rfc-fetch-property-in-const-expressions]: https://wiki.php.net/rfc/fetch_property_in_const_expressions

[rfc-ffi]: https://wiki.php.net/rfc/ffi

[rfc-fiber]: https://wiki.php.net/rfc/fiber

[rfc-fibers]: https://wiki.php.net/rfc/fibers

[rfc-file-descriptor-function]: https://wiki.php.net/rfc/file-descriptor-function

[rfc-final-anonymous-classes]: https://wiki.php.net/rfc/final_anonymous_classes

[rfc-final-class-const]: https://wiki.php.net/rfc/final_class_const

[rfc-finally]: https://wiki.php.net/rfc/finally

[rfc-first-class-callable-syntax]: https://wiki.php.net/rfc/first_class_callable_syntax

[rfc-fix-list-behavior-inconsistency]: https://wiki.php.net/rfc/fix_list_behavior_inconsistency

[rfc-forbid-dynamic-scope-introspection]: https://wiki.php.net/rfc/forbid_dynamic_scope_introspection

[rfc-foreach-non-scalar-keys]: https://wiki.php.net/rfc/foreach-non-scalar-keys

[rfc-foreach-unwrap-ref]: https://wiki.php.net/rfc/foreach_unwrap_ref

[rfc-foreach-void]: https://wiki.php.net/rfc/foreach_void

[rfc-foreachlist]: https://wiki.php.net/rfc/foreachlist

[rfc-fpm-change-hat]: https://wiki.php.net/rfc/fpm_change_hat

[rfc-fpm-ini-syntax]: https://wiki.php.net/rfc/fpm%3Aini_syntax

[rfc-fpm]: https://wiki.php.net/rfc/fpm

[rfc-friend-classes]: https://wiki.php.net/rfc/friend-classes

[rfc-fsync-function]: https://wiki.php.net/rfc/fsync_function

[rfc-function-autoloading]: https://wiki.php.net/rfc/function_autoloading

[rfc-function-referencing]: https://wiki.php.net/rfc/function_referencing

[rfc-functional-interfaces]: https://wiki.php.net/rfc/functional-interfaces

[rfc-functionarraydereferencing]: https://wiki.php.net/rfc/functionarraydereferencing

[rfc-functiongetentropy]: https://wiki.php.net/rfc/functiongetentropy

[rfc-gc-fn-pointer]: https://wiki.php.net/rfc/gc_fn_pointer

[rfc-gd-image-export-import-pixels]: https://wiki.php.net/rfc/gd_image_export_import_pixels

[rfc-generator-delegation]: https://wiki.php.net/rfc/generator-delegation

[rfc-generator-return-expressions]: https://wiki.php.net/rfc/generator-return-expressions

[rfc-generators]: https://wiki.php.net/rfc/generators

[rfc-generics]: https://wiki.php.net/rfc/generics

[rfc-get-class-disallow-null-parameter]: https://wiki.php.net/rfc/get_class_disallow_null_parameter

[rfc-get-debug-type]: https://wiki.php.net/rfc/get_debug_type

[rfc-get-random]: https://wiki.php.net/rfc/get-random

[rfc-github-issues]: https://wiki.php.net/rfc/github_issues

[rfc-github-pr]: https://wiki.php.net/rfc/github-pr

[rfc-global-login]: https://wiki.php.net/rfc/global_login

[rfc-gmp-floating-point-add-support-for-gmp-floating-point-numbers-separate-out-floating-point-change-from-rfc-gmp-number]: https://wiki.php.net/rfc/gmp-floating-point%7CAdd+support+for+GMP+floating+point+numbers%5D%5D%5C%5C+Separate+out+floating+point+change+from+%5B%5Brfc%3Agmp_number

[rfc-gmp-number]: https://wiki.php.net/rfc/gmp_number

[rfc-grisu3-strtod]: https://wiki.php.net/rfc/grisu3-strtod

[rfc-group-use-declarations]: https://wiki.php.net/rfc/group_use_declarations

[rfc-hash-context-as-resource]: https://wiki.php.net/rfc/hash-context.as-resource

[rfc-hash-pbkdf2]: https://wiki.php.net/rfc/hash_pbkdf2

[rfc-heredoc-scanner-loosening]: https://wiki.php.net/rfc/heredoc-scanner-loosening

[rfc-heredoc-with-double-quotes]: https://wiki.php.net/rfc/heredoc-with-double-quotes

[rfc-horizontalreuse]: https://wiki.php.net/rfc/HorizontalReuse

[rfc-howto]: https://wiki.php.net/rfc/howto

[rfc-ifsetor]: https://wiki.php.net/rfc/ifsetor

[rfc-image2wbmp]: https://wiki.php.net/rfc/image2wbmp

[rfc-immutability]: https://wiki.php.net/rfc/immutability

[rfc-implement-sqlite-openblob-in-pdo]: https://wiki.php.net/rfc/implement_sqlite_openblob_in_pdo

[rfc-implement-strrstr-for-consistency]: https://wiki.php.net/rfc/implement-strrstr-for-consistency

[rfc-implicit-float-int-deprecate]: https://wiki.php.net/rfc/implicit-float-int-deprecate

[rfc-implicit-move-optimisation]: https://wiki.php.net/rfc/implicit_move_optimisation

[rfc-improve-callbacks-dom-and-xsl]: https://wiki.php.net/rfc/improve_callbacks_dom_and_xsl

[rfc-improve-hash-hkdf-parameter]: https://wiki.php.net/rfc/improve_hash_hkdf_parameter

[rfc-improve-mysqli]: https://wiki.php.net/rfc/improve_mysqli

[rfc-improve-openssl-random-pseudo-bytes]: https://wiki.php.net/rfc/improve-openssl-random-pseudo-bytes

[rfc-improve-predictable-prng-random]: https://wiki.php.net/rfc/improve_predictable_prng_random

[rfc-improve-unserialize-error-handling]: https://wiki.php.net/rfc/improve_unserialize_error_handling

[rfc-improved-error-callback-mechanism]: https://wiki.php.net/rfc/improved_error_callback_mechanism

[rfc-improved-parser-error-message]: https://wiki.php.net/rfc/improved-parser-error-message

[rfc-improved-tls-constants]: https://wiki.php.net/rfc/improved-tls-constants

[rfc-improved-tls-defaults]: https://wiki.php.net/rfc/improved-tls-defaults

[rfc-in-operator]: https://wiki.php.net/rfc/in_operator

[rfc-include-cleanup]: https://wiki.php.net/rfc/include_cleanup

[rfc-incompat-ctx]: https://wiki.php.net/rfc/incompat_ctx

[rfc-inconsistent-behaviors]: https://wiki.php.net/rfc/inconsistent-behaviors

[rfc-increment-decrement-fixes]: https://wiki.php.net/rfc/increment_decrement_fixes

[rfc-indirect-method-call-by-array-var]: https://wiki.php.net/rfc/indirect-method-call-by-array-var

[rfc-inheritance-private-methods]: https://wiki.php.net/rfc/inheritance_private_methods

[rfc-instance-counter]: https://wiki.php.net/rfc/instance_counter

[rfc-instance-method-call]: https://wiki.php.net/rfc/instance-method-call

[rfc-instanceof-improvements]: https://wiki.php.net/rfc/instanceof+improvements

[rfc-intdiv]: https://wiki.php.net/rfc/intdiv

[rfc-integer-rounding]: https://wiki.php.net/rfc/integer-rounding

[rfc-integer-semantics]: https://wiki.php.net/rfc/integer_semantics

[rfc-interface-default-methods]: https://wiki.php.net/rfc/interface-default-methods

[rfc-internal-constructor-behaviour]: https://wiki.php.net/rfc/internal_constructor_behaviour

[rfc-internal-method-return-types]: https://wiki.php.net/rfc/internal_method_return_types

[rfc-internal-serialize-api]: https://wiki.php.net/rfc/internal_serialize_api

[rfc-intersection-types]: https://wiki.php.net/rfc/intersection_types

[rfc-intl-char]: https://wiki.php.net/rfc/intl.char

[rfc-intl-charset-detector]: https://wiki.php.net/rfc/intl.charset-detector

[rfc-intl-timezone-get-windows-id]: https://wiki.php.net/rfc/intl.timezone.get-windows-id

[rfc-intldatetimepatterngenerator]: https://wiki.php.net/rfc/intldatetimepatterngenerator

[rfc-introduce-design-by-contract]: https://wiki.php.net/rfc/introduce_design_by_contract

[rfc-introduce-type-affinity]: https://wiki.php.net/rfc/introduce-type-affinity

[rfc-invalid-strings-in-arithmetic]: https://wiki.php.net/rfc/invalid_strings_in_arithmetic

[rfc-is-countable]: https://wiki.php.net/rfc/is-countable

[rfc-is-json]: https://wiki.php.net/rfc/is_json

[rfc-is-list]: https://wiki.php.net/rfc/is_list

[rfc-is-literal]: https://wiki.php.net/rfc/is_literal

[rfc-is-valid-utf8]: https://wiki.php.net/rfc/is_valid_utf8

[rfc-isset-set-operator]: https://wiki.php.net/rfc/isset-set-operator

[rfc-isset-ternary]: https://wiki.php.net/rfc/isset_ternary

[rfc-iterable-stdclass]: https://wiki.php.net/rfc/iterable-stdclass

[rfc-iterable-to-array-and-iterable-count]: https://wiki.php.net/rfc/iterable_to_array-and-iterable_count

[rfc-iterable]: https://wiki.php.net/rfc/iterable

[rfc-iterator-chaining]: https://wiki.php.net/rfc/iterator+chaining

[rfc-iterator-xyz-accept-array]: https://wiki.php.net/rfc/iterator_xyz_accept_array

[rfc-jenkins]: https://wiki.php.net/rfc/jenkins

[rfc-jit-config-defaults]: https://wiki.php.net/rfc/jit_config_defaults

[rfc-jit-ir]: https://wiki.php.net/rfc/jit-ir

[rfc-jit]: https://wiki.php.net/rfc/jit

[rfc-json-encode-decode-errors]: https://wiki.php.net/rfc/json_encode_decode_errors

[rfc-json-encode-indentation]: https://wiki.php.net/rfc/json_encode_indentation

[rfc-json-numeric-as-string]: https://wiki.php.net/rfc/json_numeric_as_string

[rfc-json-preserve-fractional-part]: https://wiki.php.net/rfc/json_preserve_fractional_part

[rfc-json-throw-on-error]: https://wiki.php.net/rfc/json_throw_on_error

[rfc-json-validate]: https://wiki.php.net/rfc/json_validate

[rfc-jsonable]: https://wiki.php.net/rfc/jsonable

[rfc-jsond]: https://wiki.php.net/rfc/jsond

[rfc-jsonserializable-]: https://wiki.php.net/rfc/jsonserializable+

[rfc-keywords-as-identifiers]: https://wiki.php.net/rfc/keywords_as_identifiers

[rfc-kill-csv-escaping]: https://wiki.php.net/rfc/kill-csv-escaping

[rfc-language-constructs-syntax-changes]: https://wiki.php.net/rfc/language-constructs-syntax-changes

[rfc-ldap-exop]: https://wiki.php.net/rfc/ldap_exop

[rfc-ldap-modify-batch]: https://wiki.php.net/rfc/ldap_modify_batch

[rfc-lemon]: https://wiki.php.net/rfc/lemon

[rfc-lexical-anon]: https://wiki.php.net/rfc/lexical-anon

[rfc-libsodium]: https://wiki.php.net/rfc/libsodium

[rfc-linecontrol]: https://wiki.php.net/rfc/linecontrol

[rfc-linking-in-stream-wrappers]: https://wiki.php.net/rfc/linking_in_stream_wrappers

[rfc-list-assoc-unique]: https://wiki.php.net/rfc/list_assoc_unique

[rfc-list-default-value]: https://wiki.php.net/rfc/list_default_value

[rfc-list-keys]: https://wiki.php.net/rfc/list_keys

[rfc-list-reference-assignment]: https://wiki.php.net/rfc/list_reference_assignment

[rfc-list-syntax-trailing-commas]: https://wiki.php.net/rfc/list-syntax-trailing-commas

[rfc-literal-string]: https://wiki.php.net/rfc/literal_string

[rfc-load-ext-by-name]: https://wiki.php.net/rfc/load-ext-by-name

[rfc-local-variable-types]: https://wiki.php.net/rfc/local_variable_types

[rfc-locale-independent-float-to-string]: https://wiki.php.net/rfc/locale_independent_float_to_string

[rfc-locked-classes]: https://wiki.php.net/rfc/locked-classes

[rfc-logicalshiftoperator]: https://wiki.php.net/rfc/logicalshiftoperator

[rfc-loop-else]: https://wiki.php.net/rfc/loop_else

[rfc-loop-or]: https://wiki.php.net/rfc/loop_or

[rfc-lsb-parentself-forwarding]: https://wiki.php.net/rfc/lsb_parentself_forwarding

[rfc-lsp-errors]: https://wiki.php.net/rfc/lsp_errors

[rfc-magic-methods-signature]: https://wiki.php.net/rfc/magic-methods-signature

[rfc-magicquotes-finale]: https://wiki.php.net/rfc/magicquotes_finale

[rfc-magicquotes]: https://wiki.php.net/rfc/magicquotes

[rfc-make-ctor-ret-void]: https://wiki.php.net/rfc/make_ctor_ret_void

[rfc-make-reflection-setaccessible-no-op]: https://wiki.php.net/rfc/make-reflection-setaccessible-no-op

[rfc-marking-overriden-methods]: https://wiki.php.net/rfc/marking_overriden_methods

[rfc-match-expression-v2]: https://wiki.php.net/rfc/match_expression_v2

[rfc-match-expression]: https://wiki.php.net/rfc/match_expression

[rfc-max-execution-wall-time]: https://wiki.php.net/rfc/max_execution_wall_time

[rfc-mb-str-pad]: https://wiki.php.net/rfc/mb_str_pad

[rfc-mb-str-split]: https://wiki.php.net/rfc/mb_str_split

[rfc-mb-trim]: https://wiki.php.net/rfc/mb_trim

[rfc-mcrypt-viking-funeral]: https://wiki.php.net/rfc/mcrypt-viking-funeral

[rfc-misc-variable-functions]: https://wiki.php.net/rfc/misc_variable_functions

[rfc-mixed-type-v2]: https://wiki.php.net/rfc/mixed_type_v2

[rfc-mixed-typehint-mixed-typehint-proposal-to-add-mixed-typehint-for-parameter-and-return-types-revived-2019-02-07-superseded-by-rfc-mixed-type-v2]: https://wiki.php.net/rfc/mixed-typehint%7CMixed+typehint%5D%5D+%5C%5C+Proposal+to+add+mixed+typehint+for+parameter+and+return+types+%28Revived%3A+2019-02-07%3B+Superseded+by+%5B%5Brfc%3Amixed_type_v2

[rfc-mixed-vs-untyped-properties]: https://wiki.php.net/rfc/mixed_vs_untyped_properties

[rfc-moduleapi-inspection]: https://wiki.php.net/rfc/moduleapi-inspection

[rfc-multibyte-char-handling]: https://wiki.php.net/rfc/multibyte_char_handling

[rfc-multiple-catch]: https://wiki.php.net/rfc/multiple-catch

[rfc-mysql-deprecation]: https://wiki.php.net/rfc/mysql_deprecation

[rfc-mysqli-bind-in-execute]: https://wiki.php.net/rfc/mysqli_bind_in_execute

[rfc-mysqli-default-errmode]: https://wiki.php.net/rfc/mysqli_default_errmode

[rfc-mysqli-execute-query]: https://wiki.php.net/rfc/mysqli_execute_query

[rfc-mysqli-fetch-column]: https://wiki.php.net/rfc/mysqli_fetch_column

[rfc-mysqli-support-for-libmysql]: https://wiki.php.net/rfc/mysqli_support_for_libmysql

[rfc-mysqlnd-localhost-override]: https://wiki.php.net/rfc/mysqlnd_localhost_override

[rfc-named-params]: https://wiki.php.net/rfc/named_params

[rfc-namedparameters-named-parameters-obsolete-dummy-rfc-for-named-parameters-superseded-by-rfc-named-params]: https://wiki.php.net/rfc/namedparameters%7CNamed+Parameters+%28obsolete%29%5D%5D%5C%5C+Dummy+RFC+for+named+parameters%2C+superseded+by+%5B%5Brfc%3Anamed_params

[rfc-nameof]: https://wiki.php.net/rfc/nameof

[rfc-namespace-scoped-declares]: https://wiki.php.net/rfc/namespace_scoped_declares

[rfc-namespace-visibility]: https://wiki.php.net/rfc/namespace-visibility

[rfc-namespaced-names-as-token]: https://wiki.php.net/rfc/namespaced_names_as_token

[rfc-namespaceresolution]: https://wiki.php.net/rfc/namespaceresolution

[rfc-namespaces-in-bundled-extensions]: https://wiki.php.net/rfc/namespaces_in_bundled_extensions

[rfc-namespaces-in-core]: https://wiki.php.net/rfc/namespaces-in-core

[rfc-namespaceseparator]: https://wiki.php.net/rfc/namespaceseparator

[rfc-native-tls]: https://wiki.php.net/rfc/native-tls

[rfc-negative-array-index]: https://wiki.php.net/rfc/negative_array_index

[rfc-nested-classes]: https://wiki.php.net/rfc/nested_classes

[rfc-never-for-parameter-types]: https://wiki.php.net/rfc/never_for_parameter_types

[rfc-new-curl-error-functions]: https://wiki.php.net/rfc/new-curl-error-functions

[rfc-new-in-initializers]: https://wiki.php.net/rfc/new_in_initializers

[rfc-new-output-api]: https://wiki.php.net/rfc/new-output-api

[rfc-new-rounding-modes-to-round-function]: https://wiki.php.net/rfc/new_rounding_modes_to_round_function

[rfc-newinis]: https://wiki.php.net/rfc/newinis

[rfc-non-capturing-catches]: https://wiki.php.net/rfc/non-capturing_catches

[rfc-nonbreakabletraits]: https://wiki.php.net/rfc/NonBreakableTraits

[rfc-nophptags]: https://wiki.php.net/rfc/nophptags

[rfc-noreturn-type]: https://wiki.php.net/rfc/noreturn_type

[rfc-normalize-array-auto-increment-on-copy-on-write]: https://wiki.php.net/rfc/normalize-array-auto-increment-on-copy-on-write

[rfc-normalize-inc-dec]: https://wiki.php.net/rfc/normalize_inc_dec

[rfc-notice-for-non-valid-array-container]: https://wiki.php.net/rfc/notice-for-non-valid-array-container

[rfc-null-coalesce-equal-operator]: https://wiki.php.net/rfc/null_coalesce_equal_operator

[rfc-null-coercion-consistency]: https://wiki.php.net/rfc/null_coercion_consistency

[rfc-null-false-standalone-types]: https://wiki.php.net/rfc/null-false-standalone-types

[rfc-null-standalone-type]: https://wiki.php.net/rfc/null-standalone-type

[rfc-nullable-casting]: https://wiki.php.net/rfc/nullable-casting

[rfc-nullable-intersection-types]: https://wiki.php.net/rfc/nullable_intersection_types

[rfc-nullable-types]: https://wiki.php.net/rfc/nullable_types

[rfc-nullsafe-calls]: https://wiki.php.net/rfc/nullsafe_calls

[rfc-nullsafe-operator]: https://wiki.php.net/rfc/nullsafe_operator

[rfc-number-format-negative-zero]: https://wiki.php.net/rfc/number_format_negative_zero

[rfc-number-format-separator]: https://wiki.php.net/rfc/number_format_separator

[rfc-numeric-literal-separator]: https://wiki.php.net/rfc/numeric_literal_separator

[rfc-object-cast-magic]: https://wiki.php.net/rfc/object_cast_magic

[rfc-object-cast-to-types]: https://wiki.php.net/rfc/object_cast_to_types

[rfc-object-comparison]: https://wiki.php.net/rfc/object-comparison

[rfc-object-initializer]: https://wiki.php.net/rfc/object-initializer

[rfc-object-scope-prng]: https://wiki.php.net/rfc/object_scope_prng

[rfc-object-typehint]: https://wiki.php.net/rfc/object-typehint

[rfc-objectarrayliterals]: https://wiki.php.net/rfc/objectarrayliterals

[rfc-objects-can-be-falsifiable]: https://wiki.php.net/rfc/objects-can-be-falsifiable

[rfc-objkey]: https://wiki.php.net/rfc/objkey

[rfc-octal-overload-checking]: https://wiki.php.net/rfc/octal.overload-checking

[rfc-ommit-double-slash-in-user-stream-wrapper-uri]: https://wiki.php.net/rfc/ommit-double-slash-in-user-stream-wrapper-uri

[rfc-on-demand-name-mangling]: https://wiki.php.net/rfc/on_demand_name_mangling

[rfc-opcache-no-cache]: https://wiki.php.net/rfc/opcache.no_cache

[rfc-operator-functions]: https://wiki.php.net/rfc/operator_functions

[rfc-operator-overloading-gmp]: https://wiki.php.net/rfc/operator_overloading_gmp

[rfc-optimizerplus]: https://wiki.php.net/rfc/optimizerplus

[rfc-optional-t-function]: https://wiki.php.net/rfc/optional-t-function

[rfc-pack-unpack-64bit-formats]: https://wiki.php.net/rfc/pack_unpack_64bit_formats

[rfc-parameter-no-type-variance]: https://wiki.php.net/rfc/parameter-no-type-variance

[rfc-parameter-type-casting-hints]: https://wiki.php.net/rfc/parameter_type_casting_hints

[rfc-parse-str-alternative]: https://wiki.php.net/rfc/parse_str_alternative

[rfc-parser-extension-api]: https://wiki.php.net/rfc/parser-extension-api

[rfc-partial-function-application]: https://wiki.php.net/rfc/partial_function_application

[rfc-partially-supported-callables-expand-deprecation-notices]: https://wiki.php.net/rfc/partially-supported-callables-expand-deprecation-notices

[rfc-password-hash-spec]: https://wiki.php.net/rfc/password_hash_spec

[rfc-password-hash]: https://wiki.php.net/rfc/password_hash

[rfc-password-registry]: https://wiki.php.net/rfc/password_registry

[rfc-pattern-matching]: https://wiki.php.net/rfc/pattern-matching

[rfc-pcre2-migration]: https://wiki.php.net/rfc/pcre2-migration

[rfc-pdo-default-errmode]: https://wiki.php.net/rfc/pdo_default_errmode

[rfc-pdo-driver-specific-subclasses]: https://wiki.php.net/rfc/pdo_driver_specific_subclasses

[rfc-pdo-escape-placeholders]: https://wiki.php.net/rfc/pdo_escape_placeholders

[rfc-pdo-float-type]: https://wiki.php.net/rfc/pdo_float_type

[rfc-pdo-mysql-get-warning-count]: https://wiki.php.net/rfc/pdo-mysql-get-warning-count

[rfc-pdov1]: https://wiki.php.net/rfc/pdov1

[rfc-pecl-http]: https://wiki.php.net/rfc/pecl_http

[rfc-peclversioning]: https://wiki.php.net/rfc/peclversioning

[rfc-performanceimprovements]: https://wiki.php.net/rfc/performanceimprovements

[rfc-permanent-hash-ext]: https://wiki.php.net/rfc/permanent_hash_ext

[rfc-phar-stop-autoloading-metadata]: https://wiki.php.net/rfc/phar_stop_autoloading_metadata

[rfc-phase-out-serializable]: https://wiki.php.net/rfc/phase_out_serializable

[rfc-php-engine-constant]: https://wiki.php.net/rfc/php_engine_constant

[rfc-php-namespace-in-core]: https://wiki.php.net/rfc/php-namespace-in-core

[rfc-php-namespace-policy]: https://wiki.php.net/rfc/php_namespace_policy

[rfc-php-native-interface]: https://wiki.php.net/rfc/php_native_interface

[rfc-php-technical-committee]: https://wiki.php.net/rfc/php_technical_committee

[rfc-php53eol]: https://wiki.php.net/rfc/php53eol

[rfc-php56timeline]: https://wiki.php.net/rfc/php56timeline

[rfc-php57]: https://wiki.php.net/rfc/php57

[rfc-php6]: https://wiki.php.net/rfc/php6

[rfc-php7-foreach]: https://wiki.php.net/rfc/php7_foreach

[rfc-php7timeline]: https://wiki.php.net/rfc/php7timeline

[rfc-php8-assertions]: https://wiki.php.net/rfc/php8_assertions

[rfc-phpdbg]: https://wiki.php.net/rfc/phpdbg

[rfc-phpng]: https://wiki.php.net/rfc/phpng

[rfc-phpp]: https://wiki.php.net/rfc/phpp

[rfc-phpvcs]: https://wiki.php.net/rfc/PHPVCS

[rfc-pipe-operator-v2]: https://wiki.php.net/rfc/pipe-operator-v2

[rfc-pipe-operator]: https://wiki.php.net/rfc/pipe-operator

[rfc-pow-operator]: https://wiki.php.net/rfc/pow-operator

[rfc-precise-float-value]: https://wiki.php.net/rfc/Precise+float+value

[rfc-precise-session-management]: https://wiki.php.net/rfc/precise_session_management

[rfc-preg-replace-callback-array]: https://wiki.php.net/rfc/preg_replace_callback_array

[rfc-preload]: https://wiki.php.net/rfc/preload

[rfc-prevent-disruptions-of-conversations]: https://wiki.php.net/rfc/prevent_disruptions_of_conversations

[rfc-println]: https://wiki.php.net/rfc/println

[rfc-proper-range-semantics]: https://wiki.php.net/rfc/proper-range-semantics

[rfc-property-accessors]: https://wiki.php.net/rfc/property_accessors

[rfc-property-capture]: https://wiki.php.net/rfc/property-capture

[rfc-property-hooks]: https://wiki.php.net/rfc/property-hooks

[rfc-property-type-hints]: https://wiki.php.net/rfc/property_type_hints

[rfc-property-write-visibility]: https://wiki.php.net/rfc/property_write_visibility

[rfc-propertygetsetsyntax-alternative-typehinting-syntax]: https://wiki.php.net/rfc/propertygetsetsyntax-alternative-typehinting-syntax

[rfc-propertygetsetsyntax-as-implemented]: https://wiki.php.net/rfc/propertygetsetsyntax-as-implemented

[rfc-propertygetsetsyntax-v1-2]: https://wiki.php.net/rfc/propertygetsetsyntax-v1.2

[rfc-protectedlookup]: https://wiki.php.net/rfc/protectedlookup

[rfc-protocol-type-hinting]: https://wiki.php.net/rfc/protocol_type_hinting

[rfc-prototype-checks]: https://wiki.php.net/rfc/prototype_checks

[rfc-pure-intersection-types]: https://wiki.php.net/rfc/pure-intersection-types

[rfc-random-ext]: https://wiki.php.net/rfc/random_ext

[rfc-random-extension-improvement]: https://wiki.php.net/rfc/random_extension_improvement

[rfc-random-function-exceptions]: https://wiki.php.net/rfc/Random-Function-Exceptions

[rfc-random-migration]: https://wiki.php.net/rfc/random_migration

[rfc-randomizer-additions]: https://wiki.php.net/rfc/randomizer_additions

[rfc-readable-var-representation]: https://wiki.php.net/rfc/readable_var_representation

[rfc-readline-interactive-shell-result-function]: https://wiki.php.net/rfc/readline_interactive_shell_result_function

[rfc-readonly-amendments]: https://wiki.php.net/rfc/readonly_amendments

[rfc-readonly-classes]: https://wiki.php.net/rfc/readonly_classes

[rfc-readonly-properties-v2]: https://wiki.php.net/rfc/readonly_properties_v2

[rfc-readonly-properties]: https://wiki.php.net/rfc/readonly_properties

[rfc-reclassify-e-strict]: https://wiki.php.net/rfc/reclassify_e_strict

[rfc-redact-parameters-in-back-traces]: https://wiki.php.net/rfc/redact_parameters_in_back_traces

[rfc-reference-reflection]: https://wiki.php.net/rfc/reference_reflection

[rfc-reflectionparameter-getclassname]: https://wiki.php.net/rfc/reflectionparameter-getclassname

[rfc-reflectionparameter-typehint]: https://wiki.php.net/rfc/reflectionparameter.typehint

[rfc-release-cycle-update]: https://wiki.php.net/rfc/release_cycle_update

[rfc-release-md5-deprecation]: https://wiki.php.net/rfc/release-md5-deprecation

[rfc-releaseprocess]: https://wiki.php.net/rfc/releaseprocess

[rfc-removal-of-dead-sapis-and-exts]: https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts

[rfc-removal-of-deprecated-features]: https://wiki.php.net/rfc/removal-of-deprecated-features

[rfc-remove-alternative-php-tags]: https://wiki.php.net/rfc/remove_alternative_php_tags

[rfc-remove-deprecated-functionality-in-php7]: https://wiki.php.net/rfc/remove_deprecated_functionality_in_php7

[rfc-remove-disable-classes]: https://wiki.php.net/rfc/remove_disable_classes

[rfc-remove-hex-support-in-numeric-strings]: https://wiki.php.net/rfc/remove_hex_support_in_numeric_strings

[rfc-remove-php4-constructors]: https://wiki.php.net/rfc/remove_php4_constructors

[rfc-remove-preg-replace-eval-modifier]: https://wiki.php.net/rfc/remove_preg_replace_eval_modifier

[rfc-remove-utf8-decode-and-utf8-encode]: https://wiki.php.net/rfc/remove_utf8_decode_and_utf8_encode

[rfc-remove-zend-api]: https://wiki.php.net/rfc/remove_zend_api

[rfc-rename-double-colon-token]: https://wiki.php.net/rfc/rename-double-colon-token

[rfc-renamed-parameters]: https://wiki.php.net/rfc/renamed_parameters

[rfc-replace-parse-url]: https://wiki.php.net/rfc/replace_parse_url

[rfc-request-response]: https://wiki.php.net/rfc/request_response

[rfc-request-tempnam]: https://wiki.php.net/rfc/request-tempnam

[rfc-reserve-even-more-types-in-php-7]: https://wiki.php.net/rfc/reserve_even_more_types_in_php_7

[rfc-reserve-keywords-in-php-8]: https://wiki.php.net/rfc/reserve_keywords_in_php_8

[rfc-reserve-more-types-in-php-7]: https://wiki.php.net/rfc/reserve_more_types_in_php_7

[rfc-resource-to-object-conversion]: https://wiki.php.net/rfc/resource_to_object_conversion

[rfc-resource-typehint]: https://wiki.php.net/rfc/resource_typehint

[rfc-restrict-globals-usage]: https://wiki.php.net/rfc/restrict_globals_usage

[rfc-retry-keyword]: https://wiki.php.net/rfc/retry-keyword

[rfc-return-types]: https://wiki.php.net/rfc/return_types

[rfc-returntypehint2]: https://wiki.php.net/rfc/returntypehint2

[rfc-revisit-trailing-comma-function-args]: https://wiki.php.net/rfc/revisit-trailing-comma-function-args

[rfc-rfc1867-non-post]: https://wiki.php.net/rfc/rfc1867-non-post

[rfc-rng-extension]: https://wiki.php.net/rfc/rng_extension

[rfc-rng-fixes]: https://wiki.php.net/rfc/rng_fixes

[rfc-rounding]: https://wiki.php.net/rfc/rounding

[rfc-runtimecache]: https://wiki.php.net/rfc/runtimecache

[rfc-safe-cast]: https://wiki.php.net/rfc/safe_cast

[rfc-same-site-cookie]: https://wiki.php.net/rfc/same-site-cookie

[rfc-same-site-parameter]: https://wiki.php.net/rfc/same-site-parameter

[rfc-saner-array-sum-product-saner-array-sum]: https://wiki.php.net/rfc/saner-array-sum-product%7CSaner+array_%28sum

[rfc-saner-inc-dec-operators]: https://wiki.php.net/rfc/saner-inc-dec-operators

[rfc-saner-numeric-strings]: https://wiki.php.net/rfc/saner-numeric-strings

[rfc-scalar-pseudo-type]: https://wiki.php.net/rfc/scalar-pseudo-type

[rfc-scalar-type-hinting-with-cast]: https://wiki.php.net/rfc/scalar_type_hinting_with_cast

[rfc-scalar-type-hints-v5]: https://wiki.php.net/rfc/scalar_type_hints_v5

[rfc-scalar-type-hints]: https://wiki.php.net/rfc/scalar_type_hints

[rfc-script-only-include]: https://wiki.php.net/rfc/script_only_include

[rfc-sealed-classes]: https://wiki.php.net/rfc/sealed_classes

[rfc-secure-html-escape]: https://wiki.php.net/rfc/secure-html-escape

[rfc-secure-serialization]: https://wiki.php.net/rfc/secure_serialization

[rfc-secure-session-options-by-default]: https://wiki.php.net/rfc/secure-session-options-by-default

[rfc-secure-unserialize]: https://wiki.php.net/rfc/secure_unserialize

[rfc-security-classification]: https://wiki.php.net/rfc/security-classification

[rfc-sendrecvmsg]: https://wiki.php.net/rfc/sendrecvmsg

[rfc-session-create-id]: https://wiki.php.net/rfc/session-create-id

[rfc-session-gc]: https://wiki.php.net/rfc/session-gc

[rfc-session-id-without-hashing]: https://wiki.php.net/rfc/session-id-without-hashing

[rfc-session-lock-ini]: https://wiki.php.net/rfc/session-lock-ini

[rfc-session-oo]: https://wiki.php.net/rfc/session-oo

[rfc-session-read-only-lazy-write]: https://wiki.php.net/rfc/session-read_only-lazy_write

[rfc-session-upload-progress]: https://wiki.php.net/rfc/session_upload_progress

[rfc-session-use-strict-mode]: https://wiki.php.net/rfc/session-use-strict-mode

[rfc-session-user-return-value]: https://wiki.php.net/rfc/session.user.return-value

[rfc-shell-exec-result-code-param]: https://wiki.php.net/rfc/shell_exec_result_code_param

[rfc-short-closures]: https://wiki.php.net/rfc/short-closures

[rfc-short-closures]: https://wiki.php.net/rfc/short_closures

[rfc-short-functions]: https://wiki.php.net/rfc/short-functions

[rfc-short-list-syntax]: https://wiki.php.net/rfc/short_list_syntax

[rfc-short-match]: https://wiki.php.net/rfc/short-match

[rfc-short-ternary-equal-operator]: https://wiki.php.net/rfc/short_ternary_equal_operator

[rfc-shortags]: https://wiki.php.net/rfc/shortags

[rfc-shorter-attribute-syntax-change]: https://wiki.php.net/rfc/shorter_attribute_syntax_change

[rfc-shorter-attribute-syntax]: https://wiki.php.net/rfc/shorter_attribute_syntax

[rfc-shortsyntaxforarrays]: https://wiki.php.net/rfc/shortsyntaxforarrays

[rfc-simple-annotations]: https://wiki.php.net/rfc/simple-annotations

[rfc-simplified-named-params]: https://wiki.php.net/rfc/simplified_named_params

[rfc-site-voting-poll]: https://wiki.php.net/rfc/site_voting_poll

[rfc-size-t-and-int64-next]: https://wiki.php.net/rfc/size_t_and_int64_next

[rfc-size-t-and-int64]: https://wiki.php.net/rfc/size_t_and_int64

[rfc-skipparams]: https://wiki.php.net/rfc/skipparams

[rfc-slim-post-data]: https://wiki.php.net/rfc/slim_post_data

[rfc-soap-get-location]: https://wiki.php.net/rfc/soap_get_location

[rfc-socket-getaddrinfo]: https://wiki.php.net/rfc/socket_getaddrinfo

[rfc-socketactivation]: https://wiki.php.net/rfc/socketactivation

[rfc-sodium-argon-hash]: https://wiki.php.net/rfc/sodium.argon.hash

[rfc-sorting-enum]: https://wiki.php.net/rfc/sorting_enum

[rfc-source-files-without-opening-tag]: https://wiki.php.net/rfc/source_files_without_opening_tag

[rfc-sourcemaps]: https://wiki.php.net/rfc/sourcemaps

[rfc-splclassloader]: https://wiki.php.net/rfc/splclassloader

[rfc-spread-operator-for-array]: https://wiki.php.net/rfc/spread_operator_for_array

[rfc-sql-injection-protection]: https://wiki.php.net/rfc/sql_injection_protection

[rfc-sqlite3-exceptions]: https://wiki.php.net/rfc/sqlite3_exceptions

[rfc-stable-sorting]: https://wiki.php.net/rfc/stable_sorting

[rfc-stack-frame-class]: https://wiki.php.net/rfc/stack-frame-class

[rfc-static-class-constructor]: https://wiki.php.net/rfc/static_class_constructor

[rfc-static-classes]: https://wiki.php.net/rfc/static-classes

[rfc-static-return-type]: https://wiki.php.net/rfc/static_return_type

[rfc-static-variable-inheritance]: https://wiki.php.net/rfc/static_variable_inheritance

[rfc-str-contains]: https://wiki.php.net/rfc/str_contains

[rfc-streammetadata]: https://wiki.php.net/rfc/streammetadata

[rfc-strict-argcount]: https://wiki.php.net/rfc/strict_argcount

[rfc-strict-operators]: https://wiki.php.net/rfc/strict_operators

[rfc-strict-sessions]: https://wiki.php.net/rfc/strict_sessions

[rfc-stricter-implicit-boolean-coercions]: https://wiki.php.net/rfc/stricter_implicit_boolean_coercions

[rfc-string-bitwise-shifts]: https://wiki.php.net/rfc/string-bitwise-shifts

[rfc-string-to-number-comparison]: https://wiki.php.net/rfc/string_to_number_comparison

[rfc-stringable]: https://wiki.php.net/rfc/stringable

[rfc-strncmpnegativelen]: https://wiki.php.net/rfc/strncmpnegativelen

[rfc-strtolower-ascii]: https://wiki.php.net/rfc/strtolower-ascii

[rfc-structural-typing-for-closures]: https://wiki.php.net/rfc/structural-typing-for-closures

[rfc-switch-expression-and-statement-improvement]: https://wiki.php.net/rfc/switch-expression-and-statement-improvement

[rfc-switch-expression]: https://wiki.php.net/rfc/switch_expression

[rfc-sync]: https://wiki.php.net/rfc/sync

[rfc-tagged-unions]: https://wiki.php.net/rfc/tagged_unions

[rfc-taint]: https://wiki.php.net/rfc/taint

[rfc-template]: https://wiki.php.net/rfc/template

[rfc-tempnam-suffix-v2]: https://wiki.php.net/rfc/tempnam-suffix-v2

[rfc-ternary-associativity]: https://wiki.php.net/rfc/ternary_associativity

[rfc-this-var]: https://wiki.php.net/rfc/this_var

[rfc-throw-error-in-extensions]: https://wiki.php.net/rfc/throw_error_in_extensions

[rfc-throw-expression]: https://wiki.php.net/rfc/throw_expression

[rfc-throwable-code-generalization]: https://wiki.php.net/rfc/throwable-code-generalization

[rfc-throwable-interface]: https://wiki.php.net/rfc/throwable-interface

[rfc-throwable-string-param-max-len]: https://wiki.php.net/rfc/throwable_string_param_max_len

[rfc-timing-attack]: https://wiki.php.net/rfc/timing_attack

[rfc-tls-peer-verification]: https://wiki.php.net/rfc/tls-peer-verification

[rfc-tls]: https://wiki.php.net/rfc/tls

[rfc-to-array]: https://wiki.php.net/rfc/to-array

[rfc-token-as-object]: https://wiki.php.net/rfc/token_as_object

[rfc-too-few-args]: https://wiki.php.net/rfc/too_few_args

[rfc-tostring-exceptions]: https://wiki.php.net/rfc/tostring_exceptions

[rfc-trailing-comma-function-calls]: https://wiki.php.net/rfc/trailing-comma-function-calls

[rfc-trailing-comma-in-closure-use-list]: https://wiki.php.net/rfc/trailing_comma_in_closure_use_list

[rfc-trailing-comma-in-parameter-list]: https://wiki.php.net/rfc/trailing_comma_in_parameter_list

[rfc-trailing-whitespace-numerics-trailing-whitespace-in-numeric-strings-proposes-to-permit-trailing-whitespace-in-numeric-strings-superseded-by-rfc-saner-numeric-strings]: https://wiki.php.net/rfc/trailing_whitespace_numerics%7CTrailing+whitespace+in+numeric+strings%5D%5D+%5C%5C+Proposes+to+permit+trailing+whitespace+in+numeric+strings.+%28Superseded+by+%5B%5Brfc%3Asaner-numeric-strings

[rfc-traitsmodifications]: https://wiki.php.net/rfc/traitsmodifications

[rfc-travis-ci]: https://wiki.php.net/rfc/travis_ci

[rfc-true-type]: https://wiki.php.net/rfc/true-type

[rfc-typecast-array-desctructuring]: https://wiki.php.net/rfc/typecast_array_desctructuring

[rfc-typechecking]: https://wiki.php.net/rfc/typechecking

[rfc-typed-class-constants]: https://wiki.php.net/rfc/typed_class_constants

[rfc-typed-properties-v2]: https://wiki.php.net/rfc/typed_properties_v2

[rfc-typed-properties]: https://wiki.php.net/rfc/typed-properties

[rfc-typehint-array-desctructuring]: https://wiki.php.net/rfc/typehint_array_desctructuring

[rfc-typesafe-callable]: https://wiki.php.net/rfc/typesafe-callable

[rfc-uconverter]: https://wiki.php.net/rfc/uconverter

[rfc-umaintained-extensions]: https://wiki.php.net/rfc/umaintained_extensions

[rfc-unary-null-coalescing-operator]: https://wiki.php.net/rfc/unary_null_coalescing_operator

[rfc-unbundle-imap-pspell-oci8]: https://wiki.php.net/rfc/unbundle_imap_pspell_oci8

[rfc-unbundle-recode]: https://wiki.php.net/rfc/unbundle_recode

[rfc-unbundle-xmlprc]: https://wiki.php.net/rfc/unbundle_xmlprc

[rfc-unbunle-unmaintained-extensions-php8]: https://wiki.php.net/rfc/unbunle-unmaintained-extensions-php8

[rfc-undefined-property-error-promotion]: https://wiki.php.net/rfc/undefined_property_error_promotion

[rfc-undefined-variable-error-promotion]: https://wiki.php.net/rfc/undefined_variable_error_promotion

[rfc-unicode-escape]: https://wiki.php.net/rfc/unicode_escape

[rfc-unicode-text-processing]: https://wiki.php.net/rfc/unicode_text_processing

[rfc-unified-crypto-source]: https://wiki.php.net/rfc/unified-crypto-source

[rfc-uniform-variable-syntax]: https://wiki.php.net/rfc/uniform_variable_syntax

[rfc-union-types-v2]: https://wiki.php.net/rfc/union_types_v2

[rfc-union-types]: https://wiki.php.net/rfc/union_types

[rfc-uniqid]: https://wiki.php.net/rfc/uniqid

[rfc-unserialize-warn-on-trailing-data]: https://wiki.php.net/rfc/unserialize_warn_on_trailing_data

[rfc-unset-bool]: https://wiki.php.net/rfc/unset_bool

[rfc-url-opcode-cache]: https://wiki.php.net/rfc/url-opcode-cache

[rfc-use-function]: https://wiki.php.net/rfc/use_function

[rfc-use-global-elements]: https://wiki.php.net/rfc/use_global_elements

[rfc-use-php-mt-rand]: https://wiki.php.net/rfc/use-php_mt_rand

[rfc-useas]: https://wiki.php.net/rfc/useas

[rfc-user-defined-operator-overloads]: https://wiki.php.net/rfc/user_defined_operator_overloads

[rfc-user-defined-session-serializer]: https://wiki.php.net/rfc/user_defined_session_serializer

[rfc-userspace-operator-overloading]: https://wiki.php.net/rfc/userspace_operator_overloading

[rfc-uuid]: https://wiki.php.net/rfc/uuid

[rfc-var-deprecation]: https://wiki.php.net/rfc/var_deprecation

[rfc-var-export-array-syntax]: https://wiki.php.net/rfc/var-export-array-syntax

[rfc-var-info]: https://wiki.php.net/rfc/var_info

[rfc-var-type]: https://wiki.php.net/rfc/var_type

[rfc-variable-syntax-tweaks]: https://wiki.php.net/rfc/variable_syntax_tweaks

[rfc-variadic-empty]: https://wiki.php.net/rfc/variadic_empty

[rfc-variadics]: https://wiki.php.net/rfc/variadics

[rfc-vector]: https://wiki.php.net/rfc/vector

[rfc-void-return-type]: https://wiki.php.net/rfc/void_return_type

[rfc-voting-who]: https://wiki.php.net/rfc/voting_who

[rfc-voting]: https://wiki.php.net/rfc/voting

[rfc-wddx-deprecate-class-instance-deserialization]: https://wiki.php.net/rfc/wddx-deprecate-class-instance-deserialization

[rfc-weak-maps]: https://wiki.php.net/rfc/weak_maps

[rfc-weakreferences]: https://wiki.php.net/rfc/weakreferences

[rfc-weakrefs]: https://wiki.php.net/rfc/weakrefs

[rfc-working-with-substrings]: https://wiki.php.net/rfc/working_with_substrings

[rfc-write-once-properties]: https://wiki.php.net/rfc/write_once_properties

[rfc-xml-option-parse-huge]: https://wiki.php.net/rfc/xml_option_parse_huge

[rfc-zend-vm-pause-api]: https://wiki.php.net/rfc/zend-vm-pause-api

[rfc-zendsignals]: https://wiki.php.net/rfc/zendsignals

[rfc-zpp-conversion-rules]: https://wiki.php.net/rfc/zpp-conversion-rules

[rfc-zpp-fail-on-overflow]: https://wiki.php.net/rfc/zpp_fail_on_overflow

[todo-php54-vote]: https://wiki.php.net/todo/php54/vote
