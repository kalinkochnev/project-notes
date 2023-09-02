- $\ket{\psi} \to U \to M$ is really the same as $\ket{\psi}\to U^{other}$
- Any intermediate measurements can be simulated as unitary operators anyways

- We simulate measurements by putting the "measured" state into a new superposition. This doesn't collapse the state

$$
\begin{align}
\ket{\psi}  \to \tilde{U} \to M \\
\ket{\psi} \otimes \ket{0} \to U \otimes I \to \ket{\phi} \otimes \ket{0} \to V
\end{align}
$$


- If the measurement $M$ is complicated to describe, then so will the algorithm $V$


$CNOT\ket{\psi,0}=\frac{1}{\sqrt{ 2 }}(\ket{00}+\ket{11})$ This is equivalent to copying the state 
- You can use CNOTs to "record" what you would have measured at that point and copy into an auxiliary register
- If $\ket{\psi}=\frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1})$, we can save a copy of $\ket{\psi}$ into another register

# Measurements as Unitary Operators
- Apply a unitary operation is really the same thing as a measurement, except you don't observe it and destroy the state
- You can save the effect of an operation/measurement into another register to observe the progress of the algorithm later
	- doing so doesn't collapse the state
- V is an operator that shoves the measurement outcome into the 2nd tensor (auxiliary space)  $V\ket{\phi,0} = \sum_{x} M_{x} \ket{\phi} \otimes \ket{x}$
- Auxiliary space keeps track of all the possible outcomes that could have been
- The complexity of an algorithm isn't solely on the unitary operations, but also the measurements. 

# No cloning theorem
There does not exist an operator $U$ such that $U\ket{\psi,0}=\ket{\psi}\otimes \ket{\psi}$ for all $\ket{\psi}$
- Orthogonal things are the only things you can clone
- Does not preserve inner norm
	- $U\ket{\psi,0}=\ket{\psi}\otimes \ket{\psi}$ and $U\ket{\phi,0}=\ket{\phi}\otimes \ket{\phi}$ 
	- $\braket{\psi | \phi}\braket{0 | 0} \neq \braket{\psi | \phi}\braket{\psi | \phi}$

## Correlary
- If you can't clone something, then you can't erase a quantum state
- $U\ket{\psi,\psi} \to \ket{\psi,0}$, which is really $U^{*}\ket{\psi,0}\to \ket{\psi,\psi}$ which is the no cloning theorem