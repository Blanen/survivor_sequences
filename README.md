# The Survivor Sequence Framework: From Binary Cycles to Harmonic Structures

## Overview

This project aims to rigorously develop a mathematical framework exploring structures emerging from constrained periodic binary sequences. We begin with **survivor sequences** – periodic binary sequences defined by a specific number-theoretic coprimality condition involving pattern counts within their cycle.

A central element of this framework is establishing a fundamental **rational projection**: a bijective map between the equivalence classes of survivor sequences (under cyclic shifts) and the projective rational line `Q P¹ = Q ∪ {∞}`. This map provides a crucial link between the discrete, combinatorial nature of the sequences and the continuous world of numbers and geometry.

Building upon this mapping, we investigate the **harmonic relationship** between different ratios derived from sequence properties. This relationship acts as a key organizing principle, guiding the exploration of emergent geometric structures (such as hyperbolic patterns), algebraic properties (like group actions), and potential connections to other areas of mathematics and physics.

The primary goal is to build this framework step-by-step with mathematical rigor, clearly defining objects, stating assumptions, and proving claims systematically.

## Core Concepts

1.  **Survivor Sequences:**
    *   The foundational objects are periodic binary sequences `S = (b₁, b₂, ..., bₙ)ʷ`. We consider sequences equivalent if they are cyclic shifts of one another, working with these **equivalence classes `[S]`**.
    *   A class `[S]` is a "survivor" if its sequences satisfy: `gcd(count(01), count(pred)) = 1`. Here, `count(01)` is the number of `01` transitions (including wrap-around) in the minimal period, and `count(pred)` is the count of the predominant digit (0 or 1) in that period.
    *   *These objects will be formally defined first, including precise definitions for counts, predominance, and the equivalence relation.*

2.  **Rational Projection (`φ'`):**
    *   We will define and prove the existence of a specific bijective map `φ': {[S]} -> Q P¹` from the set of survivor sequence classes to the projective rational line.
    *   This map is defined by specific rules based on sequence counts (`n0`, `n1`, `n01`), with the key characteristic that:
        *   The class of the all-zero sequence `[(0)ʷ]` maps to `∞`.
        *   The class of the all-one sequence `[(1)ʷ]` maps to `0`.
    *   A crucial property of this chosen map is its simple behavior under **complementation** (swapping 0s and 1s): If `[S]` maps to `r`, its complement class `[τ(S)]` maps to `1/r`.
    *   *The precise formula for `φ'` and the rigorous proof of its bijective property are fundamental early steps.*

3.  **Harmonic Ratios & Relation:**
    *   For survivor classes `[S]` where the counts `n0`, `n1`, `n01` are all non-zero, we will define three associated rational numbers (or "ratios"):
        *   `r₁`: Related to the ratio of '0' count to transitions.
        *   `r₂`: Related to the ratio of '1' count to transitions.
        *   `r₃`: Related to the ratio of the total period length to transitions.
    *   We will demonstrate that these ratios are constrained by a simple linear relationship, referred to as the **Harmonic Relation** (specifically, `r₁ + r₂ = r₃` using appropriately scaled definitions).
    *   *The rigorous definition of these ratios, including careful handling of edge cases like `[(0)ʷ]` and `[(1)ʷ]`, and the precise statement and proof of the harmonic relation are key developments following the rational projection.*

## Development Plan

The framework will be developed progressively, focusing initially on establishing a solid foundation:

1.  **Foundations:**
    *   Formal definition of periodic binary sequences, equivalence classes, counting functions, the survivor property.
    *   Rigorous definition of the chosen rational projection map (`φ'`) and proof of its bijection to `Q P¹`. Analysis of its properties (e.g., under complementation). Exploration of the connection to the Stern-Brocot structure.

2.  **Harmonic Structure:**
    *   Precise definition of the harmonic ratios (`r₁, r₂, r₃`) associated with survivor classes, addressing all edge cases.
    *   Formal statement and proof of the Harmonic Relation connecting these ratios.
    *   Initial exploration of the geometric structure implied by this relation (e.g., embedding points in a space constrained by the relation).

3.  **Geometric & Algebraic Explorations (Future Work):**
    *   Investigating geometric consequences: fractal dimensions, connections to hyperbolic geometry, potential spinor representations.
    *   Exploring algebraic structures: consistency with group actions (e.g., PSL(2, ℤ)), potential interpretations (e.g., F₁ analogies).

## Mathematical Context

This work involves concepts primarily from:

*   Set Theory & Discrete Mathematics
*   Number Theory (Elementary properties, Rationals, Projective Line)
*   Abstract Algebra (Equivalence Relations, Basic Group Theory)
*   (Future work may increasingly involve) (Complex)Geometry, Analysis, Topology, Quantum network-theory

## Status & Goals

This project is commencing with the aim of creating a clean, rigorous, and verifiable mathematical framework based on survivor sequences. The initial focus is exclusively on establishing the foundational definitions and the core rational projection and harmonic relation properties. Feedback and critique focused on mathematical precision and logical consistency are appreciated.
