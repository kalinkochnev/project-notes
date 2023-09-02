https://en.wikipedia.org/wiki/Quantum_foundations

# Entaglement
- Operations on one particle (a subspace of the tensor) affects the global state

- Alice has access to left subspace, Bob to the right
$\frac{1}{\sqrt{ 2 }}\ket{00} +\frac{1}{\sqrt{ 2 }}\ket{11}$
A       B    A     B
$\ket{0}\otimes \ket{0}; \ket{1}\otimes \ket{1}$

- Condition for  [[Entangled systems#Entaglement |entaglement]]: can we write it as a simple [[Tensor Product#Tensor Product |tensor product]]?
- Tensored vectors do not necessarily mean they are entagled!

## Acting on q-bits individually
- Alice can act only on $\ket{00}$, which is modeled by (use left on left, right on right) $U \otimes I_{B}\ket{\Phi^+}=U\otimes I\left( \frac{1}{\sqrt{ 2 }} \ket{00} + \frac{1}{\sqrt{ 2 }}\ket{11} \right)=\frac{1}{\sqrt{ 2 }}(U\ket{0})\otimes \ket{0}+\frac{1}{\sqrt{ 2 }}(U\ket{1})\otimes \ket{1}$
- U is operation by Alice, $I_{B}$ represents Bob not doing anything

### example: Find $H \otimes H\ket{\Phi^+}$ in the z basis 
- H is the haddamard [[Bases#Hadamard |operator]]
$$\begin{align}
H\ket{0} =\ket{+}; H\ket{1} =\ket{-}   \\
=H\ket{\Phi^+} \otimes H\ket{\Phi^+} \\
=\frac{1}{\sqrt{ 2 }} (H\otimes H\ket{00} +H\otimes H\ket{11} ) \\
=\frac{1}{\sqrt{ 2 }} \ket{ ++}+\frac{1}{\sqrt{ 2 } } \ket{--}  
\end{align}$$
- Change basis to Z. Sanity check, should be normalized
$$\begin{align}
=\frac{1}{\sqrt{ 2 }}\left( \frac{1}{\sqrt{ 2 } }\ket{0} +\frac{1}{\sqrt{ 2 }}\ket{1}  \right) \otimes \left( \frac{1}{\sqrt{ 2 } }\ket{0} +\frac{1}{\sqrt{ 2 }}\ket{1}  \right)+\frac{1}{\sqrt{ 2 }} \left( \frac{1}{\sqrt{ 2 } }\ket{0} -\frac{1}{\sqrt{ 2 }}\ket{1}  \right) \otimes \left( \frac{1}{\sqrt{ 2 } }\ket{0} -\frac{1}{\sqrt{ 2 }}\ket{1}  \right) \\
=\frac{1}{2\sqrt{ 2 }}(\ket{00} +\ket{10} +\ket{01} +\ket{11} ) + \frac{1}{2\sqrt{ 2 }}(\ket{00} -\ket{01} -\ket{10} +\ket{11} ) \\
=\frac{1}{2 \sqrt{ 2 } }(2\ket{00} +2\ket{11} ) \\
=\frac{1}{\sqrt{ 2 }}\ket{00} +\frac{1}{\sqrt{ 2 }}\ket{11} =\ket{\Phi^+} 
\end{align}$$
- **Only for bell states**  $U\otimes I\ket{\Phi^+}=I\otimes U^* \ket{\Phi^+}$, which basically says that if Alice does something and bob does nothing, that is the same as alice does nothing and bob does something
$$\begin{align}


\end{align}$$

## Measuring multiple entangled q-bits
[[Measurement]]
$\{M_{x}\}:\mathbb{C}^n\otimes \mathbb{C}^n\to \mathbb{C}^n\otimes \mathbb{C}^n$

- If $\{M_{x}\}$ is a valid 1 q-bit measurement, then $\{M_{x}\otimes I_{B}\}$ is a valid 2-quibit measurement (only for Alice)

**Proof: Show valid measurment**
$$\begin{align}
=\sum N_{x}^*N_{x}=\sum(M_{x}\otimes I)^*(M_{x} \otimes I) \\
= \sum(M_{x}^* \otimes I)(M_{x}\otimes I)=\sum_{x}M_{x}^*M_{x}\otimes I \\
=\left( \sum_{x}M_{x}^* M_{x} \right)\otimes I \\
=I\otimes I=I
\end{align}$$

### What happens to the whole system when Alice measures?
$M_{0}=\ket{0}\bra{0}, M_{1}=\ket{1}\bra{1}$     $N_{0}=\ket{0}\bra{0}\otimes I, N_{1}=\ket{1}\bra{1}\otimes I$
P(Alice seeing a "0") = $\bra{\Psi^+}N_{0}^*N_{0}\ket{\Psi^+}$
$$\begin{align}
N_{0}\ket{\Psi^+}=\frac{1}{\sqrt{ 2 }}(\ket{0} \bra{0} \otimes I)\ket{00} +\frac{1}{\sqrt{ 2 }}(\ket{0} \bra{0} \otimes I )\ket{11}  \\
=\frac{1}{\sqrt{ 2 }}\ket{0} \braket{0 | 0} \otimes \ket{0} + \frac{1}{\sqrt{ 2 }}\ket{0} \braket{0 | 1 }\otimes \ket{1} \\
=\frac{1}{\sqrt{ 2}}\ket{00}   
\end{align}$$
$$\begin{align}
\bra{00} \frac{1}{\sqrt{ 2 }} \frac{1}{\sqrt{ 2 }}\ket{00} =\frac{1}{2}\braket{00 | 00} =\frac{1}{2}\braket{0 | 0}\braket{0 | 0 }=\frac{1}{2}
\end{align}$$
- The post measured state, when renormalized is $\ket{00}$
- Alice measuring ends up changing bobs state to also $\ket{00}$ since it must be entangled 

# Quantum Nonlocality
https://en.wikipedia.org/wiki/Quantum_nonlocality
- Does not allow faster than light communication

## Local Variable Realism
- Imagine Charlie seals an envelope with $\ket{00}$ or $\ket{11}$ and decides 50/50 whether to send one or the other to Alice and Bob
- This has the same probability distribution as the quantum experiment, so quantum could be classical in theory

## Bell violation w/ chsh game
Experiment is trying to show that you can "play better" by exchanging quantum information instead of classical ($\lambda$), which would indicate something non-classical is happening

- A referee chooses an independent x and y randomly as either x=0 or 1 and y=0 or 1 
- Alice and bob can communicate any classical information $\lambda$ and must guess $a$ and $b$ as their best guess of x and y
- They win the game if $a \oplus b=xy$
- Classically, there is a 75% of winning but quantum has an 80-85%


x | y | xy | a and b
-|-|-|-
0 | 0 | 0 | a(0) xor b(0)
0 | 1 | 0 | a(0) xor b(1)


### Classical
- Probability of winning is sum of all possibilities 
$P(win)=\sum_{x,y,a,b} V(a,b,x,y)P(ab | xy)P(xy)$
$V(a,b,x,y)=$ 1 if a xor b = xy    or  0
$P(ab|xy)=(ab|x,y,\lambda)P(\lambda)$
- This shows quantum can't be modeled by classical methods using a hidden variable ($\lambda$)

### Quantum strategy
- Instead of sharing classical lambda, share a [[bell state]] $\ket{\Phi^+}=\ket{00}+\ket{11}$

**Alice:**
1. Preshare a bell state
2. If x=0, measure [[Bases#^eb270f|z-basis]] output -> a
3. If x=1, apply $R_{\frac{\pi}{8}}$ and then measure in[[Bases#^eb270f|z-basis]] (pi/8 is equivalent to a change in basis) output -> a

**Bob**
1. If y=0, measure in Z basis and output b
2. If y=1, change of basis with $R_{-\frac{\pi}{8}}$ and then measure in the z-basis and output b
3. 


$$\begin{align}
R_{\theta}\ket{0} =\cos \theta \ket{0} +\sin \theta \ket{1} \\
R_{\theta}\ket{1} =-\sin \theta \ket{0} +\cos \theta \ket{1}  
\end{align}$$

## Cases
**x=0, y=0**, win with probability 1
**x=1, y=0 or x=0,y=1** win with probability approx 85%
- Alice applies only $R_{\frac{\pi}{8}}$
$$\begin{align}
\left( R_{\frac{\pi}{8}}\otimes I \right)\left( \frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{11} \right)= \\
=\frac{1}{\sqrt{ 2 }}R_{\frac{\pi}{8}}\otimes I\ket{00} _{AB} + \frac{1}{\sqrt{ 2 }}R_{\frac{\pi}{8}}\otimes I \ket{11} _{AB} \\
=\frac{1}{\sqrt{ 2 }}\left( \cos \frac{\pi}{8} \ket{0} _{A} \right)\ket{0} _{B+\frac{1}{\sqrt{ 2 }}}\left( -\sin \frac{\pi}{8} + \cos \frac{\pi}{8}\ket{1}  \right) \\
=\frac{1}{\sqrt{ 2 }}\cos \frac{\pi}{8}\ket{00} +\frac{1}{\sqrt{ 2 }}\sin \frac{\pi}{8}\ket{10}-{\frac{1}{\sqrt{ 2 }}}\sin \frac{\pi}{8}\ket{01} +\frac{1}{\sqrt{ 2 }}
\end{align}$$
- If they see a 00 or a 11, then they win because product of xy must equal a xor b (add)
- Square the coefficients to get the probability of winning in this strategy $P(W)=\frac{1}{2}\cos \frac{^{2}\pi}{8}+\frac{1}{2}\cos ^{2} \frac{\pi}{8} \approx 85\%$

****
**x=1,y=1** win with probability 0.5
- Total probability of winning $P(win)=\frac{1}{4}(1+0.85+0.85+0.5)\approx 80\%$

### Comparison
shared classical < entanglement < PR-box (something that is always right) < 1 bit faster than light travel



Measuring along the basis $\ket{\psi^+}$ for state $\ket{++}$
$P(\psi^+)=\mid \braket{++ | \psi^+}\mid$

- Measuring one of the subspaces
$N_{x}:\mathbb{C}^2\to \mathbb{C}^2$
$\sum N_{x^*}N_{x}$

# Hadamard w/ entanglement
[[Bases#Hadamard Operator]]
## Superposition of all bit strings
$$\begin{align}
H \otimes H\otimes\dots \otimes H \ket{0\dots 0} = H^{\otimes n} \ket{0\dots 0} = \ket{+ \dots +}= \frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1}) \otimes \dots \otimes \frac{1}{\sqrt{ 2 }} (\ket{0}+\ket{1})\\
=\frac{1}{\sqrt{ 2 }^n} (\ket{0,0,\dots,0} + \ket{0\dots 0 1} + \dots + \ket{1 \dots 1})   \\
=\frac{1}{\sqrt{ 2 }^n}\sum_{x \in\{ 0,1 \}^{n}}\ket{x} 
\end{align}$$
- represents all possible bit strings


## Find $H^{\otimes n}$
### 1. Re-write $H$
- Assume that $\ket{x_{n}}$ represents an input vector and $\ket{y_{n}}$ is the corresp. output vector
Hadmard is defined as $H=\ket{+}\bra{0}+\ket{-}\bra{1}$
$$
\begin{align}
H=\frac{1}{\sqrt{ 2 }}(\ket{0} +\ket{1} )\bra{0} +\frac{1}{\sqrt{ 2 }}(\ket{0} -\ket{1} )\bra{1} \\
=\frac{1}{\sqrt{ 2 }}\left(\ket{0} \bra{0} +\ket{1} \bra{0} +\ket{0} \bra{1} -\ket{1}\bra{1}  \right) 
\end{align}
$$
- **Notice** only when $\ket{x_{n}}=\ket{y_{n}}=\ket{1}$ that there is negative phase on term
- Therefore, $H=\frac{1}{\sqrt{ 2 }}\sum_{x,y \in\{ 0,1 \}} (-1)^{xy}\ket{y}\bra{x}$  
	- **^-when x=1 and y=1, term is $-\ket{1}\bra{1}$**
	- $x,y \in\{ 0,1 \}$ represents all combinations of 0 and 1, so $\{ 00,01,10,11 \}$

### 2. Apply repeatedly with tensor product
$$
\begin{align}
H^{\otimes n}= \frac{1}{\sqrt{ 2^{n} }} H \otimes \dots \otimes  H \text{    factor out 1/sqrt(2) from each H} \\
=\frac{1}{\sqrt{ 2^{n} }}\left( \sum_{x_{1},y_{1} \in\{ 0,1 \}} (-1)^{x_{1}y_{1}}\ket{y_{1}}\bra{x_{1}} \right) \otimes \dots \otimes \left(\sum_{x_{n},y_{n} \in\{ 0,1 \}} (-1)^{x_{n}y_{n}}\ket{y_{n}}\bra{x_{n}} \right)
\end{align}
$$
- Applying [[Tensor Product#Properties|tensor distributive prop]] on a sum of elements really gives us all combinations of elements. 
	- $(a_{1}+a_{2})\otimes(b_{1}+b_{2})=\ket{a_{1}b_{1}}+\ket{a_{1}b_{2}}+\ket{a_{2}b_{1}}+\ket{a_{2}b_{2}}$
	- Sums are sort of building bit strings (# iterations quadruples w/ every sum since sum is already double sum x,y)

$$
\begin{align}
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x_{1},y_{1} \in\{ 0,1 \}} \sum_{x_{2},y_{2} \in\{ 0,1 \}} \dots \sum_{x_{n},y_{n} \in\{ 0,1 \}} (-1)^{x_{1}y_{1}+x_{2}y_{2}+\dots+x_{n}y_{n}} \ket{y_{1}\dots y_{n}} \bra{x_{1} \dots x_{n}} \\
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x \in \{ 0,1 \}^{n}} \sum_{y \in \{ 0,1 \}^{n}} (-1)^{x \cdot y} \ket{y} \bra{x}  \\
=\frac{1}{\sqrt{ 2^{n} }} \sum_{x,y \in \{ 0,1 \}^{n}} (-1)^{x \cdot y} \ket{y} \bra{x} 
\end{align}
$$
### Intuition
- $H\ket{0}=\ket{+}=\frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1})$ which creates a balanced superposition between 0 and 1 
- $H^{\otimes n}$ is an operator that creates a superposition of all possible bitstring inputs that maps to all possible bitstring outputs 
	- Dimension is HUGE b/c maps all combinations of inputs to every possible combination of output ($n \times n$)
- The **phase of each term** is determined by
	- When the dot product between input $\ket{x_{1} \dots x_{n}}$ and output bit string $\ket{y_{1} \dots y_{n}}$ is an odd number
	- ex: $H\ket{11}=\ket{--}=\ket{00}-\ket{01}-\ket{10}+\ket{11}$
	- $\braket{11 | 01}= (1 \cdot 0) + (1 \cdot 1)=1$ but $\braket{11 | 11}= 1 + 1 =2$ so it has no phase

- Consequently, $H^{\otimes n}\ket{x_{1} \dots x_{n}}=\frac{1}{\sqrt{ 2 }^n}\sum_{y_{1} ..y_{n}\in\{ 0,1 \}^n}(-1)^{x \cdot y}\ket{y_{1} \dots y_{n}}$