
---

# Mobile Big Data (MBD) – Assignment 1

## Course

Mobile Big Data Analytics and Management

## Student

* **Name:** Ishimwe Karekezi Guy Gael
* **AndrewID:** iguygael

---

## Overview of Our Approach

In this assignment, we analyze large-scale mobile phone activity data collected in Milan over multiple days. The dataset includes SMS activity, call activity, and internet usage at an hourly resolution and at the spatial grid (CellID) level. Our main goal was to understand **temporal patterns**, **spatial behavior**, and **differences between domestic and international communication**, using practical mobile big data analytics techniques.

We started by loading three daily activity files corresponding to **November 2nd, 4th, and 6th, 2013**, and combining them into a single dataset for analysis. From there, we focused on preparing a clean, analysis-ready dataset by handling missing values, engineering useful aggregate features, and extracting time-based information such as the hour of day.

Once the dataset was ready, we performed a series of exploratory and statistical analyses. These included identifying peak and low activity hours, comparing daytime versus nighttime usage, studying domestic versus international communication patterns, and finally analyzing the relationship between SMS and call volumes at the grid level using Pearson correlation.

Throughout the analysis, we relied mainly on **Pandas for data manipulation**, **NumPy for statistical computations**, and **Matplotlib for visualization**, keeping the workflow transparent and reproducible.

---

## Key Decisions and Methodology

### Data Loading and Merging

We loaded the three required CSV files (`sms-call-internet-mi-2013-11-02.csv`, `sms-call-internet-mi-2013-11-04.csv`, and `sms-call-internet-mi-2013-11-06.csv`) and concatenated them into a single DataFrame. We also preserved the original timestamp information and later extracted the hour component for time-based analysis.

This merging step resulted in a combined dataset containing **6,564,031 total records** across all three days, covering **10,000 unique grid squares (CellID)** and **302 unique country codes**.

---

### Handling Missing Values

One of the major challenges in this dataset was the large number of missing values, especially in the SMS, call, and internet columns. Rather than dropping rows (which would have removed most of the data), we decided to **fill missing values using column-wise mean interpolation**.

This approach allowed us to:

* Preserve the full spatial and temporal coverage of the dataset
* Maintain consistency across grids and hours
* Avoid introducing bias from selectively removing records

In total, **5,880,441 records** contained at least one missing value and were modified during this step. While mean imputation is a simplification, it was an appropriate and practical choice given the scale of the data and the exploratory nature of this analysis.

---

### Feature Engineering

After handling missing values, we created several aggregate features that simplified downstream analysis:

* `total_sms` = smsin + smsout
* `total_calls` = callin + callout
* `total_internet` = internet

These aggregate metrics allowed us to analyze overall activity levels instead of treating incoming and outgoing traffic separately. We also extracted the **hour of day** from the datetime column to support hourly trend analysis.

---

### Temporal Analysis

Using the engineered features, we analyzed how mobile activity varies over the course of a day. We computed descriptive statistics (mean, median, standard deviation, minimum, and maximum) for total calls by hour and visualized hourly averages.

We also defined:

* **Daytime:** 6:00 AM – 8:00 PM
* **Nighttime:** 8:00 PM – 6:00 AM

This allowed us to compare activity levels between daytime and nighttime periods in a clear and interpretable way.

---

### Domestic vs International Communication

To study international communication behavior, we separated the dataset into:

* **Domestic traffic:** country code 39 (Italy)
* **International traffic:** all other country codes

We compared hourly call patterns, total call volumes, total SMS volumes, and the ratio of incoming to outgoing international calls. This helped us understand whether international communication follows the same daily rhythms as domestic activity.

---

### Statistical Analysis with NumPy

For statistical comparisons, we relied on NumPy rather than higher-level abstractions where possible. In particular, we used NumPy to:

* Compute percentages of domestic vs international calls and SMS
* Calculate the ratio of incoming to outgoing international calls
* Aggregate SMS and call volumes at the grid level
* Compute the **Pearson correlation coefficient** between total SMS and total call volumes

This approach kept the analysis efficient and explicit, which is especially important when working with large datasets.

---

## Summary of Key Findings

* The combined dataset contains **6.56 million records**, covering **10,000 grid squares** across Milan.
* **Missing values were widespread**, especially in SMS and call-related columns, and were successfully handled using mean interpolation.
* **17:00 (5 PM)** is the most common peak hour for call activity across all grids, with other busy periods around **11:00** and **18:00**.
* The lowest overall activity occurs around **03:00 AM**, reflecting reduced nighttime usage.
* Approximately **73.5% of total activity happens during daytime**, while **26.5% occurs at night**.
* **Domestic calls show strong daily patterns**, peaking during business and evening hours.
* **International calls remain relatively stable throughout the day**, indicating they are less sensitive to local working hours.
* **International communication dominates overall volume**, accounting for about **66.9% of calls** and **75.0% of SMS traffic**.
* International calls are more **incoming than outgoing**, with an incoming-to-outgoing ratio of approximately **1.67**.
* At the grid level, **SMS and call volumes are very strongly correlated**, with a Pearson correlation coefficient of **0.986**. This indicates that areas with high SMS activity also tend to have high call activity.

---

## Reproducibility Notes

Due to GitHub file size limitations, the raw datasets are **not included** in this repository. To reproduce the analysis:

1. Download the dataset from Kaggle:
   *Telecom Italia Mobile Phone Activity Dataset*
2. Place the extracted files in:
   `Assignment-1/data/raw/mobile_phone_activity/`
3. Run the notebook:
   `Assignment-1/notebooks/iguygael.ipynb`

All preprocessing steps, feature engineering, and analyses are fully documented and executable within the notebook.

