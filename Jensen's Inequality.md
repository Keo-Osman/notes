---
tags:
  - maths/algebra
online-links: https://brilliant.org/wiki/jensens-inequality
---
# Weighted Jensen's Inequality
Let $I$ be an interval on the reals $f:I\to \mathbb{R}$ be [[Concavity|Convex]] on $I$, with $x_{1},x_{2},\dots ,x_{n}\in I$ and real weights $w_{1},w_{2},\dots ,w_{n}> 0$ *(In many scenarios the weights will be normalised such that $\sum w_{i}=1$)*, Then $$\frac{w_{1}f(x_{1})+w_{2}f(x_{2})\dots +w_{n}f(x_{n})}{\sum w_{i}}\geq f\left( \frac{w_{1}x_{1}+w_{2}x_{2}+\dots+w_{n}x_{n}}{\sum w_{i}} \right)$$If $f$ is concave then the inequality is flipped.
The equality holds if $x_{1}=x_{2}=\dots =x_{n}$ or $f$ is affine on the on a domain containing $x_{i}$.


**Proof**
1. W.L.O.G let $\displaystyle \sum^n w_{i}=1$.
2. Trivially for $n=1\implies w_{1}=1$ so $f(x_{1})=f(x_{1})$ and the (in)equality holds.
3. The definition of convexity means $\forall x_{1},x_{2} \quad f(w_{1}x_{1}+w_{2}x_{2}) \leq w_{1}f(x_{1})+w_{2}f(x_{2})$. *This is the $n=2$ case.*
4. Assume that Jensen's holds for $n=k$, then for $n=k+1$ with weights $w_{i}$ *(arbitrary, not necessarily the same as the $n=k$ case)* such that $\displaystyle \sum^{k+1}w_{i}=1$. If $w_{k+1}=1$ then all other terms are zero so the inequality trivially holds. If $w_{k+1}=0$ it is equivalent to the induction hypothesis so assume $w_{n} \in (0,1)$
5. Let $\displaystyle \mu_{i}=\frac{w_{i}}{1-w_{k+1}}, i=1,2,\dots,k ,\ \sum_{i=1}^{k}\mu_{i}=\frac{1}{1-w_{k+1}}\sum_{i=1}^k w_{i}=\frac{1}{1-w_{k+1}}(1-w_{k+1})=1$ 
6. So we can rewrite $\displaystyle w_{1}x_{1}+\dots+w_{k+1}x_{k+1}=(1-w_{k+1})\sum_{i=1}^{k} \mu_{i}x_{i}+w_{k+1}x_{k+1}$
7. $\displaystyle f\left( \sum_{i=1}^{k+1} w_{i}x_{i} \right)=f\left((1-w_{k+1})\sum_{i=1}^{k} \mu_{i}x_{i}+w_{k+1}x_{k+1}\right)$
8. By convexity *(same as $n=2$ case)*, $\displaystyle \leq (1-w_{k+1})f\left(\sum_{i=1}^{k} \mu_{i}x_{i}\right)+w_{k+1}f(x_{k+1})$
9. By our inductive hypothesis $\displaystyle (1-w_{k+1})f\left(\sum_{i=1}^{k} \mu_{i}x_{i}\right) \leq (1-w_{k+1})\left(\sum_{i=1}^k \mu_{i}f(x_{i})\right)=\left(\sum_{i=1}^k (1-w_{k+1})\mu_{i}f(x_{i})\right)$
10. So we get that $\displaystyle (1-w_{k+1})f\left(\sum_{i=1}^{k} \mu_{i}x_{i}\right)+w_{k+1}f(x_{k+1}) \leq \left(\sum_{i=1}^k (1-w_{k+1})\mu_{i}f(x_{i})\right) +w_{k+1}f(x_{n})= \sum_{i=1}^{k+1}w_{i}f(x_{k+1}) \quad \square$
11. The exact same argument follows for concave functions but the inequality of the $n=2$ case flips $\quad \square$.


*Intuition*: The way this proof works is that we view the last point separately and the rest as *one* convex combination. We then renormalise with $\mu$ to insure the weights sum to $1$ (ensuring that the *one* point a convex combination) so we can apply the two-point Jensen that states that $f(\alpha U+(1-\alpha)V)\leq \alpha f(U)+(1-\alpha) \forall \alpha \in[0,1]$ and we've just used $\displaystyle U=\sum_{i=1}^k \mu_{i}x_{i}, V=x_{k+1}, \ \alpha=1-w_{k+1}$. And then invoke our induction hypothesis on $f(U)$. *($U$ acts as a shortcut for all input as it forms a new point which lies in the interval as $x_{min}\leq U \leq x_{max}$)*