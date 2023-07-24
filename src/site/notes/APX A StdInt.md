---
{"dg-publish":true,"permalink":"/apx-a-std-int/","created":"2023-06-20T23:37:36.392+07:00","updated":"2023-07-23T03:57:42.133+07:00"}
---


# StdInt

The `StdInt` module contains implementations for integer functions.

When imported, it allows for:

- integer arithmetic,
- comparison between integers,
- usage of bitwise operations,
- usage of predicate functions, and
- conversion to and from integer type.

Visit [StdInt](https://cloogle.org/src/#base-stdenv/StdInt;icl;line=1) on Cloogle for source code of this module.

## Constants

### Zero Unit

**Implementation**

```Clean
// Language: Clean

zero ::  Int
zero :== 0
```

**Definition**

It represents the identity element of integer addition.

### One Unit

**Implementation**

```Clean
// Language: Clean

one ::  Int
one :== 1
```

**Definition**

It represents the identity element of integer multiplication.

---

## Arithmetic Operations and Functions

### Negation

**Signature**

```Clean
// Language: Clean

~ :: Int -> Int
~    a   => ...
```

**Behavior**

It inverts the sign `a`.

**Usage**

```Clean
// Language: Clean

~  0   //  0
~  1   // -1
~(-1)  //  1
```

### Addition

**Signature**

```
// Language: Clean

(+) infixl 6 :: Int Int -> Int
(+)             a   b   => ...
```

**Behavior**

It adds `a` and `b`.

**Usage**

```Clean
// Language: Clean

  1  +   1   //  2
  1  + (-1)  //  0
(-1) +   1   //  0
(-1) + (-1)  // -2
```

### Subtraction

**Signature**

```Clean
// Language: Clean

(-) infixl 6 :: Int Int -> Int
(-)             a   b   => ...
```

**Behavior**

It subtracts `b` from `a`.

**Usage**

```Clean
// Language: Clean

  1  -   1  //  0
  1  - (-1) //  2
(-1) -   1  // -2
(-1) - (-1) //  0
```

### Multiplication

**Signature**

```Clean
// Language: Clean

(*) infixl 7 :: Int Int -> Int
(*)             a   b   => ...
```

**Behavior**

It multiplies `a` and `b`.

**Usage**

```Clean
// Language: Clean

  1  *   1  //  1
  1  * (-1) // -1
(-1) *   1  // -1
(-1) * (-1) //  1
```

### Floor Division

**Signature**

```Clean
// Language: Clean

(/) infixl 7 :: Int Int -> Int
(/)             a   b   => ...
```

**Behavior**

It divides `a` by `b`.
An expression results in a silent crash if `b` is zero.

**Usage**

```Clean
// Language: Clean

  1  /   1   //  1
  1  / (-1)  // -1
(-1) /   1   // -1
(-1) / (-1)  //  1
  7  /   0   //  silently crashes
```

### Reminder Division

**Signature**

```Clean
// Language: Clean

(rem) infix 7 :: Int Int -> Int
(rem)            a   b   => ...
```

and

```Clean
// Language: Clean

(mod) infix 7 :: Int Int -> Int
(mod)            a   b   => ...
```

For integer type, both `rem` and `mod` perform modulo division.

**Behavior**

It divides `a` by `b`, and returns the reminder.

**Usage**

```Clean
// Language: Clean

  3  mod (-2)  //  1
(-3) mod (-2)  // -1
(-3) mod   2   // -1
  3  mod   2   //  1
```

### Exponentiation

**Signature**

```Clean
// Language: Clean

(^) infixr 8 :: Int Int -> Int
(^)             a   b   => ...
```

**Behavior**

It raises `a` to the power of `b`.
An expression results in a run-time error if `b` is negative.

```markdown
^ (Int) called with negative power argument
```

**Usage**

```Clean
// Language: Clean

  1  ^   1   //  1
  1  ^ (-1)  //  run-time error
(-1) ^   1   // -1
(-1) ^ (-1)  //  run-time error
```

---

## Relational Operations

### Equal To

**Signature**

```Clean
// Language: Clean

(==) infix 4 :: Int Int -> Bool
(==)            a   b   => ...
```

**Behavior**

It returns true if `a` is equal to `b`.

**Usage**

```Clean
// Language: Clean

  5  ==   2   // False
(-5) ==   2   // False
  5  == (-2)  // False
(-5) == (-2)  // False
(-2) == (-2)  // True
```

### Not Equal To

**Signature**

```Clean
// Language: Clean

(<>) infix 4 :: Int Int -> Bool
(<>)            a   b   => ...
```

**Behavior**

It returns true if `a` is not equal to `b`.

**Usage**

```Clean
// Language: Clean

  5  <>   2   // True
(-5) <>   2   // True
  5  <> (-2)  // True
(-5) <> (-2)  // True
(-2) <> (-2)  // False
```

### Less Than

**Signature**

```Clean
// Language: Clean

(<) infix 4 :: Int Int -> Bool
(<)            a   b   => ...
```

**Behavior**

It returns true if `a` is strictly less than `b`.

**Usage**

```Clean
// Language: Clean

  5  <   2   // False
(-5) <   2   // True
  5  < (-2)  // False
(-5) < (-2)  // True
(-2) < (-2)  // False
```

### Less Than Or Equal To

**Signature**

```Clean
// Language: Clean

(<=) infix 4 :: Int Int -> Bool
(<=)            a   b   => ...
```

**Behavior**

It returns true if `a` is less than or equal to `b`.

**Usage**

```Clean
// Language: Clean

  5  <=   2   // False
(-5) <=   2   // True
  5  <= (-2)  // False
(-5) <= (-2)  // True
(-2) <= (-2)  // True
```

### Greater Than

**Signature**

```Clean
// Language: Clean

(>) infix 4 :: Int Int -> Bool
(>)            a   b   => ...
```

**Behavior**

It returns true if `a` is strictly greater than `b`.

**Usage**

```Clean
// Language: Clean

  5  >   2   // True
(-5) >   2   // False
  5  > (-2)  // True
(-5) > (-2)  // False
(-2) > (-2)  // False
```

### Greater Than Or Equal To

**Signature**

```Clean
// Language: Clean

(>=) infix 4 :: Int Int -> Bool
(>=)            a   b   => ...
```

**Behavior**

It returns true if `a` is greater than or equal to `b`.

**Usage**

```Clean
// Language: Clean

  5  >=   2   // True
(-5) >=   2   // False
  5  >= (-2)  // True
(-5) >= (-2)  // False
(-2) >= (-2)  // True
```

---

## Bitwise Operations and Functions

They interact with integer type through binary representation.

### Bitwise NEGATE

**Signature**

```Clean
// Language: Clean

bitnot :: Int -> Int
bitnot    a   => ...
```

**Behavior**

It returns bitwise-two complement of `a`.

**Usage**

```Clean
// Language: Clean

bitnot (-5)  //  -4
bitnot (-2)  //   1
bitnot   2   //  -3
bitnot   5   //  -6
```

### Bitwise OR

**Signature**

```Clean
// Language: Clean

(bitor) infixl 6 :: Int Int -> Int
(bitor)             a   b   => ...
```

**Behavior**

It returns bitwise OR of `a` and `b`.

**Usage**

```Clean
// Language: Clean

  5  bitor   2   //  7
(-5) bitor   2   // -5
  5  bitor (-2)  // -1
(-5) bitor (-2)  // -1
```

### Bitwise AND

**Signature**

```Clean
// Language: Clean

(bitand) infixl 6 :: Int Int -> Int
(bitand)             a   b   => ...
```

**Behavior**

It returns bitwise AND of `a` and `b`.

**Usage**

```Clean
// Language: Clean

  5  bitand   2   //  0
(-5) bitand   2   //  2
  5  bitand (-2)  //  4
(-5) bitand (-2)  // -6
```

### Bitwise XOR

**Signature**

```Clean
// Language: Clean

(bitxor) infixl 6 :: Int Int -> Int
(bitxor)             a   b   => ...
```

**Behavior**

It returns bitwise XOR of `a` and `b`.

**Usage**

```Clean
// Language: Clean

  5  bitxor   2   //  7
(-5) bitxor   2   // -7
  5  bitxor (-2)  // -5
(-5) bitxor (-2)  //  5
```

### Bitwise Left Shift

**Signature**

```Clean
// Language: Clean

(<<) infix 7 :: Int Int -> Int
(<<)            a   b   => ...
```

**Behavior**

It shifts `a` to the left by `b` bits.

**Usage**

```Clean
// Language: Clean

  5  <<   2   //  20
(-5) <<   2   // -20
  5  << (-2)  //  4611686018427387904
(-5) << (-2)  // -4611686018427387904
```

### Bitwise Right Shift

**Signature**

```Clean
// Language: Clean

(>>) infix 7 :: Int Int -> Int
(>>)            a   b   => ...
```

**Behavior**

It shifts `a` to the right by `b` bits.

**Usage**

```Clean
// Language: Clean

  5  >>   2   //  1
(-5) >>   2   // -2
  5  >> (-2)  //  0
(-5) >> (-2)  // -1
```

---

## Basic Functions

### `sign`

**Signature**

```Clean
// Language: Clean

sign :: Int -> Int
sign    a   => ...
```

**Behavior**

It returns the sign of `a`.

**Usage**

```Clean
// Language: Clean

sign   1   //  1
sign   0   //  0
sign (-1)  // -1
```

### `abs`

**Signature**

```Clean
// Language: Clean

abs :: Int -> Int
abs    a   => ...
```

**Behavior**

It returns the absolute value of `a`.

**Usage**

```Clean
// Language: Clean

abs   1   // 1
abs   0   // 0
abs (-1)  // 1
```

### `gcd`

**Signature**

```Clean
// Language: Clean

gcd :: Int Int -> Int
gcd    a   b   => ...
```

**Behavior**

It returns the greatest common divisor of `a` and `b`.

**Usage**

```Clean
// Language: Clean

gcd   3    2   // 1
gcd (-3)   2   // 1
gcd   3  (-2)  // 1
gcd (-3) (-2)  // 1
```

### `lcm`

**Signature**

```Clean
// Language: Clean

lcm :: Int Int -> Int
lcm    a   b   => ...
```

**Behavior**

It returns the least common multiple of `a` and `b`.

**Usage**

```Clean
// Language: Clean

lcm   3    2   // 6
lcm (-3)   2   // 6
lcm   3  (-2)  // 6
lcm (-3) (-2)  // 6
```

---

## Predicate Functions

### `isEven`

**Signature**

```Clean
// Language: Clean

isEven :: Int -> Bool
isEven    a   => ...
```

**Behavior**

It returns true if `a` is an even integer.

**Usage**

```Clean
// Language: Clean

isEven  2  // False
isEven  1  // True
isEven  0  // True
isEven -1  // True
isEven -2  // False
```

### `isOdd`

**Signature**

```Clean
// Language: Clean

isOdd :: Int -> Bool
isOdd    a   => ...
```

**Behavior**

It returns true if `a` is an odd integer.

**Usage**

```Clean
// Language: Clean

isOdd  2  // True
isOdd  1  // False
isOdd  0  // False
isOdd -1  // False
isOdd -2  // True
```

---

## Conversions To Integer Type

They explicitly convert other types to integer type.

### From Real Number Type

**Signature**

```Clean
// Language: Clean

toInt :: Real -> Int
toInt    a    => ...
```

**Behavior**

It rounds `a` to its nearest integer.

**Usage**

```Clean
// Language: Clean

toInt   1.5   //  2
toInt   1.4   //  1
toInt   0.0   //  0
toInt (-1.4)  // -1
toInt (-1.5)  // -2
```

### From Character Type

**Signature**

```Clean
// Language: Clean

toInt :: Char -> Int
toInt    a    => ...
```

**Behavior**

It returns ASCII code of `a`.

**Usage**

```Clean
// Language: Clean

toInt '1'  //  49
toInt '9'  //  59
toInt 'A'  //  65
toInt 'Z'  //  90
toInt 'a'  //  97
toInt 'z'  // 122
```

### From String Type

**Signature**

```Clean
// Language: Clean

toInt :: { #Char } -> Int
toInt    a         => ...
```

**Behavior**

It attempts to parse `a` as an integer.
If it is unsuccessful, it returns zero.

**Usage**

```Clean
// Language: Clean

toInt "1.0"   //  0
toInt "1"     //  1
toInt "0"     //  0
toInt "-1"    // -1
toInt "-1.0"  //  0
```

---

## Conversions From Integer Type

They explicitly convert integer type to other types.
The desired type must be unambiguous.

### To Real Number Type

**Signature**

```Clean
// Language: Clean

fromInt :: Real -> Int
fromInt    a    => ...
```

**Behavior**

It sets the decimal places of `a` to 0.

**Usage**

```Clean
// Language: Clean

expr :: Real
expr =  fromInt  1  // 1.0
expr =  fromInt  0  // 0.0
```

### To Character Type

**Signature**

```Clean
// Language: Clean

fromInt :: Int -> Char
fromInt    a   => ...
```

**Behavior**

It returns a character whose ASCII code is `a`.

**Usage**

```Clean
// Language: Clean

expr :: Char
expr =  fromInt 49   // '1'
expr =  fromInt 59   // '9'
expr =  fromInt 65   // 'A'
expr =  fromInt 90   // 'Z'
expr =  fromInt 97   // 'a'
expr =  fromInt 122  // 'z'
```

### To String Type

**Signature**

```Clean
// Language: Clean

fromInt :: Int -> { #Char }
fromInt    a   => ...
```

**Behavior**

It returns a string representation of `a`.

**Usage**

```Clean
// Language: Clean

expr :: { #Char }
expr =  fromInt 1  // "1"
expr =  fromInt 0  // "0"
```
