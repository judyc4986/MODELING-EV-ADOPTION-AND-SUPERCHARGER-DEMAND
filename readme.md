# Modeling EV Adoption and Supercharger Demand in Washington State  
### A Strategic Framework for Tesla’s Annual Infrastructure Budget  
**Author:** Judy Cheng

---
## 🖥️ Interactive Simulator

**Washington EV Adoption Simulator**  
🔗 https://home-page-ev.onrender.com/

- Statewide forecasting by year  
- County-level forecasting by county + year  

---
![Statewide_Map](https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/img/maps/WA_supercharger_population_map_large.png)
## 📌 Project Overview

Tesla’s long-term EV sales growth depends on delivering a reliable, anxiety-free charging experience.  
This capstone develops a **data-driven forecasting framework** to evaluate whether Tesla can expand Supercharger infrastructure in Washington State in a way that:

- Reduces charging anxiety  
- Sustains long-term EV adoption  
- Aligns with Washington’s decarbonization mandates  
- Remains feasible within Tesla’s fixed annual infrastructure budget  

The project converts EV adoption and charging demand from an uncertain planning problem into a **predictable, year-by-year strategy**.

---

## 🎯 Objectives

- Forecast **EV adoption (2024–2050)** at the county and statewide level  
- Estimate **Supercharger demand** under geographic and population-driven constraints  
- Evaluate **budget feasibility** under Tesla’s $500M annual expansion budget  
- Translate long-term policy targets into **annual charger deployment plans**  
- Build an **interactive simulator** for county- and statewide forecasting  

---

## 🧭 Policy & Planning Framework

### Washington State Policy Targets
- **45% EV adoption by 2030**
- **70% by 2040**
- **95% by 2050**
- **80% of charging from home/workplace (L1/L2) by ~2030**

These targets anchor all adoption trajectories and constrain long-run outcomes.

### Infrastructure Planning Assumptions
- **Urban/Suburban coverage:** 2–5 mile radius  
- **Rural coverage:** up to 15 mile radius  
- **Population-based charger ratios:**  
  - Urban: ~1 per 1,500–2,500 residents  
  - Suburban: ~1 per 2,500–6,000  
  - Rural: ~1 per 5,000–15,000  

---

## 📊 Data Sources

- **Population (Age 25–59):** U.S. Census (ACS)  
- **EV Registrations (VIN-based, 2024):** Kaggle EV Dataset  
- **Tesla Supercharger Locations:** Tesla Supercharger Map  
- **County Boundaries:** ArcGIS REST API
  
All datasets are cleaned, standardized, and merged at the county level.

📁 View source code: 
https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/notebooks/Supercharger_VINGeocoding.ipynb

---

## 🗺️ Spatial Analysis (GIS)

A GIS-based analysis visualizes mismatches between:
- Population demand  
- Existing Supercharger coverage  

Key insights:
- Dense population clusters with limited charging access  
- Overloaded urban corridors  
- Large rural gaps requiring early geographic coverage  

This spatial profiling informs both **minimum coverage needs** and **priority deployment zones**.


📁 View source code: 
https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/notebooks/map.ipynb

---

## 🧪 Modeling Approach

### County Archetypes (4 → 39 Scaling)
Four prototype counties represent Washington’s diversity:
- **King:** Urban  
- **Pierce:** Urban/Suburban  
- **Kitsap:** Suburban  
- **Chelan:** Rural / Forest  

All 39 counties inherit behavior from the closest archetype based on population density.

---

### Adoption Phases (2025–2050)

1. **Phase 1 (2025–2030):** Rapid growth, heavy Supercharger expansion  
2. **Phase 2 (2030–2040):** Shift toward 80% home charging, moderated growth  
3. **Phase 3 (2040–2050):** Market saturation and slower expansion  

---

## 📈 Forecasting Engine

### Monte Carlo + Time-Series Modeling
- **1,000 stochastic adoption paths per county**
- Bounded by:
  - **Lower bound:** geographic coverage minimum  
  - **Upper bound:** population-driven charger demand  

Key mechanics:
- Charger momentum effect (trailing 3-year growth)
- Phase-specific volatility and mean reversion
- Monotonic adoption enforcement
- Saturation cap at **95% adoption**
- Charger growth capped at **50% per year**

📁 View source code: 
https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/notebooks/lower%20and%20upper%20bound.ipynb
https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/notebooks/4%20counties%20modeling.ipynb

---

## 🔢 Curve Fitting & Forecast Functions

For each county and statewide:
- Best-fit models selected from:
  - Linear  
  - Quadratic  
  - Cubic  
  - Logistic  
- Selection based on **highest R²**

### Statewide Best-Fit Models
- **Charge Points vs Year:** Cubic (R² ≈ 0.94)  
- **EV Adoption vs Year:** Quadratic (R² ≈ 0.92)

These equations enable **year-by-year deployment planning**.

---

## 🏗️ Statewide Aggregation

Statewide results are built by **aggregating county forecasts**, preserving local dynamics while producing a unified planning view:
- EV counts  
- Charger counts  
- Population-weighted adoption rates

📁 View source code: 
https://github.com/judyc4986/MODELING-EV-ADOPTION-AND-SUPERCHARGER-DEMAND/blob/main/notebooks/Scale%20Up.ipynb

---

## 💰 Budget & Feasibility Analysis

- Tesla annual expansion budget: **$500M**
- 80% allocated to top 6 EV-leading states
- **Washington share:** ≈ **$28.2M**

At ~$42,500 per stall:
- ≈ **663 stalls**
- ≈ **110 sites** (6 stalls per site)

**Conclusion:**  
Early front-loading exceeds annual limits in 2025–2026 but remains **fully affordable over the full horizon**, with slower deployment later offsetting early investment.

---

## 🔍 Key Insights

- **Statewide EV adoption converges near ~88–90% by 2050**, not 95%  
- Structural barriers prevent full saturation:
  - Rural travel distances  
  - Fleet replacement cycles  
  - Specialty and utility vehicle segments  
- **Wide geographic coverage beats urban clustering**
- Dense counties drive statewide outcomes due to population weight

---

## 🔄 Model Lifecycle

- **5-year recalibration cycle**
  - Years 1–4: Monitor & adjust within forecast bands  
  - Year 5: Re-estimate with updated population, EVs, chargers, and behavior  

Balances long-term stability with real-world adaptability.

---

## ✅ Conclusion

This capstone demonstrates that EV adoption and charging demand can be **modeled, forecasted, and budgeted with confidence**.  
With disciplined, data-driven planning, Tesla can expand Supercharger infrastructure in Washington in a way that:

- Reduces charging anxiety  
- Sustains EV sales growth  
- Maximizes return on capital  
- Supports long-term decarbonization goals  

---

## 📎 Author

**Judy Cheng**  
Finance, Cost Accounting, and Data Analytics  
Capstone: EV Adoption & Infrastructure Forecasting (2024–2050)

