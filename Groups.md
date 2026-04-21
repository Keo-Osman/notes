---
tags:
  - maths/abstract-algebra
---
# Axioms of Groups
A Group is a set together with a binary operation denoted by $(G, *)$ where $G$ is a set and $*$ is a binary operation. (Conventionally the operation is called multiplication even though it may not be standard multiplication).

A Group has to satisfy the following 4 axioms (*some corollaries included)*
1. Closure: $\forall a,b \in G$, $a * b \in G$
2. Associativity: $\forall a,b,c \in G$, $(a*b)*c = a*(b*c)$
3. Inverse: $\forall a \in G$, $\exists a^{-1}$ s.t $a*a^{-1} = e$. 
	1. Inverses are commutative $a^{-1}*a=e$
	2. Inverses are unique.
	3. $(a^{-1})^{-1}=a$
4. Identity: $\exists$ $e$ s.t $a*e=a$. 
	1. Identity is commutative $e*a=a$
	2. Identity is unique.

*Note that commutativity is not required*
## Corollary Proofs
The following properties are a direct result of the axioms and are sometimes included in the definition but do not have to be.
**Proof** $(3.1)$
Consider the product $a^{-1}*a*a^{-1}$ 
$$
a^{-1}*(a*a^{-1}) = a^{-1}*e = a^{-1} 
$$

Now multiply on the right by $(a^{-1})^{-1}$
$$
\begin{align}
(a^{-1}*a)*(a^{-1}*(a^{-1})^{-1}) &= a^{-1}*(a^{-1})^{-1}\\
(a^{-1}*a)*e &= e\\
a^{-1}*a &= e
\end{align}

$$
**Proof** $(4.1)$
1. Consider $a*a^{-1}*a$.
2. $a*a^{-1}*a=(a*a^{-1})*a=e*a$. Using $(2)$ and $(3)$
3. $a*a^{-1}*a=a*(a^{-1}*a)=a*e$. Using $(2)$ and $(3.1)$
4. Hence $a*e=e*a=e \quad \square$

**Proof** $(3.2)$
1. Assume that that exists two distinct inverses of $a$ such that $a*a^{-1}=a*a'=e$
2. Then $a*a^{-1}=a*a'\implies(a^{-1}*a)*a^{-1}=(a^{-1}*a)*a'\implies e*a^{-1}=e*a'\implies a^{-1}=a' \quad \square$ 

**Proof** $(4.2)$
1. Assume that there exists two distinct identity elements such that $a*e=a*e'=a$
2. Then $a*e=a*e'\implies (a^{-1}*a)*e=(a^{-1}*a)*e'\implies e*e=e*e'\implies e=e' \quad \square$

**Proof** $(5)$ - For a fixed $a\in G$, $a*b$ maps to a unique $x$ for all $b \in G$.
1. Assume that for a given $a\in G, \ ab=ac=x \in G\implies ab=ac\implies a^{-1}ab=a^{-1}ac\implies b=c \quad \square$

**Proof** $(3.3)$ - $(a^{-1})^{-1}=a$
1. $(a^{-1})^{-1}*a^{-1}=e\implies(a^{-1})^{-1}*a^{-1}*a=e*a\implies (a^{-1})^{-1}=e \quad \square$

***
# Cayley Tables
A Cayley Table fully describes a finite group by showing all possible products of elements in the group
Example: 
$$
\begin{array}{c|cccc}
\times_{10}& 1 & 3 & 7 & 9 \\
\hline
1 & 1 & 3 & 7 & 9 \\
3 & 3 & 9 & 1 & 7 \\
7 & 7 & 1 & 9 & 3 \\
9 & 9 & 7 & 3 & 1 \\
\end{array}
$$

When a group's elements are displayed in a Cayley Table:
1. **All entries are $\in G$**
2. **Every entry appears exactly once in each row and column** 
	1. Trivial with $(5)$
3. $e$ must appear in every row and column and it's position is symmetric about the leading diagonal 
	1. Since $e = a*a^{-1} = a^{-1}*a$ (and can only be formed from this operation), when $e$ is in location $(x, y)$ it has to be in $(y, x)$ as $x$ or $y$ are $a$ or $a^{-1}$ so $x*y = y*x$

***
# Order
The order of group $G$ denoted as $|G|$ is the size of the underlying set
The order of an element $a$ is the smallest non-negative integer $k$ *s.t* $a^k = e$. Also $\nexists k \Rightarrow |a| = \infty$

**Properties**
1. $|G| < \infty \Rightarrow |a|\ \Big| \  |G|$
2. $G \text{ is cyclic } \Leftrightarrow \exists a \text{ s.t } |a| = |G|$
3. $|a| < \infty \Rightarrow (a^m = e \Leftrightarrow |a|\ \Big|m )$
4. $|a| = \infty \Rightarrow (x \neq y \Rightarrow a^x \neq a^y)$
5. $a^x = a^y$ and $x\neq y \Rightarrow |a| < \infty$
***
# Subgroups 
If some subset of the underlying set of a group adheres to the group axioms then it is a subgroup. Every group $(G, *)$has at least 2 trivial subgroups $(\{e\}, *)$ and $(G,*)$ - itself.
**Definitions**
1. $H \subseteq G$ means $H$ is a subgroup of $G$, $H \subseteq G \Rightarrow |H| \leq |G|$
2. $H \subset G$ means $H$ is a proper subgroup of $G$ meaning $H\neq G$, $H \subset G \Rightarrow |H| < |G|$

Let $G$ be a group and $H$ a finite subset of the underlying set of $G$ $\Rightarrow$ ($H$ is a subgroup $\Leftrightarrow$ $H$ is closed under the operation of $G$)
## Subgroup Generation
$|G| < \infty \Rightarrow \forall a \in G$ generates $\langle a \rangle \subseteq G$ 
## Lagrange's Theorem
$(H \subseteq G) \wedge(|G| < \infty) \Rightarrow |H| \ \Big| \ |G|$
***
# Isomorphisms
2 groups $(G,*)$, $(H,\circ)$ are isomorphic $(G \cong H)$ if there exists a mapping called a *group isomorphism* $f: G \rightarrow H$ such that:
1. $f$ maps all elements of $G$ to $H$
2. $f$ is one to one
3. $f$ preserves structure: $f(a*b) = f(a) \circ f(b)$
## Properties
If $G \cong H$ with identity elements $e_G$, $e_H$ and $f: G \rightarrow H$ is an isomorphism then $\forall a \in G$ and $\forall n \in \mathbb{Z}$:
1. $f(e_G) = e_H$
2. $f(a^{-1}) = [f(a)]^{-1}$
3. $f(a^n) = [f(a)]^n$
4. $|G| = |H|$
5. If $G$ has $k$ elements of order $n$ then $H$ has $k$ elements of order $n$
6. If $G$ has $k$ subgroups of order $n$, $H$ has $k$ subgroups of order $n$
7. $J \subseteq G \Rightarrow \exists L \subseteq H$ such that $J \cong L$
***
# Types of Groups
## [[Modular Arithmetic]] Groups
You can use modular arithmetic to define a finite group of integers.
The operation $\times_n$ is defined as $ab \pmod{n}$
The operation $+_n$ is defined as $(a+b) \pmod{n}$
## Groups of Permutations
 A group of Permutations is a group with a set of permutations of $n$ objects with operation $a \circ b$ composition - the operation of applying permutation $b$ then $a$ forms a group.

The symmetric group $S_n$ is a group of permutation on $n$ elements where the set consists of all possible permutations that can be performed on $n$ objects coupled with the operation of composition $(a \circ b)$. *(It's basically a fully complete group of permutations of $n$ objects 1. a normal group of permutations doesn't have to contain every possible permutation of $n$, These "incomplete" groups will be be subgroups of $S_n$)*

### 2 Row Notation
You can use 2 row notation to describe permutations like: $\begin{pmatrix} 1 & ... & n \\ p_1 & ... & p_n \end{pmatrix}$
The top row shows the starting position and $p_i$ denotes what object will end up in the $i$th position and *NOT* what position the $i$th object will end up in.

**Composition**
For$a \circ b = c$, $c$ will be $\begin{pmatrix} 1 \cdots n \\ c_1 \cdots c_2 \end{pmatrix}$ where $c_i$ is found by finding $b_i$ in $b$ (in the bottom row) then find $b_i$ in top row of $a$ and $c_i$ is the corresponding $a_{(b_i)}$.
**Inverse**
To find the inverse swap top and bottom.
## Groups of Symmetries
You can construct a group of symmetries denoted by $D_{2n}$ by considering a set of all symmetrical transformations of an $n$-sided polygon coupled with the composition operation.
*There is $n$ possible rotations and $n$ possible reflections so for an $n$ sided polygon there are $2n$ elements so the group is denoted as $D_{2n}$ meaning ($D_8$ would be a square)*
## Cyclic Groups
A cyclic group is a group that can be written where all elements can be written as $a^k$ where $a$ is the group generator and $k \in \mathbb{Z}^+$. $a^k$ denotes performing the group operation $k$ times.$$a^3 = a \circ a \circ a \qquad a^k = \underbrace{a \circ a \cdots \circ a}_{k \text{ times}}$$

***
# Direct Product of Groups
The **direct product** of two groups $G_1$ and $G_2$, denoted $G_1 \times G_2$, is a group defined as follows:

**Underlying Set**
The elements of $G_1 \times G_2$ are ordered pairs $(g_1,g_2)$ such that $g_1 \in G_1$ and $g_2 \in G_2$. Formally:  $G_1 \times G_2 = \{ (g_1, g_2) \mid g_1 \in G_1, \, g_2 \in G_2 \}$

**Group Operation**
The operation on $G_1 \times G_2$ is defined component-wise. For $(g_1, g_2), (h_1, h_2) \in G_1 \times G_2$, the operation is:  $(g_1, g_2) \circ (h_1, h_2) = (g_1 \circ h_1, \, g_2 \circ h_2)$

**Identity Element**
The identity element of $G_1 \times G_2$ is: $(e_1, e_2)$

**Inverses**: 
The inverse of an element $(g_1, g_2) \in G_1 \times G_2$ is: $(g_1^{-1}, g_2^{-1})$
