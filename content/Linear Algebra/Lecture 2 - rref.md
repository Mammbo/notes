# Matrices & Vectors
- A column vector is an n x 1 matrix -> $\begin{bmatrix}1 \\ 2 \\ 3 \\ 4\end{bmatrix}$
- a row vector is an 1 x m matrix ---> $\langle 1, 2, 3 \rangle$
- An n = dimensional vector is a vector w/ n entries
- ex: ![[Screenshot 2026-09-15 at 7.06.09 PM.png]]

# RREF (reduced row echelon form)

- A matrix is said to be in reduced row echelon form (rref) if it satisifies:
	1. The leading non zero entry in each row is 1. ( called the leading one)
	2. If ith row has leading 1 at jth col, then (i + 1)th row has leading 1 > jth col
	3. Each col. containing a leading 1 has 0's in all other entries

ex: 
$$\begin{bmatrix} 1 & 0 & 0 & 2 \\ 0 & 1 & 0 & 3 \\ 0 & 0 & 1 & 4\end{bmatrix}$$
- we care about rref because we need to modify 3 x 4 matrix into another 3x 4 in rref.

### Modify def: Three matrix operations (Elementary row operations)
- Multiply/ divide a row by a non zero #
- subtract/ adda multiple of a row from another row.
- swap two rows

### Given: 
$$ \begin{gathered}

a_{11}x + a_{12}y + a_{13}z = b_1 \\
a_{21}x + a_{22}y + a_{23}z = b_2 \\
a_{31}x + a_{32}y + a_{33}z = b_3\\
= \\
\text{Augmented Matrix and Coefficent Matrix}\\
	\begin{bmatrix} 
	a_{11} & a_{12} & a_{13} & b_1 \\
	a_{21} & a_{22} & a_{23} & b_2 \\
	a_{31} & a_{32} & a_{33} & b_3 \\
	\end{bmatrix}
	\begin{bmatrix} 
	a_{11} & a_{12} & a_{13}\\
	a_{21} & a_{22} & a_{23}\\
	a_{31} & a_{32} & a_{33}\\
	\end{bmatrix}
	

\end{gathered} $$ 
This method of reducting a given augmented matrix into a rref matrix is called the **Gauss Elimination Process**
- Given a system of linear equations I can get an augmented matrix and use the Gauss elim process to get a matrix in rref. 
- Thus, the  given of any matrix A 
	1. Gauss elimination process works in finite steps
	2. the result rref is unique. 
1. The resuling matrix is called the rref of mat A, and denoted by rref(A)
![[Lecture 2 - Lin Alg reduced row echelon form.pdf]]