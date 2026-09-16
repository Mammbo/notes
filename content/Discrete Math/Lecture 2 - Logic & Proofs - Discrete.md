
# Lecture 2 — Definitions & Proof Techniques
 
## Definitions
 
| Term             | Formal definition                                                                                                                                         | Notes / Example                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Even**         | $n \in \mathbb{Z}$ is *even* $\iff \exists k \in \mathbb{Z} : n = 2k$                                                                                     | e.g. $-4,\ 0,\ 6$                                                 |
| **Odd**          | $n \in \mathbb{Z}$ is *odd* $\iff \exists k \in \mathbb{Z} : n = 2k + 1$                                                                                  | e.g. $-3,\ 1,\ 7$                                                 |
| **Prime**        | $p \in \mathbb{N}$ is *prime* $\iff p \notin \{0, 1\}$ and $\forall k \in \mathbb{Z}$ with $1 < k < p$, there is no $m \in \mathbb{Z}$ such that $mk = p$ | i.e. $p$ has no divisor strictly between $1$ and $p$              |
| **Rational**     | $x \in \mathbb{R}$ is *rational* $\iff \exists m, n \in \mathbb{Z},\ n \ne 0 : x = \dfrac{m}{n}$                                                          | the set of rationals is $\mathbb{Q}$                              |
| **Reduced form** | $\dfrac{m}{n}$ is in *reduced form* $\iff \nexists z \in \mathbb{Z} : z \mid m \ \land\ z \mid n \ \land\ z > 1$                                          | equivalently $\gcd(m, n) = 1$; e.g. $\frac{4}{8} \to \frac{1}{2}$ |
## Number sets
 
| Symbol | Set | Examples |
|--------|-----|----------|
| $\mathbb{N}$ | Natural numbers | $1,\ 2,\ 3,\ \dots$ |
| $\mathbb{Z}$ | Integers | $\dots,\ -10,\ -1,\ 0,\ 1,\ \dots$ |
| $\mathbb{Q}$ | Rationals | $-\tfrac{1}{2},\ -\tfrac{3}{5}$ |
| $\mathbb{R}$ | Reals | $\pi,\ e,\ \sqrt{2}$ |
 
## Logical notation
 
| Symbol | Meaning |
|--------|---------|
| $\implies$ | if … then … / implies |
| $\iff$ | if and only if (iff) |
| $\forall$ | for all |
| $\exists$ | there exists |
| $\nexists$ | there does not exist |
| $\land$ | and |
| $\lor$ | or |
| $\neg$ | not |
| $\mid$ | divides (e.g. $p \mid n$) |
 ## Propositions
 
> Proposition (primes)
   $\forall n \in \mathbb{N}$, if $n$ is not prime then $\exists$ a prime $p$ such that $p \mid n$.
 
## Proof techniques
 
### 1. Direct proof
 
Assume the hypothesis and derive the conclusion through a chain of implications.
 
Proposition 1
If $x \in \mathbb{Z}$ is odd, then $x^2$ is also odd.

Proof (direct)
	Let $x \in \mathbb{Z}$ be odd.
	By the definition of odd, $\exists k \in \mathbb{Z} : x = 2k + 1$. Then
	$$x^2 = (2k+1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1 = 2L + 1,$$
	where $L = 2k^2 + 2k \in \mathbb{Z}$.
	 By the definition of odd, $x^2$ is odd. $\blacksquare$
 
### 2. Proof by cases
 
Split the domain into exhaustive cases and prove the claim in each.
 
 Proposition 2
 $\forall x \in \mathbb{Z}$, $x^2 + x - 6$ is even.

Proof (by cases)
	Note that $x^2 + x - 6 = (x+3)(x-2)$ and that $6$ is even. Consider two cases.

**Case 1 — $x$ is even.** Write $x = 2k$. Then
$$x^2 + x - 6 = 4k^2 + 2k - 6 = 2(2k^2 + k - 3),$$
		which is even.
**Case 2 — $x$ is odd.** 
	By Proposition 1, $x^2$ is odd. 
	Then $x^2 + x = \text{odd} + \text{odd} = \text{even}$ (adding two odd numbers gives an even), and $\text{even} - 6$ is even.
 
In both cases $x^2 + x - 6$ is even. $\blacksquare$
 
### 3. Proof by contradiction
 
**Idea:** to prove $P$, assume $\neg P$ and derive a contradiction:
$$P \quad\text{via}\quad \neg P \implies \cdots \implies \bot \ (\text{e.g. } 0 = 1).$$
 
Proposition
	$\sqrt{2}$ is not rational.

Proof (by contradiction)
	Assume, for the sake of contradiction, that $\sqrt{2}$ is rational. Then $\exists m, n \in \mathbb{Z}$ with
$$\sqrt{2} = \frac{m}{n}, \qquad \frac{m}{n} \text{ in reduced form.}$$
	Squaring both sides: $2 = \dfrac{m^2}{n^2}$, so $2n^2 = m^2$. Hence $m^2$ is even, so $m$ is even (contrapositive of Proposition 1).
	Write $m = 2k$ for some $k \in \mathbb{Z}$. Then
$$2n^2 = m^2 = (2k)^2 = 4k^2 \implies n^2 = 2k^2,$$
	 so $n^2$ is even, and therefore $n$ is even.
	 But then $2 \mid m$ and $2 \mid n$, contradicting that $\tfrac{m}{n}$ is inreduced form.
 Therefore $\sqrt{2}$ is not rational. $\blacksquare$
 
 
## Negation & De Morgan's Laws
 
Putting $\neg$ ("not") in front of a statement negates it.
 
| Statement                      | Negation                                  |
| ------------------------------ | ----------------------------------------- |
| $x = 5$                        | $x \ne 5$                                 |
| $x > 0$                        | $x \le 0$                                 |
| $x > 0 \ \land\ x \text{ odd}$ | $\neg(x > 0) \ \lor\ \neg(x \text{ odd})$ |
| $P \lor Q$                     | $\neg P \ \land\ \neg Q$                  |
| $P \land Q$                    | $\neg P \ \lor\ \neg Q$                   |
 
De Morgan's Laws
$$\neg(P \lor Q) \equiv \neg P \land \neg Q$$
$$\neg(P \land Q) \equiv \neg P \lor \neg Q$$
$$\neg(\exists x, P(x)) \implies \forall x \neg(P(x))$$
$$\neg (\forall x, P(x)) \implies \exists x, \neg P(x)$$
$$ \neg(\text{P or Q}) \implies \neg  \text{ P AND } \neg Q $$
![[Lecture 2 - discrete.pdf]]