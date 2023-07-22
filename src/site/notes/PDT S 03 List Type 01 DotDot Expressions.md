---
{"dg-publish":true,"permalink":"/pdt-s-03-list-type-01-dot-dot-expressions/","created":"2023-07-17T01:39:07.306+07:00","updated":"2023-07-20T02:38:56.396+07:00"}
---


# DotDot Expressions

They require *StdEnum* module from the Standard Environment and provide an alternative way to implicitly construct lists.
They cannot be used as a pattern.

All type of lists can be constructed using Dot-Dot expressions, but the element type must be an instance of `Enum` class.

## General Syntax

### Example A: Infinite Lists with Step of One

```Clean
// Language: Clean

listA :: [ T ]
listA =  [ init .. ]
```

By giving the `init` value, an infinite list is constructed.
Consecutive elements differ by one unit.

#### Example Aa

```Clean
// Language: Clean

listAa :: [ Int ]
listAa =  [ 1 .. ]  // [ 1, 2, 3, ... ]
```

#### Example Ab

```Clean
// Language: Clean

listAb :: [ Real ]
listAb =  [ 'a' .. ]  // [ 'a', 'b', 'c', ... ]
```

### Example B: Infinite Lists with Custom Step

```Clean
// Language: Clean

listB :: [ T ]
listB =  [ init, next .. ]
```

By given the `init` value and `next` value, an infinite list is constructed.
Consecutive elements differ by `next - init` unit.

#### Example Ba

```Clean
// Language: Clean

listBa :: [ Int ]
listBa =  [ 1, 3 .. ]  // [ 1, 3, 5, ... ]
```

#### Example Bb

```Clean
// Language: Clean

listBb :: [ Int ]
listBb =  [ 5, 3 .. ]  // [ 5, 3, 1, ... ]
```

### Example C: Finite Lists with Step of One

```Clean
// Language: Clean

listC :: [ T ]
listC =  [ init .. last ]
```

By giving the `init` value and `last` value, a finite list is constructed.
Consecutive elements differ by one unit.

#### Example Ca

```Clean
// Language: Clean

listCa :: [ Int ]
listCa =  [ 1 .. 4 ]  // [ 1, 2, 3, 4 ]
```

#### Example Cb

```Clean
// Language: Clean

listCb :: [ Int ]
listCb =  [ 'a' .. 'd' ]  // [ 'a', 'b', 'c', 'd' ]
```

### Example D: Finite Lists with Custom Step

```Clean
// Language: Clean

listD :: [ T ]
listD =  [ init, next .. last]
```

By giving the `init` value, `next` value, and `last` value, a finite list is constructed.
Consecutive elements differ by `next` minus `init` unit.

If the step is positive, elements strictly greater than `last` are not included.

If the step is negative, elements strictly less than `last` are not included.

#### Example Da

```Clean
// Language: Clean

listDa :: [ Int ]
listDa =  [ 1, 3 .. 6 ]  // [ 1, 3, 5 ]
```

7 is not included in `listDa`.

#### Example Db

```Clean
// Language: Clean

listDb :: [ Int ]
listDb =  [ 5, 3 .. 0 ]  // [ 5, 3, 1 ]
```

-1 is not included in `listDb`.