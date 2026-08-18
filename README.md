# Applied Search Intelligence: Content Decay Prioritization
### FlyRank Machine Learning Internship Capstone

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HamzaKhanBUIC/flyrank-ml-internship/blob/main/work/notebooks/capstone.ipynb?flush_cache=true)
[![Deployed Research Paper](https://img.shields.io/badge/Research_Paper-Live_on_GitHub_Pages-238636?style=flat&logo=github)](https://hamzakhanbuic.github.io/flyrank-ml-internship/)
[![CI Smoke Tests](https://github.com/HamzaKhanBUIC/flyrank-ml-internship/actions/workflows/smoke-test.yml/badge.svg)](https://github.com/HamzaKhanBUIC/flyrank-ml-internship/actions)

> **Live Deployed Research Paper:** [https://hamzakhanbuic.github.io/flyrank-ml-internship/](https://hamzakhanbuic.github.io/flyrank-ml-internship/)  
> **Author:** Hamza Imran  
> **Project Lane:** Refresh & Content Opportunity Scoring  
> **Dataset:** 30,000 anonymized enterprise URLs across 32 client domains  

---

## 🌟 Executive Summary & Headline Results

Enterprise content libraries experience continuous, silent organic search traffic erosion as published pages age and search competition shifts. When editorial bandwidth is constrained to reviewing only ~50 pages per month, conventional heuristic rules achieve only **24% Precision@50** when ranking decaying content.

In this capstone research project, we developed a probability-calibrated Random Forest ranking engine trained on 30,000 pseudonymized URLs across 32 enterprise clients. Evaluated under strict Grouped Client-Holdout cross-validation to prevent tenant memorization and data leakage:

* **Champion Model Precision@50:** **74.0%** (37 of top 50 picks accurately identified decaying URLs).
* **Empirical Lift over Baseline:** **3.08x lift** over heuristic hand rules.
* **Discrimination:** **0.785 ROC-AUC** on sealed, unseen test client domains.
* **Operational Action Playbook:** Exported ranked queue with human-interpretable reason codes (`REFRESH_METADATA`, `EXPAND_CONTENT`, `STALE_CONTENT_REFRESH`).

---

## 📂 Completed Assignment Notebooks

Every weekly milestone is fully executed top-to-bottom with live outputs and zero data leakage:

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

---

## 🛠️ Reproducibility & Local Execution

To run the full end-to-end Python pipeline locally:

```bash
git clone https://github.com/HamzaKhanBUIC/flyrank-ml-internship.git
cd flyrank-ml-internship
pip install -r requirements.txt
python scripts/run_all.py
```

---

## 📚 Acknowledgments & Data Credit

Built on the **FlyRank ML Internship dataset** provided by [FlyRank AI](https://flyrank.ai) (Enterprise Search Intelligence telemetry, release `v20260703`). Data credit is gratefully acknowledged.
