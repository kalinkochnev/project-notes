## circuit.measure()
`QuantumCircuit.measure([0,1], [0,1])`: if you pass the entire quantum and classical registers to `measure`, the ith qubit’s measurement result will be stored in the ith classical bit.

# DAGCircuit
`bfs_successors()` - returns `(DAGNode, [DAGNodes])` where the first element is the current node and the second is the successors, in [[Graphs#Breadth first search]]

`topological_nodes`  returns `generator(DAGOpNode, DAGInNode, DAGOutNode)`

# Parameters
`qargs` - qubits that operation will be applied on
`cargs` - classical bits that operation will be applied on