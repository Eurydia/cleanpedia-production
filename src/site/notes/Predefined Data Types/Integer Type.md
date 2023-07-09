---
{"dg-publish":true,"permalink":"/predefined-data-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-09T20:16:44.729+02:00"}
---


# Integer Type

Integers are represented using 32 bits or 64 bits values.

For built-in functions on integer type, see [[Appendix A/StdInt\|StdInt]] module for additional information.

## Integer Type Declaration

Integer type is explicitly declared with `Int`.

An integer expression with explicitly type declaration is written as follows.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
```

Declaring an integer parameter in a function.

```Clean
// Language: Clean

add :: Int Int -> Int
add    x   y   =  ...
```

## Integer Literals

Integer literals can be constructed from three notations.

They can be constructed from decimal notation.

```Clean
// Language: Clean

x :: Int
x = -13
x =  0
x =  13
```

They can be constructed from octal notation by prefixing octal digits with `0`.

```Clean
// Language: Clean

x :: Int
x = -015 // decimal -13
x =  00  // decimal  0
x =  015 // decimal  13
```

And they can be constructed from hexadecimal notation by prefixing hexadecimal digits with `0x`.

```Clean
// Language: Clean

x :: Int
-0xD  // decimal -13
 0x0  // decimal  0
 0xd  // decimal  13
```

## Using Integer Literal as Pattern

The following function definition is written with decimal notation.

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    1   =  True
isUnit    _   =  False
```

The following function definition is written with octal notation.

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    01  =  True
isUnit    _   =  False
```

The following function definition is written with hexadecimal notation.

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    0x1 =  True
isUnit    _   =  False
```

The function definitions mentioned above are equivalent.

Different notations can mix freely.

```Clean
// Language: Clean

fastMul :: Int Int -> Int
fastMul    01  rhs =  rhs
fastMul    lhs 0x1 =  lhs
fastMul    lhs rhs =  lhs * rhs
```