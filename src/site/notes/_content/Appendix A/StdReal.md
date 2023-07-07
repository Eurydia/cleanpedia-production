---
{"dg-publish":true,"permalink":"/content/appendix-a/std-real/","created":"2023-06-20T18:37:36.396+02:00","updated":"2023-07-07T23:26:13.629+02:00"}
---


# StdReal

The `StdReal` module contains definitions for operations and functions relating to real number type. 

When imported, this module allows for:
- real number arithmetic,
- comparison between real numbers,
- usage of trigonometric function,
- property testing, and
- conversion to and from real number type.

Visit [StdReal](https://cloogle.org/src/#base-stdenv/StdReal;icl;line=1) on Cloogle for source code of this module.

## Constants

### Zero Unit

**Implementation**

```Clean
// Language: Clean

zero ::  Real
zero :== 0.0
```

**Definition**: represents identity element of real number addition.

### One Unit

**Implementation**

```Clean
// Language: Clean

one ::  Real
one :== 1.0
```

**Definition**: represents identity element of real number multiplication.

### Infinity Representation

**Implementation**

```Clean
// Language: Clean

Infinity ::  Real
Infinity :== 1E9999
```

**Definition**: represents real numbers too large to represents.

### Not-A-Number Representation

**Implementation**

```Clean
// Language: Clean

NaN ::  Real
NaN :== 1E9999 + (-1E9999)
```

**Definition**: represents real numbers which cannot be represented.

See [NaN](https://en.wikipedia.org/wiki/NaN).

---

## Arithmetic Operations and Functions

### Negation

**Signature**

```Clean
// Language: Clean

~ :: Real -> Real
~    a    =  ...
```

**Behavior**: inverts sign of `a`.

**Usage**

```Clean
// Language: Clean

~  1.0   // -1.0
~  0.0   //  0.0
~(-1.0)  //  1.0
```

### Addition

**Signature**


```Clean
// Language: Clean
 
(+) infixl 6 :: Real Real -> Real
(+)             a    b    =  ...
```

**Behavior**: adds `a` and `b`.

**Usage**

```Clean
// Language: Clean

  2.5  +   1.5   //  4.0
  2.5  + (-1.5)  //  1.5
(-2.5) +   1.5   // -1.0
(-2.5) + (-1.5)  // -4.0
```

### Subtraction

**Signature**

```Clean
// Language: Clean
 
(-) infixl 6 :: Real Real -> Real
(-)             a    b    =  ...
```

**Behavior**: subtracts `b` from `a`.

**Usage**

```Clean
// Language: Clean

  2.5  -   1.5   //  1.0
  2.5  - (-1.5)  //  4.0
(-2.5) -   1.5   // -1.5
(-2.5) - (-1.5)  // -1.0
```

### Multiplication

**Signature**

```Clean
// Language: Clean
 
(*) infixl 7 :: Real Real -> Real
(*)             a    b    =  ...
```

**Behavior**: multiplies `a` with `b`.

**Usage**

```Clean
// Language: Clean

  2.5  *   1.5   //  3.75
  2.5  * (-1.5)  // -3.75
(-2.5) *   1.5   // -3.75
(-2.5) * (-1.5)  //  3.75
```

### Division

**Signature**

```Clean
// Language: Clean

(/) infixl 7 :: Real Real -> Real
(/)             a    b    =  ...
```

**Behavior**: divides `a` with `b`. 

**Usage**

```Clean
// Language: Clean

  2.5  /   1.5   //  1.66666666666667
  2.5  / (-1.5)  // -1.66666666666667
(-2.5) /   1.5   // -1.66666666666667
(-2.5) / (-1.5)  //  1.66666666666667
  1.0  /   0.0   //  #INF
(-1.0) /   0.0   // -#INF
  0.0  /   0.0   //  #NaN
```

### Exponentiation

**Signature**

```Clean
// Language: Clean

(^) infixr 8 :: Real Real -> Real
(^)             a    b    =  ...
```

**Behavior**: raises `a` to the power of `b`.

**Usage**

```Clean
// Language: Clean

  2.5  ^   1.5   //  3.95284707521047
  2.5  ^ (-1.5)  //  0.25298221281347
(-2.5) ^   1.5   //  #NAN
(-2.5) ^ (-1.5)  //  #NAN
  0.0  ^   0.0   //  1.0
  0.0  ^   1.0   //  0.0
  0.0  ^ (-1.0)  //  #INF
```

---

## Relational Operations

Equality comparison between two real numbers is unaffected by rounding errors.

### Equal To

**Signature**

```Clean
// Language: Clean

(==) infix 4 :: Real Real -> Bool
(==)            a    b    =  ...
```

**Behavior**: returns true if `a` is equal to `b`.

**Usage**

```Clean
// Language: Clean

  5.0  ==   2.0   // False
(-5.0) ==   2.0   // False
  5.0  == (-2.0)  // False
(-5.0) == (-2.0)  // False
(-2.0) == (-2.0)  // True
```

### Not Equal To

**Signature**

```Clean
// Language: Clean

(<>) infix 4 :: Real Real -> Bool
(<>)            a    b    =  ...
```

**Behavior**: returns true if `a` is not equal to `b`.

**Usage**

```Clean
// Language: Clean

  5.0  <>   2.0   // True
(-5.0) <>   2.0   // True
  5.0  <> (-2.0)  // True
(-5.0) <> (-2.0)  // True
(-2.0) <> (-2.0)  // False
```

### Less Than

**Signature**

```Clean
// Language: Clean

(<) infix 4 :: Real Real -> Bool
(<)            a    b    =  ...
```

**Behavior**: returns true if `a` is strictly less than `b`.

**Usage**

```Clean
// Language: Clean

  5.0  <   2.0   // False
(-5.0) <   2.0   // True
  5.0  < (-2.0)  // False
(-5.0) < (-2.0)  // True
(-2.0) < (-2.0)  // False
```

### Less Than Or Equal To

**Signature**

```Clean
// Language: Clean

(<=) infix 4 :: Real Real -> Bool
(<=)            a    b    =  ...
```

**Behavior**: returns true if `a` is less than or equal to `b`.

**Usage**

```Clean
// Language: Clean

  5.0  <=   2.0   // False
(-5.0) <=   2.0   // True
  5.0  <= (-2.0)  // False
(-5.0) <= (-2.0)  // True
(-2.0) <= (-2.0)  // True
```

### Greater Than

**Signature**

```Clean
// Language: Clean

(>) infix 4 :: Real Real -> Bool
(>)            a    b    =  ...
```

**Behavior**: returns true if `a` is strictly greater than `b`.

**Usage**

```Clean
// Language: Clean

  5.0  >   2.0   // True
(-5.0) >   2.0   // False
  5.0  > (-2.0)  // True
(-5.0) > (-2.0)  // False
(-2.0) > (-2.0)  // False
```

### Greater Than Or Equal To

**Signature**

```Clean
// Language: Clean

(>=) infix 4 :: Real Real -> Bool
(>=)            a    b    =  ...
```

**Behavior**: returns true if `a` is greater than or equal to `b`.

**Usage**

```Clean
// Language: Clean

  5.0  >=   2.0   // True
(-5.0) >=   2.0   // False
  5.0  >= (-2.0)  // True
(-5.0) >= (-2.0)  // False
(-2.0) >= (-2.0)  // True
```

---

## Basic Functions

### `sign`

**Signature**

```Clean
// Language: Clean

sign :: Real -> Int
sign    a    =  ...
```

**Behavior**: returns sign of `a`.

**Usage**

```Clean
// Language: Clean

sign   1.0   //  1
sign   0.0   //  0
sign (-1.0)  // -1
```

### `abs`

**Signature**

```Clean
// Language: Clean

abs :: Real -> Real
abs    a    =  ...
```

**Behavior**: returns absolute value of `a`.

**Usage**

```Clean
// Language: Clean

abs   1.0   // 1.0
abs   0.0   // 0.0
abs (-1.0)  // 1.0
```

### `entier`

**Signature**

```Clean
// Language: Clean

entier :: Real -> Int
entier    a    =  ...
```

**Behavior**: returns largest integer which is less than `a`.

**Usage**

```Clean
// Language: Clean

entier   1.5   //  1
entier   0.0   //  0
entier (-1.5)  // -2
```

### `ln`

**Signature**

```Clean
// Language: Clean

ln :: Real -> Real
ln    a    =  ...
```

**Behavior**: returns natural logarithm of `a`.

**Usage**

```Clean
// Language: Clean

ln   2.5   //  0.916290731874155
ln   1.5   // -1.405465108108164
ln   0.0   // -#INF
ln (-1.5)  //  #NAN
ln (-2.5)  //  #NAN
```

### `log10`

**Signature**

```Clean
// Language: Clean

log10 :: Real -> Real
log10    a    =  ...
```

**Behavior**: returns logarithm base ten of `a`.

**Usage**

```Clean
// Language: Clean

log10   2.5   //  0.397940008672038
log10   1.5   // -0.176091259055681
log10   0.0   // -#INF
log10 (-1.5)  //  #NAN
log10 (-2.5)  //  #NAN
```

### `exp`

**Signature**

```Clean
// Language: Clean

exp :: Real -> Real
exp    a    =  ...
```

**Behavior**: raises $e$ to the power of `a`.

See [Euler's number](https://en.wikipedia.org/wiki/E_\(mathematical_constant\)).

**Usage**

```Clean
// Language: Clean

exp   2.5   // 12.1824939607035
exp   1.5   //  4.48168907033806
exp   0.0   //  1.0
exp (-1.5)  //  0.22313016014843
exp (-2.5)  //  0.0820849986238988
```

### `sqrt`

**Signature**

```Clean
// Language: Clean

sqrt :: Real -> Real
sqrt    a    =  ...
```

**Behavior**: returns square root of `a`.

**Usage**

```Clean
// Language: Clean

sqrt   2.5   // 1.58113883008419
sqrt   1.5   // 1.22474487139159
sqrt   0.0   // 0.0
sqrt (-1.5)  // #NAN
sqrt (-2.5)  // #NAN
```

---

## Trigonometric Functions

### `sin`

**Signature**

```Clean
// Language: Clean

sin :: Real -> Real
sin    a    =  ...
```

**Behavior**: returns sine of `a`.

**Usage**

```Clean
// Language: Clean

sin   2.5   //  0.598472144103956
sin   1.5   //  0.997494986604054
sin   0.0   //  0.0
sin (-1.5)  // -0.997494986604054
sin (-2.5)  // -0.598472144103956
```

### `cos`

**Signature**

```Clean
// Language: Clean

cos :: Real -> Real
cos    a    =  ...
```

**Behavior**: returns cosine of `a`.

**Usage**

```Clean
// Language: Clean

cos   2.5   // -0.801143615546934
cos   1.5   //  0.0707372016677029
cos   0.0   //  1.0
cos (-1.5)  //  0.0707372016677029
cos (-2.5)  // -0.801143615546934
```

### `tan`

**Signature**

```Clean
// Language: Clean

tan :: Real -> Real
tan    a    =  ...
```

**Behavior**: returns tangent of `a`.

**Usage**

```Clean
// Language: Clean

tan   2.5   // - 0.74702229723866
tan   1.5   //  14.1014199471717
tan   0.0   //   0.0
tan (-1.5)  // -14.1014199471717
tan (-2.5)  //   0.74702229723866
```

### `asin`

**Signature**

```Clean
// Language: Clean

asin :: Real -> Real
asin    a    =  ...
```

**Behavior**: returns inverse sine of `a`.

**Usage**

```Clean
// Language: Clean

asin   2.5   //  #NAN
asin   1.5   //  #NAN
asin   0.5   //  0.523598775598299
asin   0.0   //  0.0
asin (-0.5)  // -0.523598775598299
asin (-1.5)  //  #NAN
asin (-2.5)  //  #NAN
```

### `acos`

**Signature**

```Clean
// Language: Clean

acos :: Real -> Real
acos    a    =  ...
```

**Behavior**: returns inverse cosine of `a`.

**Usage**

```Clean
// Language: Clean

acos   2.5   // #NAN
acos   1.5   // #NAN
acos   0.5   // 1.0471975511966
acos   0.0   // 1.5707963267949
acos (-0.5)  // 2.0943951023932
acos (-1.5)  // #NAN
acos (-2.5)  // #NAN
```

### `atan`

**Signature**

```Clean
// Language: Clean

atan :: Real -> Real
atan    a    =  ...
```

**Behavior**: returns inverse tangent of `a`.

**Usage**

```Clean
// Language: Clean

atan   2.5   //  1.19028994968253
atan   1.5   //  0.982793723247329
atan   0.5   //  0.463647609000806
atan   0.0   //  0.0
atan (-0.5)  // -0.463647609000806
atan (-1.5)  // -0.982793723247329
atan (-2.5)  // -1.19028994968253
```

### `sinh`

**Signature**

```Clean
// Language: Clean

sinh :: Real -> Real
sinh    a    =  ...
```

**Behavior**: returns hyperbolic sine of `a`.

**Usage**

```Clean
// Language: Clean

sinh   2.5   //  6.05020448103979
sinh   1.5   //  2.12927945509482
sinh   0.5   //  0.521095305493747
sinh   0.0   //  0.0
sinh (-0.5)  // -0.521095305493747
sinh (-1.5)  // -2.12927945509482
sinh (-2.5)  // -6.05020448103979
```

### `cosh`

**Signature**

```Clean
// Language: Clean

cosh :: Real -> Real
cosh    a    =  ...
```

**Behavior**: returns hyperbolic cosine of `a`.

**Usage**

```Clean
// Language: Clean

cosh   2.5   //  6.13228947966369
cosh   1.5   //  2.35240961524325
cosh   0.5   //  1.12762596520638
cosh   0.0   //  1.0
cosh (-0.5)  // -1.12762596520638
cosh (-1.5)  // -2.35240961524325
cosh (-2.5)  // -6.13228947966369
```

### `tanh`

**Signature**

```Clean
// Language: Clean

tanh :: Real -> Real
tanh    a    =  ...
```

**Behavior**: returns hyperbolic tangent of `a`.

**Usage**

```Clean
// Language: Clean

tanh   2.5   //  0.98661429815143
tanh   1.5   //  0.905148253644866
tanh   0.5   //  0.46211715726001
tanh   0.0   //  0.0
tanh (-0.5)  // -0.46211715726001
tanh (-1.5)  // -0.905148253644866
tanh (-2.5)  // -0.98661429815143
```

### `asinh`

**Signature**

```Clean
// Language: Clean

asinh :: Real -> Real
asinh    a    =  ...
```

**Behavior**: returns inverse hyperbolic sine of `a`.

**Usage**

```Clean
// Language: Clean

asinh   2.5   //  1.6472311463711
asinh   1.5   //  1.19476321728711
asinh   0.5   //  0.481211825059604
asinh   0.0   //  0.0
asinh (-0.5)  // -0.481211825059604
asinh (-1.5)  // -1.19476321728711
asinh (-2.5)  // -1.6472311463711
```

### `acosh`

**Signature**

```Clean
// Language: Clean

acosh :: Real -> Real
acosh    a    =  ...
```

**Behavior**: returns inverse hyperbolic cosine of `a`.

**Usage**

```Clean
// Language: Clean

acosh   2.5   // 1.56679923697241
acosh   1.5   // 0.962423650119207
acosh   0.5   // #NAN
acosh   0.0   // #NAN
acosh (-0.5)  // #NAN
acosh (-1.5)  // #NAN
acosh (-2.5)  // #NAN
```

### `atanh`

**Signature**

```Clean
// Language: Clean

atanh :: Real -> Real
atanh    a    =  ...
```

**Behavior**: returns inverse hyperbolic tangent of `a`.

**Usage**

```Clean
// Language: Clean

atanh   2.5   //  #NAN
atanh   1.5   //  #NAN
atanh   0.5   //  0.549306144334055
atanh   0.0   //  0.0
atanh (-0.5)  // -0.549306144334055
atanh (-1.5)  //  #NAN
atanh (-2.5)  //  #NAN
```

---

## Property Functions

### `isNaN`

**Signature**

```Clean
// Language: Clean

isNaN :: Real -> Bool
isNaN    a    =  ...
```

**Behavior**: returns true if `a` is not representable.

**Usage**

```Clean
// Language: Clean

isNaN  2.0               // False
isNaN  0.0               // False
isNaN (sqrt (-1.0))      // True
isNaN (ln   (-1.0))      // True
isNaN ((-1.0) /   0.0)   // False
isNaN (  0.0  ^ (-1.0))  // False
```

### `isInfinity`

**Signature**

```Clean
// Language: Clean

isInfinity :: Real -> Bool
isInfinity    a    =  ...
```

**Behavior**: returns true if `a` is too large to represent.

**Usage**

```Clean
// Language: Clean

isInfinity 2.0                // False
isInfinity 0.0                // False
isInfinity (sqrt (-1.0))      // False
isInfinity (ln   (-1.0))      // False
isInfinity ((-1.0) /   0.0)   // True
isInfinity (  0.0  ^ (-1.0))  // True
```

### `isFinite`

**Signature**

```Clean
// Language: Clean

isFinite :: Real -> Bool
isFinite    a    =  ...
```

**Behavior**: returns true if `a` is representable.

**Usage**

```Clean
// Language: Clean

isFinite 2.0                // True
isFinite 0.0                // True
isFinite (sqrt (-1.0))      // False
isFinite (ln   (-1.0))      // False
isFinite ((-1.0) /   0.0)   // False
isFinite (  0.0  ^ (-1.0))  // False
```

---

## Conversions To Real Number Type

Explicitly converts other types to real number type.

### From Integer Type

**Signature**

```Clean
// Language: Clean

toReal :: Int -> Real
toReal    a   =  ...
```

**Behavior**: converts `a` to a real number.

**Usage**

```Clean
// Language: Clean

toReal   2   //  2.0
toReal   1   //  1.0
toReal   0   //  0.0
toReal (-1)  // -1.0
toReal (-2)  // -2.0
```

### From String Type

**Signature**

```Clean
// Language: Clean

toReal :: String -> Real
toReal    a      =  ...
```

**Behavior**: parses a string `a` to a real number.

**Usage**

```Clean
// Language: Clean

toReal "1.0"   //  1.0
toReal "1"     //  1.0
toReal "0"     //  0.0
toReal "-1"    // -1.0
toReal "-1.0"  //  1.0
```

---

## Conversions From Real Number Type

Explicitly converts real number type to other types.
The desired type must be unambiguous.

### To Integer Type

**Signature**

```
fromReal :: Real -> Int
fromReal    a    =  ...
```

**Behavior**: rounds `a` to its nearest integer.

**Usage**

```Clean
// Language: Clean

expr :: Int
expr =  fromReal   1.9   //  2
expr =  fromReal   1.4   //  1
expr =  fromReal (-1.4)  // -1
expr =  fromReal (-1.9)  // -2
```

### To String Type

**Signature**

```Clean
// Language: Clean

fromReal :: Real -> { #Char }
fromReal    a    =  ...
```

**Behavior**: converts `a` to a string.

**Usage**

```Clean
// Language: Clean

expr :: { #Char }
expr =  fromReal   1.9   // "1.9"
expr =  fromReal   1.4   // "1.4"
expr =  fromReal (-1.4)  // "-1.4"
expr =  fromReal (-1.9)  // "-1.9"
```