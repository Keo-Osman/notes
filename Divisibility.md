---
tags:
  - maths/number-theory
---
# Definition
Given $a,b \in \mathbb{Z}$. We say $a$ *divides* $b$ (denoted $a|b$) *iff* $\exists k \in \mathbb{Z}\text{ s.t }b=ka$.
# Basic Divisibility Properties
**Theorem**
Let $x, y, z \in \mathbb{Z}$ 
1. $x|x$ *(reflexive property)* 
2. $x|y$ and $y|z \Rightarrow x|z$ *(transitivity property)* 
3. $x|y$ and $y≠0 \Rightarrow |x| \leq |y|$ 
4. $x|y$ and $x|z \Rightarrow x|ay+bz$ $\forall a,b \in \mathbb{Z}$ 
5. $x|y$ and $x|(y+z) \Rightarrow x|z$ 
6. $x|y$ and $y|x \Rightarrow |x|=|y|$
7. $x|y$ and $y≠0 \Rightarrow \displaystyle\frac{y}{x}|y$
8. $(z≠0)$ and $x|y \Leftrightarrow xz|yz$ 

**Theorem** $$p|\binom{p}{k} \quad (0<k<p)$$
*Proof:*
$$\binom{p}{k} = \frac{p!}{k!(p-k!)}=\frac{p(p-1)(p-2)\cdots(p-k+1)}{k!}$$
Hence $k!|p(p-1)(p-2)\cdots(p-k+1)$. Since $\gcd(p, k!) = 1$ as none of $k, k-1, \dots 1$ share any factors with $p$ as $k<p$. Using this we get $k!|(p-1)(p-2)\cdots(p-k+1)$ so $\frac{(p-1)(p-2)\cdots(p-k+1)}{k!}=S\in \mathbb{Z}\implies \binom{p}{k} = pS$ Hence $p|\binom{p}{k}$\.