# Survivor Sequence Framework: Core Definitions and Initial Implications

## 1. Overview

This document outlines the foundational definitions for a mathematical framework built upon constrained periodic binary sequences. The core objects are **Survivor Sequence Classes**, which exhibit specific number-theoretic properties. A central component of the framework is the **Rational Projection Map (`φ'`)**, establishing a bijection between the set of survivor classes with period `n ≥ 2` and the rational numbers `Q`, thereby linking discrete combinatorics to arithmetic and geometry. This document also explores preliminary answers and implications for the immediate goals of the framework based on these definitions.

## 2. Periodic Binary Sequences and Equivalence Classes

**Definition 2.1 (Periodic Binary Sequence):**
An infinite binary sequence `S = (b₁, b₂, b₃, ...)` where `bᵢ ∈ {0, 1}` is **periodic** if there exists a positive integer `n` such that `bᵢ₊<0xE2><0x82><0x99> = bᵢ` for all `i ≥ 1`.

**Definition 2.2 (Minimal Period):**
The **minimal period** `n` of a periodic sequence `S`, denoted `n = per(S)`, is the smallest positive integer `n` for which `bᵢ₊<0xE2><0x82><0x99> = bᵢ` holds. The sequence is uniquely defined by its minimal repeating unit (string) `s = (b₁, ..., bₙ)`, and can be written `S = sʷ`.

**Definition 2.3 (Equivalence Class):**
Two periodic sequences `S₁` and `S₂` are **equivalent**, denoted `S₁ ~ S₂`, if one is a cyclic shift of the other. The **equivalence class** `[S]` is the set `{T | T ~ S}`. All sequences in `[S]` share the same minimal period `n`.

## 3. Sequence Parameters (Derived from Minimal Period)

All parameters for a class `[S]` are calculated using its unique minimal period `n` and a representative minimal period string `s = (b₁, ..., bₙ)`.

**Definition 3.1 (Counts):**
* `n = per(S)`: Minimal period length (`n ≥ 1`).
* `n0`: Count of `0`s in the string `s`.
* `n1`: Count of `1`s in the string `s`. Note: `n0 + n1 = n`.

**Definition 3.2 (Transition Counts):**
* `k = count(01)`: Count of `0 -> 1` transitions in `s`, including the wrap-around transition `bₙ -> b₁`. `k ≥ 0`. For `n > 1`, `k` equals the count of `1 -> 0` transitions.
* `t = count(01) + count(10)`: Total number of transitions. `t = 2k` if `n > 1`; `t = 0` if `n = 1`.

**Definition 3.3 (Predominant Digit):**
* The **predominant digit** `a` is defined as `0` if `n0 ≥ n1`, and `1` if `n1 > n0`.
* `count(pred)`: The count of the predominant digit `a`. `count(pred) = max(n0, n1)`.
* The **non-predominant digit** `b` is `1-a`.

## 4. Survivor Sequence Classes

**Definition 4.1 (Survivor Sequence Class):**
An equivalence class `[S]` is a **Survivor Sequence Class** if its minimal period `n` and parameters satisfy one of the following:
* **Case 1:** `n = 1` (corresponding to the classes `[(0)ʷ]` and `[(1)ʷ]`).
* **Case 2:** `n > 1` and `gcd(k, count(pred)) = 1`.

**Definition 4.2 (Set of Survivors):**
Let `Σ` denote the set of all Survivor Sequence Classes. Let `Σ' = Σ \ { [(0)ʷ], [(1)ʷ] }` be the subset with period `n ≥ 2`.

**Property 4.3 (Count of Survivor Classes):**
The number `N(n)` of survivor classes `[S] ∈ Σ` having minimal period `n` appears to be given by:
* `N(1) = 2` (for classes `[(0)ʷ]` and `[(1)ʷ]`)
* `N(n) = φ(n)` for `n ≥ 2`, where `φ` is Euler's totient function.
*(Justification requires formal proof linking Def 4.1 to properties counted by `φ(n)`).*

**Property 4.4 (Generation Mechanism):**
The set `Σ'` can be generated recursively via a process equivalent to the Stern-Brocot tree construction using mediants applied to the parameters `(k, count(pred))`. This structure naturally yields pairs satisfying coprimality conditions related to `φ(n)`.

**Property 4.5 (Canonical Representation):**
Each class `[S] ∈ Σ'` can be represented by a unique canonical string: Start with the predominant digit `a`, follow with `(ab)` repeated `k` times, append remaining `n_a - k` instances of `a` (where `n_a = count(pred)`).

## 5. The Rational Projection Map (`φ'`)

**Definition 5.1 (Domain and Codomain):**
The **Rational Projection Map** `φ'` maps survivor classes with period `n ≥ 2` to the rational numbers `Q`:
`φ': Σ' -> Q`
where `Σ' = Σ \ { [(0)ʷ], [(1)ʷ] }`.

**Definition 5.2 (Formula):**
For any survivor class `[S] ∈ Σ'` (so `n ≥ 2` and `k ≥ 1`), let `n0, n1, k` be parameters derived from the minimal period `n`. Calculate the difference `Δ = n0 - n1`. The map is defined as:
* If `Δ ≥ 0` (i.e., 0 is predominant or `n0=n1`):
    `φ'([S]) = Δ / k`
* If `Δ < 0` (i.e., 1 is predominant):
    `φ'([S]) = k / Δ`

*(Note: This yields `φ'([(01)ʷ]) = 0`.)*

**Definition 5.3 (Handling `n=1` Cases):**
The classes `[(0)ʷ]` and `[(1)ʷ]` are outside the domain of `φ'`. Conceptually, they correspond to the single point at infinity (`∞`) in the projective rational line `Q P¹`. Specific geometric visualizations must define how these two classes are represented (e.g., as `∞` approached from different "sides", or as distinct points like `(0,1)` and `(0,-1)`).

**Property 5.4 (Complementation Symmetry):**
Let `τ(S)` denote the complementary sequence (0s↔1s). If `[S] ∈ Σ'` and `φ'([S]) ≠ 0`, then `[τ(S)] ∈ Σ'` and `φ'([τ(S)]) = -1 / φ'([S])`.

**Property 5.5 (Bijection Status):**
The map `φ': Σ' -> Q` is **conjectured** to be a **bijection**. *(Proving this formally is Goal #1).*

## 6. Harmonic Ratios

**Definition 6.1 (Harmonic Ratios):**
For any survivor class `[S] ∈ Σ'` (so `n ≥ 2` and `t = 2k > 0`):
* `r₁' = n0 / t`
* `r₂' = n1 / t`
* `r₃' = n / t`

**Property 6.2 (Harmonic Relation):**
These intrinsic ratios satisfy the linear relation: `r₁' + r₂' = r₃'`.

**Property 6.3 (Relation to `φ'`):**
The rational projection `r = φ'([S])` is related to the harmonic ratios by:
* If `r₁' ≥ r₂'` (`Δ ≥ 0`): `φ'([S]) = 2 (r₁' - r₂')`
* If `r₂' > r₁'` (`Δ < 0`): `φ'([S]) = 1 / (2 (r₁' - r₂'))`
*(This relationship is derived directly from the definitions).*

## 7. Preliminary Answers and Implications for Goals

This section addresses the immediate goals outlined previously, based on the definitions established above.

**7.1 Goal 1: Prove `φ': Σ' -> Q` is a bijection.**
* **Status:** Conjectured, requires formal proof.
* **Evidence/Hints:**
    * *Injectivity:* Plausible for `r ∈ Q`. If we assume `gcd(k, |n0-n1|) = 1` (which seems likely related to the survivor condition `gcd(k, max(n0,n1))=1`), then the value `r = Δ/k` or `r = k/Δ` should uniquely determine the pair `(k, |Δ|)`. Combined with the sign determining predominance, this strongly suggests `k, n0, n1` are fixed, uniquely identifying the class `[S]` via the Stern-Brocot generation. (Formal proof needed).
    * *Surjectivity:* Plausible. The Stern-Brocot process generates all coprime pairs `(p,q)`. We need to show that the map from generated parameters `(k, n_a)` via the formula `Δ/k` or `k/Δ` covers all of `Q`. Construction algorithms (like placing `k` bits based on `Δ`) likely exist, supporting surjectivity. (Formal proof needed).
* **Note:** The map extended to `φ'_{ext}: Σ -> Q P¹` by assigning `φ'_{ext}([0])=∞` and `φ'_{ext}([1])=∞` is surjective onto `Q P¹` but **not** injective at `∞`.

**7.2 Goal 2: Prove the count `N(n)` (`N(1)=2, N(n)=φ(n)` for `n>=2`).**
* **Status:** Conjectured/Observed, requires formal proof.
* **Evidence/Hints:** The Stern-Brocot generation mechanism (Property 4.4) produces `φ(n)` new coprime pairs `(p,q)` such that `p+q = n`. If the survivor parameters `(k, n_a)` or `(k, n_b)` directly correspond to these pairs and the minimal period is `n = k+n_a` or `n=k+n_b`, then the count `N(n)=φ(n)` follows. The core of the proof involves rigorously showing the equivalence between the definition `gcd(k, count(pred))=1` for minimal period `n` and the generation of these `φ(n)` unique classes via the mediant process.

**7.3 Goal 3: Establish relationship between `φ'` and harmonic ratios.**
* **Status:** **Answered.**
* **Result:** The relationship is explicitly given in Property 6.3. `φ'([S])` depends directly on the *difference* between the first two harmonic ratios (`r₁' - r₂'`), scaled appropriately.

**7.4 Goal 4: Develop geometric projections based on `φ'` and handle `[0],[1]`.**
* **Status:** Requires development.
* **Next Steps:** Now that `φ'` is precisely defined for `Σ'`, the various geometric projection maps (semicircle `ψ`, double-cover `ψ₄`, hyperbolic `ψ_ext`, spinor `ξ`, etc.) described conceptually in the wiki can be given explicit formulas. These formulas will take `r = φ'([S])` as input (for `[S] ∈ Σ'`) and map it to coordinates (e.g., angle `θ` via `r=tan(θ/2)` or `r=±2^θ`?, radius `ρ` via `n`). Specific, consistent rules must be added for visually representing the `n=1` classes `[0]` and `[1]` within each projection (e.g., mapping them to `(0,1)` and `(0,-1)` on the circle for `ψ`, or to `1` and `-1` on the hyperbolic boundary `∂D`, or to the point `∞` represented appropriately).

## 8. Summary of Foundational Status

The core objects (`Σ`) and their count (`N(n)`) seem well-defined and consistent with a fundamental number-theoretic generation process (Stern-Brocot/`φ(n)`). The crucial Rational Projection map (`φ'`) is now explicitly defined for the main set `Σ'`, satisfying the desired `-1/r` symmetry and mapping bijectively (conjectured) onto `Q`. Its relationship to the intrinsic harmonic ratios is established. The immediate next steps are the rigorous proofs of the bijection `φ': Σ' -> Q` and the count `N(n)`, followed by the explicit definition of the geometric projections.
