# Emergent Locality as Minimum-Description Communication

## 1. Model

Locality is the window of horizons in which a metric-ball permission is a cheapest sufficient reusable broadcast rule. Under coefficient 1 on every codelength, communication pays only when one emission is reused by several receivers, so the window needs the ball to beat every cheaper rule per event (A3, whose inside reading is near-site common information) as much as it needs far-site screening (A1).

**Sites and permissions.** Let V\_n = {1, …, n}. A structural hypothesis is a program ω = (M, φ, q) with placement φ : V\_n → M and permission predicate

```latex
P_\omega(i,j)=q\bigl(\phi(i),\phi(j)\bigr)\in\{0,1\},\qquad P_\omega(j,j)=0.
```

The diagonal is excluded. A site may never use its own broadcast.

**Sink and broadcasts.** There is a sink that decodes each site's observation site-wise under logarithmic loss. Site j may emit one message M\_j per event, a function of its own observation only (no relay: a message never depends on received broadcasts). Emission costs the message codelength once. Every site i with P(j, i) = 1 may use M\_j; delivery to a permitted recipient costs nothing. Point-to-point is the special case of one recipient.

Site-wise decoding is the modelling choice everything rests on. With a joint decoder, distributed source coding can exploit inter-site correlation at the joint-code level, which destroys the site-wise broadcast accounting on which the results below depend. Site-wise decoding is the right model for parallel per-site predictors with bounded memory and latency, where each site's next-step code is formed from what that site has received.

**Objective.** For N reuse events,

```latex
\mathcal{J}_N(\omega,\Pi)=L(\omega)+\operatorname{Reg}_N(\omega,\Pi)+R_N(\Pi\mid\omega)+L_{\log}(D_{1:N}\mid\Pi,\omega),
```

with coefficient 1 on every term. L(ω) = L(M) + L(φ | M) + L(q | M, φ) names the permission program and is paid once. R\_N = Σ\_t R\_t is the broadcast bill. L\_log is the sink's site-wise codelength given delivered messages. Reg\_N is parametric regret for predictive conditionals and for message encoders, of order (k/2) log N nats in expectation for k fitted parameters. All statements are in expectation under the data-generating distribution.

**Optimal sets.** For a predicate P,

```latex
C_N(P)=\inf_{\Pi:\,\operatorname{supp}\Pi\subseteq P}\mathcal{J}_N(P,\Pi),\qquad \mathcal{C}^\star_\tau(N)=\{P: C_N(P)\le C_N^\star+\tau\}.
```

Membership in C\*\_τ(N) is the only optimality claim made. The set need not be a singleton.

## 2. Why point-to-point never pays, and what broadcast buys

A message read by one site cannot reduce total codelength. A message read by several sites can, by exactly the information they share.

**Lemma 1 (point-to-point).** Let site i be decoded with side information S\_i and a transcript T\_i of messages addressed only to i, interactive or not. The saving against decoding from S\_i alone is

```latex
\Delta L_{\log,i}=I(X_i;T_i\mid S_i)\le H(T_i\mid S_i)\le H(T_i)\le L(T_i).
```

So under coefficient 1 every single-recipient channel has δ\_net = δ − r ≤ 0. Interactive protocols are covered because T\_i is the whole transcript. A new emission with one recipient never crosses.

**Broadcast value.** One emission M\_j costs H(M\_j) once and may enter the code of every i with P(j, i) = 1. Its net value per event is

```latex
v(M_j)=\sum_{i:\,P(j,i)=1} I\bigl(X_i;M_j\mid \text{other delivered broadcasts}\bigr)-H(M_j).
```

This is positive only when the message is informative to more than one receiver. Information in M\_j that is useful to at most one receiver cannot have positive net value. Full broadcast of the sender's observation, M\_j = X\_j, can pay whenever enough of X\_j is predictively reusable across several receivers: if X\_j is one bit shared with three neighbors, broadcasting it costs one bit and saves three, and the fact that j's own residual is still coded (P(j, j) = 0) does not cancel those savings. Optimal messages spend their bits on information that several receivers will use.

Communication therefore pays only when reused across receivers, and the quantity that sets its value is multi-receiver predictive common information, the sum in v(M\_j). A ball is the permission under which one emission has many nearby customers.

## 3. Permission classes and two kinds of exception

A short program is a reusable predicate. Shortness does not imply geometry: a star, a tree and a ball can all have description O(log n). Selection is by total codelength.

| Class | Predicate | Delivery |
| --- | --- | --- |
| Empty | P\_∅ | The sink decodes each site from its own past only |
| Ball | P\_r(i, j) = 1\[d(φ(i), φ(j)) ≤ r\] | One emission is delivered throughout the ball |
| Star | P\_h(i, j) = 1\[i = h or j = h\] | The hub emission is a global broadcast; each spoke emission has one customer (no relay, so the hub cannot rebroadcast) |
| Hierarchy | P\_T(i, j) = q\_T(i, j) | A broadcast goes to a separator's children or up the tree as q\_T specifies |
| Ball with exceptions | P\_{r,E} = P\_r ∪ E | The ball plus named extras of the two kinds below |

**Two kinds of exception.** Delivery to a permitted recipient is free per event, so an exception can be either of:

1. **Extra recipient.** A far site i is named as one more recipient of a broadcast M\_j the ball already pays for. Cost: a name, ΔL = O(log n), once. Per-event bill: zero. Gain: I(X\_i; M\_j | local broadcasts), which A1 caps at ε\_k(r). Crossing no earlier than ΔL / ε\_k(r), about log n / ε, and later if the gain misses the cap; finite whenever ε\_k(r) > 0.
2. **Extra emission.** A new message with its own bill. By Lemma 1 it has δ\_net > 0 only if it is informative to several receivers.

The statement "a point-to-point far edge never enters" holds for kind 2 with one recipient, and not for kind 1. If far delivery should itself cost something, charge delivery per recipient or by distance; that makes geometry a physical cost rather than a naming convenience. The present note charges delivery nothing, and the results are stated for that model.

## 4. Assumptions

Two hypotheses carry the theorem: far information is screened (A1, A1\*), and no cheaper predicate of any support beats the ball per event (A3). A0 is the inside reading of A3, stated because it says why A3 can hold for a ball. Hubs and hierarchies are ordinary competitors priced by A3 and the horizons, so the earlier A2 is not needed.

**A0 (the inside reading of A3; not a separate hypothesis).** The empty permission and every smaller radius are shorter names, so A3 already requires a(P\_∅; P\_r) < 0 and a(P\_{r'}; P\_r) < 0 for r' < r. That is δ\_loc > 0: the ball's broadcasts have positive net value over the best cheaper inside protocol. By Lemma 1 it can hold only if ball broadcasts have several customers who share information one message can carry. This paragraph is the reason A3 is satisfiable for a geometric rule, not an assumption the theorem lists.

**A1 (boundary screening).** Let A\_1, …, A\_m be disjoint interiors whose radius-r neighborhoods meet only on designated boundaries, and write X\_far,k = X\_{V\_n ∖ N\_r(A\_k)}. Under P\_r the sink's code for A\_k may use broadcasts from ∂\_r A\_k and not from earlier interiors. Assume

```latex
I\bigl(X_{A_k};X_{\mathrm{far},k}\mid X_{\partial_r A_k}\bigr)\le\varepsilon_k(r).
```

The comparison with a code that also sees far variables uses monotonicity in the second argument, I(A; B | C) ≤ I(A; B, B′ | C), not conditioning monotonicity, which fails in general. For a far message M = f(X\_far,k) added to the ball protocol, data processing gives I(X\_{A\_k}; M | X\_{∂\_r A\_k}) ≤ I(X\_{A\_k}; X\_far,k | X\_{∂\_r A\_k}) ≤ ε\_k(r), so the advantage of far broadcasts on the packed interiors is at most Σ\_k ε\_k(r) nats per event. This comparison conditions on the same local information on both sides. A competitor that removes or alters local messages changes the conditioning set, and conditional mutual information is not monotone in that set, so the bound is stated for nested far extensions of the ball protocol. The admissible coder is the boundary coder.

**A1\* (shift cover).** One packing does not price boundary or leftover sites. Assume a shift cover of S packings, each satisfying A1, such that every site is interior in at least one. By a union bound over the cover,

```latex
\Delta L_{\log}^{\mathrm{far}}\le S\,N\sum_k\varepsilon_k(r)+\Delta\operatorname{Reg}_N,
```

where ΔReg\_N includes encoder as well as predictive parameters. Summable Σ\_k ε\_k as m grows means total far-side residual is O(1) for the whole system. This typically fails at criticality, where conditional mutual information across a finite boundary decays as a power law and the sum over m \~ n / vol(r) blocks diverges. Critical long-range correlation is outside A1\* unless the power is summable on the cover.

**Hubs and hierarchies (no separate assumption).** A star or a separator tree has support outside P\_r, so Lemma 2 places it with the far users, and Section 6 prices it by its per-event advantage a(ω) and its name. If its name is shorter than the ball's, A3 requires a(ω) < 0. If its name is longer, it sits on the upper edge and enters N\_hi only when a(ω) > 0. With no relay a hub can broadcast only its own observation, so a sufficient condition for the star to satisfy A3 is a pairwise sum: sup over message encoders M\_h of Σ\_i I(X\_i; M\_h | local broadcasts) − H(M\_h) is less than the ball's net value v\_ball. That is "no low-dimensional global common cause," stated as a mutual-information condition rather than as a claim about J\_N.

When that sum exceeds v\_ball, the star has a cheaper name and a(P\_h) ≥ 0, A3 fails, and the window is empty. That is the correct outcome: a global common cause is a better explanation than geometry.

**A3 (no cheaper better predicate).** No predicate P with L(P) < L(P\_r) has G\_N(P) < 0 for arbitrarily large N, whatever its support; in the stationary case this is a(P; P\_r) < 0. The operational form is the one the theorem uses: a negative mean advantage with arbitrarily late downward spikes would still make N\_lo infinite. A0 covers only predicates whose optimal protocol runs inside the ball. A3 covers the rest: a shorter nonmetric rule, a star whose name is one site index, a hierarchy whose separator program is shorter than the embedding, any short predicate with support outside P\_r. Such a competitor wins at every horizon and empties the window. A3 is the one-line form of "the ball is the cheapest sufficient rule," and it is a hypothesis. It is strong: a tree with a shorter program and no worse per-event rate is excluded by fiat, and the outcome table marks where it fails. Section 6 lists exactly which rows of the sign table it empties.

## 5. Exhaustion lemma

Every competitor to the ball falls on exactly one side of the window, so the theorem faces each one once.

**Lemma 2 (exhaustion).** Fix a competitor ω with optimal admissible protocol Π\_ω. Exactly one of the following holds.

1. **Inside.** supp Π\_ω ⊆ P\_r. Then the ball can run Π\_ω unchanged, so C\_N(P\_r) ≤ L(ω\_r) − L(ω) + C\_N(ω) up to regret. The competitor can beat the ball only through a shorter name, ΔL(ω) = L(ω) − L(ω\_r) < 0. These competitors belong to the N\_lo analysis. If ΔL(ω) ≥ 0, the ball weakly dominates ω at every N.
2. **Outside.** Π\_ω uses permission outside P\_r: a far recipient of an existing emission (kind 1) or an emission delivered beyond the ball (kind 2). These competitors belong to the N\_hi analysis if their name is longer than the ball's, and to A3 if it is shorter, with ΔL(ω) and the per-event advantage a(ω) of Section 6 defined against the ball. Stars and separator trees are in this case.

A hub needs no separate family. Its spoke-to-hub channels are single-recipient and never pay (Lemma 1); its hub emission is a case-2 broadcast priced by a(P\_h), and its short name puts it under A3.

*Proof.* The two cases are complementary by definition of support. In case 1, running Π\_ω under P\_r is admissible and costs the same bill and residual, so only the names differ. In case 2 nothing is assumed about which local broadcasts the competitor keeps, removes, or alters. Its gap against the ball is ΔL(ω) + ΔReg\_N(ω) − Σ\_t a\_t(ω; P\_r), with a\_t the total per-event operating advantage of Section 6, by definition of J\_N. ∎

Lemma 2 sorts competitors; it does not price them. Inside competitors are priced by A3 (its inside reading, A0) and the sign table, outside competitors by A3 when cheaper and by N\_hi when not. The far user with a shorter name and nonnegative advantage is seen only by A3, which is why A3 is a separate hypothesis. With it, "no other family remains" is a deduction.

## 6. Horizons

The window has a lower edge set by cheaper names and an upper edge set by far users, and the two are defined by the signs of ΔL and δ\_net, not by one ratio.

**Per-event advantage.** For a competitor ω let R\_t(·) be the broadcast bill and ℓ\_t(·) the sink codelength at event t. The invariant quantity is the total operating advantage

```latex
a_t(\omega;P_r)=\bigl[R_t(P_r)+\ell_t(P_r)\bigr]-\bigl[R_t(\omega)+\ell_t(\omega)\bigr],
```

which makes no assumption about which local broadcasts ω keeps. For a nested extension ω = P\_r + e it reduces to a\_t = δ\_t − r\_far,t, the residual drop minus the extra far bill, which is the δ\_net of earlier drafts; that form is exact only there, and it is where named exceptions live. Write ā^(N) for the Cesàro mean. The pairwise gap is

```latex
\Delta\mathcal{J}_N(\omega)=\Delta L(\omega)+\Delta\operatorname{Reg}_N(\omega)-\sum_{t=1}^N a_t(\omega;P_r),
```

with ΔL(ω) = L(ω) − L(ω\_r). Write the cumulative gap as

```latex
G_N(\omega)=\Delta L(\omega)+\Delta\operatorname{Reg}_N(\omega)-\sum_{t=1}^{N}a_t(\omega;P_r).
```

G\_N(ω) > 0 means the ball beats ω at horizon N. The horizons below are defined from G\_N directly, so they need no stationarity and handle front-loaded or oscillating advantages without a separate caveat. The sign of ΔL and of the eventual a decides which edge a competitor can belong to, as the table shows for the stationary case.

| ΔL(ω) | eventual a(ω) | Support | Who wins at small N | Who wins at large N | Edge |
| --- | --- | --- | --- | --- | --- |
| > 0 | > 0 | outside | ball | ω | upper, N\_c^(0) = ΔL / a |
| = 0 | > 0 | outside | tie, then ω | ω | upper, N\_c^(0) = ΔReg / a |
| ≥ 0 | ≤ 0 | any | ball | ball | none, ω never crosses |
| ≥ 0 | any | inside | ball weakly | ball weakly | none, by protocol inclusion |
| < 0 | > 0 | any | ω | ω | none, ω always wins; excluded by A3 |
| < 0 | < 0 | any | ω | ball | lower, N\_c^(0) = ΔL / a |

**Lower edge.** The ball is in only after the last cheaper name has been overtaken and stays overtaken:

```latex
N_{\mathrm{lo}}=\inf\Bigl\{N:\ G_{N'}(\omega)\ge 0\ \ \forall N'\ge N,\ \forall\omega\ \text{with}\ \Delta L(\omega)<0\Bigr\},
```

and N\_lo = ∞ if the set is empty. If some cheaper competitor has G\_N(ω) < 0 for arbitrarily large N, the ball never beats it and the window is empty; A3 is the hypothesis that rules this out, for inside support (its reading A0) and for every other support alike. With one cheaper stationary competitor this reduces to the earlier N\_lo = ΔL\_loc / δ\_loc.

**Regret.** Regret is a shift of ΔL, not a fifth regime. A kind-1 listener whose encoder fits k parameters moves its crossing by about (k/2) log N, the same order as log n, so on a short run regret can reorder the upper edge. Report ΔL with regret included at the run's N.

**Upper edge.** The window closes at the first horizon where some outside competitor whose name is no shorter than the ball's is pairwise cheaper:

```latex
N_{\mathrm{hi}}=\inf\Bigl\{N:\ \exists\,\omega\ \text{outside}\ P_r\ \text{with}\ \Delta L(\omega)\ge 0\ \text{and}\ G_N(\omega)<0\Bigr\},
```

and N\_hi = ∞ if no such competitor exists. The infimum must include ΔL = 0: an outside rule whose program costs exactly the embedding, with a positive operating gain, beats the ball once its gain clears regret, and no inside argument covers it. Inside competitors with ΔL ≥ 0 are excluded from the set because the ball can run their protocol, so they never have G\_N < 0.

**Corollary (stationary ratios).** If a\_t(ω) → a(ω) in Cesàro mean and ΔReg\_N(ω) = o(N), then the crossing of G\_N(ω) is at N\_c(ω) = ΔL(ω)/a(ω) + o(N\_c); for O(log N) regret the correction is O(log N\_c / a). The zero-regret leading term N\_c^(0) = ΔL/a is what the sign table and the regime table display. On a short run the regret shift is the same order as a kind-1 name, log n, so N\_lo and N\_hi should be computed from G\_N, not from the ratio.

A1\* is used only to lower-bound N\_hi, and only for nested far extensions of the ball protocol, where the data-processing comparison of Section 4 is valid: such an extension can save at most S Σ\_k ε\_k(r) nats per event on the sink code, so a far emission whose bill exceeds that has a ≤ 0 and does not bind, and a kind-1 extra recipient has N\_c ≥ ΔL / ε\_k(r), with equality only if its gain meets the cap. Exact screening gives N\_hi = ∞ for both kinds; approximate screening lets kind-1 recipients cross at or after log n / ε.

## 7. The locality window

**Theorem (locality window, exact version).** Assume site-wise log loss at the sink, broadcast delivery with no self-delivery and no relay, coefficient 1 on every codelength, A1\*, and A3. If N\_lo < N\_hi, then for every horizon N\_lo < N < N\_hi and every tolerance τ > 0,

```latex
P_r\in\mathcal{C}^\star_\tau(N).
```

The theorem is immediate from the horizon definitions and Lemma 2; the ratios of Section 6 are its stationary corollary. The window is nonempty only if local broadcast reuse per naming bit exceeds far broadcast reuse per naming bit, and the ball eventually beats every cheaper predicate. Locality is this window. It is not a phase the system reaches and keeps.

*Proof.* Take ω ≠ P\_r in the class and apply Lemma 2.

1. If ω is inside (supp Π\_ω ⊆ P\_r) with ΔL ≥ 0, the ball weakly dominates it at every N. If ΔL < 0, then N > N\_lo gives G\_N(ω) ≥ 0 by definition of N\_lo, and A3 is what makes N\_lo finite: the ball beats or ties it.
2. If ω is outside, it is a far user, hubs and trees included. If ΔL(ω) < 0, then N > N\_lo gives G\_N(ω) ≥ 0, with A3 supplying finiteness of N\_lo. If ΔL(ω) ≥ 0, then N < N\_hi gives G\_N(ω) ≥ 0 by definition of N\_hi, the equal-name case included. No separate ΔL = 0 argument is needed.
3. There is no third case. A star or separator tree is an outside competitor and was priced in step 2 by its name and its a(ω).

So no competitor has smaller J\_N than the ball inside the window, and P\_r is a minimizer. Inside competitors with ΔL = 0 tie, so membership holds for every τ > 0 while uniqueness does not. Above N\_hi some far competitor becomes pairwise cheaper than P\_r and is therefore eligible for global optimality; that does not by itself put it in C\*\_τ(N), since a third program can beat both. P\_r may or may not remain a member. Below N\_lo some cheaper predicate has ΔJ\_N < 0 and the ball is out. ∎

**Two remarks.**

- The packing cap is not the membership argument. A far competitor under the cap can beat the ball by up to S N Σ\_k ε\_k and is not dominated. Using A1\* alone would give a tolerance version, P\_r ∈ C\*\_{τ\_N}(N) for N > N\_lo with τ\_N linear in N. That version is not stated. Below N\_hi no far competitor beats the ball pairwise, so an arbitrary τ suffices.
- A1\* enters only through N\_hi, and only for nested far extensions of the ball protocol. Its job is to say which such extensions can have a > 0, and to bound how early kind-1 recipients can cross. The theorem itself exhausts competitors through G\_N and does not need A1\* for that.

## 8. Regimes and nested permissions

The leading-order crossing ΔL / a sorts nested far extensions into four regimes; clearing it makes an exception pairwise eligible against the ball, and within the nested family it then coexists with the ball rather than evicting it.

| Regime | ΔL | a | N\_c^(0) | Example |
| --- | --- | --- | --- | --- |
| No net advantage | any | ≤ 0 | ∞ | exact screening; every single-recipient new emission |
| Extra recipient | O(log n) | ≤ ε\_k(r), no bill | ≥ log n / ε | one far site reads an existing ball broadcast |
| Sparse multi-receiver emission | O(log n) | O(1) | O(log n) | a shortcut broadcast with several customers |
| Extensive bespoke wiring | n log n | n ε | (log n) / ε | long-range edges at every site; the n cancels |

The second and third rows can fall before N\_lo. An exception can be worth naming before the ball has paid for itself. Stage order is distributional, not universal.

**Nested permissions.** Exceptions e\_j have their own horizons N\_c(e\_j) = ΔL\_j / a\_j, where for a nested extension a\_j = δ\_j − r\_far,j exactly. Inside or above the window the τ-optimal set can contain the chain

```latex
P_r\subset P_r+e_1\subset P_r+e_1+e_2\subset\cdots
```

as coexisting members. Clearing N\_c(e\_j) makes e\_j pairwise eligible against the ball, not globally optimal; the chain is guaranteed only when comparison is restricted to the nested family P\_r + E. Within that family a shortcut that has amortized its name is not evicted, because removing it re-raises the residual by its gain while saving only a name already paid. Small-world structure is this chain, not a transition from local to nonlocal. If some N\_c(e\_j) < N\_lo, that exception is purchased against a cheaper backbone than P\_r, or the pure-ball window is empty.

A finite front-loaded burst contributes O(1) cumulative benefit and amortizes no fixed name. A competitor with Σ\_t δ\_net,t = O(1) never crosses.

## 9. What is returned, and how to test it

Minimum description length buys reusable broadcast. It does not buy geometry. A metric ball is selected only inside the window where one emission has enough nearby customers to pay for the permission that names them.

| Outcome | Predicate | Condition |
| --- | --- | --- |
| Nothing local yet | P\_∅ or a shorter rule | N < N\_lo |
| Geometry | P\_r | N\_lo < N < N\_hi |
| Geometry plus exceptions | P\_r ∪ E | eligible after each N\_c(e); globally selected only after full-class comparison |
| Hub | P\_h | A3 fails for the star: a global common cause gives the hub broadcast a(P\_h) ≥ 0 with a shorter name |
| Hierarchy | P\_T | A3 fails for the tree: a separator program shorter than the embedding with a(P\_T) ≥ 0 |
| New single-recipient far emission | never | δ\_net ≤ 0 by Lemma 1 |
| Far extra recipient | P\_r ∪ {i} | N ≥ ΔL / ε\_k(r), later if its gain is below the cap; never if ε\_k(r) = 0 |

**Empirical protocol.** Score the predicate class, not a fitted radius. Candidates are {P\_∅, P\_r, P\_h, P\_T, P\_{r,E}}. For each (n, N) log L, regret including encoder parameters, broadcast bill, sink codelength, J\_N, and C\*\_τ(N).

1. **Finite-range local family.** Run two sub-families. (a) Exact screening, ε = 0: N\_hi = ∞, P\_r enters at N\_lo and stays, and no kind-1 listener ever enters. (b) Approximate screening, ε > 0: a kind-1 listener enters no earlier than ΔL / ε\_k(r) plus regret, which need not lie beyond the run, and later if its gain misses the cap. Compute that lower bound before the run and check that no listener enters before it.
2. **Local plus sparse multi-receiver shortcuts.** Compute each N\_c(e\_j). Prediction, within the nested candidate family P\_r + E: P\_r remains in the set while each e\_j joins at its own N\_c, including the case where an exception precedes the ball. Outside that family the construction must guarantee that no third rule dominates both, or the prediction is only eligibility.
3. **Local plus a single-recipient shortcut emission.** Prediction: the new emission never enters at any N. This is the sharp falsification target, and it applies only to a new emission. A name-only listener of an existing broadcast is predicted to enter at its own N\_c; running that case as if it should never enter would reject a true instance.
4. **Latent hierarchy.** Prediction: P\_T. This is a failure of A3, not of the theorem; log the tree's name and its a(P\_T) to confirm which.
5. **Global common cause.** Prediction: P\_h, and A3 fails measurably as Σ\_i I(X\_i; X\_h) grows past the ball's net value.
6. **Non-embeddable dependence graph.** Prediction: P\_r does not enter because the class offered it.

Measured transitions should land on the computed horizons. A transition that lands elsewhere falsifies the sign analysis of Section 6 before it falsifies the theorem.

## 10. Statements

Sink decodes site-wise. Each site emits one message from its own observation; no self-delivery, no relay. An emission costs once and may be used by every permitted recipient. Coefficient 1:

```latex
\mathcal{J}_N=L+\operatorname{Reg}_N+R_N+L_{\log}.
```

1. A single-recipient transcript saves at most its own codelength (Lemma 1). A new emission pays only when several receivers share the information it carries.
2. Every competitor is a cheaper name or a far user, hubs and trees among the far users (Lemma 2). The pairwise gap is ΔL + ΔReg\_N − Σ\_t a\_t with a\_t the total per-event operating advantage; δ − r\_far is its exact form only for nested extensions.
3. Under A1\* and A3, if N\_lo < N\_hi, then P\_r ∈ C\*\_τ(N) for every τ > 0 and every N\_lo < N < N\_hi, with

```latex
N_{\mathrm{lo}}=\inf\{N: G_{N'}(\omega)\ge 0\ \forall N'\ge N,\ \forall\omega:\Delta L<0\},\qquad N_{\mathrm{hi}}=\inf\{N: \exists\,\omega\ \text{outside},\ \Delta L\ge 0,\ G_N(\omega)<0\},
```

4. with G\_N = ΔL + ΔReg\_N − Σ\_t a\_t the cumulative gap. Under stationary advantage and o(N) regret, the crossings are N\_c = ΔL/a + o(N\_c). A1\* only lower-bounds N\_hi, for nested far extensions of the ball protocol, by capping their sink savings at S Σ\_k ε\_k(r) nats per event. It is not a growing tolerance, and the theorem does not use it to exhaust competitors.
5. A far extra recipient of an existing broadcast enters no earlier than ΔL / ε\_k(r), about log n / ε, and later if its gain falls short of the cap. A new single-recipient far emission never enters. Crossing a pairwise horizon makes a competitor eligible, not a member of C\*\_τ(N).

Communication pays only when a broadcast is informative to several receivers. Locality is where common information lives. Geometry is the permission under which that reuse is local, and only while the horizon sits between amortization of the ball's name and the first far broadcast that has paid for its own.
