---
tags:
  - maths/trigonometry
---
# Unit Circle and Definitions
[Animated Unit Circle](https://www.youtube.com/watch?v=Dsf6ADwJ66E)
![[Unit-Circle.jpg|400]]
Pick an angle $\theta$ and then draw a line from the origin rotated $\theta\text{ rad}$ from the positive x-Axis. This line intersects the unit circle at a point $A: (x_{a},y_{a})$.
Then we define $\sin(\theta)=y_{a}$ and $\cos(\theta)=x_{a}$.
Next draw a line tangent to the circle at $A$ this will intersect the x-Axis at a point $B:(x_{b},0)$ and it will interest the y-Axis at $C: (0,y_{c})$.
We then define the following functions: $\sec(\theta)=x_{b}, \ \csc(\theta)=y_{c}, \ \tan(\theta)=|AB|, \ \cot(\theta)=|AC|$.

*Caveat that $\tan\theta$ and $\cot\theta$ are signed length with them being positive when $\sin\theta,\cos\theta$ have the same sign and negative otherwise. This is because $\tan\theta$ is defined as $\displaystyle\frac{\sin\theta}{\cos\theta}$ and $\displaystyle\cot\theta=\frac{1}{\tan\theta}$ this is better seen with another (technically ore accurate) rearrangement of the unit circle, but that one does not as clearly show the idea of co- functions and how they are related to their counterpart.*

Notice that this forms $3$ ***similar*** *right-angled* triangles, one with sides $1,\sec(\theta),\tan(\theta)$ with perpendicular being $\sin\theta$. *(call this triangle $J$)*
Another with sides $1,\csc(\theta),\cot(\theta)$ and perpendicular height $\cos(\theta)$. This gives rise to the names of the $co$ functions as they represent the same thing but on the triangle with angle $90-\theta$ at the origin vs. the triangle with angle $\theta$ at the origin. (*we will call this "co" angle* $\theta'=90-\theta$, *and call the triangle $K$*)
Finally a smaller triangle triangle can be formed inside the unit circle with radius $1$ as hypotenuse with other lengths $\sin(\theta),\cos(\theta)$. (*call this triangle $L$*)
***
# Identities
Using these triangles we can derive important relations. 
First using similarity of $L$ and $K$ we derive that $\displaystyle \frac{\sin\theta}{\cos\theta}=\frac{\tan\theta}{1}=\tan\theta$. 
We can also derive the reciprocal relationships $$\csc\theta\equiv\frac{1}{\sin\theta}\quad \cot\theta\equiv\frac{1}{\tan\theta}\quad\sec\theta\equiv\frac{1}{\cos\theta}$$
Using Pythagoras we can also derive the following $$\cos^{2}\theta+\sin^{2}\theta\equiv{1}\quad 1+\tan^{2}\theta\equiv \sec^{2}\theta\quad \cot^{2}\theta+1\equiv \csc^{2}\theta$$

***
# Function Properties and Graphs 
## $\sin(x)$
1. Domain of $x \in  \mathbb{R}$
2. Range of $-1 \le y \le 1$
3. Period of $2 \pi$ radians
![[Sin-Gaph.png|600]]
### $\arcsin(x)$
1. Domain $-1 \le x \le 1$, *This restricted domain exists because $\sin(x) < -1, \sin(x)  1$ has no solutions for $x \in \mathbb{R}$*
2. Range is $-\frac{\pi}{2} \le y \le \frac{\pi}{2}$,  *This range is due to the one-to-one mapping to only the principal root to ensure the function exists*
![[Arcsin-Graph.png|200]]
## $\cos(x)$
1. Domain of $x \in  \mathbb{R}$
2. Range of $-1 \le y \le 1$
3. Period of $2 \pi$ radians
![[Cosine-Graph.png|600]]
### $\arccos(x)$
1. Domain $-1 \le x \le 1$, *This restricted domain exists because $\cos(x) < -1, \cos(x)  1$ has no solutions for $x \in \mathbb{R}$*
2. Range is $-\frac{\pi}{2} \le y \le \frac{\pi}{2}$,  *This range is due to the one-to-one mapping to only the principal root to ensure the function exists*
![[Arccos-Graph.png|200]]
## $\tan(x)$
1. Domain $x \in \mathbb{R}, x \ne \frac{(2n+1)\pi}{2}, n \in \mathbb{Z}$
2. Range $y \in \mathbb{R}$
3. Period of $\pi$ radians
![[Tangent-Graph.png|600]]
### $\arctan(x)$
1. Domain $x \in \mathbb{R}$
2. Range $\frac{-\pi}{2} \le y \le \frac{\pi}{2}$
3. Non-Periodic
 ![[Arctan-Graph.png|600]]
## $\csc(x)$
1. Domain $x \in \mathbb{R}, x \ne \frac{(2n+1)\pi}{2}, n \in \mathbb{z}$
2. Range of $y \ge 1 , y \le -1$
3. Period of $2 \pi$ radians
![[Cosecant-Graph.png|600]]
## $\sec(x)$
1. Domain $x \in \mathbb{R}, x \ne \frac{(2n+1)\pi}{2}, n \in \mathbb{z}$
2. Range of $y \ge 1 , y \le -1$
3. Period of $2 \pi$ radians
![[Secant-Graph.png|600]]
## $\cot(x)$
1. Domain $x \in \mathbb{R}, x \ne n\pi, n \in \mathbb{Z}$
2. Range $y \in \mathbb{R}$
3. Period of $\pi$ radians
![[Cotangent-Graph.png|600]]

***

# Addition Formulae
## Inside Addition
1. $\sin(A \pm B)\equiv \sin A \cos B \pm \sin B \cos A$
2. $\cos(A\pm B)\equiv cos A\cos B\mp\sin A\sin B$
3. $\tan(A\pm B)=\displaystyle \frac{\tan A\pm\tan B}{1\mp\tan A\tan B}\quad (A\pm B=(k+\frac{1}{2})\pi)$
## Outside Addition
1. $\displaystyle \sin A+\sin B=2\sin\frac{A+B}{2}\cos\frac{A-B}{2}$
2. $\displaystyle\sin A-\sin B=2\cos\frac{A+B}{2}\sin\frac{A-B}{2}$
3. $\displaystyle\cos A+\cos B=2\cos\frac{A+B}{2}\cos\frac{A-B}{2}$
4. $\displaystyle\cos A-\cos B=-2\sin\frac{A+B}{2}\sin\frac{A-B}{2}$
5.  $\displaystyle a\sin(x) + b\cos(x)\equiv R_{s}\sin(x + \alpha)\text{ or } R_{c}\cos(x + \beta)$ 
$$R_{s}=\operatorname{sign}(a)*\left(\sqrt{a^{2}+b^{2}}\right)\quad \alpha=\arctan\left(\frac{b}{a}\right)$$$$R_{c}=\operatorname{sign}(b)*\left(\sqrt{a^{2}+b^{2}}\right)\quad \alpha=-\arctan\left(\frac{a}{b}\right)$$
***
# T-Formulae
## Definitions/Equations
The t-formulae are formulae for the trigonometric functions using the substitution $t = \tan \left(\frac{\theta}{2}\right)$ to obtain the following formulae:

$$ 
\begin{aligned}
&\tan \left(\frac{\theta}{2}\right) = t  && \tan \theta = \frac{2t}{1-t^2}\\
& \sin \left(\frac{\theta}{2}\right) = \frac{t}{\sqrt{1+t^2}} && \sin \theta = \frac{2t}{1+t^2}\\
&\cos \left(\frac{\theta}{2}\right) = \frac{1}{\sqrt{1+t^2}} && \cos \theta = \frac{1-t^2}{1+t^2}
\end{aligned}
$$

## Solving Equations
To solve questions, you need to find $\tan \left(\frac{\theta}{2}\right)$ if not directly given, then use the t-formula for what you're trying to find. You generally find $\tan \left(\frac{\theta}{2}\right)$ 
 Finding $\sin \left(\frac{\theta}{2}\right)$ or $\cos \left(\frac{\theta}{2}\right)$ *it will either be given in the question or the reciprocal function* Then using the identity $\sin^2 + \cos^2 = 1$ to obtain the other function *Either sine or cosine* then choose the correct sign for the square root based on boundary conditions for $\theta$ in the problem. Then use $\tan (\theta) = \frac{\sin(\theta)}{\cos(\theta)}$
## Weierstrass Substitution For Integrals
You can use the t-formulae as a substitution for integrals it should be self explanatory from there but a key fact to remember is $$dx = \frac{2}{1+t^2}dt$$ 
