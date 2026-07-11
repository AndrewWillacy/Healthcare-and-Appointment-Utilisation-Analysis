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

Data cleaning and validation · Exploratory data analysis · Large-scale dataset handling · Trend analysis · Anomaly detection · Data quality assessment · Operational reporting · Healthcare utilisation analysis · Stakeholder-focused insight communication

---

## Analytical Approach

The project followed a structured workflow combining data cleaning, exploratory analysis, visualisation, operational interpretation, and recommendation development.

### 1. Data Ingestion, Cleaning & Validation

The raw datasets were imported into Python and assessed for quality, consistency, missing values, and structural reliability.

Key preparation activities included:

* Validation of missing values
* Duplicate record identification and removal
* Standardisation of date formats
* Conversion of Excel datasets to CSV format for consistency
* Validation of categorical variables
* Handling of inconsistent or unmapped values
* Data type standardisation
* Validation of appointment count fields

A significant focus of the project involved assessing the reliability of the underlying operational data.

Key data quality issues identified included:

| Issue Identified                               | Impact                              |
| ---------------------------------------------- | ----------------------------------- |
| High levels of unmapped appointment categories | Reduced reporting reliability       |
| Inconsistent appointment recording practices   | Distorted operational analysis      |
| Static daily capacity assumptions              | Misleading utilisation calculations |
| Missing or unclear appointment classifications | Reduced analytical confidence       |
| Duplicate records in regional appointment data | Inflated reporting outputs          |

The project identified that several reporting limitations originated from upstream operational recording practices rather than analytical methodology.
> **Capacity benchmark issue identified:** The NHS uses a fixed daily capacity figure of 1.2 million appointments across all days, including weekends where actual volumes are significantly lower. This fundamentally skews utilisation calculations and was flagged as a primary data quality concern throughout the analysis

> **Key data quality finding:** Across multiple metrics — particularly appointment duration — "Unknown" and unmapped values were frequently the highest-count category, often exceeding any named value. This was investigated as a systemic recording failure rather than random missingness, and treated as the primary analytical limitation rather than a problem to be imputed around.

---

### 2. Exploratory Data Analysis

Exploratory analysis was conducted using Python to identify utilisation trends, seasonal patterns, operational pressures, and missed appointment behaviour.

The analysis investigated:

* Appointment volumes by month
* Appointment duration patterns
* Service setting utilisation
* Appointment modes
* Seasonal demand variation
* Missed appointment rates
* Regional differences in utilisation
* Covid-related operational disruption
* Capacity and utilisation trends

Key exploratory findings included:

**Scale and structure:**
- 106 locations across 7 NHS regions
- Date range: 2020–2022 (covering pre-Covid baseline, lockdown period, and recovery)
- General Practice accounted for 91.5% of all appointments
- Face-to-face was the most common appointment mode; telephone became significantly more common during Covid lockdowns and remained elevated post-restriction

**Volume trends:**
- November 2021 recorded the highest monthly appointment volume (30.4 million)
- August 2021 recorded the lowest (23.9 million)
- A clear seasonal pattern emerged with dips in December–February, likely reflecting holiday periods and weather effects
- A steady upward trend in total appointments across the period, with a visible dip during lockdowns followed by recovery

**Appointment duration:**
- The majority of appointments with recorded durations lasted 6–10 minutes
- 1–5 minute appointments were the most frequently occurring named category
- "Unknown" duration was the single largest category overall — a significant data recording problem

**National categories:**
- The majority of appointments were classified as "Routine"
- Urgent appointments showed stronger seasonal variation, spiking in winter months

Visualisations included:

* Time series analysis
* Appointment trend visualisations
* Service setting comparisons
* Duration distribution charts
* Seasonal trend analysis
* Appointment category comparisons

---

### 3. Missed Appointment & Capacity Analysis

A major focus of the project involved analysing missed appointments and operational utilisation pressures.

The analysis identified:

| Observation                                                       | Operational Impact                     |
| ----------------------------------------------------------------- | -------------------------------------- |
| Missed appointments consistently represented 4–5% of appointments | Financial and operational inefficiency |
| 4–5% of appointments were unmapped or unclassifiable              | Data quality and reliability issues    |
| Routine appointments showed higher non-attendance rates           | Increased scheduling inefficiency      |
| Capacity pressure increased during winter periods                 | Evidence of operational strain         |
| Demand increased steadily following Covid disruption              | Growing utilisation pressure           |

The project also identified a significant issue relating to the use of a fixed daily capacity assumption.

A static figure of approximately 1.2 million appointments per day was applied across all days, including weekends and bank holidays, despite significantly lower appointment demand during these periods. Indeed GP practices are generally closed on these days

This introduced distortion into utilisation calculations and reduced confidence in capacity reporting outputs.

Figure 1: Average daily GP appointments per day (The red dotted line represents the 1.2M daily capacity)
<img width="800" height="500" alt="Screenshot 2025-08-08 154933" src="https://github.com/user-attachments/assets/6af06337-9d00-4eae-9c8b-13392007eab5" />


A key conclusion of the analysis was:

> The primary limitation affecting operational insight was not analytical capability, but inconsistent and unreliable operational data capture.

---
### 4. Social Media Analysis

External Twitter (X) data was analysed to explore the potential value of social media as an additional operational insight source.

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
* Social media data showed potential value for:

  * Patient sentiment monitoring
  * Public awareness campaigns
  * Engagement trend analysis
  * Service communication strategies

> The data in its current form has limited analytical value. The hashtag frequency analysis provides directional information about topics but no reliable sentiment signal. The dataset was treated as indicative of potential rather than a source of actionable insight — and this was communicated explicitly rather than overstated.

---
## Key Findings & Business Recommendations

### Finding 1: Operational Demand Continued to Increase

Appointment demand increased steadily across the analysed period, particularly following Covid-related disruption.

| Trend                            | Operational Interpretation                |
| -------------------------------- | ----------------------------------------- |
| Rising appointment volumes       | Increasing pressure on NHS infrastructure |
| Winter utilisation spikes        | Seasonal operational strain               |
| Increased telephone appointments | Covid-driven service adaptation           |

Figure 2: Appointments by mode - shows how telephone incraesed over the Covid lockdowns
<img width="1357" height="406" alt="Screenshot 2025-08-08 160117" src="https://github.com/user-attachments/assets/b502335e-f0c3-46f8-8c9d-39894f2c61b8" />

Figure 3: Estimated weekly utilisation (Covid lockdowns shown in grey)
<img width="1354" height="498" alt="Screenshot 2025-08-08 161547" src="https://github.com/user-attachments/assets/39620ebd-ef13-4cc0-b6d8-857ce6a84227" />

#### Recommendation

> Continue monitoring utilisation trends and align staffing and operational resources more dynamically around predictable seasonal demand patterns.

---

### Finding 2: Data Quality Issues Limited Operational Insight

Large volumes of unmapped and inconsistently recorded data reduced confidence in reporting outputs.

| Data Quality Issue               | Business Impact                  |
| -------------------------------- | -------------------------------- |
| Unmapped appointment categories  | Reduced reporting reliability    |
| Inconsistent recording standards | Distorted utilisation analysis   |
| Static capacity assumptions      | Misleading operational reporting |

Figure 4: Removing GP appointments shows that unmapped accounts for the highest number of appointments
<img width="900" height="400" alt="Screenshot 2025-08-08 153553" src="https://github.com/user-attachments/assets/e724385e-641f-4849-8cf4-d8cb4da916cd" />

#### Recommendation

> Prioritise improvements to operational data capture processes and standardisation before implementing more advanced analytical or forecasting models.

---

### Finding 3: Missed Appointments Represented Significant Operational Waste

Missed appointments consistently represented approximately 4–5% of all appointments across the analysed period.

These missed appointments:

* Reduced operational efficiency
* Increased pressure on healthcare services
* Created financial waste
* Reduced appointment availability for other patients

Figure 5: Missed appointments tend to occur when the wait time is between 2-7 days
<img width="780" height="400" alt="Screenshot 2025-08-08 193308" src="https://github.com/user-attachments/assets/da5b9a98-e41b-4eb7-87c1-325516573e0f" />

Figure 6: Appointment attendance status - Unknown once again accounts for a small but significant %
<img width="780" height="400" alt="Screenshot 2025-08-09 142246" src="https://github.com/user-attachments/assets/0dd04c08-fb84-4f76-90c1-a6e5cec429eb" />

#### Recommendation

> Introduce more proactive appointment reminder and rescheduling systems including:

> * SMS reminders
> * Email notifications
> * Simplified cancellation and rescheduling systems
> * Digital patient self-service tools

---

### Finding 4: Capacity Reporting Did Not Reflect Real Operational Conditions

The use of a fixed daily capacity assumption distorted utilisation analysis, particularly during weekends and bank holidays.

Figure 7: Daily capacity is static eventhough demand is dynamic
<img width="1364" height="352" alt="Screenshot 2025-08-08 154731" src="https://github.com/user-attachments/assets/099243be-7839-4e9e-9c47-dc9bbfbbb478" />

#### Recommendation

> Develop more realistic dynamic capacity models aligned to:

> * Seasonal demand
> * Day-of-week variation
> * Staffing availability
> * Regional operational pressures

---

### Finding 5: Social Media Could Support Public Engagement Analysis

Healthcare-related social media activity demonstrated potential value for:

* Public sentiment analysis
* Awareness campaign monitoring
* Identifying recurring public concerns
* Supporting engagement strategies

Figure 8: Most used health related hashtags on Twitter (X)
<img width="800" height="450" alt="tweets" src="https://github.com/user-attachments/assets/699c1879-efcf-4d47-a9b9-6f85ba601de1" />

#### Recommendation

> Explore structured sentiment analysis and social media monitoring as part of broader operational and communications analytics capability.

---

## Limitations

Several limitations impacted the reliability and scope of the analysis:

- **Fixed capacity benchmark:** The 1.2M daily figure is applied uniformly regardless of day type, making true utilisation rates unreliable
- **Data quality:** Unknown/unmapped values dominate several key metrics - particularly appointment duration - making confident conclusions difficult
- **Covid distortion:** The 2020–2022 window is not representative of typical NHS demand patterns; lockdown-era trends may not recur
- **No demographic data:** Patient demographics are not available in the dataset - it is impossible to identify which patient groups are most likely to miss appointments
- **Twitter data limitations:** Small, unrepresentative dataset with no reliable sentiment scoring; treated as indicative only
- **Bank holiday distortion:** Monday appointment counts are inflated or deflated depending on bank holiday occurrence, affecting weekly trend analysis
- **No financial modelling:** Cost implications are estimated from published £30 per missed appointment figure; actual cost calculations would require additional data
- **Analysis Focus:** The project focused primarily on exploratory rather than predictive analysis - It looked at  what has already happened rather than what is likely to happen in the future

Despite these limitations, the analysis identified clear operational trends and important process improvement opportunities.

---
## Further Analysis

Potential future enhancements include:

- **Develop a predictive model** - Predictive modelling for appointment demand forecasting
- **Demographic data integration** - link appointment records to patient demographic and socio-economic data to identify at-risk non-attendance groups
- **Extended time series** - include pre-2020 data to establish a non-Covid baseline for seasonal forecasting
- **Transport and weather overlay** - test whether proximity to transport links or weather conditions predict missed appointment rates
- **Realistic capacity modelling** - rebuild the capacity benchmark using actual working day and appointment availability patterns
- **Structured social listening** - develop a proper social media monitoring framework across Twitter/X, Facebook, and other platforms
- **Regional variation analysis** - explore whether missed appointment rates and utilisation patterns vary significantly between the seven regions
- **Patient segmentation** - Segmenting and clustering by paatient type, age, demographic etc
- **Sentiment analysis** - The use of NLP-based sentiment analysis of social media data to gauge opinion
- **Live dashborads** - Automated operational reporting dashboards for real-time utilisation monitoring
---

## Deliverables

| Deliverable              | Description                                  |
| ------------------------ | -------------------------------------------- |
| Jupyter Notebook         | Python-based exploratory analysis workflow   |
| Technical Report         | Operational findings and recommendations     |
| Data Visualisations      | Trend analysis and utilisation reporting     |
| Stakeholder Presentation | Business-focused operational insight summary |

---

## Results Summary

| Question | Finding |
|----------|---------|
| Adequate capacity? | Capacity is under strain at peaks; the capacity benchmark itself is flawed and needs rebuilding |
| Actual utilisation? | Growing demand, 91.5% GP-driven; data quality prevents a fully reliable utilisation picture |
| Missed appointments? | 4–5% DNA (Did Not Attend) rate consistently; routine appointments most affected; £30 cost per missed slot |
| Social media value? | Limited in current form; significant potential if properly developed |

---

## Repository Structure

```
├── data/
│   ├── actual_duration_clean.csv
│   ├── appointments_regional_clean.csv
│   ├── national_categories_clean.csv
│   └── twitter.csv
├── notebooks/
│   └── Willacy_Andrew_DA201_Assignment_Notebook.ipynb
├── report/
│   └── Willacy_Andrew_DA201_Assignment_Report.pdf
└── README.md
```

## About

This project was completed as part of the **LSE Data Analytics Career Accelerator (2025, Distinction)**.

The analysis focused on transforming large-scale operational healthcare data into actionable insight through structured cleaning, validation, exploratory analysis, visualisation, and operational interpretation.

**Andrew Willacy**
[LinkedIn](https://www.linkedin.com/in/andrew-willacy-572682347/) | [GitHub Portfolio](https://github.com/AndrewWillacy) | [andrew.willacy.data@gmail.com](mailto:andrew.willacy.data@gmail.com)

---
---
---

# NHS Healthcare Appointment, Utilisation & Capacity Analysis

**Healthcare Operations Analytics Project | LSE Data Analytics Career Accelerator | 2025 | Grade: 72/90**

> *How can healthcare appointment and utilisation data be used to improve operational planning, reduce missed appointments, and support more effective capacity management across a national healthcare system?*

---

## Executive Summary

This project analyses large-scale NHS appointment and utilisation data to identify operational trends, capacity pressures, missed appointment patterns, and data quality issues impacting healthcare planning and service delivery.

Using Python, Excel, and exploratory data analysis techniques, the project investigates over one million healthcare appointment records across 106 Sub-ICB locations and seven regions. The analysis explores appointment utilisation, seasonal demand patterns, HCP trends, service setting performance, missed appointment behaviour by wait time and geography, and operational strain across the healthcare network.

The project combines structured data cleaning, validation, exploratory analysis, geographic mapping, and visualisation to transform raw operational healthcare data into actionable business insight.

**A major finding of the project was that data quality limitations — particularly unmapped appointment categories, inconsistent recording practices, and an unrealistic capacity benchmark — represented a more significant barrier to reliable decision-making than analytical complexity itself.**

Key findings included:

- General Practice accounted for 91.5% of appointments across the network
- The system operated at an average of **103.2% of its stated daily capacity** across the analysis period; October 2021 was the worst month at **120.3%** of weekday capacity
- Missed appointments (DNA) consistently represented **4–5%** of all appointments; a further 4–5% had unknown status
- **Same-day appointments had a ~19.8% DNA rate** — nearly 1 in 5 not attended
- The top 10 highest-DNA Sub-ICB regions ranged from **4.7%–5.8%**, concentrated in the Midlands and London (NHS Black Country and NHS Greater Manchester worst affected)
- Significant data quality issues — particularly the dominant 'Unknown' category — reduced confidence in utilisation reporting
- Appointment demand increased steadily following Covid disruption, with clear seasonal patterns (autumn/winter capacity consistently breached)
- Social media data demonstrated limited analytical value in current form but potential for structured future use

---

## Business Problem

The NHS faces increasing demand against constrained resources. With an ageing population and post-Covid recovery pressures, understanding how capacity is being used — and where appointments are being missed — is essential for budget planning and infrastructure decisions.

Healthcare stakeholders needed to better understand:

- Whether current staffing and network capacity were sufficient
- How healthcare resources were actually being utilised
- What seasonal and regional patterns existed in demand and missed appointments
- Where operational bottlenecks and inefficiencies existed
- Whether external data sources such as social media could support operational insight

The analysis aimed to support:

- Capacity planning and resource allocation
- Service utilisation analysis
- Missed appointment reduction strategies
- Data-driven healthcare decision-making

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

| Category | Tools / Methods |
|---|---|
| **Data Cleaning & Preparation** | Python, Pandas, Excel |
| **Exploratory Analysis** | Pandas, NumPy |
| **Data Visualisation** | Matplotlib, Seaborn |
| **Geographic Analysis** | GeoPandas, GeoJSON (ONS boundary data) |
| **Analysis Techniques** | Trend analysis, anomaly detection, utilisation analysis, seasonal analysis, geographic mapping |
| **Reporting** | Stakeholder reporting, operational insight communication |

**Skills demonstrated:**

Data cleaning and validation · Large-scale dataset handling · Exploratory data analysis · Seasonal trend analysis · Geographic data visualisation · DNA pattern analysis · Anomaly detection · Data quality assessment · Operational reporting · Healthcare utilisation analysis · Stakeholder-focused insight communication

---

## Analytical Approach

### 1. Data Ingestion, Cleaning & Validation

The raw datasets were imported into Python and assessed for quality, consistency, missing values, and structural reliability.

Key preparation activities included:

- Validation of missing values and removal of 21,604 duplicate records from appointments_regional
- Standardisation of date formats (dd-mmm-yy in actual_duration vs dd/mm/yyyy in national_categories — standardised to dd/mm/yyyy)
- Conversion of national_categories.xlsx to CSV format for consistency
- Merge of NHS-ICB names reference file on ICB ONS code to add readable location names
- Validation of categorical variables and data type standardisation
- Handling of inconsistent or unmapped values

Key data quality issues identified:

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

**Seasonal patterns:**
- Summer (Aug 2021): volumes below capacity benchmark across all weeks
- Autumn (Sep–Nov 2021): capacity consistently breached from October; predictable seasonal pressure
- Winter (Dec 2021–Feb 2022): more variability; Christmas week near-zero across all settings
- Spring (Mar–May 2022): appointments concentrated Monday–Wednesday; Easter dip visible

**HCP trends:**
- GP appointments dominated throughout; Other Practice Staff and Unknown HCP types showed distinct seasonal patterns — rising in autumn and spring, contrasting with GP winter peak pressure

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

**By Sub-ICB Region:**
- Top 10 highest-DNA regions: 4.7%–5.8%
- NHS Black Country, NHS Greater Manchester, and NHS Birmingham & Solihull — all Midlands regions — showed the worst confirmed DNA rates
- Geographic mapping confirmed concentration in densely populated urban areas (Midlands and London)
- The same regions also showed the highest Unknown status rates (3.9%–4.8%), suggesting recording quality and non-attendance risk are geographically correlated

---

### 5. Social Media Analysis

Twitter (X) data was analysed to explore potential value for operational insight. The most frequent hashtag was #healthcare — appearing nearly ten times more than the second. Most tweets received zero retweets and likes.

The dataset in its current form has limited analytical value — insufficient volume, no geographic tagging, and sparse metadata. Treated as indicative of potential rather than a source of actionable insight.

---

## Key Findings & Recommendations

### Finding 1: The System Was Operating Above Structural Capacity

The NHS operated at an average of 103.2% of its stated daily capacity across the analysis period. October 2021 was the worst month at 120.3% of weekday capacity — running 20.3% above structural limits.

> **Recommendation:** Develop a demand-weighted capacity model reflecting actual working day availability by day type and season. Align staffing resources to predictable seasonal patterns, particularly the autumn/winter peak.

---

### Finding 2: Data Quality Issues Limited Operational Insight

Large volumes of unmapped and inconsistently recorded data — particularly the dominant 'Unknown' category — reduced confidence in reporting outputs across multiple metrics.

> **Recommendation:** Prioritise improvements to operational data capture processes before implementing more advanced analytical or forecasting models.

---

### Finding 3: Missed Appointments Are a Structural Problem

DNA rates of 4–5% were consistent across the period with no improvement trend — this is a structural feature requiring deliberate intervention. Same-day appointments (~19.8% DNA rate) are the highest-risk category. Geographic concentration in the Midlands and London suggests targeted regional intervention is more appropriate than uniform national campaigns.

> **Recommendation:** Introduce proactive appointment reminder and rescheduling systems (SMS, email, digital self-service). Deploy interventions differentially by region and wait time category rather than uniformly.

---

### Finding 4: The Capacity Benchmark Is Fundamentally Misconfigured

The use of a fixed 1.2 million daily capacity figure — applied uniformly including weekends when GP practices are closed — creates a systematic distortion in all downstream utilisation reporting.

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

- **Demand-weighted capacity modelling** — rebuild the benchmark using actual working day patterns
- **Demographic data integration** — link to patient demographics and socioeconomic data to identify at-risk non-attendance groups
- **Extended time series** — include pre-2020 data to establish a non-Covid seasonal baseline
- **Predictive DNA modelling** — classification model to identify high-risk appointments for proactive intervention
- **Transport and weather overlay** — test whether proximity to transport links or weather conditions predict missed appointment rates
- **Structured social listening** — social media monitoring framework across multiple platforms
- **Group consultation capacity modelling** — Group Consultation and Education accounted for only 60,632 appointments vs 97.3M routine GP consultations; modelling the potential impact of scaling group models warrants investigation
- **Live dashboards** — automated operational reporting for real-time utilisation monitoring

---

## Repository Structure

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
| Adequate capacity? | No — system averaged 103.2% of stated capacity; October 2021 reached 120.3%. Benchmark itself is fundamentally misconfigured. |
| Actual utilisation? | Growing demand, 91.5% GP-driven; seasonal peaks in autumn/winter consistently breach capacity; data quality prevents a fully reliable utilisation picture |
| Missed appointments? | 4–5% DNA consistently; same-day appointments ~19.8% DNA rate; geographic concentration in Midlands and London; no improvement trend over time |
| Social media value? | Limited in current form — insufficient volume and structure; significant potential if properly developed |

---

## About

This project was completed as part of the **LSE Data Analytics Career Accelerator (2025, Distinction)**. Grade: 72/90 (DA201).

**Andrew Willacy**
[LinkedIn](https://www.linkedin.com/in/andrew-willacy-572682347/) | [GitHub Portfolio](https://github.com/AndrewWillacy) | andrew.willacy.data@gmail.com

