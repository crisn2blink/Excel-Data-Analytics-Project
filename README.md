# My Excel Data Analytics Project

This repository contains the workbooks and resources I used to create both projects:

- The Salary Dashboard
- Salary Analysis

<br>

while working through **Luke Barousse's course "Excel for Data Analytics"**

<br>
All the Excel files used to create the dashboards and reports for the projects are included and can be easily accessed.

* * *


## Salary Dashboard

This data jobs salary dashboard was created for the purpose of helping job seekers (having a data background) investigate salaries for their desired jobs and ensure they are being adequately compensated.

![](Project_1/images/1_Salary_Dashboard_Final_Dashboard.gif)
<br>

Essentially, this dashboard simply a tool with a simple user interface that serves a specific purpose.  


### User Interface

A single interactive dashboard page where the user has three drop-down menus to make a selection in (the inputs):

<br>

- Job Title
- Country
- Job Type

<br>

The dashboard will then populate (based on the selections), the following outputs:

<br>

- Median Salary
- Top Job Platform
- Job Count (number of job postings found)  


### The Data

Scraped from many job posting sites and collected by Luke Barousse. More about the data (along with the data itself) can be found here [datanerd.tech](https://datanerd.tech/about)

- How the Data Collection Works: “Every day my pipeline collects thousands of job postings from job platforms across 170+ countries. Each posting runs through a data pipeline that extracts skills, normalizes job titles, and calculates salary benchmarks. The results are aggregated and made available here, updated daily.” - [datanerd.tech:](https://datanerd.tech: "https://datanerd.tech:") Luke Barousse
- How the Data is Pulled: I pull job postings via SerpApi from Google Jobs search results. Their API is what makes this daily collection possible

<br>

Time period covered:

1/1/2025 - 6/30/2026

<br>

Last updated: 

7/23/2026

* * *

## Salary Analysis

This Excel workbook takes things a step further and allows us to gain a deeper insight into the job market for positions in the data industry.



### Set Up

- The workbook is divided into four separate dashboards or worksheet tabs.

<br>

    - Skill_Job_Analysis
    - Salary_Vs_Skills
    - Salary_Analysis
    - Skill_Salary_Analysis

<br>

Each worksheet was engineered to help us gain insight pertaining to a specific topic.

<br>

With the goal being to gain a broad understanding of the job market to grant us an upper hand in job seeking and salary negotiations.



### The Data

Scraped from many job posting sites and collected by Luke Barousse. More about the data (along with the data itself) can be found here [datanerd.tech](https://datanerd.tech/about)

- How the Data Collection Works: “Every day my pipeline collects thousands of job postings from job platforms across 170+ countries. Each posting runs through a data pipeline that extracts skills, normalizes job titles, and calculates salary benchmarks. The results are aggregated and made available here, updated daily.” - [datanerd.tech:](https://datanerd.tech: "https://datanerd.tech:") Luke Barousse
- How the Data is Pulled: I pull job postings via SerpApi from Google Jobs search results. Their API is what makes this daily collection possible

<br>

Time period covered:

1/1/2023 - 6/30/2026

<br>

Last updated: 

7/23/2026

<br>

Below are just a few examples of what type of analysis the workbook covers:

<br>

[Check out the analysis Excel workbook here](https://github.com/crisn2blink/Excel-Data-Analytics-Project/tree/main/Project_2)  

![Number of skills w/ pay for each job](Project_2/images/2_Project_Analysis_Chart1.png)

![Likelihood top jobs found in posting](Project_2/images/2_Project_Analysis_Chart3.png)

# Project Update

Upon further inspection of the data used for the project, many records (around 1,700) pertaining to countries other than the United States had exorbitant amounts that were irrational in context for the yearly salary column.

- Many of these records were from foreign countries and it was obvious no currency conversion had been performed.
    - In fact, there is no record stating that _any_ currency conversion was ever performed or that all of the currencies were set to USD.

<br>

Because of this, the data for all countries is unreliable.

<br>

## Solution

_STEP 1_: The only way to save the work that has been done and keep the **Dashboard** and the **Salary   
Analysis Workbook** earnest, was to remove all of the records pertaining to countries other than the United States.

- This initial filtering dropped the amount of records from the original number of **67,078** to **55,357**.
    - This was only a decrease of around 12k records (as most were from the USA).

<br>

_STEP 2_: At this point, since it was obvious the data had not been properly inspected, I decided to perform the ETL process loading the data into Power Query.

The following cleaning steps were taken:

1. All columns were TRIMMED & CLEANED
2. The salary\_year\_avg & the salary\_hour\_avg column data type was changed to currency (form text)
3. The job\_posted\_date cloumn data type was changed to date/time (from text)
4. Duplicate records (where all of the fields across the board were identical save for the “job\_posted\_date” and the “search\_location”) were removed.

<br>

Upon completion of the ETL process, the number of records was further reduced from **55,357** to the final amount of **39,517**.

## Summary

- Our model now only serves the U.S market
- We went form 67,078 to 39,517 records

<br>

We gained confidence in our model and increased the integrity of our data.

<br>

For the sake of respect to the project, both the original files (with the data integrity issues) for:

- The Salary Dashboard
- The Salary Analysis

<br>

Will remain in the project files labeled with the prefix “old\_”

- The update files will simply have the prefix of “final\_” as well as the suffix “USA”

# REPOSITORY STRUCTURE
```
Excel-Data-Analytics-Project/                    # Excel data analytics portfolio project and course practice files
│
├── 1_Spreadsheets_Intro/                         # Introductory spreadsheet workbook exercises
│   ├── 1_Worksheets.xlsx                         # Practice workbook for Excel worksheets
│   ├── 2_Workbooks.xlsx                          # Practice workbook for Excel workbooks
│   └── Job_Postings_10_Rows.xlsx                 # Small sample job postings workbook
│
├── 2_Formulas_Functions/                         # Excel formulas and functions practice files
│   ├── 1_Formulas_Intro.xlsx                     # Introductory formulas workbook
│   ├── 2_Formulas_and_Functions_P1_Problem.xlsx  # Formulas and functions practice problem, part 1
│   ├── 2_Formulas_and_Functions_P2_Problem.xlsx  # Formulas and functions practice problem, part 2
│   ├── 2_Functions_Intro.xlsx                    # Introductory functions workbook
│   ├── 3_Logical_Functions.xlsx                  # Logical functions practice workbook
│   ├── 4_Math_Function.xlsx                      # Math functions practice workbook
│   ├── 5_Statistical_Functions.xlsx              # Statistical functions practice workbook
│   ├── 6_Array_Formulas.xlsx                     # Array formulas practice workbook
│   ├── 7_Lookup_Functions.xlsx                   # Lookup functions practice workbook
│   ├── 8_Text_Functions.xlsx                     # Text functions practice workbook
│   └── 9_Date_Time_Functions.xlsx                # Date and time functions practice workbook
│
├── 3_Charts_Graphs/                              # Excel charts, graphs, and visual analysis practice files
│   ├── 1_Charts_Intro.xlsx                       # Introductory charts workbook
│   ├── 2_Charts_Advanced.xlsx                    # Advanced charting workbook
│   ├── 3_Charts_P1_Problem.xlsx                  # Charts practice problem, part 1
│   ├── 3_Charts_P2_Problem.xlsx                  # Charts practice problem, part 2
│   ├── 3_Charts_Statistics.xlsx                  # Statistical charts workbook
│   └── 4_Sparklines.xlsx                         # Sparklines practice workbook
│
├── 4_Spreadsheets_Advanced/                      # Advanced spreadsheet tools and formatting practice files
│   ├── 1_Tables.xlsx                             # Excel tables practice workbook
│   ├── 2_Formatting.xlsx                         # Formatting practice workbook
│   ├── 3_Collaboration.xlsx                      # Collaboration features practice workbook
│   └── 4_Spreadsheet_Advanced_Problem.xlsx       # Advanced spreadsheet practice problem
│
├── 5_Pivot_Tables/                               # Pivot table and pivot chart practice files
│   ├── 0_Pivot_Tables.xlsx                       # Pivot tables overview workbook
│   ├── 1_PivotTable_Intro_Problem.xlsx           # Introductory pivot table practice problem
│   ├── 1_Power_Pivot_Intro_Pt1.xlsx              # Power Pivot introduction workbook
│   ├── 2_PivotTable_Advanced_Problem.xlsx        # Advanced pivot table practice problem
│   ├── 2_Pivot_Table_Advanced.xlsx               # Advanced pivot table workbook
│   ├── 3_PivotCharts_Problem.xlsx                # Pivot charts practice problem
│   ├── ~$1_Power_Pivot_Intro_Pt1.xlsx            # Temporary Excel lock file; should be removed from repo
│   └── ~$2_Pivot_Table_Advanced.xlsx             # Temporary Excel lock file; should be removed from repo
│
├── 6_Analysis_Add-Ins/                           # Excel analysis add-ins and what-if analysis practice files
│   ├── 1_Analysis_Add-ins.xlsx                   # Analysis add-ins practice workbook
│   ├── 1_Analysis_Add-ins_Problem.xlsx           # Analysis add-ins practice problem workbook
│   ├── 2_Data_Tables.xlsx                        # Data tables practice workbook
│   ├── 2_Data_Tables_Problem.xlsx                # Data tables practice problem workbook
│   ├── 3_Analysis_ToolPak.xlsx                   # Analysis ToolPak practice workbook
│   └── 3_Analysis_ToolPak_Problem.xlsx           # Analysis ToolPak practice problem workbook
│
├── 7_Power_Query/                                # Power Query extraction, transformation, and loading practice files
│   ├── 01_Power_Query_Intro.xlsx                 # Power Query introduction workbook
│   ├── 1_Power_Query_Intro_Problem.xlsx          # Power Query introduction practice problem
│   ├── 2_Power_Query_Editor.xlsx                 # Power Query Editor practice workbook
│   ├── 2_Power_Query_Task.xlsx                   # Power Query task workbook
│   ├── 2_Power_Query_Window_Problem.xlsx         # Power Query window practice problem
│   ├── 3_Advanced_Tranformations_Problem.xlsx    # Advanced transformations practice problem
│   ├── 4_Append.xlsx                             # Append queries practice workbook
│   ├── 4_Append_Merge_Problem.xlsx               # Append and merge queries practice problem
│   ├── 5_M_Language.xlsx                         # M language practice workbook
│   └── 5_M_Language_Problem.xlsx                 # M language practice problem
│
├── 8_Power_Pivot/                                # Power Pivot, data model, and DAX practice files
│   ├── 1_Power_Pivot_Intro_Problem.xlsx          # Power Pivot introduction practice problem
│   ├── 1_Power_Pivot_Intro_Pt1.xlsx              # Power Pivot introduction workbook
│   ├── 3_DAX_Intro_Problem.xlsx                  # Introductory DAX practice problem
│   ├── 4_DAX_Advanced_Problem.xlsx               # Advanced DAX practice problem
│   └── Power_Pivot_Window.xlsx                   # Power Pivot window practice workbook
│
├── Project_1/                                    # Salary Dashboard Excel project
│   ├── images/                                   # Dashboard screenshots, KPI images, charts, and demo GIFs
│   ├── source_data/                              # Source datasets used for the Salary Dashboard project
│   ├── README.md                                 # Salary Dashboard project overview and explanation
│   ├── final_project_dashboard_USA.xlsx          # Final USA-only salary dashboard workbook
│   └── old_project_dashboard.xlsx                # Original salary dashboard workbook
│
├── Project_2/                                    # Salary Analysis Excel project
│   ├── images/                                   # Salary analysis screenshots and chart images
│   ├── source_data/                              # Source datasets used for the Salary Analysis project
│   ├── README.md                                 # Salary Analysis project overview and explanation
│   ├── final_analytics_project_USA.xlsx          # Final USA-only salary analysis workbook
│   └── old_analytics_project.xlsx                # Original salary analysis workbook
│
├── .gitattributes                                # Git attributes configuration
├── LICENSE                                       # Project license
└── README.md                                     # Main project overview, project descriptions, data notes, and update summary
│
├── .gitattributes                                # Git attributes configuration
├── LICENSE                                       # Project license
└── README.md                                     # Main project overview, project descriptions, data notes, and update summary
```
