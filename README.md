# NHS Appointment Utilisation & Missed Appointments Analysis
August 2025

Grade: Distinction

Tools used: Python (pandas, matplotlib, seaborn), Jupyter Notebook, Excel, CSV

# Context/Business Questions

The NHS faces increasing demand, constrained resources, and persistent issues with missed appointments.
Each missed appointment represents a financial cost (~£30) and a lost opportunity for patient care, placing further strain on already pressured services.

This project analyses NHS appointment data to understand:

Appointment utilisation and capacity

Patterns in missed appointments

Service delivery trends over time

Whether current capacity aligns with actual demand

Opportunities to improve efficiency and patient attendance

The analysis combines appointment data with external social media signals to provide both operational and contextual insights.

The NHS posed two key questions:

Has there been adequate staff and network capacity?

What was the actual utilisation of available resources?

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

SQL was used to:

- Calculate revenue by country

- Identify top product categories globally and by country

- Analyse purchasing behaviour across demographics

- Evaluate which advertising methods drive the most successful customer responses

- Combine exposure + conversion metrics to determine channel effectiveness

- Segment customers by marital status and presence of children/teens

- Assign customers a simplified Media label for deeper spend comparisons

Example SQL tasks included:

Use of GREATEST() and LEAST() to identify best/worst performing product categories and ad channels

Multi-table joins using (INNER JOIN) to combine demographic and advertising data

GROUPBY to group results such as by marital status or country 

CASE logic for categorising customers

Aggregations to compute spend patterns, averages, and customer counts

# Tableau Dashboard

The Tableau dashboard (included as .twbx) includes:

- Customer age distribution

- Marital status & education breakdowns

- Income distributions

- Geographic map of customer locations & density

- Revenue and product category performance

- Advertising channel effectiveness summaries

Figure 4: Tableau Dashboard
<img width="900" height="600" alt="Screenshot 2025-12-13 153958" src="https://github.com/user-attachments/assets/685b0d12-1b62-406f-95fd-34674e667c78" />

The design uses a calm blue palette with clear typography to support executive-level presentations.

# Key Insights
### Customer Demographics

Customer ages range from 28 to 84, average age 55

Majority are married or living with a partner

Most customers have a graduate-level education or higher

Figure 5: Incoome by total spend

<img width="650" height="420" alt="Screenshot 2025-12-13 135615" src="https://github.com/user-attachments/assets/45a9f51f-8882-4c0b-ad4d-1ec35ef3f1a8" />


### Product Sales

Alcohol is the top-selling category, accounting for 50% of sales

Followed by meat, fish, and commodities

Vegetables and chocolate are the lowest performers

This trend is consistent across most countries

### Geographic Insights

Spain: largest customer base and highest revenue

Germany: highest average spend per customer

Montenegro: extremely low customer count → potential market concern

Figure 6: Average customer spend by country

<img width="650" height="400" alt="Screenshot 2025-12-13 135503" src="https://github.com/user-attachments/assets/b6d44b4d-d328-478a-939d-2bfd98ab2077" />


### Advertising Effectiveness

Twitter is the most successful advertising channel overall

Followed by Instagram and Facebook

Bulk email surprisingly performs well among single customers

Brochure advertising is consistently the least effective

Figure 7: Advertising channel effectiveness

<img width="650" height="310" alt="Screenshot 2025-12-13 135545" src="https://github.com/user-attachments/assets/a7fd352c-f419-4159-9aa8-b9e4c540dded" />


# Recommendations

Increase inventory in high-revenue categories like Alcohol and Meat

Invest more in high-performing ad channels (Twitter, Instagram)

Scale back brochure advertising

Consider targeted bulk email campaigns for specific demographics

Reevaluate investment in underperforming markets like Montenegro

Tailor campaigns using customer segmentation by age, income, and education

# Next Steps

**Customer Segmentation:** Apply clustering techniques to identify distinct customer personas based on demographics and spending behaviour.

**Predictive Modelling:** Build models to predict customer response to advertising campaigns and future spending patterns.

**Advertising Attribution:** Improve ad exposure logic to correctly account for customers exposed to multiple channels.

**Automated Data Pipeline:** Replace manual Excel cleaning with a reproducible Python-based ETL process.

**Enhanced Dashboards:** Add more granualar views for product categories, demographics, and regional performance, including trend and forecast analysis.

**Statistical Validation:** Apply hypothesis testing to validate differences in spend across regions and customer segments.
