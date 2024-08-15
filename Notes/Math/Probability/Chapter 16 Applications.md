Suppose that for a period of time you face the risk of loss that is unpredictable and denote the potential loss by the r.v. X
a) auto accident 
b) fire, theft, natural disasters
c) death of head of household

# Pareto distribution (Type 2)
$$
F_{X}(x)=1-\left( \frac{\theta}{x+\theta} \right)^{\alpha}, x > 0
$$
- $\alpha > 0$ is the tail parameter
- $\theta > 0$ is the scale parameter
- Gives a reasonably high probability for high losses

# $f_{X}(x)$ of $X \sim \text{Pareto}(\alpha, \theta)$
Take the derivative of the expression
$$
\begin{align}
f_{X}(x)=\frac{d}{dx}(F_{X}(x)) \\
= 0 - \alpha\left( \frac{\theta}{x+\theta} \right)^{\alpha-1} [\theta(-1)(x+\theta)^{-2}] \\
= \alpha \theta \cdot \frac{1}{(x+\theta)^{2}}\left( \frac{\theta}{x+\theta} \right)^{\alpha-1} \\
=\frac{\alpha}{\theta} \left( \frac{\theta}{x+\theta} \right)^{\alpha+1}
\end{align}
$$
## Expectation and variance
$$
\begin{align}
\mathbb{E}[X]=\frac{\theta}{\alpha-1} \\
Var(X)=\frac{\alpha \theta^{2}}{(\alpha-1)(\alpha-2)}
\end{align}
$$

If $\alpha >2$ => finite variance
If $1 < \alpha \leq 2$ => infinite variance
if $\alpha\leq 1$ => undefined variance

# Deductible Insurance
- Also known as excess of loss

**Deductibles**: Some policies will reimburse you for losses over a pre-specified amount $d$
- A person is responsible for $min(X, d)$ 
- The company pays 

$$X_{I}=X-min(X,d)=\begin{cases}
0 & \text{ if } X \leq d \\
x-d & \text{ if } X>d
\end{cases}$$
$$
\mathbb{E}[X_{I}] = \mathbb{E}[X] - \mathbb{E}[min(X, d)]
$$

## Expectation of a minimum
There are two cases
$$
\begin{align}
\mathbb{E}[min(X, d)] = \int _{0}^{d}xf_{X}(x) \, dx+ \int _{d}^{\infty}xf_{X}(x) \, dx   \\
=\int _{0}^{d}xf_{X}(x) \, dx - d F_{X}(x)|_{x=d}^{x=\infty} \\

=\int _{0}^{d}xf_{X}(x) \, dx - d [1 - F_{X}(d)]\\ \\
\text{Let u=x, du=1, } dv=1-F_{X}(x), v=-f_{X}(x) \\
\text{add a negative 1 to cancel} \\
=(-1) \int _{0}^{d}(-1)xf_{X}(x) \, dx - d [1 - F_{X}(d)]\\ \\
=(-1)\left[ x[1-F_{X}(x)]_{x=0}^{dx=d} - \int _{0}^{d}1-F_{X}(x) \, dx  \right] + d[1-F_{X}(d)] \\
=-d[1-F_{X}(d)] + \int _{0}^{d}1-F_{X}(x) \, dx + d[1-F_{X}(d)] \\
\mathbb{E}[min(X, d)] = \int _{0}^{d} 1- F_{X}(x) \, dx   

\end{align}
$$

The insurance company expects to pay
$$
\mathbb{E}[X_{I}]=\mathbb{E}[X]-\int _{0}^{d}1-F_{X}(x) \, dx 
$$
If $X \sim \text{Pareto}(\alpha,\theta)$
$$
\begin{align}
\mathbb{E}[X_{I}] = \frac{\theta}{\alpha-1} - \int _{0}^{d} \left( \frac{\theta}{x+\theta} \right)^{\alpha} \, dx  \\ \\
\text{ focusing on the integral}  \\
 \int _{0}^{d} \left( \frac{\theta}{x+\theta} \right)^{\alpha} \, dx =  \int _{0}^{d} \left( \frac{x+\theta}{\theta} \right)^{-\alpha} \, dx =  \int _{0}^{d} \left( \frac{\theta}{x} +1 \right)^{\alpha} \, dx \\
 \text{let } u = \frac{\theta}{x}+1 \\
 =\theta \int  u ^{-\alpha}\, dx  \\
\frac{\theta}{-\alpha+1} \left( \frac{x+\theta}{\theta} \right)^{-\alpha+1} |_{x=0}^{x=d} \\

\text{ the expected value of the minimum is}
=\frac{\theta}{\alpha-1}\left( 1-\left( \frac{\theta}{d+\theta} \right)^{\alpha-1} \right)

\end{align}
$$
# Limited insurance
- Company reimburses losses X up to a pre-specified cap or limit $L$.
$$
\begin{align}
X_{I} = min(X, L) \\
\mathbb{E}[X_{I}] = \mathbb{E}[min(X, L)] = \int_{0}^{L}[1 - F_{X}(x)] \, dx  \\
\text{ if pareto distributed } \\
\frac{\theta}{\alpha-1}\left( 1- \left( \frac{\theta}{d+\theta} \right)^{\alpha-1} \right) \\
\frac{\theta}{\alpha-1}\left( \frac{\theta}{d+\theta} \right)^{\alpha-1}
\end{align}
$$
# Coinsurance
- Company pays a fixed proportion $0 < k \leq 1$ of the loss $X$.
$$
X_{I}=kX, \mathbb{E}[X_{I}]=k\mathbb{E}[X]
$$
# Combination insurance
A deductible $d$, a limit $L$ and a coinsurance $k$. If $0 < k \leq 1, L \geq d$ then
- if no limit, $L=\infty$, if no deductible $d=0$, if no coinsurance $k=1$

$$
X_{I}=\begin{cases}
0 & X\leq d \\
k(X-d) & d < X \leq L \\
k(L - d) & X > L
\end{cases}
$$
$$
\begin{align}
X_{I}=k[min(X,L) - min(X, d)] \\
\mathbb{E}[X_{I}]= k[\mathbb{E}[min(X, L)] - \mathbb{E}[min(X, d)]] = k \int_{d} ^{L} [1- F_{X}(x)] \, dx 
\end{align}

$$

# Loss frequency
- In reality, accidents don't always occur. Assume $I \sim Bern(p)$ is the random variable which denotes the probability of an accident occurring. 
- If the loss is $X$, then the insurance claim is actually Y
$$
Y=I \cdot X = \begin{cases}
0 & I=0 \text{ if the accident doesn't occur} \\
X  & I=1 \text{ if the accident does occur}
\end{cases}
$$

- The cumulative probability of an event happening if there is no event
$$
F_{Y}(y)=\begin{cases}
(1-p) & y=0 \\
(1-p)+pF_{X}(y) & y > 0
\end{cases}
$$
- If $\mathbb{E}[X]=\mu_{x}, SD(X)=\sigma _X>0$ 
	- then $\mathbb{E}[Y]=p \mu_{x}, Var(Y)=p(1-p)\mu_{x}^{2}+ p \sigma_{X}^{2}$

# Examples
## Let $X \sim \text{Pareto(3, 100)}$ 
### a) $P(X > 50)$
$$= 1-F_{X}(50)=\left( \frac{100}{50+100} \right)^{3} = \left( \frac{2}{3} \right)^{3} $$
### b) $P(X > 75 | X>50) = \frac{P(X>75 \cap X > 50)}{P(X > 50)}$
$$
=\frac{\left( \frac{100}{175} \right)^{3}}{\left( \frac{100}{150}^{3} \right)}=0.62397
$$
## An insurance company offers an "excess of loss" contract (deductible) against a loss $X$. If $X \sim \text{Pareto}$, mean of $X$ is 100, variance of X is $\frac{200,000}{3}$, and $\alpha>3$, $\mathbb{E}[X_{I}]=80$. Find the deductible $d$

mean = 100 => $\frac{\theta}{\alpha-1}$ => $\theta=100(\alpha -1)$
$$
\begin{align}
\frac{\alpha \theta^{2}}{(\alpha-1)(\alpha-2)} = \frac{200,000}{3} \\
\frac{\alpha(100-(\alpha-1))}{(\alpha-1)(\alpha-2)} \\
3\alpha(\alpha-1) =20(\alpha-2) \\
3\alpha^{2} -23\alpha + 40 = 0 \\
(3\alpha -8)(\alpha -5)=0 \\

\alpha=\frac{8}{3}, 5 \\

\implies \theta=100(5-1)=400
\end{align}
$$

Find the deductible
$$
\begin{align}
80=\mathbb{E}[X_{I} ] = \mathbb{E}[X] - \mathbb{E}[min(X, d)] \\
=\frac{\theta}{\alpha-1} - \frac{\theta}{\alpha-1}\left( 1-\left( \frac{\theta}{d+\theta} \right)^{\alpha-1} \right) \\
80=\left( \frac{\theta}{\alpha-1} \right)\left( \frac{\theta}{d+\theta} \right)^{\alpha-1} = 100\left( \frac{400}{d+400} \right)^{4} = d=22.95
\end{align}
$$

## Company offers a limited insurance policy against a loss $X \sim \text{Pareto}(3.5, 250)$. If $L=5000$, find the expected payout by the insurance

$$
\mathbb{E}[X_{I}]=\frac{250}{3.5-1}\left( 1-\left( \frac{250}{5000+250} \right)^{3.5-1} \right) = 99.95 
$$

## Suppose $X \sim Exp$ with $\mathbb{E}[X]=250$. If $L=500$, what is $\mathbb{E}[X_{I}]$
if $\mathbb{E}[X]=250$ so $\lambda=\frac{1}{250}$ => $X \sim Exp(\frac{1}{250})$
[[Chapter 10 - Continuous Distributions#Exponential distribution]]
$$
\begin{align}
f_{X}(x)=\lambda e^{-\lambda x} \implies F_{X}(x)=1-e^{-\lambda x} = \int _{0}^{\infty}f_{X}(x) \, dx  \\
\mathbb{E}[X_{I} ] = \int _{0}^{500}[1-(1-e^{-x/250})] \, dx \\
=-250e^{-x/250}|_{x=0}^{500} = 250[1-e^{-2}]
\end{align}
$$
## An insurance company offers and 80% coinsurance policy. If $X \sim \text{Pareto}(\alpha, 400)$ and $P(X>100)=0.512$, what is the expected payout?
$$
\mathbb{E}[X_{I}]=k\mathbb{E}[X] = k \frac{\theta}{\alpha-1} = 0.8 \frac{400}{\alpha-1}
$$


$$
\begin{align}
P(X\leq c)=F_{X}(x)=1-\left( \frac{\theta}{x+\theta} \right)^{\alpha} \\
P(X>c)=\left( \frac{\theta}{x+\theta} \right)^{n}
\end{align}
$$
So 
$$
\begin{align}
P(X>100) = \left( \frac{400}{100+400} \right)^{\alpha}=\left( \frac{4}{5} \right)^{\alpha}=0.512 \\
\alpha \ln\left( \frac{4}{5} \right) = \ln(0.512) \\
\alpha=\frac{\ln(0.512)}{\ln\left( \frac{4}{5} \right)} = 3 
\end{align}
$$
Therefore the expected payout is $\mathbb{E}[X_{I}]=0.8 (\frac{400}{3-1})=160$



## A company offers a proportional excess of loss policy. The coinsurance rate is $90\%$ and the deductible is 25. Assume $X \sim Exp(\frac{1}{800})$. What is $\mathbb{E}[X_{I}]$

$L=\infty$ => $X_{I}=k[X-min(X, d)]$
$$
\begin{align}
\mathbb{E}[X_{I}] = k \int _{25}^{\infty} 1-(1-e^{-x/800}) \, dx  \\
=0.9(-800e^{-x/800})|_{x=25}^{x=\infty} = 0.9(800e^{-1/32}) = 697.85
\end{align}
$$

The policy holder can expect an average of 
$$
\frac{697.85}{800} \approx 87\%\text{ of your loss returned to you}
$$

## Assume the probability an accident occurs is 0.2. The loss $X$ follows a discrete distribution

| X (the distribution of damages) | 20  | 100 | 500  | 1000 |
| ------------------------------- | --- | --- | ---- | ---- |
| P(X=x)                          | 0.3 | 0.5 | 0.15 | 0.05 |
What is the probability that a claim of <= 150 occurs?
$$
\begin{align}
P(Y \leq 150) = P(I=0) + P(I=1)P(X \leq 150) \\
= (1-0.2) +(0.2)(0.3+0.5) = 0.96
\end{align}

$$