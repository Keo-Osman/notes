---
tags:
  - maths/numerical-methods
---
# Simpson's Rule for Approximating [[Integration|Integrals]]
**Theorem**
$$\int_a^b g(x) dx \approx \frac{h}{3}\left(y_0 + 4\sum_{k=1}^{n} y_{2k-1} + 2\sum_{k=1}^{n-1} y_{2k} + y_{2n}\right)$$

**Proof**
This works by approximating the function with quadratic curves. First we will find an approximation of the integral using a quadratic curve defined by passing three points: $x_{0} = a, x_{1} = \frac{a+b}{2}, x_{2} = b$ with step $h =\frac{b-a}{2}$. Then once we have a formula for approximating an integral with one quadratic curve we can generalise by splitting the integral into $n$ integrals and approximating each one individually with a quadratic curve.

First approximating $\displaystyle\int_{a}^{b}f(x)dx$ with a single quadratic.
We will first make the substitution $u = x-x_{1}$ so we get symmetric bounds (this moves $x_{1}$ to the origin) meaning we have $\displaystyle\int_{-h}^{h}f(u+x_{1})du$.
We now seek a quadratic $P(x) = Ax^{2}+Bx+C$ that passes through $(-h, y_{0}), (0, y_{1}), (h, y_{2})$ with some algebra we obtain 
$$
A = \frac{y_{0} - 2y_{1}+y_{2}}{2h^{2}}, \quad C = y_{1}
$$
$B$ doesn't matter over the integral as $Bx$ is odd.
$$
\displaystyle\int_{a}^{b}f(x)dx = \displaystyle\int_{-h}^{h}f(u+x_{1})du \approx \int_{-h}^{h}Ax^{2}+Bx+C=\frac{h}{3}(y_{0}+4y_{1}+y_{2})
$$

Splitting the integral into $2n$ sub partitions and summing them achieves the general form.