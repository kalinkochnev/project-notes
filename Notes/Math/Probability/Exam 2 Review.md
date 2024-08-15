# Discrete distributions
![[Chapter 6 - Discrete Distributions#Cheat sheet]]

# Continuous Distributions
![[Chapter 7 Continuous Distributions#Properties]]

**Expectation**


**Moment**
$$
\mathbb{E}[g(X)]= \int _{-\infty}^{\infty} g(x)f(x) \, dx 
$$

**Cumulative distribution function**
Probability of getting a value up to $k$ 
$$
F(k)=F_{X}(k)=P(-\infty < k \leq k) = \int _{-\infty}^{k} f(x)\, dx 
$$

## Normal distributiosn
**Proposition**: If $X \sim N(\mu, \sigma^{2})$ then
$$
f_{X}(x) = \frac{1}{\sigma \sqrt{ 2\pi }} e ^{-\frac{(x-\mu)^{2}}{2 \sigma^{2}}}
$$
Also $\mathbb{E}[X]=\mu$ and $Var(X)=\sigma^{2}$

[[Chapter 10 - Continuous Distributions]]
[[Chapter 11 - Multivariate Distributions]]

# Review questions
## Discrete distributions
[[Chapter 5 - Discrete Random Variables#Suppose $X=0$ with probability $ frac{1}{2}$, $X=1$ with probability $ frac{1}{4}$, ... $X=n$ with probability $ frac{1}{2 {n+1}}$. What's the expectation of $X$?|Suppose $X=0$ with probability $ frac{1}{2}$, $X=1$ with probability $ frac{1}{4}$, ... $X=n$ with probability $ frac{1}{2 {n+1}}$. What's the expectation of $X$?]]

[[Chapter 6 - Discrete Distributions#Examples]]

## Continuous distributions
**What is $\mathbb{E}[X], Var(x)$ for a uniform distribution?**

**Suppose** $$
f_{X}(x)=\begin{cases}
ax+b & 0 \leq x < 1 \\
0 & \text{otherwise}
\end{cases}
$$ **and a moment condition of  $\mathbb{E}[X^{2}]=\frac{1}{6}$. What is $a$ and $b$?**



## Normal distributions
UConn professor salaries are approximately normally dist. Suppose you know 33% of professors make <80k and 33% make more than 120k. What is $P(70k < X < 80k)$

