---
tags:
  - maths/number-theory
---
# Wilson's Theorem
**Theorem** $$\text{n is prime } \Leftrightarrow(n-1)!\equiv -1 \pmod{n}$$$$n\text{ is composite}\Leftrightarrow (n-1)! \equiv 0\pmod{n}$$

*Proof:*
**Forward Direction**
Start with $2 \cdot 3 \cdots (p-2)\pmod{p}$ using the fact that $\text{mod p}$ every element in $\{2, 3, \dots, (p-2)\}$ has a unique inverse, you can pair these elements up to get $1 \cdot 1 \cdots 1 \equiv 1 \pmod{p}$. Multiplying both sides by $(p-1)$ you obtain the desired result. 

**Reverse direction** - *Proof by contrapositive*
Assume $n$ is composite then $\exists p, q, \ 1 <p, q < n \text{ s.t } pq=n$ since $1 <p, q < n$ both $p, q$ must be contained in $(n-1)!$ so $(n-1)!=k(pq) = kn \Rightarrow n|(n-1)! \Rightarrow (n-1)! \equiv 0 \pmod{n}$. Therefore if $(n-1)! \not\equiv -1 \pmod{n}$, $n$ can't be composite and is therefore prime\.