## Process
1. Prepare a state $\ket{\psi_{x}}$, which is $\ket{x_{1}x_{2}\dots x_{n}}$ and $x_{n} \in \{ 0,1 \}$ 
-> this is actually $2^n$ because the space is a tensor of $x_{1}\dots x_{n}$ which doubles every time (since 0 or 1)

2. Run a unitary algorithm $U\ket{\psi_{x}}$
3. Measure (usually in [[Bases#Standard vectors|z-basis]]) then interpret the output
4. May need to repeat the algorithm since measurements are probabilistic

## Practicality
- It is not always practical to create $U$ because it is $2^n \times 2^n$ matrix. Use basic [[Quantum Circuit Model#Quantum circuit model]] to decompose U

# Deutsch-Joza Algorithm
#game
A person gives the computer a function $f(x)$ where $f: \{ 0,1 \}^n \to \{ 0,1 \}$ and are promised either
**balanced** - half of input space outputs a 0, and half outputs a 1 (randomly assigned)
**constant** - constant (0 or 1) for all values of x

The computer must answer in as few queries as possible to answer whether it is balanced or constant. 

Assuming $f(x)$ can be converted into a quantum circuit (so inputs are a superposition of possible inputs), this algorithm can give with 100% certainty whether balanced or constant. Uses "quantum parallelism"

## Summary
- Classical needs $2^{n-1} + 1$ queries worst case while quantum needs only 1
- Need to test half input space + 1 to determine if balanced or constant ($\frac{2^{n}}{2} +1$)
- "Phase kickback" where by algebraic manipulation you can re-express the current state differently so the classical output is in the phase

![[Pasted image 20230319165021.png]]
### $\ket{t_{1}}$
At, apply the hadamard to the inputs $\ket{t_{1}}: H^{\otimes n+1}\ket{0}^{\otimes n}\ket{1}$
$$
\begin{align} \\
\ket{t_{1}} =
\left( \frac{1}{\sqrt{ 2 ^{n}}}\sum_{x \in \{ 0,1 \}^{n}} \ket{x} \ket{-} \right) = \frac{1}{\sqrt{ 2^{n} }}\sum_{x \in \{  0,1 \}^{n}}\ket{x} \left( \frac{\ket{0} -\ket{1} }{\sqrt{ 2 }} \right) = \frac{1}{\sqrt{ 2^{n+1} }}\sum_{x \in \{  0,1 \}^{n}}\ket{x,0}-\ket{x,1} 
\end{align}
$$

### $\ket{t_{2}}$
At $\ket{t_{2}}$, apply the [[Quantum Circuit Model#Oracle gate|oracle gate]] in order to represent a classical function.
$$
\ket{t_{2}} :U_{f}\ket{t_{1}} = \frac{1}{\sqrt{ 2^{n+1} }}\sum_{x \in \{ 0,1 \}^{ n}} \ket{x}\ket{0 \oplus f(x)}-\ket{x} \ket{1 \oplus f(x)} 
$$
Check what $t_{2}$ evaluates to for cases $f(x)=0$ and $f(x)=1$
**If f(x)=1**: 
$$
\begin{align}
\frac{1}{\sqrt{ 2^{n+1} }} \sum_{x \in \{ 0,1 \}^{n}} \ket{x} \otimes (\ket{0 \oplus 1 }-\ket{1 \oplus 1})=\frac{1}{\sqrt{ 2^{n+1} }} \sum_{x \in \{ 0,1 \}^{n}} \ket{x}(\ket{1}-\ket{0}) \\
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x \in \{ 0,1 \}^{n}} -\ket{x}\ket{-}
\end{align}
$$
**If f(x)=0**: 
$$
\begin{align}
\frac{1}{\sqrt{ 2^{n+1} }} \sum_{x \in \{ 0,1 \}^{n}} \ket{x} \otimes (\ket{0 \oplus 0 }-\ket{1 \oplus 0})=\frac{1}{\sqrt{ 2^{n+1} }} \sum_{x \in \{ 0,1 \}^{n}} \ket{x}(\ket{0}-\ket{1}) \\
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x \in \{ 0,1 \}^{n}} \ket{x}\ket{-}
\end{align}
$$
*Notice the negative sign is the only difference*. We can "kick back" the phase (the sign) by making it depend on the value of f(x) only. 
$$\ket{t_{2}}=\frac{1}{\sqrt{ 2^{n} }} \sum_{x \in \{ 0,1 \}^{n}}(-1)^{f(x)} \ket{x,-}$$
### $\ket{t_{3}}$
$$
\begin{align}
\ket{t_{3}}: (H^{\otimes n}\otimes I) \ket{t_{2}}=\left( \frac{1}{\sqrt{ 2^{n} }}\sum_{x \in \{ 0,1 \}^{n}}(-1)^{f(x)}H^{\otimes n}\ket{x}  \right) \otimes I\ket{-}  \\
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x \in \{ 0,1 \}^{n}} (-1)^{f(x)} \frac{1}{\sqrt{ 2^{n} }}\left( \sum_{z \in \{ 0,1 \}^{n}} (-1)^{x \cdot z} \ket{z} \braket{x | x}  \right) \otimes \ket{-}  \\
= \frac{1}{ 2^{n}} \sum_{z \in \{ 0,1 \}^{n}} \sum_{x \in \{ 0,1 \}^{n}} (-1)^{f(x) + x \cdot z}\ket{z} \otimes \ket{-} 
\end{align} 
$$
The $\otimes\ket{-}$ is known as a separable state. It can effectively be "factored" out of the entire sum.
- $\sum_{x \in \{ 0,1 \}^{n}}$ is the superposition of all input bit strings
- $\sum_{z \in \{ 0,1 \}^{n}}$ is the sum of all possible outcomes, similar to $\alpha \ket{0\dots 0}+\beta \ket{00\dots 1}+\dots+z\ket{1\dots 1}$
- The probability of observing a particular outcome $z$ bitstring is the squared magnitude of the outcome $\mid \alpha\mid^{2}$
- Coefficient in each case is $\frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)+x\cdot z}$

### Measure the probability of outcome $z=00\dots 0$
$$
\begin{align}
P(z=0\dots 0)=\left| \frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)+x\cdot z} \right|^{2} \\
\text{because z=all zeroes, } \left| \frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)} \right|^{2}\\
\end{align}
$$
### Interpreting the results
#### If f(x) is constant (all zeroes or all ones)
- The probability is 1 if constant
**f(x)=0**
$$
\left| \frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)} \right|^{2}=\left| \frac{1}{2^{n}} 2^{n} \right|^{2} = 1
$$
**f(x)=1**
$$
\left| \frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)} \right|^{2}=\left| \frac{1}{2^{n}} (-2^{n}) \right|^{2} = 1
$$
#### If f(x) is balanced (half 1s, half 0s)
- The probability is 0 if balanced
$$
\left| \frac{1}{2^{n}} \sum_{x \in\{ 0,1 \}^{n}}(-1)^{f(x)} \right|^{2}=\left| \frac{1}{2^{n}} (1+1+\dots +1) + (-1-1 \dots -1) \right|^{2} = 0
$$



# Example
f(x)=f(y) iff $y=x xor s$ for some secret $S \in \{ 0,1 \}^{n}$

You have a punction with a hidden period s. In how many queries can you find the period?
$f(x)=f(x+r)=f(x+2r)$
- Classically best method is guess and check ($2^{n/2}$) until you find two outputs that match


# Quantum teleportation
- Can't communicate faster than light. The bell pair
- Alice needs to send two classical bits to Bob so then he can apply the x and z gate depending on what Bob's results are
- 1 entangled bit + 2 classical bits >= 1-qubit


# Superdense coding
[[Density Operators]]
1. Person A and B share a bell pair $\ket{\Phi^{+}}$
2. `A` encodes 2 bit message onto one half of entangled pair
3. `A` sends their particle to `B` so they have both particles
4. Bob does a bell measurement
| Probability | $m_{2}$ | $m_{1}$ | Operator |
| ----------- | ------- | ------- | -------- |
| p(00)           | 0       | 0       |   I       |
| p(01)           | 0       | 1       |    X      |
| p(10)           | 1       | 0       |     Z     |
| p(11)           | 1       | 1      |      XZ    |

- W/ prob p(00) Alice applies $(I_{A}\otimes I_{B}\ket{\Phi^{+}}\bra{\Phi^{+}}I^*_{A}\otimes I^{*}_{B})$. Repeat w/ other probabilities

$+p(01)(X_{A} \otimes I_{B}\ket{\Phi^{+}}\bra{\Phi^{+}} X^{*}\otimes I)$
X- not gate

$$
\rho=p(00)\ket{\Phi^{+}}\bra{\Phi^{+}}+p(01)\ket{\Psi^{+}} \bra{\Psi^{+}} + p(10)\ket{\Phi^{-}} \bra{\Phi^{-}} + p(11)\ket{\Psi^{-}} \bra{\Psi^{-}}  
$$

- Apply partial trace to see that no information is transfered
$$
\rho_{B}=tr_{A}(\rho_{AB})=tr_{A}(p(00)\ket{\Phi^{+}} \bra{\Phi^{+}} )+\dots tr_{A}(p(11)\ket{\Psi^{-}}\bra{}  )
$$

- If we ignore Alice's particle, we cannot distinguish between different states at all (everything always $\frac{I}{2}$)
	- The reduced system is identical to the coinflip $\left\{  \left( \frac{1}{2}, \ket{0} \right), \left( \frac{1}{2}, \ket{1} \right)  \right\}$ 
	- Is 1 qubit b/c Bob's system is only one particle
$$
tr_{A}(\ket{\Phi^{+}}\bra{\Phi^{+}}  )=\frac{1}{2}(\ket{0} \bra{0} +\ket{1} \bra{1}) = \frac{I}{2}
$$
## What if two density operators are "close" to one another?
- They should act similarly if they have similar parameters
$$
\Delta (\rho,\sigma)=\frac{1}{2}tr|\rho-\sigma| = \frac{1}{2} \sum|\lambda_{i}|
$$
- $\rho,\sigma$ are both two density operators
- $\lambda_{i}$ are eigenvalues of $\rho-\sigma$
- 1/2 comes from triangle inequality

### Properties
- $\Delta(\rho,\sigma)=\Delta(\sigma,\rho)$
- $\Delta(\rho,\rho)=0$
$$
\begin{align}
\Delta(\rho,\tau)\leq \Delta(p,\sigma) \leq \Delta(\rho,\sigma)+\Delta(\sigma,\tau) \\
\text{let tau=rho} \\
\Delta(\rho, \rho) \leq \Delta (\rho, \sigma) \leq 2 \Delta(\rho, \sigma) \\
0 \leq 1 \leq 2 \\
0 \leq \frac{1}{2} \leq 1
\end{align}
$$
## Distance between classical prob. distributions
- Classical random variable/information can be modeled as quantum state
- Lets say we have ensemble of states $E_{x}:\{ (P_{x}(n), \ket{n}) \}$ and $E_{y}: \{ (P_{Y}(n), \ket{n}) \}$
- Density operator $\rho=\sum_{i=0}^{n}P_{x}(i)\ket{i}\braket{ i}$ and $\rho=\sum_{i=0}^{n}P_{y}(i)\ket{i}\bra{i}$
$$
\begin{align}
\rho-\sigma=\sum_{i=0}^{n}P_{x}(i)\ket{i}\braket{ i}-\sum_{i=0}^{n}P_{y}(i)\ket{i}\braket{ i} \\
=\sum_{i}(P_{x}(i)-P_{y}(i))\ket{i} \bra{i} 
\end{align}
$$
- This is a diagonal matrix b/c $\ket{i}\bra{i}$
- Eigenvalues are the entries along the diagonal, $P_{x}(i)-P_{y}(i)$

- The distance between two different probabiltiy distributions absolute diff. between probabilities of each $\frac{1}{2}\sum_{i=0}^{n} | P_{x}(i)-P_{y}(i) |$


$$
\begin{align}
\Delta(\rho, \sigma)=max_{M}tr((M[\rho-\sigma])) \\
=max_{P} (tr(M[\rho])-tr(M[\sigma])) \\
=max_{M}(tr(M[\rho]-M[\sigma])) \\ \\

=max_{M}(tr(M[\rho])-tr(M[\sigma]))
\end{align}
$$
- Trying to find the maximum distance between the probability distributions
- $P$ first element of a two outcome measurement
- Where $M$ is a projector/measurement onto a subspace and is being applied to $\rho-\sigma$