# Survivor Sequence Framework: Foundational Definitions (Review Version)

## 1. Overview

This document outlines the foundational definitions for a mathematical framework built upon constrained periodic binary sequences. The core objects are **Survivor Sequence Classes**, characterized by number-theoretic constraints based on their minimal period structure. A central component is the **Rational Projection Map (`φ'`)**, establishing a bijection between the set of survivor classes with period `n ≥ 2` and the rational numbers `Q`. This map links discrete combinatorics with the arithmetic structure of rational numbers. The structure implied by `φ'` has a primary geometric interpretation where all rational values (and thus all corresponding sequence classes) are represented on **one semicircle**, distinguishing two main "quarters" based on the sign of the projected rational value.

## 2. Periodic Binary Sequences and Equivalence Classes

**Definition 2.1 (Periodic Binary Sequence):**
An infinite binary sequence `S = (b₁, b₂, b₃, ...)` where `bᵢ ∈ {0, 1}` is **periodic** if there exists a positive integer `n` such that `b_{i+n} = bᵢ` for all `i ≥ 1`.

**Definition 2.2 (Minimal Period):**
The **minimal period** `n` of a periodic sequence `S`, denoted `n = per(S)`, is the smallest positive integer `n` for which `b_{i+n} = bᵢ` holds. The sequence is uniquely defined by its minimal repeating unit (string) `s = (b₁, ..., bₙ)`, and can be written `S = sʷ`.

**Definition 2.3 (Equivalence Class):**
Two periodic sequences `S₁` and `S₂` are **equivalent**, denoted `S₁ ~ S₂`, if one is a cyclic shift of the other. The **equivalence class** `[S]` is the set `{T | T ~ S}`. All sequences in `[S]` share the same minimal period `n`.

## 3. Sequence Parameters (Derived from Minimal Period)

All parameters for a class `[S]` are calculated using its unique minimal period `n` and a representative minimal period string `s = (b₁, ..., bₙ)`. **Definition 3.1 (Counts):**
* `n = per(S)`: Minimal period length (`n ≥ 1`).
* `n0`: Count of `0`s in the string `s`.
* `n1`: Count of `1`s in the string `s`. Note: `n0 + n1 = n`.

**Definition 3.2 (Transition Counts):**
* `k = count(01)`: Count of `0 -> 1` transitions in `s`, including the wrap-around transition `bₙ -> b₁`. `k ≥ 0`. For `n > 1`, `k` equals the count of `1 -> 0` transitions. * `t = count(01) + count(10)`: Total number of transitions. `t = 2k` if `n > 1`; `t = 0` if `n = 1`.

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

**Property 4.3 (Count of Survivor Classes):** The number `N(n)` of survivor classes `[S] ∈ Σ` having minimal period `n` appears to be given by:
* `N(1) = 2`
* `N(n) = φ(n)` for `n ≥ 2`, where `φ` is Euler's totient function.
*(Justification requires formal proof).*

**Property 4.4 (Generation Mechanism):** The set `Σ'` can be generated recursively via a process equivalent to the Stern-Brocot tree construction using mediants applied to the parameters `(k, count(pred))`. **Definition 4.5 (Canonical Representation Rule):** For any equivalence class `[S] ∈ Σ'` (`n ≥ 2`), its **canonical representation** is the unique minimal period string `s*` obtained as follows:
1.  Consider all `n` distinct cyclic shifts `s'` of any minimal period string `s` belonging to `[S]`.
2.  For each shift `s'`, determine the length `L(s')` of its longest initial alternating prefix (i.e., the longest prefix of the form `0101...` or `1010...`).
3.  Identify the set `S_max` of all shifts `s''` for which `L(s'')` is maximal.
4.  The canonical representation `s*` is the lexicographically smallest string within the set `S_max`.
## 5. The Rational Projection Map (`φ'`)

**Definition 5.1 (Domain and Codomain):**
The **Rational Projection Map** `φ'` maps survivor classes with period `n ≥ 2` to the set of rational numbers `Q`:
`φ': Σ' -> Q`
where `Σ' = Σ \ { [(0)ʷ], [(1)ʷ] }`.

**Definition 5.2 (Formula):**
For any survivor class `[S] ∈ Σ'` (`n ≥ 2`, `k ≥ 1`), let `n0, n1, k` be parameters derived from the minimal period `n`. Calculate `Δ = n0 - n1`. The map is defined as:
* If `Δ ≥ 0` (0 is predominant or tied): `φ'([S]) = Δ / k`
* If `Δ < 0` (1 is predominant):       `φ'([S]) = k / Δ`

*(This yields `φ'([(01)ʷ]) = 0`.)*

**Definition 5.3 (Handling `n=1` Cases):**
The classes `[(0)ʷ]` and `[(1)ʷ]` are outside the domain of `φ'`. Conceptually, they correspond to the single point at infinity (`∞`) in `Q P¹`.

**Property 5.4 (Complementation Symmetry):** Let `τ(S)` be the complementary sequence (0s↔1s). If `[S] ∈ Σ'` and `φ'([S]) ≠ 0`, then `[τ(S)] ∈ Σ'` and `φ'([τ(S)]) = -1 / φ'([S])`. **Property 5.5 (Bijection Conjecture):** The map `φ': Σ' -> Q` is **conjectured** to be a **bijection**. *(Proving this formally is Goal #1).*

## 6. Harmonic Ratios

**Definition 6.1 (Harmonic Ratios):**
For any survivor class `[S] ∈ Σ'` (`n ≥ 2`, `t = 2k > 0`):
* `r₁' = n0 / t`
* `r₂' = n1 / t`
* `r₃' = n / t`

**Property 6.2 (Harmonic Relation):** These intrinsic ratios satisfy the linear relation: `r₁' + r₂' = r₃'`.

**Property 6.3 (Relation to `φ'`):** The rational projection `r = φ'([S])` is related to the harmonic ratios by:
* If `r₁' ≥ r₂'` (`Δ ≥ 0`): `φ'([S]) = 2 (r₁' - r₂')`
* If `r₂' > r₁'` (`Δ < 0`): `φ'([S]) = 1 / (2 (r₁' - r₂'))`

## 7. Immediate Goals and Geometric Interpretation

**7.1 Goal 1: Prove `φ': Σ' -> Q` is a bijection.**
* **Status:** Conjectured. Requires formal proof.

**7.2 Goal 2: Prove the count `N(n)` (`N(1)=2, N(n)=φ(n)` for `n>=2`).**
* **Status:** Conjectured. Requires formal proof.

**7.3 Goal 3: Relationship between `φ'` and harmonic ratios.**
* **Status:** **Established.** Property 6.3 gives the explicit relationship.

**7.4 Goal 4: Geometric Interpretation and Projection.**
* **Status:** Requires development.
* **Immediate Geometric Interpretation:** The map `φ'` maps `Σ'` onto `Q`.
* **Primary Visualization (Semicircle Concept):** The primary visualization represents all values `r = φ'([S]) ∈ Q` on **one semicircle** (e.g., the right-hand semicircle, angles `-π/2` to `π/2`).
    * The endpoints represent `r=0` (`[01]ʷ`) (e.g., angle 0) and `r=∞` (conceptually `[0]ʷ`, `[1]ʷ`) (e.g., angle `π/2`).
    * Values `r > 0` (0-predominant) map to the **top-right quarter** (e.g., angles `(0, π/2)`).
    * Values `r < 0` (1-predominant) map to the **bottom-right quarter** (e.g., angles `(-π/2, 0)`).
    * This single semicircle visualization therefore encodes all classes in `Σ'`, partitioning the representation into **two quarters** based on the sign of `r` (predominance).
* **Next Step:** Define an explicit primary geometric projection map (e.g., `ψ: Σ -> S¹` or a semicircle) that implements this specific visualization (mapping all `r ∈ Q` to the chosen semicircle arc and defining representations for `[0]` and `[1]`). Other projections (like a double-cover map) are separate concepts for later development. 
