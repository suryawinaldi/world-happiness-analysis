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

- **Social support and freedom matter more than GDP, independently.** GDP per capita has
  the highest simple correlation with happiness (r = 0.75), but once all six factors are
  controlled for together in a multiple regression (R² = 0.83), `freedom` (coef = 1.81)
  and `social_support` (coef = 1.44) turn out to have the largest *independent* effects —
  GDP's effect shrinks to 0.49. `generosity` and `corruption_perception` are not
  statistically significant once the other factors are accounted for.
- **The global average is rising, slowly.** Life evaluation climbed from 5.39 (2011) to
  5.65 (2025) — a small but statistically significant upward trend (p < 0.001), not a
  dramatic shift.
- **The biggest changes track real-world events.** Serbia, Bulgaria, and Georgia improved
  the most (+1.6 to +2.1 points) since 2011, while Afghanistan (−2.8), Malawi (−1.3), and
  Syria (−1.3) declined the most — consistent with conflict and economic crisis in those
  countries.
- **Stability tracks institutional strength.** The most volatile countries (Lebanon,
  Afghanistan) are ones with major crises during the period; the most stable (Sweden, the
  Netherlands, Belgium) are high-income countries with strong institutions.

Full statistical detail — p-values, regression output, and every chart — is in
`notebooks/01_exploratory_analysis.ipynb`.

## Limitations

- No `region`/`continent` field in the source data — a regional breakdown would
  require an external country → region mapping.
- Analysis is correlational, not causal.

## Author

**Surya Winaldi Yakin**
Data Analyst portfolio project.

- LinkedIn: [linkedin.com/in/surya-winaldi-yakin](https://www.linkedin.com/in/surya-winaldi-yakin-90751a279)
- Portfolio website: coming soon

