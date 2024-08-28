## Derivation of method
 Lets say we have a differential equation $\frac{d \vec{x}}{dt}= \mathbf{A}\vec{x}$ and you can write the energy of the system $V$ as a quadratic form $V=x^{T}Px$.
 If a system is stable, aka it always decays/attracts to an equilibrium, then
 $$\begin{align}
\frac{dV}{dt} < 0  \\
\dot{x}^{T}Px + x^{T}P\dot{x} < 0 \\
\end{align}$$
We know that $\dot{x}=\textbf{A}x$ so
$$
\begin{align}
(\textbf{A}x)^{T}Px + x^{T}P(\textbf{A}x) < 0 \\
x^{T}(A^{T}P + PA)x < 0
\end{align}
$$
In order for this inequality to hold true,  $A^{T}P + PA$ is negative definite (does not include 0) then $\frac{dV}{dt}<0$

In general the $\frac{d \vec{x}}{dt}= \mathbf{A}\vec{x}$ autonomous system can be characterized by eigenvalues (if all negative and real then decays). However if the matrix is time dependent this is no longer the case.

The Lyapunov method can work for time dependent matrices. So if for all time steps we can find $P$ (assuming it is positive semidefinite) so that the inequality 
$$
A^{T}P + PA \prec 0
$$
Is true, then we know the system is stable.
If it is unstable, then it is bounded by an exponential. Something is bounded by an exponential when
$$
\mid\mid x(t)\mid\mid \leq e^{c\lambda t}\mid\mid x(0)\mid\mid
$$
In the unstable case, when $V >0$ then $\frac{dV}{dt}<2\lambda V$. 
$$
\begin{align}
\frac{dV}{dt}-2\lambda V < 0 \\
x^{T}(A^{T}P + PA)x -x^{T}2\lambda Px <0 \\
x^{T}(A^{T}P + PA - 2\lambda P)x <0 \\ \\
A^{T}P + PA < 2\lambda P
\end{align}
$$
