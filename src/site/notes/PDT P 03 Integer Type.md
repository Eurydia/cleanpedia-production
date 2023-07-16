---
{"dg-publish":true,"permalink":"/pdt-p-03-integer-type/","created":"2023-07-03T09:26:33.060+02:00","updated":"2023-07-14T21:29:11.422+02:00"}
---


# Integer Type

Integers are represented using 32 bits or 64 bits values.

For built-in functions on integer type, see [[Appendix A/StdInt\|StdInt]] module for additional information.

## Integer Type Declaration

Integer type is explicitly declared with `Int`.

```Clean
// Language: Clean

expr :: Int
expr =  1 + 1
```

## Integer Literals

They can be constructed from decimal notation.

```Clean
// Language: Clean

x :: Int
x = -13
x =  0
x =  13
```

They can be constructed from octal notation by prefixing octal digits with `0`.

```Clean
// Language: Clean

x :: Int
x = -015 // decimal -13
x =  00  // decimal  0
x =  015 // decimal  13
```

And they can be constructed from hexadecimal notation by prefixing hexadecimal digits with `0x`.

```Clean
// Language: Clean

x :: Int
x = -0xD  // decimal -13
x =  0x0  // decimal  0
x =  0xd  // decimal  13
```

## Using Integer Literal as Pattern


### Example A

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    1   =  True
exampleA    _   =  False
```

The `exampleA` function has two equivalent variants.

One variant is obtained by using octal notation instead of decimal notation.

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    01  =  True
exampleA    _   =  False
```

And another variant is obtained by using hexadecimal notation.

```Clean
// Language: Clean

exampleA :: Int -> Bool
exampleA    0x1 =  True
exampleA    _   =  False
```

Python equivalent:

```Python
# Python

def exampleA(arg: int) -> bool
	match arg:
		case 1:
			return True
		case _:
			return False
```

### Example B

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   0   =  x
exampleB    0   y   =  y
exampleB    x   y   =  x + y
```

The `exampleB` function has many equivalent variants.

A variant is obtained by using octal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   00  =  x
exampleB    00  y   =  y
exampleB    x   y   =  x + y
```

A variant is obtained by using hexadecimal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   0x0 =  x
exampleB    0x0 y   =  y
exampleB    x   y   =  x + y
```

A variant is obtained by mixing octal notation and hexadecimal notation.

```Clean
// Language: Clean

exampleB :: Int Int -> Int
exampleB    x   00  =  x
exampleB    0x0 y   =  y
exampleB    x   y   =  x + y
```

Python equivalent:

```Python
# Python

def exampleB(
	argA: int,
	argB: int
) -> int:
	match (argA, argB):
		case (x, 0):
			return x
		case (0, y):
			return y
		case _:
			return x + y
```