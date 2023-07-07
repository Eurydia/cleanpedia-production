---
{"dg-publish":true,"permalink":"/content/functions/pattern-matching/pattern-matching-characters/","created":"2023-07-07T22:25:20.472+02:00","updated":"2023-07-07T22:47:58.033+02:00"}
---


# Pattern Matching Characters

```Clean
// Language: Clean

isA :: Char -> Bool
isA    'A'  =  True
isA    'a'  =  True
isA    _    =  False
```