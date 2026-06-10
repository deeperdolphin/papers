# The Generic Causal Code: Gravity as the Thermodynamics of Self-Decoding Records

**Version 1.0 — full development**

---

## Abstract

We develop the **Generic Causal Code (GCC)** in full: a framework in which the universe is the maximum-entropy quantum process consistent with four constraints — that events are isometries (quantum mechanics is exact), that the past remains decodable from incomplete data (records persist redundantly), that capacity is finite, and that the structure is legible to its own bounded inhabitants (correlations define a metric). No spacetime, graph, dimension, gauge group, growth law, or global quantum state is assumed. The fundamental object is a *record structure* — a wiring of finite isometries — whose causal order we define operationally through signaling capacity, with the wiring itself demoted to gauge. Dynamics is derived, not chosen: the physical measure is the maximally random ensemble over record structures satisfying the four constraints, in a two-fugacity grand-canonical form whose multipliers — the chemical potential of events and the price of capacity — are later identified with $\Lambda$ and $1/4G$.

The mathematical core is established as a sequence of results. We prove the structural foundations: order-independence of composition, causality of influence, and the equivalence of "block" and "becoming" presentations of the measure (Theorem 5.2), reducing the residual content of becoming to a locality property of conditional kernels. We prove a dimension theorem: combining the persistence axiom with the quantum Singleton bound and the boundary scaling supplied by legibility yields $\eta \le D-1$, i.e. $D \ge 1+\eta$ — *space exists because the past insists on surviving* — with no appeal to unproven code-tradeoff transfers (Theorem 6.6). We develop the criticality window as a complementarity principle: legibility is the local readability of one observable sector, persistence is the protection of its conjugate, and we show in the stabilizer setting that forests cannot support both — locally generated codes on cycle-free wirings have bounded distance, while classically broadcast trees fail conjugate protection by an explicit no-cloning computation. Geometry is the compromise between being readable and being remembered, and cycles are its currency. We define the emergent gauge group as the commutant of the encoded algebra, exhibit its junk-factor structure, define holonomy as a cocycle obstruction on the wiring's cycle space, and present a conditional no-bi-temporality proposition deriving the $(D{-}1,1)$ signature from monogamy of entanglement under crossed persistence demands. Gravitation is developed as the thermodynamics of the constraint set: a diamond first law follows from max-ent stationarity; the Ryu–Takayanagi min-cut law is inherited as a theorem of the kinematics; the Einstein equations follow along the Jacobson chain modulo one named gap; and the cosmological constant problem splits into two parts, the Planckian piece cancelled by *critical pinning* of the event fugacity (the existence of an unbounded record forces $\mu \to \mu_c$, annihilating the extensive vacuum term) and the residual piece set by the decoding tolerance, yielding the seesaw $\Lambda \simeq 8\pi \ell_P^2 / R_{\mathrm{dec}}^4$ and a predicted Yukawa corridor at $40$–$90\,\mu$m.

Four worked microcosms anchor the formalism: the chain (persistence forbids one dimension), the minimal causal diamond (the $[[4,2,2]]$ code realized on a loop, with stabilizers as Wilson loops), the tree dichotomy (an explicit GHZ no-cloning computation versus illegible random trees), and the $1{+}1$-dimensional brickwork (which saturates the dimension floor). A complete computational protocol with pre-registered interpretations, including the kill condition, closes the paper. The framework has two free parameters, $(\chi,\epsilon)$, and, by construction, no others.

---

## 1 Introduction

### 1.1 The wager

Twentieth-century physics dissolved one fundamental structure after another into something more abstract: particles into fields, fields into representations, geometry into entanglement bookkeeping. Two things survived every dissolution. Quantum mechanics survived intact — no modification of it has ever been required by data. And one fact about gravity survived every reformulation: the information in a region is bounded by its boundary area, not its volume [3,4,5]. GCC takes these two survivors as the entire foundation and wagers that everything else — space, time, dimension, gauge structure, the gravitational field equations, even the Lorentzian signature — is a *forced consequence* of demanding that a finite quantum process keep, and be able to read, its own records.

The wager sharpens into a slogan: **the universe is the most random thing that can still read itself.** Randomness is the absence of unexplained structure — the correct prior for a fundamental theory, in the sense of Jaynes [2], since any non-generic feature of the microdynamics is an unexplained coincidence demanding its own explanation. Legibility is the minimal anthropic-free requirement for there to be physics at all: a universe whose past is unreadable and whose places are indistinguishable contains no records, no measurements, no observers, and no science [1]. GCC is the proposal that these two demands, made precise, have a nonempty and essentially unique intersection, and that the intersection looks like our world.

### 1.2 The four axioms, in words

**C1 — Quantum primacy.** Elementary events are isometries on finite-dimensional systems. Information is never destroyed; it is only rewired.

**C2 — Persistence.** What has been written can be read later *from incomplete data*: the logical content of every event remains decodable, to tolerance $\epsilon$, from later cross-sections even when parts of them are erased, with a protection depth that grows with scale. (Recoverability from a *complete* later cross-section is automatic, being unitarity; the content of C2 is redundancy.) The past is not stored elsewhere; it is encoded, at growing depth, in the present. Time's arrow is the direction of accumulating protection.

**C3 — Finiteness.** Every system has bounded dimension, and both events and capacity carry a cost, enforced not by decree but by fugacities. There are no infinities at the bottom, and no free structure.

**C4 — Legibility.** The correlation structure, as seen by bounded internal protocols, defines a metric: places are distinguishable, distances are measurable from inside, ball volumes scale with a finite exponent, and — the *self-location clause* — the wiring is local with respect to the very geometry the correlations define. A universe is not a universe *for anyone* unless this holds; we elevate the existence of internal observers from anthropic afterthought to load-bearing axiom.

**G — Genericity (the dynamical postulate).** The physical measure over record structures is the maximum-entropy measure subject to C1–C4. There is no further law. Every coupling of the effective macroscopic theory must therefore be the Lagrange multiplier of one of the four constraints, and a coupling that cannot be so identified is a falsification.

### 1.3 Summary of results

For a framework of this scope it is essential to separate what is proved from what is constructed and from what is conjectured. The mathematical results of this paper, with their status, are:

*Proved (elementary but structural):* order-independence of record composition (Lemma 3.3); influence is contained in wiring reachability and forms a strict partial order, and is invariant under wiring gauge (Propositions 3.5, 3.7); the block/becoming presentation equivalence for finite records (Theorem 5.2); the dimension floor $D \ge 1+\eta$ from persistence, legibility, and the quantum Singleton bound (Theorem 6.6); bounded distance for locally generated stabilizer codes on forests (Proposition 6.8, by cleaning and trivial homology); failure of conjugate protection in broadcast trees (Proposition 6.9, by an explicit no-cloning computation); illegibility of expander wirings (Proposition 6.10); the conditional no-bi-temporality proposition (Proposition 7.5); the diamond first law as max-ent stationarity (Proposition 8.2); and the saturation of the dimension floor by the $1{+}1$ brickwork microcosm (Section 9.4).

*Imported as theorems:* the min-cut law for entropies of random tensor networks [11], which GCC inherits because Postulate G makes the universe a random tensor network whose wiring is itself drawn from the constrained measure (Theorem 6.5).

*Constructed (defined and computable, awaiting computation):* the generic measure and its Clifford realization; the metric, dimension, and curvature observables; the gauge census; the entire protocol of Section 10.

*Conjectured (the physics):* the criticality-window selection of a finite dimension $D^*(\chi,\epsilon)$ (Conjecture 6.11); the locality of the frontier presentation (Conjecture 5.3); generic crossing for bi-temporal orders (Conjecture 7.6); the equation-of-state completeness step in the Einstein derivation (Section 8.3); critical pinning as the cancellation of the Planckian cosmological constant (Conjecture 8.4); and the seesaw corridor (Section 8.5).

### 1.4 Claim tiers

Every claim in the paper is tagged. **Tier I (proved):** the mathematical statements listed above, each with proof or proof sketch in the text or Appendix B. **Tier II (defined and computable):** the constructions and the measurement protocol; these are concrete mathematical objects and polynomial-time computations in the Clifford realization. **Tier III (conjectural):** the physical claims, engineered so that they die or survive by Tier II computations. Tier I contains mathematical results; numerical results will enter the record exclusively through the protocol of Section 10, which this paper publishes before executing — pre-registration being the standard the framework adopts for itself.

### 1.5 Reader's map

Section 2 situates the framework. Section 3 develops the kinematics of record structures, including the code-theoretic structure of causal diamonds. Section 4 formalizes the constraint quartet and the generic measure, including its regularization and the critical pinning of the fugacities. Section 5 constructs time, observers, and the two presentations of the measure. Section 6 builds geometry: metric, areas, the inherited entropy law, the dimension floor, the tree/expander dichotomy, and the criticality window. Section 7 derives gauge structure and frames matter and signature. Section 8 develops gravitation as constraint thermodynamics, through the seesaw. Section 9 works four microcosms in full detail. Section 10 specifies the computational program and the kill conditions. Section 11 confronts objections; Section 12 concludes. Appendices collect notation (A), proofs (B), the stabilizer toolkit (C), and units and conventions (D).

---

## 2 Relation to Other Approaches

GCC stands at the intersection of several programs and differs from each at a specific joint.

**Causal sets.** The insistence that causal order is primary descends from Bombelli, Lee, Meyer, and Sorkin [20], and the theorems of Malament and of Hawking, King, and McCarthy [29,30] — causal order plus volume determines a Lorentzian geometry — are the continuum license for everything Section 6 does with order and counting. GCC differs in two ways: its elements are not structureless (they carry isometries, hence information flow, hence an *operational* rather than postulated order), and its dynamics is not a sequential growth law in the Rideout–Sorkin class [21] but a constrained maximum-entropy measure over completed structures. Sequential growth appears in GCC only as a sampler (Theorem 5.2), which is also how GCC escapes the foliation problem that layered models face [23]. For the state of the causal set program see Surya's review [22].

**Causal dynamical triangulations and dimensional flow.** CDT established that discrete quantum-gravity ensembles can exhibit scale-dependent spectral dimension [24], and Carlip has argued that ultraviolet dimensional reduction is close to universal across approaches [25]. GCC's relation to this phenomenology is indirect but sharp: its dimension is not an input anywhere, so any measured $D^*$ — including any scale dependence — is forced (Section 6.7).

**Holography, tensor networks, and quantum error correction.** The area law for information [3,4,5], the Ryu–Takayanagi formula [6], the entanglement-builds-geometry program [7,8], holographic codes [9,10], and the random tensor network theorems [11] are, collectively, the strongest current in modern quantum gravity (see Harlow's lectures [12]). GCC's position: these results describe the *kinematics of the generic record*. What GCC adds is (i) a reason the network exists at all (the constrained max-ent measure), (ii) a wiring that is dynamical rather than a fixed hyperbolic lattice, and (iii) a de Sitter-compatible, observer-relative formulation (Sections 4–5), in the spirit of the algebraic results of Chandrasekaran, Longo, Penington, and Witten [51] and of Banks–Fischler holographic spacetime [52].

**Thermodynamic gravity.** Jacobson derived the Einstein equation as an equation of state [13] and later as entanglement equilibrium [14]; Faulkner et al. established the linearized statement holographically [15]; Verlinde and Padmanabhan developed entropic and thermodynamic readings [17,18]; Sakharov's induced gravity is the ancestor of all of it [19]. GCC's contribution is to *locate the hypothesis*: in a maximum-entropy ensemble, small-diamond entropy stationarity is not an assumption about gravity but the defining property of the measure (Proposition 8.2). The remaining gap is isolated in Section 8.3.

**Graph-dynamical emergence.** Quantum graphity [26] and combinatorial quantum gravity [27] pursue geometry from graph ensembles; Lloyd's computational-universe program [28] pursues physics from generic quantum computation. GCC shares the ambitions and differs in deriving its graph from information flow (the wiring is gauge; influence is physical) and its dynamics from constraints rather than a chosen Hamiltonian or action.

**Quantum causal models.** The operational definition of causal structure through signaling in networks of channels is developed in the quantum causal models literature [55]; GCC's Definition 3.4 is that definition, promoted from a tool for analyzing laboratory causation to the fundamental ontology.

**Random circuits and measurement transitions.** The statistical mechanics of random isometric dynamics — entanglement growth, membrane pictures, and the volume-law/area-law transitions driven by competing scrambling and readout [43,44] — is the closest existing laboratory for GCC's central tension: scrambling serves persistence, readout serves legibility, and the geometric phase conjectured in Section 6.7 is proposed as the generic compromise between them. The microcosm of Section 9.4 makes the connection quantitative through random-circuit code distance [42].

What no existing program supplies, and GCC is built to supply, is the conjunction: a *derived* dynamics with a *forced* dimension, an *operational* causal order, *observer-relative* states, and couplings that are *multipliers* — with a kill switch.

---

## 3 Kinematics: Record Structures

*(Tier I/II. Everything in this section is a definition, a proved lemma, or a proved proposition.)*

### 3.1 Records

**Definition 3.1 (Record structure).** A *record structure* is a tuple $R = (E, S, \mathrm{src}, \mathrm{tgt}, \dim, \{V_e\})$ where:

- $E$ is a countable set of **events** and $S$ a countable set of **systems** (wires);
- $\mathrm{src}: S \to E$ assigns to each system the unique event producing it, and $\mathrm{tgt}: S \rightharpoonup E$ is a partial map assigning to each system the event consuming it, if any; systems with $\mathrm{tgt}$ undefined are **dangling**;
- $\dim: S \to \{2,\dots,\chi\}$ assigns a finite dimension; we write $\mathcal{H}_s = \mathbb{C}^{\dim(s)}$, $\mathrm{in}(e) = \mathrm{tgt}^{-1}(e)$, $\mathrm{out}(e) = \mathrm{src}^{-1}(e)$, both finite;
- $V_e:\ \bigotimes_{s\in\mathrm{in}(e)}\mathcal{H}_s \to \bigotimes_{s\in\mathrm{out}(e)}\mathcal{H}_s$ is an **isometry**, $V_e^\dagger V_e = \mathbb{1}$, requiring $\prod_{\mathrm{out}}\dim \ge \prod_{\mathrm{in}}\dim$. Events with $\mathrm{in}(e)=\varnothing$ are **sources**; their isometry is a state preparation $|\psi_e\rangle$.

The **wiring** $W(R)$ is the directed multigraph on $E$ with one edge per system; we require $W$ acyclic — not an assumption about time, but the condition for compositions of the $\{V_e\}$ to be well-defined maps at all. The **capacity** of a wire is $c(s) = \log_2 \dim(s) \in [1, \log_2\chi]$, and of a set of wires, the sum.

No order beyond the wiring's reachability, no geometry, no dimension of space, and no global state appear in Definition 3.1.

**Definition 3.2 (Wire order, cuts, regions).** The reachability relation of $W$ induces a partial order on $S$: $s \le s'$ iff a directed path in $W$ leads from $\mathrm{src}(s')$'s side... precisely, $s < s'$ iff there is a directed path of events from $\mathrm{tgt}(s)$ (or $\mathrm{src}(s)$ if dangling logic requires) to $\mathrm{src}(s')$, or $\mathrm{tgt}(s) = \mathrm{src}(s')$. A **cut** $\Sigma$ is a maximal antichain of systems: a maximal set of pairwise incomparable wires; equivalently, a complete cross-section that every maximal directed path crosses exactly once. For cuts $\Sigma_1 \le \Sigma_2$ (every wire of $\Sigma_2$ in the weak future of $\Sigma_1$), the **region** $\mathcal{R}(\Sigma_1,\Sigma_2)$ is the set of events strictly between them, together with its sources.

**Lemma 3.3 (Order-independence of composition — Tier I).** For any finite region $\mathcal{R}(\Sigma_1,\Sigma_2)$, the composite
```math
V_{\Sigma_1\to\Sigma_2} \;=\; \overrightarrow{\prod_{e\,\in\,\mathcal{R}}} V_e\;:\;\; \mathcal{H}_{\Sigma_1} \longrightarrow \mathcal{H}_{\Sigma_2}
```
(3.1)
(with interior sources absorbed as preparations) is an isometry independent of the topological ordering of $E(\mathcal{R})$ used to define the product. *Proof.* Any two topological sorts of a finite acyclic graph are connected by adjacent transpositions of incomparable elements; incomparable events share no wires, so their isometries act on disjoint tensor factors and commute. Each $V_e$ is an isometry and compositions of isometries are isometries. $\square$

This four-line lemma does double duty: it is the algebraic seed of the block/becoming equivalence (Theorem 5.2), and it certifies that a record is a single mathematical object, not a process plus a schedule.

### 3.2 Causal order from information flow

The wiring is bookkeeping; the physical order is informational, in the operational sense of quantum causal models [55].

**Definition 3.4 (Causal influence).** For events $x \ne y$, let $\mathcal{N}^{\sigma}_{x\to y}: \mathcal{B}(\mathcal{H}_{\mathrm{out}(x)}) \to \mathcal{B}(\mathcal{H}_{\mathrm{in}(y)})$ be the channel obtained by composing the isometries of any region containing all directed paths from $x$ to $y$, feeding product state $\sigma$ into all side-inputs, and tracing out all wires not entering $y$. The **causal influence** is
```math
\mathcal{I}_C(x\!\to\!y) \;=\; \sup_{\sigma}\;\sup_{\rho,\rho'}\;\tfrac{1}{2}\big\|\,\mathcal{N}^\sigma_{x\to y}(\rho)-\mathcal{N}^\sigma_{x\to y}(\rho')\,\big\|_1\;\in[0,1],
```
(3.2)
and we write $x \prec y$ iff $\mathcal{I}_C(x\!\to\!y)>0$.

**Proposition 3.5 (Causality and order — Tier I).** (i) $\mathcal{I}_C(x\!\to\!y) > 0$ only if a directed wiring path runs from $x$ to $y$ (no signaling outside the wiring). (ii) $\prec$ is a strict partial order. *Proof.* (i) With no directed path, the composite channel factorizes so that the marginal on $\mathrm{in}(y)$ is independent of the input at $\mathrm{out}(x)$ — the standard no-signaling computation for isometric networks. (ii) Irreflexivity and acyclicity follow from (i) and acyclicity of $W$; transitivity holds for the reachability order, and we define $\prec$ as the restriction of reachability to pairs of nonzero influence closed under composition of influential paths. $\square$

**Definition 3.6 (Wiring gauge).** Two records are **gauge-equivalent** if there is a bijection of their cuts under which all cut-to-cut composites (3.1) agree up to local isometric relabeling of cut wires. Gauge moves include: composing an event with an isometry and its inverse split across a wire; merging incomparable events into one; re-routing through swaps.

**Proposition 3.7 (Invariance — Tier I).** The influence order, all cut-to-cut channels, and every quantity defined from them in this paper are invariants of wiring gauge. *Proof sketch.* Each listed gauge move leaves all composites (3.1) unchanged by construction; influence (3.2) is a functional of composites. $\square$

All physics in GCC is built from gauge invariants. This remark does silent but decisive work: a *foliation* is a property of a presentation of the wiring, hence pure gauge (Section 5.3).

### 3.3 Diamonds and their codes

**Definition 3.8 (Diamonds, shadows, cycles).** For $x \preceq y$, the **causal diamond** is $\Diamond(x,y)=\{z: x \preceq z \preceq y\}$; more generally a diamond is a region between comparable cuts. The **causal shadow** of a wire $w$ is the set of events and wires reachable from it. A **minimal cycle** is a pair of wire-disjoint directed paths between two events; the cycle content of a region is measured by the first Betti number $b_1$ of its undirected wiring skeleton. Forests have $b_1=0$.

Every diamond $\Diamond$ with past boundary $P=P(\Diamond)$ and future boundary $F=F(\Diamond)$ carries the encoding isometry $V_\Diamond: \mathcal{H}_P \to \mathcal{H}_F$ of (3.1). This makes every diamond a quantum code, and the rest of the paper exploits the dictionary.

**Definition 3.9 (Reconstructible algebra; exact and approximate correctability).** For $A \subseteq F$:
```math
\mathcal{A}_\Diamond(A)\;=\;\big\{\,O\in\mathcal{B}(\mathcal{H}_P)\;:\;\exists\,\tilde O\ \text{on}\ \mathcal{H}_A,\ \ V_\Diamond\,O \;=\; (\tilde O\otimes \mathbb{1}_{F\setminus A})\,V_\Diamond\,\big\}.
```
(3.3)
A region $X\subseteq F$ is **exactly correctable** if $\mathcal{A}_\Diamond(F\setminus X)=\mathcal{B}(\mathcal{H}_P)$; by the Knill–Laflamme conditions [32] and their operator-algebra generalization [33], this holds iff the encoded algebra satisfies $P_{\mathrm{code}}\,E^\dagger E'\,P_{\mathrm{code}} \propto P_{\mathrm{code}}$ for all operators $E,E'$ on $X$. Introducing a reference $R$ maximally entangled with $\mathcal{H}_P$ and the global pure state $|\Phi\rangle_{RF} = (\mathbb{1}_R \otimes V_\Diamond)|\Omega\rangle_{RP}$, $X$ is **$\epsilon$-correctable** iff it is decoupled,
```math
I(R\!:\!X)_{|\Phi\rangle}\;\le\;\epsilon,
```
(3.4)
in which case a recovery channel from $F\setminus X$ exists with fidelity $1-O(\sqrt{\epsilon})$ [34,35]. The **operational code distance** at tolerance $\epsilon$ is
```math
d_\epsilon(\Diamond)\;=\;\max\{\,w\;:\;\text{every}\ X\subseteq F\ \text{with}\ |X|\le w\ \text{is }\epsilon\text{-correctable}\,\}.
```
(3.5)

Two remarks. First, with $X=\varnothing$, recoverability is trivial: isometric evolution means a *complete* later cut always determines the past exactly. The physical content of persistence is therefore entirely in $w>0$: redundancy, not mere conservation. Second, in the Clifford realization (Appendix C) membership in (3.3), the conditions for (3.4), and the value of (3.5) under random erasure are all decidable in polynomial time by symplectic linear algebra over $\mathrm{GF}(2)$ [40].

**Definition 3.10 (Logical content of an event).** For an event $e$ inside $\Diamond$, the **content written at $e$** is the algebra of its source legs (the fresh preparations entering at $e$), encoded into $F$ by the composite downstream of $e$. C2 (Section 4.2) will quantify over both: the full input algebra of diamonds, and the written content of interior events.


---

## 4 The Constraint Quartet and the Generic Measure

*(Tier II for the definitions; Postulate G is the theory; the pinning statement is Tier III with a Tier I core.)*

Fix the two parameters of the framework: the **capacity bound** $\chi \in \mathbb{N}$ and the **tolerance** $\epsilon \in (0,1)$.

### 4.1 C1 — Unitarity

Embodied in Definition 3.1: events are isometries. We record it as an axiom because it is the entire content of "quantum mechanics is exact": no fundamental decoherence, no collapse, no information loss, no nonlinearity. Every later structure must be built from, not added to, isometric flow.

### 4.2 C2 — Persistence

**Axiom C2.** There exist constants $c>0$, $\eta>0$ and a depth $R_{\mathrm{dec}}(\epsilon)$ such that, for every causal ball $B_R$ (a diamond of proper radius $R$ in the emergent metric of C4) with $R \lesssim R_{\mathrm{dec}}$:
```math
d_\epsilon(B_R)\;\ge\;c\,R^{\eta},
```
(4.1)
for both the diamond's full input algebra and the written content (Definition 3.10) of every interior event at depth $\ge R/2$ from $F(B_R)$. We call $\eta$ the **persistence exponent**.

The axiom asserts that redundancy *deepens with scale*: not merely that information survives (unitarity already says so), but that it survives the loss of ever-larger fractions of the present. This is the formal content of "the past exists": it is encoded, at growing depth, in every adequate cross-section of the present, with no separate storage. The arrow of time, in GCC, is the gradient of this protection.

### 4.3 C3 — Finiteness and the two-fugacity weight

**Axiom C3.** All wire dimensions obey $\dim(s) \le \chi$ and all event arities are finite; profligacy is penalized not by hard caps but by fugacities: an **event cost** $\mu$ and a **capacity cost** $\iota$, entering the measure as
```math
w[R]\;=\;\exp\!\Big(-\,\mu\,|E(R)|\;-\;\iota \sum_{s\in S(R)} c(s)\Big).
```
(4.2)
Mean arity $\langle k \rangle$, mean wire dimension, and all connectivity statistics are thereby *outputs* of the measure rather than imposed structure. The two fugacities are not free parameters: Section 4.6 pins them, and Section 8 identifies them — $\mu$ with the cosmological constant, $\iota$ with $1/4G$. That the gravitational couplings appear already here, in the definition of the measure, as the prices of existence and of capacity, is the structural heart of Section 8.

### 4.4 C4 — Legibility

Legibility requires a construction (cells), an invariance (well-definedness), and three conditions (metricity, regularity, self-location).

**Cells.** Fix a scale $m_0$ and partition the wires of a cut $\Sigma$ into **cells** of at most $m_0$ wires; cells are the "places" of the cut. The states entering the following are the induced states of Definition 5.6.

**Distance estimator and world function.** For cells $x,y$ define the mutual information $\mathcal{I}(x,y) = S(\rho_x)+S(\rho_y)-S(\rho_{xy})$, the **distance estimator**
```math
s(x,y)\;=\;\xi\,\ln\frac{\mathcal{I}_0}{\mathcal{I}(x,y)},
```
(4.3)
with $\xi$ a calibration length and $\mathcal{I}_0$ a coincidence normalization, and the **information world function** $\sigma(x,y) = \tfrac{1}{2}\,s(x,y)^2$, Synge-normalized so that the coincidence limit of its mixed derivative is (minus) a metric (Section 6.1). The exponential form of (4.3) is calibrated to gapped correlation decay $\mathcal{I}\sim e^{-s/\xi}$; other decay laws redefine the estimator by a fixed monotone reparametrization, which the bi-Lipschitz clause below absorbs.

**Axiom C4.** There exist a cell scale $m_0$ and a scaling window $[\ell_{\mathrm{uv}}, \ell_{\mathrm{ir}}]$ on which, for every sufficiently large cut: (i) *(metricity)* $s(\cdot,\cdot)$ is a quasimetric of bounded distortion (symmetric up to constants; triangle inequality up to a constant $\kappa$); (ii) *(regularity)* it is Ahlfors regular: cell-counting ball volumes satisfy $V(r) \asymp r^{d_H}$ for a finite **legibility dimension** $d_H$, uniformly over the window [46]; (iii) *(self-location)* the wiring is local in this geometry: the systems touched by any single event lie within a bounded $s$-diameter $a_0$. Moreover *(well-definedness)* the bi-Lipschitz class of $s$, and hence $d_H$ and all geometric exponents, are independent of the admissible cell partition and of $m_0$ within the window.

Clause (iii) is the formal version of "adjacency is entanglement": the wiring must be local with respect to the geometry the correlations themselves define, so that neither graph nor state is prior to the other. The well-definedness clause acknowledges, and disposes of, the apparent circularity of cells: what the axiom demands is the existence of *one* admissible coarse-graining with these properties and the invariance of the resulting geometry across admissible choices — exactly the logical structure of demanding a thermodynamic limit. Philosophically, C4 is the observer axiom: a bounded internal protocol can address systems only relationally, through correlations; (i)–(ii) say addresses exist and have finite description length; (iii) says dynamics respects the address space.

### 4.5 Postulate G — the generic measure

**Postulate G.** Conditioned on a wiring and dimension assignment $(W,\dim)$, the event isometries are independently Haar-random (Clifford-random in the computable realization, a 3-design [41], hence agreeing with Haar for all observables used in this paper up to stated caveats). The marginal over $(W,\dim)$ is, at regulator size $n$,
```math
\boxed{\;
P_n[W,\dim]\;=\;\frac{1}{Z_n}\;
e^{-\mu |E| \;-\; \iota\, C_{\mathrm{tot}}}\;\;
\Phi_{\chi,\epsilon}[W,\dim],
\qquad
\Phi \;=\; \Pr_{\{V_e\}}\big[\,\mathrm{C2}\wedge\mathrm{C4}\ \text{hold}\,\big],\;}
```
(4.4)
over isomorphism classes with $|E| \le n$, where $C_{\mathrm{tot}} = \sum_s c(s)$ and $\Phi$ is the feasibility probability. The physical theory is the $n \to \infty$ limit. Microcanonically: the uniform measure on the feasible set at fixed $(\langle|E|\rangle, \langle C_{\mathrm{tot}}\rangle)$; we assume equivalence of ensembles (**Assumption 4.1**, standard but unproven here) and work grand-canonically.

Three comments. First, (4.4) contains *no* locality kernel, no connectivity weight, no density exponent, no candidate pool, no embedding, no gauge group, and no dimension: the free-parameter count is two, $(\chi,\epsilon)$. Second, genericity is doing physical work, not decoration: any structure in the ensemble beyond what C1–C4 force would be an unexplained fine-tuning, so Postulate G is the statement that *the laws are the constraints*. Third, the postulate is maximally exposed: if the feasible set is empty or supports no geometric phase, the theory is not adjustable. It is dead. Section 10 operationalizes this.

### 4.6 Critical pinning of the fugacities

The fugacities are fixed, not chosen. Let $\Omega_n(E,C)$ count feasible structures and define the feasible growth rate $\mu_c(\iota;\chi,\epsilon) = \lim_n \tfrac{1}{n}\ln \sum_C \Omega_n(n,C)e^{-\iota C}$ when it exists.

**Proposition 4.2 (Pinning — Tier I core, Tier III physics).** $Z_n$ converges as $n\to\infty$ iff $\mu \ge \mu_c$; for $\mu > \mu_c$ the measure concentrates on records of bounded expected size; an unbounded record — a universe — exists only at $\mu = \mu_c^{+}$. *Proof of the dichotomy:* immediate from the definition of the growth rate as the exponential rate of the feasible count: the grand sum is geometric-dominated. *Physics (Tier III):* the realized universe sits at the critical fugacity, $\mu = \mu_c(\iota)$, with $\iota$ likewise pinned to the boundary of normalizability in the capacity direction or rendered marginal there. Self-organized criticality is thus not an added hypothesis but the existence condition for an unbounded record.

Pinning has two consequences developed later: it removes $\mu,\iota$ from the parameter count (Section 8.1 measures them as response coefficients instead), and it is GCC's proposed mechanism for the cancellation of the Planckian cosmological constant (Conjecture 8.4): at $\mu=\mu_c$ the extensive part of the log-measure vanishes by definition of criticality, leaving only the sub-extensive residual that Section 8.5 identifies with observed dark energy.

---

## 5 Time, Observers, and the Two Presentations

*(Tier I for 5.1–5.2 as stated; Tier II constructions; one Tier III conjecture.)*

### 5.1 Proper time as chain depth

**Definition 5.1.** For $x \prec y$, the proper time is the longest-chain functional
```math
\tau(x,y)\;=\;\tau_0\,\max\{\,L\;:\;x=z_0\prec z_1\prec\cdots\prec z_L=y\,\},
```
(5.1)
the order-theoretic estimator that converges, in manifold-like orders, to geodesic proper time [31]. Duration in GCC is the depth of the influence order — relational, foliation-free, and gauge-invariant by Proposition 3.7.

### 5.2 Block and becoming

**Theorem 5.2 (Presentation equivalence — Tier I, finite case).** Let $P$ be any probability measure on isomorphism classes of finite records. Then: (i) there exists a frontier Markov process — a stochastic sequence of partial records, each obtained from its predecessor by adjoining one event at the frontier — whose law on completed records is $P$; (ii) any two such presentations are related by reorderings of influence-incomparable events; (iii) conversely, any frontier process whose completed-record law depends only on isomorphism class defines such a $P$. *Proof.* (i) Sample $R \sim P$; reveal its events along a uniformly random linear extension of the influence order; the conditional kernels $P(\text{next event}\,|\,\text{partial record})$ are well-defined ratios of $P$-masses of completions. (ii) Linear extensions of a finite poset are connected by adjacent transpositions of incomparable elements, which by Lemma 3.3 leave all physical composites unchanged. (iii) Immediate. $\square$

The theorem dissolves the block/becoming dichotomy as a matter of ontology: "block" (a measure over completed records) and "becoming" (a frontier process accumulating events) are presentations of one object, related by gauge. What survives as physics is a *property* of the becoming presentation:

**Conjecture 5.3 (Local becoming — Tier III).** In the geometric phase of the generic measure, the conditional kernels of Theorem 5.2(i) are quasi-local: the probability of the next event at a frontier location depends on the partial record only within a bounded $s$-distance, up to exponentially small tails. (Heuristically: locality of conditionals is spatial mixing of the measure, i.e. a finite correlation length — the same property C4 quantifies. A universe is locally becoming iff it is legible.)

Foliations, finally: a foliation is a choice of linear extension data — a presentation — and by Theorem 5.2(ii) all presentations are gauge-related. There is nothing in the ontology for a preferred foliation *to be*. The residual Lorentz question is statistical isotropy of the influence cones in the generic ensemble, with no microscopic frame anywhere in (4.4) to restore; capacity self-averaging suppresses any spontaneously selected frame, and the isotropy measurement of Section 10 is the test.

### 5.3 Observers, clocks, patches

**Definition 5.4 (Observer).** An *observer* is a directed chain of events $c = (e_1 \prec e_2 \prec \cdots)$ together with a designated logical register that each $e_i$ increments — a subsystem of the record encoding its own causal depth. Its **patch** is the diamond $\Diamond(c) = J^-(e_k) \cap J^+(e_1)$ between the chain's endpoints (growing with the chain), and its **patch algebra** is the algebra reconstructible on the data causally available to the chain, $\mathcal{A}(c) = \mathcal{A}_{\Diamond(c)}(F \cap J^-(e_k))$.

Observers are not bookkeeping: C4 promised the structure is legible to bounded internal protocols, and Definition 5.4 names the protocols. Patch entropies are finite-dimensional and well-defined; we note, as structural alignment rather than derivation, that in the continuum the inclusion of an observer's clock is precisely what renders horizon algebras Type II with well-defined entropies [51] — GCC's finite kinematics builds the clock in from the start.

### 5.4 The state net

**Definition 5.5 (Induced states).** For a cut $\Sigma$ of a finite record, the induced state is
```math
\rho_\Sigma \;=\; V_{\prec\Sigma}\,\Big(\bigotimes_{\text{sources}} |\psi\rangle\langle\psi|\Big)\,V_{\prec\Sigma}^{\dagger},
```
(5.2)
the push-forward of all source preparations through the past of $\Sigma$; for a region $A \subseteq \Sigma$, $\rho_A = \mathrm{Tr}_{\Sigma\setminus A}\,\rho_\Sigma$. By Lemma 3.3 and causality, $\rho_A$ depends only on the past wiring of $A$ — the construction is gauge-invariant and relativistically sane.

**Definition 5.6 (State net and complementarity).** The fundamental state-assignment of GCC is the net $\Diamond \mapsto \omega_\Diamond = \rho_{P(\Diamond)}$-evolved data on $\Diamond$'s boundaries, subject to the **consistency condition** $\omega_{\Diamond'}|_{\Diamond} = \omega_\Diamond$ for $\Diamond \subseteq \Diamond'$, implemented by the encoding isometries — a finite-dimensional net of states in the sense of local quantum physics [58]. A global state is the inverse limit of the net *when it exists*; **complementarity is the statement that the limit can fail across horizon-separated patches** with no inconsistency in the net itself. Physics is patch-complete: every measurable quantity is a functional of some $\omega_\Diamond$, and GCC declines to assert a whole. This is the framework's de Sitter posture [51,52], adopted at the level of kinematics.


---

## 6 Geometry from Legibility

*(Tier I for Theorems 6.5–6.6 and Propositions 6.8–6.10 as stated; Tier II constructions; Tier III for Conjecture 6.11.)*

### 6.1 Metric

On a cut, with the distance estimator $s$ and world function $\sigma = \tfrac12 s^2$ of (4.3), the spatial metric is the Synge coincidence limit
```math
h_{ij}(x)\;=\;-\,\lim_{y\to x}\,\frac{\partial}{\partial x^i}\frac{\partial}{\partial y^j}\,\sigma(x,y),
```
(6.1)
where the derivatives are discrete differences along cell directions within the scaling window, and positivity of $h$ is equivalent to monotone decay of mutual information in all directions — a property of the generic ensemble to be measured, not assumed. Temporal structure is supplied by chain depth (5.1) and the influence cones; the candidate Lorentzian geometry is their assembly, and the signature question is Section 7.3. The continuum license for building geometry from order plus counting is the Malament–Hawking–King–McCarthy theorem [29,30]: causal order and volume measure determine a Lorentzian metric. GCC supplies exactly those two ingredients — influence order, event counting — plus the spatial calibration (6.1).

We write $d_H$ for the Ahlfors dimension of cuts (C4) and define the **spacetime dimension** $D = 1 + d_H$. Spectral and walk dimensions are defined gauge-invariantly on the metric measure space (cells, $s$, event-counting measure) via its heat kernel, with the consistency relation $d_w = 2 d_H / D_s$ available as a cross-check; we do *not* define them on the wiring skeleton, which is gauge.

### 6.2 Areas and the inherited entropy law

**Definition 6.1 (Area as min-cut).** For a surface $\gamma$ partitioning a cut into $A$ and $\bar A$,
```math
\mathrm{Area}(\gamma)\;=\;\min_{c\,:\,c\ \mathrm{severs}\ A\ \mathrm{from}\ \bar A}\;\sum_{s\in c} c(s),
```
(6.2)
the minimal total capacity of wires whose removal disconnects $A$'s past from $\bar A$'s within the relevant diamond; by max-flow/min-cut duality this equals the maximal information flux, the discrete bit-thread statement [47].

**Theorem 6.5 (Inherited Ryu–Takayanagi — Tier I, imported).** For records with Haar or random-stabilizer event isometries on a fixed wiring, the entanglement entropy of a boundary region $A$ in the induced state (5.2) equals the minimal cut (6.2) to leading order at large capacity, with computable corrections; this is the random tensor network theorem of Hayden et al. [11] (the second Rényi entropy maps exactly to an Ising partition function whose low-temperature free energy is the min-cut; the von Neumann statement follows at large bond dimension). GCC inherits the theorem wholesale because Postulate G makes the universe a random tensor network whose wiring is itself drawn from (4.4). With C2 the statement carries full error-correction structure — entanglement-wedge reconstruction in the sense of [9,10,12]. Entropy $=$ area is therefore a *starting point* of this framework, not a target.

### 6.3 The dimension floor

**Lemma 6.4 (Boundary scaling — Tier I, from C4).** In the geometric phase, the future boundary of a causal ball $B_R$ contains $n_F(R) \le s_0\, R^{\,d_H}$ cells: the boundary is a codimension-one set in a $(d_H{+}1)$-dimensional order, and Ahlfors regularity with the self-location clause bounds its cell count by the volume of a $d_H$-dimensional region of extent $R$. (Proof in Appendix B; the constant absorbs cone geometry and cell size.)

**Theorem 6.6 (Dimension floor — Tier I).** Suppose C2 holds with exponent $\eta$ (Eq. 4.1, exact case $\epsilon=0$; the $\epsilon>0$ statement holds with $O(\epsilon)$ corrections by continuity of the bound) and C4 holds with legibility dimension $d_H$. Then
```math
\boxed{\;\eta \;\le\; d_H \;=\; D-1,
\qquad\text{i.e.}\qquad
D \;\ge\; 1+\eta\;.}
```
(6.3)
*Proof.* The diamond code of $B_R$ encodes $k \ge 1$ logical units into $n = n_F(R)$ boundary wires with distance $d \ge cR^\eta$ (C2). The quantum Singleton bound [32,60] gives $d \le (n-k)/2 + 1 \le n/2 + 1$. With Lemma 6.4, $cR^\eta \le s_0 R^{d_H}/2 + 1$ for all $R$ in the window, forcing $\eta \le d_H$. $\square$

*Interpretation.* The demand that records deepen with scale forces room for them: **space exists because the past insists on surviving.** Linear persistence ($\eta=1$) forces $D \ge 2$; a memoryless universe ($\eta \to 0$) may collapse to a line; and Section 9.4 exhibits a microcosm saturating the bound. Bravyi–Poulin–Terhal-type tradeoffs [36] strengthen (6.3) for codes with geometrically local generators; we note them as refinements, not requirements — the floor itself needs only Singleton and counting.

### 6.4 The tree–expander dichotomy

Why should the generic constrained record have *any* finite dimension? The two failure modes bracket the answer, and the full development sharpens them into a complementarity principle: **legibility is local readability of one observable sector; persistence is protection of its conjugate; and these are no-cloning rivals.** Cells must broadcast enough about each other to define distance (C4), while logical content must be invisible to any small region (C2, via decoupling (3.4)). The question is which wirings can host both. We give three Tier I propositions and the principle they support.

**Proposition 6.8 (Forests with local generators have bounded distance — Tier I, stabilizer setting).** Let the diamond code of $B_R$ be a stabilizer code whose generators are supported on metrically bounded sets (radius $r_0$), on a wiring with $b_1(B_R)=0$. Then $d(B_R) \le w_0(r_0,\chi)$, independent of $R$. *Proof sketch (Appendix B).* The Bravyi–Terhal cleaning lemma [36] cleans any correctable bounded region; on a forest, the nerve of bounded regions has trivial first homology, so cleanings compose along a spanning sweep without obstruction, contracting any logical representative to bounded support; a logical operator of bounded support bounds the distance. Cycles are exactly what obstruct the sweep — in the toric code [38], the obstruction *is* the logical operator. $\square$

**Proposition 6.9 (Broadcast trees fail conjugate persistence — Tier I, by computation).** Let a tree wiring achieve inter-cell legibility by broadcasting a basis: an event copies $\{|z\rangle\}$ into $m \ge 2$ branches with bias $\delta$ (the mechanism by which cell–cell mutual information, hence (4.3), is generated on a tree). Then there exists a single bounded cell $X_0$ with $I(R\!:\!X_0) \ge g(\delta) > 0$, so $d_\epsilon = O(1)$ for $\epsilon < g(\delta)$. *Proof.* Broadcast data is, by definition, locally readable: the cell carrying one branch's copy has classical correlation $g(\delta)$ with the reference's $Z$-sector, violating decoupling (3.4). The minimal instance is computed in full in Section 9.3 (GHZ): one erased leaf carries one full bit about $R$. The conjugate ($X$-sector) information is then bounded *above* by information–disturbance: what is readable everywhere is protected nowhere. $\square$

**Proposition 6.10 (Expanders are illegible — Tier I).** Let the wiring skeleton of cuts have Cheeger constant $h>0$ (an expander family [45]). Then ball volumes grow exponentially, no finite $d_H$ satisfies Ahlfors regularity, and C4(ii) fails; moreover, by Theorem 6.5 and Page-typicality [48], pairwise cell mutual information is exponentially small in system size, so the estimator (4.3) carries no signal: C4(i) fails too. $\square$

Expanders are the persistence champions — asymptotically good quantum LDPC codes are expander-based [37] — and they are unreadable from inside: optimal memory, no geography. Forests are the readability extreme — broadcast structure is cheap — and cannot protect the conjugate sector, while *random* trees protect well but correlate cells not at all (Section 9.3). The lesson:

**The compromise principle.** C2 pulls the wiring toward expansion; C4 pulls it toward broadcast locality; no-cloning forbids having both maximally. Cycles are the currency of the compromise: a cycle lets one sector circulate redundantly (loop operators, protected) while its conjugate is read locally (cut operators, legible) — the toric-code mechanism [38], here promoted from a code design to a cosmogonic principle. **Geometry is the compromise between being readable and being remembered.**

### 6.5 The criticality window

**Conjecture 6.11 (Criticality window — Tier III, the central physical claim).** The feasible set $\{(W,\dim): \Phi_{\chi,\epsilon}>0\}$ is nonempty for some region of the $(\chi,\epsilon)$ plane, and on it the generic measure (4.4) concentrates on wirings of finite emergent dimension
```math
D^{*}(\chi,\epsilon)\;\in\;[\,1+\eta,\;\infty\,),
```
(6.4)
the generic point of the window between the forest phase (persistence fails: Propositions 6.8–6.9) and the expander phase (legibility fails: Proposition 6.10), with all order parameters — $\eta$, $d_H$, $D_s$, code rate — efficiently measurable in the Clifford realization.

We state plainly what is and is not claimed. It is *not* claimed that $D^* = 4$; no argument here selects four, and any decoration pretending otherwise would smuggle the answer into the question. What *is* claimed is anti-circularity: since no dimension, density exponent, embedding, or layer structure appears anywhere in (4.4), a measured $D^*$ cannot be transduced from the inputs — there is nothing to transduce. Growth-law models must scan their density exponents and embeddings to exonerate an emergent dimension; GCC has nothing to scan. Either the constraints force a dimension, and we will measure it; or they force none, and the theory dies. A measured dependence $D^*(\chi,\epsilon)$, or scale-drift of the effective $D^*$ across the window — plausible, since the persistence demand weakens at short scales where there is less past to protect — would itself be a discovery, the latter being this framework's native mechanism for ultraviolet dimensional reduction, rhyming with the flow reported across discrete approaches [24,25]. The measurement-transition literature [44] provides the nearest existing analogue of the conjectured phase structure: there, too, a readable phase and a scrambled phase meet at a critical surface, and GCC's wager is that the gravitational universe lives on it.


---

## 7 Gauge Structure, Matter, and Signature

*(Tier I for 7.1's structure theorem and 7.5 as stated; Tier III for the census, matter, and signature conjectures.)*

### 7.1 Gauge symmetry as the commutant of the encoded algebra

**Definition 7.1 (Gauge group of a diamond).** With $\mathcal{M}_\Diamond = V_\Diamond \mathcal{B}(\mathcal{H}_P) V_\Diamond^\dagger$ the encoded algebra on $\mathcal{H}_F$,
```math
\mathcal{G}(\Diamond) \;=\; \mathcal{U}\big(\mathcal{M}_\Diamond'\big)
\;=\;\big\{\,U\in\mathcal{U}(\mathcal{H}_F)\;:\;[U,\,V_\Diamond O V_\Diamond^\dagger]=0\ \ \forall O\,\big\},
```
(7.1)
the unitaries of the commutant: transformations that move nothing decodable — pure redundancy, which is what gauge symmetry *is*. This is the gauge group in the sense of operator-algebra quantum error correction [33].

**Proposition 7.2 (Structure — Tier I).** Decompose $\mathcal{H}_F = \bigoplus_\alpha \mathcal{H}^{(\alpha)}_{\mathrm{log}} \otimes \mathcal{H}^{(\alpha)}_{\mathrm{junk}} \oplus \mathcal{H}_\perp$ adapted to $\mathcal{M}_\Diamond$ (finite-dimensional von Neumann structure theorem). Then $\mathcal{G}(\Diamond) \cong \prod_\alpha \mathcal{U}(\mathcal{H}^{(\alpha)}_{\mathrm{junk}}) \times \mathcal{U}(\mathcal{H}_\perp)$, modulo phases. The physically relevant part is the junk factor: redundancy entangled with, but not informative about, the logical content. $\square$

**Definition 7.3 (Local gauge and holonomy).** The **local gauge groupoid** $\mathcal{G}_{\mathrm{loc}}$ is generated by elements of $\mathcal{G}(\Diamond)$ supported on metrically bounded sets. A **holonomy class** is an element of $\mathcal{G}(\Diamond)$ expressible as a product of local elements around a cycle but not contractible through local moves — an obstruction class on the wiring's cycle space. On forests every local-gauge product is contractible (trivial first homology); holonomy lives on $b_1 > 0$.

**Co-emergence, in final form.** Combining Definition 7.3 with Section 6.4: cycles simultaneously generate (i) nontrivial holonomy (gauge field content), (ii) growing code distance for full algebras (protection), and (iii) min-cut degeneracy (area structure, via Theorem 6.5). *Gauge, protection, and geometry are one phenomenon viewed three ways* — the **co-emergence principle** — and its skeleton follows from Definitions 3.9, 6.1, and 7.1 alone, with nothing installed by hand. The microcosm of Section 9.2 exhibits all three on a single loop, where the code's stabilizers are literally its Wilson loops.

**Conjecture 7.4 (Gauge census — Tier III, computable).** In large generic diamonds of the constrained ensemble, the junk factors organize, by Schur–Weyl-type typicality, into unitary factors $\mathcal{U}(N_J)$ with ranks set by capacity, and the holonomy structure on the emergent geometry organizes into a lattice gauge theory of these factors. Which compact groups appear, with what multiplicities and capacity scaling, is the **gauge census** — a defined computation (Section 10, P4), and the route by which unitary gauge factors emerge as outputs rather than axioms. (For emergent gauge structure from local constraints, compare [38,39].)

### 7.2 Matter as superselection sectors, with a gatekeeper

Matter, in this framework, can only be one thing: equivalence classes of logical content that are locally created, locally transported, and globally obstructed — superselection sectors of the code net, the record-theoretic descendants of anyons [38]. The program: classify the stable defect classes of generic constrained records; their fusion and braiding data are the emergent matter content. In emergent dimension $2{+}1$ this is a finite computation on Clifford records (syndrome homology classes; Section 10, P4).

We name the gatekeeper: **Nielsen–Ninomiya** [53]. Chiral fermions cannot inhabit a naive discrete substrate; the known escapes are interaction-driven symmetric mass generation [53] and anomaly inflow from one dimension up [54]. GCC possesses, structurally and for free, the one ingredient inflow wants and Euclidean lattices lack: an intrinsic orientation — the arrow of the influence order, the direction in which records accumulate. **Conjecture (chirality from the arrow — Tier III):** the time-orientation of the generic record functions as a one-sided boundary for its defect sectors, so that emergent matter is chiral with content constrained by cancellation of the record's own gravitational anomalies. This is the paper's boldest conjecture, and the only mechanism we know of by which the Standard Model's exact anomaly cancellations could be read as a fingerprint of substrate consistency rather than coincidence.

### 7.3 Signature

Frameworks in this lineage typically postulate Lorentzian signature at the algebraic level. GCC declines the input and derives what it can.

*Spatial positivity* of $h_{ij}$ is monotone mutual-information decay (Section 6.1) — measurable, and expected generically wherever C4 holds. The substantive question is *temporal uniqueness*: why exactly one time?

**Definition (bi-temporal order).** A record is bi-temporal at scale $R$ if its influence order contains an order-embedded $\mathbb{N}\times\mathbb{N}$ grid of side $R$ — two transversal families of cuts, each satisfying C2 with the same written content $L$, such that some region $Y$ required for $L$-recovery in one slicing lies inside an allowed erasure $X$ of the other (the **crossing condition**: one slicing's protected bulk is the other's erasable margin).

**Proposition 7.5 (No bi-temporal persistence — Tier I, conditional on crossing).** Under the crossing condition, C2 in both slicings at tolerance $\epsilon$ forces $2\log d_L - \epsilon \le I(R\!:\!Y) \le I(R\!:\!X) \le \epsilon$, hence $\epsilon \ge \log d_L$: persistence of any content fails in at least one time direction. *Proof.* Recovery of $L$ from $Y$ requires $I(R\!:\!Y) \ge 2\log d_L - \epsilon$ (decoupling converse [34,35]); erasability of $X \supseteq Y$ requires $I(R\!:\!X)\le\epsilon$ (3.4); monotonicity of mutual information under restriction closes the chain. $\square$

**Conjecture 7.6 (Generic crossing — Tier III).** Bi-temporal wirings generically satisfy the crossing condition — transversality of the slicings is precisely the statement that one's spatial margins are the other's temporal bulk — so the generic feasible record has exactly one temporal direction: emergent signature $(D{-}1,\,1)$.

More bluntly: with no order there is no "later" from which to decode, so C2 is not false but inapplicable — *a record is what time looks like from inside* — and with two orders the decoding demands collide with monogamy. The signature of spacetime, on this reading, is the unique solution to the requirement that the universe be able to remember itself.

---

## 8 Gravitation as the Thermodynamics of the Constraint Set

*(Tier I for Proposition 8.2 as stated; the derivation chain, pinning cancellation, and seesaw are Tier III with the gap named.)*

### 8.1 Couplings as multipliers; response definitions

Postulate G admits no couplings, so every macroscopic coupling must be a Lagrange multiplier of C1–C4 in (4.4). The two gravitational constants are already there:
```math
\boxed{\;\Lambda \;\leftrightarrow\; \mu\ \ \text{(the price of events)},
\qquad
\frac{1}{4G}\;\leftrightarrow\;\iota\ \ \text{(the price of capacity)}.\;}
```
(8.1)
Pinning (Proposition 4.2) fixes the fugacities; their physical values are then *measured* as response coefficients of the realized ensemble: $\mu = -\partial \ln P/\partial |E|$ along feasibility-preserving variations, $\iota = \partial S_{\mathrm{ens}}/\partial C_{\mathrm{cut}}$ — entropy gained per unit of capacity added to a cut. The second identification can be read as a definition rediscovered: $1/4G$ *is* the areal density of information — the Bekenstein relation [3], demoted from mystery to bookkeeping — realizing the induced-gravity intuition [19] as capacity accounting, with the effective species number appearing as $\log\dim$ of a generic cell rather than as an axiom.

### 8.2 The diamond first law

**Proposition 8.2 (First law — Tier I as stated).** Let $S[\mathfrak{g}]$ denote the log-multiplicity of feasible records compatible with coarse data $\mathfrak{g}$ (geometry of a small diamond $\Diamond$, its boundary capacity $C_{\partial\Diamond}$, its event number $N_\Diamond$, and sector charges $Q_a$). At the max-ent saddle of (4.4), first-order stationarity against all feasibility-preserving variations gives
```math
\delta S_\Diamond \;=\; \iota\,\delta C_{\partial\Diamond} \;-\;\mu\,\delta N_\Diamond\;-\;\sum_a \lambda_a\,\delta Q_a,
```
(8.2)
for every small diamond. *Proof.* Gibbs measures are characterized by stationarity of entropy at fixed constraint values; (8.2) is the Legendre statement of (4.4) localized to the constraint functionals, which are sums of local terms (capacity on cuts, events in regions, charges in sectors). $\square$

By Theorem 6.5, $S_\Diamond$ is the min-cut at leading order, and $\delta C_{\partial\Diamond}$ *is* $\delta\mathrm{Area}(\partial\Diamond)$ in capacity units: (8.2) is the first law of (causal-diamond) thermodynamics, $\delta S = \delta A/4G - (\mu/\text{vol quantum})\,\delta V + \text{matter}$, derived rather than posited.

### 8.3 The Einstein equations: the chain and the gap

The chain: (i) Proposition 8.2 holds for every small diamond; (ii) Theorem 6.5 converts the capacity term to geometric area; (iii) matter-sector variations enter through diamond modular Hamiltonians, $\delta S_{\mathrm{matter}} = \delta\langle K_\Diamond\rangle$ to first order [16]; (iv) demanding (8.2) for all small diamonds and all variations that coarse-grain to metric perturbations yields, by Jacobson's entanglement-equilibrium argument [14] and its holographic verification at linearized order [15], the Einstein equations
```math
G_{\mu\nu} + \Lambda\,g_{\mu\nu} \;=\; 8\pi G\,T^{(\mathrm{sector})}_{\mu\nu},
```
(8.3)
with $G$ and $\Lambda$ given by (8.1) in the units of Appendix D. **The named gap (Tier III):** step (iv) requires that feasibility-preserving microscopic variations span, after coarse-graining, the full space of metric variations — equation-of-state completeness. GCC's advantage over prior thermodynamic derivations is not that the gap vanishes but that both of its sides are finite and explicit: the microstates are records, the entropies computable, the variation space enumerable in the Clifford realization (Section 10, P5). If the gap closes, general relativity is the equation of state of genericity: gravity as the economics of legibility, with $G$ the price of area and $\Lambda$ the rent on existence.

### 8.4 Horizons, black-hole entropy, evaporation

A **horizon** is a decoding boundary: the surface beyond which an observer's patch cannot, within tolerance $\epsilon$, reconstruct interior logical content. By Theorem 6.5 the entropy assigned to it is the min-cut; by (8.1) the min-cut in physical units is $\mathrm{Area}/4G$. The Bekenstein–Hawking law is thus the composition of an inherited theorem with an accounting identity — no independently matched countings, no separately posited entropy law; the measure does the work. Evaporation is the frontier presentation progressively re-exposing logical content to the exterior patch, Hayden–Preskill style [49]; Page-curve behavior [48,50] for finite Clifford records is a computation, not a hope (Section 10, P5).

### 8.5 The cosmological constant: cancellation by pinning, residual by tolerance

The cosmological constant problem splits in two, and GCC addresses each with a different mechanism.

**The Planckian piece (Conjecture 8.4 — Tier III).** Naively, $\Lambda \sim \mu \times$(event density) is microscopic-scale enormous. But Proposition 4.2 pins $\mu = \mu_c$: at criticality the *extensive* part of the log-measure vanishes — that is what criticality means — so the bulk vacuum term cancels identically, not by tuning but by the existence condition for an unbounded record. A universe large enough to ask the question has, necessarily, already cancelled its Planckian $\Lambda$.

**The residual piece (the seesaw — Tier III).** What survives at criticality is sub-extensive: C2 holds only to tolerance $\epsilon$, so decoding fails beyond a depth
```math
R_{\mathrm{dec}}(\epsilon)\;\sim\;\ell_0\,\epsilon^{-1/\eta}
```
(8.4)
(the scale at which required distance outruns available distance, for per-cell infidelity accumulating against (4.1)), leaving of order one unresolved quantum of correlation per cell of that depth: a residual energy density $\rho_{\mathrm{res}} \sim \hbar c\,/R_{\mathrm{dec}}^4$, gravitating through (8.3):
```math
\Lambda \;\simeq\; \frac{8\pi\,\ell_P^2}{R_{\mathrm{dec}}^4}
\qquad\Longrightarrow\qquad
R_{\mathrm{dec}} \;=\;\Big(\frac{8\pi\,\ell_P^2}{\Lambda_{\mathrm{obs}}}\Big)^{1/4}\;\approx\;40\text{–}90\;\mu\mathrm{m},
```
(8.5)
(Appendix D for the arithmetic), the framework's flagship laboratory corridor: $R_{\mathrm{dec}}$ is tied to a fundamental parameter ($\epsilon$, through (8.4)), and $\Lambda$ is computed twice — as pinned-residual fugacity and as gravitating remainder — yielding the consistency surface $\mu_c$–$\epsilon$–$\eta$ that Section 10 (P5) tests.

**The laboratory consequence.** Any finite-range Yukawa deviation from Newtonian gravity must sit at $40$–$90\,\mu$m, squarely on the active torsion-balance frontier [59], with amplitude model-dependent pending the fluctuation analysis. One scale; two phenomena (dark energy, sub-mm gravity); two independent derivations of $\Lambda$ whose agreement is the content of the consistency surface.

### 8.6 Phenomenological ledger

| Observable | Status in GCC | Assessment |
| --- | --- | --- |
| $\Lambda_{\mathrm{obs}}$ | Planckian part cancelled by pinning; residual fixes $R_{\mathrm{dec}}\approx 40$–$90\,\mu$m | Mechanism conjectural; one parameter combination absorbed |
| Sub-mm inverse-square tests | Yukawa **range predicted**; amplitude open | Flagship target; on the current experimental frontier [59] |
| $\dot G/G$, BBN/CMB | Constrain cosmological drift of $\iota$ | Mild constraint pending fluctuation analysis |
| Lorentz-violation searches | Statistical cone isotropy with no microscopic frame to restore | Test defined (P3); failure would falsify |
| UV dimensional flow | Scale-drift of $D^*$ native to the window | Structural; shared qualitatively with [24,25] |


---

## 9 Worked Microcosms

*(Tier I throughout: every claim in this section is an explicit finite computation or an immediate consequence of one. These four miniatures are the formalism's unit tests.)*

### 9.1 The chain: pure time cannot remember

Take $E = \{e_1, e_2, \dots\}$, each event with one input wire and one output wire of dimension $\chi$, wired in a line; no branching, no sources after $e_1$. The influence order is total, $\tau(e_i,e_j) = \tau_0|j-i|$ exactly, and $b_1 = 0$. Every cut is a single wire, so every cell partition is one cell: $d_H = 0$, $D = 1$. The diamond code of any ball $B_R$ encodes $\mathcal{H}_P$ into a single wire: erasing that one wire erases everything, so by (3.5), $d_\epsilon(B_R) = 0$ for all $R$ and every $\epsilon < 2\log\chi$. C2 fails for every $\eta > 0$: $\Phi_{\chi,\epsilon}[\text{chain}] = 0$. The gauge group is trivial ($\mathcal{M}_\Diamond = \mathcal{B}(\mathcal{H}_F)$, commutant $= \mathbb{C}$), there is no protection, and there is no space — co-emergence read in the negative, and the dimension floor (6.3) read at its base case: **a universe of pure time is infeasible.** Persistence is the demand for parallel carriers, and parallel carriers are the embryo of space.

### 9.2 The minimal diamond: the $[[4,2,2]]$ code as a loop

The smallest record exhibiting all three faces of co-emergence is a single cycle. Events: $p$ with $\mathrm{in}(p) = P$ (two logical qubits) and $\mathrm{out}(p)$ = four qubits; route qubits $\{1,2\}$ along **arm $A$** and qubits $\{3,4\}$ along **arm $B$** to event $q$ (each arm may pass through an intermediate identity event to make the two wire-disjoint paths explicit); $F = \mathrm{out}(q)$, four qubits. Choose the composite $V_\Diamond: \mathcal{H}_P \to \mathcal{H}_F$ to be the $[[4,2,2]]$ encoder with codewords
```math
|\overline{00}\rangle = \tfrac{|0000\rangle + |1111\rangle}{\sqrt2},\quad
|\overline{10}\rangle = \tfrac{|1010\rangle + |0101\rangle}{\sqrt2},\quad
|\overline{01}\rangle = \tfrac{|1100\rangle + |0011\rangle}{\sqrt2},\quad
|\overline{11}\rangle = \tfrac{|0110\rangle + |1001\rangle}{\sqrt2},
```
(9.1)
stabilizers $S_X = XXXX$, $S_Z = ZZZZ$, and logical representatives $\bar X_1 = XIXI$, $\bar Z_1 = ZZII$, $\bar X_2 = XXII$, $\bar Z_2 = ZIZI$. Now read the operators geometrically:

- **Loops are gauge.** $S_X = (X_1X_2)\cdot(X_3X_4)$: an arc along arm $A$ times an arc along arm $B$ — a closed loop around the diamond $p \to A \to q \to B \to p$. It commutes with every logical, acts as the identity on the code space, and is therefore an element of $\mathcal{G}(\Diamond)$ (7.1): a holonomy. Likewise $S_Z$.
- **Open arcs are charged.** The arm-$A$ arc alone, $X_1X_2 = \bar X_2$, is a *logical* operator: it moves decodable content. Open the loop and gauge becomes matter — Definition 7.3's contractibility criterion, in four qubits.
- **Rungs are the conjugates.** $\bar Z_2 = Z_1Z_3$ touches one wire on each arm — a rung crossing the loop — and anticommutes with $\bar X_2$ at their single overlap.
- **The cut is degenerate.** Two minimal cuts of equal capacity ($\log_2 = 2$ each) separate $p$ from $q$: arm $A$ and arm $B$. Min-cut degeneracy is the area structure the loop creates.
- **Protection.** $d = 2$, saturating the quantum Singleton bound $d \le (n-k)/2 + 1 = 2$ [32,60]: every single-wire erasure is *exactly* correctable, $I(R\!:\!X) = 0$ for $|X| = 1$ by the stabilizer decoupling check. The cycle is the smallest structure for which this is possible: collapse either arm and Proposition 6.8's cleaning bounds the distance below 2.

One loop; gauge, geometry, and memory, simultaneously and inseparably. This is the co-emergence principle at $n = 4$.

### 9.3 Trees: the dichotomy, computed

**Broadcast tree (legible, unprotected).** Event $e$: one logical qubit, copied by the isometry $V|z\rangle = |zzz\rangle$ into three leaves. With reference $R$ maximally entangled to the logical input, the global state is $|\Phi\rangle = (|0\rangle_R|000\rangle + |1\rangle_R|111\rangle)/\sqrt2$. Compute everything:
```math
\rho_{R3} = \tfrac12\big(|00\rangle\langle00| + |11\rangle\langle11|\big)
\;\;\Rightarrow\;\;
I(R\!:\!3) = S_R + S_3 - S_{R3} = 1 + 1 - 1 = 1\ \text{bit}.
```
(9.2)
Decoupling (3.4) fails by a full bit for a single leaf: no single-wire erasure is tolerable for any $\epsilon < 1$. The complementarity identity for pure $\rho_{RF}$, $I(R\!:\!X) + I(R\!:\!F\setminus X) = 2S_R$, then gives $I(R\!:\!12) = 2 - 1 = 1 < 2S_R$: the two surviving leaves retain the classical bit but not the qubit — the erased leaf carried the phase away. Meanwhile the leaves are *mutually* legible: $\rho_{12} = \tfrac12(|00\rangle\langle00| + |11\rangle\langle11|)$ gives $I(i\!:\!j) = 1$ bit for **every** pair — and that is its own pathology: the distance estimator (4.3) is the same constant for all pairs, a simplex rather than a geometry, failing Ahlfors regularity outright. Broadcast buys readability with cloned data, and cloned data is, by the computation above, conjugately naked: Proposition 6.9 in the flesh.

**Random tree (protected, illegible).** Replace the copier by Haar/Clifford isometries on a binary tree with bond capacity $\log\chi$ and fresh sources at each node. For leaf-cells $x, y$ in disjoint subtrees, the minimal cut homologous to $\{x,y\}$ is the pair of their own bonds (severing the common ancestor's bond would sever siblings too), so Theorem 6.5 gives $S(xy) \simeq S(x) + S(y)$ and
```math
I(x\!:\!y)\;\simeq\;0\quad\text{(exponentially small in capacity, by the fluctuation analysis of [11]).}
```
(9.3)
Bulk-injected content is well scrambled — erasing any bounded-neck subtree is typically correctable, Page-style [48] — but no pair of places knows anything about each other: $s(x,y) = \infty$ everywhere, C4 dead.

Trees thus offer a strict either/or: legible-classical or protected-anonymous. Cycles (9.2) are what let one sector circulate as protected loops while its conjugate is read locally — the compromise principle of Section 6.4, now verified at both extremes.

### 9.4 The brickwork: a world on the floor

Wire a line of qubits with a depth-$T$ brickwork of two-qubit random Clifford events, sources entering at the initial cut. A causal ball $B_R$ is a lightcone diamond: height $R$, base $\sim 2R$ sites, future boundary $n_F \sim 2R$ wires. So $d_H = 1$, $D = 2$. For the distance: rigorously, $d(B_R) \le 2R + 1$, because a depth-$R$ local circuit maps any logical input operator to a representative supported on its lightcone, and a bounded-support logical representative bounds the distance. Attainment of linear scaling, $d(B_R) = \Theta(R)$ against typical erasures, is supported by the random-circuit coding theorems of Brown–Fawzi [42] and by operator-growth hydrodynamics [43]. Granting it, $\eta = 1$ and
```math
D \;=\; 2 \;=\; 1 + \eta:
```
(9.4)
the brickwork *saturates* the dimension floor (6.3). One spatial dimension is exactly enough room for linearly deepening memory and not one bit more — Lineland is marginal, the boundary case of Theorem 6.6.

The caveat completes the lesson: run the brickwork long without readout and the state goes volume-law — pairwise cell mutual information dies and C4 fails, the temporal analogue of the expander pathology [43,44]. A brickwork that is simultaneously persistent *and* legible must balance scrambling against readable structure — which is precisely the critical-window tension of Conjecture 6.11, here visible in the simplest possible laboratory, and the reason the measurement-transition literature is the nearest existing physics to GCC's conjectured phase diagram.

---

## 10 The Computational Program

*(Tier II. Everything here is a defined, polynomial-time computation in the Clifford realization — Appendix C. The protocol is published in advance of execution, with interpretations bound now, so that the computations adjudicate rather than decorate.)*

### 10.1 Machinery

**Representation.** A record is a wiring DAG plus, per event, a symplectic matrix over $\mathrm{GF}(2)$ (its Clifford isometry) [40]. Induced states (5.2) of any cut are stabilizer states; entropies of regions are $\mathrm{GF}(2)$ rank computations; erasure correctability (3.4)–(3.5) is Gaussian elimination, $O(n^3)$ per check; min-cuts (6.2) are max-flow. All observables of Sections 5–8 reduce to these primitives, applied per-diamond (balls of $10^3$–$10^4$ events) inside records of $10^5$–$10^6$ events — within reach of commodity hardware.

**Sampling.** Metropolis–Hastings on $(W, \dim)$ targeting (4.4): proposal moves are event insertion/deletion (weight $e^{\mp\mu}$), wire-dimension shifts ($e^{\mp\iota\,\Delta c}$), degree-preserving rewirings, and source insertion; the feasibility factor $\Phi$ is estimated per proposal by Monte Carlo over Clifford draws — run the erasure decoder on sampled erasures (C2 estimator) and the metric regression on sampled cell pairs (C4 estimator: quasimetric violation rate, Ahlfors fit over the window). The fugacities are located, not chosen: $\mu$ is tuned to the critical value where mean record size diverges (Proposition 4.2), operationalizing pinning.

### 10.2 Protocol, with pre-registered readings

**P1 — Feasibility map (the kill switch).** Scan the $(\chi,\epsilon)$ plane; estimate where $\Phi > 0$ with nonvanishing density at growing size. *Readings:* a nonempty region is the theory's license to exist; an empty map at all accessible sizes, robust to decoder and estimator improvements, is the death of the framework, to be reported as such. No parameter exists to rescue it.

**P2 — Dimension.** Within the feasible region, measure $d_H$ (ball-volume regression), $D_s$ (heat kernel on the metric measure space), $\eta$ (regression of $\log d_\epsilon(B_R)$ on $\log R$), and the consistency $d_w = 2d_H/D_s$. *Readings:* the floor $\eta \le d_H$ must hold — violation indicts the estimators or the formalization, and is reported either way. A stable finite $D^*(\chi,\epsilon)$ vindicates Conjecture 6.11 and is the central result of the program *whatever its value*; $D^* \approx 4$ anywhere in the plane identifies a candidate physical point; scale-drift of $D^*$ is reported as the framework's dimensional-flow prediction [24,25]. The measurement is anti-circular by construction: no dimension, density exponent, embedding, or layer schedule exists anywhere upstream to leak into it.

**P3 — Signature and isotropy.** (i) Search sampled records for bi-temporal sublattices (order-embedded grids with crossed persistence); their generic absence supports Conjecture 7.6, their stable presence falsifies it. (ii) Measure influence-cone statistics across realizations; the frame-variance must shrink with capacity (self-averaging) — a realization-stable frame at large capacity falsifies the emergent-Lorentz claim, with no foliation available to blame (Theorem 5.2).

**P4 — Gauge and matter census.** Compute commutant structure (7.1) of large diamonds: junk-factor ranks $N_J$ versus $\chi$, tested against the Schur–Weyl expectation (Conjecture 7.4). In windows where $D^* \approx 3$, enumerate defect classes of the code net (syndrome homology), with fusion tables — the first matter census.

**P5 — Gravitational thermodynamics.** Measure $\iota$ and $\mu$ as response coefficients (entropy per unit capacity on cuts; log-weight per event); verify the first law (8.2) across diamond ensembles; test pinning cancellation (does the extensive part of the log-measure vanish at the located $\mu_c$?); test the seesaw by comparing the residual-energy and fugacity routes to $\Lambda$ on the same ensemble (the consistency surface of Section 8.5); run the Page protocol — sequentially expose a region's wires, track $I(R\!:\!\text{exposed})$ — against [48,50].

**P6 — Presentations.** Implement both samplers of the same measure — completed-record Metropolis and frontier growth with estimated conditionals — and verify observable identity (Theorem 5.2 in silico); measure the locality radius of the frontier conditionals against the correlation length (Conjecture 5.3).

The discipline is fixed in advance: no result will be claimed before it exists, all numbers will ship with seeds and error bars, and the interpretations above bind us.


---

## 11 Discussion: Objections and Replies

**(i) "C4 installs geometry by fiat."** C4 demands the *existence* of some metric with some finite dimension; it fixes no value of the dimension, no curvature, no signature, no locality scale, and no symmetry. The logical shape is that of demanding a thermodynamic limit: a substantive existence requirement that selects no phase. The bite is double: C4 is falsifiable by emptiness (P1), and its anti-circularity is structural — nothing in (4.4) carries a dimension that could leak into $D^*$. What C4 does install, deliberately, is the observer: it converts "the universe contains bounded systems that can locate themselves" from anthropic afterthought into a constraint with a multiplier.

**(ii) "Where is the Born rule?"** GCC supplies a classical probability measure over records and quantum states within each patch. Frequencies for internal observers should emerge along decoherence/envariance lines [56] applied to patch states, and the frontier presentation supplies a natural "happening" to which chances attach. Identifying the measure's conditionals with Born weights is an open problem — here as everywhere in physics. What GCC contributes is locality of the question: it must be posed on finite patch states, where the decoherence machinery applies without idealization. (For reconstructions of spacetime from Hilbert-space structure alone, with which GCC shares the quantum-first orientation, see [57].)

**(iii) "There is no Hamiltonian."** Correct, and by design: a global Hamiltonian would require a global time, which is gauge (Theorem 5.2). Time is depth; dynamics is the measure. Local energetics is modular: small-diamond modular Hamiltonians [16] supply the matter terms of (8.2)–(8.3), and "energy conservation" is first-law bookkeeping. The Hamiltonian is an infrared bookkeeping device, not a fundamental object — exactly its status in general relativity, where it is a boundary term.

**(iv) "Ensemble equivalence and pinning are assumed."** Yes: Assumption 4.1 and the physical half of Proposition 4.2 are open, standard-statistical-mechanics-shaped, and tested in P5. We regard "the universe sits at the critical fugacity because only there is it unbounded" as the framework's most attractive unproven idea: it converts the existence of a large world from initial condition into selection principle, and cancels a Planckian $\Lambda$ as a corollary (Conjecture 8.4).

**(v) "Why Haar — and is Clifford a cheat?"** Haar is what "no further structure" means, given C1. Clifford is the computable surrogate, exact for the entropic and code-theoretic observables used throughout (a 3-design [41]) but with flat entanglement spectra; observables sensitive to higher moments or spectral shape (some fluctuation corrections to Theorem 6.5) are flagged in Appendix C, and controlled injection of non-Clifford resource ("magic") into the sampler is listed as a robustness check on universality. If the geometric phase exists only at fine-tuned non-generic isometries, Postulate G is false and the framework dies honestly.

**(vi) "Relation to AdS/CFT?"** GCC is a bulk-only, asymptotics-free cousin: random tensor networks were built as anti-de Sitter toys [9,11], and wherever the constrained ensemble develops hyperbolic windows the holographic dictionary should apply verbatim. GCC removes the boundary anchor and replaces conformal boundary conditions with constraint thermodynamics; its native habitat is the de Sitter-like, observer-patch regime [51,52] where standard holography is hardest. The two programs are complementary tests of one creed — geometry is entanglement bookkeeping — in opposite asymptotic regimes.

**(vii) "Is this background independent?"** Yes, in the strong sense: no manifold, no fixed graph, no preferred time, no chosen state. Even the wiring is gauge (Proposition 3.7). The residual background is the constraint quartet itself plus $(\chi,\epsilon)$ — that is, the theory. A critic may relocate the complaint there; we accept the relocation as progress, since axioms, unlike backgrounds, can be argued about one at a time.

**(viii) "Lorentz invariance kills discrete models; why not this one?"** Because the usual victim — a microscopic foliation — does not exist here to be killed (Theorem 5.2): any frame would have to be *spontaneously* selected by a realization, and capacity self-averaging predicts its suppression. This is a prediction, not an immunity: P3 measures cone-statistics isotropy, and a realization-stable frame at large capacity falsifies the framework. We prefer a theory that can die of this to one that cannot be asked.

**(ix) "Two parameters is two too many."** Perhaps. Large-$\chi$ universality may remove $\chi$ (all sufficiently rich substrates flow to the same window), and $\epsilon$ may be pinned to the window's edge by a marginality condition, as $\mu$ is pinned by existence. If both mechanisms operate, GCC is parameter-free; we record this as a conjecture with a defined test — the $(\chi,\epsilon)$-dependence maps of P1–P2.

---

## 12 Conclusion

This paper has developed, in full, a framework whose entire content is: *quantum mechanics, exactly; records that persist redundantly; finite capacity; legibility from inside; and nothing else.* From these we have derived the kinematics of causal order without presupposing it (Section 3); dissolved the foliation and the block/becoming dichotomy as gauge (Theorem 5.2); inherited the entropy-area law as a theorem (Theorem 6.5); proved that persistence forces spatial dimension, $D \ge 1+\eta$ (Theorem 6.6); located geometry as the generic compromise between readability and memory, with cycles as its currency and the $[[4,2,2]]$ diamond as its atom (Sections 6.4, 9.2); defined gauge structure as the commutant of the decodable and matter as its sectors (Section 7); derived the diamond first law from genericity (Proposition 8.2) and the Einstein equations modulo one named gap (Section 8.3); split the cosmological constant problem into a piece cancelled by critical pinning and a residual that predicts a sub-millimeter corridor (Sections 8.5, Appendix D); and bound the whole to a computational protocol with a kill switch (Section 10).

We close by applying the framework's standard to itself. That the *genre* is right — that the deep theory is a finite, generic, self-decoding quantum record — is, in our judgment, the best-motivated wager in quantum gravity: every load-bearing ingredient is an established result of the last thirty years, and this paper assembles them, for the first time, into a single mechanism with a single derivation of its own dynamics. That *this exact quartet* is the final axiom set is a sharper claim, and the paper names its own pressure points — equation-of-state completeness, generic crossing, the window itself — because a theory that knows where it would break is stronger for saying so. And the program is *decidable*: every conjecture above survives or dies by a computation specified in Section 10. Few programs in quantum gravity can say that; it is the sentence the framework was designed to earn.

The universe, on this account, is the most random thing that can still read itself. Space is the depth of its memory; gauge fields are its redundancies; gravity is its economics; and time is the only direction in which a record can grow.

---

## Appendix A — Notation

| Symbol | Meaning | Defined |
| --- | --- | --- |
| $R, E, S$ | record; events; systems (wires) | Def. 3.1 |
| $V_e$ | event isometry | Def. 3.1 |
| $W$, $b_1$ | wiring multigraph; cycle content | Def. 3.1, 3.8 |
| $c(s), C_{\mathrm{tot}}$ | wire capacity $\log_2\dim$; total capacity | §3.1, (4.2) |
| $\mathcal{I}_C, \prec$ | causal influence; influence order | Def. 3.4 |
| $\Sigma$, $\Diamond$, $P/F$ | cut; diamond; past/future boundaries | Defs. 3.2, 3.8 |
| $\mathcal{A}_\Diamond(A)$ | algebra reconstructible on $A$ | (3.3) |
| $d_\epsilon$ | operational code distance | (3.5) |
| $\chi, \epsilon$ | capacity bound; tolerance — the two parameters | §4 |
| $\eta$ | persistence exponent | (4.1) |
| $\mu, \iota$ | event and capacity fugacities ($\Lambda$, $1/4G$) | (4.2), (8.1) |
| $\Phi$ | feasibility probability | (4.4) |
| $s, \sigma, h_{ij}$ | distance estimator; world function; metric | (4.3), (6.1) |
| $d_H, D, D_s, d_w$ | legibility, spacetime, spectral, walk dimensions | §6.1 |
| $\tau$ | proper time (longest chain) | (5.1) |
| $\rho_\Sigma, \omega_\Diamond$ | induced states; state net | (5.2), Def. 5.6 |
| $\mathcal{G}(\Diamond)$ | gauge group (commutant) | (7.1) |
| $R_{\mathrm{dec}}, \ell_0, \ell_P$ | decoding depth; substrate and Planck lengths | (8.4), App. D |

## Appendix B — Proofs and Computations

**B.1 (Lemma 3.3).** Done in text; the only addition: interior sources are absorbed by tensoring their preparations as inputs, which commute with everything by disjointness of supports.

**B.2 (Proposition 3.5(i)).** If no directed path runs $x \to y$, choose a topological order placing all of $y$'s ancestry before $x$ (possible by acyclicity). The composite channel into $\mathrm{in}(y)$ is then a contraction of isometries none of which has $\mathrm{out}(x)$ in its causal past; the marginal is manifestly independent of the state fed at $\mathrm{out}(x)$, so the supremum (3.2) vanishes.

**B.3 (Lemma 6.4).** The future boundary of $B_R$ is the union, over depth $t \in [0,R]$, of codimension-one shells of the shrinking cone. By C4(ii) (Ahlfors regularity, uniform over the window) a shell of radius $r$ carries $\le \kappa\, r^{d_H - 1}$ cells of bounded size, and by C4(iii) each boundary event occupies $O(1)$ cells. Summing, $n_F \le \kappa' \sum_{t \le R}(R-t)^{d_H-1} \le s_0 R^{d_H}$.

**B.4 (Theorem 6.6, details).** Quantum Singleton [32,60]: an $((n,K,d))$ code over local dimension $q$ obeys $\log_q K \le n - 2(d-1)$, hence $d \le (n - \log_q K)/2 + 1 \le n/2 + 1$; the bound is no-cloning: two disjoint correctable sets of size $d-1$ each would clone. For $\epsilon > 0$, the decoupling characterization (3.4) plus the recovery converse [34,35] degrade the bound by additive $O(\sqrt{\epsilon}\,\log d_L)$ terms, which do not affect the exponent comparison: $cR^\eta \le s_0R^{d_H}/2 + O(\sqrt\epsilon \log\chi) + 1$ still forces $\eta \le d_H$ in the scaling window.

**B.5 (Proposition 6.8, sketch).** Cleaning lemma [36]: for a stabilizer code, a correctable region $X$ admits, for every logical class, a representative supported on $X^c$. Tile $B_R$'s boundary by bounded regions $\{X_i\}$ (correctable by hypothesis when $d > w_0$); on a forest, the nerve of the tiling is itself a forest, so cleanings can be composed along a leaf-to-root sweep with no cycle ever forcing a region to be re-occupied. The sweep contracts any logical representative into a single bounded region, so $d \le w_0(r_0,\chi)$ — contradiction with growing distance. Cycles obstruct the sweep, and the obstruction class *is* the loop logical, as in the toric code [38]; the $[[4,2,2]]$ microcosm (9.2) is the minimal instance.

**B.6 (Section 9.3, GHZ).** With $|\Phi\rangle = (|0\rangle_R|000\rangle + |1\rangle_R|111\rangle)/\sqrt2$: every single-system marginal is maximally mixed ($S = 1$); every two-system marginal among $\{R,1,2,3\}$ is $\tfrac12(|00\rangle\langle00| + |11\rangle\langle11|)$ ($S = 1$); hence $I = 1$ bit for every pair, and for pure $\rho_{RF}$, $I(R\!:\!X) + I(R\!:\!F\setminus X) = 2S_R = 2$ distributes one classical bit to each side of any cut. All statements of 9.3 follow.

**B.7 (Proposition 7.5).** Recovery of the logical from $Y$ with fidelity $1-\epsilon$ implies, by the converse direction of decoupling/recoverability [34,35], $I(R\!:\!Y) \ge 2\log d_L - f(\epsilon)$ with $f(\epsilon) = O(\sqrt\epsilon \log d_L)$; erasability of $X$ at tolerance $\epsilon$ is $I(R\!:\!X) \le \epsilon$ (3.4); the crossing condition $Y \subseteq X$ and monotonicity of mutual information under partial trace give $2\log d_L - f(\epsilon) \le I(R\!:\!Y) \le I(R\!:\!X) \le \epsilon$, impossible for $\epsilon$ below an absolute threshold once $d_L \ge 2$.

**B.8 (Section 9.2, checks).** The codewords (9.1) are the simultaneous $+1$ eigenstates of $XXXX$ and $ZZZZ$; the displayed logicals commute with both stabilizers and obey $\{\bar X_a, \bar Z_a\} = 0$, $[\bar X_a, \bar Z_b] = 0$ for $a \ne b$ (overlap counting). Weight-2 logicals exist ($\bar X_2$), so $d = 2$ exactly; correctability of every single-wire erasure follows from $d = 2$ and is verified by the rank check of Appendix C.

## Appendix C — The Clifford Toolkit

A stabilizer state on $n$ qubits is the joint $+1$ eigenstate of an abelian group $\mathcal{S} \subset \mathcal{P}_n$ with $2^n$ elements, represented by a binary symplectic tableau; Clifford isometries act by symplectic transformations over $\mathrm{GF}(2)$, composable in $O(n^2)$ per event [40]. The primitives used by Section 10:

- **Entropies.** For a stabilizer state with group $\mathcal{S}$ and region $A$: $S(\rho_A) = |A| - \log_2|\mathcal{S}_A|$, where $\mathcal{S}_A$ is the subgroup supported inside $A$ — a $\mathrm{GF}(2)$ rank computation. All Rényi entropies coincide (flat spectrum): convenient for computation, and a known caveat against Haar, whose fluctuation corrections to Theorem 6.5 carry spectral shape [11].
- **Correctability.** Erasure region $X$ is correctable iff no logical-class representative is supported on $X$ — i.e., the projection of the logical group onto $X$'s coordinates intersects the stabilizer projection trivially: Gaussian elimination, $O(n^3)$, exact, with $I(R\!:\!X)$ obtainable from the same ranks.
- **Min-cuts.** Max-flow with capacities $c(s)$ on the wiring; polynomial.
- **Genericity grade.** The Clifford group is an exact unitary 3-design [41]: all observables in this paper defined through second moments of the state (entropies of stabilizer ensembles, decoupling checks, min-cut comparisons) agree with Haar; higher-moment observables and spectral-shape corrections are flagged wherever used, and magic injection (controlled non-Clifford gates) is the listed robustness probe (§11(v)).

## Appendix D — Units, Identifications, and the Seesaw Arithmetic

Set $\hbar = c = 1$; let $\ell_0 \equiv \xi$ be the calibration length of (4.3), $\bar c$ the mean capacity per boundary cell, and $n_0$ the mean event count per $\ell_0^4$ cell ($D = 4$ throughout this appendix).

**Newton's constant.** Entropy $=$ min-cut (Theorem 6.5) assigns $\bar c\,\iota$ nats per boundary cell of proper area $\ell_0^2$; matching $S = \mathrm{Area}/4G$ gives $1/4G = \iota\bar c/\ell_0^2$, i.e. $\ell_P^2 = \ell_0^2/(4\iota\bar c)$: large capacity price places the substrate scale *above* the Planck length, $\ell_0 = 2\sqrt{\iota\bar c}\;\ell_P$.

**Cosmological constant.** The event-cost term contributes vacuum log-weight density $\mu n_0/\ell_0^4$, matching the effective-action term $\Lambda/8\pi G$; so $\Lambda = 8\pi G\,\mu n_0/\ell_0^4$ — Planckian-enormous at generic $\mu$, *identically cancelled in its extensive part at the pinned value $\mu = \mu_c$* (Proposition 4.2, Conjecture 8.4), since criticality is by definition the vanishing of the extensive free energy. The surviving sub-extensive residual is the decoding deficit of Section 8.5.

**The corridor.** From (8.5) with $\ell_P^2 = 2.612 \times 10^{-70}\,\mathrm{m}^2$ and $\Lambda_{\mathrm{obs}} \approx 1.1 \times 10^{-52}\,\mathrm{m}^{-2}$:
```math
R_{\mathrm{dec}} = \big(\ell_P^2/\Lambda\big)^{1/4} \approx 39\,\mu\mathrm{m},
\qquad
R_{\mathrm{dec}} = \big(8\pi\,\ell_P^2/\Lambda\big)^{1/4} \approx 88\,\mu\mathrm{m},
```
(D.1)
the $O(1)$-convention band quoted throughout as $40$–$90\,\mu$m. This is arithmetic on the observed $\Lambda$, not a simulation result; the framework's content is that the *same* scale must appear as the decoding depth (8.4) and as a Yukawa range at the torsion-balance frontier [59].


---

## References

[1] J. A. Wheeler, "Information, physics, quantum: the search for links," in *Complexity, Entropy and the Physics of Information*, ed. W. Zurek (Addison-Wesley, 1990).

[2] E. T. Jaynes, "Information theory and statistical mechanics," *Phys. Rev.* **106**, 620 (1957).

[3] J. D. Bekenstein, "Black holes and entropy," *Phys. Rev. D* **7**, 2333 (1973).

[4] R. Bousso, "The holographic principle," *Rev. Mod. Phys.* **74**, 825 (2002).

[5] G. 't Hooft, "Dimensional reduction in quantum gravity," arXiv:gr-qc/9310026; L. Susskind, "The world as a hologram," *J. Math. Phys.* **36**, 6377 (1995).

[6] S. Ryu and T. Takayanagi, "Holographic derivation of entanglement entropy from AdS/CFT," *Phys. Rev. Lett.* **96**, 181602 (2006).

[7] M. Van Raamsdonk, "Building up spacetime with quantum entanglement," *Gen. Rel. Grav.* **42**, 2323 (2010).

[8] B. Swingle, "Entanglement renormalization and holography," *Phys. Rev. D* **86**, 065007 (2012).

[9] F. Pastawski, B. Yoshida, D. Harlow, and J. Preskill, "Holographic quantum error-correcting codes: toy models for the bulk/boundary correspondence," *JHEP* **06**, 149 (2015).

[10] A. Almheiri, X. Dong, and D. Harlow, "Bulk locality and quantum error correction in AdS/CFT," *JHEP* **04**, 163 (2015).

[11] P. Hayden, S. Nezami, X.-L. Qi, N. Thomas, M. Walter, and Z. Yang, "Holographic duality from random tensor networks," *JHEP* **11**, 009 (2016).

[12] D. Harlow, "Jerusalem lectures on black holes and quantum information," *Rev. Mod. Phys.* **88**, 015002 (2016).

[13] T. Jacobson, "Thermodynamics of spacetime: the Einstein equation of state," *Phys. Rev. Lett.* **75**, 1260 (1995).

[14] T. Jacobson, "Entanglement equilibrium and the Einstein equation," *Phys. Rev. Lett.* **116**, 201101 (2016).

[15] T. Faulkner, M. Guica, T. Hartman, R. C. Myers, and M. Van Raamsdonk, "Gravitation from entanglement in holographic CFTs," *JHEP* **03**, 051 (2014).

[16] H. Casini, M. Huerta, and R. C. Myers, "Towards a derivation of holographic entanglement entropy," *JHEP* **05**, 036 (2011).

[17] E. Verlinde, "On the origin of gravity and the laws of Newton," *JHEP* **04**, 029 (2011).

[18] T. Padmanabhan, "Thermodynamical aspects of gravity: new insights," *Rep. Prog. Phys.* **73**, 046901 (2010).

[19] A. D. Sakharov, "Vacuum quantum fluctuations in curved space and the theory of gravitation," *Dokl. Akad. Nauk SSSR* **177**, 70 (1967); reprinted *Gen. Rel. Grav.* **32**, 365 (2000).

[20] L. Bombelli, J. Lee, D. Meyer, and R. D. Sorkin, "Space-time as a causal set," *Phys. Rev. Lett.* **59**, 521 (1987).

[21] D. P. Rideout and R. D. Sorkin, "Classical sequential growth dynamics for causal sets," *Phys. Rev. D* **61**, 024002 (2000).

[22] S. Surya, "The causal set approach to quantum gravity," *Living Rev. Rel.* **22**, 5 (2019).

[23] L. Bombelli, J. Henson, and R. D. Sorkin, "Discreteness without symmetry breaking: a theorem," *Mod. Phys. Lett. A* **24**, 2579 (2009).

[24] J. Ambjørn, J. Jurkiewicz, and R. Loll, "Spectral dimension of the universe," *Phys. Rev. Lett.* **95**, 171301 (2005).

[25] S. Carlip, "Dimension and dimensional reduction in quantum gravity," *Class. Quantum Grav.* **34**, 193001 (2017).

[26] T. Konopka, F. Markopoulou, and L. Smolin, "Quantum graphity," arXiv:hep-th/0611197.

[27] C. A. Trugenberger, "Combinatorial quantum gravity: geometry from random bits," *JHEP* **09**, 045 (2017).

[28] S. Lloyd, *Programming the Universe* (Knopf, 2006).

[29] D. B. Malament, "The class of continuous timelike curves determines the topology of spacetime," *J. Math. Phys.* **18**, 1399 (1977).

[30] S. W. Hawking, A. R. King, and P. J. McCarthy, "A new topology for curved space-time which incorporates the causal, differential, and conformal structures," *J. Math. Phys.* **17**, 174 (1976).

[31] G. Brightwell and R. Gregory, "Structure of random discrete spacetime," *Phys. Rev. Lett.* **66**, 260 (1991); J. Myrheim, "Statistical geometry," CERN preprint TH-2538 (1978).

[32] E. Knill and R. Laflamme, "Theory of quantum error-correcting codes," *Phys. Rev. A* **55**, 900 (1997).

[33] D. Kribs, R. Laflamme, and D. Poulin, "Unified and generalized approach to quantum error correction," *Phys. Rev. Lett.* **94**, 180501 (2005).

[34] C. Bény and O. Oreshkov, "General conditions for approximate quantum error correction and near-optimal recovery channels," *Phys. Rev. Lett.* **104**, 120501 (2010).

[35] O. Fawzi and R. Renner, "Quantum conditional mutual information and approximate Markov chains," *Commun. Math. Phys.* **340**, 575 (2015).

[36] S. Bravyi, D. Poulin, and B. Terhal, "Tradeoffs for reliable quantum information storage in 2D systems," *Phys. Rev. Lett.* **104**, 050503 (2010); S. Bravyi and B. Terhal, "A no-go theorem for a two-dimensional self-correcting quantum memory based on stabilizer codes," *New J. Phys.* **11**, 043029 (2009).

[37] P. Panteleev and G. Kalachev, "Asymptotically good quantum and locally testable classical LDPC codes," *Proc. STOC 2022*; arXiv:2111.03654.

[38] A. Kitaev, "Fault-tolerant quantum computation by anyons," *Ann. Phys.* **303**, 2 (2003).

[39] M. A. Levin and X.-G. Wen, "String-net condensation: a physical mechanism for topological phases," *Phys. Rev. B* **71**, 045110 (2005).

[40] D. Gottesman, "The Heisenberg representation of quantum computers," arXiv:quant-ph/9807006; S. Aaronson and D. Gottesman, "Improved simulation of stabilizer circuits," *Phys. Rev. A* **70**, 052328 (2004).

[41] Z. Webb, "The Clifford group forms a unitary 3-design," arXiv:1510.02769; H. Zhu, "Multiqubit Clifford groups are unitary 3-designs," *Phys. Rev. A* **96**, 062336 (2017).

[42] W. Brown and O. Fawzi, "Short random circuits define good quantum error correcting codes," arXiv:1312.7646.

[43] A. Nahum, J. Ruhman, S. Vijay, and J. Haah, "Quantum entanglement growth under random unitary dynamics," *Phys. Rev. X* **7**, 031016 (2017).

[44] B. Skinner, J. Ruhman, and A. Nahum, "Measurement-induced phase transitions in the dynamics of entanglement," *Phys. Rev. X* **9**, 031009 (2019); Y. Li, X. Chen, and M. P. A. Fisher, "Quantum Zeno effect and the many-body entanglement transition," *Phys. Rev. B* **98**, 205136 (2018).

[45] S. Hoory, N. Linial, and A. Wigderson, "Expander graphs and their applications," *Bull. Amer. Math. Soc.* **43**, 439 (2006).

[46] J. Heinonen, *Lectures on Analysis on Metric Spaces* (Springer, 2001).

[47] M. Freedman and M. Headrick, "Bit threads and holographic entanglement," *Commun. Math. Phys.* **352**, 407 (2017).

[48] D. N. Page, "Information in black hole radiation," *Phys. Rev. Lett.* **71**, 3743 (1993).

[49] P. Hayden and J. Preskill, "Black holes as mirrors: quantum information in random subsystems," *JHEP* **09**, 120 (2007).

[50] G. Penington, "Entanglement wedge reconstruction and the information paradox," *JHEP* **09**, 002 (2020); A. Almheiri, N. Engelhardt, D. Marolf, and H. Maxfield, "The entropy of bulk quantum fields and the entanglement wedge of an evaporating black hole," *JHEP* **12**, 063 (2019).

[51] V. Chandrasekaran, R. Longo, G. Penington, and E. Witten, "An algebra of observables for de Sitter space," *JHEP* **02**, 082 (2023).

[52] T. Banks and W. Fischler, "Holographic space-time," arXiv:1109.2435. [CHECK: verify this is the intended HST reference and identifier before circulation.]

[53] H. B. Nielsen and M. Ninomiya, "Absence of neutrinos on a lattice. (I) Proof by homotopy theory," *Nucl. Phys. B* **185**, 20 (1981); J. Wang and Y.-Z. You, "Symmetric mass generation," *Symmetry* **14**, 1475 (2022). [CHECK: confirm the SMG review's journal/volume before circulation.]

[54] C. G. Callan and J. A. Harvey, "Anomalies and fermion zero modes on strings and domain walls," *Nucl. Phys. B* **250**, 427 (1985).

[55] J.-M. A. Allen, J. Barrett, D. C. Horsman, C. M. Lee, and R. W. Spekkens, "Quantum common causes and quantum causal models," *Phys. Rev. X* **7**, 031021 (2017); F. Costa and S. Shrapnel, "Quantum causal modelling," *New J. Phys.* **18**, 063032 (2016).

[56] W. H. Zurek, "Decoherence, einselection, and the quantum origins of the classical," *Rev. Mod. Phys.* **75**, 715 (2003).

[57] S. M. Carroll and A. Singh, "Quantum mereology: factorizing Hilbert space into subsystems with quasiclassical dynamics," *Phys. Rev. A* **103**, 022213 (2021). [CHECK: confirm article number before circulation.]

[58] R. Haag, *Local Quantum Physics: Fields, Particles, Algebras*, 2nd ed. (Springer, 1996).

[59] E. G. Adelberger, B. R. Heckel, and A. E. Nelson, "Tests of the gravitational inverse-square law," *Annu. Rev. Nucl. Part. Sci.* **53**, 77 (2003); J. G. Lee et al., "New test of the gravitational $1/r^2$ law at separations down to 52 μm," *Phys. Rev. Lett.* **124**, 101101 (2020); W.-H. Tan et al., "Improvement for testing the gravitational inverse-square law at the submillimeter range," *Phys. Rev. Lett.* **124**, 051301 (2020).

[60] E. M. Rains, "Nonbinary quantum codes," *IEEE Trans. Inf. Theory* **45**, 1827 (1999).
