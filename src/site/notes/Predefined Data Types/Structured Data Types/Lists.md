---
{"dg-publish":true,"permalink":"/predefined-data-types/structured-data-types/lists/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-13T22:30:13.795+02:00"}
---


# Lists

Lists can contain an infinite number of elements. 
Elements of a list must be of the same type. 

For built-in functions on list, see [[Appendix A/StdList\|StdList]], [[Appendix A/StdCharList\|StdCharList]], and [[Appendix A/StdOrdList\|StdOrdList]] module for additional information.

## List Type Declaration

In addition to the list type, the element type must be declared by placing it inside or after the list type.

Lazy lists are explicitly declared with square brackets (`[ ... ]`).

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 2, 3 ]

y :: [ ] Int
y =  [ 1, 2, 3 ]
```

## List Literals

List literals refer to the explicit enumeration of their elements, since structured data types do not have a "literal" form.

A simple list with one element.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 ]
```

Elements are comma (`,`) separated.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 2, 3 ]
```

A colon (`:`) is valid in list construction.

It can be seen as a pseudo right-associated "operator" which accepts an element on its left, and another list on its right.
It attaches the element to the front of the list.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 : [ 2, 3 ] ]

y :: [ Int ]
y =  [ 1 : [ 2 : [ 3 : [] ] ] ]

z :: [ Int ]
z =  [ 1 : 2 : 3 : [] ]
```

Commas and colons can be used together.

```Clean
// Language: Clean

x :: [ Int ] 
x =  [ 1, 2 : [ 3 ] ]

y :: [ Int ]
y =  [ 1, 2, 3 : [] ]
```

A notation for constructing a list of characters is also provided.

```Clean
// Language: Clean

x :: [ Char ]
x =  ['a', 'b', 'c']

y :: [ Char ] 
y =  [ 'abc' ]

z :: [ Char ]
z =  [ 'ab', 'c' ]
```

## List Comprehensions

All type of lists can be constructed using list comprehension.

See [[Predefined Data Types/Structured Data Types/Comprehensions\|Comprehensions]] for additional information.

## Dot-Dot Expressions

Dot-Dot expressions require `StdEnum` module from the Standard Environment.
They provide an alternative way to implicitly construct a list, but they cannot be used as a pattern.

There are four variants.

The first variant constructs infinite lists with a step of one.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. ] // [ 1 ,2 ,3 , ... ]
```

The second variant constructs infinite lists with custom step.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. ]  // [ 1, 3, 5, ... ]

y :: [ Int ]
y =  [ 2, 0 .. ]  // [ 2, 0, -2, ... ]
```

The third variant constructs finite lists with a step of one.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. 9 ]  // [ 1, 2, ..., 9 ]

y :: [ Int ]
y =  [ 0 .. 0 ]  // [ 0 ]
```

The last variant constructs finite lists with custom step.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 6 ]  // [ 1, 3, 5 ]

y :: [ Int ]
y =  [ 5, 3 .. 0 ]  // [ 5, 3, 1 ]
```

When constructing a list using the fourth variant, if an element would go "out of bound", it will not be included.

## Using List Literal as Pattern

Example A:

```Clean
// Language: Clean

exampleA :: [ Int ] -> Bool
exampleA    [ x ]   =  True
exampleA    _       =  False
```

The function `exampleA` returns `True` if it is called with a list of exactly one element.

Example B:

```Clean
// Language: Clean

exampleB :: [ Int ]     -> Bool
exampleB    [ x, y, z ] =  True
exampleB    _           =  False
```

The function `exampleB` returns `True` if it is called with a list of exactly three elements.

There are many equivalent variants to the function `exampleB`.

One variant is obtained by using colons instead of commas.

```Clean
// Language: Clean

exampleB :: [ Int ]            -> Bool
exampleB    [ x : y : z : [] ] =  True
exampleB    _                  =  False
```

Another variant is obtained by using a combination of commas and colons.

```Clean
// Language: Clean

exampleB :: [ Int ]           -> Bool
exampleB    [ x , y : [ z ] ] =  True
exampleB    _                 =  False
```

Example C:

```Clean
// Language: Clean

exampleC :: [ T ]      -> Bool
exampleC    [ x : ls ] =  True
exampleC    _          =  False
```

The function `exampleC` returns true if it is called with a list of at least one element.

Example D:

```Clean
// Language: Clean

exampleD :: [ Int ]          -> Bool
exampleD    [ x, y, z : ls ] =  True
exampleD    _                =  False
```

The function `isLenGtThree` yields true if it is called with a list with at least three elements.

Example E:

```Clean
// Language: Clean

exampleE :: [ Int ] -> Bool
exampleE    [ 1 ]   =  True
exampleE    _       =  False
```

The function `isLenOne` yields true if it is called with a list of exactly one element.
And that element must be one.

Example F:

```Clean
// Language: Clean

exampleF :: [ Int ]     -> Bool
exampleF    [ 1, y, z ] =  True
exampleF    _           =  False
```

The function `exampleF` returns true if it is called with a list of exactly three elements.
The first element of the list must be 1.

## Labelling List Pattern

Lists are lazy by default, but other variants are:
- head strict, 
- spine strict, 
- strict, 
- head strict unboxed, and
- strict unboxed. 

These variants are considered different type with unique time and space properties.
Functions defined on one type of list cannot be applied to another. 
However, overloaded functions can be introduced, which can be used on any type of list.


Head strict lists are explicitly declared by placing an exclamation mark after the opening square bracket (`[! ... ]`).

```Clean
// Language: Clean

x :: [! Int ]
x =  [! 1, 2, 3 ]

y :: [! ] Int 
y =  [! 1, 2, 3 ]
```

Tail strict lists are explicitly declared by placing an exclamation mark before the closing square bracket (`[ ... !]`).

```Clean
// Language: Clean

x :: [ Int !] 
x =  [ 1, 2, 3 !]

y :: [ !] Int
y =  [ 1, 2, 3 !]
```

Strict lists are explicitly declared by placing an exclamation mark after and before the square bracket (`[! ... !]`).

```Clean
// Language: Clean

x :: [! Int !]
x =  [! 1, 2, 3 !]

y :: [! !] Int
y =  [! 1, 2, 3 !]
```

Unboxed head strict lists are explicitly declared by placing a hash symbol after the opening square bracket (`[ # ... ]`).

```Clean
// Language: Clean

x :: [ # Int ]
x =  [ # 1, 2, 3 ]

y :: [ # ] Int
y =  [ # 1, 2, 3 ]
```

Unboxed strict lists are explicitly declared by placing a hash symbol and an exclamation mark after the opening square bracket (`[ #! ... ]`).

```Clean
// Language: Clean

x :: [ #! Int ]
x =  [ #! 1, 2, 3 ]

y :: [ #! ] Int 
y =  [ #! 1, 2, 3 ]
```
