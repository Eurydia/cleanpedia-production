---
{"dg-publish":true,"permalink":"/predefined-data-types/predefined-primitive-data-types/boolean-type/","created":"2023-07-03T09:26:49.263+02:00","updated":"2023-07-10T09:00:40.027+02:00"}
---


# Boolean Type

Booleans are represented using 8 bits values.

For built-in functions on Boolean type, see [[Appendix A/StdBool\|StdBool]] module for additional information.

## Boolean Type Declaration

Boolean type is explicitly declared with `Bool`.

```Clean
// Language: Clean

expr :: Bool
expr =  1 == 1
```

## Boolean Literals

Boolean literals have two constructors.

```Clean
// Language: Clean

x :: Bool
x =  True
x =  False
```

## Using Integer Literal as Pattern

```Clean
// Language: Clean

implies :: Bool Bool  -> Bool
implies    True False =  False
implies    _    _     =  True
```