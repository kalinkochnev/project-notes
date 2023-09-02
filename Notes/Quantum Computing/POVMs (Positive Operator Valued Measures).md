**Definition:** A collection of operators that are positive and the following are true
1) $\{E_{x}\}_{x\in X}$   for every outcome there is one POVM
2) $E_{x}$ is positive, semi-definite for all $\ket{z}$ so $\bra{z}E_{x}\ket{z} \geq 0$
Positive because $p(x)=\bra{\psi}M_{x}^*M_{x}\ket{\psi}=\braket{y |y }$ and the inner product of same vectors is always positive and real. 

3) $\sum E_{x}=I$ - must be a probability distribution

- Any valid [[Postulates of Quantum Mechanics#3: How are Quantum measurements made? |measurement]] can construct a POVM with $M_{x}^* M_{x}$
- Used when the post-measured state is unimportant 

### Create a measurement operator than can measure $\ket{0}$ or $\ket{+}$ and never be wrong
- Create 3 states