---
{"dg-publish":true,"permalink":"/appendix-a/std-bool/","created":"2023-06-20T18:37:36.389+02:00","updated":"2023-07-12T11:34:39.525+02:00"}
---


# StdBool

The `StdBool` module contains implementations for logical operations.

When imported, it allows for:
- usage of logical operations, and
- conversion from Boolean type.

Visit [StdBool](https://cloogle.org/src/#base-stdenv/StdBool;icl;line=1) on Cloogle for source code of this module.

## Logical Operations

### Logical EQUIVALENCE

**Signature**

```Clean
// Language: Clean

(==) infix 4 :: Bool Bool -> Bool
(==)            a    b    => ...
```

**Behavior**

It returns true if `a` and `b` have the same logical value.

**Usage**

```Clean
// Language: Clean

True  == True   // True
True  == False  // False
False == True   // False
False == False  // True
```

### Logical OR

**Signature**

```Clean
// Language: Clean

(||) infixr 2 :: Bool Bool -> Bool
(||)             a    b    => ...
```

**Behavior**

It returns true if  `a` or `b` is true.

**Usage**

```Clean
// Language: Clean

True  || True   // True
True  || False  // True
False || True   // True
False || False  // False
```

### Logical AND

**Signature**

```Clean
// Language: Clean

(&&) infixr 3 :: Bool Bool -> Bool
(&&)             a    b    => ...
```

**Behavior**

It returns true if `a`and `b` are true.

**Usage**

```Clean
// Language: Clean

True  && True   // True
True  && False  // False
False && True   // False
False && False  // False
```

---

## Logical Functions

### Logical NEGATE

**Signature**

```Clean
// Language: Clean

not :: Bool -> Bool
not    a    => ...
```

**Behavior**

It negates the logical value of `a`.

**Usage**

```Clean
// Language: Clean

not True        // False
not False       // True
not (not True)  // True
```

---

## Conversions From Boolean Type

They explicitly convert Boolean type to other types.
The desired type must be unambiguous.

### To String type

**Signature**

```Clean
// Language: Clean

fromBool :: Bool -> { # Char }
fromBool    a    => ...
```

**Behavior**

It returns a string representation of `a`.

**Usage**

```Clean
// Language: Clean

expr :: { # Char }
expr =  fromBool True   // "True"
expr =  fromBool False  // "False"
```
