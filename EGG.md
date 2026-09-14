# Entanglement–Gauge Gravity: A Co-Emergence Hypothesis for Causal, Entanglement, and Gauge-Topological Geometry

**September 2026**

---

## Abstract

We reformulate Entanglement–Gauge Gravity (EGG) around a single microscopic object: a growing directed acyclic graph (DAG) whose events are isometries on finite quantum registers. Three independent geometric structures live on this object and can be computed without assuming a continuum. The **order geometry** is read from the causal order and vertex counting alone: if the order approximates that of a distinguishing Lorentzian manifold, the causal relation fixes the conformal geometry and counting fixes the volume element, exactly as in causal-set theory, so the task is to test manifold-likeness rather than to manufacture a metric. The **cut geometry** is read from the isometric encoding that growth defines: the entanglement of any frontier region is bounded by, and at large bond dimension equals, the minimal cut through the network, so cut areas and the depth of minimal-cut surfaces are the entanglement geometry of the state. The **topological geometry** is read from a $\mathbb{Z}_2$ gauge theory on the growing two-complex of vertices, edges, and locally filled short cycles: its number of logical qubits is the $\mathbb{Z}_2$-dimension of the first homology of the complex, and its code distance is the size of the smallest non-contractible cycle or cocycle.

The EGG hypothesis is that suitable causal growth produces a scaling regime in which these three independently defined structures become mutually compatible: manifold-like Lorentzian order, manifold-compatible cut geometry (area scaling and wedge depth consistent with the order dimension), and a face-rule-stable, low-rank homology all describing one low-dimensional space. Cycles are required for non-trivial holonomy and for the homological code, and a single-seed tree has a one-dimensional order, but cycles do not by themselves guarantee geometry and a tree can still encode information; the hypothesis is therefore not loop proliferation but the simultaneous organization of causal, entanglement, and topological observables into a common phase. We further show that the growth schedule of earlier versions induces an expansion history of the frontier, and we present a measurement-conditioned growth rule under which that rate becomes local and state-dependent — a proof of principle for state-dependent causal growth that places EGG in contact with the theory of monitored quantum circuits, and the framework's only candidate route to backreaction.

No new simulations are reported. Legacy spectral-dimension values from Version 2 are retained as unreproduced measurements with unknown uncertainty, and we note a plausible non-geometric explanation (unbounded out-degree in the regulated model) that the programme must exclude. The continuum targets of earlier versions — teleparallel gravity, induced Newton constant, horizon entropy, a cosmological seesaw — are confined to one conditional section. The programme is staged by cost, with cheap combinatorial tests on existing graphs placed first, so that the central hypothesis can be falsified before any quantum simulation is run.

---

## 1 Introduction

### 1.1 The object

EGG proposes that spacetime is the large-scale description of a growing causal network carrying quantum information. Versions 2 and 3 of this framework [1,2] introduced most of the ingredients — stochastic causal growth, internal connection variables, an isometric encoding, and a programme of dimension measurements — but did not isolate what the theory is actually about. Version 2 identified geometry with a holonomy bilinear that vanishes identically (Appendix A), gauge structure with a Lorentz-group weight that is not normalizable (Appendix B), and code structure with a scalar flatness weight that defines no code. Version 3 corrected each of these but replaced them with nothing, leaving a benchmark without a thesis.

This version begins from the object that survives both critiques. Let $G_t$ be a DAG built layer by layer. Each vertex $v$ is an *event*: it consumes quantum registers ("ports") from earlier vertices and produces new ones. Reading the growth law as a circuit, $G_t$ is an isometry
$$
V_t:\ \mathcal{H}_{\mathrm{seed}}\longrightarrow\bigotimes_{\ell\in\mathrm{cut}(t)}\mathcal{H}_\ell,
$$
from a small logical space to the registers not yet consumed at layer $t$. That is all that is fundamental in EGG: a causal order on events, a counting measure, and an isometric quantum process along the order. Everything geometric is to be *read off* this object, and the interesting question is whether the several ways of reading it agree.

### 1.2 Three geometries, one hypothesis

The same DAG-with-circuit supports three geometric structures, each computable by itself and each with a literature that the earlier versions did not use.

**Order geometry.** If a partial order approximates the causal order of a past- and future-distinguishing Lorentzian manifold, the order fixes the conformal class of the metric [3,4] and a count of events fixes the volume element. This is the founding observation of causal-set theory [5,6], and it comes with embedding-free estimators — the Myrheim–Meyer dimension from interval abundances [7,8], proper time from longest chains, and a comparison of interval statistics with those of a Poisson sprinkling. Versions 2 and 3 measured the spectral dimension of the *undirected* graph and then tried to build a metric from mutual information with a lapse bolted on from layer counts. The correct task is different: determine whether the EGG order is manifold-like enough for the causal-set reconstruction to apply, and if it is, take the Lorentzian geometry it supplies (Section 3).

**Cut geometry.** Because growth is isometric, the entanglement entropy of any set $A$ of frontier registers obeys $S(A)\le\ln\chi\cdot|\mathrm{mincut}(A)|$, and for random tensor networks at large bond dimension the bound is saturated [9]. The areas of minimal cuts and the depth to which minimal-cut surfaces reach into the DAG are therefore the entanglement geometry of the EGG state to leading order, and they can be computed by max-flow on existing graphs before any stabilizer simulation is attempted (Section 4). The regions whose cuts are measured are defined by the order geometry alone (Section 3.5), so the two diagnostics share no input: order geometry defines the regions, cut geometry measures their boundaries. Whether any metric can be built from cut data is a question for the geometric phase, not a definition.

**Topological geometry.** Place a qubit on every edge and impose a $\mathbb{Z}_2$ gauge theory with star constraints at vertices and plaquette constraints on short cycles [10,11]. The number of logical qubits is $k_{\mathrm{top}}=\dim_{\mathbb{Z}_2}H_1(K;\mathbb{Z}_2)$, where $K$ is the two-complex whose faces are the enforced cycles (so the logical space has dimension $2^{k_{\mathrm{top}}}$); the distance is the smallest non-trivial cycle or cocycle. On a tree the code is empty. On a manifold-like complex, every sufficiently local cycle lies in the span of local face boundaries, only large-scale topology survives, and the code is small-rate and high-distance. On a crumpled complex, homology is extensive and depends on the face rule. This is the precise content of Version 2's "loops carry gauge, code, and geometry" (Section 5).

**The co-emergence hypothesis.** *A suitable growth law admits a scaling window in which the order dimension, the cut geometry, and the homological structure of the DAG are mutually consistent descriptions of a single low-dimensional space.* Agreement is the claim. The null models are the single-seed tree — whose order is one-dimensional, whose homological code is empty, and whose cut geometry is that of a tree tensor network (Section 3.4) — and the crumpled phase, in which cycles abound but organize nothing. Disagreement in a candidate phase — e.g. an order dimension of four alongside exponential cut-ball growth, or a homology that changes with the face rule — is a failure of the hypothesis for that growth law. Section 7 states the tests.

### 1.3 State-dependent growth

A framework in which geometry emerges from a state should have some route by which the state shapes the geometry. In Versions 2 and 3 the growth law was state-independent. Section 6 keeps Version 3's measurement-conditioned capacity rule and reinterprets it: the growth schedule $\Delta n(t)$ of earlier versions induces an expansion history of the frontier, and the conditioned rule makes that history local and dependent on a local observable. This is a proof of principle for state-dependent causal growth and a well-posed monitored-circuit problem with a likely phase transition in the feedback strength. A gravitational reading would additionally require identifying a coarse observable with an energy density and recovering a response law; we do not claim either, but this is the only place in the framework where such a reading could begin.

### 1.4 Claim tiers

**Tier I — reported, not reproduced.** The Version 2 numerical values (Section 7.1). No error bars, code, or seeds are available. They motivate the programme and establish nothing.

**Tier II — defined and computable.** The growth law (Section 2), the three geometries and their estimators (Sections 3–5), the state-dependent instrument (Section 6), and the programme (Section 7). Algebraic properties of these definitions — normalization, isometry, homology counts — are exact; whether any geometric phase exists is not.

**Tier III — conditional continuum targets.** Section 8. Nothing there is derived from Tier II.

### 1.5 Conventions

$\hbar=c=k_B=1$ except where restored. $N_v$ is the vertex count. $\chi$ is the port dimension ($\chi=2$ in the benchmarks). $\ell_0$ is a microscopic conversion scale, undetermined until a geometric regime is calibrated; no hierarchy between $\ell_0$ and $\ell_P$ is assumed.

---

## 2 The Growth Law

*Tier II.*

### 2.1 Layers, ports, and the causal graph

Growth proceeds in layers $t=0,1,2,\dots$. Every vertex owns $q$ outgoing ports. A port is *live* until consumed by exactly one later vertex; it is *eligible* for consumption at layer $t$ if its owner lies in layers $\max(0,t-\tau),\dots,t-1$. A vertex created at layer $t$ with $k$ consumed ports has in-degree $k\le k_{\max}\le q$ and out-degree at most $q$; total degree is bounded by $k_{\max}+q$. Parents lie strictly in earlier layers, so $G_t$ is acyclic; its transitive closure is a partial order $\prec$. The seed is a single vertex at layer 0 with $q$ live ports unless a different connected seed is declared.

Ports whose owners have aged out of the lookback window are *archived*: they remain in the output cut of the circuit but can no longer be attached to. The active frontier $F_t$ (live eligible ports) and the full cut $C_t$ (all live ports, archived or not) are distinct and every observable is reported for both.

### 2.2 Attachment kernel (Model B)

At an insertion event, choose an anchor uniformly among owners of eligible ports. Form a pool $\mathcal{P}_a$ of up to $K$ eligible owners within undirected graph distance $r_{\mathrm{pool}}$ of the anchor, distances computed in the subgraph induced by the lookback layers, nearest first, ties broken uniformly. Admissible parent sets $P$ contain the anchor and satisfy $1\le|P|\le\min(k_{\max},|\mathcal{P}_a|)$. Select $P$ with probability
$$
\Pr(P\mid G_t,a)=\frac{\gamma^{|P|}\exp\!\big[-\alpha\sum_{i<j\in P}D_g(i,j)^2/\ell_g^2\big]}{\sum_{P'}\gamma^{|P'|}\exp\!\big[-\alpha\sum_{i<j\in P'}D_g(i,j)^2/\ell_g^2\big]},
\qquad \gamma>0,\ \alpha\ge0,\ \ell_g>0,
\tag{2.1}
$$
the sum running over admissible sets. Consume one uniformly chosen live port from each parent; create the new vertex with $q$ fresh ports, eligible from layer $t+1$. If no eligible owner exists, growth halts and the realization is recorded as stalled. Nothing is silently enlarged or reused.

Model B contains no coordinate embedding. It does contain a preferred layering, a finite lookback, a pool radius, and a schedule (next subsection). "Intrinsic" means embedding-free, not covariant.

### 2.3 The schedule induces an expansion history

Earlier versions prescribed the number of insertions per layer, $\Delta n(t)=\beta\,[t^p-(t-1)^p]$, and worried that $p=4$ might inject four-dimensionality. The worry was correct but under-described. Let $n_F(t)=|F_t|$ be the number of eligible frontier ports and let $\rho_t$ be the fraction of those *ports* (not vertices or events) consumed during layer $t$. Consuming $\rho_t n_F$ ports takes $\rho_t n_F/\langle k\rangle$ events, each creating $q$ new ports, so
$$
n_F(t+1)\;\simeq\;n_F(t)\Big[1+\rho_t\Big(\tfrac{q}{\langle k\rangle}-1\Big)\Big]\;\equiv\;n_F(t)\,(1+H_t),
\tag{2.2}
$$
up to archiving losses. The externally specified $\Delta n(t)$ is an event-insertion schedule; $n_F(t)$ and $H_t$ are emergent frontier quantities that also depend on $\langle k\rangle$, port consumption, and archiving, and (2.2) is the relation between them. Choosing a schedule therefore controls, rather than literally is, the discrete expansion rate $H_t$. A power law $n_F\propto t^{p-1}$ corresponds to $H_t\simeq (p-1)/t$, a decelerating expansion of exactly the form a flat matter- or radiation-dominated FRW model produces; $p=4$ is the frontier volume of the future light cone of a point in $3+1$ dimensions. A constant consumption fraction with $q>\langle k\rangle$ gives $H_t=\mathrm{const}$ and exponential frontier growth. In a continuum this would be de Sitter-like, and de Sitter space has flat three-dimensional slices; but in EGG the only metric is graph-derived, and an exponential frontier cannot be low-dimensional in it. Every parent set lies within a pool of radius $r_{\mathrm{pool}}$, so the graph diameter of the frontier obeys $\mathrm{diam}(F_{t+1})\le\mathrm{diam}(F_t)+2r_{\mathrm{pool}}+2$ and grows at most linearly in $t$, while $n_F$ grows exponentially. A bounded-degree graph with exponentially many vertices inside a linearly growing diameter has exponential ball growth, i.e. infinite Hausdorff dimension. A constant-$H$ regime therefore has exponential volume growth rather than finite-dimensional flat geometry in the graph metric (the argument establishes no finite Hausdorff dimension, not Gromov hyperbolicity), and an exponentially growing frontier is a signature of the crumpled phase (Section 5.3), not of an expanding low-dimensional space. Finally, $q=\langle k\rangle$ gives a static frontier.

Three consequences. First, the schedule cannot be removed; it can only be declared or made dynamical, and the induced $H_t$ must be measured rather than read off $p$. We declare it: the benchmark family $\mathrm{B}_p$ uses the power-law schedule with $p$ scanned, and the family $\mathrm{B}_H$ uses a constant consumption fraction with $q/\langle k\rangle$ scanned. Second, the correct control is not "does $D_s$ track $p$" but "does the spatial dimension of the frontier track the expansion history" — a question with a known answer in cosmology, where it does not. Third, the natural place for the expansion rate to become an output rather than an input is a state-dependent capacity, Section 6.

### 2.4 Model A as a regulator control

Version 2's simulations used an auxiliary embedding of undeclared dimension and signature to form candidate pools, with weights of the form (2.1) in embedding distance. We keep Model A only as a control whose embedding dimension is scanned. Two of its properties bear directly on the legacy numbers. Its out-degree is unbounded — a vertex may be chosen as parent arbitrarily often — so it can grow hubs, and hubs are small-world shortcuts in the undirected graph. And its candidate pools were aligned with a light cone in the embedding, so its causal structure is partly inherited. Neither property is shared by Model B.

### 2.5 Foliation

The layering is a preferred foliation at the microscopic level. The Bombelli–Henson–Sorkin theorem [12] concerns Lorentz-equivariant constructions from sprinklings and does not forbid every finite-valence discretization, but it correctly signals that a layered, bounded-degree growth law has no microscopic boost symmetry. Any Lorentz invariance is emergent, to be tested by the order-geometry diagnostic of Section 3.3 and by the dispersion of propagating modes (Section 6.4). Radiative stability of an emergent Lorentz symmetry is a known difficulty [13]; we do not claim to have addressed it.

---

## 3 Order Geometry

*Tier II. Everything here is computable on any generated DAG, including the legacy graphs if they can be recovered.*

### 3.1 Order plus number is geometry

For a strongly causal (more generally, past- and future-distinguishing) Lorentzian manifold, the causal relation determines the topology, differentiable structure, and conformal class of the metric [3,4]. The one remaining function — the conformal factor — is fixed by volume. A causal set sprinkled into such a manifold therefore carries the full metric in its order and its counting measure, and causal-set theory has developed estimators that read the metric off the order without an embedding [5,6]. EGG's DAG is not a sprinkling, and a partial order does not by itself imply a Lorentzian geometry; the reconstruction theorems apply to orders that already come from a manifold. The logical chain is therefore

$$
\text{EGG order}\ \xrightarrow{\ \text{manifold-likeness tests}\ }\ \text{candidate causal-set approximation}\ \xrightarrow{\ \text{order + volume}\ }\ [g_{\mu\nu}],
$$

and the framework's task is the first arrow. If it passes, the second is supplied by the causal-set literature, and the order then furnishes light cones, a time function, and a conformal geometry before any quantum state is introduced.

This reorganizes the earlier programme. Version 2 built a spatial metric from mutual-information decay and supplied a lapse from the number of layers crossed; Version 3 correctly noted that the temporal sign in that construction was a hypothesis. Here the Lorentzian structure, when it exists, comes from the order, and the state-based geometry of Section 4 is a *second* geometry whose agreement with the first is the thing to test.

### 3.2 Estimators

Let $I(p,q)=\{r:p\prec r\prec q\}$ be an Alexandrov interval with $N$ elements and let $C_2$ be the number of related pairs within it. For a Poisson sprinkling into $d$-dimensional Minkowski space [7,8],
$$
\frac{\langle C_2\rangle}{\langle N\rangle^2}\;=\;f(d)\;\equiv\;\frac{\Gamma(d+1)\,\Gamma(d/2)}{4\,\Gamma(3d/2)},
\tag{3.1}
$$
a monotone function ($f(2)=1/4$, $f(4)=1/20$). Inverting (3.1) on intervals of a chosen size gives the **Myrheim–Meyer dimension** $d_{\mathrm{MM}}$, and the dependence of $d_{\mathrm{MM}}$ on interval size is the order-theoretic analogue of the running spectral dimension. Higher chain abundances $C_k$ give consistency checks and, in small intervals, curvature corrections [14]. The longest chain between $p$ and $q$ measures proper time up to a dimension-dependent constant; the largest antichain through a region measures spatial volume. The undirected spectral dimension of earlier versions is retained as one estimator among several, with the exact identity of Appendix C, but it is no longer the primary one: it probes a diffusion process that does not exist in the model and cannot distinguish spatial from spacetime dimension.

Two cautions. The DAG's edge set is a set of declared dependencies and need not be the transitive reduction of $\prec$; order estimators use $\prec$, link estimators use the edges, and the two probe different things. And interval-abundance estimators assume the interval is sampled from a homogeneous region; near the seed or the frontier they are biased, and only intervals far from both are used.

### 3.3 The sprinkling-consistency test

The order carries a quantitative kinematic test bearing on emergent Lorentz invariance that the diffusion-based programme lacked. Sprinklings are the Lorentz-invariant discretizations [12], and the conformal class is what the order fixes [3]. If, in a scaling window, the joint distribution of chain abundances $(C_2,C_3,\dots,C_k)$ over intervals of fixed $N$ matches that of a sprinkling into $d$-dimensional Minkowski space, the order has sprinkling-compatible statistics at that scale for those observables. This is evidence of local manifold-likeness with no preferred-frame signature in the tested statistics, not a proof of indistinguishability: finitely many abundance distributions are a finite set of moments, and order-invariant statistics cannot by themselves see every frame-dependent feature. Departures from sprinkling statistics that persist as the window grows are a preferred-frame signature. The test does not probe the dynamics of matter on the order (Section 6.4), but it costs only counting and it is sharper than isotropy of a diffusion curve.

### 3.4 What layered growth gives and does not give

A layered growth with locality will produce a partial order with a time function (the layer index) and light cones (the descendant sets). It will not automatically produce the interval statistics of a sprinkling; classical sequential growth models that respect order invariance are known to produce non-manifold-like orders [15], and EGG's wager is that enforced locality is the missing ingredient. The test is (3.1) and its $k$-chain refinements on Model B graphs. A robust $d_{\mathrm{MM}}$ different from four is a legitimate negative result for that parameter family.

One exact statement is available, and it is the correct residue of Version 2's tree-to-loop intuition on the order side.

**Tree lemma.** *In connected single-seed growth, if the underlying undirected graph of $G_t$ is a tree, then every non-seed event has exactly one parent, every Alexandrov interval of $\prec$ is a chain, and the Myrheim–Meyer estimator returns $d_{\mathrm{MM}}=1$.*

*Proof.* The existing graph is connected. If a new event took two distinct parents, the two new edges together with the existing path between the parents would form an undirected cycle; so each non-seed event has one parent. Every event then has a unique path to the seed, so its causal past is that path, a chain. For $p\prec q$ the interval $I(p,q)$ is a sub-path of the path from $q$ to the seed, hence a chain, in which every pair is related: $C_2=\binom{N}{2}$, $C_2/N^2\to1/2=f(1)$ by (3.1). $\square$

**Corollary.** $d_{\mathrm{MM}}>1$ on any interval implies $b_1(G_t)>0$: cycles are necessary for a manifold-like order of dimension greater than one, exactly as they are necessary for non-trivial holonomy and homology (Section 5). Manifold-likeness in $d\ge2$ requires spacelike-separated pairs within a common past, which is precisely two paths merging.

The lemma says nothing about encoding: an isometric tree network can protect information, and the cut geometry of a tree is non-trivial but not manifold-like (Section 4.3).

### 3.5 Spatial distance on the frontier from order alone

Frontier registers are pairwise spacelike, so no order distance exists between them without a construction. Causal-set theory supplies one that uses only the common past [27,28]: two events at spatial separation $D$ on a slice of Minkowski space have a nearest common ancestor at proper-time depth $D/2$, the past tip of the smallest diamond containing both. Let $\tau(z,x)$ be the longest-chain length from $z$ to $x$ (proper time up to a dimension-dependent constant [6]) and define, for frontier events $x,y$,
$$
d_\Sigma(x,y)\;=\;2\,\min_{z\,\prec\,x,\;z\,\prec\,y}\ \max\!\big(\tau(z,x),\,\tau(z,y)\big),
\qquad
B^\Sigma_r(x)=\{\,y\in F_t:\ d_\Sigma(x,y)\le r\,\}.
\tag{3.2}
$$
With a single seed a common ancestor always exists. In a manifold-like order $d_\Sigma$ approximates the induced spatial distance on the slice [28]; in a tree it is twice the depth of the branch point, which is why tree balls are subtrees (Section 4.3). Ball-volume growth $|B^\Sigma_r|\sim r^{d_s}$ gives an order-derived spatial Hausdorff dimension $d_s$, to be compared with $d_{\mathrm{MM}}-1$, and (3.2) is the notion of ball used throughout Section 4. The regions of the cut-geometry tests are thereby defined by the order alone, with no use of undirected graph distance, so the order and cut diagnostics share no input.

---

## 4 Cut Geometry: Isometric Growth as a Code

*Tier II.*

### 4.1 The encoding (benchmark B0)

Assign a qubit to every port. Choose a logical input $\mathcal{H}_L=(\mathbb{C}^2)^{\otimes k_L}$ with $1\le k_L\le q$ and pad the seed with $q-k_L$ qubits in $|0\rangle$. A vertex with $k$ consumed inputs applies
$$
T_v=C_v\,J_{k\to q},\qquad J_{k\to q}|\psi\rangle=|\psi\rangle\otimes|0\rangle^{\otimes(q-k)},
\tag{4.1}
$$
with $C_v$ drawn uniformly from the $q$-qubit Clifford group. Then $T_v^\dagger T_v=I$, and the composition along any history $h$ is an isometry $V_{t,h}:\mathcal{H}_L\to\mathcal{H}_{C_t}$ onto the cut. The maximally mixed logical input, $\rho_{\mathrm{cut}}=V_{t,h}(I_L/2^{k_L})V_{t,h}^\dagger$, is the reference state; pure inputs are controls. Clifford circuits and Pauli measurements are exactly simulable in the stabilizer formalism [16], with cost polynomial in the number of live qubits. The logical rate $k_L/|C_t|$ is reported with every result.

Version 3 attached classical $\mathbb{Z}_2$ transport labels to this circuit. Uniform Clifford gates absorb such labels, so they had no effect on the marginal ensemble; we drop them from B0. The gauge sector is instead the independent quantum structure of Section 5.

### 4.2 Entanglement is bounded by cuts

For any set $A$ of cut registers and any tensor cut $\Gamma$ of the DAG separating $A$ from its complement and from the logical input (or the purifying reference),
$$
S(A)\;\le\;\ln 2\cdot|\Gamma|,\qquad S(A)\;\le\;\ln 2\cdot\min_\Gamma|\Gamma|\;\equiv\;\ln2\cdot m(A).
\tag{4.2}
$$
For random tensor networks with bond dimension $\chi\to\infty$ the bound is saturated: $S(A)=\ln\chi\cdot m(A)$ with corrections controlled by $1/\chi$ [9]. At $\chi=2$ the corrections are not small, so on the benchmark $m(A)$ is an exact upper bound and a proxy, and the stabilizer computation gives the true value. The comparison between the two is itself informative: a large gap means the graph's cut structure does not control the entanglement.

The consequence for the programme is that the entanglement geometry of the B0 state is, to leading order, a *combinatorial* property of the DAG. Minimal cuts are max-flow computations and can be run on graphs of $10^5$–$10^6$ vertices today, without any quantum simulation.

### 4.3 Areas and wedges, not distances

A minimal cut is a capacity, not a separation, and Version 4 erred in treating it as one. For disjoint frontier regions $A,B$, the minimal cut separating them within their common past is bounded by $\min\!\big(m(A),m(B)\big)$ — one can always cut around the smaller region — so in any geometry it *saturates* once the separation exceeds the regions' own size. It cannot grow with distance and it is not a metric. Two-region separation enters the entanglement geometry only through the corrections to the min-cut formula at finite $\chi$, i.e. through the actual decay of mutual information $I(A\!:\!B)=S(A)+S(B)-S(AB)$, which at large $\chi$ vanishes identically for well-separated regions [9] and at $\chi=2$ must be computed in P1. If some monotone transform of the stabilizer mutual information satisfies approximate metric properties in a candidate phase, that is a discovery about the phase; we do not name it a distance in advance.

What minimal cuts do determine, and what can be computed on the graph alone, are areas and wedges. Let $B_r(x)=B^\Sigma_r(x)$ be a frontier ball in the order-derived distance (3.2), let $\Gamma^*(B_r)$ be a minimal cut, and let $\mathcal{W}(B_r)$ be the set of vertices on the $B_r$ side of $\Gamma^*$ — the analogue of an entanglement wedge. Because the ball is defined by the order and its boundary is measured by max-flow, the two quantities entering each test below are computed from different structures. The tests that decide whether the cut geometry is a geometry are:

- **Area law.** Does $m(B_r)$ scale as $r^{\,d_s-1}$, with $d_s$ the spatial dimension from $|B^\Sigma_r|$ and from $d_{\mathrm{MM}}-1$? Volume-law or exponential scaling indicates a non-geometric cut structure; a saturating $m(B_r)=O(1)$ is the tree signature (any subtree is separated by one edge).
- **Wedge depth.** Does the minimal-cut surface of $B_r$ reach into the past to a depth (in layers, or in order distance from the frontier) that scales as $r$? In a local low-dimensional geometry the wedge of a ball is a ball-like region whose depth is set by its radius; on a graph with exponential volume growth the cut hugs the frontier, and on a tree it sits at the branch point, at depth $r/2$ in $d_\Sigma$ but $O(1)$ in cut size.
- **Dimensional consistency.** Do the exponents extracted from $m(B_r)$ and from wedge depth agree with $d_{\mathrm{MM}}$ over the same window? This is the first of the co-emergence tests.

All three are max-flow computations on existing graphs.

### 4.4 Recovery, frontier, and archive

For an erased set $E\subset C_t$, the optimal entanglement fidelity $F_{\mathrm{opt}}(E)$ with a reference purifying the logical input is defined as in Version 3 and, for an isometric encoding, is equivalently a decoupling condition [17]. The **recovery radius** $R_{\mathrm{QEC}}(\epsilon,f;t)$ is the largest $r$ such that a fraction $f$ of centers have $F_{\mathrm{opt}}(B_r)\ge1-\epsilon$. Recovery from the active frontier and recovery using archived outputs are reported separately; a decoder that needs the archive is not evidence of protection on the frontier.

The archive is also a bath. The full map $V_{t,h}:\mathcal{H}_L\to\mathcal{H}_{C_t}$ is an isometry, but the active frontier alone evolves as an open system,
$$
\rho_{F_t}\;=\;\mathrm{Tr}_{\,C_t\setminus F_t}\!\big[V_{t,h}\,\rho_L\,V_{t,h}^\dagger\big],
\tag{4.3}
$$
and as layers pass, information flows from the frontier into archived registers that no future event touches. The entropy of $\rho_{F_t}$ as a function of layer is a Page-type curve for the growth process itself, computable in the stabilizer setting and requiring no black hole to define; Version 2's evaporation discussion reduces to this object. We note without building on it that expansion in EGG is thereby also a process of open-system information loss from the active geometry into inaccessible historical degrees of freedom.

### 4.5 Pairwise information distances

Mutual information $I(x,y)$ between frontier cells remains a legitimate observable, and a shortest-path completion of $-\ell\ln[I/I_{\max}]$ remains one candidate reconstruction. But pairwise mutual information in a random-circuit state at $\chi=2$ is typically zero beyond nearest neighbours and misses multipartite structure, so this reconstruction is expected to fail on most of the frontier. Its failure would not falsify the cut geometry; the cut geometry uses the full state. Version 2's world-function construction is not used (Appendix D of [2] records the counterexamples).

---

## 5 Topological Geometry: $\mathbb{Z}_2$ Gauge Theory on the Growing Two-Complex

*Tier II. This section replaces both the classical flatness weight of Version 2 and the classical label ensemble of Version 3 with a quantum gauge theory whose code content is exactly computable.*

### 5.1 Edge qubits, stars, and plaquettes

Let $K_t=(V,E,F)$ be the two-complex whose vertices and edges are those of $G_t$ (undirected) and whose faces $F$ are a declared set of short cycles — all simple cycles of length $\le L_{\max}$ in the benchmark, minimal causal diamonds only in a control. Place a qubit on every edge and define
$$
A_v=\prod_{e\ni v}X_e\quad(v\in V),\qquad B_f=\prod_{e\in\partial f}Z_e\quad(f\in F).
\tag{5.1}
$$
Every face boundary is a closed cycle and meets every vertex star in an even number of edges, so all $A_v$ and $B_f$ commute. The stabilizer group $\mathcal{S}=\langle A_v,B_f\rangle$ defines a code on $|E|$ qubits: $A_v$ is the Gauss-law constraint of a $\mathbb{Z}_2$ gauge theory, $B_f$ the flatness constraint on $f$. This is the homological code of Kitaev and of Dennis–Kitaev–Landahl–Preskill [10,11] on an arbitrary complex, not on a lattice.

### 5.2 Logical count and distance

The products of all $A_v$ over a connected component and the $\mathbb{Z}_2$-dependencies among face boundaries are the only relations, so (Appendix B)
$$
k_{\mathrm{top}}\;=\;|E|-\mathrm{rank}\langle A_v\rangle-\mathrm{rank}\langle B_f\rangle\;=\;\dim H_1(K_t;\mathbb{Z}_2).
\tag{5.2}
$$
With no faces, $k_{\mathrm{top}}=b_1(G_t)=|E|-|V|+c$, the cycle rank. Each enforced face that is independent in $\mathbb{Z}_2$ homology removes one logical qubit. $Z$-type logical operators are supported on cycles not spanned by faces; $X$-type logicals on cocycles (edge cuts) not equal to a vertex coboundary. The distance is
$$
d_{\mathrm{top}}=\min\big(d_Z,d_X\big),\qquad d_Z=\text{length of the shortest homologically non-trivial cycle},\quad d_X=\text{size of the smallest non-trivial cocycle}.
\tag{5.3}
$$
$k_{\mathrm{top}}$ is Gaussian elimination over $\mathbb{Z}_2$ and is exact at any benchmark size. The distances are not generically cheap: minimum distance of a stabilizer code is NP-hard in general [29], and shortest homologically non-trivial cycles on an arbitrary two-complex inherit that difficulty. They are reported as exact where exhaustive search over cycles and cuts up to a declared cutoff $d_{\mathrm{search}}$ finds a logical operator, and otherwise as the bound $d_{\mathrm{top}}>d_{\mathrm{search}}$.

### 5.3 The co-emergence hypothesis, stated exactly

The three phases that earlier versions named informally now have order parameters.

- **Tree.** $b_1=0$, hence $k_{\mathrm{top}}=0$: no gauge-invariant loop data and no homological code, identically. The order is one-dimensional (Section 3.4) and the cut geometry is a tree's (Section 4.3). Only the homological code is literally trivial; the encoding is not.
- **Manifold-like.** Every sufficiently local cycle lies in the span of local face boundaries, so $H_1(K_t)$ is the large-scale topology of the emergent space: $k_{\mathrm{top}}$ is $O(1)$ (or zero for a ball), $d_{\mathrm{top}}$ grows with the linear size of the region, the density of homologically non-trivial short cycles vanishes, and $H_1$ is stable under the face rule (Section 5.4).
- **Crumpled.** Defined geometrically: exponential ball-volume growth in $d_\Sigma$ and in graph distance, and failure of any common finite-dimensional scaling among the diagnostics; typically accompanied by extensive, face-rule-sensitive homology, $k_{\mathrm{top}}/|V|$ finite and varying with $L_{\max}$. Low code distance is *not* a signature of this phase — expander-based constructions yield constant-rate codes with linear distance [30] — so the phase is diagnosed by volume growth and regulator dependence, not by $d_{\mathrm{top}}$.

The hypothesis is that a Model B parameter region exists in which the manifold-like signature of $H_1$ coincides, over a common window and with common finite-size scaling, with a stable $d_{\mathrm{MM}}$ and an area-law cut geometry. Cycles are necessary for non-trivial holonomy and homological code structure, and for a manifold-like order in more than one dimension; they are not necessary for an isometric network to encode information, and they do not by themselves produce geometry. The claim that their organization coincides with the onset of manifold-like order and cut geometry is empirical, and the crumpled phase is the null model that shows it need not: cycles can be abundant, and even support a good code, without organizing into a finite-dimensional geometry.

### 5.4 Face-rule stability as a co-emergence criterion

The homology of $K_t$ depends on the face rule, and $L_{\max}$ is not a numerical regulator but part of the definition of the candidate space. Faces only kill homology. Under-filling (too small an $L_{\max}$, or diamonds only) leaves locally contractible cycles unfilled and manufactures spurious classes in $H_1$. Adding a face whose boundary already lies in $\mathrm{im}\,\partial_2$ changes nothing, whereas adding an independent face kills a homology class — a genuine one, or on a crumpled graph an accidental short cycle that no local geometry would recognize. The physical question is whether $H_1$ stabilizes once all locally contractible cycles have been filled and before large-scale classes start to be. What "large-scale topology" means is therefore

$$
H_1(K_t;L_{\max})\ \text{ stable for } L_{\max}\in[L_{\mathrm{loc}},L_{\mathrm{sys}}],
\tag{5.4}
$$

a range of face prescriptions above a locality scale $L_{\mathrm{loc}}$ and well below the system size $L_{\mathrm{sys}}$, with the diamond-only rule reproducing the same homology once diamonds are supplemented by the short non-diamond cycles the growth law produces. The existence of such a range is the operational definition of a locality scale for the topological sector, and it is elevated here to a co-emergence criterion on the same footing as a stable $d_{\mathrm{MM}}$ window and an area law: if $k_{\mathrm{top}}$ or $d_{\mathrm{top}}$ change qualitatively when $L_{\max}$ goes from 6 to 8, the graph has regulator dependence, not topology. The scan $L_{\max}\in\{4,6,8,10\}$ in P0.4 tests this directly, and $L_{\mathrm{loc}}$ so obtained should be compared with the locality scale implied by the pool radius and the onset of the $d_{\mathrm{MM}}$ window.

### 5.5 Relation to the other structures

The topological code lives on edges; the B0 encoding lives on ports. They are different codes on the same graph and must not be conflated: B0 protects the seed by delocalization through the cut structure, the gauge code protects homology classes. A single model coupling them — matter on ports charged under the edge gauge field, with gates that commute with $A_v$ — is the natural next construction and would make the connection variables dynamical rather than decorative. It is not defined here.

The classical Boltzmann ensemble on $\mathbb{Z}_2$ labels of Version 3 is a classical $\mathbb{Z}_2$ gauge theory whose $\kappa\to\infty$ limit concentrates on the flux-free configurations $B_f=+1$ of (5.1). It is retained as a cheap proxy for flux statistics; it defines no code and is not called one.

---

## 6 State-Dependent Growth

*Tier II definitions; any backreaction reading is a hypothesis that requires an energy density the benchmark does not yet have.*

### 6.1 The instrument (benchmark B1)

Retain the attachment kernel (2.1) and let the new vertex's output capacity depend on a local measurement of its $k$ inputs. With the local Pauli observable $O_a=Z_1\otimes\cdots\otimes Z_k$ on the consumed ports (the ports carry no gauge action; the $\mathbb{Z}_2$ symmetry of Section 5 lives on edge qubits, and the two sectors are uncoupled, Section 5.5) and $0\le\varepsilon\le1$, define effects $F_{a,s}=\tfrac12(I+s\varepsilon O_a)$, $s=\pm1$, Kraus operators $K_{a,s}=T_{a,s}F_{a,s}^{1/2}$ with $T_{a,s}$ the isometry (4.1) at capacity $q_s\in\{q-1,\,q+1\}$ — which requires $q-1\ge k$ for every admissible event, i.e. $q\ge k_{\max}+1$ in B1 rather than $q\ge k_{\max}$ — and outcome probability $p(s\mid a,\rho)=\tfrac12[1+s\varepsilon\,\mathrm{Tr}(O_a\rho)]$. The label $a$ carries the classical parent and port choices; including their state-independent probabilities gives a complete trace-preserving instrument [2, App. C]. At $\varepsilon=1$ the step is a Pauli measurement followed by a Clifford isometry and remains stabilizer-simulable. At $\varepsilon=0$ the capacity is state-independent and provides the matched control. A conditioned branch is not an isometry of arbitrary logical inputs, so recovery is assessed for the full channel with a declared policy for the outcome records.

### 6.2 What the feedback does and does not establish

By (2.2), capacity controls expansion. Choosing $q_{+}=q+1$, $q_{-}=q-1$ around a baseline with $q\simeq\langle k\rangle$ makes the local expansion rate
$$
H_{\mathrm{loc}}\;\propto\;\varepsilon\,\langle O_a\rangle_{\rho},
\tag{6.1}
$$
to first order: the growth of the causal graph in a neighbourhood depends on a local expectation value of the state there. B1 is thereby a proof of principle for state-dependent causal growth — the schedule of Section 2.3 replaced by a dynamical variable — and that is all it is. $O_a=Z_1\cdots Z_k$ is a Pauli observable; nothing yet makes it transform or coarse-grain like an energy density, and the same correlator occurs in separable states, so no entanglement-driven mechanism is implied either. A gravitational interpretation requires identifying a coarse observable with an energy density and recovering an appropriate response law, and the Gaussian variant of Section 6.4, which has an energy functional, is where that identification could first be attempted.

The sign is nonetheless a physical choice worth fixing now. If a coarse observable is eventually identified with an energy density, attraction requires that capacity *decrease* with it, since energy density decelerates expansion. Both signs are benchmarks; the question is which, if either, produces clustering — regions of high $\langle O\rangle$ that grow less, attract attachment, and persist. Version 3 chose the sign under which a larger $\langle O_a\rangle$ accelerates local growth without remarking on it.

### 6.3 Contact with monitored circuits

B1 is a random circuit with measurements at rate set by $\varepsilon$ and with feedback from outcomes into the circuit's own connectivity. Monitored random circuits without feedback have an entanglement transition between a volume-law and an area-law phase as the measurement rate increases [18,19]. Adaptive circuits with feedback are an active subject. The natural expectation for B1 is a critical $\varepsilon_c$ at which the entanglement structure of the frontier changes character, with the graph geometry responding through (6.1). If the geometric window of Sections 3–5 opens or closes at $\varepsilon_c$, that is a co-emergence result of a new kind: geometry and entanglement phase changing together under a single control. If not, the two are independent and the case for state-dependent growth as a precursor to backreaction is weakened.

### 6.4 Propagation, clocks, and the limits of random gates

Signalling is measured by intervention. For cells $A$ at layer $t$ and $B$ at layer $t'$, let $\mathcal{E}_{t':t}$ be the channel from cut to cut (including accessible classical records in B1) and define
$$
C_{A\to B}(t,t') = \frac{1}{2} \sup_{\rho, U_A} \left\| \mathrm{Tr}_{\bar{B}} \left[ \mathcal{E}_{t':t}\left( U_A \rho U_A^{\dagger} \right) - \mathcal{E}_{t':t}(\rho) \right] \right\|_1 .
\tag{6.2}
$$
The order-theoretic light cone bounds where $C_{A\to B}$ can be non-zero; whether the operational front is sharp, isotropic, and universal across probes is the dynamical Lorentz test.

Uniform Clifford gates will not produce clocks, quasiparticles, or a conserved energy; V3 said so and it remains true. The cheapest fix that stays exactly simulable is to replace Clifford isometries by Gaussian fermionic (matchgate) isometries [20,21]. Gaussian states are specified by a correlation matrix, support a quasiparticle dispersion, and have a measurable maximal group velocity. A Gaussian EGG state therefore has a light cone that can be compared with the order-theoretic one, a species whose dispersion can be tested for the preferred-frame terms of [13], and an energy functional. We define this variant, B0$_{\mathrm{G}}$, by (4.1) with $C_v$ a random matchgate unitary on the $q$ modes; everything in Sections 4 and 6.1–6.3 carries over with the stabilizer formalism replaced by Gaussian-state algebra.

---

## 7 Numerical Status and Programme

### 7.1 Legacy results and a caution

Version 2 reported, for Model A at $p=4$, $\gamma=0.9$, $\alpha=1.6$, $k_{\max}=12$, $K=25$, a single realization at each size and no error bars:

| $N_v$ | $\langle k\rangle$ | short-window $D_s$ | long-window $D_s$ |
|---|---|---|---|
| $2\times10^4$ | 3.84 | 1.20 | 3.42 |
| $10^5$ | 3.99 | 1.21 | 3.63 |
| $3\times10^5$ | 4.25 | 1.22 | 3.81 |

These are transcribed, not reproduced; code, seeds, and the embedding specification are unavailable. Three remarks. The short-window values are not the branched-polymer value $4/3$ and, given that $D_s(\sigma)\to2\sigma\to0$ at small $\sigma$ on every graph (Appendix C), may be contaminated by the universal initial rise. The long-window rise with $N_v$ is compatible with an asymptote at four, below four, or above four. And the rise in $\langle k\rangle$ with size, in a model with unbounded out-degree, is the signature one would expect from hub accumulation; hubs are shortcuts, and shortcuts inflate the diffusion dimension without any change in the underlying geometry. The decisive discriminator is the Hausdorff dimension from ball-volume growth on the same graphs: a branched polymer with shortcuts has $d_H\simeq2$ while $D_s$ climbs, whereas a geometric phase has $d_H$ and $D_s$ rising together. We regard this as the first computation to run.

### 7.2 Estimators

All estimators are validated on calibration ensembles before use on EGG graphs: sprinklings into $\mathbb{M}^d$ for $d=2,3,4$ (order estimators), hypercubic lattices and random regular graphs (spectral and Hausdorff), and random tensor networks on those lattices (cut geometry). Every run carries a machine-readable manifest of growth parameters, seeds, gate ensemble, record policy, Laplacian convention, probe counts, and predeclared window rule, as in [2, §9.4]. Independent graph seeds are the statistical replicates; stochastic trace probes are not.

### 7.3 The programme, staged by cost

**P0 — combinatorial, no quantum simulation.** On Model B graphs at $N_v\in\{10^4,10^5,10^6\}$, multiple seeds, and on any recoverable legacy graphs:

- (P0.1) $d_{\mathrm{MM}}$ versus interval size; chain abundances $C_2\ldots C_5$ compared with sprinkling statistics (Section 3.3).
- (P0.2) Hausdorff dimension from ball volumes on the event graph and, via $d_\Sigma$ of (3.2), on frontier cuts; walk dimension; spectral dimension by the exact identity (C.1). Free asymptote fit $D(N_v)=d_\infty+aN_v^{-\theta}$; $d_\infty$ not fixed.
- (P0.3) Minimal-cut area scaling $m(B_r)$ and wedge depth of $\Gamma^*(B_r)$ versus $r$, with exponents compared against $d_{\mathrm{MM}}$ (Section 4.3).
- (P0.4) $k_{\mathrm{top}}$ (exact), $d_{\mathrm{top}}$ (exact or as a search bound), and the density of non-trivial short cycles for $L_{\max}\in\{4,6,8,10\}$ and for diamonds only; face-rule stability of $H_1$ per (5.4), and the inferred $L_{\mathrm{loc}}$ compared with the onset of the $d_{\mathrm{MM}}$ window (Sections 5.3–5.4).
- (P0.5) Schedule controls: $\mathrm{B}_p$ at $p\in\{2,3,4,5,6\}$ and $\mathrm{B}_H$ at fixed $q/\langle k\rangle$; Model A with embedding dimension scanned; lookback $\tau$, pool radius, and $(\gamma,\alpha)$ scanned for the phase map.

P0 can falsify the co-emergence hypothesis outright: if no parameter region shows $d_{\mathrm{MM}}$, $d_H$, cut-area and wedge scaling, and a face-rule-stable $H_1$ in mutual agreement, the rest of the programme is moot for this growth family.

**P1 — stabilizer.** B0 on the P0 winners: entanglement versus min-cut, mutual-information decay $I(A\!:\!B)$ versus order distance (and whether any monotone transform of it behaves approximately as a metric in the candidate phase), recovery radius, logical rate, frontier-versus-archive recovery, the frontier Page curve, and the intervention diagnostic (6.2) with Pauli probes.

**P2 — feedback.** B1 at scanned $\varepsilon$ and both capacity signs; outcome-shuffled and $\varepsilon=0$ controls matched in capacity statistics; search for $\varepsilon_c$; clustering diagnostics; causal audit of the scheduler's use of classical records.

**P3 — dynamics.** B0$_{\mathrm{G}}$: quasiparticle dispersion, group velocity versus order light cone, isotropy, and species-dependence of limiting speeds.

### 7.4 Milestones

1. *Algorithmic:* normalized kernels, correct port bookkeeping, exact small-system agreement, resource accounting. Achievable regardless of outcome.
2. *Kinematic:* a Model B region in which P0.1–P0.4 agree over a growing window. A robust dimension other than four is a valid result.
3. *Dynamical:* a P2 regime in which state-dependent growth produces a response that is consistent across probes and survives the controls.
4. *Continuum:* the conditions of Section 8.

---

## 8 Conditional Continuum Targets

*Tier III. Nothing in this section is used by, or derived from, Sections 2–7. It records what the programme would have to deliver for a gravitational interpretation, in the order the derivations would have to occur.*

**A coframe.** Lorentz holonomies are even Clifford elements and carry no vector component (Appendix A), so a tetrad cannot be extracted from the connection sector of any version of this framework. A coframe $e^a{}_\mu$ would have to come either from an additional vector-valued sector or as a square root of the metric already reconstructed from Sections 3–4. The second option represents existing geometry; it does not derive it independently.

**An effective action.** Given a coframe and a flat spin connection, the teleparallel torsion scalar $\mathbb{T}$ differs from the Ricci scalar by a boundary term and the TEGR action reproduces Einstein's equations. Local Lorentz covariance does not select TEGR from the quadratic torsion family [22,23]; the coefficients must be computed from the microscopic dynamics, and the foliation permits additional operators. A healthy massless spin-2 sector at linear order is necessary, not sufficient.

**An induced coupling.** Induced-gravity reasoning [24,25] suggests $1/16\pi G_N=c_G\,n_{\mathrm{eff}}/\ell_0^2$ with $n_{\mathrm{eff}}$ the number of independently propagating microscopic modes. The benchmark has $\chi=2$ per port; $n_{\mathrm{eff}}$ is a count to be established, not the operator dimension $N^2$ of a hypothetical matrix sector. The same $n_{\mathrm{eff}}$ would have to reproduce $S=A/4G_N$ for entropy across a horizon, with $c_S=4\pi c_G$; the minimal-cut bound (4.2) is the place where an area law would first appear.

**A horizon.** A region from which the seed cannot be recovered is an information-theoretic boundary; an event horizon is a causal one. In EGG both are computable — the recovery radius of Section 4.4 and the descendant structure of the order — and their coincidence in a geometric phase is a test, not a definition.

**Vacuum energy.** A residual energy density $\rho\sim c_{\mathrm{vac}}\hbar c/R^4$ with $R$ an information-protection length gives $\Lambda\simeq8\pi c_{\mathrm{vac}}\ell_P^2/R^4$, and $\Lambda_{\mathrm{obs}}$ then corresponds to $R\approx88\,\mu\mathrm{m}\,c_{\mathrm{vac}}^{1/4}$ — the familiar dark-energy length. Absent a computed $c_{\mathrm{vac}}$, a demonstrated vacuum-like equation of state, and a calibrated $R_{\mathrm{QEC}}$, this is dimensional analysis. It becomes a prediction only if $R$ is computed from Sections 4–5 and the ratio $\lambda_Y/R$ for a Yukawa correction is derived from a massive mode of the effective action. Torsion-balance limits [26] are the eventual comparison; no sub-millimetre signal is claimed.

---

## 9 Conclusion

The object at the center of EGG — a causal order that is also a quantum circuit — supports three geometries, each with its own literature and its own estimators: the Lorentzian geometry of a manifold-like order, the entanglement geometry of minimal cuts, and the homological structure of a gauge theory on its locally filled cycles. Earlier versions asserted that these coincide; this version says exactly what coincidence would mean and how to measure it. A single-seed tree has a one-dimensional order, an empty homological code, and the cut geometry of a tree network: not manifold-like in any of the three senses, though not trivial in all of them. A manifold-like phase is the case in which all three agree on one low-dimensional space, with a homology that does not depend on the face rule. A crumpled phase is the case in which cycles abound but organize nothing. Which of these Model B produces is decided by counting, max-flow, and linear algebra over $\mathbb{Z}_2$ on graphs that already exist.

The theory is therefore no longer the slogan that entanglement creates spacetime. It is the claim that causal order, quantum encoding, and gauge topology are three projections of one growing quantum process, and that classical spacetime is what exists when those projections become mutually consistent. Unlike the holonomy metric of Version 2, that claim does not evaporate under an algebraic identity; it can only be settled by the measurements of Section 7.

Two ideas are new here. The growth schedule is an expansion history, and the measurement-conditioned rule makes that history local and state-dependent: a proof of principle for state-dependent causal growth, a monitored-circuit problem in its own right, and the one place a backreaction reading could begin. And the order geometry gives the Lorentz question a quantitative kinematic form — do interval statistics converge to those of a sprinkling? — that diffusion exponents could not.

What remains conjectural is confined to Section 8 and is not shorter than before; it is merely no longer in the way.

---

## Appendix A — Clifford Parity

Let $\{\gamma^a,\gamma^b\}=2\eta^{ab}$ in the four-dimensional complex representation and let $\Gamma_*$ be the chirality element, which anticommutes with each $\gamma^a$ and commutes with the even subalgebra. Elements of $\mathrm{Spin}(3,1)$ are even, products and inverses of even elements are even, and a partial trace over an internal factor preserves Clifford grading. For any loop transporter $W$ in the even subalgebra, cyclicity gives $\mathrm{tr}(\gamma^aW)=\mathrm{tr}(\Gamma_*\gamma^aW\Gamma_*^{-1})=-\mathrm{tr}(\gamma^aW)$, hence zero. Averaging cannot restore a component absent from every configuration. Curvature information resides in the bivector part; a vector carrier must be supplied separately.

## Appendix B — Homology Counting for the Edge Code

Over $\mathbb{Z}_2$, let $\partial_1:\mathbb{Z}_2^{E}\to\mathbb{Z}_2^{V}$ and $\partial_2:\mathbb{Z}_2^{F}\to\mathbb{Z}_2^{E}$ be the boundary maps of $K_t$. The $X$-type stabilizers $A_v$ generate the image of $\partial_1^{\mathsf T}$, of rank $|V|-c$ with $c$ the number of connected components; the $Z$-type stabilizers $B_f$ generate the image of $\partial_2$, of rank $\mathrm{rank}\,\partial_2$. Then $k_{\mathrm{top}}=|E|-(|V|-c)-\mathrm{rank}\,\partial_2=\dim\ker\partial_1-\dim\mathrm{im}\,\partial_2=\dim H_1(K_t;\mathbb{Z}_2)$. Logical $Z$ operators correspond to cycles in $\ker\partial_1\setminus\mathrm{im}\,\partial_2$; logical $X$ operators to cocycles in $\ker\partial_2^{\mathsf T}\setminus\mathrm{im}\,\partial_1^{\mathsf T}$. The rank computations are Gaussian elimination; the distance searches are shortest-non-trivial-cycle and minimum-non-trivial-cut problems, for which exact computation is feasible at the benchmark sizes by restricting to cycles and cuts of length up to a declared bound and reporting the bound.

## Appendix C — Heat-Trace Identity and Cutoff Limits

For $L_{\mathrm{norm}}=I-D^{-1/2}AD^{-1/2}$ on a graph with no isolated vertices, $P(\sigma)=N_v^{-1}\mathrm{Tr}\,e^{-\sigma L}$ and
$$
D_s(\sigma)=-2\,\frac{d\ln P}{d\ln\sigma}=2\sigma\,\frac{\mathrm{Tr}(Le^{-\sigma L})}{\mathrm{Tr}(e^{-\sigma L})}.
\tag{C.1}
$$
Since $\mathrm{Tr}\,L_{\mathrm{norm}}=N_v$, $D_s(\sigma)=2\sigma-2(\mu_2-1)\sigma^2+O(\sigma^3)$ with $\mu_2=1+\tfrac{2}{N_v}\sum_{\{i,j\}\in E}(d_id_j)^{-1}$; thus $D_s\to0$ as $\sigma\to0$ on every graph. At large $\sigma$ only zero modes survive and $D_s\to0$ again. A dimensional plateau is an intermediate window, chosen by a predeclared stationarity rule with reported width. Both traces in (C.1) are estimated from the same stochastic probes so that their covariance is retained.

---

## References

[1] *Entanglement–Gauge Gravity*, Version 2, unpublished draft (2026).
[2] *Entanglement–Gauge Gravity*, Version 3, unpublished draft (2026).
[3] D. B. Malament, "The class of continuous timelike curves determines the topology of spacetime," *J. Math. Phys.* **18**, 1399 (1977).
[4] S. W. Hawking, A. R. King, P. J. McCarthy, "A new topology for curved space-time which incorporates the causal, differential, and conformal structures," *J. Math. Phys.* **17**, 174 (1976).
[5] L. Bombelli, J. Lee, D. Meyer, R. D. Sorkin, "Space-time as a causal set," *Phys. Rev. Lett.* **59**, 521 (1987).
[6] S. Surya, "The causal set approach to quantum gravity," *Living Rev. Relativ.* **22**, 5 (2019).
[7] J. Myrheim, "Statistical geometry," CERN preprint TH-2538 (1978).
[8] D. A. Meyer, *The Dimension of Causal Sets*, PhD thesis, MIT (1988).
[9] P. Hayden, S. Nezami, X.-L. Qi, N. Thomas, M. Walter, Z. Yang, "Holographic duality from random tensor networks," *JHEP* **11**, 009 (2016).
[10] A. Yu. Kitaev, "Fault-tolerant quantum computation by anyons," *Ann. Phys.* **303**, 2 (2003).
[11] E. Dennis, A. Kitaev, A. Landahl, J. Preskill, "Topological quantum memory," *J. Math. Phys.* **43**, 4452 (2002).
[12] L. Bombelli, J. Henson, R. D. Sorkin, "Discreteness without symmetry breaking: a theorem," *Mod. Phys. Lett. A* **24**, 2579 (2009).
[13] J. Collins, A. Perez, D. Sudarsky, L. Urrutia, H. Vucetich, "Lorentz invariance and quantum gravity: an additional fine-tuning problem?," *Phys. Rev. Lett.* **93**, 191301 (2004).
[14] M. Roy, D. Sinha, S. Surya, "The discrete geometry of a small causal diamond," *Phys. Rev. D* **87**, 044046 (2013).
[15] D. P. Rideout, R. D. Sorkin, "Classical sequential growth dynamics for causal sets," *Phys. Rev. D* **61**, 024002 (2000).
[16] S. Aaronson, D. Gottesman, "Improved simulation of stabilizer circuits," *Phys. Rev. A* **70**, 052328 (2004).
[17] E. Knill, R. Laflamme, "Theory of quantum error-correcting codes," *Phys. Rev. A* **55**, 900 (1997).
[18] B. Skinner, J. Ruhman, A. Nahum, "Measurement-induced phase transitions in the dynamics of entanglement," *Phys. Rev. X* **9**, 031009 (2019).
[19] Y. Li, X. Chen, M. P. A. Fisher, "Quantum Zeno effect and the many-body entanglement transition," *Phys. Rev. B* **98**, 205136 (2018).
[20] B. M. Terhal, D. P. DiVincenzo, "Classical simulation of noninteracting-fermion quantum circuits," *Phys. Rev. A* **65**, 032325 (2002).
[21] L. G. Valiant, "Quantum circuits that can be simulated classically in polynomial time," *SIAM J. Comput.* **31**, 1229 (2002).
[22] M. Krššák, E. N. Saridakis, "The covariant formulation of f(T) gravity," *Class. Quantum Grav.* **33**, 115009 (2016).
[23] A. Golovnev, T. Koivisto, M. Sandstad, "On the covariance of teleparallel gravity theories," *Class. Quantum Grav.* **34**, 145013 (2017).
[24] A. D. Sakharov, "Vacuum quantum fluctuations in curved space and the theory of gravitation," *Dokl. Akad. Nauk SSSR* **177**, 70 (1967).
[25] T. Jacobson, "Black hole entropy and induced gravity," arXiv:gr-qc/9404039 (1994).
[26] J. G. Lee, E. G. Adelberger, T. S. Cook, S. M. Fleischer, B. R. Heckel, "New test of the gravitational $1/r^2$ law at separations down to 52 μm," *Phys. Rev. Lett.* **124**, 101101 (2020).
[27] D. Rideout, P. Wallden, "Spacelike distance from discrete causal order," *Class. Quantum Grav.* **26**, 155013 (2009).
[28] A. Eichhorn, S. Surya, F. Versteegen, "Induced spatial geometry from causal structure," *Class. Quantum Grav.* **36**, 105005 (2019).
[29] U. Kapshikar, S. Kundu, "On the hardness of the minimum distance problem of quantum codes," arXiv:2203.04262 (2022).
[30] P. Panteleev, G. Kalachev, "Asymptotically good quantum and locally testable classical LDPC codes," *Proc. STOC* (2022), arXiv:2111.03654; T.-C. Lin, M.-H. Hsieh, "Good quantum LDPC codes with linear time decoders from lossless expanders," arXiv:2203.03581 (2022).
