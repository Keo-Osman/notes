---
tags:
  - maths/statistics
  - maths/probability
---
# Definition
A continuous random variable is a random variable $X$ which can take any real value in an interval. For continuous random variables $\mathbb{P}(X=x) = 0 , \forall x \in \mathbb{R}$. Instead probabilities are defined over an interval e.g. for $a<b \in \mathbb{R}$ we consider $\mathbb{P}(a\leq x\leq b)$.

# PDF (Probability Density Function)
In order to do this we have a ***probability density*** [[Functions|Function]] $f_{X}(x)$ which satisfies
1. $f_{X}(x) \geq 0$
2. $\int_{a}^{b}f_{X}(x)dx = \mathbb{P}(a\leq x \leq b)$
3. $\int_{-\infty}^{\infty}f_{X}(x)dx = \mathbb{P}(-\infty\leq x \leq \infty) = 1$ *as total probability sums to $1$*
# CDF (Cumulative Density Function)
A ***Cumulative Density Function*** $F_{X}(x)$ is defined as $$F_{X}(x) = \mathbb{P}(X \leq x) = \int_{-\infty}^{x}f_{X}(t)dt$$
It has the properties that 
1. $F_{X}$ is non-decreasing
2. $\lim_{ x \to -\infty }F_{X}(x) = 0$
3. $\lim_{ x \to \infty }F_{X}(x) = 1$
4. If $F_{X}$ is [[Derivatives|Differentiable]] then $\frac{d}{dx}F_{X}(x) = f_{X}(x)$

# Expected Value
The ***Expected Value*** denoted $\mathbb{E}[X]$ of $X$ is the mean value of $X$.
It is defined/found as $$\int_{-\infty}^{\infty}xf_{X}(x)dx$$
This comes from a generalisation of the discrete case $\mathbb{E}[X] = \sum x\mathbb{P}(X=x)$.
We can also compute the expected value of any function $$\mathbb{E}[g(X)] = \int_{-\infty}^{\infty}g(x)f_{X}(x)dx$$
Also note that since $\mathbb{E}[X]$ is an [[Integration|Integral]] it is *linear*
# Variance and Standard Deviation
***Variance*** is defined as $$\operatorname{Var}(X):=\mathbb{E}[(X-\mathbb{E}[X])^{2}]=\mathbb{E}[X^{2}]-(\mathbb{E}[X])^{2}$$
Since $\mathbb{E}[X]$ is the mean, $X-\mathbb{E}[X]$ is the deviation of $X$ from the mean. So variance is the *mean squared distance of $X$ from the mean*. It is a measure of **Spread** of the variable/data.

It has the properties that:
1. $\operatorname{Var}(X)\geq0, \operatorname{Var}(X) = 0 \iff X=c$.
2. Weight larger deviations more than small ones. *Hence the squaring.*

We then define standard deviation as $$\sigma = \sqrt{\operatorname{Var(X)} }$$
To go from squared distance to distance to get spread in the original units. *However it is **NOT** quite the average distance*. But we use it over $\mathbb{E}[\ |X-\mathbb{E}[X]| \ ]$ as the standard deviation has some nicer properties.