# Definition
$$
X \sim \operatorname{Po}(\lambda) \quad P(X=x) = \frac{e^{-\lambda}\lambda^{x}}{x!} 
$$
Where $\lambda$ is the number of expected events over the interval. 
***
# Derivation
It is derived as the limit of a binomial distribution. Suppose we want to model something with an expected number of events lambda over some time interval, we could approximate this with a binomial by splitting the time interval into $n$ independent trials getting $X \sim B\left( n, \frac{\lambda}{n} \right)$ then we take $\displaystyle\lim_{ n \to \infty }$.

$$
\begin{aligned}

P(X=x) &= \lim_{ n \to \infty } \binom{n}{x}\left( \frac{\lambda}{n} \right)^{x}\left(1- \frac{\lambda}{n} \right)^{n-x} \\
&=\lim_{ n \to \infty } \frac{n!}{x!(n-x)!} \frac{\lambda^{x}}{n^{x}}\left( 1-\frac{\lambda}{n} \right)^{n}\left( 1-\frac{\lambda}{n} \right)^{-x} \\
&= \frac{\lambda^{x}}{x!} \cdot\lim_{ n \to \infty } \frac{n(n-1)\cdots(n-x+1)}{n^{x}} \left( 1-\frac{\lambda}{n} \right)^{n}\left( 1-\frac{\lambda}{n} \right)^{-x} \\
&=\frac{\lambda^{x}}{x!} \cdot\lim_{ n \to \infty } \left( 1-\frac{1}{n} \right)\left(1-\frac{2}{n}\right)\cdots \left( 1-\frac{x-1}{n} \right) \left( 1-\frac{\lambda}{n} \right)^{n}\left( 1-\frac{\lambda}{n} \right)^{-x} \\
&= \frac{\lambda^{x}}{x!} \cdot\lim_{ n \to \infty }  \left( 1-\frac{\lambda}{n} \right)^{n} \\
&= \frac{\lambda^{x}e^{-\lambda}}{x!}

\end{aligned}
$$
***
# Basic Properties
## Expectation
By definition the expectation is $\lambda$ but we can also prove it from the PMF.

$$

$$
