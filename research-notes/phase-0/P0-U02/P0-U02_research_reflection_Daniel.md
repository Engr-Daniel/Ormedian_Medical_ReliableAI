# P0-U02 Research Reflection: Research Computing Environment

**Related lab:** P0-U02-LAB-001 ([answers](answers.md), [environment report](environment_report.md))

> Developed with AI assistance (Claude) from my own two themes: how my troubleshooting improved, and getting to know different environments and how they work. The events described all come from my lab session record.

## 1. What did I understand about Python environments before this unit?

My machine already had three Pythons: a per-user Python 3.10, which was the default, Anaconda Python 3.9, and, by the end of the lab, Python 3.11.9. I knew several versions were installed, but I had not thought carefully about which one actually ran when I typed `python`.

At the start of the lab I believed `py -0p` listed every Python on the machine and that `where.exe python` showed the one that was running. Neither is quite true. `py -0p` lists only what the Windows launcher knows about. `where.exe` lists only search candidates. The only direct evidence is `sys.executable`, printed from inside the running process.

## 2. What did I learn about different environments and how they work?

The main idea I now hold is simple. Every place I run code (a terminal, a notebook, the editor) eventually hands it to one interpreter, and that interpreter can import only the packages in its own `site-packages`.

From that idea, the rest of the unit made sense:

- **Base installs vs a virtual environment.** A base installation is shared by everything that uses it. A virtual environment such as `.venv` is a separate interpreter with its own packages, created from a base Python. When `sys.prefix` differed from `sys.base_prefix`, that was the proof I was inside one.
- **Activation is a shell convenience, not magic.** It only puts `.venv\Scripts` first on `PATH` for that shell. A full path to `.venv\Scripts\python.exe` works without it.
- **The notebook is not the kernel.** VS Code shows the cells, but a separate kernel process runs them. The same notebook failed on the Python 3.10 kernel and worked on the `.venv` kernel, with no code change.
- **Declared vs installed.** I asked for one package, `ipykernel`, and received 28 installed packages in total. The requirements file records what the project chose. `pip freeze` records what is actually installed. I need both.

## 3. How did my troubleshooting improve?

Before this unit, my instinct for an import error would have been to reinstall the package. The lab trained me to follow a sequence instead: observe the exact error, identify the interpreter, list at least two hypotheses, check them with the same interpreter, make the smallest fix, and rerun the original command.

Three moments made this concrete:

- **E1, the wrong-interpreter trap.** My first diagnostic idea was a plain `python -m pip show`. In my active `.venv`, that would have checked the wrong environment, which was the very mistake I was investigating. Running `pip show` through each interpreter explicitly showed that env-a owned colorama and env-b did not.
- **E2, evidence before the failure.** Printing `sys.executable` before the failing import meant that the error still left evidence behind. I could also reject the "stale kernel" explanation, because a Python 3.10 kernel can never see a `.venv`-only package.
- **A bug I caused myself.** In a new terminal, my `$e1` variable was empty, and PowerShell reported a path starting with `\env-b`. Reading the error carefully showed the cause straight away. State hidden in an old shell session is not reproducible.

## 4. Why does this matter for reliable medical AI research?

If two runs of the same evaluation report different AUROC values, the environment is a possible explanation that has to be ruled out before the difference is interpreted. Package versions, preprocessing libraries, or a notebook on the wrong kernel can all change a result. The environment is therefore part of the experimental record, not an IT detail.

## 5. What habits am I taking forward?

- Print `sys.executable` in the failing context before changing anything.
- Install with `python -m pip`, so packages land where `python` runs.
- Record the commit, Python version, interpreter and a freeze snapshot alongside results.
- Rerun the exact failing command after every fix.

## 6. What do I still need to improve?

- **Written explanations.** During the lab I moved quickly and skipped writing my answers as I went. The written answers were drafted with AI help from my evidence and then reviewed by me. Next time I want to write at least short answers in my own words during the lab, while the reasoning is fresh.
- **First instincts.** My first diagnostic in E1 targeted the wrong interpreter. The habit of naming the interpreter explicitly needs practice until it is automatic.
- **Untested portability.** I rebuilt the environment only on my own machine. I have not yet tested a rebuild on a different machine or operating system.
