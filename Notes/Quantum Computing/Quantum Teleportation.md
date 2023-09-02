Alice has a quantum state $\ket{\psi}=\alpha \ket{0}+ \beta \ket{1}$she wants to the information send to Bob. How does she do it?

**You never are transmitting particles! Just information about the state**
- Doesn't violate [[Quantum Complexity#No cloning theorem]] b/c $\ket{\psi}$ is destroyed by measurement and there is only one particle with exactly $\ket{\psi}'s$ state

# Overview
1. Split a bell pair $\ket{\Phi^{+}}=\frac{1}{\sqrt{ 2 }}(\ket{00}+\ket{11})$ particle and give one to Alice and one to Bob
	- Alice has two particles, her quantum state and her bell pair
2. Alice applies a $CNOT$ w/ Alice's particle (control) and Bob's particle target
3. Alice applies hadamard on the state she wants to send
4. She then measures the state of $\ket{\psi}$ and her pair. She sends the classical information to Bob who then applies an X gate or a Z gate based on 
5. Alice measures her particle's state
![[Pasted image 20230327160348.png]]

# Derivation
$t_{0} = \ket{\psi}\otimes \ket{\Phi^{+}} = (\alpha \ket{0}+\beta \ket{1})\left( \frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{11} \right)=\frac{1}{\sqrt{ 2 }}(\alpha \ket{000}+\alpha \ket{011}+\beta \ket{100}+\beta \ket{111})$
### Apply CNOT and Hadamard to Alice
$t_{1}=\frac{1}{\sqrt{ 2 }}(\alpha \ket{000}+\alpha \ket{011} +\beta \ket{110} +\beta \ket{101})$
- Apply the CNOT gate to $\ket{\psi}$ (control) and to Alice's bell pair (target)
	- If $\ket{\psi}=1$, then that flips the bell pair
	- Doesn't affect Bob's bell pair

$$
\begin{align}
t_{2}=(H\otimes I^{2})\ket{t_{1}}=  \\
\frac{1}{\sqrt{ 2 }} \frac{1}{\sqrt{ 2 }}(\alpha(\ket{0}+\ket{1}) \ket{00} + \alpha(\ket{0}+\ket{1}) \ket{11}+\beta (\ket{0}-\ket{1}) \ket{10} + \beta(\ket{0}-\ket{1}) \ket{01}) \\
=\frac{1}{2}(\alpha \ket{000} +\alpha \ket{100} + \alpha \ket{011} + \alpha \ket{111} + \beta \ket{010} - \beta \ket{110} + \beta \ket{001} - \beta \ket{101})
\end{align}
$$

### Measure Alice's qubits
- Measure the first two qubits that alice has at at $\ket{t_{3}}$.
	- How would you measure something like $\alpha \ket{0}+\beta \ket{1}+\gamma \ket{0}+ \lambda \ket{0}=(\alpha+\gamma+\lambda)\ket{0}+(\beta)\ket{1}$
	- Cluster together terms
	- P(0)= $(\alpha+\gamma+\lambda)^{2}$

- Let $\ket{e_{n}}$ be the nth term here
$$
\begin{align}
\ket{00} \otimes \left( \frac{1}{2} \alpha \ket{0} + \frac{1}{2} \beta \ket{1}   \right) \\
+\ket{01} \otimes \left( \frac{1}{2}\alpha \ket{1} + \frac{1}{2} \beta\ket{0}   \right) \\
+\ket{10} \otimes \left( \frac{1}{2} \alpha \ket{0}  -\frac{1}{2} \beta \ket{1}  \right) \\
+\ket{11} \otimes \left( \frac{1}{2} \alpha \ket{1} - \frac{1}{2} \beta \ket{0}  \right) 
\end{align}
$$

### Bob applies X or Z depending on Alice's results
$Pr("00")= \braket{e_{0} | e_{0}}= \left( \frac{1}{2} \alpha^{*}\ket{0} + \frac{1}{2}\beta^{*}\braket{ 1} \right)\left( \frac{1}{2} \alpha \ket{0}+\frac{1}{2}\beta \ket{1} \right)=\frac{1}{4} | \alpha|^{2}+\frac{1}{4} \mid \beta \mid =\frac{1}{4}$
- We know $\alpha^{2}+\beta^{2}=1$ b/c is a normalized quantum state

If the state observed for Bob was...
"00" PM =  $\frac{\ket{e_{0}}}{\sqrt{ P("00") }}=\frac{\ket{e_{0}}}{\sqrt{ \frac{1}{4} }}=\alpha \ket{0}+\beta \ket{1}=\ket{\psi}$ by default

"01" $\alpha \ket{1}+\beta \ket{0} \to \text{apply X gate}\to \alpha \ket{0}+\beta \ket{1}=\ket{\psi}$
- If you have 01 you can do a bit flip and get $\ket{\psi}$ back!
- The X gate ([[Quantum Circuit Model#Basic Gates| bit flip]]) is controlled by the second bit
 
"10" $\alpha \ket{0}-\beta \ket{1} \to \text{apply Z gate} \to \alpha \ket{0}+\beta \ket{1}$
- The Z gate ([[Quantum Circuit Model#Basic Gates | phase flip]]) is controlled by the first bit

"11" $\alpha\ket{1}-\beta \ket{0} \to \text{apply Z and X basis}$
