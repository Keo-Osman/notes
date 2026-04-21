---
tags:
  - maths/complex-numbers
---
# Definition
A complex number is a number that is written as $a+b i$ where $i$ is the imaginary unit defined as $\sqrt{-1}$ and $a, b \in \mathbb{R}$. *The set of all complex numbers is written as $\mathbb{C}$*, it is an extension if *The Real Numbers*
Complex numbers have lots of applications as they are helpful when describing waves due to their connection with the [[Trigonometric Functions]]. They are also used in physics due to their ability to describe rotations and oscillations in 2 Dimensions neatly. 

***
# The Complex Conjugate
For $z = a+bi$,  $\bar{z} = a-bi$
$z+\bar{z}$ is always real as the imaginary parts cancel so $z+\bar{z}=2 a$
$z\cdot\bar{z}$ is also always real as it’s a difference of two squares
$$(a+b i)(a-b i)=a^2-(b i)^2=a^2-\left(b^2 i^2\right)=a^2-\left(-b^2\right)=a^2+b^2$$
Also the conjugation is multiplicative and additive meaning $\overline{z_{1}z_{2}} = \overline{z_{1}}\cdot \overline{z_{2}}$, and $\overline{z_{1}+z_{2}}= \overline{z_{1}}+\overline{z_{2}}$ which can be trivially proved by expanding them as $a+bi$.
***
# Forms of Complex Numbers

## Regular $a + bi$
### Basic operations
$$(a+b i) \pm(c+d i)=(a+c) \pm(b+d) i$$
$$(a+b i)(c+d i)= a c+(b c) i+(a d) i+b d i^2 = (a c-b d)+(b c+a d)i$$
$$\frac{a+b i}{c+d i}=\frac{a+b i)(c-d i)}{(c+d i)(c-d i)} = \frac{a c+b d}{c^2+d^2}+\left(\frac{b c-a d}{c^2+d^2}\right)i
$$

## Modulus Argument Form $r(\cos \theta+i \sin \theta)$ 
Complex numbers can also be written with [[Trigonometric Functions]] in the form $r(\cos \theta+i \sin \theta)$ where $\theta=\operatorname{arg}(z)$ and $r=|z|$.
The **modulus** of a complex number $z$ is written as $|z|$ and it is is defined as $\sqrt{a^2+b^2}$ where $z=a+b i$. $|z|$ is geometrically represented as the distance from the origin to $z$ on the complex plane.
The **argument** $z$ *written as $arg(z)$* is the angle $\theta$ such that $\tan \theta=\frac{y}{x}$ - it is given in radians typically given in the range $\pi -\pi<\theta \leq \pi$ *(This is called the principal argument)* This angle represents the angle rotation from the $x$-axis
### Basic Operations
#### Multiplication
$$\left|z_1 z_2\right|=\left|z_1\right| \times\left|z_2\right| \quad \arg (z_1 z_2)=\operatorname{arg}(z_1)+\operatorname{arg}(z_2)$$
$$
\begin{aligned}
\underline{Proof} \\
z_1 z_2 & =r_1\left(\cos \theta_1+\mathrm{i} \sin \theta_1\right) \times r_2\left(\cos \theta_2+\mathrm{i} \sin \theta_2\right) \\
& =r_1 r_2\left(\cos \theta_1+\mathrm{i} \sin \theta_1\right)\left(\cos \theta_2+\mathrm{i} \sin \theta_2\right) \\
& =r_1 r_2\left(\cos \theta_1 \cos \theta_2+\mathrm{i} \cos \theta_1 \sin \theta_2+\mathrm{i} \sin \theta_1 \cos \theta_2+\mathrm{i}^2 \sin \theta_1 \sin \theta_2\right) \\
& =r_1 r_2\left(\cos \theta_1 \cos \theta_2+\mathrm{i} \cos \theta_1 \sin \theta_2+\mathrm{i} \sin \theta_1 \cos \theta_2-\sin \theta_1 \sin \theta_2\right) \\
& =r_1 r_2\left(\left(\cos \theta_1 \cos \theta_2-\sin \theta_1 \sin \theta_2\right)+\mathrm{i}\left(\sin \theta_1 \cos \theta_2+\cos \theta_1 \sin \theta_2\right)\right) \\
& =r_1 r_2\left(\cos \left(\theta_1+\theta_2\right)+\mathrm{i} \sin \left(\theta_1+\theta_2\right)\right)
\end{aligned}$$

#### Division
$$\left|\frac{z_1}{z_2}\right|=\frac{|z_1|}{|z_2|} \quad \operatorname{arg}\left(\frac{z_1}{z_2}\right)=\operatorname{arg}(z_1)-\operatorname{arg}(z_2)$$
$$
\begin{aligned}
\underline{Proof} \\
\frac{z_1}{z_2} & =\frac{r_1\left(\cos \theta_1+\mathrm{i} \sin \theta_1\right)}{r_2\left(\cos \theta_2+\mathrm{i} \sin \theta_2\right)} \\
& =\frac{r_1\left(\cos \theta_1+\mathrm{i} \sin \theta_1\right)}{r_2\left(\cos \theta_2+\mathrm{i} \sin \theta_2\right)} \times \frac{\left(\cos \theta_2-\mathrm{i} \sin \theta_2\right)}{\left(\cos \theta_2-\mathrm{i} \sin \theta_2\right)} \\
& =\frac{r_1\left(\cos \theta_1 \cos \theta_2-\mathrm{i} \cos \theta_1 \sin \theta_2+\mathrm{i} \sin \theta_1 \cos \theta_2-\mathrm{i}^2 \sin \theta_1 \sin \theta_2\right)}{r_2\left(\cos \theta_2 \cos \theta_2-\mathrm{i} \cos \theta_2 \sin \theta_2+\mathrm{i} \sin \theta_2 \cos \theta_2-\mathrm{i}^2 \sin \theta_2 \sin \theta_2\right)} \\
& =\frac{r_1\left(\left(\cos \theta_1 \cos \theta_2+\sin \theta_1 \sin \theta_2\right)+\mathrm{i}\left(\sin \theta_1 \cos \theta_2-\cos \theta_1 \sin \theta_2\right)\right)}{r_2\left(\cos ^2 \theta_2+\sin ^2 \theta_2\right)} \\
& =\frac{r_1}{r_2}\left(\cos \left(\theta_1-\theta_2\right)+\mathrm{i} \sin \left(\theta_1-\theta_2\right)\right)
\end{aligned}$$
## Exponential Form $re^{i\theta}$
Every complex number can be written in the form $re^{ i\theta }$ where $r=|z|, \ \theta=\operatorname{arg}z$. Complex exponentiation is defined using the Taylor series of $e^{x}$ as it only contains integer powers of $x$ which can be extended for complex inputs $z$. 
### Derivation
**Rigorous proof**
Using the [[Series Approximations#Taylor Series|Taylor Series]]
$$
\begin{aligned}
e^{ i\theta} & =1+\mathrm{i}\theta+\frac{(\mathrm{i}\theta)^{2}}{2!}+\frac{(\mathrm{i}\theta)^{3}}{3!}+\frac{(\mathrm{i}\theta)^{4}}{4!}+\frac{(\mathrm{i}\theta)^{5}}{5!}+\frac{(\mathrm{i}\theta)^{6}}{6!}+\ldots \\
 & =1+\mathrm{i}\theta+\frac{\mathrm{i}^{2}\theta^{2}}{2!}+\frac{\mathrm{i}^{3}\theta^{3}}{3!}+\frac{\mathrm{i}^{4}\theta^{4}}{4!}+\frac{\mathrm{i}^{5}\theta^{5}}{5!}+\frac{\mathrm{i}^{6}\theta^{6}}{6!}+\ldots \\
 & =1+\mathrm{i}\theta-\frac{\theta^{2}}{2!}-\frac{\mathrm{i}\theta^{3}}{3!}+\frac{\theta^{4}}{4!}+\frac{\mathrm{i}\theta^{5}}{5!}-\frac{\theta^{6}}{6!}+\ldots \\
 & =\left(1-\frac{\theta^{2}}{2!}+\frac{\theta^{4}}{4!}-\frac{\theta^{6}}{6!}+\ldots\right)+\mathrm{i}\left(\theta-\frac{\theta^{3}}{3!}+\frac{\theta^{5}}{5!}-\ldots\right) \\
\\ 
&= \cos\theta + i\sin\theta
\end{aligned}
$$
**Intuition**
$e^{ x }$ is the unique function such that $\displaystyle\frac{d}{dx}f(x)=f(x)$ with $f(0)=1$ this relation means that the *"velocity"* of $e^{kx}$ is proportional to itself.  
Considering $e^{ix}$ we get that's it derivative is $ie^{ix}$ meaning it's velocity is a $90\degree$ rotation of itself. So starting at $e^{0}=1$ it's velocity is always tangent to it which describes circular motion so it can be described by travelling around a unit circle and hence it can described by trig functions. 
### Properties
We can also *split* the power into multiplication similar to real exponentiation as $e^{a+bi}=e^{a}\cdot e^{bi}$.
**Proof**
1. Using Taylor series we get $e^{ a+bi }=1+(a+bi)+ \frac{(a+bi)^{2}}{2!}+\cdots$ as well as $e^{a}\cdot e^{bi}=\left( 1+a+\frac{a^{2}}{2!}+\cdots \right)\left( 1+bi+\frac{(bi)^{2}}{2!}+\cdots \right)$. We can prove they are equivalent by comparing coefficients.
2. For $a^{x}b^{y}$ in $e^{a+bi}$ we can only get these terms from the expansion of $(a+bi)^{x+y}$ which itself also has a coefficient of $\frac{1}{(x+y)!}$. The coefficient from the expansion is  $(i)^{y}\cdot \binom{x+y}{y}$ - *the $i^{y}$ comes from the $(bi)^{y}$*. Putting them together we get $\displaystyle i^{y}\frac{\binom{x+y}{y}}{(x+y)!}= \frac{i^{y}}{x!y!}$.
3. With $e^{a}\cdot e^{bi}$ we can only get $a^{x}b^{y}$ by picking the $a^{x}$ term and the $b^{y}$ term in the expansion. The $a^{x}$ has a coefficient of $\frac{1}{x!}$ and the $b^{y}$ has a coefficient of $\displaystyle \frac{i^{y}}{y!}$ which when multiplied gives the same coefficient of $\displaystyle \frac{i^{y}}{x!y!}$ since every term has the same coefficient they are equal $\quad \square.$

Following this we can easily see that $e^{z+w}=e^{z}\cdot e^{w}$
**Proof**
1. Let $z=a+bi, \ w=c+di$ then $e^{z+w}=e^{(a+c)+(b+d)i}=e^{a+c}\cdot e^{(b+d)i}=e^{a}\cdot e^{bi}\cdot e^{c}\cdot e^{di}=e^{z}\cdot e^{w} \quad \square$

### Complex Logarithm
Using this exponential definition we can extend the domain of $\ln$ to $\mathbb{C\setminus}\{0\}$. Using the defining property that $\ln e^{x}=x$.
Since we have extended $e^{ x }$ to $\mathbb{C}$ we can simply define $\ln e^{z}=z$ and since every complex number can be written in this form *except* $0$ we can extend it. Writing a complex number in the form $re^{i\theta}=e^{ \ln r+i\theta }$ we get $\ln re^{i\theta}=\ln r+i\theta$ and using the fact that $r=|z|, \ \theta=\operatorname{arg}z$ we get the full definition that $$\ln z=|z|+i\operatorname{arg}(z) $$
However since $e^{z}$ is *not* bijective over $\mathbb{C}$ a proper inverse, $\ln$ can't exist. This comes down to the fact that $e^{z}\equiv e^{z+2k\pi}, k\in \mathbb{Z}$ so $\operatorname{arg}z$ is not unique. Typically this is dealt with by simply restricting $\operatorname{arg}z$ to $(-\pi,\pi]$ however other *branches* are valid it is just dependant on context. 
We can also deal with $\log_{k}z$ by simply using the change of base formula to use $\ln z$. This still works as $z^{w}=e^{w\ln z}$ still holds.
*Note that always restricting to the principal branch doesn't work. For example* $\log_{-2}(-8)=3$ *does not come from the principal branch. In fact it comes from a mixture of two different branches - due to there being two $\ln$ from using the change of base. So in general it is best to not restrict to a branch and view $\log z$ as it's whole set of possible inputs.*
### General Complex Exponentiation
Given two complex numbers $z=a+bi, \ w=c+di$ we can compute $z^{w}$ as $e^{w\ln z}$.
***
# De Moivre's Theorem
$$\begin{matrix}
(r(\cos \theta + i \sin \theta))^n \equiv r^n(\cos n\theta + i \sin n\theta)
\\
\forall n  \in \mathbb{Z}
\end{matrix}
$$
Proved simply by using induction and using the rules how $\operatorname{arg}$ adds/subtracts and $r$ multiplies/divides.

It can be used to find [[Trigonometric Functions#Identities|Trigonometric Identities]] by applying De Moivre's Theorem and the binomial expansion of $(\cos\theta + i\sin\theta)^n$ to express $\cos n\theta$ in terms of powers of $\cos \theta$ and same for $\sin \theta$
You can also use the following identities$$z=\cos\theta + i\sin\theta\Rightarrow\qquad\begin{aligned}
 &  z+\frac{1}{z}=2\cos\theta\quad z^{n}+\frac{1}{z^{n}}=2\cos n\theta \\
 &  z-\frac{1}{z}=2i\sin\theta\quad z^{n}-\frac{1}{z^{n}}=2i\sin n\theta
\end{aligned}$$to find other identities by binomially expanding the function in terms of $z$ and exponentiating the trig function. These identities themselves can be proved using De Moivre's Theorem.

***
# Roots of Complex Numbers
## $z^n = w$
**To Solve** $z^n = w$ $\quad z, w \in \mathbb{C}, n \in \mathbb{N}$, $z, w \neq 0$
1. Assume $z$ has the form $r(\cos \theta + i \sin \theta))$ so by **De Moivre's Theorem** $z^n = r^n(\cos (n\theta + 2k\pi) + i \sin (n\theta+2k\pi))$
2. Compare the modulus to solve for $r$
3. Then plug in $k= 1, 2, \dots, n$ and solve for $\theta$
## Roots of Unity
The roots of unity are the solutions to $z^n = 1$, 
If $n$ is a positive integer there is an $n$th root of unity *s.t* $1, \omega, \omega^2,...,\omega^{n-1}$ are the roots of unity
The roots of unity sum to 0 and **form the vertices of a regular $n$-gon**
If $z_1$ is one root of the equation $z^n = s$ then the roots of $z^n =s$ are given by $z_1, z_1\omega, z_1\omega^2,...,z_1\omega^{n-1}$