---
{"dg-publish":true,"permalink":"/content/appendix-a/std-bool/","created":"2023-06-20T18:37:36.389+02:00","updated":"2023-07-07T23:03:33.896+02:00"}
---


# StdBool

The `StdBool` module contains implementation for logical operations.

When imported, this module allows for:
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

**Behavior**: returns true if `a` and `b` have the same logical value.

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

**Behavior**: returns true if  `a` or `b` is true.

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

**Behavior**: returns true if `a`and `b` are true.

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

**Behavior**: negates the logical value of `a`.

**Usage**

```
// Language: Clean

not True        // False
not False       // True
not (not True)  // True
```

---

## Conversions From Boolean Type

Explicitly converts Boolean type to other types.
The desired type must be unambiguous.

### To String type

**Signature**

```Clean
// Language: Clean

fromBool :: Bool -> {#Char}
fromBool    a    => ...
```

**Behavior**: returns a string representation of `a`.

**Usage**

```Clean
// Language: Clean

expr :: {#Char}
expr =  fromBool True   // "True"
expr =  fromBool False  // "False"
```