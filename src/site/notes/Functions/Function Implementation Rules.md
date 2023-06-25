---
{"dg-publish":true,"permalink":"/functions/function-implementation-rules/","created":"2023-06-20T18:37:36.404+02:00","updated":"2023-06-24T23:17:50.253+02:00"}
---


# Function Implementation Rules

Implementations of a function must follow these rules.
Violation results in a compile-time error.

Implementations of a function must:
- be grouped together,
- share a single signature, and
- share a single identifier.

In addition, the identifier must be unique from other identifiers in the namespace.

> [!info]
> The following section is intended to provide examples and insight on each rules.

Let's investigate the rules further starting with the first.

> [!quote]
> Implementations of a function must be grouped together.

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
triple x = x * 4
```

Function implementations of `triple` are separated by a comment, which is an exception.

```Clean
// Language: Clean

quadruple 0 = 0
1 + 2
quadruple x = x * 3
```

Function implementations of `quadruple` are separated by an expression.
This function definition is invalid.

This rule is rather straightforward.

> [!quote]
> Functions implementation must share a single signature.




---