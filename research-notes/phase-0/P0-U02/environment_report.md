# P0-U02 Environment Report

**Lab:** P0-U02-LAB-001
**Trainee:** Daniel Oyewale
**Recorded:** 2026-10-16, from command output the trainee ran during the lab. Personal paths are redacted as `<user>`.
**Authorship:** compiled by an AI assistant (Claude) from the trainee's evidence; reviewed and accepted by the trainee on 2026-10-16.

## Environment

| Item | Value | Source |
| --- | --- | --- |
| Repository | `https://github.com/Engr-Daniel/Ormedian_Medical_ReliableAI` | lab instructions |
| Commit | `8e5a7d4d52bdbd8b9f47edd4b25998a43e2d1c7e` | `git rev-parse HEAD` |
| Uncommitted changes at test time | `memory.md`; `requirements-dev.txt` (ipykernel pin added during the lab) | `git status` |
| Platform | `Windows-10-10.0.19044-SP0` | `platform.platform()` |
| Shell | Windows PowerShell 5.1, in the VS Code integrated terminal | session |
| Python | `3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)]` | `sys.version` |
| Interpreter | `<repo>\.venv\Scripts\python.exe` | `sys.executable` |
| Base interpreter | Python 3.11.9 per-user install, `C:\Users\<user>\AppData\Local\Programs\Python\Python311` | installer destination |
| Environment manager | built-in `venv`, created with `py -3.11 -m venv .venv` | session |
| pip | 24.0, from `.venv\Lib\site-packages\pip` | `python -m pip --version` |
| Direct dependencies | `requirements.txt`: none. `requirements-dev.txt`: `ipykernel==7.4.0` | file contents |
| Installed packages | 28 (see snapshot below) | `python -m pip freeze` |
| Dependency consistency | `No broken requirements found.` | `python -m pip check` |
| VS Code interpreter | `.venv`, via "Python: Select Interpreter"; new terminals auto-activate it | new-terminal `sys.executable` |
| Jupyter kernel | `.venv` interpreter selected directly in VS Code; no `--user` kernelspec registered | notebook `sys.executable` |
| Hardware | Not recorded. Not relevant to this lab, which ran no computations. | — |
| Random seed | Not applicable. Nothing random was run. | — |

## Other interpreters on this machine

These are recorded because they cause the mismatch failures demonstrated in Part E.

| Interpreter | How it is reached | Notes |
| --- | --- | --- |
| Python 3.10.0, 64-bit, per-user | bare `python` outside `.venv`; `py` default | first on `PATH`; has `ipykernel`, so it can appear as a notebook kernel |
| Anaconda Python 3.9, 64-bit | `py -3.9` | registered with the launcher, not on `PATH` |
| Python 3.11.9, 64-bit, per-user | `py -3.11` | installed for this lab without adding it to `PATH` |

## Installation deviations and decisions

1. **Python 3.11.9 was installed.** No Python 3.11 existed before the lab. Installer choices:
   - "Add python.exe to PATH" left unchecked, so the default `python` stayed 3.10;
   - the standard-library test suite left out;
   - file associations turned off;
   - "precompile standard library" turned on.
2. **`ipykernel==7.4.0` was added** to `requirements-dev.txt`. The lab needed a notebook kernel, and no requirements file declared one. Only the direct dependency is pinned; its 27 transitive dependencies are recorded in the snapshot below instead.
3. **pip was not upgraded.** pip suggested upgrading 24.0 to 26.2.1. The environment was kept as `venv` created it.
4. **No kernelspec was registered.** `python -m ipykernel install --user` was not run, because VS Code selected the `.venv` interpreter directly.
5. **Activation used a temporary script permission.** VS Code ran `Set-ExecutionPolicy -Scope Process RemoteSigned` before activating. This lasts for one terminal process only, and no machine-wide policy changed.

## Environment snapshot (`python -m pip freeze`, 2026-10-16)

```text
asttokens==3.0.2
colorama==0.4.6
comm==0.2.3
debugpy==1.8.22
executing==2.3.0
ipykernel==7.4.0
ipython==9.17.1
ipython_pygments_lexers==1.1.1
jedi==0.20.1
jupyter_client==8.10.0
jupyter_core==5.9.1
matplotlib-inline==0.2.2
nest-asyncio2==1.7.4
packaging==26.3
parso==0.8.7
platformdirs==4.13.3
prompt_toolkit==3.0.53
psutil==7.2.2
pure_eval==0.2.4
Pygments==2.21.0
python-dateutil==2.9.0.post0
pyzmq==27.2.0
six==1.17.0
stack-data==0.6.3
tornado==6.5.10
traitlets==5.16.1
typing_extensions==4.16.0
wcwidth==0.9.2
```

The trainee's pasted copy of this output was missing the `pyzmq==27.2.0` line. A direct read of the project `.venv` confirms `pyzmq` is installed, so the list above is complete. `pip` and `setuptools` are installed but `pip freeze` leaves them out by default.

## Rebuild check

On 2026-10-16, the assistant rebuilt a disposable environment outside the repository, on the same machine:
1. Created it with `py -3.11 -m venv`.
2. Installed `requirements.txt`, then `requirements-dev.txt`.
3. Ran `pip check`, which reported no broken requirements.
4. Imported `ipykernel`, which reported version 7.4.0.
5. Compared its `pip freeze` with the project `.venv`. The two were byte-for-byte identical.

Rebuilds on other machines, operating systems, or later dates have not been tested. Because the 27 transitive packages are not pinned, a later rebuild from the requirements files alone may pick up newer versions. Use the snapshot above when an exact match matters.
