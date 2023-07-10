---
{"dg-publish":true,"permalink":"/predefined-data-types/structured-data-types/list/","created":"2023-07-03T09:26:06.677+02:00","updated":"2023-07-10T14:30:07.623+02:00"}
---


# List

**Type annotation**:
`[Int]`,
`[Char]`,
`[T]`,
et cetera.

#### Constructing Lists

A list can be constructed in many ways, but there are three primary methods.
The simplest way to construct a list is to explicitly write elements between a pair of square brackets (`[..]`).

```
// Language: Clean

[1]
```

Elements are comma (`,`) separated.

```
// Language: Clean

[1, 2, 3]
```

A list may be appended to the end of another list using colon (`:`).

```
// Language: Clean

[1 : [2, 3]]
```

The outer list (`[1 : ..]`) is constructed by appending the inner list (`[2, 3]`) to the end.

As a result, this method of list construction has a wide varieties which can be written.

```
// Language: Clean

[1 : [2 : [3 : []]]]
[1, 2 : [3]]
[1, 2, 3 : []]
```

Secondly, a list may be implicitly constructed with `dot-dot` expression, and a control expression may be written as follows.

```
// Language: Clean

[initial..]
```

An infinite list is generated from `initial`, which represents the starting value, subsequent elements are incremented by one.

```
// Language: Clean

[1..]  // [1, 2, 3, 4, ...]
```

To create a finite list, an `end` value may be specified.

```
// Language: Clean

[initial..end]
```

By adding `end`, elements are generated only up to `end` it self.

```
// Language: Clean

[1..5]  // [1, 2, 3, 4, 5]
```

In addition, `next` value may be specified to change how subsequent elements are generated.

```
// Language: Clean

[initial, next..end]
```

Each step is computed from `next - initial`.
If the next element is strictly greater than `end`, it will not be included.
It is possible to generate a list which is in descending order.

```
// Language: Clean

[1, 3..9]  // [1, 3, 5, 7, 9]
[5, 4..1]  // [5, 4, 3, 2, 1]
```

By omitting `end`, an infinite list with step may be generated.

```
// Language: Clean

[initial, next..]
```

The expression results in an infinite list.

```
// Language: Clean

[1, 3..]  // [1, 3, 5, 7, 9, ...]
[5, 4..]  // [5, 4, 3, 2, 1, ...]
```

It should be noted that `dot-dot` expressions requires `StdEnum` module.

And lastly, a list may be constructed with comprehension.

```
// Language: Clean

// extract from a list
[el \\ el <- list]

// extract from an array
[el \\ el <-: array]

// cartesian product
[(x, y) \\ x <- xs , y <- ys]

// pair-wise zip
[(x, y) \\ x <- xs & y <- ys]

// same as filter
[x \\ x <- xs | P x]

// nested
[(x, y) \\ x <- xs, y <- [1..x]]
```

A special notation for constructing a list of characters is also provided:

```
// Language: Clean

['a', 'b', 'c']
['abc']
['ab','c']
```

A list may contain an infinite number of elements, but elements must have the same type.

More information about built-in operations and functions on lists can be found on:

- [Appendix A: StdCharList](Appendix%20A/stdcharlist.md),
- [Appendix A: StdList](Appendix%20A/stdlist.md), and
- [Appendix A: StdOrdList](Appendix%20A/stdordlist.md).

**List patterns**

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
