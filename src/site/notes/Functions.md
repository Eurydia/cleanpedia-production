---
{"dg-publish":true,"permalink":"/functions/","created":"2023-06-20T19:38:59.204+02:00","updated":"2023-06-21T10:40:29.546+02:00"}
---


# Functions

## Defining a Function

A simple function consists of one function implementation.

See [[functions/Implementing a Function\|Implementing a Function]].

Optionally, a function definition can be explicitly typed to increase readability.

See [[functions/Typing a Function\|Typing a Function]].

---

## Calling a Function

To better demonstrate, let's define two functions with different arities.

An arity-one function called `exampleA` and an arity-two function called `exampleB`.
The body of each function does not matter.

```Clean
// Language: Clean

exampleA param = ...

exampleB paramA paramB = ...
```

A simple function call is made by placing the function name in front of its arguments.
Parentheses are not needed.

```Clean
// Language: Clean

exampleA arg
```

Arguments of a function call are space-separated.

```Clean
// Language: Clean

exampleB argA argB
```

Functions with multiple parameters can be curried.

### Currying a Function

Currying transforms a function that takes multiple arguments into an a series of intermediate functions.
These intermediate functions take a single argument and returns another intermediate function which accepts further arguments.
Eventually, the original function receives the rest of its arguments and evaluates.

To demonstrate, let's imagine an arity-three function called `exampleC`.
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

With currying `exampleC` can be called with fewer arguments than required.

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

```Clean
// Language: Clean

exampleC argA  // __intermediateB
```

> [!note]
> The arguments are always given from left to right.

---

## Constants

---

## Operators

---