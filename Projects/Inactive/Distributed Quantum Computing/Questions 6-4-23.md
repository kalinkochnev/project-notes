- Quantum repeaters
- Bell swap destroys entanglement with b and a and b and c, but connects a and c with entanglement. Creates long range entanglement without transmitting data 

- What is an eBit? And what is the storage pool for?
- https://www.quantiki.org/wiki/ebit
	- stands for entangled bit
	- storage pool is the number of shared qubit pairs for a given node 
	- When a CNOT is used, it uses up an entangled pair and requires reestablishing the entanglement between nodes
- What was the motivation for using a grid structure for the graph?
	- it is common with networking
![[Efficient Routing for Quantum Key Distribution#Questions]]

# Misc
- Is there a parallel to this network and the optimization of operations on a quantum computer? I assume there is some kind of work to figure out how to lay out the qubit structure so that the operation is executed properly
- Are there any issues of me writing about working on the project on my blog?
- Honors thesis?

# Simulation criteria
**Compatibility with Python**
- Language compatibility (C++, Python, Rust)
- Routing algorithm description (Python, C++, Rust)
- Qiskit compatibility (Y/N) 

**Open source (Y/N)**
- use overleaf

**Simulation speed**
- How long should a complete suite of tests take (X seconds)

**Scalability**
- Max number of nodes/qubits (N)
- Maximum number of neighbors (K)
- Platform (desktop, cluster of computers)

**Configurability**
- User Interface (**CLI** or GUI)
- Algorithm visualization (Y/N)
- Simulation parameters through file (Y/N)

**Data export**
- Recorded parameters of interest? (gates per network round, runtime)
- Raw data vs aggregate
- File type (text, csv, xlsx)

**Global state vs local qubit state**
- Should qubits act as isolated units like in a true network (local) or can it be a global state that an algorithm updates qubits as if they were local 

- Start with grid, implement arbitrary later