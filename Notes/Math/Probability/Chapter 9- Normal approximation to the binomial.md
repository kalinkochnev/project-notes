**Theorem**: if $S_{n} \sim Binom(n, p)$ (number of successes in n trials) and $Z \sim N(0, 1)$ then 
$$
P\left( a \leq \frac{S_{n} - np}{\sqrt{ np(1-p) }} \right) \to (n\to \infty) P(a \leq Z \leq b)
$$
- if you have a discrete variable, you can approximate the binomial distribution with a continuous normal distribution
- In binomial approximation to the poisson the number of trials stays the same $n$ but we change the probability $p_{n}$
- Here we change the number of trials $n$ but keep the probability of success the same $p_{n}$

- This is a good approximation if $np(1-p)>10$ 
	- If the chance of success $p$ is really big or really small

# Examples
## Suppose a fair coin is flipped 100 times. What is the probability there will be at least 60 heads.
$p=\frac{1}{2}, n=100$ => $np=50, np(1-p)=25$

$$
\begin{align}
P(S_{n} \geq 60) &= P\left( \frac{S_{n} - 50}{\sqrt{ 25 }}  \geq \frac{60-50}{5}\right) \\
&= P(Z\geq 2) \approx 0.0228
\end{align}
$$