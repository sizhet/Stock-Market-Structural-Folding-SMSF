````markdown
# SMPF-001 — From Historical Market Data to Folded Structural Experience

**Stock-Market Structural Folding (SMSF)**  
**A Differential-Tree Architecture for Historical Evidence Folding and Decision Unfolding**

---

## Abstract

Historical stock-market data are abundant, but historical data are not automatically reusable knowledge.

A conventional market model often transforms historical observations into indicators, statistical parameters, embeddings, or predictive models. These representations can be useful, but they frequently compress many structurally different historical episodes into a prediction-oriented representation whose internal evidence is difficult to inspect, retrieve, recombine, or reinterpret under new decision policies.

Stock-Market Structural Folding (SMSF) takes a different approach.

SMSF treats historical market experience as a collection of structural episodes that can be discovered, represented, compared, organized, and folded into a navigable structural knowledge space.

A basic historical episode is represented as:

\[
P_k = (X_k, Y_k, M_k)
\]

where:

- \(X_k\) is the antecedent structural pattern available before a decision boundary;
- \(Y_k\) is the subsequent outcome or outcome class;
- \(M_k\) contains quantitative measures describing that outcome.

The \(X\)-side may include price and volume structures, event sequences, market context, value-based events, cross-asset relationships, user-defined representations, and other structural information.

SMSF does not require one universal definition of a market pattern. Pattern discovery and Pattern Intermediate Representation (Pattern IR) may be supplied by the framework, by domain-specific algorithms, or by user plugins and AI agents.

The discovered historical structures are subsequently organized through a Pattern Differential Tree. At suitable leaves, historical RHS outcomes are analyzed and exposed through structured decision interfaces rather than prematurely collapsed into a single winning prediction.

The central objective is therefore not:

> compress history into one answer.

It is:

> **fold historical market experience into reusable structural evidence that can later be localized, queried, composed, scored, explained, and unfolded.**

This article establishes the conceptual foundation of SMSF and defines the historical experience that later SMSF stages will structurally fold.

---

# 1. Historical Data Are Not Yet Historical Knowledge

A stock market generates enormous quantities of observable data:

- prices;
- volumes;
- volatility;
- order-related measurements;
- index movements;
- sector movements;
- macroeconomic variables;
- interest rates;
- corporate events;
- policy events;
- news events;
- cross-asset relationships;
- market regimes;
- and many other forms of context.

A simplified observation at time \(t\) may be written as:

\[
O_t =
\{
Price_t,
Volume_t,
Context_t,
Events_t,
ExternalState_t,
\ldots
\}
\]

A historical database may contain millions or billions of such observations.

However,

\[
Historical\ Data
\neq
Historical\ Knowledge
\]

A raw historical record answers:

> What was observed?

A reusable structural knowledge system should additionally help answer:

> What kind of situation was this?

> What structurally similar situations occurred before?

> Under what contexts did they occur?

> What happened afterward?

> How different were the possible outcomes?

> Which historical evidence supports each outcome?

> Can the evidence be recombined with other stocks, indexes, events, or policies?

> Can a human or AI trace the recommendation back to the historical observations that produced it?

SMSF is designed around these questions.

---

# 2. From Time Series to Historical Episodes

The first conceptual transformation in SMSF is:

\[
Continuous\ Historical\ Data
\rightarrow
Structural\ Episodes
\]

Instead of treating the complete historical time series as one undifferentiated training object, SMSF identifies meaningful episodes.

An episode may exist at many granularities.

Examples include:

- several minutes;
- one trading session;
- several days;
- several weeks;
- a macroeconomic cycle;
- an event-centered interval;
- a trajectory segment;
- or another domain-defined structural interval.

Episodes may overlap.

For example:

```text
Timeline
────────────────────────────────────────────────────────────>

       [ Pattern A ]
             [ Pattern B ]
                    [ Pattern C          ]
          [        Pattern D        ]
````

Overlap is not considered an error.

Different overlapping episodes may expose different structural perspectives on the same historical region.

This is important because market structure is not necessarily partitionable into one unique sequence of non-overlapping segments.

---

# 3. The X-Y-M Historical Pattern

SMSF represents a basic historical pattern as:

$$
P_k = (X_k, Y_k, M_k)
$$

This is the minimal conceptual unit from which structural folding begins.

---

## 3.1 X — Antecedent Structure

\(X\) describes the information available on the left-hand side of the prediction or decision boundary.

Conceptually:

```text
PAST / AVAILABLE                     FUTURE / UNKNOWN
─────────────────────┬────────────────────────────────
          X          │          Y + M
                     │
              Decision Boundary
```

Possible components of \(X\) include:

* price trajectory;
* volume trajectory;
* volatility structure;
* technical structures;
* event sequences;
* market regime;
* sector context;
* index context;
* macroeconomic context;
* value-based events;
* cross-stock relationships;
* cross-asset relationships;
* structural CCC representations;
* user-defined structural dimensions;
* externally generated representations.

Therefore:

$$
X
\neq
PriceWindow
$$

in the general case.

A more realistic expression is:

$$
X =
f(
PriceStructure,
VolumeStructure,
Events,
Context,
CrossAssetState,
\ldots
)
$$

---

## 3.2 Y — Subsequent Outcome

\(Y\) represents what happened after \(X\).

For example:

```text
Y = Strong Rise
Y = Mild Rise
Y = Sideways
Y = Mild Decline
Y = Strong Decline
```

But \(Y\) does not have to be a simple directional class.

It may represent:

* trajectory type;
* breakout type;
* recovery type;
* volatility transition;
* drawdown regime;
* event response;
* multi-stage outcome;
* user-defined behavioral class.

Different horizons should normally remain distinguishable.

For example:

$$
Y^{5d}
$$

$$
Y^{20d}
$$

$$
Y^{60d}
$$

should not automatically be treated as the same outcome variable.

---

## 3.3 M — Outcome Measures

\(M\) describes quantitative properties of the RHS outcome.

For example:

$$
M =
\{
Return,
MaxDrawdown,
Volatility,
Duration,
RecoveryTime,
\ldots
\}
$$

A historical pattern might therefore contain:

```text
X:
    price compression
    volume contraction
    SP500 mild positive trend
    low volatility regime

Y:
    upside breakout

M:
    5-day return       = +4.8%
    20-day return      = +7.1%
    max drawdown       = -1.9%
    breakout duration  = 6 days
```

The distinction between \(Y\) and \(M\) is useful.

\(Y\) provides an outcome structure suitable for classification and dispatching.

\(M\) preserves richer quantitative evidence that can later support:

* scoring;
* policy evaluation;
* risk analysis;
* comparison;
* filtering;
* explanation;
* local statistical modeling.

---

# 4. X-Y-M as a Structural Knowledge Unit

The X-Y-M representation changes the meaning of a historical pattern.

A pattern is no longer merely:

> a visually recognizable shape in a stock chart.

It becomes:

> **an antecedent structural condition together with its observed subsequent outcome and measurable consequences.**

Conceptually:

$$
X
\rightarrow
Y
$$

with:

$$
M(Y)
$$

This makes historical patterns usable as structural evidence.

A richer implementation may additionally retain metadata:

$$
PKU =
(X,Y,M,C,P)
$$

where:

* \(C\) represents context and auxiliary structural information;
* \(P\) represents provenance and construction metadata.

This richer object may be viewed as a **Pattern Knowledge Unit**.

The exact implementation is intentionally open.

The important requirement is that sufficient information survive folding for later structural retrieval and unfolding.

---

# 5. Pattern Discovery Is an Open Interface

SMSF does not assume that one algorithm can discover every meaningful market pattern.

Pattern discovery may be performed by:

* deterministic algorithms;
* metric-based segmentation;
* trajectory analysis;
* event-sequence analysis;
* clustering;
* statistical algorithms;
* ANN-based algorithms;
* LLM or AI agents;
* domain-specific systems;
* human-defined rules;
* user plugins;
* hybrid systems.

Therefore the architecture should expose a conceptual interface:

```text
Historical Observations
        │
        ▼
┌─────────────────────────────┐
│ Pattern Discovery Interface │
└─────────────────────────────┘
        │
        ▼
Candidate Structural Episodes
```

The framework may provide default discovery algorithms.

However, they should not define the theoretical boundary of SMSF.

---

# 6. Pattern IR Is Also an Open Interface

Pattern discovery and Pattern representation are different problems.

A discovery algorithm answers:

> Where is a meaningful pattern?

A Pattern IR answers:

> How should that pattern be represented structurally?

SMSF therefore separates:

$$
Pattern\ Discovery
$$

from:

$$
Pattern\ IR
$$

Possible Pattern IRs include:

* normalized numerical vectors;
* trajectory structures;
* event sequences;
* CCC structures;
* differential structures;
* graph structures;
* symbolic representations;
* embeddings;
* hybrid structural objects;
* user-defined representations.

Conceptually:

```text
Historical Data
      │
      ▼
Pattern Discovery
      │
      ▼
Discovered Episode
      │
      ▼
Pattern IR
      │
      ▼
Structural X
```

This separation is important because SMSF should not require all applications to agree on one representation of market structure.

---

# 7. Pattern Semantics and Folding Machinery Are Separate

This leads to an important architectural principle:

> **SMSF does not define what a market pattern must be. It defines how discovered market structures can be folded, localized, and later unfolded.**

The distinction can be summarized as:

$$
Pattern\ Semantics
\perp
Folding\ Machinery
$$

A user may replace:

* the pattern detector;
* the Pattern IR;
* the distance metric;
* selected context dimensions;

while retaining the same downstream folding architecture.

For example:

```text
User A
    Candlestick + Volume IR
          │
          ▼
    SMSF Folding Runtime

User B
    Macro Event Sequence IR
          │
          ▼
    SMSF Folding Runtime

User C
    Trajectory CCC IR
          │
          ▼
    SMSF Folding Runtime

User D
    AI-Discovered Hybrid IR
          │
          ▼
    SMSF Folding Runtime
```

This modularity is one reason the architecture can extend beyond one particular stock-analysis methodology.

---

# 8. Context Is Structural Information

Market behavior is strongly context dependent.

The same local price pattern may produce different RHS outcomes under different environments.

Examples include:

* bull versus bear market;
* high versus low volatility;
* tightening versus easing monetary policy;
* sector expansion versus contraction;
* pre-earnings versus post-earnings;
* liquidity stress versus normal conditions.

SMSF therefore does not treat Context as incidental metadata.

Context may participate directly in \(X\):

$$
X =
(
LocalPattern,
MarketContext
)
$$

or it may later become an explicit differential dimension in the folding tree.

This distinction is important.

Context can be represented either as:

### Pattern Semantics

```text
X =
    local price structure
    + volume structure
    + market regime
```

or as:

### Structural Coordinate

```text
Pattern
   │
   ├── Bull Regime
   │
   ├── Sideways Regime
   │
   └── Bear Regime
```

The appropriate representation depends on the purpose of the folding process.

---

# 9. Value-Based Events Become First-Class Structural Objects

Discrete value-based events are often awkward to integrate into purely continuous time-series representations.

Examples include:

* Federal Reserve rate increases;
* Federal Reserve rate reductions;
* CPI surprises;
* earnings announcements;
* regulatory decisions;
* index membership changes;
* mergers;
* geopolitical events;
* policy interventions.

SMSF provides at least two natural ways to represent such events.

---

## 9.1 Event as Part of X

For example:

```text
X:
    price compression
    volume contraction
    Fed rate increase = 25 bp
    SP500 regime = weak
```

Then the event becomes part of the antecedent structural pattern.

---

## 9.2 Event as a Differential Dimension

Alternatively:

```text
Common Pattern
      │
      ├── Fed Easing
      │
      ├── Fed Unchanged
      │
      └── Fed Tightening
```

This representation makes it possible to compare:

$$
P(Y|X,Event_A)
$$

with:

$$
P(Y|X,Event_B)
$$

The question is therefore transformed from:

> How can this event be forced into a numerical feature vector?

to:

> **Where should this event exist in the structural coordinate system?**

This is a substantially different modeling perspective.

---

# 10. Multi-Granularity Folding

Market structures exist at different scales.

For example:

```text
Minutes
   ↓
Hours
   ↓
Days
   ↓
Weeks
   ↓
Months
```

A useful structural folding architecture should therefore permit:

$$
X^{g_1},
X^{g_2},
\ldots,
X^{g_n}
$$

where \(g_i\) represents a granularity.

Different granularities may:

* overlap;
* coexist;
* use different Pattern IRs;
* use different metrics;
* lead to different structural leaves;
* contribute independently to later decision composition.

SMSF does not require one universal granularity.

This permits the historical knowledge structure to preserve multiple resolutions rather than forcing all experience into one temporal scale.

---

# 11. Multi-Perspective Folding

Granularity is only one structural dimension.

The same historical interval may also be interpreted from different perspectives.

For example:

```text
Price Perspective
Volume Perspective
Volatility Perspective
Event Perspective
Market-Regime Perspective
Cross-Stock Perspective
Macro Perspective
```

Thus one historical episode may participate in multiple structural folds.

Conceptually:

$$
Episode
\rightarrow
\{
X^{price},
X^{volume},
X^{event},
X^{macro},
\ldots
\}
$$

This does not necessarily imply one giant feature space.

SMSF can preserve these perspectives as independently navigable structural dimensions and later compose their evidence.

This principle becomes especially important for multi-stock and multi-source decision unfolding.

---

# 12. Structural Folding Is More Than Pattern Folding

The term **Stock-Market Structural Folding** is intentionally broader than **Stock-Market Pattern Folding**.

Patterns provide important structural units, but SMSF ultimately folds more than pattern shapes.

The folded structure may include:

$$
\{
Pattern,
Context,
Event,
CCC,
Outcome,
Measures,
Evidence,
Provenance,
DecisionInterface,
\ldots
\}
$$

Therefore:

$$
Pattern\ Discovery
\subset
Pattern\ Representation
\subset
Structural\ Folding
$$

The purpose of Structural Folding is to preserve useful relationships among these objects while organizing them into a form suitable for later localization and unfolding.

---

# 13. From Pattern Collection to Structural Topology

Suppose historical processing discovers:

$$
P_1,P_2,\ldots,P_n
$$

where:

$$
P_i=(X_i,Y_i,M_i)
$$

A flat collection of such patterns is already more useful than raw time series, but it remains expensive to search and difficult to reason over structurally.

SMSF therefore introduces a later transformation:

$$
\{X_1,X_2,\ldots,X_n\}
\rightarrow
Pattern\ Differential\ Tree
$$

The tree organizes historical experience according to meaningful structural differences.

This produces:

$$
Historical\ Episodes
\rightarrow
Navigable\ Structural\ Space
$$

The detailed construction of the Pattern Differential Tree is the subject of **SMSF-002**.

---

# 14. Folding Should Preserve Future Unfolding Capacity

A central danger in any folding operation is excessive compression.

Suppose a historical region contains:

```text
Strong Rise      20%
Mild Rise        35%
Sideways         25%
Decline          20%
```

A premature representation might retain only:

```text
Prediction = Mild Rise
```

This is compact, but it destroys much of the structural evidence.

SMSF instead seeks to preserve a richer RHS possibility structure:

$$
\{
Y_i,
Score_i,
M_i,
Support_i,
Evidence_i,
\ldots
\}
$$

The objective is not necessarily to preserve every raw observation in every runtime object.

The objective is to preserve enough information that meaningful future unfolding remains possible.

This leads to a general design principle:

> **A good fold reduces structural complexity without unnecessarily destroying the distinctions required by future unfolding.**

For SMSF:

$$
Good\ Folding
=
Compression
+
Structural\ Preservation
+
Retrievability
$$

---

# 15. Folding Is Not Prediction

This distinction is fundamental.

A conventional prediction pipeline may be summarized as:

```text
Historical Data
      ↓
Training
      ↓
Predictive Model
      ↓
Current Input
      ↓
Prediction
```

SMSF instead begins with:

```text
Historical Data
      ↓
Pattern Discovery
      ↓
Pattern IR
      ↓
X-Y-M Historical Episodes
      ↓
Structural Folding
      ↓
Navigable Historical Evidence
```

Prediction becomes only one possible downstream operation.

A well-folded historical structure may additionally support:

* structural search;
* historical comparison;
* context comparison;
* event analysis;
* counterfactual inspection;
* risk analysis;
* pattern discovery;
* regime analysis;
* multi-source composition;
* policy evaluation;
* explanation;
* provenance tracing;
* local model training;
* AI structural queries.

Therefore:

> **Prediction is one possible API of well-folded historical structure, not the definition of the structure itself.**

---

# 16. Provenance Must Survive Folding

Structural evidence should remain traceable.

A folded pattern or leaf should therefore retain sufficient provenance to answer questions such as:

* Which stocks contributed observations?
* Which historical intervals contributed?
* Which Pattern IR version was used?
* Which metric was used?
* Which market regime was active?
* How many observations support the structure?
* Which RHS outcomes were observed?
* Which transformation produced the current representation?

A possible provenance record may contain:

```text
Pattern ID
Ticker / Asset ID
Source Time Range
Pattern IR Version
Discovery Algorithm Version
Metric Version
Context
Observation Count
Outcome Distribution
Construction Timestamp
Source References
```

This supports:

$$
Recommendation
\rightarrow
DecisionInterface
\rightarrow
Leaf
\rightarrow
Pattern
\rightarrow
HistoricalEpisode
$$

Such explanation is computationally traceable rather than merely narrative.

---

# 17. Historical Evidence Should Remain Policy-Neutral

SMSF distinguishes historical evidence from user preference.

Historical folding primarily answers:

> What happened under structurally similar conditions?

User policy answers:

> Given this evidence and my objectives, what should I prefer?

These are different questions.

Therefore the canonical historical fold should normally avoid embedding a particular user's investment policy directly into the evidence structure.

Conceptually:

$$
Evidence\ Folding
\perp
User\ Policy
$$

This permits the same folded historical evidence to support different users:

```text
                 Folded Evidence
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
   Conservative    Aggressive     Hedging
      Policy          Policy        Policy
```

Later SMSF stages may generate policy spaces dynamically from leaf evidence.

This separation preserves reuse and prevents historical evidence from being unnecessarily coupled to one decision preference.

---

# 18. Heavy Fold, Light Unfold

SMSF naturally supports an asymmetric computational architecture.

Offline processing may perform expensive operations such as:

* historical scanning;
* pattern discovery;
* Pattern IR construction;
* metric computation;
* differential-tree construction;
* leaf aggregation;
* CCC analysis;
* statistical measurement;
* provenance indexing.

Online processing can then operate on already-folded structures.

Conceptually:

$$
\boxed{
Heavy\ Offline\ Fold
}
$$

followed by:

$$
\boxed{
Light\ Online\ Unfold
}
$$

This is attractive for interactive applications because online computation can concentrate on:

* current-pattern extraction;
* leaf localization;
* evidence retrieval;
* interface composition;
* scoring;
* policy generation;
* explanation.

---

# 19. Important Methodological Constraints

Stock-market data create several methodological risks that SMSF implementations must treat explicitly.

---

## 19.1 Look-Ahead Leakage

\(X\) must contain only information available before the decision boundary.

RHS information must not leak into pattern discovery or Pattern IR construction.

---

## 19.2 Temporal Validation

Random train/test splitting may create misleading results in non-stationary markets.

Chronological validation and walk-forward evaluation should normally be preferred.

---

## 19.3 Overlapping Observations

SMSF explicitly permits overlapping patterns.

However, overlapping observations are not necessarily statistically independent.

Raw support counts should therefore not automatically be interpreted as independent sample counts.

---

## 19.4 Market Non-Stationarity

A structurally similar pattern observed in different historical regimes may have different RHS behavior.

SMSF should therefore permit:

* regime dimensions;
* recency weighting;
* temporal decay;
* context separation;
* versioned folds.

---

## 19.5 Outcome Horizon

Outcome definitions must preserve their time horizon.

For example:

$$
Y^{5d}
\neq
Y^{60d}
$$

unless an explicit transformation defines their relationship.

---

## 19.6 Score Is Not Automatically Probability

Different SMSF components may produce:

* similarity scores;
* CCC scores;
* support ratios;
* statistical probabilities;
* policy utility scores.

These values should remain semantically distinct.

A value of:

```text
Score = 0.82
```

must not automatically be presented as:

```text
Probability = 82%
```

---

## 19.7 Historical-Universe Bias

Stock-market implementations should account for issues such as:

* survivorship bias;
* delisted securities;
* mergers;
* historical index membership;
* data revisions;
* missing observations.

Structural folding cannot correct biases that have already been introduced into the historical universe.

---

# 20. The Canonical SMSF Transformation

The first-stage SMSF transformation can now be summarized as:

```text
Historical Market Observations
             │
             ▼
     Pattern Discovery
             │
             ▼
         Pattern IR
             │
             ▼
      X-Y-M Episodes
             │
             ├──── Context
             ├──── Events
             ├──── Multiple Granularities
             ├──── Multiple Perspectives
             └──── Provenance
             │
             ▼
   Structural Pattern Collection
             │
             ▼
     Differential Folding
             │
             ▼
Navigable Structural Experience
```

Or mathematically:

$$
\mathcal{H}
\rightarrow
\{P_i=(X_i,Y_i,M_i)\}_{i=1}^{N}
\rightarrow
\mathcal{F}
$$

where:

* \(\mathcal{H}\) is historical market experience;
* \(P_i\) is a discovered historical structural episode;
* \(\mathcal{F}\) is the folded structural knowledge space.

The next question is:

> How should the \(X_i\) structures be organized so that similar historical experience can be efficiently localized without destroying meaningful structural differences?

SMSF answers this with the **Pattern Differential Tree**.

---

# 21. From Historical Experience to Decision Unfolding

The complete architectural direction is:

$$
Historical\ Market\ Data
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
$$

The responsibilities remain separated:

### Offline

Fold historical evidence.

### Online

Locate and unfold relevant possibilities.

### Policy Layer

Evaluate the unfolded evidence according to current objectives.

This separation can be summarized as:

> **Fold evidence offline; unfold possibilities online; apply policy after evidence whenever possible.**

---

# 22. Why the Stock Market Is a Useful Canonical Domain

SMSF is intentionally developed first in the stock-market domain.

The stock market provides a demanding environment containing:

* large historical datasets;
* overlapping patterns;
* multiple granularities;
* multiple perspectives;
* discrete events;
* continuous variables;
* strong context dependence;
* multi-asset interaction;
* uncertainty;
* non-stationarity;
* user-dependent policies;
* measurable future outcomes.

These properties make the market a useful stress test for structural folding.

However, the stock market is an application domain rather than a claimed theoretical boundary.

The same architectural form may later be investigated for:

* trajectories;
* function tunnels;
* behavioral episodes;
* operational histories;
* calling-graph episodes;
* other historical decision systems.

Such generalization is outside the primary scope of this article.

> **The stock market is used here as a demanding canonical domain, not as a claimed boundary of the folding architecture.**

---

# 23. Core Claims

This article establishes the following claims and design hypotheses.

### Claim 1 — Historical data are not automatically reusable structural knowledge.

Raw observations require structural organization before they can support efficient retrieval, comparison, composition, and explanation.

### Claim 2 — X-Y-M provides a useful minimal representation of historical decision episodes.

It separates antecedent structure, subsequent outcome, and quantitative outcome measures.

### Claim 3 — Pattern discovery and Pattern IR should remain extensible.

The SMSF architecture should not depend on one universal definition of a stock-market pattern.

### Claim 4 — Context and value-based events can be first-class structural dimensions.

They need not be reduced to incidental metadata or blindly appended numerical features.

### Claim 5 — Structural Folding is broader than Pattern Folding.

The folded system may preserve patterns, contexts, events, outcomes, measures, evidence, provenance, and decision interfaces.

### Claim 6 — Good folding preserves future unfolding capacity.

Historical uncertainty and alternative outcomes should not be prematurely destroyed merely to produce one compact prediction.

### Claim 7 — Evidence and user policy should normally remain separated.

One folded historical knowledge structure should be reusable under multiple decision policies.

### Claim 8 — Prediction is an API, not the definition of folded knowledge.

A folded structural market runtime can support search, comparison, analysis, decision support, explanation, and AI interaction in addition to prediction.

---

# 24. Design Principle

The central design principle of SMSF-001 is:

$$
\boxed{
Many\ Historical\ Episodes
\xrightarrow{Structural\ Folding}
Navigable\ Historical\ Evidence
}
$$

followed later by:

$$
\boxed{
Current\ Observation
\xrightarrow{Structural\ Unfolding}
Relevant\ Historical\ Possibility\ Space
}
$$

The quality of the architecture therefore depends not only on how much information can be compressed, but on whether the folded representation retains the structural distinctions needed for future retrieval and decision unfolding.

---

# 25. Conclusion

Stock-Market Structural Folding begins from a simple observation:

> Historical market data contain experience, but experience becomes reusable intelligence only after it is organized into structures that can later be found, compared, composed, and unfolded.

SMSF therefore begins not with a prediction model, but with historical structural episodes.

The basic episode is:

$$
P=(X,Y,M)
$$

where \(X\) captures antecedent structure, \(Y\) captures subsequent outcome, and \(M\) preserves measurable properties of that outcome.

Pattern discovery and Pattern IR remain open interfaces. Context and value-based events can participate directly in structural representation. Multiple granularities and perspectives may coexist. Provenance remains attached to folded evidence. User policy is normally kept separate from canonical historical evidence.

The resulting objective is not to reduce market history to a single answer.

It is to construct:

$$
\boxed{
A\ Navigable\ Structural\ Memory\ of\ Historical\ Market\ Experience
}
$$

Such a memory can later support localization, Two-Way CCC analysis, leaf decision interfaces, multi-source composition, on-the-fly policy unfolding, AI structural queries, and traceable decision support.

The next stage of SMSF therefore asks:

> **How can the X-side of historical experience be organized into a differential structure that preserves meaningful similarity while exposing meaningful difference?**

That is the role of the **Pattern Differential Tree**.

---

## Next

**SMSF-002 — Pattern Differential Tree: Structural Organization of Market Experience**

The next article develops:

$$
X
\rightarrow
Metric\ Differential\ Analysis
\rightarrow
Pattern\ Differential\ Tree
\rightarrow
Structural\ Leaf
$$

and establishes the structural backbone upon which later Leaf Decision Interfaces and Online Unfolding operate.

---

## Repository

**Stock-Market Structural Folding (SMSF)**

A structural approach to folding historical market experience into reusable evidence and unfolding that evidence for online decision support.
```
