---
{"dg-publish":true,"permalink":"/pdt-s-list-type-dot-dot-expressions/","created":"2023-07-17T01:39:07.306+07:00","updated":"2023-07-25T12:30:28.732+07:00"}
---


# Dot-Dot Expressions

They require `StdEnum` module from the Standard Environment and provide an alternative way to implicitly construct lists.
They cannot be used as a pattern.

All type of lists can be constructed using Dot-Dot expressions, but the element type must be an instance of `Enum` class.

The full syntax has three components, but only the first component is mandatory.

```Clean
// Language: Clean

[ init, next .. last ]
```

## Usage Examples

If only `init` component is given, such an expression evaluates to an infinite list.
Consecutive elements differ by one unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. ]  // [ 1, 2, 3 and so on ]
```

If `init` and `last` components are given, such an expression evaluates to a finite list.
Consecutive elements differ by one unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. 4 ]  // [ 1, 2, 3, 4 ] 
```

If `init` and `next` components are given, such an expression evaluates to an infinite list.
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
x =  [ 1, 0 .. ]  // [ 1, 0, -1 and so on ]
```

If `init`, `next`, and `last` components are given, such an expression evaluates to a finite list.
Consecutive elements differ by `next` minus `init` unit.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 ..7 ]  // [ 1, 3, 5, 7 ]
```

If the difference is positive, elements strictly greater than `last` are not included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 6 ]  // [ 1, 3, 5 ]
```

When `last` is greater than `init` but lesser than `next`, only `init` is included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 2 ]  // [ 1 ]
```

When `last` is lesser than both `init` and `next`, no element is included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 0 ]  // [ ]
```

If the difference is negative, elements strictly less than `last` are not included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 4, 2 .. -3 ]  // [ 4, 2, 0, -2 ]
```

When `last` is greater than `next` but lesser than `init`, only `init` is included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 3, 1 .. 2 ]  // [ 3 ]
```

When `last` is greater than both `next` and `init`, no element is included.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 3, 1 .. 4 ]  // [ ]
```
