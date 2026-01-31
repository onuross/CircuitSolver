# CIRCUITSOLVER: AUTOMATED NODE VOLTAGE ANALYSIS ENGINE

![Status](https://img.shields.io/badge/status-planned%20%2F%20in%20progress-yellow)
![Domain](https://img.shields.io/badge/domain-electrical%20engineering-blue)
![Domain](https://img.shields.io/badge/domain-systems%20programming-blue)

CircuitSolver is a software engine designed to parse, model, and solve electrical DC circuits. Unlike a simple calculator, this engine "understands" circuit topology and automatically constructs the conductance matrix using **Node Voltage Analysis** (Knotenpotenzialverfahren).

This project bridges the gap between **Computer Science** (Graph Theory, Parsing, Memory Management) and **Electrical Engineering** (Circuit Laws, Matrix Algebra).

---

## PROJECT OBJECTIVE

The goal is to automate the mathematical transformation:

```
[G] * [phi] = [Iq]
```

Where:
- **[G]**: The Conductance Matrix (Leitwertmatrix)
- **[phi]**: The Node Potential Vector (Unknowns)
- **[Iq]**: The Source Current Vector

---

## FUNCTIONAL REQUIREMENTS

### 1. Circuit Parser (Detection Phase)

The program reads a **Netlist file** (text-based) defining connections. It does not ask for matrix coefficients directly.

**Example Input** (`circuit.txt`):
```
V1   1   0   10.0   (10V Source)
R1   1   2   100.0  (100 Ohm)
R2   2   0   200.0  (200 Ohm)
```

### 2. Matrix Assembly (MNA Algorithm)

- Iterates through the component list
- Stamps values into the system matrix **[G]** and vector **[Iq]**
- Converts Resistors (R) to Conductance (G = 1/R)
- Applies Kirchhoff's Current Law (KCL)

### 3. The Solver

- Solves the linear equation system to find node potentials **[phi]**
- Computes branch currents and voltages

---

## IMPLEMENTATION ROADMAP

### Phase 1: Python Prototype (Proof of Concept)

- **Goal**: Validate logic using high-level abstractions
- **Tools**: Python 3, NumPy
- **Task**: Parse text file → Solve using `numpy.linalg.solve`

### Phase 2: C Implementation (Hardcore Mode)

- **Goal**: High-performance, low-level implementation (No external math libraries)
- **Tools**: C (C99/C11), Make, Valgrind
- **Key Challenges**:
  - Dynamic memory allocation (`malloc`, `free`) for matrices
  - Custom Gaussian Elimination / LU Decomposition
  - Linked Lists for component storage

---

## TEST CASE (VALIDATION)

Based on HTW Dresden coursework standards:

- **Nodes**: 3 Unknowns (phi1, phi2, phi3) + GND
- **Sources**: Uq1 = 10V, Uq2 = -5V, Uq3 = 5V
- **Resistors**: Mixed 1 Ohm and 2 Ohm values

---

## FUTURE IMPROVEMENTS

- AC Circuit Support (Complex Numbers)
- Graph Visualization
- Graphical User Interface (GUI)

---

## Author

**onuross**

---

## License

*[Add your license information here]*
