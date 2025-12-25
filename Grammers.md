# Fire-lang Grammers (WIP)

## Tokens
```
integer     ::=  [0-9]+
float       ::=  ([0-9]+)(\.)?[fF]?
char        ::=  \'(.+)\'
```

## Syntaxes
```
type-name       ::=  <type-name-attr>? <type-name-id> ("::" <type-name-id>)*
type-name-id    ::=  identifier <type-name-qual>?
type-name-qual  ::=  "<" <type-name> ("," <type-name>)* ">"
type-name-attr  ::=  "const"? "ref"?

name-expr-pair  ::=  identifier ":" <expr>
name-type-pair  ::=  identifier ":" <type-name>

boolean ::=  "true" | "false"

value   ::=  integer | float | char | string | <boolean>
factor  ::=  <value>
...
expr    ::=  <assign>

stmt    ::=  scope | if | for | expr ";"

scope   ::=  "{" stmt* "}"
if      ::=  "if" <expr> <scope> ("else" (<if> | <scope>))?
for     ::=  "for" identifier "in" <expr: iterable> <scope>

template-params ::=  "<" identifier ("," identifier)* ">"

struct-field-defs   ::=  <name-type-pair> ("," <name-type-pair>)*

function            ::=  "fn" identifier <template-params>? <func-arg-list>? <func-result-type>? <scope>
func-arg-list       ::=  "(" <name-type-pair> ("," <name-type-pair>)* ")"
func-result-type    ::=  "->" <type-name>

class               ::=  "class" identifier <template-params>? <class-scope>
class-scope         ::=  "{" <var>* <function>* <class-default-ctor>? "}"
class-default-ctor  ::=  "default" "{" <name-expr-pair> ("," <name-expr-pair>)* "}"

enum                ::=  "enum" identifier <enum-scope>
enum-scope          ::=  "{" <enumerator-def> ("," <enumerator-def>)* "}"
enumerator-def      ::=  identifier <enumerator-variant>?
enumerator-variant  ::=  "(" (<type-name> ("," <type-name>)* | <struct-field-defs>) ")"

namespace        ::=  "namespace" identifier ("::" identifier)* <namespace-scope>
namespace-scope  ::=  "{" (<namespace> | <class> | <enum> | <function>)* "}"

import       ::=  "import" <import-path> ";"
import-path  ::=  identifier ("::" identifier)* ("::" "*")?

program    ::=  
    <import>*
    (<namespace> | <class> | <enum> | <function>)*

```

