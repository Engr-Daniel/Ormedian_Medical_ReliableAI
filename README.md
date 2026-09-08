# OR-MEDIAN Reliable AI Research Training

A mentorship curriculum and reproducible research-training environment for graduate trainees, research assistants, and early-stage researchers working toward reliable AI for medical imaging.

The program develops technical skills alongside evidence-driven research practice. Learn to explain decisions, investigate failures, reproduce work, critique evidence, and communicate limitations.

## Start here

Read the [Phase 0 guide](curriculum/phase-0-researcher-setup/README.md) for prerequisites, seven-day pacing, expected outputs, and readiness criteria.

**Current status:** Phase 0 — Researcher Setup, Week 1 of the 24-week program. This is a scaffold; unit lessons, labs, slide decks, and assessments are not written yet. Detailed Weeks 2–24 planning is deferred until Phase 0 is finished and Phase 1 planning begins.

## Environment defaults

Phase 0 uses Python 3.11 and its built-in `venv`, with VS Code as the documented editor. No third-party Python packages are required by this scaffold. `requirements.txt` and `requirements-dev.txt` intentionally contain comments only.

Jupyter will support notebook work and Marp Markdown will be the slide source format when those artifacts are introduced. Their setup belongs in the relevant learning activities; no notebook or slide toolchain is installed by this scaffold. A GPU and PyTorch are not required.

## Repository navigation

| Location | Purpose |
| --- | --- |
| [Phase 0 curriculum](curriculum/phase-0-researcher-setup/README.md) | Syllabus, deliverables, readiness criteria, and future unit navigation |
| [slides/phase-0/](slides/phase-0/) | Future Marp slide sources |
| [labs/phase-0/](labs/phase-0/) | Future guided executable activities |
| [assessments/phase-0/](assessments/phase-0/) | Future diagnostic, formative, and summative assessments |
| [research-notes/](research-notes/README.md) | Journals, reading notes, questions, and reasoning |
| [experiments/](experiments/README.md) | Experiment definitions and execution evidence |
| [results/](results/README.md) | Small derived tables and summaries |
| [figures/](figures/README.md) | Small figures with provenance |
| [Literature resources](resources/literature/README.md) | Shared bibliography and literature map |
| [src/](src/) | Future reusable Python code |
| [scripts/](scripts/) | Future executable utilities and entry points |
| [tests/](tests/) | Future tests for consequential reusable behavior |

Empty directories contain `.gitkeep` solely so they can be preserved in Git. Remove a placeholder when that directory gains its first real file.

Project rules are in [AGENTS.md](AGENTS.md); decisions and implementation history are in [memory.md](memory.md). The shared [PR-review skill](.agents/skills/ormedian-pr-review/SKILL.md) supports mentoring reviews of contributions.

## Data and outputs

Keep credentials, patient information, restricted datasets, and model weights out of Git. Research-paper PDFs must not be committed. Keep useful lightweight results, figures, and notes with enough context to understand and regenerate them. `.gitignore` excludes common local and large generated artifacts; it cannot determine sensitivity or file size, so inspect changes before committing.

License: TBD — pending ownership and release decision.
