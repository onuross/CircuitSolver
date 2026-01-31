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

### 2. Matrix Assembly (MNA Algorithm)
* The software must iterate through the parsed list of components and "stamp" their values into the correct positions in the system matrix $[G]$ and vector $[I_q]$.
* Convert Resistors ($R$) to Conductance ($G = 1/R$).
* Apply **Kirchhoff's Current Law (KCL)** logic to populate the diagonal and off-diagonal elements.

### 3. The Solver
* Implement a Linear Equation Solver to find $[\phi]$.
* Compute specific branch currents and voltages based on the node potentials.

---

## 🛠️ Implementation Roadmap

### Phase 1: Python Prototype (Proof of Concept) 🐍
* **Goal:** Validate the logic and math using high-level abstractions.
* **Tools:** Python 3, NumPy (for matrix verification), OOP classes (Resistor, Source, Node).
* **Task:** Write a parser that reads a text file and uses `numpy.linalg.solve` to find the potentials.

### Phase 2: C Implementation (The "Hardcore" Mode) ⚙️
* **Goal:** High-performance, low-level implementation with no external math libraries.
* **Tools:** C (C99/C11), Make, Valgrind (for memory leak detection).
* **Key Challenges:**
    * Dynamic memory allocation for matrices of arbitrary size (`malloc`, `free`).
    * Implementing a custom Gaussian Elimination or LU Decomposition algorithm from scratch.
    * Struct-based implementation of a Linked List or Dynamic Array to store circuit components.

---

## 🧪 Test Case (Validation)

To verify the engine, the following circuit (based on HTW Dresden coursework) will be used:
* **Nodes:** 3 Unknowns ($\phi_1, \phi_2, \phi_3$) + 1 Reference Node (GND).
* **Sources:**
  * $U_{q1} = 10V$
  * $U_{q2} = -5V$
  * $U_{q3} = 5V$
* **Resistors:**
  * $R_1, R_2, R_3 = 1\Omega$
  * $R_4, R_5, R_6 = 2\Omega$

**Expected Output:** The program should output the exact node potentials $[\phi_1, \phi_2, \phi_3]$ and allow calculation of any branch current (e.g., current through $R_1$).

---

## 🚀 Future Improvements
- [ ] Support for AC Circuits (Complex Numbers / Impedance).
- [ ] Visualization of the circuit graph.
- [ ] Graphical User Interface (GUI).

---
*Author: onuross*
*Context: Fundamentals of Electrical Engineering & Computer Science*