---
{"dg-publish":true,"permalink":"/introducing-scopes/","created":"2023-06-20T23:37:36.385+07:00","updated":"2023-07-02T04:27:42.207+07:00"}
---


# Introducing Scopes

## Let Expressions

A `let..in..` expression introduces a new scope within another expression.

A control expression with one local definition may be written as follows.

```
// Language: Clean

let
    localFunction x = ...
in expression
```

Definitions are local to `expression`.

```
// Language: Clean

[let 
    a = i * i 
in (a, a) \\ i <- [0..n]]
```

## Where Blocks

A `where` block can be introduced to the end of a function implementation.
It introduces a new scope local to that implementation.

A control `where` block with one definition may be written as follows.

```
// Language: Clean

functionA parameter = expression
where
    localFunc x = ...
functionA parameter = expression
```

The second implementation does not have access to `localFunc` which is local to the first implementation.

## With Blocks

A `with` block can be introduced to the end of a guarded.
It introduces a new scope local to that guarded expression.

A control `with` block with one definition may be written as follows.

```
// Language: Clean

functionA parameter
| guardA = expressionA
with 
    localFunc x = ...
| guardB = expressionB
```

However, the guard itself does not have access to definitions within its `with` block.

```
// Language: Clean

functionA n
| x == 0    = 0
with 
    x = n mod 2
| otherwise = 1
```

The definition of `functionA` is not valid since the guard cannot reference `x`.