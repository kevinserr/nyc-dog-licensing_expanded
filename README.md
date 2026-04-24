# 🐶 NYC Dog Licensing Dashboard

## Project Overview

This project uses real dog licensing data from New York City to explore trends in pet ownership across ZIP codes, time, breed, and dog age. The goal is to identify patterns that can help city agencies or animal organizations plan more effective and better-targeted town halls for dog owners.  
The project includes data cleaning and feature engineering in Python, followed by interactive visualizations built in Tableau.

## Stakeholder Description

**Stakeholder:** New York City Director of Animal Services.

The goal is to help the stakeholder connect with dog owners by hosting seasonal town halls, sharing resources, and educating the public about dog licensing and pet care.
These insights connect directly to public health by emphasizing the importance of early dog registration—ideally within the year a puppy is born—to promote timely vaccinations and responsible pet ownership.

## Core Business Question
> **Are there patterns in current dog licensing rates that help us plan and promote future town halls more effectively?**

The dashboard answers this question by identifying:
- The lowest and highest rates of dog license issuance across NYC boroughs.
- When licenses are issued most frequently.
- The average age at which dogs are licensed.
- The dog age distribution.

---

## Exploratory Data Analysis (EDA) in Python
**Tools Used:** `pandas`, `matplotlib`, `seaborn`, and `plotly`

### 1. Data Cleaning
Our team started its data cleaning process by making sure each column was in the correct format. This included:
- Renaming the columns for easy data handling.
- Removing rows with missing values (e.g., gender, breed, ZIP, date). We dropped 1,810 rows in the `name` column, 21 rows in `Gender`, and 82 in `License expire date`. These rows were dropped because they represent only 1% of all data in the dataset.
- Checking and correcting data types for each column.
- Creating a `get_borough()` function that maps ZIP codes to boroughs using a custom dictionary. For example, ZIP codes from 10001–10282 are assigned to Manhattan.

### 2. Feature Engineering
We created three new columns to help surface deeper insights from the data:
- `DogAgeAtLicense`: Calculated age based on birth year and license date.
- `IssueMonth` and `IssueYear`: Extracted from the license issue date.
- Filtered out unrealistic ages (<0 or >25). Dogs appearing to be 30 years old are likely data errors, and ages above 25 are extremely rare. Rows outside this range were removed.

### 3. Export
The final cleaned dataset is saved as `final_dataset.csv` for use in Tableau.

---

## Tableau Workflow / Visualizations

After importing the cleaned dataset into Tableau, our team created visualizations focused on neighborhoods with the highest and lowest dog licenses issued, and the average ages of dogs at licensing — supporting awareness and public health safety.

Our dashboard allows users to:
- Filter by borough and license issue year.
- View boroughs with the highest and lowest dog license rates.
- Analyze the average age of dogs at license issuance.

This dashboard helps stakeholders identify where outreach and town halls are most needed.

Find the final interactive dashboard built in Tableau here: [Dashboard](https://public.tableau.com/app/profile/kevin.serrano6220/viz/MODproject_17526900544830/Dashboard1?publish=yes)

Find the expanded policy & outreach dashboard here: [Expansion Dashboard](https://public.tableau.com/app/profile/kevin.serrano6220/viz/Dashboard_2_0_17763041091450/Dashboard2?publish=yes)

---

## Expansion

Building on the original project, this expansion reframes the dashboard for a policy audience — specifically the NYC Department of Health and Mental Hygiene — and introduces normalized metrics to enable fairer comparisons across boroughs.

### What was added

**Feature Engineering**
- Added a `dogs_per_1000` metric normalizing license counts by borough population. This surfaces the Bronx as the most under-licensed borough in the city — a finding that raw counts alone would not reveal.
- Computed `pct_of_total_dogs`, `unique_breeds`, and `density_rank` per borough to support richer comparisons.
- Generated a `borough_summary_tableau.csv` file containing all pre-aggregated metrics, ready for direct connection in Tableau.

**Dashboard Enhancements**
The Tableau dashboard was redesigned with a policy and outreach focus, including:
- A normalized horizontal bar chart showing dogs per 1,000 residents with a diverging red-to-green color scale centered at the citywide average.
- A grouped bar chart comparing each borough's share of licenses vs. share of city population, making licensing gaps immediately visible.
- An outreach priority map color-encoded by per-capita licensing rate.
- Insight-driven chart titles replacing descriptive labels (e.g., "Three boroughs fall below the citywide average of 91 per 1,000").
- KPI tiles for total licenses, citywide average, and number of boroughs needing outreach.
- Interactive filters with a borough dropdown and year slider.

**Documentation**
- Added stakeholder-facing recommendations covering targeted outreach priorities, COVID-era license lapse follow-up, and next steps for integrating external datasets such as ACS income data.

---

## Business Recommendations

Based on our findings, we propose the following:

- **Increase licensing in underrepresented boroughs.** Focus outreach efforts in the Bronx (51 dogs per 1,000 residents) and Brooklyn (73 per 1,000), which fall furthest below the citywide average of 91 per 1,000.
- **Promote early licensing (<2 years old).** Tailor content to new dog owners and puppies, since most dogs are licensed under 3 years old. This improves vaccination tracking and contributes to rabies prevention.
- **Follow up on 2020 COVID adopters.** Licensing spiked 40% in 2020 during pandemic-era adoptions. Many of those licenses may have since lapsed — a targeted renewal campaign for 2020–2021 cohorts could recover significant compliance.
- **Integrate income and housing data.** Merging with ACS data would allow the Department of Health to distinguish between low ownership rates and low compliance rates, which is critical for designing the right intervention.
- **Host targeted town halls.** Prioritize areas with low licensing rates and boroughs with high numbers of older, unlicensed dogs (>5 years old).

These efforts support:
- Stronger community relationships
- Enhanced public safety
- Improved animal care and control
- Higher rates of responsible pet ownership citywide

---

## Project Reflection

**Most Important Insight**
> Most licenses are issued in the spring and early summer, and a large number are for very young dogs. This suggests town halls should focus on new dog owner support and be held between **April and July**, in areas with high registration activity.
> The dashboard also reveals that late licensing can lead to missed vaccinations, raising public health risks — particularly related to rabies, which poses a danger to both pets and humans.
> The expansion further shows that raw license counts are misleading: normalizing by population reveals the Bronx as the most underserved borough, with a per-capita rate nearly 3x lower than Manhattan.

**Prioritizing Dashboard Features**
> Given time constraints, we prioritized visualizations that directly aligned with our business question — highlighting licensing rates across boroughs and showcasing dog age distribution. The expansion added normalization and policy framing to make those insights actionable for a government stakeholder audience.

---

## Repo Navigation
```
├── data/
│   ├── raw/
│   │   └── NYC_Dog_Licensing_Dataset_20250713.csv
│   └── cleaned/
│       ├── final_dataset.csv
│       └── borough_summary_tableau.csv
├── notebooks/
│   └── data_cleaning.ipynb
└── README.md
```

---

## Contributors

**Original project**
- Ibrahima Diallo: [LinkedIn](https://www.linkedin.com/in/ibranova/)
- Kevin Serrano Lopez: [LinkedIn](https://www.linkedin.com/in/kevin-serrano-lopez/)
- Itzel Sanchez: [LinkedIn](https://www.linkedin.com/in/itzel-sanchez-8932b6334/)
