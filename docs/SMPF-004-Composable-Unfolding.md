
# SMPF-004 — Composable Unfolding: Multi-Source Evidence, On-the-Fly Policy, and AI APIs

**Stock-Market Structural Folding (SMSF)**  
**A Differential-Tree Architecture for Historical Evidence Folding and Decision Unfolding**

---

## Abstract

Stock-Market Structural Folding (SMSF) organizes historical market experience into Pattern Differential Trees and exposes localized RHS evidence through Pattern Leaf Decision Interfaces (PLDIs).

The next architectural problem is runtime composition.

A real decision rarely depends on one stock, one pattern, one tree, one context, or one evidence source. A current decision may simultaneously depend on:

- a target stock;
- a market index;
- a sector ETF;
- volatility conditions;
- interest rates;
- macroeconomic events;
- policy events;
- cross-asset structures;
- multiple granularities;
- multiple pattern representations.

SMSF therefore treats PLDIs as composable evidence interfaces.

Instead of concatenating all raw market features into one increasingly large predictive input, each source may first perform its own structural folding:

\[
Source_i
\rightarrow
Pattern\ Tree_i
\rightarrow
PLDI_i
\]

The resulting interfaces are then composed:

\[
PLDI_1 + PLDI_2 + \cdots + PLDI_n
\rightarrow
Composite\ Evidence\ Space
\]

A scoring layer can rank candidate outcomes using a default framework scorer, a Cosine Similarity Scoring Tree, a user plugin, or an AI agent.

Policy is applied after evidence whenever possible. Because relevant historical evidence has already been localized into a small number of PLDIs, a user-specific Policy Space can often be generated dynamically at runtime:

\[
CompositeEvidence
+
UserPreference
+
PortfolioState
\rightarrow
On\text{-}the\text{-}Fly\ Policy\ Space
\]

This yields the runtime principle:

\[
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
\]

The same structured interfaces also create a natural substrate for AI interaction. Rather than reasoning only over raw rows, AI systems can query Pattern, Leaf, CCC, Outcome, Measure, Context, Policy, Score, and Provenance objects through SQL-like or structural-native APIs.

This article develops composable unfolding as the runtime layer of SMSF and establishes a broader architectural view:

\[
Knowledge\ Infrastructure
+
Runtime
+
API
\]

---

# 1. From One Leaf to a Real Decision

SMSF-003 introduced:

\[
PLDI =
Pattern\ Leaf\ Decision\ Interface
\]

A PLDI exposes the historical outcome space associated with one localized structural region.

Conceptually:

```text
Current Pattern
      │
      ▼
Pattern Differential Tree
      │
      ▼
Pattern Leaf
      │
      ▼
PLDI
      │
      ▼
Historical Possibility Space
````

This is sufficient for a minimal decision query.

However, real market decisions usually require more than one local evidence source.

For example, an MSFT decision may depend on:

```text
MSFT Local Pattern
SP500 Market Structure
QQQ Technology Context
VIX Volatility Regime
Treasury-Yield Structure
Fed Policy Event
Sector Context
```

The runtime therefore needs a composition layer.

---

![Fig-004 — Multi-Source Composable Unfolding](../figures/Fig-004-Multi-Source-Composable-Unfolding.png)

**Fig. 004 — Multi-Source Composable Unfolding.** Independently folded stocks, indexes, market indicators, contexts, and events expose source-local PLDIs that can be aligned and composed into a shared Evidence Space. SMSF therefore scales through structural decomposition and interface composition rather than requiring all information to be collapsed into one raw feature vector.

---

# 2. The Raw-Feature Concatenation Problem

A conventional approach may combine all sources into one vector:

$$
X=
[
X_{MSFT},
X_{SP500},
X_{QQQ},
X_{VIX},
X_{Rates},
X_{Fed},
\ldots
]
$$

This may be useful for some models.

However, as the number of sources grows, several problems appear:

* dimensionality increases;
* representation semantics become entangled;
* missing sources become harder to manage;
* explanation becomes difficult;
* different granularities become mixed;
* domain-specific metrics are lost;
* each new source may require retraining;
* user extensions can affect the entire model.

SMSF proposes another path.

---

# 3. Structural Folding Before Composition

Each source is first allowed to organize its own historical experience.

For example:

$$
MSFT
\rightarrow
T_{MSFT}
\rightarrow
PLDI_{MSFT}
$$

$$
SP500
\rightarrow
T_{SP500}
\rightarrow
PLDI_{SP500}
$$

$$
QQQ
\rightarrow
T_{QQQ}
\rightarrow
PLDI_{QQQ}
$$

$$
FedEvents
\rightarrow
T_{Fed}
\rightarrow
PLDI_{Fed}
$$

Then:

$$
PLDI_{MSFT}
+
PLDI_{SP500}
+
PLDI_{QQQ}
+
PLDI_{Fed}
\rightarrow
CompositeEvidence
$$

This gives SMSF one of its central scaling principles:

$$
\boxed{
Scale\ by\ interface\ composition,
not\ by\ raw\text{-}feature\ concatenation.
}
$$

---

# 4. Why Interface Composition Matters

A standardized PLDI hides internal construction details while exposing decision-relevant evidence.

One source may use:

```text
Trajectory Pattern IR
```

another:

```text
Event Sequence IR
```

another:

```text
CCC
```

another:

```text
Statistical Pattern IR
```

Yet all can expose a compatible downstream interface such as:

```text
Outcome
Score
Measures
Support
Context
Provenance
```

Therefore:

$$
InternalRepresentation_i
$$

can differ while:

$$
DecisionInterface_i
$$

remains composable.

This is a strong modularity property.

---

# 5. PLDI as the Composition Contract

A minimal PLDI contract may contain:

```text
PLDI
│
├── Source ID
├── Leaf ID
├── Structural Path
├── Horizon
├── Outcome Branches
│   ├── Outcome
│   ├── Structural Score
│   ├── Measures
│   ├── Support
│   └── Evidence
├── Context
├── Provenance
└── Version Metadata
```

The exact schema may evolve.

The architectural requirement is simpler:

> A downstream runtime should be able to consume the interface without understanding the complete internal folding algorithm that produced it.

---

# 6. Composite Evidence Space

Given:

$$
PLDI_1,
PLDI_2,
\ldots,
PLDI_n
$$

SMSF constructs a composite evidence object:

$$
E_C =
Compose(
PLDI_1,
PLDI_2,
\ldots,
PLDI_n
)
$$

This composition does not necessarily mean arithmetic averaging.

Instead, it may involve:

* outcome alignment;
* structural similarity;
* context compatibility;
* source weighting;
* support normalization;
* horizon alignment;
* risk alignment;
* provenance retention.

The result is:

$$
\boxed{
Composite\ Evidence\ Space
}
$$

rather than one forced score.

---

# 7. Outcome Alignment

Different PLDIs may expose different outcome spaces.

For example:

```text
MSFT PLDI

Strong Rise
Mild Rise
Sideways
Decline
```

while:

```text
VIX PLDI

Volatility Expansion
Stable Volatility
Volatility Contraction
```

and:

```text
Fed PLDI

Risk-On Response
Neutral Response
Risk-Off Response
```

Before composition, these structures may need to be mapped into a common decision coordinate.

For a target-stock query, that coordinate may be:

$$
TargetOutcome
$$

For a portfolio query:

$$
PortfolioUtility
$$

For a risk query:

$$
RiskState
$$

Thus:

$$
PLDI_i
\rightarrow
DecisionCoordinate
$$

before scoring.

---

# 8. Composition Is Query-Dependent

There need not be one universal composite representation.

Suppose the user asks:

> What is the likely 20-day direction of MSFT?

The composition objective differs from:

> What is the expected drawdown risk of my technology exposure?

or:

> Which of MSFT, NVDA, and AAPL has the strongest structural support under the current Fed regime?

Therefore:

$$
Composition =
f(
Evidence,
QueryObjective
)
$$

The runtime can materialize only the structure needed for the current question.

This keeps online computation small.

---

# 9. Multi-Stock Composition

Consider three target stocks:

$$
S_1,S_2,S_3
$$

Each can independently produce:

$$
PLDI_{S_1},
PLDI_{S_2},
PLDI_{S_3}
$$

A multi-stock runtime can then construct:

$$
CompositePLDI =
Compose(
PLDI_{S_1},
PLDI_{S_2},
PLDI_{S_3}
)
$$

For example:

```text
MSFT
  │
  ▼
PLDI-MSFT ─────┐
               │
AAPL           │
  │            │
  ▼            ├──► Composite Evidence
PLDI-AAPL ─────┤
               │
NVDA           │
  │            │
  ▼            │
PLDI-NVDA ─────┘
```

This makes coordinated decision support a natural extension rather than a fundamentally new model.

---

# 10. Multi-Source Composition

Sources do not have to be stocks.

A runtime may combine:

```text
Target Stock
Market Index
Sector ETF
Volatility Index
Treasury Yield
Dollar Index
Commodity
Macro Event
Policy Event
```

For example:

$$
E_C =
Compose(
PLDI_{MSFT},
PLDI_{SP500},
PLDI_{QQQ},
PLDI_{VIX},
PLDI_{Fed}
)
$$

Each source retains its own structural semantics while participating in a common decision query.

---

# 11. Multi-Granularity Composition

The same source may contribute several granularities.

For example:

$$
PLDI_{MSFT}^{1d}
$$

$$
PLDI_{MSFT}^{5d}
$$

$$
PLDI_{MSFT}^{20d}
$$

These may reveal different structural evidence.

Conceptually:

```text
MSFT 1-Day Structure ──► PLDI-1D ──┐
                                    │
MSFT 5-Day Structure ──► PLDI-5D ──┼──► Composite Evidence
                                    │
MSFT 20-Day Structure ─► PLDI-20D ─┘
```

This allows the runtime to preserve temporal perspective instead of forcing one universal window size.

---

# 12. Multi-Perspective Composition

The same historical data can also be folded from different perspectives.

For example:

```text
Price Perspective
Volume Perspective
Trajectory Perspective
Event Perspective
Macro Perspective
```

Each may produce an independent evidence interface.

Thus:

$$
E_C =
Compose(
PLDI_{price},
PLDI_{volume},
PLDI_{event},
PLDI_{macro}
)
$$

This creates a structural alternative to one giant feature vector.

---

# 13. Composition Should Preserve Source Identity

A composite interface should not erase where evidence came from.

For each candidate outcome, the runtime may retain:

```text
Source Contributions
Structural Scores
Support
Context
Conflicts
Provenance
```

For example:

```text
Candidate: Mild Rise

MSFT Local Pattern:
    support = strong

SP500:
    supportive

QQQ:
    strongly supportive

VIX:
    mildly negative

Fed Context:
    supportive
```

This preserves explanation.

---

# 14. Agreement Across Sources

If multiple independent or semi-independent sources support a similar outcome:

$$
PLDI_1
\approx
PLDI_2
\approx
PLDI_3
$$

their agreement may increase operational confidence.

However:

$$
Agreement
\neq
Truth
$$

Sources may share common historical dependence.

Therefore agreement should be represented as evidence, not automatically converted into certainty.

---

# 15. Disagreement Across Sources

Suppose:

```text
MSFT PLDI:
    bullish

SP500 PLDI:
    bullish

QQQ PLDI:
    neutral

VIX PLDI:
    risk-off

Fed Event PLDI:
    negative
```

This disagreement is itself valuable.

The runtime can expose:

$$
CrossSourceConflict
$$

rather than forcing immediate consensus.

Such disagreement may signal:

* regime transition;
* unusual local behavior;
* event risk;
* cross-market divergence;
* model mismatch;
* insufficient evidence.

---

# 16. Composite Scoring

After evidence composition, candidate outcomes may be scored.

Let:

$$
C=
\{
c_1,c_2,\ldots,c_m
\}
$$

be candidate decision outcomes.

A scoring function computes:

$$
Score(c_i|E_C)
$$

The score may use:

* structural similarity;
* support;
* source agreement;
* context alignment;
* measure compatibility;
* temporal relevance;
* user-defined weights.

The resulting ranking remains separate from user policy.

---

# 17. Cosine Similarity Scoring Tree

A default SMSF implementation may use a Cosine Similarity Scoring Tree.

Suppose a candidate is represented by:

$$
v_c
$$

and the composed evidence state by:

$$
v_e
$$

Then:

$$
cos(v_c,v_e) =
\frac{
v_c \cdot v_e
}{
\|v_c\|\|v_e\|
}
$$

can provide one transparent similarity score.

The important architectural point is not that Cosine Similarity is universally optimal.

It is that the scoring mechanism remains explicit, inspectable, and replaceable.

---

# 18. Scoring Tree Rather Than One Score

Instead of immediately generating one scalar, SMSF may preserve the scoring path.

For example:

```text
Candidate Y1
│
├── Target-Stock Evidence
├── Market Evidence
├── Sector Evidence
├── Event Evidence
├── Risk Evidence
└── Context Evidence
        │
        ▼
Composite Score
```

This can be represented as a **Scoring Tree**.

The final score therefore has provenance.

---

# 19. User Scoring Plugins

SMSF should expose scoring as a replaceable runtime interface.

Conceptually:

```text
Composite Evidence
      │
      ▼
Scoring Interface
      │
      ├── Default Scorer
      ├── Cosine Scorer
      ├── User Plugin
      ├── Domain Model
      └── AI Agent
```

Thus:

$$
Scorer =
Plugin
$$

rather than a hard-coded theoretical commitment.

---

# 20. Why Scoring Should Remain Outside the Canonical Fold

If one scoring function is embedded directly into the historical fold, the same evidence becomes tied to one interpretation.

Keeping scoring external allows:

$$
SameEvidence
+
DifferentScorer
\rightarrow
DifferentRanking
$$

without rebuilding the historical tree.

This improves reuse.

---

# 21. Evidence Before Policy

SMSF distinguishes:

$$
Evidence
$$

from:

$$
Preference
$$

from:

$$
Policy
$$

These objects answer different questions.

### Evidence

What happened historically under structurally similar conditions?

### Preference

What does the user care about?

### Policy

How should evidence and preference be mapped into an action?

This gives:

$$
MarketContext
\neq
UserPreference
\neq
DecisionPolicy
$$

This separation is fundamental.

---

# 22. User Preference

A Preference Profile may include:

```text
Investment Horizon
Risk Tolerance
Maximum Drawdown
Liquidity Constraint
Turnover Limit
Sector Constraint
Concentration Limit
Tax Consideration
Portfolio Exposure
```

For example:

```text
Preference P1

horizon = 20 days
max_drawdown = 5%
risk_tolerance = low
turnover = low
```

These values describe what the user wants.

They do not describe market history.

---

# 23. User Policy

A Policy transforms evidence and preference into decision behavior.

Let:

$$
E =
EvidenceSpace
$$

$$
P =
Preference
$$

$$
S =
PortfolioState
$$

Then:

$$
Action =
\pi(E,P,S)
$$

For example:

```text
If median drawdown > 5%
    reject candidate.

If support < threshold
    downgrade candidate.

Among remaining candidates
    maximize risk-adjusted score.
```

This is a policy, not a market pattern.

---

# 24. Why User Policy Should Usually Not Be Folded into the Main Tree

Suppose the historical tree were constructed around:

```text
Conservative User
```

Then an aggressive user might require a different tree.

This would unnecessarily duplicate historical evidence.

Instead:

$$
HistoricalEvidence
\rightarrow
ReusableFold
$$

then:

$$
ReusableFold
+
Policy_A
\rightarrow
Decision_A
$$

and:

$$
ReusableFold
+
Policy_B
\rightarrow
Decision_B
$$

Thus:

$$
\boxed{
Evidence\ Folding
\perp
User\ Policy
}
$$

---

# 25. On-the-Fly Policy Unfolding

Once the runtime has localized a small set of relevant PLDIs, most evidence is already nearby.

Therefore the system can generate a Policy Space dynamically.

Let:

$$
E_L
$$

be localized leaf evidence.

Then:

$$
PolicySpace =
g(
E_L,
Preference,
PortfolioState,
Constraints
)
$$

This process is:

$$
\boxed{
On\text{-}the\text{-}Fly\ Policy\ Unfolding
}
$$

---

# 26. Why On-the-Fly Policy Can Be Cheap

The expensive historical computation has already happened offline.

Offline:

```text
Historical Scan
Pattern Discovery
Pattern IR
Metric Analysis
Differential Folding
Leaf Construction
Two-Way CCC
PLDI Construction
Provenance Indexing
```

Online:

```text
Current Pattern
Leaf Localization
PLDI Retrieval
Small-Scale Composition
Policy Evaluation
```

Therefore:

$$
OfflineCost
\gg
OnlinePolicyCost
$$

in many implementations.

This motivates:

$$
\boxed{
Heavy\ Fold,\ Light\ Unfold
}
$$

---

# 27. Materialized Policy Space

Suppose a PLDI exposes:

```text
Y1:
    median return = +8%
    median drawdown = -7%

Y2:
    median return = +4%
    median drawdown = -2%

Y3:
    median return = +1%
    median drawdown = -1%
```

A conservative policy may materialize:

```text
Policy Space

Y1
    utility = low
    reason = drawdown exceeds threshold

Y2
    utility = high

Y3
    utility = medium
```

An aggressive policy may produce:

```text
Policy Space

Y1
    utility = highest

Y2
    utility = medium

Y3
    utility = low
```

The PLDI remains unchanged.

---

# 28. Policy Space Is Ephemeral by Default

The canonical historical fold is persistent.

Policy Space may be ephemeral.

Conceptually:

$$
PersistentEvidence
+
CurrentPreference
+
CurrentPortfolioState
\rightarrow
TemporaryPolicySpace
$$

This is useful because:

* portfolio state changes;
* risk tolerance may change;
* available capital changes;
* current exposure changes;
* user objectives change.

There is no need to permanently fold every combination.

---

# 29. Policy Folding as an Optional Second Stage

Some applications may later choose to learn policies historically.

For example:

$$
PLDI
+
HistoricalDecision
+
RealizedOutcome
\rightarrow
PolicyFold
$$

This is legitimate.

However, it is conceptually a second layer:

```text
Layer 1
Historical Evidence Folding

Layer 2
Policy Folding
```

rather than one giant mixed tree.

Thus:

$$
EvidenceFold
\rightarrow
PolicyFold
$$

is preferred over:

$$
Evidence+UserPreference+Policy
\rightarrow
OneMonolithicFold
$$

---

# 30. Three Structural Spaces

SMSF can therefore be described using three spaces.

## Observation Space

$$
O
$$

contains:

```text
Prices
Volumes
Events
Context
External State
```

## Evidence Space

$$
E
$$

contains:

```text
Pattern Leaves
PLDIs
Outcomes
Measures
Support
Provenance
```

## Policy Space

$$
A
$$

contains:

```text
Candidate Actions
Utility
Risk
Constraints
Preference Alignment
```

The runtime transformation is:

$$
O
\xrightarrow{Folding}
E
\xrightarrow{Policy}
A
$$

---

# 31. AI Over Raw Data vs AI Over Folded Structure

An AI system can operate directly on raw market data.

However, raw data provide weak structural handles.

An AI must repeatedly infer:

* pattern boundaries;
* similarity;
* context;
* historical relevance;
* possible outcomes;
* provenance.

SMSF changes the substrate.

The AI can instead receive:

```text
Pattern
Leaf
CCC
Context
Event
Outcome
Measure
Support
Score
Policy
Provenance
```

This is a much more explicit computational environment.

---

# 32. AI as a Structural Runtime Client

An AI agent can operate as a client of the SMSF runtime.

Conceptually:

```text
AI Agent
   │
   ▼
Structural Query API
   │
   ▼
SMSF Runtime
   │
   ├── Pattern Trees
   ├── PLDIs
   ├── Scoring
   ├── Policy
   └── Provenance
```

The AI does not need to reconstruct the entire historical structure on every prompt.

It queries already-folded experience.

---

# 33. A Structural Query Interface to Folded Intelligence

This suggests a broader concept:

$$
\boxed{
Structural\ Query\ Interface\ to\ Folded\ Intelligence
}
$$

Traditional SQL queries data.

SMSF-style structural APIs can query:

$$
Folded\ Experience
$$

The question changes from:

> Which database rows satisfy this predicate?

to:

> Which structural historical regions are relevant to this current situation?

---

![Fig-005 — AI Structural Query Runtime](../figures/Fig-005-AI-Structural-Query-Runtime.png)

**Fig. 005 — AI Structural Query Runtime.** Human and AI clients can operate over folded market experience through structural operations on Patterns, Leaves, PLDIs, Context, Evidence, Policy, and Provenance. Instead of repeatedly reconstructing structure from raw observations, an AI can query and manipulate an explicit structural decision substrate.

---

# 34. Three API Layers

A practical SMSF runtime may expose three API layers.

## Layer 1 — Data API

Examples:

```text
GET_PRICES
GET_VOLUME
GET_EVENTS
GET_CONTEXT
```

This accesses raw or normalized observations.

---

## Layer 2 — Structural API

Examples:

```text
MATCH_PATTERN
LOCALIZE_LEAF
GET_LEAF_CCC
COMPARE_CONTEXT
GET_PLDI
TRACE_PROVENANCE
```

This accesses folded structure.

---

## Layer 3 — Decision API

Examples:

```text
UNFOLD_OUTCOMES
MERGE_INTERFACES
SCORE_CANDIDATES
APPLY_POLICY
COMPARE_POLICIES
EXPLAIN_DECISION
```

This accesses runtime decision operations.

The second and third layers are where SMSF becomes especially useful for AI.

---

# 35. SQL-Like Query Example

A conventional SQL-style query may look conceptually like:

```sql
SELECT
    outcome,
    support,
    median_return,
    median_drawdown
FROM pattern_leaf
WHERE ticker = 'MSFT'
  AND market_regime = 'bull'
  AND fed_policy = 'easing'
  AND horizon = '20d'
ORDER BY structural_similarity DESC;
```

This already moves beyond raw time-series scanning.

However, structural-native operators can go further.

---

# 36. Structural-Native Operators

Possible future operators include:

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

These are not ordinary relational operators.

They operate on folded structural objects.

---

# 37. Structural Query Language Example

A future query might look like:

```text
MATCH PATTERN current_msft
USING price_ir, volume_ir

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
    conservative_01

RETURN
    outcome,
    score,
    support,
    median_return,
    drawdown,
    provenance;
```

The exact syntax is illustrative.

The important point is the computational abstraction.

---

# 38. Querying Folded Intelligence

In a raw database:

$$
Query
\rightarrow
Rows
$$

In SMSF:

$$
Query
\rightarrow
StructuralLocalization
\rightarrow
EvidenceUnfolding
\rightarrow
PolicyEvaluation
$$

Thus:

$$
\boxed{
Query
\rightarrow
Folded\ Intelligence
}
$$

This is a higher-order form of data access.

---

# 39. AI Can Chain Structural Queries

An AI agent may execute a sequence such as:

```text
1. Detect current MSFT pattern.

2. Localize structurally similar leaves.

3. Restrict to Fed-easing regimes.

4. Compare bull and bear contexts.

5. Retrieve 20-day outcome interfaces.

6. Merge MSFT, QQQ, SP500, and VIX evidence.

7. Apply max-drawdown policy.

8. Rank candidate outcomes.

9. Explain the top candidate.

10. Trace supporting historical episodes.
```

This gives:

$$
Query
\rightarrow
Retrieve
\rightarrow
Unfold
\rightarrow
Compare
\rightarrow
Compose
\rightarrow
Policy
\rightarrow
Explain
$$

---

# 40. AI Does Not Need Retraining for Every Query

Because much of the knowledge is stored externally in structured form, many questions can be answered through runtime operations.

For example:

> Re-evaluate MSFT using a 60-day horizon.

may require:

```text
Different PLDI retrieval
+
Different Policy
```

rather than retraining a global model.

Likewise:

> Compare current MSFT under easing vs tightening historical contexts.

can become:

$$
COMPARE\_CONTEXT
$$

rather than a new training task.

---

# 41. Structural Querying Makes the Tree Alive

A static tree is useful.

A queryable tree is substantially more powerful.

Without an API:

```text
Tree
→ Stored Knowledge
```

With an API:

```text
Tree
↔ Human
↔ AI Agent
↔ Policy Runtime
↔ External Applications
```

The tree becomes an active runtime substrate.

It can support:

* retrieval;
* comparison;
* composition;
* counterfactual analysis;
* policy evaluation;
* explanation;
* experimentation.

---

# 42. Human and AI Can Share the Same Runtime

Because the SMSF runtime exposes explicit structural interfaces, both humans and AI systems can operate on the same objects.

A human may ask:

> Why is this leaf relevant?

An AI may call:

```text
TRACE_DIFFERENTIAL_PATH
```

A human may ask:

> What changes if the Fed context is removed?

An AI may call:

```text
COMPARE_CONTEXT
```

A human may ask:

> Show a conservative recommendation.

An AI may call:

```text
APPLY_POLICY conservative
```

Thus the runtime becomes a shared structural workspace.

---

# 43. Explanation by Execution Trace

SMSF explanation can arise from the actual runtime path.

For example:

```text
Current MSFT Pattern
        │
        ▼
Localized to Leaf L-204
        │
        ▼
because:
    compression pattern
    contracting volume
    bull market
    Fed easing
        │
        ▼
PLDI retrieved
        │
        ▼
MSFT + QQQ + SP500 evidence composed
        │
        ▼
Conservative policy applied
        │
        ▼
Mild Rise ranked first
```

This is:

$$
\boxed{
Explanation\ by\ Execution\ Trace
}
$$

rather than explanation generated independently after the decision.

---

# 44. Counterfactual Queries

The structural organization also supports counterfactual comparison.

For example:

```text
Current Pattern:
    same local MSFT structure

Compare:
    Fed Easing
vs
    Fed Tightening
```

The runtime may retrieve:

$$
PLDI(X,FedEasing)
$$

and:

$$
PLDI(X,FedTightening)
$$

then compare their RHS distributions.

This yields:

$$
CounterfactualComparison =
Compare(
Evidence_A,
Evidence_B
)
$$

without requiring the system to claim causal identification.

---

# 45. Structural Counterfactual Does Not Automatically Mean Causality

This distinction is important.

If:

$$
Outcome(X,Event_A)
\neq
Outcome(X,Event_B)
$$

the result demonstrates historical structural difference.

It does not automatically establish:

$$
Event_A
\rightarrow
CausalOutcome
$$

A structural comparison API should therefore distinguish:

```text
Historical Conditional Difference
```

from:

```text
Causal Effect
```

unless a valid causal methodology is explicitly used.

---

# 46. Runtime Gap Detection

A current query may fail to map cleanly to historical evidence.

Possible signals include:

```text
No Matching Leaf
Low Structural Similarity
Low Support
High Cross-Source Conflict
New Event Type
Context Mismatch
Model Disagreement
```

The runtime may return:

$$
GAP
$$

instead of a forced recommendation.

This creates a structural learning loop.

---

# 47. Fold → Unfold → Observe → Compare → Gap → Refold

After a decision horizon completes, realized outcomes become available.

The system can compare:

$$
PredictedPossibilitySpace
$$

with:

$$
ObservedOutcome
$$

Discrepancies can become structural learning signals.

This suggests:

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

This is a natural path toward a **Structural Market Learning Runtime**.

---

# 48. Refolding Does Not Require Immediate Online Mutation

For operational stability, the runtime may separate:

```text
Online Observation
```

from:

```text
Offline Structural Update
```

For example:

```text
Runtime Gap
      │
      ▼
Candidate Update Queue
      │
      ▼
Offline Validation
      │
      ▼
Tree Rebuild / Leaf Split / New Branch
      │
      ▼
New Tree Version
```

This preserves reproducibility.

---

# 49. Provenance Must Survive Composition

When multiple PLDIs are composed, provenance must not disappear.

A final decision trace may be:

```text
Decision
   │
   ▼
Policy
   │
   ▼
Composite Score
   │
   ├── MSFT PLDI
   │      └── Leaf L-204
   │
   ├── SP500 PLDI
   │      └── Leaf L-087
   │
   ├── QQQ PLDI
   │      └── Leaf L-122
   │
   └── Fed PLDI
          └── Leaf L-011
```

Each leaf can then trace to historical episodes.

Thus:

$$
Decision
\rightarrow
CompositeEvidence
\rightarrow
SourcePLDI
\rightarrow
Leaf
\rightarrow
HistoricalEpisode
$$

---

# 50. Versioned Runtime Decisions

A reproducible decision should record:

```text
Decision ID
Decision Time
Query
Current Pattern IR
Tree Versions
PLDI Versions
Scorer Version
Policy Version
Portfolio State
Source Set
Outcome Horizon
```

This makes later audit possible.

A recommendation should not be detached from the versions that produced it.

---

# 51. A Canonical Online Runtime

A compact SMSF runtime can be written as:

```text
Current Market State
        │
        ▼
Pattern Discovery / Pattern IR
        │
        ▼
Tree Localization
        │
        ▼
PLDI Retrieval
        │
        ▼
Multi-Source Composition
        │
        ▼
Composite Evidence
        │
        ▼
Scoring
        │
        ▼
On-the-Fly Policy Unfolding
        │
        ▼
Decision Report
        │
        ▼
Provenance / Explanation
```

This is the online counterpart of Offline Structural Folding.

---

# 52. Minimal Decision Report

A runtime report may contain:

```text
Target:
    MSFT

Horizon:
    20 days

Localized Leaves:
    MSFT-L204
    SP500-L087
    QQQ-L122
    VIX-L041

Candidate Outcomes:

    Mild Rise
        structural score = ...
        support = ...
        median return = ...
        median drawdown = ...

    Strong Rise
        structural score = ...
        support = ...
        median return = ...
        median drawdown = ...

    Sideways
        ...

Policy:
    conservative_20d

Policy Ranking:
    1. Mild Rise
    2. Sideways
    3. Strong Rise

Warnings:
    cross-source disagreement = moderate

Provenance:
    available
```

The report should preserve typed evidence rather than presenting one unexplained number.

---

# 53. Three Parallel Runtime Reports

A richer SMSF runtime may produce:

## Structural Historical Report

Derived from:

$$
PLDI
$$

## Local Statistical Report

Derived from:

$$
LocalModel
$$

## Policy Report

Derived from:

$$
PLDI
+
Preference
+
PortfolioState
$$

These three views should remain distinguishable.

---

# 54. Decision as a Runtime Materialization

The historical fold is persistent.

The final decision is often temporary.

Thus:

$$
Decision =
Materialize(
CurrentState,
FoldedEvidence,
Policy
)
$$

This is a useful architectural distinction.

SMSF stores reusable historical structure.

It materializes decisions on demand.

---

# 55. Knowledge Infrastructure + Runtime + API

At this point, SMSF can be understood as three layers.

## Layer 1 — Knowledge Infrastructure

```text
Historical Data
Pattern Discovery
Pattern IR
Pattern Differential Trees
Leaf CCC
PLDI
Provenance
```

## Layer 2 — Runtime

```text
Localization
Composition
Scoring
Policy Unfolding
Gap Detection
Decision Trace
```

## Layer 3 — API

```text
Human Queries
AI Agents
SQL-Like Queries
Structural Operators
Application Integrations
```

Thus:

$$
\boxed{
SMSF =
Knowledge\ Infrastructure
+
Runtime
+
API
}
$$

---

# 56. What SMSF Is Not

SMSF should not be interpreted as:

### A guaranteed trading system

Historical structural similarity does not guarantee future return.

### A single machine-learning model

SMSF is an architecture capable of incorporating multiple models.

### A fixed pattern library

Pattern discovery and Pattern IR are extensible.

### A single giant tree

Multiple trees and interfaces may coexist.

### A fixed policy

Policies can be supplied dynamically.

### A claim of causal inference

Historical conditional comparison is not automatically causal inference.

These boundaries are important.

---

# 57. General Architectural Pattern

Although developed in a stock-market setting, the runtime structure can be expressed more generally:

$$
HistoricalEpisodes
\rightarrow
StructuralFolding
\rightarrow
DecisionInterfaces
\rightarrow
ComposableUnfolding
\rightarrow
Policy
$$

This may later be applicable to other domains containing:

* repeated historical episodes;
* identifiable antecedent structure;
* measurable outcomes;
* reusable local evidence;
* decision-dependent policies.

Examples may include:

* trajectories;
* function tunnels;
* behavioral episodes;
* operational histories;
* calling-graph episodes.

Such generalization is intentionally left outside the primary scope of the SMSF repository.

---

# 58. Core Claims

This article makes the following architectural claims.

### Claim 1 — PLDIs can serve as composable evidence interfaces.

Different historical structures can be folded independently and combined at runtime.

### Claim 2 — Multi-source scaling need not require raw-feature concatenation.

Structural decomposition followed by interface composition provides an alternative scaling strategy.

### Claim 3 — Composition should preserve source identity and disagreement.

Conflict among evidence sources is itself useful information.

### Claim 4 — Scoring should remain replaceable.

Default framework scoring, Cosine Similarity, user plugins, and AI agents can coexist.

### Claim 5 — Evidence and policy should normally remain separate.

Reusable historical evidence should not be permanently coupled to one user's decision preference.

### Claim 6 — Policy Space can often be materialized online.

Localized leaf evidence makes user-specific policy generation computationally lightweight.

### Claim 7 — Heavy Fold, Light Unfold is a useful runtime principle.

Expensive structural work is performed offline; online computation focuses on localization, composition, policy, and explanation.

### Claim 8 — AI can operate naturally over folded structural objects.

Pattern, Leaf, Outcome, Measure, Policy, and Provenance provide explicit handles for AI reasoning.

### Claim 9 — SQL-like and structural-native APIs can turn folded knowledge into an interactive runtime substrate.

### Claim 10 — Runtime disagreement and failed localization can become structural learning signals.

---

# 59. Design Principles

The major design principles established across SMSF can now be summarized.

### Principle 1

$$
Historical\ Data
\neq
Historical\ Knowledge
$$

### Principle 2

$$
Pattern\ Discovery
\perp
Folding\ Machinery
$$

### Principle 3

$$
X
\rightarrow
Localization
$$

before:

$$
Y
\rightarrow
Decision\ Analysis
$$

### Principle 4

$$
Leaf
\rightarrow
Possibility\ Interface
$$

not immediately:

$$
Leaf
\rightarrow
Winner
$$

### Principle 5

$$
Evidence\ Folding
\perp
User\ Policy
$$

### Principle 6

$$
Scale =
Structural\ Decomposition
+
Interface\ Composition
$$

### Principle 7

$$
Heavy\ Fold
\rightarrow
Light\ Unfold
$$

### Principle 8

$$
Query
\rightarrow
Folded\ Intelligence
$$

rather than only:

$$
Query
\rightarrow
Raw\ Rows
$$

---

# 60. Canonical SMSF Architecture

The complete SMSF architecture can be summarized as:

```text
                       OFFLINE

Historical Market Data
        │
        ▼
Pattern Discovery Plugin
        │
        ▼
Pattern IR Plugin
        │
        ▼
X-Y-M Historical Episodes
        │
        ▼
Pattern Differential Folding
        │
        ▼
Pattern Differential Trees
        │
        ▼
Pattern Leaves
        │
        ├── Leaf CCC
        ├── Historical Y/M
        ├── Provenance
        └── Optional Local Model
        │
        ▼
Two-Way CCC
        │
        ▼
Pattern Leaf Decision Interfaces
        │
        │
════════╪══════════════════════════════════
        │
        │                ONLINE
        ▼
Current Market State
        │
        ▼
Current Pattern IR
        │
        ▼
Leaf Localization
        │
        ▼
Relevant PLDIs
        │
        ├── Target Stock
        ├── Market Index
        ├── Sector
        ├── Volatility
        ├── Macro
        └── Events
        │
        ▼
Multi-Source Interface Composition
        │
        ▼
Composite Evidence Space
        │
        ▼
Scoring Tree / Plugin / Agent
        │
        ▼
On-the-Fly Policy Unfolding
        │
        ▼
Decision Space
        │
        ▼
Recommendation / Comparison / Explanation
        │
        ▼
Provenance Trace
```

---

# 61. The Central Runtime Equation

SMSF can be summarized operationally as:

$$
\boxed{
Raw\ History
\rightarrow
Pattern\ IR
\rightarrow
Differential\ Folding
\rightarrow
Decision\ Interface
\rightarrow
Composable\ Unfolding
\rightarrow
Policy\ Decision
}
$$

The architecture separates three expensive conceptual problems:

$$
Recognition
$$

$$
Evidence
$$

$$
Policy
$$

and allows them to interact through explicit interfaces.

---

# 62. Conclusion

Stock-Market Structural Folding begins by transforming raw market history into reusable structural experience.

Historical patterns are represented as:

$$
(X,Y,M)
$$

Their antecedent structures are organized through Pattern Differential Trees.

Their localized future outcomes are exposed through Pattern Leaf Decision Interfaces.

Composable Unfolding completes the runtime path.

Rather than constructing one monolithic predictive input, multiple stocks, indexes, events, contexts, and granularities can first perform local structural folding and then expose standardized interfaces.

These interfaces can be composed, scored, queried, and evaluated under dynamically generated policies.

This yields:

$$
\boxed{
Fold\ evidence\ offline.
}
$$

$$
\boxed{
Unfold\ possibilities\ online.
}
$$

$$
\boxed{
Materialize\ policy\ when\ needed.
}
$$

AI systems can then interact with the same structural substrate through explicit runtime operations.

The result is not merely a stock prediction model.

It is a possible architecture for:

$$
\boxed{
Queryable,\ Composable,\ Policy\text{-}Aware\ Folded\ Market\ Experience
}
$$

The stock market provides the canonical domain.

The deeper architectural idea is that historical experience can be folded into structures that remain alive because they can later be localized, queried, composed, unfolded, scored, traced, and reinterpreted.

---

## SMSF Core Series

1. **SMSF-001 — From Historical Market Data to Folded Structural Experience**

2. **SMSF-002 — Pattern Differential Tree: Structural Organization of Market Experience**

3. **SMSF-003 — From Pattern Leaves to Decision Interfaces**

4. **SMSF-004 — Composable Unfolding: Multi-Source Evidence, On-the-Fly Policy, and AI APIs**

Together:

$$
Historical\ Experience
\rightarrow
Structural\ Folding
\rightarrow
Decision\ Interfaces
\rightarrow
Composable\ Unfolding
$$

---

## Repository

**Stock-Market Structural Folding (SMSF)**

A differential-tree architecture for folding historical market experience into navigable structural evidence and unfolding that evidence through composable, policy-aware, AI-queryable runtime interfaces.


