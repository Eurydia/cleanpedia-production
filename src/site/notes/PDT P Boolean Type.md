---
{"dg-publish":true,"permalink":"/pdt-p-boolean-type/","created":"2023-07-03T14:26:49.263+07:00","updated":"2023-07-23T03:57:41.967+07:00"}
---


# Boolean Type

Booleans are represented using 8 bits values.

For built-in functions and operations on Boolean type, see [[APX A 02 StdBool\|APX A 02 StdBool]].

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

