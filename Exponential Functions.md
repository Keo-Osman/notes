---
tags:
  - maths/algebra
---
# Definition
An exponential function is defined as $f(x) = a^x$
In general if $x \in \mathbb{Z}^+$ $f(x) = \underbrace{a \cdot a \cdots a}_{n \text{ times}}$
$$x \in \mathbb{Z}^- \Rightarrow f(-x) = \frac{1}{f(x)} = \frac{1}{a^{x}}$$
$$x \in \mathbb{Q} \Rightarrow f(x) = a^x = a^{\textstyle \frac{p}{q}} = \sqrt[q]{a^p} = (\sqrt[q]{a})^p$$

To Extend to *The Real Numbers* you take any series $r_n$ where $\forall n$ $r_n \in \mathbb{Q}$ and that converges to $x \in \mathbb{R}$ then $f(x) = \displaystyle\lim_{n \to \infty} a^{\textstyle r_n}$ since by definition $r_n$ converges the limit converges and therefore $f(x)$ exists and thus $f$ has domain $\mathbb{R}$

# [[Epsilon-Delta Definition of a Limit|Limits]]
$a > 1 \Rightarrow \lim_{x \to \infty} a^x = \infty$, $\lim_{x \to -\infty} a^x = 0$
$a = 1 \Rightarrow \lim_{x \to \infty} a^x = 1$ $\lim_{x \to -\infty} a^x = 1$
$0 < a < 1 \Rightarrow \lim_{x \to \infty} a^x = 0$ $\lim_{x \to -\infty} a^x = \infty$