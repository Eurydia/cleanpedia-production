---
{"dg-publish":true,"permalink":"/functions/function-implementation-rules/","created":"2023-06-20T23:37:36.404+07:00","updated":"2023-07-23T03:57:42.072+07:00"}
---


> [!info] Prerequisites
> To properly understand each implementation rule, understanding of function signatures is required.
> 
> See [[Functions/Function Signature\|Function Signature]].


# Function Implementation Rules

Implementations of a function must follow these rules.
Violation can result in a compile-time error.

Implementations of a function must:
- be grouped together,
- share a single function signature, and
- share a single identifier.

In addition, the identifier must be unique from other identifiers.

## Example

Let's investigate the rules further starting with the first.

> [!quote]
> Implementations of a function must be grouped together.

When a function is defined with multiple function implementations, nothing can be placed between them, except comments.

The function definition of `double` will serve as a benchmark.

```Clean
// Language: Clean

double 0 = 0
double x = x * 2
```

The definition of `double` are textually grouped together.

Comments can be placed between two function implementations without violating the rule.

```Clean
// Language: Clean

double 0 = 0
// So there's this one book
double x = x * 2
```

With a benchmark in place, let's see what happens when this rule is violated.

```Clean
// Language: Clean

badDouble 0 = 0
1 + 2
badDouble x = x * 2
```

It is clear that the definition of `badDouble` is invalid.
An expression (`1 + 2`) is separating its function implementations.

On an interesting note, if a function definition consists of only one function implementation, this rule would never be violated.

> [!quote]
> Functions implementation must share a single function signature.

To avoid confusion, let's define a new bench mark function called `triple`.

```Clean
// Language: Clean

triple 0 = 0
triple x = x * 3 
```

Both function implementations share a single function signature, which is 

---