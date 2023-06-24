---
{"dg-publish":true,"permalink":"/functions/function-implementation-selection/","created":"2023-06-23T22:49:38.415+02:00","updated":"2023-06-24T11:39:23.369+02:00"}
---


#function #function-implementation #function-implementation-selection 

# Function Implementation Selection

When a function is defined, exactly one function implementation must be selected.
The body of the function implementation is evaluated and returned.

> [!important]
> Implementations are tried in descending order.
> The first implementation, whose parameters match with every argument, is selected.

See the steps in [[Functions/Example/Function Implementation Selection Steps In Action\|action]].

> [!warning]
> When no function implementation can be selected, the function call results in a run-time error 


## Demonstration: No Function Implementation Is Selected

To demonstrate, a function called `isPrime` is described as follows:
- accepts one integer, and
- checks whether it is prime or not.

```Clean
// Language: Clean

isPrime 1  // False
isPrime 2  // True
isPrime 3  // True
```

The function is crudely defined for the sake of demonstration.

```Clean
// Language: Clean

isPrime 1 = False
isPrime 2 = True
isPrime 3 = True
```

It behaves as intended but only with integers between 1 and 3, inclusive.

Let's investigate by calling `isPrime` with 6.

```Clean
// Language: Clean

isPrime 6  // ?
```

The first function implementation is tried.
The parameter does not match the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `1`       | `6`      | Fail   |

The first function implementation is not selected.

The second function implementation is tried.
The parameter does not match the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `2`       | `6`      | Fail   |

The second function implementation is not selected.

The third function implementation is tried.
The parameter does not match the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `3`       | `6`      | Fail   |

The third function implementation is not selected.

We have exhausted every implementation of `isPrime` but none of them was selected.
Since a result cannot be obtained from any function implementation, it defaults to a run-time error.

```Clean
// Language: Clean

isPrime 6  // Uh oh
```
