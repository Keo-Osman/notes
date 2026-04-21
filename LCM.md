---
tags:
  - maths/number-theory
---
# Definition
Given $a, b \in \mathbb{Z}$, $\operatorname{lcm}(a,b) = m$ is defined as the least *positive* integer such that $m=ka=nb$ where $k, n \in \mathbb{Z}$\.
*Remark*
You can have $\operatorname{lcm}$ of negative numbers *(one or both)* but the $\operatorname{lcm}$ is always strictly positive\.

**Theorem**
1. $\operatorname{lcm}(s,t) = m$, $m \cdot s' = t'$ $\Rightarrow gcd(s',t') = 1$
2. If $m'$ is common multiple of $s$ and $t$ and $m' \cdot s' = t'$, $gcd(s',t') = 1$
3.  $m'$ is a common multiple of $s$ and $t$ $\Rightarrow m | m'$
4. $m | s$, $n | s$ $\Rightarrow \operatorname{lcm}(m,n) | s$
5. $n \in \mathbb{Z}$ $\Rightarrow n \cdot \operatorname{lcm}(s,t) = \operatorname{lcm}(ns, nt)$
6. $s = p_1^{\alpha_1} \cdots p_k^{\alpha_k}$, $t = p_1^{\alpha_1} \cdots p_k^{\alpha_k}$ $\Rightarrow \operatorname{lcm}(s,t) = p_1^{\textstyle\max(\alpha_1,\beta_1)} \cdots p_k^{\textstyle\max(\alpha_k,\beta_k)}$
7. $mn = \operatorname{gcd}(m,n) \cdot \operatorname{lcm}(m,n)$ $\forall m,n \in \mathbb{Z}$

