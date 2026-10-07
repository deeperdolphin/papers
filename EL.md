# Emergent Locality as Minimum-Description Communication

## 1. Model

A permission predicate is a sparsity pattern for the predictors: site i may be predicted from exactly the sites it is allowed to hear. An MDL learner pays for a sparsity pattern by naming it and by the parametric complexity of the predictor class it induces, and it earns the pattern back only through reuse, because under coefficient 1 positive communication value requires reuse across receivers (Lemma 1); reuse is necessary, not sufficient, since the summed predictive information must still exceed the message entropy. A learner choosing from a class that contains a metric ball selects the ball only inside a window of horizons: early, some highly regular dense patterns, the complete predicate above all, are cheap to name before their induced class complexity dominates; late, their far information outruns that complexity. The ball holds the middle because its induced class has n·vol(r) parameters against n² for the complete predicate; on operating cost the dense predicate is the better code, a(P\_full) ≥ 0 by protocol inclusion, and it loses only on the class it induces. What is emergent is the window and the nested-exception chain inside it, not geometry itself: the theorem does not derive the ball, it prices it against everything else in the class.

The hypotheses are H1 (far information is screened through the boundary broadcasts), H2 (every competitor that wins early is overtaken, uniformly over the class), and, for the unrestricted dense competitor only, H1^sup (screening holds uniformly over message encoders). Section 4 says why H2 can hold for a ball, and Section 9 marks every outcome where it fails.

**Sites and permissions.** Let V\_n = {1, …, n}. A structural hypothesis is a program ω = (M, φ, q) with placement φ : V\_n → M and permission predicate

```latex
P_\omega(i,j)=q\bigl(\phi(i),\phi(j)\bigr)\in\{0,1\},\qquad P_\omega(j,j)=0.
```

The diagonal is excluded. A site may never use its own broadcast.

**Sink and broadcasts.** There is a sink that decodes each site's observation site-wise under logarithmic loss. Site j may emit one message M\_j per event, a function of its own observation only (no relay: a message never depends on received broadcasts). Emission costs the message codelength once. Every site i with P(j, i) = 1 may use M\_j; delivery to a permitted recipient costs nothing. Point-to-point is the special case of one recipient.

Site-wise decoding is the modelling choice everything rests on. With a joint decoder, distributed source coding can exploit inter-site correlation at the joint-code level, which destroys the site-wise broadcast accounting on which the results below depend. Site-wise decoding is the right model for parallel per-site predictors with bounded memory and latency, where each site's next-step code is formed from what that site has received.

**Objective.** For N reuse events,

```latex
\mathcal{J}_N(\omega,\Pi)=L(\omega)+\operatorname{COMP}_N(\omega)+R_N(\Pi\mid\omega)+L_{\log}(D_{1:N}\mid\Pi,\omega),
```

with coefficient 1 on every term. L(ω) = L(M) + L(φ | M) + L(q | M, φ) names the permission program and is paid once. COMP\_N(ω) is the stochastic complexity, the minimax regret at horizon N, of the predictor class the permission induces, charged to the predicate whether or not a particular protocol uses its inputs. It is a property of the predicate, not of the fitted protocol; charging the fitted protocol instead would let a dense permission run a sparse protocol at sparse cost and dominate every sparser predicate outright. R\_N = Σ\_t R\_t is the broadcast bill. L\_log is the sink's site-wise codelength given delivered messages. Statements are in expectation under the data-generating distribution.

**Predictor family.** The scaling of COMP\_N with the permission has to come from a stated family; an arbitrary function of k discrete inputs has a class that grows exponentially in k, and then no dense-versus-local comparison follows. Split the complexity into predictor and encoder parts, k(P) = k\_pred(P) + k\_enc(P). Fix a parametric family in which each permitted directed edge (j, i) contributes a parameter block of bounded dimension d to site i's predictor: additive or generalized-linear predictors, exponential-family conditionals with per-edge sufficient statistics, or any family with that per-edge structure. Each sender emits one receiver-independent broadcast M\_j = f\_j(X\_j) from a fixed-dimensional encoder, so k\_enc(P) = O(n) and adding a recipient adds no encoder parameter. The dense penalty comes from the predictor class alone. Then

```latex
k_{\mathrm{pred}}(P)=d\,|P|+O(n),\qquad k_{\mathrm{enc}}(P)=O(n),\qquad \operatorname{COMP}_N(P)=\tfrac{k(P)}{2}\log N+O(k(P))\ \ (N\gg k(P)),
```

so that

```latex
\operatorname{COMP}_N(P_{\mathrm{full}})-\operatorname{COMP}_N(P_r)\approx\tfrac{d}{2}\bigl(n^2-n\,\mathrm{vol}(r)\bigr)\log N .
```

For N below k(P) the predictor contribution to the minimax regret is bounded by the data's codelength under a uniform code, at most N·n·log|A| for finite alphabet A; the encoder contribution needs its own finite-alphabet bound, C\_enc(N, P), and the displayed bound is for the predictor part. Either way it is linear in N, the asymptotic formula overstates it there, and this matters for dense predicates with k \~ d n² and for where their initial run ends. Every complexity claim below is for this family; a family without per-edge structure needs its own COMP\_N and may change the horizons.

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

Positive communication value therefore requires reuse across receivers. Reuse is necessary and not sufficient: the quantity that sets the value is multi-receiver predictive common information, the sum in v(M\_j), which must exceed the message entropy. A ball is the permission under which one emission has many nearby customers.

## 3. Permission classes and two kinds of exception

A short program is a reusable predicate. Shortness does not imply geometry: a star, a tree and a ball can all have description O(log n). Selection is by total codelength.

| Class | Predicate | Name | Delivery |
| --- | --- | --- | --- |
| Empty | P\_∅ | O(1) | The sink decodes each site from its own past only |
| Complete | P\_full ≡ 1, off-diagonal | O(1) | Every emission is delivered to every other site; contains every other class |
| Ball | P\_r(i, j) = 1\[d(φ(i), φ(j)) ≤ r\] | O(n log n) for the placement φ, less if sites carry coordinates | One emission is delivered throughout the ball |
| Star | P\_h(i, j) = 1\[i = h or j = h\] | O(log n) | The hub emission is a global broadcast; each spoke emission has one customer (no relay) |
| Hierarchy | P\_T(i, j) = q\_T(i, j) | depends on T | A broadcast goes to a separator's children or up the tree as q\_T specifies |
| Ball with exceptions | P\_{r,E} = P\_r ∪ E | ball plus O(log n) per exception | The ball plus named extras of the two kinds below |

**Two kinds of exception.** Delivery to a permitted recipient is free per event, so an exception can be either of:

1. **Extra recipient.** A far site i is named as one more recipient of a broadcast M\_j the ball already pays for. Cost: a name, ΔL = O(log n), once. Per-event bill: zero. Gain: I(X\_i; M\_j | local broadcasts), which H1 caps at ε\_k(r). Its class complexity grows by one input at one site. Crossing no earlier than ΔL / ε\_k(r), about log n / ε, and later if the gain misses the cap; finite whenever ε\_k(r) > 0.
2. **Extra emission.** A new message with its own bill. By Lemma 1 it has δ\_net > 0 only if it is informative to several receivers.
3. **Global rebroadcast.** One existing ball message M\_j is delivered to every site. Name O(log n), which j, plus "to all"; bill zero; class increment d·n, one block at each of n predictors, so structural cost log n + (dn/2) log N. Gain: that message's total far value, at most E\_r by Lemma 3, and equal to E\_r only if one ball message already carries the system's far information; if that information is spread across emitters, one rebroadcast buys its own share, and the whole tail costs many rebroadcasts or P\_full. This is the cheapest single-message purchase of far information, and it is what free delivery creates. Whether it binds N\_hi before the listener depends on its realized share, which must be estimated, not assumed.

The statement "a point-to-point far edge never enters" holds for kind 2 with one recipient, and not for kinds 1 or 3. If far delivery should itself cost something, charge delivery per recipient or by distance; that makes geometry a physical cost rather than a naming convenience. The present note charges delivery nothing, and the results are stated for that model.

**The complete predicate is the competitor that decides the thesis.** With free delivery, P\_full has an O(1) name, shorter than the ball's placement. Every ball protocol is admissible under P\_full, so protocol inclusion runs against the ball: a(P\_full; P\_r) ≥ 0 at every horizon. If complexity were charged to the fitted protocol, P\_full could run the ball's protocol at the ball's cost and dominate outright. That is why COMP\_N is charged to the predicate: in the per-edge family of Section 1, P\_full induces k \~ d n² parameters against d n vol(r) for the ball, so COMP\_N(P\_full) − COMP\_N(P\_r) ≈ (d/2)(n² − n vol(r)) log N, and the complete permission pays that whether or not any protocol uses the inputs. The thesis is then one claim: the permission is the predictor's sparsity pattern, and MDL pays for sparsity patterns by naming them and charging the class they induce. Two consequences for P\_full. Early it beats the ball, and the question is for how long. For N below k the complexity of a saturating class is at most the data's own codelength, N·n·log|A| for the predictor part plus a finite-alphabet encoder term. That is a ceiling: it says how cheap P\_full is allowed to be, so it guarantees that P\_full wins at least until N·n·log|A| reaches the ball's name plus (d n vol(r)/2) log N, around N of order (log n)/log|A|. The run ends only when a lower bound on COMP\_N(P\_full) clears the ball's name, the ball's class complexity, and the cumulative operating gap, which protocol inclusion makes favor P\_full. So the run ends at that scale only if the saturated-class regret is Θ(N·n·log|A|), not merely bounded by it; otherwise the ceiling gives "no earlier than" and nothing more. Compute COMP\_N(P\_full) for N < k, with a matching lower bound, in the stated family rather than from either asymptotic formula. Late, under approximate screening, its far gain outruns (d/2) n² log N and it is an upper-edge competitor, no earlier than (d n²/2E\_r) log N, which is (n²/ε) log N under summable decay and (d n vol(r)/2ε) log N under a per-interior cap. The H1 cap alone gives that bound only for the nested sub-protocol that keeps the ball's messages; the optimal P\_full protocol can re-encode every message to serve far receivers, which changes the boundary broadcasts. The general crossing needs H1^sup of Section 4, screening uniform over message encoders. Under H1^sup the same crossing holds for the optimized P\_full; without it, the headline prediction is a bound for the nested sub-protocol and nothing more.

## 4. Assumptions

Two hypotheses carry the theorem: far information is screened through the boundary broadcasts (H1, with its cover form H1\*), and every competitor that wins early is overtaken, uniformly over the class (H2). A third, H1^sup, is needed only to price the unrestricted complete predicate. A remark gives H2's inside reading, which is why it can hold for a ball. Hubs, hierarchies, and the complete predicate are ordinary competitors priced by H2 and the horizons.

**Remark (inside reading of H2; not a separate hypothesis).** The empty permission and every smaller radius are shorter names with fewer parameters, so H2 already requires a(P\_∅; P\_r) < 0 and a(P\_{r'}; P\_r) < 0 for r' < r. That is δ\_loc > 0: the ball's broadcasts have positive net value over the best cheaper inside protocol. By Lemma 1 it can hold only if ball broadcasts have several customers who share information one message can carry. This paragraph is the reason H2 is satisfiable for a geometric rule against sparse competitors, not an assumption the theorem lists. Against the complete predicate the mechanism is different, and Section 3 states it: class complexity, not reuse.

**H1 (boundary screening, in the conditioning the protocol uses).** Let A\_1, …, A\_m be disjoint interiors whose radius-r neighborhoods meet only on designated boundaries, and write X\_far,k for the variables outside N\_r(A\_k). Under P\_r the sink's code for A\_k conditions on the boundary broadcasts B\_k, the messages the ball protocol delivers from the boundary of A\_k. Those are functions of the boundary variables, not the boundary variables themselves, and conditional mutual information is not monotone in the conditioning set, so a cap stated against the boundary variables would not bound anything the sink does. Assume instead

```latex
I\bigl(X_{A_k};X_{\mathrm{far},k}\mid B_k\bigr)\le\varepsilon_k(r),\qquad B_k=\{M_j:\ j\in\partial_r A_k\}.
```

For a far message M = f(X\_far,k) added to the ball protocol, data processing gives I(X\_{A\_k}; M | B\_k) ≤ I(X\_{A\_k}; X\_far,k | B\_k) ≤ ε\_k(r), so the advantage of far broadcasts on the packed interiors is at most Σ\_k ε\_k(r) nats per event. This comparison conditions on the same B\_k on both sides, which is why it is stated for nested far extensions of the ball protocol: a competitor that removes or alters local messages changes B\_k, and the bound does not transfer. The admissible coder is the boundary coder.

**H1\* (shift cover).** One packing does not price boundary or leftover sites. Assume a shift cover of S packings, each satisfying H1, such that every site is interior in at least one. By a union bound over the cover,

```latex
\Delta L_{\log}^{\mathrm{far}}\le S\,N\sum_k\varepsilon_k(r)+\Delta\operatorname{COMP}_N,
```

where ΔCOMP\_N is the class-complexity difference of the extension, encoder parameters included. Write E\_r = S Σ\_k ε\_k(r) for the total far information per event; Lemma 3 below says no admissible protocol gains more than E\_r from far delivery. Two scalings of E\_r are consistent with H1, and the horizons differ by a factor of n between them, so the paper must say which it is using:

- **Summable decay:** Σ\_k ε\_k < ∞ as m grows, E\_r = O(ε). Total far-side residual is O(1) for the whole system. This is the strong form, and it typically fails at criticality, where conditional mutual information across a finite boundary decays as a power law and the sum over m \~ n / vol(r) blocks diverges.
- **Per-interior cap, no decay:** ε\_k ≤ ε for each of m \~ n / vol(r) interiors, E\_r = Θ(nε / vol(r)). This is what "a(P\_full) ≤ C n ε" assumes.

The horizon theorem in Section 7 is stated in E\_r so that it holds in either regime; the specialization to each is given there.

**Exact screening.** H1 conditions on the boundary broadcasts B\_k, which are functions of the boundary variables. A Markov field or a local Hamiltonian gives X\_A ⊥ X\_far | X\_∂, not X\_A ⊥ X\_far | B\_k, and a lossy boundary message need not preserve the separation. Exact screening, ε = 0, therefore holds for such data only when the boundary broadcasts retain a sufficient boundary statistic for the interior; otherwise H1 holds with some ε > 0 set by what the messages discard. Under exact screening the window is one-sided, N\_hi = ∞, and locality once bought is kept; the transient reading of the window applies to approximately screened data, including Markov data whose boundary messages are compressed.

**H1^sup (encoder-uniform screening).** H1 and H1\* bound the far-side advantage of a competitor that keeps the ball's messages. A competitor free to re-encode every message, the optimized complete predicate above all, changes the boundary broadcasts and escapes that bound. Assume, uniformly over admissible message tuples M = (M\_j),

```latex
\sup_{\mathbf M\in\mathfrak M(P)}\ \sum_{i}I\bigl(X_i;\ \mathbf M_{\mathrm{far}(i)}\mid \mathbf M_{\mathrm{loc}(i)}\bigr)\le S\sum_k\varepsilon_k(r),
```

where 𝔐(P) is the admissible set: no-relay, no-self-delivery message tuples, each M\_j a function of X\_j alone, delivered under P; M\_loc(i) are the messages i receives from inside its ball and M\_far(i) the rest. Call the right-hand side E\_r. It is a hypothesis about the data, not a consequence of H1, and it is used in exactly one place: the upper-edge crossing of the optimized P\_full.

**Lemma 3 (local projection).** Let Π be any protocol admissible under P\_full. Its local projection π\_r Π keeps every message encoder M\_j = f\_j(X\_j), hence every transmitted message and the same bill R\_N, and delivers each message only to recipients permitted by P\_r. Then π\_r Π is admissible under P\_r, so the ball's optimal protocol satisfies OpCost(P\_r\*) ≤ OpCost(π\_r Π), and therefore

```latex
a(\Pi;P_r^\star)=\operatorname{OpCost}(P_r^\star)-\operatorname{OpCost}(\Pi)\le\operatorname{OpCost}(\pi_r\Pi)-\operatorname{OpCost}(\Pi)=\sum_i I\bigl(X_i;\mathbf M_{\mathrm{far}(i)}\mid\mathbf M_{\mathrm{loc}(i)}\bigr)\le E_r .
```

The middle quantity is the value of the extra far deliveries with the encoders held fixed, which is exactly what H1^sup bounds; the ball's optimality handles the comparison to its own messages. The bridge Π\_full → π\_r Π\_full → Π\_r\* removes the need to compare a re-encoded dense protocol to the ball's particular messages. Under H1^sup, a(P\_full; P\_r) ≤ E\_r, and the P\_full crossing of Section 6 follows.

**Hubs, hierarchies, and the complete predicate (no separate assumption).** A star, a separator tree, or the complete predicate has support outside P\_r, so Lemma 2 places it with the far users, and Section 6 prices it by its per-event advantage a(ω) and its structural cost ΔL̃\_N(ω). If that name is shorter than the ball's, H2 requires a(ω) < 0. If it is no shorter, the competitor sits on the upper edge and enters N\_hi only when its cumulative advantage clears the name. With no relay a hub can broadcast only its own observation, so a sufficient condition for the star to satisfy H2 is a pairwise sum: sup over message encoders M\_h of Σ\_i I(X\_i; M\_h | local broadcasts) − H(M\_h) is less than the ball's net value v\_ball. That is "no low-dimensional global common cause," stated as a mutual-information condition. For the complete predicate the structural cost is complexity-dominated once N is of order log n and above, and H2 is silent on it there; on the short early range Section 3 describes, it is a cheaper competitor that beats the ball, and that run ends no later than the lower edge.

When the hub sum exceeds v\_ball, the star has a cheaper name and a(P\_h) ≥ 0, H2 fails, and the window is empty. That is the correct outcome: a global common cause is a better explanation than geometry.

**H2 (every initial winning run ends, uniformly).** Write ΔL̃\_N(ω) = ΔL(ω) + ΔCOMP\_N(ω) for the structural cost of ω against the ball at horizon N, and G\_N(ω) = ΔL̃\_N(ω) − Σ\_{t≤N} a\_t(ω; P\_r) for the cumulative gap, G\_N(ω) > 0 meaning the ball beats ω at N. For each competitor let T\_lo(ω) be the end of its initial winning run, the largest N such that G\_{N'}(ω) < 0 for every N' ≤ N, with T\_lo(ω) = 0 if the ball wins from the first event (Section 6 states this with its partner T\_hi(ω), the first return). A competitor wins early if T\_lo(ω) > 0; these are the structures with lower early cost: the empty permission, smaller radii, cheap nonmetric rules, stars, trees, and the complete predicate before its class complexity bites. H2 is the single statement

```latex
\sup_{\omega}T_{\mathrm{lo}}(\omega)<\infty .
```

It says every initial winning run ends and the ends are bounded over the class; equivalently, N\_lo < ∞. H2 is a uniform lower-edge finiteness assumption, not a derivation of it. It says nothing about returns: a competitor may win early, be overtaken, and win again later, as the complete predicate does under approximate screening; that return is T\_hi's business and belongs to the upper edge. The pairwise version, each run ends, is not enough over an infinite class, because the ends can be unbounded while each is finite. In the stationary case H2 reads a(P; P\_r) < 0 for every P with lower structural cost, with the crossings ΔL̃/a bounded over the class.

The inside reading of H2 covers the empty permission and smaller radii, and Lemma 1 says why it can hold there. H2 also covers a shorter nonmetric rule, a star whose name is one site index, and a hierarchy whose separator program is shorter than the embedding. It is strong: a tree with a shorter program and no worse per-event rate is excluded by fiat, and the outcome table marks where that happens. H2 is the one-line form of "the ball is the cheapest sufficient rule," and it is a hypothesis, not a consequence of anything above. The complete predicate is an early winner on a short range, of order log n events, and H2 asks only that the ball overtake it there; its late return is the upper edge's business.

## 5. Exhaustion lemma

Every competitor to the ball falls on exactly one side of the window, so the theorem faces each one once.

**Lemma 2 (exhaustion).** Fix a competitor ω with optimal admissible protocol Π\_ω. Exactly one of the following holds.

1. **Inside.** supp Π\_ω ⊆ P\_r. Then the ball can run Π\_ω unchanged, so its bill and residual are no larger: a(ω; P\_r) ≤ 0 at every horizon. Names and class complexities differ, and a smaller support has both a shorter name and a smaller class, so ΔL̃\_N(ω) < 0 is the normal case. The competitor can beat the ball only through that smaller structural cost, never through operating cost; it is a genuine lower-edge competitor that the ball must beat on operating cost, which is H2's inside reading. If ΔL̃\_N(ω) ≥ 0, the ball weakly dominates ω at that N, since a ≤ 0 and the structural gap is nonnegative.
2. **Outside.** Π\_ω uses permission outside P\_r: a far recipient of an existing emission (kind 1) or an emission delivered beyond the ball (kind 2). These competitors belong to the N\_hi analysis if their structural cost ΔL̃\_N is no lower than the ball's, and to H2 if it is shorter, with the per-event advantage a(ω) of Section 6 defined against the ball. Stars, separator trees, and the complete predicate are in this case.

A hub needs no separate family. Its spoke-to-hub channels are single-recipient and never pay (Lemma 1); its hub emission is a case-2 broadcast priced by a(P\_h), and its short name puts it under H2. The complete predicate needs none either: protocol inclusion makes a(P\_full) ≥ 0, so it beats the ball wherever its structural cost ΔL̃\_N is negative or its cumulative gain clears a positive one. It is priced at both ends of the window.

*Proof.* The two cases are complementary by definition of support. In case 1, running Π\_ω under P\_r is admissible and costs the same bill and residual, so the operating advantage of ω is at most zero and the gap is the structural difference ΔL̃\_N(ω) minus a nonpositive sum. In case 2 nothing is assumed about which local broadcasts the competitor keeps, removes, or alters. Its gap against the ball is ΔL(ω) + ΔCOMP\_N(ω) − Σ\_t a\_t(ω; P\_r), with a\_t the total per-event operating advantage of Section 6, by definition of J\_N. ∎

Lemma 2 sorts competitors; it does not price them. Inside competitors are priced by H2 (its inside reading) and the sign table, outside competitors by H2 when their structural cost is lower and by N\_hi when not. The far user with a shorter name and nonnegative advantage is seen only by H2, which is why H2 is a separate hypothesis. With it, "no other family remains" is a deduction.

## 6. Horizons

The window is an open interval between a supremum of pairwise last-crossings and an infimum of pairwise first-returns; the signs of a competitor's structural cost and advantage say which edge it can set, and the ratios below are the stationary shorthand.

**Per-event advantage.** For a competitor ω let R\_t(·) be the broadcast bill and ℓ\_t(·) the sink codelength at event t. The invariant quantity is the total operating advantage

```latex
a_t(\omega;P_r)=\bigl[R_t(P_r)+\ell_t(P_r)\bigr]-\bigl[R_t(\omega)+\ell_t(\omega)\bigr],
```

which makes no assumption about which local broadcasts ω keeps. For a nested extension ω = P\_r + e it reduces to a\_t = δ\_t − r\_far,t, the residual drop minus the extra far bill, which is the δ\_net of earlier drafts; that form is exact only there, and it is where named exceptions live. Write ā^(N) for the Cesàro mean. The pairwise gap is

```latex
\Delta\mathcal{J}_N(\omega)=\Delta L(\omega)+\Delta\operatorname{COMP}_N(\omega)-\sum_{t=1}^N a_t(\omega;P_r),
```

with ΔL(ω) = L(ω) − L(ω\_r). Write the cumulative gap as

```latex
G_N(\omega)=\Delta L(\omega)+\Delta\operatorname{COMP}_N(\omega)-\sum_{t=1}^{N}a_t(\omega;P_r).
```

G\_N(ω) > 0 means the ball beats ω at horizon N. The horizons below are defined from G\_N directly, so they need no stationarity and handle front-loaded or oscillating advantages without a separate caveat. The sign of ΔL and of the eventual a decides which edge a competitor can belong to, as the table shows for the stationary case.

| ΔL̃\_N(ω) | eventual a(ω) | Support | Who wins at small N | Who wins at large N | Edge |
| --- | --- | --- | --- | --- | --- |
| > 0 for all N | > 0 | outside | ball | ω | upper, N\_c^(0) = ΔL̃ / a |
| < 0 early, > 0 late (complexity-dominated) | ≥ 0 | outside, e.g. P\_full | ω, then ball | ω | both: sets N\_lo early, N\_hi late under approximate screening; never returns under exact screening |
| = 0 | > 0 | outside | tie, then ω | ω | upper, N\_c^(0) = ΔCOMP / a |
| ≥ 0 | ≤ 0 | any | ball | ball | none, ω never crosses |
| ≥ 0 | ≤ 0 (forced) | inside | ball weakly | ball weakly | none: a ≤ 0 by protocol inclusion and the structural gap is nonnegative |
| < 0 | ≤ 0 (forced) | inside | ω | ball if a < 0 | lower, N\_c^(0) = ΔL̃ / a; H2's inside reading requires a < 0 |
| < 0 | > 0 | outside | ω | ω | none, ω always wins; excluded by H2 |
| < 0 | < 0 | outside | ω | ball | lower, N\_c^(0) = ΔL̃ / a |

**Pairwise crossings.** For each competitor ω define the end of its initial winning run and its first return:

```latex
T_{\mathrm{lo}}(\omega)=\sup\{N:\ G_{N'}(\omega)<0\ \text{for all}\ N'\le N\},\qquad T_{\mathrm{hi}}(\omega)=\inf\{N>T_{\mathrm{lo}}(\omega):\ G_N(\omega)<0\},
```

with T\_lo(ω) = 0 if the ball beats ω from the first event, T\_lo(ω) = ∞ if ω beats the ball at every horizon, and T\_hi(ω) = ∞ if ω never returns. T\_lo measures an initial contiguous losing interval, and every later negative episode is assigned to T\_hi; "lo" and "hi" are the edges of the first interval on which the ball beats everyone, not monotone pairwise crossings. These are pairwise objects, so pairwise hypotheses bound them: H2 says T\_lo(ω) < ∞ for every competitor with lower structural cost, and H1\* lower-bounds T\_hi(ω) for nested far extensions.

**Lower edge.** The lower edge is the last horizon at which any early winner still beats the ball:

```latex
N_{\mathrm{lo}}=\sup_{\omega:\ T_{\mathrm{lo}}(\omega)>0}T_{\mathrm{lo}}(\omega),
```

with N\_lo = 0 if no competitor ever wins early. The early winners are the structures with lower cost on an initial range: the empty permission, smaller radii, cheap nonmetric rules, and dense predicates before their class complexity bites. H2 is exactly the statement that this supremum is finite; it is stated uniformly because each T\_lo being finite does not bound the supremum over an infinite class. With one cheaper stationary competitor the lower edge reduces to the earlier N\_lo = ΔL\_loc / δ\_loc.

**Class complexity.** ΔCOMP\_N is a shift of the structural cost, not a separate regime, but it moves with N and it is large for dense predicates. A kind-1 listener adds one input at one site, about (1/2) log N, the same order as its log n name, so on a short run it can reorder the upper edge. For P\_full the shift is of order (d/2) n² log N once N ≫ d n², and for N < d n² it is at most the data's codelength, N·n·log|A|. That ceiling guarantees P\_full wins at least until about N \~ (log n)/log|A|; where its run actually ends depends on a lower bound on COMP\_N(P\_full), and it ends at that scale only if the saturated regret is Θ(N·n·log|A|). An experiment should expect P\_full to win on an initial range no shorter than that, and should measure where the run ends rather than assume it. Report ΔL̃\_N with COMP evaluated at the run's N.

**Upper edge.** The upper edge is the first horizon at which any competitor beats the ball after its initial run has ended. The infimum ranges over every competitor, inside ones included; nothing in the exact definitions forbids an inside competitor a late return through some finite-N shape of COMP\_N. In the regular parametric regime of the corollary in Section 7 inside competitors never return, and the upper edge is set by outside competitors with eventually positive advantage:

```latex
N_{\mathrm{hi}}=\inf_{\omega}T_{\mathrm{hi}}(\omega),
```

with N\_hi = ∞ if no competitor ever returns. Three return families compete for the infimum, each priced by name plus class increment against a gain Lemma 3 caps: a single listener at ≳ (log n)/ε\_1, with ε\_1 its own far share; a global rebroadcast of one message at ≳ (dn / 2E\_r) log N; the optimized complete predicate at ≳ (d n² / 2E\_r) log N under H1^sup. Which returns first depends on E\_r: with summable decay, E\_r = O(ε), the listener is first and the rebroadcast and P\_full are later by factors of n and n²; with a per-interior cap and no decay, E\_r = Θ(nε / vol(r)), the n cancels in the rebroadcast's bound, (d vol(r) / 2ε) log N, which can precede the listener's (log n)/ε only if the rebroadcast realizes a share of E\_r comparable to the cap; P\_full is then bounded below by (d n vol(r) / 2ε) log N. Nothing forces N\_lo < N\_hi: each ω has T\_hi(ω) > T\_lo(ω), but the supremum of one over the class can exceed the infimum of the other. That is the hypothesis of the theorem, and it has content. The worked example is the complete predicate, which appears in both sets: it wins early on a short initial run, is overtaken when its class complexity grows past the ball's structural cost, and under approximate screening returns when N·a(P\_full) clears that complexity, no earlier than (d n² / 2E\_r) log N, since Lemma 3 under H1^sup gives a(P\_full) ≤ E\_r; it becomes ≍ only with a matching realized gain Θ(E\_r). If a kind-1 listener returns at ΔL / ε before the ball has finished overtaking P\_full, then N\_hi ≤ N\_lo and the window is empty even though H2 holds throughout. Under exact screening with sufficient boundary broadcasts no outside competitor returns and N\_hi = ∞. An outside rule with structural cost exactly zero against the ball has T\_lo = 0 and returns as soon as its gain clears the difference in class complexity.

**Corollary (stationary ratios).** If a\_t(ω) → a(ω) in Cesàro mean and ΔCOMP\_N(ω) = o(N), then the crossing of G\_N(ω) is at N\_c(ω) = ΔL(ω)/a(ω) + o(N\_c); for O(log N) class complexity the correction is O(log N\_c / a). The leading term N\_c^(0) = ΔL̃/a is what the sign table and the regime table display. On a short run the complexity shift is the same order as a kind-1 name, log n, and for dense predicates it is the whole structural cost, so N\_lo and N\_hi should be computed from G\_N, not from the ratio.

H1\* is used only to lower-bound N\_hi, and only for nested far extensions of the ball protocol, where the data-processing comparison of Section 4 is valid: such an extension can save at most S Σ\_k ε\_k(r) nats per event on the sink code, so a far emission whose bill exceeds that has a ≤ 0 and does not bind, and a kind-1 extra recipient has N\_c ≥ ΔL / ε\_k(r), with equality only if its gain meets the cap. Exact screening gives N\_hi = ∞ for both kinds; approximate screening lets kind-1 recipients cross at or after log n / ε.

## 7. The locality window

**Window Lemma (exact).** Assume site-wise log loss at the sink, broadcast delivery with no self-delivery and no relay, and coefficient 1 on every codelength. If N\_lo < N\_hi, then for every horizon N\_lo < N < N\_hi and every tolerance τ > 0,

```latex
P_r\in\mathcal{C}^\star_\tau(N).
```

The window is the open interval between a supremum of pairwise last-crossings and an infimum of pairwise first-returns, so the hypothesis N\_lo < N\_hi is not automatic, and the pairwise hypotheses do the work: H2 makes the lower edge finite, H1\* bounds the upper edge for nested extensions, Lemma 2 and the sign table say which competitors can set each, and the per-edge family of Section 1 fixes how both scale with n, r, d, and ε. The ratios are the stationary corollary. The window is nonempty only if every early winner is overtaken before any far competitor returns; locality is this interval, and it can be empty while every hypothesis holds.

**Theorem (horizon scaling).** This is the substantive result; the lemma above is bookkeeping. In the stationary per-edge family with ΔL\_ball = Θ(n log n), a\_loc = Θ(ng), ΔCOMP at N\_lo of order o(n log n), and H1 with total far information E\_r per event:

- N\_lo = O((log n)/g).
- A single listener returns no earlier than (log n)/ε\_1, with ε\_1 its own far share.
- A global rebroadcast of one ball message returns no earlier than (dn / 2E\_r) log N.
- The optimized complete predicate returns no earlier than (d n² / 2E\_r) log N, under H1^sup via Lemma 3.

N\_hi is the least of these, so the nonemptiness condition is (log n)/g < min over the three, and the three horizons are experimentally distinguishable. All three are lower bounds; which one binds depends on realized shares of E\_r, so equalities need matching lower bounds on realized gains. The condition specializes by regime:

- **Summable decay, E\_r = O(ε):** the listener is first, N\_hi ≳ (log n)/ε, and the condition is g > C·ε. The rebroadcast and P\_full are later by factors of order n and n² respectively, so P\_full returns at (n²/ε) log N, not (n/ε) log N.
- **Per-interior cap, E\_r = Θ(nε / vol(r)):** the n cancels in the rebroadcast's bound, N\_c ≳ (d vol(r) / 2ε) log N, and if the rebroadcast realizes its cap the condition is g/ε ≳ (log n)/(d vol(r) log N). Evaluated at N ≈ N\_lo ≈ (log n)/g, log N ≈ log log n, so the right side grows like (log n)/log log n: for fixed g, ε, r the window closes as n grows, at a rate so slow that experimental sizes will likely not see it. Which of listener and rebroadcast binds is decided by the rebroadcast's realized share of E\_r.

**As a number.** The lower edge is set by the empty permission: name gap about n log n against local gain n·g, so N\_lo ≈ (log n)/g. The first return is set by whichever of listener, global rebroadcast, and complete predicate has the smallest structural cost per unit of far gain; with E\_r pinned, that is a computable comparison of three numbers. Under summable decay the condition reduces to

```latex
\varepsilon < g :
```

a far listener's gain must be smaller than one site's local reuse gain, with matched leading constants. Under the per-interior cap the candidate binding competitor is the global rebroadcast, and if it realizes its cap the window closes as (log n)/log log n, slowly enough to be invisible at experimental sizes but closed in the limit. What free delivery does is make that competitor exist at all: one existing message, named once, delivered everywhere, with no new emission. With delivery priced at c per recipient it costs n·c per event, more than E\_r whenever c > ε/vol(r) in the per-interior regime; that theorem also reprices the ball's own bill by vol(r)·c per message, which moves N\_lo, and is not pursued here. The listener bound is one-sided, N\_hi is the infimum over all three families, and the exact edges remain the pairwise T\_lo and T\_hi.

*Proof.* Take ω ≠ P\_r in the class and apply Lemma 2.

1. If ω is inside (supp Π\_ω ⊆ P\_r), then a(ω) ≤ 0 by protocol inclusion. Its initial run ends at T\_lo(ω) ≤ N\_lo < N, and any later return is at T\_hi(ω) ≥ N\_hi > N, so G\_N(ω) ≥ 0. The lemma makes no claim that inside competitors never return; that is the corollary below, for regular classes.
2. If ω is outside, it is a far user, hubs and trees included. If ω is outside, N > N\_lo ≥ T\_lo(ω) means its initial run has ended, and N < N\_hi ≤ T\_hi(ω) means it has not returned, so G\_N(ω) ≥ 0 on the interval. H2 makes T\_lo(ω) finite when ω has lower structural cost; H1\* lower-bounds T\_hi(ω) when ω is a nested extension; the complete predicate is handled at both ends by its own T\_lo and T\_hi; the equal-cost case has T\_lo = 0 and needs no separate argument.
3. There is no third case. A star or separator tree is an outside competitor and was priced in step 2 by its name and its a(ω).

So no competitor has smaller J\_N than the ball inside the window, and P\_r is a minimizer. Inside competitors with ΔL = 0 tie, so membership holds for every τ > 0 while uniqueness does not. Above N\_hi some far competitor becomes pairwise cheaper than P\_r and is therefore eligible for global optimality; that does not by itself put it in C\*\_τ(N), since a third program can beat both. P\_r may or may not remain a member. Below N\_lo some cheaper predicate has ΔJ\_N < 0 and the ball is out. ∎

**Two remarks.**

- The packing cap is not the membership argument. A far competitor under the cap can beat the ball by up to S N Σ\_k ε\_k and is not dominated. Using H1\* alone would give a tolerance version, P\_r ∈ C\*\_{τ\_N}(N) for N > N\_lo with τ\_N linear in N. That version is not stated. Below N\_hi no far competitor beats the ball pairwise, so an arbitrary τ suffices.
- H1\* enters only through N\_hi, and only for nested far extensions of the ball protocol; H1^sup, through Lemma 3, extends the bound to the optimized complete predicate. Neither is needed for the lemma, which exhausts competitors through G\_N. Under exact screening the window is one-sided, N\_hi = ∞, and "not a phase the system keeps" does not apply; it is a statement about approximately screened data.
- **Corollary (no late return for regular classes).** If ΔCOMP\_N(ω) = (Δk/2) log N + O(Δk) and a(ω) < 0 persistently, the increment of G\_N past the crossing is |a| − |Δk|/(2N), positive because the crossing sits at N ≳ (|Δk|/2|a|) log N; so an inside competitor, once overtaken, never returns. This is a statement about the asymptotic parametric regime, not part of the exact definitions.

## 8. Regimes and nested permissions

The leading-order crossing ΔL / a sorts nested far extensions into four regimes; clearing it makes an exception pairwise eligible against the ball, and within the nested family it then coexists with the ball rather than evicting it.

| Regime | Structural cost | Gain cap (Lemma 3) | N\_c^(0) | Example |
| --- | --- | --- | --- | --- |
| No net advantage | any | ≤ 0 | ∞ | exact screening; every single-recipient new emission |
| Extra recipient | log n + (d/2) log N | ≤ ε\_1 | ≥ (log n)/ε\_1 | one far site reads an existing ball broadcast |
| Global rebroadcast | log n + (dn/2) log N | ≤ E\_r | ≥ (dn/2E\_r) log N | one ball message delivered to every site |
| New multi-receiver emission | log n + bill + class increment | ≤ its share of E\_r | ≥ cost / share | a shortcut broadcast with several customers; no far emission has O(1) gain unless E\_r does |
| Extensive bespoke wiring | n log n + (dn/2) log N | ≤ E\_r | ≥ (n log n)/E\_r | long-range edges at every site |
| Complete predicate | (d n²/2) log N | ≤ E\_r | ≥ (d n²/2E\_r) log N | under H1^sup |

The second and third rows can fall before N\_lo. An exception can be worth naming before the ball has paid for itself. Stage order is distributional, not universal.

**Nested permissions.** Exceptions e\_j have their own horizons N\_c(e\_j) = ΔL\_j / a\_j, where for a nested extension a\_j = δ\_j − r\_far,j exactly. Inside or above the window the τ-optimal set can contain the chain

```latex
P_r\subset P_r+e_1\subset P_r+e_1+e_2\subset\cdots
```

as coexisting members. Clearing N\_c(e\_j) makes e\_j pairwise eligible against the ball, not globally optimal; the chain is guaranteed only when comparison is restricted to the nested family P\_r + E. Within that family a shortcut that has amortized its name is not evicted, because removing it re-raises the residual by its gain while saving only a name already paid. Small-world structure is this chain, not a transition from local to nonlocal. This is the result the note actually delivers, and it deserves to be read on its own terms: a learner that pays for names does not flip from a local code to a nonlocal one when the first shortcut pays for itself. It keeps the ball, which still explains the bulk of the reuse at the cheapest name, and adds shortcuts one at a time as each one's persistent gain clears its address. The selected structure at any horizon is a ball plus the set of exceptions that have already amortized, and the order in which they arrive is set by their gains, not by any transition in the data. Under exact screening no shortcut ever arrives and the ball is the fixed point; under approximate screening the chain grows without bound and the ball is never evicted from within the nested family. What is emergent is this ordering, not the ball. If some N\_c(e\_j) < N\_lo, that exception is purchased against a cheaper backbone than P\_r, or the pure-ball window is empty.

A finite front-loaded burst contributes O(1) cumulative benefit and amortizes no fixed name. A competitor with Σ\_t δ\_net,t = O(1) never crosses.

## 9. What is returned, and how to test it

Minimum description length buys reusable broadcast and cheap predictors. It does not buy geometry. A metric ball is selected only inside the window where one emission has enough nearby customers to beat the sparse alternatives and an induced class of n·vol(r) parameters is enough cheaper than one of n² to beat the dense one, which is the better code on operating cost. The theorem prices a ball that is already in the class; it does not derive it.

| Outcome | Predicate | Condition |
| --- | --- | --- |
| Nothing local yet | P\_∅ or a shorter rule | N < N\_lo |
| Geometry | P\_r | N\_lo < N < N\_hi |
| Geometry plus exceptions | P\_r ∪ E | eligible after each N\_c(e); globally selected only after full-class comparison |
| Hub | P\_h | H2 fails for the star: a global common cause gives the hub broadcast a(P\_h) ≥ 0 with a shorter name |
| Hierarchy | P\_T | H2 fails for the tree: a separator program shorter than the embedding with a(P\_T) ≥ 0 |
| New single-recipient far emission | never | δ\_net ≤ 0 by Lemma 1 |
| Far extra recipient | P\_r ∪ {i} | N ≥ ΔL / ε\_k(r), later if its gain is below the cap; never if ε\_k(r) = 0 |
| Complete graph | P\_full | N ≥ (d n²/2E\_r) log N: under H1\* for the nested sub-protocol, under H1^sup for the optimized P\_full; never under exact screening with sufficient boundary broadcasts |

**Empirical protocol.** Score the predicate class, not a fitted radius. Candidates are {P\_∅, P\_r, P\_h, P\_T, P\_{r,E}, P\_full}, with E ranging over listeners, new emissions, and global rebroadcasts. For each (n, N) log L, COMP\_N of the induced class (predictor part d|P|, encoder part O(n), in the stated family), broadcast bill, sink codelength, J\_N, and C\*\_τ(N).

1. **Finite-range local family.** Run two sub-families. (a) Exact screening, ε = 0: N\_hi = ∞, P\_r enters at N\_lo and stays, and no kind-1 listener ever enters. (b) Approximate screening, ε > 0: a kind-1 listener enters no earlier than ΔL / ε\_k(r) plus its class-complexity increment, which need not lie beyond the run, and later if its gain misses the cap. Compute that lower bound before the run and check that no listener enters before it.
2. **Local plus sparse multi-receiver shortcuts.** Compute each N\_c(e\_j), and compute g and ε directly: g from the ball's per-site net broadcast value, ε from the listeners' conditional information. Prediction, at leading order: N\_lo tracks (log n)/g. Under summable decay the window is nonempty when g > C·ε and the first return tracks (log n)/ε, if the listeners' gain attains the cap; under a per-interior cap the first return is the smaller of the listener's (log n)/ε\_1 and the rebroadcast's (d vol(r)/2ε) log N, decided by the rebroadcast's realized share of E\_r, and the condition is g/ε ≳ (log n)/(d vol(r) log N). Estimate that share directly. Then, within the nested candidate family P\_r + E: P\_r remains in the set while each e\_j joins at its own N\_c, including the case where an exception precedes the ball. Outside that family the construction must guarantee that no third rule dominates both, or the prediction is only eligibility.
3. **Local plus a single-recipient shortcut emission.** Prediction: the new emission never enters at any N. This is the sharp falsification target, and it applies only to a new emission. It tests the accounting model, not the locality claim: it is a corollary of Lemma 1 plus coefficient 1, and a pass here is not evidence for the window. A name-only listener of an existing broadcast is predicted to enter at its own N\_c; running that case as if it should never enter would reject a true instance.
4. **Latent hierarchy.** Prediction: P\_T. This is a failure of H2, not of the theorem; log the tree's name and its a(P\_T) to confirm which.
5. **Global common cause.** Prediction: P\_h, and H2 fails measurably as Σ\_i I(X\_i; X\_h) grows past the ball's net value.
6. **Non-embeddable dependence graph.** Prediction: P\_r does not enter because the class offered it.
7. **Dense competitor, the headline test.** Include P\_full in the class at every (n, N). Prediction under approximate screening: the ball wins while (d/2) n² log N of class complexity exceeds the cumulative far gain, and P\_full enters no earlier than (d n²/2E\_r) log N, after the global rebroadcast of a single message, which enters no earlier than (dn/2E\_r) log N; both bounds hold for the optimized protocols only under H1^sup, so an early entry is a test of H1^sup before it is a test of the thesis. Include the global rebroadcast in the class; it is the return family free delivery creates. Under exact screening with sufficient boundary broadcasts P\_full never enters. Expect P\_full to win on an initial run of at least order log n events, longer if the saturated regret is below its ceiling; measure where the run ends, and run well past N \~ d n², where its complexity enters the logarithmic regime. If P\_full enters earlier than the bound, or beats the ball under exact screening, the class-complexity mechanism is wrong and the thesis fails; this is the test that decides whether the paper's claim holds.

Measured transitions should land on the computed horizons. A transition that lands elsewhere falsifies the sign analysis of Section 6 before it falsifies the theorem.

## 10. Statements

Sink decodes site-wise. Each site emits one message from its own observation; no self-delivery, no relay. An emission costs once and may be used by every permitted recipient. Coefficient 1:

```latex
\mathcal{J}_N=L+\operatorname{COMP}_N+R_N+L_{\log}.
```

1. A single-recipient transcript saves at most its own codelength (Lemma 1). A new emission pays only when several receivers share the information it carries.
2. Every competitor is a lower structural cost or a far user, hubs, trees, and the complete predicate among the far users (Lemma 2). The pairwise gap is ΔL + ΔCOMP\_N − Σ\_t a\_t with a\_t the total per-event operating advantage; δ − r\_far is its exact form only for nested extensions.
3. Under H1\* and H2, if N\_lo < N\_hi, then P\_r ∈ C\*\_τ(N) for every τ > 0 and every N\_lo < N < N\_hi, with

```latex
N_{\mathrm{lo}}=\sup_{\omega}T_{\mathrm{lo}}(\omega),\qquad N_{\mathrm{hi}}=\inf_{\omega}T_{\mathrm{hi}}(\omega),
```

4. with G\_N = ΔL + ΔCOMP\_N − Σ\_t a\_t the cumulative gap and COMP\_N the stochastic complexity of the predictor class the permission induces, charged to the predicate. T\_lo(ω) is the end of ω's initial winning run and T\_hi(ω) its first return. Under stationary advantage and o(N) class complexity, the crossings are N\_c = ΔL̃/a + o(N\_c). The condition N\_lo < N\_hi is a hypothesis with content: a supremum of last-crossings against an infimum of first-returns. Scaling: N\_lo = O((log n)/g) provided ΔL = Θ(n log n), a\_loc = Θ(ng), and ΔCOMP at N\_lo is o(n log n). With E\_r = S Σ\_k ε\_k the total far information per event and Lemma 3 capping every far gain by its share of E\_r: a listener returns no earlier than (log n)/ε\_1, a global rebroadcast no earlier than (dn/2E\_r) log N, the optimized P\_full no earlier than (d n²/2E\_r) log N under H1^sup. N\_hi is the least of these. Under summable decay the listener binds and g > C·ε opens the window; under a per-interior cap the rebroadcast's bound is (d vol(r)/2ε) log N with the n cancelled, it binds only if its realized share of E\_r is near the cap, and the window then closes as (log n)/log log n. Equalities need matching lower bounds on realized gains. H1\* only lower-bounds N\_hi, for nested far extensions of the ball protocol, by capping their sink savings at S Σ\_k ε\_k(r) nats per event. It is not a growing tolerance, and the theorem does not use it to exhaust competitors. The complete predicate is priced at both ends by its class complexity, (d/2) n² log N, which is the only term that separates it from the ball; its crossing is bounded below by (d n²/2E\_r) log N, for the nested sub-protocol under H1\* and for the optimized P\_full under H1^sup.
5. A far extra recipient of an existing broadcast enters no earlier than ΔL / ε\_k(r), about log n / ε, and later if its gain falls short of the cap. A new single-recipient far emission never enters. Crossing a pairwise horizon makes a competitor eligible, not a member of C\*\_τ(N).

Positive communication value requires a broadcast informative to several receivers, which is why the ball can beat the sparse alternatives. The claim the note supports is this: in a specified per-edge parametric predictor family, reusable local broadcast can make a metric-ball sparsity pattern MDL-optimal over a finite or one-sided range of horizons, provided every early winner is uniformly overtaken and sufficiently distant predictive information is screened. The predictor class a permission induces is paid for whether or not it is used, which is why the ball beats the dense one. A permission is a sparsity pattern, and MDL pays for sparsity patterns by naming them; locality is selected where reuse and class complexity both favor the ball. Geometry is the permission under which that reuse is local, and only while the horizon sits between amortization of the ball's name and the first far broadcast that has paid for its own.

**What is assumed, not derived.** Two conditionals remain, both stated inline above. H1^sup is assumed, not derived from a property of the data; until it is, the upper edge for the optimized P\_full and for the global rebroadcast is conditional on it. COMP\_N(P\_full) for N < d n² is bounded above by the data's codelength and not computed; the end of P\_full's initial run, and so the lower edge it may set, is bounded below and not located. Everything else in the horizon theorem is a lower bound that becomes an equality only with a matching lower bound on the realized gain. The scaling of E\_r must be pinned before any horizon is quoted. Run family 7 first.
