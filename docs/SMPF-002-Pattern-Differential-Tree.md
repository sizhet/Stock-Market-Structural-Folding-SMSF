````markdown
# SMPF-002 — Pattern Differential Tree: Structural Organization of Market Experience

**Stock-Market Structural Folding (SMSF)**  
**A Differential-Tree Architecture for Historical Evidence Folding and Decision Unfolding**

---

## Abstract

Stock-Market Structural Folding (SMSF) represents historical market experience as structural episodes:

\[
P_i=(X_i,Y_i,M_i)
\]

where \(X_i\) describes the antecedent structure, \(Y_i\) describes the subsequent outcome, and \(M_i\) records quantitative properties of that outcome.

Once these episodes have been discovered, a central problem remains:

> How should a large collection of historical \(X\)-structures be organized so that structurally similar experience can be efficiently localized while meaningful differences remain visible?

SMSF addresses this problem through the **Pattern Differential Tree**.

The Pattern Differential Tree organizes historical patterns according to measured structural differences. Rather than treating historical experience as a flat collection of windows or forcing all observations into one monolithic feature space, the tree progressively separates pattern populations using selected metrics, perspectives, granularities, contexts, and value-based events.

Conceptually:

\[
\{X_1,X_2,\ldots,X_N\}
\xrightarrow{Differential\ Folding}
T_X
\]

where \(T_X\) is a navigable structural topology over historical antecedent patterns.

The tree is not merely a classification taxonomy. It is a runtime structure for localization, retrieval, comparison, explanation, later Two-Way CCC analysis, and online decision unfolding.

Context and events may appear either inside Pattern IR or as explicit differential dimensions. Multiple perspectives may coexist. Different branches may use different metrics. Leaf granularity may be adaptive rather than globally fixed.

The resulting architecture transforms historical pattern collections into a structured search and decision substrate:

\[
Historical\ Experience
\rightarrow
Structural\ Difference
\rightarrow
Differential\ Tree
\rightarrow
Localized\ Evidence
\]

This article defines the Pattern Differential Tree, its construction principles, its relationship to Pattern IR, and its role as the structural backbone of SMSF.

---

# 1. The Problem After Pattern Discovery

SMSF-001 introduced historical structural episodes:

\[
P_i=(X_i,Y_i,M_i)
\]

Suppose an offline process discovers:

\[
P_1,P_2,\ldots,P_N
\]

The system now possesses many historical experiences.

But a flat collection remains difficult to use.

For example:

```text
Pattern-000001
Pattern-000002
Pattern-000003
...
Pattern-987451
````

Given a current market pattern \(X_q\), the runtime must answer:

> Which historical experiences are structurally relevant?

A brute-force solution is:

$$
d(X_q,X_i)
\quad
\forall i
$$

followed by ranking all historical observations.

This may work at small scale.

However, it leaves several important problems unresolved:

* structural differences remain implicit;
* context is difficult to inspect;
* multiple perspectives are flattened;
* explanation becomes similarity-score reporting;
* repeated queries repeat large amounts of work;
* historical experience remains weakly organized;
* local structural populations are not explicitly represented.

SMSF therefore introduces an intermediate structural object:

$$
\boxed{
Pattern\ Differential\ Tree
}
$$

---

# 2. Core Transformation

The basic transformation is:

$$
\{X_1,X_2,\ldots,X_N\}
\rightarrow
T_X
$$

where:

$$
T_X = Pattern\ Differential\ Tree
$$

The tree progressively organizes historical antecedent patterns according to structural differences.

Conceptually:

```text
Historical X Patterns
        │
        ▼
Difference Detection
        │
        ▼
Metric / Perspective Selection
        │
        ▼
Differential Branching
        │
        ▼
Local Structural Populations
        │
        ▼
Pattern Leaves
```

The resulting tree provides a structural coordinate system over historical experience.

---

# 3. Why "Differential Tree"?

The word **differential** is central.

The tree does not primarily ask:

> What predefined category does this pattern belong to?

It asks:

> Along which meaningful structural dimension do these patterns differ?

Suppose a population contains patterns with similar price trajectories but substantially different volume behavior.

A useful differential dimension may be:

```text
Volume Structure
      │
      ├── Contraction
      ├── Neutral
      └── Expansion
```

Another population may instead be best separated by market regime:

```text
Market Context
      │
      ├── Bull
      ├── Sideways
      └── Bear
```

A third population may require a continuous metric split:

```text
Trajectory Distance
      │
      ├── Region A
      ├── Region B
      └── Region C
```

The differential dimension therefore does not have to be globally identical across the tree.

This gives the tree adaptive structural semantics.

---

# 4. Structural Difference Before Decision Outcome

An important design discipline is:

> **The Pattern Differential Tree is primarily constructed from the X-side.**

That is:

$$
X
\rightarrow
Tree
$$

rather than:

$$
Y
\rightarrow
Tree
$$

This separation matters.

If future outcome \(Y\) directly determines the antecedent tree structure, the system risks leaking RHS information into historical localization.

The intended architecture is:

```text
                 X
                 │
                 ▼
      Pattern Differential Tree
                 │
                 ▼
               Leaf
                 │
                 │
          historical Y/M
                 │
                 ▼
       Leaf Decision Analysis
```

Thus:

$$
X
\rightarrow
Localization
$$

and later:

$$
Y,M
\rightarrow
Decision\ Interface
$$

This preserves the conceptual boundary between:

* antecedent structural organization;
* subsequent outcome analysis.

---

# 5. Pattern IR Defines the Searchable Structural Object

The Pattern Differential Tree does not operate directly on an abstract notion of "pattern."

It operates on a Pattern IR.

Let:

$$
IR(X_i)
$$

be the intermediate representation of pattern \(X_i\).

Then differential analysis operates on:

$$
d(IR(X_i),IR(X_j))
$$

or on selected structural dimensions within the IR.

Different Pattern IRs may expose different dimensions.

For example:

```text
Pattern IR
│
├── PriceTrajectory
├── VolumeTrajectory
├── VolatilityState
├── EventSequence
├── MarketContext
├── CrossAssetContext
└── StructuralMetadata
```

Another user may define:

```text
Pattern IR
│
├── CCC
├── TrajectorySignature
├── EventGraph
└── RegimeCoordinates
```

SMSF does not require these representations to be identical.

The tree consumes the structural interface exposed by the selected Pattern IR.

---

# 6. Metric Distance as a Differential Mechanism

A core implementation mechanism is Metric Distance.

Given two pattern representations:

$$
X_a,\ X_b
$$

a metric may define:

$$
d(X_a,X_b)
$$

Small distance suggests structural similarity.

Large distance suggests meaningful difference.

However, SMSF should not assume that one metric is sufficient for all structures.

Instead:

$$
d_k(X_a,X_b)
$$

may represent a metric under perspective \(k\).

Examples include:

$$
d_{price}
$$

$$
d_{volume}
$$

$$
d_{trajectory}
$$

$$
d_{event}
$$

$$
d_{context}
$$

$$
d_{cross-asset}
$$

Therefore the differential tree may be constructed through:

$$
\mathcal{D}
=
\{
d_1,d_2,\ldots,d_K
\}
$$

rather than one universal metric.

---

# 7. Metric Distance Is Not the Same as Structural Meaning

SMSF uses metrics as tools.

It does not equate:

$$
Metric\ Similarity
=
Structural\ Identity
$$

Two patterns may be numerically close under one metric but structurally different under another perspective.

For example:

```text
Pattern A:
    price shape ≈ Pattern B

but

Pattern A:
    Fed easing

Pattern B:
    Fed tightening
```

Price-distance alone may report:

$$
d_{price}(A,B)\approx 0
$$

while context difference remains substantial.

Therefore:

$$
Structural\ Comparison
=
Metric\ Evidence
+
Perspective
+
Context
+
IR\ Semantics
$$

The differential tree provides a mechanism for preserving these distinctions rather than collapsing all similarity into one scalar.

---

# 8. Multi-Perspective Differential Folding

A major capability of the Pattern Differential Tree is **multi-perspective folding**.

Suppose one historical population is examined from:

```text
Price
Volume
Volatility
Market Regime
Macro Event
Cross-Stock State
```

The tree may use these perspectives sequentially or selectively.

For example:

```text
Root
│
├── Price Structure A
│   │
│   ├── Low Volatility
│   │   │
│   │   ├── Bull Context
│   │   └── Bear Context
│   │
│   └── High Volatility
│
└── Price Structure B
    │
    ├── Volume Expansion
    └── Volume Contraction
```

Different branches need not use identical dimensions.

This is important.

The useful difference for one structural population may be irrelevant for another.

---

# 9. Differential Dimensions Can Be Continuous or Discrete

A Pattern Differential Tree is not restricted to categorical branching.

A differential dimension may be:

### Continuous

```text
Volatility
│
├── [0.00, 0.15)
├── [0.15, 0.30)
└── [0.30, +∞)
```

### Ordinal

```text
Trend Strength
│
├── Weak
├── Medium
└── Strong
```

### Categorical

```text
Market Regime
│
├── Bull
├── Sideways
└── Bear
```

### Event-Based

```text
Fed Policy Event
│
├── Tightening
├── Unchanged
└── Easing
```

### Structural

```text
Trajectory Form
│
├── Compression
├── Breakout
├── Reversal
└── Oscillation
```

### Metric-Derived

```text
Distance Region
│
├── Near
├── Intermediate
└── Far
```

This flexibility is important because market structure is heterogeneous.

---

# 10. Context as a Differential Coordinate

SMSF-001 introduced Context as first-class structural information.

The Pattern Differential Tree provides a natural place to operationalize that idea.

Consider a local pattern:

```text
Price Compression
+
Volume Contraction
```

Its RHS behavior may differ dramatically under different market regimes.

Instead of encoding regime only as an opaque feature, SMSF may construct:

```text
Price Compression
      │
      ▼
Volume Contraction
      │
      ▼
Market Regime
      │
      ├── Bull
      ├── Sideways
      └── Bear
```

Context becomes a structural coordinate.

This makes questions such as the following directly inspectable:

> How does the same local pattern behave under different market regimes?

The tree therefore supports not only retrieval but structural comparison.

---

# 11. Value-Based Events as Differential Layers

Value-based events are particularly well suited to explicit differential branching.

Consider a historical population sharing a similar local price structure.

The tree may introduce:

```text
Fed Policy
│
├── Rate Increase
├── No Change
└── Rate Decrease
```

or more finely:

```text
Fed Rate Change
│
├── ≤ -50 bp
├── -25 bp
├── 0 bp
├── +25 bp
└── ≥ +50 bp
```

The same principle applies to:

* CPI surprise;
* earnings surprise;
* policy announcement;
* regulatory action;
* index inclusion;
* merger event;
* liquidity intervention.

This creates a structural basis for later comparisons such as:

$$
Outcome(X,Event_A)
$$

versus:

$$
Outcome(X,Event_B)
$$

Thus an event can become part of the navigable historical topology.

---

# 12. Event in X vs Event as a Tree Layer

These two approaches are complementary.

## Case A — Event Is Part of X

$$
X=(Pattern,Event)
$$

Use this when the event is semantically inseparable from the pattern being studied.

Example:

> Post-Fed-rate-cut rebound pattern.

---

## Case B — Event Is a Differential Layer

```text
Common Pattern
      │
      ├── Event A
      ├── Event B
      └── Event C
```

Use this when the objective is to preserve a common structural pattern while comparing event-conditioned outcomes.

This distinction gives SMSF a useful modeling choice:

> Should an event define the pattern, or should it differentiate otherwise similar patterns?

The answer depends on the research objective.

---

# 13. Multi-Granularity Differential Trees

Historical patterns may exist at different temporal granularities.

For example:

$$
g\in
\{
5m,
1h,
1d,
5d,
20d,
60d
\}
$$

SMSF may maintain:

$$
T_X^{5m}
$$

$$
T_X^{1d}
$$

$$
T_X^{20d}
$$

or combine granularity as an explicit structural coordinate.

For example:

```text
Pattern Family
│
├── Intraday
│   ├── 5-Minute
│   └── 1-Hour
│
├── Short-Term
│   ├── 1-Day
│   └── 5-Day
│
└── Medium-Term
    ├── 20-Day
    └── 60-Day
```

There is no requirement that all granularities share identical metrics or leaf criteria.

This allows SMSF to preserve scale-specific structure.

---

# 14. Multiple Trees Are Allowed

The term "Pattern Differential Tree" should not be interpreted as requiring exactly one universal tree.

A deployment may maintain:

```text
Price Pattern Tree

Volume Pattern Tree

Macro Event Tree

Cross-Stock Tree

Trajectory Tree
```

or:

```text
MSFT Tree

SP500 Tree

QQQ Tree

VIX Tree
```

or multiple trees defined by different Pattern IRs.

Later online composition may combine their leaf interfaces.

Therefore:

$$
SMSF
\neq
One\ Giant\ Tree
$$

A more scalable interpretation is:

$$
SMSF
=
\{T_1,T_2,\ldots,T_n\}
+
Composition
$$

This becomes important when the system scales across multiple stocks, indexes, events, and structural perspectives.

---

# 15. Scale by Structural Decomposition

A naive multi-stock model may construct:

$$
X=
[
MSFT,
SP500,
QQQ,
VIX,
Rates,
Events,
\ldots
]
$$

and place everything into one very high-dimensional representation.

SMSF permits another strategy.

Each source may first be structurally folded:

$$
MSFT
\rightarrow
T_{MSFT}
$$

$$
SP500
\rightarrow
T_{SP500}
$$

$$
QQQ
\rightarrow
T_{QQQ}
$$

$$
VIX
\rightarrow
T_{VIX}
$$

At runtime, evidence can later be composed through their leaf interfaces.

Thus:

> **Scale by structural decomposition first, then interface composition.**

This can reduce the pressure to construct one universal raw-feature space.

---

# 16. Differential Tree Construction

A generic construction process can be described as follows.

Given:

$$
S_0=
\{X_1,X_2,\ldots,X_N\}
$$

start with:

```text
Root = S0
```

For a candidate node \(S\):

1. inspect structural variation;
2. identify candidate differential dimensions;
3. evaluate available metrics;
4. select a useful structural split;
5. partition \(S\);
6. recursively analyze child populations;
7. stop when leaf criteria are satisfied.

Conceptually:

```text
function build(node):

    inspect(node.patterns)

    if leafCondition(node):
        return Leaf(node.patterns)

    perspective = choosePerspective(node)
    metric      = chooseMetric(node, perspective)
    split       = deriveDifferentialSplit(node, metric)

    children = partition(node.patterns, split)

    for child in children:
        build(child)
```

This is conceptual pseudocode rather than a mandatory implementation.

SMSF intentionally leaves room for different tree-construction algorithms.

---

# 17. What Makes a Good Differential Split?

A useful differential split should expose meaningful structural distinction.

Possible criteria include:

* metric separation;
* structural coherence;
* stability;
* sufficient support;
* interpretability;
* context significance;
* downstream outcome differentiation;
* computational efficiency;
* user-defined importance.

However, caution is required with downstream \(Y\).

The tree should not become an outcome-leaking classifier.

A safe distinction is:

### Tree Construction

primarily based on available \(X\)-structure.

### Tree Evaluation

may examine whether the resulting structural regions produce meaningful RHS distinctions.

Thus \(Y\) can help evaluate whether a structural fold is useful without becoming illicit future information during online localization.

---

# 18. Structural Recognition Above Metric Similarity

Metric distance is necessary but not sufficient.

Suppose:

$$
d(X_a,X_b)
<
d(X_a,X_c)
$$

A pure nearest-neighbor system concludes that \(X_b\) is more relevant.

But structural information may reveal:

```text
Xa and Xb:
    numerically similar
    structurally different regime

Xa and Xc:
    slightly farther numerically
    same event structure
    same trajectory family
    same market context
```

The Pattern Differential Tree can preserve these distinctions explicitly.

Thus SMSF favors:

$$
Structural\ Recognition
$$

over blindly accepting:

$$
Lowest\ Scalar\ Distance
$$

Metrics remain important, but they operate inside a structural organization rather than replacing it.

---

# 19. Adaptive Leaf Granularity

A leaf should not necessarily contain a fixed number of observations.

Different regions of market history have different structural density.

For example:

```text
Dense Structural Region
    → finer leaves

Sparse Structural Region
    → broader leaves
```

Possible leaf criteria include:

* minimum observation count;
* maximum internal distance;
* structural coherence;
* metric stability;
* context purity;
* computational budget;
* downstream evidence sufficiency.

Therefore leaf granularity may adapt to the available historical evidence.

---

# 20. What Is a Pattern Leaf?

A Pattern Leaf represents a localized historical structural population.

Let:

$$
L_j
=
\{
P_{j1},P_{j2},\ldots,P_{jn}
\}
$$

where each:

$$
P_{jk}
=
(X_{jk},Y_{jk},M_{jk})
$$

and the \(X_{jk}\) values are structurally related according to the tree path.

A leaf therefore contains:

```text
Leaf
│
├── Structural Path
├── X Population
├── Historical Y Population
├── Historical M Population
├── Context
├── Provenance
└── Structural Statistics
```

The leaf is not yet the final decision answer.

It is a localized evidence container.

---

# 21. Leaf CCC

Once a sufficiently coherent leaf has been formed, SMSF may compute a CCC representation for its \(X\)-population.

Conceptually:

$$
CCC(L_j)
=
CCC(
X_{j1},
X_{j2},
\ldots,
X_{jn}
)
$$

The Leaf CCC can serve as:

* a structural summary;
* a recognition handle;
* a localization reference;
* a compact runtime representation;
* a comparison object.

This gives the leaf both:

$$
Raw/Indexed\ Evidence
$$

and:

$$
Structural\ Core
$$

The exact CCC construction is implementation-dependent.

---

# 22. Leaf CCC Does Not Replace Leaf Evidence

This distinction is important.

The leaf CCC should not destroy the underlying historical population.

Instead:

```text
Pattern Leaf
│
├── Leaf CCC
│
├── Observation References
│
├── Y Distribution
│
├── M Measures
│
├── Context
└── Provenance
```

Thus the CCC acts as a structural handle rather than a lossy replacement for all historical evidence.

This supports later:

* explanation;
* auditing;
* re-analysis;
* local modeling;
* policy unfolding;
* provenance tracing.

---

# 23. The Leaf as the Offline/Online Handshake

The Pattern Leaf has a special architectural role.

Offline:

$$
Historical\ Patterns
\rightarrow
Differential\ Tree
\rightarrow
Leaf
$$

Online:

$$
Current\ Pattern
\rightarrow
Differential\ Tree
\rightarrow
Leaf
$$

Therefore the leaf becomes a handshake point between:

$$
Offline\ Folding
$$

and:

$$
Online\ Unfolding
$$

This is one of the most important structural properties of SMSF.

The offline system organizes historical experience.

The online system localizes current experience into the same structural topology.

---

# 24. Online Localization

Given a current target pattern:

$$
X_q
$$

the online runtime traverses the Pattern Differential Tree.

Conceptually:

```text
Current X
   │
   ▼
Root
   │
   ▼
Differential Test
   │
   ▼
Branch
   │
   ▼
Differential Test
   │
   ▼
Branch
   │
   ▼
Pattern Leaf
```

This converts the online problem from:

$$
Compare\ X_q\ with\ every\ historical\ pattern
$$

into:

$$
Navigate\ X_q\ through\ folded\ structural\ differences
$$

The result is structural localization.

---

# 25. Localization Need Not Be Hard Single-Path Routing

A strict tree may choose exactly one child at every branch.

However, market patterns may lie near structural boundaries.

SMSF can therefore permit:

### Hard Routing

$$
X_q\rightarrow L_i
$$

or:

### Soft Routing

$$
X_q
\rightarrow
\{
(L_i,w_i),
(L_j,w_j),
\ldots
\}
$$

where:

$$
w_i
$$

represents localization relevance.

This enables the runtime to preserve uncertainty near differential boundaries.

It may also improve robustness when Pattern IR or metric boundaries are approximate.

---

# 26. Multi-Leaf Retrieval

Online unfolding may therefore retrieve:

$$
L_1,L_2,\ldots,L_k
$$

rather than exactly one leaf.

For example:

```text
Current Pattern
      │
      ▼
Differential Tree
      │
      ├── Leaf A   similarity = 0.91
      ├── Leaf B   similarity = 0.84
      └── Leaf C   similarity = 0.72
```

These leaves may later contribute weighted decision evidence.

This preserves the distinction between:

$$
Localization
$$

and:

$$
Final\ Decision
$$

which is another important SMSF design discipline.

---

# 27. Structural Search vs Flat Similarity Search

A flat similarity engine performs:

$$
Query
\rightarrow
Nearest\ Historical\ Windows
$$

A Pattern Differential Tree performs:

$$
Query
\rightarrow
Structural\ Localization
\rightarrow
Relevant\ Historical\ Region
$$

The latter exposes the path.

For example:

```text
Current MSFT Pattern
        │
        ▼
Price: Compression
        │
        ▼
Volume: Contraction
        │
        ▼
Market: Bull
        │
        ▼
Fed: Easing
        │
        ▼
Leaf L-204
```

This path itself is explanatory evidence.

The runtime can answer not only:

> Which leaf matched?

but:

> Why was this historical region selected?

---

# 28. Differential Paths as Explanations

Each tree traversal produces a structural path:

$$
Path(X_q)
=
(D_1,D_2,\ldots,D_n)
$$

where \(D_i\) represents a differential decision.

For example:

```text
Trajectory Family      = Compression
Volume State           = Contracting
Volatility Regime      = Low
Market Regime          = Bull
Fed Policy             = Easing
```

This gives SMSF an intrinsic explanation structure.

The explanation does not need to be generated after the fact.

It already exists in the computation.

This can be described as:

$$
\boxed{
Explanation\ by\ Structural\ Traversal
}
$$

---

# 29. Provenance Through the Tree

Each leaf should preserve references to the historical episodes that contributed to it.

Thus:

$$
Leaf
\rightarrow
Pattern\ IDs
\rightarrow
Historical\ Episodes
\rightarrow
Source\ Data
$$

The complete trace may be:

```text
Online Recommendation
        │
        ▼
Decision Interface
        │
        ▼
Pattern Leaf
        │
        ▼
Differential Path
        │
        ▼
Historical Patterns
        │
        ▼
Original Time Ranges
```

This provides computationally traceable evidence.

---

# 30. Versioning the Fold

Markets change.

Pattern IRs change.

Metrics change.

Tree-building algorithms change.

Therefore the Pattern Differential Tree should be treated as a versioned structural artifact.

Possible metadata include:

```text
Tree ID
Tree Version
Construction Time
Historical Cutoff
Pattern IR Version
Metric Set Version
Context Schema Version
Tree Algorithm Version
Observation Universe
```

This permits comparisons such as:

$$
T^{v1}
$$

versus:

$$
T^{v2}
$$

and avoids treating the fold as permanently correct.

---

# 31. Incremental Growth

A mature implementation need not rebuild the entire tree after every new observation.

Possible operations include:

```text
New Historical Episode
        │
        ▼
Pattern Discovery
        │
        ▼
Pattern IR
        │
        ▼
Tree Localization
        │
        ▼
Existing Leaf
        │
        ├── Accept
        ├── Update
        ├── Split
        └── Create Candidate Branch
```

This suggests a future path toward structural continual learning.

However, incremental tree evolution is not required for the minimal SMSF architecture.

The first implementation may rebuild trees offline.

---

# 32. Gap Detection

New market structures may fail to fit existing leaves well.

Suppose:

$$
\min_j d(X_q,L_j)
>
\tau
$$

or multiple structural tests fail.

The system may classify the observation as a:

$$
Structural\ Gap
$$

Possible responses include:

```text
Gap
│
├── store observation
├── mark low-confidence localization
├── request alternate Pattern IR
├── invoke user/AI plugin
├── create candidate branch
└── trigger future refolding
```

This prevents the runtime from forcing every new pattern into an existing historical category.

---

# 33. Pattern Differential Tree as Structural Memory

At this point the tree can be understood as more than an index.

It contains:

* historical structural distinctions;
* local pattern populations;
* structural paths;
* context coordinates;
* event coordinates;
* leaf CCCs;
* provenance;
* links to RHS evidence.

Thus:

$$
Pattern\ Differential\ Tree
\approx
Structural\ Memory
$$

of historical market experience.

This memory is navigable.

That property is central to later AI interaction.

---

# 34. AI-Friendly Structural Navigation

An AI agent operating on a Pattern Differential Tree does not need to reason only over raw price tables.

It can operate on explicit structural objects such as:

```text
Pattern
Differential Dimension
Branch
Leaf
CCC
Context
Event
Outcome
Measure
Provenance
```

This makes queries possible at a higher semantic level.

For example:

```text
Find leaves structurally similar to current MSFT.

Compare the same price pattern under
Fed tightening and Fed easing.

Return leaves with at least 100 observations.

Show the differential path for Leaf L-204.

Trace the historical episodes supporting this leaf.
```

The tree therefore provides a natural substrate for future structural query APIs.

---

# 35. SQL-Like Structural Query Direction

A future SMSF runtime may expose operations such as:

```text
MATCH PATTERN
LOCALIZE LEAF
COMPARE CONTEXT
FILTER SUPPORT
UNFOLD OUTCOME
MERGE INTERFACES
TRACE PROVENANCE
```

For example:

```text
MATCH current_msft
IN price_pattern_tree

UNDER
    market_regime = bull
    fed_policy = easing

RETURN
    matching_leaves,
    structural_distance,
    support,
    provenance
```

Such an interface would not merely query database rows.

It would query:

$$
\boxed{
Folded\ Structural\ Experience
}
$$

Detailed API design remains a future SMSF direction.

---

# 36. The Tree Does Not Yet Make the Final Decision

This boundary should remain explicit.

The Pattern Differential Tree answers:

> Where in historical structural experience does the current pattern belong?

It does not yet answer:

> What should the user do?

The architecture is:

$$
Current\ X
\rightarrow
Pattern\ Differential\ Tree
\rightarrow
Leaf
$$

then:

$$
Leaf
\rightarrow
Historical\ Y/M\ Analysis
\rightarrow
Decision\ Interface
$$

then later:

$$
Decision\ Interface
+
Policy
\rightarrow
Recommendation
$$

This separation keeps:

* localization;
* evidence;
* policy;

architecturally distinct.

---

# 37. From Pattern Leaf to Two-Way CCC

Once the Pattern Differential Tree has localized a structurally coherent historical population, the next question becomes:

> What RHS outcomes occurred for the observations in this leaf?

Suppose:

$$
L_j
=
\{
(X_1,Y_1,M_1),
\ldots,
(X_n,Y_n,M_n)
\}
$$

SMSF can analyze:

$$
\{Y_1,Y_2,\ldots,Y_n\}
$$

through Two-Way CCC and construct a structured outcome interface.

Conceptually:

```text
Pattern Leaf
     │
     ▼
Historical RHS Population
     │
     ▼
Two-Way CCC Analysis
     │
     ▼
Outcome Branches
     │
     ▼
Pattern Leaf Decision Interface
```

This is the subject of **SMSF-003**.

---

# 38. Canonical Pattern Differential Tree Architecture

The complete structure developed in this article can be summarized as:

```text
                   HISTORICAL X PATTERNS
                           │
                           ▼
                     Pattern IR
                           │
                           ▼
              Structural Difference Analysis
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
         Metric        Perspective      Context
        Distance        Difference       / Event
            │              │              │
            └──────────────┼──────────────┘
                           ▼
                  Differential Branch
                           │
                           ▼
                    Local Population
                           │
                           ▼
                  Further Differencing
                           │
                           ▼
                     Pattern Leaf
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
          Leaf CCC      Evidence      Provenance
                           │
                           ▼
                     Historical Y/M
                           │
                           ▼
                    SMSF-003:
              Leaf Decision Interface
```

---

# 39. Core Properties

A useful SMSF Pattern Differential Tree should aim for the following properties.

### 39.1 Structural

Branches represent meaningful differences rather than arbitrary database partitions.

### 39.2 Navigable

Current patterns can be efficiently localized.

### 39.3 Multi-Perspective

Different structural dimensions may participate in the fold.

### 39.4 Multi-Granularity

Different temporal scales may coexist.

### 39.5 Context-Aware

Market context can become an explicit structural coordinate.

### 39.6 Event-Aware

Value-based events can participate directly in branching.

### 39.7 Extensible

Pattern IRs, metrics, and discovery algorithms may be supplied by plugins.

### 39.8 Traceable

Leaves retain provenance to historical episodes.

### 39.9 Adaptive

Different structural regions may use different leaf granularities.

### 39.10 Policy-Neutral

The canonical tree primarily organizes historical evidence rather than one user's decision preference.

---

# 40. Core Claims

This article makes the following architectural claims.

### Claim 1 — Historical patterns benefit from structural organization beyond flat similarity search.

A differential topology exposes meaningful historical distinctions before online decision scoring.

### Claim 2 — The X-side should define the primary localization structure.

This preserves the boundary between antecedent recognition and RHS outcome analysis.

### Claim 3 — Metric distance should operate inside structural semantics.

No single scalar distance should automatically define structural identity.

### Claim 4 — Context and value-based events can become explicit differential coordinates.

This makes context-conditioned historical comparison directly navigable.

### Claim 5 — Multiple trees and perspectives are legitimate.

SMSF does not require one universal high-dimensional tree.

### Claim 6 — Pattern leaves are localized evidence containers.

They are not final predictions.

### Claim 7 — Leaf CCC provides a structural handle without replacing underlying evidence.

### Claim 8 — The leaf forms the handshake between offline folding and online unfolding.

### Claim 9 — Structural traversal provides intrinsic explanation.

### Claim 10 — A Pattern Differential Tree can serve as AI-queryable structural memory.

---

# 41. Design Principle

The central principle of SMSF-002 is:

$$
\boxed{
Do\ not\ merely\ search\ historical\ patterns.
Fold\ their\ meaningful\ differences.
}
$$

The objective is to transform:

$$
Flat\ Historical\ Pattern\ Collection
$$

into:

$$
Navigable\ Structural\ Topology
$$

so that current observations can later be localized against organized historical experience rather than repeatedly compared against an undifferentiated archive.

---

# 42. Conclusion

SMSF begins by converting historical market observations into X-Y-M structural episodes.

The Pattern Differential Tree performs the next transformation:

$$
\{X_1,X_2,\ldots,X_N\}
\xrightarrow{Differential\ Folding}
T_X
$$

The tree organizes historical antecedent structures through meaningful differences.

These differences may arise from:

* pattern geometry;
* trajectory;
* volume;
* volatility;
* context;
* value-based events;
* market regime;
* cross-asset state;
* user-defined structural dimensions.

Metric distance supports this process but does not define structural meaning by itself.

The resulting leaves contain localized historical populations, structural paths, CCC summaries, evidence, and provenance.

They provide the critical handshake:

$$
Offline\ Structural\ Folding
\leftrightarrow
Online\ Structural\ Localization
$$

However, localization alone is not a decision.

The next stage must examine the RHS outcomes attached to each leaf and expose those outcomes without prematurely collapsing their uncertainty.

That leads to the next SMSF component:

$$
Pattern\ Leaf
\rightarrow
Two\text{-}Way\ CCC
\rightarrow
Pattern\ Leaf\ Decision\ Interface
$$

---

## Next

**SMSF-003 — From Pattern Leaves to Decision Interfaces**

The next article develops:

* RHS outcome partitioning;
* Two-Way CCC analysis;
* Y-Buckets;
* outcome measures;
* support and scoring;
* Pattern Leaf Decision Interfaces;
* uncertainty-preserving outcome representation;
* local ANN companion models;
* online decision unfolding.

---

## Repository

**Stock-Market Structural Folding (SMSF)**

A differential-tree architecture for folding historical market experience into navigable structural evidence and unfolding that evidence for online decision support.
