# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a LinkedIn Learning course repository for "Quantum Computing Fundamentals" containing Jupyter notebook examples for quantum computing concepts using Qiskit. The course was updated from Qiskit 0.13 to work with Qiskit 1.0+ API.

## Development Environment

### Recommended Python Version
- Python 3.11 (Qiskit 1.0+ requires Python 3.9 or newer)

### Setup Options

#### Option 1: Conda Environment (Recommended)
```bash
conda env create -f environment.yml
conda activate qiskit
```

#### Option 2: pip
- Install dependencies: `pip install -r requirements.txt`

### Key Dependencies
- `qiskit` - Main quantum computing framework
- `qiskit-aer` - Quantum simulator backend
- `qiskit-ibm-provider` - IBM Quantum provider
- `qiskit-ibm-runtime` - IBM runtime services  
- `jupyter` - Notebook environment
- `matplotlib` - Plotting and visualization
- `pylatexenc` - LaTeX rendering support

### Development Setup
The repository includes a devcontainer configuration that automatically installs requirements on creation. Use GitHub Codespaces or VS Code with Dev Containers extension.

## Repository Structure

The `src/` directory contains 28 lesson folders organized by course sections:

- `01_*` - Introduction to quantum computing concepts (measurement, Bloch sphere)
- `02_*` - Multiple qubits 
- `03_*` - Pauli gates (X, Y, Z) and binary encoding
- `04_*` - Superposition gates (Hadamard, phase, rotation) and random numbers
- `05_*` - Multi-qubit gates (CNOT, Toffoli, SWAP) and binary adder
- `06_*` - Entanglement and Bell states
- `07_*` - Real quantum hardware
- `08_*` - Quantum protocols (superdense coding, teleportation)

Each lesson folder typically contains:
- `*_begin.ipynb` - Starting notebook for hands-on exercises
- `*_end.ipynb` - Completed solution notebook

## Working with Notebooks

### Common Qiskit 1.0+ Import Pattern
```python
from qiskit import *
from qiskit.visualization import plot_histogram
%matplotlib inline
```

### Updated Simulator Usage (Post Qiskit 1.0)
```python
from qiskit.providers.basic_provider import BasicProvider
simulator = BasicProvider().get_backend('basic_simulator')
compiled_circuit = transpile(circuit, simulator)
result = simulator.run(compiled_circuit, shots=1024).result()
```

### Running Notebooks
- Use Jupyter: `jupyter notebook` or `jupyter lab`
- VS Code with Python extension provides native notebook support
- GitHub Codespaces includes pre-configured Jupyter environment

## Key Architecture Notes

- All quantum circuits use `QuantumRegister` and `ClassicalRegister` objects
- Circuits require explicit `transpile()` before execution on simulators
- Results are obtained via `.result().get_counts()` method
- Visualizations use `plot_histogram()` and matplotlib integration
- Course examples focus on educational concepts rather than production code

## Contributing

This repository does not accept pull requests. It serves as course material for LinkedIn Learning.