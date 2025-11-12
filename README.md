# Used Car Price Analysis 🚗  
**PSTAT 126 Final Project — University of California, Santa Barbara**  
**Authors:** Aliza Samad, Michelle Brataatmadja, Madeleine Bulman, Isaiah Singer  
**Date:** November 2024  

## Overview  
This project analyzes the factors that influence the **resale prices of used cars**, focusing on variables related to maintenance and performance such as **age, mileage, engine capacity, transmission type, and power**.  

The study applies multiple regression models and transformations to identify which predictors significantly affect used-car prices, and whether these effects differ across **brand segments (Economy vs. Premium)**.  

### Research Questions  
1. **How does car age influence resale price**, considering mileage, engine capacity, and transmission type as maintenance indicators?  
2. **How does power correlate with price**, and does this relationship differ between economy and premium brands?  

---

## Data  
- **Source:** [Second Hand Car Price Dataset — Kaggle](https://www.kaggle.com/datasets/sujithmandala/second-hand-car-price-prediction)  
- **Sample Size:** 100 cars  
- **Response Variable:** Price  
- **Predictors:**  
  - Car ID, Brand, Model, Year, Kilometers Driven, Fuel Type, Transmission, Owner Type, Mileage, Engine, Power, Seats  
- **Derived Variable:** `Segment` (Economy vs. Premium, based on CARFAX brand classification)

---

## Methodology  
### Model 1 — Maintenance Factors  
Explores how **Year**, **Mileage**, **Transmission**, and **Engine**, and their interactions influence resale price.  
- Stepwise selection used to optimize variable inclusion.  
- Model includes higher-order interaction terms (e.g., `Engine:Mileage:Year`).  

### Model 2 — Brand and Power Relationship  
Examines how **Power** predicts **Price**, and how this relationship differs across **brand segments**.  
- Log-transformed model: `log(Price) ~ I(Power^-0.95) * Segment`  
- Focus on interaction between transformed power and brand category.  

### Statistical Tests & Diagnostics  
- **AIC/BIC** for model selection  
- **R² & Adjusted R²** for model fit  
- **Shapiro–Wilk tests** and Q–Q plots for residual normality  
- **VIF** for multicollinearity  
- **Cook’s distance** and leverage plots for influential points  
- **Homoscedasticity & Linearity** diagnostics  

---

## Results  
### Model 1 — Age, Mileage, and Maintenance  
- **R² = 0.849**, Adjusted R² = 0.830 → strong fit.  
- None of the age-related predictors or interactions were statistically significant.  
- Concludes that **car age and its interactions with maintenance factors** do **not significantly** affect resale price.  
- Transmission type shows practical importance — manual cars generally sell for less.  

### Model 2 — Power and Brand  
- **R² = 0.910**, Adjusted R² = 0.907 → excellent fit.  
- All main effects and interactions statistically significant (`p < 0.001`).  
- Findings:  
  - **Higher power = higher price**.  
  - **Premium brands** (Audi, BMW, Mercedes) are priced substantially above economy brands.  
  - The **effect of power on price is steeper** for premium brands than for economy brands.  

---

## Discussion & Conclusions  
- **Model 1:** Car **age alone** does not strongly predict resale price within the limited 5-year range.  
- **Model 2:** **Power and brand** are dominant predictors of price; premium cars benefit more from increases in power.  
- **Practical Insight:**  
  - Buyers seeking performance should expect to pay more for premium brands.  
  - Manual transmissions typically lower resale value.  
  - For budget-conscious buyers (e.g., students), **economy cars** offer the best value.  

### Limitations  
- Narrow range of car years (2016–2021) may understate the effect of age.  
- Presence of outliers may affect homogeneity of variance.  
- Small sample size (n = 100) limits generalizability.  

### Future Improvements  
- Broaden dataset to include older cars and larger sample sizes.  
- Incorporate external economic factors (inflation, interest rates).  
- Explore non-linear models or machine learning regressors for improved predictive accuracy.  

---

## Tools & Techniques  
- **R packages:** `tidyverse`, `ggplot2`, `broom`, `car`, `pwr`  
- **Techniques Used:**  
  - Multiple Linear Regression  
  - Interaction and Transformation Terms  
  - Diagnostic Plots and Outlier Analysis  
  - Model Fit and Significance Testing  

---

## Project Files  
- [`FinalProject126.Rmd`](scripts/PSTAT126FinalProject.Rmd) — R Markdown source code  
- [`FinalProject126.pdf`](outputs/PSTAT126FinalProject.pdf) — Final report with visualizations and conclusions  

---

*Created by Isaiah Singer — Data Analyst/Scientist | R, Python, SQL | UCSB Statistics & Data Science*
