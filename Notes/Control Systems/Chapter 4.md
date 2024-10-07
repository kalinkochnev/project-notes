![[Control System Engineering.pdf#page=187&rect=191,280,541,708|Control System Engineering, p.138]]

# Laplace Transform solution of state space equations
Let the state variable in the frequency domain be represented as:

$X(s)=(sI - A)^{-1} x(0) + (sI-A)^{-1}BU(s)=(sI-a)^{-1}(x(0)+BU(S))$ (assuming non-zero conditions)
and the output equation  $Y(s)=CX(s)+DU(s)$ 

Substitute $X(s)$ in $CX(s)+DU(s)$ and assume the initial conditions are zero
$$
\begin{align}
Y(s) &= C\left[(sI-A)^{-1}(x(0)+BU(s))\right] + DU(s) \\
&= C(sI-A)^{-1}BU(s)+DU(s) \\
&= [C(sI-A)^{-1}B+D]U(s)
\end{align}
$$
Solve for $\frac{Y(s)}{X(s)}$
$$
\begin{align}
Y(s)=[C(sI-A)^{-1}B+D]U(s) \\
\frac{Y(s)}{X(s)} = C(sI-A)^{-1}B+D
\end{align}
$$
We know that the inverse of a matrix [[Cramer's Rule#Solving for $A {-1}$|using the adjugate]] is $A^{-1}=\frac{1}{\det[A]}\text{adj}[A]$.

So 
$$
\begin{align}
\frac{Y(s)}{X(s)} &= C\left[\frac{\text{adj}[sI-A]}{\det[sI-A]} \right]B+D \\
&= \frac{C\text{adj}[sI-A]B+D\det [sI-A]}{\det[sI-A]}
\end{align}
$$
The roots of the denominator are the poles, which are also the eigenvalue of $sI-A$
