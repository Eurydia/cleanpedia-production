---
{"dg-publish":true,"permalink":"/pdt-p-real-number-type/","created":"2023-07-03T14:26:06.677+07:00","updated":"2023-07-24T23:17:18.433+07:00"}
---


# Real Number Type

Real numbers are represented by 64 bits values.

For built-in functions and operations on real number type, see [[APX A StdReal\|APX A StdReal]] module.

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

x :: Real
x = -1.3
x =  0.0
x =  1.3
```

And they can be constructed from scientific notation.

```Clean
// Language: Clean

x :: Real
x = -1.3E-2  // -0.13
x =  0E1     //  0
x =  1.3E-2  //  0.13
```

Only upper case "E" can be used in scientific notations.
The expression results in a compile-time error if lower case "e" is used.

```Clean
// Language: Clean

y :: Real
y =  13e-2  // compile-time error
```

