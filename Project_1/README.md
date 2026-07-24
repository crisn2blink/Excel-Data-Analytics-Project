# Excel Salary Dashboard

## Introduction

This data jobs salary dashboard was created to help job seekers investigate salaries for their desired jobs and ensure they are being adequately compensated.

<br>

The dashboard comprises of:

- A single protected worksheet
- 3 drop down selection menus (the inputs)
- 3 graph visuals (output)
- 3 KPI cards (output)

<br>

The only interaction that the user has, is to select from the three drop-down menus the desired inputs to for the dashboard to generate the corresponding outputs (**data validation**).

<br>

Data Validation: Implementing the filtered list as a data validation rule under the `Job Title`, `Country`, and `Type` option in the Data tab ensures:

- 🎯 User input is restricted to predefined, validated schedule types
- 🚫 Incorrect or inconsistent entries are prevented
- 👥 Overall usability of the dashboard is enhanced

<br>

![](images/1_Salary_Dashboard_Data_Validation.gif)

<br>

## Instructions

Once the dashboard is open, the user selects from drop-down menus the following three criteria for the job they are interested int

<br>

Inputs

- **Job Title**
    - These are all the different job tittles from which the user can choose from (all within the field of data)
- **Country**
    - The country of interest for the job
- **Type**
    - Examples: full -time, part-time, contract, internship etc.

<br>

The dashboard will the provide the user with the following:

<br>

Outputs (*the inputs that affect the specific output will be in bold*)

1. Left-most graph: Bar graph of the top 10 job titles in the selected **country**

    - Sorted by highest to lowest median salary
    - With the selected **job title**’s bar highlighted to stand out

<br>

![](images/1_Salary_Dashboard_Chart1.png)

<br>

2. Center graph: Map of the world with countries and the respective median salaries based on the **job title** & **type**
    - The darker the shade of color indicates a higher median salary from said country

<br>

![](images/1_Salary_Dashboard_Chart2.png)

<br>

3. Right-most graph: Bar graph of all the types of jobs with the selected **job title** & **country**
    - Sorted by highest to lowest median salary for the type
    - With the selected **type**’s bar highlighted to stand out

<br>

![](Files/image%203.png)

<br>

4. Bottom left-most KPI: Median salary for the selected **job title** in the selected **country** for the selected **type**

**<br>
**

**![](Files/image%204.png)**

<br>

5. Bottom center KPI: Job platform with the highest count of job postings for the selected **job title** in the selected **country** for the selected **type**

**<br>
**

**![](Files/image%205.png)**

**<br>
**

6. Right-most KPI: The job postings count for the selected **job title** in the selected **country** for the selected **type**

**<br>
**

**![](Files/image%206.png)**

<br>

Based on all of the above outputs, the user now has an idea for the type of salary they should expect to earn for the job they are searching for.

* * *

<br>

## What Goes on in the Background (information for data geeks)

_Formulas & functions that make the visuals work_

### LEFT-MOST VISUALS

### Output #1: Bar graph of the top 10 job titles in the selected **country**

The median salaries used for this graph are calculated using the following **array** formula:

<br>

\=MEDIAN(  
  IF(

Clause 1:    (jobs\[job\_title\_short\]=$A2)\*  
Clause 2:    (jobs\[salary\_year\_avg\]<>0)\*  
Clause 3:    (jobs\[job\_country\]=Job\_Country\_D)\*  
Clause 4:    (ISNUMBER(SEARCH(Job\_Schedule\_Type\_D, jobs\[job\_schedule\_type\]))),  
Clause 5:    jobs\[salary\_year\_avg\]  
  )  
)  
<br>

**Process**:

Clause 1: The formula is applied to an array of values in an adjacent column (the job titles) and returns the value of the median salary (based on job postings) for that specific job title with all of the following conditions:

- Clause 2: Any job posting that had a value of 0 from that job title was excluded from the median calculation.
- Clause 3: Only job postings that pertain to the selected **country** (from the main dashboard drop-down menu) are included in the median calculation.
- Clause 4: Only job postings that contain the text from the selected **type** (from the main dashboard drop-down menu) within the job posting’s “type” field are included in the median calculation.
- Clause 5: If all of the conditions are met for a specific job posting, then its yearly salary figure (salary\_year\_avg\*) is included in the median calculation

<br>

**NOTE**: The title for the figure “salary\_year\_avg” is a bit misleading because this simply indicated the job posting’s yearly salary compensation (there is no average here).

<br>

- 🔍 **Multi-Criteria Filtering:** Checks job title, country, schedule type, and excludes blank salaries.
- 📊 **Array Formula:** Utilizes `MEDIAN()` function with nested `IF()` statement to analyze an array (comprised of all the job titles)
- **🔢 Formula Purpose:** This formula populates the table, returning the median salary based on job title, country, and type specified.
    - Which populates the bar graph in our dashboard visual

<br>

Background Table

[![1\_Salary\_Dashboard\_Screenshot1.png](https://github.com/crisn2blink/Excel-Data-Analytics-Project/raw/main/Project_1/images/1_Salary_Dashboard_Screenshot1.png)](https://github.com/crisn2blink/Excel-Data-Analytics-Project/blob/main/Project_1/images/1_Salary_Dashboard_Screenshot1.png)

<br>

### Output #4: KPI of median salary for the selected job title in the selected country for the selected type

The following formula is used to generate the value for the “Median Salary” KPI (output #4) which is also pulled from the above table

<br>

\=XLOOKUP(Job\_Title\_D,'Salary (Median)'!D3:D12,'Salary (Median)'!E3:E12, "No Results")

<br>

- Formula looks up the value the user selected for the “Job Title” drop-down menu and proceeds to pull the information for that specific job title from the above table. This gives us the value displayed in the Median Salary KPI (output #4)

* * *

<br>

### CENTER VISUALS

### Output #2: Map of the world with countries where there are job postings with the selected **job title** & **typ****e**

The median salaries used for this graph are calculated using the following array formula:

<br>

\=MEDIAN(  
IF(  
Clause 1:  (jobs\[job\_country\]=A3)\*  
Clause 2:  (jobs\[salary\_year\_avg\]<>0)\*  
Clause 3:  (jobs\[job\_title\_short\]=Job\_Title\_D)\*  
Clause 4:  (ISNUMBER(SEARCH(Job\_Schedule\_Type\_D, jobs\[job\_schedule\_type\]))),  
Clause 5:  jobs\[salary\_year\_avg\]  
 )  
)  
<br>

Clause 1: Notice that this formula is almost identical to the formula for output #1, the bar graph. However, there is a difference in that here, the array of adjacent values that the formula is now being applied to are the different countries (not the different job titles).

- Clause 2: Any job posting that had a value of 0 from that job title was excluded from the median calculation.
- Clause 3: Only job postings that pertain to the selected **job title** (from the main dashboard drop-down menu) are included in the median calculation.
- Clause 4: Only job postings that contain the text from the selected **type** (from the main dashboard drop-down menu) within the job posting’s “type” field are included in the median calculation.
- Clause 5: If all of the conditions are met for a specific job posting, then its yearly salary figure (salary\_year\_avg\*) is included in the median calculation

<br>

**NOTE**: The title for the figure “salary\_year\_avg” is a bit misleading because this simply indicated the job posting’s yearly salary compensation (there is no average here).

<br>

- 🔍 **Multi-Criteria Filtering:** Checks job title, country, schedule type, and excludes blank salaries.
- 📊 **Array Formula:** Utilizes `MEDIAN()` function with nested `IF()` statement to analyze an array (comprised of all the countries)
- **🔢 Formula Purpose:** This formula populates the table, returning the median salary based on job title, country, and type specified.
    - Which populates the map in our dashboard visual

<br>

Background Table  

![](Files/image%207.png)

**NOTE**: The error values come about if there are no matching job postings included in the median calculation for the specific country

<br>

### **Output #5: Top job platform with the highest count of job postings for the selected job title in the selected country for the selected type**

For this KPI we use the following array formula:

<br>

\=COUNTIFS(

 Clause 1: jobs\[job\_via\],A3,

 Clause 2: jobs\[job\_title\_short\],Job\_Title\_D,

 Clause 3: jobs\[job\_country\],Job\_Country\_D,

 Clause 4: jobs\[job\_schedule\_type\], Job\_Schedule\_Type\_D)

)

<br>

Clause 1: The formula is applied to an array of values in an adjacent column (the job platforms (job\_via)) and returns the value of the Count of job postings for that specific job platform that meet all of the following conditions:

- Clause 2: The job title for the post must match the user-selected **job title** (from the main dashboard drop-down menu)
- Clause 3: The country for the post must match the user-selected **country** (from the main dashboard drop-down menu)
- Clause 4: The job type for the post must match the user-selected **type** (from the main dashboard drop-down menu)

<br>

This results in the following reference table:

<br>

![](Files/image%208.png)

<br>

We then proceed to sort the table from highest to lowest value.

The KPI for Top Platform (output #5) simply references the top position in this table.

* * *

<br>

### RIGHT-MOST VISUALS

### Output #3: Bar graph of all the types of jobs with the selected **job title** & **country**

The median salaries used for this graph are calculated using the following array formula:

<br>

\=MEDIAN(  
  IF(

Clause 1: (jobs\[job\_title\_short\]=Job\_Title\_D)\*  
Clause 2: (jobs\[salary\_year\_avg\]<>0)\*  
Clause 3: (jobs\[job\_country\]=Job\_Country\_D)\*  
Clause 4: (ISNUMBER(SEARCH($A4, jobs\[job\_schedule\_type\]))),  
Clause 5: jobs\[salary\_year\_avg\]  
  )  
)  
<br>

Notice that this formula is almost identical to all the previous median formulas. However, there is a difference in that here, the array of adjacent values that the formula is now being applied to are the different job types (full-time, part-time, contractor etc.).

- Clause 1: Only job postings that pertain to the selected **job title** (from the main dashboard drop-down menu) are included in the median calculation.
- Clause 2: Any job posting that had a value of 0 from that job title was excluded from the median calculation.
- Clause 3:  Only job postings that pertain to the selected **country** (from the main dashboard drop-down menu) are included in the median calculation.
- Clause 4: The formula is applied to an array of values in an adjacent column (the job type) and returns the value of the median salary of job postings for that specific job type that meet all of these conditions.
- Clause 5: If all of the conditions are met for a specific job posting, then its yearly salary figure (salary\_year\_avg\*) is included in the median calculation

<br>

**NOTE**: The title for the figure “salary\_year\_avg” is a bit misleading because this simply indicated the job posting’s yearly salary compensation (there is no average here).

<br>

- 🔍 **Multi-Criteria Filtering:** Checks job title, country, schedule type, and excludes blank salaries.
- 📊 **Array Formula:** Utilizes `MEDIAN()` function with nested `IF()` statement to analyze an array (comprised of all the job types)
- **🔢 Formula Purpose:** This formula populates the table, returning the median salary based on job title, country, and type specified.
    - Which populates the bar chart in our dashboard visual

<br>

Background table

![](Files/image%209.png)

<br>

* * *

<br>

### Output #6: The job postings count for the selected **job title** in the selected **country** for the selected **type**

For this KPI we use the following array formula:

<br>

**NOTE**: Notice that I deliberately placed clause 2 ahead of clause 1 for simplification purposes and to facilitate ease of understanding.

<br>

\=COUNT(  
  IF(  
Clause 2: (jobs\[job\_country\]=Job\_Country\_D)\*  
Clause 1: (jobs\[job\_title\_short\]=$A4)\*  
Clause 3: (ISNUMBER(SEARCH(Job\_Schedule\_Type\_D, jobs\[job\_schedule\_type\]))),  
Clause 4: jobs\[salary\_year\_avg\]  
 )  
)

<br>

Clause 1: The formula is applied to an array of values in an adjacent column (the job title) and returns the value of the Count of job postings for that specific job title that meet all of the following conditions:

- Clause 2:The country for the post must match the user-selected **country** (from the main dashboard drop-down menu)
- Clause 3:  The job title for the post must match the user-selected **job title** (from the main dashboard drop-down menu)
- Clause 4: The job type for the post must include the user-selected **type** (from the main dashboard drop-down menu)

<br>

This results in the following reference table:

![](Files/image%2010.png)

<br>

Which we then proceed to use the following lookup formula to pull the Count for the **job title** value that was selected by the user (from the main dashboard drop-down menu); thus arriving at output #6.

<br>

**NOTE**: If for some reason there are no job postings for the selected **job title** when the additional filters (**country** & **type**) (from the main dashboard drop-down menu) are applied, then the lookup formula will return “No Result”.

<br>

\=XLOOKUP(Job\_Title\_D,'Data Validation'!D3:D12,'Data Validation'!E3:E12,"No Result")

* * *

<br>

### Excel Skills Used

The following Excel skills were utilized for the analysis:

- **📉 Charts**
- **🧮 Formulas and Functions**
- **❎ Data Validation**

**

* * *

**<br>

### Conclusion

I created this dashboard to highlight salary trends across a variety of data-related roles. Using data from my Excel course, it helps users make more informed career decisions by exploring how factors such as location and job type affect salary levels.

<br>
