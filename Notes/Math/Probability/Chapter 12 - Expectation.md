5N^CH
There is not a clear way to define expectation for multivariate distributions

$$
\begin{align}
\mathbb{E}[g(X,Y)] = \sum_{x}\sum_{y} g(x,y) p_{XY}(x,y) \\
= \int _{x} \int _{y} g(x,y)f_{XY}(x,y) \, dy  \, dx 
\end{align}
$$

# Ways to define expectation
## With addition
$$
\begin{align}
\mathbb{E}[X+Y] &= \int \int (x+y) f_{XY}(x,y) \, dy  \, dx  \\
&=\int \int xf_{XY}(x,y)  \, dy  \, dx  +  \int  \int yf_{XY}(x,y) \, dx  \, dy  \\
&= \int  x f_{X}(x) \, dx + \int y f_{Y}(y) \, dy \\
& \mathbb{E}[X] + \mathbb{E}[Y] 
\end{align}
$$

## With multiplication
**Proposition:** If X and Y are independent, then $h(\cdot)$ and $k(\cdot)$ are functions that 
$$
\mathbb{E}[h(X)k(Y)] = \mathbb{E}[h(X)] \mathbb{E}[k(Y)]
$$
so
$$
\mathbb{E}[XY]=\mathbb{E}[X]\mathbb{E}[Y]
$$
**proof**
$$
\begin{align}
\mathbb{E}[h(X)k(Y)] &= \int \int h(X) k(Y) f_{XY}(x,y) \, dx  \, dy  \\
&=\int \int h(X)f_{X}(x) k(Y) f_{Y}(y) \, dx  \, dy  \\ \\
&=\int  k(Y) f_{Y}(y)  \left[ \int h(X)f_{X}(x)  \, dx  \right] \, dy  \\ \\
&= \mathbb{E}[X] \mathbb{E}[Y]
\end{align}
$$

# Covariance
Measures how far data in X is from its mean and how far data in Y is from its mean. Is multiplicative
$$
\begin{align}
Cov(X,Y)&=\mathbb{E}[(X- \mathbb{E}[X]) (Y- \mathbb{E}[Y])] \\
&=\mathbb{E}[XY - X \mathbb{E}[Y] - Y \mathbb{E}[X] + \mathbb{E}[X]\mathbb{E}[Y]] \\
&=\mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y] - \mathbb{E}[Y]\mathbb{E}[X] + \mathbb{E}[X]\mathbb{E}[Y] \\
&=\mathbb{E}[XY] -\mathbb{E}[X]\mathbb{E}[Y]
\end{align}
$$
## Properties
Let $X,Y,Z$ be random variables and $a, b$ be constants

- If we take $Cov(X,X)$ we get the same thing as $Var(X)$
$$
\mathbb{E}[XX]-\mathbb{E}[X]\mathbb{E}[X]=E[X^{2}]-E[X]^{2}
$$
- If $X, Y$ are independent, then $Cov(X,Y)=0$
- $Cov(X,Y)=Cov(Y,X)$
- $Cov(aX, Y)=aCov(X,Y) = a Cov(X, aY)$
- $Cov(X+b,Y)=Cov(X,y)=Cov(X,Y+b)$
	- translations don't affect spread of data
- $Cov(X+Y, Z)=Cov(X,Z)+Cov(Y, Z)$
- $Var(aX+bY)=Cov(aX+bY, aX+bY) = a^{2}Var(X)+2abCov(X,Y)+b^{2}Var(y)$
	- If X, Y independent, then $Var(X+Y)=Var(X)+Var(y)$

# Conditional Expectation
$$
\begin{align}
\mathbb{E}[Y|X=x]&=\sum_{y}y f_{Y|X=x}(y) \\
&=\int y f_{Y|X=x}(y) \, dy  \\
&= \int y \left( \frac{f_{XY}(x,y)}{f_{X}(x)} \right) \, dy  \\
\end{align}
$$

The regression of $Y$ on $X$ is really the conditional
$\text{regression}=\mathbb{E}[Y|X=x]$  "what is the expected Y given some particular x"?


## Correlation coefficient of X and Y
$$
\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{ Var(X)Var(y) }}
$$
- They are uncorrelated if $\rho=0$, Positively correlated if $\rho>0$, negatively correlated if $\rho<0$
- Bears some resemblance to taking normalized dot product? [[Complex Linear Algebra#Inner Product]] or a projection?

## Properties
- $\rho(X,Y)=\rho(Y, X)$
- If X,Y independent => $\rho=0$
- $\rho(aX+b, cY+d)= \rho(X,Y)$ if $a, c > 0$ 
- $-1\leq \rho(X,Y)\leq 1$
- $\rho(X,Y)=1$ => $Y=aX+b$ for $a>0$
- $\rho(X,Y)=-1$ => $Y=aX+b$ for $a<0$
# Examples
## Suppose we have $n$ independent copies of a random variable $X$ call them $\{ X_{i} \}_{i=1}^{n}$ where $\mathbb{E}[X_{i}]=p$

Consider the sample mean
$$
\overline{X}:=\frac{1}{n}\sum_{i=1}^{n}X_{i}
$$
What is the mean and variance of the sample mean?
$$
\begin{align}
\mathbb{E}[\overline{X}] &= \mathbb{E}\left[ \frac{1}{n} \sum_{i=1}^{n}X_{i} \right] \\
\text{you can split addition over expectation} \\
&=\frac{1}{n}\sum_{i=1}^{n}\mathbb{E}[X_{i}] \\
&=\frac{1}{n}\sum_{i=1}^{n}p = \frac{1}{n} n p = p
\end{align}
$$
Interpretation: The mean of the sample avg numbers slept should converge to the population mean p

$$
\begin{align}
Var(\overline{X}) &= Var\left( \frac{1}{n} \sum X_{i} \right)  \\
&=\left( \frac{1}{n} \right)^{2} \sum_{i=1}^{n}Var(X_{i}) = \frac{1}{n}Var(X_{i})
\end{align}
$$
If the $X_{i}$'s are Bernoulli, then $Var(X_{i})=p(1-p)$ and
=> $Var(\overline{X})=\frac{p(1-p)}{n}$

- The more samples $n$ you get, the variance converges to 0 so the sample mean gets to the population mean

## Suppose X and Y have joint PMF... Find $\mathbb{E}[XY]$

| X/Y | 0   | 1   |
| --- | --- | --- |
| 0   | 0.2 | 0.7 |
| 1   | 0   | 0.1 |
$$
\begin{align}
\mathbb{E}[XY]&=\sum_{x}\sum_{y} x y p_{XY}(x,y) \\
& 0(0)(0.2) + 0(1)(0.7) + 1(0)(0) + 1(1)(0.1) = 0.1
\end{align}
$$

## Suppose ... find $\mathbb{E}[XY]$ and $Var(Y)$ 
$$
f_{XY}(x, y)=\begin{cases}
f_{XY}(x,y)=10xy^{2} &0 < x < y < 1 \\
0 & \text{otherwise}
\end{cases}
$$
$$
\begin{align}
\mathbb{E}[XY]&=\int _{0}^{1} \int _{x}^{1} x y 10xy^{2} \, dy  \, dx \\
&= \int _{0}^{1}\left[ x^{2} \frac{5}{2}y ^{4} \right]_{x}^{1} \, dx  \\
&= \int _{0}^{1} \frac{5}{2}x^{2} - \frac{5}{2}x^{6} \, dx = \frac{20}{21}
\end{align}
$$
Need to integrate over all space because X, Y are both dependent on each other
$$
\begin{align}
\mathbb{E}[Y^{2}]&=\int _{0}^{1} \int _{x}^{1} y ^{2} 10 x y ^{2}  \, dy  \, dx  \\
&= \int _{0}^{1}2xy^{5} |_{y=x}^{y=1} \, dx \\
&= \int _{0}^{1}2x_{0}2x^{6} \, dx = \frac{5}{7}  \\
\mathbb{E}[Y] &= \int _{0}^{1} \int _{x}^{1} y 10xy^{2} \, dy  \, dx \\
&= \int _{0}^{1} \frac{5}{2}x - \frac{5}{2}x^{5} \, dx = \frac{5}{6}  \\
Var[Y]&=\mathbb{E}[Y^{2}]-\mathbb{E}[Y]^{2} \\
\end{align}
$$

## If ... find $\rho(X,Y)$

$$f_{XY}(x,y)=\begin{cases}
 \frac{1}{y} & 0<x<y<1 \\
0 & \text{otherwise}
\end{cases}$$
To calculate $\rho(X,Y)$ we need $\mathbb{E}[XY], \mathbb{E}[X^{2}], \mathbb{E}[Y^{2}], \mathbb{E}[X], \mathbb{E}[Y]$

$$
\begin{align}
\mathbb{E}[XY] &= \int _{0}^{1} \int _{x}^{1}  x y \frac{1}{y} \, dy  \, dx = \int  \, dx   \\
&= \int _{0}^{1}x - x^{2} \, dx \\
&= \frac{1}{6} 
\end{align}
$$

$$
\begin{align}
\mathbb{E}[X^{2}] &= \int _{0}^{1} \int  _{x}^{1} x^{2} \cdot 1/y \, dy \, dx  \\
&=\int  _{x}^{1}  \int _{0}^{1}  x^{2} \cdot 1/y \, dx \, dy \\
&= \int _{0}^{1} \frac{1}{3}y^{2} \, dy 
\end{align}
$$
$$
\begin{align}
\mathbb{E}[Y^{2}]&=\int _{0}^{1}\int _{x}^{1} y ^{2} \cdot \frac{1}{y} \, dy  \, dx  \\
&= \int _{0}^{1} \frac{1}{2} y^{2} |_{y=x}^{y=1}\, dx \\
&=\int _{0}^{1} \frac{1}{2} - \frac{1}{2}x^{2} \, dx=\frac{1}{3}  
\end{align}
$$

$$
\begin{align}
\mathbb{E}[X] &= \int _{0}^{1} \int _{0}^{y} x \frac{1}{y} \, dx  \, dy = \frac{1}{4} \\
\mathbb{E}[Y] &= \int _{0}^{1} \int _{x}^{1} y \frac{1}{y} \, dy  \, dx  = \frac{1}{2}
\end{align}
$$

$$
\begin{align}
Cov(X,Y) &= E[XY]-E[X]E[Y] = \frac{1}{6}-\frac{1}{2}\cdot \frac{1}{4}=\frac{1}{24}\\
Var(X)&=\frac{1}{9} - \left( \frac{1}{4} \right)^{2}\\
Var(Y)&= \frac{1}{3}-\left( \frac{1}{2} \right)^{2} \\
\rho(X,Y) = \frac{\frac{1}{24}}{\sqrt{ \frac{7}{144} \frac{1}{12} }} = 0.5647
\end{align}
$$

## If ... find $Var(X|Y=2)$
$$
f_{XY}(x,y)=\begin{cases}
\frac{1}{18}e^{-((x+y)/6)} & 0<y<x \\
0 & \text{otherwise}
\end{cases}
$$

To calculate the variance of a conditional you need to find expectations of conditionals
$$
Var(X|Y=2)=\mathbb{E}[X^{2}|Y=2] - \mathbb{E}[X|Y=2]^{2}
$$
Remember that
$$
\begin{align}
\mathbb{E}[X|Y=y]=\int x f_{X|Y=y} (x|y) \, dx  \\
f_{X|Y=y}(x|y)=\frac{f_{XY}(x,y)}{f_{y}(y)}
\end{align}
$$

We need to find $f_{X|Y=2}(X|2)$ which needs $f_{Y}(y)$

$$
\begin{align}
f_{Y}(y)&=\int _{y}^{\infty} \frac{1}{18} e^{-x/6} e^{-y/6} \, dx  \\
&=\frac{1}{18}e^{-y/6} \int _{y}^{\infty} e^{-x/6} \, dx \\
&=\frac{1}{18}e^{-y/6} [-6 e^{-x/6}]_{x=y}^{x=\infty} \\
&=\frac{1}{3} e^{-y/6}e^{-y/6} \\
\end{align}
$$

$$
\begin{align}
f_{X|Y=2}&=\frac{f_{XY}(x,2)}{f_{Y}(2)} \\
&=\frac{\frac{1}{18} e ^{-x/6} e^{-2/6}}{ \frac{1}{3} e^{-2/6} e^{-2/6}} \\
&=\frac{1}{6}e^{1/3}e^{-x/6}
\end{align}
$$
Be careful of bounds of integration. Need to integrate from x=2 to infty
$$
\begin{align}
\mathbb{E}[X^{2}|Y=2]&=\int_{2}^{\infty} x^{2} \frac{1}{6}e^{1/3}e^{-x/6} \, dx  \\
&\text{need to do integration by parts twice} \\ \\
&=\frac{1}{6}e^{-1/3}[  -6x^{2}e^{-x/6} - 72xe^{-x/6} - 432 e^{-x/6}]_{x=2}^{\infty} \\
&= \frac{1}{6}e^{1/3}[0 + (6\cdot 4 + 72 \cdot 2 e ^{-1/3} + 432 e^{-1/3})] \\
&= 4 + 24+72 = 100
\end{align}
$$
![[Pasted image 20240329130744.png]]


Calculate the first moment
$$
\begin{align}
\mathbb{E}[X|Y=2] &= \frac{1}{6}e^{1/3} \int _{2}^{\infty}x e^{-x/6} \, dx  \\
&= \frac{1}{6}e^{1/3}[-6xe^{-x/6} - 36 e ^{-x/6}]_{x=2}^{\infty} \\
&=8
\end{align}
$$

Calculate the variance
$$
Var(X|Y=2) = 100 - 8^{2} = 36
$$

## Find the correlation coefficient between X and Y $\rho(X,Y)$

| Y\X        | 0   | 1   | $p_{Y}(y)$ |
| ---------- | --- | --- | ---------- |
| 0          | 0   | 0.3 | 0.3        |
| 1          | 0.2 | 0.5 | 0.7        |
| $p_{X}(x)$ | 0.2 | 0.8 |            |

Calculate all the moments
$$
\begin{align}
\mathbb{E}[XY]= 0(0)(0) + \dots + (0)(0)(0) + (1)(1)(0.5)=0.5 \\ \\
\text{multiply x for all values in the grid}\\
\mathbb{E}[X] = 0(0) + 0(0.2) + 1(0.3)+1(0.5) = 0.8 \\
\mathbb{E}[Y]=0.7 \\
\mathbb{E}[X^{2}]=\mathbb{E}[X] = 0.8\\
\mathbb{E}[Y^{2}]=\mathbb{E}[Y]=0.7 \\
\end{align}
$$

Calculate the variances
$$
\begin{align}
Var(X)=0.8-(0.8)^{2} = 0.16 \\
Var(Y)=0.7-0.7^{2}=0.21 \\
Cov(X,Y) = 0.5 - (0.8)(0.7) = -0.06 \\
\end{align}
$$

Calculate the correlation coefficients
$$
\rho(X,Y)= \frac{-0.06}{\sqrt{ 0.16 \cdot 0.21 }} = -0.3273
$$