# Factorization Selection: A Description-Length Principle for Emergent Locality in a Non-Geometric Fermionic Hamiltonian

Eric Hartford
**September 2026**

---

## Abstract

We propose a principle for how a tensor factorization of a Hilbert space into local sites can be selected by a Hamiltonian and a state jointly, without assuming a lattice, a metric, or a clock. The microscopic data are a sparse polynomial $H$ in $M$ Majorana operators whose interaction hypergraph is an expander — so that no geometry is planted — and a physical state, taken in this paper to be a ground-space state of $H$. A factorization $F$ is a bounded change of variables (a rotation of the modes from a declared finite gate alphabet, a shallow even circuit, and a partition into sites). The physical factorization minimizes the total description length

$$
\mathcal{C}(F;H,\Psi)=L(F)+L(H\mid F)+L(\Psi\mid F),
$$

the bits needed to specify the change of variables, the Hamiltonian's terms in the resulting site algebra, and a tensor network for the state on the same sites, all at one declared precision. Charging for $F$ is essential: without it a sufficiently fine-tuned rotation can make any $H$ and $\Psi$ look simple, and the principle would reward encoding the answer in the basis. With it, a geometric factorization wins only if the compression it buys exceeds the cost of the transformation that reveals it.

The principle is static, so it does not consume the clock it might later produce; it is not vacuous, because with unrestricted transformations every state is a product state in some basis and with the state term removed the selection is fixed by the spectrum alone. The paper's conjecture has two stages. At the sizes now accessible ($M\le24$ modes, at most twelve sites), it is that for expander couplings and ground-space states a factorization exists that is substantially cheaper than the best zero-transformation baseline $\mathcal{C}_0$ (the best mere pairing of the original modes into sites), whose support hypergraph is reproducibly less expander-like than that baseline's quotient support $\mathcal{S}_{F_\varnothing}^{(\eta)}$, and which changes reproducibly when the state changes at fixed $H$. The claim that the selected support has a finite spatial dimension is reserved for a later scaling study; twelve sites cannot carry a Hausdorff exponent. A pre-test is also needed on the state's vote itself, since tensor networks on sparse expanders can represent volume-law states with polynomial resources and the ground state may already be cheap in the ultraviolet presentation. We give a nested search over transformation classes designed so that the conjecture can be falsified within a declared class rather than merely not found, and two pre-tests framed as empirical questions. No numerics are reported, no gravitational, cosmological, or particle-physics claims are made, and Section 7 lists what earlier versions claimed and this one does not. Predecessors, in particular the loss-functional co-emergence of locality of Shokrian Zini, Brown, and Freedman, are compared in Section 8.

---

## 1 Introduction

### 1.1 The missing principle

Accounts of emergent spacetime from quantum information assume a tensor factorization of the Hilbert space into subsystems. Random tensor networks assume a graph; holographic codes assume bulk and boundary factors; entanglement-based metric reconstructions [1] begin from a factorization; Jacobson's derivation of the Einstein equation as an equation of state [2,3] begins from causal diamonds with algebras attached. The factorization carries the locality, the locality carries the geometry, and the factorization is taken as given.

Cotler, Penington, and Ranard showed that, for a generic Hamiltonian spectrum, a factorization in which $H$ is few-body is essentially unique when it exists [4]. That is the uniqueness half of what is needed. It leaves existence open, and it leaves the state no role: a spectrum-selected factorization cannot change unless $H$ changes, whereas one expects the same theory to have geometric and non-geometric states. Carroll and Singh's quantum mereology [5] gives the state a role through predictability of dynamics, which presupposes a time, hence a clock, hence a factor — the circularity a state-dependent principle has to avoid. Shokrian Zini, Brown, and Freedman [6] postulate a loss functional of both a Hamiltonian and a state and minimize it to find a tensor-product structure respected by both, which they describe as a co-emergence of locality; that is the closest predecessor to what follows, and Section 8 states exactly where the present proposal differs.

### 1.2 The proposal

The physical factorization $F^*$ minimizes a three-part description length,

$$
F^*=\arg\min_{F\in\mathcal{F}}\ \mathcal{C}(F;H,\Psi),\qquad
\mathcal{C}=L(F)+L(H\mid F)+L(\Psi\mid F),
\tag{1.1}
$$

over a declared class $\mathcal{F}$ of bounded transformations. $L(H\mid F)$ restricts the candidates: a factorization in which $H$ is many-body makes its term list long. $L(\Psi\mid F)$ selects among candidates: the tensor network a state needs depends on which sites have been chosen. $L(F)$ makes the principle an honest two-part code: the transformation that reveals the simplicity is itself transmitted, at the same precision as everything else. No time appears in (1.1). Time, if the framework ever produces one, is constructed after $F^*$ exists.

Two further choices are structural. The degrees of freedom are fermionic, because a fermionic Hilbert space carries no canonical tensor product — writing Majoranas as qubits requires an ordering — and a principle whose content is that factorization is selected is at home where none is given. And the interaction hypergraph of $H$ is an expander, because an expander has exponential ball growth and no finite-dimensional geometry, so that any geometric factorization found is provably a different object from the coupling list.

### 1.3 What this paper is and is not

It is a definition of a class of ultraviolet Hamiltonians, a definition of a class of factorizations, a selection principle, one conjecture, and an experiment designed so that the conjecture can fail in a declared sense. Its one interesting prediction is that a non-geometric $H$ and a ground-space $\Psi$ can jointly pay for a nontrivial change of factorization whose support graph is reproducibly more local than the coupling hypergraph, and, more sharply, that $F^*(H,\Psi_1)\neq F^*(H,\Psi_2)$ at fixed $H$. A finite spatial dimension is a scaling claim reserved for larger systems (Section 4.6). It does not derive gravity, Lorentz invariance, the dimension of space, the cosmological constant, or matter content, and it makes no claim about neutrinos, black-hole spectra, or intermediate scales. Earlier versions did; Section 7 records the withdrawals. Appendix E records the broader picture that motivated the proposal, labelled as bets that do not follow from anything in Sections 2–6.

---

## 2 The Ultraviolet Object

*Definitions.*

### 2.1 Modes, Hamiltonian, sparsity parameters

Let $\chi_1,\dots,\chi_M$ be Majorana operators, $M$ even, $\{\chi_a,\chi_b\}=2\delta_{ab}$, acting on a Fock space of dimension $2^{M/2}$. The Hamiltonian is

$$
H\;=\;i^{q/2}\sum_{S\in E}J_S\,\chi_S,\qquad \chi_S=\prod_{a\in S}\chi_a,\qquad |S|=q,
\tag{2.1}
$$

where $E$ is the hyperedge set of a $q$-uniform hypergraph on the $M$ modes and the $J_S$ are independent Gaussian couplings. Two sparsity parameters are used, following the distinction that the sparse-SYK literature makes:

$$
\kappa=\frac{|E|}{M}\quad(\text{terms per mode}),\qquad r=\text{per-mode hypergraph degree},\qquad r=q\kappa\ \text{for a regular hypergraph}.
\tag{2.2}
$$

Dense SYK [7,8,9] has $\kappa\sim M^{q-1}$. The sparse model of Xu, Susskind, Su, and Swingle [10] has $\kappa=O(1)$ and retains the global features of SYK — including a maximally chaotic low-temperature sector — over a wide range of $\kappa$ down to order one. We rely on that paper only for the definition and for the statement that sparsity does not by itself remove SYK physics; we do not assume any regime in which it does (Section 5.1). Couplings are specified at precision $p$ bits; $M$, $q$, $\kappa$, the hypergraph, and $p$ are the parameters. There are no spatial labels.

### 2.2 The expander property

A random $r$-regular $q$-uniform hypergraph is, with high probability, an expander: balls in its natural metric grow exponentially and every cut through a ball is proportional to the ball's volume. No factorization in the declared class has $E$ itself as its support hypergraph — a site contains $2m\ge2$ Majoranas, so the support of any zero-transformation factorization is the quotient of $E$ under a pairing of modes into sites, and the ultraviolet data contain no such pairing. What the expander property guarantees is weaker and must be checked rather than assumed: that the quotient support remains expander-like under the *best* zero-transformation pairing (Section 4.1). If it does, any more local minimizer of (1.1) is a different object from the coupling list and nothing was planted.

### 2.3 Reference complex structure

A set of Majorana operators has no distinguished Fock vacuum. Defining one requires a complex structure — a pairing of the modes into complex fermions, $c_j=\tfrac12(\chi_{2j-1}+i\chi_{2j})$ for the pairing $J_0$ — and the vacuum $|\Omega_{J_0}\rangle$ depends on that choice. Where a reference state is needed, the ultraviolet data are therefore $(H,J_0)$, and $J_0$ is a declared convention whose influence on any result must be tested by varying it. This paper avoids the dependence in its primary claim by using ground states, which require no reference; prepared states, which do, appear only as controls (Section 2.4).

### 2.4 Physical states and controls

A state is **physical**, for the purposes of the conjecture of Section 4.6, if it lies in the ground space of $H$; when the spectrum is gapped, the first excited state is included. For the numerics of Section 5 only Hamiltonian realizations with $E_0<E_1<E_2$ are used, so that "the ground state" and "the first excited state" are unique vectors; a degenerate level would leave an arbitrary choice within an eigenspace, and different vectors in the same eigenspace could select different $F$ for a trivial reason. Complexity relative to a reference plays no role in this definition, so the vacuity of Appendix B cannot enter it.

Two classes of **control** state are used in the experiment, each with an expected outcome (an earlier version also used thermal states, but the state cost of Section 4.1 is defined for pure states and no mixed-state cost $L(\rho\mid F)$ was defined; they are dropped rather than defined here):

- *Prepared states:* $W|\Omega_{J_0}\rangle$ for $W$ a short circuit of even gates on $O(1)$ of the undressed modes. These are expected to behave like physical states if the selected geometry is robust under $J_0\to J_0'$ for several random reference pairings, and to expose $J_0$-dependence otherwise.
- *Haar-random parity-even states:* expected to admit no cheap $F$ at all.

---

## 3 Factorizations

*Definitions.*

### 3.1 The class $\mathcal{F}$

A factorization is a triple $F=(O,\{B_i\},V)$ with:

- $O\in\mathcal{G}_s\subset SO(M)$, a rotation of the modes, $\chi'=O\chi$, drawn from a **declared finite class**: products of at most $s$ Givens rotations on pairs of modes, with angles from a finite alphabet of $2^{p}$ values. Each Givens rotation is $\exp(\theta\chi_a\chi_b/2)$ acting by conjugation, so the class lies in $SO(M)$ and is implemented on Fock space by the parity-preserving Gaussian unitary $U_O$ with $U_O^\dagger\chi_aU_O=\sum_bO_{ab}\chi_b$ [24,25]; reflections ($\det O=-1$) are implemented by odd operators and are excluded. $\mathcal{G}_s$ is nested in $s$, $\mathcal{G}_0=\{\mathbb{1}\}$, and for small $s$ is exhaustively enumerable. A general element of $SO(M)$ at precision $p$ is the limit $s\to\binom{M}{2}$ and costs $\sim\binom{M}{2}p$ bits (Section 4.1).
- $\{B_i\}$, a partition of the rotated modes into $n=M/2m$ sites of $2m$ modes each; $m$ is a declared convention, scanned.
- $V\in\mathcal{V}_D$, a parity-preserving unitary from a declared class of circuits of depth at most $D=O(1)$ built from even gates on $O(1)$ rotated modes; continuous gate parameters are charged at $p$ bits each (Section 4.1).

**Convention.** Let $W=VU_O^\dagger$. The site generators are $\tilde\chi_a=W\chi_aW^\dagger=V\chi'_aV^\dagger$. The coefficients of the original $H$ when expanded in monomials of the $\tilde\chi$ are the coefficients of
$$
H_F\;=\;W^\dagger HW\;=\;U_O\,V^\dagger H\,V\,U_O^\dagger
$$
expanded in monomials of the original $\chi$, since $H=\sum_Sc_S\tilde\chi_S=W\big(\sum_Sc_S\chi_S\big)W^\dagger$. This convention — generators transformed actively, Hamiltonian by the inverse — is used throughout. (Earlier versions wrote $VOHO^{\mathsf T}V^\dagger$, mixing the index space of $O$ with the Fock space, and then $VU_OHU_O^\dagger V^\dagger$, the wrong direction of conjugation.)

Site $i$ is the subalgebra generated by $\{V\chi'_aV^\dagger:a\in B_i\}$, of local dimension $2^m$. Even operators on distinct sites commute, odd ones anticommute, physical observables are even, and physical states have definite parity. No Jordan–Wigner encoding is used; entanglement between sites is the fermionic partial trace on parity-symmetric states [11,12] and tensor networks are fermionic [13,14].

The restrictions on $O$ and $V$ are part of the principle, not of the experiment. If $V$ were arbitrary, the eigenbasis of $H$ would be a legal factorization in which $H$ is a list of eigenvalues, cheap for a reason unrelated to locality. If $O$ were free of charge, a fine-tuned rotation could make any $H$ and $\Psi$ simple while the information that accomplished it went untransmitted. Both are excluded by $\mathcal{F}$ and by $L(F)$.

### 3.2 The quotient

Two triples related by site-local unitaries and permutations of sites define the same factorization. The term listing and the tensor entries depend on the local basis, so the cost of a factorization is defined as the minimum of $\mathcal{C}$ over site-local representatives; in practice a canonical representative (e.g. the site basis that diagonalizes the on-site part of $H$) is declared and used.

### 3.3 Support hypergraph and codebook

Expanding $H_F$ in Majorana monomials of the rotated modes and grouping by site, each term $T$ touches a set of sites $\mathrm{supp}_F T$; after conjugation by an interacting $V$ a degree-$q$ monomial need not remain degree $q$, so supports are taken as they actually are. The **support hypergraph** $\mathcal{S}_F$ has the sites as vertices and every touched set as a hyperedge $e$, with weight $w_e^2$ the summed squared coefficients of the terms supported on it. Because Majorana monomials are orthonormal under the normalized trace, $\sum_e w_e^2=\|H\|_F^2/\dim$ is invariant under $U_O$ and $V$, so weights are comparable across factorizations. $\mathcal{S}_F$ is exact and is not chosen.

The **weight-carrying support** at level $\eta$ is $\mathcal{S}_F^{(\eta)}$, the smallest set of hyperedges carrying a fraction $\eta$ of $\sum_ew_e^2$. Every geometric or graph-theoretic diagnostic is computed on $\mathcal{S}_F^{(\eta)}$ and must be stable for $\eta\in\{0.90,0.95,0.99\}$; a conclusion that holds only at one $\eta$ is not reported. This is what stops a nearly geometric graph with many weak long-range terms from being declared geometric by fiat.

The **codebook** $G_F$ is a hypergraph on the same sites chosen as part of the description of $H$: terms whose support is a codebook hyperedge are listed cheaply, others expensively. An optimizer left free to choose $G_F$ would pick a lattice as a dictionary and hide the couplings in the residual; the cost of listing $G_F$ and the **honesty condition**
$$
\frac{\sum_{e\in G_F}w_e^2}{\sum_e w_e^2}\;\ge\;\eta_H,\qquad \eta_H\ \text{declared},\ \text{e.g. }0.95,
\tag{3.1}
$$
prevent this. Geometric diagnostics are computed on $\mathcal{S}_F$ restricted to its weight-carrying hyperedges, never on the codebook.

---

## 4 The Selection Principle

*Definitions, two exact statements, and one conjecture.*

### 4.1 The three costs

Fix one description language — a two-part code — and one precision $p$ for all real numbers.

- $L(F)$: bits to specify the transformation. For $O\in\mathcal{G}_s$: $s$ pair labels at $\log_2\binom{M}{2}$ bits each and $s$ angles at $p$ bits, plus $\log_2 s$. For the partition: $\log_2$ of the number of partitions of $M$ modes into blocks of $2m$. For $V\in\mathcal{V}_D$: the gate list — gate type and mode labels — plus every continuous gate parameter at $p$ bits. A general rotation at precision $p$ would cost $\sim\binom{M}{2}p$ bits.
- $L(H\mid F)$: bits to list a codebook $G_F$ as an adjacency structure, then each term $T$ of $H_F$ as a codebook hyperedge index or, off-codebook, its actual site set at $|\mathrm{supp}_FT|\log_2n$ bits; an operator label within the site tensor product on that support; and a coefficient at precision $p$. Terms are charged by the support they actually have after $V$, not by the degree $q$ they had before it; otherwise an interacting $V$ could create complexity in $H$ that the cost does not see.
- $L(\Psi\mid F)$: bits to list a fermionic tensor network on the sites, with bonds along the codebook hyperedges, reproducing $|\Psi\rangle$ to fidelity $1-\epsilon$: bond dimensions and tensor entries at precision $p$.

**The baseline.** There is no "ultraviolet presentation" in the class $\mathcal{F}$: the microscopic data contain no pairing of modes into sites, and an earlier version's $F_{\mathrm{UV}}=(\mathbb{1},\{B_i\}_{\mathrm{UV}},\mathbb{1})$ quietly supplied one. The baseline is instead the best description obtainable without any change of variables,
$$
\mathcal{C}_0(H,\Psi)\;=\;\min_{\{B_i\}}\ \mathcal{C}\big(O=\mathbb{1},\{B_i\},V=\mathbb{1};\,H,\Psi\big),
\qquad F_\varnothing=\arg\min,
\tag{4.1}
$$
minimized over the zero-transformation class $\mathcal{F}_\varnothing=\{O=\mathbb{1},V=\mathbb{1}\}$ (pairings only). The quantity the experiment measures is
$$
\Delta\mathcal{C}\;=\;\mathcal{C}_0-\mathcal{C}(F^*),
$$
the amount by which a genuine change of variables beats the best mere grouping of the original Majoranas. The baseline geometry to be improved upon is $\mathcal{S}_{F_\varnothing}^{(\eta)}$, the quotient of $E$ under the best pairing, not $E$ itself; whether that quotient is expander-like is established first (Section 5.1). $\mathcal{C}_0$ is itself a minimum over $(M-1)!!$ pairings and is exactly computable only where Section 5.3 permits; at larger $M$ it is the best sampled pairing and is reported as such.

### 4.2 Why the model cost matters, and what it implies

Charging for $F$ has a consequence worth stating before any computation, together with a caveat that determines whether the state votes at all. The ground state of a sparse SYK Hamiltonian is highly entangled across mode bipartitions, and one might expect $L(\Psi\mid F_\varnothing)$ on the baseline to approach the exponential cost of a generic state, so that a rotation making it area-law on some $G_F$ would save enough to pay $\binom{M}{2}p$ for a general rotation. That expectation is not justified. Sahu and Swingle show that tensor networks on sparse expander graphs represent volume-law states with polynomial resources [26], because every cut through an expander is volume-sized and bounded bond dimension already yields volume-law entanglement. Entanglement entropy and representation cost are different quantities, and on an expander the second can be small while the first is maximal. It is therefore possible that $L(\Psi\mid F_\varnothing)=\mathrm{poly}(M)$ and that the best mere pairing is already cheap for both $H$ and $\Psi$ — in which case $F^*\approx F_\varnothing$, the state's cost hardly varies across candidates, and the principle collapses toward spectrum selection. Whether the state cost varies enough across candidate factorizations to have a vote is the second pre-test of Section 5.1, run before any search.

If the state does vote, the tension is three-way. A rotation that makes $\Psi$ cheap also acts on $H$: a $q$-body term in the undressed modes becomes a sum of up to $M^q$ $q$-body terms in the rotated modes, so a generic $O$ makes $H$ dense and its support hypergraph complete rather than geometric. The principle is therefore a real three-way tension — the transformation must be cheap, the Hamiltonian must stay sparse and few-body on a codebook, and the state must become compressible on that codebook — and none of the three can be bought with the others for free. A geometric $F^*$ exists only if the compression of $H$ and $\Psi$ together pays for the change of variables that reveals it. This is the sharpened content of the proposal, and it is what an uncharged $O$ would have concealed.

### 4.3 Two exact statements

**Lemma (vacuity, unrestricted).** For any definite-parity pure state there is a parity-preserving unitary that maps it to the Fock vacuum of any declared pairing, in which it is a product state (Appendix B). Hence over unrestricted transformations $\min_F L(\Psi\mid F)$ is $O(n)$ for every state and selects nothing. Within $\mathcal{F}$, $\min_F L(\Psi\mid F)$ alone is not vacuous — it finds a nearby split that makes this state cheap — but it ignores $H$ and is the wrong principle for that reason.

**Theorem (Cotler–Penington–Ranard [4], stated at the strength we use).** For generic spectra, a factorization in which $H$ is few-body is essentially unique up to site-local unitaries and permutations when one exists. Hence $\min_F L(H\mid F)$ alone is spectrum-determined: the state has no vote and the selection cannot change without changing $H$.

The principle (1.1) is the tension between these, with $L(F)$ ensuring the tension is not resolved by free information in the basis.

### 4.4 Why the state cost is not conditional on $H$

An earlier version defined the state's cost as a conditional Kolmogorov complexity $K(\Psi\mid H,F)$. For any ground state there is a short program — "diagonalize $H$, return the lowest eigenvector" — that never mentions $F$, so that quantity is $O(1)$ in every factorization and ranks nothing (Appendix A). The state votes only if its cost is a *representation* cost in $F$, as in Section 4.1.

### 4.5 The hybrid, and the bias

The Hamiltonian decides which factorizations are candidates; the state decides which candidate is physical; the model cost decides whether either is worth the transformation. In the limit where $H$ is exactly few-body in exactly one factorization the candidate set is a singleton and the state's role reduces to distinguishing a low-entanglement from a high-entanglement phase within a fixed split (a state whose cost is the same in every candidate — which the Sahu–Swingle mechanism can produce — is this limit). The soft cost is what makes the candidate set a cloud in which the state's vote is real. We say this rather than hide it.

The principle has no power-law bias toward one-dimensional factorizations — a tensor-network listing is extensive in $n$ in every dimension, with $d$ entering through the coordination number — but a path has an unusually short adjacency list and at $M\sim24$ that mild compressibility can dominate. Section 5.5 treats a path as a live outcome for this reason. Dimension is not selected by the principle and is not claimed to be — and at the sizes of Section 5.2 it could not be measured if it were (Section 4.6).

### 4.6 The conjecture

The conjecture is split by what the accessible sizes can support. At $M=24$ and $m=1$ there are twelve sites; at $m=2$, six; the exhaustively certified calculation at $M=14$ has seven. On a twelve-vertex graph no scaling window distinguishes $V(r)\sim r^2$ from $V(r)\sim r^3$, and Hausdorff dimension and face-rule-stable topology are large-system concepts. The small-$M$ conjecture therefore asks for something a small graph can exhibit.

**Small-$M$ conjecture.** *For $H$ of the form (2.1) with expander couplings in some range of $(q,\kappa)$, and for ground-space states, there exists $F\in\mathcal{F}$ at moderate $(s,D)$ such that (i) $\Delta\mathcal{C}=\mathcal{C}_0-\mathcal{C}(F)>0$ is a substantial fraction of $\mathcal{C}_0$ under the honesty condition (3.1); (ii) the weight-carrying support $\mathcal{S}_{F}^{(\eta)}$ is reproducibly less expander-like than the baseline quotient $\mathcal{S}_{F_\varnothing}^{(\eta)}$, by finite-graph diagnostics — Laplacian spectral gap $\lambda_2$, conductance, diameter, and $V(r)$ — measured against null ensembles matched in size, edge count, and degree sequence $(n,|E|,\{d_i\})$ and, for weighted supports, in weight distribution, together with path, cycle, small-lattice, and complete-graph references; and (iii) for the ground state and first excited state of the same gapped $H$ the minimizers differ reproducibly in $\mathcal{S}_{F^*}^{(\eta)}$.*

**Scaling conjecture (not tested here).** *In the large-$M$ limit the selected support has polynomial ball growth with a stable exponent $d_s>1$.* This is what a positive small-$M$ result would make worth pursuing; it is not what twelve sites can establish, and a very local-looking twelve-node graph is not to be assigned a dimension.

The small-$M$ conjecture is the paper's only claim beyond definitions, and Section 5 is its test.

---

## 5 The Experiment

*No results are reported.*

### 5.1 Two pre-tests, as empirical questions

**(a) State vote.** Before any search, determine whether the state changes the *ranking* among near-optimal Hamiltonian descriptions; spreads are the wrong quantity, since a state term of ten bits can decide a winner among candidates whose Hamiltonian costs differ by two bits while a thousand-bit spread elsewhere is irrelevant, and a large state spread perfectly correlated with the Hamiltonian cost changes nothing. Define the candidate cloud
$$
\mathcal{N}_\delta\;=\;\big\{F\in\mathcal{F}_k:\ L(F)+L(H\mid F)\le C_H^{\min}+\delta\big\},
$$
the factorizations within $\delta$ bits of the cheapest Hamiltonian description in the searched class, and compute $L(\Psi\mid F)$ on $\mathcal{N}_\delta$ for the ground state. The questions are: is $\mathrm{Var}_{\mathcal{N}_\delta}L(\Psi\mid F)>0$ beyond convention-dependence; does $\arg\min_F[L(F)+L(H\mid F)]$ differ from $\arg\min_F\mathcal{C}(F;H,\Psi)$; and, most directly, is $F^*_{\Psi_1}\neq F^*_{\Psi_2}$ for the ground and first excited states? If the state does not reorder $\mathcal{N}_\delta$ — the outcome the Sahu–Swingle mechanism [26] makes plausible for an expander, where the state may be cheap in every candidate — then the state has no effective vote at these sizes, the minimizer is spectrum-selected, and clause (iii) is disfavored before the search is run. That is reported as the result. Also established here: whether the baseline quotient $\mathcal{S}_{F_\varnothing}^{(\eta)}$ is expander-like by the diagnostics of Section 5.4, so that "less expander-like" has a measured reference.

**(b) Spectral.**

Whether a geometric factorization exists is a property of $H$ alone, and some necessary conditions are spectral invariants. Dense SYK has an extensive zero-temperature entropy $S_0\propto M$ and a Schwarzian low-energy density of states [9]; a generic few-body Hamiltonian on a finite-growth graph has a unique or weakly degenerate ground state. Heuristically — with the caveat that frustrated local models can have extensive degeneracy — an extensive $S_0$ obstructs any geometric representation. Since sparse SYK retains dense-limit physics down to $\kappa=O(1)$ [10], we do *not* assume a sparsity window in which these signatures disappear. The pre-test is the empirical question: as $\kappa$ is lowered at fixed $q$ and $M$, is there any regime in which the low-energy spectrum ceases to carry the dense-SYK signatures that appear incompatible with a finite-growth local representation? If the answer is no at accessible $M$, the conjecture is disfavored for the class (2.1) before any search, and that is reported as the result. If a window exists, the search is run in it.

### 5.2 Sizes

$M\in\{20,22,24\}$ Majorana modes for the pre-test and the sampled search, Fock dimension $2^{M/2}\le2^{12}$, exactly diagonalizable; $M\in\{12,14\}$ for exhaustive certification of $\mathcal{F}_0$ (Section 5.3). The search is the expensive part: partitions alone number $(M-1)!!$ at $m=1$, and $\mathcal{G}_s$ and $\mathcal{V}_D$ multiply that.

### 5.3 Nested search and what can be falsified

Because (1.1) is a nonconvex minimization, failure of a local optimizer establishes only that a minimum was not found. To make the conjecture falsifiable in a declared sense, the search is nested over classes

$$
\mathcal{F}_0\subset\mathcal{F}_1\subset\mathcal{F}_2\subset\cdots,\qquad
\mathcal{F}_0=\{V=\mathbb{1},\ O\in\mathcal{G}_{s_0}\},\quad \mathcal{F}_1=\{V\in\mathcal{V}_1,\ O\in\mathcal{G}_{s_1}\},\ \dots
$$

and exhaustive enumeration is possible only where the arithmetic allows it. At $m=1$ the number of partitions of $M$ modes into pairs is $(M-1)!!$: $10{,}395$ at $M=12$, $135{,}135$ at $M=14$, $2.0\times10^{6}$ at $M=16$, $6.5\times10^{8}$ at $M=20$, and $3.2\times10^{11}$ at $M=24$. Since each evaluation of $\mathcal{C}$ rewrites $H$ and compresses a tensor network, exhaustive enumeration of $\mathcal{F}_0$ is confined to $M\le14$ with $s_0=0$ and $V=\mathbb{1}$, where every pairing is evaluated.

Enumerating the outer class does not by itself certify the minimum of $\mathcal{C}$: each pairing still requires two inner minimizations, $\min_{G_F}L(H\mid F)$ and, worse, the variational tensor-network compression behind $L(\Psi\mid F)$, which is nonconvex. Outer exhaustion therefore licenses only the statement "the factorization class was exhaustively enumerated," not "the conjecture was falsified or confirmed." To preserve genuine certification at tiny $M$ we define a **certification cost** $\mathcal{C}_{\mathrm{cert}}$ whose inner problems are exact: the codebook is fixed deterministically as $G_F=\mathcal{S}_F^{(\eta_H)}$, removing the first minimization; and the state is coded as a fermionic tree tensor network, with the tree topology enumerated (for $n\le7$ sites there are $n^{\,n-2}\le16{,}807$ labelled trees) and the bond dimension on each tree edge set to the exact Schmidt rank of $|\Psi\rangle$ across the bipartition that edge defines, computed by singular value decomposition on the parity-symmetric state. $\mathcal{C}_{\mathrm{cert}}$ is then a computable function of $F$ with no variational residue, and its minimum over all pairings at $M\le14$ is certified. Within $\mathcal{F}_0$, at those sizes, and for $\mathcal{C}_{\mathrm{cert}}$, the small-$M$ conjecture is *falsified* or *confirmed*. The expressive variational cost of Section 4.1 is the second, larger experiment: exact restricted MDL test first, expressive variational MDL search second. At $M\in\{20,22,24\}$, $\mathcal{F}_0$ is sampled — a declared number of pairings drawn uniformly, with the fraction of the class covered reported — and all larger classes are searched by a declared ansatz from declared initializations, whose output is a local minimum. The honest statement for everything beyond exhaustible $\mathcal{F}_0$ is that the conjecture is disfavored if increasingly expressive searches systematically fail to find $\Delta\mathcal{C}>0$ with geometric support.

### 5.4 Three questions, with controls

1. **Compression.** Can $H$ and $\Psi$ jointly pay for a nontrivial change of factorization — is there $F\in\mathcal{F}_k$ with $\mathcal{C}(F)$ substantially below the baseline $\mathcal{C}_0$, the honesty condition (3.1) satisfied, and the state's bond dimension bounded rather than growing with $n$? *Controls:* Haar states should fail this; robustness under $p\to p\pm2$ and $\epsilon\to\epsilon/10$ is required; and, because additive coding constants are not negligible at $M\le24$, the qualitative minimizer must survive two or three independently reasonable coding conventions for graphs and term lists, $F^*_{\mathcal{C}_1}\simeq F^*_{\mathcal{C}_2}\simeq F^*_{\mathcal{C}_3}$, rather than relying on an asymptotic invariance argument at tiny $M$.
2. **Locality.** Is $\mathcal{S}_{F^*}^{(\eta)}$ reproducibly less expander-like than the baseline quotient $\mathcal{S}_{F_\varnothing}^{(\eta)}$ — larger diameter, smaller $\lambda_2$ and conductance, slower $V(r)$ — against null ensembles matched in $(n,|E|,\{d_i\})$ (configuration-model graphs with the same degree sequence) and in weight distribution, with path, cycle, small-lattice, and complete-graph references, stably for $\eta\in\{0.90,0.95,0.99\}$? Matching degree is what distinguishes organization from mere sparsification: an optimizer that only reduces the number of significant edges lowers $\lambda_2$ and conductance and raises the diameter without finding anything local. Dimension is not asked for at these sizes.
3. **State vote.** For the ground state and the first excited state of the same gapped $H$, do the minimizers differ in $\mathcal{S}_{F^*}^{(\eta)}$? *Controls:* the same state from several random initializations must return the same $\mathcal{S}_{F^*}$ up to site permutation before a difference between states is credited; prepared-state controls must give the same answer under $J_0\to J_0'$.

Two cost proxies are run side by side — the listing cost of Section 4.1, and $L(F)+L(H\mid F)$ plus the distance of $|\Psi\rangle$ from the low-energy subspace of the codebook-truncated Hamiltonian converted to bits by a declared rule (the energy variance with respect to the full $H$ is a unitary invariant and cannot serve). Agreement at the minimizer is evidence of language independence; disagreement is a result.

### 5.5 Outcomes

In decreasing order of prior probability:

- **A pre-test fails:** the state cost does not vary across candidates (spectrum selection), or no spectral window exists; or **no $F$ compresses** within exhaustible $\mathcal{F}_0$ at $M\le14$ and sampled or ansatz searches at $M\le24$ fail systematically. The small-$M$ conjecture is falsified within $\mathcal{F}_0$ at $M\le14$ and disfavored beyond it for the class (2.1).
- **Compression with a path or a backboned complete graph.** A path found under a charged $O$ with no encoding is a fact about $H$, to be understood rather than read as a low-dimensional preview.
- **Compression with a support reproducibly less expander-like than the baseline quotient $\mathcal{S}_{F_\varnothing}^{(\eta)}$ that moves under a change of state at fixed $H$.** The small-$M$ conjecture holds within the searched class. This is the headline a positive result would carry, and it is already interesting; the scaling conjecture then becomes the next project.

The third outcome would surprise us. The design makes the first cheap to reach and, within $\mathcal{F}_0$, unambiguous.

---

## 6 Beyond the Conjecture: Targets, Not Claims

*Nothing in this section follows from Sections 2–5. It records what a positive result would make it sensible to attempt next.*

**Locality and algebras of regions.** If $\mathcal{S}_{F^*}$ has finite growth, a region is a set of sites and its algebra is the even subalgebra they generate; regions nest and disjoint regions commute. That net is the starting point of algebraic quantum field theory [15], obtained here as an output. The state-dependence of $F^*$ is *not* the state-dependence of holographic reconstruction, in which a wedge moves within a fixed bulk/boundary split [16]; a new $F^*$ is a new tensor product of the fundamental space, and whether wedge-like behaviour appears after coarse-graining within one $F^*$ is open.

**Time.** The parameter $t$ in $e^{-iHt}$ is not identified with any emergent clock. If region algebras exist, relational time in the sense of Page and Wootters [17], with modular flows [18] supplying the local version, is the construction to attempt. Its consistency with slow entanglement growth would be a check on $F^*$, not the criterion that selected it.

**Gauge redundancy.** A factorization is invertible, so at this stage emergent and fundamental operators are in one-to-one correspondence and there is no redundancy. Redundancy can arise only after an effective subspace $P_{\mathrm{eff}}$ is identified — the low-energy sector of $F^*$, if it forms an approximate quantum code — through the equivalence $O\sim O'$ iff $P_{\mathrm{eff}}OP_{\mathrm{eff}}=P_{\mathrm{eff}}O'P_{\mathrm{eff}}$ [16,19]. Whether the selected low-energy sector forms such a code is a further question.

**Gravity.** Given region algebras, an area–entanglement identification (which at finite bond dimension is the min-cut bound of random tensor networks [20]), and modular flow that is locally a boost, Jacobson's argument [2,3] derives the Einstein equation as an equation of state, with a known caveat for non-conformal matter [21]. The argument takes a background manifold as input and can be attempted only after $F^*$ is geometric. This is the standard for "has gravity" and it has not been met.

---

## 7 Claims and Non-Claims

**Claimed.** (a) The principle (1.1) over the class $\mathcal{F}$ is well-posed, static, non-vacuous, and honestly two-part. (b) The small-$M$ conjecture of Section 4.6. (c) The prediction that a non-geometric $H$ and a ground-space $\Psi$ can jointly pay for a nontrivial change of factorization, that the change turns an expander support into a reproducibly more local one, and that the selection can change at fixed $H$. The finite-dimensional-geometry claim is the scaling conjecture and is not claimed here.

**What would disfavor the conjecture.** A negative state-vote or spectral pre-test at accessible $M$; falsification within an exhaustible $\mathcal{F}_0$; systematic failure of increasingly expressive searches; or a proof that expander polynomials admit no factorization in $\mathcal{F}$ with $\Delta\mathcal{C}>0$ and geometric support.

**Not claimed, and withdrawn from earlier versions.** That the principle selects three spatial dimensions. That emergent Lorentz invariance follows (the ultraviolet plants no frame; whether the minimizer produces one is unknown). That finite Hilbert-space dimension forbids exact continuous symmetries (false: finite multiplets carry exact $SU(2)$) or fixes a floor for $\Lambda$. That black-hole spectra are random-matrix-like, that there is no intermediate scale, or that neutrinos are Majorana particles (starting from Majorana *operators* implies nothing about emergent neutrino fields). That gauge redundancy follows from factorization. That the framework has gravity.

---

## 8 Relation to Predecessors

**Shokrian Zini, Brown, and Freedman [6].** The closest predecessor: a loss functional of a Hamiltonian and a state, minimized to obtain a tensor-product structure respected by both, described as a co-emergence of locality. The novelty claimed here is therefore not "use $H$ and $\Psi$ jointly." It is: the cost is a description length with an explicit model term, so that the transformation is charged and the principle is an MDL principle rather than a loss; the ultraviolet Hamiltonian is an explicit expander, so that no geometry is planted; the factorizations are fermionic and ordering-free; the test is state-dependent movement at fixed $H$; and the diagnostics are geometric properties of the selected support hypergraph. Whether these differences matter is for the numerics to say.

**Cotler–Penington–Ranard [4]** supplies the uniqueness half and the spectrum-only limit. **Carroll–Singh [5]** supplies the state's role through predictability, replaced here by a static representation cost to avoid the clock. **Cao–Carroll–Michalakis [1]** reconstruct geometry given a factorization; this proposal is upstream of that step. **Sparse SYK [10]** is the ultraviolet object, used without assuming any sparsity window in which its dense-limit physics disappears.

**Entanglement–Gauge Gravity [22].** A growing causal graph with an isometric Clifford circuit and three conjecturally coincident geometries — local, growing, bosonic, with an attachment kernel. The present proposal is its complement on nearly every axis. The two share the geometric diagnostics (ball growth, cut scaling, face-stable homology), which apply verbatim to $\mathcal{S}_{F^*}$; causal-order diagnostics do not, since $\mathcal{S}_{F^*}$ is spatial.

**Diamond-algebra pictures.** A net of algebras on causal diamonds with area as entanglement and the Einstein equation as its first law describes an equilibrium; this proposal attempts to name what would equilibrate, and would be its ultraviolet if the conjecture held and Section 6 were carried out. That is a statement of intent, not a result.

---

## 9 Conclusion

The proposal is that space is the cheapest description of the world, with "cheapest" now meaning what a two-part code means: the transformation that reveals the simplicity is paid for at the same rate as the simplicity it buys. The Hamiltonian restricts, the state selects, the model cost keeps both honest, and nothing temporal or spatial is assumed. One conjecture rests on this, and it has a pre-test that may end the matter, an exhaustible class in which it can be falsified outright, and a most-probable outcome of failure. If it fails, the class (2.1) is ruled out as a substrate for emergent locality by this principle at accessible sizes. If it holds for $\mathcal{C}_{\mathrm{cert}}$ within exhaustible $\mathcal{F}_0$ at $M\le14$ and survives the variational search at $M=24$, the foundational claim fits on a blackboard and the questions of dimension, time, and dynamics become questions about a specific object.

---

## Appendix A — Why conditioning on $H$ deletes the state's vote

For a ground state (or any indexed eigenstate) the program "construct $H$; diagonalize; return the indexed eigenvector" has length $O(1)$ beyond the description of $H$ and makes no reference to a factorization. Hence $K(\Psi\mid H,F)$ is bounded independently of $F$ and $\min_F[K(H\mid F)+K(\Psi\mid H,F)]$ is determined by the first term alone. Changing universal language shifts $K$ by an additive constant and cannot introduce $F$-dependence. The representation cost of Section 4.1 charges for tensors on the sites of $F$, which depends on which sites were chosen.

## Appendix B — The vacuity lemma

Let $|\Psi\rangle$ have definite parity on the Fock space of $M$ Majorana modes and let $J$ be any pairing with vacuum $|\Omega_J\rangle$ of the same parity (adjust by one fermion if needed). The parity-preserving unitary group acts transitively on states of a given parity, so some $W$ maps $|\Psi\rangle$ to $|\Omega_J\rangle$, a product state in the $J$-paired block partition. With unrestricted $V$ the factorization $(\mathbb{1},\{B_i\}_J,W)$ therefore has $L(\Psi\mid F)=O(n)$ and $\min_F L(\Psi\mid F)$ carries no information beyond parity. Restricting $V$ to $\mathcal{V}_D$ and charging $L(F)$ removes this degeneracy, which is one of the two reasons those restrictions are part of the principle.

## Appendix C — Cost accounting

*Model.* $L(O)=\log_2 s+s\big[\log_2\binom{M}{2}+p\big]$ for $O\in\mathcal{G}_s$; $L(\{B_i\})=\log_2\big[M!/((2m)!^{n}\,n!)\big]$; $L(V)=$ declared bits per gate times gate count. A general $O\in O(M)$ at precision $p$ would cost $\binom{M}{2}p$, which for $M=24$, $p=8$ is $2208$ bits — larger than $L(H\mid F_\varnothing)$ for a sparse $H$ with $\kappa=O(1)$, so a generic rotation cannot be paid for by the Hamiltonian term alone and must be paid for, if at all, by the state.

*Hamiltonian.* $L(E)$ for the codebook as an adjacency structure ($O(nc\log n)$ for a random hypergraph of degree $c$, less for a compressible one); per term $T$, $\log_2|E(G_F)|+O(|\mathrm{supp}_FT|\log 2m)+p$ on-codebook, $|\mathrm{supp}_FT|\log_2 n+O(|\mathrm{supp}_FT|\log 2m)+p$ off-codebook, with $|\mathrm{supp}_FT|$ the support after $V$.

*State.* For a fermionic tensor network on the codebook with bond dimensions $\chi_e$: $\sum_e\log_2\chi_e$ plus $p\times$(tensor entries). For an area-law state on a codebook of bounded degree $c$ this is $O(n\,c\,\chi^{c}\,p)$, extensive in $n$ in every dimension. On an expander codebook the same bounded-$\chi$ cost already accommodates volume-law entanglement [26], which is why the state's cost may fail to vary across candidates (Section 5.1a).

*Baseline.* $\mathcal{C}_0=\min_{\{B_i\}}\big[L(\{B_i\})+L(H\mid \mathbb{1},\{B_i\},\mathbb{1})+L(\Psi\mid\mathbb{1},\{B_i\},\mathbb{1})\big]$, in which $H$'s support is the quotient of $E$ under the pairing and the state term is whatever the ground state costs as a network on that quotient — possibly only polynomial in $M$ despite volume-law entanglement [26]. *Certification cost.* $\mathcal{C}_{\mathrm{cert}}$ replaces the codebook minimization by $G_F=\mathcal{S}_F^{(\eta_H)}$ and the variational state cost by a tree tensor network with exact Schmidt ranks $r_e$ on tree edges: $\sum_e\log_2 r_e$ plus $p$ times the entry count $\sum_i 2^m\prod_{e\ni i}r_e$, minimized over labelled tree topologies.


---

## References

[1] C. Cao, S. M. Carroll, S. Michalakis, "Space from Hilbert space: recovering geometry from bulk entanglement," *Phys. Rev. D* **95**, 024031 (2017).
[2] T. Jacobson, "Thermodynamics of spacetime: the Einstein equation of state," *Phys. Rev. Lett.* **75**, 1260 (1995).
[3] T. Jacobson, "Entanglement equilibrium and the Einstein equation," *Phys. Rev. Lett.* **116**, 201101 (2016).
[4] J. S. Cotler, G. R. Penington, D. H. Ranard, "Locality from the spectrum," *Commun. Math. Phys.* **368**, 1267 (2019), arXiv:1702.06142.
[5] S. M. Carroll, A. Singh, "Quantum mereology: factorizing Hilbert space into subsystems with quasiclassical dynamics," *Phys. Rev. A* **103**, 022213 (2021), arXiv:2005.12938.
[6] V. Shokrian Zini, A. R. Brown, M. H. Freedman, "The smallest interacting universe," *JHEP* **01**, 082 (2023), arXiv:2208.00944. See also M. H. Freedman, V. Shokrian Zini, "The universe from a single particle," *JHEP* **01**, 140 (2021).
[7] S. Sachdev, J. Ye, "Gapless spin-fluid ground state in a random quantum Heisenberg magnet," *Phys. Rev. Lett.* **70**, 3339 (1993).
[8] A. Kitaev, "A simple model of quantum holography," KITP talks (2015).
[9] J. Maldacena, D. Stanford, "Remarks on the Sachdev–Ye–Kitaev model," *Phys. Rev. D* **94**, 106002 (2016).
[10] S. Xu, L. Susskind, Y. Su, B. Swingle, "A sparse model of quantum holography," arXiv:2008.02303 (2020).
[11] S. B. Bravyi, A. Yu. Kitaev, "Fermionic quantum computation," *Ann. Phys.* **298**, 210 (2002).
[12] M.-C. Bañuls, J. I. Cirac, M. M. Wolf, "Entanglement in fermionic systems," *Phys. Rev. A* **76**, 022311 (2007).
[13] C. V. Kraus, N. Schuch, F. Verstraete, J. I. Cirac, "Fermionic projected entangled pair states," *Phys. Rev. A* **81**, 052338 (2010).
[14] P. Corboz, R. Orús, B. Bauer, G. Vidal, "Simulation of strongly correlated fermions in two spatial dimensions with fermionic projected entangled-pair states," *Phys. Rev. B* **81**, 165104 (2010).
[15] R. Haag, *Local Quantum Physics* (Springer, 1996).
[16] A. Almheiri, X. Dong, D. Harlow, "Bulk locality and quantum error correction in AdS/CFT," *JHEP* **04**, 163 (2015).
[17] D. N. Page, W. K. Wootters, "Evolution without evolution: dynamics described by stationary observables," *Phys. Rev. D* **27**, 2885 (1983).
[18] A. Connes, C. Rovelli, "Von Neumann algebra automorphisms and time-thermodynamics relation in generally covariant quantum theories," *Class. Quantum Grav.* **11**, 2899 (1994).
[19] D. Harlow, "Wormholes, emergent gauge fields, and the weak gravity conjecture," *JHEP* **01**, 122 (2016), arXiv:1510.07911.
[20] P. Hayden, S. Nezami, X.-L. Qi, N. Thomas, M. Walter, Z. Yang, "Holographic duality from random tensor networks," *JHEP* **11**, 009 (2016).
[21] H. Casini, D. A. Galante, R. C. Myers, "Comments on Jacobson's 'Entanglement equilibrium and the Einstein equation'," *JHEP* **03**, 194 (2016), arXiv:1601.00528.
[22] *Entanglement–Gauge Gravity: A Co-Emergence Hypothesis for Causal, Entanglement, and Gauge-Topological Geometry*, Version 4.3, unpublished draft (2026).
[23] L. Bombelli, J. Henson, R. D. Sorkin, "Discreteness without symmetry breaking: a theorem," *Mod. Phys. Lett. A* **24**, 2579 (2009).
[24] S. Bravyi, "Lagrangian representation for fermionic linear optics," *Quantum Inf. Comput.* **5**, 216 (2005), arXiv:quant-ph/0404180.
[25] R. Jozsa, A. Miyake, "Matchgates and classical simulation of quantum circuits," *Proc. R. Soc. A* **464**, 3089 (2008), arXiv:0804.4050.
[26] S. Sahu, B. Swingle, "Efficient tensor network simulation of quantum many-body physics on sparse graphs," arXiv:2206.04701 (2022).
