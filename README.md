# Technical Report (Process & Reflection)

This document provides a behind-the-scenes look at the process, reasoning, and decisions taken during the analysis of **New York Airport passenger and freight volume (2000–2024)**. It is intended for a technical audience who may wish to replicate or extend the work.

---

## 1. Dataset Origin
- **Source:** [Port Authority of New York and New Jersey (PANYNJ)](https://www.panynj.gov/airports/en/statistics-general-info.html)  
- **Size:** Covers monthly revenue passenger and freight volumes from **2000 through 2024**. Includes four airports: JFK, EWR, LGA, and SWF.  
- **Variables:**  
  - `Date` (monthly granularity)  
  - `Airport` (categorical: JFK, EWR, LGA, SWF)  
  - `Passengers` (monthly passenger volume)  
  - `Freight` (monthly freight volume)  
- **Credibility:** High, as data is sourced from an official transportation authority.  

---

## 2. Cleaning & Preprocessing
Steps performed:
1. **Loading Data** with `pandas.read_csv()`.  
2. **Date Conversion**: Converted `Date` column into `datetime` format for time-series analysis.  
3. **Null Handling**: Dropped rows with missing values to avoid errors during visualization.  
4. **Feature Creation**:  
   - Grouped by airport and month to enable comparisons.  
   - Calculated airline market share for 2000 and 2024 from passenger volumes.  
5. **Subset Selection**: Retained only relevant columns (`Date`, `Airport`, `Passengers`, `Freight`).  

---

## 3. Visualization Choices
- **Line Charts:** Used for **long-term trends** (2000–2024), as they best capture fluctuations and seasonality over time.  
- **Bar Charts:** Used for **categorical comparisons** (e.g., market share by airline, passenger vs freight). 
- **Colors:** Relied on Seaborn defaults for readability. Considered thematic palettes (e.g., red for decline, green for recovery) but kept defaults for consistency.

---

## 4. Reflection
- **What Worked Well:**  
  - Pandas groupby functions made it easy to summarize by airport and airline.  
  - Seaborn + Matplotlib provided clean visualizations quickly.  
  - Plotly enabled interactive exploration, especially for long time series.  

- **Challenges:**  
  - Dropping nulls may have removed useful information. Imputation strategies could improve this.  
  - Some charts became cluttered when showing all airports or airlines simultaneously.  
  - Limited documentation on column definitions required assumptions.  

- **Future Improvements:**  
  - Add rolling averages (e.g., 3-month moving average) to smooth noisy trends.  
  - Perform statistical tests (e.g., ANOVA) to quantify airport/airline differences.  
  - Explore freight vs passenger correlations under economic shocks (2008 crisis, COVID-19).  
  - Enhance labeling, annotations, and color schemes for clearer storytelling.  
  - Package code into reusable functions for reproducibility.  

---

## 5. Code Access
Full analysis is in the Jupyter Notebook:  
[`ITCS_5122_Project_1.ipynb`](./ITCS_5122_Project_1.ipynb)
