# Localized vs. generic climate messaging on Instagram

Empirical study and analysis: **Do localized (landmark-based) climate video ads on Instagram produce higher “concern” responses than generic ads?**  
Work includes survey-style polling exports, **two-proportion z-tests**, **Bayesian Beta–Binomial** comparison, and a full **LaTeX report** with literature review.


---

## Highlights

- Instagram **A/B-style** deployment (contextualized vs generic creatives), segmented by location, age, and gender  
- Analysis in **`src/climate_polling_analysis.ipynb`**: parsing ad set names, EDA, frequentist tests, posterior simulation  
- Academic write-up in **`doc/`** (`main.tex`, `references.bib`) — compile to PDF for the full narrative, methods, and limitations  

---

## Repository layout

| Path | Purpose |
|------|--------|
| `src/climate_polling_analysis.ipynb` | Main statistical analysis (pandas, statsmodels, matplotlib/seaborn) |
| `doc/main.tex` | Project report (natbib, bibliography) |
| `doc/references.bib` | BibTeX references |
| `data/instagram_ad_polling_questions/` | German **polling question copy** per city/region (creative text, not platform exports) |
| `requirements.txt` | Python dependencies |

Place Meta / Instagram **results exports** (e.g. `Climate_Perception_results_Part1.xlsx`) under `data/` as expected by the notebook, or adjust the path in the first data-loading cell.

---

## Setup

```bash
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

`openpyxl` is included for reading `.xlsx` files with pandas.

---

## Run the analysis

1. Add your campaign export spreadsheet to `data/` (same filename as in the notebook, or edit the path in the notebook).  
2. Open and run:

```bash
jupyter lab src/climate_polling_analysis.ipynb
```

Re-run all cells to regenerate tables and plots.

---

## Build the PDF report

Requires a LaTeX distribution (e.g. TeX Live, MiKTeX) and `bibtex` / `biber` as configured for `natbib`.

```bash
cd doc
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

Include figure assets referenced in `main.tex` (e.g. demographic flowchart, posterior plot, gender chart) in the same folder as `main.tex` if you publish the compiled PDF.

---

## Results
Aggregated tests did **not** show a significant difference between contextualized and generic arms at conventional levels; **Bayesian** summaries indicated **high uncertainty** (small, imbalanced samples). A descriptive **gender gap** in “Yes” responses was noted in the report. See the PDF for full discussion and limitations.

