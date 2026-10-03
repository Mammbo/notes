---
tags: [linear-algebra, lecture]
lecture: 3
---

# Lecture 4 — Matrix Algebra & Linear Transformations

## Matrix Algebra

**Rank:** The rank of $A$ is the number of leading 1's in $\text{rref}(A)$.

**Entrywise operations:** Matrices of the same size can be added and subtracted entrywise, and multiplied or divided by a scalar entrywise.

### Matrix–Vector Multiplication

If $A = (a_{ij})$ is an $n \times m$ matrix and $\vec{v} = (b_j)$ is an $m \times 1$ vector, then $A\vec{v}$ is an $n$-dimensional vector:

$$
A\vec{v} =
\begin{pmatrix}
a_{11}b_1 + a_{12}b_2 + \cdots + a_{1m}b_m \\
a_{21}b_1 + a_{22}b_2 + \cdots + a_{2m}b_m \\
\vdots \\
a_{n1}b_1 + a_{n2}b_2 + \cdots + a_{nm}b_m
\end{pmatrix}
$$

Equivalently, the $i$-th entry is

$$
(A\vec{v})_i = \sum_{j=1}^{m} a_{ij} b_j \qquad \text{for } 1 \le i \le n
$$

> [!example]
> $$
> \underbrace{\begin{pmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{pmatrix}}_{3\times 2}
> \underbrace{\begin{pmatrix} 7 \\ 8 \end{pmatrix}}_{2\times 1}
> = \begin{pmatrix} 7 + 16 \\ 21 + 32 \\ 35 + 48 \end{pmatrix}
> = \underbrace{\begin{pmatrix} 23 \\ 53 \\ 83 \end{pmatrix}}_{3\times 1}
> $$

### Systems of Linear Equations as $A\vec{x} = \vec{b}$

A system of linear equations can be written as a matrix equation:

$$
\begin{aligned}
x_1 + 2x_2 &= 5 \\
3x_1 + 4x_2 &= 6
\end{aligned}
\quad \iff \quad
\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
=
\begin{bmatrix} 5 \\ 6 \end{bmatrix}
$$

### Proposition: Matrix Multiplication is Linear

Let $A$ be an $n \times m$ matrix, $\vec{x}, \vec{y} \in \mathbb{R}^m$, and $c \in \mathbb{R}$. Then:

1. $A(\vec{x} + \vec{y}) = A\vec{x} + A\vec{y}$
2. $A(c\vec{x}) = c(A\vec{x})$

i.e. $\vec{x} \mapsto A\vec{x}$ is a **linear operation**.

**Proof of (1).** Let $A = (a_{ij})$, $\vec{x} = (x_1, \dots, x_m)^T$, $\vec{y} = (y_1, \dots, y_m)^T$. Then

$$
A(\vec{x} + \vec{y}) = A \begin{pmatrix} x_1 + y_1 \\ \vdots \\ x_m + y_m \end{pmatrix}
= \begin{pmatrix} \sum_{j=1}^m a_{1j}(x_j + y_j) \\ \vdots \\ \sum_{j=1}^m a_{nj}(x_j + y_j) \end{pmatrix}
$$

and

$$
A\vec{x} + A\vec{y}
= \begin{pmatrix} \sum_{j=1}^m a_{1j}x_j \\ \vdots \\ \sum_{j=1}^m a_{nj}x_j \end{pmatrix}
+ \begin{pmatrix} \sum_{j=1}^m a_{1j}y_j \\ \vdots \\ \sum_{j=1}^m a_{nj}y_j \end{pmatrix}
= \begin{pmatrix} \sum_{j=1}^m a_{1j}(x_j + y_j) \\ \vdots \\ \sum_{j=1}^m a_{nj}(x_j + y_j) \end{pmatrix}
$$

Hence they are equal. $\blacksquare$

**Proof of (2).** Essentially the same as (1). $\blacksquare$

---

## Linear Transformations

### $\mathbb{R}^n$ and Functions

$\mathbb{R}^n$ is the $n$-dimensional vector space — the set of all $n$-dimensional vectors:

$$
\mathbb{R}^n = \left\{ \begin{pmatrix} a_1 \\ \vdots \\ a_n \end{pmatrix} : a_1, \dots, a_n \in \mathbb{R} \right\}
$$

Given two sets $X$ and $Y$, a **function** $f: X \to Y$ is a collection of assignments $f(x) \in Y$ to each $x \in X$.

- $f: \mathbb{R} \to \mathbb{R}$ given by $f(x) = x^2$
- $f: \mathbb{R}^2 \to \mathbb{R}$ given by $f(x, y) = x^2 y + \sin y + e^{-x}$

### Definition: Linear Transformation

> [!definition]
> A function $T: \mathbb{R}^m \to \mathbb{R}^n$ of the form
> $$T(\vec{x}) = A\vec{x}$$
> for some $n \times m$ matrix $A$ is called a **linear transformation**.

> [!example] Identity
> The $2 \times 2$ matrix $A = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$ models a linear map $T: \mathbb{R}^2 \to \mathbb{R}^2$:
> $$T\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} x_1 \\ x_2 \end{pmatrix}$$
> so $T(\vec{x}) = \vec{x}$.

> [!example] $1 \times 2$ matrix
> The $1 \times 2$ matrix $\begin{pmatrix} 2 & 3 \end{pmatrix}$ models a linear map $T: \mathbb{R}^2 \to \mathbb{R}^1 = \mathbb{R}$:
> $$T\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 2 & 3 \end{pmatrix}\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = 2x_1 + 3x_2$$

> [!example] 90° rotation
> $A = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$ gives $T: \mathbb{R}^2 \to \mathbb{R}^2$ by
> $$T\begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} -y \\ x \end{pmatrix}$$
> which rotates every vector $90^\circ$ counterclockwise.

### Systems of Equations as Linear Maps

The system

$$
\begin{aligned}
a_{11}x_1 + \cdots + a_{1m}x_m &= b_1 \\
&\ \ \vdots \\
a_{n1}x_1 + \cdots + a_{nm}x_m &= b_n
\end{aligned}
$$

is modeled by $A\vec{x} = \vec{b}$ with $A$ an $n \times m$ matrix, $\vec{x} \in \mathbb{R}^m$, $\vec{b} \in \mathbb{R}^n$.

Equivalently: define $T: \mathbb{R}^m \to \mathbb{R}^n$ by $T(\vec{x}) = A\vec{x}$. Given $\vec{b} \in \mathbb{R}^n$, solving the system means finding $\vec{x} \in \mathbb{R}^m$ with

$$T(\vec{x}) = \vec{b}$$

### Theorem: Finding the Matrix of a Linear Map

> [!theorem]
> Let $T: \mathbb{R}^m \to \mathbb{R}^n$ be a linear map. Then its matrix is
> $$A = \begin{pmatrix} | & | & & | \\ T(\vec{e}_1) & T(\vec{e}_2) & \cdots & T(\vec{e}_m) \\ | & | & & | \end{pmatrix}$$
> where $\vec{e}_1, \dots, \vec{e}_m$ are the standard basis vectors:
> $$\vec{e}_1 = \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix},\quad \vec{e}_2 = \begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{pmatrix},\quad \dots,\quad \vec{e}_m = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix}$$
> For $2 \times 2$: $\vec{e}_1 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$, $\vec{e}_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$.

**Proof.** Since $T$ is a linear map, by definition there exists an $n \times m$ matrix $A = (a_{ij})$ such that $T(\vec{x}) = A\vec{x}$. Then

$$
T(\vec{e}_1) = \begin{pmatrix} a_{11} & \cdots & a_{1m} \\ \vdots & \ddots & \vdots \\ a_{n1} & \cdots & a_{nm} \end{pmatrix}
\begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix}
= \begin{pmatrix} a_{11} \\ a_{21} \\ \vdots \\ a_{n1} \end{pmatrix}
$$

which is the first column of $A$. Likewise $T(\vec{e}_2) = (a_{12}, a_{22}, \dots, a_{n2})^T$ is the second column, and in general $T(\vec{e}_j)$ is the $j$-th column. $\blacksquare$

> [!example] 90° rotation, revisited
> Let $T: \mathbb{R}^2 \to \mathbb{R}^2$ be $90^\circ$ counterclockwise rotation (assume $T$ is linear). What matrix defines $T$?
> $$T(\vec{e}_1) = T\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \end{pmatrix}, \qquad T(\vec{e}_2) = T\begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} -1 \\ 0 \end{pmatrix}$$
> $$\therefore\ A = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$$

### Theorem: Characterizing Linear Maps

> [!theorem]
> A function $T: \mathbb{R}^m \to \mathbb{R}^n$ is a linear transformation if and only if:
> 1. $T(\vec{u} + \vec{v}) = T(\vec{u}) + T(\vec{v})$ for all $\vec{u}, \vec{v} \in \mathbb{R}^m$
> 2. $T(c\vec{v}) = c\,T(\vec{v})$ for all $\vec{v} \in \mathbb{R}^m$, $c \in \mathbb{R}$

> [!definition] Equivalent definition
> A function $T: \mathbb{R}^m \to \mathbb{R}^n$ is a **linear map** if properties (1) and (2) above hold.

 ![[Lecture 4.pdf]]