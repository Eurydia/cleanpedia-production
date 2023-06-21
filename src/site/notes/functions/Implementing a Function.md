---
{"dg-publish":true,"permalink":"/functions/implementing-a-function/","created":"2023-06-20T18:37:36.405+02:00","updated":"2023-06-20T22:42:36.605+02:00"}
---


# Implementing a Function

To implement  a function, we need to know what a function implementation looks like first.

## Control Forms of a Function Implementation

A control form of a function implementation is written as follows.

```
// Language: Clean
 
identifier paramSeq = body
```

More specifically, a function implementation consists of three components.

| Component    | Description                                                                             |
| ------------ | --------------------------------------------------------------------------------------- |
| `identifier` | The function name.                                                                      |
| `paramSeq`   | A fixed sequence of space-separated parameters. They can be referenced by `body`. |
| `body`       | An expression. It is evaluated when the function call is made.                          |

### Extending Parameters 

A parameter of a function can be a simple variable name, a literal.
When a literal is used as a parameter, it invokes a special behavior which is discussed later part of this page.

If a parameter represents a structured datatype, it can be replaced by a destructuring pattern.
See [[functions/Destructuring Patterns\|Destructuring Patterns]].

### Extending Expression

A function implementation has ownership over one expression.

By introducing [[functions/Guarded Expressions\|guarded expressions]], a function implementation can have ownership over multiple guarded expressions, instead of one ordinary expression.

---

## Function Implementation Rules

Function implementations must follow [[functions/Implementation Rules\|specific rules]].
Violation of these rules results in a compile-time error.

---

## Selecting a Function Implementation To Be Evaluated

A function definition often contains multiple function implementations.
This is important since of all function implementation, only one can be selected.

> [!question]
> How do we determine which function implementation should be selected when there more than one?

The answer to the posted question is as follows.

> [!success]
> Implementations are tried in descending order, and the first implementation, whose parameters match with every argument, is selected.

To demonstrate, a function called `safeDivide` is described as follows:
- accepts two integers as arguments, 
- returns the result of division, and
- returns zero when the given denominator is 0.

```
// Langauge: Clean

safeDivide 6 2  // 3
safeDivide 2 0  // 0
```

It can be defined using two function implementations.

```Clean
safeDivide m 0 = 0
safeDivide m n = m / n
```

Let's call `safeDivide` with 9 and 6 and investigate.

```Clean
safeDivide 9 6  // ?
```

Apply the rule to see which function implementation is selected.

The first function implementation is tried, and the first parameter matches the first argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |

The second parameter does not match the second argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `0`       | `6`      | Fail   |

The first function implementation is not selected.

Next, second is tried, and both parameters match both arguments.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `n`       | `6`      | Pass   |

The second function implementation is selected.

The result is obtained from the expression of the second function implementation, which is `m / n`.
It evaluates to 1.

```
// Language: Clean

safeDivide 9 6  // 1
```

Let's call `safeDivide` with 9 and 0 instead.

```
// Language: Clean

safeDivide 9 0
```

The first function implementation is tried, and the first parameter matches the first argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |

The second parameter matches the second argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `m`       | `9`      | Pass   |
| 2      | `0`       | `0`      | Pass   |

The first function implementation is select.

The result is obtained from the expression of the first function implementation, which is 0.

```
// Language: Clean

safeDivide 9 0  // 0
```

> [!important]
> This behavior does not perform equality checks.

### Importance of Implementation Order

If implementation order is changed, `safeDivide` would have unintended behaviors.
To demonstrate, the implementation order of `safeDivide` is changed.

```
// Language: Clean

safeDivide m n = m / n
safeDivide m 0 = 0
```

The second function implementation is never reached even if `safeDivide`  is called with 0.

```
// Language: Clean

safeDivide 9 0  // Uh oh
```

### No Valid Candidate for Selection

If no function implementation is a valid candidate for selection, the function definition is [[functions/Partial Functions\|partial]] and the function call results in a run-time error.

---