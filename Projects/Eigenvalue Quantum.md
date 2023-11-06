

"An arbitrary square matrix C can be written as a sum of a Hermitian matrix A and a skew hermitian matrix B"
- https://en.wikipedia.org/wiki/Skew-Hermitian_matrix
- https://math.stackexchange.com/questions/4548536/can-every-non-hermitian-matrix-be-written-as-a-sum-of-hermitan-matrices
- https://math.stackexchange.com/questions/3214416/prove-that-any-normal-matrix-is-the-sum-of-hermitian-matrices


- Non-hermitian eigenvalue problem https://netlib.org/utk/people/JackDongarra/etemplates/node204.html




https://www.sciencedirect.com/science/article/pii/S0024379520302998
https://arxiv.org/pdf/2006.01837.pdf - pg 10 SVD, spectrum of non-hermitian section 2.3
- VQD can calculate as many eigenvalues as we want
- VQD needs # of eigenvalues to solve for, a quantum circuit to optimize, and an optimizer

1. Convert the unitary matrix to the circuit representation
2. Parameterize the circuit for use with the optimizer
3. Pick an optimizer
4. Pass it to VQD

[Qiskit VQD](https://qiskit.org/documentation/stubs/qiskit.algorithms.eigensolvers.VQD.html#qiskit.algorithms.eigensolvers.VQD)
[Parameterized circuit](https://qiskit.org/documentation/stubs/qiskit.circuit.QuantumCircuit.html#qiskit.circuit.QuantumCircuit)
- Parameters mean that a variable value is not required to be fixed at circuit definition
