---
name: paperlocus
description: "Reference-aware whole-paper reading and structured research-note generation. Supports CS, natural-science, economics, management, financial econometrics, and quantitative finance papers."
---

# PaperLocus

See the public README in the repository root for the project overview.

## Working Mode

- Treat this skill as a whole-paper reading and literature-positioning workflow.
- Produce the output in the user's preferred language. Default to Chinese if the user writes in Chinese.
- Build understanding from the paper itself first.
- Prefer a reusable Markdown note over a one-off loose summary.

## Context Construction Strategy

- Do not dump the whole paper into context unless the user explicitly wants deep reading.
- Prefer a layered context:
  1. the current paper's title, abstract, introduction claims, method frame, and core results
  2. a small set of core related papers, not the entire bibliography
  3. a reusable Markdown note that records the paper's positioning and insights
- Prioritize: papers explicitly discussed or criticized in the introduction > strong baselines used in experiments > the same narrow subfield the user is working on.

## Input Acquisition

- Accept PDF, local file, arXiv link, DOI, webpage, screenshot, or title-only input. Prefer full text.
- If sections are missing or unreadable, say so explicitly and narrow the scope.
- For PDF / local files: extract title, abstract, headers, introduction, method, results, conclusion first.
- For links / webpages: recover bibliographic metadata and the paper text before summarizing; prefer the paper over third-party commentary.
- For screenshots: treat as partial evidence; don't pretend to understand the whole paper.
- For title-only: recover abstract-level context first; if still unavailable, give a scoped triage note.

## First Decision: Classify The Paper Type

Classify into one of four branches. The classification determines which workflow to use.
If unclear, state which signals conflict and why you chose the branch.
For concrete examples see [references/paper_type_examples.md](references/paper_type_examples.md).

### Branch A: Computer-Science Conference Or arXiv

Prefer when most of:
1. abstract centered on a new model, algorithm, framework, benchmark, or training recipe
2. paper structure: `introduction -> related work -> method -> experiments -> conclusion`
3. introduction critiquing prior methods and motivating a technical design
4. main evidence is benchmarks, ablations, scaling curves, and metrics
5. contribution framed as "we propose" more than "we discover" or "we find"

### Branch B: Nature Or Science-Family

Prefer when most of:
1. abstract centered on a scientific finding, mechanism, or empirical claim about the world
2. paper organized around findings and evidence, not a standalone method section
3. introduction emphasizes a scientific question, knowledge gap, or competing explanations
4. main evidence is an accumulated chain supporting a conclusion
5. contribution framed as "we find", "we reveal", or "we show that X is true"

### Branch C: Economics And Management

Prefer when most of:
1. abstract centered on a causal question, economic mechanism, market behavior, or management phenomenon
2. paper structure: `introduction -> theory/hypotheses -> data -> empirical strategy -> results -> robustness -> conclusion`
3. introduction emphasizes a causal relationship, economic trade-off, or management problem
4. main evidence is regression tables, causal estimates, reduced-form or structural results, or theoretical proofs
5. contribution framed as "we find that X causes Y", "we estimate", "we show that...", or "we develop a model of..."

### Branch D: Financial Econometrics And Quantitative Finance

Prefer when most of:
1. abstract centered on a financial model, volatility/risk forecast, asset pricing factor, portfolio method, derivative pricing, or trading strategy
2. paper structure: `introduction -> model/method -> data -> estimation/calibration -> evaluation -> application`
3. introduction emphasizes a financial market pattern, risk measurement problem, or investment decision
4. main evidence is model diagnostics, forecast accuracy, risk backtests, portfolio performance, or pricing errors
5. contribution framed as "we propose a new model for...", "we identify a new factor...", "we develop a strategy that...", or "we improve forecast accuracy by..."

### Mixed Cases
- Classify by narrative logic, not venue. A methods paper in a science journal is still a methods paper.
- If the paper proposes a new financial model AND applies it (e.g., new volatility model + option pricing), default to Branch D.
- When uncertain, choose the branch that best matches how results are organized.

---

## Branch A: Computer-Science Workflow

- Explain the paper as `built on A, changed B, therefore obtained C`.
- Extract: the core sub-direction, key prior works critiqued, proposed framework, main claimed contributions.
- For experiments, explain why each exists, which claim it supports, and what metrics/baselines matter.

---

## Branch B: Nature / Science-Family Workflow

- Identify the core scientific question and what existing understanding the paper challenges, extends, or fills in.
- Separate the key finding from the method used to obtain it.
- Reconstruct the evidence chain supporting the central conclusion.
- State mechanism, scope of applicability, and limitations.

---

## Branch C: Economics And Management Workflow

- Identify the core research question and what gap, puzzle, or debate it addresses.
- Explain the paper as `to answer question Q, the paper uses approach A and finds result R`.
- Extract:
  - the research question and why it matters
  - the conceptual or theoretical framework
  - the empirical approach: data, identification strategy (if causal), and main specification
  - the key findings: direction, magnitude, and robustness
  - how the paper positions itself against prior work
- For theoretical papers: focus on model logic, key assumptions, main propositions and their intuition, and testable implications.
- For empirical papers: focus on the identification strategy — what causal challenge exists, how it's addressed, and whether the identifying assumptions are plausible.
- Always distinguish correlation from causation, and statistical significance from economic significance.
- State limitations: internal validity, external validity, data constraints.

---

## Branch D: Financial Econometrics And Quantitative Finance Workflow

- Identify what financial quantity is being modeled, forecast, priced, or optimized, and why it matters.
- Explain the paper as `to model/forecast/price X, the paper proposes method M and evaluates it against benchmarks B using criteria C`.
- Extract:
  - the financial object (volatility, returns, factors, option prices, portfolio weights, risk measures)
  - the data: asset class, frequency, sample period — note whether crisis periods are covered
  - the proposed model or method and the key innovation
  - the benchmark models or methods used for comparison
  - the evaluation criteria, across the relevant dimensions:
    - **Statistical**: fit, forecast accuracy, diagnostic tests
    - **Risk**: VaR/ES backtesting, tail behavior, stress scenarios
    - **Economic**: portfolio performance, utility gains, trading profits net of costs
  - whether evaluation is genuinely out-of-sample
- Flag when:
  - in-sample results are emphasized over out-of-sample
  - transaction costs are absent or unrealistic
  - new factors lack multiple-testing correction
  - crisis periods are excluded from the sample
  - survivorship or look-ahead bias is unaddressed
- State limitations: model risk, parameter instability, data constraints, overfitting risk.

---

## Anti-Hallucination Rules

- Separate `paper claim`, `evidence`, `inference`, and `open question` when precision matters.
- Do not invent prior-work links, metrics, datasets, or novelty claims unsupported by the source.
- Treat summaries that erase the comparison points a researcher would use as hallucination.

### Economics / Management / Finance specific
- **Correlation ≠ causation**: do not imply causality unless the paper establishes it. Flag the distinction.
- **Identification credibility**: do not accept "we use IV" or "we use DiD" at face value — note whether the identifying assumptions are plausible.
- **In-sample vs out-of-sample**: in-sample fit is cheap; out-of-sample performance matters. Flag when papers conflate them.
- **Data snooping**: flag when parameters appear to have been tuned on the full sample.
- **Transaction costs**: a trading strategy with 2% gross alpha and 2.5% realistic costs is a net loser.
- **Factor overfitting**: a new factor significant at 5% among 300 tested is noise. Note whether multiple-testing corrections are used.
- **Crisis coverage**: a strategy or model tested only in calm periods is fragile. Note whether stress periods (2008, 2020) are included.
- **Survivorship / look-ahead bias**: note if delisted stocks, merged firms, or forward-looking data leakage are unaddressed.
- **Statistical vs economic significance**: a tiny effect with p < 0.01 may not matter. Note effect size, not just p-values.

---

## Output Template

Produce a compact note, selecting from these fields based on paper type:

- **One-sentence summary**
- **Paper card**: authors, year, venue, DOI/link
- **Paper type**: branch
- **Position in the literature**
- **Research question / introduction arc**
- **Method frame / empirical framework**
- **For Branch C**: identification strategy, data & sample, key causal estimates
- **For Branch D**: model specification, data (frequency, asset, period), competing models, evaluation
- **Core results / main estimates** — for Branch D, across statistical, risk, and economic dimensions where applicable
- **Main contributions**
- **Limitations and checks**
- **Policy / managerial / investment implications**
- **Sections worth close reading**
