---
{"dg-publish":true,"permalink":"/content/primitive-types/character-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-07T22:30:50.417+02:00"}
---


# Character Type

## Character Literal

A character literal is constructed by placing a character inside a pair of single quotation marks (`'..'`).

```Clean
// Language: Clean

'a'
'9'
'Z'
'+'
```

Character literal can be used as a **pattern**.

See [[_content/Functions/Pattern Matching/Pattern Matching Characters\|Pattern Matching Characters]] for additional examples.

## Typing Character Expressions

An expression, which evaluates to character type, can be explicitly typed using `Char`.

```Clean
// Language: Clean

expr :: Char
expr =  'a'
```

## Built-In Functions on Character Type

Functions, which operate on character type, are defined in `StdChar` module, which is a part of the Standard Environment.

See [[_content/Appendix A/StdChar\|StdChar]] for additional details.
