- Showing it is not true: $\sim(P\to Q) \equiv P \wedge \sim Q$. [[Conditional and Biconditional]]
- Assume our conclusion is false, and if it leads to contradiction, then it must be true
- We can now prove statements that are not conditionals

**Defintion:** A real number x is rational if $x = \frac{a}{b}$ for some $a,b \in \mathbb{Z}$. Also x is irrational if it is not rational #definition

**Proof** The number $\sqrt{ 2 }$ is irrational #proof
Assume $\sqrt{ 2 }$ is rational.
$\sqrt{ 2 } = \frac{a}{b}; b, a \in \mathbb{Z}$ and $b \neq 0$ where the [[Greatest Common Divisor | GCD(a,b)=1]]
If the gcd is not one, then divide the fraction by the GCD and reduce

$$\begin{align}
b\sqrt{ 2 }=a \\
2b^{2}=a^{2} \\
\end{align}$$
So $a^{2}$ is even therefore a is even. So $a=2k, k\in \mathbb{Z}$. Then
$$\begin{align}
2b^{2}=(2k)^{2} \\
2b^{2}=4k^{2}; \text{ divide by two} \\
b^{2}=2k^{2}
\end{align}$$
So $b^{2}$ is also even, so then $b$ is even. 
Contradiction! We assumed that gcd(a,b) =1, however $a$ and $b$ are both even which would imply gcd =2. The assumption must be false, therefore $\sqrt{ 2 }$ must be irrational

****
**Prove** There are infinitely many primes #proof
Assume that there are finitely many primes. Let $p_{1},p_{2},\dots, p_{n}$ be all the prime numbers.

Consider $a=p_{1}p_{2}p_{3}\dots p_{n}+1$. 

$a$ must not be prime because it is larger than any of the primes themselves. Then a must be divisible by some prime (since not prime itself). Let $p_{k}$ represent some prime that divides $a$
$$\begin{align}
\frac{a}{p_{k}}=\frac{p_{1}\dots p_{n}}{p_{k}}+\frac{1}{p_{k}} \\
\frac{a}{p_{k}}=\left( p_{1}\dots p_{k-1}p_{k+1}\dots p_{n} \right)+\frac{1}{p_{k}}
\end{align}$$
The LHS must be an integer since $p_{k}$ is a factor. We also know $\left( p_{1}\dots p_{k-1}p_{k+1}\dots p_{n} \right)$ is an integer. Then
$$\frac{a}{p_{k}}-\left( p_{1}\dots p_{k-1}p_{k+1}\dots p_{n} \right)=\frac{1}{p_{k}}$$
$\frac{1}{p_{k}}$ must equal an integer according to the LHS, but $\frac{1}{p_{k}}$ can never be an integer. Therefore the assumption that there are finitely many primes must be false. There are infinitely many primes

## Discussion
**Prove**: For every $x\in [\frac{\pi}{2}, \pi]$, $\sin x-\cos x\geq 1$
For sake of contradiction assume for every $x\in[\frac{\pi}{2},\pi]$, $\sin x-\cos x<1$.

- You can square across an equality if you know everything is positive
$$\begin{align}
\sin x-\cos x<1 \\
0 \leq \sin x<1+\cos x
\end{align}$$
$\sin x$ is always greater or equla to 0 in the interval. Since each quantity is positive, we can square everything
$$\begin{align}
\sin ^{2}x<1+2\cos x+\cos ^{2}x \\
\sin ^{2}x<(\sin ^{2}x +\cos ^{2}x) + 2\cos x+\cos ^{2}x \\
0<2\cos ^{2}x+2\cos x \\
0<2\cos x(\cos x+1) \\
\end{align}$$

*Case 1*: Divide by cosx
$\cos x<-1$ 
Not possible

Case 2: cosx=0 -> $x=\frac{\pi}{2}$


# Contradiction with Conditionals
$\sim(P \to Q)\equiv P \wedge\sim Q$
- Assume P and not Q when doing proof by contradiction

## Discussion
**Prove**: Suppose $a,b,c\in\mathbb{Z}$. If $a^{2}+b^{2}=c^{2}$, then $a$ or $b$ is even (determine the parity of c)

Assume for sake of contradiction that $a^{2}+b^{2}=c^{2}$ and $a,b$ are odd. Then $a =2k+1$ and $b=2m+1$ for $k, m \in \mathbb{Z}$. 

$$\begin{align}
a^{2}+b^{2}=(2k+1)^{2}+(2m+1)^{2} \\
=4k^{2}+4k+1+4m^{2}+4m+1 \\
=2(2k^{2}+2k+2m^{2}+2m+1)
\end{align}$$
So $c^{2}$ is even. Thus c is even. $c=2n, n \in \mathbb{Z}$.
$$\begin{align}
c^{2}=4n^{2}=2(2k^{2}+2k+2m^{2}+2m+1) \\
2n^{2}=2k^{2}+2k+2m^{2}+2m+1
\end{align}$$
$2n^2$ is even but it can't be odd according to the RHS. Then the assumption is not odd. Thus, if $a^{2}+b^{2}=c^{2}$ the a or b is even.


**Proposition**: Every non-zero rational number can be written as the product of two irrational numbers

*Scratch:*: $a=\sqrt{ 2 } \left(\frac{a}{\sqrt{ 2 }}\right)$ is rational if a!=0, so if we can prove $\frac{a}{\sqrt{ 2 }}$ is irrational then we can show this is true
*Lemma:* If $a \in \mathbb{Q}, a\neq 0$ then $\frac{a}{\sqrt{ 2 }}$ is irrational
- If we use proof by contradiction then we can assume P and not q (rational)
Assume for sake of contradiction $a \in \mathbb{Q}$ and $\frac{a}{\sqrt{ 2 }}$ is rational
$$\begin{align}
\frac{a}{\sqrt{ 2 }}=\frac{p}{q}; p,q \in \mathbb{Z}
\end{align}$$
Then, $\sqrt{ 2 }= \frac{aq}{p}= \frac{m}{n} \frac{q}{p} = \frac{mq}{np}; m,n \in \mathbb{Z}; n\neq 0$
Thus $\sqrt{ 2 }=\frac{mq}{np}; mq,np \in\mathbb{Z}; np \neq 0$ which is a contradiction since sqrt 2 is irrational. Thus the assumption is false. $\frac{a}{\sqrt{ 2 }}$ is therefore irrational

- Continue with a direct proof after the lemma

Assume $a \in \mathbb{Q}$ and $a \neq 0$. Then $a = \sqrt{ 2 }\left( \frac{a}{\sqrt{ 2 }} \right)$ where $\sqrt{ 2 } \in \mathbb{I}$ and $\frac{a}{\sqrt{ 2 }} = \mathbb{R} - \mathbb{Q}$


