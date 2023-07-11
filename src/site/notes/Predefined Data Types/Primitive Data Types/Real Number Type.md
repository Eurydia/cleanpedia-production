---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/real-number-type/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-11T10:37:09.149+02:00"}
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

Example 1:

```Clean
// Language: Clean

isUnit :: Real -> Bool
isUnit    1.0  =  True
isUnit    _    =  False
```

The definition of `isUnit` has an alternative variant.

One variant is obtained by using scientific notation instead of decimal notation.

```Clean
// Language: Clean

isUnit :: Real -> Bool
isUnit    1E1  =  True
isUnit    _    =  False
```

The behavior of `isUnit` is unchanged, as each notation represents the same numerical value.

Example 2:

```Clean
// Language: Clean

add :: Real Real -> Real
add    0.0  y    =  y
add    x    0.0  =  x
add    x    y    =  x + y
```

Since different notation can mix freely, the definition of `add` can be written in various ways.

```Clean
// Language: Clean

add :: Real Real -> Real
add    0.0  y    =  y
add    x    1E0  =  x
add    x    y    =  x + y
```