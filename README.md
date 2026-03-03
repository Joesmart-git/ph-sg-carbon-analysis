# Diverging Paths: Carbon Emissions in the Philippines vs. Singapore

[![View Visual Case Study on Notion](https://img.shields.io/badge/View_Visual_Case_Study-Notion-black?logo=notion)](https://whispering-crater-183.notion.site/Project-Diverging-Paths-Carbon-Emissions-in-the-Philippines-vs-Singapore-313e54702f0b80d6b704cf2b001910a6?source=copy_link) 

## Project Overview
This project analyzes and compares the carbon emission drivers between a lower-middle-income archipelago (The Philippines) and a high-income city-state (Singapore). 
<img width="1289" height="1070" alt="image" src="https://github.com/user-attachments/assets/4c80e2e8-e925-4652-9fa8-598ed570bb8d" />
By analyzing historical emissions data alongside population and economic indicators, this project bridges raw environmental data with strategic insights regarding how national income brackets dictate energy transitions.

### Data Sourcing & Provenance ###
The dataset was sourced from Our World in Data, specifically focusing on historical CO2 emissions, energy mix transitions, and macro-population metrics for Southeast Asia.
Because the data originated from a highly credible, standardized pipeline, extensive pre-processing and wrangling were not required. Instead, the focus of this pipeline was dedicated to data modeling and DAX optimization—ensuring that semi-additive measures (like historical population) and per-capita ratios computed accurately across dynamically filtered timelines and income brackets.

* **Tools Used:** Power BI, DAX
* **Role:** Data Analyst

## Strategic Insights ##
The analysis revealed two primary drivers of carbon emission divergence:

* **Scale vs. Efficiency:** The Philippines produces a vastly larger and rapidly growing absolute volume of CO2 (peaking in 2018), which is strongly correlated with its massive population growth. Conversely, Singapore's absolute emissions are lower, but it maintains a dense carbon footprint relative to its size.
* **The Energy Mix Transition:** The primary divergence lies in fuel sources, dictated heavily by income group. The lower-middle-income Philippines is fueling its rapid growth with a massive surge in Coal usage. Meanwhile, high-income Singapore has completely transitioned its energy mix away from coal, relying entirely on Oil and Gas.
* **Conclusion:** Population size acts as a baseline multiplier for emissions, but a nation's economic bracket ultimately dictates its carbon sources.

## Executive Dashboard and Key Findings ##
### 1. What's the highest year for Carbon Emissions? ###
The Philippines' emissions have surged continuously, peaking in 2018. Singapore, conversely, saw its emissions peak in 2015 and have since plateaued or slightly declined.
<img width="1259" height="553" alt="image1" src="https://github.com/user-attachments/assets/4f59fcb9-021d-495c-9a7c-cbd6d28f1cdf" />

### How's the trend in population for Philippines? For Singapore? ###
The Philippines is experiencing rapid, compounding population growth, surging well past 100 million. Singapore's population is also growing steadily, but on a vastly smaller, more controlled scale of around 6 million. This massive difference in sheer human volume is the critical context needed before comparing their total carbon footprints
<img width="1138" height="448" alt="image2" src="https://github.com/user-attachments/assets/d4a03c14-dd8f-46e0-92a1-87a52e6930f5" />

### 3. Is population a big factor for Carbon Emissions? ###
Yes. Both countries show a strong, positive correlation between population growth and total CO2 emissions, indicating that headcount acts as a baseline multiplier for a nation's carbon footprint.
<img width="1442" height="1073" alt="image3" src="https://github.com/user-attachments/assets/2c86b66c-8ed3-4ba1-9d68-fbe4100e6725" />

### 4. How's the performance of Philippines and Singapore in comparison to the world? ###
The two nations are on entirely diverging trajectories on the global stage. The Philippines is capturing a rapidly growing share of total global emissions (surging past 1.5%), indicating highly carbon-intensive industrial growth. Conversely, Singapore's share of global emissions peaked in the mid-1990s and has steadily declined since, suggesting a maturing economy that is successfully decoupling its wealth generation from raw carbon output.
<img width="1271" height="729" alt="image4" src="https://github.com/user-attachments/assets/c53aceea-bac6-4a70-8fe9-d403c3adf94a" />

### 5. How do their emission sources compare, and does income play a role? ###
This is where the two countries diverge. The Philippines (Lower-Middle Income) relies heavily on Coal to fuel its growth. Singapore (High Income) relies entirely on Oil and Gas, mirroring the broader global trend where high-income nations abandon coal for gas.
<img width="1631" height="1073" alt="image5" src="https://github.com/user-attachments/assets/2721c8ba-cdda-46a0-b764-01141f008ff0" />
<img width="1642" height="647" alt="image6" src="https://github.com/user-attachments/assets/4526f6cb-3544-4188-8735-6e842889e150" />

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
* [Expanded SEA Dataset (PHP SG).xlsx](Expanded%20SEA%20Dataset%20(PHP%20SG).xlsx) - The dataset used for the Power BI model.
* [Project Diverging Paths Carbon Emissions in the Philippines vs Singapore.pbix](Project%20Diverging%20Paths%20Carbon%20Emissions%20in%20the%20Philippines%20vs%20Singapore.pbix) - The core interactive Power BI file.

## Let's Connect
If you're looking for a Data Analyst who can turn complex datasets into clear, actionable business insights, let's connect.

* **Email:** joesmartverdilloapan@gmail.com 
* **LinkedIn:** [Joesmart V. Apan](https://www.linkedin.com/in/joesmart-apan-7735ab215)
