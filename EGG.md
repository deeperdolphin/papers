# Entanglement–Gauge Gravity: Emergent Geometry, Gauge Holonomy, and Quantum Information on a Growing Causal Graph

**Version 2 — revised draft**

---

## Abstract

We propose **Entanglement–Gauge Gravity (EGG)**, a microscopic framework in which the Universe is fundamentally a growing causal graph whose vertices carry finite operator algebras and whose large-scale organization gives rise to spacetime geometry, gravity, and gauge interactions. Geometry is not fundamental but emergent; gravity arises as the universal infrared description of how gauge redundancy and information protection organize on the causal substrate.

The framework rests on three ingredients: a stochastic causal growth law; local algebras $\mathcal{A}_v = M_N(\mathbb{C})\otimes\mathrm{Cl}(3,1)$ with link variables transporting both internal $U(N)$ and frame data; and gauge-invariant consistency weights defined on **causal diamonds** (closed loops of the causal graph). A structural observation organizes the whole construction: on a tree, every link configuration is gauge-trivial, so gauge dynamics, error-correcting redundancy, and curvature observables all vanish identically. **Gauge structure, quantum error correction, and geometry therefore co-emerge at the tree-to-loop crossover** of the growing graph — the same crossover at which the measured spectral dimension flows from its ultraviolet value toward four.

We outline how these structures organize into an infrared teleparallel description dynamically equivalent to General Relativity, with the Newton constant induced by the $N^2$ matrix degrees of freedom per vertex and the Bekenstein–Hawking entropy following automatically from the same counting. A seesaw relation, $\Lambda_{\mathrm{ent}}\sim \ell_P^{2}/R_{\mathrm{code}}^{4}$, ties the observed cosmological constant to the finite depth $R_{\mathrm{code}}$ of the information-protecting structure; matching the observed value fixes $R_{\mathrm{code}}\approx 40\text{–}90\,\mu\mathrm{m}$, predicting that any finite-range deviation from Newtonian gravity must appear at precisely the length scales now probed by torsion-balance experiments.

Numerically, we implement the growth law and measure the spectral dimension by diffusion on graphs of up to $3\times10^{5}$ vertices. We find a robust scale-dependent dimension: a universal ultraviolet plateau $D_s^{\mathrm{UV}}\simeq1.2\text{–}1.4$, consistent with branched-polymer and causal-tree universality, flowing toward $D_s^{\mathrm{IR}}\simeq4$ at large scales, with the infrared plateau sharpening systematically with system size. We are explicit about what these results do and do not establish: the simulations to date use a density exponent and an auxiliary embedding that could in principle inject the observed dimensionality. We therefore **pre-register a set of decisive control experiments** — a density-exponent scan, an embedding ablation, and an intrinsic-locality variant of the model — whose outcomes will either substantiate or falsify the emergence claim. The paper organizes all of its assertions into three explicit tiers: numerically established, defined-and-computable, and conjectural.

---

## 1 Introduction

The empirical success of quantum field theory and General Relativity leaves unresolved a fundamental question: *what microscopic structure, if any, underlies spacetime itself?* Despite their accuracy within their respective domains, the two frameworks make incompatible assumptions about locality, background structure, and ultraviolet behavior. This tension has motivated a wide range of approaches: causal-set kinematics and sequential-growth dynamics [1,2], causal dynamical triangulations (CDT) [3,4], gauge-theoretic and teleparallel formulations of gravity [5,6], asymptotically safe renormalization-group flows [7], graph-dynamical models of emergent geometry [8,9,10], and holographic constructions based on quantum error correction and tensor networks [11,12]. Each captures important aspects of the problem; none has converged on a shared microscopic picture of spacetime, matter, and information.

**Entanglement–Gauge Gravity (EGG)** takes a definite stance. The Universe is not built on a pre-existing manifold. It is a growing causal structure: a directed acyclic graph whose vertices carry finite quantum degrees of freedom and whose large-scale organization gives rise to geometry, dimensionality, and gravitational dynamics. Gravity is not a fundamental interaction but the effective, hydrodynamic description of how gauge redundancy and information protection organize across this structure — a stance in the lineage of Sakharov's induced gravity [13] and Jacobson's derivation of the Einstein equation as an equation of state and as a condition of entanglement equilibrium [14,15].

The framework combines three ingredients. First, a **stochastic causal growth law** generates a layered causal network. Second, each vertex hosts the finite algebra $M_N(\mathbb{C})\otimes\mathrm{Cl}(3,1)$, and each causal link carries a transport operator with both internal $U(N)$ and Lorentz-frame components; the matrix factor supplies a large-$N$ control parameter, the Clifford factor supplies the raw material for frame fields and spinors. Third, **gauge-invariant consistency weights on causal diamonds** — closed loops of the causal graph — enforce coherent information transport and induce code-like protection of coarse-grained observables.

A single structural fact organizes these ingredients, and we state it here because it is the conceptual heart of the revised framework. *On a tree, the cycle space is empty: every configuration of link variables is gauge-equivalent to the identity.* There are then no gauge-invariant holonomy observables, no curvature or torsion content, and no nontrivial code structure — gauge dynamics is pure gauge. All three structures switch on together when loops form. Since the loop content of the growing graph is controlled by the same connectivity parameter that drives the measured dimensional flow, **gauge fields, error correction, and geometry co-emerge at the tree-to-loop crossover**. The ultraviolet branched-polymer regime is not merely low-dimensional; it is the pre-gauge, pre-geometric phase of the theory.

### 1.1 Claim structure

To keep the epistemic status of every statement explicit, we organize the paper's claims into three tiers and tag each section accordingly.

**Tier I — numerically established (this work, Section 9).** The growth law at the studied parameter point generates large, stable, sparse causal graphs; the spectral dimension exhibits a universal ultraviolet plateau $D_s^{\mathrm{UV}}\simeq1.2\text{–}1.4$ consistent with the branched-polymer value $4/3$; and the infrared spectral dimension increases systematically with system size, reaching $\approx 3.8$ at $3\times10^{5}$ vertices.

**Tier II — defined and computable, not yet computed (Sections 3–4, 9.5).** The quantum state of the network (an isometric tensor network generated by the growth itself), mutual-information observables, the information-theoretic metric, the operational code distance, curvature diagnostics, and — critically — the control experiments that test whether the infrared dimension is emergent or injected by the simulation inputs. These are concrete computations with specified protocols.

**Tier III — conjectural continuum identifications (Sections 5–8).** The teleparallel effective action, the induced Newton constant, the emergent Einstein equations, the cosmological seesaw, and black-hole thermodynamics. These are structurally motivated and internally consistent, but not derived from first principles.

We believe this discipline is not a weakness but the appropriate way to present a framework of this scope: Tier I motivates Tier II, and Tier II, if successful, would begin to constrain Tier III.

The remainder of the paper is organized as follows. Section 2 defines the growth law in two variants — an embedded regulator model (the one simulated to date) and an intrinsic-locality model — and confronts the Lorentz-invariance question directly. Section 3 introduces the local algebras, link transport, diamond consistency weights, the co-emergence principle, the quantum state of the network, and the corrected code-distance structure. Section 4 constructs geometry from mutual information via a world-function coincidence limit. Section 5 builds gauge-invariant metric and frame observables from diamond holonomies and presents the teleparallel effective action with a selection principle for the GR-equivalent point. Section 6 presents the emergent field equations. Section 7 rebuilds the ultraviolet and phenomenological discussion around the cosmological seesaw. Section 8 treats black-hole thermodynamics with consistent large-$N$ counting. Section 9 reports the numerical results and pre-registers the decisive control experiments. Section 10 concludes; Section 11 is a brief, explicitly speculative outlook.

We set $\ell_P=\sqrt{\hbar G/c^{3}}$ and denote by $\ell_0$ the microscopic graph scale. As shown in Section 5, consistency of the induced-gravity normalization implies $\ell_0 \simeq N\,\ell_P$ up to order-unity constants: the discreteness scale lies *above* the Planck length by a factor of the internal gauge dimension.

---

## 2 Microscopic Growth Law

The fundamental structure in EGG is a growing causal network. Vertices are added in discrete layers, and each new vertex is connected only to vertices in its causal past, so the graph is a directed acyclic graph (DAG). No metric or dimensionality is assumed; these are diagnosed *a posteriori* through diffusion, order-theoretic, and correlation observables.

### 2.1 Growth schedule

Let $t\in\mathbb{N}$ be the **layer index**. At layer $t$, the number of new vertices added is

```math
\Delta n(t) \;=\; \big\lceil \beta\,\big(t^{\,p}-(t-1)^{p}\big)\big\rceil \;\approx\; p\,\beta\, t^{\,p-1},
\qquad p=4 \text{ in the simulations reported here,}
```

(2.1)

so that the cumulative vertex count grows as $n(t)\simeq\beta t^{p}$. We emphasize from the outset that **$p$ is a control parameter, not a principle**. The choice $p=4$ guarantees sufficient causal depth for a four-dimensional macroscopic regime to be *possible*; whether it is the *source* of the observed infrared dimensionality is an empirical question. The density-exponent scan defined in Section 9.5 — rerunning the entire programme at $p\in\{2,3,5,6\}$ — is the decisive test. If the infrared spectral dimension tracks $p$, the model transduces causal density into geometry and the emergence claim must be withdrawn in its strong form; if $D_s^{\mathrm{IR}}\approx4$ proves robust against $p$, the emergence claim is dramatically strengthened. We commit to reporting the outcome either way.

### 2.2 Parent selection: embedded and intrinsic variants

Each new vertex $v$ receives a *parent set* $P_v$ drawn stochastically from existing vertices. We define two variants of the attachment law.

**Model A (embedded regulator — the model simulated to date).** Candidate parents are drawn from a pool of the $K$ vertices nearest the new vertex's prospective lightcone in an auxiliary embedding of dimension $d_{\mathrm{emb}}$, and the parent set is selected with probability

```math
\boxed{
\Pr(P_v) \;\propto\;
\gamma^{|P_v|}\,
\exp\!\left[
-\alpha \sum_{p<q\,\in P_v}\frac{d_{pq}^{2}}{\ell_0^{2}}
\right],
\qquad |P_v|\le k_{\max},
}
```

(2.2a)

where $d_{pq}$ is the separation of candidate parents in the auxiliary embedding. **[AUTHOR NOTE: state $d_{\mathrm{emb}}$ and the embedding signature explicitly here — the simulations must declare exactly what was used, since this is the locus of the circularity concern discussed below.]**

We are explicit about the status of this construction: the auxiliary embedding is a **regulator that breaks background independence**, and the lightcone-aligned candidate pool inherits causal structure from it. A skeptical reader is entitled to suspect that the four-dimensional infrared geometry reported in Section 9 is partially or wholly injected by $d_{\mathrm{emb}}$, the pool geometry, and $p=4$. We share this concern, which is why Model A is presented as a regulated starting point rather than as the fundamental dynamics, and why the embedding-ablation experiments of Section 9.5 (varying $d_{\mathrm{emb}}$, deforming the pool) are part of the core programme.

**Model B (intrinsic locality — the fundamental proposal).** All reference to an embedding is removed. Locality is enforced using only data intrinsic to the existing graph: let $D_g(p,q)$ denote the undirected graph distance between candidate parents, computed (by truncated breadth-first search) within the most recent $\tau$ layers, and let the candidate pool consist of the $K$ vertices of smallest graph eccentricity within those layers relative to a randomly chosen anchor vertex. The attachment probability is

```math
\boxed{
\Pr(P_v) \;\propto\;
\gamma^{|P_v|}\,
\exp\!\left[
-\alpha \sum_{p<q\,\in P_v} \frac{D_g(p,q)^{2}}{\ell_g^{2}}
\right],
\qquad |P_v|\le k_{\max},
}
```

(2.2b)

with $\ell_g$ an order-unity scale in graph units. Model B is background-independent in the strict sense: the only structures it uses are the causal order and the graph metric the order itself generates. It is the EGG analogue of the order-invariance requirement of classical sequential growth [2] — with the crucial difference that locality is enforced rather than absent. It is known that order-invariant sequential-growth models generically fail to produce manifold-like causal sets; EGG's wager is that intrinsic locality is precisely the missing ingredient. If Model B reproduces the dimensional flow of Model A, the background-independence objection evaporates and the result becomes, to our knowledge, the first manifold-like infrared phase from a purely intrinsic causal growth law. If it does not, Model A's results must be reinterpreted as properties of a regulated theory whose regulator dependence has to be quantified. Either outcome is scientifically valuable, and Section 9.5 commits to both runs.

### 2.3 Interpretation of the parameters

**Connectivity $\gamma$** controls parent-set size and hence the loop content of the graph. Small $\gamma$ yields tree-like, strongly anisotropic structure; larger $\gamma$ proliferates loops. As established in Section 3, loops are simultaneously the carriers of gauge dynamics, error-correcting redundancy, and curvature/torsion observables, so $\gamma$ controls not merely connectivity but the onset of *all* post-tree structure in the theory. The numerical results show that the tree-like ultraviolet regime is not a failure mode: $D_s^{\mathrm{UV}}\simeq1.2\text{–}1.4$ matches the universal value $4/3$ of branched-polymer and random-tree geometries, placing the microscopic phase in a known universality class. We note for contrast that in dynamical-triangulation language the branched-polymer phase is the *degenerate* phase one must escape; in EGG the claim is that the growth dynamics escapes it automatically at large scales, and the burden of Section 9 is to substantiate that claim.

**Locality $\alpha$** suppresses parent sets whose members are mutually distant. For $\alpha\gg1$ the graph remains tree-like at all scales; for $\alpha\ll1$ locality is lost and the graph approaches a dense, expander-like, non-geometric structure (for which $D_s$ diverges rather than settling at four). The physically relevant regime is $\alpha=\mathcal{O}(1)$. Mapping the phase boundaries in the $(\gamma,\alpha)$ plane — tree / geometric / crumpled — is part of the Section 9.5 protocol; the claim of "no fine-tuning" is meaningful only once the geometric phase is shown to occupy a finite region rather than a point.

### 2.4 Lorentz invariance and the preferred foliation

We confront directly an issue the framework cannot evade. A theorem of Bombelli, Henson, and Sorkin [16] establishes that Poisson sprinkling is, in effect, the only way to discretize a Lorentzian manifold without selecting a preferred frame; any discrete structure with bounded valence and regular layering breaks microscopic Lorentz invariance. EGG's growth law is layered and has $k_{\max}$-bounded valence: it therefore possesses a preferred foliation at the fundamental level, and microscopic Lorentz invariance is *not* a symmetry of the theory.

We adopt the same strategic position as causal dynamical triangulations [3,4] and Hořava-type constructions [17]: the foliation is fundamental, and **infrared Lorentz invariance is an emergent property to be demonstrated, not assumed**. This is a genuine vulnerability — observational constraints on preferred-frame effects are severe — and we prefer to state it as a falsifiable conjecture with concrete tests: (i) isotropy of the emergent lightcones extracted from mutual-information decay (Section 4), and (ii) the dispersion relation of long-wavelength collective modes in the tensor-network realization (Section 3.3), both computable within the Section 9.5 programme. We also note the instructive contrast with sprinkled causal sets, whose exact Lorentz invariance comes at the price of infinite valence and intrinsic nonlocality, producing a spectral dimension that *increases* in the ultraviolet [18]. EGG sits at the opposite pole: bounded valence and enforced locality, at the price of a foliation. The two programmes thus bracket the discreteness–Lorentz tension from opposite sides.

### 2.5 Relation to other discrete approaches

*Causal sets and sequential growth.* EGG's growth law descends conceptually from Rideout–Sorkin classical sequential growth [2], but departs from it in two ways: locality is enforced (intrinsically in Model B), and vertices carry operator algebras rather than being structureless. The departure from strict order-invariance is deliberate and is the price paid for manifold-likeness.

*Causal dynamical triangulations.* CDT [3,4] shares the preferred foliation and the strategy of emergent infrared dimensionality, and its measured dimensional flow ($D_s\approx2$ in the UV to $\approx4$ in the IR) is the closest established analogue of our result. EGG differs in its ultraviolet universality class ($4/3$, tree-like, versus $\approx2$) and in carrying gauge and informational structure on the graph from the outset.

*Quantum graphity and combinatorial quantum gravity.* The idea that geometry emerges from a graph dynamics with local quantum degrees of freedom appears in quantum graphity [8] and in Trugenberger's combinatorial quantum gravity [9], where Ollivier curvature plays the organizing role. EGG differs in being causal and growth-based rather than equilibrium-based, and in tying the graph dynamics to gauge holonomy and error correction.

*Hypergraph rewriting.* The Wolfram programme [10] models the Universe as deterministic or rule-based hypergraph rewriting. EGG shares the discrete, background-free ambition and the use of spectral diagnostics, but differs fundamentally: dynamics is stochastic attachment constrained by locality and information-theoretic consistency, vertices carry operator algebras, and the foundational objects are information flow and gauge redundancy rather than rewriting rules. The ultraviolet universality class observed here ($D_s\simeq4/3$) is a signature of stochastic, locality-constrained tree growth; any relationship to rewriting systems would have to appear at the level of coarse-grained universality.

*Random tensor networks and holographic codes.* Once the quantum state of the network is defined (Section 3.3), EGG becomes a random tensor network in the sense of [12] — with the decisive difference that the network's graph is not a fixed hyperbolic lattice but is *generated dynamically by the causal growth law itself*. Holographic error-correcting codes [11] are the static ancestors of the code structure proposed here.


---

## 3 Vertex Algebra, Diamond Consistency, and the Quantum State of the Network

*(Tier II–III: structures defined here are computable in the realization of Section 3.3; continuum interpretations are conjectural.)*

### 3.1 Local algebras and link transport

To each vertex $v$ we associate the finite algebra

```math
\boxed{
\mathcal{A}_v \;=\; M_N(\mathbb{C}) \,\otimes\, \mathrm{Cl}(3,1),
}
```

(3.1)

the $N\times N$ complex matrices tensored with the real Clifford algebra of signature $(3,1)$, with generators $\{\gamma^a,\gamma^b\}=2\eta^{ab}$, $a,b=0,\dots,3$. The matrix factor supplies a local $U(N)$ gauge redundancy and a large-$N$ control parameter; the Clifford factor supplies the raw material for frame fields and spinorial structure.

We state plainly what is input and what is claimed emergent, correcting an inconsistency in an earlier version of this framework. **The signature $(3,1)$ of the local algebra is an input.** What is claimed to be emergent is its *geometric realization*: whether the coarse-grained correlation structure of the network actually organizes into a metric of Lorentzian signature with isotropic lightcones is a property of the dynamics, made sharp and computable in Sections 4–5, not a consequence of the algebraic choice alone. (One can write $\mathrm{Cl}(3,1)$ on any graph; most graphs will not develop Lorentzian geometry.)

Each causal link $p\to v$ carries a transport operator

```math
V_{p\to v} \;=\; U_{p\to v}\,\otimes\,\Lambda_{p\to v},
\qquad U_{p\to v}\in U(N),\quad \Lambda_{p\to v}\in \mathrm{Spin}(3,1),
```

(3.2)

mediating internal gauge transport and local-frame transport respectively. Under a local internal gauge transformation $g_v\in U(N)$ and a local frame rotation $s_v\in\mathrm{Spin}(3,1)$,

```math
V_{p\to v} \;\longrightarrow\; (g_v\otimes s_v)\,V_{p\to v}\,(g_p\otimes s_p)^{-1}.
```

(3.3)

### 3.2 Causal diamonds, gauge-invariant consistency weights, and the co-emergence principle

An earlier version of this framework imposed consistency weights built from single-link traces $\mathrm{Tr}\,U_{p\to v}$. Such terms are not invariant under (3.3); a model whose action is built from them does not actually possess the gauge symmetry it advertises. We therefore rebuild the consistency structure on the gauge-invariant objects the causal graph naturally provides: its **closed loops**.

A **minimal causal diamond** $\Diamond$ is a pair of directed paths $\pi_1,\pi_2$ from a vertex $p$ to a vertex $q$ ($p\prec q$) that share no interior vertices. To each diamond associate the holonomy

```math
W_{\Diamond} \;=\; V_{\pi_1}\,V_{\pi_2}^{-1}
\;\equiv\; \Big(\overrightarrow{\textstyle\prod_{\ell\in\pi_1}}V_\ell\Big)\Big(\overrightarrow{\textstyle\prod_{\ell\in\pi_2}}V_\ell\Big)^{-1},
```

(3.4)

based at $p$. Under (3.3), $W_\Diamond \to (g_p\otimes s_p)\,W_\Diamond\,(g_p\otimes s_p)^{-1}$: diamond holonomies transform by conjugation at the base point, so their normalized trace

```math
\mathbb{tr}(X)\;\equiv\;\frac{1}{4N}\,\mathrm{Tr}_{M_N\otimes\mathrm{Cl}}(X)
```

is fully gauge invariant. The microscopic consistency weight is then the Wilson-type product over minimal diamonds,

```math
\boxed{
\mathcal{W}[\{V\}] \;=\; \prod_{\Diamond}\exp\!\Big[\frac{N^{2}}{\lambda_t}\,\mathrm{Re}\;\mathbb{tr}\big(W_{\Diamond}\big)\Big],
}
```

(3.5)

with $\lambda_t$ a 't Hooft coupling held fixed as $N\to\infty$. The weight is maximized on **flat configurations** $W_\Diamond=\mathbb{1}$; these are the "stabilized" configurations, and deviations from flatness play the role of correctable errors. The construction is the $U(N)\times\mathrm{Spin}(3,1)$ analogue, on causal diamonds, of the plaquette stabilizers of Kitaev's toric code [19] — which is itself exactly a $\mathbb{Z}_2$ lattice gauge theory. The phrase "stabilizer-inspired" of the earlier draft is hereby made concrete: the stabilizer group is generated by the flatness conditions on diamonds, and it is gauge invariant by construction.

**The co-emergence principle.** This repair has a structural consequence that we regard as the central insight of the revised framework. The diamonds of a graph generate its cycle space. *On a tree the cycle space is empty*: every link configuration can be brought to $V_\ell=\mathbb{1}$ by a gauge transformation, all holonomies are trivial, the weight (3.5) is identically constant, and there are no gauge-invariant observables beyond constants. In the tree-like ultraviolet phase of the growth law there is therefore **no gauge dynamics, no curvature or torsion content, and no nontrivial code** — not approximately, but identically. All three structures switch on together when loops proliferate, and loop proliferation is controlled by the same connectivity parameter $\gamma$ that drives the measured flow of the spectral dimension from $4/3$ toward $4$. Gauge fields, error correction, and geometry are not three mechanisms that happen to coexist; they are a single mechanism — the cycle structure of the causal graph — viewed through three lenses. The ultraviolet regime of EGG is the pre-gauge, pre-geometric phase of the theory, and the tree-to-loop crossover is its fundamental phase transition.

### 3.3 The quantum state of the network

An earlier version of this framework invoked mutual information between vertices without specifying the quantum state of the network — leaving those quantities undefined. We repair this by observing that **the growth law itself defines a state**: it is, read quantum mechanically, an instruction for building an isometric tensor network.

Assign to each link a finite Hilbert space $\mathcal{H}_\ell$ (dimension $\chi$). Each vertex $v$ created with parent set $P_v$ carries a fixed budget of outgoing legs and applies an isometry

```math
T_v:\;\bigotimes_{p\in P_v}\mathcal{H}_{p\to v}\;\longrightarrow\;\bigotimes_{c}\mathcal{H}_{v\to c}\,,
```

(3.6)

where the outgoing legs are consumed by subsequently created children; legs not yet consumed at layer $t$ are the *dangling legs* of the network. Starting from a small seed state, the state of "space at layer $t$" is

```math
|\Psi_t\rangle \;=\; \Big(\prod_{v:\,\mathrm{layer}(v)\le t} T_v\Big)\,|\mathrm{seed}\rangle
\;\in\;\bigotimes_{\ell\,\mathrm{dangling}}\mathcal{H}_\ell\,,
```

(3.7)

defined on the cut of dangling legs. The isometries are drawn from an ensemble — Haar-random, or random Clifford, or biased by the diamond weights (3.5); the interplay between the weight and the isometry ensemble is an open question flagged for future work. We call the resulting ensemble of states the **EGG ensemble**.

Two consequences are immediate. First, EGG is revealed as a **random tensor network in the sense of Hayden et al. [12], whose graph is generated dynamically by the causal growth law** rather than fixed by hand — a precise point of contact with holographic duality. Second, choosing the isometries to be random *Clifford* operations makes the entire state exactly and efficiently simulable by the Gottesman–Knill theorem [20]: entanglement entropies, mutual informations, and erasure-recovery properties of $|\Psi_t\rangle$ are computable by binary linear algebra at the $10^{5}$–$10^{6}$-vertex scale of our existing graphs. Every information-theoretic quantity invoked in Sections 4 and 8 is thereby promoted from conjecture to **Tier II: defined and computable**, and the corresponding computations are part of the Section 9.5 protocol.

### 3.4 Code structure and a corrected distance law

The flatness stabilizers of Section 3.2, acting on the states of Section 3.3, delocalize logical information over extended causal regions. An earlier version of this framework posited a code distance growing *exponentially* with the radius $R_{\mathrm{code}}$ of a causal ball. That scaling must be retracted: for codes generated by geometrically local constraints, distance is bounded *polynomially* in region size — in $D$ spatial dimensions, $d\lesssim O(R^{D-1})$, by the tradeoff theorems of Bravyi, Poulin, and Terhal [21]. An exponential law would require nonlocality that the growth law itself forbids. We therefore replace the earlier ansatz by

```math
\boxed{
d_{\mathrm{code}}(R)\;\sim\; c_0\,N^{\,\nu}\,\Big(\frac{R}{\ell_0}\Big)^{\zeta},
\qquad 1\le \zeta \le D-1,
}
```

(3.8)

with $\nu,\zeta$ to be *measured*, not assumed. In the Clifford realization the measurement is concrete and efficient: erasure decoding for stabilizer codes is polynomial-time, so the **operational code depth** — the probability that logical information survives erasure of a causal ball of radius $R$ — is directly computable on our existing graphs. We note with candor that the geometric proxy data reported in Section 9.3 (boundary-separation distances growing sublinearly with $R$) already disfavored the exponential law of the earlier draft and are consistent with the polynomial form (3.8); the largest-radius data point is, moreover, shown there to be a finite-size artifact. The framework's infrared scales must therefore be built on polynomial protection depth, and Section 5.4 does so.

---

## 4 Entanglement and the Emergence of Geometry

*(Tier II: every object in this section is computable in the Clifford realization of Section 3.3.)*

With the state $|\Psi_t\rangle$ defined, correlation-based geometry becomes well posed. For coarse-graining cells $x,y$ on a fixed cut (double-cone cells of temporal depth $\sim2\ell_0$ and graph radius $\sim2\ell_0$, as before), define the mutual information

```math
\mathcal{I}(x,y)\;=\;S(\rho_x)+S(\rho_y)-S(\rho_{xy}),
```

(4.1)

a positive, regulator-independent measure of total correlation requiring no prior notion of distance.

### 4.1 An information world function

An earlier version of this framework defined the emergent metric as the coordinate Hessian of a coarse-grained scalar information potential. That construction is not tensorial — the second coordinate derivative of a scalar fails to transform covariantly except at critical points — and we replace it with a construction modeled on Synge's world function [22], in the spirit of the mutual-information geometry of Cao, Carroll, and Michalakis [23].

Generic many-body states exhibit decay of mutual information with separation; we *define* separation through that decay. Introduce the **information world function**

```math
\sigma(x,y)\;\equiv\;-\,\xi^{2}\,\ln\!\frac{\mathcal{I}(x,y)}{\mathcal{I}_0},
```

(4.2)

with $\xi$ a correlation length and $\mathcal{I}_0$ a coincidence normalization, and extract the spatial metric on the cut from the coincidence limit of the mixed bilocal derivative,

```math
\boxed{
h_{ij}(x)\;=\;-\,\lim_{y\to x}\,\frac{\partial}{\partial x^{i}}\frac{\partial}{\partial y^{j}}\,\sigma(x,y),
}
```

(4.3)

which, unlike a scalar Hessian, transforms as a tensor by construction (it is the standard coincidence-limit extraction of a metric from a bi-scalar distance function). Positive-definiteness of $h_{ij}$ follows wherever mutual information decays monotonically in all directions — a property to be verified, not assumed, in the EGG ensemble.

### 4.2 Assembly of the Lorentzian metric

The full spacetime metric is assembled in ADM form from the foliation the growth law itself provides:

```math
ds^{2}\;=\;-\,\mathcal{N}(x)^{2}\,d\tau^{2}\;+\;h_{ij}(x)\big(dx^{i}+\mathcal{N}^{i}d\tau\big)\big(dx^{j}+\mathcal{N}^{j}d\tau\big),
```

(4.4)

with the lapse $\mathcal{N}$ fixed by the local layer thickness (the graph depth traversed per unit coarse time) and the shift $\mathcal{N}^{i}$ by the drift of cells between cuts. We are explicit about what this construction does and does not claim. The Lorentzian *signature* of (4.4) is supplied by the causal layering — time enters through the foliation, space through correlation decay — and is therefore an output of the combination (growth law + state), not of either alone. What remains genuinely open, and computable, is whether the emergent lightcones are *isotropic and foliation-independent in the infrared* — the emergent-Lorentz-invariance question of Section 2.4. A claim in an earlier draft that preliminary numerics exhibited a $(+,-,-,-)$ Hessian signature is withdrawn: the state had not been specified, so the claim was not well defined. Its sharp, well-defined successors are: (i) positive-definiteness and isotropy of $h_{ij}$ from (4.3), and (ii) the independent signature test on the holonomy bilinear $\mathbb{G}_{\mu\nu}$ of Section 5.1. Both are part of the Section 9.5 protocol.

### 4.3 Status

Diffusion observables (Section 9) determine *whether* the graph admits a geometric phase and its dimensionality; the construction above determines *which* geometry, encoding anisotropy and curvature. It plays the role of a constitutive relation in hydrodynamics: it does not generate the geometric phase, but specifies how microscopic correlations organize into metric data once that phase exists.

---

## 5 Gauge-Invariant Geometry from Holonomy, and the Teleparallel Effective Action

*(Tier III, with Tier II ingredients: the observables of Section 5.1 are computable; the effective action and its couplings are conjectural.)*

### 5.1 Elitzur-safe metric observables from diamond holonomies

An earlier version of this framework defined a collective frame field as the expectation value of a single-link trace, $\langle\mathrm{Tr}(T^{a}U_{v\to w})\rangle$. That definition fails twice over. First, it violates **Elitzur's theorem** [24]: a local gauge symmetry cannot break spontaneously, and the expectation value of any gauge-variant local operator vanishes identically — the proposed field is exactly zero. Second, its index $a$ ranges over the $N^{2}$ generators of $U(N)$, whereas a frame field requires a four-valued local Lorentz index; teleparallel gravity is the gauge theory of translations, not of an internal unitary group, and no mechanism was given for selecting four directions out of $N^{2}$. Both failures are repaired at once by building the frame from the gauge-invariant loop observables of Section 3.2 and extracting the Lorentz index from the Clifford factor.

For a minimal diamond $\Diamond$ based at cell $x$, define the **internal-trace holonomy**

```math
\mathcal{W}_{\Diamond}\;\equiv\;\frac{1}{N}\,\mathrm{Tr}_{M_N}\!\big(W_{\Diamond}\big)\;\in\;\mathrm{Cl}(3,1),
```

(5.1)

which is exactly invariant under internal $U(N)$ transformations (conjugation at the base point traces out) and transforms by Spin conjugation under local frame rotations, $\mathcal{W}_\Diamond\to s_x\,\mathcal{W}_\Diamond\,s_x^{-1}$. Expand in the Clifford basis and extract the vector component,

```math
w^{a}(\Diamond)\;=\;\tfrac{1}{4}\,\mathrm{tr}_{\mathrm{Cl}}\!\big(\gamma^{a}\,\mathcal{W}_{\Diamond}\big),
```

(5.2)

which transforms as a **local Lorentz vector** — precisely the transformation law a co-frame must have. Coarse directions enter through the diamonds themselves: let $\Diamond_\mu(x)$ denote the minimal diamonds at $x$ whose extent is aligned with the emergent direction $\mu$ (temporal diamonds span adjacent layers; spatial diamonds lie within a cut). The fully gauge-invariant — and therefore Elitzur-safe — metric observable is the connected bilinear

```math
\boxed{
\mathbb{G}_{\mu\nu}(x)\;\propto\;\eta_{ab}\,\Big\langle\, w^{a}\big(\Diamond_\mu(x)\big)\;w^{b}\big(\Diamond_\nu(x)\big)\,\Big\rangle,
}
```

(5.3)

invariant under both $U(N)$ and local $\mathrm{Spin}(3,1)$ (the $\eta_{ab}$ contraction removes the frame ambiguity). Whether $\mathbb{G}_{\mu\nu}$ is nondegenerate and Lorentzian in the EGG ensemble is a sharp, computable question — the second signature test promised in Section 4.2 — and its agreement or disagreement with the mutual-information metric (4.3)–(4.4) is a stringent internal consistency check between the gauge and entanglement sectors of the framework. Note also the structural echo of Section 3.2: on a tree all $\mathcal{W}_\Diamond$ are trivially the identity, $w^{a}=0$, and $\mathbb{G}_{\mu\nu}$ vanishes — there is no metric content before loops. Geometry, in the holonomy sense, is *made of* the same cycles that carry gauge dynamics and code structure.

### 5.2 Frame section and torsion

For the teleparallel description one chooses a **frame section**: a smooth assignment $H^{a}{}_{\mu}(x)$ with $\eta_{ab}H^a{}_\mu H^b{}_\nu=\mathbb{G}_{\mu\nu}$, defined up to local Lorentz rotations — exactly the redundancy a tetrad is supposed to have. In the Weitzenböck gauge the torsion of the emergent frame is

```math
T^{a}{}_{\mu\nu}\;=\;\partial_{\mu}H^{a}{}_{\nu}-\partial_{\nu}H^{a}{}_{\mu},
```

(5.4)

reflecting the fact that the microscopic variables are transporters: parallel transport is fundamental, curvature derived, so torsion is the natural carrier of gravitational information.

### 5.3 The effective action and a selection principle for the GR point

An earlier version of this framework wrote the infrared action as a single torsion-squared invariant, $S^{a}{}_{\mu\nu}S_{a}{}^{\mu\nu}$, and invoked the Weitzenböck identity to claim equivalence with General Relativity. That claim was incorrect as stated: the identity holds only for one specific combination of the three independent quadratic torsion invariants. The general quadratic theory is the Hayashi–Shirafuji "new general relativity" family [25], whose generic members propagate extra (and typically ghostly) modes and are *not* equivalent to GR. The correct statement uses the **teleparallel torsion scalar**

```math
\mathbb{T}\;=\;\tfrac{1}{4}\,T^{\rho\mu\nu}T_{\rho\mu\nu}\;+\;\tfrac{1}{2}\,T^{\rho\mu\nu}T_{\nu\mu\rho}\;-\;T^{\rho}{}_{\rho\mu}\,T_{\nu}{}^{\nu\mu},
```

(5.5)

for which (conventions of [6]) $e\,\mathbb{T}=-e\,R+2\,\partial_\mu\!\big(e\,T_{\nu}{}^{\nu\mu}\big)$: this combination, and only this combination, differs from the Einstein–Hilbert Lagrangian by a boundary term. The conjectured infrared action is therefore

```math
\boxed{
S_{\mathrm{eff}}\;=\;\frac{1}{16\pi G_N}\int d^{4}x\;e\,\big(\mathbb{T}\;-\;2\,\Lambda_{\mathrm{ent}}\big)\;+\;S_{\mathrm{edge}},
}
```

(5.6)

with $e=\det H^a{}_\mu$ and $S_{\mathrm{edge}}$ the effective action of the matter-like modes (Section 6).

Why should coarse-graining land on the TEGR point of the Hayashi–Shirafuji family rather than a generic member? We propose a **selection principle**. The frame section $H^{a}{}_{\mu}$ of Section 5.2 is defined only up to local Lorentz rotations — the choice of Clifford basis per cell is pure convention introduced by the coarse-graining, with no microscopic counterpart. A legitimate effective action must therefore depend on the section only through boundary terms. Within quadratic torsion theories, invariance under local Lorentz rotations of the frame up to a total derivative singles out precisely the combination (5.5) [6,26]; the same point is also distinguished as the ghost-free member of the family. The TEGR point is thus not an aesthetic choice but the unique quadratic theory consistent with the conventional character of the frame section. Elevating this argument from a selection principle to a derivation — by performing the large-$N$ integration over short-wavelength holonomy fluctuations and exhibiting the coefficients of the three invariants — is the central open analytic problem of the framework, and we state it as such.

The Newton constant is **induced**, in the sense of Sakharov [13]: each cell of size $\ell_0$ carries $\sim N^{2}$ matrix degrees of freedom whose short-distance correlations stiffen the frame field, giving

```math
\frac{1}{16\pi G_N}\;\simeq\;\frac{c_G\,N^{2}}{\ell_0^{2}}
\qquad\Longleftrightarrow\qquad
\ell_P\;\simeq\;\frac{\ell_0}{\sqrt{16\pi c_G}\;N},
```

(5.7)

with $c_G$ an order-unity constant. Two remarks. First, the dimensions are now correct (an earlier draft's $\kappa\sim N\ell_0^{2}$ was dimensionally inconsistent for a gravitational stiffness). Second, (5.7) inverts the naive hierarchy: the discreteness scale $\ell_0$ sits a factor $\sim N$ *above* the Planck length. Large $N$ does not hide the graph deeper below $\ell_P$; it generates $\ell_P$ from a coarser substrate. The same $N^{2}$ counting will be required, independently, by black-hole thermodynamics in Section 8 — a nontrivial internal consistency condition that the earlier draft's $\ln N$ entropy law violated.

### 5.4 The cosmological seesaw

An earlier version of this framework set $\Lambda_{\mathrm{ent}}\sim R_{\mathrm{code}}^{-2}$ while simultaneously taking $R_{\mathrm{code}}\sim10$–$100\,\mu$m for laboratory phenomenology. Those two statements are mutually inconsistent by roughly sixty orders of magnitude (the observed $\Lambda\approx1.1\times10^{-52}\,\mathrm{m}^{-2}$ would require $R_{\mathrm{code}}$ of order the Hubble radius). The repair is a **seesaw**, and it converts the framework's worst internal inconsistency into its sharpest prediction.

The code structure of Section 3.4 protects information only up to the depth $R_{\mathrm{code}}$; beyond it, of order one quantum of correlation per code cell remains unresolved. The residual energy density is Casimir-like,

```math
\rho_{\mathrm{res}}\;\sim\;\frac{\hbar c}{R_{\mathrm{code}}^{4}},
```

(5.8)

and gravitates through the emergent Einstein equations with the induced $G_N$ of (5.7), giving

```math
\boxed{
\Lambda_{\mathrm{ent}}\;\simeq\;\frac{8\pi\,\ell_P^{2}}{R_{\mathrm{code}}^{4}}\,.
}
```

(5.9)

The Planck-squared prefactor is what the earlier draft was missing, and it is forced by dimensional analysis once the vacuum term is recognized as *gravitating residual energy* rather than a bare geometric scale. Inverting (5.9) against the observed cosmological constant fixes

```math
R_{\mathrm{code}}\;=\;\Big(\frac{8\pi\,\ell_P^{2}}{\Lambda_{\mathrm{obs}}}\Big)^{1/4}\;\approx\;40\text{–}90\;\mu\mathrm{m},
```

(5.10)

the spread reflecting order-unity normalization choices. This is, not coincidentally, the well-known "dark-energy length" $(\hbar c/\rho_\Lambda)^{1/4}\approx85\,\mu$m long noted in the experimental-gravity literature [27,28]; EGG gives that scale a microscopic identity — the information-protection depth of the causal network — and, crucially, ties it to a *second*, independent observable: the range of finite-distance deviations from Newtonian gravity (Section 7). One scale, two phenomena. This is the framework's flagship quantitative consequence.

### 5.5 Consistency with the Weinberg–Witten theorem

Any claim of an emergent graviton must answer Weinberg and Witten [29], who forbid a massless spin-2 particle in any Lorentz-invariant quantum field theory possessing a Lorentz-covariant conserved stress tensor. EGG evades the theorem's hypotheses rather than its conclusion: the fundamental theory is not a Lorentz-invariant QFT (Section 2.4 — the growth law selects a foliation, and exact Lorentz symmetry is at best emergent in the infrared), and no Lorentz-covariant conserved microscopic $T^{\mu\nu}$ exists on the graph. This is the same evasion route taken by induced-gravity and analogue-gravity constructions and by CDT. The theorem then functions not as an obstruction but as a *prediction of the framework's logic*: if gravity is emergent in this sense, exact microscopic Lorentz invariance must fail — which is precisely the falsifiable commitment made in Section 2.4.


---

## 6 Emergent Field Equations

*(Tier III.)*

In the geometric phase, variation of (5.6) with respect to the frame, translated to metric variables via $g_{\mu\nu}=\eta_{ab}H^a{}_\mu H^b{}_\nu$, yields — by virtue of the TEGR equivalence established for the specific scalar (5.5) — field equations of Einstein form:

```math
\boxed{
G_{\mu\nu}\;+\;\Lambda_{\mathrm{ent}}\,g_{\mu\nu}\;=\;8\pi G_N\,T^{(\mathrm{edge})}_{\mu\nu},
}
```

(6.1)

with $T^{(\mathrm{edge})}_{\mu\nu}=-\frac{2}{\sqrt{-g}}\frac{\delta S_{\mathrm{edge}}}{\delta g^{\mu\nu}}$ sourced by modes propagating on extended structures of the graph.

Equation (6.1) is an **infrared consistency condition**, not a microscopic law, and we state its intellectual lineage explicitly: it is the EGG realization of Jacobson's programme, in which the Einstein equation arises as an equation of state [14] and, in its modern form, as the condition of entanglement equilibrium — stationarity of entanglement entropy in small causal diamonds at fixed volume [15]. In EGG the small causal diamonds are not a device of the argument but the literal microscopic carriers of gauge, code, and geometric structure (Section 3.2); the framework can be read as a proposal for *what the microscopic degrees of freedom are* in a Jacobson-type derivation. As in hydrodynamics, the universality of (6.1) reflects the insensitivity of long-wavelength behavior to microscopic detail once the structural conditions — a stable geometric phase with protected correlations — are met. The numerical programme of Section 9 tests those structural conditions; it does not yet test the dynamics of (6.1), and verifying that dynamics (fluctuations, propagation, matter coupling) is the principal open problem downstream of the analytic task stated in Section 5.3.

---

## 7 Ultraviolet Structure and Phenomenology

*(Tier III, with the constraints stated honestly.)*

### 7.1 Two ultraviolet softening mechanisms

An earlier version of this framework described its ultraviolet behavior as an asymptotically safe fixed point while writing a beta function, $\beta_g=-(b_1/N)g^{3}$, whose only fixed point is Gaussian. We correct the characterization and separate two distinct mechanisms.

**Dimensional reduction.** The measured flow $D_s\to4/3$ at short scales is itself an ultraviolet regulator: the power counting of gravitational fluctuations is governed by the spectral dimension, and for $D_s<2$ the gravitational coupling becomes power-counting super-renormalizable [30]. In EGG the deep ultraviolet is not a smaller four-dimensional spacetime but an effectively $(4/3)$-dimensional tree — indeed (Section 3.2) a *pre-geometric* phase in which the gravitational observables literally vanish. The "trans-Planckian problem" is not solved but dissolved: geometric notions cease to apply below the tree-to-loop crossover.

**Large-$N$ asymptotic freedom of the holonomy sector.** The diamond weight (3.5) defines, in the geometric phase, a lattice gauge theory whose 't Hooft coupling runs as

```math
\beta_{\lambda_t}\;=\;-\,b_0\,\lambda_t^{2}\;+\;\mathcal{O}(\lambda_t^{3}),\qquad b_0>0,
```

(7.1)

i.e., the sector is **asymptotically free**, flowing to the Gaussian fixed point in the ultraviolet. We no longer characterize this as asymptotic safety; a nontrivial fixed point would require a zero of the beta function at $\lambda_t^{*}\neq0$, which nothing in the present construction supplies. (Asymptotic safety remains a logical possibility for the intermediate regime, but we make no claim.) The earlier draft's logarithmic running formula for $G(k)$ is withdrawn; the quantitative running of the gravitational coupling awaits the fluctuation analysis of Section 5.3.

### 7.2 The sub-millimeter prediction

The seesaw (5.9)–(5.10) fixes the range of finite-distance modifications of gravity. At separations approaching $R_{\mathrm{code}}$ the Newtonian potential acquires a Yukawa correction,

```math
\Phi(r)\;=\;-\,\frac{G_N M}{r}\Big[\,1\;+\;\alpha\,e^{-r/R_{\mathrm{code}}}\,\Big],
\qquad
R_{\mathrm{code}}\;\approx\;40\text{–}90\;\mu\mathrm{m}\ \ \text{(fixed by }\Lambda_{\mathrm{obs}}\text{)},
```

(7.2)

with the **range fixed by cosmology** and the amplitude $\alpha$ model-dependent (between $\mathcal{O}(N^{-2})$ and $\mathcal{O}(1)$ depending on how strongly the lightest massive collective mode couples; computing it is part of the open fluctuation analysis). The logical structure of the prediction is therefore asymmetric, and we state it precisely: *any* observed finite-range deviation from the inverse-square law must appear at $40$–$90\,\mu$m if the seesaw mechanism is right; null results at ever-smaller $\alpha$ progressively bound $N$ and the mode couplings but cannot by themselves falsify the mechanism. Torsion-balance experiments currently probe exactly this window — the strongest limits constrain $|\alpha|\lesssim\mathcal{O}(1)$ at $\lambda\approx40\,\mu$m, tightening rapidly toward $|\alpha|\lesssim10^{-2}$ near $200\,\mu$m [27,28,31] **[AUTHOR NOTE: pull the current published exclusion curve (Eöt-Wash 2020, HUST 2020, and any successors) and quote the exact $(\alpha,\lambda)$ limits here]** — so the prediction sits on the active experimental frontier rather than beyond it.

### 7.3 What is not testable, stated plainly

Collective gravitational excitations acquire modified dispersion at high momentum,

```math
\omega^{2}\;=\;k^{2}\Big[\,1\;+\;c_2\,(\ell_P k)^{2}\;+\;\dots\Big].
```

(7.3)

At gravitational-wave frequencies $(\ell_P k)^{2}\sim10^{-80}$: the correction is unobservable by some seventy orders of magnitude, and an earlier draft's claim that binary-merger observations constrain $N$ through (7.3) was numerically meaningless and is withdrawn. We retain (7.3) only as a statement of principle — Lorentz-violating dispersion is suppressed to second order in $\ell_P k$ because the foliation affects only the deep ultraviolet — and not as phenomenology.

### 7.4 Summary of observational handles

| Observable | Status in EGG | Honest assessment |
| --- | --- | --- |
| Cosmological constant $\Lambda_{\mathrm{obs}}$ | Fixes $R_{\mathrm{code}}\approx40\text{–}90\,\mu$m via the seesaw (5.9) | Postdiction / consistency; one parameter absorbed |
| Sub-mm inverse-square tests | Yukawa range **predicted** at $40\text{–}90\,\mu$m; amplitude open | The flagship target; on the current experimental frontier |
| Lunar laser ranging, BBN/CMB bounds on $\dot G/G$ | Constrain any cosmological-scale running of $G_N$ | Mild constraint pending the fluctuation analysis |
| GW dispersion | $(\ell_P k)^{2}$-suppressed | Not testable; previous claim withdrawn |
| UV dimensional reduction | $D_s\to4/3$ (Tier I, measured) | Structural; shared qualitatively with CDT/Hořava/asymptotic safety [30] |

---

## 8 Black-Hole Thermodynamics and Information

*(Tier III, now with internally consistent large-$N$ counting.)*

### 8.1 Entropy from the induced-gravity counting

In EGG a horizon is a maximal erasure surface: the boundary beyond which the code structure of Section 3.4 can no longer protect interior logical information for an exterior observer. The entropy is the entanglement entropy of the matrix degrees of freedom across that surface. Each cell of area $\ell_0^{2}$ carries $\sim N^{2}$ such degrees of freedom (the adjoint-valued link and vertex content), so

```math
S_{\mathrm{BH}}\;\simeq\;c_S\,N^{2}\,\frac{A}{\ell_0^{2}}
\;=\;\frac{A}{4\,G_N}
\qquad\text{provided}\qquad c_S=4\pi c_G\,,
```

(8.1)

using the induced Newton constant (5.7). The area law is thus not an additional postulate: **the same $N^{2}$ counting that generates $G_N$ generates $S_{\mathrm{BH}}=A/4G_N$**, with one order-unity matching condition between the two coarse-graining coefficients. This is the resolution of the "species problem" familiar from induced gravity — the species dependence of entanglement entropy cancels against the species dependence of the induced coupling [13,32,33] — promoted here to an internal consistency requirement of the framework. An earlier draft's entropy law $S\propto A\ln N$ is withdrawn: it counted only an $N$-dimensional register per cell while the gravitational stiffness was generated by $N^{2}$ adjoint modes, and the mismatch would have violated $S=A/4G$ within the framework's own conventions. Deviations from the strict area law remain possible for Planckian ($\ell_0$-scale) black holes, where the discrete cell structure resolves, but we make no sharp claim.

### 8.2 Evaporation and unitarity

Hawking radiation is read as the gradual erosion of the horizon's error-protecting capacity: as quanta are emitted, the operational code depth (Section 3.4) of the horizon region decreases, and logical information becomes progressively reconstructible from the exterior — the information was delocalized by construction, never destroyed. This picture aligns with the modern reconstruction-based account of evaporation [11,34] and requires no modification of quantum mechanics. We emphasize its standing honestly: EGG does not yet derive a Page curve or a microstate count; what it offers is a setting in which the qualitative requirements any such derivation must meet — area-law protected entropy, polynomial code depth, unitary leakage — arise from one mechanism. In the Clifford realization, toy versions of these statements (erasure thresholds of horizon-like regions, recovery of logical content as a region is progressively "evaporated") are directly simulable, and we flag them as a natural extension of the Section 9.5 programme.

---

## 9 Numerical Programme and Results

*(Tier I, with its scope stated exactly; Section 9.5 is the pre-registered Tier II protocol.)*

The numerical programme tests the **internal viability of the microscopic growth law** — whether it produces stable, sparse, geometric structure — and explicitly does *not* yet test the continuum identifications of Sections 5–8. All results below were obtained with **Model A** (the embedded regulator, Eq. 2.2a) at density exponent $p=4$; this scope restriction is the reason for the control protocol of Section 9.5.

We generated causal graphs at sizes $N_{\mathrm{v}}\in\{2\times10^{4},\,10^{5},\,3\times10^{5}\}$ with parameters $\gamma=0.9$, $\alpha=1.6$, $k_{\max}=12$, candidate pool $K=25$, and measured (i) connectivity statistics, (ii) the spectral dimension via Hutchinson trace estimation with Lanczos quadrature on the normalized undirected graph Laplacian, and (iii) a geometric proxy for causal protection depth. **[AUTHOR NOTE: state the number of independent random seeds per size; if results to date are single realizations, say so here and add seed variance in the rerun.]**

### 9.1 Graph connectivity and causal structure

The growth law generates DAGs with stable, modest local connectivity and no fragmentation, percolation collapse, or runaway valence. The mean undirected degree was

```math
\langle k\rangle \approx 3.84,\;\;3.99,\;\;4.25
\qquad\text{at}\qquad
N_{\mathrm{v}}=2\times10^{4},\;10^{5},\;3\times10^{5}.
```

The graphs are sparse and exhibit no small-world shortcuts at the scales probed. Two cautions, recorded for the rerun: the upward drift of $\langle k\rangle$ with size must be shown to saturate (slow densification would eventually produce expander-like behavior, for which $D_s$ diverges rather than settling at four), and the non-small-world claim should be quantified by verifying that graph diameter scales as $N_{\mathrm{v}}^{1/4}$ rather than $\log N_{\mathrm{v}}$. Both checks are in the Section 9.5 protocol. We also retract a suggestion in an earlier draft that $\langle k\rangle\to4$ is itself "consistent with" four-dimensionality; mean degree has no clean relation to emergent dimension, and we let the spectral and order-theoretic estimators carry that burden.

### 9.2 Spectral dimension and emergent geometry

The return probability and running spectral dimension are

```math
P(\sigma)=\frac{1}{N_{\mathrm{v}}}\,\mathrm{Tr}\,e^{-\sigma L_{\mathrm{norm}}},
\qquad
D_s(\sigma)=-2\,\frac{d\ln P}{d\ln\sigma}.
```

This probe is deliberately conservative: it discards causal directionality, assumes no manifold prior, and is sensitive to spectral pathologies and shortcuts. (On any finite graph $P(\sigma)\to1/N_{\mathrm{v}}$ as $\sigma\to\infty$, driving $D_s\to0$; the infrared plateau is therefore a *window* below the spectral-gap scale, and the rerun will report plateau windows and verify that they widen with system size, rather than extracting plateaus from fixed fractions of the diffusion range as was done to date.)

Across all sizes the spectral dimension is strongly scale dependent:

```math
\begin{aligned}
N_{\mathrm{v}}=2\times10^{4}:&\quad D_s^{\mathrm{UV}}\approx1.20,\quad D_s^{\mathrm{IR}}\approx3.42,\\
N_{\mathrm{v}}=10^{5}:&\quad D_s^{\mathrm{UV}}\approx1.21,\quad D_s^{\mathrm{IR}}\approx3.63,\\
N_{\mathrm{v}}=3\times10^{5}:&\quad D_s^{\mathrm{UV}}\approx1.22,\quad D_s^{\mathrm{IR}}\approx3.81.
\end{aligned}
```

Two features stand out. First, the ultraviolet value stabilizes at $D_s^{\mathrm{UV}}\simeq1.2$–$1.4$, consistent with the universal branched-polymer/random-tree value $4/3$ and only weakly sensitive to causal directionality (checked separately with directed Laplacians): the microscopic phase sits in a known universality class, with no tuning toward a target ultraviolet dimension. Second, the infrared value increases monotonically with size with no sign of saturation below four. Within Model A at $p=4$, this establishes a robust dimensional flow from a tree-like ultraviolet to an approximately four-dimensional infrared.

What it does **not** yet establish is that the infrared "four" is emergent rather than transduced from the inputs ($p=4$; the embedding; the lightcone-aligned pool). That question is answerable only by the controls of Section 9.5, and we decline to claim more than the data support.

### 9.3 Causal protection depth, and a corrected reading of the data

As a proxy for code depth we measured $d_{\mathrm{geo}}(R)$, the minimal graph distance separating past and future temporal boundaries of a causal ball of radius $R$. For the $N_{\mathrm{v}}=3\times10^{5}$ graph,

```math
d_{\mathrm{geo}}(R{=}10)\approx8,\qquad
d_{\mathrm{geo}}(R{=}20)\approx15,\qquad
d_{\mathrm{geo}}(R{=}40)\approx18.
```

We correct the interpretation given in an earlier draft. The growth from $R=10$ to $R=20$ is consistent with approximately **linear** scaling of protection depth, in line with the polynomial law (3.8) and the locality bounds behind it [21] — and *inconsistent* with the exponential law that draft had posited. The apparent flattening at $R=40$ is a **finite-size artifact**: a ball of radius 40 in a four-dimensional geometry contains of order $40^{4}\sim10^{6}$ vertices, exceeding the entire graph, so that data point saturates the system and carries no scaling information. The rerun will confine $R$ to the regime $R^{4}\ll N_{\mathrm{v}}$ and, in the Clifford realization, replace this proxy by the operational distance itself (erasure-recovery probability, Section 3.4).

### 9.4 Summary of established findings

Within the stated scope — Model A, $p=4$, single parameter point — the numerics establish that: the growth law produces large, stable, sparse causal graphs free of connectivity pathologies; the ultraviolet geometry lies in the branched-polymer universality class, $D_s^{\mathrm{UV}}\simeq4/3$; the infrared spectral dimension flows toward four with increasing system size; and the causal protection depth grows polynomially, consistent with (3.8). These are the Tier I claims of this paper, no more and no less.

### 9.5 Decisive control experiments: a pre-registered protocol

We commit in advance to the following experiments and to the interpretations of their possible outcomes, so that the framework's central empirical claim is exposed to falsification rather than insulated from it.

**(C1) Density-exponent scan.** Rerun the full programme at $p\in\{2,3,5,6\}$ (Model A unchanged otherwise). *Pre-registered interpretations:* if $D_s^{\mathrm{IR}}\approx4$ for all $p$, dimensional emergence is established in the strong sense (a major result); if $D_s^{\mathrm{IR}}$ tracks $p$, the strong emergence claim is **withdrawn** and the model is reinterpreted as a dimension-transduction map from causal density to geometry (a well-defined, weaker result that we would still report); if neither, the map $D_s^{\mathrm{IR}}(p)$ is characterized as the primary finding.

**(C2) Embedding ablation and the intrinsic model.** Within Model A, vary $d_{\mathrm{emb}}\in\{2,3,4,5\}$ and deform the candidate-pool geometry; then run **Model B** (Eq. 2.2b), which uses no embedding at all. *Pre-registered interpretations:* survival of the dimensional flow in Model B establishes background-independent emergence and becomes the paper's headline; failure confines all Tier I claims to the regulated theory and demands quantification of regulator dependence.

**(C3) Statistics and finite-size scaling.** Multiple independent seeds per size with error bars; extension to $10^{6}$ vertices (the Hutchinson–Lanczos pipeline scales); plateau extraction by stationarity of $D_s(\sigma)$ with reported windows; fits of $D_s^{\mathrm{IR}}(N_{\mathrm{v}})=4-c\,N_{\mathrm{v}}^{-\theta}$ against alternatives that asymptote below four.

**(C4) Independent dimension estimators.** The Myrheim–Meyer order-theoretic dimension [35,36] (purely causal, embedding-free); the Hausdorff dimension from ball-volume scaling $V(r)\sim r^{d_H}$, with the sharp discriminator that branched polymers have $d_H=2$ so a genuinely geometric infrared requires $d_H\to4$ alongside $D_s\to4$; the walk-dimension consistency relation $d_w=2d_H/D_s$; and the combinatorial Laplacian alongside the normalized one.

**(C5) Phase diagram.** Scan $(\gamma,\alpha)$ to map the tree / geometric / crumpled-expander phases and demonstrate that $D_s^{\mathrm{IR}}\approx4$ occupies a finite region; monitor $\langle k\rangle(N_{\mathrm{v}})$ and diameter scaling per Section 9.1.

**(C6) Curvature.** The Benincasa–Dowker action density [37] (cited but unused in the earlier draft) as a discrete Ricci-scalar diagnostic of near-flatness, and the Ollivier–Ricci curvature distribution [38].

**(C7) The Clifford tensor-network campaign.** Realize the EGG ensemble (Section 3.3) with random Clifford isometries on the existing graphs and compute: mutual-information decay $\mathcal{I}(x,y)$ versus graph distance (testing the world-function ansatz (4.2)); ball-entropy scaling (area law?); positive-definiteness and isotropy of the information metric (4.3); the signature and nondegeneracy of the holonomy bilinear $\mathbb{G}_{\mu\nu}$ (5.3) and its agreement with the information metric; and the operational code distance via erasure decoding, fitting $(\nu,\zeta)$ in (3.8). This campaign converts the framework's information-theoretic core from conjecture to measurement.

---

## 10 Conclusion

Entanglement–Gauge Gravity proposes that spacetime, gravity, and gauge structure are macroscopic manifestations of a single microscopic substrate: a growing causal graph carrying finite operator algebras, with gauge-invariant consistency enforced on its causal diamonds. The revised framework is organized around one structural principle — on a tree there is no gauge dynamics, no code, and no geometry; all three are made of loops and switch on together at the tree-to-loop crossover — and one quantitative wager — the seesaw $\Lambda_{\mathrm{ent}}\simeq8\pi\ell_P^{2}/R_{\mathrm{code}}^{4}$, which ties the observed dark-energy scale to a predicted modification of gravity at $40$–$90\,\mu$m, on the active frontier of torsion-balance experiments.

The paper's claims are tiered, and we restate them as such. Established numerically (Tier I): the growth law supports a stable, sparse causal phase whose spectral dimension flows from the branched-polymer value $4/3$ in the ultraviolet toward four in the infrared, with polynomial causal protection depth. Defined and computable (Tier II): the quantum state of the network as a dynamically grown random tensor network — exactly simulable in its Clifford realization — together with the information metric, the holonomy metric, curvature diagnostics, operational code distance, and, decisively, the control experiments (density-exponent scan, embedding ablation, intrinsic-locality model) that will determine whether the infrared dimension is emergent or injected. Conjectural (Tier III): the teleparallel effective action at the GR-equivalent point selected by the frame-section redundancy, the induced Newton constant and the matching Bekenstein–Hawking entropy from one $N^{2}$ counting, the Einstein equations as a Jacobson-type consistency condition, and the cosmological seesaw.

The framework's honest vulnerabilities are equally explicit: a preferred foliation with emergent Lorentz invariance unproven; a regulated growth law whose background-independent variant is defined but untested; and a continuum limit whose central analytic step — the large-$N$ fluctuation integration that should produce (5.5)–(5.7) — remains open. We regard the combination of a falsifiable laboratory-scale prediction, a pre-registered numerical protocol capable of killing the core claim, and a stated analytic programme as the appropriate standard for a proposal of this scope. Whether or not Nature realizes this structure, the framework sharpens the question it was built to address: what spacetime is, and what it must be built from.

---

## 11 Outlook (explicitly speculative)

If the control experiments of Section 9.5 uphold the emergence claim and the analytic programme of Section 5.3 closes, the resulting picture would be economical: spacetime as the hydrodynamic phase of causal information flow; gravity as the universal infrared description of holonomy stiffness, with the equivalence principle reflecting the universality of that description rather than a geometric axiom; the ultraviolet not as a violent trans-Planckian regime but as a pre-geometric tree in which gravitational observables simply vanish; black-hole entropy and the induced Newton constant as two readings of one $N^{2}$ counting, with evaporation as decoded leakage rather than destruction; dark energy as the gravitating residue of finite information depth, already tied by the seesaw to a laboratory length; and the arrow of time as the growth direction of the causal network, with time-reversal symmetry emergent and approximate. Matter would be the physics of stable excitation patterns on the loop structure — a sector about which the present framework says almost nothing concrete, and which we list first among its open problems, alongside the fluctuation analysis, the restoration (or observable violation) of infrared Lorentz invariance, and the derivation of a Page curve in the Clifford realization. Each of these is a place where the framework can fail; that is what makes it worth pursuing.

---

## Appendix A — Glossary (revised entries marked •)

* **$\ell_P$** — Planck length, $\sqrt{\hbar G/c^{3}}$. • In EGG an *emergent* scale: $\ell_P\simeq\ell_0/(\sqrt{16\pi c_G}\,N)$, Eq. (5.7).
* **$\ell_0$** — microscopic graph scale. • Sits a factor $\sim N$ *above* $\ell_P$.
* **Causal graph / growth law** — as before; • now in two variants: Model A (embedded regulator, simulated) and Model B (intrinsic locality, fundamental proposal), Eqs. (2.2a/b).
* **Layer index $t$** — • the discrete time of the growth schedule (2.1); replaces the circular "time defined by vertex count" of the earlier draft.
* **Minimal causal diamond $\Diamond$** — • a pair of interior-disjoint directed paths between $p\prec q$; the elementary loop of the causal graph; carrier of holonomy, stabilizer, and geometric content.
* **Diamond holonomy $W_\Diamond$ / consistency weight** — • Eqs. (3.4)–(3.5); the gauge-invariant replacement for the single-link "stabilizers" of the earlier draft; maximized on flat configurations.
* **Co-emergence principle** — • on a tree the cycle space is empty, so gauge dynamics, error correction, and holonomy geometry all vanish identically; all three switch on together at the tree-to-loop crossover controlled by $\gamma$.
* **EGG ensemble** — • the ensemble of states $|\Psi_t\rangle$ (3.7) generated by reading the growth law as an isometric tensor network; in its Clifford realization, exactly simulable (Gottesman–Knill).
* **Operational code depth** — • erasure-recovery probability of causal balls in the Clifford realization; polynomial law (3.8) replaces the retracted exponential ansatz.
* **Information world function $\sigma(x,y)$** — • Eq. (4.2); bilocal distance functional built from mutual-information decay; the metric is its coincidence-limit mixed derivative (4.3), replacing the non-tensorial Hessian construction.
* **Holonomy metric $\mathbb{G}_{\mu\nu}$** — • Eq. (5.3); the Elitzur-safe, fully gauge-invariant metric bilinear built from Clifford vector components of diamond holonomies.
* **Frame section $H^{a}{}_\mu$** — • a local-Lorentz choice of square root of $\mathbb{G}_{\mu\nu}$; its conventional character is the selection principle for the TEGR point.
* **TEGR torsion scalar $\mathbb{T}$** — • Eq. (5.5); the unique quadratic torsion combination equivalent to GR up to a boundary term; replaces the incorrect single-invariant action of the earlier draft.
* **Cosmological seesaw** — • $\Lambda_{\mathrm{ent}}\simeq8\pi\ell_P^{2}/R_{\mathrm{code}}^{4}$, Eq. (5.9); fixes $R_{\mathrm{code}}\approx40$–$90\,\mu$m and replaces the internally inconsistent $R_{\mathrm{code}}^{-2}$ law.
* **Dimension transduction** — • the pre-registered fallback interpretation if the infrared spectral dimension is found to track the density exponent $p$ (protocol C1).
* **Spectral dimension, UV/IR, double-cone cell, large-$N$ limit, teleparallel gravity, Weitzenböck identity, emergent geometry** — as in the earlier draft.

---

## References

[1] L. Bombelli, J. Lee, D. Meyer, R. D. Sorkin, "Space-time as a causal set," *Phys. Rev. Lett.* **59**, 521 (1987). **[AUTHOR NOTE: the earlier draft cited "Phys. Rev. D 34 (1986) 373" — verify and correct.]**
[2] D. P. Rideout, R. D. Sorkin, "Classical sequential growth dynamics for causal sets," *Phys. Rev. D* **61**, 024002 (2000).
[3] J. Ambjørn, J. Jurkiewicz, R. Loll, "Spectral dimension of the universe," *Phys. Rev. Lett.* **95**, 171301 (2005).
[4] R. Loll, "Quantum gravity from causal dynamical triangulations: a review," *Class. Quantum Grav.* **37**, 013002 (2020).
[5] K. Hayashi, T. Shirafuji — see [25].
[6] R. Aldrovandi, J. G. Pereira, *Teleparallel Gravity: An Introduction* (Springer, 2013).
[7] M. Reuter, "Nonperturbative evolution equation for quantum gravity," *Phys. Rev. D* **57**, 971 (1998).
[8] T. Konopka, F. Markopoulou, L. Smolin, "Quantum graphity," arXiv:hep-th/0611197 (2006).
[9] C. A. Trugenberger, "Combinatorial quantum gravity: geometry from random bits," *JHEP* **09**, 045 (2017).
[10] S. Wolfram, "A class of models with the potential to represent fundamental physics," *Complex Systems* **29**, 107 (2020).
[11] F. Pastawski, B. Yoshida, D. Harlow, J. Preskill, "Holographic quantum error-correcting codes," *JHEP* **06**, 149 (2015).
[12] P. Hayden, S. Nezami, X.-L. Qi, N. Thomas, M. Walter, Z. Yang, "Holographic duality from random tensor networks," *JHEP* **11**, 009 (2016).
[13] A. D. Sakharov, "Vacuum quantum fluctuations in curved space and the theory of gravitation," *Dokl. Akad. Nauk SSSR* **177**, 70 (1967); reprinted *Gen. Rel. Grav.* **32**, 365 (2000).
[14] T. Jacobson, "Thermodynamics of spacetime: the Einstein equation of state," *Phys. Rev. Lett.* **75**, 1260 (1995).
[15] T. Jacobson, "Entanglement equilibrium and the Einstein equation," *Phys. Rev. Lett.* **116**, 201101 (2016).
[16] L. Bombelli, J. Henson, R. D. Sorkin, "Discreteness without symmetry breaking: a theorem," *Mod. Phys. Lett. A* **24**, 2579 (2009).
[17] P. Hořava, "Spectral dimension of the universe in quantum gravity at a Lifshitz point," *Phys. Rev. Lett.* **102**, 161301 (2009).
[18] A. Eichhorn, S. Mizera, "Spectral dimension in causal set quantum gravity," *Class. Quantum Grav.* **31**, 125007 (2014).
[19] A. Yu. Kitaev, "Fault-tolerant quantum computation by anyons," *Ann. Phys.* **303**, 2 (2003).
[20] D. Gottesman, "The Heisenberg representation of quantum computers," arXiv:quant-ph/9807006 (1998); S. Aaronson, D. Gottesman, *Phys. Rev. A* **70**, 052328 (2004).
[21] S. Bravyi, D. Poulin, B. Terhal, "Tradeoffs for reliable quantum information storage in 2D systems," *Phys. Rev. Lett.* **104**, 050503 (2010).
[22] J. L. Synge, *Relativity: The General Theory* (North-Holland, 1960).
[23] C. Cao, S. M. Carroll, S. Michalakis, "Space from Hilbert space: recovering geometry from bulk entanglement," *Phys. Rev. D* **95**, 024031 (2017).
[24] S. Elitzur, "Impossibility of spontaneously breaking local symmetries," *Phys. Rev. D* **12**, 3978 (1975).
[25] K. Hayashi, T. Shirafuji, "New general relativity," *Phys. Rev. D* **19**, 3524 (1979).
[26] M. Krššák, E. N. Saridakis, "The covariant formulation of f(T) gravity," *Class. Quantum Grav.* **33**, 115009 (2016).
[27] E. G. Adelberger, B. R. Heckel, A. E. Nelson, "Tests of the gravitational inverse-square law," *Annu. Rev. Nucl. Part. Sci.* **53**, 77 (2003).
[28] R. Sundrum, "Fat gravitons, the cosmological constant and submillimeter tests," *Phys. Rev. D* **69**, 044014 (2004).
[29] S. Weinberg, E. Witten, "Limits on massless particles," *Phys. Lett. B* **96**, 59 (1980).
[30] S. Carlip, "Dimension and dimensional reduction in quantum gravity," *Class. Quantum Grav.* **34**, 193001 (2017).
[31] J. G. Lee, E. G. Adelberger, T. S. Cook, S. M. Fleischer, B. R. Heckel, "New test of the gravitational $1/r^{2}$ law at separations down to 52 μm," *Phys. Rev. Lett.* **124**, 101101 (2020); W.-H. Tan *et al.*, *Phys. Rev. Lett.* **124**, 051301 (2020).
[32] T. Jacobson, "Black hole entropy and induced gravity," arXiv:gr-qc/9404039 (1994).
[33] V. P. Frolov, D. V. Fursaev, A. I. Zelnikov, "Statistical origin of black hole entropy in induced gravity," *Nucl. Phys. B* **486**, 339 (1997).
[34] P. Hayden, J. Preskill, "Black holes as mirrors: quantum information in random subsystems," *JHEP* **09**, 120 (2007).
[35] J. Myrheim, "Statistical geometry," CERN preprint TH-2538 (1978).
[36] D. A. Meyer, *The Dimension of Causal Sets*, PhD thesis, MIT (1988).
[37] D. M. T. Benincasa, F. Dowker, "The scalar curvature of a causal set," *Phys. Rev. Lett.* **104**, 181301 (2010).
[38] Y. Ollivier, "Ricci curvature of Markov chains on metric spaces," *J. Funct. Anal.* **256**, 810 (2009).
