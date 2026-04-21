---
tags:
  - maths/number-theory
---
# Bezout's Identity
**Theorem** $$\forall m,n \in \mathbb{Z}, \exists x,y \in \mathbb{Z} \text{ s.t }\gcd(m,n) = mx+ny$$
*Proof:*
First, consider the set of $S = \{mx+ny \ | \ x, y \in \mathbb{Z}, \ mx+ny>0\}$. Since $S$ consists of non-negative integers there exists a minimal element $d$. So $d=mx_0+ny_0$. Then by the division algorithm $m = qd+r$, $0\leq r < d \Rightarrow r = m - qd = m - q(mx_0+ny_0)=m(1-qx_0)+b(-qy_0)$. This means that $r$ is a linear combination of $m, n$. If $0<r<d$ then $r \in S$ but this contradicts the minimality of $d$ so $r=0$. Hence $d|m$. The same argument can be made to show that $d|n$ meaning $d|\gcd(m,n)=g$. Since $g|m$ and $g|n$, $g|mx_0+ny_0=d$ so we get $d|g$ and $g|d$ so $d=\gcd(m,n)$

*Remark*
This also proves that $|mx +ny| \geq \gcd(m,n)$ as $d$ was the minimal element.

You can figure out $x$ and $y$ by going through the Euclidean Algorithm backwards and collecting like terms.
Two integers $a$, $b$ are coprime if $\gcd(m,n) = 1$ so by Bezout's Identity $\exists x,y \in \mathbb{Z}$ *s.t* $mx + ny = 1$