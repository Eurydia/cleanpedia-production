---
{"dg-publish":true,"permalink":"/content/functions/pattern-matching/pattern-matching-real-numbers/","created":"2023-07-07T16:51:18.187+02:00","updated":"2023-07-07T20:53:52.366+02:00"}
---


# Pattern Matching Real Numbers

## Using Decimal Notation as Pattern

```Clean
// Language: Clean

isUnit :: Real -> Bool
isUnit    1.0  =  True
isUnit    _    =  False
```

---

## Using Scientific Notation as Pattern

```Clean
// Language: Clean

isUnit :: Real -> Bool
isUnit    1E1  =  True
isUnit    _    =  False
```

---

## Mixing Multiple Notations

Different notations can mix freely, as they represent the same numerical value.

```Clean
// Language: Clean

fastMul :: Real Real -> Real
fastMul    1.0  rhs  =  rhs
fastMul    lhs  1E0  =  lhs
fastMul    lhs  rhs  =  lhs * rhs
```