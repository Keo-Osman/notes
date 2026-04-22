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
By definition $\mathbb{E}[X] = \lambda$ but we can also prove it from the PMF.

$$
\begin{aligned}
\mathbb{E}[X] &= \sum xP(x=x) \\
&= \sum_{x=0}^{\infty}x\cdot \frac{\lambda^{x}e^{-\lambda}}{x} \\
&= \lambda e^{-\lambda} \sum_{x=1}^{\infty} \frac{\lambda^{x-1}}{(x-1)!} \\
&= \lambda e^{ -\lambda } e^{\lambda} \\
&= \lambda
\end{aligned}
$$
## Variance
The Poisson also has variance $\lambda$ which we can prove directly.

$$
\begin{aligned}
\mathbb{E}[X^{2}] &= \sum_{x=0}^{\infty}x^{2}P(X=x) \\
&= \sum_{x=0}^{\infty} x^{2} \frac{e^{ -\lambda }\lambda^{x}}{x!} \\
&= \lambda e^{ -\lambda }\sum_{x=1}^{\infty}x \cdot \frac{\lambda^{x-1}}{(x-1)!} \\
&= \lambda e^{ -\lambda }\sum_{y=0}^{\infty}(y+1) \cdot \frac{\lambda^{y}}{y!} \\
&= \lambda e^{ -\lambda }\left[\sum_{y=0}^{\infty}y \cdot \frac{\lambda^{y}}{y!} + \sum_{y=0}^{\infty} \frac{\lambda^{y}}{y!}\right] \\ 
&= \lambda e^{ -\lambda }\left[\lambda \sum_{z=0}^{\infty} \cdot \frac{\lambda^{z}}{z!} +  e^{ \lambda }\right] \\ 
&= \lambda e^{ -\lambda }\left[\lambda e^{ \lambda } + e^{ \lambda } \right] \\
&= \lambda^{2}+\lambda \\
\\
\operatorname{Var}(X) &= \mathbb{E}[X^{2}] - \mathbb{E}[X]^{2} \\
&= \lambda^{2}+\lambda - \lambda^{2} \\
&= \lambda
\end{aligned}

$$

***
# Advanced Properties
#### Theorem - Addition of Poisson

$$
X \sim \operatorname{Po}(\lambda_{1}), \  Y \sim \operatorname{Po}(\lambda_{2}) \implies (X+Y) \sim \operatorname{Po}(\lambda_{1}+\lambda_{2})  
$$
##### Proof
$$
\begin{aligned}
P(X+Y = k) &= \sum_{i=0}^{k}P(X=i)P(Y=k-i) \\
&= \sum_{i=0}^{k} \frac{e^{ -\lambda_{1} }\lambda_{1}^{i}}{i!} \cdot \frac{e^{ -\lambda_{2} }\lambda_{2}^{k-i}}{(k-i)!} \\
&= \frac{e^{ -(\lambda_{1}+\lambda_{2}) }}{k!}\sum_{i=0}^{k} \frac{k!}{i!(k-i!)} \lambda_{1}^{i}\lambda_{2}^{k-i} \\
&= \frac{e^{ -(\lambda_{1}+\lambda_{2}) }}{k!}(\lambda_{1}+\lambda_{2})^{k}
\end{aligned}
$$
