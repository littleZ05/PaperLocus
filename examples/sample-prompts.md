# Sample Prompts

These prompts are ordered from safest first-time trial to deeper paper reading.

## 1. First-Time Smoke Test

Use this after installing the skill. It verifies that `$paperlocus` is visible
without asking Codex to parse a long PDF.

```text
Use $paperlocus to read the title-only paper request: Attention Is All You Need.
Do not browse. Create a concise Chinese reusable Markdown note.
Clearly mark the note as title-only and separate paper claims, inference, and uncertainty.
```

CLI version:

```bash
codex exec -c 'model_reasoning_effort="low"' --skip-git-repo-check 'Use $paperlocus to read the title-only paper request: Attention Is All You Need. Do not browse. Create a concise Chinese reusable Markdown note as trial-note.md. Clearly mark the note as title-only and separate paper claims, inference, and uncertainty.'
```

On Windows, use `codex.cmd` with the same arguments.

## 2. Abstract-Only Triage

```text
Use $paperlocus to read this title and abstract.
Classify the paper type, explain the likely literature position, and clearly mark what cannot be known without the full paper.
```

## 3. Local PDF Reading

```text
Use $paperlocus to read ./paper.pdf and produce a structured Chinese Markdown note.
First recover the title, abstract, section headings, introduction, method, experiments, and conclusion.
If any section is unavailable or extraction is noisy, say so explicitly before making strong claims.
```

## 4. Long PDF Staged Reading

```text
Use $paperlocus to make an initial triage note for ./paper.pdf.
Extract the title, abstract, section headings, and conclusion first.
Then classify the paper type and list which sections should be read next.
```

## 5. Method Paper vs Evidence-Chain Paper

```text
Use $paperlocus to decide whether this Nature paper should be read as a method paper or as a scientific evidence-chain paper.
Explain which narrative signals drive the decision.
```

## 6. Reference-Aware Understanding

```text
Use $paperlocus to explain this paper in relation to the core prior works criticized in the introduction and the main baselines used in the experiments.
Do not summarize the whole bibliography; focus on the papers that shape the argument.
```

## 7. Literature-Graph Note

```text
Use $paperlocus to turn this paper into a reusable Markdown note for my literature graph.
Keep the note compact, reference-aware, and suitable for later retrieval.
Separate paper claims, evidence, inference, and open questions.
```
