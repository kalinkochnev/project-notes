# Distributed Quantum Computing
We want to combine the computation power of multiple quantum computers, but what is stopping us?

---
## Two main questions:
- How do we exchange entangled particles over large distances without degradation?
- How do we distribute the work of a quantum algorithm?

---

# Objectives
Develop a simulation to answer questions about mapping a quantum algorithm to an arbitrary network of worker nodes and repeater nodes.

**Simulation code objectives:**
- Easily extensible
- Unit tested
- Documented
- Performance sensitive


---
## What does the simulation do?
- Can specify any circuit, network topology, and routing algorithm to experiment with ways of distributing work
- No quantum computation/entanglement is done, but the simulation emulates the networking procedure that would be done by real computers

---
# Features
---
### 1) Direct interoperability with Qiskit

```python
def cnot_circuit(n_qubits: int):
    circuit = QuantumCircuit(n_qubits, n_qubits)
    for i in range(n_qubits):
        for j in range(1):
            circuit.h(i)

    for i in range(n_qubits - 1):
        circuit.cx(i, i + 1)
        circuit.measure(i, i)
    circuit.measure(n_qubits - 1, n_qubits - 1)
    return circuit
```

--

![[cnot_diagram.png]]

--

![[cnot_circuit.png]]

---

### 2) Realistic execution order of workers
*Example simulation log*
```
[2023-07-19 12:08:25,960] INFO: Worker 0 executed H on qubits [0]
[2023-07-19 12:08:25,960] INFO: Worker 0 executed H on qubits [1]
[2023-07-19 12:08:25,960] INFO: Worker 0 executed CX on qubits [0, 1]
[2023-07-19 12:08:25,960] INFO: Worker 12 executed H on qubits [2]
[2023-07-19 12:08:25,960] INFO: |>> WAITING: Entanglement (Wire 1 -> Wire 2) between Worker(id=0) and Worker(id=12)
[2023-07-19 12:08:25,961] INFO: Selected path: [0, 5, 6, 7, 12]
[2023-07-19 12:08:25,961] INFO: |>> DONE: Worker 0 entangled with Worker 12 and executed CX
[2023-07-19 12:08:25,961] INFO: Worker 12 executed H on qubits [3]
[2023-07-19 12:08:25,961] INFO: Worker 12 executed CX on qubits [2, 3]
[2023-07-19 12:08:25,961] INFO: Worker 24 executed H on qubits [4]
[2023-07-19 12:08:25,961] INFO: |>> WAITING: Entanglement (Wire 3 -> Wire 4) between Worker(id=12) and Worker(id=24)
[2023-07-19 12:08:25,961] INFO: Selected path: [12, 17, 22, 23, 24]
[2023-07-19 12:08:25,961] INFO: |>> DONE: Worker 12 entangled with Worker 24 and executed CX
[2023-07-19 12:08:25,961] INFO: Worker 24 executed H on qubits [5]
[2023-07-19 12:08:25,961] INFO: Worker 24 executed CX on qubits [4, 5]
[2023-07-19 12:08:25,961] INFO: Worker 0 executed MEASURE on qubits [0] and cbits [0]
[2023-07-19 12:08:25,961] INFO: Worker 0 executed MEASURE on qubits [1] and cbits [1]
[2023-07-19 12:08:25,961] INFO: Worker 12 executed MEASURE on qubits [2] and cbits [2]
[2023-07-19 12:08:25,961] INFO: Worker 12 executed MEASURE on qubits [3] and cbits [3]
[2023-07-19 12:08:25,961] INFO: Worker 24 executed MEASURE on qubits [4] and cbits [4]
[2023-07-19 12:08:25,961] INFO: Worker 24 executed MEASURE on qubits [5] and cbits [5]
```

---

### 3) Network topology and routing algorithms easily extendable
![[topology.png|200]]

---

### 4) Inline documentation
```python
class Network(ABC):
    """An abstract class to initialize the network with worker and repeater nodes.
    Should be overriden for different configurations of networks.

    Attributes
    ----------
    wire_map: `dict[QBitIndex, Node]`
        A mapping between Qubit indices to the worker that runs it.
    """

# ...
```

---
### 5) Unit tests
![[Pasted image 20230719124558.png]]

---
## Initial findings
- The issue of distributed quantum computing appears highly similar to that of finding the optimal usage of qubits on a quantum processor [^1]

>  A mapping algorithm (or mapper) finds an assignment of circuit qubits to architecture vertices such that gates can be executed efficiently.

[^1]: A. M. Childs, E. Schoute, and C. M. Unsal, “Circuit Transformations for Quantum Architectures”.
---

# Future work
- Better parameter configuration
- Statistics reporting
- Parallelization with GNU Parallel
- Work out unaccounted edge cases

---
### Continued:
- More topologies
- Importing/exporting networks
- Command line interface
- Visualization of algorithm mapped to a network

---

# Questions?