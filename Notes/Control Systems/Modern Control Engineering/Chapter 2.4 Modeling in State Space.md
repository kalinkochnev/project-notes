**State** - state of a dynamical system is the the smallest set of variables such that knowledge of the state at $t=t_{0}$ and the input $t\geq t_{0}$ completely determines behavior of the system 
- state variables do not necessarily need to be physical quantities or measurable or observable. Usually are though.
-  # of state variables is same for any different state-space repr. of the same system

**State vector** - the $n$ state variables can be considered the $n$ components of a vector $\vec{x}$

**State space** - Any state can be represented by a point in n-dimensional state space. Axes are state variables $x_{1}\dots x_{n}$

# State space representation
- Dynamical systems are modeled with 3 types of vars: inputs $u_{1}(t)\dots u_{n}(t)$, outputs $y_{1}(t)\dots y_{m}(t)$, and state
- Integrators track/remember state. For every state variable there is 1 integrator.

## Vectorized state space representation
How the system changes is a function of the current state and the current input
$$
\begin{gather}
\dot{x}_{1}(t)=f_{1}(x_{1}\dots x_{n}; u_{1}\dots u_{n}) \\
\dot{x}_{2}(t)=f_{2}(x_{1}\dots x_{n}; u_{1}\dots u_{n})\\
\vdots \\
\dot{x}_{n}(t)=f_{n}(x_{1}\dots x_{n}; u_{1}\dots u_{n})\\
\end{gather}
$$
The output of the system is also a function of current state and current input
$$
\begin{gather}
\dot{y}_{1}(t)=g_{1}(x_{1}\dots x_{n}; u_{1}\dots u_{n}) \\
\dot{y}_{2}(t)=g_{2}(x_{1}\dots x_{n}; u_{1}\dots u_{n})\\
\vdots \\
\dot{y}_{m}(t)=g_{m}(x_{1}\dots x_{n}; u_{1}\dots u_{n})\\
\end{gather}
$$
We can vectorize all of these equations as so
$$
\begin{gather}
\textbf{x}(t)=\begin{bmatrix}
x_{1}(t)  \\
\vdots \\
x_{n}(t)
\end{bmatrix}
\textbf{y}(t)=\begin{bmatrix}
y_{1}(t)  \\
\vdots \\
y_{n}(t)
\end{bmatrix}
\textbf{u}(t)=\begin{bmatrix}
u_{1}(t) \\
\vdots \\
u_{r}(t)
\end{bmatrix}
 \\
\textbf{f}(\textbf{x}, \textbf{u}, t) = \begin{bmatrix}
f_{1}(x_{1}\dots x_{n}; u_{1}\dots u_{n}) \\
\vdots \\
f_{n}(x_{n}\dots x_{n}; u_{1}\dots u_{n})
\end{bmatrix}

\textbf{g}(\textbf{x}, \textbf{u}, t) = \begin{bmatrix}
g_{1}(x_{1}\dots x_{n}; u_{1}\dots u_{n}) \\
\vdots \\
g_{n}(x_{n}\dots x_{n}; u_{1}\dots u_{n})
\end{bmatrix}
\end{gather}
$$
The entire system can then be described as
$$
\begin{align}
\dot{\textbf{x}}(t)=\textbf{f}(\textbf{x}, \textbf{u}, t)\\
\textbf{y}(t)=\textbf{g}(\textbf{x}, \textbf{u}, t)
\end{align}
$$
- If $f$ or $g$ depend on time, it is a time varying system
## Linearization
- Perhaps $f$ and $g$ are linear with respect to $\textbf{x}(t)$ and $\textbf{u}(t)$ (the current state and current input) 
$$
\begin{gather}
\dot{\textbf{x}}(t)=\textbf{A}(t)\textbf{x}(t) + \textbf{B}(t)\textbf{u}(t) \\
\textbf{y}(t)=\textbf{C}(t)\textbf{x}(t) + \textbf{D}(t)\textbf{u}(t)
\end{gather}
$$
- State matrix = $\textbf{A}(t)$, Input matrix = $\textbf{B}(t)$. Output matrix= $\textbf{C}(t)$, Direct transmission matrix $\textbf{D}(t)$

In the block diagram representation, notice the summing point that adds together the state matrix (which gives the next state based on current state) as well as the input matrix which modifies how the input affects the state

![[Pasted image 20231222100626.png]]

## Derivation of transfer function from state space
- Eigenvalues of the system are the poles of the transfer function
![[Pasted image 20231222110443.png]]