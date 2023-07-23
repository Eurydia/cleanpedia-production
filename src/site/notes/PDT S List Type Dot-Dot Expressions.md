---
{"dg-publish":true,"permalink":"/pdt-s-list-type-dot-dot-expressions/","created":"2023-07-17T01:39:07.306+07:00","updated":"2023-07-23T05:26:13.429+07:00"}
---


# Dot-Dot Expressions

They require `StdEnum` module from the Standard Environment and provide an alternative way to implicitly construct lists.
They cannot be used as a pattern.

## General Syntax

All type of lists can be constructed using Dot-Dot expressions, but the element type must be an instance of `Enum` class.

The full syntax has three arguments, but only the first is mandatory.

```Clean
// Language: Clean

[ init, next .. last ]
```

If only `init` is given, an infinite list is constructed.
Consecutive elements differ by one unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. ]  // [ 1, 2, 3 and so on ]
```

If `init` and `last` are given, a finite list is constructed.
Consecutive elements differ by one unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. 4 ]  // [ 1, 2, 3, 4 ] 
```

If `init` and `next` are given, an infinite list is constructed.
Consecutive elements differ by `next` minus `init` unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. ]  // [ 1, 3, 5 and so on ]
```

It is possible to construct an infinite list whose elements are in descending order.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 0 .. ]  // [1, 0, -1 and so on ]
```

By giving the `init`, `next`, and `last`, a finite list is constructed.
Consecutive elements differ by `next` minus `init` unit.

If the step is positive, elements strictly greater than `last` are not included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 6 ]  // [ 1, 3, 5 ]
```

Notice that 7 is not a part of the list.

If the step is negative, elements strictly less than `last` are not included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 4, 2 .. -3 ]  // [ 4, 2, 0, -2 ]
```

Notice that -4 is not a part of the list.

## Additional Examples

Case 1:
- positive step,
- `last` is smaller than `next`, and
- `last` is larger than `init`.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 2 ] // [ 1 ]
```

Case 2:
- negative step,
- `last` is larger than `next`, and
- `last` is smaller than `init`.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 3, 1 .. 2 ] // [ 3 ]
```

Case 3:
- positive step,
- `last` is smaller than `next`, and
- `last` is smaller than `init`.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 0 ] // [ ]
```

Case 4:
- negative step,
- `last` is larger than `next`, and
- `last` is larger than `init`.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 3, 1 .. 4 ] // [ ]
```
