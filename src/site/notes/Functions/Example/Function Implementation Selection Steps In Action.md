---
{"dg-publish":true,"permalink":"/functions/example/function-implementation-selection-steps-in-action/","created":"2023-06-24T16:07:50.699+07:00","updated":"2023-06-24T16:42:55.355+07:00"}
---


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

> [!warning]
> Changing implementation order of a function affects its behavior.

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
