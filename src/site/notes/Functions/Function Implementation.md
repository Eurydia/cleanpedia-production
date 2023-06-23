---
{"dg-publish":true,"permalink":"/functions/function-implementation/","created":"2023-06-20T18:37:36.405+02:00","updated":"2023-06-23T22:51:36.276+02:00"}
---


Let's see what a function implementation looks like.

A control form of a function implementation is written as follows.

```markdown
identifier paramSeq = body
```

More precisely, a function implementation consists of three components.

| Component    | Description                        |
| ------------ | ---------------------------------- |
| `identifier` | A function name.                   |
| `paramSeq`   | A fixed-length parameter sequence. |
| `body`       | An expression to be evaluated.     |

Each parameter of a function can be a simple variable name, but it can be replaced by a literal as well.
When a literal is used as a parameter, it invokes a special behavior, which is later discussed in this page.

If a parameter represents a [[Built-in Data Types/Structured Data Types\|structured data type]], it can be replaced by a [[Functions/Destructuring Patterns\|destructuring pattern]].

Furthermore, we can deduce from the control from that a function implementation has ownership over one body.

However, by introducing [[Functions/Guarded Bodies\|guarded bodies]], a function implementation can have ownership over multiple guarded bodies, instead of one ordinary body.

Function implementations must also follow [[Functions/Function Implementation Rules\|specific rules]].
Violation of these rules results in a compile-time error.


---