---
{"dg-publish":true,"permalink":"/content/predefined-data-types/primitive-data-types/real-number-type/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-08T12:19:21.966+02:00"}
---


# Real Number Type

Real numbers are represented by 64 bits values.

## Real Number Literals

A real number literal can be constructed with decimal notation or scientific notation.

Real number literals constructed with decimal notation can be written as follows.

```
// Language: Clean

-1.3
 0.0
 1.3
```

Real number literals constructed with scientific notation can be written as follows.

```
// Language: Clean

-13E-2  // -0.13
 0E0    //  0
 13E-2  //  0.13
```

Only uppercase "E" maybe used in scientific notations.
The expression results in a compile-time error if a lowercase "e" is used.

```Clean
// Language: Clean

13e-2  // Uh-oh
```

## Typing Real Number Expressions

An expression, which resolves to real number type, can be explicitly typed using `Real`.

```Clean
// Language: Clean

expr :: Real
expr =  1.0 + 1.0
```

## Using Real Number Literal as Pattern

See [[_content/Functions/Pattern Matching/Pattern Matching Real Numbers\|Pattern Matching Real Numbers]] for additional examples.

## Built-In Functions on Real Number Type

See [[_content/Appendix A/StdReal\|StdReal]] module for additional information.