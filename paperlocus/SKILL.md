---
name: paperlocus
description: "Reference-aware whole-paper reading and structured research-note generation. Use when the user wants to understand an entire paper, place it in the literature, compare it against core prior work or baselines, or decide whether a paper should be read as a method paper or as a Nature or Science-style evidence-chain paper."
---

# PaperLocus

See the public README in the repository root for the project overview.

## Working Mode

- Treat this skill as a whole-paper reading and literature-positioning workflow.
- Produce the output in the user's preferred language. Default to Chinese if the user writes in Chinese.
- Build understanding from the paper itself first.
- Prefer a reusable Markdown note over a one-off loose summary.

## Context Construction Strategy

- Do not dump the whole paper into context unless the user explicitly wants deep reading of the full text.
- Prefer a layered context:
  1. the current paper's title, abstract, introduction claims, method frame, and core experiments
  2. a small set of core related papers, not the entire bibliography
  3. a reusable Markdown note that records the paper's positioning and insights
- Prioritize:
  1. papers explicitly discussed or criticized in the introduction
  2. strong baselines repeatedly used in experiments
  3. only the same narrow subfield the user is currently working on

## Input Acquisition

- Accept PDF, local file, arXiv link, DOI, webpage, screenshot, or title-only input.
- Prefer full text when available.
- If only a title or partial artifact is available, recover the minimum missing context before making strong claims.
- If some sections are missing or unreadable, say so explicitly and narrow the scope of the summary.

### Input-Specific Handling

- For PDF or local files:
  - extract title, abstract, section headers, introduction, method, experiments, and conclusion first
  - skip acknowledgments, checklists, and boilerplate unless they matter
- For arXiv links, DOI links, or webpages:
  - recover bibliographic metadata and the main paper text or abstract before summarizing
  - prefer the paper itself over third-party commentary
- For screenshots:
  - treat them as partial evidence only
  - do not pretend to understand the whole paper from a screenshot unless the screenshot truly covers the needed sections
- For title-only requests:
  - first recover abstract-level context and basic metadata
  - if the paper text is still unavailable, provide a scoped triage note rather than a confident full-paper overview

## First Decision: Classify The Paper Type

- Decide whether the paper follows a computer-science conference or arXiv narrative, or a Nature or Science-family narrative.
- If the type is unclear, state the uncertainty and default to the computer-science workflow unless the paper is clearly organized around scientific discovery and an evidence chain.
- Use the checklist below before committing to a branch.
- For concrete examples of the distinction, see [references/paper_type_examples.md](references/paper_type_examples.md).

### Paper Type Classification Checklist

- Prefer the computer-science conference or arXiv branch when most of the following are true:
  1. the abstract is centered on a new model, algorithm, framework, benchmark, or training recipe
  2. the paper structure looks like `introduction -> related work -> method -> experiments -> conclusion`
  3. the introduction spends substantial space critiquing prior methods and motivating a technical design
  4. the main evidence is comparison against baselines, ablations, scaling curves, and benchmark metrics
  5. the contribution is framed as "we propose" more than "we discover" or "we show"
- Prefer the Nature or Science-family branch when most of the following are true:
  1. the abstract is centered on a scientific finding, mechanism, or empirical claim about the world
  2. the paper structure is organized around findings and evidence rather than a standalone method section
  3. the introduction emphasizes a scientific question, gap in knowledge, or competing explanations
  4. the main evidence is an accumulated chain of experiments, observations, or measurements supporting a conclusion
  5. the contribution is framed as "we find", "we reveal", or "we show that X is true", with methods serving the finding
- Mixed cases:
  - If the paper appears in a science journal but still reads like a method paper, classify by narrative logic, not venue alone.
  - If the paper proposes a method for a scientific domain, ask whether the central output is a tool or a scientific conclusion.
  - When uncertain, say which signals conflict, then choose the branch that best matches how the results section is organized.

## Computer-Science Conference Or arXiv Workflow

- Explain the paper as `built on A, changed B, therefore obtained C` whenever the source supports that framing.
- Extract:
  - the core sub-direction
  - the key prior works the paper critiques
  - the proposed framework
  - the main claimed contributions
- For experiments, explain:
  - why each experiment exists
  - which claim it is meant to support
  - what metrics and baselines matter

## Nature Or Science-Family Workflow

- Identify the core scientific question.
- State what existing understanding the paper challenges, extends, or fills in.
- Separate the key finding from the method used to obtain it.
- Explain what each major experiment or dataset is meant to prove.
- Reconstruct the evidence chain that supports the central conclusion.
- State the mechanism-level explanation, scope of applicability, and limitations.

## Anti-Hallucination Rules

- Separate `paper claim`, `evidence`, `inference`, and `open question` when precision matters.
- Do not invent prior-work links, metrics, datasets, implementation details, or novelty claims that are not supported by the paper or a verified source.
- Treat hallucination broadly:
  - not only fabricated facts
  - also distorted positioning against the field
  - also summaries that erase the comparison points a researcher would naturally use to understand the work

## Output Template

Use a compact note with:

- one-sentence summary
- paper card
- paper type
- position in the literature
- introduction arc or scientific question
- method frame
- experiment design and core results
- main contributions
- limitations, counterexamples, and checks
- sections worth close reading
