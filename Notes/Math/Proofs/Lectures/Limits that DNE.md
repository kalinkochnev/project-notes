- The [[Limit definition]] doesn't exist if "For every L, $\lim_{ x \to a }f(x) \neq L$" (take the negation of the limit definition)

# Definition for DNE
**Original limit def:** $\forall \epsilon >0, \exists \delta >0$ s.t. ($\forall x$) $0<|x-c| < \delta \implies|f(x)-L|<\epsilon$

**Negation:**  $\forall L, \exists \epsilon >0, \exists x \text{ s.t. } 0<|x-a|<\delta \text{ and } |f(x)-L|\geq\epsilon$

$$
\exists \epsilon >0, \forall \delta >0, \exists x \text{ s.t. } 0<|x-a| <\delta \text{ and } |f(x) -L|\geq \epsilon
$$
# Example
Show that $\lim_{ x \to 2 } \frac{|x-2|}{x-2}$ does not exist.
WTS: $\forall L, \exists \epsilon >0, \exists x \text{ s.t. } 0<|x-a|<\delta \text{ and } |f(x)-L|\geq\epsilon$

**Scratch:**
![[Pasted image 20230421102229.png]]

**Proof:** (want to show a contradiction by assuming the limit does exist)
Let $L \in \mathbb{R}$. Let $\epsilon =\frac{1}{2}$. Let $\delta>0$
Assume that $\forall x, 0<|x-a|<\delta \implies | \frac{|x-2|}{x-2}-L|<\epsilon$

Let $x=2+\frac{\delta}{2}$ and $\hat{x}=2-\frac{\delta}{2}$ so that $f(x)=\frac{|x-2|}{x-2}=\frac{|2+\frac{\delta}{2}-2|}{2+\frac{\delta}{2}-2}=1$ and $f(\hat{x})=\frac{|x-2|}{x-2}=\frac{|2-\frac{\delta}{2}-2|}{2-\frac{\delta}{2}-2}=-1$

Since $|1-L|< \frac{1}{2}$,
$$
\begin{align}
-\frac{1}{2}\leq 1 - L \leq \frac{1}{2} \\
-\frac{3}{2}\leq - L \leq -\frac{1}{2} \\
\frac{1}{2}\leq L \leq \frac{3}{2} \\
\end{align}
$$
And also $|-1-L|=|1+L|< \frac{1}{2}$
$$
\begin{align}
-\frac{1}{2}\leq 1 + L \leq \frac{1}{2} \\
-\frac{3}{2}\leq L \leq -\frac{1}{2} \\
-\frac{3}{2}\leq L \leq -\frac{1}{2} \\
\end{align}
$$
This is a contradiction


# Discussion
Show $\lim_{ x \to 0 }\sin(\frac{1}{x})$ does not exist
but $\lim_{ x \to 0 }x\sin(\frac{1}{x})$ does