---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/boolean-type/","created":"2023-07-03T09:26:49.263+02:00","updated":"2023-07-12T21:44:09.065+02:00"}
---


# Boolean Type

Booleans are represented using 8 bits values.

For built-in functions on Boolean type, see [[Appendix A/StdBool\|StdBool]] module for additional information.

## Boolean Type Declaration

Boolean type is explicitly declared with `Bool`.

```Clean
// Language: Clean

expr :: Bool
expr =  1 == 1
```

## Boolean Literals

They have two constructors.
One for each logical value.

```Clean
// Language: Clean

x :: Bool
x =  True
x =  False
```

## Using Boolean Literal as Pattern

Example A:

```Clean
// Language: Clean

exampleA :: Bool -> Bool
exampleA    True =  False
exampleA    _    =  True
```

The function `exampleA` returns `True` when it is called with `False` and vice versa.

```Clean
// Language: Clean

exampleA True   // False
exampleA False  //True
```

Example B:

```Clean
// Language: Clean

exampleB :: Bool Bool  -> Bool
exampleB    True True  =  False
exampleB    _    _     =  True
```

The function `exampelB` returns `True` if both of its argument are `True`.
Otherwise, it returns `False`.

```Clean
// Language: Clean

exampleB True  True   // True
exampleB True  False  // False
exampleB False True   // False
exampleB False False  // False
```