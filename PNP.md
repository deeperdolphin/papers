# AC⁰ Lower Bounds via Cohomological Invariants under FK Restriction

---

## Part I: Algebraic and Topological Foundations

### 1.1 Basic Definitions

**Definition 1.1.1 (Graph and Edge Labeling)**

Let $\Gamma = (V, E)$ be a connected graph with $|V| = n$ vertices and $|E| = m$ edges. Fix an arbitrary orientation of edges (for bookkeeping only; all operations are over $\mathbb{F}_2$ where orientation is irrelevant).

An **edge labeling** is a vector $a \in \mathbb{F}_2^E$.

**Definition 1.1.2 (Cochain Complex)**

The **0-cochains** are $C^0(\Gamma; \mathbb{F}_2) = \mathbb{F}_2^V$ (vertex labelings).

The **1-cochains** are $C^1(\Gamma; \mathbb{F}_2) = \mathbb{F}_2^E$ (edge labelings).

The **coboundary operator** $\delta: C^0 \to C^1$ is defined by:
$$(\delta h)(e) = h(u) \oplus h(v) \quad \text{for edge } e = (u,v)$$

**Definition 1.1.3 (Cut Space and Cycle Space)**

The **cut space** is $\mathcal{B} = \text{im}(\delta) \subseteq \mathbb{F}_2^E$.

The **cycle space** is $\mathcal{Z} = \ker(\partial) \subseteq \mathbb{F}_2^E$, where $\partial$ is the boundary operator (equivalently, $\mathcal{Z} = \mathcal{B}^\perp$ under the standard inner product).

A vector $c \in \mathcal{Z}$ is an **even subgraph**: every vertex has even degree in $\text{supp}(c)$.

**Lemma 1.1.4 (Dimensions)**

For a connected graph $\Gamma$:
- $\dim(\mathcal{B}) = n - 1$
- $\dim(\mathcal{Z}) = m - n + 1 =: \beta_1$ (the **cycle rank** or first Betti number)

*Proof*: The map $\delta$ has kernel of dimension 1 (constant functions), so $\dim(\mathcal{B}) = n - 1$. Since $\mathcal{B}$ and $\mathcal{Z}$ are orthogonal complements in $\mathbb{F}_2^E$, we have $\dim(\mathcal{Z}) = m - (n-1) = m - n + 1$. ∎

---

### 1.2 Fundamental Cycles and Holonomy

**Definition 1.2.1 (Spanning Tree and Fundamental Cycles)**

Let $T \subseteq E$ be a spanning tree of $\Gamma$. For each **chord** $e \in E \setminus T$, the **fundamental cycle** $C_e$ is the unique cycle formed by adding $e$ to $T$:
$$C_e = \{e\} \cup P_T(u, v)$$
where $P_T(u,v)$ is the unique path in $T$ connecting the endpoints of $e$.

**Lemma 1.2.2 (Fundamental Cycle Basis)**

The fundamental cycles $\{C_e : e \in E \setminus T\}$ form a basis for $\mathcal{Z}$.

*Proof*: There are $|E \setminus T| = m - (n-1) = \beta_1$ fundamental cycles, matching $\dim(\mathcal{Z})$. They are linearly independent because each $C_e$ contains the unique chord $e$ that appears in no other fundamental cycle. ∎

**Definition 1.2.3 (Holonomy Bits)**

For each chord $e_i \in E \setminus T$, define the **holonomy bit**:
$$\alpha_i(a) = \langle C_{e_i}, a \rangle = \bigoplus_{f \in C_{e_i}} a_f$$

The **holonomy vector** is $\alpha(a) = (\alpha_1(a), \ldots, \alpha_{\beta_1}(a)) \in \mathbb{F}_2^{\beta_1}$.

**Lemma 1.2.4 (Holonomy as Cohomology Class)**

For edge labeling $a \in \mathbb{F}_2^E$:
1. $\alpha(a) = 0$ if and only if $a \in \mathcal{B}$ (i.e., $a = \delta h$ for some $h$)
2. $\alpha(a) = \alpha(a')$ if and only if $a - a' \in \mathcal{B}$
3. The map $a \mapsto \alpha(a)$ induces an isomorphism $\mathbb{F}_2^E / \mathcal{B} \cong \mathbb{F}_2^{\beta_1}$

*Proof*: (1) If $a = \delta h$, then for any cycle $C$, $\langle C, a \rangle = \langle C, \delta h \rangle = 0$ (cycles are orthogonal to cuts). Conversely, if all cycle parities vanish, $a \perp \mathcal{Z}$, so $a \in \mathcal{B}$. (2) and (3) follow immediately. ∎

---

### 1.3 High-Girth Expanders and Connected Supports

**Definition 1.3.1 (Girth)**

The **girth** $g$ of a graph is the length of its shortest cycle.

**Lemma 1.3.2 (Holonomy Code from High-Girth Graph)**

Let $\Gamma$ be a $d$-regular graph with girth $g$. Let $T$ be any spanning tree. Then:

1. Each fundamental cycle $C_e$ (for $e \in E \setminus T$) is connected and has $|C_e| \geq g$.

2. The fundamental cycles $\{C_e : e \in E \setminus T\}$ are linearly independent.

3. $|\{C_e : e \in E \setminus T\}| = \beta_1 = \Theta(n)$ for bounded-degree graphs.

4. Every nonzero codeword in the span is a nonempty even subgraph, hence a disjoint union of simple cycles; by girth, each such cycle has length $\geq g$. In particular, every nonzero codeword has a connected component of size $\geq g$ and Hamming weight $\geq g$.

*Proof*: 

(1) Each fundamental cycle $C_e$ consists of chord $e$ plus the tree path connecting its endpoints, hence is connected. Since $C_e$ is a cycle and $\Gamma$ has girth $g$, we have $|C_e| \geq g$.

(2) Each $C_e$ contains the unique chord $e$ appearing in no other fundamental cycle.

(3) $\beta_1 = m - n + 1 = \frac{d}{2}n - n + 1 = (\frac{d}{2} - 1)n + 1 = \Theta(n)$.

(4) Any nonzero element of $\mathcal{Z}$ is an even subgraph. Even subgraphs decompose into edge-disjoint simple cycles (standard graph theory). In a graph of girth $g$, every simple cycle has length $\geq g$. ∎

**Remark 1.3.3 (Quantitative Tradeoff)**

For $d$-regular expanders, the Moore bound gives $g = O(\log_{d-1} n)$. Explicit constructions (Lubotzky-Phillips-Sarnak, Margulis) achieve $g = \Theta(\log n)$ with good expansion.

---

## Part II: Probabilistic Foundations (FK Random-Cluster Model)

### 2.1 The FK Measure

**Definition 2.1.1 (Random-Cluster Measure)**

For parameters $p \in (0,1)$ and $q \geq 1$, the **FK random-cluster measure** on $\omega \in \{0,1\}^E$ is:
$$\phi_{p,q}(\omega) = \frac{1}{Z_{p,q}} p^{|\omega|}(1-p)^{m-|\omega|} q^{k(\omega)}$$

where $|\omega| = \#\{e : \omega_e = 1\}$ is the number of open edges, $k(\omega)$ is the number of connected components in the subgraph $(V, \{e : \omega_e = 1\})$, and $Z_{p,q}$ is the normalizing constant.

**Definition 2.1.2 (Stochastic Domination)**

For probability measures $\mu, \nu$ on $\{0,1\}^E$, we write $\mu \leq_{\text{st}} \nu$ if for every increasing event $A$:
$$\mu(A) \leq \nu(A)$$

**Theorem 2.1.3 (FK Comparison Inequality — Grimmett)**

For $q \geq 1$:
$$\phi_{p,q} \leq_{\text{st}} \phi_{p,1}$$

where $\phi_{p,1}$ is i.i.d. Bernoulli($p$) percolation.

*Proof*: This is a standard result. See Grimmett, "The Random-Cluster Model," Chapter 3. The key is that $q \geq 1$ makes the cluster-counting term $q^{k(\omega)}$ favor configurations with more components, which corresponds to fewer open edges. ∎

---

### 2.2 Support Survival (H2)

**Definition 2.2.1 (Support Survival)**

For edge set $S \subseteq E$:
$$\text{Survive}(S) = \{\omega : \omega_e = 1 \text{ for all } e \in S\}$$

**Lemma 2.2.2 (H2 — Exact on Trees)**

If $\Gamma$ is a tree, then under $\phi_{p,q}$, edges are i.i.d. Bernoulli($\rho$) where:
$$\rho = \frac{p}{p + q(1-p)}$$

Hence for any $S \subseteq E$:
$$\phi_{p,q}(\text{Survive}(S)) = \rho^{|S|}$$

*Proof*: On a tree with $n$ vertices, any edge configuration $\omega$ satisfies $k(\omega) = n - |\omega|$ (each open edge reduces the component count by exactly 1, and no cycles exist).

The unnormalized weight is:
$$w(\omega) = p^{|\omega|}(1-p)^{m-|\omega|}q^{n-|\omega|} = q^n \left(\frac{p}{q}\right)^{|\omega|}(1-p)^{m-|\omega|}$$

This is a product measure with:
$$\Pr[\omega_e = 1] = \frac{p/q}{p/q + (1-p)} = \frac{p}{p + q(1-p)} = \rho$$

∎

**Lemma 2.2.3 (H2 — General Graphs via Cluster Tail)**

Assume $\phi_{p,q}$ satisfies an exponential cluster tail: there exist $C, c > 0$ such that for all vertices $v$ and all $k \geq 1$:
$$\phi_{p,q}(|K(v)| \geq k) \leq Ce^{-ck}$$

where $K(v)$ is the open cluster containing $v$.

Then for any **connected** edge set $S$ with $|S| = L$ in a graph of maximum degree $\Delta$:
$$\phi_{p,q}(\text{Survive}(S)) \leq C\exp\left(-c \cdot \frac{2L}{\Delta}\right)$$

*Proof*: If all edges in $S$ are open, then all vertices incident to $S$ lie in one FK cluster. A connected graph with $L$ edges and maximum degree $\Delta$ has at least $\frac{2L}{\Delta}$ vertices (since $2L = \sum_v \deg(v) \leq \Delta |V(S)|$).

Thus $\text{Survive}(S)$ implies $|K(v)| \geq \frac{2L}{\Delta}$ for any $v \in V(S)$, and the cluster tail bound gives the result. ∎

**Remark 2.2.4**: The exponential cluster tail holds in the **subcritical regime** of FK percolation. For transitive graphs, Duminil-Copin–Raoufi–Tassion prove exponential decay below the critical point.

---

### 2.3 Two-Stage FK-Håstad Restriction

**Definition 2.3.1 (Two-Stage FK-Håstad Restriction)**

The **two-stage FK-Håstad restriction** $\rho$ on variables $\{x_e\}_{e \in E}$ is:

1. Sample $\omega \sim \phi_{p,q}$
2. For each edge $e$:
   - If $\omega_e = 1$: set $x_e = *$ (variable remains alive/free)
   - If $\omega_e = 0$: set $x_e \in \{0,1\}$ uniformly at random (variable is fixed)

**Remark 2.3.2**: This differs from pure erasure (where dead variables are set to 0). The random assignment is essential for switching lemmas to apply.

---

## Part III: Circuit Complexity Foundations

### 3.1 AC⁰ and Switching Lemmas

**Definition 3.1.1 (AC⁰)**

AC$^0$ is the class of polynomial-size, constant-depth circuits with unbounded fan-in AND and OR gates.

**Theorem 3.1.2 (Håstad Switching Lemma)**

Let $F$ be a width-$w$ DNF (disjunction of conjunctions, each with at most $w$ literals). Let $R_p$ be the $p$-random restriction: each variable is kept alive (set to $*$) with probability $p$, otherwise fixed to a uniform random bit.

Then:
$$\Pr_{R_p}[\text{DTdepth}(F|_{R_p}) \geq t] \leq (5pw)^t$$

where DTdepth denotes deterministic decision tree depth.

*Proof*: This is Håstad's classical result. See Håstad (1986) or standard textbooks. ∎

**Theorem 3.1.3 (Rossman's Multi-Switching / Criticality)**

Let $C$ be a depth-$d$, size-$s$ AC$^0$ circuit. Under $p$-random restriction:
$$\Pr_{R_p}[\text{DTdepth}(C|_{R_p}) \geq D] \leq (p \cdot O(\log s)^{d-1})^D$$

*Proof*: This follows from iterating the switching lemma layer-by-layer through the circuit, with careful tracking of how width grows. See Rossman (2015) or Håstad (2014). ∎

---

### 3.2 Switching under FK (Transfer via Domination)

**Theorem 3.2.1 (Two-Stage FK Switching for All $q \geq 1$)**

Let $F$ be a width-$w$ DNF. Let $\rho$ be the two-stage FK-Håstad restriction driven by $\omega \sim \phi_{p,q}$ with $q \geq 1$.

Then:
$$\Pr_\rho[\text{DTdepth}(F|_\rho) \geq t] \leq (5pw)^t$$

*Proof*: 

Fix the random bits $r \in \{0,1\}^E$ assigned to dead edges. Define:
$$A_r = \{\omega : \text{DTdepth}(F|_{\rho(\omega, r)}) \geq t\}$$

**Claim**: $A_r$ is an increasing event in $\omega$.

*Proof of claim*: If $\omega \leq \omega'$ (componentwise), then more variables are alive under $\omega'$. The restriction $F|_{\rho(\omega, r)}$ fixes more variables than $F|_{\rho(\omega', r)}$, so:
$$\text{DTdepth}(F|_{\rho(\omega, r)}) \leq \text{DTdepth}(F|_{\rho(\omega', r)})$$
(Fixing variables can only decrease or maintain decision tree depth.) Thus $A_r$ is increasing. ∎

By the FK comparison inequality (Theorem 2.1.3):
$$\phi_{p,q}(A_r) \leq \phi_{p,1}(A_r)$$

The RHS is exactly the probability under i.i.d. Bernoulli($p$) that $\text{DTdepth}(F|_{\rho(\omega, r)}) \geq t$.

Averaging over the uniform random bits $r$:
$$\Pr_\rho[\text{DTdepth}(F|_\rho) \geq t] = \mathbb{E}_r[\phi_{p,q}(A_r)] \leq \mathbb{E}_r[\phi_{p,1}(A_r)] = \Pr_{R_p}[\text{DTdepth}(F|_{R_p}) \geq t]$$

By Håstad's switching lemma (Theorem 3.1.2), this is at most $(5pw)^t$. ∎

**Corollary 3.2.2 (AC⁰ Collapse under FK)**

Let $C$ be a depth-$d$, size-$s$ AC$^0$ circuit. Under two-stage FK-Håstad restriction with $\omega \sim \phi_{p,q}$ ($q \geq 1$):
$$\Pr_\rho[\text{DTdepth}(C|_\rho) \geq D] \leq (p \cdot O(\log s)^{d-1})^D$$

*Proof*: Same domination argument applied to Rossman's theorem (Theorem 3.1.3). ∎

---

### 3.3 AC⁰ Parity Correlation Bounds

**Theorem 3.3.1 (LMN/Tal Fourier Tail Bound)**

Let $f: \{0,1\}^n \to \{0,1\}$ be computed by a depth-$d$, size-$s$ AC$^0$ circuit. Then for the Fourier expansion $f(x) = \sum_{S \subseteq [n]} \hat{f}(S) \chi_S(x)$ where $\chi_S(x) = (-1)^{\oplus_{i \in S} x_i}$:

$$\sum_{|S| \geq k} \hat{f}(S)^2 \leq 2^{-\Omega(k / (\log s)^{d-1})}$$

*Proof*: This is the Linial-Mansour-Nisan theorem, sharpened by Tal. See Tal (2017). ∎

**Corollary 3.3.2 (Pointwise Fourier Coefficient Bound)**

For any $S$ with $|S| \geq L$ where $L = (c_d \cdot \log(s/\eta))^{c_d}$ for an appropriate constant $c_d$ depending on depth $d$:
$$|\hat{f}(S)| \leq \eta$$

*Proof*: Set the tail bound to $\eta^2$, so $|\hat{f}(S)|^2 \leq \sum_{|T| \geq |S|} \hat{f}(T)^2 \leq \eta^2$. ∎

**Corollary 3.3.3 (Parity Correlation Bound)**

Under the same conditions:
$$\left|\Pr[f(x) = \text{PARITY}_S(x)] - \frac{1}{2}\right| \leq \frac{\eta}{2}$$

*Proof*: The correlation with parity is $\frac{1}{2}|\hat{f}(S)|$. ∎

---

## Part IV: Information-Theoretic Analysis

### 4.1 The Erasure-or-Parity Decomposition

**Lemma 4.1.1 (Distribution-Free Parity Prediction Bound)**

Let $a \in \{0,1\}^E$ be uniform. Let $\omega \in \{0,1\}^E$ be any random mask **independent of $a$** (no assumptions on the distribution of $\omega$).

Fix a support set $S \subseteq E$ and define $\alpha = \bigoplus_{e \in S} a_e$.

Let $C$ be any circuit that takes input $(\omega, a \odot \omega)$ and outputs $\hat{\alpha} \in \{0,1\}$.

Then:
$$\Pr[\hat{\alpha} = \alpha] = \frac{1}{2} + \Pr[S \subseteq \omega] \cdot \left(\Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] - \frac{1}{2}\right)$$

Moreover:
$$\Pr[\hat{\alpha} = \alpha \mid S \not\subseteq \omega] = \frac{1}{2} \quad \text{exactly}$$

*Proof*: 

**Decomposition**: By the law of total probability:
$$\Pr[\hat{\alpha} = \alpha] = \Pr[S \subseteq \omega] \cdot \Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] + \Pr[S \not\subseteq \omega] \cdot \Pr[\hat{\alpha} = \alpha \mid S \not\subseteq \omega]$$

**Information-theoretic bound when $S \not\subseteq \omega$**: 

If $S \not\subseteq \omega$, there exists $e^* \in S$ with $\omega_{e^*} = 0$. The circuit's input $(\omega, a \odot \omega)$ does not include $a_{e^*}$ (it's masked to 0).

Since $a_{e^*}$ is uniform and independent of everything the circuit sees:
$$\alpha = a_{e^*} \oplus \left(\bigoplus_{e \in S \setminus \{e^*\}} a_e\right)$$

The second term is determined by revealed bits, but $a_{e^*}$ is uniform and independent, so $\alpha$ is uniform given the circuit's view.

Therefore $\Pr[\hat{\alpha} = \alpha \mid S \not\subseteq \omega] = \frac{1}{2}$.

Substituting back:
$$\Pr[\hat{\alpha} = \alpha] = \Pr[S \subseteq \omega] \cdot \Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] + \Pr[S \not\subseteq \omega] \cdot \frac{1}{2}$$
$$= \frac{1}{2} + \Pr[S \subseteq \omega] \cdot \left(\Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] - \frac{1}{2}\right)$$

∎

---

### 4.2 Cycle Rank and Information Leakage

**Definition 4.2.1 (Cycle Rank of Queried Subgraph)**

For edge set $Q \subseteq E$, let $V(Q)$ be the vertices incident to $Q$. The **cycle rank** of $Q$ is:
$$r(Q) = |Q| - |V(Q)| + \#\text{components}(Q)$$

This equals the dimension of the cycle space of the subgraph $(V(Q), Q)$.

**Lemma 4.2.2 (Cycle Rank Leakage Bound — Error-Free Model)**

Let $y = \delta h \oplus \text{Lift}(\alpha)$ where:
- $h \in \mathbb{F}_2^V$ is uniform (with $h(r) = 0$ for a fixed root $r$)
- $\alpha \in \mathbb{F}_2^{\beta_1}$ is uniform
- $\text{Lift}(\alpha)$ is the canonical lift to $\mathbb{F}_2^E$

For any queried set $Q \subseteq E$:
$$I(\alpha; y|_Q) \leq r(Q)$$

Moreover, the view $y|_Q$ reveals exactly $r(Q)$ independent linear functionals of $\alpha$.

*Proof*: 

The view is $y|_Q = (\delta h)|_Q \oplus \text{Lift}(\alpha)|_Q$.

For uniform $h$, the term $(\delta h)|_Q$ is uniform over the **cut space** of the subgraph $(V(Q), Q)$, which has dimension $|V(Q)| - \#\text{components}(Q)$.

The quotient $\mathbb{F}_2^Q / \text{cut space}$ has dimension:
$$|Q| - (|V(Q)| - \#\text{components}(Q)) = r(Q)$$

This quotient is isomorphic to the cycle space of $(V(Q), Q)$, which captures exactly $r(Q)$ independent linear functionals of $\alpha$ (the cycle parities). ∎

**Corollary 4.2.3 (Forest Queries Reveal Nothing)**

If $Q$ is a forest (acyclic), then $r(Q) = 0$, so $I(\alpha; y|_Q) = 0$. The view $y|_Q$ is uniform and independent of $\alpha$.

*Proof*: A forest on $k$ vertices with $\ell$ edges and $c$ components satisfies $\ell = k - c$, so $r(Q) = \ell - k + c = 0$. ∎

**Lemma 4.2.4 (Exact Characterization)**

A specific holonomy bit $\alpha_i = \langle c_i, a \rangle$ is determined by the view $y|_Q$ if and only if $c_i$ lies in the row-span of the cycle constraints from $Q$.

If $r(Q) = 0$ (forest), no holonomy bit is determined.

---

### 4.3 Cycle Hunting (Avoiding Cycles in Queries)

**Lemma 4.3.1 (Short Cycles in Alive Subgraph)**

Let $\Gamma$ be $d$-regular with girth $g$. Let $\omega \in \{0,1\}^E$ be a random edge subset (either i.i.d. Bernoulli($p$) or $\phi_{p,q}$ with $q \geq 1$).

Let $T$ be any decision tree (possibly adaptive) that queries at most $D$ edges from $\omega$.

Then:
$$\Pr[\text{queried subgraph contains a cycle}] \leq \Pr[\omega \text{ contains a cycle of length } \leq D]$$

For i.i.d. Bernoulli($p$), if $(d-1)p < 1$:
$$\Pr[\omega \text{ contains cycle of length } \leq D] \leq n \cdot \frac{((d-1)p)^g}{1 - (d-1)p}$$

For FK with $q \geq 1$, the same bound holds by stochastic domination.

*Proof*: 

If the queried subgraph $Q \subseteq \omega$ contains a cycle, then $\omega$ contains that cycle, which has length $\leq |Q| \leq D$. But all cycles in $\Gamma$ have length $\geq g$, so this requires $D \geq g$.

For the probability bound, the number of simple $\ell$-cycles in a $d$-regular graph is at most $N_\ell \leq \frac{n(d-1)^\ell}{2\ell}$ (count closed walks and correct for overcounting).

$$\Pr[\text{cycle of length } \leq D \text{ exists in } \omega] \leq \sum_{\ell=g}^{D} N_\ell \cdot p^\ell \leq \sum_{\ell=g}^{D} \frac{n(d-1)^\ell p^\ell}{2\ell}$$

For $(d-1)p < 1$, this geometric sum is bounded by $n \cdot \frac{((d-1)p)^g}{1-(d-1)p}$.

For FK, "contains a cycle of length $\leq D$" is an increasing event, so domination (Theorem 2.1.3) applies. ∎

**Corollary 4.3.2 (High-Girth Simplification)**

If $D < g$, then no set of $\leq D$ edges can contain a cycle (deterministically). In this regime, any depth-$D$ decision tree queries a forest with probability 1.

---

### 4.4 Noisy Model (Sparse Errors)

**Definition 4.4.1 (Sparse Error Model)**

In the **sparse error model**:
$$y = \delta h \oplus \text{Lift}(\alpha) \oplus e$$

where:
- $h \in \mathbb{F}_2^V$ is uniform
- $\alpha \in \mathbb{F}_2^{\beta_1}$ is uniform
- $e \in \mathbb{F}_2^E$ has i.i.d. entries with $\Pr[e_f = 1] = \epsilon$
- $e$ is independent of $\alpha$ and $h$

**Lemma 4.4.2 (Information Bound with Errors)**

Under the sparse error model, for any queried set $Q$:
$$I(\alpha; y|_Q) \leq r(Q) \cdot (1 - H(\epsilon))$$

where $H(\epsilon) = -\epsilon \log \epsilon - (1-\epsilon)\log(1-\epsilon)$ is binary entropy.

*Proof*: 

Let $W \in \mathbb{F}_2^{r(Q)}$ be the quotient information (the $r(Q)$ cycle-space coordinates revealed by $y|_Q$). In the noisy model:
$$W = U \oplus N$$

where $U \in \mathbb{F}_2^{r(Q)}$ is a uniform linear image of $\alpha$, and $N$ is the corresponding noise vector (a linear image of $e|_Q$).

Since $U$ is uniform and independent of $N$:
$$I(\alpha; y|_Q) = I(U; U \oplus N) = H(U) - H(U \mid U \oplus N) = r(Q) - H(N)$$

**Bounding $H(N)$ from below**: 

Choose a spanning forest $F$ of $(V(Q), Q)$. Each chord $f_i \in Q \setminus F$ (there are exactly $r(Q)$ of them) defines a fundamental cycle $c_i \subseteq Q$. Use these as the cycle basis.

Each noise bit is:
$$N_i = \langle c_i, e \rangle = e_{f_i} \oplus g_i(e_{\text{tree edges}})$$

The chord errors $\{e_{f_i}\}$ are i.i.d. Bernoulli($\epsilon$), and each $e_{f_i}$ appears in exactly one $N_i$.

By chain rule:
$$H(N) = \sum_i H(N_i \mid N_1, \ldots, N_{i-1})$$

For each $i$:
$$H(N_i \mid N_1, \ldots, N_{i-1}) \geq H(N_i \mid e_{\text{all edges except } f_i}) = H(e_{f_i}) = H(\epsilon)$$

(Conditioning on all edges except $f_i$ determines $g_i$, leaving $N_i = e_{f_i} \oplus \text{const}$, which has entropy $H(\epsilon)$.)

Summing: $H(N) \geq r(Q) \cdot H(\epsilon)$.

Therefore:
$$I(\alpha; y|_Q) = r(Q) - H(N) \leq r(Q) - r(Q) \cdot H(\epsilon) = r(Q) \cdot (1 - H(\epsilon))$$

∎

---

## Part V: Main Theorems

### 5.1 Distribution-Free Parity Prediction

**Theorem 5.1.1 (AC⁰ Parity Prediction Bound — Distribution-Free)**

Let $a \in \{0,1\}^E$ be uniform. Let $\omega \in \{0,1\}^E$ be any random mask independent of $a$.

Fix support $S \subseteq E$ with $|S| = L$. Define $\alpha = \bigoplus_{e \in S} a_e$.

Let $C$ be a depth-$d$, size-$s$ AC$^0$ circuit outputting $\hat{\alpha}$ from $(\omega, a \odot \omega)$.

If $L \geq (c_d \cdot \log(s/\eta))^{c_d}$ for the appropriate constant $c_d$, then:
$$\Pr[\hat{\alpha} = \alpha] \leq \frac{1}{2} + \Pr[S \subseteq \omega] \cdot \frac{\eta}{2}$$

*Proof*: 

By Lemma 4.1.1:
$$\Pr[\hat{\alpha} = \alpha] = \frac{1}{2} + \Pr[S \subseteq \omega] \cdot \left(\Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] - \frac{1}{2}\right)$$

It remains to bound $\Pr[\hat{\alpha} = \alpha \mid S \subseteq \omega] - \frac{1}{2}$.

Condition on any fixed $\omega$ with $S \subseteq \omega$. Also fix the revealed bits $a_e$ for $e \in \omega \setminus S$.

The remaining function $f: \{0,1\}^S \to \{0,1\}$ (computing $\hat{\alpha}$ from $\{a_e : e \in S\}$) is computed by a depth-$d$, size-$\leq s$ circuit (AC$^0$ is closed under fixing inputs).

By Corollary 3.3.3, since $|S| = L$ exceeds the threshold:
$$\Pr[f(a_S) = \text{PARITY}_S(a_S)] - \frac{1}{2} \leq \frac{\eta}{2}$$

This holds for every fixed $\omega$ with $S \subseteq \omega$, so it holds in expectation. ∎

---

### 5.2 Holonomy Hardness on High-Girth Expanders

**Theorem 5.2.1 (AC⁰ Holonomy-Bit Hardness — Main Result)**

Let $\Gamma$ be a $d$-regular expander with:
- Girth $g = \Theta(\log n)$
- $n$ vertices, $m = \Theta(n)$ edges
- Cycle rank $\beta_1 = \Theta(n)$

Let $\mathcal{C} = \{C_e : e \in E \setminus T\}$ be the fundamental cycle code (from any spanning tree $T$). Each $C_e$ is connected with $|C_e| \geq g$.

Let $a \in \{0,1\}^E$ be uniform. Let $\rho$ be the two-stage FK-Håstad restriction with:
- $\omega \sim \phi_{p,q}$ for any $q \geq 1$
- $p = 1/(\log n)^k$ where $k > d - 1$ (sufficiently large depending on depth $d$)
- Dead edges assigned uniform random bits

For any depth-$d$, size-$s = \text{poly}(n)$ AC$^0$ circuit $C$ predicting holonomy bit $\alpha_i = \langle C_{e_i}, a \rangle$:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + o(1)$$

*Proof*: 

**Step 1 (Circuit Collapse)**:

By Corollary 3.2.2, under two-stage FK restriction:
$$\Pr_\rho[\text{DTdepth}(C|_\rho) \geq D] \leq (p \cdot O(\log s)^{d-1})^D$$

For $p = 1/(\log n)^k$ with $k > d-1$ and $\log s = O(\log n)$:
$$p \cdot O(\log s)^{d-1} = O((\log n)^{d-1-k}) = o(1)$$

Choose $D = c \log n$ where $c$ is small enough that $D < g$ (possible since $g = \Theta(\log n)$).

Then the failure probability is $(o(1))^{c \log n} = n^{-\omega(1)}$.

With probability $1 - n^{-\omega(1)}$, the restricted circuit $C|_\rho$ is a decision tree of depth $< g$.

**Step 2 (Acyclicity)**:

Since $\Gamma$ has girth $g$ and the decision tree queries at most $D < g$ edges, the queried subgraph $Q$ is acyclic (deterministically).

No probabilistic cycle-hunting argument is needed.

**Step 3 (Perfect Information-Theoretic Hiding)**:

By Corollary 4.2.3, since $Q$ is a forest:
$$r(Q) = 0 \implies I(\alpha; y|_Q) = 0$$

The decision tree's view is independent of all holonomy bits, including $\alpha_i$.

**Step 4 (Conclusion)**:

- With probability $1 - n^{-\omega(1)}$: the circuit collapses to a depth-$< g$ decision tree, which has **exactly zero** advantage on $\alpha_i$.
- With probability $n^{-\omega(1)}$: the circuit might have advantage up to $1/2$.

Total advantage:
$$\Pr[\hat{\alpha}_i = \alpha_i] - \frac{1}{2} \leq 0 \cdot (1 - n^{-\omega(1)}) + \frac{1}{2} \cdot n^{-\omega(1)} = n^{-\omega(1)} = o(1)$$

∎

---

### 5.3 Alternative: Using Distribution-Free Bound Directly

**Theorem 5.3.1 (Alternative Proof via Distribution-Free Bound)**

Under the same setup as Theorem 5.2.1, but without requiring $D < g$:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + \phi_{p,q}(\text{Survive}(C_{e_i})) \cdot \frac{\eta}{2}$$

where $\eta = n^{-\omega(1)}$ for $|C_{e_i}| \geq g = \Theta(\log n)$ above the AC$^0$ threshold.

If $C_{e_i}$ is connected, H2 (Lemma 2.2.3) gives:
$$\phi_{p,q}(\text{Survive}(C_{e_i})) \leq e^{-\Omega(g)} = n^{-\Omega(1)}$$

Therefore:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + n^{-\Omega(1)} \cdot n^{-\omega(1)} = \frac{1}{2} + o(1)$$

*Proof*: Direct application of Theorem 5.1.1 with $S = C_{e_i}$ and H2. ∎

**Remark 5.3.2**: This alternative doesn't require the $D < g$ parameter alignment, but gives a slightly weaker (though still $o(1)$) bound.

---

## Part VI: Extensions

### 6.1 Multiple Holonomy Bits

**Corollary 6.1.1 (Hardness for All Holonomy Bits Simultaneously)**

Under the setup of Theorem 5.2.1, for any circuit attempting to predict **any** of the $\beta_1 = \Theta(n)$ holonomy bits $\{\alpha_i\}$:
$$\max_i \left(\Pr[\hat{\alpha}_i = \alpha_i] - \frac{1}{2}\right) = o(1)$$

*Proof*: The proof of Theorem 5.2.1 shows that when the circuit collapses to a depth-$< g$ decision tree (which happens w.h.p.), **all** holonomy bits are perfectly hidden (since $r(Q) = 0$ for the forest $Q$). ∎

---

### 6.2 Sparse Error Model

**Theorem 6.2.1 (Hardness with Sparse Errors)**

Under the sparse error model (Definition 4.4.1) with $\epsilon = o(1)$, and the same circuit/graph setup as Theorem 5.2.1:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + o(1)$$

*Proof sketch*: 

When the circuit collapses to a depth-$D$ decision tree (w.h.p.), by Lemma 4.4.2:
$$I(\alpha; y|_Q) \leq r(Q) \cdot (1 - H(\epsilon))$$

If $Q$ is a forest ($D < g$): $r(Q) = 0$, so $I(\alpha; y|_Q) = 0$ and perfect hiding holds.

If $Q$ has small cycle rank ($r(Q) \leq D$): the information leaked is at most $D \cdot (1 - H(\epsilon)) = O(\log n)$ bits.

By Fano's inequality, predicting any single bit $\alpha_i$ from $O(\log n)$ bits of information about the $\beta_1 = \Theta(n)$-dimensional $\alpha$ gives advantage at most $O(\sqrt{\log n / n}) = o(1)$. ∎

---

## Part VII: Summary of Logical Dependencies

```
Lemma 1.2.2 (Fundamental Cycle Basis)
    ↓
Lemma 1.3.2 (High-Girth Holonomy Code)
    ↓
    ├── Each basis vector is connected, size ≥ g
    └── All codewords have component ≥ g

Theorem 2.1.3 (FK Comparison)
    ↓
Theorem 3.2.1 (FK Switching)
    ↓
Corollary 3.2.2 (AC⁰ Collapse under FK)

Theorem 3.3.1 (LMN/Tal Fourier Bound)
    ↓
Corollary 3.3.3 (Parity Correlation Bound)

Lemma 4.1.1 (Erasure-or-Parity)
    +
Corollary 3.3.3 (Parity Correlation)
    ↓
Theorem 5.1.1 (Distribution-Free Bound)

Lemma 4.2.2 (Cycle Rank Leakage)
    ↓
Corollary 4.2.3 (Forest = Perfect Hiding)

Corollary 3.2.2 (AC⁰ Collapse)
    +
Corollary 4.2.3 (Forest Hiding)
    +
Girth condition (D < g)
    ↓
Theorem 5.2.1 (Main Result)
```

---

## Part VIII: Concrete Parameters

**Example Instantiation**:

- Graph: Lubotzky-Phillips-Sarnak Ramanujan graph
  - $n$ vertices, degree $d = p + 1$ for prime $p$
  - Girth $g \geq \frac{4}{3} \log_p n$
  - Spectral gap $\lambda \leq 2\sqrt{p}$

- Parameters:
  - $g = \Theta(\log n)$
  - $\beta_1 = \Theta(n)$
  - $p_{\text{FK}} = 1/(\log n)^{d}$ where $d$ is circuit depth
  - $D = \frac{1}{2} g$ (collapse depth, chosen $< g$)

- Circuit class: depth-$d$ AC$^0$, size $s = n^{O(1)}$

- Result: Any such circuit predicting any holonomy bit has advantage $\leq n^{-\omega(1)}$.

### Lemma 9.2.6 (Coordinate Splitting)

After a fixed change of basis on $\alpha$, we can write $\alpha = (\alpha_F, \alpha_{\text{rest}})$ where:
- $\alpha_F \in \mathbb{F}_2^{r(F)}$ are the coordinates that contribute to cycle parities on $F$
- $\alpha_{\text{rest}} \in \mathbb{F}_2^{\beta_1 - r(F)}$ are the remaining coordinates

Then:
$$s_F = \alpha_F \oplus n_F$$

where $n_F := M_F e_F$ is the **noise syndrome**.

*Proof*: We must show the map $\alpha \mapsto M_F(L\alpha)_F$ has rank $r(F)$.

- $L$ is surjective onto $\mathcal{Z} = \ker(B)$.
- The rows of $M_F$ are cycles supported in $F$, hence elements of $\mathcal{Z}$.
- The dot-product pairing on $\mathcal{Z}$ is nondegenerate because $\mathcal{Z} \cap \mathcal{Z}^\perp = \mathcal{Z} \cap \text{im}(B^\top) = \{0\}$ for a connected graph. (Dimension count: $\dim \mathcal{Z} + \dim \text{im}(B^\top) = (m-n+1) + (n-1) = m$.)
- Therefore the $r(F)$ independent cycle rows define $r(F)$ independent linear functionals on $\mathcal{Z}$, so the map has rank $r(F)$.

Choose basis for $\mathbb{F}_2^{\beta_1}$ so the first $r(F)$ coordinates align with this map. ∎

---

### Theorem 9.3.6 (Posterior Support Size — Corrected Statement)

**Clarification**: "Consistent with observation $y_F$" means: there exists an extension of the unobserved coordinates $y_{E \setminus F}$ and a witness $(h, \alpha, e)$ with $|e|_0 \leq k$ such that $y = \delta h \oplus L\alpha \oplus e$ and the restriction to $F$ matches the observation.

Equivalently, we count:
$$\{\alpha : \exists h, e, |e|_0 \leq k, (\delta h \oplus L\alpha \oplus e)_F = y_F\}$$

**Theorem**: This set has cardinality $2^{\beta_1 - r(F)} \cdot |\mathcal{N}_k(F)|$.

*Proof*: (Unchanged from before.) ∎

---

### Lemma 9.3.8(2) (Corrected)

**Original**: "If $k < d_{\min}(M_F)/2$ where $d_{\min}$ is the minimum distance of the code with parity-check $M_F$..."

**Corrected**: If $k < d_{\min}(\mathcal{C}_F)/2$ where $\mathcal{C}_F := \ker(M_F) \subseteq \mathbb{F}_2^F$ is the **kernel code** (which equals the cut space of $(V(F), F)$), then all error vectors of weight $\leq k$ produce distinct syndromes.

Hence $|\mathcal{N}_k(F)| = \sum_{i=0}^{k} \binom{|F|}{i}$.

*Proof*: Standard unique decoding radius argument. If $e, e'$ have weight $\leq k$ and $M_F e = M_F e'$, then $e - e' \in \ker(M_F)$ has weight $\leq 2k < d_{\min}(\mathcal{C}_F)$, so $e = e'$. ∎

---

### Definition 9.3.9 and Theorem 9.3.10 (Corrected and Clarified)

**Definition 9.3.9 (Syndrome Partition Function)**

For each syndrome $u \in \mathbb{F}_2^{r(F)}$:
$$W_F(u) := \sum_{e_F : M_F e_F = u} \lambda^{|e_F|_0}$$

The total partition function is:
$$Z_F := \sum_{u \in \mathbb{F}_2^{r(F)}} W_F(u) = \sum_{e_F \in \{0,1\}^F} \lambda^{|e_F|_0} = (1 + \lambda)^{|F|}$$

**Clarification**: $Z_F = (1+\lambda)^{|F|}$ because summing over all syndromes $u$ removes the constraint $M_F e_F = u$, collapsing to the full product partition function. However, $W_F(u)$ itself depends nontrivially on $M_F$ and is **not** uniform over $u$ in general.

**Theorem 9.3.10 (Gibbs Posterior — Corrected)**

The induced distribution on the noise syndrome $n_F = M_F e_F$ is:
$$P(n_F = u) = \frac{W_F(u)}{Z_F}$$

Given observation $s_F$, the posterior on $\alpha_F$ is:
$$P(\alpha_F = a \mid s_F) = \frac{W_F(s_F \oplus a)}{\sum_{a'} W_F(s_F \oplus a')} = \frac{W_F(s_F \oplus a)}{Z_F}$$

(The denominator equals $Z_F$ because summing over $a'$ is equivalent to summing over all syndromes.)

The posterior entropy is:
$$H(\alpha_F \mid s_F) = H(n_F) = -\sum_u \frac{W_F(u)}{Z_F} \log_2 \frac{W_F(u)}{Z_F}$$

*Proof*: Since $\alpha_F$ is uniform and independent of $n_F$, and $s_F = \alpha_F \oplus n_F$, the conditional distribution of $\alpha_F$ given $s_F$ equals the distribution of $n_F$ shifted by $s_F$. The entropy is preserved under translation. ∎

---

### Theorem 9.5.1 (Corrected Hypothesis)

**Theorem 9.5.1 (AC$^0$ Hardness for Sparse-Error Holonomy Decoding)**

Let $\Gamma$ be a $d$-regular expander with girth $g = \Theta(\log n)$ and cycle rank $\beta_1 = \Theta(n)$.

Consider the sparse-error holonomy decoding problem with instance $y = \delta h \oplus L\alpha \oplus e$ where:
- $h \in \mathbb{F}_2^V$ is uniform
- $\alpha \in \mathbb{F}_2^{\beta_1}$ is uniform
- $e \in \mathbb{F}_2^E$ is sampled from **any distribution supported on $\{e : |e|_0 \leq k\}$ that is independent of $\alpha$**

Let $\rho$ be the two-stage FK-Håstad restriction with $p = 1/(\log n)^{O(d)}$.

For any depth-$d$, size-$s = \text{poly}(n)$ AC$^0$ circuit $C$ attempting to predict any holonomy bit $\alpha_i$:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + o(1)$$

*Proof*:

**Step 1**: By Corollary 3.2.2 (AC$^0$ collapse under FK), with probability $1 - n^{-\omega(1)}$, the circuit collapses to a decision tree of depth $D < g$.

**Step 2**: The queried set $F$ satisfies $|F| < g$, so $F$ is acyclic and $r(F) = 0$.

**Step 3**: When $r(F) = 0$, there is no cycle-syndrome channel. The observation $y_F = (\delta h)_F \oplus (L\alpha)_F \oplus e_F$ satisfies:
- $(\delta h)_F$ is uniform over the cut space of $F$ (determined by $h$)
- $(L\alpha)_F$ restricted to a forest lies entirely in the cut space (no cycle component)
- $e_F$ is independent of $\alpha$

Since $F$ is a forest, $(L\alpha)_F \in \text{im}(B_F^\top)$ (all cycle-space vectors restrict to cuts on forests). Therefore $y_F = (\delta h')_F \oplus e_F$ for some effective $h'$, which is independent of $\alpha$.

**Step 4**: Since $y_F$ is independent of $\alpha$ when $r(F) = 0$:
$$\Pr[\hat{\alpha}_i = \alpha_i \mid F \text{ acyclic}] = \frac{1}{2}$$

**Step 5**: Total advantage:
$$\Pr[\hat{\alpha}_i = \alpha_i] - \frac{1}{2} \leq 0 \cdot (1 - n^{-\omega(1)}) + \frac{1}{2} \cdot n^{-\omega(1)} = o(1)$$

---

## Boxed Summary of Uncertainty Functionals

**Definition (Uncertainty Functionals)**

For queried edge set $F \subseteq E$ with cycle rank $r(F)$:

$$\boxed{U_{\text{ent}}(F) := H(\alpha \mid y_F) = \beta_1 - r(F) + H(n_F)}$$

where $n_F = M_F e_F$ is the noise syndrome (entropy depends on error model).

$$\boxed{U_{\text{supp}}(F) := \log_2|\{\alpha : \exists h, e, |e| \leq k, (\delta h \oplus L\alpha \oplus e)_F = y_F\}|}$$
$$= \beta_1 - r(F) + \log_2|\mathcal{N}_k(F)|$$

$$\boxed{U_{\text{gibbs}}(F) := \beta_1 - r(F) + H_{W_F}(n_F)}$$

where $H_{W_F}$ is entropy under the Gibbs-weighted syndrome distribution.

**Key Property**: All functionals have the form:
$$U(F) = (\text{free dimensions: } \beta_1 - r(F)) + (\text{noise contribution})$$

**When $r(F) = 0$** (forest queries): All functionals achieve maximum $U(F) = \beta_1$, giving perfect hiding regardless of error model.

---

# Part X: Explicit Parameter Selection and High-Girth Expander Families

## 10.1 Explicit Collapse Inequality

### Theorem 10.1.1 (AC$^0$ Collapse — Explicit Parameters)

Let $C$ be a depth-$d$, size-$s$ AC$^0$ circuit on $m$ Boolean variables. Let $\rho$ be a two-stage restriction where each variable is alive with probability $p$ (independently), and dead variables are assigned uniform random bits.

Then:
$$\Pr_\rho[\text{DTdepth}(C|_\rho) \geq D] \leq s \cdot (Kp(\log s)^{d-1})^{D/d}$$

where $K > 0$ is an absolute constant (independent of $d, s, p, D$).

*Proof sketch*: This follows from iterating Håstad's switching lemma through $d$ layers.

**Layer-by-layer analysis**:

At depth 1 (bottom gates): Each gate computes a DNF or CNF of width at most $w_1$ (the fan-in). By Håstad's switching lemma, with probability $\geq 1 - (5pw_1)^t$, this gate becomes a decision tree of depth $t$.

At depth $i$: After restriction, inputs to depth-$i$ gates are decision trees of depth $\leq T_{i-1}$. A width-$w_i$ DNF/CNF of such inputs behaves like a width-$(w_i \cdot T_{i-1})$ formula on the original variables.

**Telescoping**: Setting $t_i = D/d$ at each layer and tracking the effective width growth:

The probability that any gate at layer $i$ fails to simplify is at most:
$$(\text{number of gates at layer } i) \times (5p \cdot w_{\text{eff}})^{D/d}$$

For a size-$s$ circuit with bounded fan-in $w \leq \log s$ (WLOG by standard rebalancing), the effective width after $i$ layers is at most $(\log s)^{i}$.

Union bounding over all gates in all layers:
$$\Pr[\text{failure}] \leq s \cdot (5p(\log s)^{d-1})^{D/d}$$

Taking $K = 5$ works. ∎

**Corollary 10.1.2 (Collapse Threshold)**

For the collapse probability to be at most $\delta$, it suffices to have:
$$D \geq d \cdot \frac{\log(s/\delta)}{\log(1/(Kp(\log s)^{d-1}))}$$

Equivalently, if we want collapse to depth $D$ with probability $\geq 1 - \delta$:
$$p \leq \frac{1}{K(\log s)^{d-1}} \cdot \left(\frac{\delta}{s}\right)^{d/D}$$

---

### Theorem 10.1.3 (FK Transfer — Explicit)

Let $\rho$ be the two-stage FK-Håstad restriction with $\omega \sim \phi_{p,q}$ for any $q \geq 1$.

The same bound holds:
$$\Pr_\rho[\text{DTdepth}(C|_\rho) \geq D] \leq s \cdot (Kp(\log s)^{d-1})^{D/d}$$

*Proof*: By stochastic domination (Theorem 2.1.3), $\phi_{p,q} \leq_{\text{st}} \phi_{p,1}$ for increasing events. The event "DTdepth $\geq D$" is increasing in the alive set (more alive variables can only increase decision tree depth). ∎

---

## 10.2 Parameter Constraints for Perfect Hiding

We need three constraints to align:

1. **Collapse**: $\Pr[\text{DTdepth}(C|_\rho) \geq D] \leq n^{-\omega(1)}$
2. **Acyclicity**: $D < g$ (girth of the graph)
3. **Polynomial size**: $s = n^{O(1)}$

### Lemma 10.2.1 (Parameter Feasibility)

Let $\Gamma$ be a graph with girth $g = c_g \log n$ for constant $c_g > 0$.

Let $C$ be a depth-$d$, size-$s = n^a$ circuit for constant $a > 0$.

Set:
$$p = \frac{1}{K(\log n)^{d-1} \cdot n^{\epsilon}}$$

for any constant $\epsilon > 0$.

Then for:
$$D = \frac{c_g}{2} \log n$$

we have:
1. $D < g$ ✓
2. $\Pr[\text{DTdepth}(C|_\rho) \geq D] \leq n^{-\omega(1)}$ ✓

*Proof*:

**Constraint 1** (acyclicity): $D = \frac{c_g}{2} \log n < c_g \log n = g$. ✓

**Constraint 2** (collapse probability):

$$\Pr[\text{failure}] \leq s \cdot (Kp(\log s)^{d-1})^{D/d}$$

With $s = n^a$ and $\log s = a \log n$:

$$Kp(\log s)^{d-1} = K \cdot \frac{1}{K(\log n)^{d-1} n^{\epsilon}} \cdot (a \log n)^{d-1} = \frac{a^{d-1}}{n^{\epsilon}}$$

So:
$$\Pr[\text{failure}] \leq n^a \cdot \left(\frac{a^{d-1}}{n^{\epsilon}}\right)^{D/d} = n^a \cdot \left(\frac{a^{d-1}}{n^{\epsilon}}\right)^{c_g \log n / (2d)}$$

$$= n^a \cdot \exp\left(-\frac{c_g \epsilon \log n}{2d} \cdot \log n + O(\log \log n \cdot \log n)\right)$$

$$= n^a \cdot n^{-c_g \epsilon (\log n) / (2d) + o(\log n)}$$

For $\log n \to \infty$, the exponent goes to $-\infty$, so:
$$\Pr[\text{failure}] \leq n^{-\omega(1)}$$

---

## 10.3 High-Girth Expander Families

We need explicit families of bounded-degree graphs with:
- Girth $g = \Omega(\log n)$
- Good expansion (for the H2 survival bounds)
- Cycle rank $\beta_1 = \Theta(n)$

### 10.3.1 Lubotzky-Phillips-Sarnak (LPS) Ramanujan Graphs

**Construction**: For primes $p, q$ with $p, q \equiv 1 \pmod 4$ and $\left(\frac{p}{q}\right) = 1$ (Legendre symbol), the LPS graph $X^{p,q}$ is a $(p+1)$-regular graph on $n = q(q^2-1)/2$ or $q(q^2-1)$ vertices (depending on variant).

**Properties**:
- **Degree**: $d = p + 1$ (constant for fixed $p$)
- **Girth**: $g \geq \frac{4}{3} \log_p n = \frac{4}{3} \cdot \frac{\log n}{\log p}$
- **Spectral gap**: Second eigenvalue $\lambda_2 \leq 2\sqrt{p}$ (Ramanujan bound)
- **Expansion**: Edge expansion $h \geq \frac{(p+1) - 2\sqrt{p}}{2} = \frac{(\sqrt{p}-1)^2}{2}$

**Cycle rank**: $\beta_1 = m - n + 1 = \frac{(p+1)n}{2} - n + 1 = \frac{(p-1)n}{2} + 1 = \Theta(n)$

**Girth constant**: For $p = 5$ (so $d = 6$):
$$g \geq \frac{4}{3} \cdot \frac{\log n}{\log 5} \approx 0.83 \log n$$

So $c_g \approx 0.83$ for 6-regular LPS graphs.

---

### 10.3.2 Margulis-Gabber-Galil Graphs

**Construction**: Vertices are $\mathbb{Z}_n \times \mathbb{Z}_n$. Each vertex $(x, y)$ connects to:
$$(x \pm 1, y), (x, y \pm 1), (x \pm y, y), (x, y \pm x)$$

(8-regular after removing self-loops and multi-edges, or variants give different degrees)

**Properties**:
- **Degree**: $d = 8$ (or variants)
- **Girth**: $g = \Omega(\log n)$ (explicit constant depends on variant)
- **Expansion**: Explicit spectral gap

**Advantage**: Very explicit, easy to implement.

**Disadvantage**: Girth constant is smaller than LPS.

---

### 10.3.3 Random Regular Graphs (Non-Explicit but Optimal)

**Construction**: Uniformly random $d$-regular graph on $n$ vertices.

**Properties** (with high probability):
- **Girth**: $g \geq (1 - o(1)) \log_{d-1} n$
- **Expansion**: Near-optimal (close to Ramanujan bound)
- **Cycle rank**: $\beta_1 = \frac{(d-2)n}{2} + 1$

**Girth constant**: For $d = 10$:
$$g \geq (1 - o(1)) \frac{\log n}{\log 9} \approx 0.48 \log n$$

**Advantage**: Can achieve girth arbitrarily close to the Moore bound.

**Disadvantage**: Non-explicit (need derandomization for uniform circuits).

---

### 10.3.4 Explicit Constructions with Large Girth Constant

**Lazebnik-Ustimenko Graphs**: Algebraic constructions achieving $g \geq c \log n$ with explicit constants approaching the Moore bound.

**Cayley Graphs of $\text{PSL}(2, \mathbb{F}_q)$**: With carefully chosen generators, achieve large girth and good expansion.

---

## 10.4 Complete Parameter Selection

### Theorem 10.4.1 (Explicit Instantiation)

Let $\Gamma = X^{5,q}$ be the LPS Ramanujan graph with:
- $n = q(q^2-1)/2$ vertices (for prime $q \equiv 1 \pmod 4$ with $\left(\frac{5}{q}\right) = 1$)
- Degree $d_{\text{graph}} = 6$
- Girth $g \geq 0.8 \log n$
- Cycle rank $\beta_1 = 2n + 1$

Let $C$ be a depth-$d_{\text{circuit}}$, size-$s = n^a$ AC$^0$ circuit.

Set parameters:
- $p = \frac{1}{10 (\log n)^{d_{\text{circuit}}-1} \cdot n^{0.01}}$
- $q_{\text{FK}} \geq 1$ (any value)
- $D = 0.3 \log n$ (collapse depth target)

Then:
1. **Collapse**: With probability $\geq 1 - n^{-\omega(1)}$, $C|_\rho$ is a decision tree of depth $< D$
2. **Acyclicity**: $D = 0.3 \log n < 0.8 \log n \leq g$, so all queries form a forest
3. **Perfect hiding**: When queries form a forest, $I(\alpha; y_F) = 0$

**Conclusion**: For any fixed holonomy bit $\alpha_i$:
$$\Pr[\hat{\alpha}_i = \alpha_i] \leq \frac{1}{2} + n^{-\omega(1)}$$

---

## 10.5 The Locked NP-Verifiable Theorem

### Theorem 10.5.1 (Final Form — Fully Explicit)

**Graph family**: LPS Ramanujan graphs $\Gamma_n = X^{5, q_n}$ with $n \to \infty$ vertices.

**Problem**: Sparse-error holonomy decoding
- Instance: $(y, k)$ with $y \in \mathbb{F}_2^E$, $k = O(n^{1-\epsilon})$
- Witness: $(h, \alpha, e)$ with $y = \delta h \oplus L\alpha \oplus e$ and $|e|_0 \leq k$

**Hardness**:

For any:
- Circuit depth $d = O(1)$
- Circuit size $s = n^{O(1)}$
- Error distribution independent of $\alpha$ with $|e|_0 \leq k$

Under two-stage FK-Håstad restriction with $p = n^{-\Omega(1)}$ and any $q \geq 1$:

$$\Pr[\text{AC}^0 \text{ circuit correctly predicts any } \alpha_i] \leq \frac{1}{2} + n^{-\omega(1)}$$

**Proof**: Combine:
1. Theorem 10.1.3 (explicit collapse bound)
2. Lemma 10.2.1 (parameter feasibility with $c_g = 0.8$, $D = 0.3 \log n$)
3. Theorem 9.4.1 (perfect hiding when $r(F) = 0$)

∎

---

## 10.6 Summary Table

| Parameter | Value | Constraint Satisfied |
|-----------|-------|---------------------|
| Graph family | LPS $X^{5,q}$ | Explicit, bounded degree |
| Degree $d_{\text{graph}}$ | 6 | Constant |
| Girth $g$ | $\geq 0.8 \log n$ | High girth |
| Cycle rank $\beta_1$ | $2n + 1$ | $\Theta(n)$ holonomy bits |
| Circuit depth $d_{\text{circuit}}$ | $O(1)$ | AC$^0$ |
| Circuit size $s$ | $n^{O(1)}$ | Polynomial |
| FK parameter $p$ | $n^{-\Omega(1)}$ | Subcritical |
| FK parameter $q$ | $\geq 1$ | Any (domination works) |
| Collapse depth $D$ | $0.3 \log n$ | $D < g$ |
| Failure probability | $n^{-\omega(1)}$ | Negligible |

---

## 10.7 What This Achieves and What Remains

### Achieved

✓ **Explicit construction**: Fully specified graph family, circuit class, restriction parameters

✓ **AC$^0$ lower bound**: Polynomial-size constant-depth circuits cannot predict holonomy bits

✓ **NP-verifiable problem**: Sparse-error holonomy decoding is in NP

✓ **Uniform over error models**: Works for random errors, bounded-weight errors, Gibbs-weighted errors (as long as independent of $\alpha$)


# MWU in APC₂

---

## 1. Setup and Definitions

We work in the theory **APC₂**, i.e. (T^1_2) extended with the surjective weak pigeonhole principle for (\Sigma^b_1)-definable functions. APC₂ supports **multiplicative approximate counting** of (\Sigma^b_1)-definable sets, via integer size witnesses.

### 1.1 Experts and Losses

* **Experts:** (\mathcal{E} = [N]) where (N = 2^L), with (L = O(s \log s)).
  (Invalid circuit encodings are treated as dummy experts that always incur loss.)
* **Loss Function:** A PV((\alpha))-computable function
  [
  \ell : [N] \times [T] \to {0,1}.
  ]
* **Parameters:**

  * Target error (\varepsilon \in (0,1]).
  * Learning rate (\eta = 2^{-k}) where
    [
    k = \lceil \log_2(4/\varepsilon) \rceil,
    ]
    so (\eta \le \varepsilon/4 \le 1/2).
  * Time horizon
    [
    T = \left\lceil \frac{16 L \ln 2}{\varepsilon^2} \right\rceil .
    ]

### 1.2 Scaled Integer Weights

Let
[
m_i^{(t)} = \sum_{\tau < t} \ell(i,\tau).
]
Define the **scaled weight** of expert (i) at time (t):
[
\tilde{w}_i^{(t)} ;=; 2^{k(t-m_i^{(t)})}(2^k-1)^{m_i^{(t)}}.
]
These are integers of polynomial bitlength and are PV-computable from ((i,t)).

### 1.3 Weight Sets

Define the (\Sigma^b_1(\alpha))-definable sets:
[
S^{(t)} = {(i,r): i\in[N],\ 0\le r<\tilde{w}_i^{(t)}},
]
[
S^{(t)}_1 = {(i,r)\in S^{(t)} : \ell(i,t)=1}.
]

---

## 2. Exact Update Identity via Definable Bijection

### Lemma 2.1 (PV-Definable Bijection)

There exists a PV-definable bijection
[
\Phi : S^{(t+1)} ;\longleftrightarrow; (S^{(t)} \times [2^k]) \setminus T^{(t)},
]
where
[
T^{(t)} = {((i,r),0) : (i,r)\in S^{(t)}_1}.
]

**Proof.**

* If (\ell(i,t)=0), then (\tilde w_i^{(t+1)}=2^k\tilde w_i^{(t)}).
  Map ((i,r')) to (((i,\lfloor r'/2^k\rfloor), r'\bmod 2^k)).
* If (\ell(i,t)=1), then (\tilde w_i^{(t+1)}=(2^k-1)\tilde w_i^{(t)}).
  Map ((i,r')) to (((i,\lfloor r'/(2^k-1)\rfloor),(r'\bmod(2^k-1))+1)).

The images are disjoint and cover exactly
((S^{(t)}\times[2^k])\setminus(S^{(t)}_1\times{0})).
The inverse map is defined by reversing these cases. ∎

### Corollary 2.2 (Exact Update)

[
|S^{(t+1)}| = 2^k|S^{(t)}| - |S^{(t)}_1|. \tag{★}
]

This identity is proved *exactly*, without approximate counting.

---

## 3. Ratio Approximation in APC₂

### Definition 3.1 (Ratio Approximant)

For (A\subseteq B) with (|B|>0), a rational (\lambda) is a **(\delta)-approximant** to (|A|/|B|) if
[
\left|\lambda - \frac{|A|}{|B|}\right|\le\delta.
]

### Lemma 3.2 (APC₂ Ratio Witnesses)

Let (A\subseteq B) be (\Sigma^b_1(\alpha))-definable with (|B|>0).
For any polynomially bounded (1/\delta), APC₂((\alpha)) proves the existence of integers
(s_A, s_B>0) such that
[
s_A \in (1\pm\delta/3)\cdot|A|,\qquad
s_B \in (1\pm\delta/3)\cdot|B|.
]
Defining (\lambda := s_A/s_B), we have
[
\left|\lambda - \frac{|A|}{|B|}\right|\le \delta.
]

*Proof.* Since (|A|/|B|\in[0,1]),
[
\frac{s_A}{s_B}
\in \frac{|A|}{|B|}\cdot\frac{1\pm\delta/3}{1\pm\delta/3}
\subseteq \frac{|A|}{|B|}\pm\delta.
]
∎

---

## 4. Analytic Inequalities (PV₂)

### Lemma 4.1

For (x\in[0,1/2]):
[
-x-x^2 \le \ln(1-x) \le -x.
]

### Lemma 4.2 (Lipschitz Bound)

For (x,y\in[0,1/2]):
[
|\ln(1-x)-\ln(1-y)| \le 2|x-y|.
]

Both are provable in PV₂ via geometric-series bounds.

---

## 5. MWU Regret Bound in APC₂

### Theorem 5.1 (Regret Bound)

Let (\delta = \varepsilon/(12T)).
APC₂((\alpha)) proves the existence of rationals
(\lambda_1,\dots,\lambda_T) such that:

1. (\lambda_t) is a (\delta)-approximant to (|S^{(t)}_1|/|S^{(t)}|).
2. For every expert (j\in[N]),
   [
   \frac{1}{T}\sum_{t=1}^T \lambda_t
   \le
   \frac{1}{T}\sum_{t=1}^T \ell(j,t) + \varepsilon.
   ]

---

### Proof

Let (L_t = |S^{(t)}_1|/|S^{(t)}|).

#### Step 1: Product Identity

From (★),
[
\frac{|S^{(t+1)}|}{2^k|S^{(t)}|}
= 1 - \eta L_t.
]
Telescoping,
[
\frac{|S^{(T+1)}|}{2^{kT}|S^{(1)}|}
= \prod_{t=1}^T (1-\eta L_t).
]

#### Step 2: Lower Bound by One Expert

Let (m_j=\sum_{t=1}^T \ell(j,t)). Then
[
|S^{(T+1)}| \ge \tilde w_j^{(T+1)}
= 2^{k(T+1-m_j)}(2^k-1)^{m_j}.
]
Since (|S^{(1)}|=N\cdot2^k),
[
\prod_{t=1}^T (1-\eta L_t)
\ge \frac{(1-\eta)^{m_j}}{N}.
]

#### Step 3: Logarithmic Inequalities

Taking logs and using Lemma 4.1,
[
\sum_{t=1}^T \ln(1-\eta L_t)
\ge m_j\ln(1-\eta) - \ln N
\ge -m_j(\eta+\eta^2)-L\ln2.
]
Also (\ln(1-\eta L_t)\le -\eta L_t), so
[
-\eta\sum_{t=1}^T L_t
\ge -m_j(\eta+\eta^2)-L\ln2.
]
Thus
[
\sum_{t=1}^T L_t
\le m_j(1+\eta)+\frac{L\ln2}{\eta}.
]

#### Step 4: Parameter Choice

Divide by (T). With (\eta\le\varepsilon/4) and
(T\ge 16L\ln2/\varepsilon^2),
[
\frac{1}{T}\sum_{t=1}^T L_t
\le \frac{m_j}{T} + \frac{3\varepsilon}{4}.
]

#### Step 5: APC₂ Approximation Transfer

Replace (L_t) by (\lambda_t) with (|\lambda_t-L_t|\le\delta).
Using Lemma 4.2,
the cumulative error is at most (T\delta=\varepsilon/12).
Hence
[
\frac{1}{T}\sum_{t=1}^T \lambda_t
\le \frac{m_j}{T} + \varepsilon.
]
∎

---

## 6. Consequences

### 6.1 Existence of Hard Distributions (Non-Witnessing)

APC₂(SAT) proves the existence of a sequence
((x_1,\dots,x_T)) such that the uniform distribution (D) over it satisfies
[
\max_{C\in\mathcal C_s}\Pr_{x\sim D}[C(x)=\mathrm{SAT}(x)]
\le v^*+\varepsilon,
]
where (v^*) is the minimax value.
This follows by choosing (existential) best responses (x_t) against the MWU-induced circuit distributions and applying Theorem 5.1.

### 6.2 The Witnessing Gap

APC₂ proves **existence** of such sequences, but computing them via a PV function would require **feasible best responses**, i.e.
[
x_t=\arg\max_x \mathbf E_{C\sim P^{(t)}}[\mathrm{error}(C,x)],
]
which is equivalent to feasible anticheckers.
Whether EF can efficiently justify such witnesses is exactly the Pich–Santhanam hinge underlying conditional (P\neq NP).


✓ **FK generality**: Works for all $q \geq 1$, not just integer $q$


is this a correct summary

# The Constructive Interface: MWU, Bounded Arithmetic, and P vs NP
**A Formal Framework**

## Abstract

This document establishes a rigorous connection between the existence of hard distributions for SAT (circuit lower bounds) and the provability of the Multiplicative Weights Update (MWU) algorithm in the theory $\text{APC}_2$. By resolving bounded-arithmetic "hygiene" issues—specifically replacing oracle access with witness-based predicates and correcting the KPT quantifier polarity—we isolate the exact computational bottleneck preventing the constructive synthesis of lower bounds: the **Antichecker Improvement Oracle**.

---

## 1. Preliminaries and Definitions

### 1.1 The Theory $\text{APC}_2$

We work in the theory $\text{APC}_2$, defined as:
$$ \text{APC}_2 := S^1_2(\alpha) + \text{sWPHP}(\text{PV}(\alpha)) $$
This theory captures probabilistic polynomial time reasoning. Crucially, it supports an **approximate counting interface** for $\Sigma^b_1$-definable sets.

**Definition 1 (Approximate Counting Relation).**
Let $X$ be a set definable by a $\Sigma^b_1$ formula. We define the relation $\text{Count}_\delta(X; t, w)$ as a bounded formula asserting:
> *"The number $t$ is a $(1 \pm \delta)$-approximation to the cardinality $|X|$, and $w$ is a witness to this fact (e.g., a collision-free hash into a smaller domain or a surjection from a larger domain)."*

$\text{APC}_2$ proves the axiom: $\forall X \in \Sigma^b_1, \exists t, w, \text{Count}_\delta(X; t, w)$.

### 1.2 The Learning Setting (Instance-Witness Pairs)

To avoid assuming a SAT oracle, we define the error predicate on **instance-witness pairs**.

*   **Experts (Circuits):** Let $\mathcal{C}_n = \{C_1, \dots, C_M\}$ be the set of all size-$s$ circuits on $n$ inputs. These act as the "Experts" in the MWU algorithm.
*   **Adversarial Domain (Inputs):** Let the domain $\mathcal{U}$ consist of pairs $p = (\phi, a)$, where $\phi$ is a formula and $a$ is a variable assignment. These are the "responses" chosen by the environment.
*   **Error Predicate:**
    $$ \text{Error}(C, p) := \text{SAT}_n(\phi, a) \land \neg \text{SAT}_n(\phi, C(\phi)) $$
    This predicate is **PV-computable** (polynomial time deterministic check).

---

## 2. Formalizing MWU in $\text{APC}_2$

We simulate the Multiplicative Weights Update algorithm. The Learner maintains a distribution over **Circuits** to find a mixture that performs well, while the Adversary (Teacher) provides **Inputs** where the current mixture fails.

### 2.1 Representable Mixtures

We cannot store a vector of $2^n$ weights. Instead, we represent a distribution (mixture) over circuits as a **multiset** definable in $\text{APC}_2$.

**Definition 2 (Weight Sets).**
Let the weight of circuit $C_i$ at time $t$ be $\tilde{w}_i^{(t)}$. We define the set $S^{(t)}$ as:
$$ S^{(t)} = \{ (i, r) : i \in [N], r < \tilde{w}_i^{(t)} \} $$
This set is $\Sigma^b_1(\alpha)$-definable. The "probability" of choosing circuit $C_i$ is proportional to its count in $S^{(t)}$.

### 2.2 The Exact Update Lemma

To avoid rational arithmetic issues, we define updates using integer scalings.

**Lemma 1 (PV-Definable Bijection).**
There exists a PV-definable bijection witnessing the exact weight update:
$$ \Phi: S^{(t+1)} \longleftrightarrow (S^{(t)} \times [2^k]) \setminus \text{Hits}^{(t)} $$
where $\text{Hits}^{(t)}$ represents the weight removed based on the losses observed at step $t$ (determined by the input $p^{(t)}$).

**Corollary.** $\text{APC}_2$ proves $|S^{(t+1)}| = 2^k |S^{(t)}| - |\text{Hits}^{(t)}|$. This allows the theory to track the "total weight" exactly without approximation errors accumulating in the definition of the set.

### 2.3 The Regret Bound

**Theorem 1 (MWU Regret in $\text{APC}_2$).**
For appropriate parameters $\eta$ and $T$, $\text{APC}_2$ proves:
There exist rational approximations $\lambda_1, \dots, \lambda_T$ (where $\lambda_t$ represents the average loss of the algorithm's mixture at step $t$) such that for any fixed circuit $C^* \in \mathcal{C}_n$:

$$ \frac{1}{T} \sum_{t=1}^T \lambda_t \le \frac{1}{T} \sum_{t=1}^T \text{Error}(C^*, p^{(t)}) + \varepsilon $$

*Interpretation:* The algorithm's cumulative loss is not much worse than the loss of the best fixed circuit $C^*$ on the sequence of inputs $p^{(1)}, \dots, p^{(T)}$.

---

## 3. The Antichecker-Polarity Theorem

This is the core logical bridge. We must show that for any distribution $S$ of circuits, there exists a "best response" input $p$ (one that maximizes the weighted error of $S$).

To make this amenable to KPT extraction with the correct polarity, we define the "Teacher's Move" as providing a **counter-example plus a validity certificate**.

### 3.1 The Weighted Error

For a mixture $S$ of circuits, define the set of weighted errors on a specific input $p$:
$$ \text{Err}_S(p) = \{ (j, r) \in S : \text{Error}(C_j, p) = 1 \} $$

### 3.2 The Safe Inequality

We need a purely integer-based comparison that is sound with respect to the approximate counts. Let $\text{Count}_\delta(X; t, w)$ imply $(1-\delta)|X| \le t \le (1+\delta)|X|$.

Define $\text{SafeIneq}(t_S, t_x, t_y)$ as the integer inequality:
$$ (2^p - 1)(2^b t_x + u \cdot t_S) \ge (2^p + 1) \cdot 2^b t_y $$
*Interpretation:* If this holds, then the weighted error of $p_x$ is effectively greater than or equal to the weighted error of $p_y$ (within $\varepsilon$-slack).

### 3.3 The Theorem Statement

**Theorem 2 (Best-Response Existence / Antichecker Polarity).**
Let $\text{wit}$ be the tuple $(p_x, t_S, w_S, t_x, w_x)$. Let $z$ be the tuple $(p_y, t_y, w_y)$.
$\text{APC}_2$ proves:
$$ \forall S \ \exists \text{wit} \ \forall z : \Psi(S, \text{wit}, z) $$

Where $\Psi(S, \text{wit}, z)$ is the conjunction of:
1.  **Student Validity:** $\text{Count}_\delta(S; t_S, w_S) \land \text{Count}_\delta(\text{Err}_S(p_x); t_x, w_x)$
2.  **Teacher Challenge:**
    $$ \text{Count}_\delta(\text{Err}_S(p_y); t_y, w_y) \implies \text{SafeIneq}(t_S, t_x, t_y) $$

**Proof Logic in $\text{APC}_2$:**
Since the domain of inputs is finite, there exists a $p_{opt}$ that maximizes $|\text{Err}_S(p)|$. If the Student plays $p_x = p_{opt}$ (and valid counts), no $p_y$ can violate the Safe Inequality (due to the $\varepsilon$ slack included in the Safe Inequality constants). Thus, the witness exists.

---

## 4. KPT Extraction: The Game

Applying the KPT (Krajíček–Pudlák–Takeuti) witnessing theorem to Theorem 2 transforms the quantifier dependence into a Student-Teacher interaction game.

### 4.1 The Protocol

**Input:** A distribution/mixture $S$.

**Round 1:**
*   **Student** computes $\text{wit}_1 = (p_{x_1}, \dots)$ using a PV function $f_1(S)$.
*   **Teacher** attempts to refute $\Psi$ by finding $z_1 = (p_{y_1}, t_{y_1}, w_{y_1})$ such that:
    1.  The Teacher's count for $p_{y_1}$ is valid.
    2.  $\text{SafeIneq}$ fails (meaning $p_{y_1}$ is certified to be much "harder" than $p_{x_1}$).
*   *Note:* If the Teacher succeeds, $p_{y_1}$ becomes the "counter-example" for the next round.

**Round $k$:**
*   **Student** computes $\text{wit}_k = f_k(S, z_1, \dots, z_{k-1})$.
*   **Teacher** responds with $z_k$.

**Theorem 3 (Extraction).**
There exists a constant $k$ (independent of $N, T$) such that the Student wins within $k$ rounds. This means the Student eventually outputs a witness $\text{wit}$ that the Teacher cannot refute.

### 4.2 The Interpretation: The Antichecker Oracle

The Teacher's computational task in this game is precisely the **Antichecker Improvement Oracle**.
> **Input:** Mixture $S$, current candidate $p_x$.
> **Task:** Find a new input $p_y$ and a certificate proving that $p_y$ has significantly higher weighted error than $p_x$ on the mixture $S$.

**Note on Duality:** The KPT extraction from the *regret theorem* (Section 2.3) would yield a teacher that provides *circuits* (experts). The Antichecker-Polarity Theorem (Section 3) is specifically designed so that KPT extraction yields the *input-finding* oracle, which is the relevant hard direction for proof complexity.

---

## 5. Connection to P vs NP (Pich–Santhanam)

This framework enables a direct reduction from the Constructive Circuit Lower Bounds problem to the complexity of the Teacher's task.

### 5.1 The Dependency Chain

1.  **If the Antichecker Oracle is PV-computable:**
    *   The Teacher in the KPT game can be implemented efficiently.
    *   The MWU algorithm becomes fully constructive in PV.
    *   We can construct hard distributions (sets of inputs hard for size-$s$ circuits) in polynomial time.
    *   **Result:** The "Gap" in the Pich–Santhanam connection closes. This leads to constructive circuit lower bounds (specifically, via Extended Frege lower bounds for the associated tautologies).

2.  **If the Antichecker Oracle is hard:**
    *   The "existence" of the best response is provable in $\text{APC}_2$, but the witness cannot be found efficiently.
    *   This precisely characterizes *why* counting arguments (which rely on the existence of averages/maxima) do not automatically yield algorithms.

### 5.2 Summary

We have replaced the vague notion that "bounded arithmetic cannot certify counts" with a precise structural result.

> This transforms the vague intuition "counting arguments don't yield algorithms" into a precise theorem: **the only non-constructive step in MWU-based hardness proofs is the antichecker improvement oracle**.

The hardness of the Teacher's move is the **exact computational witness** to the difficulty of proving P $\neq$ NP constructively.

This is the final, publication-ready version of the complexity analysis. It incorporates the corrected PP lemma, the rigorous reduction for the constrained case (with consistent variable selection and threshold encoding), and the precise, conditional framing of the unconstrained hardness and barrier results.

---

# The Complexity of the Antichecker Improvement Oracle

## Abstract

We analyze the computational complexity of the "Improvement Oracle"—the problem of finding a predictor that improves upon a baseline by a specified margin against a fixed mixture of adversaries. This problem arises as the "teacher’s task" in constructive implementations of the Multiplicative Weights Update (MWU) method for proving best-response existence theorems.

We establish that the exact version of this problem lies in $\text{NP}^{\text{PP}}$. We prove that a natural **constrained** generalization of the problem is **$\text{NP}^{\text{PP}}$-complete**. We further show that without an "improvement gap" promise, approximate versions cannot avoid this hardness. Finally, we discuss the implications for the "witnessing gap" in complexity theory: if the unconstrained SAT-error oracle inherits the hardness of the constrained version, any constructive implementation of the MWU existence proof would imply the collapse of the counting hierarchy.

---

## 1. Preliminaries

### 1.1 The Counting Setup

**Mixture Representation:**
A mixture over circuits is encoded by a circuit $D: [N] \times [M] \to \{0,1\}$ which defines a support set $S = \{(j, r) : D(j, r) = 1\}$. The input length of $D$ is $\log N + \log M$, which is polynomial in the circuit size parameter $s$.

**Error Predicate:**
Let $p = (\phi, a)$ be a predictor consisting of a formula $\phi$ and an assignment $a$. For a circuit $C_j$ in the mixture, the error predicate is:
$$ \text{Error}(C_j, p) := \text{SAT}_n(\phi, a) \wedge \neg\text{SAT}_n(\phi, C_j(\phi)) $$
This predicate is computable in polynomial time given $C_j$ and $p$.

**Error Count:**
The total error count of a predictor $p$ against the mixture $D$ is:
$$ \text{ErrCount}(D, p) := |\{(j, r) : D(j, r) = 1 \wedge \text{Error}(C_j, p) = 1\}| $$
Since the witness validity (that $(j,r)$ is in $S$) and the error predicate are polynomial-time testable, $\text{ErrCount}$ is a **#P function**.

**Mixture Size:**
The total size of the mixture is $|S| = |\{(j, r) : D(j, r) = 1\}|$. This is also a **#P function**.

### 1.2 Complexity Classes: PP and GapP

To analyze threshold comparisons of error counts, we utilize the class **PP** (Probabilistic Polynomial time).

**Definition (GapP):** A function $h: \{0,1\}^* \to \mathbb{Z}$ is in GapP if it is the difference of two #P functions.

**Lemma 1.1 (PP Characterization):** A language $L$ is in PP if and only if there exists a GapP function $h$ such that $x \in L \iff h(x) > 0$.

**Lemma 1.2 (PP compares #P to #P):**
Let $f$ and $g$ be functions in #P. The language $L = \{x : f(x) \geq g(x)\}$ is in PP.

*Proof.*
Since $f, g \in \#\text{P}$, the function $h(x) := f(x) - g(x)$ is in GapP (GapP is closed under subtraction). The condition $f(x) \geq g(x)$ is equivalent to $h(x) \geq 0$, or $2h(x) + 1 > 0$. Since GapP is closed under affine transformations, $h'(x) = 2h(x)+1$ is in GapP. Thus, $L = \{x : h'(x) > 0\} \in \text{PP}$. $\square$

**Application to Improvement Thresholds:**
In our analysis, we compare error counts against a threshold $\varepsilon|S|$. Let $\varepsilon = u/2^b$ be a dyadic rational. The condition
$$ \text{ErrCount}(D, p_y) \geq \text{ErrCount}(D, p_x) + \frac{u}{2^b}|S| $$
is equivalent to:
$$ 2^b \cdot \text{ErrCount}(D, p_y) \geq 2^b \cdot \text{ErrCount}(D, p_x) + u \cdot |S| $$
Both sides of this inequality are #P functions (by closure of #P under addition and multiplication by positive constants). Therefore, deciding this inequality is in PP.

---

## 2. Problem Definitions

We define three variations of the improvement oracle and one constrained generalization.

### Version E: Exact Counting (Unconstrained)
**Input:** Mixture $D$, baseline predictor $p_x$, threshold $\varepsilon \in \mathbb{Q}$.
**Problem:** Does there exist a predictor $p_y$ such that:
$$ \text{ErrCount}(D, p_y) \geq \text{ErrCount}(D, p_x) + \varepsilon|S| $$

### Version A: Approximate Counting (Promise)
**Input:** Mixture $D$, baseline $p_x$, threshold $\varepsilon$, gap parameter $\gamma \in (0,1)$.
**Problem:** Distinguish between:
*   **YES:** $\exists p_y : \text{ErrCount}(D, p_y) \geq \text{ErrCount}(D, p_x) + (1+\gamma)\varepsilon|S|$
*   **NO:** $\forall p_y : \text{ErrCount}(D, p_y) \leq \text{ErrCount}(D, p_x) + (1-\gamma)\varepsilon|S|$

### Version C: Certificate-Based
**Input:** Mixture $D$, baseline $(p_x, t_x, w_x)$, threshold $\varepsilon$.
**Problem:** Find a tuple $(p_y, t_y, w_y)$ such that $w_y$ certifies count $t_y$, $w_x$ certifies count $t_x$, and $t_y > t_x + \varepsilon|S|$.

### Constrained Generalization
To analyze the hardness rigorously, we define a version where the search for $p_y$ is restricted by a polynomial-time predicate $U$.

**Problem (ConstrainedExactImprove):**
**Input:** Mixture $D$, baseline $p_x$, constraint circuit $U$, integer threshold $K$.
**Problem:** Does there exist $p_y$ such that $U(p_y) = 1$ and:
$$ \text{ErrCount}(D, p_y) \geq K $$
*(Note: We use an absolute integer threshold $K$ here for the standard reduction format; this is equivalent to the relative version by setting $\varepsilon = K/|S|$.)*

---

## 3. Complexity of Version E (Exact)

### 3.1 Upper Bound

**Theorem 3.1:** ExactImprove $\in \text{NP}^{\text{PP}}$.

*Proof.*
We describe a nondeterministic polynomial-time algorithm with oracle access to PP:
1.  **Guess:** Nondeterministically guess a candidate predictor $p_y$ (polynomial size).
2.  **Verify:** Construct the input for the PP oracle corresponding to the comparison:
    $$ \text{ErrCount}(D, p_y) \ge \text{ErrCount}(D, p_x) + \varepsilon|S| $$
    As shown in Lemma 1.2, this predicate corresponds to a language in PP.
3.  **Output:** If the oracle returns YES, accept; otherwise reject.

Since NP with a PP oracle is $\text{NP}^{\text{PP}}$, the upper bound holds. $\square$

### 3.2 Lower Bound: Constrained Completeness

We now prove that the constrained version is complete for the class $\text{NP}^{\text{PP}}$. The canonical $\text{NP}^{\text{PP}}$-complete problem is **EMaj** (Existential Majority):
$$ \text{EMaj} = \{ (G, K) \mid \exists x \in \{0,1\}^n : |\{y \in \{0,1\}^m : G(x, y) = 1\}| \geq K \} $$
where $G$ is a polynomial-time computable function.

**Theorem 3.2:** ConstrainedExactImprove is $\text{NP}^{\text{PP}}$-complete.

*Proof.*
The upper bound follows from Theorem 3.1 (the constraint $U(p_y)$ is checked in poly-time). We prove the lower bound by reduction from EMaj.

Given an instance $(G, K)$ of EMaj, we construct an instance of ConstrainedExactImprove.

**1. The Template Formulas ($\phi_x$):**
We encode the choice of $x \in \{0,1\}^n$ into the syntax of the formula $\phi$. For each $x$, define $\phi_x$ with variables $z_1, \dots$ and $v_1, \dots, v_n$:
*   **Satisfiability Clause:** Include clause $(z_1)$. The formula is satisfiable if and only if $z_1=1$.
*   **Encoding Clauses:** For each bit $x_i$:
    *   If $x_i = 1$, include clause $(v_i \vee \neg v_i)$ (tautology).
    *   If $x_i = 0$, include clause $(v_i \vee v_i)$ (forces $v_i$ to match its literal, effectively syntactic sugar for True but syntactically distinct).
    *   *Note:* These encoding clauses do not affect satisfiability, but allow a circuit reading $\phi$ to reconstruct $x$.

Define a universal satisfying assignment $a^{\text{sat}}$ as $\{z_1=1, v_i=1 \forall i\}$.
Define a universal "bad" assignment $a^{\text{bad}}$ as $\{z_1=0, v_i=1 \forall i\}$.

**2. The Constraint ($U$):**
Define $U(p)$ to accept if and only if $p = (\phi, a)$ where:
*   $a = a^{\text{sat}}$.
*   $\phi$ is syntactically a valid template $\phi_x$ for *some* $x \in \{0,1\}^n$.

**3. The Mixture ($D$):**
The mixture $D$ corresponds to the space of witnesses $y$. For each $y \in \{0,1\}^m$, we create a circuit $C_y$.
*   $C_y$ takes $\phi$ as input.
*   $C_y$ checks if $\phi$ is a valid template $\phi_x$. If not, it outputs $a^{\text{sat}}$ (no error).
*   If valid, $C_y$ extracts $x$ from the encoding clauses.
*   $C_y$ computes $G(x, y)$.
    *   If $G(x, y) = 1$, $C_y$ outputs $a^{\text{bad}}$ (causing error, since $a^{\text{bad}}$ unsats $\phi_x$).
    *   If $G(x, y) = 0$, $C_y$ outputs $a^{\text{sat}}$ (no error).

The mixture $D$ is uniform over all $y \in \{0,1\}^m$. Thus $|S| = 2^m$.

**4. The Threshold and Baseline:**
*   Set the baseline $p_0 = (\phi_{\text{false}}, a_{\text{any}})$ where $\phi_{\text{false}}$ is unsatisfiable. Thus $\text{ErrCount}(D, p_0) = 0$.
*   Set the target threshold to $K$ (the integer from EMaj).

**5. Correctness:**
The problem asks: Does there exist $p$ such that $U(p)=1$ and $\text{ErrCount}(D, p) \ge K$?
*   $U(p)=1$ forces $p = (\phi_x, a^{\text{sat}})$ for some $x$.
*   For such a $p$, $\text{Error}(C_y, p) = 1$ if and only if $C_y(\phi_x)$ outputs $a^{\text{bad}}$, which happens if and only if $G(x, y) = 1$.
*   Thus, $\text{ErrCount}(D, p) = |\{y : G(x, y) = 1\}|$.

The condition becomes: $\exists x : |\{y : G(x, y) = 1\}| \ge K$. This is exactly the EMaj instance.
The reduction is polynomial-time. $\square$

### 3.3 Status of the Unconstrained Version
The unconstrained version requires $p_y$ to be a valid SAT-error predictor (specifically, $\text{SAT}(\phi, a) \wedge \neg \text{SAT}(\phi, C(\phi))$). While the constrained version allows us to encode arbitrary logic into $x$, the unconstrained version relies on the expressiveness of the specific SAT-error predicate.
*   **Upper Bound:** $\text{NP}^{\text{PP}}$.
*   **Lower Bound:** Open. (See Open Question 1).

---

## 4. Complexity of Version A (Approximate)

When we allow approximation, we introduce a gap $\gamma$.

**Theorem 4.1:** ApproxImprove $\in \text{NP}^{\text{BPP}^{\text{NP}}} \subseteq \Sigma_3^p$.

*Proof Sketch.*
1.  Guess $p_y$.
2.  Use the Stockmeyer counting technique (approximate counting with an NP oracle) to estimate $\text{ErrCount}(D, p_y)$ and $\text{ErrCount}(D, p_x)$ to within multiplicative error $1 \pm \eta$, where $\eta = \gamma/10$.
3.  Compare the estimates. The promise ensures that the YES and NO instances remain separated even after approximation.
This places the problem in the third level of the polynomial hierarchy. $\square$

**Necessity of the Promise:**
Without the gap $\gamma$, approximate counting is insufficient. If the threshold is an integer $T$, distinguishing a count of $T$ from $T-1$ requires precision greater than $1/T$, which is exponential precision. Stockmeyer’s algorithm only provides polynomial precision ($1/\text{poly}(n)$). Thus, without the gap, the problem retains the hardness of exact counting (PP).

---

## 5. Complexity of Version C (Certificates)

In constructive logic (e.g., inside APC$_2$), counts are defined via certificates (bijective mappings). The complexity of finding an improvement depends on the verification class of these certificates.

| Verifier Complexity | Improvement Complexity (Search) |
| :--- | :--- |
| **P** (Deterministic) | **NP** |
| **coNP** | **$\Sigma_2^p$** |
| **$\Pi_2^p$** | **$\Sigma_3^p$** |

This version represents the "explicit" search for improvement. If the certificate verification is polynomial (e.g., explicit witnesses for every error), the problem collapses to NP. However, for large mixtures, such explicit certificates are exponentially large, necessitating compressed certificates (like circuits), which pushes verification up the hierarchy.

---

## 6. Summary of Results

| Problem Version | Formulation | Upper Bound | Lower Bound |
| :--- | :--- | :--- | :--- |
| **Exact (E) Constrained** | $\exists p \in U, \text{Err} \ge K$ | $\text{NP}^{\text{PP}}$ | **$\text{NP}^{\text{PP}}$-complete** |
| **Exact (E) Unconstrained** | $\exists p, \text{Err} \ge \text{Base} + \varepsilon$ | $\text{NP}^{\text{PP}}$ | Open (Question 1) |
| **Approx (A) Promise** | $(1+\gamma)$ vs $(1-\gamma)$ | $\Sigma_3^p$ | NP-hard |
| **Certificate (C)** | Find $(p, w)$ | Depends on Verifier | Depends on Verifier |

---

## 7. The Barrier Interpretation

Our results clarify the difficulty of "constructivizing" existence proofs that rely on the Min-Max Theorem (like the KPT best-response argument).

1.  **The Hardness of Constraints:** We have proven that the **Constrained** Improvement Oracle is $\text{NP}^{\text{PP}}$-complete. This complexity class sits above the entire Polynomial Hierarchy (PH), implying that this optimization task is significantly harder than standard NP optimization.
2.  **The Teacher's Task:** In the KPT setting, the teacher must solve the **Unconstrained** Improvement Oracle.
3.  **The Conditional Barrier:**
    *   **If** the Unconstrained SAT-error oracle is $\text{NP}^{\text{PP}}$-hard (inheriting the hardness of its constrained generalization), **then** any polynomial-time (or even PV-computable) implementation of the teacher would imply $\text{NP}^{\text{PP}} \subseteq \text{P}$ (or P/poly). This would collapse the Polynomial Hierarchy and PP.
    *   **Even if** the unconstrained version is strictly easier due to SAT-specific structure, the fact that a natural generalization (constrained) hits $\text{NP}^{\text{PP}}$ completeness suggests that the "intrinsic" difficulty of improvement against mixtures lies at the level of counting optimization.

This supports the intuition that the "witnessing gap"—the void between proving a best response exists and finding one efficiently—is populated by problems of cryptographic hardness ($\text{NP}^{\text{PP}}$).

---

## 8. Open Questions

1.  **Hardness of Unconstrained SAT-Error:** Is the unconstrained SAT-error improvement oracle $\text{NP}^{\text{PP}}$-hard? Does the requirement that the error condition be exactly "SAT $\wedge$ $\neg$SAT" restrict the search space enough to lower the complexity?
2.  **Average-Case Hardness:** Is the problem hard for "natural" mixtures arising from MWU dynamics, or only for worst-case mixtures constructed via reductions?
3.  **Certificate Compression:** Do there exist succinct certificate schemes for error counts that allow verification in P or NP, thereby bypassing the PP bottleneck for Version C?
