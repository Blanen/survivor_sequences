# Survivor Sequence Framework: Core Definitions and Initial Implications

## 1. Overview

This document outlines the foundational definitions for a mathematical framework built upon constrained periodic binary sequences. The core objects are **Survivor Sequence Classes**, which exhibit specific number-theoretic properties. A central component of the framework is the **Rational Projection Map (`φ'`)**, establishing a bijection between the set of survivor classes with period `n ≥ 2` and the rational numbers `Q`, thereby linking discrete combinatorics to arithmetic and geometry. This document also explores preliminary answers and implications for the immediate goals of the framework based on these definitions.

## 2. Periodic Binary Sequences and Equivalence Classes

**Definition 2.1 (Periodic Binary Sequence):**
An infinite binary sequence `S = (b₁, b₂, b₃, ...)` where `bᵢ ∈ {0, 1}` is **periodic** if there exists a positive integer `n` such that `b_{i+n} = bᵢ` for all `i ≥ 1`.

**Definition 2.2 (Minimal Period):**
The **minimal period** `n` of a periodic sequence `S`, denoted `n = per(S)`, is the smallest positive integer `n` for which `b_{i+n} = bᵢ` holds. The sequence is uniquely defined by its minimal repeating unit (string) `s = (b₁, ..., bₙ)`, and can be written `S = sʷ`.

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
Each class `[S] ∈ Σ'` can be represented by a unique canonical string. If `a` is the predominant digit and `b` the non-predominant, the string starts with `a`, is followed by the pattern `(ab)` repeated `k` times, and concludes with the remaining `n_a - k` instances of `a` appended (where `n_a = count(pred)`).

## 5. The Rational Projection Map (`φ'`)

**Definition 5.1 (Domain and Codomain):**
The **Rational Projection Map** `φ'` maps survivor classes with period `n ≥ 2` to the set of rational numbers `Q`:
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
The classes `[(0)ʷ]` and `[(1)ʷ]` are outside the domain of `φ'`. Conceptually, they correspond to the single point at infinity (`∞`) in the projective rational line `Q P¹`. Specific geometric visualizations must define how these two classes are represented.

**Property 5.4 (Complementation Symmetry):**
Let `τ(S)` denote the complementary sequence where 0s and 1s are swapped. If `[S] ∈ Σ'` and `φ'([S]) ≠ 0`, then `[τ(S)] ∈ Σ'` and the map satisfies:
`φ'([τ(S)]) = -1 / φ'([S])`
*(Note: If `φ'([S]) = 0`, which occurs for `[S]=[01]`, then `[τ(S)]=[S]`. The symmetry holds projectively).*

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

## 7. Preliminary Answers and Implications for Goals

This section addresses the immediate goals for the framework based on the definitions established above.

**7.1 Goal 1: Prove `φ': Σ' -> Q` is a bijection.**
* **Status:** Conjectured. Formal proof required.
* **Plausibility:**
    * *Injectivity:* Seems likely for `r ∈ Q`. Given `r ≠ 0`, the sign determines predominance, and the value `|r|` likely determines the coprime pair `(k, |Δ|)` uniquely via the formula `|r|=|Δ|/k` or `|r|=k/|Δ|` (assuming `gcd(k, |Δ|) = 1` follows from the survivor condition). This pair `(k, |Δ|)`, plus predominance, should uniquely define the class `[S]` via the Stern-Brocot generation.
    * *Surjectivity:* Seems likely. The Stern-Brocot process generates all coprime parameter pairs `(k, n_a)`. Showing that the map `(k, n_a) -> r = φ'([S])` covers all of `Q` requires demonstrating that appropriate pre-image parameters can always be found, potentially via construction algorithms.
* **Note:** If extended to `φ'_{ext}: Σ -> Q P¹` by assigning `∞` to `[0]` and `[1]`, the map is surjective onto `Q P¹` but not injective at `∞`.

**7.2 Goal 2: Prove the count `N(n)` (`N(1)=2, N(n)=φ(n)` for `n>=2`).**
* **Status:** Conjectured based on empirical data and generation mechanism. Formal proof required.
* **Plausibility:** The proof likely involves demonstrating that the survivor condition `gcd(k, max(n0,n1))=1` for minimal period `n` is equivalent to selecting the `φ(n)` classes corresponding to coprime parameter pairs `(k, n_a)` or `(k, n_b)` generated by the Stern-Brocot process where the period `n` equals `k+n_a` or `k+n_b`. This connects the definition to fundamental properties counted by `φ(n)`.

**7.3 Goal 3: Establish relationship between `φ'` and harmonic ratios.**
* **Status:** **Answered.**
* **Result:** Property 6.3 gives the explicit formulas. `φ'([S])` is proportional to the difference `r₁' - r₂'` or its reciprocal, linking the projection value to the relative imbalance `n0-n1` scaled by the total transition count `t=2k`. The formulas are consistent with the `r -> -1/r` symmetry.

**7.4 Goal 4: Develop geometric projections based on `φ'` and handle `[0],[1]`.**
* **Status:** Requires explicit development.
* **Next Steps:** Define geometric projection maps (`ψ` for circle/semicircle, `ψ₄` for double-cover, hyperbolic boundary `ψ_ext`, spinor `ξ`, etc.). These maps will take `r = φ'([S])` for `[S] ∈ Σ'` as input and convert it to coordinates (e.g., angles, points on sphere/disk). Explicit rules must be defined for representing the classes `[0]` and `[1]` (corresponding to `∞`) within each specific visualization (e.g., North/South poles, points `1`/`-1`, points `(0,1)`/`(0,-1)`).

## 8. Summary of Foundational Status

The framework's core objects (`Σ`) and their count (`N(n)`) are consistently defined and appear well-motivated by number theory (`φ(n)`) and combinatorial generation (Stern-Brocot). The Rational Projection map (`φ'`) is now explicitly defined for the main set `Σ'`, satisfying key symmetry properties and relating directly to harmonic ratios. The immediate next steps involve the rigorous proofs of the bijection `φ': Σ' -> Q` and the count `N(n)`, followed by the explicit definition and analysis of the geometric projections.
