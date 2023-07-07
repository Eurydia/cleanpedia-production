---
{"dg-publish":true,"permalink":"/content/functions/pattern-matching/pattern-matching-booleans/","created":"2023-07-07T22:25:29.390+02:00","updated":"2023-07-07T22:47:07.558+02:00"}
---


# Pattern Matching Booleans

```Clean
// Language: Clean

neg :: Bool -> Bool
neg    True =  False
neg    _    =  True
```