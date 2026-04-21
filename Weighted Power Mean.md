---
tags:
  - maths/algebra
---
# Weighted F-Mean (Mean in an Arbitrary Function)
Given any function $f:I\to \mathbb{R}$ which is both [[Continuity|Continuous]] and [[Functions#Injective|Injective]] *(So that $f^{-1}$ is well defined)*, The *f-mean* of $x_{1},x_{2},\dots ,x_{n} \in I$ with weights $w_{1},w_{2},\dots ,w_{n} \in \mathbb{R}^{+}$ is defined as $$M_{f}(x_{1},x_{2},\dots ,x_{n})=f^{-1}\left( \frac{\sum w_{i}f(x_{i})}{\sum w_{i}} \right)$$
Since $f$ is both [[Continuity|Continuous]] and [[Functions#Injective|Injective]] it follows that $f$ is strictly *monotonic* so it follows that $x_{min} \leq \text{f-mean} \leq x_{max}$.


# Weighted Power Mean
The *weighted power mean* is the case of $f(x)=x^p$ and $I=\mathbb{R}^+$ of the *f-mean*.

**Proof**
1. $f(x)=x^p, \ f^{-1}(x)=x^{1/p}$
2. $\displaystyle M_{f}=f^{-1}\left(\frac{\sum w_{i}f(x_{i})}{\sum w_{i}} \right) =\left(\frac{\sum w_{i}x_{i}^{p}}{\sum w_{i}}\right)^{1/p} \quad \square$

Given $a_{1},a_{2},\dots ,a_{n} \in \mathbb{R}^+$ with weights $w_{1},w_{2},\dots ,w_{n} \in \mathbb{R}^{+}$ where$\text{ W.L.O.G, } \sum w_{i}=1$ and $p \in\mathbb{R}$, The weighted power mean is $$\displaystyle M_{p}(a_{1},a_{2},\dots,a_{n})=\begin{cases}
\displaystyle  \left( \sum w_{i}a_{i}^p \right)^{1/p} &p\neq 0 \\
\displaystyle  \prod a_{i}^{w_{i}} &p=0
\end{cases}$$
The weights $w_{i}$ serve to emphasises a certain element so if $a_{i}$ is more important then $w_{i}$ will be greater. In the case where $\displaystyle w_{1}=w_{2}=\dots =w_{n}=\frac{1}{n}$, we get an unweighted/regular version. 
Some special case for $p$ are: $p=-1\text{ :HM}, \ p=0\text{ :GM}, \ p=1\text{ :AM}, \ p=2\text{ :QM}$.
$a_{i}=0$ is valid for $p>0$.
## Weighted Geometric Mean 
The *weighted geometric mean* is the case of the *f-mean* where $I=\mathbb{R}^{+}$ and $f(x)=\ln(x)$

**Proof** 
1. $\displaystyle M_{f}=f^{-1}\left( \frac{\sum w_{i}f(x_{i})}{\sum w_{i}} \right)=e^{ \displaystyle\frac{\sum w_{i}\ln(x_{i})}{\sum w_{i}} }$
2. Using logarithm laws we get that $\displaystyle\frac{\sum w_{i}\ln(x_{i})}{\sum w_{i}}=\ln\left(\left( \prod x_{i}^{w_{i}}\right)^{\displaystyle\frac{1}{\sum w_{i}}}\right)$
3. So $\exp\left( \ln\left(\left( \prod x_{i}^{w_{i}}\right)^{\displaystyle\frac{1}{\sum w_{i}}}\right) \right)=\left(\displaystyle \prod x_{i}^{w_{i}}\right)^{\displaystyle\frac{1}{\sum w_{i}}}$
4. W.L.O.G we can assume that $\sum w_{i}=1$ to get a cleaner version and obtain $M_{f}=\displaystyle \prod x_{i}^{w_{i}} \quad \square$

It is also the $\displaystyle \lim_{ p \to 0 }$ of the *power mean* $\displaystyle \lim_{ p \to 0 } M_{p}(a_{1},a_{2},\dots,a_{n})=\prod a_{i}^{w_{i}}$
**Proof**
1. $\text{ W.L.O.G } \sum w_{i}=1$
2. $\displaystyle M_{p}=\left( \sum w_{i}x_{i}^{p} \right)^{1/p}$
3. $\displaystyle \ln M_{p}=\frac{\ln \left(\sum w_{i}x_{i}^{p}\right)}{p}$
4. $\displaystyle \ \lim_{ p \to 0 } \ln M_{p}=\frac{0}{0}$ indeterminate form we can use [[L'Hopitals Rule]]
5. $\displaystyle \lim_{ p \to 0 } \ \ln M_{p}=\frac{\frac{d}{dp} \ln \left(\sum w_{i}x_{i}^{p}\right)}{\frac{d}{dp}p}=\frac{d}{dp}\ln \left(\sum w_{i}x_{i}^{p}\right)=\frac{\sum w_{i}x_{i}^{p}\ln x_{i}}{\sum w_{i}x_{i}^{p}} \bigg|_{p=0}=\frac{\sum w_{i}\ln x_{i}}{\sum w_{i}}$
6. Therefore $\displaystyle \lim_{ p \to 0 } \ M_{p}=\exp\left( \displaystyle\frac{\sum w_{i}\ln x_{i}}{\sum w_{i}}\right)=\prod x_{i}^{w_{i}} \quad \square$
# Weighted Power Mean Inequality
$$q>p\implies M_{q}(a_{1},a_{2},\dots,a_{n})\geq M_{p}(a_{1},a_{2},\dots,a_{n})$$
The equality holds if and only if $a_{1}=a_{2}=\dots=a_{n}$.
For the cases of $p \in\{-1,0,1,2\}$ we get the inequality $\text{QM}\geq\text{AM}\geq\text{GM}\geq\text{HM}$. Again the equality only holding when all elements are equal.

**Proof**
1. $\text{ W.L.O.G }$let $q>p$. Define $f(t)=t^{q/p}$ then either:
	1. $q>p>0\implies \frac{p}{q}>1$
	2. $0>q>p\implies \frac{p}{q}>1$
	3. $q>0>p\implies \frac{p}{q}<0$
	4. All of which $\implies f$ is convex on $\mathbb{R}^{+}$.
2. Take our non-negative reals $x_{1},x_{2},\dots ,x_{n}\to x^{p}_{1},x^{p}_{2},\dots ,x^{p}_{n}$.
3. Then apply [[Jensen's Inequality]] Inequality (Also $\text{ W.L.O.G } \sum w_{i}=1$).
4. $\sum w_{i}f(x^{p}_{i})\geq f\left( \sum w_{i}x^{p}_{i}\right)\implies \sum w_{i}x_{i}^{q}\geq\left( \sum w_{i}x^{p}_{i} \right)^{q/p}$ 
5. Raising both sides to the power $\frac{1}{q}$ gives $\left( \sum w_{i}x^{q}_{i} \right)^{1/q}\geq\left( \sum w_{i} x^{p}_{i}\right)^{1/p}$ as desired.
6. We've already established that $M_{0}$ is the geometric mean. Since $M_{x}$ is continuous and monotonic we can take the limit of the inequality to complete it $\quad \square.$
# Young's Inequality
Let $p,q\in \mathbb{R}^{+}\text{ s.t } \frac{1}{p}+\frac{1}{q}=1$. Then if $a,b\in \mathbb{R}_{\geq0}$
$$
ab\leq \frac{a^{p}}{p}+\frac{b^{q}}{q}
$$
Where equality holds iff $a^{p}=b^{q}$

**Proof**
1. This is just the case of AM-GM with $a^{2},b^{2}$
