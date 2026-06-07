# PaperLocus

`PaperLocus` is a Codex skill for reading research papers the way researchers actually use them:

- not just summarizing a paper in isolation
- but locating it in the literature
- comparing it against the core prior works and baselines
- and turning the result into reusable Markdown notes

It is designed for users who switch between:

- `ccf-a / arXiv` method papers
- `Nature / Science / Nature-*` papers
- hybrid papers that look like method papers even when they are published in science venues

## Why PaperLocus

Most paper-reading tools stop at surface summarization:

- "what is the paper about"
- "what method does it use"
- "what are the results"

That is useful, but it often misses the part that matters most for actual research work:

- what research path this paper belongs to
- which prior work it inherits from
- what exactly it changes
- which baseline or reference paper it is really arguing with
- whether it should be read as a method paper or as a scientific evidence-chain paper

`PaperLocus` is built to answer those questions directly.

## Core Selling Points

### 1. Narrative-aware paper classification

PaperLocus does not classify papers by venue alone.

It distinguishes between:

- `computer-science / arXiv / ccf-a style` papers
- `Nature / Science evidence-chain style` papers
- mixed cases where the venue is scientific but the narrative is still method-led

That means papers like `scGPT` or `Geneformer` can still be read as method papers when that is the right interpretation.

### 2. Reference-aware understanding

PaperLocus is designed to read a paper with the comparison frame a human researcher would naturally bring:

- the core prior works criticized in the introduction
- the dominant baselines in the result tables
- the narrow subfield the user is actually working in

Instead of flattening everything into a generic summary, it asks:

- built on what
- changed what
- therefore obtained what

### 3. Reusable Markdown notes

The output is designed to become a durable research note, not a one-off chat response.

It works especially well for workflows where you want:

- an Obsidian-style literature graph
- note nodes that can later be indexed by RAG
- compact but high-signal reading notes for group meetings and paper discussions

### 4. Better hallucination control for research reading

PaperLocus treats hallucination broadly.

It tries to prevent:

- fabricated facts
- incorrect benchmark or dataset details
- distorted positioning against the field
- summaries that erase the comparison points needed for real understanding

## How It Thinks

```mermaid
flowchart TD
    A[Input Paper] --> B[Recover Core Content]
    B --> C[Classify Narrative Type]
    C --> D1[Method Paper Branch]
    C --> D2[Science Evidence-Chain Branch]
    D1 --> E[Extract Core Prior Works]
    D1 --> F[Extract Baselines and Main Claims]
    D2 --> G[Extract Scientific Question]
    D2 --> H[Reconstruct Evidence Chain]
    E --> I[Reusable Markdown Note]
    F --> I
    G --> I
    H --> I
```

## What Makes It Different

```mermaid
flowchart LR
    A[Raw PDF or Link] --> B[Surface Summary Tool]
    A --> C[PaperLocus]
    B --> D[Single-paper recap]
    C --> E[Paper position in the literature]
    C --> F[Reference-aware understanding]
    C --> G[Reusable Markdown note]
```

## Supported Inputs

PaperLocus is designed to work with:

- PDF
- local files
- arXiv links
- DOI links
- webpages
- screenshots
- title-only requests

It does not treat these inputs equally.

The workflow changes depending on input type:

- `PDF / local file`
  - extract title, abstract, section headers, introduction, method, experiments, conclusion
  - skip acknowledgments, checklists, and boilerplate by default
- `arXiv / DOI / webpage`
  - recover metadata and paper text or abstract first
  - prefer the paper itself over third-party commentary
- `screenshot`
  - treat as partial evidence only
  - do not pretend to understand the whole paper from a fragment
- `title only`
  - recover abstract-level context first
  - downgrade to a triage note if the paper cannot be recovered

## Classification Logic

PaperLocus uses narrative logic instead of venue heuristics.

### Method-paper signals

- the abstract is about a new model, algorithm, benchmark, or training recipe
- the structure looks like `introduction -> related work -> method -> experiments`
- the main evidence is benchmark comparison, ablation, or scaling
- the contribution is framed as `we propose`

### Science evidence-chain signals

- the abstract is about a scientific finding, mechanism, or claim about the world
- the structure is driven by findings and supporting evidence
- the paper is organized around a scientific question or competing explanations
- the contribution is framed as `we find`, `we reveal`, or `we show that`

### Mixed-case rule

If the venue suggests one branch but the narrative suggests another, PaperLocus follows the narrative and explicitly notes the conflict.

## Validation Examples

The current version has been manually stress-tested on:

### Science-venue but method-led papers

- `scBERT`
- `scGPT`
- `Transfer learning enables predictions in network biology`
- `scLong`

Expected behavior:

- classify them as method-led papers
- not as classical evidence-chain science papers

### Classical evidence-chain papers

- `A kilonova as the electromagnetic counterpart to a gravitational-wave source`
- `A formal test of the theory of universal common ancestry`

Expected behavior:

- classify them into the `Nature / Science` evidence-chain branch

### Local arXiv and embodied-AI papers

- `Scalable Diffusion Models with Transformers`
- `Unified World Models`
- `Motus`
- `LDA-1B`
- `DINOv3`

Expected behavior:

- classify them as method papers
- emphasize prior-work positioning and baseline structure

## Repository Layout

```text
paperlocus/
  README.md
  examples/
    sample-prompts.md
    sample-output.md
  paperlocus/
    SKILL.md
    agents/
      openai.yaml
    references/
      paper_type_examples.md
```

## Naming

The project name `PaperLocus` emphasizes the core idea that this skill is not only about reading a paper, but about locating it in the literature:

- what line of work it belongs to
- what prior papers it builds on
- what it changes
- and where it sits in the research landscape

## Installation

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -r paperlocus ~/.codex/skills/
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force $HOME\.codex\skills | Out-Null
Copy-Item -Recurse .\paperlocus $HOME\.codex\skills\
```

## Optional Runtime Dependencies

The skill itself is Markdown-only, but it works best with these optional capabilities:

- PDF reading support
  - `pypdf`
  - `pdfplumber`
- a PDF-focused helper skill for page-level inspection
- web access for DOI, arXiv, and webpage recovery

## Example Prompts

```text
Use $paperlocus to read this PDF and produce a structured Chinese reading note.
```

```text
Use $paperlocus to decide whether this Nature paper should be treated as a method paper or as an evidence-chain paper.
```

```text
Use $paperlocus to explain this paper in relation to the core prior works criticized in the introduction.
```

More prompt examples are available in [examples/sample-prompts.md](examples/sample-prompts.md).

## Output Style

The default output is a compact whole-paper note with sections such as:

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

A compact sample output is available in [examples/sample-output.md](examples/sample-output.md).

## Best Use Cases

PaperLocus is especially useful for:

- weekly paper reading
- group meeting preparation
- structured literature reviews
- building a long-running Markdown note base
- comparing a new paper against the field rather than reading it in isolation

## Design Philosophy

PaperLocus is optimized for:

- high-quality context, not maximum context
- literature positioning, not just summarization
- reusable notes, not ephemeral chat output
- faithful interpretation, not overconfident compression

## Status

This is an actively iterated research-reading skill. The current emphasis is on:

- better hybrid paper classification
- cleaner reference-aware notes
- stronger support for literature-graph workflows
