https://en.wikipedia.org/wiki/Floor_and_ceiling_functions
## Floor and Ceiling
Where $m$ and $n$ are integers and $x$ is any real number
$\lfloor x \rfloor=m \iff m\leq x<m+1$ 
$\lceil x \rceil=n \iff n-1<x\leq n$

### Properties
**Floor equality**: $\lfloor x+m \rfloor=\lfloor x \rfloor+m$
![[Pasted image 20230314123456.png]]
![[Pasted image 20230314123503.png]]

**Floor of $\frac{n}{2}$**
$$
\lfloor \frac{n}{2} \rfloor =\begin{cases}
\frac{n}{2} & \text{if n is even} \\
\frac{n-1}{2}
\end{cases}
$$
![[Pasted image 20230314124119.png]]
![[Pasted image 20230314124128.png]]
![[Pasted image 20230314124137.png]]

**Floor and Quotient Remainder**
Big idea: If you have a number $n$, it is a multiple of $q=\lfloor \frac{n}{d} \rfloor$ and some remainder $r=n-\lfloor \frac{n}{d} \rfloor$

![[Pasted image 20230314125149.png]]
![[Pasted image 20230314125159.png]]
![[Pasted image 20230314125207.png]]
![[Pasted image 20230314125215.png]]
![[Pasted image 20230314125222.png]]

# Euclid's Lemma
If a prime divides the product $ab$ of two integers $a$ and $b$, then $p$ must divide either $a$ or $b$.

If $p \mid a_{1}a_{2}\dots a_{n}$, then $p\mid a_{i}$ for some i