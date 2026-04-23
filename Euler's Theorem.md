---
tags:
  - maths/number-theory
---
*Links:* [[Modular Arithmetic]]
# Euler's Theorem
Euler's Theorem is a more general case of [[Fermat's Little Theorem]] using [[Euler's Totient Function]]. 

$$
a^{\varphi(n)}\equiv 1 \pmod{n} \quad \gcd(a,n)=1
$$In the case of $n$ being prime $\varphi(n)= n-1$ and it simplifies to Fermat's Little Theorem\.

##### Proof
By considering the elements of $S$ *(The [[Modular Arithmetic#Reduced Residue System|Reduced Residue System]] $\text{mod n}$)*, and multiplying them together. $(a\cdot 1)\cdots(a\cdot(n-1)) \equiv 1 \cdots (n-1) \pmod{n}$. Hence $$\displaystyle a^{\varphi(n)}\cdot \prod_{\substack{1\leq i <n \\ \gcd(i, n)=1}} i \equiv \prod_{\substack{1\leq i <n \\ \gcd(i, n)=1}} i$$
Since the products only contain $i$ coprime to $n$ the whole product will share no prime factors to $n$ and so the whole product is coprime to $n$ and therefore can be cancelled. Therefore $a^{\varphi(n)}\equiv 1 \pmod{n}$ as required\.