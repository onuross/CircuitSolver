# ⚡ CircuitSolver
**Automated Node Voltage Analysis Engine**

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Domain](https://img.shields.io/badge/Domain-Electrical%20Engineering%20%7C%20Systems%20Programming-blue)

**CircuitSolver** is a software engine that automatically analyzes and solves **DC electrical circuits** using  
**Node Voltage Analysis (Knotenpotenzialverfahren)**.

Unlike simple calculators, this project understands **circuit topology**, parses a netlist, constructs the
conductance matrix, and solves the resulting linear system.

This project intentionally bridges:

- **Electrical Engineering** (KCL, circuit laws, matrix equations)
- **Computer Science** (parsing, data structures, memory management, numerical methods)

---

## 🎯 Project Goal

Automatically transform a circuit description into the mathematical system:

\[
[G] \cdot [\phi] = [I_q]
\]

Where:

- **\( [G] \)** — Conductance matrix (Leitwertmatrix)
- **\( [\phi] \)** — Node potential vector (unknowns)
- **\( [I_q] \)** — Source current vector

The solver computes all node voltages and allows derivation of branch currents and voltage drops.

---

## 🧩 Core Features

### 1. Circuit Parsing
Reads a text-based **netlist** describing components and connections.

**Example (`circuit.txt`):**
```text
# Component  NodeA  NodeB  Value
V1           1      0      10.0   # 10V source
R1           1      2      100.0  # 100 Ohm
R2           2      0      200.0  # 200 Ohm
