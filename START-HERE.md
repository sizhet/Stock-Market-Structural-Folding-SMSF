
# START HERE — Stock-Market Structural Folding (SMSF)

> **A 10–15 minute guide to the architecture, core objects, and reading path of SMSF.**

---

## 1. The Question

Stock markets generate enormous amounts of historical data.

But storing historical data is not the same as organizing historical experience.

A conventional market dataset is usually organized around:

\[
Ticker \times Time \times Features
\]

Stock-Market Structural Folding (SMSF) asks a different question:

> **Can historical market experience be folded into a navigable structural form so that relevant possibilities can later be localized, queried, composed, and unfolded?**

The central transformation is:

\[
\boxed{
Raw\ History
\rightarrow
Folded\ Structural\ Experience
\rightarrow
Online\ Decision\ Unfolding
}
\]

---

# 2. The One-Minute Architecture

SMSF has four major steps:

```text
1. Historical Experience
        │
        ▼
      X-Y-M
        │
        ▼
2. Pattern Differential Tree
        │
        ▼
3. Pattern Leaf Decision Interface
        │
        ▼
4. Composable Unfolding
````

Or:

$$
\boxed{
X\text{-}Y\text{-}M
\rightarrow
Differential\ Tree
\rightarrow
PLDI
\rightarrow
Composable\ Unfolding
}
$$

These four steps correspond directly to the four core articles.

---

# 3. Step 1 — Fold Historical Episodes

SMSF begins with historical observations such as:

```text
Price
Volume
Volatility
Market Context
Events
Macro State
Cross-Asset State
```

A Pattern Discovery process identifies meaningful historical episodes.

Each episode is represented as:

$$
P_i=(X_i,Y_i,M_i)
$$

where:

### X — Antecedent Structure

What structural condition existed before the outcome?

### Y — Outcome

What happened afterward?

### M — Measures

How did the outcome occur quantitatively?

For example:

```text
X:
    price compression
    volume contraction
    bull market
    Fed easing

Y:
    mild rise

M:
    20-day return = +4.2%
    max drawdown = -1.8%
    recovery time = 5 days
```

Thus:

$$
\boxed{
X\rightarrow(Y,M)
}
$$

becomes the basic historical experience unit.

---

# 4. Pattern Discovery Is Pluggable

SMSF does not require one universal definition of a market pattern.

A Pattern Discovery plugin may use:

* price/volume structures;
* trajectory signatures;
* CCC representations;
* event sequences;
* technical structures;
* statistical patterns;
* AI-discovered structures;
* domain-specific Pattern IRs.

Therefore:

$$
PatternDiscovery
\perp
StructuralFolding
$$

The SMSF architecture begins after useful structural episodes can be represented.

This allows Pattern Discovery algorithms to evolve without redesigning the entire downstream runtime.

---

# 5. Step 2 — Build the Pattern Differential Tree

Once many historical \(X\)-patterns have been discovered, SMSF must organize them.

A flat collection such as:

```text
Pattern-000001
Pattern-000002
Pattern-000003
...
Pattern-900000
```

is historical storage.

It is not yet structural knowledge.

SMSF therefore constructs:

$$
\{X_1,X_2,\ldots,X_N\}
\xrightarrow{Differential\ Folding}
T_X
$$

where:

$$
T_X
=
Pattern\ Differential\ Tree
$$

---

# 6. What Does "Differential" Mean?

The tree asks:

> **Along which meaningful structural dimensions do these patterns differ?**

For example:

```text
Root
 │
 ├── Price Compression
 │       │
 │       ├── Volume Expansion
 │       │
 │       └── Volume Contraction
 │                 │
 │                 ├── Bull Market
 │                 └── Bear Market
 │
 └── Price Expansion
```

Possible differential dimensions include:

```text
Price Structure
Volume Structure
Trajectory
Volatility
Market Regime
Macro Context
Event State
Cross-Asset State
```

Metric Distance may help construct these differences.

But SMSF does not assume:

$$
MetricSimilarity
=
StructuralIdentity
$$

Metrics operate inside structural semantics.

---

# 7. Context Is a Structural Coordinate

Important Context does not have to be buried inside one large feature vector.

For example:

```text
Same Local Pattern
       │
       ▼
Market Regime
   ├── Bull
   ├── Sideways
   └── Bear
```

This makes it possible to compare:

$$
Outcome(X|Bull)
$$

with:

$$
Outcome(X|Bear)
$$

directly through the structural organization.

---

# 8. Value-Based Events Fit Naturally

Value-based events are particularly important.

For example:

```text
Fed Policy
   │
   ├── Tightening
   ├── Unchanged
   └── Easing
```

An event can be modeled in two ways.

### Event Inside X

Use this when the event is part of the pattern definition itself.

$$
X=(Pattern,Event)
$$

### Event as a Differential Layer

Use this when the goal is to compare the same pattern under different event conditions.

```text
Common Pattern
      │
      ├── Fed Tightening
      ├── Fed Unchanged
      └── Fed Easing
```

This turns previously awkward value-based context into an explicit structural coordinate.

---

# 9. Pattern Leaves

After successive differentiation, the tree reaches localized historical populations:

$$
L_j
$$

A Pattern Leaf may contain:

```text
Structural Path
Leaf CCC
Historical X Population
Historical Y Population
Historical M Population
Context
Provenance
```

The leaf answers:

> **Which historical structural region is relevant?**

It does not yet answer:

> **What should we do?**

That distinction is essential.

---

# 10. Step 3 — Build the Pattern Leaf Decision Interface

Suppose a Pattern Leaf contains:

$$
L_j=
\{
(X_1,Y_1,M_1),
\ldots,
(X_n,Y_n,M_n)
\}
$$

Its historical RHS may contain several different outcomes.

For example:

```text
Strong Rise      22%
Mild Rise        34%
Sideways         26%
Decline          18%
```

SMSF does **not** immediately reduce this to:

```text
Prediction = Mild Rise
```

Instead, Two-Way CCC analysis organizes the RHS evidence into a:

$$
\boxed{
PLDI =
Pattern\ Leaf\ Decision\ Interface
}
$$

---

# 11. What Is a PLDI?

A PLDI exposes a structured historical possibility space.

For example:

```text
PLDI — Leaf L-204

Y1 — Strong Rise
    Structural Score
    Support
    Median Return
    Drawdown
    Evidence
    Provenance

Y2 — Mild Rise
    Structural Score
    Support
    Median Return
    Drawdown
    Evidence
    Provenance

Y3 — Sideways
    ...

Y4 — Decline
    ...
```

Conceptually:

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
\}_{i=1}^{K}
$$

---

# 12. Why Keep Multiple Outcomes?

Because historical structural similarity does not imply deterministic futures.

If the fold stores only:

$$
\arg\max_i Y_i
$$

then much of the historical uncertainty has already been destroyed.

SMSF instead follows:

$$
\boxed{
Preserve\ possibilities\ before\ selecting\ actions.
}
$$

This leaves later runtime stages free to apply:

* different scoring methods;
* different risk preferences;
* different portfolio states;
* different policies;
* different AI agents.

---

# 13. Score Is Not Probability

SMSF keeps numerical semantics explicit.

These are not automatically interchangeable:

$$
StructuralScore
$$

$$
SupportRatio
$$

$$
Probability
$$

$$
Similarity
$$

$$
PolicyUtility
$$

For example:

```text
structural_score = 0.81
```

does **not** automatically mean:

```text
probability = 81%
```

unless a calibrated statistical model explicitly defines it that way.

---

# 14. Optional Local Models

A sufficiently populated Pattern Leaf may also train a local model.

Examples:

```text
Logistic Regression
Small MLP
Gradient Boosting
Bayesian Model
```

The architecture becomes:

```text
Pattern Leaf
   │
   ├── PLDI
   │      └── Structural Historical Evidence
   │
   └── Local Model
          └── Statistical Estimate
```

The model is a companion.

It does not replace the PLDI.

The principle is:

$$
\boxed{
Structural\ Localization
\rightarrow
Local\ Approximation
}
$$

---

# 15. Step 4 — Composable Unfolding

A real market decision rarely depends on one evidence source.

For an MSFT query, relevant sources might include:

```text
MSFT
SP500
QQQ
VIX
Treasury Rates
Fed Events
Sector Context
```

SMSF allows each source to fold independently:

$$
Source_i
\rightarrow
Tree_i
\rightarrow
PLDI_i
$$

Then:

$$
PLDI_1+PLDI_2+\cdots+PLDI_n
\rightarrow
CompositeEvidence
$$

This gives the scaling principle:

$$
\boxed{
Scale\ by\ interface\ composition,
not\ by\ raw\text{-}feature\ concatenation.
}
$$

---

# 16. Why Composition Is Powerful

Different sources can use different internal representations.

For example:

```text
MSFT
    → Price/Volume Pattern IR

SP500
    → Trajectory IR

Fed Events
    → Event IR

VIX
    → Volatility-State IR
```

Yet each can expose a compatible decision-facing interface.

Thus:

$$
Different\ Internal\ Representations
$$

can become:

$$
Compatible\ Structural\ Interfaces
$$

This allows the architecture to scale without requiring one universal representation.

---

# 17. Evidence Before Policy

SMSF makes a strong separation:

$$
MarketContext
\neq
UserPreference
\neq
DecisionPolicy
$$

Historical evidence should normally remain reusable and user-independent.

Thus:

$$
EvidenceFolding
\perp
UserPolicy
$$

One PLDI may support:

```text
Conservative Policy
Aggressive Policy
Income Policy
Risk-Control Policy
Portfolio-Hedging Policy
```

without rebuilding the historical evidence tree.

---

# 18. On-the-Fly Policy Unfolding

Suppose relevant PLDIs have already been localized.

The runtime now possesses:

```text
Outcomes
Measures
Support
Scores
Context
Provenance
```

near the current structural location.

Given:

$$
P_u=UserPreference
$$

and:

$$
S=CurrentPortfolioState
$$

the runtime can generate:

$$
PolicySpace
=
g(PLDI,P_u,S)
$$

on demand.

For example:

```text
Evidence
    │
    ▼
max drawdown < 5%
20-day horizon
low risk tolerance
    │
    ▼
On-the-Fly Policy Space
    │
    ▼
Candidate Ranking
```

There is no need to precompute every possible policy combination.

---

# 19. Heavy Fold, Light Unfold

This leads to one of the simplest descriptions of SMSF:

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

### Offline

Perform the expensive work:

```text
Historical Search
Pattern Discovery
Pattern IR
Differential Folding
Leaf Construction
Two-Way CCC
PLDI Construction
Provenance Indexing
```

### Online

Perform the localized work:

```text
Current Pattern
Leaf Localization
PLDI Retrieval
Composition
Scoring
Policy
Explanation
```

The historical work is reused across many runtime queries.

---

# 20. AI as a Native SMSF Client

SMSF is particularly interesting for AI because the runtime exposes explicit structural objects.

Instead of reasoning only over:

```text
rows
columns
tokens
raw time series
```

an AI can manipulate:

```text
Pattern
Differential Dimension
Tree
Leaf
CCC
PLDI
Outcome
Measure
Context
Event
Policy
Provenance
```

The AI therefore operates over an already-organized historical experience substrate.

---

# 21. Structural Query Interface to Folded Intelligence

Traditional SQL often follows:

$$
Query
\rightarrow
Rows
$$

SMSF suggests:

$$
Query
\rightarrow
StructuralLocalization
\rightarrow
EvidenceUnfolding
\rightarrow
PolicyEvaluation
$$

or more simply:

$$
\boxed{
Query
\rightarrow
Folded\ Intelligence
}
$$

A future AI/SQL-style runtime might support operations such as:

```text
PATTERN_MATCH
STRUCTURAL_SIMILARITY
LEAF_LOCALIZE
UNFOLD
COMPARE_CONTEXT
MERGE_INTERFACES
POLICY_SCORE
TRACE_PROVENANCE
DETECT_GAP
```

---

# 22. Example AI Query

A conceptual query might be:

```text
MATCH PATTERN current_msft

LOCALIZE IN smsf_tree

UNFOLD OUTCOME
FOR horizon = 20d

UNDER CONTEXT
    fed = easing
    sp500_regime = bullish

MERGE
    qqq_context,
    vix_context

APPLY POLICY
    conservative_20d

RETURN
    outcome,
    score,
    support,
    drawdown,
    provenance;
```

The exact language is not defined yet.

The architectural point is that AI can query **folded structural experience**, not merely raw observations.

---

# 23. Explanation Comes from the Runtime

A decision may follow:

```text
Current MSFT Pattern
        │
        ▼
Pattern Differential Tree
        │
        ▼
Leaf L-204
        │
        ▼
PLDI
        │
        ▼
MSFT + SP500 + QQQ + VIX
        │
        ▼
Composite Evidence
        │
        ▼
Conservative Policy
        │
        ▼
Candidate Ranking
```

The same path can be returned as an explanation.

Therefore:

$$
\boxed{
Explanation\ by\ Execution\ Trace
}
$$

is built into the architecture.

---

# 24. Provenance

The runtime should be able to trace:

$$
Decision
\rightarrow
Policy
\rightarrow
CompositeEvidence
\rightarrow
PLDI
\rightarrow
PatternLeaf
\rightarrow
HistoricalEpisodes
$$

This allows a user or AI agent to ask:

> Which historical episodes support this recommendation?

The answer comes from the computational structure itself.

---

# 25. Gap Detection

SMSF should also be able to say:

> Existing folded experience is insufficient.

Possible signals include:

```text
NO_MATCHING_LEAF
LOW_STRUCTURAL_SIMILARITY
LOW_SUPPORT
CONTEXT_MISMATCH
CROSS_SOURCE_CONFLICT
MODEL_DISAGREEMENT
NEW_EVENT_TYPE
```

A system should not force every new observation into an old structure.

Instead:

$$
NewObservation
\rightarrow
Gap
\rightarrow
CandidateStructuralUpdate
$$

This suggests a future learning loop:

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

---

# 26. The Four Core Articles

SMSF is intentionally built around four primary articles.

---

## SMPF-001 — From Historical Market Data to Folded Structural Experience

**Question:**

> What should be folded?

Read this first to understand:

* historical episodes;
* \(X-Y-M\);
* Pattern Discovery;
* Pattern IR;
* structural experience;
* folding objectives.

---

## SMPF-002 — Pattern Differential Tree

**Question:**

> How should historical antecedent structures be organized?

Read this for:

* Differential Trees;
* Metric Distance;
* multi-perspective folding;
* Context;
* value-based events;
* Pattern Leaves;
* Leaf CCC;
* structural localization.

---

## SMPF-003 — From Pattern Leaves to Decision Interfaces

**Question:**

> Once the relevant historical region is found, how should its possible futures be represented?

Read this for:

* RHS analysis;
* Two-Way CCC;
* Y-Buckets;
* Measures;
* PLDI;
* uncertainty preservation;
* local companion models;
* decision provenance.

---

## SMPF-004 — Composable Unfolding

**Question:**

> How does folded evidence become a live runtime?

Read this for:

* multi-stock composition;
* multi-source composition;
* Scoring Trees;
* scoring plugins;
* On-the-Fly Policy Unfolding;
* AI agents;
* SQL-like Structural APIs;
* runtime gap detection.

---

# 27. Recommended Reading Paths

## 10-Minute Path

Read:

```text
README.md
    ↓
Fig-001 — SMPF Grand Map
    ↓
this START-HERE.md
```

Goal:

> Understand the complete architecture.

---

## Core Theory Path

Read:

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

> Understand the full folding/unfolding logic.

---

## Decision Runtime Path

Read:

```text
SMPF-003
    ↓
SMPF-004
```

Goal:

> Understand PLDI, composition, scoring, and policy.

---

## AI/API Path

Read:

```text
SMPF-004
    ↓
Fig-005 — AI Structural Query Runtime
```

Goal:

> Understand how AI can query and manipulate folded structural experience.

---

# 28. Five Core Figures

### Fig-001 — SMPF Grand Map

The complete offline-folding / online-unfolding architecture.

### Fig-002 — X-Y-M Pattern Knowledge Unit

The minimal representation of historical structural experience.

### Fig-003 — Pattern Tree and Leaf Decision Interface

How \(X\)-side localization connects to RHS possibility structure.

### Fig-004 — Multi-Source Composable Unfolding

How independently folded sources compose at runtime.

### Fig-005 — AI Structural Query Runtime

How AI and applications can query folded structural experience.

---

# 29. The Architecture in One Diagram

```text
                         HISTORICAL MARKET

                               │
                               ▼
                       Pattern Discovery
                               │
                               ▼
                         Pattern IR
                               │
                               ▼
                            X-Y-M
                               │
                               ▼
                   Pattern Differential Tree
                               │
                               ▼
                         Pattern Leaf
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
                 Leaf CCC          Historical Y/M
                                          │
                                          ▼
                                    Two-Way CCC
                                          │
                                          ▼
                                         PLDI
                                          │
══════════════════════════════════════════╪════════════════════
                                          │
                                    ONLINE RUNTIME
                                          │
                                          ▼
                                  Current Pattern
                                          │
                                          ▼
                                  Leaf Localization
                                          │
                                          ▼
                                    Relevant PLDIs
                                          │
                              ┌───────────┼───────────┐
                              ▼           ▼           ▼
                           Stock       Market       Events
                              └───────────┼───────────┘
                                          ▼
                                Composite Evidence
                                          │
                                          ▼
                                  Scoring / Agent
                                          │
                                          ▼
                               On-the-Fly Policy
                                          │
                                          ▼
                           Decision / Comparison
                                          │
                                          ▼
                             Explanation / Provenance
```

---

# 30. Eight Principles to Remember

If you remember only eight ideas from this repository, remember these:

### 1.

$$
\boxed{
Historical\ Data
\neq
Historical\ Structural\ Experience
}
$$

### 2.

$$
\boxed{
PatternDiscovery
\perp
FoldingRuntime
}
$$

### 3.

$$
\boxed{
X
\rightarrow
Localization
\quad before \quad
Y
\rightarrow
DecisionAnalysis
}
$$

### 4.

$$
\boxed{
Leaf
\rightarrow
PossibilitySpace
\quad not\ immediately \quad
Leaf
\rightarrow
Winner
}
$$

### 5.

$$
\boxed{
EvidenceFolding
\perp
UserPolicy
}
$$

### 6.

$$
\boxed{
StructuralLocalization
\rightarrow
LocalApproximation
}
$$

### 7.

$$
\boxed{
Scale
=
StructuralDecomposition
+
InterfaceComposition
}
$$

### 8.

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

---

# 31. What This Repository Is Trying to Establish

The first SMSF release does not attempt to solve every stock-market modeling problem.

Its objective is narrower and more foundational:

> **Establish a minimal structural architecture for converting historical market experience into reusable decision interfaces.**

The skeleton is:

$$
\boxed{
HistoricalEpisodes
\rightarrow
PatternDifferentialTree
\rightarrow
PLDI
\rightarrow
ComposableUnfolding
}
$$

Everything else can evolve around this backbone.

---

# 32. Why Start with the Stock Market?

The stock market provides a demanding experimental environment because it combines:

* abundant historical data;
* measurable future outcomes;
* multiple granularities;
* overlapping patterns;
* contextual regimes;
* value-based events;
* uncertainty;
* cross-source interaction;
* changing user policies;
* non-stationarity.

If structural folding can remain useful under these conditions, the architecture may have significance beyond finance.

But SMSF deliberately begins with one concrete domain.

Generalization should follow evidence.

---

# 33. What Comes Later

Potential future work includes:

```text
Pattern IR Contract
Pattern Discovery Plugin API
Metric Plugin API
Differential Tree Builder
PLDI Schema
Two-Way CCC Runtime
Local Model Interface
Multi-Source Composition Engine
Scoring Plugin API
Policy API
Structural Query API
Walk-Forward Validation
Gap Detection
Incremental Refolding
```

These are extensions of the core architecture.

They should not obscure the first-order idea.

---

# 34. Final Mental Model

The simplest way to understand SMSF is this:

### Offline

Ask:

> What happened before, what happened afterward, and how can those experiences be structurally organized?

Then fold:

$$
History
\rightarrow
Structure
$$

### Online

Ask:

> Where does the current situation belong, what historical possibilities live there, and how should they be composed under the current policy?

Then unfold:

$$
CurrentState
\rightarrow
RelevantPossibilitySpace
$$

Together:

$$
\boxed{
History
\xrightarrow{Fold}
StructuralExperience
\xrightarrow{Unfold}
DecisionSpace
}
$$

---

# 35. Start Reading

Begin with:

**SMPF-001 — From Historical Market Data to Folded Structural Experience**

Then continue:

```text
SMPF-001
    ↓
SMPF-002
    ↓
SMPF-003
    ↓
SMPF-004
```

The conceptual progression is:

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

That is the shortest path through **Stock-Market Structural Folding (SMSF)**.

