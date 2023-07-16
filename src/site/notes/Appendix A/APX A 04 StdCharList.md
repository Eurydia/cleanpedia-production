---
{"dg-publish":true,"permalink":"/appendix-a/apx-a-04-std-char-list/","created":"2023-06-20T18:37:36.390+02:00","updated":"2023-07-16T17:37:11.551+02:00"}
---


# StdCharList
 
## Basic Functions

### `cjustify`

**Signature**

$$
\begin{align*}
n\rightarrow{A}\rightarrow{R}
\end{align*}
$$

where:
- $n$ is of type $\textbf{Int}$, and
- $A$ and $R$ are of type $[\textbf{Char}]$.

**Behavior**: center-aligns $A$ with left and right spaces.

**Usage**

```
// Language: Clean

cjustify 5 ['a', 'b', 'c']  // [' ', 'a', 'b', 'c', ' ']
cjustify 5 ['a', 'b']       // [' ', 'a', 'b', ' ', ' ']
cjustify 3 ['a', 'b']       // ['a', 'b', ' ']
cjustify 3 ['a']            // [' ', 'a', ' ']
cjustify 1 ['a', 'b']       // ['a', 'b']
```

### `ljustify`

**Signature**

$$
\begin{align*}
n\rightarrow{A}\rightarrow{R}
\end{align*}
$$

where:
- $n$ is of type $\textbf{Int}$, and
- $A$ and $R$ are of type $[\textbf{Char}]$.

**Behavior**: left-aligns $A$ with spaces.

**Usage**

```
// Language: Clean

ljustify 5 ['a', 'b', 'c']  // ['a', 'b', 'c', ' ', ' ']
ljustify 5 ['a', 'b']       // ['a', 'b', ' ', ' ', ' ']
ljustify 3 ['a', 'b']       // ['a', 'b', ' ']
ljustify 3 ['a']            // ['a', ' ', ' ']
ljustify 1 ['a', 'b']       // ['a', 'b']
```

### `rjustify`

**Signature**

$$
\begin{align*}
n\rightarrow{A}\rightarrow{R}
\end{align*}
$$

where:
- $n$ is of type $\textbf{Int}$, and
- $A$ and $R$ are of type $[\textbf{Char}]$.

**Behavior**: right-aligns $A$ with spaces.

**Usage**

```
// Language: Clean

rjustify 5 ['a', 'b', 'c']  // [' ', ' ', 'a', 'b', 'c']
rjustify 5 ['a', 'b']       // [' ', ' ', 'a', 'b']
rjustify 3 ['a', 'b']       // [' ', 'a', 'b']
rjustify 3 ['a']            // [' ', ' ', 'a']
rjustify 1 ['a', 'b']       // ['a', 'b']
```

### `flatlines`

**Signature**

$$
\begin{align*}
{A}\rightarrow{R}
\end{align*}
$$

where:
- $n$ is of type $\textbf{Int}$, and
- $A$ and $R$ are of type $[\textbf{Char}]$.

**Behavior**: joins elements of $A$ with newline characters.

**Usage**

```
// Language: Clean

flatlines [['a'], ['b']]  // ['a', '\n', 'b', '\n']
flatlines ['a']           // ['a', '\n']
flatlines []              // []
```

### `mklines`

**Signature**

$$
\begin{align*}
A\rightarrow{R}
\end{align*}
$$

where:
- $n$ is of type $\textbf{Int}$,
- $A$ is of type $[\textbf{Char}]$, and
- $R$ is of type $[[\textbf{Char}\|\textbf{Char}]]$.

**Behavior**: splits $A$ at newline characters.

**Usage**

```
// Language: Clean

mklines ['a', '\n', 'b', '\n']  // [['a'], ['b']]
mklines ['a', '\n']             // [['a']]
mklines []                      // []
```
