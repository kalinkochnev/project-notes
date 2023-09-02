# Basic Gates
**Circuit:** acts on n-qubits and consists of multiple "gates" (simple unitary operators)

https://en.wikipedia.org/wiki/Quantum_logic_gate
**NOT gate**: the X pauli matrices
**Phase flip**: the Z pauli matrixes


## Pauli X-gate
- Maps $\ket{0} \to \ket{1}$ and $\ket{1}\to \ket{0}$

- Each wire = 1 qubit, unless notated otherwise
- Each qubit wire is really tensored together
![[Quantum Gates.png]]

## Oracle gate
$\{ 0,1 \}^{n}$ represents an n-bit string. $f(x)$ represents a classical function converted to quantum gates
Let $U_{f}$ be the oracle function $\{ 0,1 \}^{n}\to \{ 0,1 \}^{m}$
$$
\begin{align}
U_{f}\ket{x} \otimes \ket{y}=\ket{x} \ket{y \oplus f(x)}   
\end{align}
$$

### Ensure invertible
- $U_{f}\ket{x}=\ket{f(x)}$ is not answer. Not invertible b/c $n \neq m$ (diff dimension size)
	- **Solution:** Def an $n$ qubit input register $\ket{x}^{\otimes n}$ and init output register w/ $m$ qubits $\ket{y}^{\otimes m}$ so $n+m \to n+m$
- Input register is "pass through"  
- Output register is dummy input (initialized $\ket{y}^{\ket{m}}=\ket{0}^{\ket{m}}$)

### Ensure inner product preserved
#### Option 1 (definition of XOR)
- $b \oplus b = 0$ b/c if same, output is always 0
- $a \oplus 0=a$ (**see highlighted table**)
- Therefore, $a \oplus b \oplus b=a$

| a   | b   | $a \oplus b$ |
| --- | --- | ------------ |
| ==0==   |==0==   | ==0==           |
| 0   | 1   | 1            |
|==1==   | ==0==   | ==1==            |
| 1   | 1   | 0            |

- $U_{f}$ is its own inverse. $U_{f}U_{f}=I$
$$
\begin{align}
U_{f}\ket{x} \ket{y \oplus f(x)} = \ket{x}\ket{(y \oplus f(x))\oplus f(x)}=\ket{x} \ket{y}       \\
\end{align}
$$


#### Option 2 (intuitively)
Let two different states be $\ket{x,y} \to \ket{ x, y \oplus f(x)}$ and $\ket{x', y'} \to \ket{x', f(x') \oplus y'}$
- Inner product must be preserved, so $\braket{x,y | x',y'}$ must equal $\braket{x,y \oplus f(x) \mid x', y'\oplus f(x')}$
- If $x$ and $x'$ are different (0 and 1), then the inner products are both $\braket{0 | 0}\otimes \braket{y | y'}=0$ and same with $\braket{x | x'} \braket{y \oplus f(x) | y' \oplus f(x')} = 0$
- If y and y' are the same, then $\braket{x,y | x',y'}=1$ and $\braket{x | x'} \otimes \braket{1 \oplus f(x) | 1 \oplus f(x')}=1$ b/c x and x' must be 1 or else it would cancel
- etc
![[Oracle Gate.png]]

# Controlled Operations
- Any controlled operation $c(U)$ can be constructed from single qubit ops and a CNOT
- "If one thing is true, do U. Otherwise, do nothing"

## Control-Not $(CNOT)$
- If the **control** is in a state of $\ket{1}$, then apply the NOT gate to the **target**
$CNOT\ket{a,b}=\ket{a, a \oplus b}$
$$
\begin{align}
CNOT\ket{0,0}=\ket{0,0} \\
CNOT\ket{0,1} =  \ket{0,1} \\
CNOT\ket{1,0} = \ket{1, 1} \\
CNOT\ket{1,1} =\ket{1, 0}   
\end{align}
$$
## Controlled Gate
- A unitary operator that applies a gate depending on a control bit (when = 1)
$$c(U)=\ket{0}\bra{0}_{A}\otimes I_{B}+\ket{1}\bra{1}_{A} \otimes U$$
- Can replace $I_{B}$ with another gate if you want to apply a diff operator when = 0

### Check
- Check $c(U)\ket{0}\otimes \ket{\psi}=\ket{0}$ should not use U b/c control is inactive

$$
\begin{align}
c(U)\ket{0} \otimes \ket{\psi} =\ket{0} \bra{0} \otimes I\ket{0,\psi}+\ket{1} \bra{1} \otimes  U \ket{0,\psi} \\
=\ket{0} \ket{\psi} +0
\end{align}
$$
- CHeck $c(U)\ket{1}\otimes \ket{\psi}= U\ket{\psi}$
$$
\begin{align}
c(U)\ket{1} \otimes \ket{\psi} = \ket{0} \bra{0} \otimes I\ket{1,\psi}+\ket{1} \bra{1} \otimes  U \ket{1,\psi}  \\
= 0 +\ket{1} U\ket{\psi} 
\end{align}
$$
#### Exercise: show is unitary operation

### How to make any U a controlled operation w/ basic gates
- Only need CNOT gates
- Any gate U can be written in the form $U=e^{i\alpha} A X B X C$ 
	- where $X=NOT$ and $ABC=I$ 
	- A,B,C are unitary operators. They are all rotation operators
![[Pasted image 20230320153123.png]]
#### If control=0
t2 = t1: $\ket{0}\otimes C\ket{\psi}$
- Nothing changes at t2 b/c the controlled 
t4 = t3: $\ket{0} \otimes BC \ket{\psi}$
t5 : $\ket{0}\otimes ABC\ket{\psi} \equiv \ket{0}\otimes I\ket{\psi}=\ket{0,\psi}$
- Doesn't apply 

#### If control=1
- Should map $\ket{1,\psi}$ to $\ket{1}\otimes U\ket{\psi}$
t1: $\ket{1}\otimes XC\ket{\psi}$
t3: $\ket{1} \otimes BXC \ket{\psi}$
t4: $\ket{1}\otimes XBXC \ket{\psi}$
t5: $\ket{1}\otimes AXBXC\ket{\psi}$

## Alpha gate
- A unitary gate which applies a phase
- $\ket{0} \to e^{i\alpha}\ket{0}$ and $\ket{1} \to e^{i\alpha} \ket{1}$

### A controlled alpha gate
- A controlled alpha gate that applies a phase if control=1
- $\ket{0,\psi}\to \ket{0, \psi}$ and $\ket{1,\psi}\to \ket{1}\otimes e^{i\alpha}\ket{\psi}$

- It is equivalent to a single gate on one qubit
	- Applying a phase on a single qubit applies it globally
	- Only the top wire is the control, which is why we don't put it on the bottom wire
$$
V=\begin{pmatrix}
1 & 0 \\
0 & e^{i\alpha}
\end{pmatrix}
$$![[Pasted image 20230320153144.png]]


## Toeffoli gate
- A 3 qubit operation, $\ket{x,y,z} \to \ket{x,y,z\oplus xy}$
- Means if $y$ AND $z$ are both 1, then flip z
- Like a double input controlled NOT, $C^{2}(X)$
- Can be built from CNOT (2-qubit op) and unitaries (1-qubit op). Can't do it classically with the same number of inputs

### Ex: If all 5 wires =1, then do U
- Need to add 4 dummy wires (Need N-1 auxiliary wires in general)
- Need to "deallocate" the dummy wires at the end because if you don't, the entanglement may affect future results
$C^{5}(U)$

![[Pasted image 20230320155126.png]]