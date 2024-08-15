A continuous random variable is a **standard normal** or Gaussian if it has the density
$$
f_{z}(x)=\frac{1}{\sqrt{ 2\pi }} e^{-x^{2}/2}
$$

**Theorem**: $f_{z}$ is a PDF and $\mathbb{E}[Z]=0$ and $Var(x)=1$

## Proof that standard normal is a probability distribution
**Proof**: WTS: $\frac{1}{\sqrt{ 2\pi }} \int _{-\infty}^{\infty} e^{-x^{2}/2} \, dx=1$ 
This is not integrable the way it is. We need to do a substitution and convert to polar coordinates
Let $$I=\int _{0}^{\infty} e^{-x^{2}/2} \, dx$$ (half the normal). Then

$$
\begin{align}
I^{2} &= \int _{0}^{\infty} \int _{0}^{\infty} e^{-x^{2}/2} e^{-y^{2}/2} \, dx  \, dy  \\ \\
&=\int _{0}^{\infty} \int _{0}^{\infty} e^{-(x^{2}+y^{2})/2} \, dx  \, dy \\ \\


\end{align}

$$
To convert to polar coordinates $x^{2}+y^{2}=r^{2}$ and  $dxdy=r dr d\theta$. We also need to change the bounds of the integral for $\theta$. To stay in the first quadrant we integrate from $0 \to \frac{\pi}{2}$

$$
\begin{align}
&=\int _{0}^{ \pi/2} \int _{0}^{\infty} r e^{-r^{2}/2} \, dr  \, d\theta \\
\end{align}
$$
U substitution $u = -\frac{r^{2}}{2}$ so $du = -r dr$
$$
\begin{align}
&=\int _{0}^{ \pi/2} \int _{0}^{\infty} e^{u} \, du  \, d\theta \\ \\
&=\int _{0}^{\pi/2} [-e ^{-r^{2}/2}]_{0}^{\infty} \, d\theta = \int _{0}^{\pi/2} (0-(-1)) \, d\theta = \pi /2 \\ \\
I^{2}=\frac{\pi}{2}
\implies I=\sqrt{ \frac{\pi}{2} } \\ \\
\frac{1}{\sqrt{ 2\pi }} * 2 I = 1
  
\end{align}
$$

# Expected value
$$
\mathbb{E}[Z] = \frac{1}{\sqrt{ 2\pi }} \int _{-\infty}^{\infty} x e^{-x^{2}/2}\, dx = 0
$$
The expected value is zero because $xe^{-x^{2}/2}$ is an odd function. When you integrate symmetrically it cancels out

# Variance
If there is no mean, then we integrate by parts
$$
\begin{align}
Var(Z) = \mathbb{E}[Z^{2}] - (0)^{2}
= \frac{1}{\sqrt{ 2\pi }}\int _{-\infty}^{\infty} x^{2} e^{-x^{2}/2} \, dx  \\
= \frac{1}{\sqrt{ 2\pi }}\int _{-\infty}^{\infty} x( xe^{-x^{2}/2}) \, dx 
\end{align}
$$
Let $u=x, du=1$ and $dv=xe^{-x^{2}/2}, v =-e^{-x^{2}/2}$

$$
\begin{align}
uv - \int _{-\infty}^{\infty} v du \, dx\\
\frac{1}{\sqrt{ 2\pi }}\left( -xe^{-x^{2}/2} |_{-\infty}^{\infty} - \int _{-\infty}^{\infty} \, -e^{-x^{2}/2} dx  \right) \\
Var(X)=\frac{1}{\sqrt{ 2\pi }} 2 I = 1
\end{align}
$$
# CDF of standard normal
It has its own symbol.
$$
P(Z \leq x) = \Phi(x)= \int _{-\infty} ^{x} e^{-y^{2}/2} \, dy 
$$

- Values are usually tabulated
- Since $Z$ is symmetric, the area under the curve to the left of $-x$ is the same as one minus x the area under the curve to the left of $x$ 
$$
\Phi(-x)=1-\Phi(x)
$$

# Non-zero mean/variance
We say $X \sim N(\mu, \sigma^{2})$ if $X=\sigma Z+\mu$ when $Z \sim N(0, 1)$
- Any normal distribution can be rescaled and shifted to go back to the standard normal distribution

**Proposition**: If $X \sim N(\mu, \sigma^{2})$ then
$$
f_{X}(x) = \frac{1}{\sigma \sqrt{ 2\pi }} e ^{-\frac{(x-\mu)^{2}}{2 \sigma^{2}}}
$$
Also $\mathbb{E}[X]=\mu$ and $Var(X)=\sigma^{2}$

# Upper bound of  Z being >= x 
**Proposition:** for $Z \sim N(0, 1)$ and $x>0$, we have
$$
P(Z\geq x) = 1- \Phi(x)\leq \frac{1}{x\sqrt{ 2\pi }} e^{-x^{2}/2}
$$
If $x\gg 0$ then
$$
P(Z \geq x) \leq e^{-x^{2}/2}
$$

# Examples
## Find $P(1\leq X\leq 4)$ if $X \sim N(2, 25)$
$$
\begin{align}
X=\sqrt{ 25 }Z + 2 \\
P(1 \leq X \leq 4) = P(1\leq 5Z + 2 \leq 4)  \\
= P(-0.2 \leq Z \leq 0.4)  \\
= P(Z\leq 0.4) - P(Z <-0.2) \\
= \Phi(0.4) - (1-\Phi(0.2)) \\
= 0.65532 - (1-0.57026) \\
=0.2347
\end{align}
$$

## Find $c$ such that $P(|Z| \geq c) = 0.05$
We are essentially doing a 95% confidence interval. This is the area of the tails.
By symmetry we only have to calculate the area of one of the tails. 
$$
P(Z \geq c) = 0.025
$$
$\Phi(c)$ measures everything to the left of $c$, so take the complement
$$
\begin{align}
1-\Phi(c) = 1-0.975 = 0.025 \\
\implies c=1.96 \approx 2
\end{align}
$$
95% of the probability is contained within about 2 standard deviations of the curve

## Suppose $X$ is normal with mean 6. If $P(X>16)=0.0228$, what is the standard deviation of X?
$$
\begin{align}
P(X>16)&=P\left(  \frac{x-6}{\sigma} > \frac{16-6}{\sigma} \right) \\
&=P\left( Z > \frac{10}{\sigma} \right) = 0.00228 \\
&=1-\Phi\left( \frac{10}{\sigma}  \right) = 0.0228 \\
\implies \Phi\left( \frac{10}{\sigma} \right) = 0.9772 \\
\end{align}
$$
By the table
$$
\begin{align}
\frac{10}{\sigma}=2 \\
\sigma=5
\end{align}
$$

## The peak temperature $T$ on a July day in Antarctica is normally distributed with variance 225. With probability 0.5, the temperature exceed 10 F. What is $P(T>32)$?
By symmetry $P(T>10)=\frac{1}{2} \implies \mu = 10$
$$
\begin{align}
\implies T \sim N(10, 15^{2}) \\
P(T>32) = P\left( Z > \frac{32-10}{15} \right) = P(Z>1.47) = 1-\Phi(1.47) = 0.0701
\end{align}
$$

## UConn professor salaries are approximately normally dist. Suppose you know 33% of professors make <80k and 33% make more than 120k. What is $P(70k < X < 80k)$
$$
\begin{align}
P(X\geq 120k) = 0.33 \\
P(X \leq 80k)= 0.33 \\

\implies P\left( Z \geq \frac{120k - \mu}{\sigma} \right) = 0.33 \\
\implies P\left( Z \leq \frac{80k-\mu}{\sigma} \right)=0.33 \\

\Phi\left( \frac{120k - \mu}{\sigma} \right) = 1 - 0.33 = 0.67 \\
-\frac{80k - \mu}{\sigma} = \sigma^{-1}(1-0.33) \\
\frac{120k - \mu }{\sigma} = \Phi^{-1}(0.67) \\ \\
\text{ 80k is on the left of the mean (-) so need to take complement and look at table }\\

\frac{120k-\mu }{\sigma} = 0.44 \\
\frac{80k - \mu}{\sigma}=-0.44 \\
\implies \mu=100k, \sigma=45454.5
\end{align}
$$

The probability that you make between 70k and 80k is
$$
P(X\leq 80k) - P(X < 70k) = 0.33 - \Phi\left( \frac{70k-100k}{45454.5} \right) = 0.0753 
$$