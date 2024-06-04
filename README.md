Exploratory Data Analysis (EDA) Project – World Layoffs
Project Overview
Aim
The objective of this project is to conduct an exploratory data analysis (EDA) on the World Layoffs dataset using SQL queries. This analysis aims to extract meaningful insights and trends related to layoffs globally from 2020 to 2023. Following data cleaning, the EDA involves investigating various aspects such as date ranges, maximum layoffs, company-specific layoffs, industry trends, and funding patterns.
Dataset Description
The dataset used for this analysis contains information on layoffs across different companies and industries from 2020 to 2023. Key fields include:
•	Company: Name of the company
•	Industry: Industry to which the company belongs
•	Total Laid Off: Number of employees laid off
•	Percentage Laid Off: Ratio of employees laid off to total employees
•	Date: Date when the layoff occurred
•	Stage: Hierarchical stage affected by the layoff
•	Country: Country where the company is located
•	Location: Specific location of the firm
•	Funds Raised: Funds raised by the company in millions
Data Cleaning Summary
Before conducting the EDA, the dataset underwent comprehensive cleaning, including:
1.	Duplicate Removal: Identified and removed duplicate records.
2.	Date Field Standardization: Updated data types for the date field to ensure consistency.
3.	Data Entry Standardization: Standardized entries in the date and country fields.
4.	Error Formatting: Corrected formatting errors in the industry and country fields.
5.	Handling NULL Values: Managed NULL values using statistical imputation.
6.	Statistical Updates: Applied descriptive statistics to fill in missing data.

Exploratory Data Analysis (EDA)
SQL Queries and Insights
Dataset Overview

USE World_layoff;
SELECT * FROM layoffs_staging2;
Date Range Analysis
Select min(date), max(date)
from layoffs_staging2;
Insight: This date range captures the period affected by COVID-19 (during and after).
Maximum Layoffs in a Single Day
Select max(total_laid_off) 
from Layoffs_staging2;
Insight: The maximum number of employees laid off in a single day was 12,000.
Maximum Layoffs and Their Percentage
Select max(total_laid_off), max(percentage_laid_off)
from Layoffs_staging2;
Companies with 100% Layoffs
Select count(company)
from layoffs_staging2
where percentage_laid_off = 1; 

Select *
from layoffs_staging2
where percentage_laid_off = 1
Order by total_laid_off DESC;
Total Employees Laid Off by Company
Select company, sum(total_laid_off)
from layoffs_staging2
Group by company
order by 2 DESC;
Industry with Maximum Layoffs
Select industry, sum(total_laid_off)
from layoffs_staging2
Group by industry
order by 2 DESC;
Country with Maximum Layoffs
Select country, sum(total_laid_off)
from layoffs_staging2
Group by country
order by 2 DESC;
Yearly Layoffs
Select Year(date), sum(total_laid_off)
from layoffs_staging2
Group by Year(date)
order by 1 DESC;
Layoffs by Hierarchical Stage
Select stage, sum(total_laid_off)
from layoffs_staging2
Group by stage
order by 2 DESC; -- laid_offs based on stage

Select stage, avg(percentage_laid_off)
from layoffs_staging2
Group by stage
order by 2 DESC;  -- % laid_offs based on the stage
Monthly Layoffs
Select substring(date,1,7) as month, sum(total_laid_off)
from layoffs_staging2
where substring(date,1,7) is not null
group by month
Order by 1 ASC;
Company with Maximum Funds Raised
Select company, percentage_laid_off, max(funds_raised_millions)
from layoffs_staging2;
Total Funds Raised by Company
Select Company, Sum(funds_raised_millions) as Total_raised_funds
from layoffs_staging2
Group by company
order by total_raised_funds DESC;
Yearly Funds Raised by Company
Select Company, Sum(funds_raised_millions) as Total_raised_funds, year(date) as year
from layoffs_staging2
Group by company
order by total_raised_funds DESC;
Rolling Total of Layoffs
With Rolling_total as 
(
Select substring(date,1,7) as month, sum(total_laid_off) as total_off
from layoffs_staging2
where substring(date,1,7) is not null
group by month
Order by 1 ASC
)
Select month, sum(total_off) over (order by month) as rolling_total
from Rolling_total;
Company Layoffs by Year
Select company, year(date), sum(total_laid_off)
from layoffs_staging2
Group by company, year(date)
order by 1 ASC;
Top 5 Companies by Layoffs Each Year

With company_year (company,year,total_laid_off) as
(
Select company, year(date), sum(total_laid_off)
from layoffs_staging2
Group by company, year(date)
), company_year_rank as
(
Select *, 
dense_rank() over(partition by year order by total_laid_off DESC) as ranking
from company_year where year is not null 
order by ranking ASC
)
Select *
from company_year_rank
where ranking <= 5 order by year;
Top 5 Companies by Funds Raised Each Year

With company_year (company, year, total_laid_off, percentage_laid_off, Total_funds_raised) as
(
Select company, year(date) as year, total_laid_off, percentage_laid_off, sum(funds_raised_millions) as total_funds_raised
from layoffs_staging2
Group by company, year(date)
), fundranking as
(
Select *, 
dense_rank() over(partition by year order by total_funds_raised DESC) as fundranking
from company_year where year is not null 
order by fundranking ASC
)
Select *
from fundranking 
where fundranking<= 5
order by year;
Results and Learnings
Results
•	Time Range: The dataset covers layoffs from early 2020 to late 2023, highlighting the ongoing and post-impact of COVID-19.
•	Layoff Peaks: Identified peak layoff periods, company, and maximum layoffs on a single day.
•	Company and Industry Trends: Analyzed which companies and industries experienced the highest layoffs.
•	Country Trends: Determined the countries with the most layoffs.
•	Hierarchical Impact: Examined layoffs across different hierarchical stages.
•	Funding Insights: Investigated the companies with the maximum funding throughout the years.
Learnings
•	SQL Proficiency: Enhanced skills in writing complex SQL queries for data analysis.
•	Trend Analysis: Gained insights into global layoff trends and patterns during the time period of 2020-2023.
•	Statistical Application: Applied statistical techniques to understand and interpret data trends.
•	Data-Driven Decisions: Developed the ability to make data-driven decisions based on exploratory analysis.
Conclusion
This exploratory data analysis project provides valuable insights into global layoff trends from 2020 to 2023. The cleaned and analyzed dataset can serve as a critical resource for understanding the impact of economic events on employment across various industries and regions. The findings from this EDA will inform future analyses and support strategic decision-making processes.

