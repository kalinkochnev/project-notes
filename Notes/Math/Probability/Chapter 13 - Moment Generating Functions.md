**Definition:** The moment generating function (MGF) of a random variable $X$ is 
$$
m_{X}(t) = \mathbb{E}[e^{tX}]
$$
Provided the expectation is finite
- infinite series where coefficients count something you are interested in
- This function has coefficients that represent the different moments
- Usually you don't need to calculate every coefficient. You can exploit some kind of pattern to calculate the coefficient

If $X$ is discrete
$$
m_{X}(t) = \sum_{X}e^{tx} p_{X}(x)
$$
If $X$ is continuous
$$
m_{X}(t) = \int _{-\infty}^{\infty} e^{tx}f_{x}(x) \, dx 
$$


## proof of moment generating expectation
**Recall** taylor series of $e^{tX}$ [[Calculus#Series]]
$$
\begin{align}
e^{tX}&=1+(tX)+\frac{(tX)^{2}}{2!}+\frac{(tX)^{3}}{3!} + \dots \\
&= \sum_{k=0}^{\infty} \frac{(tX)^{k}}{k!}
\end{align}
$$

We know that the expectation of a sum is the same as sum of expectations
$$
\begin{align}
\mathbb{E}[e^{tX}] &= \mathbb{E}\left[  \sum_{k=0}^{\infty} \frac{(tX)^{k}}{k!} \right] \\ \\
&\text{The coefficients are the moments}\\
&=\sum_{k=0}^{\infty}\mathbb{E}[X^{k}] \frac{t^{k}}{k!} = m_{X}(t)
\end{align}
$$
If we take $k$ derivatives of $t$, we should get $\mathbb{E}[X^{k}]$. This is because it cancels out the $\frac{r^{k}}{k!}$ coefficient in the sum
$$
\mathbb{E}[X^{k}] = \frac{d^{k}}{dt^{k}} m_{X}(0)
$$
# Examples
## If $X\sim Bern(p)$ then what is $m_{X}(t)$
Bernoulli variable either takes on value of 1 with probability $p$ and 0 with probability $1-p$
$$
\begin{align}
m_{X}(t)&=e^{t\cdot 0}(1-p)+e^{t \cdot 1} p \\
&=p e ^{t} +(1-p)
\end{align}
$$
To find the first term we can take the first derivative
$$
\begin{align}
\mathbb{E}[X^{k}] &= \frac{d^{k}}{dt^{k}} m_{X}(0) \\
\mathbb{E}[X^{1}]&=\frac{d}{dt} m_{X}(0) = p e ^{0}=p
\end{align}
$$

To calculate second derivative
$$
\begin{align}
\mathbb{E}[X ^{2}] &= \frac{d^{2}}{dt^{2}} m_{X}(0) \\
&=p
\end{align}
$$
Can quickly find the variance $Var(X)=p-p^{2}$


## If $X \sim Binom(n, p)$ then 
It is discrete so sum over all possible values of $x$
$$
\begin{align}
\mathbb{E}[e^{tX}] &= \sum_{k=0}^{n} e^{t k} \left({n \choose k} p^{k}(1-p)^{n-k}\right) \\
&=\sum_{k=0}^{n} {n \choose k} (e^{t} p)^{k} (1-p)^{n-k}
\end{align}
$$
Remember the binomial theorem $(a+b)^{n}=\sum_{k=0}^{n}{n \choose k} a^{k}b^{n-k}$
$$
=(pe^{t}+(1-p))^{n}
$$

Therefore the moment generating function for the binomial distribution is
$$
m_{X}(t)=(pe^{t} + (1-p))^{n}
$$

Calculate the variance. Calculate one derivative
$$
\begin{align}
\mathbb{E}[X]&=\frac{d}{dt}m_{X}(0)=n(pe^{0}+1-p)^{n-1} [pe^{0}] \\
&=np
\end{align}
$$

**Recall** that $X=\sum_{i=1}^{n}X_{i}$ where $X_{i}\sim Bern(p)$

For the binomial
$$
\begin{align}
m_{X}(t)&=\mathbb{E}\left[ e^{t \sum_{i} X_{i}} \right] \\ \\
&\text{Addition in exponent is same as multiplication in base} \\
&=\mathbb{E}[ \Pi_{i=1}^{n} e^{t X_{i}}] =  \Pi_{i=1}^{n}\mathbb{E}[ e^{t X_{i}}] \\
&=\Pi_{i=1}^{n}(pe^{t} + (1-p))  \\
&= (pe^{t} + (1-p))^{n}
\end{align}
$$

## If $X \sim Pois(\lambda)$ then find $m_{X}(t)$
$$
\begin{align}
m_{X}(t)&=\mathbb{E}[e^{tX}]=\sum_{x}e^{tx}p_{X}(x) \\
&= \sum_{k=0}^{\infty} e^{tk}\left( e^{-\lambda} \frac{\lambda^{k}}{k!} \right) \\
&= e^{-\lambda} \sum_{k=0}^{\infty} \frac{(e^{t}\lambda)^{k}}{k!} \\
&= e^{-\lambda} e^{e^{t}\lambda} \\
&\implies m_{X}(t)=e^{\lambda(e^{t}-1)} \\
\end{align}
$$

The first moment is the first derivative of $m_{X}$ evaluated at 0
$$
\begin{align}
\mathbb{E}[X]&=\frac{d}{dt} m_{X}(0) \\
&= e^{\lambda(e^{t}-1)}(\lambda e^{t}) \\

&\mathbb{E}[X]=\frac{d}{dt}m_{X}(0)=\lambda
\end{align}
$$

## If $X \sim Exp(\lambda)$ then
Measures the time between two different events
$$
\begin{align}
\mathbb{E}[e^{tX}] &= \int _{0}^{\infty} e^{tx}(\lambda e ^{-\lambda x}) \, dx  \\
&=\lambda \int _{0}^{\infty} e^{(t-\lambda)x} \, dx \\
&=\frac{\lambda}{t-\lambda} e^{(t-\lambda)x}|_{x=0}^{\infty} 
\end{align}
$$
This only goes to zero is $t-\lambda<0$ => $t<\lambda$
$$
\begin{align}
&=\frac{\lambda}{t-\lambda}(0-1) \\
&\implies m_{X}(t)=\frac{\lambda}{\lambda-t} \text{ if } t<\lambda
\end{align}
$$
If we take a derivative to find the first moment, we get
$$
\begin{align}
\mathbb{E}[X] = \frac{d}{dt}m_{X}(0) = \frac{\lambda}{(\lambda-0)^{2}}=\frac{1}{\lambda}
\end{align}
$$

Can easily find the nth derivative (and moment) easily
$$
\mathbb{E}[X^{n}] = \frac{n!}{\lambda^{n+1}}
$$




## If $Z \sim N(0, 1)$
$$
\begin{align}
m_{Z}(t)&=\int _{-\infty}^{\infty} e^{tz} \left(\frac{1}{\sqrt{ 2\pi }} e^{-x^{2}/2} \right) \, dx  \\
&=\frac{1}{\sqrt{ 2\pi }} \int _{-\infty}^{\infty} e^{tx -x^{2}/2} \, dx  \\
&\text{add an extra term to cancel and complete the square} \\
&=\frac{1}{\sqrt{ 2\pi }}  \int _{-\infty}^{\infty} e^{t^{2}/2} e^{-t^{2}/2 + tx - x^{2}/2} \, dx \\
&=\frac{1}{\sqrt{ 2\pi }}  \int _{-\infty}^{\infty} e^{t^{2}/2} e^{-(x-t)^{2}/2}  \, dx \\ 
&=e^{t^{2}/2} \left[ \frac{1}{\sqrt{ 2\pi }}  \int _{-\infty}^{\infty} e^{-(x-t)^{2}/2}  \, dx \right]\\ 
\end{align}
$$
We see another standard normal appear and we know the PDF of that is  1
$$
m_{Z}(t)=e^{t^{2}/2}
$$

## If $X \sim N(\mu, \sigma^{2})$
$$
\begin{align}
m_{X}(t)&=\mathbb{E}[e^{tX}] = \mathbb{E}[e^{t(\sigma z+\mu)}] \\
&=e^{t \mu} \mathbb{E}[e^{(t\sigma)z}] \\
&= e^{t \mu}e^{(t\sigma)^{2}/2}
\end{align}
$$

