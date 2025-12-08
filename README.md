# w207-predictive-maintenance

## New to the repo start here:

1. install uv + clone
   ```bash

   pip install uv
   git clone https://github.com/PaulTerrasi/w207-predictive-maintenance.git
   cd w207-predictive-maintenance

2. Python 3.12 venv + exact dependencies from lock Macs we recommend you use acceleration **
   ```bash
   uv venv --python 3.12
   uv sync --frozen               # add: --extra mac-accel  (Apple Silicon GPU)

3. (optional) Jupyter kernel **
   ```bash
   uv run python -m ipykernel install --user --name 207-pm --display-name "Python 3.12 (207-pm)"

4. Install LFS
   ```bash
   git lfs install
   git lfs pull

# Project Structure

Project Proposal: Predicting Failure of Milling Machine

Kim Chen (kim_chen@ischool.berkeley.edu), Paul Terrasi(paul.terrasi@ischool.berkeley.edu),
Jeremy Liu(jeremy_liu@ischool.berkeley.edu), Juba Cochran(jubacochran@ischool.berkeley.edu)

Motivation:

The practice of forecasting machinery failure is formally known as predictive maintenance or sometimes called damage propagation modeling. Historically, maintenance strategies have relied on scheduled servicing or reactive repairs after a breakdown. Now however, sectors like big industry, manufacturing, and healthcare leverage preventive maintenance to reduce downtime, optimize spare parts management, and to dramatically improve the accuracy of identifying failing machinery components. Being able to accurately predict equipment failure can increase the useful life of a machine or component while also maximizing uptime. In addition to lower operational costs, predictive maintenance has a significant benefit in helping to ensure human safety.

```text
.
├── data
│   ├── interim
│   ├── processed
│   └── raw
├── experiments
│   ├── notebooks
├── notebooks
    ├── juba_experiments_code
├── reports_by_milestone
│   ├── week_03
│   ├── week_07
│   └── week_14
├── scripts
├── slides
└── src
    ├── config
    └── pipeline

```

### Directory Glossary
- `src/` — Python package code (config, data, features, models, pipelines, utils).
- `scripts/` — CLI wrappers that call into `src/`.
- `notebooks/` — Individual code.
- `slides/` — presentation sources/assets.
- `data/` — project datasets.
  - `data/raw/` — **immutable** original dataset (do not modify).
  - `data/interim/` — cleaned/validated intermediates.
  - `data/processed/` — model-ready features/tables.
- `experiments/` — configs, results, and experiment notebooks.
- `reports_by_milestone/` — deliverables organized by week (e.g., `week_03/`, `week_07/`, `week_14/`).
