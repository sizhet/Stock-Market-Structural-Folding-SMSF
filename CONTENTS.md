
# CONTENTS — Stock-Market Structural Folding (SMSF)

> **Repository map and recommended reading order**

---

## 1. Core Reading Path

The primary SMSF series contains four core articles.

Recommended order:

\[
\boxed{
001 \rightarrow 002 \rightarrow 003 \rightarrow 004
}
\]

Conceptually:

\[
\boxed{
What\ to\ Fold
\rightarrow
How\ to\ Organize
\rightarrow
How\ to\ Expose
\rightarrow
How\ to\ Unfold
}
\]

---

## 2. Core Articles

### SMPF-001 — From Historical Market Data to Folded Structural Experience

**File**

```text
docs/SMPF-001-From-Historical-Market-Data-to-Folded-Structural-Experience.md
````

**Focus**

* historical market experience;
* X-Y-M representation;
* Pattern Discovery;
* Pattern IR;
* Context;
* value-based events;
* multi-granularity episodes;
* provenance;
* structural folding;
* Heavy Fold / Light Unfold foundation.

**Core question**

> What exactly should be folded from historical market data?

---

### SMPF-002 — Pattern Differential Tree

**File**

```text
docs/SMPF-002-Pattern-Differential-Tree.md
```

**Focus**

* Pattern Differential Tree;
* Metric Distance;
* multi-perspective differentiation;
* Context as structural coordinate;
* Event as differential layer;
* Pattern Leaves;
* Leaf CCC;
* structural localization;
* gap detection;
* AI-friendly structural navigation.

**Core question**

> How should historical antecedent structures be organized into a navigable topology?

---

### SMPF-003 — From Pattern Leaves to Decision Interfaces

**File**

```text
docs/SMPF-003-From-Pattern-Leaves-to-Decision-Interfaces.md
```

**Focus**

* RHS outcome organization;
* Y-Buckets;
* Measures;
* Two-Way CCC;
* Pattern Leaf Decision Interface (PLDI);
* uncertainty-preserving folding;
* local statistical / ANN companion models;
* decision provenance;
* multi-leaf and multi-source interface composition.

**Core question**

> Once a relevant Pattern Leaf is found, how should its historical future possibilities be exposed?

---

### SMPF-004 — Composable Unfolding

**File**

```text
docs/SMPF-004-Composable-Unfolding.md
```

**Focus**

* multi-stock composition;
* multi-source composition;
* interface composition;
* Cosine Similarity Scoring Tree;
* user scoring plugins;
* Evidence Space;
* Policy Space;
* On-the-Fly Policy Unfolding;
* AI-agent runtime;
* SQL-like Structural Query APIs;
* provenance and explanation;
* Fold → Unfold → Observe → Gap → Refold loop.

**Core question**

> How can folded evidence become a composable, policy-aware, AI-queryable runtime?

---

# 3. Repository Entry Documents

### README.md

**Purpose**

Repository overview and high-level architecture.

Start here if you want to understand:

* why SMSF exists;
* the complete architecture;
* the four core articles;
* the central design principles;
* the major figures.

---

### START-HERE.md

**Purpose**

A 10–15 minute guided introduction.

Recommended for first-time readers who want the shortest path through:

$$
X\text{-}Y\text{-}M
\rightarrow
Differential\ Tree
\rightarrow
PLDI
\rightarrow
Composable\ Unfolding
$$

---

### CONTENTS.md

**Purpose**

Repository navigation and reading map.

You are here.

---

# 4. Core Figures

The five core figures provide a visual path through the architecture.

---

### Fig-001 — SMPF Grand Map

**File**

```text
figures/Fig-001-SMPF-Grand-Map.png
```

**Shows**

* complete SMSF architecture;
* historical folding;
* structural organization;
* runtime unfolding;
* ecosystem and API direction.

**Best paired with**

```text
README.md
SMPF-001
```

---

### Fig-002 — X-Y-M Pattern Knowledge Unit

**File**

```text
figures/Fig-002-XYM-Pattern-Knowledge-Unit.png
```

**Shows**

* X as antecedent/context;
* Y as outcome/consequent;
* M as measures;
* Pattern Knowledge Unit structure.

**Best paired with**

```text
SMPF-001
```

---

### Fig-003 — Pattern Tree and Leaf Decision Interface

**File**

```text
figures/Fig-003-Pattern-Tree-and-Leaf-Decision-Interface.png
```

**Shows**

* Pattern Differential Tree;
* structural leaf localization;
* PLDI;
* Y outcome branches;
* support;
* measures;
* provenance.

**Best paired with**

```text
SMPF-002
SMPF-003
```

---

### Fig-004 — Multi-Source Composable Unfolding

**File**

```text
figures/Fig-004-Multi-Source-Composable-Unfolding.png
```

**Shows**

* multiple stocks and external sources;
* independent structural folding;
* PLDI composition;
* scoring;
* runtime unfolding.

**Best paired with**

```text
SMPF-004
```

---

### Fig-005 — AI Structural Query Runtime

**File**

```text
figures/Fig-005-AI-Structural-Query-Runtime.png
```

**Shows**

* natural-language or AI query;
* structural parsing;
* leaf localization;
* PLDI retrieval;
* structural operators;
* policy;
* explanation and provenance.

**Best paired with**

```text
SMPF-004
```

---

# 5. README Poster

### README-Poster.png

**File**

```text
figures/README-Poster.png
```

**Purpose**

One-page visual overview of the entire repository.

Recommended for:

* first-time readers;
* GitHub README display;
* ResearchGate supplementary material;
* presentations;
* rapid architecture review.

---

# 6. Recommended Reading Paths

## Path A — 10-Minute Overview

```text
README.md
   ↓
README Poster
   ↓
Fig-001
   ↓
START-HERE.md
```

Goal:

> Understand the whole architecture without reading every article.

---

## Path B — Core Theory

```text
SMPF-001
   ↓
SMPF-002
   ↓
SMPF-003
   ↓
SMPF-004
```

Goal:

> Understand SMSF from historical folding to online composable unfolding.

---

## Path C — Differential Tree

```text
SMPF-001
   ↓
SMPF-002
   ↓
Fig-003
```

Goal:

> Understand structural organization, leaves, Context, Events, and localization.

---

## Path D — Decision Interface

```text
SMPF-003
   ↓
Fig-003
   ↓
SMPF-004
```

Goal:

> Understand PLDI, outcome spaces, scoring, and policy.

---

## Path E — AI / API Runtime

```text
SMPF-004
   ↓
Fig-004
   ↓
Fig-005
```

Goal:

> Understand composable unfolding and AI interaction with folded structural experience.

---

# 7. Core Concept Map

The core SMSF objects can be summarized as:

```text
Historical Observation
        │
        ▼
Pattern Discovery
        │
        ▼
Pattern IR
        │
        ▼
X-Y-M Episode
        │
        ▼
Pattern Differential Tree
        │
        ▼
Pattern Leaf
        │
        ├── Leaf CCC
        └── Historical Y/M
                │
                ▼
          Two-Way CCC
                │
                ▼
               PLDI
                │
                ▼
      Multi-Source Composition
                │
                ▼
             Scoring
                │
                ▼
      On-the-Fly Policy Unfolding
                │
                ▼
 Decision / Explanation / Provenance
```

---

# 8. Core Terms

| Term                            | Meaning                                                        |
| ------------------------------- | -------------------------------------------------------------- |
| **SMSF**                        | Stock-Market Structural Folding                                |
| **X**                           | Antecedent structural pattern / Context                        |
| **Y**                           | Subsequent outcome                                             |
| **M**                           | Quantitative outcome measures                                  |
| **Pattern IR**                  | Intermediate representation of a discovered structural pattern |
| **Pattern Differential Tree**   | Differential organization of historical X-patterns             |
| **Pattern Leaf**                | Localized historical structural population                     |
| **Leaf CCC**                    | Structural summary / runtime handle for a leaf                 |
| **Two-Way CCC**                 | RHS outcome differentiation within a localized leaf            |
| **PLDI**                        | Pattern Leaf Decision Interface                                |
| **Composable Unfolding**        | Runtime composition of multiple decision interfaces            |
| **Policy Space**                | User-specific action space generated from evidence             |
| **On-the-Fly Policy Unfolding** | Dynamic policy materialization at runtime                      |
| **Structural Query API**        | Query interface over folded structural experience              |

---

# 9. Core Architectural Separation

SMSF deliberately separates several concerns.

### Pattern Discovery vs Folding

$$
PatternDiscovery
\perp
FoldingRuntime
$$

### X Localization vs Y Analysis

$$
X
\rightarrow
Localization
$$

before:

$$
Y
\rightarrow
DecisionAnalysis
$$

### Evidence vs Policy

$$
EvidenceFolding
\perp
UserPolicy
$$

### Structural Evidence vs Local Statistical Model

$$
PLDI
\neq
LocalModel
$$

### Structural Score vs Probability

$$
StructuralScore
\neq
Probability
$$

unless explicitly calibrated.

---

# 10. Core Runtime Principles

The repository is built around several recurring principles.

### Preserve Possibilities

$$
Leaf
\rightarrow
PossibilitySpace
$$

rather than immediately:

$$
Leaf
\rightarrow
Winner
$$

### Localize Before Learning

$$
StructuralLocalization
\rightarrow
LocalApproximation
$$

### Compose Interfaces

$$
Scale =
StructuralDecomposition
+
InterfaceComposition
$$

### Separate Evidence from Policy

$$
Evidence
\rightarrow
Policy
\rightarrow
Action
$$

### Heavy Fold, Light Unfold

$$
\boxed{
Heavy\ Offline\ Folding
\rightarrow
Light\ Online\ Unfolding
}
$$

---

# 11. Generalization Boundary

SMSF uses the stock market as its canonical domain.

The architecture may later be investigated for:

```text
Trajectory Episodes
Function Tunnels
Behavioral Histories
Operational Episodes
Calling-Graph Episodes
Other Repeated Decision Systems
```

However, this repository deliberately keeps the primary scope narrow.

The stock market is used to establish the skeleton first.

---

# 12. Suggested Repository Structure

```text
Stock-Market-Structural-Folding-SMSF/
│
├── README.md
├── START-HERE.md
├── CONTENTS.md
│
├── docs/
│   ├── SMPF-001-From-Historical-Market-Data-to-Folded-Structural-Experience.md
│   ├── SMPF-002-Pattern-Differential-Tree.md
│   ├── SMPF-003-From-Pattern-Leaves-to-Decision-Interfaces.md
│   └── SMPF-004-Composable-Unfolding.md
│
├── figures/
│   ├── README-Poster.png
│   ├── Fig-001-SMPF-Grand-Map.png
│   ├── Fig-002-XYM-Pattern-Knowledge-Unit.png
│   ├── Fig-003-Pattern-Tree-and-Leaf-Decision-Interface.png
│   ├── Fig-004-Multi-Source-Composable-Unfolding.png
│   └── Fig-005-AI-Structural-Query-Runtime.png
│
├── FIGURE-INDEX.md
├── GLOSSARY.md
├── FUTURE-DIRECTIONS.md
├── CHANGELOG.md
├── CITATION.cff
└── .zenodo.json
```

---

# 13. Shortest Mental Model

If you remember only one chain, remember:

$$
\boxed{
HistoricalEpisodes
\rightarrow
DifferentialTree
\rightarrow
PLDI
\rightarrow
ComposableUnfolding
}
$$

If you remember only one runtime principle, remember:

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

If you remember only one scaling principle, remember:

$$
\boxed{
Scale\ by\ interface\ composition,
not\ by\ raw\text{-}feature\ concatenation.
}
$$

If you remember only one uncertainty principle, remember:

$$
\boxed{
Preserve\ possibilities\ before\ choosing\ actions.
}
$$

---

# 14. Start Here

For a first reading:

```text
README.md
   ↓
START-HERE.md
   ↓
SMPF-001
   ↓
SMPF-002
   ↓
SMPF-003
   ↓
SMPF-004
```

This is the canonical path through **Stock-Market Structural Folding (SMSF)**.
