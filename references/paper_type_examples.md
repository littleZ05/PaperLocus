# Paper Type Examples

Use these examples only when the paper type is unclear or when you want a concrete anchor for the classification logic.

## Branch A: Computer-Science Conference Or arXiv

### Example 1: Attention Is All You Need

- Source: arXiv, `Attention Is All You Need`, 2017
- URL: https://arxiv.org/abs/1706.03762
- Why it fits:
  - the abstract is centered on a new architecture, `Transformer`
  - the paper argues against prior sequence models and motivates a different technical design
  - the core evidence is benchmark performance, training efficiency, and transfer to another task

### Example 2: Segment Anything

- Source: arXiv, `Segment Anything`, 2023
- URL: https://arxiv.org/abs/2304.02643
- Why it fits:
  - the abstract centers on a model and a data engine, not a scientific discovery
  - the paper structure is strongly method-and-benchmark oriented

---

## Branch B: Nature Or Science-Family

### Example 1: Highly accurate protein structure prediction with AlphaFold

- Source: Nature, `Highly accurate protein structure prediction with AlphaFold`, 2021
- URL: https://www.nature.com/articles/s41586-021-03819-2
- Why it fits:
  - the paper contains strong method content, but the narrative is driven by what has now become possible or established

### Example 2: A kilonova as the electromagnetic counterpart to a gravitational-wave source

- Source: Nature, 2017
- URL: https://www.nature.com/articles/nature24303
- Why it fits:
  - the paper is organized around an astrophysical event and the evidence supporting its interpretation
  - the key question is not "what model do we propose" but "what happened and what evidence supports that conclusion"

---

## Branch C: Economics And Management

### Example C1: Minimum Wages and Employment

- Source: American Economic Review, Card & Krueger, 1994
- URL: https://www.jstor.org/stable/2118030
- Why it fits:
  - the abstract centers on a causal question: do minimum wages reduce employment?
  - uses a natural experiment (NJ vs PA minimum wage change) for identification
  - core evidence is a DiD estimate from survey data
  - conclusion framed as "we find that..." not "we propose a model that..."

### Example C2: The Colonial Origins of Comparative Development

- Source: American Economic Review, Acemoglu, Johnson & Robinson, 2001
- URL: https://www.jstor.org/stable/2677930
- Why it fits:
  - asks a causal question: do institutions cause growth?
  - identification strategy: IV (settler mortality as instrument for institutions)
  - structure: theory → historical evidence → data → IV estimation → robustness
  - central contribution is an empirical finding, not a methodological innovation

### Example C3: Automobile Prices in Market Equilibrium

- Source: Econometrica, Berry, Levinsohn & Pakes, 1995
- URL: https://www.jstor.org/stable/2171802
- Why it fits:
  - estimates a structural model of demand and supply
  - core: estimating deep parameters from equilibrium conditions
  - bridges theory (discrete choice, Nash pricing) with empirical estimation

### Example C4: Job Market Signaling

- Source: Quarterly Journal of Economics, Spence, 1973
- URL: https://www.jstor.org/stable/1882010
- Why it fits:
  - builds a theoretical model of signaling in labor markets
  - core output: equilibrium analysis (separating vs pooling)
  - generates testable implications
  - narrative is model-driven: setup → equilibrium → comparative statics → implications

---

## Branch D: Financial Econometrics And Quantitative Finance

### Example D1: Autoregressive Conditional Heteroscedasticity (ARCH)

- Source: Econometrica, Engle, 1982
- URL: https://www.jstor.org/stable/1912773
- Why it fits:
  - proposes a new time-series model for time-varying volatility
  - motivated by stylized facts: volatility clustering, fat tails
  - evaluation is statistical (fit, diagnostics), not a trading strategy
  - contribution framed as "we introduce a new class of stochastic processes"

### Example D2: Modeling and Forecasting Realized Volatility

- Source: Econometrica, Andersen, Bollerslev, Diebold & Labys, 2003
- URL: https://www.jstor.org/stable/1555185
- Why it fits:
  - models and forecasts volatility using intraday data
  - core: time-series framework for realized volatility measures
  - evaluation covers statistical fit, forecast accuracy, and economic value
  - stylized facts (long memory, log-normality) drive the modeling

### Example D3: Measuring Financial Asset Return and Volatility Spillovers

- Source: The Economic Journal, Diebold & Yilmaz, 2009
- URL: https://www.jstor.org/stable/40271225
- Why it fits:
  - uses VAR + variance decomposition to measure spillovers
  - object of study: return and volatility connectedness across markets
  - evaluation is statistical: spillover tables, directional indices, time variation
  - contribution is an empirical measurement framework, not a trading strategy

### Example D4: Common Risk Factors in the Returns on Stocks and Bonds

- Source: Journal of Financial Economics, Fama & French, 1993
- URL: https://www.sciencedirect.com/science/article/pii/0304405X93900235
- Why it fits:
  - proposes new factor portfolios (SMB, HML) for the cross-section of stock returns
  - core evidence: Fama-MacBeth regressions and factor spanning tests
  - contribution framed as identifying common risk factors
  - economic mechanism: risk compensation vs mispricing debate

### Example D5: CoVaR

- Source: American Economic Review, Adrian & Brunnermeier, 2016
- URL: https://www.jstor.org/stable/43861001
- Why it fits:
  - proposes a new systemic risk measure (CoVaR, ΔCoVaR)
  - core question: how much does each institution contribute to overall system risk?
  - estimation via quantile regression on financial returns
  - output is risk measurement and ranking, not a trading signal

### Example D6: Optimal Versus Naive Diversification

- Source: Review of Financial Studies, DeMiguel, Garlappi & Uppal, 2009
- URL: https://www.jstor.org/stable/40247619
- Why it fits:
  - compares portfolio optimization methods empirically
  - key finding: estimation error swamps optimization benefit — 1/N often wins
  - careful backtest design: rolling windows, transaction costs, multiple datasets
  - central concern is out-of-sample performance

### Example D7: Empirical Asset Pricing via Machine Learning

- Source: Review of Financial Studies, Gu, Kelly & Xiu, 2020
- URL: https://www.jstor.org/stable/48595039
- Why it fits:
  - uses ML (neural nets, trees) for cross-sectional return prediction
  - core evidence: out-of-sample R², portfolio sorts on ML predictions
  - comparison against traditional factor models and linear benchmarks
  - addresses data snooping with purged cross-validation
