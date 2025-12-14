# NHS Appointment Utilisation & Missed Appointments Analysis
August 2025

Grade: Distinction

Tools used: Python (pandas, matplotlib, seaborn), Jupyter Notebook, Excel, CSV

# Context/Business Questions

The NHS faces increasing demand, constrained resources, and persistent issues with missed appointments.
Each missed appointment represents a financial cost (~£30) and a lost opportunity for patient care, placing further strain on already pressured services.

This project analyses NHS appointment data to understand:

- Appointment utilisation and capacity

= Patterns in missed appointments

- Service delivery trends over time

- Whether current capacity aligns with actual demand

- Opportunities to improve efficiency and patient attendance

The analysis combines appointment data with external social media signals to provide both operational and contextual insights.

The NHS posed two key questions:

1. Has there been adequate staff and network capacity?

2. What was the actual utilisation of available resources?

A secondary objective was to explore missed appointments, their scale, and potential drivers.


Figure 1: 



# Data Cleaning & Preparation (Excel)

Key steps included:

Converting Excel to CSV for consistency

Removing duplicates and validating counts

Handling missing and “unmapped” values

Standardising date formats and categories

Creating cleaned datasets with a _clean suffix

A significant finding was that unmapped or poor-quality data frequently represented the largest category, limiting analytical precision.
# Database Structure

Four datasets were used:

actual_duration.csv
Appointment duration, date, location, and volume

appointments_regional.csv
Appointment mode, booking lead time, region, and count

national_categories.xlsx (converted to CSV)
Appointment category (routine, urgent, etc.) by date and region

twitter.csv
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
