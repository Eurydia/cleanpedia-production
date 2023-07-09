---
{"dg-publish":true,"permalink":"/functions/","created":"2023-06-20T19:38:59.204+02:00","updated":"2023-07-09T10:37:04.515+02:00"}
---


## Defining a Function

A simple function consists of one [[Functions/Function Implementation\|function implementation]].

Optionally, a function definition can be [[Functions/Typing a Function\|explicitly typed]] to increase readability.

---

## Calling a Function

A function call can be made by placing a function identifier in front of a sequence of space-separated arguments without parentheses.

A control form a function call is written as follows.

```Clean
// Language: Clean

identifier argSeq
```

To better demonstrate, let's define an arity-one function called `exampleA` and an arity-two function called `exampleB`.
The body of each function does not matter.

```Clean
// Language: Clean

exampleA param = ...

exampleB paramA paramB = ...
```

To call `exampleA`, place its name in front of an argument.

```Clean
// Language: Clean

exampleA arg
```

To call `exampleB`, place its name in front of a sequence of space-separated arguments.

```Clean
// Language: Clean

exampleB argA argB
```

---

## Partially Calling a Function

A function, which takes multiple arguments, can be called with fewer arguments than required.

```Clean
// Language: Clean

exampleB argA  // huh?
```

More precisely, this type of function call is known as [currying](https://en.wikipedia.org/wiki/Currying).

Currying transforms a function, which takes multiple arguments, into a series of intermediate functions.

Each intermediate function accepts a single argument and returns another intermediate function, which accepts further arguments.
Eventually, the original function receives the rest of its arguments and evaluates.

To demonstrate, let's define an arity-three function called `exampleC`.
The body of the function does not matter.

```Clean
// Language: Clean

exampleC paramA paramB paramC = ...
```

Normally, it requires three arguments to call `exampleC`.

```Clean
// Language: Clean

exampleC argA argB argC
```

Since `exampleC` takes multiple arguments, it can be curried.

```Clean
// Language: Clean

exampleC argA
```

Internally, the compiler generates intermediate functions as discussed earlier.

```Clean
// Language: Clean

__intermediateA argA = __intermediateB
where
    __intermediateB argB = __intermediateC
    where
        __intermediateC argC = exampleC argA argB argC
```

The function call is equivalent to the second step.

In other word, `exampleC` is composed of three indirect function calls, instead of one direct call.

```Clean
// Language: Clean

(((__intermediateA argA) argB) argC)
```

> [!note]
> Arguments cannot be skipped and always given from left to right.

---

## Constants

[[Appendix A/StdInt\|StdInt]]

---

## Operators

---