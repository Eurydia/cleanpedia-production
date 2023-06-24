---
{"dg-publish":true,"permalink":"/functions/function-implementation-selection/","tags":["function-implementation","function-implementation-selection"],"created":"2023-06-23T22:49:38.415+02:00","updated":"2023-06-24T11:17:57.949+02:00"}
---


# Function Implementation Selection

A function can be defined with multiple function implementations.
Only one of those function implementations can be selected.

> [!important]
> Implementations are tried in descending order.
> The first implementation, whose parameters match with every argument, is selected.

Jump to [[Functions/Function Implementation Selection#Function Implementation Selection\|#Function Implementation Selection#Demonstration Function Implementation Selection Procedure]] to see the steps in action.

> [!warning]
> When no function implementation can be selected, the function call results in a run-time error 

Jump to  

## Demonstration: Function Implementation Selection Procedure

To demonstrate, a function called `safeDivide` is described as follows:
- accepts two integers as arguments, 
- returns the result of division, and
- returns zero when the given denominator is 0.

```Clean
// Langauge: Clean

safeDivide 6 2  // 3
safeDivide 2 0  // 0
```

It can be defined using two function implementations.

```Clean
// Langauge: Clean

safeDivide m 0 = 0
safeDivide m n = m / n
```

Let's call `safeDivide` with 9 and 6 to investigate.

```Clean
// Langauge: Clean

safeDivide 9 6  // ?
```

Follow the procedure to determine which function implementation should be selected.

The first function implementation is tried.
The first parameter matches the first argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |

The second parameter does not match the second argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `0`       | `6`      | Fail   |

The first function implementation is not selected.

The second function implementation is tried.
Both parameters match both arguments.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `n`       | `6`      | Pass   |

The second function implementation is selected.

The result is obtained from the body of the second function implementation, which is `m / n`.
It evaluates to 1.

```
// Language: Clean

safeDivide 9 6  // 1
```

Let's call `safeDivide` with 9 and 0.

```
// Language: Clean

safeDivide 9 0  // ?
```

The first function implementation is tried.
The first parameter matches the first argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |

The second parameter matches the second argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `0`       | `0`      | Pass   |

The first function implementation is select.

The result is obtained from the body of the first function implementation, which is 0.

```
// Language: Clean

safeDivide 9 0  // 0
```

If implementation order has been changed, `safeDivide` would have unintended behaviors.
To demonstrate, let's swap the implementation order of `safeDivide` around.

```Clean
// Language: Clean

safeDivide m n = m / n
safeDivide m 0 = 0
```

The second function implementation is never reached even if `safeDivide`  is called with 0.

```Clean
// Language: Clean

safeDivide 9 0  // Uh oh
```

---

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
