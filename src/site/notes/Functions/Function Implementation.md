---
{"dg-publish":true,"permalink":"/functions/function-implementation/","created":"2023-06-24T20:40:52.018+07:00","updated":"2023-07-23T03:57:42.066+07:00"}
---


# Function Implementation

A control form of a function implementation is written as follows.

```markdown
identifier paramSeq = body
```

The `identifier` represents the name of a function.

The `paramSeq` represents a fixed-length space-separated parameter sequence.

The `body` represents an expressions which will be evaluated when the function is called.

Function implementations must follow a set of rules.
Violation of these rules results in a compile-time error.

See [[Functions/Function Implementation Rules\|Function Implementation Rules]] for more information.

---