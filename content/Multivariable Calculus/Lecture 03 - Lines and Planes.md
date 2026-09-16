![[Screenshot 2026-09-15 at 3.21.10 PM.png]]

# The Cross Product:
- Special  Vector product, or cross product in R^3 only.
- v x w = u
- A Vector cross a vector is a vector.
## Properities
- bilinearity
	- $u \times (cv+dw) = c(a \times v) + d(u \times w)$
- skew symmetry
	- $v \times w = -w \times v$
- The cross product of a vector by itself is 0
- basis Vectors: 
	- $i \times j = k$
	- $j \times k = i$
	- $k \times i = j$
- $v \times w$ is perpendicular to both v & w. 
- $v \times w$ points in the direction according to the right hand rule 
- $|v \times w|$  = $|v| |w| sin \theta$ where theta is the positive angel between the vectors

## How to take a cross product


$$w = (ai + b j + ck) \times (dc + ej + fk) \rightarrow \begin{bmatrix}i &j & k \\ a & b &c \\ d & e & f \end{bmatrix} \rightarrow w = \begin{bmatrix}b & c \\ e & f \end{bmatrix}i  - \begin{bmatrix} a & c \\ d & f \end{bmatrix}j +\begin{bmatrix}a & b \\ d & e \end{bmatrix}k$$
$$\text{At this point you cross multiply subtracting the products like so}$$
$$ w = (bf - ce)i + (cd - af)j + (ac - bd)k$$

## Cross products & area
- the area of is  this formal defintion: $|v \times w|$  = $|v| |w| sin \theta$ 
# Lines:
	- Parametric form 
	- A line in R ^n  with pos P & direction v has parametric form r(t) = p + tv


![[Screenshot 2026-09-15 at 3.59.01 PM.png]]


$$ v_1 = <2, 1> - < 0, 0> \rightarrow R_1(t) = v_1t = \begin{bmatrix} 2 \\ 1\end{bmatrix}t$$
$$R_2(t) =  \begin{bmatrix} 6 \\ -1\end{bmatrix} + s\begin{bmatrix} 4 \\ -6\end{bmatrix} $$
$$\text{At this point set them equal to each other and solve the system of equations to get s  solve for t}$$
$$\text{that answer when you solve R1 for T is your answer}$$
# Planes
- we can define a plave via its parametric form w/ a pos vector & 2 dirction vectors
	- $r(s, t) = p + sv + tw$
	- plane equation = $n * (x- p) = 0$
- in R^3 we can also define a plave w/ 1 pos vector p & 1 normal vector n to define the plane equation.
	- $x + 2y = 16 - 8z$
- find a point on this plane. --> set x = 16 because y and z can be set to 0 so < 16, 0, 0 > is a point on the plane
- rearrange equation
	- $(x -16) + 2y +8z$
- take the coefficents of this to get n = < 1, 2, 8>
- and now we can plug into plane equation!
	- $< 1, 2, > * < < x, y, z> - < 16, 0, 0> >$
![[Lecture 3 lines and planes.pdf]]