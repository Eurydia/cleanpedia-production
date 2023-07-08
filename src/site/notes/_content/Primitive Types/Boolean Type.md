---
{"dg-publish":true,"permalink":"/content/primitive-types/boolean-type/","created":"2023-07-03T09:26:49.263+02:00","updated":"2023-07-08T12:02:21.065+02:00"}
---


# Boolean Type

Booleans are represented using 8 bits values.

## Boolean Literals

Boolean literals have two constructors.
Each constructor represents a Boolean value.

```Clean
// Language: Clean

True
False
```

## Typing Boolean Expressions

An expression, which evaluates to Boolean type, can be explicitly typed using `Bool`.

```Clean
// Language: Clean

expr :: Bool
expr =  True
```

## Using Boolean Literal as Pattern

See [[_content/Functions/Pattern Matching/Pattern Matching Booleans\|Pattern Matching Booleans]] for additional example.

## Built-In Functions on Boolean Type

See [[_content/Appendix A/StdBool\|StdBool]] module for additional information.