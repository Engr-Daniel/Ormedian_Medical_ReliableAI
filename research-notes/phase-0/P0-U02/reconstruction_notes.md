# Rebuilding the Project Environment (P0-U02)

These steps are for a new collaborator rebuilding the Ormedian_Medical_ReliableAI Python environment on Windows, without asking anyone.
They were tested on 2026-10-16 on Windows 10 with Python 3.11.9, using a disposable environment. The result matched the trainee's working environment exactly.
Other operating systems are not yet tested; shell equivalents are noted where they differ.

## 1. Get the code

```powershell
git clone https://github.com/Engr-Daniel/Ormedian_Medical_ReliableAI.git
cd Ormedian_Medical_ReliableAI
git rev-parse HEAD   # record this commit in your own environment report
```

## 2. Make sure Python 3.11 is available

```powershell
py -0p
```

- **If no 3.11 entry is listed:** install Python 3.11 64-bit from python.org. Version 3.11.9 was tested. Choose the standard Windows installer, not the "embeddable" zip.
- **"Add python.exe to PATH" is optional.** The steps below call Python 3.11 through the `py` launcher, so they work even when another version is your default `python`.

## 3. Create the environment

From the repository root:

```powershell
Test-Path .venv          # if True, inspect it before replacing it; do not delete it blindly
py -3.11 -m venv .venv
```

On macOS or Linux, use `python3.11 -m venv .venv`.

## 4. Activate it

```powershell
.venv\Scripts\Activate.ps1
```

- **If PowerShell blocks the script,** don't change the machine-wide policy. Either run the line below, which affects this terminal only, or skip activation and call `.venv\Scripts\python.exe` directly:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

- **On macOS or Linux,** activate with `source .venv/bin/activate`.

## 5. Install dependencies

Install both files. `requirements-dev.txt` does not pull in `requirements.txt`.

```powershell
python -m pip install -r requirements.txt
python -m pip install -r requirements-dev.txt
python -m pip check
```

- **`python -m pip` vs `pip`:** `python -m pip` guarantees that pip installs into the same interpreter that `python` runs.
- **Exact versions:** to copy the trainee's environment exactly, compare `python -m pip freeze` with the snapshot in [environment_report.md](environment_report.md).

## 6. Verify

```powershell
python -c "import sys; print(sys.executable); print(sys.version); print(sys.prefix != sys.base_prefix)"
python -m pip --version
python -m pip show ipykernel
```

Expected results:
- the path ends in `.venv\Scripts\python.exe`;
- the version starts with `3.11`;
- the third line prints `True`;
- pip reports a location inside `.venv`;
- `ipykernel` reports version 7.4.0.

## 7. Connect VS Code and notebooks

1. In VS Code, run **Python: Select Interpreter** and choose the `.venv` entry.
2. Open a **new** terminal and rerun the first command from step 6. It should print the `.venv` path without you activating anything.
3. In a notebook, choose **Select Kernel**, then **Python Environments**, then `.venv`. Run:

```python
import sys
print(sys.executable)
print(sys.version)
```

The path must match the terminal's.

## Known pitfalls

- **The `py` launcher's default may not be 3.11.** It can be another version, such as 3.10. Always use `py -3.11`.
- **A package imports in the terminal but fails in a notebook.** Print `sys.executable` in the notebook first. A kernel pointing at another interpreter is the usual cause.
- **"Actual environment location may have moved" warning.** This appears when a path contains a space and Windows uses a short alias such as `NAME~1`. It is harmless.
- **Shell variables don't carry over.** A new terminal does not keep variables set in an older one.
- **Don't commit `.venv`, notebook outputs that contain personal paths, or Jupyter kernel specs.** These hold absolute local paths. `.venv/` is already in `.gitignore`.
