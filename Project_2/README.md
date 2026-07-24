# Salary Analysis

## Introduction

This analysis is of the data industry job market and is based on data from job postings (from various online sources).
The analysis was completed as part of Luke Barousse's online Excel Data Analytics course.

This README was taken directly from Luke's Git Repository for his course and highlights step-by-step how we formed our analysis
and answered four major questions (each with a dedicated tab within the Excel workbook).


### Questions to Analyze

1. **Do more skills get you better pay?** (Salary_Vs_Skills)
2. **What’s the salary for data jobs in different regions?** (Salary_Analysis)
3. **What are the top skills of data professionals?** (Skill_Job_Analysis)
4. **What’s the pay for the top 10 skills?** (Skill_Salary_Analysis)

### Excel Skills Used

The following Excel skills were utilized for the analysis:

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 1/1/2023 - 6/30/2026.

It includes detailed information on:

- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

## 1️⃣ Do more skills get you better pay?

### 🔍 Skill: Power Query (ETL)

#### 📥 Extract

- I first used Power Query to extract the original data (`data_salary_all.xlsx`) and create two queries:
    - 🗃️ First one with all the data jobs information.
    - 🔧 The second listing the skills for each job ID.

#### 🔄 Transform

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.  
    - 📊 data\_jobs\_all

[![2\_Project\_Analysis\_Screenshot1.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot1.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot1.png)
    - 🛠️ data\_job\_skills

[![2\_Project\_Analysis\_Screenshot2.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot2.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot2.png)

#### 🔗 Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 data\_jobs\_all

[![2\_Project\_Analysis\_Screenshot3.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot3.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot3.png)
    - 🛠️ data\_job\_skills

[![2\_Project\_Analysis\_Screenshot4.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot4.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot4.png)

### 📊 Analysis

#### 💡 Insights

- 📈 There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Senior Data Scientist.

[![2\_Project\_Analysis\_Chart1.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Chart1.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Chart1.png)

## 2️⃣ What’s the salary for data jobs in different regions?

### 🧮 Skills: PivotTables & DAX

#### 📈Pivot Table

- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- 🧮 Then I added new measure to calculate the median salary for United States jobs.

```
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States")

```

#### 🧮 DAX

- To calculate the median year salary I used DAX.

```
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])

```

### 📊 Analysis

#### 💡 Insights

- 💼 Job roles like Senior Data Engineer and Data Scientist have higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- 💰 The salary disparity between US and Non-US roles is particularly notable in high-tech jobs.

[![2\_Project\_Analysis\_Chart2.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Chart2.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Chart2.png)

## 3️⃣ What are the top skills of data professionals?

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 I created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 Data Model

- I created a relationship between my two tables using the `job_id` column.

[![2\_Project\_Analysis\_Screenshot5.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot5.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot5.png)

#### 📃 Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

[![2\_Project\_Analysis\_Screenshot6.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Screenshot6.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Screenshot6.png)

### 📊Analysis

#### 💡Insights

- 💻 SQL and Python dominate as top skills in data-related jobs.
- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

[![2\_Project\_Analysis\_Chart3.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Chart3.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Chart3.png)

## 4️⃣ What’s the pay of the top 10 skills?

### 📊 Skill: Advanced Charts (Pivot Chart)

#### 📈 PivotChart

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
    - 👍 **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 Analysis

#### 💡Insights

- 💰 Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- 📉 Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

[![2\_Project\_Analysis\_Chart4.png](https://github.com/lukebarousse/Excel_Data_Analytics_Course/raw/main/0_Resources/Images/2_Project_Analysis_Chart4.png)](https://github.com/lukebarousse/Excel_Data_Analytics_Course/blob/main/0_Resources/Images/2_Project_Analysis_Chart4.png)

## Conclusion

All of the analysis tabs found within this workbook will help job seekers gain a deeper understanding pertianing to the data job market: what skills are in the highest demand and what
pay looks like for different scenarios.
