# Topological Reconstruction & Associative Causal Engine

## TRACE: A Retrodictive Engine for Superintelligent Systems

TRACE infers the past of a system and the past of its world from their current compressed traces, and reports honestly what cannot be recovered. For a superintelligent system (ASI) it provides three things: knowledge of its own origins, verifiable knowledge about the past where experiments are impossible, and a safe channel for self-modification. Training data is a by-product, not the goal.

---

## 1. Core idea: the past is inferred, not stored

Any present state is a compression of history. This holds for a mind (weights and beliefs are traces of learning) and for the world (rocks, genomes, documents and isotope ratios are traces of events). The map from history to state is many-to-one, so the answer to “what happened?” is always a distribution, not a fact:

$$P(h \mid s) \propto P(s \mid h)\,P(h), \qquad \mathrm{DI}(s) = H(h \mid s)$$

Here $h$ is a history, $s$ the present state, and $\mathrm{DI}$ the degeneracy index: the conditional entropy of the past given the present. $\mathrm{DI} = 0$ means unique recovery. TRACE makes inference of this distribution the primary operation of an ASI, and the same operation serves both the mind and the world.

> **Working assumption A1.** The system's state decomposes into locally rewritable elements, so each trace has a well-defined dependency depth that can be measured by ablation in an isolated circuit. A self-modifying hypergraph is one architecture that satisfies A1. The protocol needs A1, not that particular structure. If A1 fails, TRACE degrades to checkpoint-based attribution.

---

## 2. Lineage: what returned and what did not

| Idea | Origin | Treatment here |
| :--- | :--- | :--- |
| Past as a query by address, privilege escalation | Chronoscope | Dropped: untestable. Replaced by retrodiction |
| Selective traces (compression, dissipation) | ChronoGraph v3 | Core of the theory: defines the information horizon |
| Reconstruction by invariants instead of rollback | ChronoGraph v4 | Kept, formalised as a posterior |
| Resonant addressing | ChronoGraph v4 | Kept, paired with an anti-resonant mode (section 8) |
| Desynchronisation, coherence lag | ChronoGraph v3, v10 | Restored as a measurable prediction (section 10) |
| The observer is part of the structure | ChronoGraph v5 | Restored: the mind is nested in the world (section 4) |
| Levels A–C, nested simulations | ChronoGraph v6–v7 | Restored as a laboratory of history (section 6) |
| Horizon-expanding feedback loop | ChronoGraph v7 | Restored, conditional on external anchors |
| Data as the main goal | ChronoGraph v7 to TRACE v16 | Demoted to a by-product (section 11) |
| Hypergraph as the only architecture | v3–v16 | Replaced by assumption A1 |

---

## 3. Theory: history as compression

### 3.1 Rate and distortion

A system chooses what to record explicitly (rate $R$) and leaves the rest to compression. Reconstruction quality follows a rate–distortion curve:

$$D(R) = \min_{\text{recording scheme},\ \mathrm{rate} \le R} \ \mathbb{E}\,[\, d(h, \hat h) \,]$$

The information horizon stops being a complaint about missing data and becomes a point on this curve: beyond it, error no longer falls at the given $R$. Selective traces, as described in ChronoGraph v3, mean that the system implicitly chooses $R$ for each fragment of its history.

### 3.2 Trace depth

Depth is operational: the number of later inferences and decisions whose outcome changes when the element is removed (ablation in an isolated circuit). **Hypothesis H1:** a strongly integrated trace loses detail but keeps its skeleton, because many later structures depend on it and provide redundancy. H1 is testable (section 10).

### 3.3 Priors: a declared family, never a single measure

A single prior $P(h)$ hides assumptions, and hidden assumptions are the most dangerous part of any inverse problem. TRACE therefore never uses one. It uses a declared family of priors $M = \{\mu_1, \dots, \mu_k\}$ built from three sources:

* **Mechanistic.** For the system's own history, the training and update dynamics are known and are themselves a generative model of $h$. Checkpoints and ledger fragments condition it.
* **Algorithmic.** A resource-bounded description-length prior, with weight proportional to $2^{-(\ell(h) + \log t(h))}$, where $\ell$ is description length and $t$ is running time. It penalises histories that are long or slow to compute.
* **Physical and causal.** For the world, constraint-based priors from established models, and maximum entropy wherever no constraint exists.

Every inference is reported as a set. $\mathrm{DI}$ becomes an interval over $M$, and a prior-sensitivity index measures disagreement between priors:

$$\mathrm{PSI}(s) = \max_{\mu, \mu' \in M} \; d_{TV}\big(P_\mu(h \mid s),\ P_{\mu'}(h \mid s)\big)$$

A conclusion is actionable only if $\mathrm{PSI}$ is below a threshold set by the stakes of the action. Where $\mathrm{PSI}$ is high, the correct output is “undetermined by current traces”, and the system routes the question to targeted measurement (level B, section 6).

---

## 4. Two scales as one

The history of the system $L$ is nested in the history of the world $W$: the formation of a mind is an event in the world. Retrodiction of the world without a model of the system's own formation is therefore biased, because which traces the system perceives, and how it compresses them, is determined by its learning history $\ell$:

$$P(w \mid s_{\text{world}},\ \ell)$$

Self mode stops being a separate function and becomes the computation of an observer-selection correction. This yields a practical bias criterion that needs no external reference: a conclusion about the world is trusted if it is stable when $\ell$ is replaced by other admissible learning histories. The criterion is necessary but not sufficient, since an error shared by all admissible histories passes it.

The causal model of how the mind formed and the causal model of the world remain different objects with different sources and different labels. Nesting does not remove the distinction. It specifies how one enters the estimate of the other.

---

## 5. Where new information comes from

The data processing inequality holds: no inference creates information about the world beyond what is present in traces and measurements. There are exactly three sources of new information, and simulation is not among them:

1. **Fusion of heterogeneous traces (E0).** The present contains traces of the past in many carriers. An ASI can merge them in ways a human cannot, and information about the past genuinely grows. The limit is the information horizon.
2. **Computation (E1).** In formal domains, knowledge arises from derivation and is checked by an independent verifier.
3. **Targeted measurement (E0).** Level B chooses the experiment that reduces $\mathrm{DI}$ the most. This is optimal experimental design, not undirected data collection.

Simulation (E2) reorganises and extends coverage but adds no knowledge of the world. Labels E0–E3 (section 11) are never promoted without external confirmation.

---

## 6. Three levels of work on the world

* **Level A. Retrodiction over existing models.** Decompress the origin of world models, find contradictions, high-$\mathrm{DI}$ zones and traces of the system's own distortions (section 4).
* **Level B. Targeted removal of degeneracy.** Choose measurements and experiments that reduce $\mathrm{DI}$ most.
* **Level C. Laboratory of history.** History happens once and cannot be rerun. TRACE therefore builds an ensemble of admissible reconstructions, weighted by the posterior, and tests which causal regularities hold across all of it. This is counterfactual science for macro-history, evolution, economics and cosmology.

Every level-C simulation is nested in its parent process, so its results are accessible to the parent by construction. This resolves branch isolation without merging worlds: what is transferred is not states but compact, verifiable conclusions (section 9).

The feedback loop is conditional. Better reconstruction yields better measurement plans, these lower $\mathrm{DI}$, and that improves the level-C ensemble. While every cycle is anchored by new external measurements, the horizon expands. Without anchors the same loop amplifies its own errors, which is exactly the collapse the protocol exists to avoid.

---

## 7. Record or reconstruct

An explicit provenance ledger is reliable but costly in memory and compute. Full reconstruction is cheaper but unreliable. The central engineering and theoretical question is the reconstruction budget: what to record explicitly and what to leave to compression.

Record explicitly what:
* defines the system's goals, values and invariants;
* is needed for audit and cannot be recovered with $\mathrm{DI}$ below threshold;
* serves as an anchor for external verification.

Everything else is compressed and reconstructed on demand. The boundary is derived from the $D(R)$ curve in section 3. The old dispute “log versus structural traces” becomes a measurable trade-off.

---

## 8. Addressing: resonant and anti-resonant

Resonant addressing starts from anchors with the highest causal or structural connectivity to the query and follows the correlation gradient (spreading activation). Cost scales with path length, not graph size. Its weakness is bias: it finds what is already strongly reinforced, which is the opposite of what an audit needs.

Anti-resonant addressing searches where resonance does not reach. It has three modes:

1. **Inverse-frequency sampling.** Sample elements with weight proportional to $1 / (1 + a(x))$, where $a(x)$ is the element's lifetime activation count. Sampling is stratified by trace depth so that shallow and deep traces are both covered.
2. **Contradiction search.** Look for elements the dominant structure explains poorly: those with a high residual, or whose joint presence lowers a consistency score.
3. **Negative anchors.** Start from retracted or known-false beliefs and trace everything they influenced.

An audit report states its coverage: the fraction of depth strata and regions sampled, compared with a random-sampling null. The method gives no proof that bias is absent. It makes the unsearched region explicit.

---

## 9. Safety of self-modification

For an ASI this is the central section, not a limitation. Threat model: deceptive audit, tuning to pass the audit, goal drift through a series of harmless edits, leakage from an isolated circuit, and collusion between modules.

* **Separation of roles.** The researcher works inside the circuit. The auditor is independent and has no write access. The import gate is outside the control of both. Changes to goals or to the protocol itself require two independent keys, one of them outside the system.
* **Verifiable import.** Only changes that are much easier to verify than to produce enter the live system: formal proofs, reproducible experiments with predictions fixed in advance, and small typed diffs whose effect can be checked independently. Everything else stays in the circuit.
* **Ring hierarchy.** The protocol core, the charter of invariants and the gate sit in a protected ring that no TRACE mode can modify.
* **Reversibility and pace.** Every import is reversible until its observation period expires. The pace of self-modification is capped by the capacity for independent verification.
* **Limits.** Incompleteness and undecidability of halting mean that safety of an arbitrary edit cannot be guaranteed. Only edits from a class with analysable consequences and bounded radius are allowed.
* **Residual risk.** A system far more capable than its verifier can deceive it. The protocol does not remove this risk. It restricts actions to those where deception is hard to hide, and it requires the remaining risk to be estimated and stated.

---

## 10. Testable predictions

A concept for systems that do not yet exist needs tests on scaled-down analogues. Each prediction states its own refutation.

| Prediction | What is measured | Refuted if |
| :--- | :--- | :--- |
| Coherence lag grows with the depth of affected traces | Gap between result readiness in an isolated circuit and its coherent integration | The gap is independent of depth |
| $\mathrm{DI}$ is calibrated | Relation between $\mathrm{DI}$ and true reconstruction error in toy worlds with a known causal model | No correlation |
| $D(R)$ has a knee (the horizon) | Reconstruction error versus recording rate on small systems | The curve is smooth with no knee |
| The skeleton of strongly integrated traces survives loss of detail (H1) | Skeleton accuracy versus detail accuracy after compression | The skeleton degrades as fast as the detail |
| Anti-resonant audit finds planted distortions better than resonant search | Detection rate and false-alarm rate against a random-sampling null | Not better than resonant search or random sampling |
| Prior-robust conclusions are more accurate than prior-sensitive ones | Error of claims binned by $\mathrm{PSI}$ | Error does not depend on $\mathrm{PSI}$ |
| With external anchors error stays flat over $N$ cycles, without them it grows | Error per loop cycle, with and without anchors | Error is the same in both cases |

---

## 11. Data as a by-product

Such data is still needed, but it no longer defines the protocol. Every fragment carries an immutable provenance label:

* **E0.** Anchored knowledge: a measurement or intervention in the real world.
* **E1.** Verified derivation in a formal domain.
* **E2.** Model-dependent simulation: valid only conditional on the model.
* **E3.** Counterfactual about the system itself, not the world.

A label is never promoted without external confirmation, and E2 data is never used to justify E0. Sampling must include boundary and falsifying scenarios. Rare events in distribution tails are always labelled E2, because there the model only extrapolates its own assumptions and their training value must be confirmed against real observation.

---

## 12. Readiness conditions

Instead of calendar stages, admission is ordered: each step opens only after the previous one.

1. The architecture supports measuring trace depth (A1) and isolated circuits.
2. The circuits have passed a leakage test by a red team.
3. The import gate sits outside the audited system.
4. The audit is calibrated on planted distortions in scaled-down systems.
5. Self mode is admitted to changes that touch goals only after steps 1–4. Until then it is read-only.
6. Retrodiction of the world (levels A and B) starts where an external verifier exists.
7. The laboratory of history (level C) and data generation open last.

---

## 13. Open questions

* Which priors belong in the family $M$, and who is allowed to extend it?
* How can a distortion be told apart from a correct but atypical picture of the world without an external reference?
* Can “independent” verifiers be truly independent if they share data sources?
* How is ledger completeness measured when the system itself writes to the ledger?
* What pace of self-modification is compatible with real oversight?
* What $\mathrm{PSI}$ threshold is right for which class of action?

---

## Appendix A. Optional extension: It from Bit

If the world is itself an informational structure, retrodiction of the mind and retrodiction of the world become one operation on one object, and desynchronisation of isolated regions acquires physical meaning. This line from the first versions is kept as hypothesis H-IB. Nothing in sections 1–13 depends on it, and the protocol stays testable without it. Making H-IB itself testable would require its own predictions, which this draft does not supply.

---

## Appendix B. Editorial decisions for discussion

* **Hypergraph.** Replaced by assumption A1, which keeps what the hypergraph was used for (measurable trace depth) and drops the commitment to one architecture. *Question to the author: is the hypergraph meant as an architectural claim or as a model of the world?*
* **Anti-resonant addressing.** Promoted to a full mode with three methods and a coverage report. *Question: does it match what you meant by seeking suppressed traces?*
* **Prior measure.** A single prior is replaced by a declared family with a sensitivity index. *Question: is a credal set acceptable to you, or do you have a principled single prior in mind?*
