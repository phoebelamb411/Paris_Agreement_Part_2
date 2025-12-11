# Data Dictionary

## emissions_finance_merged.csv

This file contains the merged dataset of 2024 CO2 emissions and 2022 climate finance contributions for 15 OECD donor countries.

---

## Column Definitions

| Column Name | Data Type | Unit | Description |
|------------|-----------|------|-------------|
| `country` | String | - | Country name (full name) |
| `iso3` | String | - | ISO 3166-1 alpha-3 country code (e.g., USA, DEU, JPN) |
| `year` | Integer | - | Year of emissions data (2024 for all rows) |
| `emissions_mt` | Float | Mt CO2 | Total CO2 emissions from fossil fuels and industry (million tonnes) |
| `emissions_per_capita` | Float | tonnes CO2 | Per capita emissions (emissions_mt ÷ population) |
| `finance_usd_millions` | Integer | USD millions | Climate finance contribution (bilateral, reported to OECD, 2022) |
| `finance_usd_billions` | Float | USD billions | Climate finance in billions (finance_usd_millions ÷ 1000) |
| `finance_per_emission` | Float | USD/Mt CO2 | Finance efficiency (finance_usd_millions ÷ emissions_mt) |
| `emission_rank` | Float | - | Rank by emissions (1 = highest emitter) |
| `finance_rank` | Float | - | Rank by climate finance (1 = highest contributor) |
| `rank_difference` | Float | - | Emission rank minus finance rank (negative = under-contributing) |

---

## Key Calculations

### `finance_per_emission`
```python
finance_per_emission = finance_usd_millions / emissions_mt
```
**Interpretation:** How many USD a country contributes per million tonnes of CO2 emitted.
- **Higher values** = more efficient contribution relative to emissions
- **Example:** Norway at $32.27/Mt is 14× more efficient than USA at $2.34/Mt

### `rank_difference`
```python
rank_difference = emission_rank - finance_rank
```
**Interpretation:** Gap between emissions rank and finance rank
- **Negative (green in charts)** = Under-contributing relative to emissions
  - *Example:* South Korea is rank 3 in emissions but rank 12 in finance → -9 difference
- **Positive (red in charts)** = Over-contributing relative to emissions  
  - *Example:* France is rank 9 in emissions but rank 3 in finance → +6 difference
- **Zero or near-zero** = Contributing proportionally
  - *Example:* Germany is rank 4 in both → 0 difference

---

## Data Sources

### Emissions Data
**Source:** Our World in Data (https://ourworldindata.org/co2-emissions)  
**Original Source:** Global Carbon Project (2024)  
**Year:** 2024  
**Scope:** Territorial CO2 emissions from fossil fuels and industry  
**Excludes:** Land use change, international aviation/shipping  
**Method:** Downloaded from: https://github.com/owid/co2-data

### Climate Finance Data
**Source:** OECD Climate Finance Reports  
**Year:** 2022 (most recent comprehensive data)  
**Scope:** Bilateral public climate finance to developing countries  
**Part of:** $100 billion commitment (2009-2025)  
**Method:** Based on OECD DAC reporting by donor countries

---

## Sample Rows

```csv
country,iso3,year,emissions_mt,emissions_per_capita,finance_usd_millions,finance_usd_billions,finance_per_emission,emission_rank,finance_rank,rank_difference
United States,USA,2024,4904.12,14.197,11500,11.5,2.34,1.0,2.0,-1.0
Japan,JPN,2024,961.867,7.772,13500,13.5,14.04,2.0,1.0,1.0
South Korea,KOR,2024,583.679,11.286,900,0.9,1.54,3.0,12.0,-9.0
```

---

## Data Quality Notes

### ✅ Completeness
- **No missing values** in any column
- All 15 countries have both emissions and finance data
- ISO3 codes standardized to OWID format

### ⚠️ Limitations

1. **Different Data Years**
   - Emissions: 2024 (most current available)
   - Climate finance: 2022 (OECD's latest comprehensive data)
   - **Justification:** Climate finance data has a 2-year reporting lag

2. **Scope Differences**
   - Emissions: Territorial (where CO2 is emitted)
   - Finance: Bilateral only (excludes multilateral contributions like World Bank)

3. **Definition Variability**
   - Countries may define "climate finance" slightly differently
   - OECD provides standardization but some variation remains

4. **Missing Countries**
   - China, India, Brazil excluded (not OECD donors)
   - Some small OECD members excluded due to incomplete data

---

## Usage Examples

### Python
```python
import pandas as pd

# Load data
df = pd.read_csv('emissions_finance_merged.csv')

# Get top 5 emitters
top_emitters = df.nlargest(5, 'emissions_mt')

# Calculate correlation
corr = df['emissions_mt'].corr(df['finance_usd_billions'])

# Find under-contributors
under_contrib = df[df['rank_difference'] < 0]
```

### R
```r
library(tidyverse)

# Load data
df <- read_csv('emissions_finance_merged.csv')

# Get top 5 contributors
top_contrib <- df %>% 
  arrange(desc(finance_usd_billions)) %>% 
  head(5)

# Calculate correlation
cor(df$emissions_mt, df$finance_usd_billions)
```

### Excel
1. Open CSV in Excel
2. Insert → Pivot Table for quick analysis
3. Use CORREL function: `=CORREL(D:D, G:G)` for emissions vs finance
4. Conditional formatting on `rank_difference` to highlight gaps

---

## Suggested Analyses

### Basic Statistics
- Mean, median, standard deviation of `finance_per_emission`
- Correlation between emissions and finance
- Distribution of rank differences

### Comparative Analysis
- Group by region (Europe vs non-Europe)
- Compare per capita emissions to finance contributions
- Identify outliers in efficiency

### Trend Analysis (if combined with historical data)
- Track rank_difference over time
- See if correlation is strengthening or weakening
- Monitor individual countries' trajectories

---

## Updates & Versioning

**Current Version:** 1.0 (December 2024)

**Update Schedule:**
- Emissions data: Updated annually (Our World in Data releases)
- Climate finance: Updated when OECD publishes new reports (typically annual with 2-year lag)

**Version History:**
- v1.0 (2024-12): Initial release with 2024 emissions + 2022 finance

---

## Citation

When using this dataset, please cite:

**Data:**
```
Emissions: Ritchie, H., Rosado, P., & Roser, M. (2023). CO₂ and Greenhouse Gas Emissions. 
Our World in Data. https://ourworldindata.org/co2-emissions

Climate Finance: OECD (2024). Climate Finance Provided and Mobilised by Developed Countries 
in 2013-2022. https://www.oecd.org/climate-change/finance-usd-100-billion-goal/
```

**Analysis:**
```
Lamb, P. (2024). Climate Finance vs Emissions: A Fairness Analysis.
GitHub: github.com/phoebelamb411/Paris_Agreement_Part_2
```

---

## Contact

Questions about this dataset? Open an issue on GitHub or contact:
- 💼 [LinkedIn](https://www.linkedin.com/in/phoebelamb)
- 🐙 [GitHub](https://github.com/phoebelamb411)

---

## Related Files

- **README.md** - Project overview and key findings
- **Part2_Climate_Finance_Analysis.ipynb** - Analysis notebook
- **scatter_emissions_vs_finance.png** - Visualization of relationship
- **ranking_emitters_vs_donors.png** - Comparison of rankings
- **diverging_responsibility_gap.png** - Fairness gap analysis

---

*Last updated: December 2024*
