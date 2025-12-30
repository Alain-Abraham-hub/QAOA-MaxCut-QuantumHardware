# Max-Cut with QAOA: From Classical Baselines to Quantum Hardware

An end-to-end implementation of the Quantum Approximate Optimization Algorithm (QAOA) for solving the Maximum Cut (Max-Cut) problem. This project demonstrates the complete workflow from classical optimization baselines through QUBO formulations to quantum circuit execution on real IBM quantum hardware.

## Overview

The Maximum Cut problem is a classic NP-hard combinatorial optimization problem where the goal is to partition graph vertices into two sets to maximize the number of edges between the sets. This project implements multiple approaches:

- **Classical Methods**: Greedy and random baseline algorithms
- **QUBO Formulation**: Ising model representation for quantum computing
- **QAOA Circuit**: Parametric quantum circuit with cost and mixer Hamiltonians
- **Parameter Optimization**: Classical optimization of quantum circuit parameters
- **Quantum Execution**: Running on IBM's real quantum hardware

## Notebooks

### 1. `01_classical_maxcut.ipynb`
Implements classical baseline algorithms for the Max-Cut problem:
- Greedy algorithm for finding approximate solutions
- Random baseline for performance comparison
- Problem formulation and graph representation

### 2. `02_qubo_and_ising.ipynb`
Converts the Max-Cut problem into quantum-compatible formats:
- QUBO (Quadratic Unconstrained Binary Optimization) formulation
- Ising model representation
- Mapping between classical and quantum problem encodings

### 3. `03_qaoa_circuit.ipynb`
Builds the quantum circuit for QAOA:
- Creates parametric quantum circuit with cost Hamiltonian
- Implements mixer Hamiltonian for exploration
- Demonstrates circuit structure and gate operations

### 4. `04_parameter_optimization.ipynb`
Optimizes QAOA parameters using classical methods:
- Uses COBYLA optimizer from SciPy
- Finds optimal gamma (cost phase) and beta (mixer phase)
- Evaluates circuit on quantum simulator
- Tracks optimization progress

### 5. `05_*` (Future)
Additional notebooks for advanced analysis and comparison

### 6. `06_run_on_ibm_quantum_hardware.ipynb`
Executes optimized QAOA on real IBM quantum hardware:
- Connects to IBM Quantum Platform
- Transpiles circuit for hardware compatibility
- Runs circuit with 4000 shots
- Analyzes measurement outcomes
- Visualizes results with histograms

## Requirements

```bash
pip install qiskit qiskit-aer qiskit-ibm-runtime scipy numpy matplotlib
```

Optional for visualization:
```bash
pip install pylatexenc
```

## Setup

### IBM Quantum Account
To run on real quantum hardware, you need an IBM Quantum account:

1. Create account at [IBM Quantum](https://quantum.ibm.com)
2. Get your API token from the dashboard
3. Update the token in notebook 6 (or save it using `QiskitRuntimeService.save_account()`)

### Configuration
The project uses the IBM Quantum open plan by default, which supports batch execution mode. Real hardware execution requires transpilation to match the target backend's native gates.

## Results

The QAOA algorithm finds approximate solutions to Max-Cut by:

1. **Encoding the problem** in the cost Hamiltonian
2. **Exploring the solution space** with the mixer Hamiltonian  
3. **Measuring outcomes** and computing cut values
4. **Optimizing parameters** to maximize the expected cut value

Results on 4-qubit graph:
- Graph edges: `[(0,1), (0,2), (1,2), (1,3)]`
- Optimal parameters: `gamma ≈ 1.50`, `beta ≈ 1.49`
- Execution: 4000 shots on real IBM quantum processor

## Key Concepts

### QAOA (Quantum Approximate Optimization Algorithm)
A hybrid quantum-classical algorithm that uses parameterized quantum circuits to find approximate solutions to optimization problems.

### Cost Hamiltonian
Encodes the Max-Cut objective: applies phases to computational basis states based on the number of edges cut by that state.

### Mixer Hamiltonian  
Enables exploration of the solution space by applying X rotations, creating superposition between different bitstring solutions.

### Parameters
- **γ (gamma)**: Cost Hamiltonian phase angle
- **β (beta)**: Mixer Hamiltonian phase angle

These are optimized classically to maximize the expected cut value.

## Files

```
.
├── 01_classical_maxcut.ipynb           # Classical baselines
├── 02_qubo_and_icing.ipynb             # Problem formulation
├── 03_qaoa_circuit.ipynb               # QAOA circuit design
├── 04_parameter_optimization.ipynb     # Parameter tuning
├── 06_run_on_ibm_quantum_hardware.ipynb # Real hardware execution
├── README.md                            # This file
└── LICENSE
```

## References

- [Quantum Approximate Optimization Algorithm](https://arxiv.org/abs/1602.07674)
- [Qiskit Documentation](https://qiskit.org/documentation/)
- [IBM Quantum](https://quantum.ibm.com/)
- [Maximum Cut Problem](https://en.wikipedia.org/wiki/Maximum_cut)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

Hebron - December 2025
