---
{"dg-publish":true,"permalink":"/functions/function-implementation-rules/","created":"2023-06-20T18:37:36.404+02:00","updated":"2023-06-24T16:40:39.150+02:00"}
---


# Function Implementation Rules

When a function is defined, its function implementations must follow these rules.
Violation results in a compile-time error.

Implementations of a function must:
- be grouped together,
- share a single identifier, and
- share a single signature.

> [!info]- You have encountered an **example marker**.
> Proceeding sections aim to provide more explanation.

Let's investigate the rules further starting with the first.

> [!quote]
> Implementations of a function must be grouped together.

What does the rule implies exactly?

When a function is defined with multiple function implementations, nothing can be placed between them, except comments.

```Clean
// Language: Clean

double 0 = 0
double x = x * 2
```

Function implementations of `double` are grouped together.

```Clean
// Language: Clean

triple 0 = 0
// So there's this one book
triple x = x * 3
```

Function implementations of `triple` are separated by a comment, which is still valid.

```Clean
// Language: Clean

quadruple 0 = 0
1 == 1
quadruple x = x * 3
```

Function implementations of `quadruple` are separated by an expressions.
According to the first rule, this function definition is invalid.

Not but much can be said about this rule 

Intuitively, this rule seems almost unnecessary.
If two function implementations have different names, there is no reason to assume that they are two different functions.

Non-comment entities cannot be placed between implementations of a function.

```Clean
// Language: Clean

badFunction paramA = ...
6 + 2
badFunction paramB = ...
```

The function definition is invalid because functions implementations are separated by an expression (`6 + 2`).

> [!important] #3

```Clean
// Language: Clean

badFunction m 0 = False
badFunction m n = m / n
```

The first function implementation accepts two integers and returns a Boolean, but the second accepts two integers and return an integer.

The function definition is invalid because function implementations have conflicting signatures.

---