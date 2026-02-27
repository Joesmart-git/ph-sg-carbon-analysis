# Diverging Paths: Carbon Emissions in the Philippines vs. Singapore

[![View Visual Case Study on Notion](https://img.shields.io/badge/View_Visual_Case_Study-Notion-black?logo=notion)](https://whispering-crater-183.notion.site/Project-Diverging-Paths-Carbon-Emissions-in-the-Philippines-vs-Singapore-313e54702f0b80d6b704cf2b001910a6?source=copy_link) 

## Project Overview
This project analyzes and compares the carbon emission drivers between a lower-middle-income archipelago (The Philippines) and a high-income city-state (Singapore). 

By analyzing historical emissions data alongside population and economic indicators, this project bridges raw environmental data with strategic insights regarding how national income brackets dictate energy transitions.

* **Tools Used:** Power BI, DAX
* **Role:** Data Analyst

## Strategic Insights
The analysis revealed two primary drivers of carbon emission divergence:

* **Scale vs. Efficiency:** The Philippines produces a vastly larger and rapidly growing absolute volume of CO2 (peaking in 2018), which is strongly correlated with its massive population growth. Conversely, Singapore's absolute emissions are lower, but it maintains a dense carbon footprint relative to its size.
* **The Energy Mix Transition:** The primary divergence lies in fuel sources, dictated heavily by income group. The lower-middle-income Philippines is fueling its rapid growth with a massive surge in Coal usage. Meanwhile, high-income Singapore has completely transitioned its energy mix away from coal, relying entirely on Oil and Gas.
* **Conclusion:** Population size acts as a baseline multiplier for emissions, but a nation's economic bracket ultimately dictates its carbon sources.

## Technical Implementation: Advanced DAX & Modeling
To ensure the dashboard was scalable and analytically rigorous, explicit DAX formulas were written rather than relying on implicit aggregations. Below are key snippets of the logic used in this analysis:

### 1. Handling Semi-Additive Measures
Population cannot be summed across multiple years without heavily distorting the data. A dynamic DAX formula was created using variables and `CALCULATE` to isolate and sum the population for only the most recently selected year.

```dax
Latest Population = 
VAR MaxYear = MAX('ph_sg_co2'[year])
RETURN
CALCULATE(
    SUM('ph_sg_co2'[population]),
    'ph_sg_co2'[year] = MaxYear
)
```

### 2. Safe Divide for Per-Capita Analysis
Comparing a massive archipelago to a city-state requires per-capita analysis. To prevent division-by-zero errors when multiplying raw tonnage by population, a safe divide measure was implemented.
```
CO2 per Capita (Tonnes) = 
DIVIDE(
    [Total CO2] * 1000000,
    [Total Population],
    0
)
```

## Repository Structure
* `/data` - Contains the dataset used for the Power BI model.
* `Project Diverging Paths Carbon Emissions in the Philippines vs Singapore.pbix` - The core interactive Power BI file.

## Let's Connect
If you're looking for a Data Analyst who can turn complex datasets into clear, actionable business insights, let's connect.

* **Email:** joesmartverdilloapan@gmail.com 
* **LinkedIn:** [Joesmart V. Apan](https://www.linkedin.com/in/joesmart-apan-7735ab215)
