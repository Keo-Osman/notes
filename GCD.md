---
tags:
  - maths/number-theory
---
# Definition
Given $a,b \in \mathbb{Z}, \ \gcd(a,b) = d$ is defined as the greatest integer $d \text{ s.t } d|a$ and $d|b$ 
# Properties
**Theorem**
1. $p$ is prime $\Rightarrow \gcd(p,m) = p$ or $\gcd(p,m) = 1$ 
2. If $d = \gcd(m,n)$, $m = d \cdot m'$, $n = d \cdot n' \Rightarrow \gcd(m',n') = 1$ 
3. $d = \gcd(m,n)$, $m = d' \cdot m''$, $n = d' \cdot n''$, $\gcd(m'',n'') = 1 \Rightarrow d' = d$
4. If $d$ is a common divisor of $m, n \Rightarrow d|\gcd(m,n)$
5. $p^k||m$ and $p^j||n \Rightarrow p^{\min(k,j)}||\gcd(m,n)$ 
6. $m = p_1^{\alpha_1} \cdots p_r^{\alpha_r}$, $n = p_1^{\beta_1} \cdots p_r^{\beta_r}$, $\alpha_i, \beta_i \geq 0 \Rightarrow \gcd(m,n) = p_1^{\min(\alpha_1,\beta_1)} \cdots p_r^{\min(\alpha_r,\beta_r)}$ 
7. $a|bc$ and $\gcd(a,b) = 1 \Rightarrow a|c$ 
8. $\gcd(a,b) = 1$ and $a|c$ and $b|c \Rightarrow ab|c$ 

**Theorem** $$\gcd(a^m-1, a^n-1)=a^{\gcd(m,n)}-1$$
*Proof:*
TODO

**Theorem** $$\gcd(a \pm kb, b) = \gcd(a, b)$$
*Proof:*
Let $\gcd(a, b) = d, \ \gcd(a \pm kb, b) = d'$. By definition $d'|b$ and $d'|a \pm kb \Rightarrow d'|a$. So $d'$ has to be a common divisor of $a$ and $b$. And $d$, by definition, is the greatest number that satisfies that. Therefore $\gcd(a \pm kb, b) = \gcd(a, b)$\.

This theorem is very common and useful and is used in [[Euclid's Division Lemma]].

**Theorem** $$\gcd(ab, n) = \gcd(a, n)\gcd\left( b, \frac{n}{\gcd(a,n)} \right)$$
This is very useful and is effectively dividing out the $b$ in the $\gcd$. A very common case of this theorem is when $\gcd(b,n) = 1$ then it simplifies to $\gcd(ab,n)=\gcd(a,n)$.
The intuition is that we first consider *"What primes $a$ contributes to the $\gcd$"*. Then $b$ can only *"contribute"* from what is left being $\displaystyle\frac{n}{\gcd(a,n)}$.

*Proof:*
We will go prime by prime. Fix a prime $p$. Then let $p^{\alpha}||n,\ p^{x}||a,\ p^{y}||b$. The power of $p$ in $\gcd(ab, n)$ is $\min(x+y, \alpha)$. We can make this power of $p$ with $\min(x, \alpha)+\min(y, \alpha-\min(x, \alpha))$. So we get $p^{\min(x, \alpha)}\cdot p^{\min(y, \alpha-\min(x, \alpha))} = \gcd(a,n)\gcd\left( b, \frac{n}{\gcd(a, n)} \right)$\.

*Proof:*
Let $d = \gcd(a, n)$ then $a = da',\ n = dn'$ with $\gcd(a', n') =1$. Then $$\gcd(ab,n) = \gcd(da'b, dn')=d\gcd(a'b, n')$$Then let $g=\gcd(a'b, n')\implies g|a'b, \ g|n'$ and with $\gcd(a', n')=1$ we must have $g|b$ hence $g=\gcd(b,n')$. Substituting that in and writing $n'$ as $\displaystyle\frac{n}{\gcd(a,n)}$ we get $\displaystyle\gcd(ab, n) = \gcd(a, n)\gcd\left( b, \frac{n}{\gcd(a,n)} \right)$ as required\.