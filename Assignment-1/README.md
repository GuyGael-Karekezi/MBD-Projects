# Mobile Big Data (MBD) – Assignment 1

## Course
Mobile Big Data Analytics and Management

## Student
- Name: Ishimwe Karekezi Guy Gael  
- AndrewID: iguygael

## Overview
This project analyzes mobile phone activity data (SMS, calls, and internet usage)
collected over multiple days in Milan. The objective is to explore temporal patterns,
grid-level behavior, and differences between domestic and international communication
using mobile big data analytics techniques.

## Dataset
The dataset is sourced from Kaggle and includes:
- SMS activity (incoming and outgoing)
- Call activity (incoming and outgoing)
- Internet traffic usage
- Spatial grid identifiers and timestamps

Raw data files are not included directly in this repository due to GitHub file size
limitations.

### Data Access and Reproducibility
## Data Access and Reproducibility

The raw datasets used in this assignment are publicly available on Kaggle:
https://www.kaggle.com/datasets/marcodena/mobile-phone-activity

Due to GitHub file size limitations, the raw CSV files are not included in this repository.
To reproduce the results, download the dataset from Kaggle and place the files under:

Assignment-1/data/raw/mobile_phone_activity/

The notebook assumes this directory structure when loading the data.


Run the notebook located in `Assignment-1/notebooks/iguygael.ipynb`.

All preprocessing, feature engineering, and analysis steps are fully documented
and executed within the notebook.

## Approach
The analysis follows these main steps:
1. Load and merge three daily mobile activity datasets
2. Clean the data and handle missing values using mean interpolation
3. Perform feature engineering to create aggregate metrics:
- total_sms
- total_calls
- total_internet
4. Extract temporal features such as hour of day
5. Analyze peak and low activity periods
6. Compare daytime versus nighttime activity
7. Compare domestic (Italy) versus international communication patterns
8. Perform statistical analysis and correlation using NumPy and Pearson correlation

## Key Decisions
- Missing values were handled using column-wise mean interpolation
- Analysis was performed at both record level and grid level
- Pearson correlation was used to study the relationship between SMS and call volumes

## Key Findings
- Mobile activity exhibits clear hourly patterns with identifiable peak hours
- Most activity occurs during daytime hours
- Domestic and international calls show different temporal behaviors
- SMS and call volumes are positively correlated at the grid level

## Repository Structure
```text
Assignment-1/
├── notebooks/
│   └── iguygael.ipynb
├── data/
│   └── processed/
├── README.md
├── requirements.txt
└── .gitignore
