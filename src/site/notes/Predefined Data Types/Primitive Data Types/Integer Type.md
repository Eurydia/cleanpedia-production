---
{"dg-publish":true,"permalink":"/predefined-data-types/primitive-data-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-12T11:14:04.115+02:00"}
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

Example A:

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    1   =  True
exampleA    _   =  False
```

The function `exampleA` returns `True` when it is called with 1.
It returns `False` when it is called with other integer.

```Clean
// Language: Clean

exampleA 1    // True
exampleA 01   // True
exampleA 0x1  // True
```

From the example, it can be inferred that `exampleA` has two alternative variants, which are equivalent to the original.

One variant is obtained by using octal notation instead of decimal notation.

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    01  =  True
exampleA    _   =  False
```

And another variant is obtained by using hexadecimal notation.

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    0x1 =  True
exampleA    _   =  False
```

Example B:

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   0   =  x
exampleB    0   y   =  y
exampleB    x   y   =  x + y
```

The function `exampleB` performs integer addition.
If one of its argument is 0, it returns the other argument.

In this example, the function `exampleB` has many equivalent variants.

One variant is obtained by using octal notation instead of decimal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   00  =  x
exampleB    00  y   =  y
exampleB    x   y   =  x + y
```

Another variant is obtained by using hexadecimal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   0x0 =  x
exampleB    0x0 y   =  y
exampleB    x   y   =  x + y
```

A variant can be obtained by mixing octal notation and hexadecimal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   00  =  x
exampleB    0x0 y   =  y
exampleB    x   y   =  x + y
```