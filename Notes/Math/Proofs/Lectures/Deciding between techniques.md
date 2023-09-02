- Depends on what information you want to assume

## Example for each
Let x be a nonzero real number, if $x+\frac{1}{x}<2$, then $x<0$. 

**Direct:** Assume P, show Q
Assume $x \in \mathbb{R}$, $x \neq 0$, and $x+\frac{1}{x}<2$. Multiply both sides by $x^{2}>0$.
$$\begin{align}
x^{3}+x<2x^{2} \\
x^{3}-2x^{2}+x<0 \\
x(x^{2}-2x+1)<0\\
x(x-1)^{2}<0 \\
\end{align}$$
We know that $(x-1)^{2}>0$ (unless x=1). Either $x<0$ or $x=1$.
If $x=1, x+\frac{1}{x}=1+\frac{1}{1}=2$, so $x\neq 1$. Thus $x<0$

**Contrapositive:** Assume ~Q then show ~P
We assume $x\in \mathbb{R}, x\neq 0, x\geq 0$, that is, $x>0$. 
We know that $(x-1)^2 \geq 0$ (attained through scratch work) so
$$\begin{align}
x^{2}-2x+1\geq 0 \\
x^{2}+1\geq 2x
\end{align}$$
Since x>0, divide by x
$x+\frac{1}{x}\geq 2$
Thus using the contrapositive we can conclude if $x+\frac{1}{x}<2$ then $x<0$

**Contradiction:** Assume P and not Q
Assume, for sake of contradiction, $x+\frac{1}{x}<2$ and $x\geq 0$.

We know $x+\frac{1}{x}<2$. Multiply by x since $x\geq 0$.
$$\begin{align}
x^{2}+1<2x \\
x^{2}-2x+1<0 \\
(x-1)^{2}<0
\end{align}$$
This is a contradiction, thus the assumption is false. So if $x + \frac{1}{x}<2$, then $x<0$