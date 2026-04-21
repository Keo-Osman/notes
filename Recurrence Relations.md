---
tags:
  - maths/algebra
---
# Definition
A Recurrence Relation describes a term of a sequence as in terms of previous terms.
They can use varying amounts of previous terms (go back further) and you can describe this by the order which is defined as the difference between the lowest & highest subscript.
They are strongly related to [[Differential Equations]] and are often solved in the same/similar ways as recurrence relations are basically discrete differential equations. 
***
# First Order Recurrence Relations
First order linear recurrence relations are in the form
$$u_n = au_{n-1} + g(n)$$
## Homogenous
If $g(n) = 0$ then the equation is **homogeneous** and the general solution is
$$u_n = a^nu_0 \quad \text{or} \quad u_n = a^{n-1}u_{1}$$
This is proved by **back substitution** *or more rigorously with **Proof by Induction***$$\begin{aligned}
u_{n} & =au_{n-1} \\
 & =a\times au_{n-2}=a^2u_{n-2} \\
 & =a^2\times au_{n-3}=a^3u_{n-3} \\
 & \vdots \\
 & =a^{n-1}u_1 \\
 & =a^nu_0
\end{aligned}$$
## Non-Homogenous
For $u_n = u_{n-1} + g(n)$, the general solution is $u_n = u_0 + \sum_{i=0}^n g(i)$

To find the general solution to $u_n = au_{n-1} + g(n)$ where $a \neq 1$ is $C.F + P.S$, Where $C.F$ is the solution to $u_n = au_{n-1}$ which is $a^nu_0$ and $P.S$ is a particular solution to the equation.

| Form of $g(n)$     | Form of $P.S$     |
| ------ | ------------- |
| $p, a \neq 1$      | $\lambda$         |
| $pn + q, a \neq 1$ | $\lambda n + \mu$ |
| $kp^n, p \neq a$   | $\lambda k^n$     |
| $ka^n$             | $\lambda na^n$    |

***
# Solving Second Order Recurrence Relations
A 2nd order linear recurrence relation can be written in the form
$$u_n + au_{n-1} + bu_{n-2} = g(n)$$
If $u_n = F(n)$ and $u_n = G(n)$ are particular solutions to a linear recurrence relation then $u_n = aF(n) + bG(n)$ is a solution.

## Homogenous
The general solution to a homogeneous 2nd order linear recurrence relation of
$u_n = au_{n-1} + bu_{n-2}$ depends on the auxiliary equation $r^2 + ar + b = 0$

This quadratic leads to 3 cases.
1. The auxiliary equation has 2 real root $\Rightarrow u_n = A\alpha^n + B\beta^n$
2. The auxiliary equation has 1 repeated root $\alpha$. $\Rightarrow u_n = (A + Bn)\alpha^n$
3. The auxiliary equation has two complex conjugate roots $re^{\pm i \theta}$ $\Rightarrow u_n = r^n(A \cos n\theta + B \sin n\theta) = C\alpha^n + D\beta^n$
## Non-Homogeneous
For non-homogeneous the general solution is
$$u_n = C.F + P.S$$

| Form of $\mathbf{g}(\boldsymbol{n})$  | Form of particular solution |
| :---: | :-: |
|    $p$ with $\alpha, \beta \neq 1$    |          $\lambda$          |
| $p n+q$, with $\alpha, \beta \neq 1$  |       $\lambda n+\mu$       |
|  $k p^n$ with $p \neq \alpha, \beta$  |        $\lambda p^n$        |
|   $p$ with $\alpha=1, \beta \neq 1$   |         $\lambda n$         |
| $p n+q$ with $\alpha=1, \beta \neq 1$ |     $\lambda n^2+\mu n$     |
|       $p$ with $\alpha=\beta=1$       |        $\lambda n^2$        |
|     $p n+q$ with $\alpha=\beta=1$     |    $\lambda n^3+\mu n^2$    |
| $k \alpha^n$ with $\alpha \neq \beta$ |    $\lambda n \alpha^n$     |
|   $k \alpha^n$ with $\alpha=\beta$    |   $\lambda n^2 \alpha^n$    |
*(When $\alpha =1$ or $\beta =1$ you have to multiply the $P.S$ by $n$ so otherwise there will be redundancy and overlap and $C.F$ and $P.S$ are supposed to be linearly independent. This stacks if $\alpha= \beta = 1$ then multiply by $n$ twice which is the same as multiplying by $n^2$)*

***
# Proving closed forms
You can rigorously prove a closed for $u_n = f(n)$ by using Proof by Induction. This will require multiple base cases if the order of the relationship is $>1$. In general for an $n$ ordered recurrence relation, you will need to prove the base case for the first $n$ terms