# Uniform distribution
$X \sim Unif(a,b)$ if 
$$
f_{X}(x) = \begin{cases}
\frac{1}{b-a}\text{ if } a\leq x \leq b \\
0
\end{cases}
$$

# Exponential distribution
$X \sim Exp(\lambda), (\lambda > 0)$ if
$$
f_{X}(x) = \lambda e^{-\lambda x}, x \geq 0
$$

- The poisson distribution models number of events per unit time
- The exponential distribution models the amount of time between two events occuring
- $\lambda$ is the rate at which events occur
- $P(X<x)$ is the probability of waiting at most $x$ seconds between events

X = # of cars passing a light per hour => $X \sim Poisson$
X = time between two cars passing a light => $X \sim Exp$

if $X \sim Exp(\lambda),$ then $\mathbb{E}[X] = \frac{1}{ \lambda}, Var(x)=\frac{1}{\lambda^2}$

- Exponential distributions are "memoryless" 
$$
P(X > s+t \mid x > t) = P(X > s)
$$
- probability of going t more minutes is the same as going s minutes to begin with

**Proof**
$$
\begin{align}
P(X >k) = \int _{k}^{\infty} \lambda e^{-\lambda x} \, dx  \\
= -\frac{\lambda}{\lambda}[e^{-\lambda x}]_{k}^{\infty} \\
 = 0 - (-e^{-\lambda k}) = e ^{-\lambda k}
\end{align}
$$

$$
\begin{align}
 P(X > s + t \mid x > t) &= \frac{P(X > s + t \cap x > t)}{P(X > t)}  \\
&= \frac{P(X > s + t)}{P(X > t)} \\
&= \frac{e^{-\lambda (s+t)}}{e^{-\lambda t}} = e ^{-\lambda s} = P(X > s)
\end{align}
$$

# Gamma distribution
$X \sim \Gamma(\alpha, \theta)$ if 
$$
f_{X}(x)= \frac{\alpha e^{-\alpha x}(\alpha x)^{\theta-1}}{\int _{0}^{\infty} e^{-y} y^{\theta-1} \, dy }\text{ if } x \geq 0
$$

**Note:**
$$
\int _{0}^{\infty} e ^{-y} y^{\theta-1} \, dx = \Gamma(\theta)
$$
If $n \in \mathbb{N}, \Gamma(n)=(n-1)!$
- The gamma function is like an extrapolation of the factorial

- Measure the time between two events
- $\alpha$=  success probability, $\theta$ = # of events
- Models the time between the 1st and theta'th event

# Chi squared distribution with n degrees of freedom
If $\alpha=\frac{1}{2}, \theta=\frac{n}{2}$ then
$$
\Gamma\left( \frac{1}{2}, \frac{n}{2} \right) := X_{n}^{2}
$$
is the chi-squared distribution with n degrees of freedom

- is the distribution of a sum of the squares of k ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) [independent](https://en.wikipedia.org/wiki/Independence_(probability_theory) "Independence (probability theory)") [standard normal](https://en.wikipedia.org/wiki/Standard_normal "Standard normal") random variables. The chi-squared distribution is a special case of the [gamma distribution](https://en.wikipedia.org/wiki/Gamma_distribution "Gamma distribution")

- If $Z \sim N(0, 1)$, then $Z^{2} := X^2$ with an infinite number of degrees of freedom

# Beta distribution
$X \sim B\eta(\alpha, \beta)$ if
$$
f_{X}(x) = \frac{1}{\int _{0}^{1}x^{\alpha -1 } (1-x)^{\beta-1}\, dx } x^{\alpha-1} (1-x)^{\beta-1} \text{ for } 0< x < 1
$$

- Models a probability distribution of probabilities

Also
$$
\int _{0}^{1}x^{\alpha-1}(1-x)^{\beta-1} \, dx = B(\alpha, \beta) = \frac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha+\beta)}
$$

# Cauchy distribution
$X \sim Cauchy(0, 1, \theta)$ if 
$$
f_{X}(x) = \frac{1}{\pi} \frac{1}{1+(x-\theta)^{2}}
$$- usually the counter example when wanting to test a new theorem in probability
- has no finite moments
$\mathbb{E}[X^{n}]$ is undefined for $n\geq 1$

- It is surprising because it is symmetric and bell shapes
- it has "fat" tails

- You have a high probability of extreme events happening
- Usually comes up with things that are spinning


# Finding density of a function applied to a distribution
If X is a continuous random variable and $Y=g(X)$, can you find $f_{Y}(x)$?

1) if $X \sim Unif(0, 1)$ and $Y=-\ln(x)$ what is $f_{Y}(x)$

$Y>0$ since $x \in[0, 1]$

$$
\begin{align}
F_{y}(x)=P(Y \leq x)= P(-\ln(X) \leq x) \\
P(\ln(X) \geq -x) \\
P(X \geq e^{-x}) \\
1-P(X\leq e^{-x}) \\
= 1- F_{X}(e^{-x}) \\
\implies F_{Y}(x) = 1- F_{X}(e^{-x}) \\
\text{ take derivatives of both sides} \\
f_{Y}(x) = 0-f_{X}(e^{-x}) (-e^{-x}) = e^{-x} \implies Y \sim Exp(1)
\end{align}
$$
We know that x is uniform on $[0, 1]$ so $$
f_{X}(e^{-x})=1
$$
