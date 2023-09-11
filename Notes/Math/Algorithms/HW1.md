$$
\begin{align}
n! =\sqrt{ 2\pi n }\left( \frac{n}{e} \right)^{n}\left( 1+\Omega\left( \frac{1}{n} \right) \right) \\
\log(n!) = \log(\sqrt{ 2\pi n } ) +n\log\left( \frac{n}{e} \right) + \log\left( 1+\Omega\left( \frac{1}{n} \right) \right) \\
\end{align}
$$
We want to compute the lower bound of $\log n!$.
$\sqrt{ 2\pi n }$ is upper bounded by $O(\sqrt{ n })$.
$n\log(\frac{n}{e})$ is upper bounded by $O(n\log n)$
It is true that $k=\Omega(\frac{1}{n})$ where k is a constant because there exists a positive constant $c$ such that $k \geq c \frac{1}{n}$ for large n. So $O\left( 1+\Omega\left( \frac{1}{n} \right) \right)=O(1+k)=O(1)$

All together we have
$$
\begin{align}
\log(n!)=\log(O(\sqrt{ n } )) + O(n\log n) + \log(O(1))
\end{align}
$$
If $f$ is a function, then $\log(f) < f$. The upper bound of $\log(f)$ is still $f$. Therefore
$$
\begin{align}
=O(\sqrt{ n } ) + O(n\log n) + O(1) \\
\log(n!)= O(n\log n)
\end{align}
$$
Since we only pay attention to the highest impact terms.

$B=n\log n$ so there exists constants $c_{1}>0,c_{2}>0$ such that
$$
c_{1}B \leq A \leq c_{1}B
$$

# Q4)
$n<n^{e}<n^{\pi}<2^{\sqrt{ \log n }}<n^{lgn}<lg(n!)$
$n^e$ is a higher degree polynomial ($n^{2.718\dots}$) than $n^{1}$
$n^{\pi}$ is a higher degree polynomial ($n^{3.141\dots}$) than $n^{2.718\dots}$
$2^{\sqrt{ lg n }}$ Any exponential surpasses any polynomial $n^{\pi}$
It is a fact that $(lg(n))^{1/2} < (lg(n))^{2}$
$$
\begin{align}
lg^{1/2}(n) < lg^{2}(n) \\
lg^{1/2}(n)lg(2) < lg(n)lg(n) \\
lg(2^{\sqrt{ lgn }}) <lg(n^{lgn}) \\
2^{\sqrt{ lgn }} < n^{lgn}
\end{align}
$$