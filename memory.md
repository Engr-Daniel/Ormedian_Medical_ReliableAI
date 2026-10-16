# Project Memory

This file preserves essential decisions and implementation history for the OR-MEDIAN Reliable AI Research Training Program. Read it with [AGENTS.md](AGENTS.md), which defines the mandatory workflow and project rules. Memory is context, not permission to start pending work.

## Current state

- Active P0-U02 lab protocol: give one small explained step, wait for the learner to run it and share evidence, then review before continuing. Learner performs the lab actions; do not automate completion. Part A in progress: learner reports both Get-Location and git rev-parse --show-toplevel match the repository root; learner reports current short commit 8e5a7d4; py -0p lists 64-bit Python 3.10 (launcher default) and Anaconda Python 3.9, with no Python 3.11 entry. where.exe python lists the Python310 executable first and WindowsApps/python.exe second. Learner reports python --version returns Python 3.10.0. Learner runtime diagnostics identify the base Python310 executable, Python 3.10.0 64-bit, and equal sys.prefix/sys.base_prefix; this process is outside a venv. Learner reports Test-Path .venv returns False. Part A3 response needs precision: launcher-known installations are not an exhaustive machine inventory, and where.exe lists search candidates rather than proving runtime identity. Learner correctly identified print(sys.executable) as direct running-interpreter evidence. Learner reports py -3.11 --version cannot find Python 3.11 and lists only 3.10/3.9. Learner confirms the installer download is complete. Screenshot confirms Python 3.11.9 (64-bit) initial setup screen, PATH unchecked and admin privileges for py.exe checked. Optional Features screenshot shows all options checked. Guidance: uncheck Python test suite; keep documentation, pip, Tcl/Tk and IDLE, and py launcher with its existing all-users selection; Advanced Options screenshot now shows per-user installation and environment-variable changes unchecked, associations and shortcuts checked, other advanced options unchecked. Learner confirms destination ends in Python\Python311. Latest screenshot confirms file associations unchecked and precompile standard library newly checked; PATH and all-users Python install remain unchecked. Installer screenshot now reports Setup was successful for Python 3.11.9 (64-bit). Learner confirms py -3.11 --version returned the expected Python 3.11.9; raw output not supplied. Learner supplied sys.executable output confirming the per-user Python311 executable. Learner reconfirms the repository .venv path is absent after installation (Test-Path returns False). Learner reports completing project .venv creation with py -3.11 -m venv. Learner supplied runtime evidence: Python 3.11.9 64-bit, project .venv/Scripts/python.exe, and True for sys.prefix != sys.base_prefix. The environment runtime is verified from learner output. Learner now supplies the (.venv) PowerShell prompt at the repository root after activation. Learner reports the short python command now resolves to the project .venv/Scripts/python.exe after activation. Learner reports python -m pip --version shows pip 24.0 from the project .venv site-packages (python 3.11). Part B commands complete. Learner submitted B1-B3: B2 accepted; B1 needs cited evidence (it asserts alignment without quoting outputs); B3 correctly explains PATH ordering but omits why direct interpreter invocation works without activation. Learner chose to skip revising B1/B3 and move to Part C; B1 and B3 remain incomplete for written evidence packaging. Part C started: both requirements files contain comments only (no packages; requirements-dev.txt does not include -r requirements.txt). Part D will need ipykernel, which no requirements file declares. Learner pasted the requirements file contents (first two comment lines of requirements.txt missing from the paste) without written predictions. Learner ran Part C commands: installs produced only pip upgrade notices (24.0 -> 26.2.1 available); pip check reports No broken requirements found; pip list shows only pip 24.0 and setuptools 65.5.0, seeded by venv rather than declared or transitive project dependencies. pip upgrade deliberately not performed. Learner chose to skip C1-C4 written answers; they remain incomplete for evidence packaging. Part D started: VS Code Python and Jupyter extensions are installed (observed via code --list-extensions). Learner selected the .venv interpreter; a new VS Code integrated terminal auto-ran a process-scoped Set-ExecutionPolicy RemoteSigned plus Activate.ps1 (no machine-wide policy change), showed the (.venv) prompt, and sys.executable resolved to the project .venv python.exe. Status-bar interpreter not reported. Learner confirms pip show ipykernel reports Package(s) not found in .venv. Learner installed ipykernel 7.4.0 into .venv site-packages with python -m pip (27 packages total including transitive dependencies such as ipython 9.17.1, jupyter-client 8.10.0, pyzmq 27.2.0, tornado 6.5.10). Pending decision: declare ipykernel==7.4.0 in requirements-dev.txt (not yet changed). Learner ran local uncommitted kernel_check.ipynb: notebook sys.executable is the project .venv python.exe (lowercase drive letter only; same file on case-insensitive Windows) and sys.version is 3.11.9 64-bit, matching the terminal. Kernel screenshot for Checkpoint D not yet supplied. Learner added a comment and ipykernel==7.4.0 to requirements-dev.txt (uncommitted working-tree change, verified by agent); pip install -r requirements-dev.txt reports all requirements already satisfied. The file's first comment line ('No third-party development dependencies are needed') is now stale; learner advised to revise it. Part D commands complete; kernel screenshot and D1-D3 answers outstanding. kernel_check.ipynb is untracked and should stay uncommitted. Part E1 constructed: two disposable Python 3.11 venvs under the user temp folder; colorama 0.4.6 installed in env-a only; import with env-b fails with ModuleNotFoundError. venv emitted 'Actual environment location may have moved' warnings because TEMP uses the 8.3 short user-folder name (the username contains a space); harmless. Learner E1 hypotheses: (1) package installed for a different interpreter; (2) distribution name differs from import name. Chosen check: python -m pip show PACKAGE. Review: good hypotheses; check is right in kind but bare python in the activated terminal would query the project .venv, not the failing interpreter. Learner ran targeted checks (after resetting $e1 lost in a new terminal): env-b reports Package(s) not found: colorama; env-a shows colorama 0.4.6 located in env-a site-packages. Evidence supports H1 (wrong interpreter) and rules out H2 for the failing context. E1 fix applied by learner: colorama installed into env-b via env-b's interpreter; the unchanged failing command now prints 'import ok'. Learner's lesson ('always check things') is too general and needs revision. Part E2 started: agent observed base Python 3.10 and Anaconda 3.9 both have ipykernel but lack nest_asyncio2, which exists only in the project .venv. E2 reproduced by learner: terminal (.venv python.exe) imports nest_asyncio2 successfully; notebook on the Python 3.10 kernel prints the base Python310 executable then raises ModuleNotFoundError for nest_asyncio2. Interpreter mismatch is supported. E2 retest by learner: notebook switched back to the .venv kernel prints the .venv python.exe (import succeeds). Learner, citing time pressure, asked to skip all remaining written work: B1/B3 revisions, C1-C4, D1-D3, E1 lesson revision, E2 competing hypotheses, E3, E4, F1-F3, environment_report.md, reconstruction_notes.md, and the troubleshooting records. Practical commands for Parts A-E are complete; written evidence is not, so mentor competency review cannot yet confirm P0-U02 readiness. Part F evidence (learner-run): HEAD 8e5a7d4d52bdbd8b9f47edd4b25998a43e2d1c7e; Windows-10-10.0.19044-SP0; Python 3.11.9 64-bit at the project .venv; pip check clean; pip freeze lists 27 packages (ipykernel 7.4.0 and its dependencies; pip/setuptools omitted by freeze). Agent verified the temp E1 venvs and kernel_check.ipynb are deleted and requirements-dev.txt has a revised first comment (second comment line about adding Jupyter tooling later is now mildly stale). P0-U02 lab practical steps are complete; all written answers and Part F reports were skipped by learner choice, so mentor readiness review remains pending. Learner authorized publishing on 2026-10-16: requirements-dev.txt, the P0-U02 lecture and lab DOCX, the evidence package, the teach-back deck and assets, and memory were committed to main and pushed (recommended-books PDFs and the Word lock file excluded). At the learner's explicit request (they state they understand the material), the agent drafted the lab submission package in research-notes/phase-0/P0-U02/ (answers.md, environment_report.md, command_log.txt, reconstruction_notes.md) and a 9-slide Marp teach-back draft slides/phase-0/P0-U02_research_computing_environment_Daniel.md with SVG diagrams in slides/phase-0/assets/P0-U02/. All are labelled AI-drafted; trainee reported on 2026-10-16 that they reviewed them and accepted the wording, and the notes were updated to say so; uncommitted per the lab's 'do not commit automatically' rule. Owner decision 2026-10-16: P0-U02 has no separate independent assessment; the guided lab P0-U02-LAB-001 serves as the unit assessment. Checkpoint D screenshot (research-notes/phase-0/P0-U02/checkpoint-d-kernel.png, no personal data) and the P0-U02 reflection are now present. Mentor review P0-U02-MR-001 is published: READY / COMPLETE. The owner replaced the Marp deck source with a rendered PDF (slides/phase-0/P0-U02_research_computing_environment.pdf, about 7 MB); the Marp source remains recoverable from commit a74a34f, and the SVG assets in slides/phase-0/assets/P0-U02/ are now unreferenced. Correction: the environment has 28 packages, not 27 (pyzmq was miscounted). Part A written reasoning/evidence packaging and project environment setup remain pending.

- Research reflection: `research-notes/phase-0/P0-U01/P0-U01_research_reflection_Daniel.md` is organized under six requested reflection questions and was published to origin/main in `c4ea9f9` on 2026-09-29. Editorial polishing preserves the learner's account; it is not a mentor competency assessment and supersedes older inventory claims that no reflection exists.
- Presentation palette: the style guide permits coordinated deep blue, navy, royal/electric blue, azure, sky blue and pale blue alongside black and white. Multiple shades may share a slide, with consistent roles and readable contrast; the logo must retain its original colours.
- Latest publication: presentation palette update `cb80ef6` and existing lab-answer/AUROC-note commit `5d3b8ce` were pushed to origin/main and verified on 2026-09-29. Learner responses and the supplementary note were not academically reviewed in this publication task.
- New artifacts observed 2026-09-29: P0-A01 submission contains trainee responses; a P0-U01 teach-back PDF is present; the AUROC supplementary DOCX is revised. These supersede older inventory claims that no submission or slide deck exists. Mentor assessment and slide rendering have not been performed; the canonical Marp source remains missing.
- Publication update: `5ef77ab` published the assessment submission, slide PDF and AUROC note to origin/main; `6830468` subsequently removed the duplicate curriculum lecture, retaining the canonical lecture-notes copy. Both publications were verified on 2026-09-29. Recommended-book PDFs remain local.
- Purpose: a reusable mentorship curriculum and reproducible research-training environment for graduate trainees, research assistants, and early-stage medical imaging AI researchers. The owner is the first learner/test user.
- Scope: Phase 0 — Researcher Setup only, Week 1 of a 24-week program. P0-U01 is COMPLETE with a READY decision in P0-U01-MR-001. P0-U02 is COMPLETE with a READY decision in P0-U02-MR-001 (2026-10-16; no separate assessment). Resume at P0-U03 - Git & GitHub for Research; its lecture note and guided lab DOCX are published. P0-U04 through P0-U07 remain planned.
- Architecture: a progressive technical track and an iterative research track converge in research projects. Research practice runs through Phases 0–5; Phase 6 formally develops rigorous independent research design and defense.
- Learning artifacts: Concept Unit, Practical Lab, Research Experiment, and Paper/Literature Unit templates. Mathematics and formal experiments apply where meaningful. Major concepts and experiments require slide material.
- Identifiers: units `P0-U01`; experiments `P1-EXP-001`; assessments `P0-A01`; reproductions `REP-001`; original projects `PRJ-001`. Unit IDs connect curriculum, slides, labs, and assessment files; assessments also carry their own IDs within documents.
- Artifact boundaries: the new final section of AGENTS.md adds `lecture-notes/` for durable teaching material; `curriculum/` now provides sequence, objectives, pacing, and navigation without duplicating full lecture notes. Labs are guided practice; slides are trainee teach-back presentations (Marp Markdown); assessments are independent reusable competency checks, with completed responses separate under `assessments/<phase>/submissions/` when privacy/ownership permits. Research notes hold reasoning and reflection; experiments hold execution evidence. Typical sequence: lecture note → recommended reading → lab → trainee teach-back → independent assessment → mentor review → reflection. Earlier structure/table descriptions have not all been reconciled with this addition.
- Tooling defaults: Python 3.11, built-in `venv`, `requirements.txt`, `requirements-dev.txt`, VS Code, Jupyter, and canonical Marp Markdown slides. These are decisions, not installed or configured infrastructure.
- Literature: `resources/literature/` contains guidance, a comments-only `references.bib`, and a headers-only `literature-map.csv`. No papers have been added. Zotero is optional. Research-paper PDFs must not be committed.
- Licensing: TBD pending ownership and Ormedian release decisions. Do not create `LICENSE` yet.
- Standards: preserve learner reasoning, make targeted fixes, verify claims, record reproducibility metadata, validate relevant work, and exclude secrets, restricted data, patient information, and unnecessary large artifacts.
- Implementation: Phase 0 scaffold, P0-U01 lecture/lab/assessment, learner lab responses, assessment submission, teach-back PDF, reflection, and final mentor review are present. The mentor record authorizes progression to P0-U02, whose lecture DOCX is present. This supersedes earlier inventory statements about absent learner work; no new competency assessment was conducted during this status check. Canonical Marp slide source remains outstanding.
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
- Resolved 2026-09-29 (MEM-0014): the outdated duplicate lecture DOCX in `curriculum/phase-0-researcher-setup/` was removed from main. The canonical `lecture-notes/` copy remains.
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

- Resume with the existing P0-U02 Research Computing Environment lecture; P0-U01 completion is recorded in the final mentor review. No fixed calendar restart date is recorded.
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

### MEM-0011 — 2026-09-29T07:42:02+01:00 (Africa/Lagos)

- Request: understand the repository context and broaden the presentation style from one blue shade to shades including deep blue, sky blue and azure.
- Decisions / rationale: allow a coordinated blue family, retaining the blue/black/white identity, consistent shade roles, readable contrast and unchanged logo colours.
- Implementation / files: updated colour guidance, illustration wording, consistency guidance and quality checks in `resources/style-guides/ORMEDIAN_PRESENTATION_STYLE.md`; updated this memory summary and log. No AGENTS.md rule conflicts required changes.
- Validation: read repository instructions, memory, root README and full presentation guide; inspected relevant Markdown inventory and read back the revised guide for consistency. Git status was blocked by an ownership safety check; no Git configuration was changed. No slide rendering or remote inspection was performed; no repository link was supplied in this request, so local context was used.
- Outcome / remaining work: requested style guidance updated locally. No commit or push performed.

### MEM-0012 — 2026-09-29T07:45:13+01:00 (Africa/Lagos)

- Request: push the updates to the owner's GitHub repository.
- Decisions / rationale: publish the presentation palette change and memory on main, including existing unpushed commit `5d3b8ce` (lab answers and AUROC supplementary note). Leave untracked recommended books local under the repository PDF policy.
- Implementation / files: prepared `resources/style-guides/ORMEDIAN_PRESENTATION_STYLE.md` and `memory.md` for commit. Existing committed learner material is preserved without modification.
- Validation: reviewed the two text diffs and existing commit file summary; verified origin matches the requested repository and live remote main is `be88708`, the parent of the pending local commit. Publication and final synchronization checks are pending.
- Outcome / remaining work: authorized publication in progress; record the verified outcome after pushing. The earlier memory description of the Daniel lab matching the template is historical; the existing lab-answer commit means it must not be treated as a current verification of learner completion.
- Verified outcome (2026-09-29T07:46:13+01:00): committed the style and memory updates as `cb80ef6af098a14765a7786a78aeda189bb539d2`, pushed main successfully, and confirmed the live remote hash matches local HEAD. Staged whitespace checks passed. Only `resources/recommended-books/` remained untracked. A follow-up memory commit records this successful publication.

### MEM-0013 — 2026-09-29T12:41:33+01:00 (Africa/Lagos)

- Request: push the current updates.
- Decisions / rationale: publish the revised AUROC supplementary note, new assessment submission and trainee slide PDF as requested; preserve learner content. Recommended-book PDFs remain local. The authored slide export is distinct from excluded research-paper PDFs; missing Marp source is recorded as pending work.
- Implementation / files: prepare the three artifacts above and this memory update for publication on main.
- Validation: verified origin and live main at `ed5faa0`; checked DOCX ZIP integrity and extracted paragraph text, file sizes, and the PDF signature. PDF text extraction was unavailable (pypdf not installed); no layout rendering, scientific review or competency assessment was performed.
- Outcome / remaining work: publication prepared; commit/push verification follows. Add the canonical Marp source in future work; learner readiness is not established by publication.
- Approval block (2026-09-29T12:49:42+01:00): automatic approval review rejected the combined publication because trainee responses require explicit approval for public export. Asked the owner whether to publish the assessment; response pending. Proceed with the AUROC note, slide PDF and memory only. A newly observed deletion of the duplicate curriculum lecture appeared during this task and is left unstaged.
- Approval received (2026-09-29T12:50:22+01:00): owner explicitly approved publishing the assessment responses to the named GitHub repository. Include the submission in this push. Git treated the PDF as text in whitespace checking; its staged blob hash matches the raw file hash, confirming unchanged bytes. Restrict whitespace validation to Markdown.
- Verified outcome (2026-09-29T12:51:23+01:00): pushed `5ef77ab087f6fc5ca91fd852d54fb6f48b5aae83`; live remote main matches local HEAD. Markdown whitespace validation passed. Assessment file changed during the task (42,519 bytes inspected; 41,880 bytes committed), so earlier text inspection does not establish exact final-content validation. Duplicate lecture deletion and recommended books remain local. This follow-up memory update records the completed publication.

### MEM-0014 — 2026-09-29T12:56:33+01:00 (Africa/Lagos)

- Request: remove the locally deleted duplicate lecture note from the remote too.
- Decisions / rationale: publish the exact deletion under curriculum while preserving the canonical lecture-notes copy; no history rewriting.
- Implementation / files: committed the duplicate DOCX deletion as `683046854107fae936f61a63e6e07ffbc97d9003`; updated this memory summary and log.
- Validation: confirmed canonical file exists, searched Markdown for exact-filename references (none outside memory), passed staged whitespace checks, and verified the published tree retains only the canonical path. Live remote main matched the deletion commit after push.
- Outcome / remaining work: duplicate removed from GitHub main. Recommended-book PDFs remain local. This memory record is published in a follow-up documentation commit.

### MEM-0015 — 2026-09-29T13:08:13+01:00 (Africa/Lagos)

- Request: polish the local P0-U01 reflection and separate the six supplied questions.
- Decisions / rationale: retain the learner's first-person experiences and reasoning; improve wording and paragraph flow without inventing experiences or answering a new assessment. Identify the unit as P0-U01 and retain P0-A01 as the related assessment.
- Implementation / files: edited `research-notes/phase-0/P0-U01/P0-U01_research_reflection_Daniel.md` into six question headings, clarified the lab scenario and metric wording, and organized intended research habits as questions; updated memory.
- Validation: read the original reflection and research-notes guidance, checked for nested AGENTS.md files (none found), and read the revised Markdown back to confirm all six questions and the original themes remain. No document rendering or competency assessment performed.
- Outcome / remaining work: polished reflection saved locally; no commit or push requested or performed.

### MEM-0016 — 2026-09-29T13:10:56+01:00 (Africa/Lagos)

- Request: push the polished reflection.
- Decisions / rationale: publish the specifically requested reflection and its memory record to the established origin/main; leave recommended books local.
- Implementation / files: committed the reflection and preceding memory update as `c4ea9f9c43ae3b923583ead2d0e92aad7fa6ea17`; updated memory with the verified outcome.
- Validation: reread the reflection, verified origin and live remote before publication, passed staged whitespace checks, pushed successfully, and confirmed live main matches the reflection commit.
- Outcome / remaining work: reflection published. This follow-up memory record is included in a documentation commit; no further reflection changes needed for this request.

### MEM-0017 - 2026-10-15T16:19:41+01:00 (Africa/Lagos)

- Request: explain current progress and where to resume.
- Decisions / rationale: use the final P0-U01 mentor record (READY, COMPLETE, proceed to P0-U02) to supersede stale memory status.
- Implementation / files: updated memory.md summary and log only. Confirmed P0-U02 lecture exists; README still incorrectly describes an empty scaffold.
- Validation: read root instructions, memory, P0-U01 guide, final mentor review, root README, and curriculum/artifact inventory. No new assessment, environment verification, or live remote check performed.
- Outcome / remaining work: resume P0-U02 lecture and computing-environment learning. No fixed resumption date is documented. README/navigation reconciliation and Marp source remain pending; no commit or push performed.

### MEM-0018 - 2026-10-15T17:22:51+01:00 (Africa/Lagos)

- Request: guide P0-U02 lab interactively, one step at a time, waiting for learner results.
- Decisions / rationale: follow the existing P0-U02-LAB-001; begin with read-only working-directory verification in PowerShell before environment changes. Preserve learner execution and diagnostic reasoning.
- Implementation / files: memory.md only; recorded the session protocol. Found and read the P0-U02 guided lab DOCX.
- Validation: read complete AGENTS.md and memory, located unit materials, extracted the lab text with standard-library ZIP/XML. No learner commands, installations, or environment changes performed.
- Outcome / remaining work: first instruction is Get-Location in the VS Code PowerShell terminal; await actual output before continuing Part A. No commit or push.

### MEM-0019 - 2026-10-15T17:30:46+01:00 (Africa/Lagos)

- Request / evidence: learner confirms Get-Location returned the expected repository folder; no raw transcript supplied.
- Decisions / rationale: proceed one step to read-only Git root detection, preserving learner execution.
- Implementation / files: memory.md only; updated current checkpoint.
- Validation: reread AGENTS.md and memory; accepted learner-reported directory result, without independently running the lab command.
- Outcome / remaining work: ask learner to run git rev-parse --show-toplevel and share output or error; await result. No environment changes, commit, or push.

### MEM-0020 - 2026-10-15T17:36:06+01:00 (Africa/Lagos)

- Request / evidence: learner reports Git root output matches the expected repository path; raw transcript not supplied.
- Decisions / rationale: advance to the read-only current commit identifier check, one command at a time.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: reread AGENTS.md and memory; no independent execution of learner commands.
- Outcome / remaining work: await actual output of git rev-parse --short HEAD. No environment changes, commit, or push.

### MEM-0021 - 2026-10-15T17:37:28+01:00 (Africa/Lagos)

- Request / evidence: learner supplied 8e5a7d4 as output of git rev-parse --short HEAD.
- Decisions / rationale: record the reported revision and continue Part A with Python launcher inventory (py -0p), waiting for output before environment selection.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; recorded learner evidence without executing lab commands.
- Outcome / remaining work: await sanitized interpreter list or exact error; Python availability remains unverified. No installation, environment changes, commit, or push.

### MEM-0022 - 2026-10-15T17:40:21+01:00 (Africa/Lagos)

- Request / evidence: learner supplied sanitized py -0p output showing Python 3.10-64 with default marker and Anaconda Python 3.9-64. No 3.11 entry is listed.
- Decisions / rationale: distinguish launcher inventory from terminal command resolution; finish baseline checks before considering Python 3.11 setup. Absence from launcher list alone does not prove absence from the machine.
- Implementation / files: memory.md only; checkpoint updated without personal paths.
- Validation: read AGENTS.md and memory and interpreted supplied output; no lab commands executed on the learner's behalf.
- Outcome / remaining work: request where.exe python output next. No installation, PATH change, environment modification, commit, or push.

### MEM-0023 - 2026-10-15T17:42:31+01:00 (Africa/Lagos)

- Request / evidence: learner supplied sanitized where.exe python output: Python310 executable first, WindowsApps executable second.
- Decisions / rationale: verify the version actually executed with python --version before concluding runtime identity; continue one step at a time.
- Implementation / files: memory.md only; updated checkpoint without personal paths.
- Validation: reread AGENTS.md and memory; interpreted supplied search results, no learner commands executed by agent.
- Outcome / remaining work: await python --version output. No environment changes, installation, commit, or push.

### MEM-0024 - 2026-10-15T17:43:27+01:00 (Africa/Lagos)

- Request / evidence: learner reports Python 3.10.0 from python --version.
- Decisions / rationale: continue baseline inspection with one read-only Python command printing executable, version and prefixes; add prefix evidence to address lab A2 without inferring venv status from version alone.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: reread AGENTS.md and memory, interpreted learner-supplied output; no lab command executed by agent.
- Outcome / remaining work: await sanitized runtime diagnostics. Python 3.11 setup and environment creation remain pending. No installation, environment changes, commit, or push.

### MEM-0025 - 2026-10-15T17:45:36+01:00 (Africa/Lagos)

- Request / evidence: learner supplied sanitized runtime diagnostics: Python310 executable, Python 3.10.0 64-bit, and identical base/active prefixes.
- Decisions / rationale: current process is outside a venv; this does not establish whether a project .venv exists. Inspect that path before creation or replacement.
- Implementation / files: memory.md only; checkpoint updated without personal paths.
- Validation: reread AGENTS.md and memory; compared the supplied prefixes and executable path. No learner commands executed by agent.
- Outcome / remaining work: await Test-Path .venv output. Baseline reasoning answers, evidence packaging and Python 3.11 availability still need attention. No environment changes, installation, commit, or push.

### MEM-0026 - 2026-10-15T17:46:41+01:00 (Africa/Lagos)

- Request / evidence: learner reports False from Test-Path .venv.
- Decisions / rationale: no existing .venv path was found in the checked repository root. Check understanding of launcher inventory versus PATH lookup before setup, preserving learner reasoning.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: reread AGENTS.md and memory; interpreted learner output, without executing lab commands.
- Outcome / remaining work: await learner explanation of differing py -0p and where.exe python results. No installation or environment changes; no commit or push.

### MEM-0027 - 2026-10-15T17:51:18+01:00 (Africa/Lagos)

- Request / evidence: learner described py -0p as all installed Pythons and where.exe as the exact running Python location.
- Decisions / rationale: clarify launcher-known installations versus current-directory/PATH candidates; use prior sys.executable output as direct runtime evidence. Explain Anaconda is launcher-known but its executable directory was not found by the terminal search.
- Implementation / files: memory.md only; learning checkpoint updated.
- Validation: reread AGENTS.md and memory; assessed explanation against supplied diagnostic outputs. No additional runtime checks performed.
- Outcome / remaining work: await learner identification of the command that directly reports the running interpreter; retain one-step guidance. No installation, environment changes, commit, or push.

### MEM-0028 - 2026-10-15T17:56:03+01:00 (Africa/Lagos)

- Request / evidence: learner correctly answered print(sys.executable) for direct runtime interpreter identity.
- Decisions / rationale: confirm understanding and request py -3.11 --version to check whether the existing launcher can start the required version before environment creation.
- Implementation / files: memory.md only; current checkpoint updated.
- Validation: read AGENTS.md and memory; assessed learner answer against previous diagnostics. No learner lab command executed by agent.
- Outcome / remaining work: await Python 3.11 version output or exact error; evidence packaging and setup remain pending. No installation, environment changes, commit, or push.

### MEM-0029 - 2026-10-15T17:58:32+01:00 (Africa/Lagos)

- Request / evidence: learner reports the existing Windows launcher cannot find Python 3.11.
- Decisions / rationale: guide one download step for the official 3.11.9 Windows 64-bit installer, preserving existing installations; this traditional installer is older than subsequent security releases, not the latest 3.11 patch.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; verified official Python 3.11.9 release page and Windows installer availability. No learner commands or installations performed.
- Outcome / remaining work: await download confirmation before guiding installer settings; installation, venv creation and evidence packaging remain pending. No commit or push.

### MEM-0030 - 2026-10-15T18:02:18+01:00 (Africa/Lagos)

- Request: learner asks whether Python 3.11.9 has been suspended after seeing its release notice.
- Decisions / rationale: explain superseded means a newer release exists; 3.11.9 remains downloadable and was the last official 3.11 binary-installer release. Later 3.11 security releases are source-only and their fixes are absent from 3.11.9. Retain the existing lab download step with this limitation explicit.
- Implementation / files: memory.md only; no installation or project policy changes.
- Validation: reread AGENTS.md and memory; checked official Python 3.11.9 and 3.11.17 release pages, including No installers policy.
- Outcome / remaining work: download confirmation remains pending; explain installer choice without claiming it is the latest patched release. No commit or push.

### MEM-0031 - 2026-10-15T18:05:05+01:00 (Africa/Lagos)

- Request: learner asks whether the embed-amd64.zip link is the intended download.
- Decisions / rationale: distinguish the embeddable ZIP from the standard Windows 64-bit installer; provide python-3.11.9-amd64.exe for the lab.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory; checked official release download table and installer link.
- Outcome / remaining work: await installer download confirmation; do not run installer yet. No installation, commit, or push.

### MEM-0032 - 2026-10-16T11:41:09+01:00 (Africa/Lagos)

- Request / evidence: learner reports installer downloaded.
- Decisions / rationale: open the installer first and inspect initial options; preserve one-step guidance and existing Python installations. Leave Add python.exe to PATH unchecked to preserve current terminal command resolution.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; download completion is learner-reported, installer screen not yet inspected.
- Outcome / remaining work: await initial screen options before selecting installation settings. No installation, commit, or push performed by agent.

### MEM-0033 - 2026-10-16T11:45:58+01:00 (Africa/Lagos)

- Request / evidence: learner shared the initial Python 3.11.9 (64-bit) setup screenshot; PATH unchecked, admin privileges for py.exe checked, per-user Python311 destination displayed.
- Decisions / rationale: choose Customize installation to inspect features before installation; retain unchecked PATH setting and one-screen-at-a-time guidance.
- Implementation / files: memory.md only; checkpoint updated without personal paths.
- Validation: read AGENTS.md and memory and visually inspected supplied screenshot. No installer actions executed by agent.
- Outcome / remaining work: await Optional Features screen; installation and environment creation remain pending. No commit or push.

### MEM-0034 - 2026-10-16T11:47:21+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Optional Features screenshot with every option checked.
- Decisions / rationale: omit the standard-library test suite, which is unnecessary for project tests; retain documentation, pip, Tcl/Tk and IDLE, and launcher with current all-users scope matching the existing system launcher. Review Advanced Options next before installation.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; inspected screenshot labels and checkbox states. No installation or runtime checks performed.
- Outcome / remaining work: await Advanced Options screenshot after learner changes and Next. No commit or push.

### MEM-0035 - 2026-10-16T11:49:33+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Advanced Options screenshot; all-users install and environment-variable changes unchecked, associations and shortcuts checked; destination ending clipped.
- Decisions / rationale: inspect destination ending using End in the location field before installation, to confirm a separate Python311 folder.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; inspected screenshot without assuming hidden path text.
- Outcome / remaining work: await destination suffix confirmation; installation pending. No installer actions, commit or push performed by agent.

### MEM-0036 - 2026-10-16T11:49:55+01:00 (Africa/Lagos)

- Request: learner greeting ("hello"); no new evidence or task.
- Decisions / rationale: none; restate the current P0-U02 checkpoint so the learner can resume.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory. No installer actions, commit, or push.
- Outcome / remaining work: still awaiting confirmation that the installer destination ends in Python\Python311 before clicking Install.

### MEM-0037 - 2026-10-16T11:51:41+01:00 (Africa/Lagos)

- Request / evidence: learner confirms installer destination ends in Python\Python311.
- Decisions / rationale: proceed with per-user installation in the separate version folder, PATH unchanged; uncheck file associations to preserve existing file-opening behavior. Existing all-users launcher selection may prompt for elevation.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; accepted learner destination confirmation and reviewed prior screenshot settings. No installation executed by agent.
- Outcome / remaining work: await setup completion or exact error before runtime verification; no commit or push.

### MEM-0038 - 2026-10-16T11:53:40+01:00 (Africa/Lagos)

- Request / evidence: learner supplied revised Advanced Options screenshot showing associations unchecked and precompile standard library checked.
- Decisions / rationale: precompiling standard-library bytecode is optional and acceptable; retain these settings and proceed with Install.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; inspected screenshot and compared options to prior screen. No installation executed or verified.
- Outcome / remaining work: await final setup success or error screen, then verify runtime. No commit or push.

### MEM-0039 - 2026-10-16T11:57:35+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Python 3.11.9 (64-bit) installer success screenshot.
- Decisions / rationale: distinguish installer success from runtime verification; close installer and request py -3.11 --version as the next single diagnostic.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; visually confirmed setup success message. No runtime command executed by agent.
- Outcome / remaining work: await version output or error; venv creation and remaining lab work pending. No commit or push.

### MEM-0040 - 2026-10-16T12:01:16+01:00 (Africa/Lagos)

- Request / evidence: learner confirms the expected Python 3.11.9 version result; no raw output supplied.
- Decisions / rationale: verify the selected interpreter executable next, maintaining one-step learner execution.
- Implementation / files: memory.md only; current checkpoint updated.
- Validation: read AGENTS.md and memory; accepted learner confirmation without running lab commands. Checked the saved memory update.
- Outcome / remaining work: await sys.executable output from py -3.11; project venv and remaining lab work pending. No commit or push.

### MEM-0041 - 2026-10-16T12:02:49+01:00 (Africa/Lagos)

- Request / evidence: learner supplied sanitized sys.executable output pointing to the per-user Python311 installation.
- Decisions / rationale: interpreter identity confirmed; recheck the project .venv path after the installation pause before environment creation.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted learner output and verified the saved memory text. No lab commands executed by agent.
- Outcome / remaining work: await Test-Path result for the repository .venv; environment creation and remaining lab work pending. No commit or push.

### MEM-0042 - 2026-10-16T12:04:43+01:00 (Africa/Lagos)

- Request / evidence: learner reports False for the explicit repository .venv path check.
- Decisions / rationale: proceed to create a project-local virtual environment with the verified Python 3.11 interpreter; use the absolute destination to avoid current-directory ambiguity.
- Implementation / files: memory.md only; checkpoint updated. Learner will execute environment creation.
- Validation: read AGENTS.md and memory; interpreted supplied result and verified saved memory content. No environment command executed by agent.
- Outcome / remaining work: await creation command completion or error, then verify the environment before activation. No commit or push.

### MEM-0043 - 2026-10-16T12:06:42+01:00 (Africa/Lagos)

- Request / evidence: learner reports environment creation done; no command output supplied.
- Decisions / rationale: verify the environment runtime directly before activation, including version, executable path, and differing prefixes.
- Implementation / files: memory.md only; current checkpoint updated.
- Validation: read AGENTS.md and memory; recorded learner report and checked saved memory content. No lab command executed by agent.
- Outcome / remaining work: await runtime diagnostic output; activation and remaining lab activities pending. No commit or push.

### MEM-0044 - 2026-10-16T12:08:39+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Python 3.11.9 64-bit, the project .venv executable path, and True for differing active/base prefixes.
- Decisions / rationale: runtime checks pass; guide activation in the current PowerShell session and await result before checking command resolution.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted all three supplied runtime results and verified saved memory content. No lab commands executed by agent.
- Outcome / remaining work: await Activate.ps1 outcome; command-resolution, pip, editor/kernel and remaining lab work pending. No commit or push.

### MEM-0045 - 2026-10-16T12:10:17+01:00 (Africa/Lagos)

- Request / evidence: learner supplied the (.venv) PowerShell prompt at the repository root after activation.
- Decisions / rationale: check sys.executable via the short python command; prompt appearance alone does not prove interpreter resolution.
- Implementation / files: memory.md only; checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied prompt and verified saved memory content. No lab commands executed by agent.
- Outcome / remaining work: await python executable path; pip, editor/kernel and remaining lab activities pending. No commit or push.

### MEM-0046 - 2026-10-16T12:13:27+01:00 (Africa/Lagos)

- Request: learner asks to continue the P0-U02 lab together.
- Decisions / rationale: resume at the MEM-0045 checkpoint. This entry was first written with a duplicate ID (MEM-0037) and a stale installer checkpoint from an outdated read of memory, then corrected. MEM-0036 also reflects that stale read and is superseded by MEM-0038 onward.
- Implementation / files: memory.md only.
- Validation: re-read AGENTS.md and memory. No lab commands, commit, or push by agent.
- Outcome / remaining work: await sys.executable output from the short python command inside the activated .venv; pip, editor/kernel and remaining lab activities pending.

### MEM-0047 - 2026-10-16T12:18:53+01:00 (Africa/Lagos)

- Request / evidence: learner confirmed their prediction and supplied sys.executable from the short python command: the project .venv/Scripts/python.exe.
- Decisions / rationale: activation changed command resolution as expected; proceed to the final Part B command, python -m pip --version, to show which pip belongs to the active interpreter.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; read Part B of the lab DOCX text. No lab commands executed by agent.
- Outcome / remaining work: await pip --version output; B1-B3 answers, Parts C-F pending. No commit or push.

### MEM-0048 - 2026-10-16T12:21:31+01:00 (Africa/Lagos)

- Request / evidence: learner confirmed prediction; pip 24.0 resolves from the project .venv site-packages for Python 3.11.
- Decisions / rationale: Part B commands complete; ask for the learner's own B1-B3 answers before Part C, without supplying model answers.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await B1-B3 answers; Parts C-F pending. Note: pip 24.0 is older than current releases; upgrading is not required by the lab and was not advised. No commit or push.

### MEM-0049 - 2026-10-16T12:28:43+01:00 (Africa/Lagos)

- Request / evidence: learner submitted written B1-B3 answers.
- Decisions / rationale: mentor review: B2 accurate; B1 states a conclusion without evidence; B3 half-complete. Request revisions without supplying model answers, per AGENTS.md section 2.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; reviewed answers against learner-supplied outputs. No lab commands executed by agent.
- Outcome / remaining work: await revised B1 and B3; Parts C-F pending. No commit or push.

### MEM-0050 - 2026-10-16T12:30:14+01:00 (Africa/Lagos)

- Request: learner declined B1/B3 revisions ("I know these things already") and asked to move to Part C.
- Decisions / rationale: learner's decision respected; B1/B3 recorded as incomplete for later evidence packaging. Part C begins with inspecting the requirements files before installing, as the lab instructs.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md, memory, Part C lab text, and both requirements files (comments only). No lab commands executed by agent.
- Outcome / remaining work: await learner inspection, prediction and install output. Open issue for Part D: ipykernel is undeclared. No commit or push.

### MEM-0051 - 2026-10-16T12:31:48+01:00 (Africa/Lagos)

- Request / evidence: learner pasted requirements file contents; the paste omits the first two comment lines of requirements.txt; no answers to the prediction questions.
- Decisions / rationale: point out the clipped paste; proceed to running the install, check and list commands with a brief prediction prompt, keeping pace with the learner.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; compared the paste with the repository files. No lab commands executed by agent.
- Outcome / remaining work: await install/check/list output; C1-C4 answers and Parts D-F pending. No commit or push.

### MEM-0052 - 2026-10-16T12:34:09+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Part C output: no installs, pip check clean, pip list shows pip 24.0 and setuptools 65.5.0, pip upgrade notices.
- Decisions / rationale: explain that pip/setuptools are bootstrapped by venv (relevant to C2); advise not upgrading pip just to silence the notice, per the lab's instruction and reproducibility. Request short C1-C4 answers.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await C1-C4; Part D needs ipykernel, which is undeclared; Parts D-F pending. No commit or push.

### MEM-0053 - 2026-10-16T12:37:23+01:00 (Africa/Lagos)

- Request: learner declined C1-C4 written answers and asked to move on.
- Decisions / rationale: learner's decision respected; C1-C4 recorded as skipped. Part D begins with VS Code interpreter selection, then a fresh integrated terminal check, before addressing the undeclared ipykernel.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md, memory, and Part D lab text; listed VS Code extensions (Python, Pylance, Jupyter present). No lab commands executed by agent.
- Outcome / remaining work: await interpreter selection and terminal sys.executable; ipykernel decision, notebook kernel check, D1-D3, Parts E-F pending. No commit or push.

### MEM-0054 - 2026-10-16T12:42:12+01:00 (Africa/Lagos)

- Request / evidence: learner pasted a fresh VS Code terminal transcript: automatic process-scoped execution-policy change and activation, then sys.executable at the project .venv python.exe.
- Decisions / rationale: terminal check passes; explain that the policy change is process-scoped only. Next run pip show ipykernel to confirm the kernel package is absent before any install decision.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied transcript. No lab commands executed by agent.
- Outcome / remaining work: await pip show ipykernel output; install decision, notebook kernel check, D1-D3, Parts E-F pending. No commit or push.

### MEM-0055 - 2026-10-16T12:43:48+01:00 (Africa/Lagos)

- Request / evidence: learner reports pip show ipykernel: WARNING: Package(s) not found: ipykernel.
- Decisions / rationale: install only ipykernel, via python -m pip in the activated .venv, as the lab permits; record the installed version. Defer declaring it in requirements-dev.txt until the version is known, as a documented decision.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await install output; requirements-dev decision, notebook kernel check, D1-D3, Parts E-F pending. No commit or push.

### MEM-0056 - 2026-10-16T12:47:42+01:00 (Africa/Lagos)

- Request / evidence: learner supplied install output: ipykernel 7.4.0 plus 26 transitive packages installed into .venv site-packages; pip show confirms location and direct requirements.
- Decisions / rationale: proceed to notebook kernel verification, the purpose of Part D. Recommend declaring ipykernel==7.4.0 in requirements-dev.txt after the kernel works, as a recorded decision; requirements file not changed yet. Notebook kept local and uncommitted because it will contain absolute local paths.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; read .gitignore (no scratch notebook path ignored); interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await notebook sys.executable/sys.version output; requirements-dev decision, D1-D3, Checkpoint D screenshot, Parts E-F pending. No commit or push.

### MEM-0057 - 2026-10-16T12:51:37+01:00 (Africa/Lagos)

- Request / evidence: learner pasted the notebook cell source, not its output. kernel_check.ipynb exists at the repo root but is 0 bytes on disk (unsaved), so no kernel or output evidence is available.
- Decisions / rationale: ask the learner to run the cell, save, and paste the printed output plus the kernel screenshot.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory; inspected kernel_check.ipynb size and attempted JSON parse (empty file). No lab commands executed by agent.
- Outcome / remaining work: await notebook output; checkpoint unchanged from MEM-0056. No commit or push.

### MEM-0058 - 2026-10-16T12:55:14+01:00 (Africa/Lagos)

- Request / evidence: learner supplied notebook output: .venv python.exe and Python 3.11.9 64-bit.
- Decisions / rationale: notebook and terminal interpreters match; drive-letter case difference is not a mismatch on Windows. Proceed to declaring the dependency: learner adds an exact pin of the direct dependency ipykernel==7.4.0 to requirements-dev.txt (transitive packages intentionally not pinned there).
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; compared notebook output with earlier terminal output. No lab commands executed by agent.
- Outcome / remaining work: await requirements-dev edit and verification output; kernel screenshot, D1-D3, Parts E-F pending. No commit or push.

### MEM-0059 - 2026-10-16T12:58:38+01:00 (Africa/Lagos)

- Request / evidence: learner edited requirements-dev.txt and supplied pip output (all requirements already satisfied, read from line 5).
- Decisions / rationale: declaration verified; flag the now-contradictory first comment for the learner to revise. Begin Part E1 with a safe construction outside the repository and the project .venv; diagnosis left to the learner per the lab's "no ready-made fix" rule.
- Implementation / files: memory.md only (requirements-dev.txt edited by learner, inspected by agent; git shows it modified and kernel_check.ipynb untracked).
- Validation: read AGENTS.md, memory, requirements-dev.txt, git status, and Part E lab text. No lab commands executed by agent.
- Outcome / remaining work: await E1 symptom output; kernel screenshot, D1-D3, E1-E4, Part F, and commit decisions pending. No commit or push.

### MEM-0060 - 2026-10-16T13:04:14+01:00 (Africa/Lagos)

- Request / evidence: learner ran the E1 setup; colorama installed into env-a; env-b import fails with ModuleNotFoundError; venv location warnings from the short 8.3 TEMP path.
- Decisions / rationale: symptom reproduced; explain the location warning as a path-alias artifact; hypotheses were not supplied, so request them with the learner's choice of cheapest check before giving diagnostics.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await E1 hypotheses and check; E2-E4, Part F, D screenshot/D1-D3 pending. Disposable venvs remain in the user temp folder for cleanup after Part E. No commit or push.

### MEM-0061 - 2026-10-16T13:08:13+01:00 (Africa/Lagos)

- Request / evidence: learner supplied two E1 hypotheses and chose python -m pip show PACKAGE as the cheapest check.
- Decisions / rationale: hypotheses accepted. Point out that bare python in the activated terminal targets the project .venv, so the check must name the failing interpreter explicitly; run it against env-b and env-a for contrast.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; reviewed learner reasoning. No lab commands executed by agent.
- Outcome / remaining work: await targeted pip show output; E1 fix/verification, E2-E4, Part F, D screenshot/D1-D3 pending. No commit or push.

### MEM-0062 - 2026-10-16T13:11:46+01:00 (Africa/Lagos)

- Request / evidence: learner gave predictions only: H2 means package present in the running environment but wrong import name; H1 means 'Package(s) not found'. No command output supplied.
- Decisions / rationale: predictions correct; H1 prediction needs to distinguish the two interpreters (env-b not found, env-a found at its own location). Ask for the actual outputs.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory; reviewed learner predictions. No lab commands executed by agent.
- Outcome / remaining work: await both pip show outputs; checkpoint unchanged from MEM-0061. No commit or push.

### MEM-0063 - 2026-10-16T13:13:54+01:00 (Africa/Lagos)

- Request / evidence: learner ran the pip show commands in a new terminal; PowerShell reported '\env-b\Scripts\python.exe' not recognized (same for env-a).
- Decisions / rationale: the error text shows $e1 expanded to empty because shell variables do not persist into new terminals; use it as a mini debugging example. Reset $e1 and rerun; no change to the environments needed.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory; interpreted supplied error. No lab commands executed by agent.
- Outcome / remaining work: await both pip show outputs after resetting $e1; checkpoint unchanged from MEM-0061. No commit or push.

### MEM-0064 - 2026-10-16T13:15:16+01:00 (Africa/Lagos)

- Request / evidence: env-b pip show: not found; env-a pip show: colorama 0.4.6 at env-a site-packages.
- Decisions / rationale: evidence contrast confirms H1 and excludes H2 in env-b; learner did not state the conclusion or fix, so ask them to choose and run the smallest fix themselves, with verification by rerunning the exact failing command.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied output. No lab commands executed by agent.
- Outcome / remaining work: await fix and verification; E1 lesson, E2-E4, Part F, D screenshot/D1-D3, temp venv cleanup pending. No commit or push.

### MEM-0065 - 2026-10-16T13:16:50+01:00 (Africa/Lagos)

- Request: learner asked "what should I do now?" after the E1 diagnosis.
- Decisions / rationale: learner was stuck on choosing the fix; provide scaffolded guidance with the concrete fix (install colorama into env-b via env-b's own interpreter) and its reasoning, then the unchanged verification command. Learner still writes the generalizable lesson.
- Implementation / files: memory.md only.
- Validation: read AGENTS.md and memory. No lab commands executed by agent.
- Outcome / remaining work: await fix and verification output plus one-sentence lesson; checkpoint unchanged from MEM-0064. No commit or push.

### MEM-0066 - 2026-10-16T13:21:24+01:00 (Africa/Lagos)

- Request / evidence: learner installed colorama into env-b with env-b's interpreter; verification printed 'import ok'; lesson submitted: 'always check things'.
- Decisions / rationale: E1 technically complete; lesson too vague to prevent the bug, so request a specific revision without supplying it. For E2, use kernel selection only (no uninstalls): nest_asyncio2 is present in .venv but absent from base Python 3.10, which already has ipykernel, so switching kernels reproduces the mismatch safely.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; agent ran read-only find_spec checks for ipykernel, nest_asyncio2 and colorama under py -3.10 and py -3.9. No lab steps performed by agent.
- Outcome / remaining work: await E1 lesson revision and E2 terminal/notebook outputs; E3-E4, Part F, D screenshot/D1-D3, temp venv cleanup pending. No commit or push.

### MEM-0067 - 2026-10-16T13:29:32+01:00 (Africa/Lagos)

- Request / evidence: terminal in .venv imports nest_asyncio2 and prints the .venv executable; notebook on the Python 3.10 kernel prints the base Python310 executable and fails with ModuleNotFoundError.
- Decisions / rationale: sys.executable evidence from both contexts supports the interpreter-mismatch hypothesis. Fix by kernel reselection only, then retest; ask the learner to name competing hypotheses (for example a stale kernel needing restart after install) that the evidence rules out. Advise sanitizing personal user-folder paths in recorded evidence.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md and memory; interpreted supplied outputs. No lab commands executed by agent.
- Outcome / remaining work: await E2 retest output; E1 lesson revision, E3-E4, Part F, D screenshot/D1-D3, temp venv cleanup pending. No commit or push.

### MEM-0068 - 2026-10-16T13:33:01+01:00 (Africa/Lagos)

- Request / evidence: learner supplied the E2 retest (.venv python.exe in the notebook) and asked to pass all remaining written work to finish the lab quickly.
- Decisions / rationale: learner's decision respected and recorded. All written answers and Part F documents are skipped, not completed; P0-U02 practical steps through E2 are done. Provide a single final batch: Part F evidence commands, cleanup of disposable artifacts, and the requirements-dev comment fix.
- Implementation / files: memory.md only; current-state checkpoint updated.
- Validation: read AGENTS.md, memory, and Part F lab text. No lab commands executed by agent.
- Outcome / remaining work: await Part F command output and cleanup confirmation; requirements-dev.txt commit decision pending; written evidence outstanding for any mentor review. No commit or push.

### MEM-0069 - 2026-10-16T13:40:57+01:00 (Africa/Lagos)

- Request / evidence: learner supplied Part F command output and ran the temp venv removal; deleted kernel_check.ipynb and edited the requirements-dev.txt comment.
- Decisions / rationale: P0-U02 lab practical work is finished. Written evidence remains skipped and is recorded as outstanding, not complete. Do not commit without the learner's explicit go-ahead.
- Implementation / files: memory.md only (requirements-dev.txt edited by learner, inspected by agent).
- Validation: read AGENTS.md and memory; agent confirmed the temp folder and notebook no longer exist, read requirements-dev.txt, and checked git status (memory.md and requirements-dev.txt modified; P0-U02 DOCX files, a Word lock file and recommended-books untracked).
- Outcome / remaining work: commit decision for requirements-dev.txt; optional tidy of its second comment line; written answers, environment_report.md and reconstruction_notes.md for mentor review; P0-U02 teach-back slides and assessment per the unit sequence. No commit or push.

### MEM-0070 - 2026-10-16T14:27:41+01:00 (Africa/Lagos)

- Request: learner asked the agent to check and complete everything left so a mentor can confirm P0-U02 readiness, gave the remote URL, and asked for a teach-back slide draft under 10 pages.
- Decisions / rationale: the learner explicitly asked for completion, so AGENTS.md section 2 permits drafting. Every draft carries an authorship note (trainee-run evidence, AI-drafted prose, trainee review pending) so the mentor can weigh it honestly. Mentor review, assessment authoring and the readiness decision were not performed, because they are the mentor's role. Files placed per the phase guide (P0-U02 evidence in research-notes/) and left uncommitted per the lab.
- Implementation / files: new research-notes/phase-0/P0-U02/answers.md, environment_report.md, command_log.txt, reconstruction_notes.md; new slides/phase-0/P0-U02_research_computing_environment_Daniel.md and three SVGs in slides/phase-0/assets/P0-U02/. requirements-dev.txt: learner had already removed the stale second comment; agent made no net change.
- Validation: git fetch showed main level with origin/main at 8e5a7d4. Agent rebuilt a disposable venv from both requirements files with py -3.11: pip check clean, ipykernel 7.4.0 imports, pip freeze byte-identical to the project .venv (28 packages). E4 pathlib example tested from two working directories. SVGs parsed as XML and rendered with headless Chrome and visually inspected. The Marp deck could NOT be rendered (no Node/Marp CLI; headless Chrome failed to load marp-core from the CDN), so its layout is unverified. Redaction checked: no username fragments in new files; pronoun check done.
- Outcome / remaining work: trainee review and rewording of drafts and slides; kernel screenshot; P0-U02 reflection; preview deck in Marp for VS Code (extension not installed); P0-U02 assessment and mentor review; commit/publish decision. Correction to MEM-0056 and MEM-0059: 28 installed packages, not 27. No commit or push.

### MEM-0071 - 2026-10-16T15:06:18+01:00 (Africa/Lagos)

- Request: learner reports reviewing the drafts and accepting the wording; asks why the agent said it could not build slides when Claude has built slides for them before.
- Decisions / rationale: update review-status notes to record the learner's acceptance while keeping the AI-drafting disclosure. Clarify that the deck was built (Marp Markdown source, as AGENTS.md requires); only local rendering/preview failed, due to missing Node/Marp tooling here. Other Claude surfaces build slides with different tools (PowerPoint files or hosted slide artifacts).
- Implementation / files: answers.md, environment_report.md, and the deck's opening comment updated; memory.md.
- Validation: read AGENTS.md and memory; grep confirmed the three updated notes.
- Outcome / remaining work: Checkpoint D screenshot, P0-U02 reflection, assessment, mentor review, Marp preview, and commit decision remain. No commit or push.

### MEM-0072 - 2026-10-16T15:14:49+01:00 (Africa/Lagos)

- Request: push the present update to GitHub; explain the Checkpoint D kernel screenshot.
- Decisions / rationale: the learner's explicit request overrides the lab's default of not committing evidence automatically. Follow the established practice of committing to main and pushing to origin; no gh CLI is available for a PR. Split into focused commits (dependency pin, unit materials, evidence package, teach-back deck, memory). Exclude resources/recommended-books (book PDFs stay local) and the ~$ Word lock file.
- Implementation / files: requirements-dev.txt; lecture-notes/phase-0 and labs/phase-0 P0-U02 DOCX; research-notes/phase-0/P0-U02/; slides/phase-0 deck and assets/P0-U02; memory.md.
- Validation: git fetch showed main level with origin/main before committing; privacy grep found no username, email or machine identifiers in the published text files; DOCX files are about 43 KB each. Push verification is recorded in the next entry.
- Outcome / remaining work: Checkpoint D kernel screenshot explained to the learner; screenshot, reflection, assessment and mentor review remain.

### MEM-0073 - 2026-10-16T15:15:04+01:00 (Africa/Lagos)

- Request / evidence: verification of the MEM-0072 publication.
- Decisions / rationale: record verified push state separately, since the publishing commit could not contain its own verification.
- Implementation / files: memory.md only (uncommitted).
- Validation: git fetch; local HEAD and origin/main both c7014e3 (commits dcbf635, 85c25eb, fefa8eb, a74a34f, c7014e3 on top of 8e5a7d4).
- Outcome / remaining work: published. Checkpoint D screenshot, P0-U02 reflection, assessment and mentor review remain. This entry is not yet pushed.

### MEM-0074 - 2026-10-16T15:22:59+01:00 (Africa/Lagos)

- Request: learner saved the Checkpoint D screenshot; stated that P0-U02 needs no separate assessment because the lab serves as the assessment; asked the agent to develop a reflection from their themes (improved troubleshooting; understanding different environments and how they work), delete the kernel check notebook, and push.
- Decisions / rationale: the owner's assessment decision is recorded in the current state. AGENTS.md was not changed, because its unit sequence is a typical pattern, not a rule. The reflection is written in first person, cites only events from the session record, and carries an AI-assistance note. The screenshot was visually checked: it shows the .venv (3.11.9) kernel and the .venv path, with no username.
- Implementation / files: new research-notes/phase-0/P0-U02/P0-U02_research_reflection_Daniel.md and checkpoint-d-kernel.png; answers.md links the screenshot and drops it from the F1 unverified list; deleted the untracked resources/recommended-books/Phase-0-researcher-setup/kernel_check.ipynb (never committed).
- Validation: read AGENTS.md and memory; inspected the screenshot; confirmed the notebook removal. Push verification is in git history (memory commit on origin/main).
- Outcome / remaining work: P0-U02 mentor review and readiness decision; P0-U03 next after that.

### MEM-0075 - 2026-10-16T16:06:17+01:00 (Africa/Lagos)

- Request: update the remote repository.
- Evidence observed: new local changes by the owner: P0-U02 mentor review (READY / COMPLETE), a rendered P0-U02 PDF deck, deletion of the Marp deck source, and P0-U03 lecture and lab DOCX.
- Decisions / rationale: publish the owner's changes as made. Flag that deleting the Marp source conflicts with AGENTS.md section 4, which makes Marp Markdown canonical and PDF an export, and that the mentor review cites that source; it stays recoverable from a74a34f. resources/recommended-books stays local.
- Implementation / files: commits for the mentor review, the deck swap, the P0-U03 materials, and memory; current state updated to resume at P0-U03.
- Validation: read AGENTS.md and memory; read the mentor review; privacy scan of the review and PDF bytes found no username or email; checked file sizes. Push verified by matching local HEAD and origin/main.
- Outcome / remaining work: P0-U03 begins. Open item: decide whether to restore the Marp source alongside the PDF and remove or keep the orphaned SVG assets.
