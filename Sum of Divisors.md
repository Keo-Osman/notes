---
tags:
  - maths/number-theory
---
# Definition
$\sigma(n)$ is defined as the sum of positive divisors of $n$, *including* $1$ and $n$.  This can be written as $$\forall n \in \mathbb{Z}^+ \quad\sigma(n) = \sum_{d|n} d$$
***
# Properties
**Theorem** $$\displaystyle\sigma(n) = \frac{p_1^{\alpha_1+1} - 1}{p_1 - 1} \cdots \frac{p_k^{\alpha_k+1} - 1}{p_k - 1} = \prod_{i=1}^k \frac{p_i^{\alpha_i+1} - 1}{p_i - 1}$$
*Proof:*
Let $n = p_1^{\alpha_1} \cdots p_k^{\alpha_k}$ then the divisors will have the form $d = p_1^{\beta_1} \cdot p_k^{\beta_k}$ $0 \leq \beta_i \leq \alpha_i$ $\forall i$. Every possible divisor appears exactly once so each combination of $k_i$ will appear exactly once which can be written as $(1 + p_1 + ... + p_1^{\alpha_1}) \cdot (1 + p_k + ... + p_k^{\alpha_k})$ which are geometric series, therefore $$\sigma(n) = \frac{p_1^{\alpha_1+1} - 1}{p_1 - 1} \cdots \frac{p_k^{\alpha_k+1} - 1}{p_k - 1} = \prod_{i=1}^k \frac{p_i^{\alpha_i+1} - 1}{p_i - 1}$$as required\.
***
**Theorem**
$\sigma(n)$ is [[Arithmetic Functions#Multiplicative Functions|Multiplicative]]\.

*Proof:*

Let $n = p_1^{\alpha_1} \cdot p_2^{\alpha_2}\cdots p_k^{\alpha_k}$. Every positive divisor $d = p_1^{\beta_1} \cdot p_2^{\beta_2} \cdots p_k^{\beta_k} \quad 0 \leq \beta_i \leq \alpha_i\ \forall i$.
Therefore, the sum of all positive divisors of $n$ is given by  $$\displaystyle\sigma(n) = \sum_{0 \leq \beta_1 \leq \alpha_1} \sum_{0 \leq \beta_2 \leq \alpha_2} \dots \sum_{0 \leq \beta_k \leq \alpha_k} p_1^{\beta_1} \cdot p_2^{\beta_2} \cdots p_k^{\beta_k}$$This multiple summation can be factored into a product of separate geometric series:  $$\displaystyle\sigma(n) = \left( \sum_{0 \leq \beta_1 \leq \alpha_1} p_1^{\beta_1} \right) \left( \sum_{0 \leq \beta_2 \leq \alpha_2} p_2^{\beta_2} \right) \cdots  \left( \sum_{0 \leq \beta_k \leq \alpha_k} p_k^{\beta_k} \right)$$Now suppose $a$ and $b$ are two positive integers with $\gcd(a, b) = 1$, and let  $\displaystyle a = \prod_{i=1}^r p_i^{\alpha_i}$ and $\displaystyle b = \prod_{j=1}^s q_j^{\gamma_j}$ where the $p_i$ and $q_j$ are distinct primes (since $a$ and $b$ are coprime). Then $\displaystyle ab = \prod_{i=1}^r p_i^{\alpha_i} \cdot \prod_{j=1}^s q_j^{\gamma_j}$, and using the previous identity for $\sigma(n)$, we get $$\displaystyle\sigma(ab) = \left( \prod_{i=1}^r \sum_{0 \leq \beta_i \leq \alpha_i} p_i^{\beta_i} \right) \left( \prod_{j=1}^s \sum_{0 \leq \delta_j \leq \gamma_j} q_j^{\delta_j} \right) = \sigma(a)\sigma(b)$$Therefore $\sigma$ is multiplicative\.