# Fitbit Activity Analysis
## Background and Overview
**Problem:** Are the individuals in the dataset more active on weekdays or weekends? \
This project investigates whether physical activity levels, measured by step counts, differ between weekdays and weekends. Understanding these patterns is critical for assessing how structured routines, such as work or school schedules, influence activity. Insights from this analysis could guide individuals in maintaining consistent physical activity throughout the week and inform public health officials in designing policies or interventions to promote regular movement, particularly on days with lower activity levels. By addressing this question, the project aims to contribute to strategies that enhance personal health and community wellbeing.

[Python Analysis](https://github.com/nith263/weekday-weekend-activity-analysis/blob/main/python-final-analysis.ipynb)
[Excel Analysis](https://github.com/nith263/weekday-weekend-activity-analysis/blob/main/final-analysis.xlsx)

## Data Structure 
### Datasets 

**Dataset 1:** `dailySteps_merged`

This dataset captures the phsyical activity of thirty-three Fitbit users collected through an Amazon Mechanical Turk Survey. Thet data includes the total daily step count for each individual across a two month period.

**Features:**
- **Timeframe:** 03/12/2026 - 05/12/2016
- **Source:** An Amazon Mechanical Turk Survey collected the daily step data from a Fitbit tracker device.
- **Variables:**
  - `Id`: An integer column with a unique identifier for each participant
  - `ActivityDay`: The date of data that has been collected in MM/DD/YYYY format
  - `StepTotal`: The total number of steps recorded on that day
- **Calculated Fields:**
  - `Day`: The name of the day of the week e.g., Monday
  - `IsWeekend`: True if the day is a weekend or false otherwise
  - `WeekendBand`: The upper bound value of the average steps taken (used for visualisation)

**Dataset 2:** `hourlySteps_merged`

This dataset captures the hourly physical activity of 33 Fitbit users collected through the same Amazon Mechanical Turk Survey. The data includes the total hourly step count for each individual over a given timeframe.

**Features:**
- **Timeframe:** 03/12/2026 - 05/12/2016
- **Source:** An Amazon Mechanical Turk Survey collected the daily step data from a Fitbit tracker device.
- **Variables:**
  - `Id`: An integer column with a unique identifier for each participant
  - `ActivityHour`: The date and time of data collection in MM/DD/YYYY HH:MM AM/PM format
  - `StepTotal`: The total number of steps recorded on that day

## Workbook Sheets Description
### Raw Datasets 
- **1.1. dailySteps_merged:** Contains the dailyStep_merged dataset with fields transformed and calculated in Power Query
- **1.2. hourlySteps_merged:** Contains the hourlySteps_merged dataset with fields transformed in Power Query

### Outlier Calculations
- **2.1. outlier-total-days:** Determine which individual is an outlier, in terms of their total days of data
- **2.2. outlier-daily-steps:** Determine if certain days in the data contain an unusual number of steps

### Analysis Workflow
- **3.1. daily-data-cleaned:** Contains the daily data with the outlier removed
- **3.2. consistent-data:** Contains the days of data which fit the criteria of being consistent
- **3.3. descriptive-measures:** Contains descriptive measures obtained from the dataset, such as average steps and participant consistency
- **3.4. visual-analysis:** Plots the average weekday and weekly steps for comparison
- **3.5. assumption-checking:** Checks normality assumptions for hypothesis testing
- **3.6. mwu-hypothesis-testing:** Performs Mann-Whitney U hypothesis test

## Executive Summary
This project investigates whether daily step counts differ significantly between weekdays and weekends using a dataset of over 900 records. The analysis aimed to understand patterns in physical activity and their potential implications for lifestyle planning. Visual exploration suggested a possible difference in distributions, prompting a statistical test. Using the Mann-Whitney U test, no significant difference was found (p=0.99), indicating that any observed differences in step counts are consistent with random variation. These findings suggest that daily step counts are relatively stable across weekdays and weekends, but further research could explore other factors influencing activity patterns. 

## Insights Deep Dive
### Consistent Activity Tracking
![image](https://github.com/user-attachments/assets/b772e4c6-5fe1-431a-86e5-3fbaa57608f0)

The consistency metric is used to capture the percentage of days a participant consistently wore their tracker. This metric is defined using Tang et al (2018), where a valid day of activity tracking is defined as having at least 500 steps. 

- Most individuals exhibit a level of consistency with the median value close to 100%. The average consistency per participant is 90%, suggesting that majority of participants maintain regular physical activity tracking.
- A small subset of individuals shows significantly lower consistency, with values falling below 60%. These outliers indicate variability in adherence to the minimum activity threshold and may reflect unique behavioural patterns, such as intermittent activity due to lifestyle or health constraints.

### Daily Steps Distribution
![image](https://github.com/user-attachments/assets/10ecdcb1-f9fa-406c-b2d9-27db1d96abcf)

- The boxplots for the weekdays display relatively similar spreads of activity and median step counts. This can be attributed to the more the structured routines apparent during weekdays. 
- Weekends have greater variability, suggesting shifting activity patterns. The weekends have lower median step counts in comparison to all weekdays, suggesting lower activity on weekends.
- Saturday has the widest range of step counts with the highest maximum value across all days. Additionally, Saturday has a higher median value than Sunday suggesting that Saturday is an active day potentially due to social or recreational activities.

### Weekdays vs Weekend Comparison
![image](https://github.com/user-attachments/assets/e6677691-2c1e-45a2-b181-42be6188f039)

The average step count on weekdays is visibly higher than on weekends. This suggests that individuals are generally more active on weekdays, possibly due to structured routines such as work or school, which may necessitate more movement.

## Recommendations
- **Weekend Specific Challenges:** Create challenges specifically on weekend to promote physical activity for Saturdays and Sundays. 
- **Weekend Specific Rewards:** Offer rewards or discounts for users who meet step goals on weekends. 
- **Customised Weekend Reminders:** Use personalised notifications to remind users to stay active on weekends, suggesting specific activities like walking in a park, joining a fitness class, or exploring local trails.
