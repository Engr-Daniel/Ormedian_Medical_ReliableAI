# P0-U02 Lab Answers: Research Environment Setup, Verification and Troubleshooting

**Lab:** P0-U02-LAB-001
**Unit:** P0-U02 Research Computing Environment
**Trainee:** Daniel Oyewale
**Lab sessions:** 2026-10-15 (Part A) and 2026-10-16 (Parts A to F)

> **Authorship note for the mentor.**
> The trainee ran every command and supplied every output quoted here, during a guided session with an AI assistant (Claude).
> At the trainee's request, the assistant drafted the written answers from that evidence. The trainee gave short answers of their own for A3, B2, B3 and the E1 hypotheses, and those ideas are kept.
> **Trainee review:** completed 2026-10-16. The trainee reviewed the draft and accepted the wording without changes. The mentor may still want to probe these explanations orally.

Related files: [environment report](environment_report.md), [command log](command_log.txt), [reconstruction notes](reconstruction_notes.md).
Personal paths are redacted as `<user>`.

---

## Part A: Baseline environment inspection

**A1. Which interpreter did `python` resolve to before activation?**
The base Python 3.10.0 per-user installation:
`C:\Users\<user>\AppData\Local\Programs\Python\Python310\python.exe`.
`sys.executable` printed this path, and `python --version` returned `Python 3.10.0`. `where.exe python` also listed it first.

**A2. Does the terminal currently point to a virtual environment? What evidence supports your answer?**
No. Three pieces of evidence agree:
- `sys.prefix` and `sys.base_prefix` were identical, which is what a base installation reports.
- `Test-Path .venv` returned `False`, so no project environment existed yet.
- The prompt had no `(.venv)` prefix. This is the weakest of the three, because the prompt is cosmetic.

**A3. How do the outputs of `py -0p` and `where.exe python` differ in meaning?**
- `py -0p` lists the interpreters registered with the Windows Python launcher. It showed Python 3.10 as the default and Anaconda Python 3.9. It is not a complete inventory of every Python on the machine, and it does not say what the bare `python` command runs.
- `where.exe python` lists files named `python.exe` in the order the shell would search for them along `PATH`. It showed the Python310 executable first and the WindowsApps alias second. These are candidates, not proof of what actually ran.
- Only `sys.executable`, printed from inside the running process, proves which interpreter ran. That is why A1 relies on it.

**A4. What is the repository commit identifier? Why is it relevant to reproducibility?**
`8e5a7d4`, in full `8e5a7d4d52bdbd8b9f47edd4b25998a43e2d1c7e`.
The commit fixes exactly which code, configuration and dependency files were used. An environment report or result is only meaningful when tied to a revision.
Limitation: the working tree also had uncommitted changes. These were `memory.md`, and later the `requirements-dev.txt` edit made in Part D. The SHA alone therefore does not fully describe the state that was tested.

---

## Part B: Create and verify the project environment

Setup actions:
- Python 3.11.9 (64-bit) was installed per-user with "Add python.exe to PATH" left unchecked. This left the existing Python 3.10 and Anaconda installations and the default `python` command unchanged.
- `.venv` was confirmed absent both before and after installation, then created with `py -3.11 -m venv .venv`.

**B1. What evidence proves your selected interpreter belongs to `.venv`?**

| Check | Observed output | What it proves |
| --- | --- | --- |
| `.venv\Scripts\python.exe`, running `sys.executable` and `sys.version` | `...\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe`, Python 3.11.9 64-bit | The environment's own interpreter runs and is version 3.11.9 |
| `sys.prefix != sys.base_prefix` | `True` | The process is inside a virtual environment, not a base install |
| `python -c "import sys; print(sys.executable)"` after activation | `C:\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe` | The bare `python` command now resolves to `.venv` |
| `python -m pip --version` | `pip 24.0 from C:\Ormedian_Medical_ReliableAI\.venv\Lib\site-packages\pip (python 3.11)` | Installs go into `.venv`, not into a base installation |

**B2. How does `sys.prefix` differ from `sys.base_prefix` in a virtual environment?**
`sys.prefix` points to the environment currently in use, which is the project's `.venv` folder. `sys.base_prefix` points to the base Python installation the environment was created from.
In Part A, outside any environment, the two were equal. Inside `.venv`, the comparison `sys.prefix != sys.base_prefix` returned `True`.
The individual `base_prefix` value was not printed. It is expected to be the per-user Python311 folder, but that was not directly observed.

**B3. What does activation change, and why can direct interpreter invocation work without activation?**
- **Activation** changes only the current shell session. It puts `.venv\Scripts` first on `PATH`, so the bare `python` and `pip` commands find the environment's copies first. It also sets `VIRTUAL_ENV`, changes the prompt, and defines `deactivate`. It does not install anything or change the interpreter itself.
- **Direct invocation** works without activation because typing a full path skips the `PATH` search altogether. When `.venv\Scripts\python.exe` starts, it reads the `pyvenv.cfg` file next to it and sets `sys.prefix` to `.venv` by itself. That is why the direct check in B1 reported the environment before any activation.
- **Execution policy:** in VS Code, activation ran after `Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned`. That change lasts only for that terminal process, and no machine-wide policy was changed.

---

## Part C: Dependency inspection and installation

**C1. Which dependencies are directly declared by the project?**
- `requirements.txt` contains comments only, so it declares no runtime dependencies.
- `requirements-dev.txt` originally contained comments only. During Part D, `ipykernel==7.4.0` was added, so it is now the only directly declared dependency.
- `requirements-dev.txt` does **not** include `-r requirements.txt`, so the two files must be installed separately.

**C2. Which installed packages appear to be transitive? How can you tell?**
- **Before `ipykernel`:** `pip list` showed only `pip 24.0` and `setuptools 65.5.0`. Neither is a declared or transitive dependency. `venv` installs them when it creates the environment, from the copies bundled with Python.
- **After `ipykernel`:** all 27 other installed packages are transitive.
  - The `Requires` line of `pip show ipykernel` lists 11 direct requirements, including `comm`, `debugpy`, `ipython`, `jupyter-client`, `pyzmq` and `tornado`.
  - The install log shows deeper chains such as `(from jedi>=0.18.2->ipython>=7.23.1->ipykernel)` and `(from python-dateutil>=2.8.2->jupyter-client>=8.9.0->ipykernel)`.
  - Nothing other than `ipykernel` was requested by name.

**C3. Does `pip check` report a dependency conflict? Include its actual output.**
No. Both runs returned:

```
No broken requirements found.
```

The first run, in Part C, covered only pip and setuptools. The second, in Part F, covered all 28 packages after the `ipykernel` install.
`pip check` compares installed versions against the requirements each package declares. It does not prove the packages work correctly at runtime.

**C4. Why is `pip freeze` useful as a snapshot but insufficient as the sole dependency design?**
- **Useful:** it records the exact version of every installed package. The 28 lines in Part F are enough to rebuild this environment exactly.
- **Insufficient on its own:**
  - It mixes the one package the project chose (`ipykernel`) with the 27 that came with it, so the intent is lost.
  - Nobody can tell which pins are safe to upgrade.
  - It records accidental installs as if they were requirements.
  - It leaves out `pip`, `setuptools` and the Python version itself.
- **Design used here:** the requirements files record intent, meaning the direct dependencies with pinned versions. A freeze file records state, meaning everything that was installed. A reproducible project needs both.

---

## Part D: VS Code and Jupyter interpreter verification

Steps:
1. **Interpreter selection:** `.venv` was selected with "Python: Select Interpreter".
2. **New terminal:** a newly opened integrated terminal auto-activated `.venv`, and `sys.executable` returned `C:\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe`.
3. **Kernel package:** `pip show ipykernel` returned `WARNING: Package(s) not found: ipykernel`. The trainee installed it with `python -m pip install ipykernel`, which gave version 7.4.0 in `.venv\Lib\site-packages`. The pin was then recorded in `requirements-dev.txt`.
4. **Notebook check:** a local, uncommitted `kernel_check.ipynb` was run with the `.venv` kernel, then deleted after the lab.
5. **Kernel registration:** `python -m ipykernel install --user ...` was **not** run, because VS Code could select the `.venv` interpreter directly. No user-level Jupyter kernel specification was created.

**D1. Does notebook `sys.executable` match the terminal interpreter?**
Yes. The notebook printed `c:\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe` and `3.11.9 (tags/v3.11.9:de54cf5, ...) [MSC v.1938 64 bit (AMD64)]`.
The terminal printed the same path with an uppercase `C:`. Windows paths are case-insensitive, so both name the same file. A plain string comparison in code would wrongly report a mismatch.

**D2. What is the distinction between a Jupyter frontend and a kernel?**
The frontend is the interface, here the VS Code notebook editor. It shows cells and outputs and sends code to be run.
The kernel is a separate process that actually runs the code. Here it is the `.venv` interpreter running `ipykernel`.
Which packages a notebook can import depends on the kernel's interpreter, not on the frontend. E2 demonstrates this.

**D3. Which evidence would demonstrate that the notebook is using the wrong interpreter?**
- **Strongest:** `sys.executable` printed inside a notebook cell points outside `.venv`. In E2 it showed the base Python310 interpreter.
- **Supporting:** `sys.version` is not 3.11.9, the kernel name at the top right is not `.venv`, or an import that works in the `.venv` terminal fails in the notebook.
- The kernel label alone is weaker than `sys.executable`, because a label is just a display name.

**Checkpoint D screenshot:** not yet supplied. *Trainee to add a screenshot of the selected `.venv` kernel.*

---

## Part E: Independent troubleshooting challenges

### E1: Package present, import fails

| Field | Record |
| --- | --- |
| Challenge ID | E1 |
| Setup | Two disposable Python 3.11 environments under `%TEMP%\p0u02-e1`; `colorama` installed into `env-a` only. The project `.venv` was not touched. |
| Observed symptom | `env-a`: `Successfully installed colorama-0.4.6`. `env-b`: `ModuleNotFoundError: No module named 'colorama'` |
| Execution context | `env-b\Scripts\python.exe`, run directly |
| Hypothesis 1 | The package was installed for a different interpreter from the one running the import |
| Hypothesis 2 | The installed distribution name differs from the import name, as with `scikit-learn` and `sklearn` |
| Cheapest diagnostic test | `pip show colorama`, run through **each** interpreter explicitly. Bare `python -m pip show` would have queried the activated project `.venv`, which is the same mistake under investigation. |
| Actual evidence | `env-b`: `WARNING: Package(s) not found: colorama`. `env-a`: `colorama 0.4.6`, Location `...\p0u02-e1\env-a\Lib\site-packages` |
| Interpretation | `env-a` owns the package, and the failing interpreter `env-b` does not have it. Hypothesis 1 is supported. Hypothesis 2 is rejected for `env-b`, because there is no installed package whose import name could differ. |
| Minimal correction | `& "$e1\env-b\Scripts\python.exe" -m pip install colorama` installs only into the failing environment |
| Retest result | The unchanged original command printed `import ok` |
| Remaining uncertainty | The scenario was constructed, so its cause was known in advance. Real cases may also involve a local file shadowing the module, or a different `sys.path`. |
| Lesson for future research | Before reinstalling anything, print `sys.executable` in the failing context and query packages through that same interpreter with `python -m pip`. |

Incidental observations:
- **Lost variable:** in a new terminal, `$e1` was empty, so the command path became `\env-b\Scripts\python.exe` and PowerShell could not find it. Shell variables do not carry over between sessions. Commands that rely on hidden state from an earlier session are not reproducible.
- **Path warnings:** `venv` warned "Actual environment location may have moved". `%TEMP%` uses a short alias of the user folder, ending in `~1`, because the Windows username contains a space. Both spellings name the same folder.

### E2: Terminal works, notebook fails

The mismatch was reproduced by switching the kernel only, without uninstalling anything. `nest_asyncio2` is installed in `.venv` as a dependency of `ipykernel`. The base Python 3.10 can serve as a kernel but does not have `nest_asyncio2`.

| Context | Interpreter (`sys.executable`) | `import nest_asyncio2` |
| --- | --- | --- |
| `.venv` terminal | `C:\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe` | `import ok` |
| Notebook, Python 3.10 kernel | `c:\Users\<user>\AppData\Local\Programs\Python\Python310\python.exe` | `ModuleNotFoundError: No module named 'nest_asyncio2'` |
| Notebook after the fix, `.venv` kernel | `c:\Ormedian_Medical_ReliableAI\.venv\Scripts\python.exe` | No error reported |

- **Competing hypotheses:**
  1. The notebook kernel uses a different interpreter.
  2. The kernel is stale: it started before the package was installed and needs a restart.
  3. Something in the notebook's working directory shadows the module.
- **Conclusion:** the notebook printed `sys.executable` *before* the import, so the failure left its evidence behind. The kernel interpreter was not `.venv`, which supports hypothesis 1. Hypothesis 2 is rejected, because restarting a Python 3.10 kernel cannot make a `.venv`-only package appear, and `nest_asyncio2` was installed long before. Hypothesis 3 was not needed to explain the evidence.
- **Fix and retest:** switching the kernel back to `.venv` and rerunning the same cell printed the `.venv` interpreter, with no error reported.

### E3: An incomplete reproducibility claim

Claim: "Python 3.11, seed 42, AUROC 0.82."
This names one language version, one seed and one number. It identifies neither the data, nor the code, nor the model, nor how the metric was computed.

Missing evidence, in priority order:
1. **Data and split.** Dataset name and version, which test set, and the split procedure. For medical imaging this means whether the split was at patient or study level. Without this, it isn't known what was evaluated, and leakage cannot be ruled out.
2. **Code revision.** The commit SHA, plus any uncommitted changes.
3. **Model weights.** The exact checkpoint, the pretrained source, and the rule for choosing the checkpoint, such as last epoch or best validation score.
4. **Evaluation protocol.** The positive class, how AUROC was computed and with which library, the number of test cases, the prevalence, and a confidence interval. AUROC 0.82 with no interval or sample size cannot be compared with anything.
5. **Preprocessing.** Resizing, normalization, intensity handling and augmentation, together with the library versions that implement them.
6. **Dependencies.** The requirements files plus a freeze snapshot, and the full Python patch version, since "3.11" is not 3.11.9.
7. **Hardware and numerics.** The CPU or GPU model, the CUDA and cuDNN versions, and the determinism settings.
8. **Randomness and variance.** Which libraries the seed covered (Python, NumPy, PyTorch, data loader workers), and how many runs or seeds were used. One seed gives no measure of run-to-run variation.

**E3 answer.**
- **Essential for reproducing the run:** items 1 to 6.
- **Most likely to explain a discrepancy** between this 0.82 and someone else's result:
  - a different split or test population, including prevalence or case mix;
  - a different checkpoint selection;
  - preprocessing library versions;
  - nondeterministic GPU operations;
  - ordinary seed-to-seed variance, which a single run cannot measure.

### E4: Portable paths

```python
"""Write a small summary file to a project-relative results directory."""
from pathlib import Path

# This file lives in <project>/scripts/, so the project root is one level up.
PROJECT_ROOT = Path(__file__).resolve().parents[1]
RESULTS_DIR = PROJECT_ROOT / "results" / "p0-u02-e4-demo"


def main() -> None:
    RESULTS_DIR.mkdir(parents=True, exist_ok=True)
    output_path = RESULTS_DIR / "summary.txt"
    output_path.write_text("environment check: ok\n", encoding="utf-8")
    print(f"current working directory: {Path.cwd()}")
    print(f"wrote: {output_path.relative_to(PROJECT_ROOT)}")


if __name__ == "__main__":
    main()
```

**How it was verified.** The assistant ran this example in a disposable folder outside the repository, not as part of the trainee's lab session. It was run from two different working directories. Both runs wrote `results\p0-u02-e4-demo\summary.txt` under the same project root. No real data file was touched.

**Why it is portable.**
- The path is built from the script's own location, not from `C:\Users\<user>\...`.
- It also doesn't depend on the folder you happen to run it from.
- `pathlib` chooses the correct path separator for each operating system.

**Notebooks differ.** Notebook cells have no `__file__`. Their working directory is usually the notebook's own folder, which can be changed in settings, and not the repository root. The same relative path can therefore point somewhere else from a notebook than from a script. Make the root explicit in notebooks, for example by searching upward for a known marker such as the `.git` folder.

**Assumptions that remain:**
- The script stays exactly one level below the root, because `parents[1]` depends on that.
- The results folder is writable.
- Collaborators keep the same folder layout.
- Data that lives outside the repository will still need a configured location, such as an environment variable or a configuration file, rather than a hard-coded path.

---

## Part F: Reproducibility evidence and reconstruction

**F1. What did you verify directly? What remains unverified?**

Verified by the trainee's own commands:
- the commit;
- the platform, `Windows-10-10.0.19044-SP0`;
- Python 3.11.9 64-bit running from `.venv`;
- `pip` belonging to `.venv`;
- the VS Code terminal and the notebook kernel both resolving to `.venv`;
- a clean `pip check`;
- the full `pip freeze`.

Verified by the assistant on the same machine:
- Rebuilding a disposable environment from `requirements.txt` and `requirements-dev.txt` with `py -3.11` produced a `pip freeze` **identical** to the project `.venv`, with 28 packages. `pip check` was clean, and `ipykernel` 7.4.0 imported.

Unverified:
- a rebuild on a different machine, operating system or network;
- a rebuild with a Python 3.11 patch version other than 3.11.9;
- the VS Code status-bar interpreter, which was not reported;
- the kernel-selection screenshot, still pending;
- kernel registration with `ipykernel install --user`, which was not performed;
- behaviour after upgrading `pip` from 24.0.

**F2. What would another researcher need to reconstruct the environment without contacting you?**
- **Source:** the repository URL and commit.
- **Python:** Python 3.11, with 3.11.9 64-bit tested, and how to call it on Windows (`py -3.11`) when another version is the default.
- **Environment:** the exact `venv` creation and activation commands.
- **Dependencies:** both requirements files, installed separately, plus the freeze snapshot for an exact match.
- **Editor:** VS Code interpreter and kernel selection steps.
- **Verification:** the commands to check the result, with the expected outputs.
- **Known pitfalls:** PowerShell execution policy, Python 3.10 being the launcher default, and the space in the username.

All of this is written up in [reconstruction_notes.md](reconstruction_notes.md).

**F3. Which aspects of an environment can still vary even when dependencies and seeds are recorded?**
- **Python and platform:** the Python patch version, how Python was built, the operating system version, and file-system behaviour. Examples seen in this lab are case-insensitive paths and the short `~1` alias of the user folder.
- **Hardware and drivers:** the CPU or GPU model, drivers, CUDA and cuDNN, and the numerical libraries such as BLAS, which affect floating-point results.
- **Thread count and nondeterminism:** the number of threads used, and GPU operations that are nondeterministic by design.
- **Locale and encoding:** while preparing these notes, a script under the base Python 3.10 failed with `UnicodeEncodeError` on the Windows `cp1252` console encoding.
- **Environment variables and shell state:** for example, the lost `$e1` variable in E1.
- **Package availability over time:** a new install can pick up different versions of anything not pinned, and packages can be removed from the index.
- **Data and preprocessing versions:** even when the code is unchanged.
