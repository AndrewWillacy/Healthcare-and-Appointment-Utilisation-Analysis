# Healthcare Appointment Utilisation & Capacity Analysis

**Healthcare Operations Analytics Project | 2025**

> *How can healthcare appointment and utilisation data be used to improve operational planning, reduce missed appointments, and support more effective capacity management across a national healthcare system?*

---

## Executive Summary

This project analyses large-scale NHS appointment and utilisation data to identify operational trends, capacity pressures, missed appointment patterns, and data quality issues impacting healthcare planning and service delivery.

Using Python, Excel, and exploratory data analysis techniques, the project investigates over one million healthcare appointment records across 106 locations and seven regions. The analysis explores appointment utilisation, seasonal demand patterns, appointment duration trends, service setting performance, and operational strain across the healthcare network.

The project combines structured data cleaning, validation, exploratory analysis, and visualisation to transform raw operational healthcare data into actionable business insight.

A major finding of the project was that data quality limitations — particularly unmapped appointment categories, inconsistent recording practices, and unrealistic capacity assumptions — represented a more significant barrier to reliable decision-making than analytical complexity itself.

Key findings included:

* General Practice accounted for over 90% of appointments across the network
* Missed appointments consistently represented approximately 4–5% of all appointments
* Capacity pressures became more visible during winter periods and post-lockdown recovery
* Significant data quality issues reduced confidence in utilisation reporting
* Appointment demand increased steadily following Covid disruption
* Social media data demonstrated potential value for patient sentiment monitoring and engagement analysis

The final recommendations focused on improving data quality processes, strengthening capacity planning, reducing missed appointments, and improving operational resource allocation.

---

## Business Problem

The NHS faces increasing demand against constrained resources. With an ageing population and post-Covid recovery pressures, understanding how capacity is being used — and where appointments are being missed — is essential for budget planning and infrastructure decisions.

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

| Source                        | Data Collected                                                   | Purpose                              |
| ----------------------------- | ---------------------------------------------------------------- | ------------------------------------ |
| **actual_duration.csv**       | Appointment durations, locations, dates, appointment counts      | Utilisation and duration analysis    |
| **appointments_regional.csv** | Appointment types, modes, booking lead times, appointment status | Regional operational analysis        |
| **national_categories.xlsx**  | National appointment categories and service settings             | Capacity and service trend analysis  |
| **twitter.csv**               | NHS-related social media data                                    | Sentiment and engagement exploration |

All datasets were provided as semi-wrangled extracts from publicly available NHS integrated care board (ICB) data. The Excel file was converted to CSV for consistency before analysis.

The combined datasets included:

* Appointment volumes
* Service settings
* Appointment modes
* Appointment durations
* Regional operational data
* Appointment categories
* Missed appointment records
* Social media activity relating to healthcare

The analysis covered:

* 106 healthcare locations
* 7 NHS regions
* Data spanning the Covid and post-Covid recovery period
* Over 1 million appointment-related records

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

#### Recommendation

> Introduce more proactive appointment reminder and rescheduling systems including:

> * SMS reminders
> * Email notifications
> * Simplified cancellation and rescheduling systems
> * Digital patient self-service tools

---

### Finding 4: Capacity Reporting Did Not Reflect Real Operational Conditions

The use of a fixed daily capacity assumption distorted utilisation analysis, particularly during weekends and bank holidays.

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

---

## Results Summary

| Question | Finding |
|----------|---------|
| Adequate capacity? | Capacity is under strain at peaks; the capacity benchmark itself is flawed and needs rebuilding |
| Actual utilisation? | Growing demand, 91.5% GP-driven; data quality prevents a fully reliable utilisation picture |
| Missed appointments? | 4–5% DNA rate consistently; routine appointments most affected; £30 cost per missed slot |
| Social media value? | Limited in current form; significant potential if properly developed |

---
## About

This project was completed as part of the **LSE Data Analytics Career Accelerator (2025, Distinction)**.

The analysis focused on transforming large-scale operational healthcare data into actionable insight through structured cleaning, validation, exploratory analysis, visualisation, and operational interpretation.

**Andrew Willacy**
[LinkedIn](https://www.linkedin.com/in/andrew-willacy-572682347/) | [GitHub Portfolio](https://github.com/AndrewWillacy) | [andrew.willacy.data@gmail.com](mailto:andrew.willacy.data@gmail.com)




---
---
# NHS Appointment Utilisation & Missed Appointments Analysis
**LSE Data Analytics Career Accelerator — DA201: Diagnostic Analysis using Python | August 2025**

> *Has the NHS had adequate staff and network capacity? What was the actual utilisation of resources, and what is driving missed appointments?*

---

## Executive Summary

This project analyses real-world NHS appointment data covering over one million records across 106 locations and seven regions in England, spanning 2020 to 2022. Using Python, the analysis identifies utilisation patterns, seasonal trends, capacity gaps, and the scale and distribution of missed appointments. A Twitter dataset was also reviewed to assess the potential value of social media as an external data source for patient engagement insight.

**Key result:** While the NHS delivered increasing appointment volumes across the period, the data reveals persistent strain during peak periods, a 4–5% missed appointment rate carrying significant financial and social cost, and — critically — that poor data quality is itself the primary barrier to reliable capacity planning. Unmapped and unknown values are frequently the highest-count category in key metrics, making confident conclusions difficult without improved data capture at source.

---

## Business Problem

The NHS faces increasing demand against constrained resources. With an ageing population and post-Covid recovery pressures, understanding how capacity is being used — and where appointments are being missed — is essential for budget planning and infrastructure decisions.

Two core questions drove the analysis:

> **1. Has there been adequate staff and network capacity?**
> **2. What was the actual utilisation of resources?**

Supporting analytical questions included:
- What are the seasonal and monthly trends in appointment volumes?
- Which service settings and appointment modes drive the most activity?
- What is the scale and pattern of missed appointments?
- Can Twitter data provide useful insight into public sentiment around NHS services?

---

## Data Sources

| File | Contents |
|------|----------|
| `actual_duration.csv` | Appointment durations, location, date, count |
| `appointments_regional.csv` | Appointment mode, status, booking lead time, location, date, count |
| `national_categories.xlsx` | Service setting, context type, national category, location, date, count |
| `twitter.csv` | Tweets referencing NHS-related topics scraped from Twitter/X |

All datasets were provided as semi-wrangled extracts from publicly available NHS integrated care board (ICB) data. The Excel file was converted to CSV for consistency before analysis.

---

## Tools & Skills Used

| Category | Tools / Libraries |
|----------|------------------|
| **Language** | Python 3 |
| **Data Processing** | pandas, NumPy |
| **Visualisation** | Matplotlib, Seaborn |
| **Environment** | Jupyter Notebook |
| **External Data** | Twitter/X dataset (hashtag and sentiment analysis) |

**Skills demonstrated:** Large-scale real-world dataset handling · Multi-dataset cleaning and validation · Outlier and anomaly detection · Trend and seasonal analysis · Data quality investigation · Social media data assessment · Stakeholder-focused insight communication

---

## Analytical Approach

### 1. Data Ingestion & Cleaning

Four datasets were imported and cleaned independently before analysis:

- **Null values** checked across all datasets — none found in primary fields
- **Duplicates** identified and removed in `appointments_regional` only
- **Data types** validated and corrected where necessary
- **Excel to CSV conversion** applied to `national_categories.xlsx` for consistency
- **Cleaned datasets** saved with `_clean` suffix to preserve originals
- **Capacity benchmark issue identified:** The NHS uses a fixed daily capacity figure of 1.2 million appointments across all days, including weekends where actual volumes are significantly lower. This fundamentally skews utilisation calculations and was flagged as a primary data quality concern throughout the analysis

**Key data quality finding:** Across multiple metrics — particularly appointment duration — "Unknown" and unmapped values were frequently the highest-count category, often exceeding any named value. This was investigated as a systemic recording failure rather than random missingness, and treated as the primary analytical limitation rather than a problem to be imputed around.

### 2. Exploratory Data Analysis

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

**Missed appointments:**
- 4–5% of appointments were recorded as missed (DNA — Did Not Attend) across the period
- A further 4–5% were unmapped or unclassifiable
- Missed appointments were more frequent in routine categories than urgent ones
- At £30 per missed appointment, the financial cost is substantial — and the social cost of lost slots equally significant

**National categories:**
- The majority of appointments were classified as "Routine"
- Urgent appointments showed stronger seasonal variation, spiking in winter months

### 3. Twitter / Social Media Analysis

The Twitter dataset was reviewed to assess its potential value as an external signal for patient behaviour and sentiment. Top trending hashtags included `#healthcare`, `#health`, and `#medicine`.

**Honest assessment:** The data in its current form has limited analytical value. The hashtag frequency analysis provides directional information about topics but no reliable sentiment signal. The dataset was treated as indicative of potential rather than a source of actionable insight — and this was communicated explicitly rather than overstated.

---

## Key Findings

### Capacity & Utilisation

| Finding | Detail |
|---------|--------|
| Demand is growing | Steady upward trend across the period; GP services under most pressure |
| Capacity calculation is flawed | 1.2M daily figure applied uniformly including weekends — skews all utilisation metrics |
| Peak pressure visible | Winter months and post-lockdown recovery periods show clear capacity strain |
| Data quality is the primary problem | Unknown/unmapped values dominate key metrics; reliable utilisation analysis requires better recording at source |

### Missed Appointments

| Metric | Value |
|--------|-------|
| DNA rate | 4–5% consistently across the period |
| Unmapped/unclassifiable | Further 4–5% |
| Financial cost per missed appointment | £30 |
| Most affected category | Routine appointments |
| Least affected category | Urgent appointments |

### Social Media

Twitter data shows potential as a channel for understanding public sentiment but requires significant development before it could inform operational decisions.

---

## Recommendations

**1. Fix the capacity benchmark**
The 1.2 million daily capacity figure must be adjusted to reflect actual working days and appointment availability patterns. Applying a uniform figure across weekends and bank holidays produces misleading utilisation rates.

**2. Improve data recording at source**
Unknown and unmapped values are the single biggest barrier to reliable insight. Without consistent recording of appointment duration, status, and context type, capacity planning will remain guesswork. Investment in data quality at ICB level is more valuable than additional analytical sophistication.

**3. Address missed appointments through process, not punishment**
Text and email reminders for routine appointments could reduce DNA rates, with the caveat that digital access cannot be assumed for all patients. Making rescheduling and cancellation easier — through apps or patient portals where available — is likely more effective than financial penalties, which disproportionately affect the most vulnerable patients.

**4. Develop social media monitoring properly**
Twitter/X and other platforms have real potential for understanding patient concerns and informing public health campaigns. The current dataset is insufficient — a structured social listening programme across multiple platforms would generate more actionable insight.

**5. Build demand forecasting from historical trends**
Historical appointment volume data can support winter surge planning, though the 2020–2022 window is unusual due to Covid and may not represent typical seasonal patterns. Longer historical data would improve forecast reliability.

---

## Limitations

- **Fixed capacity benchmark:** The 1.2M daily figure is applied uniformly regardless of day type, making true utilisation rates unreliable
- **Data quality:** Unknown/unmapped values dominate several key metrics — particularly appointment duration — making confident conclusions difficult
- **Covid distortion:** The 2020–2022 window is not representative of typical NHS demand patterns; lockdown-era trends may not recur
- **No demographic data:** Patient demographics are not available in the dataset — it is impossible to identify which patient groups are most likely to miss appointments
- **Twitter data limitations:** Small, unrepresentative dataset with no reliable sentiment scoring; treated as indicative only
- **Bank holiday distortion:** Monday appointment counts are inflated or deflated depending on bank holiday occurrence, affecting weekly trend analysis
- **No financial modelling:** Cost implications are estimated from published £30 per missed appointment figure; actual cost calculations would require additional data

---

## Further Analysis

- **Demographic data integration** — link appointment records to patient demographic and socio-economic data to identify at-risk non-attendance groups
- **Extended time series** — include pre-2020 data to establish a non-Covid baseline for seasonal forecasting
- **Transport and weather overlay** — test whether proximity to transport links or weather conditions predict missed appointment rates
- **Realistic capacity modelling** — rebuild the capacity benchmark using actual working day and appointment availability patterns
- **Structured social listening** — develop a proper social media monitoring framework across Twitter/X, Facebook, and other platforms
- **Regional variation analysis** — explore whether missed appointment rates and utilisation patterns vary significantly between the seven regions

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

---

## Results Summary

| Question | Finding |
|----------|---------|
| Adequate capacity? | Capacity is under strain at peaks; the capacity benchmark itself is flawed and needs rebuilding |
| Actual utilisation? | Growing demand, 91.5% GP-driven; data quality prevents a fully reliable utilisation picture |
| Missed appointments? | 4–5% DNA rate consistently; routine appointments most affected; £30 cost per missed slot |
| Social media value? | Limited in current form; significant potential if properly developed |

---

## About

This project was completed as part of the **LSE Data Analytics Career Accelerator (DA201: Diagnostic Analysis using Python), August 2025**, achieving a score of 72/90.

**Andrew Willacy**
[LinkedIn](https://www.linkedin.com/in/andrew-willacy-572682347/) | [GitHub Portfolio](https://github.com/AndrewWillacy) | andrew.willacy.data@gmail.com

---
---

# NHS HEALTHCARE AND APPOINTMENT UTILISATION ANALYSIS 
July 2025

Grade: Distinction

Tools used: Python (pandas, matplotlib, seaborn), Jupyter Notebook, Excel, CSV

# Context/Business Questions

The NHS faces increasing demand, constrained resources, and persistent issues with missed appointments.
Each missed appointment represents a financial cost (~£30) and a lost opportunity for patient care, placing further strain on already pressured services.

This project analyses NHS appointment data to understand:

- Appointment utilisation and capacity

- Patterns in missed appointments

- Service delivery trends over time

- Whether current capacity aligns with actual demand

- Opportunities to improve efficiency and patient attendance

The analysis combines appointment data with external social media signals to provide both operational and contextual insights.

The NHS posed two key questions:

1. Has there been adequate staff and network capacity?

2. What was the actual utilisation of available resources?

A secondary objective was to explore missed appointments, their scale, and potential drivers.

# Data Cleaning & Preparation (Excel)

Key steps included:

- Converting Excel to CSV for consistency

- Removing duplicates and validating counts

- Handling missing and “unmapped” values

- Standardising date formats and categories

- Creating cleaned datasets with a _clean suffix

A significant finding was that **unmapped or poor-quality data frequently represented the largest category**, limiting analytical precision.

# Database Structure

Four datasets were used:

**actual_duration.csv**

Appointment duration, date, location, and volume

**appointments_regional.csv**

Appointment mode, booking lead time, region, and count

**national_categories.xlsx (converted to CSV to match the other files)**

Appointment category (routine, urgent, etc.) by date and region

**twitter.csv (File created through sentiment analysis)**

Tweets referencing NHS-related topics to explore public sentiment

All datasets were cleaned, validated, and standardised before analysis.
Duplicates were identified and removed where present.


# Analytical Approach (Python)

The analysis was conducted in Python using Jupyter Notebook, focusing on:

Exploratory data analysis (EDA)

Time-series trend analysis

Appointment duration distributions

Capacity vs utilisation comparisons

Missed appointment rates

Seasonal and pandemic-related effects

Qualitative exploration of NHS-related Twitter data

Visualisations were produced using Matplotlib and Seaborn.

Aggregations to compute spend patterns, averages, and customer counts


# Key Insights
📌 Appointment Volumes & Duration

Over 106 locations across 7 regions

General Practice accounts for ~91.5% of all appointments

Most appointments last 6–10 minutes

Same-day appointments are the most common

A large proportion of duration data is unknown, indicating data quality issues

📌 Service Delivery & Trends

Face-to-face appointments dominate, followed by telephone

Telephone appointments increased significantly during Covid

Appointment volumes peaked in November 2021 (~30.4M) and were lowest in August 2021 (~23.9M)

Seasonal dips observed in winter months, likely due to holidays and weather

📌 Missed Appointments

4–5% of appointments were missed

A further 4–5% were unmapped

Missed appointments are more common in routine than urgent care

Missed slots represent both financial loss and reduced access for other patients

📌 Capacity & Utilisation

Demand for appointments has increased steadily

Capacity strain is most visible during peak periods (e.g. winter)

A fixed daily capacity figure (1.2M) is applied across all days, including weekends, which skews utilisation analysis

Bank holidays and weekends distort apparent under-utilisation

📌 Social Media Insights

Common hashtags include #healthcare, #health, #medicine

Social media data has potential for sentiment analysis, but current data is limited

Opportunity exists to use social platforms for engagement and awareness campaigns

# Recommendations
1️⃣ Capacity Planning

Improve data quality and reduce unmapped values

Replace fixed daily capacity assumptions with demand-driven models

Monitor appointment volumes monthly and seasonally

Use historical data to plan for winter and flu-season spikes

2️⃣ Reducing Missed Appointments

Introduce or expand text/email reminders (with accessibility in mind)

Improve appointment booking, rescheduling, and cancellation processes

Target high no-show regions with awareness campaigns

3️⃣ Social Media Integration

Expand analysis beyond Twitter to other platforms

Monitor sentiment trends at regional level

Use positive campaigns to counter negative sentiment during crises

4️⃣ Further Data Development

Incorporate demographic and socio-economic data

Explore external factors such as transport, weather, and employment patterns

Better identify patient groups most at risk of non-attendance

# Next Steps

Patient Segmentation: Apply clustering techniques to identify patient groups based on appointment type, attendance behaviour, region, and service setting.

Predictive Modelling: Build models to predict missed appointments and appointment demand using historical trends, seasonality, and booking lead times.

Capacity Forecasting: Improve capacity planning by modelling demand peaks (e.g. winter, flu season) and aligning staffing levels to predicted utilisation.

Automated Data Pipeline: Replace manual preprocessing with a reproducible Python-based ETL workflow, including data validation and quality checks.

Enhanced Dashboards: Develop interactive dashboards with granular views of appointment modes, missed appointment rates, regional utilisation, and trend analysis.

Statistical Validation: Apply hypothesis testing to validate differences in missed appointment rates across regions, appointment categories, and service types.
