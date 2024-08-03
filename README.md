# QuantumEmbeddings
Class generation to create different types of data embeddings returned as circuit objects that can easily be used in Qiskit, inspired by Pennylane.


Example formats for what each data point should appear as can be seen below:

Basis Embedding: Encodes n binary features into a basis state of n qubits.

For example, np.array([0, 1, 0]) will prepare state |010⟩. See https://docs.pennylane.ai/en/stable/code/api/pennylane.BasisEmbedding.html

Amplitude Embedding: Encodes 2^n features into the amplitude vector of n qubits.

The input vector must be comprised of a combination of the angles (in radians) meant to be plugged into the vector. To determine the length of the ideal vector, experiment with the number of qubits you wish to see in the feature map first, then organize the elements in accordance with the ParameterVector elements attached to each gate.

Your input vector will append each value to the circuit in the following order: [x[0], x[1], x[2]..., x[n]].

Note: Ensure that the angles for the CRX gates are either 0 or pi. For the CRX gates surrounding the RY gates, the angles will always be pi. If all of the RZ 
gates are 0 for any single qubit, all CRX gates except for the biggest one must be set to 0 radians (the CRX gate spanning from the target qubit (the single qubit) and the control qubit (qubit n) must be set to pi at all times).

Angle Embedding: Embeds the vector elements into the feature map as arrays. Number of elements corresponds to number of qubits, though there are exceptions (see AngleEmbedding.ipynb).
