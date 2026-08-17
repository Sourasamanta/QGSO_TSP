# Quantum Gravitational Search Optimization for TSP

A hybrid **Quantum Gravitational Search Optimization (QGSO)** approach for solving the **Traveling Salesman Problem (TSP)** using Qiskit and classical optimization techniques.

## Overview

This project implements and evaluates a quantum-enhanced variant of the **Gravitational Search Optimization (GSO)** algorithm for solving TSP instances.

The implementation uses real-world geographic coordinates of eight cities in Odisha, India, and calculates inter-city distances using the **Haversine formula**.

The project compares the performance of:

* Classical Gravitational Search Optimization (GSO)
* Quantum Gravitational Search Optimization (QGSO)
* OR-Tools
* Exact brute-force TSP solution

## Key Features

* Real-world geographic TSP instance
* Haversine-based distance calculation
* Classical GSO implementation
* Quantum-enhanced GSO implementation
* Quantum measurement using Qiskit AerSimulator
* Mass-controlled quantum rotations
* Hermitian Hamiltonian validation
* Unitary operator validation
* QUBO formulation using Qiskit Optimization
* Exact TSP benchmark
* OR-Tools benchmark
* Multiple experimental runs
* Convergence tracking

## Cities

The TSP instance contains the following cities:

* Bhubaneswar
* Cuttack
* Puri
* Khordha
* Dhenkanal
* Jajpur
* Balasore
* Berhampur

The coordinates used by the implementation are defined in the source code.

## Methodology

### 1. Distance Matrix

The geographic distance between each pair of cities is calculated using the Haversine formula. The resulting matrix is used as the cost function for the TSP.

### 2. Classical GSO

The classical GSO algorithm initializes a population of candidate tours and evaluates each tour according to its total travel distance.

Agents are assigned normalized masses based on their fitness. Stronger agents influence weaker agents, while mutation maintains population diversity.

### 3. Quantum GSO

QGSO extends the classical approach by introducing quantum-controlled decisions.

Agent masses are used to construct quantum operators and control `RY` rotations. The resulting quantum measurements determine whether an agent moves toward stronger gravitational attractors.

### 4. QUBO Formulation

The TSP is formulated as a quadratic optimization problem using binary variables.

The formulation enforces:

* Each city is visited exactly once.
* Each tour position contains exactly one city.
* The objective minimizes the total travel distance.

The quadratic program is subsequently converted into a QUBO using `QuadraticProgramToQubo`.

### 5. Benchmarking

QGSO and GSO results are compared against an exact brute-force solution and an OR-Tools solution. Multiple runs with controlled random seeds are used for additional evaluation.

## Configuration

The current configuration is:

| Parameter       | Value |
| --------------- | ----: |
| Population Size |    20 |
| Iterations      |    50 |
| Mutation Rate   |  0.20 |
| Experiments     |     3 |
| Master Seed     |    42 |

These parameters are defined in the main configuration section.

## Technologies

* **Python**
* **Qiskit**
* **Qiskit Aer**
* **Qiskit Optimization**
* **NumPy**
* **NetworkX**
* **Matplotlib**
* **OR-Tools**
* **Folium**

## Installation

Install the required dependencies using:

```bash
pip install qiskit qiskit-aer qiskit-optimization networkx matplotlib ortools folium
```

## Running the Project

Run the Python implementation in a Jupyter Notebook or Google Colab environment.

The program:

1. Creates the city distance matrix.
2. Builds the TSP QUBO model.
3. Runs classical GSO.
4. Runs QGSO.
5. Computes the exact TSP solution.
6. Solves the problem using OR-Tools.
7. Performs multiple experimental runs.
8. Compares the resulting tour distances.

## Results

The implementation reports the final tours and distances obtained by:

```text
GSO
QGSO
OR-Tools
Exact Solution
```

This allows the optimization quality of QGSO to be evaluated against both classical metaheuristic and reference solutions.

## Project Structure

```text
QGSO-TSP/
│
├── QGSO_TSP.ipynb
├── README.md
└── requirements.txt
```

> Update the filenames above to match the actual files in your repository.

## Reproducibility

Experiments use fixed random seeds to provide reproducible initialization and comparison across GSO and QGSO runs.

## License

This project is intended for research, experimentation, and educational purposes.

Add an appropriate license file if you plan to distribute the project publicly.
