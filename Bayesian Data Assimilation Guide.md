This guide isn't complete yet I will keep updating it adding new information about the other filters/techniques and maybe expand on what I've already done but for now this should be enough to get you up to understanding the problem and the Kalman filter (KF) in the linear all gaussian case as well as ensemble Kalman filter (EnKF).

***
# The Problem We are Trying to Solve
We are trying to model a *dynamic* system - a system that evolves over time - and make predictions about state of the system. This could be anything really, such as the weather, some position and velocity of an object, a population over time, volatility of a stock. Just anything that *changes over time*. We are looking specifically at dynamic systems that are governed by/can be modelled with *differential equations*. However all these techniques apply to dynamic systems that are modelled without an ODE.

The problem is that we don't know the *exact* state of the system. We can make observations/measurements but these aren't exact as they have error/noise. (*This could be due to a sensor only having finite precision*). So we can't completely trust our observations, and if we are slightly off this error can compound over time and the predictions we make could become wildly off from the true value. 

Another problem that we have to deal with is that our model may not be perfect and/or the system may be *stochastic* (random/non-deterministic). Even if we did know the **exact** state of the system at some point our model might not be able to perfectly predict the true value and again this error may compound over time. This could be due to the fact there are external conditions we can't account for or that the system is too complicated to model every single part so we simplify a bit. E.g. we can't model every single particle in a system. It is too complicated to deal with, we don't have enough computation power and we can't make measurements of the whole system.

# The Solution / Core Loop of Bayesian Data Assimilation
Instead of the model making predictions of the single value of the state, We model the state as a *random variable* and keep track of the *probability distribution*. That is instead of predicting that the current state of the system is a specific value we talk about what the probability that the true state value falls within some region is. And we take the mean of this random variable to be our guess for the true state. This also allows us to model how confident we are in the guess.

The two core functions of any model is
1. How we take our current distribution estimate and get a new distribution of the state at some later time. We will refer to this as the **propagation** step.
2. When we receive an observation of the state (may not be of every variable we are trying to model), How do we update a distribution. *To what extent do we prefer either the noisy observation or our noisy prediction more? How do we combine these two to get a more accurate prediction of the state?*. We will refer to this as the **update** step

***
# Prerequisites
## Brief Note on Vectors, Matrices and Linear Algebra
### Vectors
The system that we are trying to model will have more than 1 variable. Instead of treating them as separate variables we group together as a *vector*. 
A vector is not *"something with direction and magnitude"*. This only applies to certain *vector spaces* that have geometric meaning but vectors are not inherently geometric objects. In the case of our project the vectors we are dealing with are just the most natural mathematical way to group things and they do not have any geometric meaning/properties unless specified.

For the purpose of the project a vector we will only be talking about vectors in $\mathbb{R}^{n}$ so they can be thought of as simply a list of real numbers. In code this will simply be a 1D array of floats *(more specifically an `np.array`)* And the *dimension* of the vector is just the length of the list. The set of $n$ dimensional vectors is denoted as $\mathbb{R}^{n}$. For a vector $\mathbf{x}$ with 5 variables we can say that $\mathbf{x}  \in \mathbb{R}^{5}$.
### Matrices
Matrices are a two dimensional grid of numbers *(The actual definition is a bit more abstract than this but this definition is enough for the project)*. Generally this grid is a square but can be non-square although those only come up very briefly in the project with the *observation map*. We can have an $m\times n$ matrix ($m$ rows, $n$ columns) and we denote the set of these matrices as $\mathbb{R}^{m\times n}$. *(Not an actual multiplication in the "exponent")*
However it is often better to think of a matrix as a list of vectors. An $m\times n$ matrix can either be interpreted as $m$ different $n$ dimensional *row* vectors or $n$ different $m$ dimensional *column* vectors.
In code this will be a 2D array of floats again more specifically an `np.array`.

In this project matrices are used for three purposes
1. As a function on vectors - focus on column vectors.
2. A way to represent systems of equations - focus on row vectors.
3. The covariance matrix - just a grid of numbers. It's matrix properties and the properties of it's row and column vectors aren't really relevant.

For the project knowing much about matrices as functions or systems of equations isn't too vital but it is helpful in some cases. The most common occurrence of matrices is the covariance. Matrices as functions on vectors comes up quite a bit as the *state transition matrix* but depending on the system we are modelling it is not always possible. Representing systems of equations with matrices is only applicable with a very specific type of equation system and for most cases won't work.
### *"Linear"*
The word linear will come up a few times in this project. This does not refer to a linear polynomial $y=mx +c$. It refers to a linear function which is a function $f: V\to W$ ($V, W$ are vector spaces) that satisfies
1. $f(x+y) = f(x)+f(y), \quad\forall x, y \in V$
2. $f(cx) = cf(x), \quad\forall x \in V, c \in \mathbb{R}$
This definition isn't really too important all you really need to know is that linear refers to a *"nice"* type and will lead to simpler properties. A linear function that can be represented as a matrix. 
If a linear function's domain and codomain are the same vector space. Such as $f: \mathbb{R}^{3}\to \mathbb{R}^{3}$ then $f$ is a ***linear transform***

Annoyingly $f(x) = mx + c, c \neq0$ isn't actually linear with this definition it's *affine (linear map + translation)*. These terms are often used interchangeably as they have similar properties and many times if we say linear we also include affine.
### Matrices as functions
I won't go into too much detail as it's not really necessary but matrices are *linear transforms* on vectors. Because of the properties of linear functions they can be determined, by where the *basis vectors* end up after the transformation. For $\mathbb{R}^{n}$ these are the unit vectors $\begin{pmatrix}1 \\ 0 \\ \vdots \\ 0\end{pmatrix}, \begin{pmatrix}0 \\ 1 \\ \vdots \\ 0\end{pmatrix},\dots,\begin{pmatrix}0 \\ 0 \\ \vdots \\ 1\end{pmatrix}$
A matrices column vectors are where each of the basis vectors end up after the transform.
Matrix-Vector multiplication is how these functions are applied. E.g. $A \in \mathbb{R}^{n \times n}, \mathbf{v} \in \mathbb{R}^{n}$ then $A\mathbf{v}$ is the result of applying the linear transform $A$ on the vector $\mathbf{v}$. And matrix multiplication is function composition so if $A \in \mathbb{R}^{n \times n}, B \in \mathbb{R}^{n \times n}$ then $AB$ is a new matrix and is the composition of functions of $A, B$. Like regular functional composition it is read right to left. We apply $B$ first then $A$.

### Matrices as Systems of Equations
The linear system of equations:
$$
\begin{aligned} a_{1}x + b_{1}y + c_{1}z& = v_{1} \\
a_{2}x + b_{2}y + c_{2}z& = v_{2} \\ 
a_{3}x + b_{3}y + c_{3}z& = v_{3}
\end{aligned}
$$
Is equivalent to this matrix equation
$$
\begin{aligned}
\begin{pmatrix} a_{1} & b_{1} & c_{1} \\ a_{2} & b_{2} & c_{2} \\ a_{3} & b_{3} & c_{3} \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} &= \begin{pmatrix} v_{1} \\ v_{2} \\ v_{3} 
\end{pmatrix} 
\\
\end{aligned}$$
Notice how we have just taken each row of coefficients and put the as a row vector.
If we have a linear system of equations $A\mathbf{x} = \mathbf{v}$ we can solve it by *inverting* the matrix. to get $\mathbf{x}=A^{-1}\mathbf{v}$. 
In code you should try to not compute inverses directly and instead opt to use solve.
If calculating $A^{-1}B$ or $A^{-1}\mathbf{v}$ use `np.linalg.solve(A, B)` or likewise `np.linalg.solve(A, v)`. If you are computing $AB^{-}$ then use `np.linalg.solve(B.T, A.T).T`
Although `np.linalg.inv(A)` does it exist you should never really use it, always prefer `np.linalg.solve` as it has better performance and stability.

### Transpose 
If we have a matrix then we can compute it's $A^{T}$ and it is just swapping the rows and columns of a matrix. It turns an $m\times n$ matrix into a $n\times m$ matrix. More formally $A^{T}_{ij}=A_{ji}$ where $M_{ij}$ is the element in the $i$th row and $j$th column. It also applies to row or column vectors by treating them as $n\times 1$ or $1 \times n$ matrices.

You will most commonly see it in matrix multiplications with forms $ABA^{T}$ this is the matrix equivalent of scaling by square e.g. $a^{2}b$.
You will also see with a vector $\mathbf{v}$, the product $\mathbf{v}\mathbf{v}^{T}$ this is a generalisation of $v^{2}$ in the scalar case. For an $n$ dimensional vector it produces an $n\times n$ matrix.

## Differential Equations
There are different types: Ordinary differential equations (ODEs), Partial (PDEs) and stochastic (SDEs). We will mainly be looking at ODEs for now.
An ODE is an equation consisting of derivatives (and higher order derivatives e.g. second and third derivative - *however I haven't dealt with any of these in the context of Bayesian data assimilation yet*)
If we have an ODE in multiple variables such as the Lorenz equations $$ \begin{aligned}\frac{dx}{dt}&=\sigma(y-x)\\\frac{dy}{dt}&=x(\rho-z)-y\\\frac{dz}{dt}&=xy-\beta z\end{aligned} $$
We can group the variables into a vector $\mathbf{v} = \begin{pmatrix}x \\ y \\ z\end{pmatrix}$ and write the equation as $$\frac{d\mathbf{v}}{dt} = \mathbf{f}(\mathbf{v}, t)$$ where $f$ is a vector function e.g. $f:\mathbb{R}^{3}\to\mathbb{R}^{3}$ $$f\begin{pmatrix}
x \\
y \\
z
\end{pmatrix} = \begin{pmatrix}
\sigma(y-x) \\
x(\rho - z) - y \\
xy-\beta z
\end{pmatrix}$$
And if the set of equations is *linear* then we can write the function as a matrix and get $\frac{d\mathbf{v}}{dt} = A\mathbf{v}$.

For this project we will be discretising the ODE meaning instead of looking at the whole continuous solutions we care about the solution at discrete points of time. For the most part we won't really be solving ODEs analytically (exactly) we will be using approximations using methods like Euler's method or RK4, DOP853. The exception being linear ODEs where we will use matrix exponentials.

## Continuous Random Variables
You don't need to learn all of this in detail you just need to understand at a high level what a random variable and a probability distribution is and what variance/covariance is. We generally don't really care about evaluating any actual probabilities using integrals we just care about the distribution/random variable as a whole. 

### Definition
A continuous random variable is a random variable $X$ which can take any real value in an interval. For continuous random variables $\mathbb{P}(X=x) = 0 , \forall x \in \mathbb{R}$. Instead probabilities are defined over an interval e.g. for $a<b \in \mathbb{R}$ we consider $\mathbb{P}(a\leq x\leq b)$.

### Probability Density Function
In order to do this we have a ***probability density*** function $f_{X}(x)$ which satisfies
1. $f_{X}(x) \geq 0$
2. $\int_{a}^{b}f_{X}(x)dx = \mathbb{P}(a\leq x \leq b)$
3. $\int_{-\infty}^{\infty}f_{X}(x)dx = \mathbb{P}(-\infty\leq x \leq \infty) = 1$ *as total probability sums to $1$*

### Expected Value
The ***Expected Value*** denoted $\mathbb{E}[X]$ of $X$ is the mean value of $X$.
It is defined/found as $$\int_{-\infty}^{\infty}xf_{X}(x)dx$$
This comes from a generalisation of the discrete case $\mathbb{E}[X] = \sum x\mathbb{P}(X=x)$.

### Variance
***Variance*** is defined as $$\operatorname{Var}(X):=\mathbb{E}[(X-\mathbb{E}[X])^{2}]=\mathbb{E}[X^{2}]-(\mathbb{E}[X])^{2}$$
Since $\mathbb{E}[X]$ is the mean, $X-\mathbb{E}[X]$ is the deviation of $X$ from the mean. So variance is the *mean squared distance of $X$ from the mean*. It is a measure of **Spread** of the variable/data.

It has the properties that:
1. $\operatorname{Var}(X)\geq0, \operatorname{Var}(X) = 0 \iff X=c$.
2. Weight larger deviations more than small ones. *Hence the squaring.*

We then define standard deviation as $$\sigma = \sqrt{\operatorname{Var(X)} }$$
To go from squared distance to distance to get spread in the original units. *However it is **NOT** quite the average distance*. But we use it over $\mathbb{E}[\ |X-\mathbb{E}[X]| \ ]$ as the standard deviation has some nicer properties.

### Dealing with Multiple Random Variables
When we have multiple random variables we consider it as a vector in $\mathbb{R}^{n}$. E.g. $\mathbf{X} = (X_{1}, X_{2}, \dots, X_{n}) \in \mathbb{R}^{n}$. We can consider how individual variables in $\mathbf{X}$ are distributed by just consider $X_{i}$ as a single continuous random variable.
But also many concepts generalise nicely to $n$ variables at once.

#### Joint Probability Density Function
Again we don't really care about actual probabilities or the integral that much but for the sake understanding of how distributions work over a vector/multiple variables and completion:
A ***Joint Probability Density Function*** is $$f_{\mathbf{X}}(\mathbf{X}): \mathbb{R}^{n} \to \mathbb{R}, \quad f_{\mathbf{X}}\geq0$$ Where $$\forall A\subset \mathbb{R}^{n},\ \mathbb{P}(\mathbf{X}\in A) = \int_{A}f_{\mathbf{X}}(\mathbf{x})d\mathbf{x}$$
This $\int_{A}$ means to integrate over a region/volume. Basically it takes the case of an integral finding an *area* under a curve over a *range* and generalises it to finding the $n$-dimensional volume over a *region*. 
Thinking of it too geometrically isn't really helpful here though. It is just a generalisation of the idea that we can't assign individual probabilities for a continuous variable and we have to talk the probability that the variable lies within a given regions. Here a *region* is just the generalisation of a range into $n$ variables. 

## Bayes Theorem
$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$
**Terminology**
1. $P(A)$ is called the ***Prior***. This is what our current belief/hypothesis is about $A$ is *before* we see the data/evidence. It is our starting point.
2. $P(B|A)$ is called the ***Likelihood***. It is the probability of observing the evidence if our hypothesis was true. Effectively it measures how well our hypothesis/current beliefs are *compatible* with the evidence $B$ we just observed.
3. $P(B)$ is called the ***Evidence*** *or* ***Marginal Likelihood***. This is the probability of observing $B$ across *all* possible hypotheses. It serves as a normalisation constant. 
4. $P(A|B)$ is called the ***Posterior***. This is our updated belief in our hypothesis $A$ *after* accounting for the new evidence $B$.

*Note*
Often Bayes' Theorem is written as $\text{Posterior} \propto\text{Likelihood}\times\text{Prior}$ and we leave out the normalisation factor $P(B)$ (*the evidence*). As it is often hard to compute as well as the fact that we don't have to compute it if we have *conjugacy* that is the posterior PDF is in the same *family* as the prior PDF but just with new parameter values.

This theorem is the case for having one specific event but it can be easily generalised for a full probability distribution by replacing all the probability functions $P$ with a distribution $p$. *(Continuous distributions are always denoted by a lowercase $p$)*.

Bayes theorem allows us to take our current belief and obtain a more accurate belief by incorporating new evidence.

## Normal Distribution
The normal distribution is the most common distribution. It's PDF is: 
$$\begin{aligned}
\mathcal{N}(x;\mu, \sigma^{2})&=\frac{1}{\sqrt{2\pi\sigma^{2}}}\exp\left( -\frac{(x-\mu)^{2}}{2\sigma^{2}} \right)\quad&\text{(single dimensional)} \\
\mathcal{N}(\mathbf{x};\mu, \Sigma)&=\frac{\exp\left( -\frac{1}{2}(\mathbf{x}-\mu)^{T}\Sigma^{-1}(\mathbf{x}-\mu) \right)}{\sqrt{(2\pi)^{k}|\Sigma|}}\quad &(k\text{ dimensional})
\end{aligned} $$
*You don't need to know the actual function - it will only be used in some proofs. $\exp(x)$ just means $e^{ x }$*


All you need to know is that it is symmetric at the mean and the probability density exponentially decays as you move further from the mean. The (co)variance controls how fast this decays.
A key property that makes it useful in this context is that when applying a *linear (or affine) transform* to a normal distributed random variable, the resultant random variable will be normally distributed and the mean and the new covariance can be easily calculated exactly.

It is denoted as $\mathcal{N}(\mu, \Sigma)$ where $\mu$ is the mean and $\Sigma$ is the covariance matrix. If we are only dealing with one variable then the variance is the standard deviation squared so we write $\mathcal{N}(\mu, \sigma^{2})$
If we want the actual value (probability density) at a specific point we can write $\mathcal{N}(x;\mu,\Sigma )$ basically $x$ is the value we are plugging into the function $\mu, \Sigma$ are the parameters and the semi-colon just serves to separate them making it clear which is which.
The normal distribution is often called a *Gaussian*. These are the exact same things.

## Markov Assumption and Markov Chains
*"A Markov chain or Markov process is a stochastic process describing a sequence of possible events in which the probability of each event depends only on the state attained in the previous event"*.
This effectively mean if we have some random sequence of events such as moves in a game of chess the next state only depends on the current state meaning we don't care about how we got to our current state e.g. what moves were actually played in order to predict the next state.
Mathematically if we have a sequence of random variables that form a Markov chain $\mathbf{X}_{1},\mathbf{X}_{2},\dots ,\mathbf{X}_{n}$ then $\mathbb{P}(\mathbf{X}_{n+1}=x|\mathbf{X}_{1},\mathbf{X}_{2},\dots ,\mathbf{X}_{n})=\mathbb{P}(\mathbf{X}_{n+1}=x|\mathbf{X}_{n})$.
Explicitly the Markov assumption we use is that $p(\mathbf{x}_{t}|\mathbf{x}_{0:t-1})=p(\mathbf{x}_{t}|\mathbf{x}_{t-1})$ and for our observations $p(\mathbf{z_{t}}|\mathbf{x_{0:t}})=p(\mathbf{z}_{t}|\mathbf{x}_{t})$. This subscript $\mathbf{a}_{1:b}$ just means the sequence of $\mathbf{a}_{1},\mathbf{a}_{2},\dots ,\mathbf{a}_{b}$.

## Time Homogeneous
We will be only be looking at *time homogeneous* systems. All this means is that the system has no dependence on absolute time only on state. There is no absolute frame of reference only relative.
***
# Setup and Notation
## General Setup
The current state at time $t$ will be denoted as $\mathbf{x}_{t} \in \mathbb{R}^{n}$. It is a random vector. Although physically the **TRUE** state can only have one single value we represent our uncertainty by always viewing the true state as a random variable. This is the key *Bayesian* way of thinking. More precisely with KF we keep track of the *conditional distribution* $p(\mathbf{x}_{t}|\mathbf{z}_{1:t})$

If we are dealing with a system that does not evolve with time but just with discrete steps you may see $\mathbf{x}_{k}$ instead. Likewise any subscript $t$ may be seen as $k$ instead.

Our *estimate* for the state will be denoted as $\hat{\mathbf{x}}_{t}$. The hat ( $\hat{}$ ) on any variable indicates it is an *estimator*. It is the *single output* value for the model being the optimum estimate given our distribution. For the KF and it's variants and most other cases it is defined as the mean of our distribution: $\hat{\mathbf{x}}_{t}=\mathbb{E}[\mathbf{x}_{t}|\mathbf{z}_{1:t}]$. In more complex cases the optimum estimate isn't necessarily the mean but for all our cases it is.

When talking about the state at time $t$ before and after an observation; $\hat{\mathbf{x}}_{t}$ is after the observation *(the posterior)* and $\hat{\mathbf{x}}_{t}^{-}$ indicates our estimate at time $t$ before the observation *(the prior - conditioned on $\mathbf{z}_{1:t-1}$ rather than $\mathbf{z}_{1:t}$)*

You may in other sources see $\hat{\mathbf{x}}_{t|t}$ and $\hat{\mathbf{x}}_{t|t-1}$ instead of $\hat{\mathbf{x}}_{t}$ and $\hat{\mathbf{x}}_{t}^{-}$ respectively the subscript $t|t$ means at time $t$ given all observations up to and including at time $t$. Likewise the subscript $t|t-1$ means at time $t$ given all observations up to and including at time $t-1$.

## Model Equation
Our model equation will take in some state and return the next state. It may also take in a control vector this is a deterministic input that we know to the model. An example of where we would have this is if we are tracking an autonomous vehicle/robot and we are giving it commands. (Including doesn't complicate any maths it only effects the mean propagation).

Our model equation is $$\mathbf{x}_{t}=f_{t}(\mathbf{x}_{t-1})+b_{t}(\mathbf{u}_{t})+\mathbf{w_{t}}\quad \mathbf{w}_{t}\sim \mathcal{N}(0, Q_{t}) $$
Again, here $\mathbf{x}_{t}$ is a random variable not a single value.
Where $f$ is our *state transition model*, $b$ is the *control input model*, $\mathbf{u}_{t}$ is the control vector.
$\mathbf{w}_{t}$ is process noise how we model uncertainty growing due to model imperfections and/or the system being stochastic. $Q_{t}$ is the process noise covariance at time $t$ however, often the process noise doesn't change over time and is constant. 

Since $\mathbf{w}_{t}$ is zero mean it has no effect on the mean of $\mathbf{x}_{t}$ and $\hat{\mathbf{x}}_{t}$ is unaffected by it.
Keep in mind that out state transition, control model and process noise covariance $f, b, Q$ are all allowed to vary over time however often in practice they stay the same and the subscript $t$ may be omitted.

For the regular KF our model needs to be linear (or affine - can happen you include the control vector). So we get model equation $$\mathbf{x}_{t}=F\mathbf{x}_{t-1}+b(\mathbf{u}_{t})+\mathbf{w}_{t}$$
The control model can be non-linear as we only require linearity in $\mathbf{x}_{t-1}$. However this only works if our control vector is not random, sometimes we can have a random control vector in this case we need $b$ to be linear. IN this case you may see it being a matrix $B$ (or $G$). It is always deterministic and does not depend on the state so no matter the state the same control input gives the same additive term on the state.

However there are some cases where $b$ can depend on the state e.g. we get $b(\mathbf{x}_{t-1}, \mathbf{u}_{t})$ but this won't work with regular KF.
In general I haven't looked into having the control vector but it doesn't really change anything else equation wise if you have it or not so we will mostly be ignoring it for now. But if you do want to include a deterministic control vector it is as simple as just adding the term to the mean propagation and everything else stays the same.
If you want to the control vector to be non-deterministic/a random variable other things might change.

## Observations
We can make observations about our system and we denote an observation at time $t$ as $\mathbf{z}_{t}$ it has dimension $m$ with $m\leq n$ often $m \ll n$.
Before we actually make the observation it is a random variable as our observations aren't exact. But we will only receive one value for the observation and it is our realised value and it is what the KF conditions on. 
Our observations won't be in the exact same form as the state vector as we may not observe every variable in the state, we may observe only a transformed version/related version of the variable e.g. we are trying to predict velocity but can only observe speed. So we have the observation equation $$\mathbf{z}_{t}=h_{t}(\mathbf{x}_{t})+\mathbf{v}_{t}, \quad\mathbf{v}_{t}\sim \mathcal{N}(0, R)$$
Again to emphasise, we are treating $\mathbf{x}_{t}$ as a random vector of the true state here.
$h$ is the *observation map* it is a function that maps state space to observation space e.g. given the true state what observations do we actually make? It can be non-linear but for now we will assume that if we can observe a variable we can observe it directly meaning $h$ can be represented as a non-square matrix $H$ *(or the square identity matrix $I$ if we observe every variable at once)*. Again $H$ can vary with time but the subscript is often omitted. We will be dealing with time varying $H$ as we may be observing different variables at different times.
Measurements may not be made every step. 

$h$ used so we can transform our estimate into the same form as the observation - what observations would our estimate give - so the terms become compatible and we can compute the innovation $\tilde{y}_{t}=\mathbf{z}_{t}-H_{t}\hat{\mathbf{x}}_{t}^{-}$

***
# Kalman Filter (KF)
The Kalman filter covers both propagation and update. It requires certain assumptions/properties that being the model is linear/affine and that all probability distributions our gaussian. It also requires the observation map to be linear.
The gaussians allow us to just keep track of mean and covariance and the calculations on the distribution are all exact, the linear model is required to preserve all gaussian distributions as the propagation of a gaussian through a linear model will give us back a gaussian.
So we have $\mathbf{x}_{t}\sim \mathcal{N}(\hat{\mathbf{x}}_{t}, P_{t})$ where $P_{t}$ is the covariance of our distribution. Like before we may want to differentiate between our covariance at time $t$ but before and after an update/observation. We will use $P_{t}$ to denote after and $P_{t}^{-}$ to denote before. Again in other sources you may see $P_{t|t}$ and $P_{t|t-1}$.

## Propagation
The propagation is fairly simple. 
We have our distribution on the state $\mathbf{x}_{t-1}$ and we put it through the model equation to get $$\mathbf{x}_{t}=F\mathbf{x}_{t-1}+B\mathbf{u}_{t}+\mathbf{w}_{t}, \quad \mathbf{w}_{t}\sim \mathcal{N}(0, Q)$$
Again since $\mathbf{x}_{t-1}$ was gaussian to the affine nature of our model $\mathbf{x}_{t}$ must be.
To calculate our estimate of this new distribution we have
$$
\begin{aligned}
\hat{\mathbf{x}}_{t} &= \mathbb{E}[\mathbf{x}_{t}]\\
&=\mathbb{E}[F\mathbf{x}_{t-1}+B\mathbf{u}_{t}+\mathbf{w}_{t}]\\
&=F\mathbb{E}[\mathbf{x}_{t-1}]+B\mathbf{u}_{t}+\mathbb{E}[\mathbf{w}_{t}]\\
&=F\hat{\mathbf{x}}_{t-1}+B\mathbf{u}_{t}
\end{aligned}
$$
The key part of the KF that made this so simple is that $F$ is linear so we could pull it out of the expectation. And $B\mathbf{u}_{t}$ (being the affine part) is deterministic so it's expectation is itself. Also a key part is the noise $\mathbf{w}_{t}$ being $0$ mean so the expectation makes it vanish.

To propagate the covariance is simple as we have the distribution $\mathbf{x}_{t}$ so we just calculate $\operatorname{Cov}(\mathbf{x}_{t}):=\mathbb{E}[(\mathbf{x}_{t}-\mu_{t})(\mathbf{x}_{t}-\mu_{t})^{T}]$ and substituting in  $\mathbf{x}_{t}=F\mathbf{x}_{t-1}+B\mathbf{u}_{t}+\mathbf{w}_{t}$, and $\mu_{t}=\hat{\mathbf{x}}_{t}=F\hat{\mathbf{x}}_{t-1}+B\mathbf{u}_{t}$ therefore $\mathbf{x}_{t}-\mu_{t}=F(\mathbf{x}_{t-1}-\hat{\mathbf{x}}_{t-1})+\mathbf{w}_{t}$. Performing the expectation/matrix algebra we get $$P_{t}=FP_{t-1}F^{T}+Q$$

## Update
There are multiple ways to derive the following KF equations we will start with *MMSE* - minimum mean square error - as it is much more intuitive and motivates the why/how better. Then we will derive it again with Bayes' theorem. 

### MMSE Derivation
When we receive an observation we have two differing estimates about the state one being our current estimate $\hat{\mathbf{x}}_{t}^{-}$ and the other being our realised measurement $\mathbf{z}_{t}$. We want to combine them in a way to get the optimum estimate about the true state.

*Just for now, for ease and clarity, we will ignore the observation map and assume $\mathbf{z}_{t}$ measures all the variables of $\mathbf{x}_{t}$*
We will do this by taking a weighted average $\hat{\mathbf{x}}_{t}=(I-K)\hat{\mathbf{x}}_{t}^{-}+K\mathbf{z}_{t}$. Here $K$ is our weight and is called the Kalman gain. $K$ is different each update step so you may see $K_{t}$ but the subscript is often omitted.
Here this equation only covers the mean however we can update the whole random variable with 

This is more commonly written as $\hat{\mathbf{x}}_{t}=\hat{\mathbf{x}}_{t}^{-}+K(\mathbf{z}_{t}-\hat{\mathbf{x}}_{t}^{-})$. The vector $\mathbf{z}_{t}-\hat{\mathbf{x}}_{t}^{-}$ is called the ***innovation*** vector and is the difference between our estimate and the observation it is also generally denoted as $\tilde{y}$. In this form we have $\text{posterior}=\text{prior}+\text{gain}\times\text{innovation}$. Effectively we can think of the innovation being the amount of new information and the gain being how sensitive we are to new information. 

This innovation form is ***always*** used as when when we introduce the observation map $\hat{\mathbf{x}}_{t}$ and $\mathbf{z}_{t}$ may not be in the same form/have the same dimension so taking an average of them won't work directly so we prefer the innovation-gain form. The weighted average is only for intuition (but when $H=I$ they are **algebraically equivalent**) 

Introducing back the observation map we get the equation $$\begin{aligned}
\hat{\mathbf{x}}_{t}&=\hat{\mathbf{x}}_{t}^{-}+K\tilde{y}_{t} \\ 
\tilde{y}_{t}&=\mathbf{z}_{t}-H \hat{\mathbf{x}}_{t}^{-}
\end{aligned}$$
The goal of the KF is how do we find the optimum $K$ given our current knowledge? The answer is that we pick $K$ such that the resultant distribution of $\mathbf{x}_{t}$ minimal (co)variance *(in practice this means the minimal **trace** of the covariance)*.

In order to go from just the mean update equation we have right now to the whole distribution update we just replace the estimate $\hat{\mathbf{x}}_{t}^{-}$ with the random variable $\mathbf{x}_{t}^{-}$ so we get $$\mathbf{x}_{t} = \mathbf{x}^{-}_{t}+K(\mathbf{z}_{t}-H\mathbf{x}_{t}^{-})$$
here we are treating $\mathbf{z}_{t}$ as a random variable not just the realised value we receive.
Then we want to find the covariance of this distribution $$\begin{aligned}
\operatorname{Cov}(\mathbf{x}_{t})&=\operatorname{Cov}(\mathbf{x}^{-}_{t}+K(\mathbf{z}_{t}-H\mathbf{x}_{t}^{-})) \\
&=\operatorname{Cov}( (I-KH)\mathbf{x}^{-}_{t}+K\mathbf{z}_{t}) &(\text{rearranging})\\
&=(I-KH)\operatorname{Cov}(\mathbf{x}_{t}^{-})(I-KH)^{T}+K\operatorname{Cov}(\mathbf{z_{t}})K^{T} &\text{Expanding}\operatorname{Cov}(MA+NB) \\
&\quad +(I-KH)\operatorname{Cov}(\mathbf{x}_{t}^{-}, \mathbf{z}_{t})K^{T}+K\operatorname{Cov}(\mathbf{z}_{t},\mathbf{x}_{t}^{-})(I-KH)^{T}   \\
&=(I-KH)\operatorname{Cov}(\mathbf{x}_{t}^{-})(I-KH)^{T}+K\operatorname{Cov}(\mathbf{z_{t}})K^{T}&\text{Using }\operatorname{Cov}(\mathbf{x}^{-}_{t}, \mathbf{z}_{t})=\operatorname{Cov}(\mathbf{z}_{t}, \mathbf{x}^{-}_{t})=0 \\
P_{t}&=(I-KH)P_{t}^{-}(I-KH)^{T}+KRK^{T} &\text{Using }\operatorname{Cov}(\mathbf{x}_{t}^{-})=P_{t}^{-}, \ \operatorname{Cov}(\mathbf{z}_{t})=R  
\end{aligned}$$
We want to find $K$ such that $\operatorname{tr}(P_{t})$ is minimal. This involves taking partial derivates with respect to the matrix $K$ but after all that we find that $$K=P_{t}^{-}H^{T}(HP_{t}^{-}H^{T}+R)^{-1}$$

Now that we've found $K$ we can update our mean with the linear update $\hat{\mathbf{x}}_{t}=\hat{\mathbf{x}}_{t}^{-}+K(\mathbf{z}_{t}-H \hat{\mathbf{x}}_{t}^{-})$ here for $\mathbf{z}_{t}$ we use the single realised value that we received as our observation. We then update our covariance using $P_{t}=(I-KH)P_{t}^{-}(I-KH)^{T}+KRK^{T}$ and we are done with the update step.
### Bayes' Theorem Derivation
Although this derivation is definitely less intuitive, more algebra heavy and doesn't really motivate the idea of Kalman gain well, we will have to use this method for non Kalman filter methods of BDA. It also doesn't make the linear update assumption it just so happens that in the case of everything gaussian it is optimal.

When we receive an observation $\mathbf{z}_{t}$. we want to update our distribution with Bayes' theorem in the following form $$p(\mathbf{x}_{t}|\mathbf{z}_{1:t})=\frac{p(\mathbf{z}_{t}|\mathbf{x}_{t})p(\mathbf{x}_{t}|\mathbf{z}_{1:t-1})}{p(\mathbf{z}_{t}|\mathbf{z}_{1:t-1})}$$
Identifying the 4 key components
1. **Posterior** - $p(\mathbf{x}_{t}|\mathbf{z}_{1:t})$. This is $p(\text{Current State}|\text{All measurements})$ basically updating our distribution on the state to include the information gained by out measurements.
2. **Likelihood** - $p(\mathbf{z}_{t}|\mathbf{x}_{t})$. This is the probability of our measurement if $\mathbf{x}_{t}$ was the real state. Comes directly from the observation model/noise. $\mathbf{z}_{t}=H\mathbf{x}_{t}+\mathbf{v}_{t}, \quad \mathbf{v}_{t}\sim \mathcal{N}(0, R_{t})$. Therefore $\mathbf{z}_{t}|\mathbf{x_{t}}\sim \mathcal{N}(H\mathbf{x}_{t}, R_{t})$
3. **Prior** - $p(\mathbf{x}_{t}|\mathbf{z}_{1:t-1})$. This is the probability distribution we had before seeing the current measurement. It was the result of propagating the posterior at $t-1$ through our model as we saw earlier. Our current belief modelled by $\mathcal{N}(\hat{\mathbf{x}}_{t}, P_{t})$
4. **Evidence** - $p(\mathbf{z}_{t}|\mathbf{z}_{1:t-1})$. The probability of observing $\mathbf{z}_{t}$ under the model. *In practice we often don't compute/care about this*.

Substituting in our distributions and ignoring the normalising evidence constant we get $$p(\mathbf{x}_{t}|\mathbf{z}_{1:t})\propto \mathcal{N}(\mathbf{z}_{t};H\mathbf{x}_{t}, R_{t})\mathcal{N}(\mathbf{x}_{t};\hat{\mathbf{x}}_{t}^{-}, P_{t}^{-})$$
Note here we are actually multiplying the *probability density functions* here this is ***NOT*** the same as finding the product of two normally distributed variables.

The product of two normals is proportional to a normal so using this fact we don't have to compute this directly and we can use the formula $\mathcal{N}(\mu_{1}, \Sigma_{1})\mathcal{N}(\mu_{2}, \Sigma_{2})\propto\mathcal{N}(\mu_{3}, \Sigma_{3})$ where 
$$
\begin{aligned}
\Sigma_{3} &= (\Sigma_{1}^{-1}+\Sigma_{2}^{-1})^{-1} \\
\mu_{3} &= \Sigma_{3}(\Sigma_{1}^{-1}\mu_{1}+\Sigma_{2}^{-1}\mu_{2})
\end{aligned}
$$

However our two normals are currently in different variables ($\mathbf{x}_{t}$ and $\mathbf{z}_{t}$). But we can get them in the same variable by, instead of viewing $p(\mathbf{z}_{t} | \mathbf{x}_{t})$ as a function in $\mathbf{z}$ for a fixed $\mathbf{x}$, we view it as a function in $\mathbf{x}$ for fixed $\mathbf{z}$. Then with some complicated algebra we get that $p(\mathbf{z}_{t}|\mathbf{x}_{t}) \propto \mathcal{N}(\mathbf{x}_{t};(H^{T}R_{t}^{-1}H)^{-1}H^{T}R_t^{-1}\mathbf{z}_{t}, (H^{T}R_{t}^{-1}H)^{-1})$ so now we have:
$$
\begin{aligned}
\Sigma_{1} &=(H^{T}R_t ^{-1}H)^{-1}, &&\mu_{1} = \Sigma_{1}H^{T}R^{-1}_{t}\mathbf{z_{t}}\\
\Sigma_{2} &= P_{t}^{-}, &&\mu_{2}=\hat{\mathbf{x}}_{t}^{-}
\end{aligned}
$$ 
Putting this together we get that $P_{t}= ((P_{t}^{-})^{-1} + H^{T}R_{t}^{-1}H)^{-1}$ and $\hat{\mathbf{x}}_{t}=P_{t}(H^{T}R^{-1}\mathbf{z}_{t}+(P_{t}^{-})^{-1}\hat{\mathbf{x}}_{t}^{-})$. So we have a closed formula for the new mean and covariance once we receive an observation. We can then do some rearranging (and using the Woodbury matrix identity) to factor out a matrix $K$ to get the exact same KF equations as before with the same gain $K$.

$p(\text{observation} | \text{state})$
***
# Ensemble Kalman Filter (EnKF)
EnKF is one way to use the KF equations we've just derived but with different assumptions. EnKF works with *non-linear* models and since non-linearity do not preserve gaussians our distributions will have to be non-gaussian. We will still model observation noise ($\mathbf{v}_{t} \sim\mathcal{N}(0, R)$) and process noise ($\mathbf{w}_{t} \sim\mathcal{N}(0, Q)$ as gaussians it's just that our actual state estimate $\mathbf{x}_{t}$ distribution can't be gaussian.

The set up and notation stays the same except now our model function is non-linear so we have $$\mathbf{x}_{t}=f(\mathbf{x}_{t-1})+b(\mathbf{u}_{t})+\mathbf{w}_{t}, \quad\mathbf{w}_{t}\sim \mathcal{N}(0, Q) $$ 

To manage dealing with arbitrary distributions we deal with an array of samples (*particles*). And instead of acting with exact maths on a whole distribution we use samples to get estimates of the distribution properties. This method of using random samples to approximate computations that would otherwise be very costly/complex is called *Monte Carlo*.

We take our initial belief which, for example, could be a gaussian $\mathbf{x}_{t}\sim \mathcal{N}(\hat{\mathbf{x}}_{0}, P_{0})$ and we take some random samples from it, forming an array of particles which is our distribution. And our update and propagate step will act on the array of particles. We can then get our estimate by taking the simple mean of the particles and our covariance with a **sample** mean (*applying Bessel's correction - only to covariance not mean here)*.

To denote the $i$th particle in the array we will use $\mathbf{x}_{t}^{(i)}$.
## Propagate
Propagating our distribution is very simple. We treat each particle individually and propagate it through the model so $$\mathbf{x}_{t}^{(i)}=f(\mathbf{x}_{t-1}^{(i)})+b(\mathbf{u}_{t})+\mathbf{w}_{t}^{(i)}, \quad\mathbf{w}_{t}^{(i)}\sim_{\text{i.i.d}} \mathcal{N}(0, Q)$$
Here $\mathbf{u}_{t}$ is constant across all particles as we are only considering deterministic input. The $+\mathbf{w}_{t}^{(i)}$ is a single random sample from the normal $\mathcal{N}(0, Q)$ and the $\text{i.i.d}$ means *independent (and) identically distributed*. Basically for each particle to add in process noise we add a independent random amount of noise sampled from the process noise distribution.

## Update
For the update step we will use the linear Kalman filter like before by approximating our distribution with a  gaussian. To do this we simply compute the mean and *sample* covariance of the particles and then treat our distribution as though it was modelled by a gaussian with that mean and covariance. 

To actually perform this update we compute the Kalman gain like before using the sample covariance as $P_{t}^{-}$.
Then for each particle $\mathbf{x}_{t}^{(i)-}$ we have 
$$\mathbf{x}_{t}^{(i)} = \mathbf{x}_{t}^{(i)-} + K_{t}(\mathbf{z}_{t}^{(i)}-H\mathbf{x}_{t}^{(i)-})$$
And although we have only one measurement $\mathbf{z}_{t}$ we form a whole array of perturbed measurements with $\mathbf{z}_{t}^{(i)} = \mathbf{z}_{t}+\mathbf{w}_{t}^{(i)}, \quad \mathbf{w}_{t}^{(i)}\sim_{\text{i.i.d}} \mathcal{N}(0, R)$. Basically for each particle we add a little bit of noise to the observation we received using the distribution in which we believe observation noise follows. *In this case* $\mathcal{N}(0, R)$. 
The reason we inject this noise is that we would be updating the particles to have the correct mean but we need to have some method for the particle distribution's covariance to increase due to observation covariance so we add random noise to reflect this. Without this there is no way for the ensemble to *"see"* the randomness in the measurements.
***
# Extended Kalman Filter (EKF)
EKF is another way of dealing with a non-linear model. It is pretty simple. EKF works by preserving gaussians by instead of applying the non-linear model function applying a linear approximation of it. 

It makes this linear approximation with the *Jacobian* this is a matrix of partial derivatives. It is the generalisation of the derivative with an $\mathbb{R}^{n}\to \mathbb{R}^{m}$ function. It is linear function and can be represented as a matrix $J$.
## Propagate
We propagate our mean using the non-linear model function. Meaning $\hat{\mathbf{x}}_{t}=f(\hat{\mathbf{x}}_{t-1})$.
However in order to keep a normal we propagate the covariance with a linear approximation.
We expand using the Taylor series around the mean $\hat{\mathbf{x}}_{t}$ our function $$f(\mathbf{x}_{t})\approx f(\hat{\mathbf{x}}_{t})+\frac{\partial f}{\partial \mathbf{x}}\bigg|_{\displaystyle \hat{\mathbf{x}}_{t}}(\mathbf{x}_{t}-\hat{\mathbf{x}}_{t})$$
Here $\displaystyle\frac{\partial f}{\partial \mathbf{x}}\bigg|_{\displaystyle \hat{\mathbf{x}}_{t}}$ is precisely the Jacobian of $f$ at $\hat{\mathbf{x}}_{t}$ so call it $J$. So we have $f(\mathbf{x}_{t})\approx f(\hat{\mathbf{x}}_{t})+J(\mathbf{x}_{t}-\hat{\mathbf{x}}_{t})$ and putting this in our model equation we have
$$
\begin{aligned}
\mathbf{x}_{t}&\approx f(\hat{\mathbf{x}}_{t-1})+J(\mathbf{x}_{t-1}-\hat{\mathbf{x}}_{t-1}) + \mathbf{w}_{t}\\
&=\hat{\mathbf{x}}_{t}+J(\mathbf{x}_{t-1}-\hat{\mathbf{x}}_{t-1})+ \mathbf{w}_{t}\\
&=J\mathbf{x}_{t-1}+\mathbf{w}_{t}+(\hat{\mathbf{x}}_{t}-\hat{J}\mathbf{x}_{t-1})\\
&=J\mathbf{x}_{t-1}+\mathbf{w_{t-1}}+c
\end{aligned}
$$


We want to calculate the new covariance of this so we get
$$
\begin{aligned}
P_{t} &= \operatorname{Cov}(\mathbf{x}_{t}) \\
&\approx \operatorname{Cov}(J\mathbf{x}_{t-1}+\mathbf{w_{t-1}}+c)\\
&=\operatorname{Cov}(J\mathbf{x}_{t-1}+\mathbf{w_{t-1}}) &\operatorname{Cov}(\mathbf{X}+c)=\operatorname{Cov}(\mathbf{X})  \\
&=J\operatorname{Cov}(\mathbf{x}_{t-1})J^{T} +\operatorname{Cov}(\mathbf{w}_{t-1})&\operatorname{Cov}(M\mathbf{X})=M\operatorname{Cov}(\mathbf{X})M^{T}  \\
&= JP_{t-1}J^{T}+Q
\end{aligned}
$$
Note this is the exact same form as KF but $F$ replaced with the Jacobian $J$.
## Update
Since we've forced our distribution to be gaussian via linear approximations we can use the exact same update step as the KF with no modifications.
***

