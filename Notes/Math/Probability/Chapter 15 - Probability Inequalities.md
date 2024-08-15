# Markov's inequality
If $X\geq 0$ and $a>0$, then 
$$
P(X\geq a) \leq \frac{\mathbb{E}[X]}{a}
$$
# Chebyshev's inequality
If $X$ is a random variable and $b>0$ then
$$
P(\left|X- \mathbb{E}[X] \right| \geq b) \leq \frac{Var(X)}{b^{2}}
$$
The probability we are b units away from the mean is <= var/b^2

# Chernoff bounds
Let $m_{X}(t)$ be a MGF (moment generating function), then for any $a \in \mathbb{R}$
$$
\begin{align}
P(X\geq a) \leq \min_{t>0} e^{-ta}m_{X}(t) \\
\end{align}
$$
You can use the derivative to find the minimum/critical points

# Cauchy-Schwarz inequality
$$
(\mathbb{E}[XY])^{2} \leq (\mathbb{E}[X])^{2} (\mathbb{E}[Y])^{2}
$$
This is equality iff $X=aY$




# Jensen's inequality
**Background:**
If $g$ is a twice differentiable function
If $g''(x)<0$ on $[a,b]$ then $g$ is **concave** on $[a,b]$
If $g''(x)>0$ on $[a,b]$ then $g$ is **convex** on $[a,b]$

If $P(a \leq X \leq b)=1$ (the pdf is 0 outside of this interval). If $g: \mathbb{R} \to \mathbb{R}$ is
1) convex on $[a, b]$ then
$$
\mathbb{E}[g(X)] \geq g(\mathbb{E}[X])
$$

2) concave on $[a, b]$ then 
$$
\mathbb{E}[g(X)] \leq g(\mathbb{E}[X])
$$

# Examples
## If $X \sim Binom(n, p)$. 
Then $X\geq0$ and the value it can take on is up to n (it is sum of n bernoulli trials)

If $p<q<1$ use markov's inequality
$$
P(X\geq nq) \leq \frac{np}{nq} = \frac{p}{q}
$$
- is a constant bound on the probability

## If $X \sim Binom(n, p)$ then $Var(X) = np(1-p)$
If $p<q<1$ 

$$
\begin{align}
P(X\geq nq) &= P(X-np \geq nq-np) \\
&\leq P(|X-np| \geq n(q-p)) \text{ this counts both tails of dist} \\
&\text{use Chebyshev's inequality} \\
\leq \frac{np(1-p)}{(n(q-p))^{2}} = \frac{p(1-p)}{n(q-p)^{2}}
\end{align}
$$
- chebyshev collapses to 0


## If $X \sim Binom(n, p)$ then
$$
m_{X}(t)=(pe^{t} + (1-p))^{n}
$$
If we want to bound the probability of this then 
$$
P(X \geq nq) \leq \min_{t>0} e^{-tnq}(pe^{t}+(1-p))^{n}
$$
Let $f(t)=e^{-tnq}(pe^{t}+(1-p))^{n}$. Take the derivative
$$
\begin{align}
f'(t)&=e^{-tnq}n(pe^{t}+(1-p))^{n-1} (pe^{t}) -nqe^{-tnq} (pe^{t}+(1-p))^{n} = 0 \\
&npe^{t}e^{-tnq}(pe^{t}+(1-p))^{n-1}=nqe^{-tnq}(pe^{t}+(1-p))^{n} \\
&pe^{t}=q(pe^{t}+(1-p)) \\
&pe^{t}-pqe^{t} = q(1-p) \\
& e ^{t} = \frac{q(1-p)}{p(1-q)}
\end{align}
$$

Plug the value of $e^{t}$ into $f(t)$
$$
\begin{align}
P(X \geq nq) &\leq \min_{t>0} e^{-tnq}(pe^{t}+(1-p))^{n} \\
& \leq \left(\frac{q(1-p)}{p(1-q)}\right)^{-nq}\left(p\left(\frac{q(1-p)}{p(1-q)} \right) + (1-p) \right)^{n} \\
&= \left( \frac{p}{q} \right)^{nq} \left( \frac{1-p}{1-q} \right)^{n(1-q)}
\end{align}

$$- the bound collapses exponentially to 0

### Numerical example
If $p=\frac{1}{2}$, $q=\frac{3}{4}$ then
**Markov:** $$
P\left( X\geq \frac{3n}{4} \right) \leq \frac{2}{3}
$$
**Chebyshev** $$
P\left( X\geq \frac{3n}{4} \right) \leq \frac{4}{n}
$$
**Chernoff**
$$
P\left( X\geq \frac{3n}{4} \right) \leq \left( \frac{16}{27} \right)^{n/4}
$$



## Suppose $a_{1}, \dots ,a_{n}$ are positive numbers and $X$ is a discrete random variable with density $p_{X}(a_{k})=\frac{1}{n}$ for $k=1\dots n$. If $g(x)=-\ln(x)$ then $g$ is convex on $(0, \infty)$

- The expected value of $X$ is the arithmetic mean because everything has equal probability
By Jensen's inequality
$$
\begin{align}
-\ln(\mathbb{E}[X]) \leq \mathbb{E}[-\ln(X)] \\
-\ln\left( \frac{1}{n} \sum a_{k} \right) \leq \frac{1}{n} \sum(-\ln a_{k})
\end{align}
$$
Raise both sides to the $e$
$$
\begin{align}
\left( \frac{1}{n}\sum a_{k} \right)^{-1} \leq e^{\ln(a_{1}\dots a_{n})^\left( -\frac{1}{n} \right)} \\
\left( \frac{1}{n}\sum a_{k} \right)^{-1} \leq (a_{1}\dots a_{n})^{1/n} \\
\frac{1}{n}\sum a_{k} \geq (a_{1}\dots a_{n})^{1/n}
\end{align}
$$
The arithmetic mean is bounded by the geometric mean

## $g(x)=x^{2}$
Therefore $\mathbb{E}[X^{2}] \geq (\mathbb{E}[X])^{2}$
$$
\begin{align}
\mathbb{E}[X^{2}] - (\mathbb{E}[X])^{2} \geq 0 \\
Var(X) \geq 0
\end{align}
$$

## Let $X \sim Exp(\lambda)$. Then $f_{X}(x)=\lambda e^{-\lambda x}$, $x\geq0$.
Find $P(X \geq n \lambda)$ and then find the bounds on this probability

$$
\begin{align}
\int _{n\lambda}^{\infty} \lambda e^{-\lambda x} \, dx \\
-e^{-\lambda x}|_{n\lambda}^{\infty} = e^{-\lambda^{2} n} 
\end{align}
$$
**Markov's inequality**
$$
\begin{align}
P(X \geq n \lambda) \leq \frac{\mathbb{E}[X]}{n\lambda} = \frac{1}{n\lambda^{2}} \\
e^{-\lambda^{2}n} \leq \frac{1}{n\lambda^{2}}
\end{align}
$$

**Chebyshevs**
$$
\begin{align}
P(X \geq n \lambda) = P\left( X - \frac{1}{\lambda} \geq n \lambda - \frac{1}{\lambda} \right) \leq P\left( \left|X - \frac{1}{\lambda}\right| \geq \frac{n\lambda^{2}-1}{\lambda} \right)  \\
P\left( \left|X - \frac{1}{\lambda}\right| \geq \frac{n\lambda^{2}-1}{\lambda} \right)  \leq Var(X) \left( \frac{\lambda}{n\lambda^{2}-1} \right)^{2} \\
Var(X) \left( \frac{\lambda}{n\lambda^{2}-1} \right)^{2} = \frac{1}{\lambda^{2}} \frac{\lambda^{2}}{n\lambda^{2}- 1} = \frac{1}{n\lambda^{2}-1}
\end{align}
$$
**Chernoff**
$$
P(X \geq n \lambda) \leq min_{t>0} e^{-tn\lambda} m_{X}(t)
$$
The moment generating function for the exponential is $m_{X}(t)=\frac{\lambda}{\lambda-t}$. Minimize the RHS of inequality

$$
\begin{align}
f(t)=e^{-tn\lambda} \left( \frac{\lambda}{\lambda-t} \right) \\
f'(t)=e^{-tn\lambda}\frac{\lambda}{(\lambda-t)^{2}} + (-n \lambda) e^{-tn\lambda}\left( \frac{\lambda}{\lambda-t} \right)=0 \\
n\lambda=\frac{1}{\lambda-t} \\
\lambda-t=\frac{1}{n\lambda} \\
t=\frac{n\lambda^{2}-1}{n\lambda} \leq e^{((n\lambda^{2}-1)/n\lambda) (-n\lambda)}  \\
\implies P(X \geq n \lambda) \leq n \lambda^{2}e^{}
\end{align}
$$

## Suppose $X>0$ and $Var(X)>0$. Which is larger?
a) $\mathbb{E}[X^{4}]$ or $(\mathbb{E}[X])^{4}$
If $g=x^{4}$ => $g''=12x^{2}>0$ => g is convex
Therefore $\mathbb{E}[X^{4}] \geq (\mathbb{E}[X])^{4}$

b) $\mathbb{E}[e^{X}]$ vs $e^{\mathbb{E}[X]}$
If $g(x)=e^{X}$ => $g''=e^{x}>0$
g is convex
$$
\mathbb{E}[e^{X}] \geq e^{\mathbb{E}[X]}
$$

c) $\mathbb{E}[\ln(X+1)]$ versus $\ln(\mathbb{E}[X]+1)$
$g=\ln(x+1) \implies g'=\frac{1}{x+1} \implies g'' = -\frac{1}{(x+1)^{2}} < 0$ so g is concave
$$
\implies \mathbb{E}[\ln(X+1)] \leq \ln(\mathbb{E}[X]+1)
$$



## A survey finds that the average american family produces 17.2 pounds of glass garbage annually with SD 2.5. What is the probability that the average of 55 randomly selected families is between 17 and 18 pounds

Let X=sample mean=$\frac{1}{n}S_{n}$. The CLT says that 
$$
P\left( a\leq \frac{S_{n}-n\mu}{\sigma \sqrt{ n }} \leq b \right) \to P(a \leq Z \leq b)
$$
We want to find X from the partial sum so divide by 1/n
$$
\begin{align}
P\left( a\leq \frac{X-\mu}{\left( \frac{\sigma}{n} \right)} \leq b \right) \to P(a \leq Z \leq b) \\
P\left( \frac{17-17.2}{\frac{2.5}{(\sqrt{ 55 })}} \leq Z \leq \frac{18-17.2}{\frac{2.5}{\sqrt{ 55 }}}\right) \\
\approx 0.7146
\end{align}
$$
