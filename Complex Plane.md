---
tags:
  - maths/complex-numbers
---
# Definitions
[[Complex Numbers]] can be represented on a **Cartesian Plane** *(called the complex plane or an argand diagram)* as a point $(x, y)$ or [[Vectors|Vector]] $\begin{pmatrix} x \\ y \end{pmatrix}$ where $z=x+iy$. Therefore the $x$-axis is the real axis and the $y$-axis is the imaginary axis.

---
# Loci
## Circle  $\left|z-z_1\right|=r$
Given $z_1, z_2$,  $|z_2-z_1|$ is the distance between points $z_1, z_2$. So you can replace $z_2$ with the general point $z$ to obtain a locus of points that are all equidistant form $z_1$. Therefore you get a circle centre $z_1$ described by to locus $\left|z-z_1\right|=r$
## Circle $|z-z_1| = k|z-z_2|$ 
The locus of points $z$ that satisfy $|z-z_1| = k|z-z_2|, \space k\in \mathbb{R}, k>0, k\neq 1$ is a **circle**.
You can find the equation by splitting $z$ into $x+iy$ then squaring both sides *(which gets rid of modulus and $i$ terms*) and solving from there.
In basic terms it's the locus of points that are $k$ times further from $a$ than they are from $b$.
*When $k=1$ it's a straight line perpendicular bisector which can be thought of as a circle with infinite radius*
## Circle Arc $\arg(\frac{z-z_1}{z-z_2}) = \theta$
The Locus $\displaystyle \arg\left(\frac{z-z_1}{z-z_2}\right) = \theta$ is an arc of a circle with end points $z_1,z_2$. The arc is drawn **anticlockwise** from $z_1$ to $z_2$. You can find the equation of a circle by considering the 2 congruent isosceles triangles formed by $z_1CM$, $z_2CM$ where $C$ is the circle centre and $M$ is the midpoint of the line $z_1z_2$.
## Perpendicular Bisector $\left|z-z_1\right|=\left|z-z_2\right|$
Given $z_1, z_2$ the locus $\left|z-z_1\right|=\left|z-z_2\right|$ Is the perpendicular bisector of the line segment connecting $z_1, z_2$
## Half Line $\arg \left(z-z_1\right)=\theta$ 
Given $z_1$ the locus of points described by $\arg \left(z-z_1\right)=\theta$ forms a straight half-line that makes angle $\theta$ with the line extending from $z_1$ that is parallel to the real axis but does not include $z_1$

---
# Transformations on the Complex Plane
You can transform loci by mapping the $z$ plane onto a $w$ plane to get $z = x+iy \rightarrow w = u+iv$
$w = z+a+bi$ represents translation by [[Vectors|Vector]] $\begin{pmatrix} a \\ b \end{pmatrix}$, $a,b \in \mathbb{R}$
$w = kz$, $k\in \mathbb{R}$ represents enlargement with scale factor $k$ centre $(0,0)$
$w = iz$ represents anti-clockwise rotation of $\frac{\pi}{2}$ about $(0,0)$
## Möbius transformations
They are transformations in the form $$w = \frac{az+b}{cz+d} \quad a,b,c,d \in \mathbb{C}$$