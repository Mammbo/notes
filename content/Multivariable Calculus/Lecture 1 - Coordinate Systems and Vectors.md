![[Screenshot 2026-09-12 at 2.38.55 PM.png]]
![[Screenshot 2026-09-12 at 2.39.59 PM.png]]
# Spaces The planes in which we will operate in ;

**Notation:**

$\mathbb{R} \rightarrow$ The Real Numbers / Scalars — the complete ordered field. *(Scalar means $\mathbb{R}$)*

$\mathbb{R}^2 \rightarrow$ Cartesian Plane — the set of all pairs of real numbers:

$$\mathbb{R}^2 = \{ (x, y) \mid x, y \in \mathbb{R} \}$$

$$\mathbb{R}^3 = \{ (x, y, z) \mid x, y, z \in \mathbb{R} \}$$

$$\mathbb{R}^n = \{ (x_1, \dots, x_n) \mid x_i \in \mathbb{R} \}$$
### The Distance formula for two points in R ^n space is 
$$d(P, Q) = \sqrt{\sum_{i=1}^{n}(p_i - q_i)^2}$$
# Vectors
- A Vector is a directed line segment in $\mathbb{R}^n$ modulo location 
	- if direction or line doesnt change they are the same vector 
		- i.e adding up vectors forces in physics.

##  Vector Notation

$$v = \vec{v} = \langle v_1, v_2, \dots, v_n \rangle = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix} \quad \rightarrow \text{good for vector equations}$$

The $v_i$'s are the components of $v$ — the displacements in each dimension.

## Vector Operations

**Magnitude** *(turns vector $\rightarrow$ scalar)*

$$|v| = \sqrt{\sum_{i=1}^{n} v_i^2}$$
The mage or length of a vector is a non negative scalar.
It is non degenerate which just means.

## Scalar Multiplication:
- Preserves direction and changes length
 $$c\vec{v} = \langle cv_1, cv_2, \dots, cv_n \rangle$$

$$|cv| = |c| \cdot |v|$$
## Normalize a vector:
- A unit vector has a magnitude 1.
- Normalizing a vector just means converting it to a unit vector.

For every non zero vector that v != 0 con be normalized by dividing by its mag
$$u = \frac{v}{|v|}$$
## Addition
Vector addition: works literally how you think it would 
A sum of scaled vectors is calledd a linear combination and is the fundamental vector expression.
$$ v + w = \langle v_1 + w_1, v_2 + w_2, ..., +v_n +w_n  \rangle $$
$$\sum_{i=1}^n c_iv_i$$

# Special Linear Combinations: Vector form of the scalar operation for the distance formula
# the result is a vector pointing from the original to the next point 
$$(1 - t)v + tw$$
for some 0 <= t <= 1 are called convex combinations
# Handwritten Notes:![[Lecture1 - multi.pdf]]