# v0.1.0 - Initial public release

PaperLocus is a Codex skill for reading research papers through their position in the literature.

## Highlights

- Introduces `PaperLocus`, a Codex skill for whole-paper reading and literature positioning
- Distinguishes between method-led papers, science evidence-chain papers, and hybrid cases where venue and narrative logic conflict
- Produces reusable Markdown notes instead of one-off loose summaries
- Adds reference-aware reading centered on introduction-critical prior work, dominant experimental baselines, and narrow subfield context
- Adds a first-time smoke-test path: start with a title-only or abstract-only note at low reasoning effort before trying long PDFs

## Included

- narrative-aware classification of method papers vs science evidence-chain papers
- reference-aware reading centered on core prior works and baselines
- reusable Markdown note generation for long-running literature workflows
- sample prompts, sample outputs, first-time quick-start guidance, and real paper-type examples

## Best For

- `ccf-a / arXiv` method papers
- `Nature / Science / Nature-*` papers
- mixed cases where venue and narrative logic do not match cleanly

## Quick Trial

After installing the skill, run a small smoke test before deep PDF reading:

```text
Use $paperlocus to read the title-only paper request: Attention Is All You Need.
Do not browse. Create a concise Chinese reusable Markdown note.
Clearly mark the note as title-only and separate paper claims, inference, and uncertainty.
```
