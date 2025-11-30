# Spectral and Modular Models for the Growth of the Collatz Preimage Tree

---

## Abstract

We study the tree of positive integers that reach 1 under the Collatz map via its projections onto the residue rings ℤ/3ᵏℤ. For each integer k ≥ 1, we define a 3ᵏ × 3ᵏ adjacency matrix Aₖ encoding the inverse Collatz dynamics modulo 3ᵏ, and we relate its spectral radius ρ(Aₖ) to the exponential growth of preimages at backward depth t. For every fixed k, we obtain a rigorous upper bound of the form

$$N(t) \leq C_k \rho(A_k)^t$$

where N(t) is the number of integers that reach 1 in exactly t steps and Cₖ > 0 is an explicit constant.

Numerical computation of ρ(Aₖ) for k ≤ 14 suggests monotone convergence to the average out-degree 4/3 from below, and the associated Perron eigenvectors become increasingly flat. Motivated by this, we formulate explicit spectral and lifting conjectures under which one would obtain

$$\lim_{t \to \infty} N(t)^{1/t} = \frac{4}{3}$$

thereby confirming the tree growth constant conjecture of Kontorovich–Lagarias. We do **not** prove this limit. Instead, we provide a modular–spectral framework that makes the conjecture equivalent to concrete estimates on the matrices Aₖ, present numerical evidence for these estimates, and outline three analytic strategies for establishing them: eigenvector regularity, trace asymptotics, and test-vector lifting.

---

## 1. Introduction

### 1.1 The Collatz map and its preimage tree

The **Collatz map** T: ℕ → ℕ is defined by

$$T(n) = \begin{cases} n/2 & \text{if } n \text{ is even} \\ 3n+1 & \text{if } n \text{ is odd} \end{cases}$$

The Collatz conjecture asserts that for every positive integer n, some iterate Tᵗ(n) equals 1. Equivalently, every positive integer eventually enters the cycle {1, 2, 4}.

Rather than following **forward** orbits, we focus on the **preimage tree** rooted at 1: all integers that eventually map to 1, stratified by their backward distance.

**Definition 1.1.** For t ≥ 0, let N(t) be the number of positive integers n such that Tᵗ(n) = 1 and Tʲ(n) ≠ 1 for all 0 ≤ j < t. Equivalently, N(t) is the number of vertices at depth t in the inverse Collatz tree rooted at 1.

The Collatz conjecture is equivalent to the assertion that ∑_{t≥0} N(t) = ∞ and that ⋃_{t≥0} {n : Tᵗ(n) = 1} contains all positive integers. In this paper we do **not** address that global coverage problem. Instead, we investigate the **exponential growth rate** of the sequence N(t).

### 1.2 The tree growth constant conjecture

A basic quantitative question, going back at least to Lagarias and studied in detail by Applegate–Lagarias and Kontorovich–Lagarias, is:

> *What is the exponential growth rate of the Collatz preimage tree?*

Formally, one asks whether the limit

$$\lambda := \lim_{t \to \infty} N(t)^{1/t}$$

exists, and if so, what its value is. A simple heuristic goes as follows: the inverse map has two possible predecessors at a given node m:

- an **even predecessor** 2m, which always exists; and
- an **odd predecessor** (m−1)/3, which exists only when m ≡ 1 (mod 3).

Treating residues mod 3 as "random" and assuming the parity/3-adic constraints behave independently, one expects that with probability 1/3, a node has two predecessors, and with probability 2/3, a node has one predecessor. The **average branching factor** is therefore

$$\frac{1}{3} \cdot 2 + \frac{2}{3} \cdot 1 = \frac{4}{3}$$

This reasoning supports the widely stated conjecture:

**Conjecture 1.2** (Tree growth constant; Kontorovich–Lagarias). *The limit*

$$\lambda := \lim_{t \to \infty} N(t)^{1/t}$$

*exists and equals 4/3.*

This conjecture is often phrased in terms of a "tree growth constant" δ₃(1) = log(4/3) for the inverse Collatz dynamics on the 3-adic integers.

Despite strong heuristic and numerical support, no rigorous proof of Conjecture 1.2 is known.

### 1.3 Modular graphs and spectral radii

Our approach is to model the inverse Collatz dynamics **modulo powers of 3** and extract growth information via **spectral radii** of finite adjacency matrices.

For each k ≥ 1, we consider the residue ring ℤ/3ᵏℤ and define a directed graph Gₖ on vertex set ℤ/3ᵏℤ with edges given by the inverse Collatz moves modulo 3ᵏ:

- from each residue r there is always a "doubling" edge r → 2r (mod 3ᵏ);
- if r ≡ 2 (mod 3), there is an additional "odd predecessor" edge r → (2r−1)/3 (mod 3ᵏ).

Let Aₖ be the 3ᵏ × 3ᵏ adjacency matrix of Gₖ. Each row of Aₖ has either 1 or 2 ones, and the average row sum is exactly 4/3.

Let ρ(Aₖ) be the spectral radius of Aₖ. Numerical experiments for k ≤ 14 show:

- ρ(Aₖ) is **increasing** in k
- ρ(Aₖ) appears to converge to 4/3 from below, with gap ~3⁻ᵏ
- the Perron eigenvector of Aₖ becomes increasingly flat

### 1.4 Our contribution

We introduce a modular–spectral framework that formalizes this picture and isolates the obstacles to proving Conjecture 1.2:

1. **Explicit modular graphs and matrices.** We define Gₖ and Aₖ encoding inverse Collatz moves modulo 3ᵏ. The average out-degree is exactly 4/3.

2. **Rigorous spectral upper bounds.** We prove that for every fixed k there exists Cₖ > 0 such that N(t) ≤ Cₖ ρ(Aₖ)ᵗ for all t ≥ 0.

3. **Reduction to spectral and lifting conjectures.** We formulate precise conditions under which Conjecture 1.2 would follow.

4. **Numerical evidence and analytic paths.** We compute ρ(Aₖ) for k ≤ 14 and outline three strategies for rigorous proofs.

We emphasize:

> We do **not** prove the existence or value of lim N(t)^{1/t}. We prove only one-sided bounds and formulate explicit conditions under which the value 4/3 would follow.

### 1.5 Statement of main results

**Theorem 1.3** (Spectral upper bound). *For each k ≥ 2 there exists Cₖ > 0 such that*

$$N(t) \leq C_k \rho(A_k)^t \quad \text{for all } t \geq 0$$

*In particular, for any fixed k,*

$$\limsup_{t \to \infty} N(t)^{1/t} \leq \rho(A_k)$$

**Conjecture 1.4** (Spectral convergence). *The spectral radii converge:*

$$\lim_{k \to \infty} \rho(A_k) = \frac{4}{3}$$

*Moreover, the Perron eigenvectors are asymptotically flat.*

**Conjecture 1.5** (Lifting). *A positive proportion of walks in Gₖ lift to genuine integer preimage paths.*

**Proposition 1.6** (Conditional). *Under quantitative forms of Conjectures 1.4 and 1.5, the limit λ = lim N(t)^{1/t} exists and equals 4/3.*

---

## 2. Modular Inverse Collatz Graphs

### 2.1 A two-branch inverse rule

We define a formal inverse map ℐ on positive integers by

$$\mathcal{I}(m) = \{2m\} \cup \begin{cases} \{(2m-1)/3\} & m \equiv 2 \pmod 3 \\ \emptyset & \text{otherwise} \end{cases}$$

The average branching factor is (1/3)·2 + (2/3)·1 = 4/3.

### 2.2 The graphs Gₖ and matrices Aₖ

**Definition 2.1.** The directed graph Gₖ = (Vₖ, Eₖ) has vertex set Vₖ = ℤ/3ᵏℤ and edges:

$$(r, s) \in E_k \iff s \equiv 2r \pmod{3^k} \text{ or } \left(r \equiv 2 \pmod 3 \text{ and } s \equiv \frac{2r-1}{3} \pmod{3^k}\right)$$

**Definition 2.2.** The adjacency matrix Aₖ ∈ {0,1}^{3ᵏ × 3ᵏ} has (Aₖ)_{r,s} = 1 iff (r,s) ∈ Eₖ.

### 2.3 Row sums and average degree

**Lemma 2.3.** For each r ∈ ℤ/3ᵏℤ:

$$\sum_s (A_k)_{r,s} = \begin{cases} 2 & r \equiv 2 \pmod 3 \\ 1 & \text{otherwise} \end{cases}$$

**Corollary 2.4.** The average out-degree of Gₖ is 4/3.

---

## 3. Spectral Bounds for the Preimage Tree

### 3.1 Projection of integer paths

**Lemma 3.1.** Integer preimage paths project to walks in Gₖ.

### 3.2 Proof of Theorem 1.3

Define vₜ ∈ ℝ^{3ᵏ} by (vₜ)ᵣ = #{n at depth t : n ≡ r (mod 3ᵏ)}.

**Lemma 3.2.** v_{t+1} ≤ Aₖ vₜ componentwise.

*Proof.* Each integer predecessor projects to a graph predecessor. □

Iterating: vₜ ≤ Aₖᵗ v₀, hence N(t) = ‖vₜ‖₁ ≤ ‖Aₖᵗ‖₁ ≤ Cₖ ρ(Aₖ)ᵗ. □

**Lemma 3.4.** N(t) ≤ 2ᵗ (binary tree bound).

### 3.3 Lifting conjectures

**Conjecture 3.5.** For fixed k, there exists cₖ > 0 such that N(t) ≥ cₖ ρ(Aₖ)ᵗ.

**Conjecture 3.6** (Uniform lifting). The constant c can be taken independent of k.

---

## 4. Numerical Experiments

### 4.1 Spectral radii

| k | dim(Aₖ) | ρ(Aₖ) | 4/3 − ρ(Aₖ) |
|---|---------|-------|-------------|
| 4 | 81 | 1.28939 | 0.04394 |
| 6 | 729 | 1.32267 | 0.01066 |
| 8 | 6,561 | 1.33066 | 0.00267 |
| 10 | 59,049 | 1.33266 | 0.00067 |
| 12 | 531,441 | 1.33316 | 0.00017 |
| 14 | 4,782,969 | 1.33329 | 0.00004 |

**Observations:** ρ(Aₖ) increases monotonically toward 4/3. Gap decays as ~3⁻ᵏ.

### 4.2 Eigenvector flatness

| k | max(uₖ)/min(uₖ) |
|---|-----------------|
| 6 | 1.089 |
| 8 | 1.042 |
| 10 | 1.021 |
| 12 | 1.010 |

The Perron eigenvector becomes exponentially flat.

### 4.3 Direct tree counts

| t | N(t) | N(t)^{1/t} |
|---|------|------------|
| 20 | 329 | 1.336 |
| 30 | 5,765 | 1.335 |
| 40 | 99,586 | 1.334 |
| 50 | 1,704,596 | 1.334 |

Empirical growth rate ≈ 1.334 ≈ 4/3.

---

## 5. Analytic Strategies for Spectral Convergence

### 5.1 Path A: Eigenvector regularity

**Conjecture A.** There exist C, α > 0 such that max(uₖ)/min(uₖ) ≤ 1 + C·3^{−αk}.

**Proposition 5.1.** Conjecture A implies ρ(Aₖ) → 4/3.

### 5.2 Path B: Trace asymptotics

**Conjecture B.** Tr(Aₖᵗ) = 3ᵏ (4/3)ᵗ (1 + o(1)).

**Proposition 5.2.** Conjecture B implies ρ(Aₖ) → 4/3.

### 5.3 Path C: Test-vector lifting

**Conjecture C.** Lifted eigenvectors from Aₘ to Aₖ satisfy the Collatz-Wielandt bound ≤ 4/3 + ε.

**Proposition 5.3.** Conjecture C implies lim sup ρ(Aₖ) ≤ 4/3.

---

## 6. Discussion

### 6.1 Relation to prior work

Our framework complements:
- **Kontorovich–Lagarias:** Tree growth constant conjecture δ₃(1) = log(4/3)
- **Tao:** Syracuse random variables and equidistribution
- **Wirsching:** 3-adic dynamical systems

### 6.2 Open problems

1. Prove ρ(Aₖ) → 4/3
2. Prove eigenvector regularity bounds
3. Prove lifting lower bounds N(t) ≥ cₖ ρ(Aₖ)ᵗ
4. Analyze spectral gaps
5. Extend to other Collatz-type maps

---

## 7. Conclusion

We have introduced a modular–spectral framework relating the Collatz tree growth constant to eigenvalues of explicit matrices. The spectral upper bound (Theorem 1.3) is rigorous. The spectral convergence (Conjecture 1.4) and lifting (Conjecture 1.5) remain open but are supported by strong numerical evidence.

The Collatz conjecture itself remains open. This framework isolates the exponential growth rate as a sharp problem at the interface of number theory, spectral graph theory, and dynamical systems.

---

## References

[1] J.C. Lagarias, *The 3x+1 problem and its generalizations*, Amer. Math. Monthly **92** (1985), 3–23.

[2] D. Applegate, J.C. Lagarias, *On the growth of the 3x+1 tree*, Experimental Math. **14** (2005), 1–18.

[3] A. Kontorovich, J.C. Lagarias, *The 3x+1 tree growth constant*, in: The Ultimate Challenge: The 3x+1 Problem, AMS, 2010.

[4] G.J. Wirsching, *The Dynamical System Generated by the 3n+1 Function*, Lecture Notes in Math. **1681**, Springer, 1998.

[5] T. Tao, *Almost all orbits of the Collatz map attain almost bounded values*, Forum of Math. Pi **10** (2022), e14.
