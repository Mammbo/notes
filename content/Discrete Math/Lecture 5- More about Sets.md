
 
> [!tip] For proofs
> - "It is false that ___"
> - State the method (e.g. proof by induction)
> - **Declare variables!**
 
---
 
## Review
 
| Notation | Meaning |
|---|---|
| $x \in A$ | $x$ is an element of $A$ |
| $A \subseteq B$ | $\forall x \in A,\ x \in B$ |
| $\lvert A \rvert$ | size |
| $\varnothing \equiv \{\}$ | empty set |
| $\{x \in \mathbb{Z} : x \geq 0\}$ | set builder |
 
---
 
## Power Set
 
$\{1, 2, 3\}$ has $2^3 = 8$ subsets. In general, if $\lvert A \rvert = n$, $A$ has $2^n$ subsets.
 
**Power set** $\mathcal{P}(A)$ = the set of all subsets of $A$:
 
$$\mathcal{P}(\{1,2,3\}) = \big\{\varnothing,\ \{1\},\ \{2\},\ \{3\},\ \{1,2\},\ \{1,3\},\ \{2,3\},\ \{1,2,3\}\big\}$$
 
$$\lvert \mathcal{P}(A) \rvert = 2^{\lvert A \rvert} \quad (A \text{ finite})$$
 
e.g. $\mathcal{P}(\varnothing) = \{\varnothing\}$
 
---
 
## Set Operations
 
| Operation | Definition |
|---|---|
| Union | $A \cup B = \{x : x \in A \lor x \in B\}$ |
| Intersection | $A \cap B = \{x : x \in A \land x \in B\}$ |
| Complement | $\overline{A} = \{x \in U : x \notin A\}$ ($U$ = universe) |
| Difference | $A \setminus B = \{x \in A : x \notin B\}$ |
 
e.g. $A = \{1,2,3\},\ B = \{3,4,6\}$:
- $A \cup B = \{1,2,3,4,6\}$
- $A \cap B = \{3\}$
- irrationals $= \mathbb{R} \setminus \mathbb{Q}$
### Shorthand & Intervals
 
$$[n] = \{1, 2, 3, \ldots, n\} \subseteq \mathbb{N}$$
 
| Interval | Definition |
|---|---|
| $[a, b]$ | $\{x \in \mathbb{R} : a \leq x \leq b\}$ |
| $[a, b)$ | $\{x \in \mathbb{R} : a \leq x < b\}$ |
| $(a, b]$ | $\{x \in \mathbb{R} : a < x \leq b\}$ |
| $(a, b)$ | $\{x \in \mathbb{R} : a < x < b\}$ |
 
e.g. $[1, 7) \cap [6, 10] = [6, 7)$
 
---
 
## Set Equality
 
$$A = B \iff \text{same elements} \iff A \subseteq B \land B \subseteq A$$
 
$$\iff \forall x,\ (x \in A \implies x \in B) \land (x \in B \implies x \in A)$$
 
### Proof by Double Containment
Basically a definition proof. **Must prove both ways!**
 
**Claim:** $\mathcal{P}(A \cap B) = \mathcal{P}(A) \cap \mathcal{P}(B)$
 
e.g. $A = \{1,2,3\},\ B = \{2,3,4\},\ A \cap B = \{2,3\}$
$$\mathcal{P}(A \cap B) = \{\varnothing, \{2\}, \{3\}, \{2,3\}\}$$
 
**Proof:** Let $X$ be any set.
 
$$\begin{aligned}
X \in \mathcal{P}(A \cap B) &\iff \forall y \in X,\ y \in A \cap B \\
&\iff \forall y \in X,\ y \in A \land y \in B \\
&\iff X \subseteq A \land X \subseteq B \\
&\iff X \in \mathcal{P}(A) \land X \in \mathcal{P}(B) \\
&\iff X \in \mathcal{P}(A) \cap \mathcal{P}(B)
\end{aligned}$$
 
Every step is $\iff$, so both containments hold. $\blacksquare$
 
### Prove This: De Morgan's Law
 
$$\overline{A \cup B} = \overline{A} \cap \overline{B}$$
 
> [!example]- Proof
> $$\begin{aligned}
> x \in \overline{A \cup B} &\iff x \notin A \cup B \\
> &\iff \lnot(x \in A \lor x \in B) \\
> &\iff x \notin A \land x \notin B \\
> &\iff x \in \overline{A} \land x \in \overline{B} \\
> &\iff x \in \overline{A} \cap \overline{B} \quad \blacksquare
> \end{aligned}$$
 
---
 
## Cartesian Product
 
$$A \times B = \{(a, b) : a \in A,\ b \in B\} \qquad \lvert A \times B \rvert = \lvert A \rvert \cdot \lvert B \rvert$$
 
e.g. $A = \{1,2\},\ B = \{3,4,5\}$:
$$A \times B = \{(1,3), (1,4), (1,5), (2,3), (2,4), (2,5)\}$$
 
- $\mathbb{R} \times \mathbb{R}$ = the plane; a curve $C \subseteq \mathbb{R} \times \mathbb{R}$
- Grades: $A = \{A, B, C, D, F\},\ B = \{+, -, \text{“”}\},\ C = \{D-, F+, F-\}$
  $$\text{Grades} = (A \times B) \setminus C$$
**Tuples:**
- $A \times B \times C \times D = \{(a, b, c, d)\}$ → 4-tuple
- $k$-tuple: $(a_1, a_2, \ldots, a_k)$
- $A \times A \times A \times A = A^4$
---
 
## Indexed Family of Sets
 
Like $\sum_{i=1}^n a_i$, but for sets:
 
$$\bigcup_{i=1}^{n} A_i = A_1 \cup A_2 \cup \cdots \cup A_n \qquad \bigcap_{i=1}^{n} A_i = A_1 \cap A_2 \cap \cdots \cap A_n$$
 
**Example:** $A_i = [i],\quad B_i = [i, i+1]$
 
| | $A_i = [i]$ | $B_i = [i, i+1]$ |
|---|---|---|
| $i = 1$ | $\{1\}$ | $[1, 2]$ |
| $i = 2$ | $\{1, 2\}$ | $[2, 3]$ |
| $i = 3$ | $\{1, 2, 3\}$ | $[3, 4]$ |
| $\bigcup$ | $\{1, \ldots, n\} = [n]$ | $[1, n+1]$ |
| $\bigcap$ | $\{1\}$ | $\varnothing$ |
 
> [!question] Why $\bigcap B_i = \varnothing$?
> Neighbors only touch at one point: $B_1 \cap B_2 = [1,2] \cap [2,3] = \{2\}$.
> But $B_3 = [3,4]$ doesn't contain 2, so $\{2\} \cap B_3 = \varnothing$.
> No single number lies in **every** interval (for $n \geq 3$).
 