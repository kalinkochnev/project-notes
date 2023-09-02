For every $\epsilon>0$ want to get the function close to some $y$ (ex: -12) by making $x$ close within a range $\delta$ to what you are approaching (ex: 1)
- Given an $\epsilon$, you can find a $\delta$ such that 

# Definition
$\forall \epsilon >0, \exists \delta >0$ s.t. ($\forall x$) $0<|x-c| < \delta \implies|f(x)-L|<\epsilon$
- Given any epsilon I can find a del-ta such that the distance between $x$ and the input I am approaching $c$ is less than $\delta$.
- For any $x$ in that range the function value is between $L-\epsilon <f(x)<L+\epsilon$
- 

# Examples
#### **Prove** that $\lim_{ x \to 2 } 3x+4=10$
$\forall\epsilon>0, \exists\delta>0$ s.t. $0<|x-2|<\delta \implies |f(x)-10|<\epsilon$
*Scratch work:*
- We want to show that delta depends on epsilon
$$
\begin{align}
|f(x)-10|<\epsilon \\
|3x+4-10|<\epsilon \\
|3x-6|<\epsilon \\
3|x-2| < \epsilon \\
|x-2| < \frac{\epsilon}{3} \\
\text{ let } \delta=\frac{\epsilon}{3}
\end{align}
$$

Proof:
Let $\epsilon>0$ and $\delta=\frac{\epsilon}{3}$
Assume that $0<|x-2|<\delta$. Then
$$
\begin{align}
|x-2|< \frac{\epsilon}{3} \\
3|x-2| < \epsilon \\
|3x-6|<\epsilon \\
|3x+4-10|<\epsilon \\
|f(x)-10|<\epsilon
\end{align}
$$
As needed.

#### Prove that $\lim_{ x \to 2 }5x^{2}=20$
$\forall \epsilon>0, \exists\delta s.t. 0<|x-2|<\delta \implies|5x^{2}-20|<\epsilon$
**Scratch work**
$$
\begin{align}
|5x^{2}-20|<\epsilon \\
5|x^{2}-4| < \epsilon \\
5|x-2| |x+2|< \epsilon \\
|x-2| < \frac{\epsilon}{5|x+2|}
\end{align}$$
You can't make $\delta$ depend on x. Need to find a $\delta$ so that
$$
|x-2|<\delta< \frac{\epsilon}{5|x+2|}
$$
We know x is close to 2 and is bounded by delta
$$
-\delta < x-2<\delta
$$
We can arbitrarily restrict delta so that it never gets too big, so let $d\leq 1$.
$$
\begin{align}
-1 < -\delta < x-2 < \delta < 1 \\
\text{add +4 to get x+2} \\
3 < x-2 < 5 \\
\text{ what the case is, } |x-2| < 5
\end{align}
$$
So let $\delta=\frac{\epsilon}{5(5)} < \frac{\epsilon}{5|x+2|}$. This works b/c |x+2| < 5, so a smaller denominator means a bigger number. 

**Proof** 
Let $\epsilon>0$ and Let $\delta=min\{\frac{\epsilon}{25},1\}$. Assume $0<|x-2|<\delta=\frac{\epsilon}{25}$
Note that $|x-2|<1$ b/c $\delta<1$. So
$$
\begin{align}
-1<x-2<1 \text{ (add 4 to both sides)} \\
3 < x +2 < 5 \\
|x+2|<5
\end{align}
$$
So $|x-2|< \frac{\epsilon}{25}< \frac{\epsilon}{5|x+2|}$. Then $5|x-2\mid |x+2|<\epsilon$.
So $| 5x^{2}-20|<\epsilon$

# Discussion
Consider $\lim_{ x \to 3 }2x+1=7$.
If $\epsilon=0.5$, which $\delta$ gives $0<|x-3|<\delta \implies |2x+1-7|<\epsilon$
![[Pasted image 20230419112914.png]]