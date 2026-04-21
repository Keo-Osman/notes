---
tags:
  - maths/geometry
  - maths/linear-algebra
---
# Definition
A linear transformation is a function $L: V\to W$ where $V$ and $W$ are a [[Vectors#Vector Spaces|Vector Spaces]] *(In most cases $V=W$ and we call $L$ a linear operator)*. 
And $L$ **must** have the properties that $$L(\mathbf{v}+\mathbf{w})=L(\mathbf{v})+L(\mathbf{w}) \quad \text{and} \quad L(c \mathbf{v})=cL(\mathbf{v})$$
This means that all straight lines become new but still straight lines after the transformation as well as the origin has to map to itself. Grid lines remain parallel and evenly spaced. This is a ***VERY*** important property and is really the defining property of a linear transform and why the are so special.
**Proof**
Given any straight line. Take the [[Vectors#Straight Lines|Straight Line Vector Equation]] $\mathbf{a}+\lambda \mathbf{b}$, applying a linear transform gets $L(\mathbf{a}+\lambda\mathbf{b})=L(\mathbf{a})+L(\lambda \mathbf{b})=L(\mathbf{a})+\lambda L(\mathbf{b})$.
Since $L(\mathbf{a})$ and $L(\mathbf{b})$ are just vectors themselves we simply have another straight line equation showing the straight lines remain straight after a transform.
Also notice that two parallel lines will have the same direction vector $\mathbf{b}$ so taking the transform of a parallel line $\mathbf{c}+\lambda \mathbf{b}$ gets $L(\mathbf{c})+\lambda L(\mathbf{b})$ which is parallel to $L(\mathbf{a})+L(\lambda \mathbf{b})=L(\mathbf{a})+\lambda L(\mathbf{b})$ as they have the same direction vector $L(\mathbf{b}) \quad \square.$

Using this we can show that a linear transform is defined solely by the what happens to the basis vectors after the transform. Given a vector $\mathbf{v}=\sum a_{i}\mathbf{b_{i}}$ where $b_{i}$ are the basis vectors. Let $L(b_{i})=c_{i}$ then $L(\mathbf{v})=L\left( \sum a_{i}\mathbf{b_{i}} \right)=\sum L(a_{i}\mathbf{b_{i}})=\sum a_{i}L(\mathbf{b_{i}})=\sum a_{i}c_{i}$ as we can see $L(\mathbf{v})$ has the same format as $\mathbf{v}$ but with the basis vectors changed to the new ones after the transform.
***
# Representation as a [[Matrices|Matrix]]
Using this property that a linear transform is based upon where the basis vector land we can write a transform as a square matrix with column vectors as the new basis vectors. 
For 2D this is $\begin{pmatrix}a&c\\b&d\end{pmatrix}$ where the basis vectors -*typically* $\hat{i}=\begin{pmatrix}1\\0\end{pmatrix}$ and $\hat{j}=\begin{pmatrix}0\\1\end{pmatrix}$ - map to $\begin{pmatrix}a\\ b \end{pmatrix}$ and $\begin{pmatrix}c\\ d\end{pmatrix}$ respectively. 
Then to find $L(\mathbf{v})$ we can write it out as a matrix-vector multiplication $\begin{pmatrix}a&c\\b&d \end{pmatrix}\mathbf{v}$ with $\mathbf{v}=\begin{pmatrix}x\\y\end{pmatrix}$ and using our what out basis vectors change to we get $$\begin{pmatrix}a&c\\b&d \end{pmatrix}\begin{pmatrix}x\\y\end{pmatrix}=x\begin{pmatrix}a\\b\end{pmatrix}+y\begin{pmatrix}c\\d\end{pmatrix}$$
## [[Matrices#Matrix Multiplication|Matrix Multiplication]]
Matrix multiplication is simply finding a single matrix that has the exact same effect as applying the matrices one after another. *Matrix multiplication is read from right to left eg $AB$ is a transformation by $B$ then $A$. This comes from functional notation.* 
For 2D If we apply two linear transforms in a row we get $$\begin{pmatrix}
e&g\\f&h
\end{pmatrix}\left(\begin{pmatrix}a&c\\b&d \end{pmatrix}\begin{pmatrix}x\\y\end{pmatrix}\right)$$
We want to find a single matrix that has the exact same effect as applying the matrices one after another.
To find this we can consider where the basis vectors end up. By definition the basis vector $\hat{i}$ ends up at $\begin{pmatrix}a \\ b\end{pmatrix}$ and then carrying out matrix-vector multiplication with $\begin{pmatrix}e&g\\f&h\end{pmatrix}\begin{pmatrix}a \\ b\end{pmatrix}=\begin{pmatrix}ae+bg \\ af+bh\end{pmatrix}$ doing the same with $\hat{j}$ yields that $$\begin{pmatrix}
e&g\\f&h
\end{pmatrix}\begin{pmatrix}a&c\\b&d \end{pmatrix}=\begin{pmatrix}
ae+bg & ce+dg\\
af+bh & cf+dh
\end{pmatrix}$$
This process of tracking the basis vectors can be generalised for any dimension.
***
# Column Space and Rank
For an $n \times n$ matrix $A$, the ***rank*** of a $A$ is the number of dimensions in the output after a linear transform under $A$. If $\det A\neq 0$ that means that the rank of $A$ is equal to the dimension of $A$ e.g. $n$. If $\det A=0$ that means the space has *collapsed/shrunk* into a lower dimension and the rank of $A$ is $<n$.

The column space of $A$, denoted as $\operatorname{Col}A$ is similar and is simply the span of the column vectors in $A$. Equivalently defined as the set of all possible outputs of $\mathbf{A}v$.
If $A$ is an $n \times n$ real number matrix than if $\operatorname{rank}A=k$ and the column space of $A$ is $\mathbb{R}^{k}$. So the rank of a matrix is simply the number of dimensions of the column space.
***
# Null Space
For a matrix $A$ the null space *(also called the kernel)* is the set of all vectors $\mathbf{x} \text{ s.t } A \mathbf{x}=0$ denoted as $\operatorname{Null}A$. This is the space of all vectors that collapse onto the origin under the linear transformation of $A$. The bigger the null space the more dimensions are lost. The dimension of the null space is called the $\operatorname{nullity}A$
The null space is connected to rank as for an $n\times n$ matrix $A$$$\operatorname{rank}A+\operatorname{nullity}A=n $$
***
# Specific Transformations 
## Rotations
$$
\begin{aligned}

& \stackrel{\displaystyle\text{2D About the origin}}{\begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{pmatrix}}
\quad
\stackrel{\displaystyle\text{About the x-axis}}{\begin{pmatrix}
1 & 0 & 0 \\
0 & \cos\theta & -\sin\theta \\
0 & \sin\theta & \cos\theta
\end{pmatrix}}
\\
& \stackrel{\displaystyle\text{About the y-axis}}{\begin{pmatrix}
\cos\theta & 0 & \sin\theta \\
0 & 1 & 0 \\
- \sin\theta & 0 & \cos\theta
\end{pmatrix}}
\quad
\stackrel{\displaystyle\text{About the z-axis}}{\begin{pmatrix}
\cos\theta & -\sin\theta &0 \\
\sin\theta & \cos\theta&0 \\
0 & 0 & 1 
\end{pmatrix}}

\end{aligned}
$$
## Enlargement and Stretches
You can represent a stretch with matrix $\begin{pmatrix} a & 0 \\ 0 & b \end{pmatrix}$ It has stretch factor $a$ parallel to the $x$-axis and stretch factor $b$ parallel to the $y$-axis.
For stretches only along the $x$-axis, points on the $y$-axis are invariant and the line $x=0$ is invariant and vice versa.
For stretches in both direction the only invariance is the origin
For a linear transform by matrix $M$, $|M|$ is the scale factor of area (if it's negative the shape has been reflected)
## Reflections
$$
\begin{aligned}
& \stackrel{\displaystyle\text{2D reflection in y axis}}{\begin{pmatrix}
-1 & 0 \\
0 & 1
\end{pmatrix}}
\quad
& \stackrel{\displaystyle\text{2D reflection in x axis}}
{\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}}
\\
& \stackrel{\displaystyle\text{2D reflection in line y=x}}{\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}}
\quad
& \stackrel{\displaystyle\text{2D reflection in line y = -x}}{\begin{pmatrix}
0 & -1 \\
-1 & 0
\end{pmatrix}}
\end{aligned}
$$

$$
\begin{aligned}
\quad
& \stackrel{\displaystyle\text{3D reflection in plane x = 0}}{\begin{pmatrix}
-1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}}
\quad
& \stackrel{\displaystyle\text{3D reflection in plane y = 0}}{\begin{pmatrix}
1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 1
\end{pmatrix}}
\\
& \stackrel{\displaystyle\text{3D reflection in plane z = 0}}{\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & -1
\end{pmatrix}}
\end{aligned}
$$