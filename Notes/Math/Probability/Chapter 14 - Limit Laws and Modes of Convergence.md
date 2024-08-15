Suppose we have a probability space consisting of a sample space $\Omega$, a $\sigma$ field $F$, and a probability $P$ on $F$. We are going to consider a collection of random variables $X$ all defined on the same probability space.

**Def**: We say a sequence $\{ X_{i} \}_{i=0}^{\infty}$ of random variables is **independent and identically distributed (iid)** if they are mutually independent and all have the same distribution.

$S_{n}=\sum_{i=1}^{n}X_{i}$ is the "partial sum process".
- If $X_{i}$ are discrete or continous and are identically distributed  then they have the same probability density.

# Strong law of large numbers (SLLN)
Suppose $\{ X_{i} \}_{i=0}^{\infty}$ is **iid**, with $\mathbb{E}|X_{i}|<\infty$ and let $\mathbb{E}[X_{i}]=\mu$. Then the SLLN says 
$$
\frac{S_{n}}{n}=\frac{1}{n} \sum_{i=1}^{n}X_{i} \to_{n\to \infty} \mu
$$
- Convergence here means $\frac{S_{n}(\omega)}{n}\to \mu$ for every $\omega \in \Omega$ except possibly a set $\omega_{0}$ of probability zero
- This is sometimes called "almost sure" convergence

# Weak law of large numbers (WLLN)
Suppose $\{ X_{i} \}_{i=1}^{\infty}$ **idd** with finite first and second moments. For every $\varepsilon> 0$
$$
P\left( \left|\frac{S_{n}}{n}-\mathbb{E}[X_{1}] \right| > \varepsilon \right) \to_{n\to \infty} 0
$$
- the probability that the difference between the expectation of a random variable and the population mean being greater than some epsilon approaches 0 as the number of samples increases
- Sample mean converges to the population mean

# Central Limit Theorem (CLT)
If $\{ X_{i} \}_{i=1}^{\infty}$ **iid** with finite variances ($\mathbb{E}[X_{i}]^{2} <\infty$). Let $\mu=\mathbb{E}[X_{i}]$ and $\sigma^{2}=Var(X_{i})$ then
$$
P\left( a \leq \frac{S_{n} - n \mu}{\sqrt{ n } \sigma} \leq b \right) \to_{n\to \infty} P(a\leq Z \leq b)
$$
Where $a,b \in \mathbb{R}$ and $Z \sim N(0, 1)$

- "convergence of distribution" - with enough samples a distribution begins to look more and more normal

**Def**: Let $\{ X_{i} \}_{i=1}^{\infty}$ be a sequence with CDFs $F_{i}(x)$. If $X$ is a random variable defined on the same space with CDF $F_{X}(x)$ then we say $\{  X_{i} \}$ converges weakly or converges in distribution to $X$ if 
$$
F_{i}(x) \to_{i \to \infty} f_{X}(x)
$$
==check this one==
We write $X_{i} \to^d X$

**Def**:
$\{ X_{i} \}$ a sequence, $X$ is a random variable. 
$\{ X_{i} \}$  converges to $X$ in probability if for any $\varepsilon>0$ 

$$
\lim_{ i \to \infty } P(|X_{i} - X| > \varepsilon) = 0
$$
We write $X_{i} \to^P X$

**Def**
$\{ X_{i} \}$ converges almost surely or almost everywhere with probability $1$ to $X$ if
$$
P(X_{i} \to_{i \to \infty} X) =1
$$
and we write $X_{i}\to X$ to mean converges almost surely

## $L^{P}$ convergence
**Def**: For $p\geq 1$, $\{ X_{i} \}$ converges in the $p^{\text{th}}$ mean or in the $L^p$-norm to $X$ if 
$$
\lim_{ i \to \infty }  \mathbb{E}\mid X_{i}-X\mid^{p} = 0
$$
Denoted by $X_{i} \to ^{L^p} X$

![[limittheorems.excalidraw]]

# Examples
## 
This is a sequence of random variables that converges
$X_{n} = n U\left( 0, \frac{1}{n \right})$

## If $X_{i} \sim Pois(\lambda)$ then
The sum of a bunch of poissons is a poisson
$S_{n}=\sum_{i=1}^{n} \sim Pois(n\lambda)$

The central limit theorem says that 
$\frac{Pois(n\lambda) - n \lambda}{\lambda \sqrt{ n }} \to ^{d} N(0, 1)$