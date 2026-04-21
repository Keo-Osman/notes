---
tags:
  - maths/number-theory
---
# Definition
## Floor
The *floor function* also called the *greatest integer function* is defined as $f \left \lfloor{x} \right \rfloor :  \mathbb{R} \rightarrow \mathbb{Z}$, it is the greatest integer $n$ such that $n \leq x <n+1$.
## Fractional Part
The *fractional part* of $x$ denoted by $\{x\}=x-\left \lfloor{x} \right \rfloor$ For positive $x$ this is simply the decimal part but for negative integers it's the the $1 -$ fractional part. E.g. $\{-2.4\}=0.6$.
## Ceiling
The *ceiling function* gives the integer larger than $x$. It's is defined as $f \left \lceil{x} \right \rceil : \mathbb{R} \rightarrow \mathbb{Z}$
***
# Properties
**Theorem**
Let $x \in \mathbb{R}$ and $n \in \mathbb{Z}$.
1. $x-1<\left \lfloor{x} \right \rfloor \leq x$
2. $x \leq \left \lceil{x} \right \rceil < x+1$
3. $0\leq \{x\}<1$
4. $\left \lfloor{x+n} \right \rfloor=n+\left \lfloor{x} \right \rfloor$
5. $\left \lceil{x+n} \right \rceil=n+\left \lceil{x} \right \rceil$
6. $\{x+n\}=\{x\}$
7. $n\leq x \Rightarrow n \leq \left \lfloor{x} \right \rfloor, n \in \mathbb{N}, x \in \mathbb{R}$
***
# Hermite's Identity
**Theorem** $$\displaystyle x \in \mathbb{R}, \ m \in \mathbb{N} \implies \sum_{i=0}^{m-1} \left\lfloor  x+\frac{i}{m}  \right\rfloor=\lfloor x \rfloor+\left\lfloor  x+\frac{1}{m}  \right\rfloor+\dots + \left\lfloor  x+\frac{m-1}{m}  \right\rfloor=\lfloor mx \rfloor$$
*Proof:*
The key fact is that $$\displaystyle\lfloor x\rfloor \leq \left\lfloor  x+\frac{1}{n}  \right\rfloor \leq \cdots \leq \left\lfloor  x+\frac{n-1}{n}  \right\rfloor =\left\lfloor  \lfloor x \rfloor+\{x\}+1-\frac{1}{n}  \right\rfloor=\lfloor  x\rfloor+1+\left\lfloor  \{x\}-\frac{1}{n}  \right\rfloor \leq \lfloor x \rfloor+1$$
Therefore $\displaystyle\exists i \text{ s.t } \left\lfloor  x+\frac{i-1}{n}  \right\rfloor=\lfloor x \rfloor$ and $\displaystyle\left\lfloor  x+\frac{i}{n}  \right\rfloor=\lfloor x \rfloor+1$. So $\displaystyle\sum_{i=0}^{m-1} \left\lfloor  x+\frac{i}{m}  \right\rfloor=i\lfloor x \rfloor+(n-i)(\lfloor x \rfloor+1)$.

Note that $\displaystyle\{x\}+\frac{i-1}{n}<1$ and $\displaystyle\{x\}+\frac{i}{n}\geq1$, together this gives $\displaystyle \frac{n-i}{n} \leq\{x\} < \frac{n-i+1}{n}$. Using this we get that $n\lfloor x \rfloor+n-i\leq n\lfloor x \rfloor+n\{x\}=nx<n\lfloor x \rfloor+n-i+1 \implies \lfloor nx \rfloor=n\lfloor x \rfloor+n-i$. Using this we get $\displaystyle\sum_{i=0}^{m-1} \left\lfloor  x+\frac{i}{m}  \right\rfloor=i\lfloor x \rfloor+(n-i)(\lfloor x \rfloor+1) =n\lfloor x \rfloor+n-i=\lfloor nx \rfloor$.

**Proof 2**
INSERT PROOF

***
# Floor Function of Rational Numbers
**Theorem**
Let $p, q \in \mathbb{Z}, q \neq 0$ and $r$ be the remainder when $p$ is divided by $q$ then. $\displaystyle \left\lfloor  {\frac{p}{q}} \right \rfloor =\frac{p-r}{q}$\. 

*Proof:*
This follows from [[Euclid's Division Lemma]] with $\displaystyle p=q \left\lfloor  \frac{p}{q}  \right\rfloor+r$. 
***
# Floor Function and Divisors
## Properties
1. The number of multiples of $d$ which are $\displaystyle \leq n=\left\lfloor  \frac{n}{d}  \right\rfloor \ n,d \in \mathbb{N}$
2. $\displaystyle\left\lfloor  \frac{n}{k}  \right\rfloor-\left\lfloor  \frac{n-1}{k}  \right\rfloor = \begin{cases} 1, &k|n\\0, & k \nmid n \end{cases}$  
3. $\displaystyle\sum_{k=1}^n\tau(k)=\sum_{k=1}^n \left\lfloor  \frac{n}{k}  \right\rfloor$ *[[Number of Divisors]]*
4. $\displaystyle\sum_{k=1}^n\sigma(k)=\sum_{k=1}^n k\left\lfloor  \frac{n}{k}  \right\rfloor$ *[[Sum of Divisors]]*
## Explanations
1. The number of multiples of $d$ which are $\displaystyle \leq n=\left\lfloor  \frac{n}{d}  \right\rfloor \ n,d \in \mathbb{N}$
	1. Let $n=ad+b$ where the amount of multiples of $\displaystyle d \leq n=a$.
	2. $\displaystyle \left\lfloor  \frac{n}{d}  \right\rfloor=\left\lfloor  \frac{ad+b}{d}  \right\rfloor=\left\lfloor  \frac{ad}{d}  +\frac{b}{d}\right\rfloor=\lfloor a \rfloor+\left\lfloor  \frac{b}{d}  \right\rfloor=a$.
2. $\displaystyle\left\lfloor  \frac{n}{k}  \right\rfloor-\left\lfloor  \frac{n-1}{k}  \right\rfloor = \begin{cases} 1, &k|n\\0, & k \nmid n \end{cases}$  
	1. This is a consequence of property 1. If $k|n$ then there will be one more multiple of $k\leq n$ than $\leq n-1$ so you get $(a+1)-a=1$.
	2. If $k\nmid n$ then there will be the same amount of multiples of $k\leq n$ so you get $a-a=0$. 
3. $\displaystyle\sum_{k=1}^n\tau(k)=\sum_{k=1}^n \left\lfloor  \frac{n}{k}  \right\rfloor$ 
	1. Form and $n\times n$ table with rows and columns $\{1,2,\dots,n\}$. The $(i, j)$ element is $1$ if $i$ is a multiple of $j$. Count the total number of $1$'s, $T$
	2. Fix column $j$. The number of $1$'s in the $j$th column is $\displaystyle\left\lfloor  \frac{n}{j}  \right\rfloor$ by property 1. So $\displaystyle T=\left\lfloor  \frac{n}{1}  \right\rfloor+\left\lfloor  \frac{n}{2}  \right\rfloor + \cdots+\left\lfloor  \frac{n}{n}  \right\rfloor$.
	3. Fix row $i$. The number of $1$'s in the $i$th row is simply $\tau(n)$. So $T=\tau(1)+\tau(2)+\cdots+\tau(n)$.
	4. Meaning $\displaystyle T=\left\lfloor  \frac{n}{1}  \right\rfloor+\left\lfloor  \frac{n}{2}  \right\rfloor + \cdots+\left\lfloor  \frac{n}{n}  \right\rfloor=\tau(1)+\tau(2)+\cdots+\tau(n)$.
4. $\displaystyle\sum_{k=1}^n\sigma(k)=\sum_{k=1}^n k\left\lfloor  \frac{n}{k}  \right\rfloor$
	1. Same construction as property 3. However instead of writing a $1$ write $j$. And consider the sum of the whole table $S$
	2. Fix column $j$. The sum of the $j$th column is $\displaystyle S=1\left\lfloor  \frac{n}{1}  \right\rfloor+2\left\lfloor  \frac{n}{2}  \right\rfloor+\cdots+n\left\lfloor  \frac{n}{n}  \right\rfloor$
	3. Fix row $i$. The sum of the $i$th row is $S=\tau(1)+\tau(2)+\cdots+\tau(n)$
	4. Meaning $\displaystyle S=1\left\lfloor  \frac{n}{1}  \right\rfloor+2\left\lfloor  \frac{n}{2}  \right\rfloor+\cdots+n\left\lfloor  \frac{n}{n}  \right\rfloor=\tau(1)+\tau(2)+\cdots+\tau(n)$