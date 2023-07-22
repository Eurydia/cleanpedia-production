---
{"dg-publish":true,"permalink":"/pdt-p-03-integer-type/","created":"2023-07-03T14:26:33.060+07:00","updated":"2023-07-20T19:20:25.979+07:00"}
---


# Integer Type

Integers are represented using 32 bits or 64 bits values.

For built-in functions and operations on integer type, see [[Appendix A/StdInt\|StdInt]] module for additional information.

## Integer Type Declaration

Integer type is explicitly declared with `Int`.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
```

## Integer Literals

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
x = -015  // decimal -13
x =  00   // decimal  0
x =  015  // decimal  13
```

And they can be constructed from hexadecimal notation by prefixing hexadecimal digits with `0x`.

```Clean
// Language: Clean

x :: Int
x = -0xD  // decimal -13
x =  0x0  // decimal  0
x =  0xd  // decimal  13
```


