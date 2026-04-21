---
tags:
  - maths/number-theory
---
# Definition
Euler's totient function is defined as $$\varphi(n) = \text{the number of positive integers} \leq n, \text{ that are coprime to } n$$
***
# Properties
##### Theorem - Multiplicative
$\varphi(n)$ is [[Arithmetic Functions#Multiplicative Functions|Multiplicative Function]]

###### Proof
Consider $\varphi(mn)$. Then consider the set numbers $0<k< mn$. By [[Euclid's Division Lemma]] every such number can be written in the form $k = mr+c$ with $0 \leq r \leq n-1  ,\ 1 \leq a \leq m$. You can think of putting this in a grid with each $k$ being in row index $r$ and column index $c$. $\gcd(m, n) =1 \Rightarrow (\gcd(k, mn) =1 \Leftrightarrow \gcd(k, m)=1 \land \gcd(k, n)=1)$

Let $k_{{row}_i}$ be the subset of $k$ that has coefficient $i$ for $m$ e.g. $k=mi+c$. Each $k_{{row}_i}$ forms a complete residue class $\text{mod m}$ as $k_{{row}_i} \equiv \{1, 2,\dots, m\} = \{0, 1, 2,\dots, m-1\}$ so for each $k_{{row}_i}$ there are $\varphi(m)$ elements coprime to $m$. Then let $k_{{col}_i}$ be the subset of $k$ with remainder $i$ e.g. $k = mr +i$. Each $k_{{col}_i}$ forms a complete residue class $\text{mod n}$ as $k_{{col}_i} \equiv \{1, 2,\dots, n\} = \{0, 1, 2,\dots, n-1\}$ so for each $k_{{col}_i}$ there are $\varphi(n)$ elements coprime to $n$.

So the total amount that is coprime to $mn$ is $\varphi(m)\varphi(n)$ - *You can think this as starting in the top row there are $\varphi(m)$ elements that are coprime to $m$ and each of them form a column in which there are $\varphi(n)$ that are also coprime to $n$. Only the columns where the first element is coprime to $m$ work as any element that has a common factor $d$ with $m$ will form a column in which all those elements share that common factor with $m$.* (This is due to the [[Divisibility|fact]] that $\gcd(a\pm km, m) = \gcd(a, m)$)

##### Theorem - Computation_1
$$\varphi(p^k) = p^k-p^{k-1}$$
###### Proof
Every number $\leq p^k$ other than a multiple of $p$ is coprime to $p^k$. There are $p^{k-1}$ multiples of $p\leq p^k$ and there are $p^k$ numbers $\leq p^k$ so combing them we get $\varphi(p^k) =p^k-p^{k-1}$\.

##### Theorem - Computation_2
$$n = p_1^{\alpha_1}p_2^{\alpha_2}\cdots  p_k^{\alpha_k} \implies \varphi(n) = n\left(1-\frac{1}{p_1}\right)\cdots\left(1-\frac{1}{p_k}\right)$$
###### Proof
Using the previous theorem, $\displaystyle\varphi(p^k) = p^k-p^{k-1}=p^{k}\left(1-\frac{1}{p_k}\right)$
Since $\varphi$ is multiplicative and primes are pairwise coprime. $$\begin{aligned}\displaystyle \varphi(n) &= \varphi(p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_k^{\alpha_k}) \\ &=  \varphi(p_1^{\alpha_1})\cdot\varphi(p_2^{\alpha_2})\cdots\varphi(p_k^{\alpha_k})\\&=p_1^{\alpha_1}\left(1-\frac{1}{p_1}\right)\cdot p_2^{\alpha_2}\left(1-\frac{1}{p_2}\right)\cdots p_k^{\alpha_k}\left(1-\frac{1}{p_k}\right)\\&=p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_k^{\alpha_k}\left(1-\frac{1}{p_1}\right)\cdots\left(1-\frac{1}{p_k}\right)\end{aligned}$$


##### Theorem - Sum of Divisors
$$\displaystyle \sum_{d|n} \varphi(d) = n$$
###### Proof
Let $n = p_1^{\alpha_1} \cdot p_2^{\alpha_2}\cdots p_k^{\alpha_k}$. Every positive divisor $d = p_1^{\beta_1} \cdot p_2^{\beta_2} \cdots p_k^{\beta_k} \quad 0 \leq \beta_i \leq \alpha_i\ \forall i$ $$\displaystyle \sum_{d|n} \varphi(d) = \sum_{0 \leq \beta_1 \leq \alpha_1} \sum_{0 \leq \beta_2 \leq \alpha_2} \dots \sum_{0 \leq \beta_k \leq \alpha_k} \varphi(p_1^{\beta_1} \cdot p_2^{\beta_2} \cdots p_k^{\beta_k})$$
Using the fact that $\varphi(n)$ is multiplicate we get $\displaystyle \sum_{d|n} \varphi(d) = \sum_{0 \leq \beta_1 \leq \alpha_1} \sum_{0 \leq \beta_2 \leq \alpha_2} \dots \sum_{0 \leq \beta_k \leq \alpha_k} \varphi(p_1^{\beta_1}) \varphi(p_2^{\beta_2}) \cdots \varphi(p_k^{\beta_k})$. You can repeatedly factor out $\displaystyle\sum_{0\leq\beta_k\leq\alpha_k}\varphi(p_k^{\beta_k})$ from the summation with $0\leq\beta_{k-1}\leq\alpha_{k-1}$ as it is constant as you are changing all $\beta_k$ up to ***but not including*** $\beta_k$ so the summation is constant and can be factored out. This obtains $$\displaystyle \left(\sum_{0\leq\beta_1\leq\alpha_1} \varphi(p_1^{\beta_1}) \right)\cdots \left(\sum_{0\leq\beta_k\leq\alpha_k} \varphi(p_k^{\beta_k}) \right)$$ 
For each term we get $\varphi(1)+\varphi(p)+\varphi(p^2)+\cdots+\varphi(p^\alpha)$ which using $\varphi(p^k) = p^k-p^{k-1}$ gets a telescoping sum of $1+(p-1)+(p^2-p)+\cdots+(p^{\alpha}-p^{\alpha-1})=p^{\alpha}$. Replacing every sum we get $p_1^{\alpha_1} \cdot p_2^{\alpha_2}\cdots p_k^{\alpha_k} = n$\.

##### Theorem - Bounds
$\displaystyle\left(\frac{6}{\pi^2}\right)n^2 < \sigma(n)\varphi(n) < n^2$
###### Proof
INSERT PROOF