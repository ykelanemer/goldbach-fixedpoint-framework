# Peer Review & Mathematical Critique: "An Unconditional Proof of the Goldbach Conjecture via the $P^*_\infty$ Fixed-Point Framework"

**Author:** Dr. Youcef Kelanemer  
**Reviewer:** Mathematical Peer Reviewer / Senior Number Theory Referee  
**Date:** September 2026  
**Document Under Review:** `gc_paper.tex` / `gc_paper.pdf` (24 pages)  
**Classification:** Primary 11P32; Secondary 15A18, 05C20, 11D45  

---

## 1. Executive Summary & Recommendation

The manuscript proposes an arithmetic-dynamical and spectral approach to the binary Goldbach Conjecture. The central strategy is:
1. Assume a counterexample $2N > 6$ exists.
2. Define a prime-factor mapping $D(S) = \bigcup_{p \in S} \operatorname{PrimeFactors}(2N - p) \setminus \operatorname{PrimeFactors}(2N)$.
3. Construct the descending chain $P^*(0) \supseteq P^*(1) \supseteq \dots$ and argue it stabilizes at a non-empty stationary set $P^*_\infty = D(P^*_\infty)$.
4. Extract a minimal strongly connected component (terminal island $I$ of cardinality $k = |I|$) governed by an irreducible exponent matrix $M \in \mathbb{Z}_{\ge 0}^{k \times k}$ with zero diagonal.
5. Attempt a systematic elimination of all cardinalities $k \ge 1$:
   - Low dimensions $k = 1, 2, 3$ via Diophantine arguments;
   - Binary/square-free exponent domains via modular congruences;
   - Dimensions $k = 4, 5$ via Newton trace identities;
   - Large dimensions $k \ge 6$ via Perron–Frobenius spectral bounds and Baker's theory of linear forms in logarithms.
6. Conclude that no terminal island can exist, implying $P^*_\infty = \emptyset$, contradicting $P^*_\infty \neq \emptyset$, thereby proving the Goldbach Conjecture.

### Recommendation: **REJECT**

While the arithmetic-dynamical framework $P^*(n+1) = D(P^*(n))$ and the reformulation into directed graphs are novel and imaginative heuristics, **the paper contains multiple fatal mathematical errors, logical leaps, and unsubstantiated claims that completely invalidate the claimed proof.** The proof collapses at several independent junctures. Below is an exhaustive technical report detailing the major fatal flaws, secondary conceptual gaps, and minor errors.

---

## 2. Primary Fatal Flaws (The "Showstoppers")

---

### Fatal Flaw 1: The Subgraph Cycle Fallacy in $k = 4$ and $k = 5$ (Propositions 4.17 & 4.18)

In **Proposition 4.17** (lines 743–748) and **Proposition 4.18** (lines 791–796), the author claims:
$$\operatorname{Tr}(M) = 0, \quad \operatorname{Tr}(M^2) = 0, \quad \operatorname{Tr}(M^3) = 0$$
for any governing exponent matrix of dimension $k = 4$ and $k = 5$.

The author justifies this as follows:
- $\operatorname{Tr}(M) = 0$ because $k=1$ self-loops were eliminated in Proposition 4.1.
- $\operatorname{Tr}(M^2) = 0$ because 2-prime cycles were eliminated in Proposition 4.2.
- $\operatorname{Tr}(M^3) = 0$ because 3-prime cycles were eliminated in Proposition 4.5.

#### Why This is Mathematically Fatal:
This is a **fundamental confusion between an autonomous terminal component (an island) and a subgraph of a larger graph.**

- **What Proposition 4.2 actually proved:** There cannot exist an *isolated, autonomous* 2-prime island $I = \{p_1, p_2\}$ where $2N - p_1 = p_2^{a_1}$ and $2N - p_2 = p_1^{a_2}$ (i.e. where neither complement has any other prime factors).
- **What occurs in $k = 4$ and $k = 5$:** In an island of 4 primes $\{p_1, p_2, p_3, p_4\}$, two vertices $p_1$ and $p_2$ can easily have mutual divisibility:
  $$p_2 \mid (2N - p_1) \quad \text{and} \quad p_1 \mid (2N - p_2),$$
  as long as $2N - p_1$ also has other prime factors from $\{p_3, p_4\}$ (for example, $2N - p_1 = p_2 p_3$ and $2N - p_2 = p_1 p_4$).
  
In this case, $a_{1,2} \ge 1$ and $a_{2,1} \ge 1$, which means the directed graph $G = (I, R)$ contains the 2-cycle $p_1 \to p_2 \to p_1$. Consequently, the $(1,1)$-entry of $M^2$ is non-zero:
$$(M^2)_{1,1} \ge a_{1,2} a_{2,1} \ge 1 \implies \operatorname{Tr}(M^2) \ge 2 > 0.$$

The non-existence of an autonomous $k=2$ island does **not** preclude a 2-cycle from existing as a subgraph within a strongly connected $k=4$ graph! Because edges leave $\{p_1, p_2\}$ to $\{p_3, p_4\}$, $\{p_1, p_2\}$ is **not** an island on its own.

The exact same fallacy applies to 3-cycles: a 3-cycle $p_1 \to p_2 \to p_3 \to p_1$ can exist in a $k=4$ or $k=5$ graph without $\{p_1, p_2, p_3\}$ being an isolated island, meaning $\operatorname{Tr}(M^3) > 0$.

#### Consequence:
The characteristic polynomials:
$$P_M(\lambda) = \lambda^4 - c_4 \quad (k=4) \qquad \text{and} \qquad P_M(\lambda) = \lambda^5 - c_4\lambda - c_5 \quad (k=5)$$
are **completely false**. In general, $c_2 \neq 0$ and $c_3 \neq 0$. The entire structural collapse of $k=4$ and $k=5$ rests on these non-zero coefficients vanishing, and therefore **the proofs of Proposition 4.17 and Proposition 4.18 are entirely invalidated.**

---

### Fatal Flaw 2: The Decoupling Barrier and Asymptotic Elimination (Proposition 4.14 & Corollary 4.16)

Section 4.5 and Section 4.6 claim to rule out all large islands $k \ge 6$ by establishing that the cumulative upper-spectrum Perron weight satisfies:
$$U_{\text{Large}} < \frac{2}{\rho(M)} \le \frac{2}{3},$$
which is claimed to force the matrix $M$ to become reducible via Baker–Matveev theory. This argument contains multiple fatal errors:

#### 2.1 Applying Baker–Matveev to an Exact Zero Identity
In Step 4 of Proposition 4.14 (lines 706–708):
> *"By taking natural logarithms of the governing system $2N - p_i = \prod_{j=1}^k p_j^{a_{i,j}}$, each row generates a linear form in logarithms $\Lambda_i = \ln(2N - p_i) - \sum_{j=1}^k a_{i,j} \ln p_j = 0$. Because the distinct primes $p_1, \dots, p_k$ are multiplicatively independent over $\mathbb{Q}$, Theorem 4.10 (Baker–Matveev) establishes that non-zero linear combinations of $\ln p_j$ are bounded strictly away from zero..."*

**The Error:**  
Baker–Matveev provides a lower bound on $|\Lambda|$ **if and only if** $\Lambda \neq 0$. Here, $\Lambda_i$ is **identically zero** by definition of the prime factorization of the integer $2N - p_i$. One cannot invoke a theorem providing a lower bound for non-zero forms to deduce constraints on an exact integer equality ($\Lambda_i \equiv 0$).

#### 2.2 Confusion Between Upper Bounds and Lower Bounds on Eigenvector Components
In Step 4 of Proposition 4.14 and Step 3 of Corollary 4.16:
The author derives:
$$\min_{j \in J_{\text{Large}}} u_j \le \frac{U_{\text{Large}}}{m} < \frac{2}{m \cdot \rho(M)} \le \frac{2}{3m}.$$
The author then claims that this upper bound contradicts the lower bound from Lemma 4.13:
$$u_j \ge \delta(k, \rho) = \frac{1}{k \cdot \rho(M)^{k-1}} > 0.$$

**The Error:**  
An **upper bound** on a minimum component does not contradict a **lower bound** unless the upper bound is strictly smaller than the lower bound!  
Let us test the author's own numbers for $k = 6, \rho(M) = 3, m = 3$:
- The upper bound gives: $\min_{j \in J_{\text{Large}}} u_j \le \frac{2}{3 \times 3} = \frac{2}{9} \approx 0.222$.
- The lower bound from Lemma 4.13 gives:
  $$\delta(6, 3) = \frac{1}{6 \cdot 3^{6-1}} = \frac{1}{6 \times 243} = \frac{1}{1458} \approx 0.000686.$$

Is there any contradiction in having:
$$0.000686 \le \min_{j \in J_{\text{Large}}} u_j \le 0.222222?$$
**None whatsoever.** Any number between $0.0007$ and $0.22$ satisfies both bounds. The author has conflated "the capacity decays" with "the capacity drops below the strictly positive lower bound $\delta(k, \rho)$."

#### 2.3 The False Reducibility Implication
The author claims (lines 708–709 and 727–728):
> *"Forcing $U_{\text{Large}} < \frac{2}{\rho(M)}$ under discrete integer exponent constraints forces at least one incoming or outgoing edge weight to vanish ($a_{r,j} = 0 \text{ for all } r$), causing the directed graph $G = (I, R)$ to decouple into reducible subgraphs."*

**The Error:**  
This statement has no mathematical basis. In an irreducible non-negative matrix, eigenvector components $u_j$ can be small without any matrix entries vanishing. For any normalized vector ($\sum u_i = 1$) in $\mathbb{R}^k$, the average component is $1/k$. As $k \to \infty$, the average component naturally scales as $O(1/k) \to 0$. In a simple directed cycle $C_k$, every component is identically $u_j = 1/k \to 0$, yet the graph is strongly connected and irreducible for all $k$. Scaling of eigenvector components does **not** force edge weights to vanish.

#### 2.4 Unsubstantiated Spectrum Partitioning ($m \ge 2$ and $m \ge \lfloor k/2 \rfloor$)
In Step 3.3 of Proposition 4.14, the author asserts without proof:
> *"At least $m \ge 2$ distinct primes must lie in the upper spectrum $(\sqrt{2N}, \frac{2N-5}{3}]$."*

And in Step 1 of Corollary 4.16:
> *"forcing at least $m \ge \lfloor k/2 \rfloor \ge 3$ distinct primes into the upper spectrum..."*

Neither Proposition 2.13 (which only bounds $\max(P^*_\infty) \le \frac{2N-5}{3}$) nor Proposition 3.2 (strong connectivity) provides any lower bound on the number of primes exceeding $\sqrt{2N}$. It is entirely possible *a priori* for an island to have only 0 or 1 prime strictly greater than $\sqrt{2N}$, with all other primes below $\sqrt{2N}$ raised to higher powers (e.g. $3^a \approx 2N$).

---

### Fatal Flaw 3: The Reversed Inequality in the Square-Free Domain (Proposition 4.8)

In **Proposition 4.8**, Subcase 2.5.b (lines 560–563), the author attempts to rule out sparse binary-exponent graphs for $k = 4$.

The author establishes:
$$2N \ge 7 p_4 + 3 \implies p_4 \le \frac{2N - 3}{7}.$$
Then for an incoming neighbor $p_m$, $2N - p_m = p_4 p_j$ with $p_j < p_4 \le \frac{2N-3}{7}$. The author writes:
> *"we get: $2N - p_m = p_4 p_j \le \left(\frac{2N - 3}{7}\right)^2 < 2N - p_m \quad \text{for all } 2N \ge 8$, yielding a direct arithmetic contradiction."*

#### Why This is Mathematically Fatal:
The inequality $\left(\frac{2N - 3}{7}\right)^2 < 2N - p_m$ is **COMPLETELY FALSE** for all large $N$.

Let us evaluate this directly:
- Let $2N = 100$:
  $$\left(\frac{97}{7}\right)^2 \approx (13.857)^2 \approx 192.0 > 100 - p_m \quad (\approx 97).$$
- Let $2N = 1000$:
  $$\left(\frac{997}{7}\right)^2 \approx (142.43)^2 \approx 20286 \gg 1000 - p_m.$$

The function $f(N) = \left(\frac{2N-3}{7}\right)^2$ is **quadratic** in $N$, while $2N - p_m$ is **linear** in $N$. For all $2N > 55$, $\left(\frac{2N-3}{7}\right)^2$ is strictly **greater** than $2N - p_m$. The author's claimed contradiction relies on an inequality that runs in the exact opposite direction.

Furthermore, in Step 2.6 (lines 568–570) for $k \ge 5$, the author claims:
> *"the product $Q_{k,i} = \prod p_j$ grows superlinearly with respect to $k$, exceeding the mandatory compositeness ceiling $Q_{k,i} = \frac{2N - p_k}{p_i} < \frac{2N}{3}$, creating a contradiction for all $k \ge 5$."*

This is completely unfounded. If $N = 10^{12}$, a product of two or three small primes in $Q_{k,i}$ (e.g. $3 \times 5 \times 7 = 105$) is orders of magnitude smaller than $2N/3 \approx 6.6 \times 10^{11}$. The cardinality $k$ has no necessary coupling to the magnitude of $N$.

---

### Fatal Flaw 4: Unjustified Diophantine Steps in $k = 2$ and $k = 3$ (Propositions 4.2 & 4.5)

#### 4.1 In Proposition 4.2 ($k = 2$, lines 422–426):
The author attempts to prove that:
$$2N - p_1 = p_2^{a_1} \quad \text{and} \quad 2N - p_2 = p_1^{a_2}$$
has no solutions for $a_1, a_2 \ge 2$.
1. **Subcase 2.4.a ($a_1 = 2$):**  
   The author writes (line 423):
   > *"For $a_2 \ge 4$: dividing the identity repeatedly by $p_1$ induces an integer descent on constant terms down to $p_1 \mid 1$, which is impossible for any prime $p_1 \ge 3$."*  
   This statement is an assertion without proof. No descent mechanism is established.
2. **Subcase 2.4.b ($a_1 \ge 3$):**  
   The author writes (lines 425–426):
   > *"By Theorem 4.3 (Mihăilescu's Theorem, for unit power differences) and Theorem 4.4 (Zsigmondy's Theorem...), the primitive factors in $p_1^{a_2-1} - 1$ force the power difference $|p_2^{a_1} - p_1^{a_2}|$ for $a_2 > a_1 \ge 3$ to strictly exceed $p_1 p_2 > p_2 - p_1$, precluding any integer solution."*  
   - Mihăilescu's Theorem solves Catalan's conjecture: $x^a - y^b = 1$. It does **not** apply to $x^a - y^b = C$ for $C = p_2 - p_1 \ge 2$. Pillai's conjecture (that $|x^a - y^b| \to \infty$) is a famous **unsolved** problem in number theory.
   - Zsigmondy's Theorem guarantees the existence of a primitive prime factor; it provides no lower bound of the form $|p_2^{a_1} - p_1^{a_2}| > p_1 p_2$. This entire step is mathematically unjustified.

#### 4.2 In Proposition 4.5 ($k = 3$, lines 467–468):
The author derives:
$$2N \ge p_2(p_1 + 1) + p_1 \implies p_2^{a-1} \ge p_1 + 1.$$
The author then concludes:
> *"For $3 \le p_1 < p_2 < p_3 \le \frac{2N-5}{3}$, this superlinear growth rate contradicts the compositeness ceiling $p_3 = \max(I) \le \frac{2N-5}{3}$."*

**The Error:**  
This is a pure non-sequitur. The inequality $p_2^{a-1} \ge p_1 + 1$ is trivially satisfied for almost all primes (e.g. $p_1 = 3, p_2 = 5, a = 2 \implies 5^1 \ge 3 + 1 = 4$, which is true). It does not imply superlinear growth that exceeds $2N/3$, nor does it contradict $p_3 \le (2N-5)/3$.

---

## 3. Secondary Conceptual & Methodological Issues

### 3.1 Misleading Use of Deep Machinery as "Window Dressing"
The manuscript frequently cites deep, celebrated theorems that ultimately play no logical role in the proof or are misapplied:
- **Theorem 4.10 (Baker–Matveev):** Quoted at length (Definition of heights, linear forms in logs). However, in Proposition 4.9, the bound $a_{i,j} \le \frac{\ln(2N-3)}{\ln 3}$ is proven using nothing more than $3^a \le 2N-3$ (elementary high-school algebra). Baker's theorem is completely unused there, and in Proposition 4.14 it is applied to an exact zero.
- **Theorem 4.3 (Mihăilescu):** Quoted for differences of 1, but the problem involves differences of $p_2 - p_1 \ge 2$.
- **Theorem 4.4 (Zsigmondy):** Quoted, but the necessary quantitative bounds on prime power differences are not implied by Zsigmondy.

### 3.2 The Fundamental Gap in the Elimination Strategy
The overarching architecture claims:
$$\text{No minimal terminal island } I \text{ exists} \implies P^*_\infty = \emptyset \implies \text{Contradiction with } P^*_\infty \neq \emptyset.$$

Even if the proof that $P^*_\infty \neq \emptyset$ under the counterexample hypothesis is correct (Propositions 2.1–2.11), the proof that no island $I$ exists fails for **every single cardinality $k \ge 2$**:
- $k = 2$: Unproved Diophantine descent and misapplication of Mihăilescu/Zsigmondy.
- $k = 3$: Non-sequitur in Step 2.2.
- $k = 4, 5$: False assumption that subgraphs cannot have 2-cycles or 3-cycles ($\operatorname{Tr}(M^2) = \operatorname{Tr}(M^3) = 0$).
- Square-free: Reversed inequality in Step 2.5.b ($192 < 97$).
- $k \ge 6$: Misapplication of Baker–Matveev to zero, and comparing an upper bound $\le 0.222$ to a lower bound $\ge 0.0007$ thinking it is a contradiction.

Since **not a single case $k \ge 2$ is rigorously eliminated**, the claimed contradiction never materializes.

---

## 4. Specific Section-by-Section Corrections & Minor Issues

1. **Lemma 4.13 (`lem:perron_floor`):**
   - The path length is denoted by $m \le k-1$:
     $$u_j = \frac{1}{\rho(M)^m} \sum_{i=1}^k u_i (M^m)_{i,j} \ge \frac{1}{k \cdot \rho(M)^{k-1}}.$$
   - However, immediately in Proposition 4.14 and Corollary 4.16, the variable $m$ is reused to denote the cardinality of the upper-spectrum primes $m = |J_{\text{Large}}| \ge 2$. This dual use of $m$ creates confusion and should be changed to $\ell \le k-1$ for the path length.

2. **Step 1 of Proposition 4.14 (line 665):**
   - The trace power is written as $\operatorname{Tr}(M^m)$, once again overloading $m$. It should be $\operatorname{Tr}(M^r)$ or $\operatorname{Tr}(M^\ell)$.

3. **Proposition 2.7 (Convergence, lines 177–181):**
   - The notation $|P^*(n)|$ is treated as a sequence of natural numbers. While finite descending chains of sets do stabilize, the proof would benefit from clarifying that $D$ is monotonic: $A \subseteq B \implies D(A) \subseteq D(B)$, which guarantees $P^*(n+1) \subseteq P^*(n)$ for all $n \ge 1$. (This step is one of the few logically sound parts of the paper).

4. **Formatting and Overfull Hboxes:**
   - Lines 177–178: Overfull `\hbox` (31.9pt too wide).
   - Line 687: Overfull `\hbox` (14.8pt too wide) in the display math equation for $\mathbf{u}^T \mathbf{x}$.

---

## 5. Detailed Guidance for the Author

1. **What is salvageable?**
   - The formulation of the operator $D(S) = \bigcup_{p \in S} \operatorname{PrimeFactors}(2N - p) \setminus \operatorname{PrimeFactors}(2N)$ and the proof that $D(P^*(0)) \subseteq P^*(0)$ with $q \nmid 2N$ is an interesting, valid dynamical framework.
   - The elimination of single-prime loops ($k = 1$) in Proposition 4.1 is mathematically correct.
   - The spectral radius lower bound $\rho(M) \ge 2$ (Proposition 4.11) via Collatz–Wielandt is mathematically correct *under the assumption that an autonomous island $I$ exists*.

2. **What cannot be salvaged?**
   - **The claim of an unconditional proof of the Goldbach Conjecture.** The gaps identified above (especially the subgraph cycle fallacy in $k=4, 5$ and the reversed inequality in square-free domains) are not minor typos; they are foundational barriers that standard additive number theory has struggled with for centuries (the parity barrier).
   - **The Spectral Radius Decoupling Barrier (Proposition 4.14).** Perron–Frobenius theory governs asymptotic growth of matrix powers; it does not possess the arithmetic rigidity to rule out integer matrices whose eigenvector components decay as $O(1/k)$.
   - **The application of Baker's theory.** Baker's theorem bounds non-zero linear forms away from zero; it cannot constrain an exact integer factorization.

### Conclusion
The paper in its current state is unpublishable in any peer-reviewed mathematical journal. The author is strongly advised to retract the claim of having proven the Goldbach Conjecture, remove the invalid propositions (Propositions 4.2, 4.5, 4.8, 4.14, 4.17, 4.18, and Corollary 4.16), and reframe the work as an exploratory dynamical heuristic or computational study of the operator $D$.
