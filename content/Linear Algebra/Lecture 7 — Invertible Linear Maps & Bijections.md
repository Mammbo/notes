## Recall

$T:\mathbb{R}^m\to\mathbb{R}^n$, $S:\mathbb{R}^p\to\mathbb{R}^m$, so $T\circ S:\mathbb{R}^p\to\mathbb{R}^n$.

- $T \leftrightarrow A$: $n\times m$
- $S \leftrightarrow B$: $m\times p$
- $T\circ S \leftrightarrow AB$: $n\times p$

Equivalently, for $A=(a_{ij})$, $B=(b_{jk})$: $$AB = \left(\sum_{j=1}^m a_{ij}b_{jk}\right)$$

### Properties of matrix multiplication

- $(AB)C = A(BC)$
- **But** $AB\neq BA$ in general
- $(A_1+A_2)B = A_1B + A_2B$
- $A(B_1+B_2) = AB_1 + AB_2$
- $c(AB) = (cA)B = A(cB)$
- $I_nA = A$, $AI_m = A$

---

## Invertible Linear Maps

> [!abstract] Def A linear map $T:\mathbb{R}^m\to\mathbb{R}^n$ is **invertible** if it is bijective. A matrix $A$ is invertible if its associated linear map $T_A:\mathbb{R}^m\to\mathbb{R}^n$ is invertible.

> [!note] Prop
> 
> 1. If $T:\mathbb{R}^m\to\mathbb{R}^n$ is an invertible linear map, then $m=n$.
> 2. If $A$: $n\times m$ is invertible, then $m=n$.

> [!note] Prop If $T:\mathbb{R}^n\to\mathbb{R}^n$ is an invertible linear map with inverse function $T^{-1}$, then $T^{-1}$ is a linear map.

**Proof.** Need $T^{-1}(\vec u+\vec v) = T^{-1}(\vec u)+T^{-1}(\vec v)$ and $T^{-1}(c\vec v) = cT^{-1}(\vec v)$.

By bijectivity and linearity of $T$: $$\vec u+\vec v = T(T^{-1}(\vec u)) + T(T^{-1}(\vec v)) = T\big(T^{-1}(\vec u)+T^{-1}(\vec v)\big)$$ Apply $T^{-1}$ to both sides: $$T^{-1}(\vec u+\vec v) = T^{-1}\Big(T\big(T^{-1}(\vec u)+T^{-1}(\vec v)\big)\Big) = T^{-1}(\vec u)+T^{-1}(\vec v)$$ The scalar case is similar. $\blacksquare$

> [!abstract] Def (Inverse matrix) $A$: $n\times n$ invertible $\implies T_A:\mathbb{R}^n\to\mathbb{R}^n$ invertible $\implies (T_A)^{-1}:\mathbb{R}^n\to\mathbb{R}^n$ is linear. Define $A^{-1}$ to be the matrix of $(T_A)^{-1}$.

> [!note] Prop $A$: $n\times n$ invertible. Then $AA^{-1} = I_n$ and $A^{-1}A = I_n$.

**Proof.** $T_A\circ (T_A)^{-1}$ is the identity function, i.e. $T_A(T_A^{-1}(\vec v)) = \vec v$. Similarly $(T_A)^{-1}\circ T_A$ is the identity. $\blacksquare$

> [!abstract] Alt. Def An $n\times n$ matrix $A$ is invertible if there exists $B$: $n\times n$ such that $AB = I_n$ and $BA = I_n$.

**Ex.** $A = \begin{pmatrix}1&2\3&4\end{pmatrix}$. Is $A$ invertible? If so, compute $A^{-1}$. _(left open)_

### Why we care

If $T$ (or $A$) is invertible, apply $T^{-1}$ to both sides: $$T(\vec x) = \vec b \implies T^{-1}(T(\vec x)) = T^{-1}(\vec b) \implies \vec x = T^{-1}(\vec b)$$ which is the **unique** solution. Next step: how to compute the inverse.

---

## Bijective Functions

> [!abstract] Def $f:X\to Y$ is **bijective** if for every $y\in Y$ there exists a **unique** $x\in X$ with $f(x)=y$.

i.e. every $y$ is hit, and by exactly one $x$ — a 1:1 correspondence between $X$ and $Y$.

If $f$ is bijective, its **inverse** $f^{-1}:Y\to X$ is $$f^{-1}(y) = \text{the unique } x\in X \text{ with } f(x)=y$$

**Ex.** $X={1,2,3,4}$, $Y={a,b,c,d}$, $f(1)=b,\ f(2)=c,\ f(3)=d,\ f(4)=a$. Bijective, so $$f^{-1}(a)=4,\quad f^{-1}(b)=1,\quad f^{-1}(c)=2,\quad f^{-1}(d)=3$$

> [!note] Prop $f:X\to Y$ bijective with inverse $f^{-1}$. Then
> 
> 1. $f^{-1}(f(x)) = x\ \ \forall x\in X$ and $f(f^{-1}(y)) = y\ \ \forall y\in Y$
> 2. $f^{-1}$ is bijective and $(f^{-1})^{-1} = f$

> [!note] Prop $f:X\to Y$ is bijective $\iff$ there exists $g:Y\to X$ with $g(f(x)) = x$ and $f(g(y)) = y$.

**Proof.** ($\Rightarrow$) $g = f^{-1}$ works.

($\Leftarrow$) Suppose such $g$ exists.

- _Uniqueness:_ if $f(x)=y$, apply $g$: $g(f(x)) = g(y) \implies x = g(y)$.
- _Existence:_ given $y$, $x = g(y)$ satisfies $f(x) = f(g(y)) = y$. $\blacksquare$

---

## Propositions

> [!note] Thm $T:\mathbb{R}^n\to\mathbb{R}^n$ linear. If $T$ is invertible, then every $T(\vec x)=\vec b$ has the unique solution $\vec x = T^{-1}(\vec b)$.

> [!note] Prop $A, B$: $n\times n$ invertible. Then $AB$ is invertible and $$(AB)^{-1} = B^{-1}A^{-1}$$

**Proof.** Suffices to show $(AB)(B^{-1}A^{-1}) = I_n$ and $(B^{-1}A^{-1})(AB) = I_n$. $$(AB)(B^{-1}A^{-1}) = A(BB^{-1})A^{-1} = AI_nA^{-1} = AA^{-1} = I_n$$ The second is computed similarly. $\blacksquare$