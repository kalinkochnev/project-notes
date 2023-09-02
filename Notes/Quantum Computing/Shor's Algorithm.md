- Factoring can be converted into a period finding problem, which can be solved with quantum phase estimation
- Let $N=pq$ where $p,q$ are odd and of almost equal length

# Factoring
Two prime factors of a number $n$ can be determined by
$$
\begin{align}
n^{2}\equiv 1 \text{ (mod n)} \\
n^{2}-1\equiv 0 \text{ (mod n)} \\
(n+1)(n-1)\equiv 0 \text{ (mod n)}
\end{align}
$$
- This says that (n+1)(n-1) are divisible by n
- Therefore, n+1 has a number that divides it and n. Same w/ n-1
$gcd(n+1, n)$ and $gcd(n-1, n)$ are the factors
- Can be extended to $r$ roots so $n^{r}\equiv 1 \text{ (mod n)}$

# Periodicity
- $f$ is periodic if $f(a)=f(a+n)$ for period size $n$
- $f(r)=a^{r} \text{ (mod n)}$ are periodic
- $a$ must be co-prime with $n$ (guess, if not, try again with a different guess)

**Example:** Want to find factors for $n=21$ and $a=2$
- This function has a period of 6
- f(0) = f(0+6)
| r   |          | f(r) |
| --- | -------- | ---- |
| 0*   | 2^0 % 21 | 1    |
| 1*   | 2^1 % 21 | 2    |
| 2*   | 2^2 % 21 | 4    |
| 3*   | 2^3 % 21 | 8    |
| 4*   | 2^4 % 21 | 16   |
| 5*   | 2^5 % 21 | 11   |
| 6   | 2^6 % 21 | 1    |
| 7   | 2^7 % 21 | 2     |
