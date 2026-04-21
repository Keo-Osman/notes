---
tags:
  - maths/linear-algebra
---
# Definition
An **Eigenvector** of [[Matrices|Matrix]] A is a non-zero column [[Vectors|Vector]] $\mathbf{x}$ that satisfies $A\mathbf{x} = \lambda \mathbf{x}$ where $\lambda$ is a scalar. The value of $\lambda$ is the **eigenvalue** corresponding to the **eigen vector** $\mathbf{x}$.

This corresponds to a vector that is an invariant vector under the [[Linear Transforms|Linear Transform]] transform $A$. The corresponding eigenvalue $\lambda$ can be thought of as the magnitude scale factor for the eigenvector. 

However the definition can be applied to any *linear operator* on any vector space as they can be represented as a matrix. E.g. for a linear operator $L$ there is an eigen vector that satisfies $L(\mathbf{x})=\lambda \mathbf{x}$.
# Characteristic Equation
$$
\begin{aligned}
&A\mathbf{x} = \lambda \mathbf{x} = \lambda I\mathbf{x} \\
&A\mathbf{x} - \lambda I\mathbf{x}  = (A- \lambda I)\mathbf{x} = 0\\
\Rightarrow&\det(A-\lambda I) = 0
\end{aligned}
$$
The solutions of $\lambda$ are the eigenvalues of $A$. To find the eigen-vectors of $A$ we simply solve $A\mathbf{x}=\lambda \mathbf{x}$.
## Eigenspace, Multiplicity
Given an eigen value $\lambda$ of $A$. The ***algebraic multiplicity*** of $\lambda$ denoted $\operatorname{AM}(\lambda)=$ the number of times the root appears in the characteristic equation of $A$ e.g. $(2-\lambda)^{2}$ the eigen vector $\lambda=2$ has $AM=2$.
The eigenspace is simply the span of the eigenvectors.

***
# Cayley-Hamilton Theorem
All matrices $M$ satisfy their own characteristic equation 
$$
\begin{aligned}
&\det(M-\lambda I) = 0 \\
\Rightarrow &a_n{\lambda}^{n} + a_{n-1}{\lambda}^{n-1} + \cdots a_2{\lambda}^2 + a_1{\lambda} + a_0  = 0 \\
\lambda=M\implies& \det(M-MI)=\det 0\\
\Rightarrow &a_n{M}^{n} + a_{n-1}{M}^{n-1} + \cdots a_2{M}^2 + a_1{M} + a_0 I = 0
\end{aligned}
$$
This theorem can be used to find various variations of M such as $M^{-1}$ and $M^k$  by multiplying or dividing through by $M$ and using the fact that $I = MM^{-1} \Rightarrow I \div M = M^{-1}$
***
# Diagonalisation and Eigen Basis
The motivation is to compute higher powers of an arbitrary matrix $A$ but this is very compute heavy.
However for certain matrices which are diagonal e.g. a square matrix such that every element except those which lie on the leading diagonal are $0$, we can compute high powers very easily - simply just raise each element to the power we are trying to compute and you are done.

Using this fact, for $n\times n$ matrices with $n$ real valued eigen vectors we can perform a [[Change of Basis]] so that the eigen vectors are the basis vectors. So given the change of basis matrix $P$, which is simply the eigen vectors as column vectors we compute $A$ in terms of the eigen-basis as $P^{-1}AP$.
The special reason why eigen vectors as basis is that under transform $A$ they simply scale. This gives the property that for basis eigen-vectors $e_{n}$, $e_{n}\to k_{n}e_{n}$ under the transform so writing this as a matrix in terms of $e$ we a guaranteed to get a ***diagonal*** matrix

So to find a high power of a matrix $A$ we perform the change of basis to an eigne basis yielding a diagonal matrix. Then raise it easily to a high power then undo the change of basis.