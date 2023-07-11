---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/character-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-11T12:12:51.055+02:00"}
---


# Character Type

Characters are represented using 8 bits values.

For built-In functions on character type, see [[Appendix A/StdChar\|StdChar]] module for additional information.

## Character Type Declaration

Character type is explicitly declared with `Char`.

```Clean
// Language: Clean

expr :: Char
expr =  'a'
```

## Character Literals

Character literals are constructed by placing a character inside a pair of single quotation marks (`'...'`).

```Clean
// Language: Clean

x :: Char
x =  '1'
x =  'a'
x =  'A'
x =  '+'
```

## Using Character Literal as Pattern

Example:

```Clean
// Language: Clean

isA :: Char -> Bool
isA    'A'  =  True
isA    'a'  =  True
isA    _    =  False
```