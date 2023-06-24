---
{"dg-publish":true,"permalink":"/functions/partial-functions/","created":"2023-06-20T18:37:36.406+02:00","updated":"2023-06-23T23:01:29.223+02:00"}
---


A partially defined function is a function which results in a run-time error when called with arguments outside of its domain.

They are caused by an oversight where not all possible arguments, which can be given to a function, is not accounted for.

In a practical environment, however, it is easier to accidentally defined a partial function with  [[Functions/Guarded Bodies\|guarded bodies]] than with [[Functions/Function Implementation\|function implementations]].



## Resolving Partial Functions

A built-in function called `abort` from [[appendix-a/StdMisc\|StdMisc]] completes a function by terminating the program early.

---