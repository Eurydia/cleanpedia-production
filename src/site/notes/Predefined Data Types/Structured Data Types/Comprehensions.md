---
{"dg-publish":true,"permalink":"/predefined-data-types/structured-data-types/comprehensions/","created":"2023-07-13T21:50:18.970+02:00","updated":"2023-07-13T22:27:40.805+02:00"}
---


# Comprehensions

They provide an alternative way to implicitly construct lists and arrays, but they cannot be used as a pattern.

In this note, comprehensions are used to construct lazy lists.
However, any type of list or array can be constructed.

## Example A: Simple Generators

Comprehensions iterate over a generator, which is an existing list or array.
In each iteration, an element is extracted from the generator.

A left arrow (`<-`) is used to extract elements from a list generator.

```Clean
// Language: Clean

listA :: [ T ]
listA =  [ e \\ e <- lsGen ]
```

To extract elements from an array generator, a colon (`:`) must be added to the end.

```Clean
// Language: Clean

listA :: [ T ]
listA =  [ e \\ e <-: arrGen ]
```

Python equivalent:

```Python
# Language: Python

listA: list[any] = []
for e in lsGen:
	lista.append(e)
```

## Example B: Nesting Generators

Commas (`,`) are used to join generators by nesting.
The right-most generator is the fastest.

```Clean
// Language: Clean

listB :: [ ( T, K ) ]
listB =  [ ( eX, eY ) \\ 
    eX <- lsGenX , 
    eY <- lsGenY 
]
```

Python equivalent:

```Python
# Language: Python

listB: list[tuple[any, any]] = []
for eX in lsGenX:
	for eY in lsGenY:
		listB.append((eX, eY))
```

## Example C: Zipping Generators

Ampersands (`&`) are used to join generators by zipping.
Iteration stops as soon as one generator runs out of element.

```Clean
// Language: Clean

listC :: [ ( T, K ) ]
listC =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY
]
```

Python equivalent:

```Python
# Language: Python

listC: list[tuple[any, any]] = []
for eX, eY in zip(lsGenX, lsGenY):
	listC.append((eX, eY))
```

## Example D: Nesting and Zipping Generators

Ampersands bind more tightly than commas when joining generators.

### Example Da

```Clean
// Langauge: Clean

listDa :: [ ( T, K, V ) ]
listDa =  [ ( eX, eY, eZ ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY , 
    eZ <- lsGenZ
]
```

Python equivalent:

```Python
# Language: Python

listDa: list[tuple[any, any, any]] = []
for eX, eY in zip(lsGenX, lsGenY):
	for eZ in lsGenZ:
		listDa.append((eX, eY, eZ))
```

### Example Db

```Clean
// Langauge: Clean

listDb :: [ ( T, K, V ) ]
listDb =  [ ( eX, eY, eZ ) \\ 
    eX <- lsGenX , 
    eY <- lsGenY & 
    eZ <- lsGenZ 
]
```

Python equivalent:

```Python
# Language: Python

listDb: list[tuple[any, any, any]] = []
for eX in lsGenX:
	for eY, eZ in zip(lsGenY, lsGenZ):
		listDb.append((eX, eY, eZ))
```

## Example E: Conditional Iteration

A condition can be introduced after each generator.
An iteration is skipped if it fails to satisfy the condition.

```Clean
// Langauge: Clean

listEa :: [ T ]
listEa =  [ e \\ e <- lsGen | pred e ]
```

Python equivalent:

```Python
# Language: Python

listEa: list[any] = []
for e in lsGen:
	if not pred(e):
		continue
	listEa.append(e)
```

## Example F: Conditional Iteration in Nested Generators

Each nested generator can have its own condition.

### Example Fa

```Clean
// Langauge: Clean

listFa :: [ ( T, K ) ]
listFa =  [ ( eX, eY ) \\ 
    eX <- lsGenX | predX eX , 
    eY <- lsGenY | predY eY
]
```

Python equivalent:

```Python
# Language: Python

listFa: list[tuple[any, any]] = []
for eX in lsGenX:
	if not predX(eX):
		continue
	for eY in lsGenY:
		if not predY(eY):
			continue
		listFa.append((eX, eY))
```

### Example Fb

```Clean
// Langauge: Clean

listFb :: [ ( T, K ) ]
listFb =  [ ( eX, eY ) \\ 
    eX <- lsGenX | predX eX , 
    eY <- lsGenY | predY eX eY
]
```

Python equivalent:

```Python
# Language: Python

listFb: list[tuple[any, any]] = []
for eX in lsGenX:
	if not predX(eX):
		continue
	for eY in lsGenY:
		if not predY(eX, eY):
			continue
		listFb.append((eX, eY))
```

## Example G: Conditional Iteration in Zipped Generators

Zipped generators can only have a condition.

### Example Ga

```Clean
// Langauge: Clean

listGa :: [ ( T, K ) ]
listGa =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY | pred eX 
]
```

Python equivalent:

```Python
# Language: Python

listGa: list[tuple[any, any]] = []
for eX, Ey in zip(lsGenX, lsGenY):
	if not predY(eX):
		continue
	listGa.append((eX, eY))
```

### Example Gb

```Clean
// Langauge: Clean

listGb :: [ ( T, K ) ]
listGb =  [ ( eX, eY ) \\ 
    eX <- lsGenX & 
    eY <- lsGenY | pred eX eY
]
```

Python equivalent:

```Python
# Language: Python

listGb: list[tuple[any, any]] = []
for eX, Ey in zip(lsGenX, lsGenY):
	if not predY(eX, eY):
		continue
	listGb.append((eX, eY))
```