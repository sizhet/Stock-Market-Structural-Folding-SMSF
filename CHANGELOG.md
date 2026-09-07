# Changelog

All notable changes to **Stock-Market Structural Folding (SMSF)** will be documented in this file.

This repository follows a research-oriented versioning model:

- **Major versions** — substantial architectural or theoretical changes;
- **Minor versions** — new research components, algorithms, experiments, or runtime capabilities;
- **Patch versions** — corrections, clarifications, metadata updates, and non-breaking documentation improvements.

---

## [1.0.0] — 2026-09-07

### Initial Public Architecture

Version 1.0.0 establishes the initial conceptual architecture of **Stock-Market Structural Folding (SMSF)**:

> **A Differential-Tree Architecture for Historical Evidence Folding and Decision Unfolding**

The release introduces a structural approach for transforming historical market observations into reusable, navigable, composable, and queryable historical experience.

The canonical architecture is:

\[
\boxed{
HistoricalEpisodes
\rightarrow
PatternDifferentialTree
\rightarrow
PLDI
\rightarrow
ComposableUnfolding
}
\]

---

### Added — Historical Experience Folding

Introduced the **X-Y-M historical episode model**:

\[
P_i=(X_i,Y_i,M_i)
\]

where:

- **X** — antecedent structural pattern;
- **Y** — subsequent outcome;
- **M** — quantitative outcome measures.

Established the distinction between:

```text
Historical Data
````

and:

```text
Folded Historical Experience
```

Defined Pattern Discovery and Pattern IR as extensible components rather than fixed assumptions of the SMSF architecture.

---

### Added — Pattern Differential Tree

Introduced the **Pattern Differential Tree** as the primary structural organization for historical X-patterns.

Established:

$$
\{X_1,\ldots,X_N\}
\xrightarrow{Differential\ Folding}
T_X
$$

Key design principles include:

* X-side structural localization;
* multi-granularity differentiation;
* multi-perspective differentiation;
* Metric Distance as a tool rather than structural truth;
* Context as a structural coordinate;
* value-based Events as first-class structural dimensions;
* support for multiple specialized trees;
* explainable Differential Paths;
* Pattern Leaves as localized historical populations.

Established the architectural boundary:

$$
X
\rightarrow
Localization
$$

before:

$$
Y,M
\rightarrow
DecisionAnalysis
$$

---

### Added — Pattern Leaf Decision Interface

Introduced the **Pattern Leaf Decision Interface (PLDI)**.

A PLDI exposes a structured historical possibility space:

$$
PLDI
=
\{
Y_i,
Score_i,
M_i,
Support_i,
Evidence_i,
Provenance_i
\}
$$

rather than prematurely collapsing historical evidence into a single winner.

Established the principle:

$$
\boxed{
Preserve\ possibilities\ before\ choosing\ actions.
}
$$

---

### Added — Two-Way CCC

Introduced **Two-Way CCC** as the structural bridge between:

* localized X-side historical structure; and
* differentiated Y/M-side outcome structure.

Canonical transformation:

$$
PatternLeaf
\rightarrow
Historical(Y,M)
\rightarrow
TwoWayCCC
\rightarrow
PLDI
$$

This turns a Pattern Leaf from a historical cluster into a decision-facing structural interface.

---

### Added — Structural Unfolding

Defined online decision retrieval as **Structural Unfolding** rather than merely prediction.

Canonical online path:

```text
Current Observation
        ↓
Pattern Representation
        ↓
Leaf Localization
        ↓
PLDI Retrieval
        ↓
Evidence Unfolding
```

Established:

$$
CurrentObservation
\xrightarrow{Unfold}
RelevantHistoricalPossibilitySpace
$$

---

### Added — Heavy Fold, Light Unfold

Established the central SMSF runtime principle:

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

Offline processing performs:

* Pattern Discovery;
* Pattern IR construction;
* Differential Tree construction;
* Leaf formation;
* Two-Way CCC analysis;
* PLDI construction;
* provenance indexing.

Online runtime focuses on:

* localization;
* PLDI retrieval;
* evidence composition;
* scoring;
* policy;
* explanation.

---

### Added — Multi-Source Composable Unfolding

Introduced structural composition across independently folded sources.

Examples include:

```text
Target Stock
Market Index
Sector
VIX
Treasury Rates
Macro Context
Fed Events
```

Each source may independently produce:

$$
Source_i
\rightarrow
Tree_i
\rightarrow
PLDI_i
$$

followed by:

$$
PLDI_1+\cdots+PLDI_n
\rightarrow
CompositeEvidence
$$

Established the scaling principle:

> **Scale by interface composition, not by raw-feature concatenation.**

And more generally:

$$
\boxed{
Scale
=
StructuralDecomposition
+
InterfaceComposition
}
$$

---

### Added — Evidence / Policy Separation

Established a strict distinction between:

```text
Market Context
User Preference
Decision Policy
```

with:

$$
MarketContext
\neq
UserPreference
\neq
DecisionPolicy
$$

Defined the canonical evidence architecture as policy-neutral:

$$
\boxed{
EvidenceFolding
\perp
UserPolicy
}
$$

This allows one folded historical evidence system to support multiple user policies.

---

### Added — On-the-Fly Policy Unfolding

Introduced **On-the-Fly Policy Unfolding**.

Given localized evidence \(E\), User Preference \(P\), and current state \(S\):

$$
PolicySpace
=
g(E,P,S)
$$

Policy can be materialized at runtime rather than being permanently embedded into the historical fold.

This establishes the three-space architecture:

$$
ObservationSpace
\xrightarrow{Fold}
EvidenceSpace
\xrightarrow{Policy}
ActionSpace
$$

---

### Added — Local Companion Models

Defined a role for leaf-local statistical or ANN models.

Possible models include:

* Logistic Regression;
* small MLPs;
* Gradient Boosting;
* Bayesian models.

Established:

$$
\boxed{
StructuralLocalization
\rightarrow
LocalApproximation
}
$$

Local models are treated as companions to structural evidence rather than replacements for PLDIs.

---

### Added — Structural / Statistical Disagreement

Introduced disagreement between:

$$
PLDI
$$

and:

$$
LocalModel
$$

as potentially useful runtime information.

Such disagreement may indicate:

* insufficient support;
* regime change;
* structural mismatch;
* model instability;
* missing Context;
* a new structural Gap.

---

### Added — Structural Scores and Probability Separation

Established that:

$$
StructuralScore
\neq
Probability
$$

unless explicit statistical calibration defines such a relationship.

Also distinguished:

* Structural Score;
* support;
* probability;
* similarity;
* Policy Utility.

This prevents different numerical semantics from being silently conflated.

---

### Added — Provenance Architecture

Introduced provenance as a first-class part of structural folding.

Possible provenance includes:

```text
Asset
Historical Time Range
Episode ID
Pattern IR Version
Metric Version
Tree Version
Leaf ID
PLDI Version
Data Source
Historical Cutoff
```

Established the trace:

$$
Decision
\rightarrow
Policy
\rightarrow
CompositeEvidence
\rightarrow
PLDI
\rightarrow
Leaf
\rightarrow
HistoricalEpisodes
$$

---

### Added — Explanation by Structural Traversal

Introduced structural traversal as an intrinsic explanation mechanism.

Example:

```text
Price Compression
→ Volume Contraction
→ Bull Market
→ Fed Easing
→ Leaf L-204
```

The localization path itself records why a historical population was selected.

---

### Added — Explanation by Execution Trace

Extended explanation from localization to the complete runtime:

```text
Current Pattern
→ Leaf
→ PLDI
→ Composition
→ Scoring
→ Policy
→ Decision
```

This establishes:

$$
\boxed{
Explanation\ by\ Execution\ Trace
}
$$

rather than relying solely on post-hoc narrative explanations.

---

### Added — AI Structural Query Direction

Introduced a future AI-native query layer over folded structural experience.

Potential operators include:

```text
PATTERN_MATCH
STRUCTURAL_SIMILARITY
LEAF_LOCALIZE
GET_PLDI
UNFOLD
COMPARE_CONTEXT
MERGE_INTERFACES
POLICY_SCORE
TRACE_PROVENANCE
DETECT_GAP
```

Established the conceptual transition from:

$$
Query
\rightarrow
Rows
$$

to:

$$
\boxed{
Query
\rightarrow
FoldedIntelligence
}
$$

---

### Added — Three-Layer API Model

Defined three possible runtime API layers:

```text
Data API
    ↓
Structural API
    ↓
Decision API
```

The **Data API** accesses observations.

The **Structural API** accesses Patterns, Trees, Leaves, CCCs, and PLDIs.

The **Decision API** performs Unfolding, composition, scoring, policy evaluation, and explanation.

---

### Added — Gap Detection

Introduced runtime Gap Detection for observations not adequately represented by the existing fold.

Candidate Gap signals include:

```text
NO_MATCHING_LEAF
LOW_STRUCTURAL_SIMILARITY
LOW_SUPPORT
CONTEXT_MISMATCH
NEW_EVENT_TYPE
CROSS_SOURCE_CONFLICT
MODEL_DISAGREEMENT
```

Established the principle:

$$
Unknown
\not\rightarrow
ForcedPrediction
$$

A valid runtime result may instead be:

$$
GAP
$$

---

### Added — Structural Evolution Loop

Introduced the longer-term SMSF learning loop:

$$
\boxed{
Fold
\rightarrow
Unfold
\rightarrow
Observe
\rightarrow
Compare
\rightarrow
Gap
\rightarrow
Refold
}
$$

Refolding is intended to be validated and versioned rather than uncontrolled online mutation.

---

### Added — Methodological Boundaries

Version 1.0.0 explicitly establishes several research constraints:

* avoid look-ahead leakage;
* use chronological / walk-forward validation;
* preserve outcome horizons;
* account for overlapping historical episodes;
* recognize market non-stationarity;
* preserve historical market-universe information;
* retain event and data provenance;
* distinguish Structural Similarity from causality;
* expose insufficient support;
* preserve reproducibility through versioning.

---

### Added — Four Core Articles

The initial release establishes four primary documents:

```text
SMPF-001
From Historical Market Data to Folded Structural Experience

SMPF-002
Pattern Differential Tree

SMPF-003
From Pattern Leaves to Decision Interfaces

SMPF-004
Composable Unfolding
```

Together they follow:

$$
\boxed{
What\ to\ Fold
\rightarrow
How\ to\ Organize
\rightarrow
How\ to\ Expose
\rightarrow
How\ to\ Unfold
}
$$

---

### Added — Repository Navigation

Added the repository-level documentation structure:

```text
README.md
START-HERE.md
CONTENTS.md
GLOSSARY.md
FUTURE-DIRECTIONS.md
FIGURE-INDEX.md
CITATION.cff
.zenodo.json
CHANGELOG.md
```

These documents provide:

* architecture overview;
* guided entry path;
* repository navigation;
* terminology;
* future research directions;
* visual navigation;
* citation metadata;
* release history.

---

### Added — Visual Architecture

Established five core figures:

```text
Fig-001 — SMPF Grand Map

Fig-002 — X-Y-M Pattern Knowledge Unit

Fig-003 — Pattern Tree and Leaf Decision Interface

Fig-004 — Multi-Source Composable Unfolding

Fig-005 — AI Structural Query Runtime
```

plus:

```text
README Poster
```

The visual progression is:

$$
\boxed{
Experience
\rightarrow
Structure
\rightarrow
Interface
\rightarrow
Composition
\rightarrow
Runtime
}
$$

---

## Research Scope of v1.0.0

Version 1.0.0 establishes the **architectural skeleton**.

It does not claim to provide:

* a universal market Pattern Discovery algorithm;
* a universal Pattern IR;
* a universal similarity metric;
* a universal trading strategy;
* guaranteed market prediction;
* causal inference from structural similarity;
* a complete production trading platform.

The purpose of the initial release is narrower:

> **Establish a structural architecture for folding historical market experience into navigable evidence and unfolding that evidence through reusable decision interfaces.**

---

## Next

The next development stage should prioritize:

```text
Make the Fold executable.
        ↓
Make the Unfold queryable.
        ↓
Make the Gap measurable.
```

Candidate implementation work includes:

* canonical X-Y-M schema;
* Pattern Discovery plugin contract;
* Pattern IR contract;
* Differential Tree Builder;
* PLDI schema;
* Two-Way CCC implementation;
* runtime localization;
* single-stock canonical demo;
* multi-source composition;
* policy plugin;
* Structural Query API;
* walk-forward validation;
* Gap Detection;
* controlled refolding.

---

## Version Summary

**v1.0.0 establishes:**

$$
\boxed{
HistoricalMarketExperience
\xrightarrow{StructuralFolding}
NavigableEvidence
\xrightarrow{StructuralUnfolding}
DecisionSpace
}
$$

with the central runtime principle:

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

and the central scaling principle:

$$
\boxed{
Scale\ by\ Structural\ Decomposition
+
Interface\ Composition
}
$$
