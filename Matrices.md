---
tags:
  - maths/geometry
  - maths/linear-algebra
aliases:
  - Matrix
---
# Definition
A matrix is an array of elements organised in rows and columns
The size of on array can be described by row $\times$ columns such as a 2 x 4 matrix $$\left(\begin{array}{cccc}1 & 4 & -1 & 1 \\ 2 & 3 & 0 & 2\end{array}\right)$$

***
# Matrix Operations
### Addition
To add two matrices simply add the corresponding elements
### Multiplication by a Scalar
To multiply a matrix by a scalar simply multiply every individual element by the scalar
### Matrix Multiplication
[[Linear Transforms#Matrices Matrix Multiplication Matrix Multiplication]]
Matrices $A$, $B$ can be multiplied if $A$ has dimensions $n \times m$, and $B$ has dimensions $m \times k$. The resulting matrix will have dimensions $n \times k$ *(If this condition is met then $A$ is said to be multiplicatively conformable with $B$).* Matrix multiplication is associative but not commutative.

To compute a matrix multiplication, take the dot product of each row of the first matrix with each column of the second matrix.
Also worded as: For $AB = C$, each element $C_{ij}$ is the dot product of the $i$-th row of $A$and the $j$-th column of $B$
For example 
$$
\left(\begin{array}{ccc}
5 & -1 & 2 \\
8 & 3 & -4
\end{array}\right) \times\left(\begin{array}{cc}
2 & 2 \\
9 & -3 \\
7 & 4
\end{array}\right)=\left(\begin{array}{cc}
15 & 21 \\
15 & -9
\end{array}\right)
$$

***
# Identity Matrix
The identity matrix is the matrix $I$ that is all zero apart from having 1's on the leading diagonal. In terms of linear transforms this represents that all unit vectors remain where they are.
$$
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{pmatrix}
$$
It has the unique property that $AI = IA = A$ for all matrices. This makes it the [[Groups#Axioms of Groups|Identity Element]] of a [[Groups|Group]] of matrices under the operation of multiplication hence the name

***
# Transpose
The transpose of a matrix is found by interchanging the rows and the columns. For example, if $A = \begin{pmatrix} 1 & 2 \\ 4 & 3 \end{pmatrix}$, $A^{T} = \begin{pmatrix} 1 & 4 \\ 2 & 3 \end{pmatrix}$.

***
# Matrix Inverses
The inverse of any non-singular matrix $A$ is the matrix $A^{-1}$ such that $$AA^{-1} \equiv A^{-1}A \equiv I$$
If $\det A\neq 0$, $A^{-1}$ is guaranteed to exist but if $\det A=0$ then $A^{-1}$ does not exist. This can be related to the null space of $A$. If $\operatorname{nullity}A\neq 0$ e.g. no dimensions are lost/collapsed then every transform can be undone. However if $\operatorname{nullity}A\geq 1$ then information/space is lost and the inverse doesn't exist because multiple vectors collapse into the same vector so the inverse transform is multivalued and therefore not a proper linear transform.
## Computation
### 2x2 
 $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, then $A^{-1} = \frac{1}{|A|} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$ 
### 3x3 
For a given $3 \times 3$ matrix $A$, $A^{-1} =\displaystyle\frac{1}{|A|}C^{T}$ where $C$ is the matrix of cofactors.
To find $C$
1. Form the matrix of the minors. This is where each of the nine elements of the matrix is replaced by its minor
2. Change the signs of some elements with alternating signs as shown $$\begin{pmatrix} + & - & + \\ - & + & - \\ + & - & + \end{pmatrix}​$$
***
# Systems of Linear Equations
## How to Solve Systems of Linear Equations
If $A\begin{pmatrix} x \\ y \\ z \end{pmatrix} = v$ then $\begin{pmatrix} x \\ y \\ z \end{pmatrix} = A^{-1}v$
If A is non-singular then a unique solution for $\begin{pmatrix} x \ y \ z \end{pmatrix}$ can be found for any vector v
To solve a given system of equations for $x, y, z$: $$
\begin{aligned} ax + by + cz& = j \\
dx + ey + fz& = k \\ 
gx + hy + iz& = l
\\
\begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} &= \begin{pmatrix} j \\ k \\ l 
\end{pmatrix} 
\\
\end{aligned}$$
$$\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i \end{pmatrix}^{-1} \begin{pmatrix} j \\ k \\ l 
\end{pmatrix}$$
## Cramer's Rule
**Cramer's Rule** is an alternate way of finding solutions to linear systems of equations which has very nice simple geometric intuition. However it is slower to compute both by hand and for computers than gaussian elimination.

Given an $n\times n$ matrix $A$ with column vectors $\vec{u}_{1},\vec{u}_{2},\dots ,\vec{u}_{n}$ and two other vectors $\vec{v},\vec{w}$ giving the equation $A\vec{v}=\vec{w}$.
You can find the solution with $$v_{k}=\frac{\det A_{k}}{\det A}$$
Where $A_{k}$ is the matrix where $\vec{u}_{k}$ is replaced by $\vec{w}$.

**Proof**
The reason why this works is that we consider area. In $n$ dimensions, for each basis vector, consider the volume bound by $\vec{v}$ and the $n-1$ other basis vectors. 
For a given basis vector $e_{k}$ we can compute this *signed* volume with $\det I_{k}$ where $I_{k}$ is the identity matrix with the $k$th column replaced by $\vec{v}$. Which by using some basic geometry is simply equal to $v_{k}$ as the *base* are/volume is equal to $1$ and the perpendicular height is the coordinate of $v$ in the direction of the basis vector $e_{k}$ we chose. 
After the transformation $A$ the volume scales by a factor of $\det A$ so the new area is simply $(\det A)v_{k}$ but we can compute this area in another way as we know all the vectors needed after the transformation. All the basis vectors transform to become the column vectors of the matrix $A$ and the vector $\vec{v}$ transforms to $\vec{w}$ which we know so we can simply compute the volume with $\det A_{k}$ so equating these areas gives $(\det A)v_{k}=\det A_{k}$ and rearranging gives the formula as required $\quad \square$.
## Linear Equation Consistency
A system of linear equations is consistent if at least one set of values that satisfy all equations simultaneously. If the matrix corresponding to a system is non-singular then the system has one solution and is consistent.

However if it is singular then either
1. The system is consistent and has infinitely many solutions
2. It is inconsistent with no solutions
![[Linear-Equation-Consistency-1.png|500]]
![[Linear-Equation-Consistency-2.png|500]]
