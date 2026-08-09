# Resonance Frequency as a Temporally Evolving Cardiac State During HRV Biofeedback

**Multi-Epoch Sliding-Window Analysis with Passive Control in Cognitively Active Adolescent Novices**

[!\[License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[!\[Python 3.10+](https://img.shields.io/badge/Python-3.10+-green.svg)](https://python.org)

\---

## Overview

This repository contains the complete, reproducible analysis for the manuscript:

> \*Resonance Frequency as a Temporally Evolving Cardiac State During HRV Biofeedback:  
> A Multi-Epoch Sliding-Window Analysis with Passive Control in Cognitively Active Adolescent Novices.\*  


Key Findings

* A **multi-epoch sliding-window LMM framework** reveals that HRVBF-specific LF amplification is **temporally localized to the first 5 minutes** of the session (β = 0.081, 95% CI \[0.001, 0.162], *p* = .048)
* **Full-session aggregation obscures this effect**: session-level RF prevalence was identical in HRVBF and control groups (70% each)
* Results are **threshold-independent**: sensitivity analysis across 5 LFpeak/TP thresholds (0.30–0.50) yielded perfectly invariant inferential outcomes (5/5 significant; 20/20 positive)

\---

## Repository Structure

```
LF\_RF\_Analysis/
├── LF\_RF\_Analysis\_Publication.ipynb   ← Main analysis notebook 
├── requirements.txt                   ← Python dependencies
├── README.md
│
├── data/                              ← Window-level and participant-level CSVs
│   ├── windows\_full.csv               ← All windows, full session (\~491 rows)
│   ├── windows\_first.csv              ← First 5 min epoch (\~310 rows)
│   ├── windows\_center.csv             ← Centre 5 min epoch
│   ├── windows\_last.csv               ← Last 5 min epoch
│   ├── participants\_full.csv          ← Participant-level summaries, full session
│   ├── participants\_first.csv
│   ├── participants\_center.csv
│   └── participants\_last.csv
│
│   
│
└── figures/← 600 dpi PNG (174mm max width)
    
```

**Source data** (EDF and TXT physiological recordings) are deposited separately at:  
`\[OSF/Zenodo DOI — to be inserted]`

\---

## How to Run

### 1\. Clone the repository

```bash
git clone https://github.com/\[YOUR\_USERNAME]/LF\_RF\_Analysis.git
cd LF\_RF\_Analysis
```

### 2\. Install dependencies

```bash
pip install -r requirements.txt
```

### 3\. Set data paths

Open `LF\_RF\_Analysis\_Publication.ipynb` and edit **Cell 1**:

```python
HRVBF\_DIR   = Path('/path/to/Source\_HRVBF')    # E01–E10 EDF + TXT files
CONTROL\_DIR = Path('/path/to/Source\_Control')  # K01–K10 EDF + TXT files
OUT\_DIR     = Path('./outputs')                # will be created automatically
```

### 4\. Run the notebook

```bash
# Option A — Jupyter interactive
jupyter notebook LF\_RF\_Analysis\_Publication.ipynb

# Option B — Execute and export (fully automated)
jupyter nbconvert --to notebook --execute LF\_RF\_Analysis\_Publication.ipynb \\
  --output LF\_RF\_Analysis\_executed.ipynb \\
  --ExecutePreprocessor.timeout=900
```

\---

## Analysis Pipeline Summary

|Cell|Content|
|-|-|
|1|Imports, paths, APB figure specs|
|2|Signal processing functions (IPI extraction, Welch PSD)|
|3|Data loading (BioTrace TXT + EDF)|
|4|Temporal epoch framework + window extraction engine|
|5|**Main loop** — all 20 participants × 4 epochs|
|6|Participant-level summaries|
|7|**LMM** (Group × Condition, REML) — all 4 epochs|
|8|**Tables 1–6** with captions|
|9–17|**Figures 1–9** (each: build → inspect → save)|

\---

## Spectral Metric

**LFpeak/TP** = LF\_power / (LF\_power + HF\_power)

* LF band: 0.04–0.15 Hz
* HF band: 0.15–0.40 Hz
* Range: \[0, 1] — dimensionally consistent, bounded, threshold-free as continuous outcome
* Classification threshold (for prevalence counts only): 0.40 (sensitivity: 0.30–0.50)

\---

## Reproducibility

* All analyses are **fully deterministic** — no random seeds required
* Python ≥ 3.10 recommended
* Tested with: numpy 2.4.4 · pandas 3.0.2 · scipy 1.17.1 · matplotlib 3.10.8 · statsmodels 0.14.6 · mne 1.4+

\---

## Citation

If you use this code or data in your research, please cite:

```bibtex
@article{yunus2026rf,
  author  = {Yunus et al. 2026}
  title   = {Resonance Frequency as a Temporally Evolving Cardiac State 
             During {HRV} Biofeedback: A Multi-Epoch Sliding-Window Analysis 
             with Passive Control in Cognitively Active Adolescent Novices},
  year    = {2026},
  note    = {under review}
}
```

\---

## License

MIT License — see [LICENSE](LICENSE) file.

\---

## Contact

Corresponding author: Nasrettin Yunus \[corresponding author email — nasrettinyunus@gmail.com]

