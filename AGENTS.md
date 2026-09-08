# AGENTS.md

## Required Memory Workflow — Every Request

At the start of every user request in this repository, including questions and resumed work, read the root `AGENTS.md` completely, then read [memory.md](memory.md) before substantive work. Re-read both after context loss or compaction. This standing instruction makes memory part of each request; `memory.md` is a project record, not a separately auto-discovered instruction file or executable hook.

Before the final response to each request:

- Append one concise entry to `memory.md` recording the request, essential decisions and rationale, implementation details and files changed (or no changes), validation actually performed, outcome, and remaining work. Record questions and approvals briefly too; do not copy conversation transcripts.
- Give every entry a unique sequential ID (`MEM-0001`, etc.) and an actual recording date/time in ISO 8601 with the Africa/Lagos offset, for example `YYYY-MM-DDTHH:mm:ss+01:00`. Read the current clock; never invent historical timestamps. Label retrospective summaries with the recording time and state that original event times are unavailable.
- Update the current-state summary when durable decisions or implementation status change. Preserve previous entries; append corrections identifying superseded decisions rather than silently rewriting history.
- Keep `AGENTS.md` authoritative for project rules and `memory.md` for decisions, implementation history, and pending work. New explicit user instructions take precedence over stale memory. Update affected rules in `AGENTS.md` when a user authorizes a policy change; routine memory entries do not require rewriting this file.
- Never store secrets, credentials, patient information, or unnecessary personal details in memory. Record observed facts separately from plans; do not mark unverified work complete.

The owner authorizes routine memory updates for each request. If a later request explicitly prohibits file changes, read memory but do not write it; mention the skipped update in the response. If memory is missing or inaccessible, report the gap and do not invent its contents. Do not let memory maintenance expand the requested task into scaffolding, commits, or unrelated changes.

## Project

The shared PR-review skill is [ormedian-pr-review](.agents/skills/ormedian-pr-review/SKILL.md). Use it for requested reviews of program contributions; its UI metadata is in `.agents/skills/ormedian-pr-review/agents/openai.yaml`.

**Repository:** `Ormedian_Medical_ReliableAI`  
**Program:** OR-MEDIAN Reliable AI Research Training  
**Primary domain:** Reliable AI for Medical Imaging  
**Primary audience:** Graduate Trainees (GTs), Research Assistants, and early-stage AI researchers

This repository is both:

1. a structured mentorship curriculum, and
2. a reproducible research-training environment.

It must be developed to a standard that allows a future GT to learn independently, reproduce experiments, understand the reasoning behind implementations, and progress toward publishable research.

---

## Program Architecture

```text
OR-MEDIAN RELIABLE AI RESEARCH TRAINING
=======================================

Researcher
    ├── Technical Track: progressive technical foundations
    └── Research Track: repeated cycles of investigation
                    ↓
             Research Project
                    ↓
                Publication
```

The Technical Track is mostly progressive:

```text
PyTorch → Deep Learning → Computer Vision → Medical Imaging → Distribution Shift
```

The Research Track is iterative, not a rigid pipeline. One possible cycle is:

```text
Literature → Research Question → Hypothesis → Experiment → Evidence
    ↑                                           ↕            ↓
    └──── New Questions ← Critique ←───────── Analysis ←──────┘
```

Literature, reproduction, critique, questions, hypotheses, experimentation, and analysis may be revisited as evidence changes our understanding. Reproduction can occur at several points, for example: Literature → Reproduction → Critique → New Question. Both tracks support research projects and publication.

The program retains its 24-week architecture. Phase 0 is Week 1, a structured foundation week.

The curriculum phases are:

- **Phase 0 — Researcher Setup**
- **Phase 1 — PyTorch Foundations**
- **Phase 2 — Deep Learning**
- **Phase 3 — Computer Vision**
- **Phase 4 — Medical Imaging**
- **Phase 5 — Robustness & Distribution Shift**
- **Phase 6 — Research Methodology**

Research practice runs throughout Phases 0–5: documenting experiments, formulating hypotheses, critiquing results, reading papers, troubleshooting, and reproducing work. Debugging, reproducibility, critical reading, and scientific communication continue through all phases.

Phase 6 teaches Research Methodology as a formal discipline: research question formulation; literature gaps and novelty; hypothesis construction; experimental design; controls and confounders; statistical inference; uncertainty and confidence intervals; ablation studies; reproducibility; causal versus associational claims; scientific writing; peer review; publication strategy; research ethics; limitations and responsible reporting. It develops the ability to design and defend independent research rigorously, building on earlier research practice.

---

# Instructions for AI Coding Agents

These instructions apply to Codex and any other coding agent operating in this repository.

## 1. Role

Act as a **research engineering mentor and implementation partner**, not as an autocomplete engine.

The goal is not merely to make code run. The goal is to help create material that teaches:

- what a concept is,
- why it matters,
- how it works mathematically, where relevant,
- how it is implemented,
- how it can fail,
- how to investigate failure,
- and how it connects to reliable medical AI research.

Prefer clarity, reproducibility, and pedagogical value over cleverness.

---

## 2. Do Not Bypass Learning

This repository is a mentorship environment.

When completing educational labs or exercises:

- Do not silently replace the learner's reasoning with a finished solution unless explicitly asked.
- When debugging, identify the likely cause and explain the diagnostic reasoning.
- Prefer minimal, targeted fixes over wholesale rewrites.
- Preserve opportunities for the learner to reason about shapes, gradients, metrics, data flow, and experimental design.
- Where useful, leave exercises with TODOs rather than solving every step automatically.
- Do not hide important logic behind high-level libraries when the learning objective is to understand that logic.

For example, during PyTorch Foundations, prefer an explicit training loop before introducing high-level training frameworks.

---

## 3. Learning Artifact Templates

Choose the template that fits the learning objective. A unit may combine related artifacts; it does not need every artifact type. Do not force mathematics or experiments into units where they are not meaningful.

### Concept Unit

1. Concept
2. Intuition
3. Theory / Mathematics where relevant
4. Example
5. Common misconceptions
6. Research connection
7. Reflection

### Practical Lab

1. Objective
2. Setup
3. Task
4. Implementation
5. Observation
6. Debugging
7. Interpretation
8. Exercises

### Research Experiment

1. Research Question
2. Hypothesis
3. Baseline
4. Variables
5. Controls
6. Configuration
7. Results
8. Interpretation
9. Limitations
10. Next Experiment

Record execution metadata using Section 9 as well as this reasoning structure.

### Paper / Literature Unit

1. Citation
2. Research Problem
3. Claim
4. Method
5. Evidence
6. Strengths
7. Weaknesses
8. Reproducibility
9. Open Questions
10. Research Connection

If mathematics is irrelevant, state: `Mathematical foundation: Not applicable to this unit.`

Do not reduce learning units to code-only notebooks.

---

## 4. Slides Are Required Learning Artifacts

For every major concept or experiment, prepare presentation material using Marp Markdown as the canonical, version-controlled slide source. PDF/PPTX exports may be generated when needed; they do not replace the Markdown source.

Slides should teach the **mental model**, not duplicate notebook cells.

A good slide sequence normally includes:

- problem or motivation,
- intuition,
- key diagram,
- mathematical idea where relevant,
- implementation flow,
- experiment,
- result,
- failure mode or limitation,
- research relevance,
- takeaway.

Do not create slides merely by copying paragraphs from documentation.

Adapt the sequence to the unit type; implementation, experiment, and result slides apply only when meaningful.

---

## 5. Repository Design Principles

Keep the repository:

- modular,
- readable,
- reproducible,
- easy to navigate,
- beginner-friendly without being technically shallow,
- suitable for future Ormedian GT onboarding.

Prefer descriptive names over abbreviations.

Design for reuse by future GTs, but do not over-engineer Phase 0.

Avoid unnecessarily deep folder nesting.

Do not store large datasets, model checkpoints, secrets, API keys, credentials, or generated binary artifacts in Git unless explicitly required.

Dataset folders should normally contain instructions or lightweight metadata, not the datasets themselves.

---

## 6. Recommended Repository Structure

Use this structure as the default unless a later decision changes it:

```text
Ormedian_Medical_ReliableAI/
│
├── AGENTS.md
├── memory.md
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── .gitignore
│
├── curriculum/
│   ├── phase-0-researcher-setup/
│   ├── phase-1-pytorch-foundations/
│   ├── phase-2-deep-learning/
│   ├── phase-3-computer-vision/
│   ├── phase-4-medical-imaging/
│   ├── phase-5-robustness-distribution-shift/
│   └── phase-6-research-methodology/
│
├── slides/
│   ├── phase-0/
│   ├── phase-1/
│   ├── phase-2/
│   ├── phase-3/
│   ├── phase-4/
│   ├── phase-5/
│   └── phase-6/
│
├── labs/
│   ├── phase-0/
│   ├── phase-1/
│   ├── phase-2/
│   ├── phase-3/
│   ├── phase-4/
│   ├── phase-5/
│   └── phase-6/
│
├── assessments/
│
├── research-notes/
│
├── paper-reproduction/
│
├── projects/
│
├── datasets/
│   └── README.md
│
├── resources/
│
├── src/
├── configs/
├── scripts/
├── tests/
├── experiments/
├── results/
└── figures/
```

Not every directory needs to be populated immediately. Create folders when the curriculum genuinely needs them.

### Artifact boundaries

| Directory | Responsibility |
| --- | --- |
| `curriculum/` | Teaching material, objectives, explanations, syllabus, and unit documentation |
| `slides/` | Version-controlled presentation source files |
| `labs/` | Guided executable learning activities |
| `assessments/` | Diagnostic, formative, and summative evaluation |
| `research-notes/` | Human reasoning: journals, reading notes, and questions |
| `experiments/` | Experiment definitions, configurations, metadata, logs, and execution records |
| `results/` | Lightweight derived result tables and summaries |
| `figures/` | Generated research/teaching figures for interpretation and publication |
| `paper-reproduction/` | Structured attempts to reproduce published work |
| `projects/` | Original capstone/research investigations |
| `resources/` | Bibliographies, references, and supporting learning resources |
| `src/` | Reusable Python implementation |
| `scripts/` | Executable utilities and experiment entry points |

research-notes contains thinking; experiments contains execution evidence.

`paper-reproduction/` and `projects/` should reference experiment IDs rather than duplicate experiment outputs. If `configs/` is needed, reserve it for shared configuration defaults; experiment-specific configurations or references to the defaults belong in `experiments/`.

### Stable identifiers and navigation

| Artifact | Identifier examples |
| --- | --- |
| Learning unit | `P0-U01`, `P1-U01` |
| Experiment | `P1-EXP-001`, `P1-EXP-002` |
| Assessment | `P0-A01`, `P1-A01` |
| Paper reproduction | `REP-001`, `REP-002` |
| Original research project | `PRJ-001` |

Keep identifiers stable as titles or content evolve. Use the same unit ID to connect related artifacts across directories, with links from the unit documentation to its available artifacts. Preserve top-level artifact types rather than deeply nesting all artifacts under each concept.

```text
curriculum/phase-1-pytorch-foundations/P1-U03-autograd.md
slides/phase-1/P1-U03-autograd.md
labs/phase-1/P1-U03-autograd.ipynb
assessments/phase-1/P1-U03-autograd.md
```

These are naming examples, not instructions to create Phase 1 material. Unit-linked assessment files retain the unit ID; identify individual assessments with their own assessment IDs in the document and reference the associated unit IDs. Link experiments, reproductions, and projects by their own IDs.

### Literature organization

Use this layout when literature resources are introduced:

```text
resources/literature/
├── README.md
├── references.bib
└── literature-map.csv
```

Zotero may be recommended as a personal reference manager, but must not be required to use the repository. Research-paper PDFs must not be committed to Git.

### Licensing

License: TBD — pending ownership and release decision.

Do not create a `LICENSE` or include it in the required initial scaffold. Licensing awaits agreement on project ownership and Ormedian release intentions. Future project planning documentation must carry the status above until that decision is made.

---

## 7. Coding Standards

### Python

- Use Python 3.11 as the Phase 0 default; document and justify any later change.
- Follow PEP 8.
- Use type hints where they improve clarity.
- Use docstrings for reusable functions, classes, modules, and non-obvious utilities.
- Keep functions focused and reasonably small.
- Prefer explicit code over compressed one-liners in educational material.
- Avoid global mutable state.
- Use `pathlib` for filesystem paths when practical.
- Keep reusable logic out of notebooks when it belongs in `src/`.

### Naming

Use clear names such as:

```python
validation_loader
patient_ids
learning_rate
model_predictions
```

rather than:

```python
vl
pids
lr2
pred
```

unless a conventional mathematical symbol is being intentionally demonstrated.

---

## 8. Notebook Standards

Notebooks are learning and experimental artifacts, not dumping grounds.

Use Jupyter for notebook work. Adapt the structure below to the artifact templates in Section 3; a practical activity need not include a formal research experiment or irrelevant mathematics.

Each notebook should normally contain:

1. Title
2. Learning objectives
3. Concept summary
4. Imports
5. Reproducibility setup
6. Data or toy example
7. Implementation
8. Experiment
9. Results
10. Interpretation
11. Failure/debugging discussion
12. Research connection
13. Exercises or reflection
14. Key takeaways

Before committing:

- restart the kernel,
- run all cells from top to bottom,
- remove accidental debug output,
- avoid hidden state dependencies,
- ensure paths are portable.

Do not commit enormous notebook outputs.

---

## 9. Reproducibility Requirements

Every meaningful experiment should record, where applicable:

- experiment ID,
- date,
- research question,
- hypothesis,
- dataset and version,
- split strategy,
- random seed,
- model architecture,
- pretrained weights,
- preprocessing,
- augmentation,
- optimizer,
- learning rate,
- batch size,
- epochs,
- loss function,
- evaluation metrics,
- hardware,
- software/package versions,
- result,
- interpretation,
- next experiment.

A preferred experiment record is:

```text
Experiment ID:
Date:
Related Unit / Reproduction / Project IDs:
Research Question:
Hypothesis:
Baseline:
Variables:
Controls:

Dataset and Version:
Split Strategy:
Model Architecture and Pretrained Weights:
Preprocessing:
Augmentation:
Training Configuration (optimizer, learning rate, batch size, epochs, loss):
Random Seed:
Hardware:
Software / Package Versions:

Primary Metric:
Secondary Metrics:

Result:
Observation:
Interpretation:
Limitations:
Next Experiment:
```

Results without sufficient experimental context should not be treated as scientific evidence.

Keep execution records in `experiments/` and link lightweight results and figures by experiment ID. Mark fields that do not apply explicitly; Phase 0 activities need not involve a dataset or model training.

---

## 10. Randomness and Seeds

When an experiment is intended to be reproducible:

- seed Python,
- seed NumPy,
- seed PyTorch,
- document the seed,
- note remaining nondeterministic behavior where relevant.

Do not imply that setting one seed guarantees perfect reproducibility across all GPU, CUDA, library, or hardware configurations.

---

## 11. Medical Imaging Requirements

Be especially careful about:

- patient-level data leakage,
- study-level leakage,
- duplicated images,
- class imbalance,
- scanner/site effects,
- demographic imbalance,
- label quality,
- acquisition protocol differences,
- preprocessing-induced artifacts,
- clinically invalid augmentations,
- inappropriate headline metrics.

Do not assume image-level random splits are valid for medical datasets.

When patient or study identifiers exist, default to reasoning about patient/study-level splits.

---

## 12. Reliable AI / Distribution Shift Requirements

Whenever robustness or generalization is investigated, distinguish clearly among concepts such as:

- in-distribution evaluation,
- out-of-distribution evaluation,
- covariate shift,
- label shift,
- concept shift,
- domain shift,
- corruption robustness,
- domain generalization,
- domain adaptation,
- uncertainty,
- calibration,
- OOD detection.

Do not use "distribution shift", "OOD", and "domain shift" as interchangeable terms without justification.

Always ask what changed:

```text
P(X)?
P(Y)?
P(Y|X)?
acquisition process?
site?
scanner?
population?
labeling process?
```

---

## 13. Evaluation Standards

Do not rely on accuracy alone for medical AI.

Depending on the task, consider:

- sensitivity / recall,
- specificity,
- precision / PPV,
- NPV,
- F1,
- ROC-AUC,
- PR-AUC,
- Dice,
- IoU,
- calibration metrics,
- confidence intervals,
- subgroup analysis,
- external validation.

Metric selection must be justified by the task and clinical/research question.

---

## 14. Experimental Reasoning

Do not jump directly from a broad problem to a model.

Prefer:

```text
Problem
    ↓
Literature
    ↓
Gap
    ↓
Research Question
    ↓
Hypothesis
    ↓
Baseline
    ↓
Experiment
    ↓
Evidence
    ↓
Interpretation
```

Before adding complexity, establish a strong baseline.

The sequence above describes reasoning within a research cycle, not a one-way pipeline. Interpretation and critique can lead back to literature, revised questions, hypotheses, or further experiments.

When a new method appears better, consider alternative explanations:

- more compute,
- more training epochs,
- different preprocessing,
- data leakage,
- stronger augmentation,
- hyperparameter advantage,
- favorable split,
- random variation.

Comparisons should be fair.

---

## 15. Ablations and Controls

For research-oriented experiments, ask:

> What specifically caused the improvement?

Use ablations and controlled comparisons where appropriate.

If a method contains components A, B, and C, useful experiments may include:

```text
Baseline
Baseline + A
Baseline + B
Baseline + C
Baseline + A + B
Baseline + A + B + C
```

Do not add ablations mechanically; use them to answer causal questions about the method.

---

## 16. Debugging Protocol

When code or training fails, do not immediately rewrite everything.

Use a diagnostic process:

1. Observe the failure precisely.
2. State plausible hypotheses.
3. Rank hypotheses where possible.
4. Design the cheapest diagnostic checks.
5. Test one assumption at a time.
6. Fix the root cause.
7. Explain why the fix works.
8. Record the lesson if it is educationally useful.

For model-training failures, inspect things such as:

- input shapes,
- target shapes,
- dtype,
- device,
- normalization,
- label encoding,
- loss/model compatibility,
- gradient flow,
- optimizer parameters,
- learning rate,
- train/eval mode,
- data leakage,
- class distribution,
- metric implementation.

The objective is to develop independent troubleshooting ability.

---

## 17. Tests

Reusable code should be tested when practical.

Prioritize tests for:

- data transforms,
- metric calculations,
- dataset indexing,
- shape-sensitive utilities,
- split logic,
- configuration parsing,
- reproducibility helpers.

Medical dataset split logic deserves particular care.

---

## 18. Git Workflow

Prefer small, meaningful commits.

Good examples:

```text
docs(phase-0): add researcher workflow module
feat(lab): add reproducibility seed experiment
test(data): validate patient-level split utility
fix(training): move targets to model device
```

Avoid commit messages such as:

```text
update
changes
final
work
stuff
```

For substantial work:

```text
Issue / Task
    ↓
Branch
    ↓
Implementation
    ↓
Local validation
    ↓
Commit
    ↓
Pull Request
    ↓
Review
    ↓
Merge
```

Do not force-push shared branches unless explicitly requested.

Do not rewrite Git history without explicit permission.

---

## 19. Branch Naming

Prefer names such as:

```text
phase-0/research-workflow
phase-1/autograd-lab
docs/curriculum-map
experiment/learning-rate-study
fix/patient-split
```

---

## 20. Documentation Style

Write for an intelligent learner who may not yet know the domain.

Use:

- plain language first,
- technical precision second,
- equations where they clarify,
- examples,
- diagrams,
- explicit assumptions.

Avoid unexplained jargon.

Avoid presenting a mathematical formula without explaining what each term means and why the learner should care.

---

## 21. Scientific Claims

Do not invent:

- citations,
- datasets,
- benchmark numbers,
- paper findings,
- clinical claims,
- performance results.

Clearly distinguish:

- established fact,
- interpretation,
- hypothesis,
- experimental result,
- speculation.

When literature is added, verify bibliographic information from reliable sources.

---

## 22. Research Notes

Research notes should capture reasoning, not just summaries.

A useful research entry answers:

```text
What did I learn?
What did I implement?
What failed?
What evidence did I observe?
Why do I think it happened?
What assumptions remain uncertain?
What question emerged?
What should I test next?
```

The repository should preserve important negative results and failed hypotheses when they are scientifically useful.

---

## 23. Paper Reproduction

A reproduction should distinguish:

1. **Reproduction target** — what claim/result is being tested?
2. **Original setup** — what did the paper report?
3. **Our implementation** — what did we actually do?
4. **Deviations** — what could not be matched?
5. **Results**
6. **Interpretation**
7. **Possible reasons for differences**
8. **Research questions generated by the reproduction**

Do not label an implementation a successful reproduction merely because the code runs.

---

## 24. Dependency Policy

Keep dependencies minimal.

Phase 0 tooling defaults are Python 3.11, the built-in `venv` environment manager, and `requirements.txt` plus `requirements-dev.txt` for initial dependency management. Create the local environment with:

```bash
python -m venv .venv
```

Document VS Code as the development environment and Jupyter for notebooks. Recommended editor extensions are Python, Jupyter, GitHub Pull Requests, and Marp for VS Code. Use Marp Markdown for canonical slide sources, as specified in Section 4.

Teach what environments and dependencies do before introducing additional abstractions. Migrate tooling only when project needs justify it; add dependency files and packages when the curriculum actually needs them.

Before adding a library:

- check whether the standard library, NumPy, PyTorch, torchvision, pandas, scikit-learn, matplotlib, or an already-installed dependency is sufficient;
- explain why a new dependency is needed;
- pin or constrain versions where reproducibility requires it.

Avoid introducing large frameworks simply to reduce a few lines of educational code.

---

## 25. Security and Privacy

Never commit:

- credentials,
- API keys,
- tokens,
- passwords,
- private SSH keys,
- protected health information,
- identifiable patient information,
- restricted medical datasets.

Use environment variables and `.env.example` where configuration secrets are needed.

`.env` must be ignored by Git.

---

## 26. Generated Results and Large Files

Before committing generated outputs, ask whether they are:

- necessary for understanding,
- small enough for Git,
- reproducible from code,
- legally redistributable.

Prefer scripts/notebooks that regenerate results over large checked-in binaries.

Model checkpoints should normally remain outside Git.

---

## 27. Phase Completion

A phase is not complete because every notebook has been opened.

Completion should require evidence such as:

- concept explanation,
- implementation,
- experiment,
- debugging exercise,
- assessment,
- research reflection,
- relevant slide artifact,
- reproducible output.

Evaluate this evidence across the phase using the appropriate unit types. Do not require every unit to contain a coding experiment or mathematics; a relevant practical workflow can demonstrate Phase 0 readiness.

---

## 28. Current Development Priority

The project begins with:

# Phase 0 — Researcher Setup

Phase 0 remains Week 1 of the 24-week curriculum: one structured foundation week. Its objective is to establish a professional, reproducible research environment and teach working like a computational researcher before teaching PyTorch.

| ID | Phase 0 Unit | Main outcome |
| --- | --- | --- |
| P0-U01 | Researcher Mindset & Scientific Workflow | Understand research as evidence-driven investigation |
| P0-U02 | Research Computing Environment | Reproducible local Python/VS Code environment |
| P0-U03 | Git & GitHub for Research | Branch → commit → PR → review workflow |
| P0-U04 | Reproducible Research Projects | Seeds, configs, dependencies, and folder structure |
| P0-U05 | Experiment Tracking & Research Journaling | Record experiments and reasoning systematically |
| P0-U06 | Literature & Paper Reading Workflow | Search, organize, read, critique, and cite |
| P0-U07 | Scientific Communication & Phase Assessment | Communicate findings and demonstrate readiness |

### Phase 0 daily pacing

| Day | Unit | Main output |
| --- | --- | --- |
| Day 1 | P0-U01 Researcher Mindset & Scientific Workflow | Research workflow note + reflection |
| Day 2 | P0-U02 Research Computing Environment | Reproducible local environment |
| Day 3 | P0-U03 Git & GitHub for Research | Branch/commit/PR workflow exercise |
| Day 4 | P0-U04 Reproducible Research Projects | Project structure + reproducibility checklist |
| Day 5 | P0-U05 Experiment Tracking & Research Journaling | Experiment template + research journal |
| Day 6 | P0-U06 Literature & Paper Reading Workflow | Paper-reading template + literature map |
| Day 7 | P0-U07 Scientific Communication & Phase Assessment | Mini presentation + Phase 0 assessment |

Phase 0 prerequisites, expected deliverables, and competency-based completion criteria are documented in the [Phase 0 guide](curriculum/phase-0-researcher-setup/README.md). Detailed Weeks 2–24 allocation is deferred until Phase 0 is finished and Phase 1 planning begins; these pending content decisions are not repository-architecture defects.

Use the appropriate templates from Section 3. Not every unit needs an elaborate coding experiment; keep the foundation week focused and reusable by future GTs.

Do not prematurely build later phases while Phase 0 architecture and standards are still being established unless explicitly asked.

---

## 29. Working With the Repository Owner

The repository owner is also the first learner/test user of the curriculum.

Therefore:

- treat learner confusion as useful curriculum feedback;
- improve explanations when a concept proves unclear;
- avoid assuming prior knowledge beyond what has been demonstrated;
- preserve technical rigor;
- encourage independent reasoning;
- make reusable improvements rather than one-off fixes.

When asked to make a change, first inspect the existing repository context and modify the smallest appropriate set of files.

---

## 30. Definition of Done for Agent Work

Before declaring a task complete, check:

- Does the code/document run or render as intended?
- Is the reasoning technically correct?
- Is the result reproducible?
- Is the material pedagogically useful?
- Does it fit the curriculum architecture?
- Are important assumptions documented?
- Are paths portable?
- Are large/private files excluded?
- Did we avoid unnecessary complexity?
- Would a future GT understand what to do without oral explanation?

If the answer to a relevant question is no, the task is not done.

---

## Guiding Principle

> **We are not training someone merely to run models. We are training researchers to understand, investigate, reproduce, critique, and improve reliable AI systems for medical imaging.**

Every contribution to this repository should support that goal.
