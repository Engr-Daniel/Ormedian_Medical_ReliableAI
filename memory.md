# Project Memory

This file preserves essential decisions and implementation history for the OR-MEDIAN Reliable AI Research Training Program. Read it with [AGENTS.md](AGENTS.md), which defines the mandatory workflow and project rules. Memory is context, not permission to start pending work.

## Current state

- Purpose: a reusable mentorship curriculum and reproducible research-training environment for graduate trainees, research assistants, and early-stage medical imaging AI researchers. The owner is the first learner/test user.
- Scope: Phase 0 — Researcher Setup only, Week 1 of a 24-week program. Design for future GTs without over-engineering. The minimum Phase 0 scaffold is now created locally; lessons remain unwritten.
- Architecture: a progressive technical track and an iterative research track converge in research projects. Research practice runs through Phases 0–5; Phase 6 formally develops rigorous independent research design and defense.
- Learning artifacts: Concept Unit, Practical Lab, Research Experiment, and Paper/Literature Unit templates. Mathematics and formal experiments apply where meaningful. Major concepts and experiments require slide material.
- Identifiers: units `P0-U01`; experiments `P1-EXP-001`; assessments `P0-A01`; reproductions `REP-001`; original projects `PRJ-001`. Unit IDs connect curriculum, slides, labs, and assessment files; assessments also carry their own IDs within documents.
- Artifact boundaries: `research-notes/` contains thinking; `experiments/` contains execution evidence. Reproductions and projects reference experiment IDs rather than duplicate outputs. `configs/`, if needed, holds shared defaults; experiment-specific configuration belongs in `experiments/`. Full directory responsibilities are in AGENTS.md Section 6.
- Tooling defaults: Python 3.11, built-in `venv`, `requirements.txt`, `requirements-dev.txt`, VS Code, Jupyter, and canonical Marp Markdown slides. These are decisions, not installed or configured infrastructure.
- Literature: `resources/literature/` contains guidance, a comments-only `references.bib`, and a headers-only `literature-map.csv`. No papers have been added. Zotero is optional. Research-paper PDFs must not be committed.
- Licensing: TBD pending ownership and Ormedian release decisions. Do not create `LICENSE` yet.
- Standards: preserve learner reasoning, make targeted fixes, verify claims, record reproducibility metadata, validate relevant work, and exclude secrets, restricted data, patient information, and unnecessary large artifacts.
- Implementation: initial guidance, memory, and skill were published to origin/main (`f7a388f`, followed by memory update `c63b0d6`). The Phase 0 scaffold is now local and uncommitted. It contains a root overview, ignore rules, comments-only requirements files, a Phase 0 guide, artifact-directory guidance, literature tracking files, and six `.gitkeep` placeholders. No lesson, executable lab, installed environment, slide deck, or assessment task has been implemented.
- Phase 0 readiness: prerequisites and evidence-based Ready / Ready with review / Repeat selected units decisions are in [the phase guide](curriculum/phase-0-researcher-setup/README.md). No numerical scoring or fixed study hours were introduced. Practical reproduction and responsible sharing are required for progression; missing explanations may receive targeted review.
- PR review skill: the authoritative shared copy is now [.agents/skills/ormedian-pr-review/SKILL.md](.agents/skills/ormedian-pr-review/SKILL.md), with `agents/openai.yaml` alongside it. The personal copy was moved into this repository to avoid competing copies and to distribute it with the project. The owner chose mentoring reviews with prioritized findings, explanations, and diagnostic steps. Invoke with `$ormedian-pr-review` and a PR URL or local diff target. The skill reads current repository rules and memory; it does not automatically publish reviews or merge PRs.
- Remote: `https://github.com/Engr-Daniel/Ormedian_Medical_ReliableAI.git` (`origin`); local publication branch is `main`.

## Phase 0 schedule

| Day | Unit | Main output |
| --- | --- | --- |
| 1 | P0-U01 Researcher Mindset & Scientific Workflow | Research workflow note + reflection |
| 2 | P0-U02 Research Computing Environment | Reproducible local environment |
| 3 | P0-U03 Git & GitHub for Research | Branch/commit/PR workflow exercise |
| 4 | P0-U04 Reproducible Research Projects | Project structure + reproducibility checklist |
| 5 | P0-U05 Experiment Tracking & Research Journaling | Experiment template + research journal |
| 6 | P0-U06 Literature & Paper Reading Workflow | Paper-reading template + literature map |
| 7 | P0-U07 Scientific Communication & Phase Assessment | Mini presentation + Phase 0 assessment |

## Pending decisions and work

- Author unit content and actual assessment tasks when requested, using the Phase 0 guide's prerequisites and competency criteria.
- Defer detailed Weeks 2–24 allocation until Phase 0 is finished and Phase 1 planning begins.
- Await the owner's next instruction before writing P0-U01. Publication of the scaffold was authorized in MEM-0007.
- Resolve project ownership/release intentions before selecting a license.

## Request log

Append concise entries with this structure; use the actual recording time, not the placeholder:

```text
### MEM-NNNN — YYYY-MM-DDTHH:mm:ss+01:00 (Africa/Lagos)
- Request:
- Decisions / rationale:
- Implementation / files:
- Validation:
- Outcome / remaining work:
```

### MEM-0001 — 2026-09-08T15:33:39+01:00 (Africa/Lagos)

- Request: establish persistent project memory, consult it for every request, timestamp each entry, and connect it to AGENTS.md.
- Decisions / rationale: use a small Markdown current-state summary plus an append-only request log. Put the per-request read/update requirement near the beginning of AGENTS.md so it is easy to discover. This is an instruction-driven workflow, not a background hook or a guarantee of automatic execution.
- Prior context (retrospective): the owner approved the architecture updates in AGENTS.md and subsequently supplied the seven-day Phase 0 schedule. The summary above captures those decisions; exact original event times are unavailable. This timestamp is the recording time read from the system clock during memory initialization.
- Implementation / files: created `memory.md`; added the mandatory memory workflow and the memory file's tree entry to `AGENTS.md`. No curriculum scaffold, global Codex configuration, or Git history changes.
- Validation: read the memory file and AGENTS.md workflow back; confirmed reciprocal relative links and that the only project files are AGENTS.md and memory.md. AGENTS.md is 29,626 bytes, below Codex's documented default 32 KiB instruction limit by itself.
- Outcome / remaining work: persistent memory initialized and file content inspected. Future automatic compliance has not been tested in a fresh Codex session.

### MEM-0002 — 2026-09-08T15:41:23+01:00 (Africa/Lagos)

- Request: create a reusable skill to review program PRs from researchers and GTs. The owner selected mentoring feedback with prioritized findings, explanations, and suggested diagnostic steps.
- Decisions / rationale: install `ormedian-pr-review` in the default personal skills directory, with automatic selection left enabled. Read current repository policy at review time so the skill can follow later phases without stale scope rules. Return reviews in the conversation unless publication is explicitly authorized.
- Implementation / files: created the personal skill's `SKILL.md` and `agents/openai.yaml`; updated this memory file. Guidance covers review target/revision selection, pedagogy, reproducibility, scientific validity, medical data leakage, evidence-based priorities, validation limits, and merge-readiness recommendations. No curriculum scaffold or AGENTS.md changes.
- Validation: bundled `quick_validate.py` passed; parsed UI YAML, checked description length and default invocation policy, and read the completed skill for consistency. No actual PR or independent behavioral review was run.
- Outcome / remaining work: skill files are installed and structurally validated. Test with the first real PR or supplied diff; discovery in a fresh Codex session has not been verified. No GitHub review was posted and no commit was made.

### MEM-0003 — 2026-09-08T15:46:16+01:00 (Africa/Lagos)

- Request: locate the skill's openai.yaml file, which is not visible in the project workspace.
- Decisions / rationale: clarify that the installed skill is outside the repository in the personal Codex skills directory; provide a direct file link and full path.
- Implementation / files: no skill changes or relocation; updated memory only.
- Validation: confirmed `C:/Users/LENOVO T460S/.codex/skills/ormedian-pr-review/agents/openai.yaml` exists and read its contents. The current session's available-skills catalog now includes `ormedian-pr-review`, confirming discovery; review behavior remains untested.
- Outcome / remaining work: file located; no additional setup performed.

### MEM-0004 — 2026-09-08T15:48:48+01:00 (Africa/Lagos)

- Request: ask whether keeping the skill inside this repository would cause a problem.
- Decisions / rationale: recommend the supported `.agents/skills/ormedian-pr-review/` repository location for shared GT use, containing both SKILL.md and agents/openai.yaml. This is advice, not an approved relocation. Avoid maintaining competing personal and repository copies with the same name.
- Implementation / files: updated memory only; skill files remain in the personal directory.
- Validation: verified repository skill discovery and duplicate-name behavior in official documentation at https://learn.chatgpt.com/docs/build-skills.
- Outcome / remaining work: explain the shared version-control benefits and supported layout; no migration performed.

### MEM-0005 — 2026-09-08T15:52:53+01:00 (Africa/Lagos)

- Request: add all project files to the specified GitHub repository so the remote is up to date.
- Decisions / rationale: publish the existing project instructions, memory, and shared PR-review skill on main. This authorizes committing and pushing. The remote contains no refs; no existing remote history needs merging. Supersedes the personal-only skill location described in MEM-0002 through MEM-0004.
- Implementation / files: moved the two skill files into `.agents/skills/ormedian-pr-review/`, linked the skill from AGENTS.md, and updated memory. No curriculum scaffold or license created; no global Git configuration changed.
- Validation: verified the origin URL and empty remote with Git, inspected project and skill content, and passed the bundled skill validator after relocation.
- Outcome / remaining work (updated 2026-09-08T15:54:17+01:00): initial commit `f7a388f27b5d5467d705f0634d016a9e07d5a261` pushed successfully; `ls-remote` confirmed origin/main matches that commit. A follow-up documentation commit records this verified publication. Skill behavior on a real PR and curriculum development remain future work.

### MEM-0006 — 2026-09-08T16:00:57+01:00 (Africa/Lagos)

- Request: create only the minimum Phase 0 scaffold, document prerequisites, seven units/pacing, deliverables, competency outcomes, and future navigation; no lessons, later phases, license, commits, or pushes.
- Decisions / rationale: add no Python dependencies; defer Jupyter packages until notebook activities exist. Use six `.gitkeep` files to retain requested empty directories. Use Planned/As needed navigation text rather than broken links. Define evidence-based readiness and mentor review without arbitrary scores. The CSV has 20 research-tracking fields and no data rows.
- Implementation / files: added the requested root files, Phase 0 guide, four artifact-directory READMEs, literature README/bibliography/map, and empty-directory placeholders. Updated AGENTS.md's stale prerequisites/criteria planning sentence to link the guide and updated memory. Ignore rules exclude common local, model, archive, and array artifacts while retaining ordinary notes, CSV/JSON/log records, and small figures by default.
- Validation: checked local Markdown links, unique headers and absence of CSV data rows, zero requirements entries, and 22 positive/negative Git ignore cases. No dependencies installed or runtime experiments run; no browser-based Markdown rendering was performed.
- Outcome / remaining work: scaffold created locally for review. Unit content and actual assessments remain unwritten. No commit or push performed for this request.

### MEM-0007 — 2026-09-08T16:18:21+01:00 (Africa/Lagos)

- Request: update the remote repository with the approved Phase 0 scaffold.
- Decisions / rationale: commit and push the existing scaffold and its documentation updates to origin/main; this supersedes the previous request's no-commit/no-push restriction for these files.
- Implementation / files: publishing the 18 scaffold files plus AGENTS.md and memory updates. No lesson content or additional dependencies added.
- Validation: confirmed origin is the specified GitHub repository and remote main matches local HEAD before publication. Scaffold validation from MEM-0006 passed; publication checks will inspect the staged changes and confirm remote synchronization.
- Outcome / remaining work: publication in progress; unit lessons and assessment tasks remain future work.
