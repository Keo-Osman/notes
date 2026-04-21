---
tags:
  - maths/calculus
---
# Definition
$f(x)$ is continuous at $\displaystyle a \Leftrightarrow \lim_{x \to a} f(x) = f(a)$

*This also implicitly requires that:*
1. $f(a)$ is defined
2. $\lim_{x \to a} f(x)$ exists

A function is continuous on an interval $\Leftrightarrow$ it is continuous at **every** number in that interval.
Continuity has **sidedness**. A function can be continuous from the left or right if the limit is one sided.
***
# Laws of Continuity
1. If $f$ and $g$ are continuous at $a$ then the following are continuous at $a$. $\displaystyle f\pm g,cf,f\cdot g, \frac{f}{g}$
2. $g$ is continuous at $a$  and $f$ is continuous at $g(a) \Rightarrow (f \circ g)(x)$ is continuous at $a$
3. $f$ is continuous at $b$ and $\displaystyle\lim_{x \to a} g(x) = b \Rightarrow \lim_{x \to a} f(g(x)) = b$
***
# Continuous Functions
[[Polynomials]], Rational, Root and [[Trigonometric Functions]] are all continuous for all numbers in their domain.
***
# Intermediate Value Theorem
$f$ is continuous on $[a,b]$ and $f(a) \neq f(b)$ 
$\Rightarrow\forall k \text{ s.t. }  \operatorname{min}\{f(a), f(b)\} < k < \operatorname{max}\{f(a), f(b)\} \quad\exists c \text{ s.t. } f(c) = k$

*Proof:*
$\text{ W.L.O.G } f(a) < f(b)$ as if $f(b) < f(a)$ we can consider the function $g(x) = f(b+a-x)$ then $g(a) = f(b), g(b) = f(a)$ so $g(a) < g(b)$ and if the theorem holds for $g$ meaning $g(y) = k$ then $g(y) = f(b+a-y)=k$ and $a \leq b+a - y \leq b$.
Define $S = \{x \in[a, b] | f(x) < k\}$ and $c = \operatorname{Sup}S$. We claim that $f(c) = k$.
Note that $S$ is not empty as $a \in S$ and since $b \not\in S$ we get that $a\leq c \leq b$.
Assume for contradiction that $f(c) \neq k$. Then we can split into 2 cases.

**Case 1** $f(c) > k \implies f(c) = k + \Delta, \Delta>0$
First note that by definition this means that $c \not\in S$. Since $c$ is a lower upper bound we have that $\forall \varepsilon>0, \exists d \in S \text{ s.t } c\geq d > c- \varepsilon$. But as $x \in S$ and $c \not\in S$ we have that $x \neq c$ so $c > d > c-\varepsilon$.
Then by continuity at $c$, $\forall \varepsilon>0 \exists \delta \text{ s.t } 0 < |x-c| < \delta \implies |f(x) - f(c)| < \varepsilon$.
Consider the case with $\varepsilon < \Delta$, we can pick a suitable $d \in S \text{ s.t } 0 < |d - c| < \delta$ with $f(d) = k - \Delta_{d}, \Delta_{d} > 0$ so by continuity we must have $|(k-\Delta_{d}) - (k + \Delta)| = \Delta + \Delta_{d} < \varepsilon \implies \Delta < \varepsilon$ a contradiction.

**Case 2** $f(c) < k \implies f(c) = k - \Delta, \Delta > 0$
We can't have $c = b$ as by our $\text{ W.L.O.G }$ we have said that $k < f(b)$ but $f(c) < k$.
So $\forall d > c, d \not\in S \implies f(d) > k$ so let $f(d) = k + \Delta_{d}, \Delta_{d}>0$. There exist infinitely many $c< d < b$ so we can make $|d-c|$ arbitrarily small.
By continuity at $c$, $\forall\varepsilon, \exists \delta \text{ s.t } 0 < |x-c| < \delta \implies |f(x) - f(c)| < \varepsilon$. Consider $\varepsilon < \Delta$, pick $d$ so that $|d-c| <\delta$ then we must have $|f(d) - f(c)| < \varepsilon\implies|k+\Delta_{d} - (k-\Delta)| = \delta + \Delta_{d} < \varepsilon \implies \Delta < \varepsilon$ a contradiction of $\varepsilon < \Delta$.

The only valid case left is $f(c) = k$\.

***
# Extreme Value Theorem
$f$ is continuous on $[a,b] \Rightarrow f$ attains a global maximum and minimum value on $[a, b]$