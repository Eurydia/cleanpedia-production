---
{"dg-publish":true,"permalink":"/functions/function-implementation/","tags":["function-implementation"],"created":"2023-06-20T18:37:36.405+02:00","updated":"2023-06-24T11:04:01.123+02:00"}
---


# Function Implementation

A group of one or more function implementations make up a function definition.
Function implementations consist of three components as follows:
- a function identifier,
- a fix-length space-separated parameter sequence, and
- a function body.

A control function implementation with one parameter is written as follows.

```markdown
identifier param = body
```

A control function implementation with two parameters is written as follows.

```markdown
identifier paramA paramB = body
```

If multiple function implementations are used to defined a function, a [[Functions/Function Implementation Selection\|procedure]] exists to help determine which one should be evaluated.

By introducing [[Functions/Guarded Bodies\|guarded bodies]], a function implementation can have ownership over multiple guarded bodies, instead of one ordinary body.

Function implementations must also conform to [[Functions/Function Implementation Rules\|specific rules]].
Violation of these rules results in a compile-time error.