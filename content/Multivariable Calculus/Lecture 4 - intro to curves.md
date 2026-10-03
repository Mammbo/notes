## Distances
 
**Definition.** The distance between two sets is the min of all distances between points in the respective sets:
$$\operatorname{dist}(X, Y) = \min_{x \in X,\ y \in Y} |x - y|$$
 
### Point to plane
 
Find the distance from a position $\vec{y}$ to a plane with normal $\vec{n}$ and position $\vec{P}$.
 
The distance is the length of the projection of $\vec{y} - \vec{P}$ onto the normal:
$$\boxed{\ \left\| \operatorname{proj}_{\vec{n}}(\vec{y} - \vec{P}) \right\| = \operatorname{dist}\ }$$
 ## Space Curves
 
**Definition.** A curve in $\mathbb{R}^n$ is the image of a vector-valued function
$$f : \mathbb{R} \longrightarrow \mathbb{R}^n$$
(input is a scalar, output is a vector). It has the form:
$$r(t) = \langle x(t),\ y(t),\ z(t)\rangle$$
 
**Examples:**
- Twisted cubic: $\langle t,\ t^2,\ t^3\rangle$
- Helix: $\langle \cos(t),\ \sin(t),\ t\rangle$ — the $\langle\cos t, \sin t\rangle$ part traces a circle

## Calculus of Vector Functions
 
**Limits** are taken component-wise:
$$\lim_{t \to a} \vec{r}(t) = L$$
 
$$\lim_{t \to a} r(t) =
\begin{bmatrix}
\lim_{t \to a} x(t) \\[4pt]
\lim_{t \to a} y(t) \\[4pt]
\lim_{t \to a} z(t)
\end{bmatrix}$$
 if any limit here fails then the whole thing does not exist

![[Lecture 4 intro to curves.pdf]]