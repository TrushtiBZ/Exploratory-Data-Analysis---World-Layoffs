# World Layoffs Exploratory Data Analysis (EDA) Project

## Project Overview

### Aim
The objective of this project is to conduct an exploratory data analysis (EDA) on the World Layoffs dataset using SQL queries. This analysis aims to extract meaningful insights and trends related to layoffs globally from 2020 to 2023.

### Tools and Languages
- **Tool**: MySQL Workbench
- **Language**: SQL

### Dataset Description
The dataset used for this analysis contains information on layoffs across different companies and industries from 2020 to 2023. Key fields include:
- **Company**: Name of the company
- **Industry**: Industry to which the company belongs
- **Total Laid Off**: Number of employees laid off
- **Percentage Laid Off**: Ratio of employees laid off to total employees
- **Date**: Date when the layoff occurred
- **Stage**: Hierarchical stage affected by the layoff
- **Country**: Country where the company is located
- **Location**: Specific location of the firm
- **Funds Raised**: Funds raised by the company in millions

## Data Cleaning Summary
Before conducting the EDA, the dataset underwent comprehensive cleaning, including:
1. **Duplicate Removal**: Identified and removed duplicate records.
2. **Date Field Standardization**: Updated data types for the date field to ensure consistency.
3. **Data Entry Standardization**: Standardized entries in the date and country fields.
4. **Error Formatting**: Corrected formatting errors in the industry and country fields.
5. **Handling NULL Values**: Managed NULL values using statistical imputation.
6. **Statistical Updates**: Applied descriptive statistics to fill in missing data.

## Exploratory Data Analysis (EDA): [https://github.com/TrushtiBZ/Projects](https://github.com/TrushtiBZ/Exploratory-Data-Analysis---World-Layoffs/blob/f56722751372ccc74406d7cb7e260c6daa2db03e/EDA%20-%20Wrold%20Layoff.sql)

## Results and Learnings

### Results

- **Time Range**: The dataset covers layoffs from early 2020 to late 2023, highlighting the ongoing and post-impact of COVID-19.
- **Layoff Peaks**: Identified peak layoff periods, company, and maximum layoffs on a single day.
- **Company and Industry Trends**: Analyzed which companies and industries experienced the highest layoffs.
- **Country Trends**: Determined the countries with the most layoffs.
- **Hierarchical Impact**: Examined layoffs across different hierarchical stages.
- **Funding Insights**: Investigated the companies with the maximum funding throughout the years.


### Learnings

- **SQL Proficiency**: Enhanced skills in writing complex SQL queries for data analysis.
- **Trend Analysis**: Gained insights into global layoff trends and patterns during the COVID-19 pandemic.
- **Statistical Application**: Applied statistical techniques to understand and interpret data trends.
- **Data-Driven Decisions**: Developed the ability to make data-driven decisions based on exploratory analysis.

## Conclusion

This exploratory data analysis project provides valuable insights into global layoff trends from 2020 to 2023. The cleaned and analyzed dataset can serve as a critical resource for understanding the impact of economic events on employment across various industries and regions. The findings from this EDA will inform future analyses and support strategic decision-making processes.
