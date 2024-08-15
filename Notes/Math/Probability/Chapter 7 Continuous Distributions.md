**Support** - all non-zero probability intervals

**Definition**: A random variable $X$ is said to have a continuous distribution if there exists some function $f$ or $f_{X}$ such that 
$$
P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx 
$$
for all $a, b$. $f$ is called the density or PDF for $X$.

Specifically, $X$ has an absolutely continuous distribution
- PMF is discrete, PDF is continuous

## Properties
$$
\begin{align}
\int _{\infty}^{\infty} f(x) \, d=1=P(-\infty < x < \infty)  \\
P(X=a)=\int _{a}^{a} f(x) \, dx = 0 
\end{align}
$$
- Points do not have any probability

# Cumulative distribution function of X (CDF)
Probability of getting a value up to $k$ 
$$
F(k)=F_{X}(k)=P(-\infty < k \leq k) = \int _{-\infty}^{k} f(x)\, dx 
$$
- The density at a certain point is defined as the rate of change of the CDF at that point by the fundamental theorem of calculus
- Derivative of the CDF is the PDF
$$
F'(k)=f(k)
$$

# Expectation
For a continuous random variable with density $f$ we define the expectation of $X$ to be
$$
\mathbb{E}[X] = \int _{-\infty}^{\infty} x f(x)dx
$$
If the integral converges absolutely. In this case we say $X$ is integrable
=> the order you add the rectangles doesn't matter

[[Calculus#Series]]
**Absolutely convergent if**
$$
\int _{-\infty}^{\infty} |x|f(x) \, dx < \infty 
$$
- Not all density functions have finite expectation!!

## Advanced calculus techniques
Suppose $X$ is a non-negative continuous random variable with a finite expectation. Then there is a sequence of discrete random variables $\{ X_{n} \}^{\infty}_{n=1}$ such that
$$
\mathbb{E}[X_{n}] \to_{n\to \infty} \mathbb{E}[X]
$$
- If you have the right sequence of discrete distributions (and their expectation), then you can approximate the continuous one with the sum of the discrete ones
- This is very important because it is hard to prove some results directly in the continuous case. But if we can use sums of discrete distributions we can use the same results from the discrete case

ex: showing linearity
$$
\begin{align}
\mathbb{E}(X+Y)&=\int _{\infty}^{\infty} (x+y)f_{X+Y}(x+y) \, d(x+y)  \\ \\
&\vdots \text{ very very hard to do this} \\
&= \mathbb{E }[X] + \mathbb{E}[Y] \\
&= \lim_{ n \to \infty } \mathbb{E}(X_{n}+Y_{n}) \\
&= \lim_{ n \to \infty } \mathbb{E}X_{n}+\mathbb{E}Y_{n} \\
\end{align}
$$

# Moments
If $X$ is a continuous random variable and $g$ is a real valued function, then
$$
\mathbb{E}[g(X)]= \int _{-\infty}^{\infty} g(x)f(x) \, dx 
$$
In particular, the $n$th moment of $X$ is
$$
\mathbb{E}(X^{n}) = \int _{-\infty}^{\infty} x^{n} f(x) \, dx 
$$


**Proof** Define $X_{n}(\omega)=\frac{k}{2^{n}}$ if $\frac{k}{2^{n}} < X(\omega) < \frac{k+1}{2^{n}}$
- Main idea: Like taking the lower rectangular approximation of an integral, but the boxes are of different widths. 
- Chop the height of the curve into multiples of $\frac{k}{2^{n}}$ (we choose this specific multiple)

$$
\begin{align}
0 \leq \mathbb{E}X-\mathbb{E}X_{n} \\
= \int _{0}^{\infty}xf(x) \, dx - \sum_{k=1}^{\infty}\int _{\frac{k}{2^{n}}}^{(k+1)/2^{n}} \frac{k}{2^{n}} f(x)\, dx \\
= \sum_{k=1}^{\infty}\left( \int _{\frac{k}{2^{n}}}^{(k+1)/2^{n}} \left[xf(x)-\frac{k}{2^{n}}f(x) dx \right]\right) \\

\leq \sum_{i=1}^{\infty} \frac{1}{2^{n}} \int _{\frac{k}{2^{n}}}^{(k+1)/2^{n}} f(x)dx=\frac{1}{2^{n}} \\

0 \leq \mathbb{E}X-\mathbb{E}X_{n} \leq \frac{1}{2^{n}} \\
1/2^n \to 0 \text{ as } n\to \infty \\
\implies \mathbb{E}X_{n} \to \mathbb{E}X \text{ as } n \to \infty
\end{align}
$$




# Distributions
## Uniform
A random variable $X$ has the uniform distribution on $[a, b]$ if
$$
f_{x}(x) = \begin{cases}
\frac{1}{b-a} & a \leq x \leq b \\
0 & \text{otherwise}
\end{cases}
$$


# Examples
## Suppose $f(x)=\frac{c}{x^{3}}$ for $x\geq 1$ is a density for $X$. What is $c$?
- This implies that $f=0 \text{ for } x<1$

Since $f$ is a PDF, then 
$$
\begin{align}
1=\int _{\infty}^{\infty} f(x) \, dx=\int _{1}^{\infty} \frac{c}{x^{3}} \, dx   \\
1=c \left[\frac{1}{-2} x ^{-2}\right]_{1}^{\infty} \\
1=c\left[ 0 - \left( -\frac{1}{2} \right) \right] \\
1=\frac{c}{2} \\
\implies c=2
\end{align}
$$

Any continuous function can be made into a density function over a specific interval by dividing over

**expected value**
$$
\begin{align}
\mathbb{E}[X]&=\int _{1}^{\infty} x \frac{2}{x^{3}} \, dx  \\
&=2\int _{1}^{\infty}x^{-2} \, dx = 2\left[ -\frac{1}{x}  \right]^{\infty}_{1} = 2
\end{align}
$$



## What is $\mathbb{E}[X], Var(x)$ for a uniform distribution?
You only need to integrate over the support (non-zero probability)
$$
\begin{align}
\mathbb{E}X = \int_{a}^{b} x\left( \frac{1}{b-a} \right) \, dx  \\
&= \frac{1}{b-a}\left[ \frac{1}{2}x^{2} \right]_{a}^{b} = \frac{1}{b-a} \left( \frac{b^{2}}{2} - \frac{a^{2}}{2} \right) \\
&=\frac{b^{2}-a^{2}}{2(b-a)} = \frac{b+a}{2}
\end{align}
$$

$$
\begin{align}
Var(X) = \mathbb{E}X^{2}-(\mathbb{E}X)^{2}
&= \int _{a}^{b} x^{2}\left( \frac{1}{b-a} \right) \, dx - \left( \frac{b+a} {2}\right) ^{2} \\
&= \frac{b^{3}-a^{3}}{3(b-a)} - \left( \frac{b^{2}+2ab+a^{2}}{4} \right) \\ \\
&= \frac{b^{2}+2ab+a^{2}}{3} - \left( \frac{b^{2}+2ab+a^{2}}{4} \right) \\
&=\frac{b^{2} + 2ab + a^{2} }{12}  \\
&= \frac{(b-a)^{2}}{12} 
\end{align}
$$

## What is $F_{X}(x)$ and what is $P(3 \leq X \leq 4)$?
Let $u=x$
$$
F_{X}(x)=\int _{1}^{x} \frac{2}{u^{3}} \, du = \left[ -\frac{1}{u^{2}} \right]^{x}_{1} = 1-\frac{1}{x^{2}}
$$

Using the PDF
$$
\int_{3}^{4} \frac{2}{x^{3}} \, dx = \left[ -\frac{1}{x^{2}} \right]_{3}^{4}=-\frac{1}{16}+\frac{1}{9}=\frac{7}{144} 
$$

Using the CDF. It is easier since we can just use the different of two different evals of CDF
$$
F_{X}(4) - F_{X}(3) = \left( 1-\frac{1}{4^{2}} \right)-\left( 1-\frac{1}{3^{2}}\right) = \frac{7}{144}
$$

## Suppose  $$f_{X}(x)=\begin{cases}
2x & \text{ if } 0\leq x < 1 \\
0 & \text{otherwise}
\end{cases}$$ what is the expected value of X?
$$
\mathbb{E}X = \int _{0}^{1}x (2x) \, dx = \frac{2}{3}[x^{3}]_{0}^{1}=\frac{2}{3}
$$

$$
Var(X) = \int_{0}^{1}x^{2} (2x) \, dx - \left( \frac{2}{3} \right)^{2}= \frac{1}{2}[x^{3}]_{0}^{1} - \frac{4}{9}=  \frac{1}{18}
$$

## Suppose $$
f_{X}(x)=\begin{cases}
ax+b & 0 \leq x < 1 \\
0 & \text{otherwise}
\end{cases}
$$ and a moment condition of  $\mathbb{E}[X^{2}]=\frac{1}{6}$. What is $a$ and $b$?
Apply the moment condition
$$
\begin{align}
\frac{1}{6}&=\mathbb{E}{X^{2}} = \int _{0}^{1} x^{2} (ax+b) \, dx  \\
&= \int _{0}^{1} ax^{3}+bx^{2} \, dx = \frac{1}{4}a+\frac{1}{3}b
\end{align}
$$

We also know the density must be equal to 1
$$
1=\int _{0}^{1}ax+b \, dx =\frac{1}{2}a+b
$$

Now we have two equations
$$
\begin{align}
\begin{cases}
\frac{1}{6} = \frac{1}{4}a + \frac{1}{3}b \\
1=\frac{1}{2}a+b
\end{cases} \\

\begin{cases}
2 = 3a + 4b \\
2=a+2b
\end{cases} \\
a=-2, b=2
\end{align}
$$

## The UPhone has a battery life given by a random variable $X$ (in hours) with PDF $$
f_{X}(x) = \begin{cases}
\frac{10}{x^{2}} & x \geq 10 \\
0 & x < 10
\end{cases}
$$ 
### a) What is the probability that the phone lasts more than 20 hours
$$
P(X > 20) = \int _{20}^{\infty} \frac{10}{x^{2}} \, dx = -10\left[ \frac{1}{x} \right]_{20}^{\infty} = 0+\frac{10}{20}=\frac{1}{2} 
$$

### b) what is the CDF?
$$
F_{X}(k) = \int _{-\infty}^{x} \frac{10}{u^{2}} \, du =   \int _{10}^{x} \frac{10}{x^{2}} \, du = 1-\frac{10}{x}
$$

## Let $$
f_{X}(x) = \begin{cases}
\frac{2}{x^{2}} & x \geq 2 \\
0 & x< 2
\end{cases}
$$ what is the expected value?
$$
\mathbb{E}X=\int _{2}^{\infty} x\frac{2}{x^{2}} \, dx = [2\ln(x)]_{2}^{\infty} = +\infty
$$
This function is not integrable! It does not have a first moment but it does have a second moment
