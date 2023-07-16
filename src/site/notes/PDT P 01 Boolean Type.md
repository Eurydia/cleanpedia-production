---
{"dg-publish":true,"permalink":"/pdt-p-01-boolean-type/","created":"2023-07-03T09:26:49.263+02:00","updated":"2023-07-16T17:35:28.394+02:00"}
---


# Boolean Type

Booleans are represented using 8 bits values.

For built-in functions on Boolean type, see [[APX A 02 StdBool\|APX A 02 StdBool]] module for additional information.

## Boolean Type Declaration

Boolean type is explicitly declared with `Bool`.

```Clean
// Language: Clean

expr :: Bool
expr =  1 == 1
```

## Boolean Literals

They have two constructors.
One for each logical value.

```Clean
// Language: Clean

x :: Bool
x =  True
x =  False
```

