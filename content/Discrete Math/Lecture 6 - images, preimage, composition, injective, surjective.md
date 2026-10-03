
# Functions: Image, Preimage, Composition, Injective/Surjective

## Image

For $f: A \to B$ and $U \subseteq A$, the **image of $U$ under $f$**:

$$f[U] = {f(a) : a \in U} \subseteq B$$

The **image of $f$** $= f[A]$

## Preimage

For $f: A \to B$ and $V \subseteq B$, the **preimage of $V$ under $f$**:

$$f^{-1}[V] = {a \in A : f(a) \in V} \subseteq A$$

> [!todo] Look at recitation problems For $U \subseteq A$: what is $f^{-1}[f[U]]$?

---

## Operations on Functions

**e.g.** Student $\xrightarrow{f}$ hw & exam scores $\xrightarrow{g}$ total % $\xrightarrow{h}$ letter

$$\begin{aligned} f &: \text{Students} \to [100] \times [10] \times [78] \ g &: [100] \times [10] \times [78] \to \mathbb{R} \ h &: \mathbb{R} \to \text{Letters} \end{aligned}$$

$G(s) = h(g(f(s)))$ maps Students $\to$ Letters.

### Function Composition

For $f: A \to B$ and $g: B \to C$:

$$g \circ f : A \to C \quad \text{via} \quad (g \circ f)(x) = g(f(x))$$

---

## Injective (One-to-One)

$f: A \to B$ is **injective** iff

$$\forall x_1, x_2 \in A,\quad f(x_1) = f(x_2) \implies x_1 = x_2$$

Equivalently: $x_1 \neq x_2 \implies f(x_1) \neq f(x_2)$ (no two inputs hit the same output).

```
A       B
• ────→ •
• ────→ •
• ────→ •
        •   ← extra outputs OK
```

**Prop:** $f: \mathbb{R} \to \mathbb{R},\ f(x) = 2x + 1$ is injective.

**Proof:** Suppose $f(x_1) = f(x_2)$. $$2x_1 + 1 = 2x_2 + 1 \implies 2x_1 = 2x_2 \implies x_1 = x_2 \quad \blacksquare$$

---

## Surjective (Onto)

$g: A \to B$ is **surjective** iff

$$\forall y \in B,\ \exists x \in A \text{ with } f(x) = y$$

(every output gets hit)

**Prop:** $f: \mathbb{R} \to \mathbb{R},\ f(x) = 2x + 1$ is surjective.

**Proof:** Let $y \in \mathbb{R}$. Let $x = \frac{y-1}{2}$. Then $$f(x) = 2\left(\frac{y-1}{2}\right) + 1 = y - 1 + 1 = y \quad \blacksquare$$

> [!tip] Surjective proof strategy Solve $y = f(x)$ for $x$, then plug that $x$ back in.

---

## Bijective

A function that is **injective and surjective** is **bijective**:

$$\forall y \in B,\ \exists!, x \in A \text{ with } f(x) = y$$

(every output hit by **exactly one** input)

---

## Functions & Sizes of Sets

Functions are useful to talk about the sizes of sets:

|If $\exists, f: A \to B$ that is...|Then|
|---|---|
|injective|$\lvert A \rvert \leq \lvert B \rvert$|
|bijective|$\lvert A \rvert = \lvert B \rvert$|