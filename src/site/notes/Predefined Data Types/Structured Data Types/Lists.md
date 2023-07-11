---
{"dg-publish":true,"permalink":"/predefined-data-types/structured-data-types/lists/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-11T14:16:45.970+02:00"}
---


# Lists

Lists can contain an infinite number of elements. 
Elements of a list must be of the same type. 

Lists are lazy by default, but they can be defined as:
- head strict, 
- spine strict, 
- strict, 
- head strict unboxed, and
- strict unboxed. 

Lazy, strict, and unboxed lists are considered different type.
They have unique time and space properties.

Because these lists are of different type, functions defined on one type of list cannot be applied to another. 
However, overloaded functions can be introduced, which can be used on any type of list.

For built-in functions on list, see [[Appendix A/StdList\|StdList]], [[Appendix A/StdCharList\|StdCharList]], and [[Appendix A/StdOrdList\|StdOrdList]] module for additional information.

## List Type Declaration

The element type must be declared in addition to the list type.

Lazy lists are explicitly declared with square brackets (`[ ... ]`).

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 2, 3 ]
```

Head strict lists are explicitly declared by placing an exclamation mark after the opening square bracket (`[ ! ... ]`).

```Clean
// Language: Clean

x :: [ ! Int ]
x =  [ ! 1, 2, 3 ]
```

Tail strict lists are explicitly declared by placing an exclamation mark before the closing square bracket (`[ ... ! ]`).

```Clean
// Language: Clean

x :: [ Int ! ]
x =  [ 1, 2, 3 ! ]
```

Strict lists are explicitly declared by placing an exclamation mark after and before the square bracket (`[ ! ... ! ]`).

```Clean
// Language: Clean

x :: [ ! Int ! ]
x =  [ ! 1, 2, 3 ! ]
```

Unboxed head strict lists are explicitly declared by placing a hash symbol after the opening square bracket (`[ # ... ]`).

```Clean
// Language: Clean

x :: [ # Int ]
x =  [ # 1, 2, 3 ]
```

Unboxed strict lists are explicitly declared by placing a hash symbol and an exclamation mark after the opening square bracket (`[ #! ... ]`).

```Clean
// Language: Clean

x :: [ #! Int ]
x =  [ #! 1, 2, 3 ]
```

## List Literals

It does not make much sense for a structured to have a "literal" form.
For the sake of uniformity, list literals refer to the explicit enumeration of its elements.

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

A colon (`:`) is used to construct a new list from an existing one.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 , 2 : [ 3 ] ]

y :: [ Int ]
y =  [ 1 : [ 2, 3 ] ]
```

Multiple colons can be used to construct a list.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 : [ 2 : [ 3 : [] ] ] ]

y :: [ Int ]
y =  [ 1 : 2 : 3 ]
```

A special notation for constructing a list of characters is also provided.

```Clean
// Language: Clean

x :: [ Char ]
x =  ['a', 'b', 'c']

y :: [ Char ] 
y =  [ 'abc' ]
```

## List Comprehensions

List comprehensions provide an alternative way to implicitly construct a list, but they cannot be used as a pattern.

They construct a list using an existing list.

```Clean
// Language: Clean

newList :: [ T ]
newList =  [ el \\ el <- ls ]
```

It is equivalent to a `for` loop.

```Python
# Language: Python

newList: list[any] = []
for el in ls:
	newList.append(el)
```

They can construct a list from an existing array, but a different arrow must be used.

```Clean
// Language: Clean

newList :: [ T ]
newList =  [ el \\ el <-: arr ]
```

A comma (`,`) is used to join generators.
The right-most generator is the fastest.

```Clean
// Language: Clean

newList :: [ ( T, K ) ]
newlist =  [ ( elx, ely ) \\ elx <- lsx , ely <- lsy ]
```

It is equivalent to `for` loops with left-to-right nesting.

```Python
# Language: Python

newList: list[tuple[any, any]] = []
for elx in lsx:
	for ely in lsy:
		newList.append((elx, ely))
```

An ampersand (`&`) is used to zip generators.
Iteration stops as soon as one generator runs out of element.

```Clean
// Language: Clean

newList :: [ ( T, K ) ]
newList =  [ ( elx, ely ) \\ elx <- lsx & ely <- lsy ]
```

It is equivalent to using `zip()` in `for` loop.

```Python
# Language: Python

newList: list[tuple[any, any]] = []
for elx, ely in zip(lsx, lsy):
	newList.append((elx, ely))
```

A condition can be introduced after each generator.

```Clean
// Langauge: Clean

newList :: [ T ]
newList =  [ elx \\ elx <- lsx | pred elx ]
```

It is equivalent to an `if` block in `for` loop.

```Python
# Language: Python

newList: list[any] = []
for elx in lsx:
	if not pred(elx):
		continue
	newList.append(elx)
```

If two generators are joined with comma, each generator can have its own condition.

```Clean
// Langauge: Clean

newList :: [ ( T, K ) ]
newList =  [ ( elx, ely ) \\ elx <- lsx | predx elx , ely <- lsy | predy ely ]
```

It is equivalent to an`if` block to each nested `for` loop.

```Python
# Language: Python

newList: list[tuple[any, any]] = []
for elx in lsx:
	if not predx(elx):
		continue
	for ely in lsy:
		if not predy(ely):
			continue
		newList.append((elx, ely))
```

If two generators are joined with ampersand, they will share a condition.

```Clean
// Langauge: Clean

newList :: [ ( T, K ) ]
newList =  [ ( elx, ely ) \\ elx <- lsx | predx elx & ely <- lsy | predy ely ]  // compile-time error
```



## Dot-Dot Expressions

Dot-Dot expressions require `StdEnum` module from the Standard Environment.
They provide an alternative way to implicitly construct a list, but they cannot be used as a pattern.

There are four variants.

The first variant constructs infinite lists with a step of one.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. ]
// Equivalent to [ 1 ,2 ,3 , ... ]
```

The second variant constructs infinite lists with custom step.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. ]  
// Equivalent to [ 1, 3, 5, ... ]

y :: [ Int ]
y =  [ 2, 0 .. ]
// Equivalent to [ 2, 0, -2, ... ]
```

The third variant constructs finite lists with a step of one.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1 .. 9 ]
// Equivalent to [ 1, 2, ..., 9 ]

y :: [ Int ]
y =  [ 0 .. 0 ] 
// Equivalent to [ 0 ]
```

The last variant constructs finite lists with custom step.

```Clean
// Language: Clean

x :: [ Int ]
x =  [ 1, 3 .. 6 ]  
// Equivalent to [ 1, 3, 5 ]

y :: [ Int ]
y =  [ 5, 3 .. 0 ]
// Equivalent to [ 5, 3, 1 ]
```

When constructing a list using the fourth variant, if an element would go "out of bound", it will be discarded.

## Using List Literal as Pattern

Lists can be specified as patterns as follow:

```
// Language: Clean

getFst :: [T]       -> T
getFst    [x, y, z] =  x

getSnd :: [T]       -> T
getSnd    [x, y, z] =  y

getThd :: [T]       -> T
getThd    [x, y, z] =  z
```

The results of these function calls are as expected:

```
// Language: Clean

getFst [1, 2, 3]  // 1
getSnd [1, 2, 3]  // 2
getThd [1, 2, 3]  // 3
```

However, they will result in a run-time error if it is invoked with a list which does not have exactly three elements.

```
// Language: Clean

getFst [1]          // NOT OK :(
getSnd [1, 2]       // NOT OK :(
getThd [4, 3, 2, 1] // NOT OK :(
```

To remedy this issue, an addition element should be introduce.

```
// Language: Clean

getFstAny :: [T]     -> T
getFstAny    [x : r] =  x

getSndAny :: [T]        -> T
getSndAny    [x, y : r] =  y

getThdAny :: [T]           -> T
getThdAny    [x, y, z : r] =  z
```

The right-hand side of colon ($:$) matches with any number of elements, including zero.
It is worth noting that $r$ is always a list.

```
// Language: Clean

getFstAny [1]           // x = 1
                        // r = []

getFstAny [1, 2]        // x = 1
                        // r = [2]

getFstAny [4, 3, 2, 1]  // x = 4
                        // r = [3, 2, 1]
```

However, the second function still requires the list to have at least two elements.

```
// Language: Clean

getSndAny [1]           // NOT OK :(

getSndAny [1, 2]        // x = 1
                        // y = 2
                        // r = []

getSndAny [4, 3 ,2 ,1]  // x = 4
                        // y = 3
                        // r = [2, 1]
```

Similarly, the third function requires a list with at least three elements.

```
// Language: Clean

getThdAny [1]           // NOT OK :(

getThdAny [1, 2]        // NOT OK :(

getThdAny [4, 3, 2, 1]  // x = 4
                        // y = 3
                        // z = 2
                        // r = [1]
```
