# The $P^*_\infty$ Fixed-Point Framework for the Goldbach Conjecture

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21712619.svg)](https://doi.org/10.5281/zenodo.21712619)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)

**Author:** Dr. Youcef Kelanemer (Ph.D. in Numerical Analysis, Université Paris XI - Paris-Sud)  
**MSC2020 Classification:** Primary 11P32; Secondary 15A18, 05C20, 11D45  
**Keywords:** Goldbach Conjecture, Fixed-Point Dynamics, Perron–Frobenius Theorem, Trace Nullities, Spectral Radius, Diophantine Systems  

---

## Executive Summary

This repository contains the formal mathematical manuscript establishing an arithmetic-dynamical fixed-point framework ($P^*_\infty$) that reformulates hypothetical Goldbach counterexamples $2N > 6$ into an isolated, finite **Linear-Algebraic & Diophantine Matrix System** $\mathcal{S}(2N, k, M)$.

Through modular growth constraints, trace energy identities, Newton polynomial reductions, and Perron–Frobenius spectral graph theory, the framework proves the complete structural collapse of all low-cardinality loops ($k = 0, 1, 2, 3, 4, 5$), all square-free exponent domains ($a_{i,j} \in \{0, 1\}$), and all large stationary islands ($k \ge 6$).

---

## Architectural Taxonomy of Ruling Propositions

| Island Dimension ($k$) | Mathematical Result & Mechanism | Ruling Proposition |
| :--- | :--- | :--- |
| **$k = 0$** | Non-Emptiness & Stationary Set Convergence | Proposition 8 |
| **$k = 1$** | Elimination of Self-Loops ($\text{Tr}(M) = 0$) | Proposition 4 |
| **$k = 2$** | Elimination of 2-Cycles ($\text{Tr}(M^2) = 0$) | Proposition 13 |
| **$k = 3$** | Elimination of 3-Cycles ($\text{Tr}(M^3) = 0$) | Proposition 14 |
| **$k = 4$** | Newton Trace Squeeze ($\lambda^4 - c_4$) | Proposition 20 |
| **$k = 5$** | Newton Trace Squeeze ($\lambda^5 - c_4\lambda - c_5$) | Proposition 20B |
| **$k \ge 6$** | Spectral Decoupling Barrier ($U_{\text{Large}} < \frac{2}{\rho(M)} \le \frac{2}{3}$) | Corollary 19.1 |
| **Square-Free** | Elimination of Binary Exponents ($a_{i,j} \in \{0, 1\}$) | Proposition 16 |

---

## Repository Structure

```text
├── paper/
│   ├── gc_paper.pdf       # Full compiled manuscript
│   └── gc_paper.tex       # LaTeX source file
├── README.md              # Project overview & documentation
└── LICENSE                # Creative Commons Attribution 4.0 International
