---
{"dg-publish":true,"permalink":"/content/primitive-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-07T22:27:26.346+02:00"}
---


# Integer Type

## Integer Literals

An integer literal can be constructed with decimal notation, octal notation, and hexadecimal notation.

Integer literals constructed with decimal notation can be written as follows.

```Clean
// Language: Clean

-13
 0
 13
```

Integer literals constructed with octal notation can be written by prefixing octal digits with "`0`".

```Clean
// Language: Clean

-015  // decimal -13
 00   // decimal  0
 015  // decimal  13
```

Integers literals constructed with hexadecimal notation can be written by prefixing hexadecimal digits with "`0x`".

```Clean
// Language: Clean

-0xD  // decimal -13
 0x0  // decimal  0
 0xd  // decimal  13
```

Integer literals can be used as a **pattern**.

See [[_content/Functions/Pattern Matching/Pattern Matching Integers\|Pattern Matching Integers]] for additional examples.

## Typing Integer Expressions

An expression, which resolves to integer type, can be explicitly typed using `Int`.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
```

## Built-In Functions on Integer Type

Functions, which operate on integer type, are defined in `StdInt` module, which is a part of the Standard Environment.

See [[_content/Appendix A/StdInt\|StdInt]] for additional details.
