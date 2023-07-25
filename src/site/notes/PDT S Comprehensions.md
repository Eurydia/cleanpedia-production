---
{"dg-publish":true,"permalink":"/pdt-s-comprehensions/","created":"2023-07-14T02:50:18.970+07:00","updated":"2023-07-25T13:08:15.124+07:00"}
---


# Comprehensions

They provide an alternative way to implicitly construct lists and arrays, but they cannot be used as a pattern.

While it is possible to construct every types of list or array with comprehension, for simplicity, they are used to construct lazy lists.

Comprehensions iterate over a **generator**, which is an existing list or array.
In each iteration, the left-most element is extracted from the generator.
Its value is stored in a **selector**.

## Usage Examples

### Extracting Elements From Different Kinds of Generators

A left arrow (`<-`) is used to extract elements from a list generator.

```Clean
// Language: Clean

x ::  [ T ]
x = [ e \\ e <- lsGen ]
```

An array generator uses a different arrow which has a colon (`:`) at the end.

```Clean
// Language: Clean

x :: [ T ]
x =  [ e \\ e <-: arrGen ]
```

An overloaded list generator uses an arrow which has a vertical bar (`|`) between the arrow head and the shaft.

```Clean
// Language: Clean

x :: [ T ]
x =  [ e \\ e <|- overloadedLsGen ]
```

Python equivalent:

```Python
# Language: Python

x: list[any] = []
for e in lsGen:
	x.append(e)
```

### Nesting Generators

Commas (`,`) are used to join generators by nesting.
The right-most generator is the fastest.

```Clean
// Language: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX , 
    eY <- lsGenY 
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eX in lsGenX:
	for eY in lsGenY:
		x.append((eX, eY))
```

### Zipping Generators

Ampersands (`&`) are used to join generators by zipping.
Iteration stops as soon as one generator runs out of element.

```Clean
// Language: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eX, eY in zip(lsGenX, lsGenY):
	x.append((eX, eY))
```

### Nesting and Zipping Generators

Ampersands bind more tightly than commas when joining generators.

Example 1:

```Clean
// Langauge: Clean

x :: [ ( T, K, V ) ]
x =  [ ( eX, eY, eZ ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY , 
    eZ <- lsGenZ
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any, any]] = []
for eX, eY in zip(lsGenX, lsGenY):
	for eZ in lsGenZ:
		x.append((eX, eY, eZ))
```

Example 2:

```Clean
// Langauge: Clean

x :: [ ( T, K, V ) ]
x =  [ ( eX, eY, eZ ) \\ 
    eX <- lsGenX , 
    eY <- lsGenY & 
    eZ <- lsGenZ 
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any, any]] = []
for eX in lsGenX:
	for eY, eZ in zip(lsGenY, lsGenZ):
		x.append((eX, eY, eZ))
```

### Conditional Iteration

A condition can be introduced after each generator.
An iteration is skipped if it fails to satisfy the condition.

```Clean
// Langauge: Clean

x :: [ T ]
x =  [ e \\ e <- lsGen | pred e ]
```

Python equivalent:

```Python
# Language: Python

x: list[any] = []
for e in lsGen:
	if not pred(e):
		continue
	x.append(e)
```

### Conditional Iteration in Nested Generators

Each nested generator can have its own condition.

Example 1:

```Clean
// Langauge: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX | predX eX , 
    eY <- lsGenY | predY eY
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eX in lsGenX:
	if not predX(eX):
		continue
	for eY in lsGenY:
		if not predY(eY):
			continue
		x.append((eX, eY))
```

Example 2:

```Clean
// Langauge: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX | predX eX , 
    eY <- lsGenY | predY eX eY
]
```

Python equivalent:

```Python
# Language: Python`

x: list[tuple[any, any]] = []
for eX in lsGenX:
	if not predX(eX):
		continue
	for eY in lsGenY:
		if not predY(eX, eY):
			continue
		x.append((eX, eY))
```

### Conditional Iteration in Zipped Generators

A group of zipped generators can only have a condition.

Example 1:

```Clean
// Langauge: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY | pred eX 
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eX, Ey in zip(lsGenX, lsGenY):
	if not predY(eX):
		continue
	x.append((eX, eY))
```

Example 2:

```Clean
// Langauge: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY | pred eX eY
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eX, eY in zip(lsGenX, lsGenY):
	if not predY(eX, eY):
		continue
	x.append((eX, eY))
```

Example 3:

```Clean
// Langauge: Clean

x :: [ ( T, K ) ]
x =  [ ( eX, eY ) \\ 
    eW <- lsGenW & 
    eX <- lsGenX | predWX eW eX ,
    eY <- lsGenY &
    eZ <- lsGenZ | predYZ eY eZ
]
```

Python equivalent:

```Python
# Language: Python

x: list[tuple[any, any]] = []
for eW, eX in zip(lsGenW, lsGenX):
	if not predWX(eW, eX):
		continue
	for eW, eX in zip(lsGenW, lsGenX):
		if not predYZ(eY, eZ):
			continue
		x.append((eX, eY))
```

## Additional Usage Examples

### Conversion Between List and Array

Conversion between a lazy list and a lazy array can be done with comprehension.

Example 1:

```Clean
// Language: Clean

xList :: [ T ]
xList =  [ e \\ e <-: xArr ] 
```

Example 2:

```Clean
// Language: Clean

xArr :: { T }
xArr =  { e \\ e <- xList } 
```