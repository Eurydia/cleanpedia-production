---
{"dg-publish":true,"permalink":"/predefined-data-types/character-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-09T10:37:04.581+02:00"}
---


# Character Type

Characters are represented using 8 bits values.

## Character Literals

Character literals are constructed in the same way by placing a character inside a pair of single quotation marks (`'...'`).

```Clean
// Language: Clean

'1'
'a'
'A'
'+'
```

## Typing Character Expressions

An expression, which evaluates to character type, can be explicitly typed using `Char`.

```Clean
// Language: Clean

expr :: Char
expr =  'a'
```

## Using Character Literal as Pattern

See [[_content/Functions/Pattern Matching/Pattern Matching Characters\|Pattern Matching Characters]] for additional examples.

## Built-In Functions on Character Type

See [[Appendix A/StdChar\|StdChar]] module for additional information.
