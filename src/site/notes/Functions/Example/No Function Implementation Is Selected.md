---
{"dg-publish":true,"permalink":"/functions/example/no-function-implementation-is-selected/","created":"2023-06-24T11:42:18.895+02:00","updated":"2023-06-24T11:46:22.991+02:00"}
---


# No Function Implementation Is Selected

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

---