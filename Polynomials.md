---
tags:
  - maths/algebra
---
# Polynomial Operations
## Multiplication
Let $A(x)=\sum a_{i}x^i, \ B(x)=\sum b_{i}x^i, \text{ and } C(x)=\sum c_{i}x^i=A(x)B(x)$ then $$c_{j}=a_{0}b_{j}+a_{1}+b_{j-1}+\dots+a_{j}b_{0}=\sum_{\substack{s+t=j\\s,t\geq 0}}a_{s}b_{t}$$
## Division
Let $f(x),g(x) \in K[x]$ where $K$ is one of $\mathbb{Z},\mathbb{Q},\mathbb{R},\mathbb{C}, \mathbb{Z}_{n}$ then $$f(x)=Q(x)g(x)+R(x)$$ where $Q(x),R(x) \in K[x]$ and the degree of $R(x)<$ the degree of $g(x)$ 
### Remainder Theorem
If polynomial $P(x)$ is divide by $x-a$ the remainder will be $P(a)$. 
Using the [[Euclid's Division Lemma|Division Algorithm]] we get that $P(x)=Q(x)(x-a)+r$ plugging in $a$ we get $P(a)=Q(a)(a-a)+r=r \quad \square$.
### Factor Theorem
If $P(a)=0$ then $x-a$ is a factor of $P$. 
This trivially follows from the remainder theorem as $P(a)=o\implies r=0$ hence the factor theorem.
***
# Roots
## Reality of Roots
Given a polynomial with all real coefficients, it can any combination of complex or real roots as long as the complex roots come in complex conjugate pairs.
This means that given a polynomial $f$, $f(z)=0 \Leftrightarrow f(\bar{z})=0$
**Proof**
1. We will use the fact that conjugation is multiplicative and additive.
2. Let $f(z) = \sum a_{n}z^{n}$
3. Then $f(\bar{z})=\sum a_{n}(\bar{z})^{n}= \sum a_{n}\overline{z^{n}}=\sum\overline{a_{n}z^{n}}=\overline{\sum a_{n}z^{n}}=\bar{0}=0$ 

## Linear Transformations of Roots
Given a polynomial in terms of $x$ with roots $\alpha, \beta, \gamma$, you can find the polynomial in terms of $w$ with roots $(k\alpha + c)$, $(k\beta + c)$, $(k\gamma + c)$ by using the equation $w = kx + c$, then rearranging for $x$ and plugging into the original polynomial and expanding and simplifying.
## Vieta's Formulae
Given a polynomial $P(x)=a_nx^n+a_{n-1}x^{n-1}+\dots+a_{0}$ with roots $r_{1}, r_{2}, \dots,r_{n}$ then for any integer $1\leq k\leq n$, $$\sum_{1\leq i_{1}<i_{2}<\dots<i_{k}\leq n} \left(\prod_{j=1}^k r_{i_{j}}\right)=(-1)^k \frac{a_{n-k}}{a_{n}}$$
This is more easily written as $\displaystyle \text{sum of all products of k roots} = (-1)^n \frac{a_{n-k}}{a_{n}}$.
This can be simply proved directly by considering $a_{n}x^n+a_{n-1}x^{n-1}+\dots+a_{0}=a_{n}(x-r_{1})(x-r_{2})\cdots(x-r_{n})$ and expanding out $\text{RHS}$ and comparing coefficients of identical powers of $x$.
## Rational Roots Theorem
Suppose $P(x) \in \mathbb{Z}[x]$ has a rational zero $\displaystyle x=\frac{p}{q}, \ \gcd(p,q)=1$, then $p|a_{0}, \ q|a_{n}$.
**Proof**
Suppose $P(x) =a_{n}x^n+a_{n-1}x^{n-1}+\dots+a_{0}, \ a_{n} \in \mathbb{Z}, \ a_{n}\neq 0$ and $P(p / q)=0$ for some coprime $p, q \in \mathbb{Z}$.
1. $\displaystyle P\left(\frac{p}{q}\right)=a_n\left(\frac{p}{q}\right)^n+a_{n-1}\left(\frac{p}{q}\right)^{n-1}+\cdots+a_1\left(\frac{p}{q}\right)+a_0=0$ 
2. Multiply $q^n$ yielding $a_n p^n+a_{n-1} p^{n-1} q+\cdots+a_1 p q^{n-1}+a_0 q^n=0$
3. $p\left(a_n p^{n-1}+a_{n-1} q p^{n-2}+\cdots+a_1 q^{n-1}\right)=-a_0 q^n$
4. (*$p|0$ trivially holds so assume $p\neq 0$*) Thus, $p|a_0 q^n$. But $p$ is coprime to $q$ and therefore to $q^n$, so $p$ must divide the remaining factor $a_0$.
5. On the other hand, shifting the $a_n$ term to the right side and factoring out $q$ on the left side produces: $q\left(a_{n-1} p^{n-1}+a_{n-2} q p^{n-2}+\cdots+a_0 q^{n-1}\right)=-a_n p^n$
6. Reasoning as before, it follows that $q$ divides $a_n \quad \square$.
### Irrationality Criterion
*Any rational zero of a monic polynomial must be an integer, conversely any non-integer zero of a monic polynomial is irrational.*
**Proof**
Let $P(x)=x^n+a_{n-1}x^{n-1}+\dots+a_{0}$. If $\displaystyle P\left( \frac{p}{q} \right)=0$ then by [[Polynomials#Rational Roots Theorem|Rational Root Theorem]], $q|1$ therefore $\displaystyle \frac{p}{q}\in \mathbb{Z}\quad \square$


