---
tags:
  - maths/algebra
---
# Definition
For sequences $\{a_{1_{1}},a_{1_{2}},\dots ,a_{1_{n}}\},\{a_{2_{1}},a_{2_{2}},\dots ,a_{2_{n}}\},\dots,\{a_{k_{1}},a_{k_{2}},\dots ,a_{k_{n}}\} \in \mathbb{R}_{\geq0}$ and weights $\lambda_{1},\lambda_{2},\dots ,\lambda_{k} \in \mathbb{R}_{\geq_{0}}\text{ s.t } \sum \lambda_{i}=1$, Holders states that $$\sum_{j=1}^{n}\prod_{i=1}^{k}a_{i_{j}}^{\lambda_{i}}\leq \prod_{i=1}^{k}\left( \sum_{j=1}^{n}a_{i_{j}} \right)^{\lambda_{i}}$$With the equality holding if and only if the sequences are proportional to each other


**Proof**
1. First note that $\forall j, \sum a_{j}=0\implies$ the inequality trivially holds. Therefore $\forall j, \ \sum a_{j}>0$.
2. Define a normalised sequence $\displaystyle b_{i_{j}}:=\frac{a_{i_{j}}}{A_{i}}\therefore\sum_{j=1} b_{i_{j}}=1, A_{i}=\sum_{j=1} a_{i_{j}}$
3. $\displaystyle\sum_{j=1}^{n}\prod_{i=1}^{k}a_{i_{j}}^{\lambda_{i}}=\sum_{j=1}^{n}\prod_{i=1}^{k}{A_{i}b_{i_{j}}}^{\lambda_{i}}=\left( \prod_{i=1}^{k}A_{i}^{\lambda_{i}} \right)\sum_{j=1}^{n}\prod_{i=1}^{k}b_{i_{j}}^{\lambda_{i}}=\left(\prod_{i=1}^{k}\left( \sum_{j=1}^{n}a_{i_{j}} \right)^{\lambda_{i}}\right)\sum_{j=1}^{n}\prod_{i=1}^{k}b_{i_{j}}^{\lambda_{i}}$
4. Thus it suffices to prove $\displaystyle\sum_{j=1}^{n}\prod_{i=1}^{k}b_{i_{j}}^{\lambda_{i}}\leq 1$
5. By [[Weighted Power Mean|Weighted AM-GM]] $\displaystyle\prod_{i=1}^{k}b_{i_{j}}\leq \sum_{i=1}^{k}\lambda_{i}b_{i_{j}}$
6. Summing over $j$ gives $\displaystyle\sum_{j=1}^{n}\prod_{i=1}^{k}b_{i_{j}}^{\lambda_{i}}\leq \sum_{j=1}^{n}\sum_{i=1}^{k}\lambda_{i}b_{i_{j}}=\sum_{i=1}^{k}\lambda_{i}\sum_{j=1}^{n}b_{i_{j}}=\sum_{i=1}^{k}\lambda_{i}\cdot 1=1$ as desired $\quad \square$ 
## Variants
### Cauchy-Schwarz
Using $k=2$ on Holders Inequality with $\lambda_{1}=\lambda_{2}=\frac{1}{2}$ then transformations $a_{i}\to a_{i}^{2}, \ b_{i}\to b_{i}^{2}$)$$\left( \sum a_{i}^{2} \right)\left( \sum b_{i}^{2} \right)\geq \left( \sum a_{i}b_{i} \right)^{2}$$
*Note that now we introduced the squares we have expanded the domain so now we get that* $a,b \in \mathbb{R}$


### $k=2$ Case
Using Holders with two sequences $a_{i},b_{i}$ and weights $\lambda_{1}=\frac{p}{p+q}, \lambda_{2}=\frac{q}{p+q}$ for $p,q\in \mathbb{R}^{+}$
Let $a_{1},a_{2},\dots ,a_{n} \in \mathbb{R}\geq_{0}$ and $b_{1},b_{2},\dots ,b_{n} \in \mathbb{R}_{\geq_{0}}$ and $p,q \in \mathbb{R}^{+}$, Then $$\displaystyle \left( \sum a_{i} \right)^{p}\left( \sum b_{i} \right)^{q}\geq\left( \sum (a_{i}^{p}b_{i}^{q})^{\frac{1}{p+q}} \right)^{p+q}$$With the equality only holding when the sequences are proportional to each other.

**Proof**
1. Plugging in conditions to Holders we get $\displaystyle \left( \sum a_{i} \right)^{\frac{p}{p+q}}\left( \sum b_{i} \right)^{\frac{q}{p+q}}\geq \left( \sum a^{\frac{p}{p+q}}b^{\frac{q}{p+q}} \right)$
2. Rearranging and raising both sides to the power of $p+q$ gets $\displaystyle \left( \sum a_{i} \right)^{p}\left( \sum b_{i} \right)^{q}\geq\left( \sum (a_{i}^{p}b_{i}^{q})^{\frac{1}{p+q}} \right)^{p+q}$ as desired $\quad \square$.

**Alternate Proof**
1. Since the inequality is homogeneous we can scale both $a_{i}$ and $b_{i}$ such that $\sum a_{i}=\sum b_{i}=1$
2. Then by **Weighted AM-GM** $\displaystyle \sum \sqrt[p+q]{a_{i}^{p}b_{i}^{q}} \leq \sum \frac{pa_{i}+qb_{i}}{p+q}=\frac{1}{p+q}\left( p\sum a_{i} +q\sum b_{i}\right)=1=\left( \sum a_{i} \right)^{p}\left( \sum b_{i} \right)^{q} \quad \square$

More concretely the scaling that is used is $a_{i}\to ta_{i} \text{ s.t }\sum ta_i=1$ and $b_{i}\to sb_{i} \text{ s.t } \sum sb_{i}$.
So we yield that $\displaystyle \left( \sum ta_{i} \right)^{p}\left( \sum sb_{i} \right)^{q}=t^{p}s^{q}\left( \sum a_{i} \right)^{p}\left( \sum b_{i} \right)^{q}$ and $\displaystyle \left( \sum ((ta_{i})^{p}(sb_{i})^{q})^{\frac{1}{p+q}} \right)^{p+q}=\left(t^{\frac{p}{p+q}}s^{\frac{q}{p+q}} \sum (a_{i}^{p}b_{i}^{q})^{\frac{1}{p+q}} \right)^{p+q}=t^{p}s^{q}\left( \sum (a_{i}^{p}b_{i}^{q})^{\frac{1}{p+q}} \right)^{p+q}$
So both sides scale by a positive factor of $t^{p}s^{q}$ so we can divide through and now we have $\sum a_{i}=\sum b_{i}=1$
### Classical Conjugate-Exponent Form
Using the $k=2$ case and making transformations $a_{i}\to a_{i}^{p}, \ b_{i}\to b_{i}^{q}$ and renaming exponents so that $\frac{p}{p+q}\to \frac{1}{p}, \ \frac{q}{p+q}\to \frac{1}{q}$ *(This adds the condition $p,q>1$)* we get $$\sum a_{i}b_{i}\leq \left( \sum a_{i}^{p} \right)^{1/p}\left( \sum b_{i}^{q} \right)^{1/q}$$


### Titu's Lemma
*Titu's Lemma* states that for $a_{1},a_{2},\dots ,a_{n}\in \mathbb{R}$ and $b_{1},b_{2},\dots ,b_{n}\in \mathbb{R}^{+}$ $$\frac{a_{1}^{2}}{b_{1}}+\frac{a_{2}^{2}}{b_{2}}+\dots+\frac{a_{n}^{2}}{b_{n}}\geq \frac{(a_{1}+a_{2}+\dots+a_{n})^{2}}{b_{1}+b_{2}\dots +b_{n}}$$

Note this is just *Cauchy-Schwarz* applied to the sequences $\displaystyle \left\{\frac{a_{n}}{\sqrt{b_{n}}}\right\}$ and $\{\sqrt{b_{n}}\}$ *hence the extra restrictions on $b_{i}\in \mathbb{R}^{+}$*. We can extend the domain to $a_{k} \in \mathbb{R}$ as if $a_{k}<0$ $RHS$ stays the same and $LHS$ will decrease or remain constant.
This is a very useful version for eliminating fractions.