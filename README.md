# bash_tutorial — Assignment 1: Git Repo + First Software Environment

A minimal **Python + R + Bash** project that prints *Hello World* from each language, built two ways:
once **by hand** and once **with an AI assistant** — so the two approaches can be compared side by side.

> Course: BSGP 7030 · Assignment 1 (10 pts) · Submission: this GitHub repo URL

---

## 📦 What's in here

| Part | Folder | How it was built |
|------|--------|------------------|
| **A — Manual** | [`manual/`](manual/) | Every character typed by hand. No AI tools. |
| **B — AI-assisted** | [`ai/`](ai/) | Same project, regenerated with an AI tool from a high-level prompt. |

### Repository layout

```
bash_tutorial/
├── README.md              ← you are here
├── .gitignore             ← ignores .ipynb_checkpoints
│
├── manual/                ← Part A: hand-built
│   ├── hello_bash.sh      ← Hello World in Bash
│   ├── hello_Py.py        ← Hello World in Python
│   ├── hello_R.r          ← Hello World in R
│   ├── hello_bash.ipynb   ← Bash notebook
│   ├── hello_Py.ipynb     ← Python notebook
│   ├── hello_R.ipynb      ← R notebook
│   ├── environment.yml    ← conda environment definition
│   └── setup_env.sh       ← rebuilds the env + launches JupyterLab
│
└── ai/                    ← Part B: AI-assisted
    ├── hello.sh           ← Hello World in Bash
    ├── hello.py           ← Hello World in Python
    ├── hello.R            ← Hello World in R
    ├── hello_bash.ipynb   ← Bash notebook
    ├── hello_python.ipynb ← Python notebook
    └── hello_r.ipynb      ← R notebook
```

---

## 🛠️ Installation & usage

### Prerequisites

- A terminal with **Bash** (Linux/macOS, or WSL on Windows)
- **conda / Miniconda** (on the OSC cluster this is provided via `module load`)
- **git** (to clone the repository)

### 1. Get the code

```bash
git clone https://github.com/mafreitas/demo_bsgp_delete_later.git
cd demo_bsgp_delete_later          # this is the bash_tutorial project
```

### 2. Build the conda environment

The hand-built `setup_env.sh` is written for the **OSC** cluster. It creates the
conda environment, registers Python and R Jupyter kernels, and serves JupyterLab:

```bash
cd manual
bash setup_env.sh
```

What it does, step by step:

1. `module load miniconda3/24.1.2-py310` — load Miniconda on OSC
2. `conda env create -f environment.yml` — create the `7030_class_1` environment
3. `conda activate 7030_class_1`
4. Register the **Python** kernel (`ipykernel`) and **R** kernel (`IRkernel`)
5. Launch JupyterLab on port `2000`

> **Not on OSC?** Skip the `module load` line and create the environment directly:
> ```bash
> conda env create -f manual/environment.yml
> conda activate 7030_class_1
> ```

### 3. Run the Hello World scripts

From the repository root, with the environment active:

```bash
# Manual versions (Part A)
bash    manual/hello_bash.sh     # → Hello World
python  manual/hello_Py.py       # → Hello World
Rscript manual/hello_R.r         # → Hello World

# AI-assisted versions (Part B)
bash    ai/hello.sh              # → Hello, World!
python  ai/hello.py              # → Hello, World!
Rscript ai/hello.R               # → Hello, World!
```

The scripts also carry a `#!/usr/bin/env …` shebang, so you can run them directly
once they're executable:

```bash
chmod +x ai/hello.sh ai/hello.py ai/hello.R
./ai/hello.sh
```

### 4. Open the notebooks

1. Start JupyterLab (this happens automatically at the end of `setup_env.sh`, or
   run it yourself):
   ```bash
   jupyter lab --no-browser --port=2000
   ```
2. On a remote cluster like OSC, forward the port from your local machine:
   ```bash
   ssh -N -L 2000:localhost:2000 <user>@<host>
   ```
   then open the URL JupyterLab prints (it includes a one-time token) in your browser.
3. In the file browser, open any notebook:
   - `manual/hello_bash.ipynb`, `manual/hello_Py.ipynb`, `manual/hello_R.ipynb`
   - `ai/hello_bash.ipynb`, `ai/hello_python.ipynb`, `ai/hello_r.ipynb`
4. **Pick the right kernel** from the top-right kernel selector before running:
   - Python notebooks → **Python (7030_class_1)**
   - R notebooks → **R (7030_class_1)**
5. Run all cells with **Run ▸ Run All Cells** (or `Shift+Enter` cell by cell).

### The conda environment

`manual/environment.yml` defines the `7030_class_1` environment:

| Package | Purpose |
|---------|---------|
| `python=3.10` | Python runtime |
| `jupyterlab` | Notebook/IDE interface |
| `ipykernel` | Python kernel for Jupyter |
| `r-base` | R runtime |
| `r-irkernel` | R kernel for Jupyter |

---

## 📓 Notebooks

Each folder contains three Hello World notebooks (Bash, Python, R). Open them in
JupyterLab after running `setup_env.sh`, making sure to select the matching
**Python (7030_class_1)** or **R (7030_class_1)** kernel.

---

## 🤖 Manual vs. AI — at a glance

| | Manual (`manual/`) | AI-assisted (`ai/`) |
|---|---|---|
| Output string | `Hello World` | `Hello, World!` |
| Env scaffolding | `environment.yml` + `setup_env.sh` | *(see `REFLECTION.md`)* |
| Built by | Typing every character | High-level prompt to an AI tool |

---

## ✅ Assignment checklist

- [x] Project folder `bash_tutorial`
- [x] Hello World scripts in Bash, Python, R
- [x] Hello World notebooks in Bash, Python, R
- [x] `environment.yml`
- [x] `setup_env.sh`
- [x] Git repository initialized and committed
- [x] Pushed to GitHub
- [x] AI-assisted version in `ai/`

---

*Author: Mike Freitas · BSGP 7030*
