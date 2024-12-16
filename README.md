# COMP47670 Project 1  
### Chungman Lee (23205535)

### New data has beed added onthe original source so the lenghth of the data can be different now.

## How to View
Open "Chungman_Lee_23205535_Global_Warming.ipynb" or "Chungman_Lee_23205535_Global_Warming.html" file.

## Overview
In this project, I analyzed multiple datasets related to global warming sourced from a public API (http://global-warming.org/). These datasets include temperature anomalies, greenhouse gas concentrations (CO2, methane, nitrous oxide), polar ice extent, and ocean warming measures. The primary goal was to gain insights into how these factors interrelate and to identify trends and patterns that may indicate the causes and effects of global warming.

## Data Collection
**Datasets:**
- **Temperature**: Monthly global mean surface temperature anomaly from 1880.
- **Carbon Dioxide (CO2)**: Quasi-daily measurements from 2013.
- **Methane**: Monthly data starting from the mid-1980s.
- **Nitrous Oxide (N2O)**: Monthly data from the early 2000s.
- **Polar Ice**: Monthly Arctic sea ice extent and area since 1979.
- **Ocean Warming**: Annual sea surface temperature anomalies from 1880.

**Challenges in Data Collection:**
- Each dataset covered different time frames and sampling frequencies, making direct comparisons difficult.
- Lack of detailed metadata required careful interpretation of variables and their formats.
- Some features needed to be resampled (e.g., daily to monthly) and filled forward (ffill) to align with other datasets.

**Data Storage:**
- Raw JSON data were saved in a `raw` directory.
- Processed and merged data were saved as `global_warming_data.json` in a `data` directory for further analysis.

## Data Preprocessing
- **Resampling and Merging**:  
  All datasets were converted to a uniform monthly frequency. For datasets with different periods, outer joins were used, resulting in NaN values where data were missing. These gaps were handled by methods like forward fill.
  
- **Normalization**:  
  MinMaxScaler was applied to normalize all features to a [0,1] range for consistent comparison and correlation analysis.

## Exploratory Data Analysis
1. **Summary Statistics & Visualizations**:  
   - **Box Plots** and **Histograms/KDE**:  
     Revealed distribution shapes, median positions, and outliers. Land temperature anomalies had notable outliers, indicating recent, extreme temperature spikes.
   
   - **Time Series Analysis**:  
     Trends in temperature and greenhouse gases showed noticeable increases over time. Polar ice extent and area showed a downward trend, implying detrimental effects from warming.
     
   - **Seasonal Decomposition** of land temperature anomalies identified a clear upward trend aside from seasonal variations.

2. **Correlation and Relationships**:
   - A **correlation heatmap** indicated strong positive correlations among greenhouse gases, and moderate positive correlations between greenhouse gases and temperature anomalies.
   - Polar ice features showed a negative correlation with temperature and greenhouse gas concentrations.
   
   - **Scatter Plots with Trend Lines**:
     - Methane had a stronger linear relationship with temperature anomalies than CO2 did.
     - Ocean temperature showed steeper trend lines relative to greenhouse gas anomalies compared to land temperature, suggesting the ocean’s sensitivity to greenhouse gas levels.

## Key Insights
- Temperature anomalies (land and ocean) and greenhouse gases are consistently increasing, supporting the global warming narrative.
- Polar ice extent and area are declining, correlating negatively with rising temperatures and greenhouse gas concentrations.
- Methane appears more closely tied to temperature anomalies than CO2 or N2O, at least within the analyzed timeframe and dataset structure.

## Challenges Faced
- Different time frames and frequencies of datasets made direct comparisons and merges challenging.
- Lack of comprehensive metadata required assumptions and careful handling of data formats.
- Balancing multiple datasets and handling NaN values was non-trivial.

## Future Work
- **Causality Tests**: Distinguish correlation from causation by applying causality analysis (e.g., Granger causality tests).
- **Dimensionality Reduction & Clustering**: Use PCA or clustering to find patterns in multivariate space.
- **Domain Integration**: Incorporate socio-economic or policy data to understand the drivers behind emissions changes and temperature anomalies.
- **Predictive Modeling**: Build and evaluate machine learning models (e.g., regression models, LSTM networks) to forecast future temperature anomalies or ice extent under various greenhouse gas scenarios.

## Conclusion
This project assembled and explored multiple datasets related to global warming. Despite temporal mismatches and data complexity, significant insights emerged: greenhouse gases and temperature anomalies have risen in tandem, while polar ice has shrunk. Such analyses pave the way for more detailed, causality-focused studies and predictive modeling in the fight against climate change.
