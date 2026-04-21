---
tags:
  - maths/statistics
  - "#maths/probability"
---
*Links*: [[Single Continuous Random Variable]]
When we have multiple random variables we consider it as a [[Vectors|Vector]] in $\mathbb{R}^{n}$. E.g. $\mathbf{X} = (X_{1}, X_{2}, \dots, X_{n}) \in \mathbb{R}^{n}$. We can consider how individual variables in $\mathbf{X}$ are distributed by just consider $X_{i}$ as a [[Single Continuous Random Variable]].
But also many concepts generalise nicely to $n$ variables at once.

# Joint Probability Density Function
A ***Joint Probability Density Function*** is $$f_{\mathbf{X}}(\mathbf{X}): \mathbb{R}^{n} \to \mathbb{R}, \quad f_{\mathbf{X}}\geq0$$ Where $$\forall A\subset \mathbb{R}^{n},\ \mathbb{P}(\mathbf{X}\in A) = \int_{A}f_{\mathbf{X}}(\mathbf{x})d\mathbf{x}$$

## Marginal PDF
Given a joint PDF we can find a marginal PDF which is just a regular PDF of a subset of variables. For a subset of indices $I \subset\{1, 2, \dots, n\}$ we get $$f_{(X_{i})i\in I}(\mathbf{x_{I}}) = \int_{\mathbb{R}^{n-|I|}}f_{\mathbf{X}}(\mathbf{x})d\mathbf{x_{I^{c}}}$$
This is basically saying for any fixed $x_{I}$ to get the PDF is equal to summing the PDF of what all the other variables could possibly be. In short you fix $x_{I}$ and vary $x_{I^{c}}$.

## Independence
Variables $X_{1},X_{2},\dots ,X_{n}$ are **mutually independent** iff $$f_{\mathbf{X}}(\mathbf{x}) = \prod f_{X_{i}}(x)$$
Pairwise independence is not enough.

We can generalise this further to consider disjoint subsets of $\mathbf{X}$ that are independent of each other but may be dependant on other variables in that subset. 
Formally we get 
**Theorem**
Given a random vector $\mathbf{X}$ with probabilistic graphical model $G$. If we have $k$ disjoint subsets of $\mathbf{X}$, $\mathbf{Y}_{1},\mathbf{Y}_{2},\dots ,\mathbf{Y}_{k}$. That are independent of each other that is $\forall i,j,k,l, \ i\neq k, j\neq l$. There is no path in $G$ between $Y_{ij}$ and $Y_{kl}$. Then 
$$f_{(\mathbf{Y}_{1},\mathbf{Y}_{2},\dots ,\mathbf{Y}_{k})}(\mathbf{y}) = \prod f_{\mathbf{Y_{i}}}(\mathbf{y}_{i})$$
*Note*: a *probabilistic graphical model* $G$ just means a dependency graph where two nodes are connected if they are mathematically independent.

# Expected Value
$$\mathbb{E}[g(x)] = \int_{\mathbb{R}^{n}}g(\mathbf{x})f_{\mathbf{X}}(\mathbf{x})d\mathbf{x}$$

# Mean
$$\mu = \mathbb{E}[\mathbf{X}] = \begin{pmatrix}
\mathbb{E}[X_{1}]  \\
\vdots \\
\mathbb{E}[X_{n}]
\end{pmatrix}$$
# Covariance
For two random variables $X, Y$ $$\operatorname{Cov}(X, Y) = \mathbb{E}[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])] $$
1. $\operatorname{Cov}>0 \implies X$ above the mean, $Y$ is above.
2. $\operatorname{Cov} <0\implies X$ above the mean, $Y$ is below.
3. $\operatorname{Cov}\implies$ No *linear relationship*

*Note:* $\operatorname{Cov}=0$ does not mean independence.

**Lemma**
$$\operatorname{Cov}(X, X) = \operatorname{Var}(X) $$
*Proof:*
$\operatorname{Cov}(X, X) = \mathbb{E}[(X-\mathbb{E}[X])(X-\mathbb{E}[X])]= \mathbb{E}[(x-\mathbb{E}[x])^{2}] := \operatorname{Var(X)}$

## Covariance Matrix
For $n$ random variables we define a covariance [[Matrices|Matrix]] denoted $\Sigma$.
It is defined as $$\Sigma:=\mathbb{E}[(\mathbf{X}-\mathbb{E}[\mathbf{X}])(\mathbf{X}-\mathbb{E}[\mathbf{X}])^{\top}]$$
So we get that $$\Sigma_{ij}=\operatorname{Cov}(X_{i}, X_{j}) $$
We can using this compute the variance of a linear $a^{\top}\mathbf{X}$ with $\operatorname{Var}(a^{\top}\mathbf{X}) = a^{\top}\Sigma a$
# Correlation Matrix
$$R_{ij}=\frac{\Sigma_{ij}}{\sqrt{\Sigma_{ii}\Sigma_{jj}}}$$
# Linear Transforms
For $\mathbf{Y}=A\mathbf{X}+\mathbf{b}$ we have that $\mathbb{E}[\mathbf{Y}]= A\mathbf{\mu}+\mathbf{b}$ and $\operatorname{Cov}(\mathbf{Y})=A\Sigma A^{\top}$

# Conditionals and Bayes' Theorem
For two random vectors $\mathbf{X}, \mathbf{Y}$ we have $$f_{\mathbf{X| \mathbf{Y}}}(\mathbf{x}|\mathbf{y})=\frac{f_{\mathbf{X},\mathbf{Y}}(\mathbf{x}, \mathbf{y})}{f_{\mathbf{Y}}(\mathbf{y})}, \quad f_{\mathbf{Y}}(\mathbf{y}) >0$$
