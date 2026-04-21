---
tags:
  - maths/linear-algebra
---
[Why are Determinants Like That? (YT)](https://www.youtube.com/watch?v=Sv7VseMsOQc)
# Definition and Derivation
In an $n$ dimensional [[Vectors#Vector Spaces|Vector Space]] *(specifically $\mathbb{R}^{n}$)* we want to define a function to calculate the area/volume bounded by $n$ linearly independent vectors. 
## 2D $\mathbb{R}^{2}$
First we will start in $\mathbb{R}^{2}$ with basis vectors $\hat{i},\hat{j}$ so some natural properties of this area function (call it $A(\vec{v},\vec{u})$) are as following:
1. $A(\hat{i},\hat{j})=1$
2. $A(\vec{v},\vec{v})=0$
3. $A(0,\vec{v})=A(\vec{w},0)=0$
4. $A(k\vec{v},n\vec{u})=knA(\vec{v},\vec{u}) \ \forall k,n \in \mathbb{R}$
5. $A(\vec{v}+\vec{u},\vec{w})=A(\vec{v},\vec{w})+A(\vec{u},\vec{w}) \text{ and } A(\vec{v},\vec{w}+\vec{u})=A(\vec{v},\vec{w})+A(\vec{v},\vec{u})$

However we can notice that setting $\vec{u}=-\vec{v}$ in 5 gives that $A(\vec{v}+(-\vec{v}),\vec{w})=A(0,\vec{w})=0$ but using the rule in 5 we get $A(\vec{v}+(-\vec{v}),\vec{w})=A(\vec{v},\vec{w})+A(-\vec{v},\vec{w})=0\implies$ $$A(-\vec{v},\vec{w})=-A(\vec{v},\vec{w})$$
*Justifying why in property 4 the domain is $\mathbb{R}$ and not $\mathbb{R}_{\geq0}$*.

Next we try $A(\vec{v}+\vec{w},\vec{v}+\vec{w})=0$ but applying rule 5 gives $A(\vec{v}+\vec{w},\vec{v}+\vec{w})=A(\vec{v},\vec{v})+A(\vec{w},\vec{w})+A(\vec{v},\vec{w})+A(\vec{w},\vec{v})\implies$ $$A(\vec{v},\vec{w})=-A(\vec{w},\vec{v})$$
The sign gives the *orientation* of the parallelogram. If $A<0$ then orientation is negative and if $A>0$ the orientation is positive. For convention we choose orientation to be positive when going from $\vec{v}$ to $\vec{w}$ is counter-clockwise. For example $A(\hat{i},\hat{j})=1$ because going from $\hat{i}$ to $\hat{j}$ is a counter-clock wise rotation. However this is just convention you *could* define $A(\hat{j},\hat{i})=1$ so $A(\hat{i},\hat{j})=-1$ but you must pick *some* orientation to be positive and convention is counter-clockwise.
### Computation
By writing $\vec{v},\vec{w}$ as linear combinations of the basis vectors we get $A(\vec{v},\vec{w})=A(v_{1}\hat{i}+v_{2}\hat{j},w_{1}\hat{i}+w_{2}\hat{j})$ and applying or rules we get $$A(\vec{v},\vec{w})=v_{1}w_{2}-v_{2}w_{1}$$
Now instead of the function taking multiple vectors as input we have the function call it $\det A$ where $A$ is an $n\times n$ *(in this case $2\times 2$)* matrix with column vectors $\vec{v},\vec{w}$
## Generalisation to $\mathbb{R}^{n}$
In $\mathbb{R}^{n}$ we have basis vectors $e_{1},e_{2},\dots,e_{n}$ where $e_{k}$ is a column vector with all $0$s except a $1$ in the $k$th row.
So our axioms for $V$ *(no $V$ for volume)* are as follows:
1. $V(e_{1},e_{2},\dots,e_{n})=1$
2. $V(\vec{v}_{1},\vec{v}_{1}, \vec{v}_{3},\vec{v}_{4},\dots,\vec{v}_{n})=0$ - if any two vectors are the same they bound no volume. Holds if there are duplicates in *any* 2 slots.
3. $V(0,\vec{v}_{2},\vec{v}_{3},\dots ,\vec{v}_{n})=0$ - a zero in any slot means the whole thing $=0$
4. $V(k_{1}\vec{v}_{1},k_{2}\vec{v}_{2},\dots,k_{n}\vec{v}_{n})=\left(\prod k_{i}\right)V(\vec{v}_{1},\vec{v}_{2},\dots ,\vec{v}_{n}) \quad\forall k_{i}\in \mathbb{R}$
5. $V(\vec{v}_{1}+\vec{w},\vec{v}_{2},\dots ,\vec{v}_{n})=V(\vec{v}_{1},\vec{v}_{2},\dots ,\vec{v}_{n})+V(\vec{w},\vec{v}_{2},\dots ,\vec{v}_{n})$ - works in any slot.
*Combining 4 and 5 gives the property of multi-linearity - linear in every slot.*

By computing $V(\vec{v}_{1}+\vec{w},\vec{v}_{1}+\vec{w},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})=0$ as we have two of the same vectors but expanding out using 5 gives. $=V(\vec{v}_{1},\vec{v}_{1},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})+V(\vec{w},\vec{w},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})+V(\vec{v}_{1},\vec{w},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})+V(\vec{w},\vec{v}_{1}+\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})$
$\implies V(\vec{v}_{1},\vec{w},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})=-V(\vec{w},\vec{v}_{1},\vec{v}_{3},\vec{v}_{4},\dots ,\vec{v}_{n})$
*This generalises to any slot meaning swapping any two vectors flips the sign again giving rise to the idea of orientation.* 

We can also see that the sign of $A(\text{basis vectors})$ corresponds to the number of swaps needed to reach the permutation $e_{1},e_{2},\dots ,e_{n}$ more specifically the sign is negative for an odd amount of swaps and positive for an even amount.
From this we define a function $\operatorname{sign}(\mathbf{p})$ where $\mathbf{p}$ is a permutation of $1,2,\dots,n$ and $\operatorname{sign}(\mathbf{p})=(-1)^{\text{no. swaps to reach } 1,2,\dots,n}$ equivalently defined as 
$$\operatorname{sign}(\mathbf{p})=
\begin{cases}  1&\text{even no. swaps}\\-1& \text{odd no. swaps}
\end{cases}$$
### Computation
#### Leibniz Formula
We first write a vector in terms of the basis vectors giving $\displaystyle\vec{v}_{i}=\sum_{j=1}^{n} v_{ij}e_{j}$
$$
\begin{aligned}
&V\left(\sum_{j_{1}=1}^{n} v_{1j_{1}}e_{j_{1}},\sum_{j_{2}=1}^{n} v_{2j_{2}}e_{j_{2}},\dots,\sum_{j_{n}=1}^{n} v_{nj_{n}}e_{j}\right)
\\
&=\sum_{j_{1}=1}^{n}\sum_{j_{2}=1}^{n}\dots\sum_{j_{n}=1}^{n}\left(\prod_{i=1}^{n}v_{ij_{n}}\right)V(e_{j_{1}},e_{j_{2}},\dots,e_{j_{n}})
\\
&=\sum_{\substack{p\text{ is a permuation of}\\\text{of }1,2,\dots,n}}v_{1p_{1}}v_{2p_{2}}\dots v_{np_{n}}V(e_{p_{1}},e_{p_{2}},\dots e_{p_{n}})
\\
&=\boxed{ \sum_{\substack{p\text{ is a permuation of}\\\text{of }1,2,\dots,n}}\operatorname{sign(\mathbf{p})}\prod_{i=1}^{n}v_{ip_{i}}} 
\end{aligned}
$$

The reason why we get from $\displaystyle\sum_{j_{1}=1}^{n}\sum_{j_{2}=1}^{n}\dots\sum_{j_{n}=1}^{n}$ to $\displaystyle \sum_{\substack{p\text{ is a permuation of}\\\text{of }1,2,\dots,n}}$ is because the first sum goes over every sequence with length $n$ where the elements are any number from $1$-$n$ but as any volume with a repeated vector is zero we only consider the subset of those sequences where every element is unique which is the permutations of $1,2,\dots,n$.

Now instead of the function taking multiple vectors as input we have the function call it $\det A$ where $A$  is an $n\times n$ matrix with column vectors $\vec{v}_{1},\vec{v}_{2},\dots ,\vec{v}_{n}$.
#### Recursive Formula
Using the Leibniz formula we can derive a recursive formula. Given an $n\times n$ matrix $A$ $$\det A=\sum_{i=1}^{n}a_{1i}\det(A_{1i})=\sum_{j=1}^{n}a_{j1}\det(A_{j1})$$
**Proof**
*Note that in this proof subscripts are flipped e.g. $v_{ij}$ is the $j$th element of the $i$th column vector as we are emphasising **column** vectors but it doesn't matter as the determinant is constant under transpose.*

We will go through every permutation by going through every case where $p_{1}=1$ then $p_{1}=2$ up to $p_{1}=n$. When considering the case $p_{1}=k$ ($k$ has been removed from $1,2,\dots,n$) we will rename the remaining numbers/index to be $\rho^{k}_{i}$ from $1,2,\dots, n-1$ and rename the remaining vectors elements $\vec{w}_{k}$. So the remaining elements are denoted as $v_{ip_{i}}\to(w_{k})_{i\rho^{k}_{i}}$. 

For every even $k$ we pick up a minus sign formally $\operatorname{sign}(\mathbf{p})=\begin{cases}-\operatorname{sign}(\mathbf{\rho^{k}})&k\text{ even}\\ \operatorname{sign}(\mathbf{\rho^{k}})&k\text{ odd}\end{cases}$.
The reason why is because for any permutation $\mathbf{p}$ keep $p_{1}$ in place then do all the required swaps to get the remaining elements in order then you can move $p_{1}$ to the right place by repeatedly swapping adjacent elements to move $p_{1}$ further in the sequence. If $p_{1}$ is odd this requires an even amount of swaps not affecting the sign but if $p_{1}$ is even this requires an odd amount of swaps flipping the sign.

Putting this together we get 
$$\begin{aligned}
&\det A\\
&=v_{11}\left(\sum_{{\substack{\rho^{1}\text{ is a}\\ \text{perm of}\\\text{of }[1,n-1]}}}\operatorname{sign}(\mathbf{\rho}^{1})\prod_{i=1}^{n-1}(w_{1})_{i\rho^{1}_i}\right) -v_{12}\left(\sum_{{\substack{\rho^{2}\text{ is a}\\ \text{perm of}\\\text{of }[1,n-1]}}}\operatorname{sign}(\mathbf{\rho}^{2})\prod_{i=1}^{n-1}(w_{2})_{i\rho^{2}_i}\right)+\dots+(-1)^{n}v_{1n}\left(\sum_{{\substack{\rho^{n}\text{ is a}\\ \text{perm of}\\\text{of }[1,n-1]}}}\operatorname{sign}(\mathbf{\rho}^{n})\prod_{i=1}^{n-1}(w_{n})_{i\rho^{n}_i}\right)
\\
&=\sum_{j=1}^{n}v_{1j}\sum_{{\substack{\rho^{j}\text{ is a}\\ \text{perm of}\\\text{of }[1,n-1]}}}\operatorname{sign}(\mathbf{\rho}^{j})\prod_{i=1}^{n-1}(w_{j})_{i\rho^{k}_{i}} 
\\
&=\sum_{j=1}^{n}v_{1j}\det(A_{1j})
\end{aligned}
$$
The trick is that we can notice that each term $\displaystyle\sum_{{\substack{\rho^{j}\text{ is a}\\ \text{perm of}\\\text{of }[1,n-1]}}}\operatorname{sign}(\mathbf{\rho}^{j})\prod_{i=1}^{n-1}(w_{j})_{i\rho^{k}_{i}}$ has the same format as a determinant but with dimension $(n-1)\times(n-1)$ and if we pay attention to the fact we have removed the first column and the $j$th row we realise it is the determinant of the minor $A_{1j}$.
