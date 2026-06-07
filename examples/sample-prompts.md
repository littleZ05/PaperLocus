# Sample Prompts

These prompts are ordered from safest first-time trial to deeper paper reading.

## 1. First-Time Smoke Test

Use this after installing the skill. It verifies that `$paperlocus` is visible without a long PDF.

```text
/paperlocus Read the title-only paper: Attention Is All You Need.
Create a concise Chinese Markdown note. Mark the note as title-only
and separate paper claims, inference, and uncertainty.
```

## 2. Abstract-Only Triage

```text
/paperlocus Read this title and abstract.
Classify the paper type, explain the likely literature position,
and clearly mark what cannot be known without the full paper.
```

## 3. Local PDF Reading

```text
/paperlocus Read ./paper.pdf and produce a structured Chinese Markdown note.
First recover the title, abstract, section headings, introduction, method,
experiments, and conclusion. If any section is unavailable or extraction is
noisy, say so explicitly.
```

## 4. Long PDF Staged Reading

```text
/paperlocus Make an initial triage note for ./paper.pdf.
Extract the title, abstract, section headings, and conclusion first.
Then classify the paper type and list which sections should be read next.
```

## 5. Multi-Branch Classification

```text
/paperlocus Read this paper and classify it into one of four branches:
CS/arXiv method, Nature/Science evidence-chain, economics/management,
or financial econometrics/quantitative finance. Explain which signals
drive the decision.
```

## 6. Economics Paper — Focus on Identification

```text
/paperlocus Read this economics paper and explain:
- the research question and why it matters
- the identification strategy: what is the causal challenge and how is it addressed?
- the data and sample construction
- the main causal estimates and their economic significance
- whether the identifying assumptions are plausible
```

## 7. Financial Econometrics Paper — Focus on Model Evaluation

```text
/paperlocus Read this financial econometrics paper and explain:
- what financial quantity is being modeled or forecast
- the data: asset class, frequency, sample period (does it cover crises?)
- the proposed model, key innovation, and competing benchmarks
- evaluation across statistical, risk, and economic dimensions
- whether out-of-sample performance is genuinely out-of-sample
```

## 8. Quantitative Finance Paper — Focus on Practical Validity

```text
/paperlocus Read this quant finance paper and evaluate:
- the proposed method and what problem it solves
- the backtest design or empirical setup
- whether transaction costs, survivorship bias, and data snooping are addressed
- whether results are economically significant, not just statistically so
```

## 9. Reference-Aware Understanding

```text
/paperlocus Explain this paper in relation to the core prior works
criticized in the introduction and the main baselines.
Do not summarize the whole bibliography; focus on the papers
that shape the argument.
```

## 10. Literature-Graph Note

```text
/paperlocus Turn this paper into a reusable Markdown note for my
literature graph. Keep the note compact, reference-aware, and
suitable for later retrieval. Separate paper claims, evidence,
inference, and open questions.
```
