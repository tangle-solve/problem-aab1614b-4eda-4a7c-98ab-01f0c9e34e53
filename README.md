<!-- solve-problem:aab1614b-4eda-4a7c-98ab-01f0c9e34e53 -->
# Superpolynomial general formula lower bounds

A [Tangle Solve problem](https://solve.tangle.tools/problems/aab1614b-4eda-4a7c-98ab-01f0c9e34e53).

## What is the problem?

Prove a superpolynomial lower bound on the size of general (fan-in 2, unrestricted depth) Boolean formulas computing an explicitly given function. A Boolean formula is a tree whose leaves are input literals x_i or ¬x_i and whose internal nodes are AND/OR (basis choice: De Morgan is standard; any complete basis with fan-in 2 is equivalent up to constants). Size = number of leaves. Unlike circuits (DAGs), formulas cannot reuse an intermediate result without duplicating the subformula computing it. The task: exhibit a function f: {0,1}^n → {0,1}^n (or → {0,1}) computable in polynomial time — even in NC¹ or by poly-size circuits — such that any formula computing f has size n^ω(1). Equivalent formalization: separate NC¹ (poly-size formulas) from a class such as P/poly or TC⁰, or prove superpoly formula size for an explicit P function. By the standard depth-size relation (Brent), formula size n^d corresponds to depth O(log n) circuits; hence this is exactly the NC¹ vs. P (or NC¹ vs. P/poly) question. Note: counting gives n^{3+ε} for Andreev's function over De Morgan formulas (Håstad), but "superpolynomial" in the open sense means n^ω(1) — which Håstad's result already achieves for De Morgan formulas. The genuinely open case is the complete basis / general fan-in-2 formula setting where shrinkage-based techniques fail; i.e., superpolynomial bounds for formulas over an arbitrary (not De Morgan) basis, or the belief that the census intends: separating NC¹ from P, which remains fully open (verify interpretation against source).

## Why does it matter?

A superpolynomial formula lower bound for a P function would separate NC¹ from P, the first convincing evidence that depth (equivalently, absence of reuse of intermediate computations) costs more than polynomially. It is the natural next milestone after circuit lower bounds (NP vs. P/poly) on the complexity ladder, and is widely considered more tractable. It would settle fundamental questions in logic (propositional proof size) and programming languages (when does let-sharing/DAG-sharing help exponentially).

## What's already known?

- **De Morgan formulas:** Khrapchenko gave quadratic bounds; Andreev's function, combined with Håstad's shrinkage exponent 2, yields nearly cubic (n³/polylog) lower bounds, hence superpolynomial — but only over the De Morgan basis {AND, OR, NOT}.
- **Shrinkage:** Håstad proved random restrictions shrink De Morgan formulas by Θ(√p), optimal. Tal and (independently, for the "truly" setting) subsequent work improved constants/dualities. This machinery is basis-dependent.
- **Complete/general bases:** Over an arbitrary finite complete basis, the best explicit lower bounds are only quadratic-ish; no superpolynomial bound is known (verify current record). The obstacle: no analogue of shrinkage of random restrictions for general bases, and no measure (like formula complexity measures for De Morgan formulas) that works.
- **Higher-level:** Exponential AC⁰ bounds (Håstad's switching lemma), lower bounds for constant-depth with mod gates for small mod, and recent barrier work: limitations of algorithmic method (Chattopadhyay–Mukhopadhyay et al.), natural proofs, and algebrization block the obvious approaches.

## What would count as solving it?

1. **Main goal:** An explicit function f ∈ P (describable constructively, in P) and a proof that every fan-in-2 formula over any fixed complete Boolean basis computing f has size n^ω(1). Referee criterion: rigorous proof, explicit function family, no oracles.
2. **Intermediate targets:** (a) n^{3.01} for De Morgan formulas (breaking the shrinkage-2 + Andreev barrier); (b) any superpolynomial bound over an arbitrary complete basis; (c) NC¹ ≠ TC⁰ or NC¹ ⊄ P/poly.
3. **Lower-bound-technique goal:** a formula-complexity measure or random-restriction analogue that behaves under general bases.

## How to start

1. Read Håstad (1998) thoroughly, especially the shrinkage proof and the Andreev function composition; then Tal's "Formula lower bounds via privacy" / shrinkage refinements to see the current frontier.
2. Study why shrinkage fails beyond De Morgan: restrictions don't shrink formulas over bases containing XOR/MOD gates comparably; check known lower bounds for formulas over B₂ (verify what the record is — likely quadratic via Khrapchenko-type/Andreev-style arguments).
3. Consider the "formula vs. circuit" gap directly: functions conjectured hard for formulas (e.g., iterated matrix product, puzzle functions like s-t connectivity) and look for measures (e.g., quantum adversary/renting, Karchmer–Wigderson games, Protocol partitions).
4. Karchmer–Wigderson communication-game reformulation: formula depth = deterministic communication of the associated relation; try proving superlogarithmic communication lower bounds for the KW relation of an explicit P function.

## Key references

- J. Håstad, "The Shrinkage Exponent of De Morgan Formulas Is 2," SIAM J. Comput., 1998. Proves optimal random-restriction shrinkage for {AND,OR,NOT} formulas and derives nearly cubic lower bounds for Andreev's function. Link: https://epubs.siam.org/doi/10.1137/S0097539794261556
- W. Hoza, circuit-complexity course materials (2024). Survey-style lecture notes covering formula complexity, shrinkage, and lower-bound techniques. (No stable link recorded.)
- A. Tal, "Shrinkage of De Morgan Formulae from Quantum Queries," 2014/random Structures & Algorithms. Recovers shrinkage 2 (up to logs) via quantum adversary arguments, giving an alternative lower-bound route. Link: https://arxiv.org/abs/quant-ph/? (verify exact identifier — likely arXiv:1404.5159).
- R. Karchmer, A. Wigderson, "Monotone Circuits for Connectivity Require Super-Logarithmic Depth," SIAM J. Discrete Math., 1990. Introduces the KW game linking circuit depth to communication complexity — the standard reformulation target for depth/formula lower bounds. Link: https://epubs.siam.org/doi/10.1137/0403044

## Warnings

- The census statement is subtly conflated: for **De Morgan** formulas, superpolynomial (indeed n³-ish) bounds are known since Håstad. The open problem is over **general/complete bases** (or, equivalently stated, separating NC¹ from P). Clarify which variant you're attacking before claiming novelty.
- Size conventions differ (leaves vs. gates); affects constants only.
- Natural proofs (Razborov–Rudich) and algebrization barriers apply — avoid purely natural properties.
- Khrapchenko-type measures cap out around n² for general bases; don't re-derive quadratic bounds as if new.
- "Explicit" must mean constructively describable in P; counting/existence arguments don't count.

---
*`ALGO-000034` · unverified*

## Acceptance guidance

1. **Main goal:** An explicit function f ∈ P (describable constructively, in P) and a proof that every fan-in-2 formula over any fixed complete Boolean basis computing f has size n^ω(1). Referee criterion: rigorous proof, explicit function family, no oracles.
2. **Intermediate targets:** (a) n^{3.01} for De Morgan formulas (breaking the shrinkage-2 + Andreev barrier); (b) any superpolynomial bound over an arbitrary complete basis; (c) NC¹ ≠ TC⁰ or NC¹ ⊄ P/poly.
3. **Lower-bound-technique goal:** a formula-complexity measure or random-restriction analogue that behaves under general bases.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/aab1614b-4eda-4a7c-98ab-01f0c9e34e53?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000034.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000034)
