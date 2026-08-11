# World Happiness Analysis (WHR 2026)

Exploratory data analysis of the **World Happiness Report 2026**, using the official
Figure 2.1 dataset (Gallup World Poll based, 168 countries, 2011–2025).

## Question

> What socio-economic factors are associated with differences in life satisfaction
> across countries, and how have these relationships evolved over time?

## Data

- **Source:** [World Happiness Report — official data sharing page](https://worldhappiness.report/data-sharing/)
- **File:** `WHR26_Data_Figure_2_1_Data_for_Figure_2.csv`
- **Coverage:** 168 countries, years 2011–2025 (no 2013)
- **Variables:** Life evaluation (3-year average), 95% confidence interval, and six
  explanatory factors (GDP per capita, social support, healthy life expectancy,
  freedom, generosity, perceptions of corruption), plus dystopia + residual.

Raw data lives in `data/raw/` and is never modified. Cleaned data is written to
`data/processed/` by the notebook.

## Project structure

```
world-happiness-analysis/
├── data/
│   ├── raw/            # original WHR 2026 export, untouched
│   └── processed/      # cleaned dataset produced by the notebook
├── notebooks/
│   └── 01_exploratory_analysis.ipynb
├── src/                # reusable Python code (future work)
├── visuals/             # exported charts (PNG)
├── requirements.txt
└── README.md
```

## Analysis

The notebook goes beyond a surface-level EDA:

1. **Data understanding & cleaning** — checks panel balance (which countries have how
   many years of data), missing values, and duplicates before touching the numbers.
2. **2025 snapshot** — distribution, skew, top/bottom 15 countries.
3. **Correlation + significance** — Pearson r *and* p-value for every factor, not just
   the coefficient.
4. **Multiple regression (OLS)** — puts all six factors into one model at once, so the
   coefficients show each factor's *independent* association with happiness once the
   others are controlled for (rather than raw correlations, which conflate overlapping
   factors like GDP and life expectancy).
5. **Trend analysis** — tests whether the 2011–2025 global trend is statistically
   significant (linear regression on year, not just eyeballing a line chart).
6. **Biggest movers** — which countries improved or declined the most between their
   first and most recent recorded year.
7. **Volatility** — which countries have the most/least stable happiness scores over
   time.

## How to run

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/01_exploratory_analysis.ipynb
```

## Key findings

*(fill in after reviewing the notebook output)*

- ...
- ...

## Limitations

- No `region`/`continent` field in the source data — a regional breakdown would
  require an external country → region mapping.
- Analysis is correlational, not causal.

## Author

*(your name / LinkedIn / portfolio link)*
