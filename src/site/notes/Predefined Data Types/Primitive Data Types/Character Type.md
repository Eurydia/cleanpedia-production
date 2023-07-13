---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/character-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-13T11:33:57.093+02:00"}
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

They are constructed by placing a character inside a pair of single quotation marks (`'...'`).

```Clean
// Language: Clean

x :: Char
x =  '1'
x =  'a'
x =  'A'
x =  '+'
```

## Using Character Literal as Pattern

Example A:

```Clean
// Language: Clean

exampleA :: Char -> Bool
exampleA    'G'  =  True
exampleA    _    =  False
```

The `exampleA` function returns `True` when it is called with upper case 'G'.
Otherwise, it returns `False`.

Example B:

```Clean
// Language: Clean

exampleB :: Char -> Bool
exampleB    'G'  =  True
exampleB    'g'  =  True
exampleB    _    =  False
```

The `exampleB` function returns `True` when it is called with lower case or upper case 'G'.
Otherwise, it returns `False`.

Example C:

```Clean
// Language: Clean

exampleC :: Char Char -> Bool
exampleC    'G'  'G'  =  True
exampleC    _    _    =  False
```

The `exampleC` function returns `True` when it is called with two upper case 'G'.
Otherwise, it returns `False`.

Example D:

```Clean
// Language: Clean

exampleD :: Char Char -> Bool
exampleD    'G'  'G'  =  True
exampleD    'G'  'g'  =  True
exampleD    'g'  'G'  =  True
exampleD    'g'  'g'  =  True
exampleD    _    _    =  False
```

The `exampleD` function returns `True` when both of its arguments are 'G'.
Otherwise, it returns `False`.
