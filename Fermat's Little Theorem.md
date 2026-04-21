---
tags:
  - maths/number-theory
---
*Links:* [[Modular Arithmetic]]
# Fermat's Little Theorem
**Theorem**
Let $p$ be prime and $\gcd(a, p) = 1$, then $$a^{p-1} \equiv 1\pmod {p}$$
*Proof:*
Using the [[Modular Arithmetic#Reduced Residue System|Reduced Residue System]] $\text{(mod p)}$, $S$. Multiplying all the elements together yields $a \cdot 2a \cdots (p-1)a \equiv 1 \cdot 2 \cdot (p-1) \pmod{p}$. This gives $a^{p-1} \cdot (p-1)! \equiv (p-1)!$. Since $\gcd((p-1)! \ , p) = 1$, you get $a^{p-1} \equiv 1\pmod {p}$\. 

*Proof:* 
**By Induction**
*Base case:* $1^p\equiv 1 \pmod{p}$
***Induction forwards***
Assume $a^p \equiv a \pmod{p}$, then $(a+1)^p \equiv a^p+1^p\equiv (a+1)\pmod{p}$ by assumption.

**Induction backwards**
Assume $a^p\equiv a\pmod{p}$, then $(a-1)^p\equiv a^p+(-1)^p$. For $p>2 ,\ p$ is odd. so we get $a^p-1$ which by our assumption $\equiv (a-1)\pmod{p}$. For $p=2$, we get $(a-1)^2=a^2-2a+1$ which by our our assumption $\equiv a-2a+1\equiv-a+1 +(2a-1)\equiv (a-1) \pmod{2}$.

Therefore we get the fact that $a^p\equiv a \pmod{p}$. If $a$ has an inverse you get $a^{p-1}\equiv 1 \pmod{p}$\.