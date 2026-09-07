
# GLOSSARY — Stock-Market Structural Folding (SMSF)

> **Core terminology for the Stock-Market Structural Folding architecture**

---

## SMSF

**Stock-Market Structural Folding**

A structural architecture for folding historical market experience into navigable evidence and unfolding relevant possibilities for online decision support.

Canonical flow:

\[
Historical\ Data
\rightarrow
Structural\ Folding
\rightarrow
Decision\ Interfaces
\rightarrow
Composable\ Unfolding
\]

---

## Historical Observation

A recorded market state at a particular time or interval.

Possible fields include:

```text
Price
Volume
Volatility
Market Context
Events
Macro Variables
Cross-Asset State
````

Historical observations are raw evidence.

They are not yet structurally organized experience.

---

## Historical Episode

A bounded historical segment used as a candidate unit of experience.

An episode may contain:

* an antecedent structure;
* a subsequent outcome;
* quantitative outcome measures;
* Context;
* provenance.

SMSF commonly represents an episode as:

$$
P_i=(X_i,Y_i,M_i)
$$

---

## Pattern

A meaningful recurring or structurally recognizable configuration found in historical observations.

A Pattern may represent:

* price trajectory;
* volume behavior;
* event sequence;
* market regime;
* multi-variable structure;
* domain-specific structural object.

SMSF does not prescribe one universal Pattern definition.

---

## Pattern Discovery

The process that identifies meaningful historical Patterns.

Possible implementations include:

* rule-based algorithms;
* statistical methods;
* trajectory analysis;
* clustering;
* CCC-based methods;
* AI/LLM methods;
* user-defined plugins.

SMSF treats Pattern Discovery as an extensible interface.

$$
PatternDiscovery
\perp
FoldingRuntime
$$

---

## Pattern IR

**Pattern Intermediate Representation**

A structured representation of a discovered Pattern suitable for comparison, differentiation, indexing, and runtime localization.

Pattern IR may encode:

```text
Price Structure
Volume Structure
Trajectory
Events
Context
Graph Structure
CCC
Other Structural Features
```

Different Pattern IRs may coexist.

---

## X

**Antecedent Structure**

The structural condition that exists before a historical outcome.

Examples:

```text
Price Compression
Volume Contraction
Bull Market
Fed Easing
Low Volatility
```

In the Pattern Differential Tree, \(X\) is primarily responsible for localization.

$$
X
\rightarrow
Localization
$$

---

## Y

**Outcome / Consequent**

The historical result that follows \(X\).

Examples:

```text
Strong Rise
Mild Rise
Sideways
Decline
Breakout
Reversal
Trajectory Class
```

Y should normally be defined together with a time horizon.

For example:

$$
Y^{5d}
,\quad
Y^{20d}
,\quad
Y^{60d}
$$

---

## M

**Measures**

Quantitative properties associated with a historical outcome \(Y\).

Examples:

```text
Return
Maximum Drawdown
Volatility
Duration
Recovery Time
Tail Loss
Support
Distribution Statistics
```

M preserves richer information than the outcome label alone.

---

## X–Y–M Pattern Knowledge Unit

A compact representation of historical structural experience:

$$
P=(X,Y,M)
$$

where:

* \(X\) describes the antecedent structure;
* \(Y\) describes the outcome;
* \(M\) describes quantitative consequences.

It is the basic experience unit used by SMSF.

---

## Structural Folding

The process of transforming many historical episodes into a reusable structural organization.

Conceptually:

$$
Many\ Historical\ Episodes
\xrightarrow{Fold}
Navigable\ Structural\ Experience
$$

Structural Folding is not equivalent to prediction.

Its purpose is to preserve useful structure for later retrieval and unfolding.

---

## Good Fold

A fold that balances:

$$
\boxed{
Compression
+
Structural\ Preservation
+
Retrievability
}
$$

A Good Fold reduces complexity without destroying the distinctions required for future unfolding.

---

## Differential

A meaningful distinction used to separate structural populations.

A Differential may arise from:

* metric distance;
* categorical state;
* event type;
* regime;
* trajectory difference;
* structural condition;
* Context.

The key question is:

> Along which dimension do these historical structures meaningfully differ?

---

## Differential Dimension

A coordinate used to organize structural differences.

Examples:

```text
Price Trend
Volume Regime
Volatility State
Market Regime
Fed Policy
Event Type
Sector Context
```

Differential Dimensions may be:

* continuous;
* categorical;
* ordinal;
* event-based;
* graph-based;
* structurally derived.

---

## Metric Distance

A numerical measure used to compare Pattern representations.

Examples may include:

* Euclidean distance;
* Cosine distance;
* trajectory distance;
* domain-specific metrics.

SMSF treats Metric Distance as a tool.

It does not assume:

$$
MetricSimilarity =
StructuralIdentity
$$

---

## Structural Similarity

Similarity defined by meaningful structural relationships rather than only numeric closeness.

Structural Similarity may include:

* matching topology;
* matching Context;
* event equivalence;
* trajectory shape;
* differential path compatibility.

Metric similarity may contribute to Structural Similarity but does not fully define it.

---

## Pattern Differential Tree

A tree that organizes historical \(X\)-patterns according to meaningful structural differences.

Conceptually:

$$
\{X_1,\ldots,X_N\}
\xrightarrow{Differential\ Folding}
T_X
$$

The tree provides:

* structural organization;
* hierarchical differentiation;
* localization;
* explainable traversal paths;
* leaf formation.

---

## Differential Path

The sequence of structural distinctions traversed from the root of a Pattern Differential Tree to a leaf.

For example:

```text
Compression
→ Contracting Volume
→ Bull Market
→ Fed Easing
```

A Differential Path can serve as part of the explanation for why a current Pattern localized to a particular leaf.

---

## Localization

The runtime process of mapping a current Pattern to one or more relevant historical structural regions.

$$
X_q
\rightarrow
L_j
$$

or, for soft localization:

$$
X_q
\rightarrow
\{
(L_i,w_i)
\}
$$

where \(w_i\) represents structural relevance.

---

## Hard Localization

Localization to one primary Pattern Leaf.

$$
X_q
\rightarrow
L_j
$$

Useful when structural boundaries are sufficiently clear.

---

## Soft Localization

Localization to multiple leaves with relevance weights.

$$
X_q
\rightarrow
\{
(L_1,w_1),
\ldots,
(L_k,w_k)
\}
$$

Useful when the current structure lies near boundaries or historical evidence is ambiguous.

---

## Pattern Leaf

A localized historical structural population at the end of a Differential Path.

A Pattern Leaf may contain:

```text
Historical X Population
Historical Y Population
Historical M Population
Context
Leaf CCC
Provenance
Version Metadata
```

The leaf acts as the offline/online handshake.

---

## Leaf CCC

A structural summary or handle associated with a Pattern Leaf.

Leaf CCC helps represent and access the localized structural population.

It does not replace the historical evidence stored or indexed behind the leaf.

---

## CCC

A structural representation used within the broader Structural Intelligence framework.

Within SMSF, CCC may be used as:

* a leaf structural handle;
* a Pattern representation;
* a structural comparison object;
* part of Two-Way CCC analysis.

The exact internal representation may vary by implementation.

---

## Two-Way CCC

A two-sided structural analysis connecting:

1. localized antecedent structure on the \(X\)-side; and
2. differentiated outcome structure on the \(Y/M\)-side.

Conceptually:

$$
X\text{-side Localization}
\rightarrow
Leaf
\rightarrow
Y/M\text{-side Analysis}
$$

Two-Way CCC transforms a Pattern Leaf's historical RHS population into a structured decision-facing interface.

---

## RHS

**Right-Hand Side**

The \(Y/M\) portion of an historical episode:

$$
(X,Y,M)
$$

where:

$$
RHS=(Y,M)
$$

RHS analysis focuses on what happened after the antecedent structure \(X\).

---

## Y-Bucket

A structured category representing a class of historical outcomes.

Examples:

```text
Strong Rise
Mild Rise
Sideways
Mild Decline
Strong Decline
```

A Y-Bucket should usually specify its prediction or observation horizon.

---

## Outcome Horizon

The future interval over which \(Y\) and \(M\) are defined.

Examples:

```text
5 Days
20 Days
60 Days
```

Outcomes with different horizons should not be silently mixed.

---

## Pattern Leaf Decision Interface

**PLDI**

A structured interface exposing the historical RHS possibility space of a Pattern Leaf.

A conceptual PLDI contains:

$$
\{
Y_i,
Score_i,
M_i,
Support_i,
Evidence_i,
Provenance_i
\}
$$

for multiple outcome branches.

The PLDI is a central SMSF runtime contract.

---

## Decision Interface

A structure that exposes possible outcomes, supporting evidence, measures, and scores without necessarily selecting one final action.

A Decision Interface differs from a Decision Answer.

$$
DecisionInterface
\neq
FinalDecision
$$

---

## Possibility Space

The set of historically supported alternative outcomes exposed by a PLDI.

For example:

$$
\{
StrongRise,
MildRise,
Sideways,
Decline
\}
$$

SMSF attempts to preserve the possibility space before later scoring or policy selection.

---

## Uncertainty-Preserving Folding

A folding strategy that retains meaningful alternative historical outcomes rather than collapsing them into one label.

Conceptually:

$$
ManyEpisodes
\rightarrow
FewStructuredOutcomeBranches
$$

without:

$$
FewBranches
\rightarrow
OneForcedAnswer
$$

---

## Uncertainty Recovery

The process of estimating or restoring confidence information during or after unfolding.

Possible mechanisms include:

* local model calibration;
* multi-leaf retrieval;
* multi-source agreement;
* validation data;
* distilled scoring;
* temporal weighting.

Uncertainty Preservation and Uncertainty Recovery are complementary strategies.

---

## Support

The amount of historical evidence associated with a Pattern Leaf or outcome branch.

Examples:

```text
Observation Count
Support Ratio
Temporal Coverage
Regime Coverage
```

Support is evidence strength.

It is not automatically statistical certainty.

---

## Structural Score

A score representing structural relevance or compatibility.

A Structural Score may reflect:

* similarity;
* tree path compatibility;
* source agreement;
* Context match;
* evidence weighting.

A Structural Score is not automatically a probability.

$$
StructuralScore
\neq
Probability
$$

unless explicitly calibrated.

---

## Probability

A statistically defined probability associated with an outcome.

Probabilities may be produced by:

* logistic regression;
* Bayesian models;
* calibrated classifiers;
* other statistical models.

SMSF keeps probabilities semantically separate from Structural Scores.

---

## Policy Utility

A user- or policy-specific evaluation of an outcome or action.

For example:

$$
Utility(Y_i|Preference,PortfolioState)
$$

Policy Utility is not the same as historical frequency, Structural Score, or statistical probability.

---

## Local Model

A statistical or ANN model trained within or near a localized Pattern Leaf.

Possible Local Models include:

* Logistic Regression;
* small MLP;
* Gradient Boosting;
* Bayesian models.

The guiding principle is:

$$
StructuralLocalization
\rightarrow
LocalApproximation
$$

---

## Companion Model

A Local Model that operates alongside the PLDI rather than replacing it.

The PLDI provides historical structural evidence.

The Companion Model provides a statistical estimate.

Their outputs remain distinguishable.

---

## Model Disagreement

A condition where the PLDI and Local Model support different outcomes.

For example:

```text
PLDI:
    Mild Rise favored

Local Model:
    Decline favored
```

Model disagreement may indicate:

* structural gap;
* regime change;
* insufficient support;
* model instability;
* missing Context.

It is therefore useful information.

---

## Evidence Space

The structural space containing historical decision-relevant evidence.

Typical objects include:

```text
Pattern Leaves
PLDIs
Outcomes
Measures
Support
Context
Provenance
```

Evidence Space answers:

> What happened historically under structurally relevant conditions?

---

## Observation Space

The space of current and historical market observations.

$$
O
$$

It may contain:

```text
Prices
Volumes
Events
Context
External State
```

Structural Folding transforms Observation Space into Evidence Space.

---

## Policy Space

The user-specific decision space generated from evidence, preferences, constraints, and current state.

$$
A =
\pi(E,P,S)
$$

where:

* \(E\) = Evidence Space;
* \(P\) = User Preference;
* \(S\) = Portfolio State.

---

## User Preference

A description of what the user values or constrains.

Examples:

```text
Risk Tolerance
Investment Horizon
Maximum Drawdown
Liquidity Requirement
Turnover Limit
Sector Constraint
```

Preference is not market evidence.

---

## Decision Policy

A mapping from evidence and user state to candidate actions.

$$
Action =
\pi(E,P,S)
$$

Policy determines how evidence is interpreted for a specific user or objective.

---

## Evidence Folding

The process of constructing reusable historical evidence independent of one specific user policy.

SMSF generally prefers:

$$
EvidenceFolding
\perp
UserPolicy
$$

This allows the same historical fold to support many policies.

---

## On-the-Fly Policy Unfolding

Dynamic generation of a user-specific Policy Space from localized evidence.

Conceptually:

$$
LocalizedEvidence
+
Preference
+
PortfolioState
\rightarrow
PolicySpace
$$

Policy is materialized when needed rather than necessarily precomputed offline.

---

## Heavy Fold, Light Unfold

A core SMSF runtime principle.

### Heavy Fold

Perform expensive work offline:

```text
Historical Search
Pattern Discovery
Pattern IR
Differential Tree Construction
Leaf Analysis
Two-Way CCC
PLDI Construction
Provenance Indexing
```

### Light Unfold

Perform smaller localized operations online:

```text
Current Pattern
Leaf Localization
PLDI Retrieval
Composition
Scoring
Policy
Explanation
```

Thus:

$$
\boxed{
Heavy\ Fold
\rightarrow
Light\ Unfold
}
$$

---

## Structural Unfolding

The runtime process of retrieving and expanding relevant folded historical evidence for a current observation.

$$
CurrentObservation
\rightarrow
StructuralLocalization
\rightarrow
RelevantPossibilitySpace
$$

Structural Unfolding is broader than simply returning one prediction.

---

## Composable Unfolding

The composition of multiple localized evidence interfaces during runtime.

$$
PLDI_1
+
PLDI_2
+
\cdots
+
PLDI_n
\rightarrow
CompositeEvidence
$$

Sources may include:

* multiple stocks;
* indexes;
* sectors;
* volatility;
* macro variables;
* events;
* multiple granularities.

---

## Interface Composition

Combining standardized decision/evidence interfaces rather than concatenating all raw input features.

Core principle:

$$
\boxed{
Scale\ by\ interface\ composition,
not\ by\ raw\text{-}feature\ concatenation.
}
$$

---

## Structural Decomposition

Breaking a complex decision environment into independently foldable structural sources.

For example:

```text
MSFT
SP500
QQQ
VIX
Fed Events
```

Each can maintain its own Pattern Tree and PLDI.

Structural Decomposition precedes Interface Composition.

---

## Composite Evidence

Evidence produced by combining multiple PLDIs.

$$
E_C =
Compose(
PLDI_1,
\ldots,
PLDI_n
)
$$

Composite Evidence should preserve:

* source identity;
* support;
* conflicts;
* provenance;
* horizon;
* structural relevance.

---

## Multi-Source Composition

Composition across different market or contextual sources.

Examples:

```text
Target Stock
Market Index
Sector ETF
Volatility Index
Interest Rates
Macro Events
Policy Events
```

---

## Multi-Granularity Composition

Composition across different temporal or structural scales.

For example:

$$
PLDI^{1d}
+
PLDI^{5d}
+
PLDI^{20d}
$$

This preserves multiple time perspectives.

---

## Source Agreement

A condition where multiple PLDIs support compatible outcomes.

Agreement can strengthen evidence but does not prove correctness.

$$
Agreement
\neq
Truth
$$

---

## Cross-Source Conflict

A condition where different evidence sources support incompatible outcomes.

Cross-Source Conflict may indicate:

* regime transition;
* unusual local behavior;
* event risk;
* structural mismatch;
* uncertainty.

SMSF preserves conflict rather than automatically hiding it.

---

## Scoring

The process of ranking candidate outcomes using Composite Evidence.

Possible inputs include:

* Structural Similarity;
* support;
* source agreement;
* Context compatibility;
* measures;
* temporal relevance.

Scoring remains a replaceable runtime component.

---

## Scoring Tree

A transparent structure showing how multiple evidence dimensions contribute to a candidate score.

For example:

```text
Candidate Outcome
    │
    ├── Target-Stock Evidence
    ├── Market Evidence
    ├── Event Evidence
    ├── Risk Evidence
    └── Context Evidence
            │
            ▼
       Composite Score
```

---

## Cosine Similarity Scoring Tree

A Scoring Tree using Cosine Similarity as one possible default similarity mechanism.

For vectors \(v_c\) and \(v_e\):

$$
cos(v_c,v_e) =
\frac{v_c\cdot v_e}
{\|v_c\|\|v_e\|}
$$

SMSF does not claim Cosine Similarity is universally optimal.

It is an explicit and replaceable scoring option.

---

## Scoring Plugin

A user- or application-provided scoring implementation.

Possible scorers include:

```text
Default Scorer
Cosine Scorer
Risk-Adjusted Scorer
Domain-Specific Scorer
AI Agent Scorer
```

---

## Structural Query

A query over folded structural objects rather than only raw database rows.

A Structural Query may involve:

```text
Pattern Matching
Leaf Localization
Context Comparison
PLDI Retrieval
Outcome Unfolding
Policy Evaluation
Provenance Tracing
```

---

## Structural Query API

An API exposing operations over folded structural experience.

Possible operations include:

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

---

## Structural Query Interface to Folded Intelligence

The broader idea that an AI or application can query pre-organized structural experience.

Traditional query:

$$
Query
\rightarrow
Rows
$$

SMSF-style query:

$$
Query
\rightarrow
Folded\ Intelligence
$$

This allows runtime access to structural knowledge rather than only raw records.

---

## Data API

The lowest SMSF API layer.

Possible operations include:

```text
GET_PRICES
GET_VOLUME
GET_EVENTS
GET_CONTEXT
```

The Data API accesses raw or normalized observations.

---

## Structural API

The middle SMSF API layer.

Possible operations include:

```text
MATCH_PATTERN
LOCALIZE_LEAF
GET_LEAF_CCC
GET_PLDI
COMPARE_CONTEXT
TRACE_PROVENANCE
```

The Structural API accesses folded knowledge.

---

## Decision API

The upper SMSF API layer.

Possible operations include:

```text
UNFOLD_OUTCOMES
MERGE_INTERFACES
SCORE_CANDIDATES
APPLY_POLICY
COMPARE_POLICIES
EXPLAIN_DECISION
```

The Decision API operates on structural evidence at runtime.

---

## AI Structural Runtime Client

An AI agent that interacts with SMSF through structural and decision APIs.

Instead of rebuilding market structure from raw data for every prompt, the AI can query:

```text
Patterns
Leaves
PLDIs
Outcomes
Measures
Policies
Provenance
```

---

## Provenance

Metadata linking folded structures back to their historical sources.

Possible provenance fields include:

```text
Ticker
Date Range
Historical Episode ID
Pattern IR Version
Tree Version
Leaf ID
Metric Version
Construction Time
Data Source
```

Provenance is preserved through the SMSF runtime.

---

## Decision Provenance

The full trace from a runtime recommendation back to historical evidence.

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
HistoricalEpisode
$$

Decision Provenance supports audit and explanation.

---

## Explanation by Structural Traversal

Explanation derived from the Differential Path used to localize a current Pattern.

For example:

```text
Compression
→ Contracting Volume
→ Bull Market
→ Fed Easing
→ Leaf L-204
```

The traversal itself explains why the historical region was selected.

---

## Explanation by Execution Trace

Explanation derived from the actual runtime computational path.

For example:

```text
Current Pattern
→ Leaf
→ PLDI
→ Multi-Source Composition
→ Scoring
→ Policy
→ Decision
```

This is stronger than producing an unrelated post-hoc explanation.

---

## Context

Information describing the surrounding market or environmental state.

Examples:

```text
Bull/Bear Regime
Interest-Rate Environment
Volatility State
Sector State
Macro Environment
```

Context may be:

* part of \(X\); or
* an explicit Differential Dimension.

---

## Value-Based Event

A semantically meaningful event whose importance is not naturally represented by simple numeric distance.

Examples:

```text
Fed Rate Hike
Fed Rate Cut
Earnings Surprise
Regulatory Event
Geopolitical Event
```

Value-Based Events can become first-class structural coordinates.

---

## Market Context

External or environmental information relevant to historical outcomes.

Market Context describes the world.

It should not be confused with User Preference or Decision Policy.

$$
MarketContext
\neq
UserPreference
\neq
DecisionPolicy
$$

---

## Gap

A condition where existing folded knowledge does not adequately represent a new observation or runtime result.

Possible Gap types include:

```text
No Matching Leaf
Low Structural Similarity
Low Support
Context Mismatch
New Event Type
Cross-Source Conflict
Model Disagreement
```

---

## Structural Gap

A Gap caused by missing, insufficient, or incorrect structural organization.

A Structural Gap may indicate the need for:

* a new branch;
* a new Differential Dimension;
* a new Pattern IR;
* a leaf split;
* a new tree;
* refolding.

---

## Gap Detection

The runtime or validation process that identifies insufficient structural coverage.

Instead of forcing a decision:

$$
Unknown
\not\rightarrow
ForcedPrediction
$$

SMSF can return:

$$
GAP
$$

---

## Refolding

The process of updating structural knowledge after new evidence or detected gaps.

Possible changes include:

```text
New Pattern
New Branch
Leaf Split
New Differential Dimension
Metric Revision
PLDI Update
New Tree Version
```

---

## Structural Market Learning Runtime

A possible future extension of SMSF based on the cycle:

$$
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
$$

This introduces controlled structural evolution over time.

---

## Versioning

The practice of assigning explicit versions to folded structural artifacts.

Versioned objects may include:

```text
Pattern IR
Metric
Differential Tree
Leaf
PLDI
Local Model
Scorer
Policy
```

Versioning supports reproducibility.

---

## Historical Cutoff

The latest historical timestamp available when a fold, PLDI, or model was constructed.

Recording the Historical Cutoff helps prevent look-ahead leakage and makes experiments reproducible.

---

## Look-Ahead Leakage

Use of future information when constructing or evaluating a historical model or fold.

SMSF validation should ensure that:

$$
FutureData
\notin
PastDecisionState
$$

This is essential in market research.

---

## Walk-Forward Validation

A time-aware validation method where training/folding uses historical data available before the validation interval.

Conceptually:

```text
Past
→ Build / Fold
→ Validate on Later Period
→ Move Forward
```

It is generally more appropriate than random splitting for temporally dependent market data.

---

## Non-Stationarity

The property that market relationships change over time.

SMSF must assume that:

$$
HistoricalStructure
$$

may not remain equally relevant forever.

Possible responses include:

* recency weighting;
* regime separation;
* gap detection;
* refolding;
* versioning.

---

## Structural Memory

The view of Pattern Differential Trees and PLDIs as persistent organized historical experience.

Unlike raw storage, Structural Memory is designed for:

* localization;
* retrieval;
* comparison;
* unfolding;
* explanation.

---

## Folded Intelligence

Knowledge that has been structurally compressed and organized while retaining useful relationships for later retrieval and unfolding.

In SMSF:

$$
HistoricalData
\xrightarrow{Fold}
FoldedMarketExperience
$$

Folded Intelligence is not equivalent to one trained parameter set.

It may exist explicitly as trees, leaves, interfaces, measures, and provenance.

---

# Compact Concept Chain

The primary SMSF terminology can be remembered through one chain:

```text
Historical Observation
        ↓
Pattern Discovery
        ↓
Pattern IR
        ↓
X-Y-M Episode
        ↓
Pattern Differential Tree
        ↓
Pattern Leaf
        ↓
Leaf CCC
        ↓
Two-Way CCC
        ↓
PLDI
        ↓
Composable Unfolding
        ↓
Composite Evidence
        ↓
On-the-Fly Policy
        ↓
Decision
        ↓
Provenance
```

Or mathematically:

$$
\boxed{
History
\xrightarrow{Fold}
StructuralEvidence
\xrightarrow{Unfold}
PossibilitySpace
\xrightarrow{Policy}
Decision
}
$$

---

## See Also

* `README.md`
* `START-HERE.md`
* `CONTENTS.md`
* `SMSF-001 — From Historical Market Data to Folded Structural Experience`
* `SMSF-002 — Pattern Differential Tree`
* `SMSF-003 — From Pattern Leaves to Decision Interfaces`
* `SMSF-004 — Composable Unfolding`

