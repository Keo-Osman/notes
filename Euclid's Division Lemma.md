---
tags:
  - maths/number-theory
---
# Euclid's Division Lemma
**Theorem** $$\forall a,b \in \mathbb{Z}, \ \exists q, r \in \mathbb{Z} \ \text{ s.t } \ a=bq+r, \ 0\leq r \leq b $$
*Proof:*
TODO

***
# Euclid's Division Algorithm
By repeatedly apply property 8: $a = bq + r \Rightarrow \gcd(a,b) = \gcd(b,r)$. You can find the $\gcd$ of any 2 numbers easily

8. $a = bq + r \Rightarrow \gcd(a,b) = \gcd(b,r)$
	1. $\gcd(a, b) = \gcd (bq+r, b)$
	2. By property 7, $\gcd (bq+r, b)= \gcd(bq+r-q(b), b) = \gcd(a, b)$