---
{"dg-publish":true,"permalink":"/appendix-a/std-char/","created":"2023-06-20T18:37:36.390+02:00","updated":"2023-07-07T23:25:57.798+02:00"}
---


# StdChar

The `StdChar` module contains definitions for operations and functions relating to real number type. 

When imported, this module allows for:
- addition and subtraction between characters,
- comparison between characters,
- character manipulation,
- property testing, and
- conversion to and from character type.

Visit [StdChar](https://cloogle.org/src/#base-stdenv/StdChar;icl;line=1) on Cloogle for source code of this module.

## Constants

### Zero Unit

**Implementation**

```Clean
// Language: Clean

zero ::  Char
zero :== (toChar 0)
```

**Definition**: represents a character with ASCII value of zero.

### One Unit

**Implementation**

```Clean
// Language: Clean

one ::  Char
one :== (toChar 1)
```

**Definition**: represents a character with ASCII value of one.

---

## Arithmetic Operations

Two arithmetic operations are available on character type.
They are rarely used due to their implementations.

### Addition

**Signature**

```Clean
// Language: Clean

(+) infixl 6 :: Char Char -> Char
(+)             a    b    => ...
```

**Behavior**: converts `a` and `b` to integers, then the result of their addition is converted back to a character.

**Usage**

```Clean
// Language: Clean

'1' + '1'  // 49 + 49 ->  98 ('b')
'A' + 'A'  // 65 + 65 -> 130 ('é')
'a' + 'a'  // 97 + 97 -> 194 ('┬')
```

### Subtraction

**Signature**

```Clean
// Language: Clean

(-) infixl 6 :: Char Char -> Char
(-)             a    b    => ...
```

**Behavior**: converts `a` and `b` to integers, then the result of their subtraction is converted back to a character.

**Usage**

```Clean
// Language: Clean

'z' - '0'  // 122 - 48 -> 74 ('J')
'z' - '1'  // 122 - 49 -> 73 ('I')
'z' - '2'  //  97 + 50 -> 72 ('H')
```

---

## Relational Operations

Characters are compared based on their ASCII value.

### Equal To

**Signature**

```Clean
// Language: Clean

(==) infix 4 :: Char Char -> Bool
(==)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is equal to ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' == 'A'  // False
'a' == '1'  // False
'A' == 'a'  // False
'1' == '1'  // True
```

### Not Equal To

**Signature**

```Clean
// Language: Clean

(<>) infix 4 :: Char Char -> Bool
(<>)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is not equal to ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' <> 'A'  // True
'a' <> '1'  // True
'A' <> 'a'  // True
'1' <> '1'  // False
```

### Less Than

**Signature**

```Clean
// Language: Clean

(<) infix 4 :: Char Char -> Bool
(<)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is strictly less than ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' < 'A'  // True
'a' < '1'  // False
'A' < 'a'  // True
'1' < '1'  // False
```

### Less Than Or Equal To

**Signature**

```Clean
// Language: Clean

(<=) infix 4 :: Char Char -> Bool
(<=)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is less than or equal to ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' <= 'A'  // True
'a' <= '1'  // False
'A' <= 'a'  // True
'1' <= '1'  // True
```

### Greater Than

**Signature**

```Clean
// Language: Clean

(>) infix 4 :: Char Char -> Bool
(>)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is strictly greater than ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' > 'A'  // False
'a' > '1'  // True
'A' > 'a'  // False
'1' > '1'  // False
```

### Greater Than Or Equal To

**Signature**

```Clean
// Language: Clean

(>=) infix 4 :: Char Char -> Bool
(>=)            a    b    => ...
```

**Behavior**: returns true if ASCII value of `a` is greater than or equal to ASCII value of `b`.

**Usage**

```Clean
// Language: Clean

'1' >= 'A'  // False
'a' >= '1'  // True
'A' >= 'a'  // False
'1' >= '1'  // True
```

---

## Manipulation Functions

Manipulates a character.

### `digitToInt`

**Signature**

```Clean
// Language: Clean

digitToInt :: Char -> Int
digitToInt    a    => ...
```

**Behavior**: returns ASCII value of `a` offset by  `-48`.

**Usage**

```Clean
// Language: Clean

toUpper '1'  //  1  (49 - 48)
toUpper 'a'  //  49 (97 - 48)
toUpper 'A'  //  17 (65 - 48)
toUpper '-'  // -3  (45 - 48)
```

### `toUpper`

**Signature**

```Clean
// Language: Clean

toUpper :: Char -> Char
toUpper    a    => ...
```

**Behavior**: returns uppercase of `a`.
If it is not possible, `a` itself is returned instead.

**Usage**

```Clean
// Language: Clean

toUpper '1'  // '1'
toUpper 'a'  // 'A'
toUpper 'A'  // 'A'
toUpper '-'  // '-'
```

### `toLower`

**Signature**

```Clean
// Language: Clean

toLower :: Char -> Char
toLower    a    => ...
```

**Behavior**: returns lowercase of `a`.
If it is not possible, `a` itself is returned instead.

**Usage**

```Clean
// Language: Clean

toLower '1'  // '1'
toLower 'a'  // 'a'
toLower 'A'  // 'a'
toLower '-'  // '-'
```

---

## Property Functions

### `isUpper`

**Signature**

```Clean
// Language: Clean

isUpper :: Char -> Bool
isUpper    a    => ...
```

**Behavior**: returns true if `a` is an uppercase character.

**Usage**

```Clean
// Language: Clean

isUpper '1'  // False
isUpper 'a'  // False
isUpepr 'A'  // True
isUpper '-'  // False
```

### `isLower`

**Signature**

```Clean
// Language: Clean

isLower :: Char -> Bool
isLower    a    => ...
```

**Behavior**: returns true if `a` is a lowercase character.

**Usage**

```Clean
// Language: Clean

isLower '1'  // False
isLower 'a'  // True
isLower 'A'  // False
isLower '-'  // False
```

### `isAlphanum`

**Signature**

```Clean
// Language: Clean

isAlphanum :: Char -> Bool
isAlphanum    a    => ...
```

**Behavior**: returns true if `a` is an alphanumeric character.

**Usage**

```Clean
// Language: Clean

isAlphanum '1'  // True
isAlphanum 'a'  // True
isAlphanum 'A'  // True
isAlphanum '-'  // False
```

### `isAlpha`

**Signature**

```Clean
// Language: Clean

isAlpha :: Char -> Bool
isAlpha    a    => ...
```

**Behavior**: returns true if `a` is an alphabetic character.

**Usage**

```Clean
// Language: Clean

isAlpha '1'  // False
isAlpha 'a'  // True
isAlpha 'A'  // True
isAlpha '-'  // False
```

### `isDigit`

**Signature**

```Clean
// Language: Clean

isDigit :: Char -> Bool
isDigit    a    => ...
```

**Behavior**: returns true if `a` is a decimal digit.

**Usage**

```Clean
// Language: Clean

isDigit '1'  // True
isDigit 'a'  // False
isDigit 'A'  // False
isDigit '-'  // False
```

### `isOctDigit`

**Signature**

```Clean
// Language: Clean

isOctDigit :: Char -> Bool
isOctDigit    a    => ...
```

**Behavior**: returns true if `a` is an octal digit.

**Usage**

```Clean
// Language: Clean

isOctDigit '1'  // True
isOctDigit '8'  // False
isOctDigit 'a'  // False
isOctDigit 'A'  // False
isOctDigit '-'  // False
```

### `isHexDigit`

**Signature**

```Clean
// Language: Clean

isHexDigit :: Char -> Bool
isHexDigit    a    => ...
```

**Behavior**: returns true if `a` is a hexadecimal digit.

**Usage**

```Clean
// Language: Clean

isHexDigit '1'  // True
isHexDigit 'G'  // False
isHexDigit 'a'  // True
isHexDigit 'A'  // True
isHexDigit '-'  // False
```

### `isAscii`

**Signature**

```Clean
// Language: Clean

isAscii :: Char -> Bool
isAscii    a    => ...
```

**Behavior**: returns true if `a` is a 7-bit ASCII character.

See [7-bit ASCII characters](https://en.wikipedia.org/wiki/ASCII) for more information.

**Usage**

```Clean
// Language: Clean

isAscii '1'  // True
isAscii 'a'  // True
isAscii 'A'  // True
isAscii '-'  // True
isAscii 'Ç'  // False
```

### `isControl`

**Signature**

```Clean
// Language: Clean

isControl :: Char -> Bool
isControl    a    => ...
```

**Behavior**: returns true if `a` is a control character.

See [ASCII control characters](https://en.wikipedia.org/wiki/ASCII#Control_characters) for more information.

**Usage**

```Clean
// Language: Clean

isControl '1'   // False
isControl 'a'   // False
isControl 'A'   // False
isControl '-'   // False
isControl '\t'  // True
```

### `isPrint`

**Signature**

```Clean
// Language: Clean

isControl :: Char -> Bool
isControl    a    => ...
```

**Behavior**: returns true if `a` is a printable character.

See [ASCII printable character](https://en.wikipedia.org/wiki/ASCII#Printable_characters) for more information.

**Usage**

```Clean
// Language: Clean

isPrint '1'  // True
isPrint 'a'  // True
isPrint 'A'  // True
isPrint '-'  // True
isPrint '\t' // False
```

### `isSpace`

**Signature**

```Clean
// Language: Clean

isSpace :: Char -> Bool
isSpace    a    => ...
```

**Behavior**: returns true if `a` is a space character.

Space characters includes:

| Glyph  | Name            |
| ------ | --------------- |
| `' '`  | Space           |
| `'\t'` | Horizontal tab  |
| `'\v'` | Vertical tab    |
| `'\n'` | Line feed       |
| `'\r'` | Carriage return |
| `'\f'` | Form feed       |

**Usage**

```Clean
// Language: Clean

isSpace '1'   // False
isSpace 'a'   // False
isSpace 'A'   // False
isSpace '-'   // False
isSpace '\t'  // True
```

---

## Conversions To Character Type

Explicitly converts other types to character type.

### From Integer Type

**Signature**

```Clean
// Language: Clean

toChar :: Int -> Char
toChar    a   => ...
```

**Behavior**: returns an ASCII character whose value is `a`.

**Usage**

```Clean
// Language: Clean

toChar 49  // '1'
toChar 65  // 'A'
toChar 97  // 'a'
```

---

## Conversions From Character Type

Explicitly converts character type to other types.
The desired type must be unambiguous.

### To Integer Type

**Signature**

```Clean
// Language: Clean

fromChar :: Char -> Int
fromChar    a    =>  ...
```

**Behavior**: returns ASCII value of `a`.

**Usage**

```Clean
// Language: Clean

expr :: Int
expr =  fromChar '1'  // 49
expr =  fromChar 'A'  // 65
expr =  fromChar 'a'  // 97
```

### To String Type

**Signature**

```Clean
// Language: Clean

fromChar :: Char -> { #Char }
fromChar    a    => ...
```

**Behavior**: returns a one-character string containing `a`.

**Usage**

```Clean
// Language: Clean

expr :: { #Char }
expr =  fromChar '1'  // "1"
expr =  fromChar 'A'  // "A"
expr =  fromChar 'a'  // "a"
```