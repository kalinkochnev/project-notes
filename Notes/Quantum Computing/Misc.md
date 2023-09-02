# BQP subset PSPACE
- Any polynomial time quantum algorithm
	- meaning a circuit with a polynomial # of gates
	- A gate is a unitary operation (easy to describe)
	- Outputs Pr(given $\ket{x}$, output is "y") = $\bra{y} U_{p}\dots U_{1}\ket{x}$
$$
\begin{align}
=\bra{y} U_{p}IU_{p-1}\dots IU_{3}IU_{2}IU_{1} \ket{x} 
\end{align}
$$
The identity operator is defined as the $\sum_{i \in\{ 0,1 \}^{n}} \ket{i}\bra{i}$
$$
\begin{align}
\bra{y} U_{p}\left( \sum_{i \in\{ 0,1 \}^{n}} \ket{i}\bra{i} \right)U_{p-1}\dots U_{2} \left( \sum_{i \in\{ 0,1 \}^{n}} \ket{i}\bra{i} \right)U_{1} \ket{x}  \\
= \sum_{i_{1},i_{2},\dots ,i_{n}}\dots U_{3}\ket{i_{2}} \bra{i_{2}} U_{2} \ket{i_{1}} \bra{i_{1}} U_{1} \ket{x} 
\end{align}
$$
- You can simulate a quantum algorithm just by evaluating the inner product
- This is pretty doable because $U_{n}$ is very easy to compute and you can just evaluate term by term and not store massive amounts of state data
- However you have a massive sum/for loop which 
- Quantum algorithms can't do better than polynomial time