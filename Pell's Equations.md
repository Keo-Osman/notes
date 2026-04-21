---
tags:
  - maths/number-theory
---
# Definition
Pell's equations are equations in the form $x^2-dy^2=1$ where $d$ is not a square.
There are infinite integer solutions to the equation.
***
# Norm
Define a number $z= x+y\sqrt{d}$, then the *conjugate* of $z$ is $\bar{z}=x-y\sqrt{d}$. The conjugate is *multiplicative*.
The *Norm* of $z$ is given as $N(z)=z \bar{z}=x^2-dy^2$. *Note the resemblance to [[Complex Numbers]].*
The Norm is *multiplicative* - $N(z_{1}z_{2})=N(z_{1})N(z_{2})$. 
This leads us to seeing that $x^2-dy^2=1$ is the same as $N(z)=1$
Using the fact that $N$ is multiplicative, $N(z)=1\implies N(z^k)=1$. So from one solution we can generate infinitely many.
***
# Fundamental Solution
We can find a *fundamental solution* $\epsilon=x_{0}+y_{0}\sqrt{d}, \ x, y, \in \mathbb{N}$ such that every solution $(x, y)$ is found by $$x+y\sqrt{d}=\epsilon^n=(x_{0}+y_{0}\sqrt{d})^n$$
**Proof**
1. Consider $\alpha$ to be the smallest real in the for $x+y\sqrt{d}>1$ and $N(\alpha)=1$.
2. Consider $\beta=a+b\sqrt{d}$ such that $(a,b)$ is another solution to $X^2-dY^2=1$.
3. Let $k$ be such that $\alpha^k\leq\beta<\alpha^{k+1}$. *This is guaranteed to exist as $\alpha^n$ is continuous and these inequalities cover the whole domain.*
4. Since $N(\alpha)=1\implies \ \displaystyle \frac{1}{x+y\sqrt{d}} \times \frac{x-y\sqrt{d}}{x-y\sqrt{d}}=\frac{x-y\sqrt{d}}{z \bar{z}=N(\alpha)}=x-y\sqrt{d}$
5. Define $\displaystyle 1 \leq\gamma=\frac{\beta}{\alpha^k}=(a-b\sqrt{d})(x-y\sqrt{d})^k$. Since $N$ is multiplicative $N(\gamma)=1$.
6. Expanding $\gamma$ gets something in the for $r+s \sqrt{d}$. Since $N(\gamma)=1$, $1 \leq\gamma \implies \bar{\gamma} \leq  1$.
7. Hence $r-s\sqrt{d}\leq 1 \leq r+s\sqrt{d} \implies r-s\sqrt{d}\leq r+s\sqrt{d}\implies 0 <+2s\sqrt{d}\implies s\geq 0$.
8. We can also prove that $r\geq 0$ as $r=\frac{\gamma+\bar{\gamma}}{2}$ and by *AM-GM* $r=\frac{\gamma+\bar{\gamma}}{2}\geq \sqrt{\gamma\cdot\ \bar{\gamma}}=\sqrt{\gamma\cdot\frac{1}{\gamma}}=1$. *($\bar{\gamma}=\gamma^{-1}$ by the same algebra in step 4 since $N(\gamma)=1$).*
9. Since $\gamma<\alpha$ the minimality of $\alpha$ is contradicted unless $\gamma=1$ which only happens when $\beta=\alpha^k$ as desired.

***
# General and Recursive Solutions of Pell's Equations
INSERT PROOF
Let $(x_{0}, y_{0})$ be the *fundamental solution* and $(x_{n-1}, y_{n-1})$ be the $n$th solution, then
$$
x_{n-1}=\frac{1}{2}((x_{0}+y_{0}\sqrt{d})^n+(x_{0}-y_{0}\sqrt{d})^n), \quad y_{n-1}=\frac{1}{2\sqrt{d}} ((x_{0}+y_{0}\sqrt{d})^n-(x_{0}-y_{0}\sqrt{d})^n)
$$
$$
x_{n}=2x_{0}x_{n-1}-x_{n-2}, \quad y_{n}=2x_{0}y_{n-1}-y_{n-2}
$$

***
# Negative Pell's Equations