# Paris Agreement – Climate Finance vs Emissions (Part 2)

![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)

---

## 🎯 Research Question

**Are the world's biggest polluters paying their fair share for climate solutions?**

This analysis examines whether developed countries' greenhouse gas emissions predict their climate finance contributions—and reveals significant fairness gaps in who pays versus who pollutes.

---

## 🔍 Key Findings

### **The Correlation Gap**
- **Only 40% (R²=0.403)** of climate finance variation is explained by emissions levels
- **60% is determined by other factors** – suggesting fairness issues in the current system

### **The Winners** ✅ (Paying More Than Expected)
| Country | Emissions Rank | Finance Rank | Over-Contribution |
|---------|---------------|--------------|-------------------|
| 🇫🇷 France | 9th | 3rd | **+6 ranks** |
| 🇸🇪 Sweden | 13th | 9th | +4 ranks |
| 🇳🇴 Norway | 14th | 10th | +3.5 ranks |

**France contributes $27.26 per ton of emissions** – the most efficient among major emitters.

### **The Laggards** ⚠️ (Paying Less Than Expected)
| Country | Emissions Rank | Finance Rank | Under-Contribution |
|---------|---------------|--------------|---------------------|
| 🇰🇷 South Korea | 3rd | 12th | **-9 ranks** |
| 🇦🇺 Australia | 6th | 13th | -7 ranks |
| 🇨🇦 Canada | 5th | 10th | -5.5 ranks |

**South Korea contributes only $1.54 per ton** – 18x less efficient than Norway ($32.27/ton).

### **The United States**: 
- #1 emitter (4,904 Mt CO2) but #2 in finance ($11.5B)
- Contributing **$2.34 per ton** – 14x less than Norway
- **Would need $157B/year** to match Norway's per-ton contribution

---

## 📊 Visualizations

### 1. The Fairness Gap
![Fairness Gap](output/diverging_responsibility_gap.png)
*Countries to the right are under-contributing relative to emissions; countries to the left are over-contributing.*

### 2. Who Emits vs Who Pays
![Rankings Comparison](output/ranking_emitters_vs_donors.png)
*Direct comparison showing emissions rankings don't match finance rankings.*

### 3. The Weak Relationship
![Scatter Plot](output/scatter_emissions_vs_finance.png)
*R² = 0.403 shows emissions only moderately predict climate finance contributions.*

---

## 💡 Why This Matters

### **The Climate Justice Debate**
The Paris Agreement aims to hold global warming to 1.5°C, requiring **$100 billion annually** in climate finance from developed countries. But who should pay?

**Three perspectives:**
1. **Polluter Pays**: High emitters should contribute proportionally
2. **Capacity to Pay**: Wealthy nations should contribute regardless of emissions  
3. **Historical Responsibility**: Cumulative emissions since industrialization matter

**This analysis shows:** Current contributions follow none of these principles consistently.

### **Real-World Impact**
- Developing countries face climate impacts they didn't cause
- Inadequate finance delays renewable energy transitions
- Climate finance gaps threaten Paris Agreement goals
- **Fair contribution frameworks** could increase total funding

---

## 🛠️ Methodology

### **Data Sources**
- **Emissions**: [Our World in Data](https://ourworldindata.org/co2-emissions) (2024 data)
  - Source: Global Carbon Project
  - Coverage: 200+ countries, 1750-2024
  - Latest year: 2024
  
- **Climate Finance**: OECD Climate Finance Reports (2022 data)
  - Most recent comprehensive year with all donor reporting
  - Bilateral contributions to developing countries
  - Part of the $100 billion commitment

### **Scope**
- **15 developed countries** (OECD donors with $100B commitment)
- Total analyzed: **$61.5 billion** in climate finance
- Total emissions: **9,514 Mt CO2** (2024)

### **Analysis Approach**
1. Merged 2024 emissions with 2022 climate finance data
2. Calculated correlation (Pearson's r)
3. Ranked countries by emissions and finance separately
4. Computed rank differences to identify fairness gaps
5. Calculated finance efficiency (USD per Mt CO2)

### **Note on Data Years**
- Emissions: 2024 (most current available)
- Climate finance: 2022 (OECD's latest comprehensive data)
- **This is standard** in climate research due to reporting lags

---

## 🚀 Quickstart

### **Prerequisites**
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### **Clone & Run**
```bash
git clone https://github.com/phoebelamb411/Paris_Agreement_Part_2.git
cd Paris_Agreement_Part_2
jupyter notebook
```

Then open `Part2_Climate_Finance_Analysis.ipynb` and run all cells.

---

## 📁 Repository Structure

```
Paris_Agreement_Part_2/
├── raw_data/
│   └── owid-co2-data.csv          # Downloaded automatically, or place here
├── scripts/
│   └── part2_analysis.py          # Python script version (optional)
├── output/
│   ├── scatter_emissions_vs_finance.png
│   ├── ranking_emitters_vs_donors.png
│   ├── diverging_responsibility_gap.png
│   └── emissions_finance_merged.csv
├── Part2_Climate_Finance_Analysis.ipynb  # Main analysis
├── DATA_DICTIONARY.md             # Column definitions
└── README.md
```

---

## 📈 Detailed Results by Country

| Country | Emissions (Mt) | Finance ($B) | $/Mt | Emission Rank | Finance Rank | Gap |
|---------|---------------|--------------|------|---------------|--------------|-----|
| 🇺🇸 USA | 4,904 | 11.5 | 2.34 | 1 | 2 | -1 |
| 🇯🇵 Japan | 962 | 13.5 | 14.04 | 2 | 1 | +1 |
| 🇰🇷 South Korea | 584 | 0.9 | 1.54 | 3 | 12 | **-9** |
| 🇩🇪 Germany | 572 | 6.5 | 11.36 | 4 | 4 | 0 |
| 🇨🇦 Canada | 533 | 1.2 | 2.25 | 5 | 10 | -5.5 |
| 🇦🇺 Australia | 387 | 0.8 | 2.07 | 6 | 13 | -7 |
| 🇬🇧 UK | 313 | 2.8 | 8.95 | 7 | 6 | +1 |
| 🇮🇹 Italy | 302 | 4.2 | 13.91 | 8 | 5 | +3 |
| 🇫🇷 France | 264 | 7.2 | **27.26** | 9 | 3 | **+6** |
| 🇪🇸 Spain | 220 | 2.1 | 9.53 | 10 | 7 | +3 |
| 🇳🇱 Netherlands | 115 | 1.8 | 15.68 | 11 | 8 | +3 |
| 🇧🇪 Belgium | 85 | 0.6 | 7.02 | 12 | 14 | -2.5 |
| 🇸🇪 Sweden | 38 | 1.5 | 39.37 | 13 | 9 | +4 |
| 🇳🇴 Norway | 37 | 1.2 | **32.27** | 14 | 10 | +3.5 |
| 🇨🇭 Switzerland | 32 | 0.6 | 18.71 | 15 | 14 | +0.5 |

*Full dataset available in [output/emissions_finance_merged.csv](output/emissions_finance_merged.csv)*

---

## 🔬 Technical Details

### **Statistical Methods**
- **Pearson correlation coefficient**: Measures linear relationship strength
- **R² (coefficient of determination)**: Proportion of variance explained
- **Rank difference analysis**: Identifies outliers in fairness

### **Data Quality Checks**
- ✅ All 15 countries have both emissions and finance data
- ✅ No missing values in merged dataset
- ✅ ISO3 country codes standardized
- ✅ Units consistent (Mt CO2, USD millions)

### **Limitations**
1. **Climate finance definitions vary** between countries
2. **Different reporting years** (emissions 2024, finance 2022)
3. **Sample limited to OECD donors** (excludes China, India)
4. **Doesn't include multilateral contributions** (World Bank, etc.)
5. **Per capita analysis not included** (future enhancement)

---

## 🔄 Comparison with Part 1

| Aspect | Part 1 | Part 2 |
|--------|--------|--------|
| **Focus** | Emissions vs targets | Finance vs emissions |
| **Question** | Are countries on track? | Are emitters paying? |
| **Data** | 2015-2024 trends | 2024 emissions + 2022 finance |
| **Countries** | 5 (USA, UK, EU27, Japan, Canada) | 15 (all OECD donors) |
| **Tools** | R (tidyverse, ggplot2) | Python (pandas, matplotlib) |
| **Key Finding** | Most countries off-track | Weak correlation (R²=0.403) |

**Together, these projects tell a complete story**: Countries are failing to meet emissions targets AND the funding burden is unfairly distributed.

---

## 📚 Further Reading

### **Key Research**
- OECD (2024). *Climate Finance Provided and Mobilised by Developed Countries in 2013-2022*
- Ritchie, H., et al. (2023). *CO₂ and Greenhouse Gas Emissions*. Our World in Data
- UNFCCC (2024). *Standing Committee on Finance Reports*

### **Related Topics**
- **Loss and Damage**: Compensation for unavoidable climate impacts
- **Adaptation Finance**: Helping countries cope with climate change
- **Climate Justice**: Ethical frameworks for climate responsibility
- **South-South Cooperation**: Climate finance from emerging economies

---

## 🎓 Skills Demonstrated

**Data Analysis:**
- Multi-source data integration
- Correlation analysis
- Rank-based fairness metrics

**Data Engineering:**
- Automated data download from APIs/GitHub
- Data cleaning and standardization
- CSV export for reproducibility

**Visualization:**
- Diverging bar charts for comparative analysis
- Scatter plots with trend lines
- Side-by-side rankings
- Professional chart formatting

**Research:**
- Literature review (OECD, UNFCCC reports)
- Clear methodology documentation
- Transparent limitations acknowledgment

---

## ⚠️ Important Notes

### **China & Emerging Economies**
This analysis focuses on developed countries with explicit $100B commitments. China, as a developing country under UNFCCC classification, is not obligated to contribute but does provide ~$4.5B annually through South-South cooperation (not tracked by OECD).

### **The $100 Billion Goal**
- Committed in 2009 at COP15
- Target: $100B/year by 2020
- **First achieved in 2022** ($115.9B)
- Continues through 2025
- **New goal for 2025+** under negotiation at COP29

---

## 🗺️ Future Enhancements

**Planned for v2.0:**
- [ ] Per capita emissions analysis
- [ ] Historical cumulative emissions
- [ ] Adaptation vs mitigation finance breakdown
- [ ] Income group comparisons
- [ ] Interactive visualizations (Plotly)
- [ ] Time series (2013-2024 trends)
- [ ] Regression analysis with additional variables

**Ideas Welcome!** Open an issue to suggest improvements.

---

## 🤝 Contributing

Found an issue? Have a suggestion? Contributions welcome!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📜 License & Attribution

**Code**: MIT License  
**Data**: 
- Our World in Data: CC BY 4.0
- OECD Climate Finance Data: Public domain with attribution

**Please cite:**
```
Lamb, P. (2024). Climate Finance vs Emissions: A Fairness Analysis. 
GitHub: github.com/phoebelamb411/Paris_Agreement_Part_2
Data: Our World in Data (2024) + OECD (2022)
```

---

## 🌟 Acknowledgments

- **Our World in Data** for maintaining excellent, accessible emissions data
- **OECD** for transparent climate finance reporting
- **Global Carbon Project** for rigorous emissions tracking
- **Climate policy researchers** whose work inspired this analysis

---

## 🔗 Connect

- 💼 [LinkedIn](https://www.linkedin.com/in/phoebelamb)
- 🐙 [GitHub](https://github.com/phoebelamb411)
- 📊 [Part 1: Emissions vs Targets](https://github.com/phoebelamb411/Paris_Agreement_Part_1)

---

## 📌 Citation

If you use this analysis or methodology:

**APA:**
```
Lamb, P. (2024). Are the World's Biggest Polluters Paying Their Fair Share? 
An Analysis of Climate Finance vs Emissions Among OECD Countries. 
Retrieved from https://github.com/phoebelamb411/Paris_Agreement_Part_2
```

**BibTeX:**
```bibtex
@misc{lamb2024climatefinance,
  author = {Lamb, Phoebe},
  title = {Climate Finance vs Emissions: A Fairness Analysis},
  year = {2024},
  publisher = {GitHub},
  url = {https://github.com/phoebelamb411/Paris_Agreement_Part_2}
}
```

---

## 💬 Questions?

Open an issue or reach out on [LinkedIn](https://www.linkedin.com/in/phoebelamb)!

**This project is part of a climate policy analysis series:**
- **Part 1**: [Emissions vs Paris Agreement Targets](https://github.com/phoebelamb411/Paris_Agreement_Part_1) ✅
- **Part 2**: Climate Finance vs Emissions (this repo) ✅
- **Part 3**: Coming soon – Climate finance effectiveness analysis

---

*"The question isn't just whether countries are cutting emissions—it's whether those most responsible are funding the solutions."* 🌍
