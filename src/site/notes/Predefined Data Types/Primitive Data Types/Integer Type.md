---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-10T09:01:37.787+02:00"}
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

And they can be constructed from hexadecimal notation by prefixing hexadecimal digits with `0x`.

```Clean
// Language: Clean

x :: Int
x = -0xD  // decimal -13
x =  0x0  // decimal  0
x =  0xd  // decimal  13
```

## Using Integer Literal as Pattern

The definitions of `isUnitA`, `isUnitB`, and `isUnitC` are equivalent.

```Clean
// Language: Clean

isUnitA :: Int -> Bool
isUnitA    1   =  True
isUnitA    _   =  False

isUnitB :: Int -> Bool
isUnitB    01  =  True
isUnitB    _   =  False

isUnitC :: Int -> Bool
isUnitC    0x1 =  True
isUnitC    _   =  False
```

Multiple notations can mix freely.

```Clean
// Language: Clean

sum :: Int Int -> Int
sum    00  y   =  y
sum    x   0x0 =  x
sum    x   y   =  x + y
```