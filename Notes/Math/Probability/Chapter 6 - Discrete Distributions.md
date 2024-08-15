# Bernoulli Distributions
A random variable $X$ such that $P(X=1)=p$ and $P(X=0)=1-p$ is a **Bernoulli random variable** with parameter $p$

$$
\begin{align}
\mathbf{E}(X)=p \\
\mathbf{E}(X^2)=p \\
Var(X)=p(1-p)
\end{align}
$$
$X \sim Bern(p)$ => $X$ is distributed as  Bernoulli

# Binomial distribution
- Models the $k$ successes in $n$ bernoulli trials

A random variable $X$ has a binomial distribution with parameters $n$ and $p$ if
$$
P(X=k)={n \choose k}p^{k}(1-p)^{n-k}
$$
For all $K=0, \dots, n$
$$
\begin{align}
\mathbf{E}(X)=np \\
Var(X)=np(1-p)
\end{align}
$$

If $X=$#of successes in n Bernoulli trials then  $X \sim Binom(n, p)$

# Poisson distribution
$X \sim Pois(\lambda)$ if
$$
P(X=i)=e^{-\lambda} \frac{\lambda^{i}}{i!}
$$
$$
\begin{align}
\mathbf{E}(X)=\lambda  \\
Var(X)=\lambda
\end{align}
$$
For all $i=0, 1, 2\dots$
- If $X=$count of something per unit time then $X \sim Pois(\lambda)$
- X can take on an infinite number of values
- expresses the probability of a given number of [events](https://en.wikipedia.org/wiki/Event_(probability_theory) "Event (probability theory)") occurring in a fixed interval of time if these events occur with a known constant mean rate and [independently](https://en.wikipedia.org/wiki/Statistical_independence "Statistical independence") of the time since the last event.

**Proof of expectation**
$$
\begin{align}
\mathbf{E}(X)&=\sum_{i=0}^{\infty}i P(X=i) \\
&=\sum_{i=0}^{\infty}i e^{-\lambda} \frac{\lambda^{i}}{i!} \\
&=e^{-\lambda} \sum_{i=0}^{\infty}i \frac{\lambda^{i}}{i!}  \\
&=e^{-\lambda} \sum_{i=1}^{\infty} \frac{\lambda^{i}}{(i-1)!}  \\
&=\lambda e^{-\lambda} \sum_{i=1}^{\infty} \frac{\lambda^{i-1}}{(i-1)!}  \\ \\
&=\lambda e^{-\lambda} e^{\lambda} \\ \\
&= \lambda
\end{align}
$$

## Examples of poisson
- How many cars pass through an intersection every hour
- The number of dna mutations per minute
- The number of bankruptcies filed every month
- Number of births/deaths/marriages/divorces per year

## Binomial approximation to the poisson
If we had a sequence of binomial distributions $X_{n} \sim Binom(n, p_{n})$ and if $\lim_{ n \to \infty } np_{n}=\lambda$ then
$$
\lim_{ n \to \infty } X_{n} = Y \sim Pois(\lambda)
$$

- If you have a sequence of binomial random variables, if it happens that the probability of the binomial variables converges to a constant, then it 
- **If someone gives you a poisson variable, you can approximate it with a binomial variable**
- This is accomplished by
$$
p=\frac{\lambda}{n},  \forall n > \lambda
$$
ex:
$$
Pois(5) \approx Binom\left( 30, \frac{1}{6} \right)
$$
# Uniform distribution
$X \sim unif(n)$ if $P(X=k)=\frac{1}{n}$ for $k=1, 2, ..n$

# Geometric distribution
$X \sim Geom(p),  [0 < p < 1]$ if $P(X=i)=(1-p)^{i-1} p$ for $i=1, 2, \dots$
- This measure the probability the first success occurs on the ith trial (i-1 failures before)
- In Bernoulli trials if $X=$ time of first success, then $X \sim Geom(p)$
$$
\begin{align}
\mathbf{E}(X)=\frac{1}{p} \\
Var(X)=\frac{1-p}{p^{2}} \\
F_{X}(i) = 1-(1-p)^{i}
\end{align}
$$

# Negative binomial
$X \sim Negbinom(r, p)$ if $P(X=n)={n-1 \choose r-1} p^{r}(1-p)^{n-r}$ for $n=r, r+1, \dots$
- Very similar to the geometric distribution. Instead of time for the first success, it is the time for the rth success
- It is the probability of needing $n$ trials in order to get $k$ successes while binomial says what is the probability of getting k successes in n trials 
$$
Negbinom(1, p)=Geom(p)
$$

# Hypergeometric distribution
$X \sim Hyp(m, n, N)$ if 
$$
{\displaystyle p_{X}(k)=\Pr(X=k)={\frac {{\binom {K}{k}}{\binom {N-K}{n-k}}}{\binom {N}{n}}},}
$$
for $i=0, 1, \dots m$
- Sampling without replacement
- $N$ is the population size,
- $K$ is the number of success states in the population,
- $n$ is the number of draws (i.e. quantity drawn in each trial),
- $k$ is the number of observed successes,
- ${a \choose b}$  is a [binomial coefficient](https://en.wikipedia.org/wiki/Binomial_coefficient "Binomial coefficient").
- describes the probability of $k$successes (random draws for which the object drawn has a specified feature) in $n$draws, _without_ replacement, from a finite [population](https://en.wikipedia.org/wiki/Statistical_population "Statistical population") of size $N$ that contains exactly $K$ objects with that feature, wherein each draw is either a success or a failure. In contrast, the [binomial distribution](https://en.wikipedia.org/wiki/Binomial_distribution "Binomial distribution") describes the probability of $k$ successes in $n$. draws _with_ replacement.


# Cheat sheet
| Name              | Description                                     | Parameters                                           | PMF $P_{X}(K)$                                               | Expected $\mathbb{E}[X]$ | $Var(X)$                                              |
| ----------------- | ----------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------ | ------------------------ | ----------------------------------------------------- |
| Bernoulli         | A single trial of binomial                      | $p \in[0,1]$                                         | $${1 \choose k}p^{k}(1-p)^{1-k}$$                            | $p$                      | $p(1-p)$                                              |
| Binomial          | Probability of $k$ successes in $n$ trials      | $n \in \mathbb{N}$ (number of trials), $p \in[0, 1]$ | $${n \choose k}p^{k}(1-p)^{n-k}$$<br>                        | $np$                     | $np(1-p)$                                             |
| Poisson           | Count variable per unit time                    | $\lambda > 0$                                        | $$e^{-\lambda}\left( \frac{\lambda^{n}}{n!} \right)$$        | $\lambda$                | $\lambda$                                             |
| Geometric         | Probability of first success on the $k$th trial | $p \in (0, 1)$ (no guaranteed success/failure)       | $(1-p)^{k-1}p$ if $k\geq 1$                                  | $\frac{1}{p}$            | $\frac{1-p}{p^{2}}$                                   |
| Negative binomial | $r$th success on the $k$th trial                | $r \in \mathbb{N}, p \in (0, 1)$                     | $${k-1 \choose r-1}p^{r}(1-p)^{k-r}$$                        | $\frac{r}{p}$            | $\frac{r(1-p)}{p^{2}}$                                |
| Hypergeometric    | sampling from a population without replacement  | $N \in \mathbb{N}_{0}, m,n \in N_{0}$                | $$\frac{{m \choose k}{N-m \choose n-k}}{{N \choose n}}$$<br> | $\frac{nm}{N}$           | $\frac{nm(N-n)}{N(N-1)})\left( 1-\frac{M}{N} \right)$ |
|                   |                                                 |                                                      |                                                              |                          |                                                       |
# Examples
## Suppose on average there are 5 homicides per month in Hartford. What is the probability that there is at most 1 homicide next month
- This is poisson since the random variable is per unit time
- $5=\mathbf{E}(X)=\lambda$

$$
\begin{align}
P(X=i)=e^{-5} \frac{5^{i}}{i!} \\
P(X\leq 1) = P(X=0)+P(X=1) \\
=e^{-5}+5e^{-5}
\end{align}
$$

## On average there is 1 large earthquake per year in California. What is the probability there are 2 next year?
- Random variable is count of earth quakes per year

$$
\begin{align}
1=\lambda=\mathbf{E}(X) \implies P(X=i) = \frac{1}{i!e} \\
P(X=2)=\frac{1}{2e}
\end{align}
$$

## A company prices its hurricane insurance under the following assumptions:
1) There is at most 1 hurricane every year
2) $P$ of hurricane in any year is $0.05$
3) # hurricanes in a given year is independent of all the other years
What is the probability that there are fewer than 3 hurricanes in a 20-year period

Let $X$ be the number of hurricanes in a 20 year period
This problem is $X \sim Binom(20, 0.05)$ 
$$
\begin{align}
P(X<3)&=P(X=0)+P(X=1)+P(X=2) \\
&= {20 \choose 0} (0.05)^{0}(0.95)^{20} + {20 \choose 1} (0.05)^{1}(0.95)^{19}+ {20 \choose 2}(0.05)^{2}(0.95)^{18} \\
=0.9245
\end{align}
$$

## UConn has a 0.6 probability of making a free throw. Suppose each free through is independent of the rest. What is the probability that UConn makes at least 2/10 free throws

Let $X$ be the number of free throws that made it in out of 10 tries
$X \sim Binom(10, 0.6)$
$$
\begin{align}
P(X\geq 2)&= 1- P(X < 2) = 1 - P(X=0)-P(X=1) = 0.998
\end{align}
$$

## An egg carton has 12 eggs, 3 of which have a double yolk. We're making an omelette with 5 eggs. What is the probability our omelette has at least 2 double  yolk eggs

Let $X$ be the number of double yolk eggs in the omelette
$X \sim HypG(m (\text{pop size of interest})=3, n (\text{sample size})=5, N=12)$
$$
\begin{align}
P(X\geq 2) &= P(X=2) + P(X=3) \\
&= \frac{{3 \choose 2}{9 \choose 3}}{{12 \choose 5}} + \frac{{3 \choose 3}{9 \choose 2}}{{12 \choose 5}}
\end{align}
$$

## Suppose we are rolling a fair dice.
**a) What is the probability we see 6 even numbers before we see an odd number?**
let $X$ be the number of even rolls before an odd number $X \sim Geo(0.5)$
Seeing 6 evens and then an odd is 7 trials total
$$
P(X=7) = 0.5^{6}0.5^{1}=\frac{1}{128}
$$
**B) What is the probability that we see our fifth 2 on the 10th roll?**
Let $X$ be the number of rolls to get the fifth 2
$X \sim NegBinom(r=5, p=\frac{1}{6})$

$$
P(X=10) = {9 \choose 4 } \left( \frac{1}{6} \right)^{5}\left( \frac{5}{6} \right)^{5}
$$