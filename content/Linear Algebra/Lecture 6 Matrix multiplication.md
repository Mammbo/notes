
## Recall
A linear map $T:\mathbb{R}^m \to \mathbb{R}^n$ is of the form $T(\vec{x}) = A\vec{x}$.

- Linear map $=$ matrix
- Special (geometrically meaningful) linear maps $T:\mathbb{R}^2\to\mathbb{R}^2$ ↔ special $2\times2$ matrices

### Special $2\times 2$ maps
**Scale** by $k$:
$$\begin{pmatrix} k & 0 \\ 0 & k \end{pmatrix}$$

**Orthogonal projection** $\text{proj}_L:\mathbb{R}^2\to\mathbb{R}^2$, where $\begin{pmatrix} a \\ b\end{pmatrix}$ is the direction vector of $L$:
$$\frac{1}{a^2+b^2}\begin{pmatrix} a^2 & ab \\ ab & b^2 \end{pmatrix}$$

**Reflection** $\text{ref}_L:\mathbb{R}^2\to\mathbb{R}^2$:
$$\frac{1}{a^2+b^2}\begin{pmatrix} a^2-b^2 & 2ab \\ 2ab & -a^2+b^2 \end{pmatrix}$$

**Rotation** $\text{rot}_\theta:\mathbb{R}^2\to\mathbb{R}^2$:
$$\underbrace{\begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}}_{\text{counterclockwise}} \qquad \underbrace{\begin{pmatrix} \cos\theta & \sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix}}_{\text{clockwise}}$$

### Ex: Chaining linear maps
$$\mathbb{R}^2 \xrightarrow{\text{rot}_{45}} \mathbb{R}^2 \xrightarrow{\text{scale}_2} \mathbb{R}^2$$
$$
\begin{aligned}
\text{scale}_2\!\left(\text{rot}_{45}\begin{pmatrix} x\\y\end{pmatrix}\right)
&= \text{scale}_2\!\left(\begin{pmatrix} \tfrac{1}{\sqrt2} & -\tfrac{1}{\sqrt2} \\ \tfrac{1}{\sqrt2} & \tfrac{1}{\sqrt2}\end{pmatrix}\begin{pmatrix} x\\y\end{pmatrix}\right)
= \text{scale}_2\begin{pmatrix} \tfrac{1}{\sqrt2}x - \tfrac{1}{\sqrt2}y \\ \tfrac{1}{\sqrt2}x + \tfrac{1}{\sqrt2}y \end{pmatrix} \\
&= \begin{pmatrix} 2 & 0 \\ 0 & 2\end{pmatrix}\begin{pmatrix} \tfrac{1}{\sqrt2}x - \tfrac{1}{\sqrt2}y \\ \tfrac{1}{\sqrt2}x + \tfrac{1}{\sqrt2}y \end{pmatrix}
= \begin{pmatrix} \sqrt2 x - \sqrt2 y \\ \sqrt2 x + \sqrt2 y\end{pmatrix}
= \begin{pmatrix} \sqrt2 & -\sqrt2 \\ \sqrt2 & \sqrt2\end{pmatrix}\begin{pmatrix} x\\y\end{pmatrix}
\end{aligned}
$$

---

## Matrix Products

Let $T:\mathbb{R}^m\to\mathbb{R}^n$, $S:\mathbb{R}^p\to\mathbb{R}^m$ be linear maps. Then
$$T\circ S:\mathbb{R}^p \xrightarrow{S} \mathbb{R}^m \xrightarrow{T} \mathbb{R}^n, \qquad (T\circ S)(\vec{x}) \equiv T(S(\vec{x}))$$

> [!note] Prop
> If $T:\mathbb{R}^m\to\mathbb{R}^n$ and $S:\mathbb{R}^p\to\mathbb{R}^m$ are linear maps, then $T\circ S:\mathbb{R}^p\to\mathbb{R}^n$ is a linear map.

**Proof.** Recall: $T$ is linear iff
1. $T(\vec u+\vec v) = T(\vec u)+T(\vec v)$
2. $T(c\vec v) = cT(\vec v)$

So need $(T\circ S)(\vec u+\vec v) = (T\circ S)(\vec u)+(T\circ S)(\vec v)$ and $(T\circ S)(c\vec v) = c(T\circ S)(\vec v)$ for all $\vec u,\vec v\in\mathbb{R}^p$.
$$
\begin{aligned}
(T\circ S)(\vec u+\vec v) &= T(S(\vec u+\vec v)) = T(S(\vec u)+S(\vec v)) = T(S(\vec u)) + T(S(\vec v)) = (T\circ S)(\vec u)+(T\circ S)(\vec v) \\
(T\circ S)(c\vec v) &= T(S(c\vec v)) = T(cS(\vec v)) = cT(S(\vec v)) = c(T\circ S)(\vec v) \qquad \blacksquare
\end{aligned}
$$

> [!note] Prop
> If $T$ has matrix $A=(a_{ij})$ ($n\times m$) and $S$ has matrix $B=(b_{jk})$ ($m\times p$), then $T\circ S:\mathbb{R}^p\to\mathbb{R}^n$ has matrix
> $$\left(\sum_{j=1}^m a_{ij}b_{jk}\right), \quad 1\le i\le n,\ 1\le k\le p$$

**Proof (sketch).** Compute $(T\circ S)(\vec e_k) = T(S(\vec e_k)) = T\begin{pmatrix} b_{1k}\\ \vdots \\ b_{mk}\end{pmatrix}$; the rest is verbose computation.

### Definition
For $A=(a_{ij})$ ($n\times m$) and $B=(b_{jk})$ ($m\times p$):
$$A\cdot B = \left(\sum_{j=1}^m a_{ij}b_{jk}\right) \quad (n\times p)$$

**Reason:** if $A\leftrightarrow T$ and $B\leftrightarrow S$, then $A\cdot B \leftrightarrow T\circ S$.

**Rule:** entry $(i,k)$ of $AB$ = row $i$ of $A$ · column $k$ of $B$. Inner dimensions must match.

### Examples
$A = \begin{pmatrix}1&2&3\end{pmatrix}$ ($1\times3$), $B = \begin{pmatrix}4\\5\\6\end{pmatrix}$ ($3\times1$):
$$AB = 1\cdot4+2\cdot5+3\cdot6 = 4+10+18 = 32$$
$$BA = \begin{pmatrix}4\\5\\6\end{pmatrix}\begin{pmatrix}1&2&3\end{pmatrix} = \begin{pmatrix}4&8&12\\5&10&15\\6&12&18\end{pmatrix}$$

$A = \begin{pmatrix}1&2\\3&4\\5&6\end{pmatrix}$ ($3\times2$), $B = \begin{pmatrix}7&8&9&10\\11&12&13&14\end{pmatrix}$ ($2\times4$):
$$AB = \begin{pmatrix}
1\cdot7+2\cdot11 & 1\cdot8+2\cdot12 & 1\cdot9+2\cdot13 & 1\cdot10+2\cdot14\\
3\cdot7+4\cdot11 & 3\cdot8+4\cdot12 & 3\cdot9+4\cdot13 & 3\cdot10+4\cdot14\\
5\cdot7+6\cdot11 & 5\cdot8+6\cdot12 & 5\cdot9+6\cdot13 & 5\cdot10+6\cdot14
\end{pmatrix}
= \begin{pmatrix}29&32&35&38\\65&72&79&86\\101&112&123&134\end{pmatrix}$$

$BA$: $(2\times4)(3\times2)$, $4\neq3$ → undefined.

**$AB \neq BA$:** $A = \begin{pmatrix}1&2\\3&4\end{pmatrix}$, $B = \begin{pmatrix}5&6\\7&8\end{pmatrix}$
$$AB = \begin{pmatrix}5+14 & 6+16\\15+28 & 18+32\end{pmatrix} = \begin{pmatrix}19&22\\43&50\end{pmatrix}, \qquad
BA = \begin{pmatrix}5+18 & 10+24\\7+24 & 14+32\end{pmatrix} = \begin{pmatrix}23&34\\31&46\end{pmatrix}$$

> [!important] Conclusion
> $AB \neq BA$ in general.

---

## Properties

> [!note] Prop (Associativity)
> $A$: $n\times m$, $B$: $m\times p$, $C$: $p\times q$. Then $(AB)C = A(BC)$.

**Proof.** Let $T:\mathbb{R}^m\to\mathbb{R}^n$, $S:\mathbb{R}^p\to\mathbb{R}^m$, $P:\mathbb{R}^q\to\mathbb{R}^p$ be the linear maps for $A,B,C$. Then $AB\leftrightarrow T\circ S$, so
$$(AB)C \leftrightarrow (T\circ S)\circ P, \qquad A(BC)\leftrightarrow T\circ(S\circ P)$$
which are the same map. $\blacksquare$

> [!note] Prop (Distributivity)
> $A_1,A_2$: $n\times m$, $B$: $m\times p$. Then $(A_1+A_2)B = A_1B + A_2B$.

> [!note] Prop (Scalars)
> $A$: $n\times m$, $B$: $m\times p$, $c\in\mathbb{R}$. Then $A(cB) = (cA)B = c(AB)$.

### Special matrices
**Zero matrix** ($n\times m$): all entries $0$.

**Identity matrix** $I_n$ ($n\times n$):
$$I_n = \begin{pmatrix}1&0&\cdots&0\\0&1&\cdots&0\\\vdots&&\ddots&\vdots\\0&0&\cdots&1\end{pmatrix}$$

> [!note] Prop
> $A$: $n\times m$. Then $I_nA = A$ and $AI_m = A$.


![[Lecture 6 mat multiplication.pdf]]