# The Flying Geese: Can Bangladesh become a follower of the leading geese?

A comparative analysis of Bangladesh and Vietnam (and seven other Asian economies) using World Bank WDI data.

**Paper:** [`bangladesh_flying_geese.pdf`](bangladesh_flying_geese.pdf) / [`bangladesh_flying_geese.md`](bangladesh_flying_geese.md)
**Author:** Mohammad Jawad Hasan, supervised by Prof. Dr. Israt Rayhan

## Repository layout

| Path | What it is |
|---|---|
| `export_import.ipynb` | Main analysis notebook (data prep, structural breaks, Kojima quadrant, rank correlations, panel unit roots, Granger/Toda-Yamamoto causality, trade competitiveness) |
| `wdi_data.csv` | World Bank WDI extract: 9 economies, 24 indicators, 1976-2025 (long format; missing values are `..`) |
| `images/` | Figures written by the notebook and referenced in the paper |
| `docs/robustness_notes.md` | Robustness checks added during review and what they change |
| `Papers/` | Reference papers and links |
| `requirements.txt` | Python dependencies |

Economies: Bangladesh, China, Indonesia, Japan, Korea (Rep.), Malaysia, Philippines, Singapore, Viet Nam.

## Reproduce

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace export_import.ipynb   # run from the repo root
```

The notebook must be run from the repository root (it reads `wdi_data.csv` and writes `images/`). It needs Python 3.12 or newer.

Figures `fig_decomposition.png` and `fig_workflow.png` cited in the paper are not produced by the notebook.

## Methods in the notebook

Chow test and Zivot-Andrews (structural breaks), Kojima FDI-upgrading quadrant, rolling correlations, Spearman/Kendall lead-lag correlations, Pesaran CD, IPS/CIPS panel unit roots, Dumitrescu-Hurlin and Toda-Yamamoto causality, Net Trade Competitiveness ratio. References are given next to each method inside the notebook.

## Read before citing results

Several headline results are sensitive to specification (short post-break regimes, trending levels, very short high-tech-export series). See [`docs/robustness_notes.md`](docs/robustness_notes.md).

## Research notes (Phase 1)

- Show that leading countries helped follower countries advance in economic growth.
- Explain why Vietnam climbed the global value chain quickly even though it entered the RMG industry at almost the same time as Bangladesh, which remains dominant in RMG.
- Compare countries' manufacturing contribution and foreign-investment shares, and how they moved away from agricultural dependency.
- Explain heterogenisation and homogenisation for the focal case, Bangladesh.
