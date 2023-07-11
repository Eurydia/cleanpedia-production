---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-11T10:37:37.035+02:00"}
---


# Integer Type

Integers are represented using 32 bits or 64 bits values.

For built-in functions on integer type, see [[Appendix A/StdInt\|StdInt]] module for additional information.

## Integer Type Declaration

Integer type is explicitly declared with `Int`.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
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

They can be constructed from hexadecimal notation by prefixing hexadecimal digits with `0x`.

```Clean
// Language: Clean

x :: Int
x = -0xD  // decimal -13
x =  0x0  // decimal  0
x =  0xd  // decimal  13
```

## Using Integer Literal as Pattern

Example 1:

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    1   =  True
isUnit    _   =  False
```

The definition of `isUnit` has two alternative variants.

One variant is obtained by using octal notation instead of decimal notation.

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    01  =  True
isUnit    _   =  False
```

And another is obtained using hexadecimal notation.

```Clean
// Language: Clean

isUnit :: Int -> Bool
isUnit    0x1 =  True
isUnit    _   =  False
```

The behavior of `isUnit` is unchanged, as each notation represents the same numerical value.

Example 2:

```Clean
// Language: Clean

add :: Int Int -> Int
add    0   y   =  y
add    x   0   =  x
add    x   y   =  x + y
```

Since different notation can mix freely, the definition of `add` can be written in various ways.

```Clean
// Language: Clean

add :: Int Int -> Int
add    00  y   =  y
add    x   0x0 =  x
add    x   y   =  x + y
```