# Introduction to discovery
- For almost a century physicists have tried to link together the physics of relativity involving large scale objects with the quantum mechanical understanding of matter on the smallest scale. 
- String theory is a theory of quantum gravity and holds much promise, but there is little way to verify its findings experimentally. 
- One obstacle in the ability to do so is the extremely limited ability to measure the forces of gravity of particles. 
- Despite the challenge, a group of scientists in 2022 published a paper in Nature detailing an experiment conducted on a Google's Sycamore quantum computer which claimed to have created an object with wormhole-like properties. 
- This was an unexpected publication because scientists thought that it would be impossible to simulate a wormhole for at least another decade of progress in quantum computing hardware research. 
- To indisputably prove that a wormhole was created on a quantum computer, computers would need to have at least 100 qubits for each side of the traversable wormhole. 
- The size of the quantum computer is not the only issue. The number of terms of the hamiltonian corresponds to the number of quantum gates necessary to simulate a behavior. In order to describe the physics of the 100 qubit entangled systems of particles using the Hamiltonian, 3,921,225 terms in the hamiltonian are necessary. This is far outside of reach of today's quantum computers. 
- This paper does not simulate a full-blown wormhole but a sparsified model capable of being run on today's quantum computers. Using machine learning, the researchers identified the terms of the Hamiltonian that contributed most to wormhole dynamics. The researchers claimed that even with only 9 qubits and 164 two qubit gates they were able to observe key characteristics of a wormhole. One of which is known as size-winding. 
- This claim has been met with much pushback regarding the characteristics of the learned Hamiltonians. Another group of scientists have stated that the scrambling and unscrambling behavior was not because of wormhole dynamics, but because of the Hamiltonians commuting with one another. The fact that the Hamiltonians commute is is an artifact of sparsification. The commutivity is what allows the sparsified model to be easily simulated, while an uncommutative model has much more chaotic interdependence among terms which better capture the dynamics of a wormhole.  

- Despite the inconsistencies that need to be resolved, this still marks a significant moment in quantum gravity research. This is one of the first attempts at demonstrating experimental evidence.
- Even though they may not have undeniably demonstrated wormhole characteristics, their methods have opened the door to future experimental probing of quantum gravity. 

# Wormholes
- A traversable wormhole can be understood as connecting two points in space, effectively creating a shorter path than if you were to travel the full length normally.  
![[Pasted image 20230429135252.png]]
- However, traversable wormholes are very unstable and can collapse in on themselves, effectively removing it from existance. One such example of an unstable wormhole is a Schwarzschild wormhole. 
- It has been shown that if matter with negative energy, known as "exotic matter", were to exist, it can prop open a wormhole. However, such matter has not yet been discovered.

- On the quantum mechanical level, there are momentary violations of the Null Energy condition, which says that the energy density along any macroscopic region must be greater than or equal to 0. Therefore, we can have momentary wormholes on the quantum mechanical level.

# Quantum Gravity
-  The study of holography in the context of string theory allows physicists to view space-time as a duality to quantum systems. 
- A specific duality, known as the AdS/CFT correspondence conjecture, is a bridge for physicists to understand anti-de Sitter (AdS) spaces and conformal field theories (CFT).
- The current argument of AdS/CFT is that large quantum systems with enough entanglement can result in emergent behavior such as gravity. 

- Anti-de Sitter space is one of three solutions to Einstein's field equations which dictate the shape of space-time depending on the distribution of mass. This particular space is used to formulate a quantum theory of gravity. 
- Meanwhile conformal field theories, and specifically the quantum field theories, are used to describe the behavior of elementary particles, which are a group of experimentally verified theories. 
- The particular solution to Einstein's equations depends on the cosmological constant of the universe. When the constant is positive, a positive constant curvature of space exists in the universe (like a sphere), known as de-Sitter Space. This is the universe that we live in. Then there is Minkowsi space which is a plane with no curvature as a result of zero cosmological constant. And finally, there anti-de Sitter space which has constant negative curvature, such as a hyperbolic plane. 
- This is the first visible limitation of the current string theory formulation of quantum gravity. So far the current formulation of the AdS/CFT correspondence only works for AdS space and not the type of space that reality actually is (de Sitter). So the wormhole created in this paper is not a real wormhole in this sense, but it does allow the transportation of quantum information. 

# SYK model
- Not every quantum system has a quantum dual, and only a few have been proven to have one. One such system is known as the Sachdev-Ye-Kitaev (SYK) model. 
- The SYK model has been shown to be an exactly solveable problem that demonstrates quantum many-body chaos.

https://phys.org/news/2021-02-numerical-evidence-quantum-chaos-sachdev-ye-kitaev.html
- Many body chaos is a sign of quantum gravity because it is closely related to how fast gravity can scramble information.
- There is a fundamental limit to how fast information can spread and scramble throughout a system which black holes, a system with extreme relativistic effects, can reach.
- The SYK model has been shown to also  reach the universal speed limit, which makes it an attractive candidate for quantum gravity research.
- An interesting side note is that the only difference between thermodynamic entropy and Shannon entropy is the unit of measure. Thermodynamic entropy is measured in terms of energy divided by temperature while Shannon entropy is measured in bits. This is why we can talk about "information" in the context of quantum systems and black holes, since they are analogous in this regard.

- It was theorized that by linking together two SYK models, you can create a traversable wormhole, albeit only able to transport information.
- Compared to most other nascent applications of a quantum computer, the SYK model does not have to be fine-tuned in order to have appreciable results on a noisy quantum computer. **(wormholes pdf)**

# Quantum Circuit
## Background
-   In quantum computing we concern ourselves with operators that do not depend on time. If we had a computer that made calculations that are dependent at the point in time you made them, this would result in non-deterministic computation. This is generally an undesirable quality. 
$$
i\hbar \frac{\partial}{\partial t}\ket{\psi(t)}=\hat{H}\ket{\psi(t)}
$$
- However, quantum mechanical processes do depend on time. This is the relation that Schrodinger’s equation conveys. It is a partial differential equation that predicts how a quantum system ($\ket{\psi}$) will evolve over time.

-   To make sense of this operation, we must examine what means. is known as the Hamiltonian. It is a linear operator that describes the total kinetic $\hat{T}$ and potential energy $\hat{V}$ of a quantum system.
$$
\hat{H}=\hat{T}+\hat{V}
$$
-   A more intuitive understanding of the Hamiltonian arises when looking at it from its spectral decomposition. 
$$
\hat{H}=\sum_{\psi \in \text{energy levels}} E_{\psi} \ket{\psi} \bra{\psi}  
$$
Where $E_{\psi}$ is the energy level of a particular outcome state $\ket{\psi}$.

- The eigenvectors of the hamiltonian represent linearly independent states of a quantum system that we can actually see observe upon measuring, such as $\ket{0}$ and $\ket{1}$. Meanwhile the eigenvalue represents the total energy of the quantum system for each independent state of the quantum system.

- Assume that you apply the hamiltonian operator to one of its eigenvectors $\ket{\Psi}$. By definition, this is the same as scaling an observable state by a constant eigenvalue. This eigenvalue represents the total energy of the system for that particular state of the particle. 
$$
\hat{H}\ket{\Psi} =E_{\Psi}\ket{\Psi} \text{ where } E_{\psi} \text{ is the energy for observable } \ket{\Psi} 
$$

This indicates that if the particle is at a superposition of eigenstates, $\ket{\Psi}=\ket{\psi_{1}}+\ket{\psi_{2}}$, applying the Hamiltonian will give the total energy of the superposition.
$$
\hat{H}\ket{\Psi}=\hat{H}\ket{\psi_{1}}+\hat{H}\ket{\psi_{2}}=\text{ total energy}
$$
  
-   So looking at Schrodinger’s equation again, it says the change in a quantum state at any given time is proportional to the total energy of the state at that time.
$$
i\hbar \frac{\partial}{\partial t}\ket{\psi(t)}=\hat{H}\ket{\psi(t)}
$$
-   There are in fact solutions to Schrodinger’s equation that do not depend on time. The quantum states that satisfy this criteria are actually the eigenvectors of the Hamiltonian. These are known as **stationary states**.

-   The state of the particle itself is not stationary. It is constantly fluctuating as time passes, but the probability distribution of the particle’s properties like spin, position, velocity, remains constant across time. 
![[StationaryStatesAnimation.gif]]
-   The solutions to Schrodinger’s equations are waves that change with time, also known as the wave function. 
- The wave function that dictates the evolution of a stationary state is a standing wave. When you look at the probability distribution of one of these stationary states, you see that in fact it does not depend on time. 
- If a state is not stationary, meaning that the state of a particle does depend on time (as seen in the 3rd row), the probability distribution also fluctuates with time.

- Stationary states arise when the Hamiltonian is constant and doesn't depend on time. As mentioned before, the state itself is in constant flux as time changes. Therefore the state of a particle does depend on time. However, the **probability** of an outcomes is what doesn't depend on time. 
- If we solve Schrodinger's equation using the time-independent solution, we see that the state does change with time, however, only  along the phase.
$$
\begin{align}
i\hbar \frac{\partial}{\partial t}\ket{\Psi} = \hat{H}\ket{\Psi}  \\
\frac{\partial}{\partial t}\ket{\Psi} = \frac{1}{i\hbar} E_{\Psi}\ket{\Psi} \\
\frac{\partial}{\partial t}\ket{\Psi} = -\frac{i}{\hbar} E_{\Psi}\ket{\Psi} \\
\ket{\Psi(t)} =e^{-iE_{\psi}t/\hbar}\ket{\Psi(0)} 
\end{align}
$$

- We can see that the probability has no relationship with time despite the state itself changing with time.
- For example, lets say we are representing the wave function of a particle whose observable is its position $x$. This would be denoted $\ket{\Psi(x,t)}$
- If the hamiltonian is constant, and therefore its observable eigenstates are constant, The state of the particle still changes with time, but the probability of the particle being at position $x$ is 
$$
\begin{align}
P(x)=\braket{\Psi(x,t) | \Psi(x,t)}=\ket{\Psi(x,t)}\ket{\Psi(x,t)}^{*} \\
\text{where } \ket{\Psi(x,t)}^{*} = e^{iE_{\psi}t/\hbar} \bra{\Psi(x,0)}  \\
= (e^{-iE_{\psi}t/\hbar})(e^{iE_{\psi}t/\hbar})\braket{\Psi(x,0) | \Psi(x,0)} \\ \\
P(x)=\braket{\Psi(x,0) | \Psi(x,0)}
\end{align}
$$
- Using Schrodinger's equation for evolving a time independent quantum state, we can define the time evolution operator $\hat{U}(t)=\exp({-\hat{i}Ht/\hbar})$. Or the reverse time evolution operator $\exp(i \hat{H}t)$.

## Circuit
![[Pasted image 20230430121420.png]]
The process for creating a circuit that has wormhole behavior is as follows. 

**1. Prepare the TFD state**
Firstly, prepare $n$ qubits onto a left and a right system for a total of $2n$ qubits. The left ($\ket{E_{j}}_{L}$) and right ($\ket{E_{j}}_{R}$) systems are initially entangled to the thermofield double (TFD) state.
$$\ket{TFD}=\frac{1}{\sqrt{ Tr(e^{-\beta H}) }} \sum_{j \in \text{energy levels}}e^{-\beta E_{j}/2}\ket{E_{j}}_{L}\otimes  \bar{\ket{E_{j}}_{R}}$$
The TFD state is related to a collection of Bellpairs assuming an infinite temperature (the $\beta$, loosely interpreted as entropy), so there only exist approximate methods to generate a TFD state with finite temperature. 

The TFD is used because it allows treating a mixed state $\rho=e^{-\beta H}$ as a pure state $\ket{TFD}\bra{TFD}$ in a larger dimensional system. If we trace out the right system, so we only pay attention to the left system $\rho_{L}=tr_{R}(\ket{TFD}\bra{TFD})$ we get our original mixed state $\rho=e^{-\beta H}$. This means that there is fundamentally no difference between the higher dimensional pure state and the lower dimensional mixed state. (http://www.hartmanhep.net/topics2015/17-eternalblackholes.pdf)

When considering the gravitational dual, the TFD state is used because of its ability to be injected with negative energy. 

**2. Move backwards in time and insert the message**
We first devolve the left qubit system backwards in time using the reverse time evolution operator $\exp(i \hat{H}_{L}t_{L})$. 

We have a $m$ qubit message $\psi_{in}$ (where $m \ll n$) which we inject it into the left system. This means we can throw away/ignore the original $m$ qubits and replace them with our message qubits using the SWAP gate.

The combination of the reverse time evolution and the message insertion is the same as inserting a qubit into the past. 

**3. Evolve the right system forward in time**
Next in the circuit, we evolve the right system forward in time using $e^{-i\hat{H}_{L}t_{L}}$. This has the effect of scrambling the the information of the $m$ qubits onto the $n$ total qubits of the left system. And it brings the left system "back to the present". This is indicated in the Penrose diagram with a star to represent message insertion.

If we did nothing to the rest of the system from here on, time will eventually pass, causing the message to be destroyed by hitting the singularity of the wormhole. 

**4. Couple the left and the right systems after insertion**
Now we focus on the qubits ($n-m$) that were not replaced with the message in both the left and the right system, known as the carrier qubits. For those qubits only, apply $\exp(igV)$ where
$$
V=\frac{1}{n-m}\sum_{i\in \text{ carrier qubits}} (\sigma_{z})_{i}^{L} (\sigma_{z})_{i}^{R}
$$
**5. Evolve the right system forward in time**
Apply the forward time evolution to the right system. This is what allows the message to cross the boundary of the right side of the wormhole and emerge unscrambled. 


## Penrose Diagram Interpretation

![[Pasted image 20230430123510.png]]
(https://en.wikipedia.org/wiki/Penrose_diagram)
The Penrose diagram is a way to visualize wormholes and black holes. Along the x-axis is the spatial dimension while the time dimension is along the y-axis. Moving to the top-right represents an infinitely far future in space and time, while moving to the bottom-left is an infinitely distant past along space and time.

![[Pasted image 20230430123216.png]]
(https://en.wikipedia.org/wiki/Light_cone)
The Penrose diagram indicates what futures are reachable and which ones aren't. The fundamental assumption is that nothing can travel faster than light. If we traced out every point in space that was reachable by a photon across time, this would create a "light cone". Anything inside this light cone is a place in space-time that is considered reachable from the present. However, anything outside this light cone is not physically possible to be reached, or else you would have to travel faster than the speed of light to get there. 

In general, light is represented by a 45 degree ray. Any angle greater means you travel slower than light. And angle less than 45 degrees means you travel faster than light. 

![[Pasted image 20230430121409.png]]
The Penrose diagram presented by the paper depicts a wormhole with two openings, a left (L) and a right (R). The right horizon (45 degree line) represents the untraversable barrier between the left wormhole and the right wormhole.

If we inserted the message into our system and didn't create a negative energy shockwave by coupling with $\exp(igV)$, this would have kept the particle on the left wormhole. Eventually the message will hit the singularity (top border) and disappear. 

On the other hand, the coupling results in a negative energy shockwave which allows the message to cross the horizon of the right opening of the wormhole. 


## Quantum Teleportation versus Quantum Wormhole
This "teleportation" of information might sound like the standard quantum teleportation protocol. After all, we are still transfering quantum information. There is, however, a subtle distinction between the two. 

What makes the traversable wormhole protocol different is that it does not require any post-processing for the sending or receiving party. The message simply appears onto the receiving end of the system. We do not require Alice to make any measurements in order to communicate classically to Bob what controlled operations to apply, such as the $X$ and $Z$ gates. 

# Conclusions
The interest in this protocol doesn't come from the pure quantum interpretation of this experiment. It is possible to generate other such quantum circuits with similar properties of scrambling and unscrambling. What makes this particular configuration interesting is that this quantum system has a known gravitational dual according to string theory. This system can be visualized as two entangled black holes such that there is a traversable wormhole between the two. It's also important to make clear that a real wormhole was not actually created in the lab. This was only a highly tailored quantum system that was selected because of it's interesting consequences theoretically. 

This report only scratches the surface with the work that is being done in this field. It was quite challenging to research this report and I hope to have conveyed the complexities and depth accurately. It is likely in the coming years we will continue to hear more about wormhole and the quantum to gravity duality as innovations in quantum computing hardware come about. It is a very exciting time to be involved with quantum gravity research and I am excited to see what else comes to fruition.
