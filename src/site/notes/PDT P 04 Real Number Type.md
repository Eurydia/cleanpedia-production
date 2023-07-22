---
{"dg-publish":true,"permalink":"/pdt-p-04-real-number-type/","created":"2023-07-03T14:26:06.677+07:00","updated":"2023-07-16T22:40:39.149+07:00"}
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

Only uppercase "E" is allowed in scientific notations.
The expression results in a compile-time error if lower case "e" is used.

```Clean
// Language: Clean

13e-2  // compile-time error
```

