---
{"dg-publish":true,"permalink":"/predefined-data-types/predefined-primitive-data-types/real-number-type/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-10T08:55:15.293+02:00"}
---


# Real Number Type

Real numbers are represented by 64 bits values.

For built-in functions on real number type, see [[Appendix A/StdReal\|StdReal]] module for additional information.

## Real Number Type Declaration

Real number type is explicitly declared with `Real`.

```Clean
// Language: Clean

expr :: Real
expr =  1.0 + 1.0
```

## Real Number Literals

Real number literals can be constructed from two notations.

They can be constructed from decimal notation.

```Clean
// Language: Clean

-1.3
 0.0
 1.3
```

And they can be constructed from scientific notation.

```Clean
// Language: Clean

-1.3E-2  // -0.13
 0E1     //  0
 1.3E-2  //  0.13
```

In scientific notations, only uppercase "E" is allowed.
The expression results in a compile-time error if a lowercase "e" is used.

```Clean
// Language: Clean

13e-2  // compile-time error
```

## Using Real Number Literal as Pattern

The definitions of `isUnitA` and `isUnitB` are equivalent.

```Clean
// Language: Clean

isUnitA :: Real -> Bool
isUnitA    1.0  =  True
isUnitA    _    =  False

isUnitB :: Real -> Bool
isUnitB    1E1  =  True
isUnitB    _    =  False
```

Multiple notations can mix freely.

```Clean
// Language: Clean

add :: Real Real -> Int
add    0.0  y    =  y
add    x    0E1  =  x
add    x    y    =  x + y
```