---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/boolean-type/","created":"2023-07-03T09:26:49.263+02:00","updated":"2023-07-13T22:28:25.182+02:00"}
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

The `exampleA` function returns `True` when it is called with `False`.
Otherwise, it returns `False`.

Example B:

```Clean
// Language: Clean

exampleB :: Bool Bool  -> Bool
exampleB    True True  =  False
exampleB    _    _     =  True
```

The `exampleB` function returns `True` if both of its argument are `True`.
Otherwise, it returns `False`.