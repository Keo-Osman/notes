---
tags:
  - maths/algebra
---
# Definition
A [[Functions|Funciton]] $f$ is ***concave-(down)*** on $I$ if $\forall x_{1},x_{2}\in I$ the chord between $x_{1},x_{2}$ lies below $f$.
This leads to the formal definition $$\forall x_{1},x_{2}\in I, 0\leq\lambda\leq 1 \quad f(\lambda x_{1}+(1-\lambda)x_{2})\geq \lambda f(x_{1})+(1-\lambda)f(x_{2})$$
**Derivation**
1. First we construct the line between $x_{1},x_{2}$ getting $\displaystyle y=\frac{f(x_{2})-f(x_{1})}{x_{2}-x_{1}}(x-x_{1})+f(x_{1})$.
2. Then we can use $x=\lambda x_{1}+(1-\lambda)x_{2}, \quad 0 \leq \lambda \leq 1$ to get a formula for any point $x \in [x_{1},x_{2}]$. *This is linearly interpolating between $x_{1}$ and $x_{2}$.*
3. We want the line to lie below $f$ so we get the inequality $f(x)\geq y$ which is equivalent to $\displaystyle f(\lambda x_{1}+(1-\lambda)x_{2} \geq \frac{f(x_{2})-f(x_{1})}{x_{2}-x_{1}}(\lambda x_{1}+(1-\lambda)x_{2}-x_{1})+f(x_{1}) )$.
4. With some basic algebra to clean up on *RHS* we get $f(\lambda x_{1}+(1-\lambda)x_{2})\geq \lambda f(x_{1})+(1-\lambda)f(x_{2})$ as desired $\quad \square.$

A function is ***convex-(down)*** *(equivalently concave-up)* if the reverse inequality holds e.g. the chord lies above $f$. *The exact same derivation as before*.