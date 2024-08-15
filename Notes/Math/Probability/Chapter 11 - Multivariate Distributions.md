Consider a collection of random variables $(X_{1}, X_{2}, \dots, X_{n})$ (a random vector). 

# Joint PMF
For two random discrete variables $X, Y$
$$
P_{XY}(x, y)=P(X=x, Y=y)
$$
- This is equivalent to "and"/intersection of both variables

Since it is a PMF,
$$
\sum_{i, j=1}^{\infty}P_{XY}(x_{i}, y_{i}) = 1
$$

# Joint continuity
Two random variables $X, Y$ are jointly continuous if there is a nonnegative function $f_{XY}: \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ so that for any $A \subseteq \mathbb{R}\times \mathbb{R}$
$$
P((X, Y) \in A)=\int \int _{A} f_{XY}(x, y) \, dx  \, dy 
$$

## Rectangular region
If $A=[a,b]\times[c, d]$ then
$$
P(a \leq X \leq b, c \leq Y \leq d) = \int_{-\infty}^{\infty} \int _{-\infty}^{y} f_{XY}(x,y) \, dx  \, dy 
$$

# Multivariable CDF
$$
\begin{align}
F_{XY}(x,y)&=P(X\leq x, Y\leq y)\\
&=\int _{-\infty} ^{x} \int _{-\infty }^{y} f_{XY}(x,y) \, dx  \, dy  \\
&\implies f_{XY}= \frac{\partial^{2}F}{\partial x\partial y} (x,y)
\end{align}
$$

# Marginal Probability Density functions
Suppose $f_{XY}(x, y)$ is  a joint PDF of $X$ and $Y$ are
$$
\begin{align}
f_{X}(x) = \int _{-\infty}^{\infty}f_{XY}(x, y) \, dy  \\
f_{Y}(y) = \int _{-\infty}^{\infty} f_{XY}(x,y) \, dx 
\end{align}
$$

- Like slicing up a function of two variables along a single directions
- Needed for conditional distributions

## Multivariate binomial distribution

The uni-variate binomial distribution with parameters $n, p$ is 
$$
P(X=k)=\frac{n!}{k!(n-k)!} p^{k}(1-p)^{n - k }
$$
If we let $k_{1}=k, k_{2}=n-k, p_{1}=p, p_{2}=1-p$. Then
$$
P(X=k_{1}, Y=k_{2}) = \frac{n!}{k_{1}!k_{2}!} p_{1}^{k_{1}}p_{2}^{k_{2}} = P_{XY}(k_{1}, k_{2})
$$
- The binomial distribution is essentially a joint distribution of success and failure

### Multiple categories >2
- We can generalize to more than 2 categories. If $(x_{1},\dots ,x_{r})$ is a random vector, then
$$
P(X_{1}=k_{1},\dots,X_{R}=K_{r}) = \frac{n!}{k_{1}!\dots k_{r}!}
p_{1}^{k_{1}}\dots p_{r}^{k_{r}}$$
When $k_{1}+\dots +k_{r}=n$ and $p_{1}+\dots +p_{r}=1$

# Independence 
Two discrete random variables are independent if
- Comma in P(X, Y) are like the AND symbol
$$
P(X=x, Y=y) = P(X=x)P(Y=y)
$$
For continuous distributions
$$
P(X \in A, Y \in B) = P(X \in A) P(Y \in B)
$$

- You can write the PMF as the product of the marginal PDFs
$$
P_{XY}(x, y) = P(X=x, Y=y) = P(X=x)P(Y=y)=P_{X}(x)P_{Y}(y)
$$


- For continuous distributions you can do something similar, but you can only integrate over rectangular regions (or else you get dependence on y and x)
$$
\begin{align}
\int _{a}^{b} \int _{c}^{d} f_{XY}(x, y) \, dy  \, dx = P(A\leq X\leq b, c\leq Y\leq d)  \\
= P(a \leq X \leq b)P(c \leq Y \leq d) \\
=\int _{a}^{b}f_{X}(x) \, dx \int _{c}^{d} f_{Y}(y) \, dy  \\
=\int _{a}^{b} \int _{c}^{d} f_{X}(x)f_{Y}(y) \, dy \, dy  \\
\end{align}
$$

# Convolution
If $X$ and $Y$ are independent univariate distributions, then the density of $X+Y$ is given by the convolution formula
$$
f_{X+Y}(a) = \int f_{X}(a-y)f_{Y}(y) \, dy 
$$
- This is an indefinite integral/antiderivative. So it takes a parameter a and returns a distribution of a
### Adding two gamma distributions together
 If $X \sim \Gamma(s, \lambda), Y \sim \Gamma(t, \lambda)$ then calculate the density of $X+Y$

For gamma $f_{X}(x)=\frac{se^{-sx}(sx)^{\lambda-1}}{\Gamma(\lambda)}$ and $f_{Y}(y)=\frac{te^{-tx}(tx)^{\lambda-1}}{\Gamma(\lambda)}$
$$
\begin{align}
f_{X+Y}(a) = \int f_{X}(a-y)f_{Y}(y) \, dy  \\
= \int \left(\frac{se^{-sx}(sx)^{\lambda-1}}{\Gamma(\lambda)}\right) \left(\frac{te^{-tx}(tx)^{\lambda-1}}{\Gamma(\lambda)} \right) \, dy \\
=\dots \\
=\frac{(s+t)e^{-(s+t)a}((s+t)a)^{\lambda-1}}{\Gamma(\lambda)}  \\
\implies X+Y \sim \Gamma(s+t, \lambda)
\end{align}
$$
This means that if you have a bunch of exponential distributions $X_{i} \sim \Gamma(1,\lambda)=Exp(\lambda)$ you can add the first parameters and keep the common second parameters
$$
\sum_{i=1}^{n}X_{i} \sim \Gamma(n, \lambda)
$$
### Adding two normals to get $\chi^{2}$
- If you have $Z \sim N(0,1) \implies Z^{2} \sim \Gamma(\frac{1}{2}, \frac{1}{2})=\chi_{1}^{2}$
$$
\sum_{i=1}^{n}Z_{i}^{2}\sim \Gamma\left( \frac{n}{2}, \frac{1}{2} \right)=\chi_{n}^{2}
$$

### Adding multiple normal distributed variables together
If you have a bunch of things that are normally distributed with different means and variances $X_{i} \sim N(\mu_i, \sigma_{i}^{2})$ and all the $X_{i}$'s are independent, then the combined thing is distributed normally

$$
\sum_{-1}^{n}X_{i}\sim N\left( \sum_{i=1}^{n}\mu_{i}, \sum_{i=1}^{n}\sigma_{i}^{2} \right)
$$

## For discrete variables
You do not need to find do the convolution like in the continuous case

If $X$ and $Y$ are independent discrete random variables taking on only non-negative values, then

$$
P_{X+Y}(r) = P(X+Y=r) = \sum_{k=0}^{r}P(X=k)P(Y=r - k)
$$

## Adding poisson distributed variables together
If $X\sim Pois(\lambda)$ and $Y \sim Pois(\mu)$ then
$$
\begin{align}
P_{X+Y}(r) = \sum_{k=0}^{r}P(X=k)P(Y=r-k) \\
=\sum_{k=0}^{r}\left( e^{-\lambda} \frac{\lambda^{k}}{k!} \right) \left( e^{-\mu} \frac{\mu^{k}}{k!} \right) \\
=e^{-(\lambda+\mu)} \sum_{k=0}^{r} \left( \frac{1}{k!(r-k)!} \lambda^{k} \mu^{r-k} \right) \\
\end{align}
$$
This is almost a choose function
$$
\begin{align}
=e^{-(\lambda+\mu)} \sum_{k=0}^{r} \left( \frac{1}{k!(r-k)!} \lambda^{k} \mu^{r-k} \right) \frac{r!}{r!}\\
= \frac{e^{-(\lambda+\mu)}}{r!}\sum_{k=0}^{r} \left( {r \choose k} \lambda^{k} \mu^{r-k} \right) \\
\end{align}
$$

We can use the binomial theorem $(a+b)^{n}=\sum_{k=0}^{n} {n \choose k}a^{k}b^{n-k}$
$$
\begin{align}
= \frac{e^{-(\lambda+\mu)}}{r!}\sum_{k=0}^{r} \left( {r \choose k} \lambda^{k} \mu^{r-k} \right) \\
= \frac{e^{-(\lambda+\mu)}}{r!} (\lambda+\mu)^{r} \\
\implies X+Y \sim Pois(\lambda+\mu )
\end{align}

$$


### Adding and subtracting normals
If you add or subtract normal distributions, you get a normal distribution
If $X, Y$ are independent normals then
$$
-Y \sim N(-\mathbb{E}[Y], Var(Y))
\implies X-Y = X + (-Y) \sim N(, \mu, \sigma^{2})
$$


# Conditional distributions
## Discrete case
The conditional discrete random variable $X | Y=y$ (this as a whole is a random variable) is called "X given Y=y" is a discrete random variable with PMF
$$
P((X|Y=y)=x) = P(X=x | Y=y)
$$

Therefore we have
$$
\begin{align}
P_{X|Y=y}(x) = P_{X|Y}(x|y)&=P(X=x|Y=y) \\
&=\frac{P(X=x, Y=y)}{P(Y=y)} \\
&=\frac{P_{XY}(x,y)}{P_{Y}(y)}
\end{align}
$$
This is only true if $P_{Y}(y)\neq 0$

- This is saying that you can do conditional probability the same. If you divide the joint PMF by the marginal PMF then you can get the conditional probability

## Conditional PDF
Suppose $X$ and $Y$ are jointly continuous, then the conditional PDF of $X$ given $Y$ is
$$
F_{X|Y=y}(x)=\frac{f_{XY}(x,y)}{f_{Y}(y)}
$$

# Functions on random variables
- $g(x)$ is strictly increasing if for all $x_{1}<x_{2}, g(x_{1})<g(x_{2})$
- Strictly decreasing if $g(x_{1})>g(x_{2})$
- Strictly monotone if strictly increasing or decreasing
strictly monotone functions <=> [[Functions|one to one]] <=> [[Inverse Functions|invertible]]

**Thm** Suppose $g(x)$ is differentiable and strictly monotone and $X$ is a continuous random variable. Then $Y=g(X)$ is a continuous random variable with PDF

$$
f_{Y}(y) = \begin{cases}
\frac{f_{X}(g^{-1}(y))}{|g'(g^{-1}(y))|} = \frac{f_{X}(x)}{|g'(x)}| & \text{if y is in the range of g} \\
0 & \text{otherwise}
\end{cases}
$$

- This is essentially giving you the probability of the g(X) outcome occuring
- Can do a change of variables for a multivariate distribution by using the jacobian

**Thm** SUppose $X_{1}, X_{2}$ are jointly continuous. Let
$$
(Y_{1}, Y_{2}) = g(X_{1}, X_{2}) = (g_{1}(X_{1}, X_{2}), g_{2}(X_{1}, X_{2}))
$$
so that $g: \mathbb{R}^{2} \to \mathbb{R}^{2}$ is continuous, invertible, with continuous partial derivatives. Let $h=g^{-1}$ so that
$$
(X_{1}, X_{2}) = h(Y_{1}, Y_{2}) = (h_{1}(Y_{1}, Y_{2}), h_{2}(Y_{1}, Y_{2}))
$$
Then $Y_{1}$ and $Y_{2}$ are jointly continuous with PDF
$$
f_{Y_{1}, Y_{2}} = f_{X_{1},X_{2}} (h_{1}(y_{1},y_{2}), h_{2}(y_{1},y_{2})) \cdot\mid J_{h}\mid
$$
where
$$
J_{h}=\det \begin{bmatrix}
\frac{\partial h_{1}}{\partial y_{1}} & \frac{\partial h_{1}}{\partial y_{2}} \\
 \frac{\partial h_{2}}{\partial y_{1}} & \frac{\partial h_{2}}{\partial y_{2}}
\end{bmatrix}
$$
### Finding joint PDF of non-independent events
If you know the marginal and conditional distributions you can do this
$$
f_{X_{1}, X_{2}} = f_{X_{1}}(x_{1})\cdot f_{X_{2}|X_{1}=x_{1}}(x_{2})
$$

# Examples
## If $f_{XY}(x,y)=ce^{-x}e^{-2y}$ for $0<x<\infty$ and $x < y < \infty$, what is c?
1) Densities must integrate to one

$$
\begin{align}
1=\int _{0}^{\infty} \int _{x}^{\infty} ce^{-x}e^{-2y} \, dy  \, dx  \\
=\int _{0}^{\infty} ce^{-x} \frac{1}{2}e^{-2x} \, dx  \\
=\frac{c}{6} \\
\implies c=6
\end{align}
$$
## $X \sim Exp(\lambda) \implies f_{X}(x)=\lambda e^{-\lambda x}$. Let $Y=X^2$
- Since $X^2$ is differentiable and strictly monotone from 0 to inf then
$$
g(x)=x^{2}\implies g'(x)=2x \implies g^{-1}(y)=\sqrt{ y }
$$

Plug $g^{-1}(y)$ for all x into $f_{X}$ to find the PDF
$$
f_{Y}(y)=\frac{\lambda e^{-\lambda \sqrt{ y }}}{\mid 2 \sqrt{ y }\mid} \text{ if y>0}
$$

## Let $X_{1}\sim N(0, 1)$ and $X_{2}\sim N(0, 4)$ be independent random variables. Let $Y_{1}=2X_{1}+X_{2}$ and $Y_{2}=X_{1}-3X_{2}$
- Ys are random variables that are transformed, pre-existing random variables
1) Write the probability density function for $X_{1}, X_{2}$
Because the two random variables are independent we know
$$
f_{X_{1}, X_{2}} = f_{X_{1}}f_{X_{2}}
$$
$$
\begin{align}
f_{X_{1}}(x_{1})=\frac{1}{\sqrt{ 2\pi}}e^{-x_{1}^{2}/2} \cdot \\
f_{X_{2}}(x_{2})=\frac{1}{2\sqrt{ 2\pi }} e^{-x_{2}^{2}/8}
\end{align}
$$
2) Figure out what the $g$ functions are (and their components). Solve the two systems for $x_{1}, x_{2}$
$$
\begin{align}
y_{1}=g_{1}(x_{1}, x_{2}) = 2x_{1}+x_{2} \\
y_{2}=g_{2}(x_{1},x_{2})=x_{1}-3x_{2} \\
\implies x_{1}=\frac{3}{7}y_{1}+\frac{1}{7}y_{2}=h_{1}(y_{1},y_{2}) \\
\implies x_{2}=\frac{1}{7}y_{1}-\frac{2}{7}y_{2}=h_{2}(y_{1},y_{2})
\end{align}
$$
3) Calculate the jacobian
$$
\begin{align}
J_{h}=\det \begin{bmatrix}
\frac{3}{7} & \frac{1}{7} \\
\frac{1}{7} & -\frac{2}{7}
\end{bmatrix} = -\frac{7}{49}=-\frac{1}{7}
\end{align}
$$
Finally, knowing that the two distributions are independent and substituting $x_{i}=h_{i}(y_{1},y_{2})$
$$
\begin{align}
f_{Y_{1}, Y_{2}}(y_{1},y_{2})&=f_{X_{1},X_{2}}(h_{1},h_{2}) \cdot \mid-\frac{1}{7}\mid \\
&=f_{X_{1}}(h_{1})\cdot f_{X_{2}}(h_{2}) \frac{1}{7} \\
&=\frac{1}{7}\frac{1}{\sqrt{ 2\pi}}e^{-(\frac{3}{7}y_{1} + \frac{1}{7}y_{2})^{2}/2} \cdot \frac{1}{2\sqrt{ 2\pi }} e^{-x_{2}^{2}/8}\\
\end{align}
$$
- $Y_{1}, Y_{2}$ are not independent events
