# CircuitSolver: Automated Node Voltage Analysis Engine ⚡️

![Status](https://img.shields.io/badge/Status-Planned%20%2F%20In%20Progress-yellow)
![Domain](https://img.shields.io/badge/Domain-Electrical%20Engineering%20%7C%20Systems%20Programming-blue)

**CircuitSolver** is a software engine designed to parse, model, and solve electrical DC circuits. Unlike a simple calculator, this engine "understands" circuit topology and automatically constructs the conductance matrix using **Node Voltage Analysis** (Knotenpotenzialverfahren).

This project bridges the gap between **Computer Science** (Graph Theory, Parsing, Memory Management) and **Electrical Engineering** (Circuit Laws, Matrix Algebra).

---

## 🎯 Project Objective

The goal is to automate the mathematical transformation:

$$[G] \cdot [\phi] = [I_q]$$

Where:
* **$[G]$**: The Conductance Matrix (Leitwertmatrix)
* **$[\phi]$**: The Node Potential Vector (Unknowns)
* **$[I_q]$**: The Source Current Vector

---

## 📝 Functional Requirements

### 1. Circuit Parser (Detection Phase)
Reads a Netlist file (text-based) defining connections.

**Example Input (`circuit.txt`):**
```text
# Component  NodeA  NodeB  Value
V1           1      0      10.0   # 10V Source
R1           1      2      100.0  # 100 Ohm
R2           2      0      200.0  # 200 Ohm
```

### 2. Matrix Assembly (MNA Algorithm)
* Iterates through the parsed list of components and "stamp" their values into the system matrix $[G]$ and vector $[I_q]$.
* Converts Resistors ($R$) to Conductance ($G = 1/R$).
* Applies **Kirchhoff's Current Law (KCL)**.

### 3. The Solver
* Solves the linear equation system to find $[\phi]$.
* Computes branch currents and voltages.

---

## 🛠️ Implementation Roadmap

### Phase 1: Python Prototype (Proof of Concept) 🐍
* **Goal:** Validate logic using high-level abstractions.
* **Tools:** Python 3, NumPy.
* **Task:** Parse text file -> Solve using `numpy.linalg.solve`.

### Phase 2: C Implementation (Hardcore Mode) ⚙️
* **Goal:** High-performance, low-level implementation (No external math libraries).
* **Tools:** C (C99/C11), Make, Valgrind.
* **Key Challenges:**
    * Dynamic memory allocation (`malloc`, `free`) for matrices.
    * Custom Gaussian Elimination / LU Decomposition.
    * Linked Lists for component storage.

---

## 🧪 Test Case (Validation)

Based on **HTW Dresden** coursework standards:
* **Nodes:** 3 Unknowns ($\phi_1, \phi_2, \phi

---
*Author: onuross*
