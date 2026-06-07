# v0.2.0 — Four-branch classification with economics and finance support

PaperLocus expands from two branches to four, adding dedicated workflows for economics/management papers and financial econometrics/quantitative finance papers.

## What's New

- **Two new branches**: Branch C (Economics & Management) and Branch D (Financial Econometrics & Quantitative Finance), each with its own classification checklist and unified reading workflow
- **Branch C** covers: theoretical models, reduced-form empirical papers (IV, DiD, RDD, RCT), structural estimation, case studies, and meta-analyses
- **Branch D** covers: financial econometrics (GARCH, SV, VAR, Copula, high-frequency volatility), asset pricing (factor models, Fama-MacBeth), portfolio optimization, derivatives pricing, risk management, market microstructure, and trading strategies
- **Expanded anti-hallucination rules**: domain-specific guardrails for correlation vs causation, identification credibility, in-sample vs out-of-sample, data snooping, transaction costs, factor overfitting, crisis coverage, and survivorship bias
- **Updated reference examples**: 15 paper-type examples across all four branches

## Changed

- Classification section now dispatches into four branches instead of two
- Output template extended with optional econ/finance fields
- All documentation updated to reflect the four-branch structure

## Included From v0.1.0

- narrative-aware classification of method papers vs science evidence-chain papers
- reference-aware reading centered on core prior works and baselines
- reusable Markdown note generation for long-running literature workflows
- sample prompts, sample outputs, and quick-start guidance

## Best For

- `ccf-a / arXiv` method papers
- `Nature / Science / Nature-*` papers
- economics and management papers (theory, reduced-form, structural)
- financial econometrics and quantitative finance papers
- mixed cases where venue and narrative logic do not match cleanly

## Quick Trial

After installing the skill, test with a title-only request:

```text
/paperlocus Read the title-only paper: Attention Is All You Need.
Create a concise Chinese Markdown note.
Separate paper claims, inference, and uncertainty.
```

For an econ paper test:

```text
/paperlocus Read the title and abstract of Card & Krueger (1994)
"Minimum Wages and Employment". Classify the paper type and identify
the likely identification strategy.
```
