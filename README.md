# The $P^*_\infty$ Fixed-Point Framework for the Goldbach Conjecture

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21712619.svg)](https://doi.org/10.5281/zenodo.21712619)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)

SSRN Abstract ID: 7274460

**Author:** Dr. Youcef Kelanemer (Ph.D. in Numerical Analysis, Université Paris XI - Paris-Sud)  
**MSC2020 Classification:** Primary 11P32; Secondary 15A18, 05C20, 11D45  
**Keywords:** Goldbach Conjecture, Fixed-Point Dynamics, Perron–Frobenius Theorem, Trace Nullities, Spectral Radius, Diophantine Systems  

---

## Executive Summary

This repository contains the formal mathematical manuscript establishing an arithmetic-dynamical fixed-point framework ($P^*_\infty$) that reformulates hypothetical Goldbach counterexamples $2N > 6$ into an isolated, finite **Linear-Algebraic & Diophantine Matrix System** $\mathcal{S}(2N, k, M)$.

Through modular growth constraints, trace energy identities, Newton polynomial reductions, and Perron–Frobenius spectral graph theory, the framework proves the complete structural collapse of all low-cardinality loops ($k = 0, 1, 2, 3, 4, 5$), all square-free exponent domains ($a_{i,j} \in \{0, 1\}$), and all large stationary islands ($k \ge 6$).

---

## Story of the Proof

To understand the architecture of the proof without getting lost in technical calculations, here is the high-level narrative following every step from the initial setup to the final contradiction:

### 1. The Counterexample Setup
Suppose Goldbach's Conjecture is false. That means there exists some even integer $2N > 6$ that cannot be written as the sum of two prime numbers ($p_1 + p_2$). 

If $2N$ cannot be written as $p_1 + p_2$, then for **every** prime $p < 2N$, the complementary number $2N - p$ can **never** be a prime. Every complement $2N - p$ must be a composite number, meaning it breaks down into a product of at least two prime factors.

### 2. The Iterated Divisor Machine ($D$)
Instead of searching directly for prime pairs, we define a dynamical machine:
* Take a set of primes $S$ less than $2N$ (excluding any prime factors of $2N$).
* For every prime $p$ in $S$, calculate $2N - p$.
* Collect all the prime factors of these composite numbers into a new set, called $D(S)$.

If we start with all valid primes $P^*(0)$ and repeatedly run this machine ($P^*(0) \to P^*(1) \to P^*(2) \dots$), the set of primes shrinks at each step because prime factors of $2N - p$ are strictly bounded below $2N/3$. 

Because we start with a finite collection of primes and the sets keep shrinking, the process **must stabilize** in a finite number of steps into a non-empty, stationary "fixed-point limit set" $P^*_\infty = D(P^*_\infty)$.

### 3. Terminal Islands as Directed Graphs
Inside this non-empty stationary set $P^*_\infty$, there must exist at least one self-contained, minimal core of primes called a **terminal island** $I$ of size $k = |I|$. 

In an island of $k$ primes, every prime $p_i$ has its complement $2N - p_i$ made up *entirely* of prime factors that are also inside the island $I$. This turns the hypothetical counterexample into a strongly connected directed graph governed by a $k \times k$ matrix of exponents $M$.

The proof then systematically proves that **no island of any size $k$ can exist**, creating an inescapable trap.

### 4. Ruling Out Small Islands ($k = 1, 2, 3$)
* **$k = 1$ (Single-Prime Loops):** A prime $p$ cannot be its own prime factor ($p \mid 2N - p$) because that would mean $p$ divides $2N$, which was excluded at the start. Thus, 1-prime self-loops cannot exist.
* **$k = 2$ (Two-Prime Cycles):** If two primes $p_1, p_2$ only point to each other ($2N - p_1 = p_2^{a_1}$ and $2N - p_2 = p_1^{a_2}$), subtracting the equations forces growth rates that cannot be satisfied by integers.
* **$k = 3$ (Three-Prime Cycles):** With three primes, if all exponents are $1$, subtracting adjacent equations forces one prime to equal $1$, a contradiction. If exponents are higher, exponential growth forces the prime product past $2N$.

### 5. Ruling Out Large Islands ($k \ge 6$)
For large islands of size $k \ge 6$, we analyze the graph using matrix spectral theory (Perron–Frobenius theorem):
* Because every complement $2N - p_i$ is composite, every row of the exponent matrix has at least $2$ factors, forcing the dominant eigenvalue (spectral radius) $\rho(M) \ge 2$.
* However, upper-spectrum primes (primes near $2N/3$) grow so rapidly that their logarithms dominate the system. 
* To maintain $\rho(M) \ge 2$, the eigenvector weight assigned to these large primes must shrink toward zero ($U_{\text{Large}} < \frac{2}{\rho(M)}$). 
* As $k \ge 6$ grows, the weight capacity for individual upper primes decays as $O(1/k) \to 0$. But in a strongly connected graph, no node's weight can drop to zero without breaking the graph apart into disconnected pieces. Thus, no large islands ($k \ge 6$) can exist.

### 6. Closing the Trap ($k = 4$ and $k = 5$)
With $k = 1, 2, 3$ and $k \ge 6$ eliminated, only dimensions $k = 4$ and $k = 5$ remain:
* Because 1-cycles, 2-cycles, and 3-cycles cannot exist in our graph, the matrix traces are zero ($\operatorname{Tr}(M) = \operatorname{Tr}(M^2) = \operatorname{Tr}(M^3) = 0$).
* By Newton's formulas, the characteristic polynomials collapse to $\lambda^4 - c_4$ for $k=4$ and $\lambda^5 - c_4\lambda - c_5$ for $k=5$.
* Topological graph analysis proves that it is impossible to add enough directed edges to give every node at least 2 factors without creating a 2-cycle or 3-cycle, which would break the zero-trace condition.

### 7. The Grand Contradiction
* Step 2 proved that any counterexample **forces** the existence of a non-empty stationary limit set $P^*_\infty \neq \emptyset$, which must contain a terminal island of size $k \ge 1$.
* Steps 4, 5, and 6 proved that **no terminal island of size $k = 0, 1, 2, 3, 4, 5$ or $k \ge 6$ can exist**.

Because no island of any dimension can exist, $P^*_\infty$ must be empty ($P^*_\infty = \emptyset$). This directly contradicts $P^*_\infty \neq \emptyset$, proving that **no counterexample to Goldbach's Conjecture can exist**. 

Therefore, every even integer $2N > 2$ is the sum of two prime numbers.

---

## Architectural Taxonomy of Ruling Propositions

| Island Dimension ($k$) | Mathematical Result & Mechanism | Ruling Proposition |
| :--- | :--- | :--- |
| **$k = 0$** | Non-Emptiness & Stationary Set Convergence | Proposition 3.10 |
| **$k = 1$** | Elimination of Self-Loops ($\text{Tr}(M) = 0$) | Proposition 3.5 |
| **$k = 2$** | Elimination of 2-Cycles ($\text{Tr}(M^2) = 0$) | Proposition 3.16 |
| **$k = 3$** | Elimination of 3-Cycles ($\text{Tr}(M^3) = 0$) | Proposition 3.17 |
| **$k = 4$** | Newton Trace Squeeze ($\lambda^4 - c_4$) | Proposition 3.24 |
| **$k = 5$** | Newton Trace Squeeze ($\lambda^5 - c_4\lambda - c_5$) | Proposition 3.25 |
| **$k \ge 6$** | Spectral Decoupling Barrier ($U_{\text{Large}} < \frac{2}{\rho(M)} \le \frac{2}{3}$) | Prop 3.22 & Corollary 3.23 |
| **Square-Free** | Elimination of Binary Exponents ($a_{i,j} \in \{0, 1\}$) | Proposition 3.19 |

---

## Citation & Permanent Archive

This work is permanently archived on Zenodo (CERN) under DOI: [10.5281/zenodo.21712619](https://doi.org/10.5281/zenodo.21712619).

### BibTeX
```bibtex
@article{kelanemer2026goldbach,
  author    = {Kelanemer, Youcef},
  title     = {An Unconditional Proof of the Goldbach Conjecture via the $P^*_\infty$ Fixed-Point Framework},
  year      = {2026},
  month     = jul,
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.21712619},
  url       = {https://doi.org/10.5281/zenodo.21712619}
}
```

---

## Repository Structure

```
.
├── .gitattributes
├── .gitignore
├── README.md
└── paper/
    ├── gc_paper.md
    ├── gc_paper.pdf
    └── gc_paper.tex
```
