# Activity Analysis
## Background and Overview
**Problem:** Are the individuals in the dataset more active on weekdays or weekends? /
This question explores whether individuals maintain consistent physical activity across the entire week or primarily engage in movement during structured routines on weekdays. Understanding these patterns would be crucial to helping individuals optimise their routines, as well as enabling public health officials to develop targeted policies.

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
- **3.2. visual-analysis:** Plots the average weekday and weekly steps for comparison
- **3.3. assumption-checking:** Checks normality assumptions for hypothesis testing
- **3.4. mwu-hypothesis-testing:** Performs Mann-Whitney U hypothesis test

## Executive Summary
This project investigates whether there is a significant difference in daily step counts between weekdays and weekends using a dataset of over 900 records. While visual analysis of the data suggested a potential difference, statistical testing using the Mann-Whitney U test revealed no significant difference between the two distributions ($p$=0.99). This indicates that the observed differences in step counts between weekdays and weekends are likely due to random variation rather than a true effect.


