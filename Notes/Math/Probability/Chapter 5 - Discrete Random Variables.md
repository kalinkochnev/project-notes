A **random variable** is a real-valued function on the sample space $S$. Random variables are usually denoted by $X, Y, Z$.

A **discrete random variable** is one that can only take a countably many values (at most an integer number of values)
*examples*:
	If one rolls a die, let $X$ be the number that was rolled
	If one rolls a die, let $Y$ be $1$ if the roll was even and $0$ if it was odd.
	If one tosses 10 coins, let $X$ be the number of heads (0, 1, 2... 10)
	In $n$ trials, let $X$ be the number of successes

# Probability Mass Function (PMF)
For a discrete random variable, we define the the probability mass function/the density of $X$ as
$$P_{X}(x):=P(X=x)$$
or using the [[Image and Preimage|preimage]] 
$$P(X=x)=P(X^{-1}(x))$$
**Note:**
$$
\sum_{i\in \mathbb{N}} P_{X}(x_{i}) = 1
$$
## Expectation
For a discrete random variable, we define the expectation or expected value or mean of $X$ to be
$$
\mathbb{E(X)}:= \sum_{\{ x | P_{X}(x)>0 \}} x \cdot P_{X}(x)
$$
**Only if this converges absolutely** [[Calculus#Convergence]]
- You sum over all possible outcomes times the probability of it happening



If $X$ is a random variable and $S$ is a countable sample space, then
$$
\mathbb{E}(X)= \sum_{\omega \in S} X(\omega) P(\{ \omega \})
$$
As long as the series is absolutely convergent
- $X(\omega)$ = the value of X at the value at the event $\omega$
- $P(\{ \omega \})$ probability of that event $\omega$ happening

- This version has a different amount of terms in the sum but it adds up to the same expectation

### If $X$ and $Y$ are random variables on the same sample space $S$ and $a,b \in \mathbb{R}$ are two real numbers, then $\mathbb{E}$ is a linear operator
$$
\mathbb{E}[aX+bY]=a \mathbb{E}X+b \mathbb{E}Y
$$

## Let $X$ be a discrete random variable taking on values $\{ x_{i} \}_{i \in \mathbb{N}}$ and $g$ be a real valued function, then
$$
\mathbb{E}[g(X)]=\sum_{i=1}^{\infty} g(x_{i})p_{x}(x_i)
$$
### What if $g(x)=c$
$$
\begin{align}
\mathbb{g(X)}&=\sum_{i=1}^{\infty}g(x_{i})p_{x}(x_{i}) \\
&=\sum_{i=1}^{\infty} c p_{x}(x_{i}) \\
&=c \sum_{i=1}^{\infty}
\end{align}
$$
# Moment function and Variance
## Variance and STD
$\mathbb{E}[X^{n}]$ is called the nth moment of $X$. It $\mathbb{E}[X]$ is well-defined, then
$$
\begin{align}
Var(X)&=\mathbb{E}[(X-\mathbb{E}X)^{2}] \\
SD(X)&=\sqrt{ Var(X) }
\end{align}
$$
Variance measures the average positive distance between any outcome and the average
- We take the expected value of the unsigned squared distances

Alternative formula
$$
Var(X)=\mathbb{E}[X^{2}]-(\mathbb{E}[X])^{2}
$$

**Proof:**
$$
\begin{align}
Var(X)&=\mathbb{E}[(X-\mathbb{E}X)^{2}]  \\
&= \mathbb{E}[X^{2}-2X\mathbb{E}X+(\mathbb{E}X)^{2}] \\
&=E[X^{2}]-2\mathbb{E}(X\mathbb{E}X) + \mathbb{E}[(\mathbb{E}X)^{2}] \\
&\mathbb{E}X \text{ is a constant. Can take out of expectation} \\
&=E[X^{2}]-2\mathbb{E}[X]\mathbb{E}[X]+(\mathbb{E}[X])^{2} \\
&= \mathbb{E}[X^{2}] - (\mathbb{E}X)^{2}
\end{align}
$$
### Variance/STD properties
$$
\begin{align}
Var(aX+b)=a^{2}Var(X) \\
SD(aX+b)=aSD(X)
\end{align}
$$
- If you add $b$ to every point, it doesn't affect the spread

**proof**:
$$
\begin{align}
Var(aX+b)&=\mathbb{E}(aX+b)^{2}-(\mathbb{E}(aX+b))^{2} \\
&=\mathbb{E }(a^{2}X^{2}+2abX+b^{2})-(a\mathbb{E}(X) + b)^{2} \\
&=a^{2}\mathbb{E}(X^{2})+2ab\mathbb{E}(X)+b^{2} - (a^{2}(\mathbb{E}(X))^{2}+2ab \mathbb{E}(X)+b^{2}) \\
&=a^{2}(\mathbb{E}(X^{2})-(\mathbb{E}(X))^{2})=a^{2} Var(X)
\end{align}
$$

# Cumulative distribution function (CDF)
The cumulative distribution function (CDF) or the distribution of $X$ is
$$
F_{X}(x) := P(X \leq x)
$$
For all $x \in \mathbb{R}$
- This is the sum of the probabilities up to a point
### Properties
1) F is non-decreasing
2) $\lim_{ x \to \infty }F_{X}(x)=1$
3) $\lim_{ x \to -\infty }F_{X}(x)=0$
4) $F_{X}(x)$ is right continuous
$$
\lim_{ u \to x^{+} } F_{X}(u)=F_{X}(x)
$$

# Examples
## If we toss a fair coin and $X$ is 2 if it's heads and $5$ if its tails. What is the expected value of $X$

1. Write the probability mass function

$$
P_X(x) =\begin{cases}
\frac{1}{2} & \text{if x = 2} \\
\frac{1}{2} & \text{if x=5} \\
0 & \text{otherwise}
\end{cases}
$$
2. Find the expectation
$$
\mathbb{E}(X)=2\left( \frac{1}{2} \right) + 5\left( \frac{1}{2} \right) = 3.5
$$

## Suppose $X=0$ with probability $\frac{1}{2}$, $X=1$ with probability $\frac{1}{4}$, ... $X=n$ with probability $\frac{1}{2^{n+1}}$. What's the expectation of $X$?
1. Is this a density function? Show it sums to 1
$$
\begin{align}
P(X=n)=\frac{1}{2^{n+1}} \text{ if $n\geq 0$, $n \in \mathbb{Z}$}
\sum_{i=0}^{\infty} \frac{1}{2^{n+1}} = 1
\end{align}

$$
So this is a density function

2. Find the expectation
$$
\begin{align}
\mathbb{E}(X)&=\sum_{i=0}^{\infty} n \cdot \frac{1}{2^{n+1}}= 0\left( \frac{1}{2} \right) + 1\left( \frac{1}{4} \right) + 2\left( \frac{1}{8} \right)+\dots \\
&=\frac{1}{4} \left[1+2\left( \frac{1}{2} \right) + 3 \left( \frac{1}{4} \right) + 4 \left( \frac{1}{8} \right)\right]
\end{align}
$$

The derivative of the series form of $\frac{1}{1-x}$ [[Calculus#Series]] looks like our expectation
$$
\frac{d}{dx}\left( \frac{1}{1-x} \right) = \frac{1}{(1-x)^{2}} = 1+2x+3x^{2}+4x^{3}
$$
$$
\implies \mathbb{E}(X)=\frac{1}{4}\left(  \frac{1}{\left( 1-\frac{1}{2} \right)^{2}} \right) = 1
$$

## Suppose we roll a fair die. Let $X=3$ if we roll 1 or 2, $X=4$ if we roll a 3 or 4, and $X=10$ if we roll 5 or 6. What is the mean of $X$?
$$
\mathbb{E}(X)=3\left( \frac{1}{3} \right) + 4\left( \frac{1}{3} \right) + 10 \left( \frac{1}{3} \right) = \frac{17}{3}
$$

## Consider a discrete random variable taking only positive integer values with $P_{X}(n)=\frac{1}{n(n+1)}$. What is $\mathbf{E}(X)$
$$
\mathbb{E}(X)=\sum_{i=1}^{\infty} n \left( \frac{1}{n(n+1)} \right) = \sum_{i=1}^{\infty} \frac{1}{n+1} = +\infty
$$

## Suppose we roll a fair die and let $X$ be the number that is rolled. What is $\mathbb{E}[X^{2}]$
Let $X=1,2,3,4,5,6$. Then $X^{2}=1, 4, 9, 16, 25, 36$
$$
\mathbb{E}X^{2}=(1)\left( \frac{1}{6} \right)+(4)\left( \frac{1}{6} \right)+\dots+(36)\left( \frac{1}{6} \right)
$$
## We are flipping a fair coin and $X=-1$ if tails, $X=1$ if heads.
1. calculate the first moment of $X$
$\mathbb{E}[X]=(-1)\left( \frac{1}{2} \right) + (1)\left( \frac{1}{2} \right)=0$

2. Calculate the variance of $X$ (we still consider the probability of the outcomes)
$$
\begin{align}
Var(X)&=\mathbb{E}[(X-0)^{2}] = E[X^{2}]\\
&=(-1-0)^{2}\left( \frac{1}{2} \right) + (1-0)^{2}\left( \frac{1}{2} \right) \\
&=1 \\ \\
SD(X)=+\sqrt{ 1 }=1
\end{align}

$$
### Now $X=-10$ if tails, $X=10$ if heads
$\mathbb{E}[X]=0$
$$
\begin{align}
Var(X)&=\mathbb{E}[(X-0)^{2}]=E[X^{2}] \\
&=(-10)^{2}\left( \frac{1}{2} \right)+(10)^{2}\left( \frac{1}{2} \right) \\
&=100 \\ \\
SD(X)&=\sqrt{ 100 }=10
\end{align}
$$
## Let $X$ be the number after a fair die is rolled. 
1. What is $\mathbb{E}[X]$
$$
\mathbb{E}X=1\left( \frac{1}{6} \right)+2\left( \frac{1}{6} \right)+3\left( \frac{1}{6} \right)+\dots+6\left( \frac{1}{6} \right) = \frac{7}{2}
$$
2. Find the variance
$$
\begin{align}
Var(X) &= \mathbb{E }\left[ \left( X-\frac{7}{2} \right)^{2} \right] \\
&= \left( 1-\frac{7}{2} \right)^{2}\left( \frac{1}{6} \right)+\dots+\left( 6-\frac{7}{2} \right)^{2}\left( \frac{1}{6} \right) \\
&=\left( -\frac{5}{2}  \right)^{2}\left( \frac{1}{6} \right) + \left( -\frac{3}{2} \right)^{2}\left( \frac{1}{6} \right)+\dots+\left( \frac{5}{2} \right)^{2}\left( \frac{1}{6} \right) = \frac{35}{12}
\end{align}
$$

## The density of $X$ is given by $p_{X}(n)=e^{-\lambda} \frac{\lambda^{n}}{n!}, \text{ n=0, 1, 2...}$
1. Is this a density function? Does $p_{X}(n)$ it sum up to 1?
This is actually a variation of the taylor series expansion of $e$
$$
e^{-\lambda} \sum_{i=0}^{\infty} \frac{\lambda^{n}}{n!}=e^{-\lambda}e^{\lambda}=1
$$
### What is the probability that $X=0$?
$$
P(X=0)=p_{X}(0)=e^{-\lambda} \cdot \frac{\lambda^{0}}{0!}=e^{-\lambda}
$$
### What is the probability that $X>2$?
Make sure to count the complement because it is an infinite series
$$
\begin{align}
P(X>2)&=1-P(x\leq 2) \\
&=1-[P(X=0) + P(X=1)+P(X=2)] \\
&= 1 - e^{-\lambda} - e^{-\lambda}\lambda - e^{-\lambda} \frac{\lambda^{2}}{2!}
\end{align}
$$


## Suppose $X$ has the following density function (PMF):
$p_{X}(0)=\frac{1}{8}, p_{X}(1)=\frac{3}{8}, p_X(2) = \frac{3}{8}, p_{X}(3)=\frac{1}{8}$. What is the distribution of X?
- Density means PMF while distribution means the CDF

$$
P_{X}(x)=\begin{cases}
0 & \text{if } x < 0 \\
\frac{1}{8} & \text{ if } 0\leq x<1 \\
\frac{1}{8}+\frac{3}{8}=\frac{1}{2} & \text{ if } 1 \leq x \leq 2 \\
\frac{1}{2} + \frac{3}{8}= \frac{7}{8} & \text{ if } 2 \leq x < 3 \\
1 & \text{ if } 3 \leq x 
\end{cases}
$$
![[Drawing 2024-02-09 12.31.11.excalidraw]]

### Let $X$ have the distribution (CDF)
$$
F_{X}(x)=\begin{cases}
0 & x < 0 \\
\frac{x}{2} & 0\leq x<1 \\
\frac{2}{3}  & 1\leq x<2 \\
\frac{11}{12} & 2\leq x < 3 \\
1 & 3 \leq x
\end{cases}
$$
#### What is $P(X\leq 3)$
$$
F_{X}(3)=P(X\leq 3) = 1
$$
#### What is $P(X<3)$
$$
P(X<3)=\lim_{ x \to 3^{-} } F_{X}(x)=\frac{11}{12}
$$
#### What is $P(X=3)$?
$$
P(X=3)=P(X\leq 3)-P(X < 3)=1-\frac{11}{12}=\frac{1}{12}
$$
#### $P(2 < x \leq 4)=?$
$$
P(x\leq 4) - P(x\leq 2)
$$

## Suppose $X$ is a random variable with $\mathbb{E}(X^{2})$ and $Var(X)=12$
#### $\mathbb{E}(X^{2})=?$
$$
\begin{align}
Var(X)=\mathbb{E}(X^{2})-(\mathbb{E}(X))^{2} \\
\implies \mathbb{E}(X^{2})=12+(50)^{2}=2512
\end{align}
$$
#### $\mathbb{E}(3x+2)=?$ 
$$
3\mathbb{E}(X) + 2 = 152
$$

### $Var(-X)$
$$
\begin{align}
Var(-X)=(-1)^{2}Var(X) \\
= Var(X)
\end{align}
$$
Reflecting doesn't affect spread of data

### $SD(2X)$
$$
\begin{align}
SD(2X)=\sqrt{ Var(2X) }=\sqrt{ 2^{2} Var(X) }=2SD(X)
\end{align}
$$
## Is there a random variable with $\mathbb{E}(X)=4$ and $\mathbb{E}(X^{2})=10$?
No because then you would get a negative variance
$$
\begin{align}
Var(X)&=\mathbb{E}(X^{2}) - (\mathbb{E}(X))^{2} \\
&=10-(4)^{2} =-6
\end{align}
$$

## Mark has an $8\%$ chance of getting into a car accident in the next year. If he has an accident, the insurance company will write him a check for 10k. The company decides to charge Mark a $200 premium for the year of insurance. What is the insurance company's expected profit?
- We need a density function. $x$ is the spec
$$
\begin{align}
P_{X}(200)=0.92 \\
P_{X}(200-10000)=0.08
\end{align}
$$
$$
\mathbb{E}(X)=200(0.92)+(-9800)(0.08)=-600
$$