---
{"dg-publish":true,"permalink":"/functions/guarded-bodies/","created":"2023-06-20T18:37:36.403+02:00","updated":"2023-06-23T23:02:37.760+02:00"}
---


Guarded bodies allows a function implementation to have multiple bodies.

A control function implementation with one guarded body is written as follows.

```markdown
identifier paramSeq
| guard = body
```

A guarded body consists of two components.

| Component    | Description                                        |
| ------------ | -------------------------------------------------- |
| `identifier` | A function name.                                   |
| `paramSeq`   | A fixed-length space-separated parameter sequence. |
| `guard`      | A Boolean expressions.                             |
| `body`       | An expression to be evaluated.                     |

A control function implementation with three guarded body is written as follows.

```markdown
identifier paramSeq
| guardA = bodyA
| guardB = bodyB
| guardC = bodyC
```

A control function implementation with one guarded body and a nested guarded body is written as follows.

```markdown
identifier paramSeq
| guardA
    | guardAA = bodyAA
```

---

## Guarded Body Rules

Guarded bodies extend a function implementation.
As a result, they must follow [[Functions/Guarded Body Rules\|certain rules]].

Violation of such rules results in a compile-time error.

---

## Selecting a Guarded Body To Be Evaluated

A function implementation can contain multiple guarded bodies.
When the function is called, only one guarded body can be selected.

To determine which guarded body should be selected for evaluation, a procedure is written as follows.

> [!quote]
> *Guarded bodies are only tried if their function implementation is selected.*
> *They are tried in descending order and the first guard to yield true is evaluated.*

To demonstrate, a function called `signum` is described as follows:
- accepts one integer, and
- returns the sign of that integer.

```Clean
// Language: Clean

signum  0  //  0
signum -2  // -1
signum  4  //  1
```

For the sake of simplicity, it will be defined with two implementation which has two guarded bodies.

```
// Language: Clean

signum 0 =  0
signum n
| n >  0 =  1
| n <  0 = -1
```

Let's call signum with 0 to investigate this procedure.

```
// Language: CLean

signum 0  // ?
```

The function is defined with two function implementations, so need to  [[Functions/Function Implementation#Selecting a Function Implementation To Be Evaluated\|determine which one is selected]].

The first function implementation is tried.
The parameter matches the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `0`       | `0`      | Pass   |

The first function implementation is selected.

The result is obtained from the expression of the first function implementation, which is 0.

```Clean
// Language: Clean

signum 0  // 0
```

> [!note]
> The guarded bodies of the second function implementation are not tried because the function implementation, which they belong to, is not selected.

Let's investigate a different scenario by calling `signum` with -10.

```Clean
// Language: Clean

signum -10  // ?
```

Again, we need to determine which function implementation is selected.

The first function implementation is tried. 
The parameter does not match the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `0`       | `-10`    | Fail   |

The first function implementation is not selected.

The second function implementation is tried.
The parameter matches the argument.

| Pair # | Parameter | Argument | Result |
| ------ | --------- | -------- | ------ |
| 1      | `n`       | `-10`    | Pass   |

The second function implementation is selected.
Next we need to determine which guarded body should be selected.

The first guarded body is tried.
The guard yields false.

| Guard  # | Guard   | Expression | Result |
| -------- | ------- | ---------- | ------ |
| 1        | `n > 0` | `-10 > 0`  | Fail   |

The first guarded body is not selected.

The second guarded body is tried.
The guard yields true.

| Guard  # | Guard   | Expression | Result |
| -------- | ------- | ---------- | ------ |
| 1        | `n > 0` | `-10 > 0`  | Fail   |
| 2        | `n < 0` | `-10 < 0`  | Pass   |

The second guarded body is selected.

The result is obtained from the expression of the second guarded body of the second function implementation, which is -1.

```Clean
// Language: Clean

signum -10 // -1
```