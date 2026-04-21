---
tags:
  - maths/number-theory
---
# Definition
A number base is a way of writing numbers. We use base $10$. A number in base $\ell$ we can write a number 
$$
n = \sum a_{k}\ell^{k}
$$
Where $k \in \mathbb{N}_{0}$, $\ell \in \mathbb{Z}_{\geq 2}$, $a_k\in \mathbb{N}_{0}, 0\leq a_{k} < \ell$. *It is possible to define bases with non-integer base but for now we only consider integers greater than $1$*\. 
# Properties
**Theorem**
In a base $\ell \in \mathbb{Z}^{+}$ any given integer $n$ has $\lceil \log_{\ell}n \rceil$ digits\.

*Proof:*
Let $n$ have $j+1$ digits, therefore $n=\sum_{0}^{j}a_{k}\ell^{k}$. Since $\log_{\ell}x$ is increasing, to obtain the max we require maximal $n$ therefore $n=\sum_{0}^{j}(\ell-1)l^{j}=\ell^{j+1}-1 \implies \log_{\ell}n=\log_{\ell}\ell^{j+1}<j+1$. For a minimum of $\log_{\ell}n$ we require $n=\ell^{j}\implies \log_{\ell}n\geq j$. So we have $j\leq \log_{\ell}n<j+1\implies j+1=\lceil \log_{\ell}n \rceil$\.

**Theorem**
A representation of $n$ base $\ell$ is unique\.

*Proof:*
Assume for the sake of contradiction that there exists two distinct representations of $n$ base $\ell$. Therefore $n=\sum_{0}^{A}a_{k}\ell^{k}=\sum_{0}^{B}b_{k}\ell^{k}$ and $\text{ W.L.O.G } A\geq B$. First we claim that $A=B$.
$$
\begin{aligned}


&n=\sum^{B}b_{k}\ell^{k}\leq \ell^{B+1}-1<\ell^{B+1} \\
&n=\sum^{A}a_{k}\ell^{k}\geq \ell^{A}\\
\implies &\ell^{A}<\ell^{B+1} \land A\geq B\implies A=B
\end{aligned}
$$
Next consider $n-n=0$. We get $\sum^{A}(a_{k}-b_{k})\ell^{k}=0$. Consider it $\operatorname{mod}\ell$. We get $0\equiv a_{k}-b_{k}\pmod{\ell}$. And since $|a_{k}-b_{k}|<\ell, a_{k}=b_{k}$. Then consider $\operatorname{mod}\ell^{2}$ then $\ell^{3}$ and so on and we find that every digit is identical therefore we get a contradiction so the representation is unique\.
