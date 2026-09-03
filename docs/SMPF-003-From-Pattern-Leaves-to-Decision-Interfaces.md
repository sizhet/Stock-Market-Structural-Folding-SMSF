````markdown
# SMPF-003 — From Pattern Leaves to Decision Interfaces

**Stock-Market Structural Folding (SMSF)**  
**A Differential-Tree Architecture for Historical Evidence Folding and Decision Unfolding**

---

## Abstract

In Stock-Market Structural Folding (SMSF), the Pattern Differential Tree organizes historical antecedent structures \(X\) into localized structural populations.

A Pattern Leaf therefore answers:

> Which historical episodes are structurally relevant to the current pattern?

However, localization alone does not produce a decision.

Each leaf still contains a population of historical RHS outcomes:

\[
\{
(Y_1,M_1),
(Y_2,M_2),
\ldots,
(Y_n,M_n)
\}
\]

where \(Y_i\) represents a subsequent outcome and \(M_i\) describes quantitative measures associated with that outcome.

SMSF transforms this historical RHS population into a structured **Pattern Leaf Decision Interface (PLDI)**.

Conceptually:

\[
Pattern\ Leaf
\rightarrow
RHS\ Outcome\ Partition
\rightarrow
Two\text{-}Way\ CCC
\rightarrow
Pattern\ Leaf\ Decision\ Interface
\]

A PLDI does not force the leaf into one winning prediction. Instead, it exposes a structured possibility space:

\[
\{
Y\text{-Bucket}_i,
Score_i,
Measures_i,
Support_i,
Evidence_i,
Provenance_i,
\ldots
\}
\]

This preserves alternative historical outcomes for later scoring, policy evaluation, multi-source composition, AI querying, and online unfolding.

For leaves with sufficient observations, SMSF may additionally train a local statistical or ANN companion model. Such a model does not replace the structural interface. It acts as a parallel localized estimator whose output can be compared with the structurally folded evidence.

This article develops the transition from Pattern Leaves to Decision Interfaces, defines the role of Two-Way CCC, separates structural scores from statistical probabilities, introduces local companion models, and establishes PLDI as the primary handshake between folded historical evidence and online decision unfolding.

---

# 1. Localization Is Not Yet a Decision

SMSF-002 introduced the Pattern Differential Tree.

Given a current pattern:

\[
X_q
\]

the tree localizes it into one or more relevant leaves:

\[
X_q
\rightarrow
\{
L_1,L_2,\ldots,L_k
\}
\]

Each leaf represents a structurally coherent historical population.

For example:

```text
Leaf L-204
│
├── Historical Pattern A
├── Historical Pattern B
├── Historical Pattern C
├── ...
└── Historical Pattern N
````

Each historical pattern contains:

$$
P_i=(X_i,Y_i,M_i)
$$

The \(X_i\)-side explains why the observation belongs to the leaf.

The \(Y_i,M_i\)-side records what happened afterward.

Therefore the leaf contains historical evidence about multiple possible futures.

The next problem is:

> How should those historical futures be organized without prematurely collapsing them into one answer?

---

# 2. The RHS Population

Let a Pattern Leaf be:

$$
L_j
=
\{
P_{j1},
P_{j2},
\ldots,
P_{jn}
\}
$$

with:

$$
P_{jk}
=
(X_{jk},Y_{jk},M_{jk})
$$

The RHS population is:

$$
RHS(L_j)
=
\{
(Y_{j1},M_{j1}),
(Y_{j2},M_{j2}),
\ldots,
(Y_{jn},M_{jn})
\}
$$

For example:

```text
Leaf L-204

Observation 001
    Y = Strong Rise
    M = {return:+8.1%, drawdown:-2.0%, duration:8d}

Observation 002
    Y = Mild Rise
    M = {return:+3.2%, drawdown:-1.4%, duration:6d}

Observation 003
    Y = Sideways
    M = {return:+0.4%, drawdown:-2.6%, duration:10d}

Observation 004
    Y = Strong Rise
    M = {return:+9.7%, drawdown:-3.1%, duration:7d}

...
```

The objective is not to discard this diversity.

The objective is to organize it.

---

# 3. Why a Leaf Should Not Produce One Immediate Prediction

Suppose a leaf contains:

```text
Strong Rise     22%
Mild Rise       34%
Sideways        26%
Decline         18%
```

A conventional classifier might return:

```text
Prediction = Mild Rise
```

because Mild Rise is the largest bucket.

However, this representation destroys information.

It hides:

* the 22% Strong Rise branch;
* the 26% Sideways branch;
* the 18% Decline branch;
* differences in drawdown;
* differences in duration;
* differences in volatility;
* historical support;
* policy relevance.

SMSF therefore adopts a stronger design principle:

> **A Pattern Leaf should expose a possibility structure before a winner is selected.**

Thus:

$$
Leaf
\not\rightarrow
Single\ Prediction
$$

Instead:

$$
Leaf
\rightarrow
Outcome\ Interface
$$

---

# 4. Outcome Partitioning

The first step is to partition historical RHS outcomes into meaningful Y-Buckets.

For example:

$$
\mathcal{Y}
=
\{
Y_1,Y_2,\ldots,Y_K
\}
$$

A simple directional partition may be:

```text
Y1 = Strong Rise
Y2 = Mild Rise
Y3 = Sideways
Y4 = Mild Decline
Y5 = Strong Decline
```

However, Y-Buckets may also represent:

* trajectory classes;
* volatility transitions;
* breakout behavior;
* drawdown classes;
* recovery classes;
* event-response classes;
* multi-stage future structures.

The partitioning scheme is therefore part of the application definition.

---

# 5. Outcome Horizon Must Remain Explicit

A Y-Bucket is incomplete unless its time horizon is clear.

For example:

$$
Y^{5d}
$$

and:

$$
Y^{60d}
$$

represent different decision problems.

A useful interface may therefore separate:

```text
5-Day Outcomes
20-Day Outcomes
60-Day Outcomes
```

or maintain horizon as part of the Y-Bucket definition.

For example:

```text
Y = Strong-Rise-20D
```

This prevents accidental mixing of structurally different future intervals.

---

# 6. Measures M Preserve More Than the Outcome Label

A Y-Bucket provides classification.

Measures \(M\) preserve richer quantitative structure.

For one outcome bucket, SMSF may retain:

```text
Support
Median Return
Mean Return
Return Distribution
Max Drawdown
Median Drawdown
Volatility
Recovery Time
Duration
Tail Loss
Observation Count
```

Conceptually:

$$
M(Y_i)
=
\{
m_{i1},
m_{i2},
\ldots
\}
$$

Thus two outcome buckets with similar frequency may still be very different for policy purposes.

Example:

```text
Y1 = Strong Rise
support = 0.25
median return = +9.2%
median drawdown = -7.1%

Y2 = Mild Rise
support = 0.25
median return = +3.8%
median drawdown = -1.6%
```

A risk-averse user may prefer \(Y_2\).

An aggressive user may prefer \(Y_1\).

The historical evidence itself should preserve both.

---

# 7. Two-Way CCC on the RHS

SMSF introduces Two-Way CCC analysis at the leaf.

The first CCC direction is already represented by the structural localization of the LHS pattern population.

The second direction analyzes the RHS outcome structure.

Conceptually:

```text
LHS
Historical X Population
        │
        ▼
     Leaf CCC
        │
        │
        ├───────────────┐
        │               │
        ▼               ▼
   Structural       Historical
   Localization      RHS Y/M
                        │
                        ▼
                  Two-Way CCC
                        │
                        ▼
                 Outcome Branches
```

The goal is to expose meaningful distinctions among RHS outcomes associated with a localized LHS structure.

---

# 8. Two-Way CCC as a Decision-Surface Constructor

The important point is that Two-Way CCC is not used merely as a descriptive statistic.

It constructs a decision-facing structure.

Given:

$$
L_j
$$

the RHS analysis produces:

$$
D_j
=
\{
B_1,B_2,\ldots,B_K
\}
$$

where each branch:

$$
B_i
=
\{
Y_i,
Score_i,
Measures_i,
Support_i,
Evidence_i,
\ldots
\}
$$

This structure becomes the leaf's Decision Interface.

Thus:

$$
Pattern\ Leaf
\rightarrow
Two\text{-}Way\ CCC
\rightarrow
Decision\ Surface
$$

---

# 9. Pattern Leaf Decision Interface — PLDI

We define:

$$
\boxed{
PLDI
=
Pattern\ Leaf\ Decision\ Interface
}
$$

A PLDI is the structured RHS interface attached to a Pattern Leaf.

A conceptual PLDI may look like:

```text
PLDI: Leaf L-204

Structural Path:
    Price = Compression
    Volume = Contracting
    Market Regime = Bull
    Fed Policy = Easing

Support:
    836 observations

Outcome Branches:

    Y1 = Strong Rise
        structural score = 0.76
        support = 176
        support ratio = 0.211
        median return = +8.4%
        median drawdown = -3.2%

    Y2 = Mild Rise
        structural score = 0.69
        support = 284
        support ratio = 0.340
        median return = +3.1%
        median drawdown = -1.5%

    Y3 = Sideways
        structural score = 0.46
        support = 226
        support ratio = 0.270

    Y4 = Decline
        structural score = 0.33
        support = 150
        support ratio = 0.179

Provenance:
    ...
```

The PLDI is not a final investment instruction.

It is a structured historical evidence interface.

---

# 10. The PLDI as an API Boundary

The PLDI is especially useful because it separates:

$$
Historical\ Folding
$$

from:

$$
Decision\ Policy
$$

The offline system produces:

$$
PLDI
$$

The online decision system consumes:

$$
PLDI
$$

This means downstream components do not need direct access to every raw historical observation for every decision.

Instead they can operate on a standardized interface.

Conceptually:

```text
Pattern Differential Tree
        │
        ▼
      Leaf
        │
        ▼
      PLDI
        │
        ├── Default Scorer
        ├── User Plugin
        ├── AI Agent
        ├── Policy Engine
        └── Explanation Engine
```

This is one of the central modularity mechanisms in SMSF.

---

# 11. Preserve Multiple Outcomes

A core PLDI principle is:

$$
\boxed{
Do\ not\ prematurely\ collapse\ uncertainty.
}
$$

If historical evidence supports:

$$
Y_1,Y_2,\ldots,Y_K
$$

the interface should preserve those branches.

Therefore:

$$
PLDI
=
\{
B_1,B_2,\ldots,B_K
\}
$$

rather than:

$$
PLDI
=
\arg\max_i B_i
$$

The winner, if one is needed, can be selected later.

This preserves future decision flexibility.

---

# 12. Structural Score Is Not Probability

This distinction must remain explicit.

A PLDI may contain several kinds of numbers:

```text
Structural Score
Support Ratio
Statistical Probability
Cosine Similarity
Policy Utility
Confidence
```

These values have different semantics.

Therefore:

$$
Score_i
\neq
P(Y_i|X)
$$

unless the score has explicitly been calibrated and defined as a probability.

For example:

```text
structural_score = 0.81
```

does not automatically mean:

```text
probability = 81%
```

SMSF should preserve semantic type information for all such values.

---

# 13. Support Is Evidence, Not Certainty

Suppose:

```text
Y1 support = 450
Y2 support = 120
```

This indicates different historical support.

However, support should not be treated as certainty.

Reasons include:

* overlapping patterns;
* correlated observations;
* regime concentration;
* temporal clustering;
* repeated exposure to the same macro event;
* non-stationarity.

Therefore the PLDI should expose support transparently but avoid overclaiming statistical independence.

---

# 14. Measures Can Remain Distributional

SMSF need not reduce each measure to one average.

For example:

```text
Median Return
P10 Return
P25 Return
P75 Return
P90 Return
Max Drawdown Distribution
Duration Distribution
```

may be more useful than:

```text
Mean Return
```

alone.

A PLDI can therefore preserve:

$$
Distribution(M|Y_i,L_j)
$$

rather than only:

$$
E[M|Y_i,L_j]
$$

This is particularly useful when historical outcomes have fat tails or asymmetric risk.

---

# 15. Provenance Inside the PLDI

Each outcome branch should remain traceable to historical evidence.

Thus:

$$
PLDI
\rightarrow
Y\text{-Bucket}
\rightarrow
Historical\ Episodes
$$

A branch may expose:

```text
Observation IDs
Ticker IDs
Date Ranges
Context
Event Conditions
Pattern IR Version
Tree Version
Measure Version
```

This allows the runtime to answer:

> Which historical episodes support this outcome branch?

That is stronger than generating a post-hoc textual explanation.

---

# 16. Decision Provenance

A final recommendation may be constructed from several layers.

For example:

```text
Recommendation
      │
      ▼
Policy Score
      │
      ▼
Composite PLDI
      │
      ▼
Leaf PLDI
      │
      ▼
Pattern Leaf
      │
      ▼
Historical Episodes
```

This defines:

$$
\boxed{
Decision\ Provenance
}
$$

The system can trace a recommendation backward through the actual computational structure that produced it.

---

# 17. Online PLDI Retrieval

During online operation:

$$
X_q
\rightarrow
Pattern\ Differential\ Tree
\rightarrow
Leaf
\rightarrow
PLDI
$$

For soft localization:

$$
X_q
\rightarrow
\{
(L_i,w_i)
\}
$$

the runtime retrieves:

$$
\{
(PLDI_i,w_i)
\}
$$

Thus the current pattern does not directly ask:

> What will happen?

It first asks:

> Which historical possibility interfaces are structurally relevant?

This is a major conceptual difference.

---

# 18. Online Unfolding

Once a PLDI has been retrieved, the folded historical evidence can be unfolded.

Conceptually:

```text
Current Pattern
      │
      ▼
Tree Localization
      │
      ▼
Pattern Leaf
      │
      ▼
Folded PLDI
      │
      ▼
Outcome Branches
      │
      ├── Y1
      ├── Y2
      ├── Y3
      └── Y4
```

This process is:

$$
\boxed{
Structural\ Unfolding
}
$$

The output is a possibility structure rather than necessarily one prediction.

---

# 19. Folding and Unfolding Are Asymmetric

Offline folding performs heavy structural work:

```text
Historical Search
Pattern Discovery
Pattern IR
Differential Tree Construction
Leaf Analysis
Two-Way CCC
Measure Aggregation
Provenance Indexing
```

Online unfolding can operate on the already-constructed interface:

```text
Current Pattern
Leaf Localization
PLDI Retrieval
Scoring
Policy
Explanation
```

Therefore:

$$
Heavy\ Fold
\rightarrow
Light\ Unfold
$$

This is one reason the architecture can support interactive runtime use.

---

# 20. The PLDI Is Not User Policy

A PLDI should normally remain policy-neutral.

It answers:

> What historical outcomes are associated with this structural leaf?

It should not automatically answer:

> Which outcome should this user prefer?

Therefore:

$$
PLDI
\neq
Policy
$$

Instead:

$$
PLDI
+
UserPolicy
\rightarrow
Decision
$$

This keeps reusable historical evidence separate from user-specific preference.

---

# 21. On-the-Fly Policy Unfolding

Because the relevant leaf evidence is already localized, policy evaluation can often be generated dynamically.

Let:

$$
P_u
$$

represent a user policy.

Then:

$$
PolicySpace
=
g(PLDI,P_u)
$$

For example:

```text
PLDI Outcome Branches
        │
        ▼
User Policy:
    max_drawdown < 5%
    horizon = 20d
    risk_aversion = high
        │
        ▼
On-the-Fly Policy Space
        │
        ├── Candidate A
        ├── Candidate B
        └── Candidate C
```

This avoids the need to precompute every possible policy offline.

---

# 22. Evidence Space and Policy Space

SMSF therefore distinguishes:

$$
EvidenceSpace
$$

from:

$$
PolicySpace
$$

The PLDI belongs to Evidence Space.

The user-specific decision transformation belongs to Policy Space.

Conceptually:

```text
Historical Evidence
      │
      ▼
     PLDI
      │
      ▼
Evidence Space
      │
      + User Policy
      │
      ▼
Policy Space
      │
      ▼
Decision
```

This separation improves reuse.

One PLDI can support many policies.

---

# 23. User Preference vs User Policy

A further distinction is useful.

User Preference may contain:

```text
Risk Tolerance
Investment Horizon
Liquidity Requirement
Maximum Drawdown
Turnover Preference
Sector Preference
```

User Policy defines how those preferences act on evidence.

For example:

```text
Preference:
    maximum drawdown = 5%
    horizon = 20 days
```

may become:

```text
Policy:
    reject outcomes with
    historical median drawdown > 5%

    rank remaining outcomes by
    risk-adjusted structural score
```

Thus:

$$
Preference
\rightarrow
Policy
$$

then:

$$
PLDI+Policy
\rightarrow
Decision
$$

---

# 24. Local ANN Companion Models

A Pattern Leaf may contain enough observations to support a local statistical model.

For such leaves, SMSF may train:

$$
Model_{L_j}
$$

using observations inside or near the leaf.

Possible models include:

```text
Logistic Regression
Linear Model
Small MLP
Gradient Boosting
Bayesian Model
Other Local Classifier
```

The important architectural principle is:

> **The model is local to a structurally localized region.**

Thus:

$$
Structural\ Localization
\rightarrow
Local\ Learning
$$

rather than:

$$
Entire\ Market\ History
\rightarrow
One\ Global\ Black\ Box
$$

---

# 25. Why Local Modeling Is Attractive

Suppose the global market contains many regimes.

A single model must approximate:

$$
f(X)
$$

across all of them.

SMSF instead first localizes:

$$
X_q
\rightarrow
L_j
$$

then estimates:

$$
f_j(X)
$$

inside a smaller structural region.

This can simplify the learning problem.

Conceptually:

$$
Global\ Complexity
\rightarrow
Structural\ Localization
\rightarrow
Local\ Approximation
$$

This architecture is compatible with simple models.

That simplicity may improve interpretability and maintenance.

---

# 26. Companion Model, Not Replacement Model

The local ANN/statistical model should not replace the PLDI.

Instead, the two operate in parallel.

For example:

```text
Pattern Leaf
    │
    ├── Structural Path
    │
    ├── Two-Way CCC
    │      │
    │      ▼
    │     PLDI
    │
    └── Local Statistical Model
           │
           ▼
      Model Prediction
```

Thus online output can include:

```text
Structural Evidence Report
Local Model Report
Policy-Scored Report
```

This creates multiple views of the same localized historical region.

---

# 27. Minimum Evidence for Local Models

A local model should not be created merely because a leaf exists.

Possible requirements include:

```text
Minimum Observation Count
Minimum Class Support
Temporal Coverage
Regime Diversity
Validation Performance
Calibration Quality
Data Quality
```

If these conditions are not satisfied:

```text
Leaf
└── No Local Model
```

This is not a failure.

The PLDI itself remains usable.

---

# 28. Local Model Validation

Local models should be validated using time-aware methods.

Possible approaches include:

* chronological holdout;
* rolling validation;
* walk-forward validation;
* regime-separated validation.

Random splitting may produce overly optimistic results in temporally dependent market data.

The local model should also record:

```text
Training Period
Validation Period
Feature/IR Version
Model Version
Calibration Method
Performance Metrics
```

This information should be traceable from the runtime report.

---

# 29. Structural Report vs Statistical Report

The PLDI and local model answer different questions.

### Structural Report

> What happened historically in structurally similar episodes?

### Statistical Model Report

> Given this localized region, what does the fitted model estimate?

These should remain distinguishable.

For example:

```text
Structural Report
    Mild Rise
    support ratio = 0.36
    structural score = 0.69

Local Logistic Model
    Mild Rise
    probability = 0.64
```

The values should not be silently merged into one number.

---

# 30. Agreement as Additional Evidence

If the structural interface and local model agree:

```text
PLDI:
    Mild Rise favored

Local Model:
    Mild Rise favored
```

this agreement may strengthen operational confidence.

However, agreement does not prove correctness.

It merely provides:

$$
Independent\ or\ SemiIndependent\ Support
$$

depending on how the models were constructed.

---

# 31. Disagreement Is Also Information

Suppose:

```text
PLDI:
    Mild Rise favored

Local Model:
    Strong Decline favored
```

This should not automatically be resolved by averaging.

The disagreement itself may signal:

* insufficient leaf support;
* structural transition;
* regime change;
* model instability;
* bad Pattern IR;
* missing context;
* new event influence;
* distribution shift.

Thus:

$$
PLDI
\neq
LocalModel
$$

can become a **Gap Signal**.

---

# 32. Three Parallel Decision Views

A mature SMSF runtime can expose three parallel views:

```text
A. Structural Historical View
       PLDI / Two-Way CCC

B. Local Statistical View
       ANN / Logistic Regression / Other

C. Policy View
       User Policy / Plugin / Agent
```

For example:

```text
A. Structural Evidence
    Mild Rise        0.69 structural score

B. Local Model
    Mild Rise        0.66 probability

C. User Policy
    Mild Rise        0.61 policy utility
```

These numbers should remain semantically typed.

---

# 33. Multi-Leaf PLDI Composition

If online localization returns several leaves:

$$
\{
(L_1,w_1),
(L_2,w_2),
\ldots,
(L_k,w_k)
\}
$$

their decision interfaces can be composed.

Conceptually:

```text
PLDI-L1 ──┐
          │
PLDI-L2 ──┼──► Composite Outcome Interface
          │
PLDI-L3 ──┘
```

The weights \(w_i\) may reflect structural relevance.

This allows uncertainty in localization to remain visible through later decision stages.

---

# 34. Multi-Stock and Multi-Source PLDI Composition

The same concept scales beyond one tree.

For example:

```text
MSFT Tree
    │
    ▼
PLDI-MSFT
        \
         \
SP500 Tree \
    │        \
    ▼         \
PLDI-SP500 ----► Composite Decision Structure
              /
QQQ Tree     /
    │       /
    ▼      /
PLDI-QQQ

Fed Event Tree
    │
    ▼
PLDI-FED
```

Thus:

$$
PLDI_{MSFT}
+
PLDI_{SP500}
+
PLDI_{QQQ}
+
PLDI_{FED}
$$

can be composed without concatenating every raw observation into one enormous input vector.

---

# 35. Scale by Interface Composition

This leads to an important SMSF principle:

$$
\boxed{
Scale\ by\ interface\ composition,
not\ by\ raw\ feature\ concatenation.
}
$$

Each source may first perform its own structural folding.

Then standardized evidence interfaces can be merged.

This is particularly attractive for:

* multi-stock analysis;
* index context;
* macro context;
* sector context;
* volatility context;
* event context.

---

# 36. Composite Outcome Alignment

Different PLDIs may use different outcome vocabularies.

For example:

```text
MSFT PLDI:
    Strong Rise
    Mild Rise
    Sideways
    Decline
```

while:

```text
VIX PLDI:
    Volatility Expansion
    Stable
    Volatility Contraction
```

Therefore composition may require an alignment layer.

Conceptually:

$$
PLDI_i
\rightarrow
Common\ Decision\ Coordinate
$$

This coordinate may be defined by:

* target stock outcome;
* portfolio objective;
* risk measure;
* trajectory class;
* user-defined policy objective.

This is a later composition concern rather than a requirement for individual PLDIs.

---

# 37. Scoring Tree

Once multiple decision interfaces have been aligned, SMSF may construct a scoring structure.

For example:

```text
Composite Decision Candidates
        │
        ├── Candidate Y1
        ├── Candidate Y2
        ├── Candidate Y3
        └── Candidate Y4
              │
              ▼
        Similarity / Evidence
              │
              ▼
          Scoring Tree
```

A default implementation may use Cosine Similarity or another transparent scoring mechanism.

However, the scorer should remain replaceable.

---

# 38. User Scoring Plugin

The framework may provide:

```text
Default Scorer
```

while allowing:

```text
User Scoring Plugin
AI Agent Scorer
Policy Scorer
Domain-Specific Scorer
```

Thus:

$$
CompositePLDI
\xrightarrow{Scorer}
RankedCandidates
$$

The structural evidence remains separate from the scoring implementation.

---

# 39. Why the PLDI Is AI-Friendly

A PLDI exposes explicit typed objects:

```text
Outcome
Measure
Support
Score
Context
Evidence
Provenance
```

An AI agent can therefore query these objects directly.

For example:

```text
Show outcomes with support > 100.

Compare drawdown for Y1 and Y2.

Exclude branches with median drawdown > 5%.

Trace the top-ranked outcome to historical episodes.

Compare structural and local-model disagreement.
```

This is substantially easier to govern than asking an AI to infer everything directly from raw historical tables.

---

# 40. SQL-Like PLDI Queries

A future Structural Query API might support:

```text
SELECT OUTCOMES
FROM LEAF L-204
WHERE support > 100
AND horizon = 20d
RETURN
    outcome,
    structural_score,
    median_return,
    median_drawdown,
    provenance
```

or:

```text
UNFOLD OUTCOME
FROM current_msft

COMPARE
    structural_evidence,
    local_model

APPLY POLICY
    conservative_20d
```

The PLDI provides a natural typed object for such APIs.

---

# 41. Decision Interface vs Decision Answer

This distinction is fundamental.

A Decision Interface contains:

$$
Possibilities
+
Evidence
+
Measures
+
Structure
$$

A Decision Answer contains:

$$
Selected\ Action
$$

Therefore:

$$
PLDI
\neq
FinalDecision
$$

The runtime should preserve this boundary whenever possible.

This allows the same evidence to be reused for:

* different policies;
* different users;
* different horizons;
* different portfolio states;
* different AI agents.

---

# 42. Uncertainty-Preserving Folding

The PLDI provides a practical implementation of an uncertainty-preserving folding principle.

Historical evidence is folded into a compact interface, but alternative RHS outcomes remain represented.

Conceptually:

$$
Many\ Historical\ Episodes
\rightarrow
Few\ Outcome\ Branches
$$

without:

$$
Few\ Outcome\ Branches
\rightarrow
One\ Forced\ Answer
$$

This is a useful compromise between:

* raw-history preservation;
* aggressive predictive compression.

---

# 43. Uncertainty Recovery

Not all uncertainty can or should be explicitly preserved offline.

Some uncertainty can be recovered later through:

* local model validation;
* multi-leaf retrieval;
* cross-source comparison;
* temporal reweighting;
* policy-specific scoring;
* historical resampling;
* distilled confidence estimation.

Thus SMSF can support both:

$$
Uncertainty\ Preservation
$$

and:

$$
Uncertainty\ Recovery
$$

The PLDI provides the structural substrate for both.

---

# 44. Failure and Gap Signals

A decision interface may explicitly report insufficient evidence.

Examples:

```text
LOW_SUPPORT

OUTCOME_AMBIGUITY

REGIME_MISMATCH

MODEL_DISAGREEMENT

OUT_OF_DISTRIBUTION

PROVENANCE_INSUFFICIENT

STRUCTURAL_GAP
```

This is preferable to forcing a high-confidence recommendation from weak evidence.

---

# 45. PLDI Versioning

A PLDI should be versioned with its parent fold.

Possible metadata include:

```text
PLDI ID
Leaf ID
Tree Version
Pattern IR Version
Y-Bucket Schema Version
Measure Schema Version
Two-Way CCC Version
Construction Time
Historical Cutoff
Observation Count
```

This makes reports reproducible and auditable.

---

# 46. Example End-to-End Leaf

Consider a simplified historical leaf.

```text
Leaf ID:
    L-204

Structural Path:
    Pattern = Compression
    Volume = Contracting
    Market Regime = Bull
    Fed Policy = Easing

Observations:
    836
```

Historical RHS analysis produces:

```text
Y1 = Strong Rise
    support = 176
    support ratio = 0.211
    median return = +8.4%
    median drawdown = -3.2%

Y2 = Mild Rise
    support = 284
    support ratio = 0.340
    median return = +3.1%
    median drawdown = -1.5%

Y3 = Sideways
    support = 226
    support ratio = 0.270
    median return = +0.4%
    median drawdown = -2.1%

Y4 = Decline
    support = 150
    support ratio = 0.179
    median return = -4.7%
    median drawdown = -6.4%
```

Two-Way CCC produces the structured outcome interface.

A local Logistic Regression model may additionally output:

```text
Strong Rise  = 0.24
Mild Rise    = 0.38
Sideways     = 0.23
Decline      = 0.15
```

A conservative policy may then rank:

```text
1. Mild Rise
2. Sideways
3. Strong Rise
4. Decline
```

An aggressive policy may rank:

```text
1. Strong Rise
2. Mild Rise
3. Sideways
4. Decline
```

The historical PLDI remains unchanged.

This illustrates the separation among:

$$
Evidence
$$

$$
Statistical\ Estimation
$$

and:

$$
Policy
$$

---

# 47. Canonical PLDI Architecture

The architecture developed in this article can be summarized as:

```text
                     PATTERN LEAF
                          │
          ┌───────────────┼────────────────┐
          │               │                │
          ▼               ▼                ▼
      Leaf CCC       Historical Y/M    Provenance
                          │
                          ▼
                  RHS Outcome Partition
                          │
                          ▼
                     Two-Way CCC
                          │
                          ▼
             Pattern Leaf Decision Interface
                          │
             ┌────────────┼────────────┐
             │            │            │
             ▼            ▼            ▼
           Y1           Y2           Y3 ...
             │            │            │
       Score / M /    Score / M /   Score / M /
       Support        Support       Support
             │            │            │
             └────────────┼────────────┘
                          │
          ┌───────────────┼────────────────┐
          │               │                │
          ▼               ▼                ▼
     Local Model     User Scorer      Policy Layer
          │               │                │
          └───────────────┼────────────────┘
                          ▼
                  Decision Unfolding
```

---

# 48. Core Properties of a PLDI

A useful PLDI should aim for the following properties.

### 48.1 Multi-Outcome

It preserves multiple historically supported RHS branches.

### 48.2 Measure-Rich

It retains quantitative characteristics beyond simple outcome labels.

### 48.3 Evidence-Aware

It exposes support and observation structure.

### 48.4 Policy-Neutral

It does not embed one user's preference into canonical evidence.

### 48.5 Traceable

Each branch can be linked back to historical episodes.

### 48.6 Composable

Multiple PLDIs can be merged into a larger decision structure.

### 48.7 Model-Compatible

Local ANN/statistical models can run alongside it.

### 48.8 AI-Friendly

Typed outcome, measure, and provenance fields support structured querying.

### 48.9 Uncertainty-Preserving

Alternative outcomes remain available until later decision stages.

### 48.10 Versioned

The interface remains reproducible as folds evolve.

---

# 49. Core Claims

This article makes the following architectural claims.

### Claim 1 — Pattern localization and decision construction should remain separate.

The Pattern Differential Tree identifies relevant historical structural regions; the PLDI organizes their RHS evidence.

### Claim 2 — A leaf should expose a possibility structure rather than immediately produce one winning prediction.

### Claim 3 — Two-Way CCC can convert localized RHS history into a structured decision surface.

### Claim 4 — Y-Buckets and Measures serve different purposes.

Outcome classes organize possibilities; measures preserve quantitative consequences.

### Claim 5 — Score, probability, support, and utility must remain semantically distinct.

### Claim 6 — The PLDI is a reusable API boundary between historical evidence and downstream policy.

### Claim 7 — Local statistical models are companions to structural evidence, not replacements for it.

### Claim 8 — Model disagreement can serve as a structural gap signal.

### Claim 9 — Multi-source scaling can proceed through PLDI composition.

### Claim 10 — Decision provenance can remain computationally traceable from recommendation to historical episode.

---

# 50. Design Principle

The central design principle of SMSF-003 is:

$$
\boxed{
Do\ not\ ask\ a\ Pattern\ Leaf\ for\ one\ answer.
Ask\ it\ to\ expose\ its\ historical\ possibility\ structure.
}
$$

The transformation is:

$$
Pattern\ Leaf
\rightarrow
Historical\ RHS
\rightarrow
Two\text{-}Way\ CCC
\rightarrow
PLDI
$$

and only later:

$$
PLDI
+
Scoring
+
Policy
\rightarrow
Decision
$$

---

# 51. Conclusion

The Pattern Differential Tree organizes historical antecedent structures.

The Pattern Leaf Decision Interface organizes what happened afterward.

Together they establish the central SMSF handshake:

$$
X
\rightarrow
Structural\ Localization
\rightarrow
Leaf
\rightarrow
Historical\ Outcome\ Interface
$$

A PLDI preserves:

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

rather than reducing historical uncertainty to one forced prediction.

This creates a reusable evidence surface that can support:

* online structural unfolding;
* user-defined scoring;
* on-the-fly policy generation;
* local ANN companion models;
* multi-leaf composition;
* multi-stock composition;
* AI querying;
* explanation;
* decision provenance.

The next stage extends this architecture beyond one leaf or one stock.

It asks:

> How can multiple structurally folded evidence interfaces be composed, scored, queried, and transformed into policy-aware online decisions?

That is the role of **Composable Unfolding**.

---

## Next

**SMSF-004 — Composable Unfolding: Multi-Source Evidence, On-the-Fly Policy, and AI APIs**

The next article develops:

* multi-stock evidence composition;
* multi-source PLDI composition;
* Cosine Similarity Scoring Trees;
* user scoring plugins;
* on-the-fly policy unfolding;
* policy-space construction;
* AI-agent interaction;
* SQL-like structural query APIs;
* decision explanation;
* structural runtime architecture.

---

## Repository

**Stock-Market Structural Folding (SMSF)**

A differential-tree architecture for folding historical market experience into navigable structural evidence and unfolding that evidence for online decision support.
