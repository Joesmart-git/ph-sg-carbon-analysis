# Diverging Paths: Carbon Emissions in the Philippines vs. Singapore

[![View Visual Case Study on Notion](https://img.shields.io/badge/View_Visual_Case_Study-Notion-black?logo=notion)](https://whispering-crater-183.notion.site/Project-Diverging-Paths-Carbon-Emissions-in-the-Philippines-vs-Singapore-313e54702f0b80d6b704cf2b001910a6?source=copy_link) *(Note: Paste your Notion link replacing the # inside these parentheses)*

## Project Overview
[cite_start]This project analyzes and compares the carbon emission drivers between a lower-middle-income archipelago (The Philippines) and a high-income city-state (Singapore)[cite: 6]. 

By analyzing historical emissions data alongside population and economic indicators, this project bridges raw environmental data with strategic insights regarding how national income brackets dictate energy transitions.

* [cite_start]**Tools Used:** Power BI, DAX [cite: 5]
* [cite_start]**Role:** Data Analyst [cite: 4]

## Strategic Insights
The analysis revealed two primary drivers of carbon emission divergence:

* [cite_start]**Scale vs. Efficiency:** The Philippines produces a vastly larger and rapidly growing absolute volume of CO2 (peaking in 2018), which is strongly correlated with its massive population growth[cite: 9]. [cite_start]Conversely, Singapore's absolute emissions are lower, but it maintains a dense carbon footprint relative to its size[cite: 10].
* [cite_start]**The Energy Mix Transition:** The primary divergence lies in fuel sources, dictated heavily by income group[cite: 11]. [cite_start]The lower-middle-income Philippines is fueling its rapid growth with a massive surge in Coal usage[cite: 12]. [cite_start]Meanwhile, high-income Singapore has completely transitioned its energy mix away from coal, relying entirely on Oil and Gas[cite: 13].
* [cite_start]**Conclusion:** Population size acts as a baseline multiplier for emissions, but a nation's economic bracket ultimately dictates its carbon sources[cite: 14].

## Technical Implementation: Advanced DAX & Modeling
[cite_start]To ensure the dashboard was scalable and analytically rigorous, explicit DAX formulas were written rather than relying on implicit aggregations[cite: 201]. Below are key snippets of the logic used in this analysis:

### 1. Handling Semi-Additive Measures
[cite_start]Population cannot be summed across multiple years without heavily distorting the data[cite: 203]. [cite_start]A dynamic DAX formula was created using variables and `CALCULATE` to isolate and sum the population for only the most recently selected year[cite: 204].

```dax
Latest Population = 
VAR MaxYear = MAX('ph_sg_co2'[year])
RETURN
CALCULATE(
    SUM('ph_sg_co2'[population]),
    'ph_sg_co2'[year] = MaxYear
)
