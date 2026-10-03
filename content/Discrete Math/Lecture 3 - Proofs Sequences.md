## Quick-reference card
 
| Concept                             | Rule                                            |
| ----------------------------------- | ----------------------------------------------- |
| De Morgan ($\land$)                 | $\neg(p\land q) \iff \neg p \lor \neg q$        |
| De Morgan ($\lor$)                  | $\neg(p\lor q) \iff \neg p \land \neg q$        |
| Negate $\forall$                    | $\neg\forall x\,P(x) \iff \exists x\,\neg P(x)$ |
| Negate $\exists$                    | $\neg\exists x\,P(x) \iff \forall x\,\neg P(x)$ |
| Double negation                     | $\neg\neg p \iff p$                             |
| Implication                         | $p\Rightarrow q \iff \neg p \lor q$             |
| Contrapositive (equiv)              | $p\Rightarrow q \iff \neg q \Rightarrow \neg p$ |
| $p\Rightarrow q$ is false only when | $p$ true **and** $q$ false                      |
| Prove $\exists$                     | one example                                     |
| Disprove $\forall$                  | one counterexample                              |
| Prove $p \iff q$                    | two proofs (both directions)                    |

# De Morgan's Laws (propositionals)
- Negation turns and into or and vise verse flipping each piece
- essentially push the negative inside the statement, negate each part and flip the connective![[Screenshot 2026-09-16 at 10.11.44 PM.png]]
## Negating quantifiers ( De Morgan for for all and there exists)![[Screenshot 2026-09-16 at 10.12.24 PM.png]]
# Boolean Algebra Rules: 
 
| # | Law | Name |
|---|-----|------|
| 1 | $\neg\neg p \iff p$ | double negation |
| 2 | $p \lor q \iff q \lor p$ (same for $\land$) | commutative |
| 3 | $p \lor (q \land r) \iff (p \lor q)\land(p \lor r)$ | distributive |
| 4 | $p \Rightarrow q \iff \neg p \lor q$ | implication as "or" |
# Implication review:
Starting from $p \Rightarrow q$:
 
| Name | Statement |
|------|-----------|
| **Converse** | $q \Rightarrow p$ |
| **Inverse** | $\neg p \Rightarrow \neg q$ |
| **Contrapositive** | $\neg q \Rightarrow \neg p$ |

# Implication = proof by contrapositive.
$$
\text{For any props } p,q:\qquad (p \Rightarrow q) \iff (\neg q \Rightarrow \neg p)
$$
 
**Proof (truth table).**
 
| $p$ | $q$ | $\neg p$ | $\neg q$ | $p\Rightarrow q$ | $\neg q \Rightarrow \neg p$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| T | T | F | F | **T** | **T** |
| T | F | F | T | **F** | **F** |
| F | T | T | F | **T** | **T** |
| F | F | T | T | **T** | **T** |
The two rightmost columns are identical $(\text{T},\text{F},\text{T},\text{T})$,
so the statements are logically equivalent. $\blacksquare$

## 6. Proof techniques
 
| Technique | Shape | Use when… |
|-----------|-------|-----------|
| **Direct** | $p \Rightarrow \cdots \Rightarrow q$ | the hypothesis leads forward naturally |
| **Contrapositive** | prove $\neg q \Rightarrow \neg p$ instead | the negations are easier to work with |
| **Contradiction** | assume $\neg p$, derive nonsense | "there is no…", uniqueness, irrationality |
| **Example** | exhibit one witness | proving $\exists x,\;P(x)$ |
| **Counterexample** | exhibit one failure | *dis*proving $\forall x,\;P(x)$ |
 
**Two rules to remember:**
- To prove $p \iff q$, you must do **two** proofs ($p\Rightarrow q$ *and* $q\Rightarrow p$).
- To prove "$p$ is false," prove that $\neg p$ is **true**.

# 7.  Some Worked Proofs:

### 7a. Contrapositive — a product bound
 
**Prop.** Let $x,y \in \mathbb{N}$. If $x\cdot y > 50$, then $x > 7$ or $y > 7$.
 
**Proof (contrapositive).** We prove: if $x \le 7$ **and** $y \le 7$, then $xy \le 50$.
(Note the negation used De Morgan: $\neg(x>7 \lor y>7) = (x\le7 \land y\le7)$.)
 
$$
x \le 7 \;\land\; y \le 7 \;\Longrightarrow\; xy \le 7\cdot 7 = 49 \le 50. \qquad\blacksquare
$$
 
### 7b. Contrapositive — irrationality of a square root
 
**Prop.** If $r \in \mathbb{R}$ is irrational, then $\sqrt{r}$ is irrational.
 
**Proof (contrapositive).** We prove: if $\sqrt{r}$ is **rational**, then $r$ is **rational**.
 
Suppose $\sqrt{r}$ is rational. Then $\exists\, a,b \in \mathbb{Z}$ with
$$
\sqrt{r} = \frac{a}{b}
\;\Longrightarrow\;
(\sqrt{r})^2 = \frac{a^2}{b^2}
\;\Longrightarrow\;
r = \frac{a^2}{b^2}.
$$
Since $a^2, b^2 \in \mathbb{Z}$, we have $r = \tfrac{c}{d}$ for integers $c=a^2,\,d=b^2$, so $r$ is rational. $\blacksquare$
 
### 7c. Counterexample — disproving a "for all"
 
**Claim (FALSE).** For all $x \in \mathbb{N}$, $\;x^2 + x + 17\;$ is prime.
 
**Disproof (counterexample).** Take $x = 17$:
$$
17^2 + 17 + 17 = 17(17 + 1 + 1) = 17 \cdot 19 = 323,
$$
which is **not** prime. One counterexample kills a universal claim. $\blacksquare$
 
> Equivalently, this **proves the negation** $\exists x \in \mathbb{N}:
> x^2+x+17 \text{ is not prime}$ — and an $\exists$ statement is proved by a
> single example. (This is the $\forall/\exists$ duality: *disproving* a
> $\forall$ = *proving* an $\exists$.)
 
### 7d. Negating a nested quantifier — disproving $\forall x\,\exists y$
 
**Claim (FALSE).** $\forall x \in \mathbb{R},\; \exists y \in \mathbb{R}$ such that $xy = 1$.
 
**Disproof.** The negation is
$$
\exists x \in \mathbb{R} \text{ s.t. } \forall y \in \mathbb{R},\; xy \ne 1.
$$
Consider $x = 0$. No matter what $y$ is, $xy = 0 \ne 1$. So $x=0$ witnesses the
negation, and the original claim is false. $\blacksquare$
 
### 7e. Contradiction — infinitely many primes (Euclid)
 
**Prop.** There are infinitely many primes. Equivalently, $\forall x \in
\mathbb{N}$ there is a prime $> x$ — i.e. there is **no greatest prime**.
 
**Proof (contradiction).** Assume for contradiction there *are* finitely many
primes; list all $n$ of them: $\;p_1, p_2, \dots, p_n$. Consider
$$
x = p_1 \cdot p_2 \cdots p_n + 1.
$$
Each $p_i$ divides the product $p_1\cdots p_n$, so dividing $x$ by $p_i$ leaves
remainder $1$ — thus **no $p_i$ divides $x$**. Therefore any prime factor of $x$
is a prime not in our list (or $x$ itself is prime). Either way we've found a
prime beyond $p_1,\dots,p_n$, contradicting that the list was complete. $\blacksquare$