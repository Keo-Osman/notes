---
tags:
  - maths/calculus/ODE
  - maths/linear-algebra
---
# Definition
A linear ordinary [[Derivatives|differential]] equation is a differential equation in the form $$y^{(n)}(x)+a_{n-1}y^{(n-1)}(x)+\dots+a_{0}y(x)=f(x)$$
Where $y(x)$ is an unknown function and $\displaystyle y^{(n)}(x)=\frac{d^{n}}{dx^{n}}(y)$

The ***order***, which is equal to $n$, of the differential equation and it's the highest order derivative seen in the equation.
For a linear ODE to be ***homogenous*** it simply means that $f(x)=0$.
The ***Characteristic Polynomial*** of the equation is $m^{n}+a_{n-1}m^{n-1}+\dots+a_{0}$.
***
# [[Vectors#Vector Spaces|Vector Space]]
We can look at the vector space $$V=\{f:\mathbb{R}\to \mathbb{R} \ |\ f \in C^{n}(\mathbb{R})\}$$
*the vector space of real functions n times differentiable*.
We can also notice that differentiation is a [[Linear Transforms|Linear Operator]] in $V$.
Since the equation is a linear combination of $y$ after varying amounts of differentiation - a linear operator - we can write the whole equation as $$L[y]=f(x)\quad \text{or} \quad P(D)y=0$$
Where $L$ is a linear operator and $P(D)$ is a polynomial of operator $D$ the differentiation operator. This means we can represent $L$ and $P(D)$ as a [[Matrices|Matrix]] $A$. *We will be using $P(D)$ notation*. 

Given $P(D)y=0$ the solution space is the null space of $P(D)$ which is equivalent to the [[Eigen Vectors|Eigen]] space of $P(D)$ at $0$ *(As we have the familiar form of the equation $Ay=0\cdot y$)* 
*(Also since we are over a vector space of functions the eigen vectors are sometimes called eigen functions).*
An eigen function of the base operator $D$ is clearly $y=e^{\lambda x}$ as it satisfies $\displaystyle \frac{d}{dx}y=\lambda y$.
we have $P(\lambda)=0$ then $P(D)e^{\lambda x}=P(\lambda)e^{\lambda x}=0\implies e^{\lambda x}\in \operatorname{ker}(P(D))$



So we know that $Dy$ is equivalent to $\lambda y$ substituting this into $P(D)y$ we get $(\lambda^n+a_{n-1}\lambda^{n-1}+\dots+a_{0})y=0\implies\lambda^n+a_{n-1}\lambda^{n-1}+\dots+a_{0}=0$ this is the *characteristic polynomial*. If $\lambda_{k}$ is a solution to the equation it is an eigen value of $P(D)$ and we know that the corresponding eigen vector is $e^{\lambda_{k}x}$




***
# Reduction to a System of Degree 1 ODEs 

For the *homogenous case* we define two vectors $\mathbf{y}(x)=\begin{pmatrix}y(x) \\ y'(x) \\ \vdots \\ y^{(n-1)}(x)\end{pmatrix}$ and $\mathbf{y}'(x)=\begin{pmatrix}y'(x) \\ y''(x) \\ \vdots \\ y^{(n)}(x)\end{pmatrix}$ and rearranging the equation to get $y^{(n)}(x)=-a_{k-1}y^{(k-1)}(x)-\dots-a_{1}y'(x)-a_{0}y(x)$. 
Using this we can write the matrix equation as $$
\begin{gather}
\mathbf{y}'(x)=A\mathbf{y}(x)\\ \\
A=\begin{pmatrix}
0 & 1 & 0 & \cdots & 0 \\
0 & 0 & 1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 1 \\
-a_{0} & -{a}_{1} & -a_{2} & \cdots & -a_{n-1}
\end{pmatrix}
\end{gather}$$
Since $A\mathbf{y}(x)=\mathbf{y}'(x)$ looks very similar to $A\mathbf{y(x)}=\lambda \mathbf{y}(x)$ we can find 









