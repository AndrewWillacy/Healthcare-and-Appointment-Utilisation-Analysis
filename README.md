# NHS Healthcare Appointment, Utilisation & Capacity Analysis

**Healthcare Operations Analytics Project | 2025**

> *How can healthcare appointment and utilisation data be used to improve operational planning, reduce missed appointments, and support more effective capacity management across a national healthcare system?*

---

## Executive Summary

This project analyses large-scale NHS appointment and utilisation data to identify operational trends, capacity pressures, missed appointment patterns, and data quality issues impacting healthcare planning and service delivery.

Using Python, Excel, and exploratory data analysis techniques, the project investigates over one million healthcare appointment records across 106 Sub-ICB locations and seven regions. The analysis explores appointment utilisation, seasonal demand patterns, HCP trends, service setting performance, missed appointment behaviour by wait time and geography, and operational strain across the healthcare network.

The project combines structured data cleaning, validation, exploratory analysis, geographic mapping, and visualisation to transform raw operational healthcare data into actionable business insight.

**A major finding of the project was that data quality limitations - particularly unmapped appointment categories, inconsistent recording practices, and an unrealistic capacity benchmark - represented a more significant barrier to reliable decision-making than analytical complexity itself.**

Key findings included:

- General Practice accounted for 91.5% of appointments across the network
- The system operated at an average of **103.2% of its stated daily capacity** across the analysis period; October 2021 was the worst month at **120.3%** of weekday capacity
- Missed appointments (DNA) consistently represented **4–5%** of all appointments; a further 4–5% had unknown status
- **Same-day appointments had a ~19.8% DNA rate** - nearly 1 in 5 not attended
- The top 10 highest-DNA Sub-ICB regions ranged from **4.7%–5.8%**, concentrated in the Midlands and London (NHS Black Country and NHS Greater Manchester worst affected)
- Significant data quality issues - particularly the dominant 'Unknown' category - reduced confidence in utilisation reporting
- Appointment demand increased steadily following Covid disruption, with clear seasonal patterns (autumn/winter capacity consistently breached)
- Social media data demonstrated limited analytical value in current form but potential for structured future use

---

## Business Problem

The NHS faces increasing demand against constrained resources. With an ageing population and post-Covid recovery pressures, understanding how capacity is being used - and where appointments are being missed - is essential for budget planning and infrastructure decisions.

Healthcare stakeholders needed to better understand:

* Whether current staffing and network capacity were sufficient
* How healthcare resources were actually being utilised
* Where operational bottlenecks and inefficiencies existed
* What trends could be identified in missed appointments
* Whether external data sources such as social media could support operational insight and public engagement

The analysis aimed to support:

* Capacity planning
* Operational resource allocation
* Service utilisation analysis
* Missed appointment reduction strategies
* Data-driven healthcare decision-making

---

## Data Sources

| Source | Data Collected | Purpose |
|---|---|---|
| **actual_duration.csv** | Appointment durations, locations, dates, appointment counts | Utilisation and duration analysis |
| **appointments_regional.csv** | Appointment types, modes, booking lead times, appointment status | Regional operational analysis (21,604 duplicates removed) |
| **national_categories.csv** | National appointment categories and service settings | Capacity and service trend analysis |
| **NHS-ICB_names.csv** | NHS ICB reference file (downloaded from NHS website) | Merged with appointments_regional for location name analysis |
| **tweets.csv** | NHS-related social media data | Sentiment and engagement exploration |
| **sub_icb_boundaries_geojson.geojson** | ONS Sub-ICB boundary file | Geographic mapping of DNA rates by region |

The combined datasets covered:
- 106 Sub-ICB healthcare locations across 7 NHS regions
- 42 ICB locations
- Data spanning January 2020 – June 2022 (Covid and post-Covid recovery period)
- Over 1 million appointment-related records

---

## Tools & Skills Used

| Category                        | Tools / Methods                                          |
| ------------------------------- | -------------------------------------------------------- |
| **Data Cleaning & Preparation** | Python, Pandas, Excel                                    |
| **Exploratory Analysis**        | Pandas, NumPy                                            |
| **Data Visualisation**          | Matplotlib, Seaborn                                      |
| **Analysis Techniques**         | Trend analysis, anomaly detection, utilisation analysis  |
| **Reporting**                   | Stakeholder reporting, operational insight communication |

**Skills demonstrated:**

Data cleaning and validation · Large-scale dataset handling · Exploratory data analysis · Seasonal trend analysis · Geographic data visualisation · DNA pattern analysis · Anomaly detection · Data quality assessment · Operational reporting · Healthcare utilisation analysis · Stakeholder-focused insight communication

---
## Analytical Approach

The project followed a structured workflow combining data cleaning, exploratory analysis, visualisation, operational interpretation, and recommendation development.

### 1. Data Ingestion, Cleaning & Validation

The raw datasets were imported into Python and assessed for quality, consistency, missing values, and structural reliability.

Key preparation activities included:

- Validation of missing values and removal of 21,604 duplicate records from appointments_regional
- Standardisation of date formats (dd-mmm-yy in actual_duration vs dd/mm/yyyy in national_categories — standardised to dd/mm/yyyy)
- Conversion of national_categories.xlsx to CSV format for consistency
- Merge of NHS-ICB names reference file on ICB ONS code to add readable location names
- Validation of categorical variables and data type standardisation
- Handling of inconsistent or unmapped values

A significant focus of the project involved assessing the reliability of the underlying operational data.

Key data quality issues identified included:

| Issue Identified | Impact |
|---|---|
| High levels of unmapped appointment categories | Reduced reporting reliability across multiple metrics |
| 'Unknown' category dominant in key metrics | Limits confidence in duration, status, and utilisation analysis |
| Fixed daily capacity benchmark (1.2M) applied to all days including weekends | Fundamentally distorts utilisation calculations |
| Inconsistent appointment recording practices | Distorts operational analysis |
| Duplicate records in regional appointment data (21,604 removed) | Inflated reporting outputs |

> **Key data quality finding:** The primary limitation affecting operational insight was not analytical capability, but inconsistent and unreliable operational data capture. The 'Unknown' category was frequently the largest single value in key metrics — treated as a systemic recording failure rather than random missingness.

---

### 2. Exploratory Data Analysis

Exploratory analysis was conducted using Python to identify utilisation trends, seasonal patterns, operational pressures, HCP behaviour, and missed appointment patterns.

**Scale and structure:**
- 106 Sub-ICB locations across 7 regions; NHS North West London ICB was the highest-volume location (12.1M appointments, 4.1% of total)
- General Practice accounted for 91.5% of all appointments — national patterns are almost entirely GP-driven
- Face-to-face was the most common appointment mode; telephone increased dramatically during Covid lockdowns and remained elevated post-restriction

**Volume trends:**
- November 2021 recorded the highest monthly appointment volume (30.4 million)
- August 2021 recorded the lowest (23.9 million)
- Steady upward trend across the period, with a visible dip during lockdowns followed by recovery

Figure 1: Monthly Appointment variation across the period analysed
<img width="1200" height="450" alt="Screenshot 2026-07-11 171410" src="https://github.com/user-attachments/assets/52725805-4022-46bb-8463-3959bb962f5e" />

**Seasonal patterns:**
- Summer (Aug 2021): volumes below capacity benchmark across all weeks
- Autumn (Sep–Nov 2021): capacity consistently breached from October; predictable seasonal pressure
- Winter (Dec 2021–Feb 2022): more variability; Christmas week near-zero across all settings
- Spring (Mar–May 2022): appointments concentrated Monday–Wednesday; Easter dip visible

**HCP trends:**
- GP appointments dominated throughout; Other Practice Staff and Unknown HCP types showed distinct seasonal patterns — rising in autumn and spring, contrasting with GP winter peak pressure

Figure 2: Monthly Appointments by Healthcare Professional
<img width="2066" height="788" alt="Screenshot 2026-07-10 145357" src="https://github.com/user-attachments/assets/ce121342-62d2-4fbe-8237-7a30df43577f" />

---

### 3. Capacity & Utilisation Analysis

A major focus of the project involved analysing actual capacity utilisation against the NHS stated benchmark of 1.2 million appointments per day.

| Month | Total Appointments | Utilisation |
|---|---|---|
| October 2021 | 30.3 million | 120.3% — worst crisis month |
| November 2021 | 30.4 million | 115.2% |
| August 2021 | 23.9 million | Lowest in period |
| Average across period | — | 103.2% — above benchmark every month |

**Day-of-week:** Tuesday was consistently the highest-volume day; capacity breached on Monday and Tuesday in ~90% of weeks. Friday was the only day where the majority of weeks remained within capacity. Weekends had near-zero appointments, confirming the 1.2M daily benchmark is meaningless when applied uniformly.

Figure 3: Average Daily Appointments by day of week (Note 1.2 Million Max capacity red horizontal line)
<img width="1000" height="450" alt="Screenshot 2026-07-11 172210" src="https://github.com/user-attachments/assets/b23cd8ce-9793-47b5-a666-822546d20db6" />

---

### 4. Missed Appointment Analysis

Missed appointments (DNA) consistently represented 4–5% of all appointments. A further 4–5% had unknown status — meaning the true non-attendance rate may be as high as 9% but cannot be confirmed from the data.

**By wait time (distribution of DNA appointments):**

| Wait Time Category | Share of Total DNAs | Note |
|---|---|---|
| 2–7 days | Highest share | Largest single category of missed appointments |
| Same day | ~19.8% | Nearly 1 in 5 same-day appointments not attended |
| 22+ days | Lowest share | Patients with longer lead times show stronger attendance commitment |

The structural stability of the DNA distribution over time is itself significant — the pattern remained broadly consistent throughout the Covid period, suggesting this is a structural feature of NHS appointment behaviour requiring deliberate intervention rather than post-pandemic normalisation.

Figure 4: Percentage of Missed Appointments (DNA) by Wait times
<img width="900" height="400" alt="Screenshot 2026-07-10 164231" src="https://github.com/user-attachments/assets/cab419ed-186b-46d3-9c94-9bca7bf2fd08" />

**By Sub-ICB Region:**
- Top 10 highest-DNA regions: 4.7%–5.8%
- NHS Black Country, NHS Greater Manchester, and NHS Birmingham & Solihull — all Midlands regions — showed the worst confirmed DNA rates
- Geographic mapping confirmed concentration in densely populated urban areas (Midlands and London)
- The same regions also showed the highest Unknown status rates (3.9%–4.8%), suggesting recording quality and non-attendance risk are geographically correlated

Figure 5: Top DNA Sub_ICB Regions
<img width="1500" height="700" alt="Screenshot 2026-07-10 155825" src="https://github.com/user-attachments/assets/43e83a6d-98df-4cb8-923d-ddf399ebe6d7" />

**By Service Setting:**

GP has the highest DNA rate, although this should be considered in the context of General Practice accounting for 91.5% of appointments. More notable is that DNA rates in other service settings are not substantially lower despite those settings accounting for far fewer appointments.

Figure 6: DNA by Service Setting
<img width="2103" height="863" alt="Screenshot 2025-08-09 142700" src="https://github.com/user-attachments/assets/c69dd430-3225-4be4-bb03-cc1d06f1fefc" />

---

### 5. Social Media Analysis

Twitter (X) data was analysed to explore potential value for operational insight. The most frequent hashtag was #healthcare — appearing nearly ten times more than the second. Most tweets received zero retweets and likes.

The analysis investigated:

* Trending healthcare hashtags
* Public discussion themes
* Potential sentiment indicators
* Opportunities for patient engagement analysis

Key observations included:

* Frequent use of hashtags including:

  * #healthcare
  * #health
  * #medicine

> The data in its current form has limited analytical value. The hashtag frequency analysis provides directional information about topics but no reliable sentiment signal. The dataset was treated as indicative of potential rather than a source of actionable insight — and this was communicated explicitly rather than overstated.

---

## Key Findings & Recommendations

### Finding 1: Reported Utilisation Exceeded the Stated Capacity Benchmark

Reported utilisation averaged 103.2% of the stated daily capacity benchmark across the analysis period, reaching 120.3% in October 2021. This apparent over-utilisation prompted further investigation of both appointment demand and the underlying capacity assumption.

Appointment demand showed an overall increase across the analysed period, particularly following Covid-related disruption

| Trend                            | Operational Interpretation                |
| -------------------------------- | ----------------------------------------- |
| Rising appointment volumes       | Increasing pressure on NHS infrastructure |
| Winter utilisation spikes        | Seasonal operational strain               |
| Increased telephone appointments | Covid-driven service adaptation           |

Figure 7: Monthly Appointments by Healthcare provider
<img width="2600" height="1000" alt="Screenshot 2026-07-10 145357" src="https://github.com/user-attachments/assets/17187059-5483-43bb-a0e8-20c6d6e5e790" />

> **Recommendation:** Develop a demand-weighted capacity model reflecting actual working day availability by day type and season. Align staffing resources to predictable seasonal patterns, particularly the autumn/winter peak.

---

### Finding 2: Data Quality Issues Limited Operational Insight

Large volumes of unmapped and inconsistently recorded data — particularly the dominant 'Unknown' category — reduced confidence in reporting outputs across multiple metrics.

| Data Quality Issue               | Business Impact                  |
| -------------------------------- | -------------------------------- |
| Unmapped appointment categories  | Reduced reporting reliability    |
| Inconsistent recording standards | Distorted utilisation analysis   |
| Static capacity assumptions      | Misleading operational reporting |

Figure 8: Data quality issues (Example) - Note rise in unknown/Data quality over the period
<img width="1600" height="600" alt="Screenshot 2026-07-10 154635" src="https://github.com/user-attachments/assets/c3d97ba1-485f-462b-bfb6-97fee740e896" />

> **Recommendation:** Prioritise improvements to operational data capture processes before implementing more advanced analytical or forecasting models.

---

### Finding 3: Missed Appointments Are a Structural Problem

DNA rates of 4–5% were consistent across the period with no improvement trend — this is a structural feature requiring deliberate intervention. Same-day appointments (~19.8% DNA rate) are the highest-risk category. Geographic concentration in the Midlands and London suggests targeted regional intervention is more appropriate than uniform national campaigns.

These missed appointments:

* Reduced operational efficiency
* Increased pressure on healthcare services
* Created financial waste
* Reduced appointment availability for other patients

Figure 9: Monthly Appointments by Attendance Status
<img width="1354" height="505" alt="Screenshot 2025-08-08 160941" src="https://github.com/user-attachments/assets/c87339bd-1ad2-4fe8-b966-ea48610b5e00" />

> **Recommendation:** Introduce proactive appointment reminder and rescheduling systems (SMS, email, digital self-service). Deploy interventions differentially by region and wait time category rather than uniformly.

---

### Finding 4: The Capacity Benchmark Is Fundamentally Misconfigured

The use of a fixed 1.2 million daily capacity figure - applied uniformly including weekends when GP practices are closed - creates a systematic distortion in all downstream utilisation reporting.

> **Recommendation:** Rebuild the capacity benchmark using actual working day and appointment availability patterns. Develop dynamic capacity models aligned to seasonal demand, day-of-week variation, and regional operational pressures.

---

### Finding 5: Social Media Requires Investment to Become Useful

The current Twitter dataset demonstrates the gap between ad hoc data and analytically useful data.

> **Recommendation:** Develop a structured social media monitoring framework across multiple platforms with consistent metadata, volume, and geographic tagging.

---

## Limitations

| Limitation | Impact |
|---|---|
| Fixed capacity benchmark (1.2M daily) | Applied uniformly to all days including weekends — fundamentally distorts utilisation analysis |
| 'Unknown' category dominant | Limits confidence in duration, status, and utilisation conclusions |
| Covid distortion (2020–2022) | Not representative of typical NHS demand; lockdown-era trends may not recur |
| No demographic data | Cannot identify which patient groups drive missed appointments |
| Twitter dataset | Small, unrepresentative, no reliable sentiment signal |
| Monday distortion | Bank holiday displacement inflates Monday appointment counts |
| Cross-dataset joins | Many-to-many matches when joining appointments_regional and national_categories — DNA-by-service-setting results are directional only |
| No financial modelling | Cost implications estimated from published £30/missed appointment figure only |

---

## Further Analysis

- **Demand-weighted capacity modelling** - rebuild the benchmark using actual working day patterns
- **Demographic data integration** - link to patient demographics and socioeconomic data to identify at-risk non-attendance groups
- **Extended time series** - include pre-2020 data to establish a non-Covid seasonal baseline
- **Predictive DNA modelling** - classification model to identify high-risk appointments for proactive intervention
- **Transport and weather overlay** - test whether proximity to transport links or weather conditions predict missed appointment rates
- **Structured social listening** - social media monitoring framework across multiple platforms
- **Group consultation capacity modelling** - Group Consultation and Education accounted for only 60,632 appointments vs 97.3M routine GP consultations; modelling the potential impact of scaling group models warrants investigation
- **Live dashboards** - automated operational reporting for real-time utilisation monitoring

---

## Repository Structure

**Note: The files 'national_categories.xlsx' and 'sub_icb_boundaries_geojson.geojson' are too large for Github. The are available on request if required**
```
├── CSV Files/
│   ├── actual_duration_clean.csv
│   ├── appointments_regional_clean.csv
│   ├── national_categories_clean.csv
│   ├── NHS-ICB_names.csv
│   └── tweets.csv
├── NHS_Healthcare_Jupyter_Notebook.ipynb
├── sub_icb_boundaries_geojson.geojson
├── Presentation_slides.pptx
├── NHS_Technical_Report.pdf
├── metadata_nhs.txt
└── README.md
```

---

## Results Summary

| Question | Finding |
|---|---|
| Adequate capacity? | No - system averaged 103.2% of stated capacity; October 2021 reached 120.3%. Benchmark itself is fundamentally misconfigured. |
| Actual utilisation? | Growing demand, 91.5% GP-driven; seasonal peaks in autumn/winter consistently breach capacity; data quality prevents a fully reliable utilisation picture |
| Missed appointments? | 4–5% DNA consistently; same-day appointments ~19.8% DNA rate; geographic concentration in Midlands and London; no improvement trend over time |
| Social media value? | Limited in current form - insufficient volume and structure; significant potential if properly developed |

---

## About

**Andrew Willacy**
[LinkedIn](https://www.linkedin.com/in/andrew-willacy-572682347/) | [GitHub Portfolio](https://github.com/AndrewWillacy) | andrew.willacy.data@gmail.com
