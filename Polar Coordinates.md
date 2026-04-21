---
tags:
  - maths/geometry
---
# Definition
The coordinates of $P$ can be written as $(r,\theta)$ in polar form where $r$ is the distance from the origin and $\theta$ is the angle of rotation counter-clockwise from the positive $x$-axis. This is very similar to the [[Complex Numbers#Modulus Argument Form $r( cos theta+i sin theta)$|Modulus-Argument Form of Complex Numbers]]

---
# Conversion to Cartesian
To convert from polar to Cartesian you can use the following:
- $r \cos\theta = x$
- $r \sin\theta = y$
- $r^2 = x^2 + y^2$
- $\theta = \arctan(\frac{y}{x})$

---
# Sketching curves
Common curves are: 
$r = a$, a circle with centre origin radius $a$ 
$\theta = \alpha$, a half line making angle $\alpha$ 
$r = a\theta$, a spiral starting at origin

$r = a(p + q \cos\theta)$, They are called ***Cardioids*** They are defined for all $\theta$ if $p \geq q$ so to make $r>0$ - this can be defined in some contexts but for A-level this is undefined)

Cardioids fall into 2 categories "egg" shaped and those with a "dimple", egg shaped are [[Concavity|Convex]] curves, dimples are [[Concavity|Concave]] at $\theta = \pi$. They are egg shaped when $p \geq 2q$ and dimple shaped if $q \leq p < 2q$ - This is proved by considering the number of tangents that are perpendicular to the initial line.

---
# Area enclosed by a Polar Curve
The area enclosed by a polar curve and half lines $\theta = \alpha, \theta = \beta$ where $\theta$ is measured in radians is given as: $$A = \frac{1}{2} \int_{\alpha}^{\beta} r^2 d\theta$$
Very useful trig identities for [[Integration]] 
$$\sin^2\theta = \frac{1-\cos 2\theta}{2}\quad\cos^2\theta = \frac{1+\cos 2\theta}{2}$$

---
# Tangent to Polar Curve
You can differentiate parametrically to get:
$$\frac{dy}{dx} = \frac{dy /d\theta}{dx/d\theta}$$

To find a tangent line to the parallel to the initial set: $\displaystyle\frac{dy}{d\theta} = 0$
To find a tangent perpendicular to the initial line set: $\displaystyle\frac{dx}{d\theta} = 0$
