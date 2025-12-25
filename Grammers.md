# Fire-lang Grammers (WIP)

## Tokens
```
integer     ::=  [0-9]+
float       ::=  ([0-9]+)(\.)?[fF]?
char        ::=  \'(.+)\'
```

## Expression (Terms)
```
value   ::=  integer | float | char | string | boolean

factor  ::=  value
```

## Expression (Full)
