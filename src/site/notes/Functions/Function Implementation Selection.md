---
{"dg-publish":true,"permalink":"/functions/function-implementation-selection/","created":"2023-06-24T03:49:38.415+07:00","updated":"2023-06-24T16:45:36.465+07:00"}
---


#function #function-implementation #function-implementation-selection 

# Function Implementation Selection

When a function is called, exactly one function implementation must be selected because the result will be obtained from the body of the function implementation.

> [!important]
> Implementations are tried in descending order.
> The first implementation, whose parameters match with every argument, is selected.

Visit this [[Functions/Example/Function Implementation Selection Steps In Action\|example]] to see the steps in action.

> [!warning]
> When no function implementation can be selected, the function call results in a run-time error 

Visit this [[Functions/Example/No Function Implementation Is Selected\|example]] to see the how a run-time error occurs.

---