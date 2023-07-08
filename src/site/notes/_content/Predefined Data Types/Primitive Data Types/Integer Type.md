---
{"dg-publish":true,"permalink":"/content/predefined-data-types/primitive-data-types/integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-08T12:03:00.490+02:00"}
---


# Integer Type

Integers are represented using 32 bits or 64 bits value depending on the system.

## Integer Literals

An integer literal can be constructed with decimal notation, octal notation, or hexadecimal notation.

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

## Typing Integer Expressions

An expression, which evaluates to integer type, can be explicitly typed using `Int`.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
```

## Using Integer Literal as Pattern

See [[_content/Functions/Pattern Matching/Pattern Matching Integers\|Pattern Matching Integers]] for additional examples.

## Built-In Functions on Integer Type

See [[_content/Appendix A/StdInt\|StdInt]] module for additional information.
