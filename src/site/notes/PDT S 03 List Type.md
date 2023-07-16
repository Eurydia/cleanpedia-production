---
{"dg-publish":true,"permalink":"/pdt-s-03-list-type/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-16T19:16:23.264+02:00"}
---


# List Type

Lists can contain an infinite number of elements. 
Elements of a list must be of the same type. 

For built-in functions on list, see [[Appendix A/StdList\|StdList]], [[Appendix A/APX A 04 StdCharList\|APX A 04 StdCharList]], and [[Appendix A/StdOrdList\|StdOrdList]] module for additional information.

## List Type Declaration

Lists are lazy by default, but other types are:
- head strict, 
- tail strict, 
- strict, 
- unboxed head strict, and
- unboxed strict. 

They are considered different type with unique time and space properties.
Functions defined on one type of list cannot be applied to another. 
However, overloaded functions can be introduced, which can be used on any type of list.

List type is a generic type with an arity of one.
The argument represents the element type, which is given by placing it inside or after the list type.

### Example A: Lazy Lists

They are explicitly declared with square brackets (`[ ... ]`).

#### Example Aa

```Clean
// Language: Clean

listAa :: [ Int ]
listAa =  [ 1, 2, 3 ]
```

#### Example Ab

```Clean
// Language: Clean

listAb :: [ ] Int
listAb =  [ 1, 2, 3 ]
```

### Example B: Head Strict Lists

They are explicitly declared by placing an exclamation mark after the opening square bracket (`[! ... ]`).

#### Example Ba

```Clean
// Language: Clean

listBa :: [! Int ]
listBa =  [! 1, 2, 3 ]
```

#### Example Bb

```Clean
// Language: Clean

listBb :: [! ] Int 
listBb =  [! 1, 2, 3 ]
```

### Example C: Tail Strict Lists

They are explicitly declared by placing an exclamation mark before the closing square bracket (`[ ... !]`).

#### Example Ca

```Clean
// Language: Clean

listCa :: [ Int !] 
listCa =  [ 1, 2, 3 !]
```

#### Example Cb

```Clean
// Language: Clean

listCb :: [ !] Int
listCb =  [ 1, 2, 3 !]
```

### Example D: Strict Lists

They are explicitly declared by placing an exclamation mark after and before the square bracket (`[! ... !]`).

#### Example Da

```Clean
// Language: Clean

listDa :: [! Int !]
listDa =  [! 1, 2, 3 !]
```

#### Example Db

```Clean
// Language: Clean

listDb :: [! !] Int
listDb =  [! 1, 2, 3 !]
```

### Example E: Unboxed Head Strict Lists

They are explicitly declared by placing a hash symbol after the opening square bracket (`[ # ... ]`).

```Clean
// Language: Clean

listEa :: [ # Int ]
listEa =  [ # 1, 2, 3 ]

listEb :: [ # ] Int
listEb =  [ # 1, 2, 3 ]
```

### Example F: Unboxed Strict Lists

They are explicitly declared by placing a hash symbol and an exclamation mark after the opening square bracket (`[ #! ... ]`).

#### Example Fa

```Clean
// Language: Clean

listFa :: [ #! Int ]
listFa =  [ #! 1, 2, 3 ]
```

#### Example Fb

```Clean
// Language: Clean

listFb :: [ #! ] Int 
listFb =  [ #! 1, 2, 3 ]
```

## List Literals

List literals refer to the explicit enumeration of their elements, since structured data types do not have a "literal" form.

### Example A: Singleton Lists

```Clean
// Language: Clean

listA :: [ Int ]
listA =  [ 1 ]
```

### Example B: Simple Lists

Commas (`,`) are used to separate each element

```Clean
// Language: Clean

listB :: [ Int ]
listB =  [ 1, 2, 3 ]
```

### Example C: Colons in List Enumeration

Colons (`:`) are used to list construction.

They can be seen as a pseudo right-associated "operator".
The left side of a colon is an element, and the right side is a list.

```Clean
// Language: Clean

listC :: [ Int ]
listC =  [ 1, 2, 3 ]
```

Examples given are equivalent to the `listC` list.

#### Example Ca

```Clean
// Language: Clean

listCa :: [ Int ]
listCa =  [ 1 : [ 2 : [ 3 : [] ] ] ]
```

#### Example Cb

```Clean
// Language: Clean

listCb :: [ Int ]
listCb =  [ 1 : 2 : 3 : [] ]
```

### Example D: Using Commas and Colons

```Clean
// Language: Clean

listD :: [ Int ]
listD =  [ 1, 2, 3 ]
```

Examples given are equivalent to the `listD` list.

#### Example Da

```Clean
// Language: Clean

listDa :: [ Int ] 
listDa =  [ 1, 2 : [ 3 ] ]
```

#### Example Db

```Clean
// Language: Clean

listDb :: [ Int ]
listDb =  [ 1, 2, 3 : [] ]
```

#### Example Dc

```Clean
// Language: Clean

listDc :: [ Int ]
listDc =  [ 1 : [ 2, 3 ] ]
```

### Example E: Notation for Character List

```Clean
// Language: Clean

listE :: [ Char ]
listE =  ['a', 'b', 'c']
```

Examples given are equivalent to the `listE` list.

#### Example Ea

```Clean
// Language: Clean

listEa :: [ Char ] 
listEa =  [ 'abc' ]
```

#### Example Eb

```Clean
// Language: Clean

listEb :: [ Char ]
listEb =  [ 'ab', 'c' ]
```

## List Comprehensions

All type of lists can be implicitly constructed using comprehension.
See [[PDT S 05 Comprehensions\|PDT S 05 Comprehensions]] for additional information.

## Dot-Dot Expressions

All type of lists can be implicitly constructed using Dot-Dot expressions. 
They require `StdEnum` module from the Standard Environment.

### Example A: Infinite Lists with Step of One

```Clean
// Language: Clean

listA :: [ ] T
listA =  [ initial .. ]
```

By giving the `initial` value, an infinite list is constructed.
Subsequent elements are incremented by one.

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
listAb =  [ 1.0 .. ]  // [ 1.0, 2.0, 3.0, ... ]
```

#### Example Ac

```Clean
// Language: Clean

listAc :: [ Char ]
listAc =  [ 'a' .. ]  // [ 'a', 'b', 'c', ... ]
```

### Example B: Infinite Lists with Custom Step

```Clean
// Language: Clean

listA :: [ ] T
listA =  [ initial, next .. ]
```

By given the `initial` value and `next` value, an infinite list is constructed.
Subsequent elements are incremented or decremented by `next - initial`.

#### Example Ba

```Clean
// Language: Clean

listBa :: [ Int ]
listBa =  [ 1, 3 .. ]  // [ 1, 3, 5, ... ]
```

#### Example Bb

```Clean
// Language: Clean

listBb :: [ Char ]
listBb =  [ 'a', 'c' .. ]  // [ 'a', 'c', 'e', ... ]
```

#### Example Bc

```Clean
// Language: Clean

listBc :: [ Int ]
listBc =  [ 1, 0 .. ]  // [ 1, 0, -1, ... ]
```

#### Example Bd

```Clean
// Language: Clean

listBd :: [ Int ]
listBd =  [ 'z', 'y' .. ]  // [ 'z', 'y', 'x', ... ]
```

### Example C: Finite Lists with Step of One

```Clean
// Language: Clean

listC :: [ T ]
listC =  [ initial .. last]
```

By giving the `initial` value and `last` value, a finite list is constructed.
Consecutive elements differ by one.


#### Example Ca

```Clean
// Language: Clean

listCa :: [ Int ]
listCa =  [ 1 .. 4 ]  // [ 1, 2, 3, 4 ]
```

#### Example Cb

```Clean
// Language: Clean

listCb :: [ Real ]
listCb =  [ 1.0 .. 4.0  ]  // [ 1.0, 2.0, 3.0, 4.0 ]
```

#### Example Cc

```Clean
// Language: Clean

listCc :: [ Char ]
listCc =  [ 'a' .. 'd' ]  // [ 'a', 'b', 'c', 'd' ]
```

#### Example Cd

```Clean
// Language: Clean

listCd :: [ Int ]
listCd =  [ 0 .. 0 ]  // [ 0 ]
```

### Example D: Finite Lists with Custom Step

```Clean
// Language: Clean

listD :: [ T ]
listD =  [ initial, next .. last]
```

By giving the `initial` value, `next` value, and `last` value, a finite list is constructed.
Consecutive elements differ by `next - initial`.

If the step is positive, elements strictly greater than `last` will not be included, and if the step is negative, elements strictly less than `last` will not be included.

#### Example Da

```Clean
// Language: Clean

listDa :: [ Int ]
listDa =  [ 1, 3 .. 5 ]  // [ 1, 3, 5 ]
```

#### Example Db

```Clean
// Language: Clean

listDb :: [ Int ]
listDb =  [ 5, 3 .. 1 ]  // [ 5, 3, 1 ]
```

#### Example Dc

```Clean
// Language: Clean

listDc :: [ Int ]
listDc =  [ 1, 3 .. 6 ]  // [ 1, 3, 5 ]
```

#### Example Db

```Clean
// Language: Clean

listDb :: [ Int ]
listDb =  [ 5, 3 .. 0 ]  // [ 5, 3, 1 ]
```

