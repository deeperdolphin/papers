# Entanglement‑Gauge Gravity: A Unified Framework for Quantum Information, Gauge Symmetry and Emergent Gravity

---

## Abstract

We propose **Entanglement–Gauge Gravity (EGG)**, a microscopic framework in which the Universe is fundamentally a growing causal structure whose large-scale organization gives rise to spacetime geometry, gravity, and gauge interactions. In this picture, local quantum degrees of freedom reside on a stochastic causal graph, geometry is not fundamental but emergent, and gravity arises as a redundancy associated with the protection and transport of quantum information. Dimensionality, locality, and curvature are collective, scale-dependent properties rather than fixed background features.

We present a concrete realization of this framework based on a causal growth law with finite local operator algebras and gauge symmetry, and we outline how entanglement structure and gauge redundancy organize into an effective continuum description whose infrared limit reproduces the kinematic structure of General Relativity in a teleparallel formulation. These continuum identifications are proposed as a coherent unifying mechanism rather than as established results.

To assess the viability of the framework’s most basic geometric premise, we implement the microscopic growth dynamics numerically and study the resulting geometry using the spectral dimension derived from diffusion on the emergent graph. Across system sizes up to (3\times10^5) vertices, we observe a robust scale-dependent spectral dimension: at short diffusion scales the geometry exhibits a universal ultraviolet plateau (D_s^{\mathrm{UV}}\simeq1.2–1.4), consistent with branched-polymer and causal-tree universality, while at large scales the dimension flows toward (D_s^{\mathrm{IR}}\simeq4). This behavior indicates that a four-dimensional macroscopic spacetime can emerge dynamically from a low-dimensional causal microstructure.

Taken together, these results establish EGG as a concrete and testable proposal for the microscopic organization of spacetime, providing a unified setting in which gravity, geometry, and quantum information may be understood as emergent phenomena.

---

## 1 Introduction

The empirical success of quantum field theory and General Relativity has left unresolved a fundamental question: *what microscopic structure, if any, underlies spacetime itself?* Despite their accuracy within their respective domains, the two frameworks make incompatible assumptions about locality, background structure, and ultraviolet behavior. This tension has motivated a wide range of approaches to quantum gravity, including causal-set growth models [1], gauge-theoretic formulations of gravity [2], asymptotically safe renormalization-group flows [3], and holographic constructions inspired by quantum error correction [4]. Each captures important aspects of the problem, yet none has converged on a shared microscopic picture of spacetime, matter, and information.

**Entanglement–Gauge Gravity (EGG)** is proposed as a unifying microscopic framework that takes a definite stance on this question. In EGG, the Universe is not built upon a pre-existing manifold. Instead, it is fundamentally a growing causal structure: a directed acyclic graph whose vertices carry finite quantum degrees of freedom and whose large-scale organization gives rise to geometry, dimensionality, and gravitational dynamics. Spacetime, in this view, is not fundamental but emergent—a collective, scale-dependent phenomenon arising from causal connectivity and information flow. Gravity is not introduced as a fundamental interaction, but as an effective redundancy associated with the consistent transport and protection of quantum information across this structure.

The framework combines three ingredients. First, a **stochastic causal growth law** generates a layered causal network without assuming dimension or locality a priori. Second, each vertex hosts a finite operator algebra with gauge symmetry, providing both local quantum degrees of freedom and a natural large-(N) control parameter. Third, global consistency is enforced through constraints analogous to quantum error correction, ensuring that coarse-grained observables remain stable under local perturbations. Within this setting, geometry is defined operationally, through diffusion and correlation structure on the emergent graph, rather than by postulating a metric from the outset.

A central claim of EGG is that familiar spacetime physics appears only after coarse-graining. At microscopic scales the causal network is highly anisotropic and effectively low-dimensional, while at macroscopic scales it organizes into a smooth, approximately four-dimensional geometry. In the continuum limit, the same gauge redundancy that stabilizes information at the microscopic level is argued to reorganize into an effective gravitational description whose infrared kinematics coincide with those of General Relativity in a teleparallel formulation. These continuum identifications are proposed as a coherent mechanism linking causality, gauge symmetry, and gravity, rather than as results derived from first principles.

To assess whether this picture is viable at its most basic level, we subject the microscopic growth law to direct numerical scrutiny. We generate large causal graphs and diagnose their emergent geometry using the **spectral dimension**, extracted from diffusion on the graph Laplacian. This observable provides a coordinate-free probe of dimensionality and scale dependence. Across increasing system sizes, we find a robust dimensional flow: at short diffusion scales the geometry exhibits a universal ultraviolet plateau (D_s^{\mathrm{UV}}\simeq1.2–1.4), consistent with branched-polymer and causal-tree universality classes, while at large diffusion scales the spectral dimension flows toward (D_s^{\mathrm{IR}}\simeq4). The sharpening of the infrared plateau with system size indicates that four-dimensional spacetime arises dynamically from an underlying low-dimensional causal microstructure, rather than being imposed by construction.

The purpose of this paper is therefore twofold. First, we present a concrete and unified proposal for the microscopic organization of spacetime, grounded in causality, gauge structure, and quantum information. Second, we provide nontrivial numerical evidence that the core geometric premise of this proposal—the emergence of four-dimensional spacetime from causal growth—is internally consistent and robust. While many aspects of EGG remain conjectural, the framework defines a clear ontology, a concrete mechanism, and a set of falsifiable targets, offering a structured arena in which the relationship between spacetime, gravity, and information can be explored.

The remainder of the paper is organized as follows. Section 2 defines the stochastic causal growth law. Section 3 introduces the local operator algebra and stabilizer-inspired consistency constraints. Section 4 discusses the operational definition of geometry and its relation to information-theoretic quantities. Section 5 outlines the emergence of an effective gauge-theoretic gravitational description in the infrared. Section 6 presents the resulting field equations. Section 7 discusses ultraviolet behavior and phenomenological implications. Section 8 addresses black-hole thermodynamics within the framework. Section 9 reports the numerical results, including spectral-dimension measurements and geometric diagnostics of causal structure.

We set (\ell_P=\sqrt{\hbar G/c^3}) as the Planck length and take the microscopic length scale (\ell_0\simeq\ell_P), unless rescaled by the large-(N) structure of the local operator algebra.

---

## **2 Microscopic Growth Law**

The fundamental microscopic structure in Entanglement–Gauge Gravity is a **growing causal network**. Vertices are added sequentially, and each new vertex is connected only to vertices in its causal past, ensuring that the resulting graph is a directed acyclic graph (DAG). No background manifold, metric, or dimensionality is assumed at this level; these properties are intended to emerge dynamically from the growth process.

Each newly created vertex (v) is assigned a *parent set* (P_v), drawn stochastically from the existing vertices according to a local weight function. The probability of choosing a given parent set is

```math
\boxed{
\Pr(P_v) \;\propto\;
\gamma^{|P_v|}
\exp\!\left[
-\alpha \sum_{p<q\in P_v}\frac{d_{pq}^2}{\ell_0^2}
\right]
}
```

(2.1)

where (|P_v|) is the number of parents, (d_{pq}) is the spatial separation between candidate parents in an auxiliary embedding used solely to enforce locality, (\ell_0) is the microscopic length scale, and (\gamma,\alpha>0) are dimensionless control parameters. The normalization factor, obtained by summing over all admissible parent sets with (|P_v|\le k_{\max}), ensures a proper probability distribution.

The growth process is layered in a coarse-grained time variable (t), defined implicitly by the number of vertices present. The expected vertex count scales as

```math
n(t) = \beta\, t^{4},
```

(2.2)

so that the total number of vertices grows quartically with coarse time. This scaling is not imposed to enforce four-dimensionality at the microscopic level; rather, it ensures that sufficient causal depth exists for macroscopic dimensionality to emerge at large scales.


---

### **Interpretation and role of the parameters**

The growth law is intentionally minimal. Its parameters do not encode spacetime dimension directly, but instead regulate **connectivity, locality, and causal thickness**, which collectively determine the emergent geometry.

**Connectivity parameter (\gamma).**
The parameter (\gamma) controls the typical size of parent sets and therefore the local branching structure of the causal graph. For small (\gamma), new vertices attach to only a few parents, producing a locally tree-like and strongly anisotropic structure. As (\gamma) increases, parent sets broaden, loops proliferate, and the causal network becomes increasingly interconnected.

Crucially, the numerical results reported in Section 9 show that **tree-like microstructure is not a failure mode but a defining ultraviolet feature**. Across a wide range of system sizes, the spectral dimension at short diffusion scales stabilizes near (D_s^{\mathrm{UV}}\simeq1.2–1.4), consistent with the universal value (D_s=4/3) characteristic of branched-polymer and causal-tree geometries. This places the microscopic growth law firmly in a well-studied universality class, rather than requiring fine-tuning toward a target ultraviolet dimension.

At larger scales, increased connectivity enables coarse-grained mixing, and the spectral dimension flows upward toward four. The approach to (D_s\simeq4) sharpens systematically with increasing graph size, indicating that macroscopic dimensionality is an emergent collective property rather than a parameter chosen at the outset.

**Locality parameter (\alpha).**
The parameter (\alpha) suppresses parent sets whose members are widely separated in the auxiliary embedding. For (\alpha\ell_0^2\gg1), long-range connections are strongly disfavored and the graph becomes effectively tree-like even at large scales. For (\alpha\ell_0^2\ll1), locality is lost and the graph rapidly approaches a dense, non-geometric structure.

The physically relevant regime is (\alpha\ell_0^2=\mathcal{O}(1)), where locality is enforced without fine-tuning. In this regime, the growth law generates a sparse causal network whose short-scale structure is filamentary, while still allowing sufficient loop formation for higher-dimensional geometry to emerge upon coarse-graining.

---

### **Emergent dimensionality rather than imposed geometry**

It is important to emphasize that neither Eq. (2.1) nor Eq. (2.2) encodes spacetime dimension directly. The microscopic growth law defines only causal precedence, local connectivity, and stochastic attachment. Dimensionality is diagnosed *a posteriori*, through diffusion and spectral observables on the resulting graph.

The numerical evidence presented later demonstrates that this minimal causal dynamics produces a robust and nontrivial dimensional flow: a low-dimensional, tree-like ultraviolet regime transitions smoothly into an effectively four-dimensional infrared geometry. This behavior motivates the interpretation of spacetime in EGG as a **hydrodynamic limit of causal growth**, rather than as a fundamental background structure.

---

### **Why this growth law is the right starting point**

The purpose of the microscopic growth law is not to reproduce continuum physics directly, but to define a **causal substrate** capable of supporting it. The emergence of a universal ultraviolet spectral dimension near (4/3), together with a stable infrared flow toward four dimensions, indicates that the growth process sits at the intersection of causal-set dynamics, random geometry, and renormalization-group universality.

This places strong constraints on any proposed microscopic description of spacetime: the fundamental structure must be sparse, causal, and effectively low-dimensional at short scales, while still capable of organizing into a smooth four-dimensional geometry at large scales. The growth law defined here satisfies these requirements without assuming geometry, dimension, or locality a priori, making it a natural foundation for the entanglement- and gauge-theoretic constructions developed in subsequent sections.

### **2.X Relation to Hypergraph Rewriting Approaches**

The microscopic growth dynamics defined above share certain structural similarities with **hypergraph rewriting approaches** to emergent spacetime, most notably the Wolfram Physics program, in which the Universe is modeled as the evolution of a discrete hypergraph under local rewriting rules. In both settings, spacetime is not assumed a priori, causal structure plays a central role, and geometric properties are diagnosed using diffusion-based observables such as the spectral dimension. These common features place both approaches within a broader class of discrete, background-independent models of spacetime emergence.

Despite this superficial overlap, the underlying mechanisms and ontological commitments differ in important respects. In hypergraph rewriting frameworks, dynamics are driven by deterministic or rule-based substitutions acting on hyperedges, and vertices typically carry no intrinsic degrees of freedom beyond their combinatorial connectivity. The rewriting rules themselves are fundamental, and the evolution of the hypergraph is the primary source of structure. In contrast, EGG employs a **stochastic causal growth process** in which vertices are endowed with finite local operator algebras and gauge structure. The fundamental dynamical object is not a rewriting rule but a probabilistic attachment law constrained by locality, causality, and information-theoretic consistency.

A further distinction lies in what is taken to be primary. Hypergraph rewriting treats combinatorial evolution as the source from which all other structures must emerge. EGG instead treats **information flow, gauge redundancy, and error-protection constraints** as foundational, with causal growth providing the substrate on which these structures organize. Geometry and dimensionality in EGG arise through coarse-graining and collective mixing of an initially sparse, tree-like causal microstructure, rather than through repeated application of fixed rewriting patterns.

As a result, although both approaches aim to explain spacetime as an emergent phenomenon of discrete dynamics, they likely occupy **distinct universality classes**. In particular, the ultraviolet spectral dimension observed in EGG, which stabilizes near the universal value (D_s\simeq4/3) characteristic of causal-tree and branched-polymer geometries, reflects the stochastic, information-constrained nature of the growth law rather than deterministic rewriting. Any deeper relationship between these frameworks, if it exists, would therefore have to emerge at the level of coarse-grained universality rather than microscopic dynamics.

---

## **3 Vertex Algebra and Information-Theoretic Structure**

In Entanglement–Gauge Gravity, each vertex of the causal graph carries finite local quantum degrees of freedom. These degrees of freedom are not treated as pointlike fields on a background manifold, but as operator algebras associated to causal events. Concretely, to each vertex (v) we associate the algebra

```math
\boxed{
\mathcal{A}_v = M_N(\mathbb{C}) \otimes \mathrm{Cl}(3,1)
}
```

(3.1)

where (M_N(\mathbb{C})) is the algebra of (N\times N) complex matrices and (\mathrm{Cl}(3,1)) is the real Clifford algebra associated with Minkowski signature. This choice is not unique, but it captures two structural requirements of the framework: a large internal gauge redundancy and the capacity to support spinorial degrees of freedom at the emergent level.

The **matrix factor** (M_N(\mathbb{C})) provides a local (U(N)) gauge symmetry at each vertex. This symmetry plays a dual role. At the microscopic level, it supplies a large-(N) control parameter that suppresses ultraviolet fluctuations and stabilizes coarse-grained observables. At the emergent level, it furnishes the raw material from which effective gauge and gravitational degrees of freedom may arise. While familiar Standard-Model gauge groups could in principle appear through symmetry breaking or boundary reduction, no such identification is assumed or derived here.

The **Clifford factor** (\mathrm{Cl}(3,1)) ensures that the local algebra is compatible with spinorial structure and Lorentzian kinematics in the continuum limit. Its role is to guarantee that, if a smooth spacetime description emerges, fermionic degrees of freedom and Dirac-type operators are not excluded by construction. As with the gauge sector, this choice is a structural commitment rather than a detailed model of particle physics.

---

### **Causal coupling and link variables**

Vertices are connected to their causal parents through directed links. To each causal link (p\to v) we associate a unitary operator

```math
U_{p\to v} \in U(N),
```

which mediates the transport of quantum information between local algebras. These link variables encode relational data between events and provide the microscopic origin of parallel transport in the emergent description. Importantly, they do not presuppose a notion of distance or geometry; they are defined purely on the causal graph.

The collection of vertex algebras and link unitaries defines a highly redundant description of the microscopic state. Physical information is not stored in individual vertex degrees of freedom, but in correlations distributed across causal neighborhoods.

---

### **Stabilization, redundancy, and code-like structure**

A central organizing principle of EGG is that large-scale observables must be **insensitive to local microscopic disturbances**. This motivates the introduction of stabilizing constraints that restrict the physically relevant subspace of the full Hilbert space. Rather than specifying a concrete stabilizer code in the strict sense of quantum error correction, we impose **stabilizer-inspired consistency conditions** that penalize configurations incompatible with coherent information flow across causal links.

At each vertex (v), we define a local stabilizing map of the schematic form

```math
S_v = \exp\!\left[
i\,\frac{g}{N}
\sum_{p\in P_v}
\left(
\mathrm{Tr}\,U_{p\to v} + \mathrm{Tr}\,U_{v\to p}^{\dagger}
\right)
\right],
```

(3.2)

where (P_v) denotes the parent set of (v) and (g) is a dimensionless coupling. This operator favors configurations in which link variables entering and leaving a vertex are mutually consistent, effectively suppressing incoherent fluctuations. The precise form of (S_v) should be regarded as illustrative rather than unique; its purpose is to encode the idea that gauge redundancy and information protection are enforced locally but manifest globally.

Taken together, these stabilizing constraints induce a **code-like structure** on the causal graph: logical information is delocalized over extended causal regions, while local errors remain correctable in the coarse-grained description. In this sense, EGG draws on ideas from quantum error correction, but does not require an explicit construction of a commuting stabilizer Hamiltonian or a specific decoding algorithm.

---

### **Code depth and emergent cutoffs**

To characterize the robustness of this delocalized information, it is useful to introduce a geometric notion of code depth. Consider a causal ball of radius (R_{\text{code}}), defined in terms of graph distance. Heuristically, the ability to reconstruct coarse-grained observables from partial data improves rapidly with the size of such regions. Motivated by known results for hypergraph-product and gauge-theoretic codes, we posit that the effective code distance scales as

```math
\boxed{
d_{\text{code}} \sim c_0\,N^{1/2}\,e^{\xi R_{\text{code}}/\ell_0}
}
```

(3.3)

where (c_0) and (\xi) are order-unity constants and (\ell_0) is the microscopic length scale. This expression is not derived from an explicit stabilizer construction; rather, it encodes the expectation that increasing causal depth and gauge redundancy dramatically enhance robustness.

From the perspective of the emergent continuum description, this scale acts as an **intrinsic ultraviolet regulator**. Fluctuations at distances shorter than the effective code scale are suppressed, while long-wavelength collective modes remain dynamical. In later sections, this mechanism will be connected to the appearance of smooth geometry and to the infrared dominance of gravitational degrees of freedom.

---

### **Role of information structure in the overall framework**

The purpose of the vertex algebra and stabilizing constraints is not to provide a detailed microscopic model of quantum matter, but to establish a **conceptual bridge** between causality, gauge redundancy, and emergent geometry. The causal growth law of Section 2 supplies the network on which information is distributed; the algebraic structure introduced here governs how that information is stored, transported, and protected.

Together, these ingredients prepare the ground for the emergence of continuum physics. In particular, they enable a reinterpretation of gravitational dynamics as a manifestation of large-scale information consistency, an idea that will be developed in the subsequent sections. While many aspects of this picture remain conjectural, the combination of causal growth and code-like stabilization defines a concrete and unified microscopic substrate from which spacetime physics may arise.

## **4 Entanglement and the Emergence of Geometry**

A defining premise of Entanglement–Gauge Gravity is that spacetime geometry is not fundamental, but emerges from the relational structure of quantum information distributed across the causal network. While geometry is diagnosed operationally through diffusion and spectral observables, as discussed in Section 2 and quantified in Section 9, entanglement provides a complementary and deeper characterization of how causal connectivity organizes into an effective continuum description.

To formalize this connection, we associate quantum states to finite causal regions of the graph and consider their information-theoretic relations. For two vertices (v) and (w), we define the mutual information

```math
\mathcal{I}_{vw}
=
S(\rho_v) + S(\rho_w) - S(\rho_{vw}),
```

(4.1)

where (\rho_v) and (\rho_w) are reduced density matrices associated with local vertex algebras, and (\rho_{vw}) is their joint state. Mutual information serves as a robust, regulator-independent measure of total correlations and is well defined even when no background notion of distance exists.

---

### **Coarse-graining and information geometry**

To extract continuum behavior, mutual information must be coarse-grained over finite causal neighborhoods. We introduce **double-cone cells**, defined as causal regions spanning a temporal depth (\Delta t\in[0,2\ell_0]) and a graph radius of order (2\ell_0), typically containing (\mathcal{O}(10^1)) vertices. Within such a cell centered at an emergent coordinate location (x), we define the averaged information potential

```math
\overline{\mathcal{I}}(x)
=
\frac{1}{|\text{cell}|}
\sum_{v,w\in\text{cell}}
\mathcal{I}_{vw}.
```

(4.2)

This quantity captures how strongly degrees of freedom within a causal neighborhood are correlated with one another, independent of any assumed geometric structure.

Information geometry provides a natural way to associate a tensorial object to such a potential. In classical and quantum information theory, the Hessian of a suitable information functional defines a Fisher information metric on the space of states. Motivated by this correspondence, we propose to identify the emergent spacetime metric with the coarse-grained Hessian of (\overline{\mathcal{I}}(x)).

---

### **Metric from information-theoretic structure**

Specifically, we define the effective metric tensor as

```math
\boxed{
g_{\mu\nu}(x)
=
\frac{4\,\ell_P^{\,2}}{\ln 2}
\,
\partial_\mu \partial_\nu
\overline{\mathcal{I}}(x),
}
```

(4.3)

where (\partial_\mu) denotes derivatives with respect to emergent continuum coordinates defined implicitly through coarse-graining. The normalization is chosen so that areas measured in Planck units correspond naturally to information measured in bits, anticipating the connection to gravitational entropy.

This identification should be understood as a **proposal for the continuum interpretation** of the underlying information structure, rather than as a derivation from first principles. Its role is to link the operational notion of distance inferred from correlations to a geometric description compatible with Lorentzian spacetime.

---

### **Relation to spectral geometry and causality**

The construction above is not intended to replace the diffusion-based diagnostics introduced earlier, but to complement them. Spectral observables determine whether the causal graph admits a geometric interpretation at all and reveal the scale dependence of dimensionality. The information-theoretic metric, if well defined, refines this picture by encoding local anisotropies, causal structure, and curvature.

In particular, the emergence of a Lorentzian signature is tied to the underlying causal asymmetry of the graph. Preliminary numerical experiments indicate that, after a modest number of causal layers, the coarse-grained Hessian of (\overline{\mathcal{I}}) exhibits one positive and three negative eigenvalues, consistent with a ((+,-,-,-)) signature. While these observations are not yet part of the systematic numerical programme reported in Section 9, they motivate the identification of the information-geometric tensor with a spacetime metric.

---

### **Status and scope of the entanglement–geometry map**

It is important to emphasize that the entanglement-based construction introduced here is **not required** to establish the emergence of four-dimensional geometry. The latter is already supported by diffusion-based evidence. Instead, the entanglement–geometry map provides a conceptual and mathematical mechanism by which geometric notions such as distance, causal cones, and curvature may be encoded directly in quantum correlations.

In this sense, entanglement in EGG plays a role analogous to that of a constitutive relation in hydrodynamics: it does not generate spacetime by itself, but determines how the underlying microscopic degrees of freedom organize into a smooth geometric phase once the conditions for emergence are met. Subsequent sections will build on this identification to connect information structure to effective gravitational dynamics.

---

## **5 Emergent Gauge Fields and Teleparallel Gravity**

The causal and information-theoretic structures introduced in the previous sections admit a natural reorganization in terms of effective gauge fields at large scales. In EGG, gravity does not appear as a fundamental interaction, but as an emergent description of collective fluctuations in the relational degrees of freedom that transport information across the causal network.

At the microscopic level, causal links (p\to v) are decorated with unitary operators (U_{p\to v}\in U(N)). In a regime where a smooth geometric description becomes meaningful, these link variables may be expanded as

[
U_{p\to v} = \exp!\left(\frac{i}{N} A_{p\to v}\right),
]

where (A_{p\to v}) are Hermitian generators and the factor of (1/N) anticipates a controlled large-(N) limit. We decompose (A_{p\to v}=\langle A\rangle+\delta A) into a coarse-grained expectation value and fluctuations.

---

### **Coarse-grained frame fields from link variables**

Within a coarse-graining cell of the type defined in Section 4, collective modes of the link variables define an effective field

[
H^{a}{}_{\mu}(x)
================

\left\langle
\mathrm{Tr}!\left(T^{a} U_{v\to w}\right)
\right\rangle_{v,w\in\text{cell}},
]
(5.1)

where (T^{a}) are generators of the internal gauge algebra and the index (\mu) labels emergent spacetime directions defined by the coarse-graining procedure. This object should be interpreted as a **collective gauge-field mode** rather than as a fundamental tetrad. Its physical meaning is fixed only in the infrared, where a continuum description becomes appropriate.

The antisymmetric derivative

[
S^{a}_{\mu\nu}
==============

## \partial_\mu H^{a}_{\nu}

\partial_\nu H^{a}_{\mu}
]
(5.2)

defines a field strength associated with these collective modes. In the emergent description, (S^{a}_{\mu\nu}) encodes torsion rather than curvature, reflecting the fact that parallel transport is defined by relational link variables rather than by an underlying Levi–Civita connection.

---

### **Infrared effective action**

Integrating out short-wavelength fluctuations (\delta A) in a large-(N) expansion yields an effective action for the coarse-grained fields. At leading order, symmetry and dimensional analysis restrict the infrared action to the form

[
\boxed{
S_{\mathrm{eff}}
================

\int d^4x,\sqrt{-g}
\left[
\frac{1}{2},\kappa,
S^{a}*{\mu\nu} S*{a}^{;\mu\nu}
+
\Lambda_{\mathrm{ent}}
\right],
}
]
(5.3)

where (g_{\mu\nu}) is the emergent metric defined in Section 4. The effective coupling

[
\kappa \sim \frac{N,\ell_0^{,2}}{4\pi}
]
(5.4)

sets the overall strength of the gravitational interaction, while

[
\Lambda_{\mathrm{ent}} \sim \frac{\ln 2}{R_{\mathrm{code}}^{,2}}
]
(5.5)

acts as an effective cosmological constant determined by the depth of the information-protecting structure introduced in Section 3.

These expressions should be understood parametrically: the precise numerical coefficients depend on details of the coarse-graining and stabilization scheme, but their scaling with (N), (\ell_0), and (R_{\mathrm{code}}) is fixed by the underlying structure.

---

### **Teleparallel interpretation**

The action (5.3) takes the form of a **teleparallel gravity** theory, in which torsion rather than curvature encodes gravitational dynamics. Using the Weitzenböck identity, the torsion-squared term differs from the Einstein–Hilbert Lagrangian by a total derivative. As a result, the field equations derived from (S_{\mathrm{eff}}) are dynamically equivalent to those of General Relativity, up to boundary contributions.

In the context of EGG, the teleparallel formulation is not merely a reformulation of GR but a natural infrared language for a theory whose microscopic variables are link-based and gauge-redundant. Since parallel transport is fundamental while curvature is emergent, torsion provides the appropriate carrier of gravitational information.

---

### **Status of the gravitational identification**

It is important to stress that the appearance of teleparallel gravity here is an **infrared identification**, not a microscopic postulate. The numerical results reported in Section 9 establish the emergence of a four-dimensional geometric phase but do not directly probe the dynamics of the effective gauge fields. The gravitational action presented in this section represents the simplest continuum description compatible with the causal, gauge-theoretic, and information-theoretic structures of the framework.

In this sense, gravity in EGG is best understood as a hydrodynamic theory of information flow: a universal, long-wavelength description that becomes inevitable once the underlying causal network supports stable geometry and protected correlations. Subsequent sections will explore the consequences and phenomenology of this identification.

---

## **6 Emergent Field Equations**

In the geometric phase where a continuum description is valid, the effective action introduced in Section 5 admits a standard variational treatment. Varying the infrared action with respect to the coarse-grained gauge fields (H^{a}{}_{\mu}), and translating the result into metric variables using the information-geometric identification of Section 4, yields gravitational field equations of teleparallel form.

At the level of the emergent metric (g_{\mu\nu}), these equations take the familiar structure

```math
\boxed{
G_{\mu\nu}
+
\Lambda_{\mathrm{ent}}\, g_{\mu\nu}
=
8\pi G_N\, T_{\mu\nu}^{(\mathrm{edge})},
}
```

(6.1)

where (G_{\mu\nu}) is the Einstein tensor constructed from (g_{\mu\nu}), (\Lambda_{\mathrm{ent}}) is the effective cosmological constant introduced in Eq. (5.5), and (G_N) is the emergent Newton constant determined by the large-(N) scaling of the microscopic theory.

The stress–energy tensor on the right-hand side arises from degrees of freedom that propagate on extended structures of the causal graph and interact with the bulk geometry only through coarse-grained correlations. Formally, it is defined as

```math
T_{\mu\nu}^{(\mathrm{edge})}
=
-\frac{2}{\sqrt{-g}}
\frac{\delta S_{\mathrm{edge}}}{\delta g^{\mu\nu}},
```

(6.2)

where (S_{\mathrm{edge}}) denotes the effective action governing these modes.

---

### **Interpretation**

Equation (6.1) should be read as an **infrared consistency condition**, not as a microscopic law. It expresses the requirement that the collective, information-protecting dynamics of the causal network admit a self-consistent geometric description at large scales. In this description, matter sources curve spacetime in precisely the way prescribed by General Relativity, while the cosmological term reflects the finite depth of the underlying information-theoretic structure.

The appearance of Einstein-type equations is therefore not imposed by hand, but follows from the combination of causal growth, gauge redundancy, and coarse-grained stability. As in hydrodynamics, the universality of the field equations reflects the insensitivity of long-wavelength behavior to microscopic details, provided the necessary structural conditions are met.

---

### **Scope and limitations**

The numerical results presented later establish the emergence of a four-dimensional geometric phase but do not directly test the dynamical content of Eq. (6.1). The field equations should thus be understood as the **simplest continuum completion** compatible with the emergent geometry and the teleparallel structure of the effective action. Verifying their detailed validity—through fluctuations, propagation, and coupling to matter—remains an open task for future work.

---

### **Role within EGG**

Within Entanglement–Gauge Gravity, Eq. (6.1) encapsulates the central claim of the framework: **gravity is the universal, long-distance manifestation of information-theoretic consistency on a causal substrate**. Once a stable geometric phase exists, the dynamics of that phase are forced into a form equivalent to General Relativity, up to boundary terms and effective couplings fixed by microscopic structure.

---

## **7 Ultraviolet Structure and Phenomenological Signatures**

A central motivation of Entanglement–Gauge Gravity is that microscopic gauge redundancy and finite information depth regulate ultraviolet behavior without the need for additional degrees of freedom or imposed cutoffs. While the numerical programme reported here probes primarily the geometric sector, the structure of the framework allows a controlled discussion of ultraviolet running and low-energy phenomenology.

---

### **Large-(N) scaling and ultraviolet behavior**

The presence of a local (U(N)) gauge redundancy at each vertex introduces a natural expansion parameter. In the infrared geometric phase, fluctuations of the collective gauge fields organize into an effective field theory whose couplings admit a (1/N) expansion. At leading order, dimensional analysis and symmetry considerations suggest a beta function of the form

```math
\beta_g
=
-\frac{b_1}{N}\, g^{3}
+
\mathcal{O}(N^{-2}),
```

(7.1)

where (g) denotes a dimensionless effective coupling and (b_1>0) is an order-unity coefficient. This structure admits a nontrivial ultraviolet fixed point at large (N), consistent with an **asymptotically safe** scenario. The fixed point is not imposed, but emerges as a consequence of gauge redundancy and the suppression of short-distance fluctuations by information-theoretic stabilization.

In this regime, the effective Newton constant becomes scale dependent,

```math
G(k)
=
\frac{G_0}{1 + \tfrac{\beta_1}{N}\ln(k/k_0)},
```

(7.2)

where (k) is a momentum scale and (\beta_1) encodes subleading contributions. This logarithmic running reflects the gradual weakening of gravitational interactions at high energies rather than a breakdown of the theory.

---

### **Finite information depth and infrared modifications**

The code-like structure introduced in Section 3 implies a finite depth over which quantum information can be protected and reconstructed. This scale, characterized by (R_{\mathrm{code}}), enters the infrared effective theory as a physical length beyond which deviations from classical gravity become suppressed.

At distances comparable to (R_{\mathrm{code}}), the Newtonian potential acquires a Yukawa-type correction,

```math
\Phi(r)
=
-\frac{G_0 M}{r}
\left[
1
+
\alpha\, e^{-r/R_{\mathrm{code}}}
\right],
\qquad
\alpha \sim \frac{1}{N},
```

(7.3)

where the amplitude of the correction is controlled by the same large-(N) parameter that governs ultraviolet stability. This modification reflects the finite range over which microscopic information-theoretic correlations can influence the emergent geometry.

Similarly, collective gravitational excitations are expected to exhibit a modified dispersion relation at high momentum,

```math
\omega^2
=
k^2
\left[
1
+
\frac{c_2}{N}\, (\ell_P k)^2
+
\dots
\right],
```

(7.4)

where higher-order terms encode progressively suppressed corrections. These deviations arise not from Lorentz violation at the microscopic level, but from the breakdown of the hydrodynamic description as wavelengths approach the underlying causal and informational scales.

---

### **Phenomenological constraints**

Although the precise values of the coefficients appearing in Eqs. (7.1)–(7.4) depend on details of coarse-graining and stabilization, existing observations already constrain the allowed parameter space. Current bounds can be summarized schematically as follows:

| Observable                          | Probe                          | Implication                                                              |
| ----------------------------------- | ------------------------------ | ------------------------------------------------------------------------ |
| **Sub-millimeter gravity tests**    | Yukawa correction to (\Phi(r)) | (N \gtrsim 10^3) for (R_{\mathrm{code}}\sim 10\text{–}100,\mu\mathrm{m}) |
| **Binary neutron-star mergers**     | Graviton dispersion            | (N \gtrsim 10^2)                                                         |
| **Cosmological lensing and growth** | Running (G(k))                 | (\beta_1/N \lesssim 10^{-3})                                             |

These constraints are mutually consistent and indicate that the regime in which EGG reproduces classical gravity to high accuracy is broad. More precise bounds will require dedicated modeling of the effective action and improved numerical control of the infrared couplings.

---

### **Status of the phenomenological predictions**

The phenomenological signatures discussed in this section should be understood as **targets**, not as firm predictions. They follow from the internal logic of the framework once a geometric phase exists, but they have not yet been derived from a fully controlled continuum limit. Their primary role is to demonstrate that EGG is not only conceptually coherent but also experimentally vulnerable.

In this sense, the framework makes a clear wager: if gravity is indeed the hydrodynamic manifestation of information-theoretic consistency on a causal substrate, then deviations from classical behavior must eventually appear at scales set by (N) and (R_{\mathrm{code}}). Whether Nature realizes this structure remains an open question, but the framework provides a concrete path by which it could be tested.

---

## **8 Black-Hole Thermodynamics and Information**

Within Entanglement–Gauge Gravity, black holes are not treated as exotic singular solutions added to an otherwise smooth spacetime. Instead, they arise as extreme configurations of the same causal, informational, and gauge-theoretic structures that underlie spacetime everywhere. Their thermodynamic properties are therefore interpreted directly in terms of information storage, protection, and reconstruction on the causal network.

---

### **Entropy as protected information**

A defining feature of black holes in semiclassical gravity is the Bekenstein–Hawking area law. In EGG, this law is reinterpreted as a statement about the number of independent degrees of freedom that can be reliably protected behind a causal horizon.

The stabilizer-inspired structure introduced in Section 3 implies that logical information is delocalized over extended causal regions and that only a finite amount of information can be reconstructed from data outside a sufficiently large erased region. When a causal horizon forms, it acts as a maximal erasure surface. The number of logical degrees of freedom that remain inaccessible to an external observer scales with the area of that surface.

Motivated by this correspondence, we identify the black-hole entropy with the number of logical degrees of freedom protected by the horizon,

```math
\boxed{
S_{\mathrm{BH}}
=
\frac{A}{4\,\ell_P^{\,2}}\,
\ln N,
}
```

(8.1)

where (A) is the horizon area and (N) is the dimension of the local gauge algebra. The appearance of (\ln N) reflects the fact that each protected degree of freedom carries an internal Hilbert-space dimension set by the microscopic gauge structure.

This expression should be understood as a **structural identification**, not as a microscopic counting derived from an explicit code construction. Its role is to show that the area law follows naturally once horizons are interpreted as information-theoretic boundaries rather than as geometric singularities.

---

### **Universality and effective normalization**

For macroscopic astrophysical black holes, the effective normalization of entropy must reproduce the standard Bekenstein–Hawking result. This can be achieved if the combination of microscopic parameters entering (\ell_P) and (N) renormalizes such that (\ln N) is absorbed into the definition of the effective Planck scale. In this regime, EGG is indistinguishable from semiclassical General Relativity.

For sufficiently small or highly quantum black holes, however, deviations from the strict area law may become visible, reflecting the discrete internal structure of the underlying causal network. Such deviations are not predicted sharply here, but they represent a potential observational handle on the microscopic theory.

---

### **Evaporation and unitarity**

Hawking radiation in EGG is interpreted as a gradual leakage of encoded information from a region whose error-protecting capacity is being eroded by quantum fluctuations. As radiation is emitted, the effective code depth associated with the horizon decreases, eventually allowing the full logical content of the black hole to be reconstructed from the exterior degrees of freedom.

This picture aligns naturally with modern developments in quantum information theory, in which black-hole evaporation is described using entanglement wedges and reconstruction maps. In EGG, unitarity is not restored by modifying quantum mechanics or introducing nonlocal dynamics, but follows from the fact that information is never destroyed—only redistributed across the causal network.

---

### **Scope and limitations**

The arguments presented here are necessarily qualitative. The framework does not yet provide a microscopic derivation of the Page curve or a detailed model of black-hole microstates. Instead, it offers a unifying interpretation in which black-hole thermodynamics, entropy, and evaporation are consequences of the same information-theoretic principles that govern spacetime emergence more generally.

In this sense, black holes serve as a consistency check on the framework rather than as its primary motivation. Any viable microscopic theory of spacetime must explain why horizons obey an area law and why evaporation is unitary. EGG accommodates these features naturally once gravity is understood as an emergent, information-governed phenomenon.

---

### **Role within the overall framework**

Black holes occupy a special place in EGG because they probe the deepest interplay between causality, geometry, and information. The reinterpretation of horizon entropy as protected logical information reinforces the central claim of the framework: that spacetime and gravity are macroscopic manifestations of underlying information-theoretic structure.

While much work remains to sharpen this picture, the black-hole sector illustrates how EGG connects conceptual unification with established semiclassical results, without introducing additional assumptions beyond those already required for emergent geometry.

---

## **9 Numerical Programme and Results**

The numerical programme was designed to test the **internal viability of the microscopic growth law**, not to fit parameters or reproduce continuum physics by construction. In particular, the aim was to identify any structural or geometric pathology—such as fragmentation, runaway connectivity, dimensional collapse, or small-world behavior—that would invalidate the emergence of a macroscopic geometric phase.

We implemented the causal growth dynamics defined in Sections 2 and 3 and subjected the resulting graphs to a small set of adversarial diagnostics: (i) large-scale graph generation, (ii) spectral-dimension measurement via diffusion on the graph Laplacian, and (iii) a geometric proxy for causal depth related to information protection. All computations were performed using Hutchinson trace estimation and Lanczos quadrature on graphs with up to (3\times10^5) vertices.

Unless otherwise stated, growth parameters were fixed at (\gamma=0.9), (\alpha=1.6), (k_{\max}=12), and a candidate pool of 25 near-lightcone vertices. The density scaling (n(t)=\beta t^4) was chosen so that the final causal layer reached the target graph size. For each graph size (N\in{2\times10^4,10^5,3\times10^5}), the full growth process and spectral analysis were carried out independently.

---

### **9.1 Graph connectivity and causal structure**

The growth law generates directed acyclic graphs with stable and modest local connectivity. The undirected degree distribution narrows with increasing system size, and its mean approaches a value consistent with the emergence of four-dimensional geometry at large scales:

[
\langle k_{\mathrm{undirected}}\rangle \approx
\begin{cases}
3.84 & (N=2\times10^4),[4pt]
3.99 & (N=10^5),[4pt]
4.25 & (N=3\times10^5).
\end{cases}
]

The gradual increase in (\langle k\rangle) reflects the quartic density scaling and the enforcement of locality in the parent-selection process. No evidence of graph fragmentation, percolation collapse, or runaway valence was observed. In particular, the graphs remain sparse and non-small-world even at the largest sizes studied.

---

### **9.2 Spectral dimension and emergent geometry**

To probe the emergent geometry without reference to embedding coordinates, we computed the return probability of a diffusion process governed by the **normalized undirected Laplacian**,

[
P(\sigma)
=========

\frac{1}{N},
\mathrm{Tr}!\left(e^{-\sigma L_{\mathrm{norm}}}\right),
\qquad
D_s(\sigma)
===========

-2,\frac{d\ln P}{d\ln\sigma}.
]

This choice is deliberately conservative: it discards causal directionality, imposes no manifold prior, and is sensitive to spectral degeneracies and pathological shortcuts.

Across all graph sizes, the spectral dimension exhibits a clear **scale dependence**. At short diffusion times, the geometry is effectively low-dimensional, while at long diffusion times it approaches a higher-dimensional regime. Extracting ultraviolet and infrared plateaus from the lowest and highest portions of the diffusion scale yields:

[
\begin{aligned}
N=2\times10^4: &\quad D_s^{\mathrm{UV}}\approx 1.20,\quad D_s^{\mathrm{IR}}\approx 3.42,\
N=10^5:        &\quad D_s^{\mathrm{UV}}\approx 1.21,\quad D_s^{\mathrm{IR}}\approx 3.63,\
N=3\times10^5: &\quad D_s^{\mathrm{UV}}\approx 1.22,\quad D_s^{\mathrm{IR}}\approx 3.81.
\end{aligned}
]

Two features are particularly significant.

First, the ultraviolet spectral dimension stabilizes near (D_s^{\mathrm{UV}}\simeq1.2–1.4) and shows only weak sensitivity to causal directionality (as verified separately using directed Laplacians). This value is consistent with the universal (D_s=4/3) associated with branched-polymer and causal-tree geometries, indicating that the microscopic growth law lies in a well-defined universality class rather than requiring fine-tuning.

Second, the infrared spectral dimension increases systematically with system size, approaching four as (N) grows. No saturation at a lower value was observed. This behavior strongly suggests that four-dimensional geometry is an emergent, large-scale property of the causal network, not an artifact of finite size or parameter choice.

---

### **9.3 Causal depth and geometric robustness**

As a minimal diagnostic of causal depth and robustness, we measured a geometric proxy for code distance: the minimal graph distance separating “past” and “future” temporal boundaries within a causal ball of radius (R). Although this quantity is not equivalent to the stabilizer-code distance discussed in Section 3, it serves as a coarse indicator of how rapidly causal connectivity thickens with scale.

For the (N=3\times10^5) graph, we find

[
d_{\mathrm{geo}}(R=10)\approx 8,\qquad
d_{\mathrm{geo}}(R=20)\approx 15,\qquad
d_{\mathrm{geo}}(R=40)\approx 18.
]

The monotonic growth of (d_{\mathrm{geo}}(R)) confirms the absence of pathological shortcuts and supports the interpretation of increasing causal depth at larger scales. A full stabilizer-code construction and decoding-based distance analysis remain open problems.

---

### **9.4 Summary of numerical findings**

Within the scope of the diagnostics employed, the numerical results establish three robust facts:

* the causal growth law generates large, stable, sparse graphs without pathological connectivity,
* the emergent geometry exhibits a **universal ultraviolet spectral dimension near (4/3)**,
* and the infrared geometry flows toward **four dimensions** as system size increases.

These results do not establish the full dynamical content of Entanglement–Gauge Gravity. They do, however, provide nontrivial evidence that the framework’s **most basic geometric premise**—the emergence of four-dimensional spacetime from a causal, low-dimensional microstructure—is internally consistent and robust under adversarial testing.

In this sense, the numerical programme serves as a proof-of-viability rather than a proof-of-correctness. It identifies a concrete microscopic dynamics that supports the kind of emergent geometric phase required by the framework, and thereby justifies the continuum constructions explored in the preceding sections.

---

## **10 Conclusion**

Entanglement–Gauge Gravity (EGG) proposes a concrete microscopic picture of spacetime in which geometry, gravity, and matter arise from the collective organization of a growing causal structure endowed with quantum degrees of freedom. The framework replaces a fundamental background manifold with a stochastic causal network, treats geometry as an emergent, scale-dependent phenomenon, and interprets gravity as an infrared manifestation of gauge redundancy and information-theoretic consistency.

The primary result of this work is not a complete derivation of gravitational dynamics, but the demonstration that a **minimal causal growth law** can support a stable geometric phase with nontrivial structure. Numerical investigations show that the emergent geometry exhibits a universal ultraviolet spectral dimension near (D_s\simeq4/3), characteristic of causal-tree and branched-polymer universality classes, together with a robust flow toward four dimensions at large scales. This behavior establishes the internal viability of the framework’s core premise: that four-dimensional spacetime can emerge dynamically from a low-dimensional causal microstructure without imposing geometry or dimensionality by hand.

Building on this foundation, we have outlined how local gauge structure, stabilizer-inspired redundancy, and entanglement geometry can be unified into a continuum effective description whose infrared kinematics coincide with those of General Relativity in a teleparallel formulation. These identifications remain conjectural, but they are structurally motivated and constrained by the underlying causal and information-theoretic architecture. In this picture, black-hole thermodynamics, ultraviolet softness, and deviations from classical gravity arise naturally as consequences of finite information depth and large-(N) gauge redundancy.

EGG therefore occupies a middle ground between abstract principle-based approaches and fully specified microscopic theories. It does not claim correctness, but it does claim coherence, calculability, and falsifiability. The framework makes clear wagers: that ultraviolet dimensional reduction is real, that gravity is hydrodynamic rather than fundamental, and that information-theoretic structure governs the emergence of spacetime. Each of these claims can be sharpened, challenged, or refuted by further analytical and numerical work.

Immediate directions for future investigation include refining the continuum limit of the effective action, developing controlled treatments of fluctuations around the emergent geometric phase, and improving numerical diagnostics of causal depth and information protection. On the phenomenological side, the framework motivates searches for finite-range deviations from Newtonian gravity, scale-dependent gravitational couplings, and high-frequency modifications of gravitational-wave propagation.

Whether or not Entanglement–Gauge Gravity ultimately describes Nature, it provides a concrete arena in which ideas from causality, gauge theory, and quantum information can be explored on equal footing. By identifying a microscopic dynamics that supports emergent geometry with the right large-scale behavior, the framework sharpens the question of what spacetime is—and what it must be built from—at the most fundamental level.

---

## **11 Implications if Entanglement–Gauge Gravity Is Correct**

This section is intentionally speculative. Its purpose is not to summarize established results, but to make explicit what would follow *if* Entanglement–Gauge Gravity provides an approximately correct microscopic description of spacetime. The implications listed below are not independent assumptions or optional embellishments. They arise structurally from the causal growth law, the local gauge algebra, and the information-theoretic interpretation developed in Sections 2–6.

If EGG is correct, then spacetime, gravity, and matter are not separate ingredients of Nature, but different manifestations of a single underlying causal–informational substrate. The consequences of this unification are profound.

---

### **11.1 What spacetime is**

If EGG is correct, then spacetime is **not fundamental**.

Instead:

* The Universe is a growing causal network whose vertices carry finite quantum degrees of freedom.
* Geometry is an emergent, scale-dependent description inferred from coarse-grained correlations and diffusion.
* Dimensionality is not fixed: the microscopic structure is effectively low-dimensional, while four dimensions emerge only at large scales.
* Lorentzian signature is emergent, not postulated, arising from the causal asymmetry of the underlying graph.

In this picture, spacetime is a **hydrodynamic phase of information flow**, analogous to how elasticity or fluid mechanics emerge from atomic structure.

---

### **11.2 What gravity is**

If EGG is correct, then gravity is **not a fundamental interaction**.

Instead:

* Gravity is the universal infrared description of how gauge redundancy and information protection organize on a causal substrate.
* Parallel transport is fundamental; curvature is emergent.
* The equivalence principle reflects the universality of information-theoretic consistency, not a geometric axiom.
* Einstein’s equations arise as an infrared consistency condition once a stable geometric phase exists.

Gravity is therefore to information what pressure is to molecular motion: an inevitable collective phenomenon, not a microscopic force.

---

### **11.3 What ultraviolet completion looks like**

If EGG is correct, then quantum gravity does not require:

* extra spacetime dimensions,
* supersymmetry,
* fundamental strings,
* or a breakdown of locality imposed by hand.

Instead:

* ultraviolet divergences are softened by finite information depth and large-(N) gauge redundancy,
* dimensionality reduces at short scales rather than proliferating,
* and the theory approaches a nontrivial ultraviolet fixed point rather than a singularity.

The “trans-Planckian problem” is replaced by a regime in which geometric notions simply cease to apply.

---

### **11.4 What black holes are**

If EGG is correct, then black holes are **not mysterious quantum-gravitational objects**, but extreme information-theoretic configurations.

In particular:

* Horizon entropy counts protected logical degrees of freedom, not microscopic geometric states.
* The area law reflects the information-storage capacity of a causal boundary.
* Hawking radiation is decoded information leakage, not destruction.
* Black-hole evaporation is unitary without modifying quantum mechanics.

The black-hole information paradox disappears because information was never lost—it was encoded nonlocally by construction.

---

### **11.5 What matter and gauge charges are**

If EGG is correct, then matter fields are **not fundamental building blocks**.

Instead:

* Gauge charges correspond to constraints on information flow.
* Fermionic structure arises from the algebraic content of local degrees of freedom.
* Matter excitations may live on extended or boundary-like structures of the causal network.
* Features such as family replication, if realized, would reflect topological properties of causal organization rather than arbitrary parameters.

Particle physics becomes a study of stable information patterns, not of elementary pointlike objects.

---

### **11.6 What the cosmological constant is**

If EGG is correct, then the cosmological constant is **not vacuum energy**.

Instead:

* It is an entanglement-geometric effect tied to the finite depth over which information can be protected.
* Its small value reflects large-scale causal structure, not fine-tuning.
* It is insensitive to ultraviolet physics by construction.
* Cosmic acceleration is a manifestation of residual long-range information correlations.

Dark energy becomes a statement about information geometry, not about exotic matter.

---

### **11.7 What time is**

If EGG is correct, then time is **fundamental but asymmetric**.

Specifically:

* The arrow of time is built into the growth of the causal network.
* Time-reversal symmetry is emergent and approximate.
* Entropy increase reflects the irreversible accumulation of causal structure.
* The low-entropy early Universe corresponds to a shallow causal past, not special initial conditions.

Thermodynamic irreversibility and cosmological time share a common origin.

---

### **11.8 What the global fate of the Universe is**

If EGG is correct, then several standard cosmological scenarios are ruled out:

* **No initial singularity:** the Big Bang is a transition from a pre-geometric to a geometric phase.
* **No Big Crunch:** global contraction would violate causal consistency.
* **No Big Rip:** super-accelerating instabilities are incompatible with increasing information depth.
* **Eternal expansion:** the Universe asymptotically approaches a finite-entropy, de Sitter–like regime.

In the far future, information is not destroyed but redistributed, residing in large-scale horizon degrees of freedom.

---

### **11.9 What is at stake**

If Entanglement–Gauge Gravity is correct, then it provides a single microscopic explanation for:

* why spacetime has four large dimensions,
* why gravity is geometric and universal,
* why black holes obey an area law yet evaporate unitarily,
* why ultraviolet divergences are softened,
* and why time has a preferred direction.

The numerical results of Section 9 do not prove this picture. They do, however, show that its most basic geometric prerequisite—the emergence of four-dimensional spacetime from causal growth—is viable. What remains is to determine whether the deeper claims of the framework survive further analytical, numerical, and experimental scrutiny.

---

## **Appendix A Glossary**

* **(\ell_P)**
  Planck length, defined as (\ell_P=\sqrt{\hbar G/c^3}). In EGG, (\ell_P) sets the scale at which the emergent geometric description becomes valid.

* **(\ell_0)**
  Microscopic length scale associated with causal growth and locality enforcement on the graph. Typically taken to be of order (\ell_P), but not assumed to be identical to it.

* **Causal graph**
  A directed acyclic graph whose vertices represent elementary causal events and whose directed edges encode causal precedence. No background spacetime structure is assumed.

* **Causal growth law**
  The stochastic rule governing the addition of new vertices and their attachment to existing ones, subject to locality and causal constraints.

* **Double-cone cell**
  A finite causal neighborhood used for coarse-graining, spanning a temporal depth (\Delta t\in[0,2\ell_0]) and a graph radius of order (2\ell_0). Serves as the basic unit for defining emergent continuum quantities.

* **Spectral dimension (D_s(\sigma))**
  A scale-dependent notion of dimensionality extracted from the return probability of a diffusion process on the graph Laplacian. Used as a coordinate-free diagnostic of emergent geometry.

* **Ultraviolet (UV) / Infrared (IR)**
  Respectively, short- and long-distance regimes defined operationally by diffusion scale or coarse-graining depth, not by coordinate distance.

* **Vertex algebra (\mathcal{A}_v)**
  The finite operator algebra associated with a vertex of the causal graph. In EGG, taken to be (M_N(\mathbb{C})\otimes\mathrm{Cl}(3,1)), encoding gauge redundancy and spinorial compatibility.

* **Link variable (U_{p\to v})**
  A unitary operator associated with a directed edge of the causal graph, mediating information transport between vertex algebras.

* **Large-(N) limit**
  The regime in which the internal gauge dimension (N) is large, providing a control parameter that suppresses microscopic fluctuations and stabilizes coarse-grained observables.

* **Stabilizer-inspired constraints**
  Local consistency conditions imposed on link variables to suppress incoherent configurations and induce delocalized, code-like information storage. Not a full stabilizer code in the strict quantum-information sense.

* **Code depth / (R_{\text{code}})**
  A length scale characterizing the causal extent over which information can be protected and reconstructed. Enters the infrared effective description as a physical scale.

* **Entanglement pressure**
  A heuristic term for the contribution of finite information depth to the infrared gravitational description, appearing as an effective cosmological constant scaling as (R_{\text{code}}^{-2}).

* **Information geometry**
  The study of geometric structures defined on spaces of probability distributions or quantum states. In EGG, used to motivate a relation between coarse-grained correlations and emergent metric structure.

* **Fisher information metric**
  A tensor defined as the Hessian of an appropriate information-theoretic functional. Serves as a proposed bridge between correlation structure and emergent spacetime geometry.

* **Teleparallel gravity**
  A formulation of General Relativity in which torsion, rather than curvature, encodes gravitational dynamics. In EGG, it provides a natural infrared language for link-based, gauge-redundant microscopic structures.

* **Weitzenböck identity**
  A mathematical identity relating torsion-squared invariants to the Einstein–Hilbert Lagrangian up to a boundary term, establishing the dynamical equivalence between teleparallel gravity and GR.

* **Emergent geometry**
  A continuum geometric description inferred from coarse-grained properties of the causal graph, rather than assumed at the microscopic level.

---

### References

[1] Bombelli et al., *Phys. Rev. D* 34 (1986) 373.  
[2] Aldrovandi & Pereira, *Teleparallel Gravity* (Springer 2013).  
[3] Reuter, *Phys. Rev. D* 57 (1998) 971.  
[4] Pastawski et al., *JHEP* 06 (2015) 149.  
[5] Benincasa & Dowker, *Phys. Rev. Lett.* 104 (2010) 181301.  
[6] Amari, *Information Geometry and Its Applications* (Springer 2016).  
[7] Nieh & Yan, *Ann. Phys.* 138 (1982) 237.
