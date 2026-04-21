---
tags:
  - maths/geometry
  - maths/linear-algebra
aliases:
  - Vector
---
# Vector Spaces
A vector space $V$ is a set of objects with two operations $+ : V\times V\to V$ and $\cdot : \mathbb{F} \times V\to V$ where $\mathbb{F}$ is a field *(generally $\mathbb{R}$ or $\mathbb{C}$)*.
It must also follow 8 axioms 
For $u,v,w \in V \ a,b \in \mathbb{F}$
1. Additive Closure $(\mathbf{u}+\mathbf{v})\in V$
2. Additive Commutativity $\mathbf{u}+\mathbf{v}=\mathbf{v}+\mathbf{u}$
3. Additive Associativity $(\mathbf{u}+\mathbf{v})+w=\mathbf{u}+(\mathbf{v}+w)$
4. Additive Identity $\exists 0\in V \text{ s.t }\mathbf{u}+0=\mathbf{u} \quad \forall \mathbf{u} \in V$
5. Additive Inverse $\forall \mathbf{v} \in V , \ \exists(-\mathbf{v}) \text{ s.t } \mathbf{v}+(-\mathbf{v})=0$
6. Multiplicative Closure $a\mathbf{v}\in V$
7. Multiplicative Associativity $a(b\mathbf{v})=(ab)\mathbf{v}$
8. Multiplicative Identity $1_{\mathbb{F}}\cdot \mathbf{v}=\mathbf{v}$ - *ensuring that the identity of the field acts as an identity on* $V$
9. Scalar Distributivity $a(\mathbf{u}+\mathbf{v})=a\mathbf{u}+a\mathbf{v}$
10. Vector Distributivity $(a+b)\mathbf{v}=a\mathbf{v}+b\mathbf{v}$

Common examples of vector spaces are $\mathbb{R}^{n},\mathbb{C}^{n},\mathbb{\mathbb{C}}[x]$ the set of all $m\times n$ matrices over $\mathbb{R}$.
# Basis Vectors
Given a vector space $V$ defined over $\mathbb{F}$, a basis (also called the basis vectors) is a set of vectors that are linearly independent over $\mathbb{F}$ with the property that every vector in $V$ can be written as a linear combination of the basis vectors over $\mathbb{F}$. If there are infinite elements in $V$ then there are infinitely many basis vectors.

***
# Linear Independence
Given $n$ vectors the are linearly independent if no vector can be written as a linear combination of the others.
The more rigorous definition is that a set of vectors $\mathbf{v}_{k}$ is ***linearly dependant*** if there exists solution to the equation such that $a_{1},a_{2},\dots ,a_{k}$ are not all zero.$$a_{1}\mathbf{v}_{1}+a_{2}\mathbf{v}_{2}+\dots+a_{k}\mathbf{v}_{k}=0$$
If no non-trivial solution exists then the vectors are said to be ***linearly independent***.
This equation relates back to the idea of a vector being able to written as a linear combination of the others as if a non-trivial solution exists then$\text{ W.L.O.G } a_{1}\neq 0$ so $\displaystyle \mathbf{v}_{1}=-\frac{a_{2}}{a_{1}}\mathbf{v}_{2}-\frac{a_{3}}{a_{1}}\mathbf{v}_{3}-\dots--\frac{a_{n}}{a_{1}}\mathbf{v}_{k}$ a linear combination. You can also work backwards from the idea of a linear combination to get the equation.
*Also note that if $\mathbf{v}_{i}=0$ then the vectors are linearly* ***dependant***. 
# Span
Given a subset $S$ of vector space $V$, $\operatorname{span}(S)$ is defined as the set of all finite linear combinations of the elements in $S$.
For two 2D non-zero vectors $\operatorname{span}(\mathbf{v},\mathbf{w})$ is the whole plane it the are linearly independent and if $\mathbf{v}=c\mathbf{w}$ then it is a line containing $\mathbf{v}$. In general the span of $n$, $n$-dimensional linearly independent vectors is the full $n$D space.
***
# Norm
The norm of a vector denoted $\lVert \mathbf{v} \rVert$ (*or sometimes just $\lvert \mathbf{v} \rvert$)* is an idea of **length** and it must follow the following three axioms 
1. Non-Negativity $\lVert \mathbf{v} \rVert \geq0$
2. Zero Vector $\lVert \mathbf{v} \rVert = 0 \Leftrightarrow \mathbf{v}=0$
3. Homogeneity $\lVert a\mathbf{v} \rVert=|a|\lVert \mathbf{v} \rVert$
4. Triangle Inequality $\lVert \mathbf{u}+\mathbf{v} \rVert\leq \lVert \mathbf{u} \rVert+\lVert \mathbf{v} \rVert$

These all stem from Euclidean geometry and are properties that we would want to meaningfully talk about length.
***
# Multiplying Vectors
## Inner Product
There is no single canonical way to multiply vectors in fact there are multiple ways.
When multiplying vectors we want to take into account length and angle. When multiplying vectors we want the result to be large and positive if they are close, 0 if they are perpendicular and negative if they are somewhat opposite so we can think of multiplication as measuring how *"similar"* two vectors are.
We also want to have similar properties as regular multiplication so we have the inner product  $\langle , \rangle: V\times V\to \mathbb{R}$ that follows the axioms
1. Symmetry with conjugation $\langle  \mathbf{v},\mathbf{u}\rangle = \overline{\langle  \mathbf{u},\mathbf{v}\rangle}$ *(Note for $\mathbb{R}$ we get pure symmetry $\langle  \mathbf{v},\mathbf{u}\rangle = \langle  \mathbf{u},\mathbf{v}\rangle$)*
2. Linearity in the first slot $\langle a\mathbf{v}+b\mathbf{u},\mathbf{w} \rangle=a\langle \mathbf{v},\mathbf{w} \rangle+b\langle  \mathbf{u},\mathbf{w}\rangle$
3. Positive-definiteness $\langle \mathbf{v},\mathbf{v} \rangle\geq 0$ and $\langle \mathbf{v},\mathbf{v} \rangle=0 \Leftrightarrow \mathbf{v}=0$
*Notes: if we have pure symmetry then we also get linearity in the second slot and the reason for the conjugation for symmetry is to keep positive definiteness which is important as $\langle \mathbf{v},\mathbf{v} \rangle$ should be thought of as length squared which should have positive-definiteness.*

For equal vectors it makes sense to just choose their length squared so we get the property that $\langle \mathbf{v},\mathbf{v} \rangle=\lVert v \rVert^{2}$ and there is only one such inner product that satisfies this. For a vector space over $\mathbb{R}$ it is $$\langle \mathbf{v},\mathbf{w} \rangle =\frac{1}{4}((\lVert \mathbf{v}+\mathbf{u} \rVert)^{2}-(\lVert \mathbf{v}-\mathbf{u} \rVert)^{2} ) $$
**Proof**
$\lVert \mathbf{v}+\mathbf{w} \rVert^{2}= \langle \mathbf{v}+\mathbf{w},\mathbf{v}+\mathbf{w} \rangle=\langle \mathbf{v},\mathbf{v} \rangle+2\langle \mathbf{v},\mathbf{w} \rangle+\langle \mathbf{w},\mathbf{w} \rangle=\lVert \mathbf{v} \rVert^{2}+\lVert \mathbf{w} \rVert^{2}+2\langle \mathbf{v},\mathbf{w} \rangle$
$\lVert \mathbf{v}-\mathbf{w} \rVert^{2}= \langle \mathbf{v}-\mathbf{w},\mathbf{v}-\mathbf{w} \rangle=\langle \mathbf{v},\mathbf{v} \rangle-2\langle \mathbf{v},\mathbf{w} \rangle+\langle \mathbf{w},\mathbf{w} \rangle=\lVert \mathbf{v} \rVert^{2}+\lVert \mathbf{w} \rVert^{2}-2\langle \mathbf{v},\mathbf{w} \rangle$
Using this we get our inner product as $\displaystyle\langle \mathbf{v},\mathbf{w} \rangle =\frac{1}{4}((\lVert \mathbf{v}+\mathbf{u} \rVert)^{2}-(\lVert \mathbf{v}-\mathbf{u} \rVert)^{2} ) \quad \square$
This product does satisfy all 3 inner product axioms but I won't show all the details

Note that $\langle \mathbf{v},\mathbf{v} \rangle=\lVert v \rVert^{2}$ is not required and you can define the norm and inner product independently but this is a natural axiom to state as it follows from basic Euclidean geometry and gives rise to many useful properties. It also makes the inner product unique to the norm.
## Dot Product $\mathbf{v}\cdot \mathbf{w}$
In [[Euclidean Geometry Basics|Euclidean Geometry]] of $\mathbb{R}^{n}$ we choose the norm which is the notion of length to be $\lVert \mathbf{v} \rVert=\sqrt{v_{x}^{2}+v_{y}^{2}+\dots}$ which is simply the Pythagorean theorem. 
Using the inner product in terms of the norm we get that $\langle \mathbf{v},\mathbf{u} \rangle=u_{x}v_{x}+u_{y}v_{y}+\dots$ Giving us the familiar dot product denoted as $\mathbf{v}\cdot \mathbf{u}$.
We can also derive it geometrically.
The dot product of $\mathbf{v}\cdot \mathbf{w}$ is equal to projecting $\mathbf{w}$ onto $\mathbf{v}$ and multiplying the lengths $\mathbf{v}$ and the new projected vector. It is signed so it the projection is pointing the opposite way of $\mathbf{v}$ than the dot product is negative.
Using some simple [[Trigonometric Functions|Trig]] we find that $$\mathbf{v}\cdot \mathbf{w}=|\mathbf{v}||\mathbf{w}| \cos \theta$$

The dot product is *commutative*. This arises from the fact that projections scale linearly. 
If $\mathbf{v},\mathbf{w}$ had the same length then you can use symmetry to get the it is commutive in this scenario. Say you scale $\mathbf{v}$ to get $k\mathbf{v}$, then $k\mathbf{v}\cdot \mathbf{w}=k(\mathbf{v}\cdot \mathbf{w})$ as the project of $\mathbf{w}$ remains the same but then length of $\mathbf{v}$ has scaled by $k$. But if you consider $\mathbf{w}\cdot k\mathbf{v}$ then the length of the projection of $\mathbf{v}$ scales by $k$ yielding $\mathbf{w}\cdot k\mathbf{v}=k(\mathbf{w}\cdot \mathbf{v})=k(\mathbf{v}\cdot \mathbf{w})$. 
With any pair of vectors you can always take out some scaling factor to get this form of $v,w$ with the same length meaning for all vectors the dot product is commutative.

The dot product is also *distributive over vector addition* meaning $a\cdot(b+c)=a\cdot b+a\cdot c$ for any length vectors
**Proof**
$\begin{pmatrix}a_{1} \\ \vdots\\ a_{n} \end{pmatrix}\cdot \begin{pmatrix}b_{1}+c_{1} \\ \vdots \\ b_{n}+c_{n}\end{pmatrix}=a_{1}(b_{1}+c_{1})+\dots a_{n}(b_{n}+c_{n})$
$\begin{pmatrix}a_{1} \\ \vdots \\ a_{n}\end{pmatrix}\cdot \begin{pmatrix}b_{1} \\ \vdots \\ b_{n}\end{pmatrix}+\begin{pmatrix}a_{1} \\ \vdots \\ a_{n}\end{pmatrix}\cdot \begin{pmatrix}c_{1} \\ \vdots \\ c_{n}\end{pmatrix}=a_{1}b_{1}+a_{1}c_{1}+\dots a_{n}b_{n}+a_{n}c_{n}=a_{1}(b_{1}+c_{1})+\dots a_{n}(b_{n}+c_{n})$
Hence $a\cdot(b+c)=a\cdot b+a\cdot c \quad \square$.
### Dual Vector
We also find that the dot product is equivalent to a linear transformation by the first vector as a matrix e.g. $$\begin{pmatrix}
a \\
b
\end{pmatrix}\cdot \begin{pmatrix}
c \\
d
\end{pmatrix}\equiv \begin{pmatrix}
a & b
\end{pmatrix}\begin{pmatrix}
c \\
d
\end{pmatrix}\equiv c\cdot a+d\cdot b$$
And this generalises to any $n$-length vector.

**2D Example Proof**
To see why we can imagine placing a copy of the real number line on the 2D plane (rotated at any angle) with the condition that 0 lies on the origin. Then define $\hat{u}$ to be the vector from the origin to where 1 lies on this number line. Then define a function that takes any 2D vector and projects it onto this number line with the number it lands on as output $L:\mathbb{R}^{2}\to \mathbb{R}$. Since this is a linear function we can find a matrix to describe this transform. By considering $\hat{i},\hat{j}$ and using a line of symmetry we can find that this is $\begin{pmatrix}\hat{u}_{x} & \hat{u}_{y}\end{pmatrix}$. Applying this transform is computationally equivalent to taking the dot product. If we have a non-unit vector $\mathbf{u}$ we can simply write it as $k\hat{u}$ and the dot product scales linearly so it still works.

This gives rise to the idea of a **Dual Vector**, that is given any linear transform which output is the number line you can find a vector such that taking the dot product with that vector is equivalent to applying the transform.
## Vector Cross Product $\mathbf{v} \times \mathbf{w} = |\mathbf{v}||\mathbf{w}| \sin (\theta) \hat{n}$
The *cross product* of two vectors is defined as vector $\mathbf{p}$ that has magnitude equal to that the signed area of the parallelogram $\mathbf{v},\mathbf{w}$ define and direction perpendicular to both $\mathbf{v},\mathbf{w}$ *following the right hand rule mentioned later*.
It is only defined in 3 *(and 0,1,7)* dimensions.

We can compute the magnitude using the [[Determinant]] taking $\mathbf{v},\mathbf{w}$ to be the column vectors of a matrix $A$ and computing $\det A$. *This is why the cross product is signed*. This is because the determinant measures the factor that area scales. Since $\hat{i}\times \hat{j}=1$ as they bound a unit square. $\mathbf{v},\mathbf{w}$ are simply $\hat{i},\hat{j}$ after a transformation under $A$ so the determinant is the area we are looking for. *It is positive if $\mathbf{v}$ is on the right of $\mathbf{w}$ and negative if it's on the left.*

To compute the cross product fully we can take the determinant of a special [[Matrices|Matrix]] $$\mathbf{v}\times \mathbf{w}=\det \begin{pmatrix}
\hat{i}  & v_{1} & w_{1}\\ 
\hat{j}  & v_{2} & w_{2}\\
\hat{k}  & v_{3} & w_{3}
\end{pmatrix}=\hat{i}(v_{2}w_{3}-v_{3}w_{2})+\hat{j}(v_{3}w_{1}-v_{1}w_{3})+\hat{k}(v_{1}w_{2}-v_{2}w_{1})$$
*Note that this is equivalent to $\det\begin{pmatrix}\hat{i} & \hat{j} & \hat{k} \\ v_{1} & v_{2} & v_{3} \\ w_{1} & w_{2} & w_{3} \end{pmatrix}$ as determinant doesn't change under a transpose. Also note that putting unit vectors as entries in a matrix is a notational shorthand.*

**Explanation**
First we define a function $$f \begin{pmatrix}x \\ y \\ z\end{pmatrix}=\det \begin{pmatrix}
x  & v_{1} & w_{1}\\ 
y  & v_{2} & w_{2}\\
z  & v_{3} & w_{3}
\end{pmatrix}$$
This function geometrically is computing the signed volume of the parallelepiped bounded by $\overrightarrow{(x,y,z)},\mathbf{v},\mathbf{w}$
This function is $f:\mathbb{R}^{3}\to \mathbb{R}$ and it is linear since the [[Determinant]] is *multi-linear* and we are changing a single slot. Since it is a linear transform we can define the function as matrix multiplication and more specifically since it is a transformation to $\mathbb{R}$ there must exist a dual vector $$\mathbf{p}\text{ s.t } \mathbf{p}\cdot \begin{pmatrix}x \\ y \\ z\end{pmatrix}=f\begin{pmatrix}x \\  y\\ z\end{pmatrix}$$
Meaning we can compute $f$ by taking this dot product so we get 
$$
\begin{aligned}
f\begin{pmatrix}
x \\
y \\
z
\end{pmatrix}&=p_{1}x+p_{2}y+p_{3}z\\&=\det \begin{pmatrix}
x  & v_{1} & w_{1}\\ 
y  & v_{2} & w_{2}\\
z  & v_{3} & w_{3}

\end{pmatrix}
\\
&=x(v_{2}w_{3}-v_{3}w_{2})+y(v_{3}w_{1}-v_{1}w_{3})+z(v_{1}w_{2}-v_{2}w_{1})
\end{aligned}
$$
By comparing coefficients of $x,y,z$ we get the coordinates of $\mathbf{p}$ and writing it as a sum of a linear combination of unit vectors gets the exact same thing as the determinant as the matrix with unit vectors as entries.

We can think of this as asking for any two given vectors $\mathbf{v},\mathbf{w}$, what vector $\hat{p}$ has the property that for any other vector $\mathbf{x}$,  $p\cdot \mathbf{x}$ *(projecting $\mathbf{x}$ onto $\mathbf{p}$ and multiplying the length of $\mathbf{p}$ by the length of this projected vector)* is equivalent to the volume of the parallelepiped bound by $\mathbf{x},\mathbf{v},\mathbf{w}$. *As we have just shown $\mathbf{p}$ is given exactly by $\mathbf{v}\times \mathbf{w}$*.

We can also think about this by finding the volume of the parallelepiped geometrically. First find the area of the base which is the area of the parallelogram bounded by $\mathbf{v},\mathbf{w}$ then multiply by the component of $\mathbf{x}$ which is perpendicular to both $\mathbf{v},\mathbf{w}$. But this is equivalent to taking the dot product of a vector perpendicular to $\mathbf{v},\mathbf{w}$ as the dot product is itself a projection. 
There are two such vectors that satisfy this property *(going in opposite directions)* $\hat{p}$ which is the cross product we are looking for is the one such that when the dot product is negative so is the volume of the parallelepiped by the right hand rule is negative.

Using this idea of the vector that $\mathbf{p}$ is the vector with length equal to the area of the parallelogram we can find using some basic [[Trigonometric Functions|Trig]] that the are is equal to $|\mathbf{v}||\mathbf{w}|\sin\theta$ where $\theta$ is the angle between $\mathbf{v},\mathbf{w}$ such that $0\leq\theta\leq \pi$. Then we just want a vector perpendicular to both $\mathbf{v},\mathbf{w}$ that follows the right hand rule. We call this normal vector $\hat{n}$ which has magnitude 1 to preserve the length of $\mathbf{p}$.

It is **Distributive**
$$
\begin{aligned}
a\times b & =(a_{1}\mathbf{i}+a_{2}\mathbf{j}+a_{3}\mathbf{k})\times(b_{1}\mathbf{i}+b_{2}\mathbf{j}+b_{3}\mathbf{k}) \\
 & =a_{1}b_{1}(\mathbf{i}\times\mathbf{i})+a_{1}b_{2}(\mathbf{i}\times\mathbf{j})+a_{1}b_{3}(\mathbf{i}\times\mathbf{k}) \\
 & +a_2b_1(\mathbf{j}\times\mathbf{i})+a_2b_2(\mathbf{j}\times\mathbf{j})+a_2b_3(\mathbf{j}\times\mathbf{k}) \\
 & +a_3b_1(\mathbf{k}\times\mathbf{i})+a_3b_2(\mathbf{k}\times\mathbf{j})+a_3b_3(\mathbf{k}\times\mathbf{k} \\
 & =a_{1}b_{2}\mathbf{k}+a_{1}b_{3}(-\mathbf{j})+a_{2}b_{1}(-\mathbf{k})+a_{2}b_{3}(\mathbf{i})+a_{3}b_{1}(\mathbf{j})+a_{3}b_{2}(-\mathbf{i}) \\\\
 a\times b& =(a_{2}b_{3}-a_{3}b_{2})\mathbf{i}+(a_{3}b_{1}-a_{1}b_{3})\mathbf{j}+(a_{1}b_{2}-a_{2}b_{1})\mathbf{k}\\ \\
a \times b & =
\begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
a_1 & a_2 & a_3 \\
b_1 & b_2 & b_3
\end{vmatrix}=\mathbf{i}
\begin{vmatrix}
a_2 & a_3 \\
b_2 & b_3
\end{vmatrix}-\mathbf{j}
\begin{vmatrix}
a_1 & a_3 \\
b_1 & b_3
\end{vmatrix}+\mathbf{k}
\begin{vmatrix}
a_1 & a_2 \\
b_1 & b_2
\end{vmatrix} \\ \\
 & =(a_2b_3-a_3b_2)\mathbf{i}+(a_3b_1-a_1b_3)\mathbf{j}+(a_1b_2-a_2b_1)\mathbf{k}
 \end{aligned}
 $$
$\theta$ is the angle between $a$ and $b$ where $0 \leq \theta \leq 180 \degree$. And $\hat{n}$ is the unit vector perpendicular to both $a$ and $b$ 
### Right Hand Rule
The direction of $\hat{n}$ depends on the right-hand rule, swapping $a$ and $b$ means that $\hat{n} \mapsto -\hat{n}$ therefore $b \times a = |b||a| \sin (\theta) (-\hat{n}) = - a\times b$, this means it is **anti-commutative**
![[Vectors-Right-Hand-Rule.png|350]]
### Finding Volumes - Scalar Triple Product $a \cdot (b \times c)$
$$a \cdot (b \times c) \equiv\begin{vmatrix} a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \\ c_1 & c_2 & c_3 \end{vmatrix}\equiv a_1(b_2c_3 - b_3c_2) + a_2(b_3c_1 - c_3b_1) + a_3(b_1c_2 - b_2c_1) $$
This is simply the definition/what a [[Determinant]] represents and using the geometrical definition of the cross product.
***
# Straight Lines
***Colinear***: Points are said to be *collinear* if they all lie on the same straight line
## $r = a + \lambda b$
The equation of a straight line vector passing through point $a$ and is parallel to vector $b$ is $r = a + \lambda b$ where $r$ is the **position** vector of a general point on the line. 
*So by taking varying values of $\lambda$ you can find the position vectors of varying points that lie on the straight line.*
The line has cartesian equation $\displaystyle \frac{x-a_1}{b_1} = \frac{y-a_2}{b_2} = \frac{z-a_3}{b_3} =\lambda$

## $(r-a)\times b = 0$
Suppose $a$ is the position vector of a point on a line and the line is parallel to $b$. Let $r$ be the position vector of a general point on the line. so $\overrightarrow{AR} = \overrightarrow{OR} - \overrightarrow{OA} = r-a$. Since $\overrightarrow{AR}$ is parallel to $b$, $\overrightarrow{AR} \times b = 0$ so $(r-a)\times b = 0$

***
# Planes 
***Coplanar***: Points are said to be *coplanar* if they all lie on the same plane
## $r = a + \lambda b + \mu c$
The vector of a plane that through position vector $a$ is: $r = a + \lambda b + \mu c$ where r is the **position** vector of a general point on the plane with $a$ being the position vector of a *fixed* arbitrary point on the plane and $b, c$ are *non-parallel, non-zero* vectors ***on the plane***
*The intuition of this is that $a$ gets you from the origin onto the plane and $\lambda b, \mu c$ allow you to move across the plane*

The cartesian equation of a plane is $px + qy + rz = s$ where the normal vector to the plane is $(p, q, r)$. You can find the cartesian equation given the vector equation using the cross product 

## $r \cdot n = k$
Suppose a plane $\Uppi$ passes through $A$ and has normal vector $n$ and let $R$ be an arbitrary point on $\Uppi$. Then $\overrightarrow {AR} = r - a$. Since $\overrightarrow {AR}$ lies on $\Uppi$, $\overrightarrow {AR}\cdot n = 0$ so $(r-a) \cdot n = 0 \Rightarrow r \cdot n = a \cdot n$ where $a \cdot n$ is a constant so $a\cdot n = k$. This can also be written as $n_1x+n_2y+n_3z = k$. Where $k$ represents the [[Vectors#Perpendicular Distances|Perpendicular Distance]] from the origin to the place if $n = \hat{n}$

***
# Angles Between Vectors and Planes
The ***Acute*** angle $\theta$ between 2 intersecting ***Straight Lines*** *(with direction vectors $a, b$)* is given with the formula $\displaystyle\cos \theta = \left|\frac{a \cdot b}{|a||b|}\right|$

The ***Acute*** angle $\theta$ between ***Straight Line*** *(with direction vectors $r = a + \lambda b$)* and ***Plane*** *(with equation $r.n = k$)* is given with the formula $\displaystyle\sin \theta = \left|\frac{b \cdot n}{|b||n|}\right|$

The ***Acute*** angle $\theta$ between 2 intersecting ***Planes*** *(with equations vectors $r.n_1 = k_1$ and $r.n_2 = k_2$)* is given with the formula $\displaystyle\cos \theta = \left|\frac{n_1 \cdot n_2}{|n_1||n_2|}\right|$

***
# Points of Intersection
To find if 2 lines $l_1: r = a + \lambda b$ and $l_2: r = c + \mu d$ intersect set them equal and solve the system of equations, if solutions for $\mu$ and $\lambda$ exist then they intersect, if not then there is no intersection.
Two lines are **skew** if they do not intersect but are parallel meaning solutions for  $\mu$ and $\lambda$ don't exist but their direction vectors are scalar multiples of each other.

To find the intersection of a plane and a line have the plane in the form $r.n = k$ then sub in the vector equation $r = a + \lambda b$ into the plane equation. 

***
# Perpendicular Distances
To find the shortest/perpendicular distance between 2 lines $l_1: r = a + \lambda b$ and $l_2: r = c + \mu d$, Let $A$ be a point on $l_1$ and $B$ be a point on $l_2$ then shortest/perpendicular distance between $l_1$ and $l_2$ will be the straight line segment $AB$ that is perpendicular to both lines. So $l_1 \cdot AB = l_2 \cdot AB = 0$ you can then solve for $\mu$ and $\lambda$
To find shortest distance between a line $l$ and a point $A$, Let $B$ be a point on $l$ then $l \cdot AB = 0$. You can then find the coordinates of $B$ so you can find the distance
The perpendicular distance from the origin to the plane $r\cdot \hat n = k$ is simply k
The perpendicular distance from a point $(x_0, y_0, z_0)$ to the plane $ax + by + cz = d$ is 
$$\frac{|ax_0 + by_0 + cz_0 - d|}{\sqrt{a^2 + b^2 + c^2}}$$
The distance between two parallel planes $ax + by + cz = d_1$ and $ax + by + cz = d_2$ is $$\frac{|d_1 - d_2|}{\sqrt{a^2 + b^2 + c^2}}$$

***
# Direction of Cosines
If a line is parallel to the vector $a = xi +yj+zk$ the direction ratios are $x:y:z$ and the direction of [[Trigonometric Functions|Cosines]] of the line are $$\cos \theta_x = \frac{x}{|a|} = l \quad \cos \theta_y = \frac{y}{|a|} = m \quad \cos \theta_z = \frac{z}{|a|} = n $$
The sum of the squares of the direction cosines is always one $$l^2 + m^2+n^2 = \frac{x^2+y^2+z^2}{|a|^2} = \frac{|a|^2}{|a|^2}= 1$$