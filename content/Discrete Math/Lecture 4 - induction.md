
## Strong Induction

**Regular induction:** assume $P(k)$, prove $P(k+1)$. **Strong induction:** assume $P(1) \land P(2) \land \cdots \land P(k)$, prove $P(k+1)$.

Use it when the next case depends on **more than just the previous one**.

---

## Example 1: Fibonacci $f_n < 2^n$

Recall: $f_1 = f_2 = 1,\quad f_{n+1} = f_n + f_{n-1}$

**Base cases** (need two, since $f$ uses two previous terms):

- $n=1$: $f_1 = 1 < 2^1 = 2$ ✓
- $n=2$: $f_2 = 1 < 2^2 = 4$ ✓

**Inductive step:** Let $n \geq 2$. Assume $f_1 < 2^1 \land f_2 < 2^2 \land \cdots \land f_n < 2^n$.

Need: $f_{n+1} < 2^{n+1} = 2 \cdot 2^n$

$$f_{n+1} = \underbrace{f_n}_{<,2^n} + \underbrace{f_{n-1}}_{<,2^{n-1}} < 2^n + 2^{n-1} < 2^n + 2^n = 2 \cdot 2^n = 2^{n+1} ;\checkmark$$

> [!note] Why strong induction? We assume **both** $f_n < 2^n$ and $f_{n-1} < 2^{n-1}$ (cases $n$ and $n-1$).

---

## Example 2: Prime Factorization

**Theorem:** Every $n \in \mathbb{N},\ n \geq 2$ has a prime factorization

$$n = p_1 \cdot p_2 \cdots p_k \quad (\text{each } p_i \text{ prime})$$

e.g. $12 = 2 \cdot 2 \cdot 3$

**Base case:** $n = 2$ is prime ✓

**Inductive step:** Assume $2, 3, \ldots, n$ all have prime factorizations. Show $n+1$ does.

- **Case 1: $n+1$ is prime.** Its PF is just $(n+1)$ ✓
- **Case 2: $n+1$ is not prime.** By definition, $\exists, m, q$ with $2 \leq m, q < n+1$ and $n+1 = m \cdot q$. By IH, $m$ and $q$ have PFs: $$m = p_1 \cdots p_k, \qquad q = p'_1 \cdots p'_\ell$$ $$\boxed{n+1 = p_1 \cdots p_k \cdot p'_1 \cdots p'_\ell} ;\checkmark$$

> [!note] Why strong induction? $m$ and $q$ can be **any** number below $n+1$, not just $n$.

---

## Sets

**Set:** an **unordered** collection of objects **without repeats**.

|Notation|Meaning|
|---|---|
|$A = {1, 2, 3, 4}$|set with elements 1–4|
|$1 \in A$|1 is **in** $A$|
|$5 \notin A$|5 is **not in** $A$|
|$\lvert A \rvert = 4$|size (cardinality) of $A$|

**Sets can contain anything:**

- $\mathbb{Z}$ is a set
- $C = $ odd primes
- $D = {3, \pi, \triangle, \text{red}, \text{jimin}}$
- $E = {1, 2, {3, 4}}$ → set of sets, $\lvert E \rvert = 3$
- $\lvert \mathbb{Z} \rvert = ?,\ \lvert C \rvert = ?$ (infinite)

### Set Builder Notation

$${\text{variable} : \text{condition}} \qquad (\text{":" reads "where"})$$

$$F = {x : x \in \mathbb{Z} \land x \geq 0}$$

### Empty Set

$$G = {} \equiv \varnothing \qquad \forall x,\ x \notin \varnothing$$

**Vacuous truth:**

$$\forall x \in \mathbb{N},\ x \geq -10 ;\equiv; x \in \mathbb{N} \implies x \geq -10$$

$$\forall x \in \varnothing,\ x \geq -10 ;\equiv; \underbrace{x \in \varnothing}_{F} \implies x \geq -10$$

False premise → **vacuously true**.

### Subsets

$\mathbb{N} \notin \mathbb{Z}$: $\mathbb{N}$ is a set, not an **element** of $\mathbb{Z}$. What we mean is $x \in \mathbb{N} \implies x \in \mathbb{Z}$:

$$\mathbb{N} \subseteq \mathbb{Z} \quad (\text{subset})$$

$$A \subseteq B ;\equiv; x \in A \implies x \in B$$

**Facts:**

- $\forall A,\ A \subseteq A$
- $\forall A,\ \varnothing \subseteq A$ (vacuously true)

**Proper subset:** $A \subsetneq B$ → $A \subseteq B$ and $A \neq B$