# Beyond-Data-Data-analysis-on-Job-Market-data-using-Excel
A data analysis project exploring hidden insights within the job market using Excel. This report uncovers key patterns in employment data — from role distributions and salary trends to demand hotspots — transforming raw job data into meaningful, actionable intelligence.

## Introduction

"As a former job seeker, I’ve always been surprised by the lack of data exploring the most optimal jobs and skills in the data science market. I set out to understand what skills top employers request and how to land more pay."

Recently there has been a lot of fuss and hype around Data science, AI and Machine Learning, I too am interested in these subjects and wanted to eplore the most optimal jobs and skills in the data science market. I set out to understand what skills are the most seeked after and how someone can land a high paying job.

### Questions to Analyze

To understand the data science job market, I asked the following:

1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023. 
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
    - 📊 data_jobs_all

        ![Project_Analysis_Screenshot1.png](/Resources/Images/Project_Analysis_Screenshot1.png)

    - 🛠️ data_job_skills

        ![Project_Analysis_Screenshot2.png](/Resources/Images/Project_Analysis_Screenshot2.png)

#### 🔗 Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 data_jobs_all

        ![Project_Analysis_Screenshot3.png](/Resources/Images/Project_Analysis_Screenshot3.png)

    - 🛠️ data_job_skills

        ![Project_Analysis_Screenshot4.png](/Resources/Images/Project_Analysis_Screenshot4.png)

### 📊 Analysis

#### 💡 Insights

- 📈 There is a strong positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.
- 💼 Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

    ![Skill_number_to_salary.png](/Resources/Images/Skill_number_to_salary.png)

#### 🤔 So What

- This trend emphasizes the value of acquiring multiple relevant skills, particularly for individuals aiming for higher-paying roles.

## 2️⃣ What’s the salary for data jobs in different regions?

### 🧮 Skills: PivotTables & DAX

#### 📈Pivot Table

- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
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

- 💼 Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- 💰 The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.

    ![Median_salary_US_vs_others.png](/Resources/Images/Median_salary_US_vs_others.png)

#### **🤔 So What**

- These salary insights are important for planning and salary negotiations, helping professionals and companies align their offers with market standards while considering geographical variations.

## 3️⃣ What are the top skills of data professionals?

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 I created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 Data Model

- I created a relationship between my two tables using the `job_id` column.

    ![Project_Analysis_Screenshot5.png](/Resources/Images/Project_Analysis_Screenshot5.png)

#### 📃 Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

    ![Project_Analysis_Screenshot6.png](/Resources/Images/Project_Analysis_Screenshot6.png)

### 📊Analysis

#### 💡Insights

- 💻 SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

    ![top_skills_likelihood.png](/Resources/Images/top_skills_likelihood.png)

#### 🤔So What

- Understanding prevalent skills in the industry not only helps professionals stay competitive but also guides training and educational programs to focus on the most impactful technologies.

## 4️⃣ What’s the pay of the top 10 skills?

### 📊 Skill: Advanced Charts (Pivot Chart)

#### 📈 PivotChart

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
    - 👍 **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 Analysis

#### 💡Insights

- 💰 Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- 📉 Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

    ![Combo_chart.png](/Resources/Images/Combo_chart.png)

### 🤔So What

- This chart highlights the importance of investing time in learning high-value skills like Python and SQL, which are evidently tied to higher paying roles, especially for those looking to maximize their salary in the tech industry.

## Conclusion

As a data enthusiast and former job seeker, I set out to explore the dynamics of the data science job market through this Excel-based project. Using a curated dataset of real-world job postings, I analyzed job titles, salaries, locations, and in-demand skills. By leveraging Excel tools such as Power Query, PivotTables, DAX, and data visualizations, I uncovered meaningful relationships between skill sets and compensation—highlighting the strong impact of Python, SQL, and cloud technologies on higher salaries.

I hope this project offers valuable insights for aspiring and current data professionals, helping them understand the skills that drive better career opportunities and pay growth.

## Extended Findings

- After completing the main analysis, it’s tempting to jump straight into job applications. However, as true data enthusiasts, we should leave no stone unturned. One more interesting aspect to explore is: “When do we see the highest number of job postings?”

### Steps Involved

 - By grouping the data based on the job_posted_date column, we can aggregate job postings by quarter, month, and day to uncover temporal trends.

### 📊Analysis

#### 💡Insights

 - The data reveals that the first two quarters of the year have a comparable number of job postings.
 - There’s a slight increase in Q3, followed by a sharp decline in Q4.
 - This quarterly pattern aligns with the monthly breakdown: job postings remain steady (around 2,500–3,300) during the first seven months, then spike in August (over 3,500, the yearly peak).
 - The last three months show the lowest activity, with November recording the fewest postings (below 2,000).
 - On a weekly level, postings remain consistent on weekdays but drop noticeably over the weekends.

    ![Jobs_per_quarter.png](/Resources/Images/Jobs_per_quarter.png)
    ![Jobs_per_month.png](/Resources/Images/Jobs_per_month.png)
    ![Jobs_per_day.png](/Resources/Images/Jobs_per_day.png)

### 🤔 So What

 - This pattern suggests that, except for the end of the year, job postings remain fairly steady throughout. Although opportunities decrease slightly toward year-end and on weekends, job seekers should continue staying active and alert—new and exciting roles can appear anytime.

    
