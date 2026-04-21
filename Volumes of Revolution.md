---
tags:
  - maths/calculus
---
# Volumes of Revolution
## Cartesian
In regular integration of a function $f(x)$ you obtain the area under by considering smaller rectangles with height and width $dx$ so the approximate area is $\sum f(x)dx$ as $dx \rightarrow 0$ this is written as $\int f(x)dx$

For a Volume of Revolution you do the same however the areas are small cylindrical volumes. These volume is $\pi r^2h$ in this case $f(x)$ is the radius and we consider $h$ (the width in the case) going to zero so the approximate area $\sum f(x)^2\pi dx$ as $dx \rightarrow 0$. The exact volume is written as $$\pi \int_a^b f(x)^2dx$$

You can do the same thing for a volume of revolution around the y axis by rearranging to get $x = f(y)$ then the volume will be $$\pi \int_a^b{ f(y)^2dy}$$Keep in mind that $a$ and $b$ are values of $y$ and that the radius of the volume is from the $y$ axis going across parallel to the $x$ axis until the curve.

## Parametric 
For a parametric equation defined $y = g(t), x = f(t)$ you can find the volumes of revolution with the following formulae:

**About the x axis** $$\pi \int_{t=q}^{t=p} g(t)^2 \frac{dy}{dt} dt$$
**About the y axis** $$\pi \int_{t=q}^{t=p} f(t)^2 \frac{dx}{dt} dt$$
***
# Arc Length
## Cartesian
The arc length of $y = g(x)$ from $A(x_A, y_A)$ and $B(x_B, y_B)$ is: $$s = \int_{\displaystyle x_A}^{\displaystyle x_B} \sqrt{1 + \left(\frac{dy}{dx}\right)^2} dx \quad \text{or} \quad s = \int_{\displaystyle y_A}^{\displaystyle y_B} \sqrt{1 + \left(\frac{dx}{dy}\right)^2} dy$$
## Parametric
For $x = f(t)$, $y = g(t)$, the arc length from $A(f(t_A), g(t_A))$ to $B(f(t_B), g(t_B))$ is: $$s = \int_{\displaystyle t_A}^{\displaystyle t_B} \sqrt{\left(\frac{dx}{dt}\right)^2 + \left(\frac{dy}{dt}\right)^2} dt$$
#### Polar
For $r = g(\theta)$, the arc length from half lines $\theta = \alpha$ to $\theta = \beta$ is: $$s = \int_{\displaystyle \alpha}^{\displaystyle \beta} \sqrt{r^2 + \left(\frac{dr}{d\theta}\right)^2} d\theta$$

***
# Surface Area of Volume of Revolution
The area, $S$, of the surface generated when the arc $A B$ on the curve $C$ is rotated completely about the $x$-axis is $2 \pi \int y \mathrm{ds}$, and about the $y$-axis is $2 \pi \int x \mathrm{ds}$.
## Cartesian
**About the $x$-axis:** $$S=2 \pi \int_{\displaystyle x_A}^{\displaystyle x_B} y \sqrt{1+\left(\frac{\mathrm{d} y}{\mathrm{~d} x}\right)^2} \mathrm{~d} x$$
**About the $y$-axis:** $$S=2 \pi \int_{\displaystyle y_A}^{\displaystyle y_B} x \sqrt{1+\left(\frac{\mathrm{d} x}{\mathrm{~d} y}\right)^2} \mathrm{~d} y \quad \text{or} \quad S=2 \pi \int_{\displaystyle x_A}^{\displaystyle x_B} x \sqrt{1+\left(\frac{\mathrm{d} y}{\mathrm{~d} x}\right)^2} \mathrm{~d} x$$
## Parametric
**About the $x$-axis:** $$S=2 \pi \int_{\displaystyle t_A}^{\displaystyle t_B} y \sqrt{\left(\frac{\mathrm{d} x}{\mathrm{~d} t}\right)^2+\left(\frac{\mathrm{d} y}{\mathrm{~d} t}\right)^2} \mathrm{~d} t$$
**About the $y$-axis:** $$S=2 \pi \int_{\displaystyle t_A}^{\displaystyle t_B}x \sqrt{\left(\frac{\mathrm{d} x}{\mathrm{~d} t}\right)^2+\left(\frac{\mathrm{d} y}{\mathrm{~d} t}\right)^2} \mathrm{~d} t$$
## Polar
**About the initial line $\theta = 0$**  $$S=2 \pi \int_{\displaystyle \alpha}^{\displaystyle \beta} r \sin \theta \sqrt{r^2+\left(\frac{\mathrm{d} \theta}{\mathrm{d} r}\right)^2} \mathrm{~d} \theta$$
**About the line $\theta= \displaystyle\pm \frac{\pi}{2}:$** $$ S=2 \pi \int_{\displaystyle \alpha}^{\displaystyle \beta} r \cos \theta \sqrt{r^2+\left(\frac{\mathrm{d} \theta}{\mathrm{d} r}\right)^2} \mathrm{~d} \theta$$

