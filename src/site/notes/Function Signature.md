---
{"dg-publish":true,"permalink":"/function-signature/","created":"2023-06-24T23:19:01.663+02:00","updated":"2023-06-24T23:51:57.676+02:00"}
---


# Function Signature

Every function has a signature.

A function signature represents the number of arguments, the type of each argument, and the return type of the function.

The behavior of a function is ignored when speaking in terms of function signatures.
Therefore, functions, which have completely different behaviors, can share a function signature.

## Example

To demonstrate, let's take a look at some functions.

```Clean
// Language: Clean

double x = x * 2
```

The function signature of `double` is a function which accepts one integer as argument and returns an integer.

```Clean
// Language: Clean

triple x = x * 3
```

The function signature of `triple` is a function which accepts one integer as argument and returns an integer.

Although, `double` and `triple` does two different things, they share a single function signature.

---