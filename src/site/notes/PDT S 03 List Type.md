---
{"dg-publish":true,"permalink":"/pdt-s-03-list-type/","created":"2023-07-03T14:26:06.677+07:00","updated":"2023-07-20T20:34:14.081+07:00"}
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
- unboxed head strict,
- unboxed strict, and
- overloaded.

They are considered different type with unique time and space properties.
Functions defined on one type of list cannot be applied to another.
With overloaded lists being an exception, function defined on overloaded lists will work any type of lists.

List type is a generic type with an arity of one.
The argument represents the element type, which is given by placing it inside or after the list type.

### Lazy Lists

They are explicitly declared with a pair of square brackets (`[ ... ]`).

```Clean
// Language: Clean

listAa :: [ Int ]
listAa =  [ 1, 2, 3 ]

listAb :: [ ] Int
listAb =  [ 1, 2, 3 ]
```

### Head Strict Lists

They are explicitly declared by placing an exclamation mark (`!`) after the opening square bracket (`[! ... ]`).

```Clean
// Language: Clean

listBa :: [! Int ]
listBa =  [! 1, 2, 3 ]

listBb :: [! ] Int 
listBb =  [! 1, 2, 3 ]
```

### Tail Strict Lists

They are explicitly declared by placing an exclamation mark (`!`) before the closing square bracket (`[ ... !]`).

```Clean
// Language: Clean

listCa :: [ Int !] 
listCa =  [ 1, 2, 3 !]

listCb :: [ !] Int
listCb =  [ 1, 2, 3 !]
```

### Strict Lists

They are explicitly declared by placing an exclamation mark (`!`) after and before the square bracket (`[! ... !]`).

```Clean
// Language: Clean

listDa :: [! Int !]
listDa =  [! 1, 2, 3 !]

listDb :: [! !] Int
listDb =  [! 1, 2, 3 !]
```

### Unboxed Head Strict Lists

They are explicitly declared by placing a hash symbol (`#`) after the opening square bracket (`[ # ... ]`).

```Clean
// Language: Clean

listEa :: [ # Int ]
listEa =  [ # 1, 2, 3 ]

listEb :: [ # ] Int
listEb =  [ # 1, 2, 3 ]
```

### Unboxed Strict Lists

They are explicitly declared by placing a hash symbol (`#`) and an exclamation mark (`!`) after the opening square bracket (`[ #! ... ]`).

```Clean
// Language: Clean

listFa :: [ #! Int ]
listFa =  [ #! 1, 2, 3 ]

listFb :: [ #! ] Int 
listFb =  [ #! 1, 2, 3 ]
```

### Overloaded Lists

They are explicitly declared by placing a vertical (`|`) bar after the opening square bracket (`[ | ... ]`).

```Clean
// Language: Clean

listGa :: [ | Int ]
listGa =  [ | 1, 2, 3 ]

listGb :: [ | ] Int 
listGb =  [ | 1, 2, 3 ]
```

## List Literals

List literals refer to the explicit enumeration of their elements, since structured data types do not have a "literal" form.

### Simple Lists Literals

A simple list is constructed by placing an element inside a pair of square brackets (`[ ... ]`)

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 ]
```

Elements are comma (`,`) separated.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 1, 1 ]
```

### Colons in List Literals

Commas (`,`) are used to separate each element

```Clean
// Language: Clean

listB :: [ Int ]
listB =  [ 1, 2, 3 ]
```

### Colons in Explicit List Enumeration

Colons (`:`) are used to list construction.

Multiple colons may be used in a list construction, however, doing so can lead to confusion.

```Clean
// Language: Clean

listC :: [ Int ]
listC =  [ 1, 2, 3 ]

listCa :: [ Int ]
listCa =  [ 1 : [ 2 : [ 3 : [] ] ] ]

listCb :: [ Int ]
listCb =  [ 1 : 2 : 3 : [] ]
```

### Using Commas and Colons

To improve 

```Clean
// Language: Clean

listD :: [ Int ]
listD =  [ 1, 2, 3 ]

listDa :: [ Int ] 
listDa =  [ 1, 2 : [ 3 ] ]

listDb :: [ Int ]
listDb =  [ 1, 2, 3 : [] ]

listDc :: [ Int ]
listDc =  [ 1 : [ 2, 3 ] ]
```

### Character List

```Clean
// Language: Clean

listE :: [ Char ]
listE =  ['a', 'b', 'c']

listEa :: [ Char ] 
listEa =  [ 'abc' ]

listEb :: [ Char ]
listEb =  [ 'ab', 'c' ]
```

## Implicit List Construction

Comprehensions and DotDot expressions provide ways to implicitly construct lists.
Neither of which can be used as a pattern.
See [[PDT S 05 Comprehensions\|PDT S 05 Comprehensions]] and [[PDT S 03 List Type 01 DotDot Expressions#DotDot Expressions\|PDT S 03 List Type 01 DotDot Expressions#DotDot Expressions]] for additional information.

