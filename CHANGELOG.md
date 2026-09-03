# CHANGELOG

All notable changes to the **Folding–Unfolding Intelligence (FUI)** research repository will be documented in this file.

This repository is a **living research notebook**, not a finalized theory release.

The changelog therefore records changes in:

* research structure,
* definitions,
* hypotheses,
* conceptual boundaries,
* figures,
* experiments,
* case classifications,
* falsification criteria,
* and terminology.

The format is inspired by traditional software changelogs, but adapted for an evolving research program.

---

# [Unreleased]

## Planned

* Add `CASES.md`.
* Add `CASE-TEMPLATE.md`.
* Begin structured candidate-case collection.
* Record rejected / non-FUI cases explicitly.
* Design first Core–Delta vs Enumeration benchmark.
* Define preliminary Foldability measurements.
* Design uncertainty-guided compute experiment.
* Design Decision-Sufficient Unfolding experiment.
* Explore automatic Fold split / merge criteria.
* Investigate Fold migration and portability.
* Refine terminology as experimental evidence appears.

---

# [0.1.0] — Initial Research Framework

**Status:** Research Notebook Foundation
**Research phase:** Conceptual formation
**Theory status:** Provisional

## Added

### Core Repository Structure

Established the initial repository architecture:

```text
Folding-Unfolding-Intelligence/
│
├── README.md
├── START-HERE.md
├── RESEARCH-MAP.md
│
├── docs/
│   ├── FUI-001-Folding-Unfolding-Hypothesis.md
│   ├── FUI-002-What-Makes-a-Good-Fold.md
│   ├── FUI-003-Evolutionary-Advantage-of-Unfolding.md
│   ├── FUI-004-Engineering-Leverage-of-Folding.md
│   ├── FUI-005-Uncertainty-Preserving-Folding.md
│   └── FUI-006-Open-Questions-and-Falsification.md
│
├── figures/
│   ├── Fig-000-Folding-Unfolding-Research-Map.png
│   ├── Fig-001-Enumeration-vs-Structural-Unfolding.png
│   ├── Fig-002-What-Makes-a-Good-Fold.png
│   ├── Fig-003-Evolutionary-Unfolding-Leverage.png
│   ├── Fig-004-Uncertainty-Preserving-Folding.png
│   └── Fig-005-From-Fold-to-Structural-Evolution.png
│
├── GLOSSARY.md
├── FUTURE-DIRECTIONS.md
└── CHANGELOG.md
```

---

## Added — Research Identity

Defined the repository as:

```text
Research Notebook
+
Research Compass
+
Case Laboratory
+
Falsification Workspace
```

The repository is intentionally **not** presented as a completed universal theory or finalized DOI package.

Established the core research question:

> **How can finite structure generate large amounts of useful, adaptive, uncertainty-aware variation without requiring exhaustive enumeration?**

---

## Added — FUI-001

### FUI-001 — The Folding–Unfolding Hypothesis of Intelligence

Introduced the central hypothesis:

> **A major source of intelligence may lie in the ability to fold recurring complexity into reusable core structures and unfold those structures into context-specific representations, behaviors, and actions.**

Introduced the minimal form:

$$
F:X\rightarrow C
$$

and the richer working form:

$$
F(X)\rightarrow(C,\Delta,U)
$$

with:

$$
U_f(C,\Delta,U,K)\rightarrow X'
$$

Defined:

* Core,
* Delta,
* Context,
* Uncertainty,
* Unfolding,
* Unfolding Leverage.

Established the engineering maxim:

> **Do not store every solution. Store the structure that can regenerate the solution space.**

Introduced the scaling proposition:

> **The next scaling frontier may not only be more parameters or more data, but better folds.**

---

## Added — FUI-002

### FUI-002 — What Makes a Good Fold?

Introduced the provisional **Five-Criteria Fold Test**:

$$
GoodFold =
CR+IP+UP+UF+DU
$$

where:

* `CR` — Complexity Reduction
* `IP` — Invariant Preservation
* `UP` — Uncertainty Preservation
* `UF` — Unfoldability
* `DU` — Decision Utility

Established:

$$
BetterFold\neq SmallerFold
$$

Added discussion of:

* Fold Quality,
* Fold Quality Vector,
* Fold Quality Frontier,
* Fold Granularity,
* Delta Ratio,
* Delta Growth,
* Core Stability,
* Fold Drift,
* Fold Lifecycle,
* Split / Merge / Replace.

Introduced the idea that growing Delta complexity may signal a failing Core.

---

## Added — FUI-003

### FUI-003 — The Evolutionary Advantage of Unfolding

Introduced the evolutionary thought experiment:

```text
Enumeration Intelligence
vs
Structural Intelligence
```

Defined the provisional quantity:

$$
UL=
\frac
{\text{Reachable Adaptive Behavioral Space}}
{\text{Stored Structural Complexity}}
$$

Introduced the hypothesis:

> **Evolution may sometimes favor not the organism that stores the most behaviors, but the organism that can generate the most useful behaviors from the least reusable structure.**

Added discussion of:

* behavioral enumeration,
* reusable behavioral generators,
* sample-efficiency leverage,
* search-space reduction,
* risk reduction,
* transfer,
* evolvability,
* distributed Unfolding,
* morphology as possible structural leverage,
* cultural Folding,
* external structural inheritance.

Explicitly classified human and octopus examples as thought experiments rather than established biological explanations.

---

## Added — FUI-004

### FUI-004 — Engineering Leverage of Folding

Developed the engineering interpretation:

```text
Instance Engineering
      ↓
Structural Engineering
      ↓
Core + Delta
      ↓
Selective Unfolding
      ↓
API / Migration / Composition
```

Introduced:

$$
EUL=
\frac
{\text{Useful Operational Capability}}
{\text{Core Cost + Delta Cost + Runtime Cost}}
$$

Established the principle:

> **Structure once; unfold many times.**

Added candidate connections to:

* Calling Graphs,
* Core–Delta code generation,
* runtime invariants,
* world representations,
* Brain Units,
* continual learning,
* APIs,
* migration,
* routing,
* structural scaling.

Introduced the idea of a Fold as a possible future first-class engineering object.

---

## Added — Fold–Policy–Uncertainty Triangle

Introduced the candidate runtime control model:

```text
                 FOLD
                /    \
               /      \
              /        \
         POLICY ------ UNCERTAINTY
```

Defined the three roles:

* **Fold** — what reusable structure applies,
* **Uncertainty** — how strongly the structure should be trusted,
* **Policy** — what behavior is permitted or preferred.

This created a bridge from reusable representation to governed runtime execution.

---

## Added — FUI-005

### FUI-005 — Uncertainty-Preserving Folding

Introduced uncertainty as a first-class structural component:

$$
F(X)\rightarrow(C,\Delta,U)
$$

Established the central proposition:

> **A Good Fold must preserve not only what is known, but also the structure of what is not known.**

Introduced the distinction between:

```text
Uncertainty Compression
```

and:

```text
Uncertainty Destruction
```

Added the engineering maxim:

> **Do not represent every possible world. Represent the structure that can regenerate the relevant uncertainty space when needed.**

---

## Added — Uncertainty-Governed Unfolding

Defined runtime actions:

$$
A\in
\{
Unfold,
Verify,
Explore,
Search,
Ask,
Abstain,
ReFold
\}
$$

Established:

> **Uncertainty should not merely be reported after generation; it may govern whether, where, and how Unfolding occurs.**

Added:

> **Compute should follow uncertainty.**

And:

> **Do not resolve every uncertainty. Resolve only the uncertainty required by the next decision.**

---

## Added — Decision-Sufficient Unfolding

Introduced the distinction between:

$$
WorldStateUncertainty
$$

and:

$$
DecisionUncertainty
$$

Defined **Decision-Sufficient Unfolding** as stopping Unfolding once remaining uncertainty can no longer change the relevant decision.

Added the concept of a:

## Decision-Sufficient Fold

A representation that preserves enough structure and uncertainty for a defined decision family without requiring full world reconstruction.

---

## Added — Uncertainty as a Structural Growth Signal

Introduced the loop:

```text
Persistent Uncertainty
       ↓
Localized Difference
       ↓
Candidate Pattern
       ↓
A/B Comparison
       ↓
Stable Difference
       ↓
New Branch / New Core
```

Established the working proposition:

> **Today's persistent uncertainty may reveal tomorrow's Fold.**

Connected uncertainty management to Structural Continual Learning and Fold evolution.

---

## Added — FUI-006

### FUI-006 — Open Questions, Counterexamples, and Falsification

Added explicit falsification discipline.

Established the central warning:

> **If Folding / Unfolding explains everything, it explains nothing.**

Defined multiple non-FUI and Bad-Fold cases, including:

* reversible but non-structural systems,
* compression without Unfoldability,
* Unfoldability without reuse,
* generation without structure,
* uncertainty-destroying Folds,
* Delta explosion,
* maintenance-dominated Cores,
* environments without reusable invariants.

---

## Added — FUI Boundary Rules

Established permanent guardrails:

### Guardrail 1

> **Bidirectionality alone does not constitute Folding / Unfolding.**

### Guardrail 2

> **Similar structural patterns do not imply identical mechanisms.**

### Guardrail 3

> **A useful FUI framework must explain not only what qualifies as Folding / Unfolding, but also what does not.**

---

## Added — Enumeration as a Legitimate Alternative

Explicitly established:

$$
Enumeration>Folding
$$

under some conditions.

Added likely failure regimes for Folding:

* small problem spaces,
* weak structural regularity,
* low reuse,
* high Fold-discovery cost,
* rapid environmental change,
* high routing overhead,
* unstable Cores,
* excessive uncertainty-preservation cost.

Introduced the practical hybrid principle:

> **Fold the head; enumerate the tail.**

---

## Added — Foldability

Introduced the provisional concept:

$$
\Phi(X)=Foldability
$$

Defined Foldability as the degree to which a problem family contains reusable structure that can produce positive net leverage.

Candidate indicators include:

* stable invariants,
* high reuse,
* small Deltas,
* structural persistence,
* transferable organization.

Established the candidate prediction:

$$
FUIBenefit\propto Foldability
$$

under appropriate resource conditions.

---

## Added — Net Folding Leverage

Introduced:

$$
NFL=
\frac
{\text{Total Useful Benefit}}
{\text{Total Lifecycle Cost}}
$$

to prevent claims based only on compression or storage.

Lifecycle cost explicitly includes:

* discovery,
* Core,
* Delta,
* routing,
* Unfolding,
* validation,
* maintenance,
* uncertainty,
* governance,
* failure.

---

## Added — Structural Falsification

Introduced the possibility that Folds themselves should be challenged during runtime.

Candidate loop:

```text
Core
 ↓
Prediction / Unfolding
 ↓
Observed Result
 ↓
Consistency Test
 ↓
Maintain / Repair / Split / Replace
```

Added the concept:

## Fold Criticism

as the complement of Fold Discovery.

---

## Added — Research Compass

Established six foundational questions:

```text
Q1 — What is a Fold?

Q2 — What makes a Fold good?

Q3 — How is a Fold discovered?

Q4 — When should a Fold unfold?

Q5 — Why does Folding provide leverage?

Q6 — Can Folds themselves evolve?
```

Organized them into:

```text
Representation
Runtime Intelligence
Structural Evolution
```

---

## Added — README

Created a full repository landing page covering:

* FUI overview,
* basic formalization,
* Enumeration vs Structural Unfolding,
* Good Fold criteria,
* evolutionary leverage,
* engineering leverage,
* uncertainty,
* selective Unfolding,
* Structural Evolution,
* falsification,
* reading path,
* repository structure.

Embedded the six research figures at their corresponding conceptual locations.

---

## Added — START-HERE

Created a 10–15 minute orientation path for first-time readers.

Defined the recommended reading order:

```text
README
  ↓
FUI-001
  ↓
FUI-002
  ↓
FUI-004
  ↓
FUI-005
  ↓
FUI-006
  ↓
FUI-003
```

Placed the evolutionary note later in the first-reading path to reduce the risk of biological overgeneralization before the reader understands the framework's boundaries.

---

## Added — RESEARCH-MAP

Created a living research compass connecting:

* foundational questions,
* conceptual dependencies,
* Foldability,
* Core–Delta tradeoffs,
* uncertainty,
* structural evolution,
* experimental tracks,
* runtime architecture,
* migration,
* certification,
* falsification.

Established the preferred research sequence:

```text
Concept
  ↓
Case
  ↓
Operational Definition
  ↓
Benchmark
  ↓
Algorithm
  ↓
Runtime
  ↓
Generalization
```

---

## Added — FUTURE-DIRECTIONS

Created a long-term research agenda.

Established three major phases:

```text
Near Term
Engineering Evidence

Medium Term
Fold Lifecycle / Migration

Long Term
Autonomous Fold Discovery / Evolution
```

Defined candidate experiment series:

```text
FUI-E001 — Fold vs Enumeration Benchmark

FUI-E002 — Delta Ratio and Foldability Sweep

FUI-E003 — Uncertainty-Guided Compute

FUI-E004 — Decision-Sufficient Unfolding

FUI-E005 — Automatic Fold Split

FUI-E006 — Fold Migration
```

Defined candidate algorithm series:

```text
FUI-A001 — Fold Candidate Discovery

FUI-A002 — Fold Quality Evaluation

FUI-A003 — Delta Growth Detector

FUI-A004 — Fold Split / Merge Rules

FUI-A005 — Uncertainty-Governed Router

FUI-A006 — Fold Critic
```

---

## Added — GLOSSARY

Created a terminology reference containing core, provisional, and speculative FUI concepts.

Key terms formalized include:

* Folding,
* Fold,
* Core,
* Delta,
* Unfolding,
* Foldability,
* Good Fold,
* Better Fold,
* Fold Quality,
* Fold Boundary,
* Fold Confidence,
* Fold Discovery,
* Fold Criticism,
* Structural Hallucination,
* UNKNOWN_FOLD,
* Decision-Sufficient Fold,
* Uncertainty-Governed Unfolding,
* Structural Evolution,
* Fold Migration,
* Fold Capital,
* Fold Algebra,
* Fold Interchange Format.

Established permanent terminology distinctions such as:

```text
Folding ≠ Compression

Unfolding ≠ Decompression

Reversibility ≠ FUI

Generation ≠ FUI

Analogy ≠ Mechanism

Smaller Fold ≠ Better Fold

More Certain Fold ≠ Better Fold

More Folding ≠ More Intelligence
```

---

## Added — Figures

Created the initial six-figure visual set:

### Fig-000 — Folding–Unfolding Research Map

Provides the repository-level visual overview.

### Fig-001 — Enumeration vs Structural Unfolding

Visualizes the transition from independent case accumulation to reusable Core + Delta organization.

### Fig-002 — What Makes a Good Fold?

Visualizes Fold-quality criteria and Good-Fold evaluation.

### Fig-003 — Evolutionary Unfolding Leverage

Visualizes the hypothesis that reusable structure may generate larger adaptive behavioral space from limited stored complexity.

### Fig-004 — Uncertainty-Preserving Folding

Visualizes the preservation of uncertainty and uncertainty-governed runtime behavior.

### Fig-005 — From Fold to Structural Evolution

Visualizes the loop from Fold creation through Unfolding, evaluation, structural modification, and Re-Folding.

---

## Changed — Scope Discipline

The initial broad intuition of Folding / Unfolding was deliberately narrowed.

The repository now distinguishes three broad levels:

### Level I — Reversible / Cyclic Dynamics

```text
A ⇄ B
```

Not sufficient for FUI.

### Level II — Structural Folding / Unfolding

```text
Complex Instances
      ↓
Reusable Structure
      ↓
Conditional Expansion
```

Potential FUI.

### Level III — Intelligent Folding / Unfolding

The system participates in:

* Fold discovery,
* uncertainty preservation,
* selective runtime use,
* Fold criticism,
* structural evolution.

---

## Changed — Uncertainty Role

Uncertainty was promoted from a possible output property to a first-class structural and runtime concept.

Earlier simplified form:

$$
F(X)\rightarrow(C,\Delta)
$$

Current working form:

$$
F(X)\rightarrow(C,\Delta,U)
$$

This change significantly expanded the framework from structural reuse toward runtime decision intelligence.

---

## Changed — Research Goal

The repository no longer asks primarily:

> Is Folding / Unfolding universal?

The preferred question is now:

> **Under what conditions does Folding / Unfolding create measurable structural leverage?**

This change makes the framework more falsifiable and experimentally useful.

---

## Changed — Scaling Interpretation

The research focus shifted from:

```text
Bigger Representation
```

toward the possibility of:

```text
Better Structural Organization
```

The current position is not:

```text
Structural Scaling replaces parameter scaling.
```

It is:

$$
Scaling =
ResourceScaling
+
StructuralScaling
$$

as a research hypothesis.

---

## Changed — Evolutionary Framing

Biological and evolutionary examples were explicitly downgraded from explanatory candidates to:

```text
Thought Experiment
Candidate
Speculative
```

unless stronger evidence exists.

The repository prioritizes controlled engineering evidence before stronger biological conclusions.

---

## Changed — Repository Philosophy

Established the permanent repository mode:

```text
Open Research
+
Provisional Framework
+
Falsifiable Hypothesis
```

rather than:

```text
Universal Theory
```

The repository should preserve:

* unresolved questions,
* rejected cases,
* counterexamples,
* negative results.

---

# Research Milestone Summary

The initial research framework now covers:

```text
Definition
    ↓
Good Fold
    ↓
Evolutionary Leverage
    ↓
Engineering Leverage
    ↓
Uncertainty Preservation
    ↓
Falsification
    ↓
Research Map
    ↓
Future Experimental Program
```

The next major transition is:

```text
Conceptual FUI
      ↓
Experimental FUI
```

---

# Permanent Working Principles

The current research program adopts the following working principles:

### 1. Structure Before Enumeration

Search for reusable structure where stable regularity exists.

### 2. Preserve What Matters

Do not obtain leverage by discarding essential invariants.

### 3. Preserve Uncertainty

Do not manufacture certainty through representation alone.

### 4. Unfold Selectively

Compute only what the current context or decision requires.

### 5. Let the Fold Evolve

Persistent Delta growth, uncertainty, and structural mismatch may require Core revision.

### 6. Measure Net Leverage

Count discovery, routing, maintenance, uncertainty, governance, and failure costs.

### 7. Preserve Falsifiability

A useful FUI framework must predict where Folding should fail.

---

# Permanent Research Guardrail

> **If Folding / Unfolding explains everything, it explains nothing.**

---

# Next Research Transition

The highest-value next step is not another broad conceptual expansion.

It is:

```text
Operational Definition
        ↓
Controlled Benchmark
        ↓
Measured Structural Leverage
```

The first target should be a domain in which:

* Core is explicit,
* Delta is measurable,
* Unfolding is controllable,
* an enumeration baseline exists,
* and lifecycle cost can be compared.

---

**Current version:** `0.1.0`
**Repository mode:** Open Research
**Framework status:** Provisional
**Next major phase:** Experimental FUI

