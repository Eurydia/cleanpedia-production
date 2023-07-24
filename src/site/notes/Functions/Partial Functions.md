---
{"dg-publish":true,"permalink":"/functions/partial-functions/","created":"2023-06-20T23:37:36.406+07:00","updated":"2023-07-24T23:16:56.966+07:00"}
---

# Partial Functions

A partially defined function is a function which results in a run-time error when called with arguments outside of its domain.

They are caused by an oversight where not all possible arguments, which can be given to a function, is not accounted for.

In a practical environment, however, it is easier to accidentally defined a partial function with [[Functions/Guarded Bodies\|guarded bodies]] than with [[Functions/Control Form of Function Implementation\|function implementations]].



## Resolving Partial Functions

A built-in function called `abort` from [[APX A StdMisc\|APX A StdMisc]] completes a function by terminating the program early.

---