---
tags:
  - maths/number-theory
---
# Definition
Modular arithmetic is a system of arithmetic restricted to the remainders. Defined as
$$a \equiv b \pmod{m} \Leftrightarrow m|(a-b), \ m \in \mathbb{Z}^+ \quad a, b \in \mathbb{Z}$$
or equivalently using [[Euclid's Division Lemma]] $$a \equiv b \pmod{m} \Leftrightarrow \exists k \in \mathbb{Z} \text{ s.t } a = b + km$$
# Basic Properties
**Theorem**
1. $a \equiv 0 \pmod{m} \Leftrightarrow m|a$
2. $a \equiv a \pmod{m}$
3. $a \equiv b \pmod{m} \Rightarrow b \equiv a \pmod{m}$
4. $(a \equiv b \pmod{m}) \wedge (b \equiv c \pmod{m}) \Rightarrow a \equiv c \pmod{m}$
5. Let $a, b, c, d, n, p, k \in \mathbb{Z}$ and $m, n > 0$, with $a \equiv b \pmod{m}$ and $c \equiv d \pmod{m} \Rightarrow$
	1. $ka \equiv kb \pmod{m}$
	2. $a \pm c \equiv b \pm d \pmod{m}$
	3. $ac \equiv bd \pmod{m}$
	4. $a^n \equiv b^n \pmod{m}$

---
# Reduced Residue System
## Prime Reduced Residue System
Let $S = \{0, a, 2a, \dots\} \pmod{p}$ where $p$ is prime. Then $S = \{0, 1, \dots, (n-1)\}$.
*Proof*
1. Since $ai \equiv (p+i)a \pmod{p}$, $S_1= \{0, a, 2a, \dots, (p-1)a\}$. 
2. To prove that no 2 elements in $S$ are equal assume $\exists i, j \quad 0 \leq i \neq j, \leq (p-1) \text{ s.t } ai \equiv aj \pmod{p} \Rightarrow a(i-j) \equiv 0 \pmod{p} \Rightarrow i-j | p$ but $|i-j| < p \Rightarrow i-j \nmid n$. 
3. Therefore $S = \{0, 1, \dots, (n-1)\}$.
4. Meaning you could write $aS \equiv S \pmod{p}$.

Since $0\times a = 0$, you can remove $0$ as it maps to itself from $S_1$ to $aS_1$ so you can remove $0$ from both sets to obtain a more useful set $S$ ***The Reduced Residue System $\pmod{p}$***.
## Full Definition
The full definition of a reduced residue system $\text{ mod n}$ is the set of integers *less than $n$, coprime to $n$ and distinct $\text{ mod n}$*. So $aS \equiv S \pmod{n}$. However $|S| < n$ if $n$ is composite as $ka \pmod{n}$ is not guaranteed to be coprime to with $n$ as with $n$ being composite, some $k$ will divide $n$ so $\gcd(ka, n) \neq 1 \Rightarrow \gcd(ka\pmod{n}, n)\neq 1$.
$1$ and $n-1$ are always guaranteed to be in the set as $\gcd(1, n) = \gcd(n-1, n) = 1$.

*The construction is the exact same as with prime modulo.*
$|S|\equiv \varphi(n)$ *[[Euler's Totient Function]]*
***
# Inverses
## Definition
Using the [[Modular Arithmetic#Reduced Residue System|Reduced Residue System]] $\text{mod n }$we can see that with $\gcd(a,n)=1$, $\forall b \in \mathbb{Z}^+ ,\ 0 < b < p, \ \exists! x \text{ s.t } ax \equiv b \pmod{n}$.
In particular if $b=1$ we get $ax \equiv 1 \pmod{n}$. This means that $a$ and $x$ are multiplicative inverses $\text{mod n}$. *(This comes from the fact that across the real numbers $a \cdot a^{-1} \equiv 1$*
You can find $x$ by using [[Bezout's Identity]] $\gcd(a, n) = 1\Leftrightarrow \exists p, q \text{ s.t } ax + ny=1 \Rightarrow ax=1-ny \Rightarrow ax=1 \pmod{n}$
The existence allows division. 
## Existence
However inverses are ***NOT*** guaranteed to exist but they are $\text{mod p}$ if $a \not\equiv 0 \pmod{p}$. 
**Theorem**
$a^{-1} \pmod{n}$ exists *if and only if* $\gcd(a, n)=1$\.

*Proof:*
Let $\gcd(a,n)=d$, then $ax\equiv 1\pmod{n}\implies n|ax-1\implies d|1\implies d=1$

## Uniqueness
Inverses are unique meaning only one solution exists to $ax \equiv 1 \pmod{p}$ *(meaning an element only has one inverse)*. It follows that no two elements have the same inverse due to the following.

**Theorem**
$a^{-1}=b\implies b^{-1}=a$\.

*Proof:*
Assume that there are two inverses such that $ax\equiv ay\equiv 1 \pmod{n}$ $x,y<n$. So we get that $a(x-y)\equiv 0 \pmod{n}\implies n|a(x-y)$. Since $\gcd(a,n)=1$ this must mean that $n|(x-y)$ but since $x,y<n\implies (x-y)<n$, $(x-y)=0\implies x=y$\.

## Other Useful Properties
**Theorem** -  *Pairs of Inverses*
Since $a^{-1} \equiv b \pmod{p} \Rightarrow a \equiv b^{-1} \pmod{p}$, inverses can be written in pairs $(a,b)$.
An element can be self inverse meaning $a^2\equiv 1 \pmod{p}$. This means $p|a^2-1=(a+1)(a-1) \Rightarrow p|(a+1) \text{ or } p|(a-1) \Rightarrow a \equiv 1 \text{ or } a \equiv -1$ *(This is the only case where $a$ is self inverse).*

**Theorem** $$\gcd(a^{-1}, n) = 1$$
*Proof:*
By definition $aa^{-1}= kn+1\implies1 = aa^{-1}-kn$. Let $d = \gcd(a^{-1}, n)$ so $d|a^{-1}\implies d|aa^{-1}$ as well as $d|kn$. Putting them together we get $d|aa^{-1}-kn=1$ hence $d=1$\.

## Fractional Behaviour
You can write inverses as a fraction like $a \cdot b^{-1} \equiv \frac{a}{b}$. 

**Theorem**
They can be added and multiplied normally.

*Proof:* Addition 
$$\displaystyle bd(a\cdot b^{-1}+c\cdot d^{-1})=bd(a\cdot b^{-1})+bd(c\cdot d^{-1})\equiv ad+ bc \pmod{p} \Rightarrow \frac{a}{b}+\frac{c}{d}\equiv \frac{ad+bc}{bd} \pmod {p}$$
*Proof:* Multiplication
$$\displaystyle bd(a \cdot b^{-1})\cdot(c \cdot d^{-1}) =b(a \cdot b^{-1})\cdot d(c \cdot d^{-1})\equiv a \cdot c \pmod{p} \Rightarrow \frac{a}{b} \cdot \frac{c}{d} \equiv \frac{ac}{bd} \pmod{p}$$

**Theorem** $$\frac{a}{b}\equiv 0 \pmod{n} \implies a\equiv 0 \pmod{n}$$
*Proof:*
$\frac{a}{b}\equiv a\cdot b^{-1} \equiv 0$ but since an inverse can never be zero as $x\cdot 0 \not\equiv 1$, We also can't have both $a,b^{-1}$ be proper divisors of $n$ *(For example something like $a=4, b^{-1}=2 \pmod{8}\implies ab^{-1}=0$)* as $\gcd(b^{-1}, n) =1$. So we must have $a\equiv 0$\.
***
# Congruence Equations
Equations with modular arithmetic are given in terms called congruence equations and their answers are usually given in terms of least residues.
The set of least residues $k \pmod{m}$ is $\{0, 1, \ldots, m-1\}$

Since a solution $x \equiv n \pmod{m}$ represents an infinite number of solutions, you can write a general solution as: $\{n + km : k \in \mathbb{Z}\}$

## Congruence Equation Properties
Let $a, b, m \in \mathbb{Z}, m > 0$,  $\gcd(a,m) = d$
**Theorem**
1. $d \nmid b \Rightarrow$ the equation $ax \equiv b \pmod{m}$ has no solutions
2. $d \mid b \Rightarrow$ the equation has $d$ solutions in the set of least residues
3. $(ka \equiv kb \pmod{m}) \wedge (\gcd(k,m) = d) \Rightarrow a \equiv b \pmod{\frac{m}{d}}$
***
# Modular Contradictions
In many problems you can use the fact that certain powers of $a$ can only take on certain values $\operatorname{mod}{n}$ so if you can show that it takes on a value which is impossible you can get a contradiction
**Theorem**
1. $a^2 \equiv\{0, 1\}\pmod{3}$
2. $a^2 \equiv\{0, 1\}\pmod{4}$
3. $a^2 \equiv\{0, \pm1\}\pmod{5}$
4. $(\text{odd})^2 \equiv\ 1\pmod{8}$
5. $a^3 \equiv\{0, \pm1\}\pmod{7}$
6. $a^3 \equiv\{0, \pm1\}\pmod{9}$
7. $\displaystyle a^{\textstyle \frac{p-1}{2}}\equiv \pm 1 \pmod{p}$, $\gcd(a,p)=1$ *by [[Fermat's Little Theorem]]*
8. $\displaystyle a^{\textstyle\frac{\varphi(n)-1}{2}}\equiv \pm 1 \pmod{n}$, $\gcd(a,n)=1$ *by [[Euler's Theorem]]*
***
# Advance Properties and Results
**Theorem** $$\displaystyle a^x \equiv a^y \equiv 1 \pmod{n} \Rightarrow a^{\gcd(x, y)} \equiv 1 \pmod{n}$$
*Proof:*
By [[Bezout's Identity]] $mx+ny = \gcd(m, n)$. $$a^{\gcd(m, n)} = a^{mx+ny}=a^{mx} \cdot a^{ny} = {(a^{m})}^{x} \cdot {(a^{n})}^{y} \equiv 1 \pmod{d}$$

**Theorem** $$\displaystyle ad \equiv bd \pmod{n} \Rightarrow a \equiv b \quad \left(\text{ mod} {\frac{n}{\gcd(n, d)}}\right)$$
*Proof:*
We have $n|d(a-b)$. $n=gn'$, $g=gd'$ with $g=\gcd(n,d)$. So $n'|d'(a-b)$. So $n'|(a-b)$. Therefore $\displaystyle a\equiv b \left(\text{ mod } n'= {\frac{n}{\gcd(n, d)}}\right)$\.

**Theorem** $$(a+b)^{p^i} \equiv a^{p^i}+b^{p^i} \pmod{p} \quad i \in \mathbb{N}_{0}$$
*Proof:*
First we will prove that $(a+b)^p \equiv a^p+b^p \pmod{p}$
Expanding *LHS* obtains $(a+b)^p = a^p + \binom{p}{1} ba^{p-1} + \cdots + \binom{p}{p-1}b^{p-1}a + a^p$.  Since $p|\binom{p}{k}$ *(Shown in [[Divisibility]])*, all terms except $a^p$ and $b^p$ are divisible by $p$.

*Inductive proof*
**Base case**: it is clear that $i=0$ satisfies the equation.
Then assume $(a+b)^{p^i} \equiv a^{p^i}+b^{p^i}$. $(a+b)^{p^{i+1}}=((a+b)^{(p^i)})^p$, by our assumption $\equiv (a^{p^i}+b^{p^i})^p$ which then by our first claim $\equiv(a^{(p^i)})^p + (b^{(p^i)})^p \equiv a^{p^{i+1}}+b^{p^{i+1}}$\. 

**Theorem**
$x^p-x \equiv x(x-1)(x-2)\cdots (x-(p-1)) \pmod{p} \quad \forall x$\.

*Proof:*
By [[Fermat's Little Theorem]] *LHS*$=0$. And one of $x, x-1 \dots,x-(p-1)$ is $0 \pmod{p}$\.

**Theorem** - *Wolstenholme's Theorem*
For $p>3$, $\displaystyle  1+\frac{1}{2}+\frac{1}{3}+\cdots + \frac{1}{p-1} \equiv 0 \pmod{p^2}$.

*Proof:*
1. $\displaystyle \sum_{i=1}^{p-1} \frac{1}{i} =\sum_{i=1}^{\frac{p-1}{2}} \left(\frac{1}{i}+\frac{1}{p-i}\right) = p\sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)}$ 
2. Since we have a factor of $p$ it is now sufficient to show that $\displaystyle \sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)} \equiv p \equiv 0 \pmod{p}$ for the original sum to be $\equiv 0 \pmod{p}$.
3. Since $(p-i) \equiv -i \pmod{p}$ we can replace the denominators with $-i^2$ and we can multiply the sum by $2$ to restore the amount of terms back to $p-1$, the reason being that after $\frac{p-1}{2}$ the terms descend back symmetrically so term $i$ is equivalent to term $p-i$ as $\frac{1}{i(p-i)}= \frac{1}{(p-i)(p-(p-i))} = \frac{1}{(p-i)i}$ 
4. So we get $\displaystyle 2\sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)} \equiv - \sum_{i=1}^{p-1} \frac{1}{i^2} \pmod{p}$.
5. Since inverses are unique we get that $\{1^{-1}, 2^{-1}, \dots, (p-1)^{-1}\} \equiv \{1, 2, \dots, p-1\} \pmod{p}$ so each term corresponds to a unique residue. Therefore $\displaystyle \sum_{i=1}^{p-1} \frac{1}{i^2}  \equiv \sum_{i=1}^{p-1} i^2 = \frac{(p-1)p(2p-1)}{6} \pmod{p}$ . Since $p>3 \Rightarrow \gcd(p, 6) =0 , \ \frac{(p-1)p(2p-1)}{6} \equiv kp \equiv 0 \pmod{p}$ 
6. Going back to step 4 we now get $\displaystyle 2\sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)} \equiv 0 \pmod{p} \Rightarrow p|\left(2\sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)}\right)$ but $\displaystyle \gcd(2, p)=1 \Rightarrow p|\left(\sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)}\right) \Rightarrow \sum_{i=1}^{\frac{p-1}{2}} \frac{1}{i(p-i)} \equiv 0 \pmod{p}$ which by step 2 is sufficient to prove the statement. 


**Theorem**
$\displaystyle \binom{p-1}{k} \equiv (-1)^k \pmod{p}$

*Proof:*
$$\begin{aligned}
\binom{p-1}{k}&=\frac{(p-1)!}{k!(p-1-k)!} \\
&=\frac{(p-k)!(p-k-1)!}{k!(p-k-1)!}\\
&=\frac{(p-k)!}{k!} \\
&\equiv \frac{-1\times-2\times \cdots \times-k}{k!} \\
&\equiv \frac{(-1)^kk!}{k!}\equiv (-1)^k \pmod{p}
\end{aligned}$$