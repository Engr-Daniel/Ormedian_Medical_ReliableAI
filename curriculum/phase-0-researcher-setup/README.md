# Phase 0 — Researcher Setup

[Return to the program](../../README.md)

## Objective

Establish a professional, reproducible research environment and learn to work like a computational researcher before studying PyTorch. By the end of Week 1, demonstrate a documented workflow that connects a question, practical work, evidence, interpretation, and the next investigation.

This guide defines the foundation week. Lessons, slide decks, executable labs, and assessment tasks are planned, not yet available. No P0-U01 lesson is included here.

## Prerequisites

- Access to a computer on which you can install or use Python 3.11, Git, and VS Code. Windows, macOS, or Linux is acceptable; record the operating system used. No GPU is needed.
- Internet access for software setup, GitHub collaboration, and locating literature. A GitHub account is needed by Day 3; creating it can be part of setup.
- Basic ability to navigate files, edit a text file, and follow instructions. Beginner familiarity with Python variables, functions, and running a short script is helpful; identify gaps during setup and review them with the mentor before executable tasks.
- Willingness to record uncertainty and explain decisions. Prior PyTorch, machine learning, medical imaging, or publication experience is not required.

Python, Git, and VS Code need not already be configured: establishing and checking that environment is part of the week. Learners with installation restrictions should agree on an accessible environment with the mentor and document any deviations.

## Learning units and proposed seven-day pacing

The day numbers describe the intended sequence within Week 1, not proof of competence. Use review time where evidence shows a gap; do not advance solely because a day has elapsed.

| Day | Unit | Learning outcome | Main deliverable |
| --- | --- | --- | --- |
| 1 | P0-U01 — Researcher Mindset & Scientific Workflow | Explain research as evidence-driven investigation | Research workflow note + reflection |
| 2 | P0-U02 — Research Computing Environment | Establish and explain a reproducible local Python/VS Code environment | Reproducible local environment |
| 3 | P0-U03 — Git & GitHub for Research | Demonstrate branch → commit → PR → review | Branch/commit/PR workflow exercise |
| 4 | P0-U04 — Reproducible Research Projects | Connect structure, seeds, configs, and dependencies to reproducibility | Project structure + reproducibility checklist |
| 5 | P0-U05 — Experiment Tracking & Research Journaling | Separate execution evidence from interpretation | Experiment template + research journal |
| 6 | P0-U06 — Literature & Paper Reading Workflow | Search, organize, read, critique, and cite | Paper-reading template + literature map |
| 7 | P0-U07 — Scientific Communication & Phase Assessment | Communicate evidence and demonstrate readiness | Mini presentation + Phase 0 assessment |

## Expected deliverables and evidence

These are completion expectations for the future activities, not instructions to produce every artifact while creating the scaffold. Use synthetic or non-sensitive examples; model training and medical datasets are unnecessary.

| Unit | Evidence to retain | Intended location |
| --- | --- | --- |
| P0-U01 | A workflow note connecting question, hypothesis, evidence, interpretation, and next action; reflection on assumptions | `research-notes/` |
| P0-U02 | Environment setup record: OS, Python version, creation/use of the virtual environment, interpreter verification, and a successful small script execution | `research-notes/` (keep `.venv/` local) |
| P0-U03 | Branch and commit references, a PR link, and evidence of responding to a review comment in an agreed practice workflow | `research-notes/` |
| P0-U04 | A navigable project structure, reproducibility checklist, and evidence that a small configured activity can be rerun; document the seed where randomness is used | Notes plus `experiments/` execution records |
| P0-U05 | An experiment-record template and one completed small activity record; a dated journal entry separating observation, interpretation, uncertainty, and next steps | `experiments/` and `research-notes/` |
| P0-U06 | Paper-reading template and one completed reading note, a verified bibliography entry, and a corresponding literature-map row | `research-notes/` and `resources/literature/` |
| P0-U07 | A short Marp presentation explaining the week's evidence and limitations; an assessment record with competency evidence and follow-up actions | `slides/phase-0/` and `assessments/phase-0/` |

Preserve at least one debugging account from the week: observed failure, plausible cause, diagnostic check, correction, and evidence that it worked. A setup or workflow failure is sufficient. Do not manufacture numerical results or claim experiments that were not run.

## Competency-based completion

The learner first checks their evidence, then reviews it with a mentor/reviewer. Documentation may be consulted during demonstrations: independent work means being able to explain and repeat the procedure without step-by-step prompting. For independent study, mark the outcome as a self-assessment until reviewed.

Assess each competency as **Demonstrated**, **Needs review**, or **Not yet demonstrated**, with artifact links and a short reason. Use the criteria below; a polished presentation cannot compensate for an environment that cannot be reproduced.

| Competency | Evidence of demonstration |
| --- | --- |
| Scientific workflow | Distinguish a question, hypothesis, observation, and interpretation; identify an uncertain assumption and useful next check |
| Computing environment | Run a small script with the intended Python interpreter; explain environment isolation and repeat setup from the recorded steps |
| Version control and collaboration | Explain and demonstrate branch, commit, PR, and response to feedback; inspect changes before sharing |
| Reproducibility | Rerun a small activity using recorded configuration and dependencies; explain seeds and any limits on repeatability |
| Tracking and troubleshooting | Locate execution evidence and corresponding journal reasoning; explain a diagnosed failure and its correction |
| Literature practice | Trace a reading note and map row to a verified source; distinguish a paper's claim, evidence, and limitation |
| Communication and responsible sharing | Explain the week's work with a concise slide artifact; identify missing evidence and keep sensitive or prohibited material out of shared files |

| Outcome | Decision rule | Next action |
| --- | --- | --- |
| **Ready** | All seven competencies are demonstrated with accessible evidence and reproducible practical work | Proceed to Phase 1 planning; carry forward research habits |
| **Ready with review** | Practical environment, version-control workflow, reproducibility, and responsible sharing are demonstrated; remaining gaps are limited to explanation, organization, or presentation and can be addressed in a focused review | Record the affected competencies, correction evidence, reviewer, and review date; progression is conditional on the mentor's agreement |
| **Repeat selected units** | A core practical competency is not yet demonstrated, evidence cannot be reproduced, sensitive material remains in deliverables, or other gaps require redoing an activity rather than clarification | Repeat only the affected units and reassess their evidence before progressing |

Keep the assessment record in `assessments/phase-0/`, using `P0-A01` for the phase assessment and linking P0-U01 through P0-U07 as applicable. Record date, assessor/self-assessment status, evidence, outcome, and next actions. The actual assessment tasks and detailed prompts will be authored later.

## Unit navigation

Replace **Planned** with relative links as artifacts are created. It means unavailable, not complete. **As needed** means a guided executable lab will be added only if the learning objective calls for one; a concept unit does not automatically require a notebook.

| Unit ID | Curriculum | Slides | Lab | Assessment |
| --- | --- | --- | --- | --- |
| P0-U01 | Planned | Planned | As needed | Planned |
| P0-U02 | Planned | Planned | Planned | Planned |
| P0-U03 | Planned | Planned | Planned | Planned |
| P0-U04 | Planned | Planned | Planned | Planned |
| P0-U05 | Planned | Planned | Planned | Planned |
| P0-U06 | Planned | Planned | As needed | Planned |
| P0-U07 | Planned | Planned | As needed | Planned (`P0-A01`) |

Use the same `P0-Uxx` prefix in related filenames. Curriculum files belong here; slide, lab, and assessment artifacts belong under their respective `phase-0/` directories. Assessment documents carry their own assessment IDs and related unit IDs. Retain the flat artifact-type organization defined in [AGENTS.md](../../AGENTS.md).
