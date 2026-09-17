# Project Memory

This file preserves essential decisions and implementation history for the OR-MEDIAN Reliable AI Research Training Program. Read it with [AGENTS.md](AGENTS.md), which defines the mandatory workflow and project rules. Memory is context, not permission to start pending work.

## Current state

- Purpose: a reusable mentorship curriculum and reproducible research-training environment for graduate trainees, research assistants, and early-stage medical imaging AI researchers. The owner is the first learner/test user.
- Scope: Phase 0 — Researcher Setup only, Week 1 of a 24-week program. P0-U01 is now active with authored teaching and practice materials; learner completion has not been demonstrated in repository submissions. P0-U02 through P0-U07 remain planned.
- Architecture: a progressive technical track and an iterative research track converge in research projects. Research practice runs through Phases 0–5; Phase 6 formally develops rigorous independent research design and defense.
- Learning artifacts: Concept Unit, Practical Lab, Research Experiment, and Paper/Literature Unit templates. Mathematics and formal experiments apply where meaningful. Major concepts and experiments require slide material.
- Identifiers: units `P0-U01`; experiments `P1-EXP-001`; assessments `P0-A01`; reproductions `REP-001`; original projects `PRJ-001`. Unit IDs connect curriculum, slides, labs, and assessment files; assessments also carry their own IDs within documents.
- Artifact boundaries: the new final section of AGENTS.md adds `lecture-notes/` for durable teaching material; `curriculum/` now provides sequence, objectives, pacing, and navigation without duplicating full lecture notes. Labs are guided practice; slides are trainee teach-back presentations (Marp Markdown); assessments are independent reusable competency checks, with completed responses separate under `assessments/<phase>/submissions/` when privacy/ownership permits. Research notes hold reasoning and reflection; experiments hold execution evidence. Typical sequence: lecture note → recommended reading → lab → trainee teach-back → independent assessment → mentor review → reflection. Earlier structure/table descriptions have not all been reconciled with this addition.
- Tooling defaults: Python 3.11, built-in `venv`, `requirements.txt`, `requirements-dev.txt`, VS Code, Jupyter, and canonical Marp Markdown slides. These are decisions, not installed or configured infrastructure.
- Literature: `resources/literature/` contains guidance, a comments-only `references.bib`, and a headers-only `literature-map.csv`. No papers have been added. Zotero is optional. Research-paper PDFs must not be committed.
- Licensing: TBD pending ownership and Ormedian release decisions. Do not create `LICENSE` yet.
- Standards: preserve learner reasoning, make targeted fixes, verify claims, record reproducibility metadata, validate relevant work, and exclude secrets, restricted data, patient information, and unnecessary large artifacts.
- Implementation: scaffold publication remains recorded in MEM-0007. Subsequent local history includes `12d92f5` (Lecture note and assessment), `f474d51` (structural changes), and `80eaaee` (reasoning lab). P0-U01 now has a curriculum guide, version 1.0 lecture DOCX, guided reasoning lab DOCX, and P0-A01 assessment DOCX with a mentor rubric. These are authored materials, not evidence of completed learner work. A Daniel-named lab copy is now present; its extracted paragraph text matches the guided lab template, so it does not demonstrate completion. Presentation guidance and an Ormedian logo are now present under resources/style-guides/. No trainee slide deck, completed submission, journal reflection, executable code, or experiment results were found. Both requirements files remain comments-only; environment installation was not checked.
- Phase 0 readiness: prerequisites and evidence-based Ready / Ready with review / Repeat selected units decisions are in [the phase guide](curriculum/phase-0-researcher-setup/README.md). No numerical scoring or fixed study hours were introduced. Practical reproduction and responsible sharing are required for progression; missing explanations may receive targeted review.
- PR review skill: the authoritative shared copy is now [.agents/skills/ormedian-pr-review/SKILL.md](.agents/skills/ormedian-pr-review/SKILL.md), with `agents/openai.yaml` alongside it. The personal copy was moved into this repository to avoid competing copies and to distribute it with the project. The owner chose mentoring reviews with prioritized findings, explanations, and diagnostic steps. Invoke with `$ormedian-pr-review` and a PR URL or local diff target. The skill reads current repository rules and memory; it does not automatically publish reviews or merge PRs.
- Remote: `https://github.com/Engr-Daniel/Ormedian_Medical_ReliableAI.git` (`origin`); local publication branch is `main`.

## Verified repository snapshot — 2026-09-16

- Read the current root instructions and memory, relevant Markdown guides, and text extracted from the DOCX files. DOCX layout/rendering and cited readings were not independently validated during this inventory.
- Current unit guide: [P0-U01](curriculum/phase-0-researcher-setup/P0-U01.md).
- Canonical lecture location: `lecture-notes/phase-0/P0-U01_Lecture_Notes_Researcher_Mindset_and_Scientific_Workflow.docx`. Covers scientific reasoning, bounded claims, hypotheses, diagnostic experiments, negative results, and iterative research; includes recommended further reading.
- Guided lab: `labs/phase-0/P0-U01_Lab_Researcher_Mindset_and_Scientific_Workflow.docx`. Ten reasoning activities; suggested 60–90 minutes. It asks the learner to preserve their own reasoning rather than have AI generate responses.
- Independent assessment: `assessments/phase-0/P0-A01_Assessment_Researcher_Mindset_and_Scientific_Workflow.docx`. Six sections plus mentor competency rubric; suggested 60–75 minutes. Open-resource unless the mentor specifies otherwise; answers must be the learner's own.
- New README guidance exists in lecture-notes/phase-0, labs/phase-0, slides/phase-0, and assessments/phase-0/submissions. The submissions directory contains guidance only; slides contain guidance and a placeholder, not a completed teach-back.
- Bibliography remains comments-only and the literature map has headers only, despite further-reading recommendations in the lecture. No bibliography entries were invented or imported.
- Git status outside the sandbox succeeded: branch `main`, HEAD `80eaaee`, no changes before this memory update, and no ahead/behind difference against the locally cached `origin/main`. No fresh remote query was performed, so live GitHub synchronization is not established. Sandboxed Git still reports an ownership error; no Git configuration was changed.

## Observed documentation inconsistencies

- The root README still calls the repository a scaffold with no authored lessons/labs/assessments. This is stale relative to the P0-U01 materials.
- The lecture DOCX also remains in `curriculum/phase-0-researcher-setup/`; The copies were byte-identical at the September 16 inspection, but the canonical lecture-notes copy has since been modified; that earlier equivalence must not be assumed now. Current directory guidance names lecture-notes as the teaching-material location. No duplicate was removed during this inspection.
- `P0-A01` now identifies the P0-U01 assessment, but the Phase 0 README still reserves the same ID for the overall phase assessment/P0-U07 and says actual assessment prompts are future work. This needs a later naming/navigation decision.
- The AGENTS.md tree and earlier directory table do not yet fully reflect the added lecture-notes boundaries. Record the discrepancy rather than silently changing the rules in a memory-refresh task.

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

- Next learner sequence: study P0-U01 lecture/readings, complete the guided reasoning lab, prepare teach-back slides, complete P0-A01 independently, receive mentor feedback, and record reflection. No completion should be inferred from the existence of templates.
- Defer detailed Weeks 2–24 allocation until Phase 0 is finished and Phase 1 planning begins.
- P0-U01 materials already exist; do not recreate them based on older memory. Await instructions for learner support, documentation reconciliation, or P0-U02 authoring.
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
- Outcome / remaining work (updated 2026-09-08T16:19:00+01:00): scaffold commit 20a16779bef1d90894a0f5591e9670f7f771b787 pushed successfully; remote main was verified to match local HEAD. Staged whitespace checks passed. A follow-up memory commit records the verified publication. Unit lessons and assessment tasks remain future work.

### MEM-0008 — 2026-09-16T16:58:58+01:00 (Africa/Lagos)

- Request: summarize where the project stands.
- Decisions / rationale: Phase 0 architecture and scaffold are complete; next planned content is P0-U01, not yet authored. No new lesson work requested.
- Implementation / files: read AGENTS.md and memory, inspected the file inventory, and updated memory only.
- Validation: confirmed scaffold and shared skill files remain present with no unit lessons in the inventory. Git status/log checks were rejected by an ownership safety check even with the per-command safe.directory setting; current Git synchronization was not verified. Last confirmed publication was September 8, with follow-up memory commit 2b11db8 recorded in the conversation.
- Outcome / remaining work: report completed planning/scaffold, pending lessons and learner activities, and P0-U01 as the next step. No commit or push performed.

### MEM-0009 — 2026-09-16T23:12:46+01:00 (Africa/Lagos)

- Request: inspect the repository and refresh memory to the present state; the follow-up "continue" resumes this task.
- Decisions / rationale: supersede stale claims in the current-state summary that all unit content is unwritten. Record authored P0-U01 materials separately from unobserved learner completion and preserve earlier entries as historical records.
- Implementation / files: updated memory.md only with the current artifact boundaries, P0-U01 inventory, Git snapshot, and observed inconsistencies. No lessons, rules, duplicates, assessment responses, or citations were changed.
- Validation: read root AGENTS.md completely, memory, the root and Phase 0 guides, unit guide, and new directory guidance; extracted DOCX text using Python's standard-library ZIP/XML readers; compared lecture SHA-256 hashes; checked requirements and literature files. Read-only Git status/log/remote configuration succeeded outside the sandbox after sandboxed ownership failures. HEAD is 80eaaee; cached origin/main matches. No live remote check, document rendering, or scientific content audit performed.
- Outcome / remaining work: memory now reflects active P0-U01 and pending learner work. Record stale README status, duplicate lecture, and assessment-ID conflict for later reconciliation. No commit or push performed; this memory update is local.

### MEM-0010 ? 2026-09-17T22:14:48+01:00 (Africa/Lagos)

- Request: add the current file changes and update the remote repository.
- Decisions / rationale: publish the revised canonical lecture DOCX, Daniel-named lab DOCX, presentation style guide, logo, and accumulated memory update. Leave the two untracked reading PDFs local under the repository's paper/book PDF policy. No curriculum reconciliation or new lesson content is in scope.
- Implementation / files: refreshed this summary and prepared the five files above for publication on main. The Daniel-named lab has the same extracted paragraph text as the template; learner completion remains unverified.
- Validation: read AGENTS.md and memory, inspected Git status and the style guide, checked both DOCX ZIP integrity and compared lab paragraph text. Confirmed origin URL and live remote main at 80eaaee57ed08f83d203f4bb4e3f5ed4f835e8ee before publication. Document rendering and scientific content were not independently reviewed.
- Outcome / remaining work (updated 2026-09-17T22:15:36+01:00): published commit 9ffbc1d7c8062f5cc2c00d5a1ac75a8ab263f8b1 to origin/main and verified that live remote HEAD matches local HEAD. Staged whitespace checks passed. This follow-up memory update records the verified publication. Only the reading PDFs remain untracked locally. Existing README, duplicate-lecture, and assessment-ID inconsistencies remain pending.
