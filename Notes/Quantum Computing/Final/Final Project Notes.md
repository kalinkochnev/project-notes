# Other interesting findings
- IBM Quantum Composer
- https://jonathan-hui.medium.com/qc-control-quantum-computing-with-unitary-operators-interference-entanglement-7790c69f6e98

Main points: interesting quantum mechanics/relativity necessary to understand, get across how to wormhole discovery works, describe the criticisms of the paper

- Quantum computation doesn't depend on time, yet schrodinger's equation dictates how the system evolves. There are "stationary" states that make quantum computation possible.

https://quantum-computing.ibm.com/composer/files/new?initial=N4IgdghgtgpiBcIDqBaAzgFwhuAaEAjhGlAiAPIAKAogHICKAggMoCyABAEwB0ADANwAdMAEswAYwA2AVwAmMdoMIxJIgEYBGbmPFKhYYQQBOMAObsCAbQDMAXX3iT58TfvDhJtDAwXLvN2Ce3r4aAUE%2BVpxhAJ4AFFoAnBq8AGzW1pzWKZwALAm8GgAcOQCUvv4O0rEADiLsAPRcuOy1DU0tdY2cza1dZVb%2BzVahDgAeIbZDllFj5ZMT%2BuMDAbDE0iZz7CgAfOwuFcKraOsKw7Zbuy4jhzBrG5HnO3vTAcL1jQAC4gD2MlBgaHYflwvBBuA0uG61lwOVwAFZcClcAB2XCFWwgfDyNCOETVDAib5gMggAC%2BQA

# Schrodinger’s Equation
[https://en.wikipedia.org/wiki/Schr%C3%B6dinger_equation](https://en.wikipedia.org/wiki/Schr%C3%B6dinger_equation)
-   Gives a mathematical prediction of the path a physical system will take over time
$$i\hbar \frac{\partial}{\partial t}\ket{\psi(t)}=\hat{H}\ket{\psi(t)}$$
- $\ket{\psi(t)}$ is the state vector of system
- $\hbar$ is the reduced Planck constant (relationship between energy of photon and its frequency)
- $\hat{H}$ is the [[Final Project Notes#Hamiltonian]] of the system
- Physical quantities (position, momentum, energy, spin) are "observables" - linear operators acting Hilbert space

- It is a linear differential equation, so if $\ket{\psi_{1}}$ and $\ket{\psi_{2}}$ are solutions, then so is a linear combination





# Stationary states
- Stationary states are eigenvector of the energy operator (not a superposition of different energies)
- **Stationary state** - a quantum state with observables that are independent of time. Constant probability distribution of position, velocity, etc
- Wave function is itself not stationary for a stationary state, but probability is ($\braket{\psi | M_{x}^{*} M_{x} |\psi}$)
![[StationaryStatesAnimation.gif]]
https://en.wikipedia.org/wiki/File:StationaryStatesAnimation.gif

- If the hamiltonian is constant and doesn't depend on time, Schrodingers equation has a solution of
$$
\begin{align}
i\hbar \frac{\partial}{\partial t}\ket{\Psi} = \hat{H}\ket{\Psi}  \\
\frac{\partial}{\partial t}\ket{\Psi} = \frac{1}{i\hbar} E_{\Psi}\ket{\Psi} \\ \\
\frac{\partial}{\partial t}\ket{\Psi} = -\frac{i}{\hbar} E_{\Psi}\ket{\Psi} \\
\ket{\Psi(t)} =e^{-iE_{\psi}t/\hbar}\ket{\Psi(0)} 
\end{align}
$$
- Assume that we are representing the wave function of a particle whose observable is its position $x$. This would be denoted $\ket{\Psi(x,t)}$
- If the hamiltonian is constant, and therefore its observable eigenstates are constant, The state of the particle still changes with time, but the probability of the particle being at position $x$ is 
$$
\begin{align}
P(x)=\braket{\Psi(x,t) | \Psi(x,t)}=\ket{\Psi(x,t)}\ket{\Psi(x,t)}^{*} \\
\text{where } \ket{\Psi(x,t)}^{*} = e^{iE_{\psi}t/\hbar} \bra{\Psi(x,0)}  \\
= (e^{-iE_{\psi}t/\hbar})(e^{iE_{\psi}t/\hbar})\braket{\Psi(x,0) | \Psi(x,0)} \\ \\
P(x)=\braket{\Psi(x,0) | \Psi(x,0)}
\end{align}
$$
# Wave function
-  A wave function describes a quantum state of an isolated quantum system
- Complex valued probability amplitude (denoted $\Psi$)

# Hamiltonian
- An operator corresponding to the total energy of the system (KE + PE) of all particles associated with the system
- The spectral decomposition of the hamiltonian is the set of possible outcomes of a system's total energy. The eigenvalues are the specific energy levels permissible
- $\hat{H}=\hat{T}+\hat{V}$ 
	- $\hat{T}=\frac{\hat{p}\cdot  \hat{p}}{2m}=-\frac{\hbar^{2}}{2m}\nabla^{2}$ is the kinetic energy operator (m is mass)
		- $\hat{p}=-i\hbar \nabla$ (i is imaginary number, h is reduced planks constant)
		- $\nabla \cdot \nabla =\frac{\partial^{2}}{\partial x^{2}}+\frac{\partial^{2}}{\partial y^{2}}+\frac{\partial^{2}}{\partial z^{2}}$
	- $\hat{V}=V(r,t)$ potential energy operator (depends on spatial configuration of particles and time)

$$
\hat{H}=\sum_{\psi \in \text{energy levels}} E_{\psi} \ket{\psi} \bra{\psi}  
$$
Where $E_{\psi}$ is the energy level of a particular outcome state $\ket{\psi}$.
$$
\hat{H}\ket{\Psi} =E\ket{\Psi} 
$$
Assume that you apply the hamiltonian operator to one of its eigenvectors $\ket{\Psi}$. By definition, this is the same as scaling the eigenvector state by a constant eigenvalue. This eigenvalue represents the total energy of the system for that particular state of the particle. 

This indicates that if the particle is at a superposition of eigenstates, $\ket{\Psi}=\ket{\psi_{1}}+\ket{\psi_{2}}$, applying the Hamiltonian will give the total energy of the superposition. 

$$
\hat{H}\ket{\Psi}=\hat{H}\ket{\psi_{1}}+\hat{H}\ket{\psi_{2}}=\text{ total energy}
$$
## Time independent solution
Assume that $\hat{H}$ is a linear operator and $\ket{\Psi}$ is the eigen vector of $\hat{H}$ and $E_{\Psi}$ is the eigen value (energy level)

# Quantum teleportation
- Quantum teleportation is the communication of a quantum message that uses classical information to do so

# Wormholes Theory Paper
- Quantum systems with enough entanglement can give rise to quantum gravitational characteristics. Is a result of emergent behavior

- The transfering of quantum information can be purely describes with Schrodinger's equation. However the system is much more easily describable with the dual to the quantum system, a wormhole connecting two black holes. 

- Wormhole formulations using relativity lead to paradoxes, but it was discovered that a wormhole could be held open with a shockwave of negative energy
It is easier to calculate different properties on one side of the duality than the other ocassionally

https://en.wikipedia.org/wiki/Holographic_principle
https://www.sciencedaily.com/terms/holographic_principle.htm

- You can observe a particle traversing through a worm hole when viewed through the gravitational viewpoint.  
- Quantum viewpoint is that the information of a single particle is scrambled into a system of entangled particles and afterwards appears unscrambled as another particle in the system
- They did not actually create a wormhole but mimic the behavior of a wormhole in every way

- To simulate a indisputable wormhole system, need at least 100 qubits per cloud
- As the number of particles increase, the size of the hamiltonian increases exponentially (3,921,225 terms for a 100 particles)

- Using a neural network, only the most impactful terms of the hamiltonian were kept while the remaining were pruned.  https://arxiv.org/abs/2008.02303

# TFD State
http://www.hartmanhep.net/topics2015/17-eternalblackholes.pdf
- Exhibits strong left-right corelations that permit negative energy injection
- For finite temp. there are only approximate methods for generating the TFD state

- The TFD formalism treats the mixed state $\rho=e^{i\beta H}$ as a pure state in a larger system
- Double number of DOFs. Exists in two different spacetimes
- Then the TFD is a particular pure state in the doubled system
- If you only look at one of the systems, 

# QC Hardware Paper
- Used 9 qubits with 164 two qubit gates

# Controversy
- Gravitational scrambling is not the only method. Some quantum systems that had no holographic dual (wormhole behavior) could transport quantum information, but not as efficiently as the gravitational case. 
- Black holes are the most efficient scramblers in nature

- The sparsified hamiltonian have "fully commuting" terms which allow for much simpler simulation but do not have interdependence with one another
- Other researchers argued that perfect size winding is just a result of the smallness of the system

**Claim:** "non-gravitational systems with sufficient entanglement may exhibit phenomena characteristics of quantum gravity"


# Circuit
- Non-gravitational dual the boundary
- Gravitational dual the bulk
- Some phenomena are easier to explain in bulk (gravitational) and others that are easier on the boundary (non-gravitational)
- A negative energy shockwave imparts a time advance


- Evolve backwards with reverse time evolution. This make it so you inject a message into the past on the left side
- The coupling of the left and right side of the circuit is the analog to the the negative energy shockwave.
- The forward evolution corresponds to the message traveling out of the right boundary

- $H$ is the hamiltonian (assumed to be scrambling) 
	- $H\ket{E_{j}}=E_{j}\ket{E_{j}}$
	- Scrambling hamiltonian makes it so information of state is spread to rest of quantum system and can't distinguish the initial state from other states
	- Example: Sachdev-Ye-Kitaev (SYK) model

2. Insert a message of choice

1. Message "dissapears" into the system
2. After a period of time, the message unscrambles itself at apoint from where it started



Takeaways:
- Wormholes could "point the way to general class of quantum communication procedures"


# Sachdev-Ye-Kitaev model (SYK)
https://phys.org/news/2021-02-numerical-evidence-quantum-chaos-sachdev-ye-kitaev.html
https://en.wikipedia.org/wiki/Sachdev%E2%80%93Ye%E2%80%93Kitaev_model
![[Pasted image 20230424183822.png]]
*A schematic phase diagram showing the behavior of the Sachdev-Ye-Kitaev model for different regimes of temperature and system size. From high to low temperature, the model transitions from behaving like interacting particles, to a semiclassical black hole, to a highly quantum black hole. Credit: Kobrin et al.*

- It is an exactly solveable mode which was predicted to show many-body chaos in a quantum system
- Information spreads exponentially fast, similar to butterfly effect in classical chaos
- There is a theoretical limit to how fast information make be scrambled/spread
- If two copies of the SYK model are coupled, in theory, it would allow for the transfer of quantum information throw a traversable wormhole
- The only difference between Thermodynamic entropy and Shannon entropy is the unit of measure (energy divided by temperature versus bits)

- Randomized Hamiltonian systems like the SYK model have gravitational duals
- SYK model doesn't need to be fined tuned to have appreciable results like other uses of quantum computers


- Beta "inverse temperature" - represents response of entropy to increase in energy



# CFT=AdS correspondence
https://en.wikipedia.org/wiki/AdS/CFT_correspondence
- The CFT=AdS is a conjecture correspondence between quantum gravity using anti-de Sitter space (negative cosmological constant) and String theory, and conformal field theories which describe elementary particles in the universe

- Gravity results from curvature of space-time geometry as a result of mass/energy
- At quantum level particles exchange force through particles
- Describes how a theory of space-time gravity emerges from quantum theory 

- A field theory describes how a field changes in space and time
## AdS
https://en.wikipedia.org/wiki/Anti-de_Sitter_space
- Theories of relativity put space and time equally, so you look at space-time as one geometry instead of separaetely.
- The solution to Einstein's field eequations result in different space time shapes/surfaces depending on the value of different cosmological constants
- A positive cosmological constant (constant positive curvature) results in elliptic or spherical space 
- 0 curvature is a flat plane
- And a negative curvature is a hyperbolic plane
- Spacetime with constant curvature has three different

- 

# Penrose diagrams

# Black Holes
https://www.nytimes.com/2022/10/10/science/black-holes-cosmology-hologram.html

# Wormholes
https://en.wikipedia.org/wiki/Wormhole#Traversable_wormholes
https://i4is.org/einstein-rosen-bridge/
- A traversable wormholes can transport you from two distant places in the universe, or even between universes
- The issue is that wormholes are very unstable and can collapse in on themselves, thereby removing it from existence. A Schwarzschild wormhole is one such example. 
- An Einstein-Rosen bridge
- Need "exotic matter" which is a substance with negative energy in order to keep the wormhole open. 

# Holography
https://en.wikipedia.org/wiki/Holographic_principle

**Holographic principle** - the entropy of ordinary mass is proportional to surface area (not volume!)
- "volume is illusory" and the universe is a hologram