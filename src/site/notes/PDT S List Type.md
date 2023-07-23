---
{"dg-publish":true,"permalink":"/pdt-s-list-type/","created":"2023-07-03T14:26:06.677+07:00","updated":"2023-07-23T04:19:36.359+07:00"}
---


# List Type

Lists can contain an infinite number of elements. 
Elements of a list must be of the same type. 

For built-in functions and operations on list, see [[Appendix A/StdList\|StdList]], [[Appendix A/APX A 04 StdCharList\|APX A 04 StdCharList]], and [[Appendix A/StdOrdList\|StdOrdList]] module for additional information.

## List Type Declaration

Lazy list is explicitly declared by placing the element type inside a pair of square brackets (`[ ... ]`).

```Clean
// Language: Clean

expr :: [ Int ]
expr =  [ 1, 2, 3 ]
```

List type can be placed in front of element type.

```Clean
// Language: Clean

expr :: [ ] Int
expr =  [ 1, 2, 3 ]
```

## List Literals

They are the explicit enumeration of elements, and can be used as patterns.

Commas (`,`) are used to separate each element of a list.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 2, 3 ]
```

Colons (`:`) act as right-associate pseudo-operator in list construction.
They accept two arguments.
An element on its left, and a list on its right.
They evaluate by prepending the element to the front of the list, and return a new list.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 : 2 : 3 : [] ]
x =  [ 1 : [ 2 : [ 3 : [] ] ] ]
```

Commas and colons can be used together.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 : [ 2, 3 ] ]
x =  [ 1, 2 : [ 3 ] ]
```

A special constructor is provided for lists of characters.

By placing multiple characters inside a pair of single quotation marks (`' ... '`), each character is treated as an element of the list.

```Clean
// Language: Clean

xc :: [ Char ]
xc =  [ 'a', 'b', 'c' ]
xc =  [ 'abc' ]
```

Commas can be used with this special notation.

```Clean
// Language: Clean

xc :: [ Char ]
xc =  [ 'a', 'bc' ]
```

## Implicit List Construction

Lists can be implicitly constructed, but they cannot be used as patterns.

Colons can be used to construct lists from existing ones.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 2, 3 ]

y :: [ Int ]
y =  [ 1 : x ]
```

Dot-Dot expressions construct lists from enumerable data types, see [[PDT S List Type Dot-Dot Expressions\|PDT S List Type Dot-Dot Expressions]].

And comprehensions construct list using from generators, see [[PDT S Comprehensions\|PDT S Comprehensions]].

## Additional List Types

So far only lazy lists are discussed, but other types of lists are:
- head strict, 
- tail strict, 
- strict, 
- unboxed head strict,
- unboxed strict, and 
- overloaded.

They are considered different type with unique time and space properties.

A function defined on one type of list cannot be applied to others.
However, a function defined on overloaded list can be applied to any type of list.

Head strict lists are explicitly declared by placing an exclamation mark (`!`) after the opening square bracket (`[! ... ]`).

```Clean
// Language: Clean

x :: [! Int ]
x =  [! 1, 2, 3 ]
```

Tail strict lists are explicitly declared by placing an exclamation mark (`!`) before the closing square bracket (`[ ... !]`).

```Clean
// Language: Clean

x :: [ Int !] 
x =  [ 1, 2, 3 !]
```

Strict lists are explicitly declared by placing an exclamation mark (`!`) after and before the square bracket (`[! ... !]`).

```Clean
// Language: Clean

x :: [! Int !]
x =  [! 1, 2, 3 !]
```

Unboxed head strict lists are explicitly declared by placing a hash symbol (`#`) after the opening square bracket (`[ # ... ]`).

```Clean
// Language: Clean

x :: [ # Int ]
x =  [ # 1, 2, 3 ]
```

Unboxed strict lists are explicitly declared by placing a hash symbol (`#`) and an exclamation mark (`!`) after the opening square bracket (`[ #! ... ]`).

```Clean
// Language: Clean

x :: [ #! Int ]
x =  [ #! 1, 2, 3 ]
```

Overloaded lists are explicitly declared by placing a vertical (`|`) bar after the opening square bracket (`[ | ... ]`).

```Clean
// Language: Clean

x :: [ | Int ]
x =  [ | 1, 2, 3 ]
```



