# Python Course Setup Guide (for R Users New to Conda)

This guide is written for people who mainly use **R/RStudio** and are new to Python environment management.

You will create an isolated Python environment for the course so your existing tools are not affected.

## TL;DR

```bash
conda create --name prof_opt python=3.14
conda activate prof_opt
pip install pytest snakeviz "line_profiler[all]" numpy pandas matplotlib
python -c "import pytest, snakeviz, line_profiler, numpy, pandas, matplotlib; print('All good')"
```


## What you are installing

The course recommends:
- **Python 3.14**

Course packages (installed with `pip`):
- `pytest`
- `snakeviz`
- `line_profiler[all]`
- `numpy`
- `pandas`
- `matplotlib`

---

## Why use an environment? (R analogy)

If you use `renv` in R, a Python environment is the same idea:
- It keeps project dependencies isolated.
- It avoids breaking your system Python or other projects.
- You can delete/recreate it safely.

With conda, we create an environment called `prof_opt`.

---

## 0) Prerequisite: check whether conda is available

Open a terminal and run:

```bash
conda --version
```

If you see a version (for example `conda 24.x.x`), continue to Step 1.

If you get “command not found”, install one of these first:
- **Miniforge** (recommended lightweight option)
- **Miniconda**
- **Anaconda** (larger distribution)

Then reopen your terminal and run `conda --version` again.

---

## 1) Create a new conda environment with Python 3.14

Run:

```bash
conda create --name prof_opt python=3.14
```

What this does:
- `create` makes a new environment
- `--name prof_opt` names it `prof_opt`
- `python=3.14` installs Python 3.14 in that environment

When prompted with `Proceed ([y]/n)?`, type `y` and press Enter.

---

## 2) Activate the environment

Run:

```bash
conda activate prof_opt
```

You should now see `(prof_opt)` at the start of your terminal prompt.

That means all Python and `pip` commands now target this course environment.

---

## 3) Confirm Python version

Run:

```bash
python --version
```

Expected: `Python 3.14.x`

If you do not see 3.14, stop and check that `(prof_opt)` is visible in your prompt.

---

## 4) Install the course packages with pip

Run:

```bash
pip install pytest snakeviz "line_profiler[all]" numpy pandas matplotlib
```

Notes:
- Quotation marks around `line_profiler[all]` are important in many shells.
- This may take a few minutes.

---

## 5) Verify the installation

Run:

```bash
python -c "import pytest, snakeviz, line_profiler, numpy, pandas, matplotlib; print('All good')"
```

If successful, you should see:

```text
All good
```

---
## Troubleshooting

### `conda: command not found`
- Conda is not installed, or shell init is incomplete.
- Install Miniforge/Miniconda, then restart terminal.
- If needed, run:

```bash
conda init zsh
```

Then close and reopen terminal.

### `python --version` is not 3.14 after activation
- Ensure `(prof_opt)` is shown in prompt.
- Check path:

```bash
which python
```

It should point inside a conda environment path, not system Python.

### `pip install` fails with permission errors
- Most often this means environment was not activated.
- Run `conda activate prof_opt` and retry.
- Do **not** use `sudo pip install`.

### Package import error after installation
- Re-run install while environment is active.
- Upgrade pip and retry:

```bash
python -m pip install --upgrade pip
pip install pytest snakeviz "line_profiler[all]" numpy pandas matplotlib
```

---

## Optional: use from R/RStudio via reticulate

If you use `reticulate`, you can point R to this Python environment:

```r
library(reticulate)
use_condaenv("prof_opt", required = TRUE)
py_config()
```

This ensures your R session uses the same Python and packages as the course setup.

---

