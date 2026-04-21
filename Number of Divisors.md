---
tags:
  - maths/number-theory
---
# Definition
$\tau(n)$ is defined as the number of *positive* divisors of $n$, including $1$ and $n$. 
# Properties
**Theorem**
Given $n = p_1^{\alpha_1} \cdots p_r^{\alpha_k}$ the $\tau(n) =\displaystyle\sum_{d|n}1 = (\alpha_1+1)(\alpha_2+1) \cdots (\alpha_k+1)$\.

*Proof:*
Any divisor must be in the form $p_1^{\beta_1} \cdots p_k^{\beta_k}$ with $0 \leq \beta_k \leq \alpha_k$ $\forall k$. So for each $k$ there are $\alpha_k+1$ choices for $k_k$. Since they are independent you multiply\.
***
**Theorem**
$n = p_1^{\alpha_1} \cdots p_k^{\alpha_k}$ $\Rightarrow$ there are $(2\alpha_1+1)(2\alpha_2+1) \cdots (2\alpha_k+1)$ distinct ordered pairs $(a,b) \in \mathbb{Z}^+$ such that $\operatorname{lcm}(a,b) = n$\.

*Proof:*
Given that $a, b$ are divisors of $n$, they must have the form $a = p_1^{\beta_1} \cdots p_k^{\beta_k}$ and $p_1^{\gamma_1} \cdots p_k^{\gamma_k}$ since $$
\operatorname{\operatorname{lcm}}(a,b) =  p_1^{\textstyle\max(\beta_1,\gamma_1)} \cdots p_k^{\textstyle\max(\beta_k,\gamma_k)}
$$There are $2\alpha_1+1$ options for each $(\beta_k,\gamma_k)$: $$\underbrace{(0,\alpha_k), (1,\alpha_k),...,}_{\alpha \text{ terms}} (\alpha_k,\alpha_k)\underbrace{,...,(\alpha_k,0)}_{\alpha \text{ terms}}$$ So you multiply number of choices together\.
***
**Theorem** $$\forall n \in \mathbb{Z}^+,\ \displaystyle\prod_{d|n} d = n^{\textstyle\frac{\tau(n)}{2}}$$

*Proof:*
**Case 1** $n=a^2$
You can split the divisors into $\textstyle\frac{\tau(n)}{2}-1$ pairs $(d, \textstyle\frac{n}{d})$ so their product is $n$ multiplying all together you get $n^{\textstyle\frac{\tau(n)-1}{2}}$ Then multiply by $\sqrt{n}$ yielding $n^{\textstyle\frac{\tau(n)}{ 2}}$

**Case 2** $n\neq a^2$
You can split the divisors into $\textstyle\frac{\tau(n)}{2}$ pairs $(d, \textstyle\frac{n}{d})$ so their product is $n$ multiplying all together you get $n^{\textstyle\frac{\tau(n)}{2}}$\.
***
**Theorem** $$\forall n \in \mathbb{Z}^+,\ \tau(n) \leq 2\sqrt{n}$$

*Proof:*
Let $d_1, d_2, ..., d_k$ be the divisors of $n \leq \sqrt{n}$. The rest of the divisors are $\frac{n}{d_1}, \frac{n}{d_2}, ..., \frac{n}{d_k}$. In each set there are $k$ numbers so $\tau(n) = 2k$ (or $2k-1$ if $n$ is a perfect square) Since $d_i$ are distinct positive integers $\leq \sqrt{n}$ there can be at most $\lfloor\sqrt{n}\rfloor$ so $k \leq \sqrt{n}$ $\Rightarrow$ $\tau(n) \leq 2k \leq 2\sqrt{n}$\.
***
**Theorem**
$\tau(n)$ is odd $\Leftrightarrow n=k^2$\.

*Proof:*
Using $\tau(n) = (\alpha_1+1)(\alpha_2+1) \cdots (\alpha_k+1)$ we can deduce that $\tau(n) \text{ is odd } \Leftrightarrow \alpha_n \text { is even } \forall n$ therefore $n$ is square\. 
***
**Theorem**
$\tau(n)$ is [[Arithmetic Functions#Multiplicative Functions|Multiplicative]]\.

*Proof:*
Let $a =p_1^{\alpha_1} \cdots p_k^{\alpha_k}$ and $b=P_1^{\beta_1} \cdots P_r^{\beta_r}$ with $\gcd(a,b) = 1$. Meaning they share no prime factors. $\tau(a) = (1+\alpha_1)\cdots (1+\alpha_k)$ and $\tau(b) = (1+\beta_1) \cdots (1+\beta_r)$ therefore $ab = p_1^{\alpha_1} \cdots p_k^{\alpha_k} P_1^{\beta_1} \cdots P_r^{\beta_r}$. Since they share no prime factors $P_i \neq p_j  \ \forall i, j$ so there is no crossover in primes and this is the proper prime factorisation. 
$$\tau(a)\tau(b)=\tau(ab)=(1+\alpha_1)\cdots (1+\alpha_k)(1+\beta_1) \cdots (1+\beta_r)$$
*(If $a, b$ weren't coprime they would share factors and this would not be the proper prime factorisation: you could get $p_i^{\alpha_i +\beta_j}$ terms. This means that $\tau$ is not completely multiplicative)*\. 