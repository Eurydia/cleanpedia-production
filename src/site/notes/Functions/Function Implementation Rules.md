---
{"dg-publish":true,"permalink":"/functions/function-implementation-rules/","created":"2023-06-20T18:37:36.404+02:00","updated":"2023-06-23T11:18:12.167+02:00"}
---


When a function is defined, its function implementations must follow a set of rules.
Violation of these rules results in a compile-time error.

Let's discuss what these rules are.

## Implementation Rule of Naming

*Implementation of a function must share a single name.*

Implementations of a function should have the same name.
More importantly, the name of a function must be unique from other names in the same scope.

---

## Implementation Rule of Grouping

*Implementations of a function must be together.*

Non-comment entities cannot be placed between implementations of a function.

```Clean
// Language: Clean

badFunction paramA = ...
6 + 2
badFunction paramB = ...
```

The function definition is invalid because functions implementations are separated by an expression (`6 + 2`).

---

## Implementation Rule of Signature

*Implementations of a function must share a single signature.*

```Clean
// Language: Clean

badFunction m 0 = False
badFunction m n = m / n
```

The first function implementation accepts two integers and returns a Boolean, but the second accepts two integers and return an integer.

The function definition is invalid because function implementations have conflicting signatures.

---