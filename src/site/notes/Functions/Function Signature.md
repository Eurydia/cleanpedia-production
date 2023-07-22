---
{"dg-publish":true,"permalink":"/functions/function-signature/","created":"2023-06-25T04:19:01.663+07:00","updated":"2023-07-23T03:57:42.062+07:00"}
---


# Function Signature

Every function has a signature.

A function signature represents the following:
- number of arguments, 
- the type of each argument, and 
- the return type.

When speaking in terms of function signatures, the behavior of a function is ignored .
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

Although, `double` and `triple` do two different things, they share a single function signature.

---