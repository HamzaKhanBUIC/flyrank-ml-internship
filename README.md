# Applied Search Intelligence: Content Decay Prioritization

> Ranks a 30,000-URL content library so an editor who can review about 50 pages a month sees the pages most likely to be losing search traffic first.

**Status:** Completed capstone from my Machine Learning Engineering internship at FlyRank (Jun–Sep 2026, remote) · Built from FlyRank's [`flyrank-ml-internship-starter`](https://github.com/flyrank-bih/flyrank-ml-internship-starter) template and dataset · Author: Hamza Imran
**Demo:** [Research paper (GitHub Pages)](https://hamzakhanbuic.github.io/flyrank-ml-internship/) · [Capstone notebook in Colab](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/capstone.ipynb?flush_cache=true)

[![CI Smoke Tests](https://github.com/HamzaKhanBUIC/flyrank-ml-internship/actions/workflows/smoke-test.yml/badge.svg)](https://github.com/HamzaKhanBUIC/flyrank-ml-internship/actions)

## Provenance

This repository started as a copy of FlyRank's starter template. The dataset (`data/raw/content_refresh_anonymized.csv`), the pipeline in `scripts/`, `outputs/`, `skills/`, the lessons in `notebooks/`, the `docs/` folder and the `LICENSE` come from that template and belong to FlyRank. My own work is in `work/notebooks/` (weekly notebooks W1-W7 and the capstone), `work/outputs/` and the research paper `index.html`.

## Results (capstone notebook outputs)

Data: 30,000 pseudonymized URLs from 32 clients. Evaluation is a single client-grouped holdout (`GroupShuffleSplit`, 25 train clients, 7 test clients), so no client appears in both train and test. The numbers below are the committed outputs of `work/notebooks/capstone.ipynb` (also in `work/outputs/capstone_summary.json`).

| Model | Precision@50 | ROC-AUC | Lift vs hand rule |
|:---|:---:|:---:|:---:|
| Heuristic hand rule (baseline) | 0.40 | 0.478 | 1.00x |
| Decision Tree (depth 4) | 0.50 | 0.590 | 1.25x |
| **Random Forest (100 trees)** | **0.70** | **0.605** | **1.75x** |
| HistGradientBoosting (best P@50) | 0.72 | 0.596 | 1.80x |

## Completed Assignment Notebooks

Every weekly milestone is fully executed top-to-bottom with live outputs and leakage checks (W3, W6):

| Week | Card | Assignment Name & Topic | Open in Colab |
|:---:|:---:|:---|:---:|
| **W1** | **ML-02** | Research Question & Lane Framing | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w01_research_question.ipynb?flush_cache=true) |
| **W2** | **ML-03** | ML Task Framing (Ranking & P@50) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w02_ml_task_framing.ipynb?flush_cache=true) |
| **W3** | **ML-04** | Data Contract & Schema Boundaries | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w03_data_contract.ipynb?flush_cache=true) |
| **W3** | **ML-05** | Feature Vector & Leakage Audit | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w03_feature_leakage_check.ipynb?flush_cache=true) |
| **W4** | **ML-06** | Signal Audit & Hypothesis Verdicts | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w04_signal_audit.ipynb?flush_cache=true) |
| **W4** | **ML-07** | Baseline Score Engine & Priority Queue | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w04_baseline_score.ipynb?flush_cache=true) |
| **W5** | **ML-08** | Capstone Model Benchmark Suite | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w05_model.ipynb?flush_cache=true) |
| **W6** | **ML-09** | Validation & Generalization Audit | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w06_validation_audit.ipynb?flush_cache=true) |
| **W7** | **ML-10** | Content Action Playbook & Exports | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/w07_action_playbook.ipynb?flush_cache=true) |
| **W8** | **ML-11** | **Capstone Research Paper & Demo** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/capstone.ipynb?flush_cache=true) |

## Quickstart

Runs the starter template's end-to-end Python pipeline (Python 3.12 in CI; it writes `outputs/model_report.md`, which is the template's report and not the capstone result):

```bash
git clone https://github.com/HamzaKhanBUIC/flyrank-ml-internship.git
cd flyrank-ml-internship
pip install -r requirements.txt
python scripts/run_all.py
```

## Configuration

No configuration is needed for the main path. Notebook `notebooks/03_working_with_the_full_release.ipynb` can read a Hugging Face token from Colab secrets or the `HF_TOKEN` environment variable to download the full release; the token is never stored in the repository.

## Limitations

- Precision@50 is computed over only 50 pages, so one page is 2 percentage points. The gap between Random Forest (0.70) and HistGradientBoosting (0.72) is one page and is not meaningful.
- ROC-AUC is 0.605 for Random Forest, so the model is only modestly better than chance across the whole library. Its value is at the top of the ranking.
- One grouped holdout of 7 clients, not cross-validation. Results change with the split and with library versions (a re-run on current scikit-learn gave Random Forest P@50 0.62 and lift 1.55x). `requirements.txt` sets lower bounds only.
- The label is `trend_direction == down` from the dataset, and the model describes past decay. It does not show that a refresh recovers traffic.
- The pseudonymized data is FlyRank's. Do not try to join it to real client names.

## Acknowledgments & Data Credit

Built on the **FlyRank ML Internship dataset** provided by [FlyRank AI](https://flyrank.ai) (release `v20260703`). Data credit is gratefully acknowledged.

## License

The `LICENSE` file is the template's: "Copyright (c) 2026 FlyRank". See [DATA_USE.md](DATA_USE.md) for data terms.
