# SQL_Project_Data_Job_Analysis
A comprehensive analysis of the data job market
# Introduction
This repository provides an in-depth analysis of the data job market, with a specific focus on data analyst roles. It includes insights into the highest-paying positions, the most in-demand skills, and explores the critical areas where high demand aligns with lucrative salaries in the field of data analytics. Whether you're a data professional or aspiring to enter the field, this project offers valuable information to help you navigate and excel in the competitive data job market.

SQL queries? Check them out here [Data Job Analysis](/ /)
# Background
This project was created to better understand and navigate the data analyst job market by identifying the highest-paying roles and the most in-demand skills, aiming to simplify the job search process for others.The data includes valuable information on job titles, salaries, locations, and key skills.

## Through SQL queries, I sought to answer the following questions:

Which data analyst jobs offer the highest salaries?
What skills are required for these high-paying roles?
Which skills are most in demand for data analysts?
Which skills correlate with higher salaries?
What are the most essential skills to learn?

# Tools Utilized
To thoroughly explore the data analyst job market, I relied on several essential tools:
* ### SQL
* ### PostgreSQL
* ### Visual Studio Code
* ### Github

# The Analysis
## 1. Top paying Data Analyst jobs

```sql
SELECT
    job_id,
    job_title,
    job_location,
    job_schedule_type,
    salary_year_avg,
    job_posted_date,
    name AS company_name
FROM
    job_postings_fact
LEFT JOIN company_dim ON job_postings_fact.company_id=company_dim.company_id
WHERE
    job_title_short='Data Analyst' AND
    job_location='Anywhere' AND
    salary_year_avg IS NOT NULL
ORDER BY
    salary_year_avg DESC
LIMIT 10
```
## Insights on the Top 10 Paying Data Analyst Jobs in 2023

### 1. Top Paying Companies:

- **Mantys** leads with an impressive average salary of $650,000 for data analyst positions.
- **Meta** follows with an average salary of $336,500.
- Other notable companies include AT&T with $255,829.5, Pinterest Job Advertisements with $232,423, and Uclahealthcareers offering $217,000.
### 2. Salary Distribution:
- The average salaries among the top companies vary significantly, from $184,000 at Get It Recruit - Information Technology to $650,000 at Mantys.
- The distribution shows a steep decline from the highest-paying company, suggesting that only a few companies offer exceptionally high salaries, while others are relatively lower but still competitive.
### 3. Notable Trends:
- Companies like **Meta** and **AT&T**, which are known for their large-scale operations, offer strong average salaries, reflecting their ability to compensate top talent in the field.
- **Mantys** stands out with a remarkably high average salary, which might be indicative of either a high-demand, specialized role or an outlier in the dataset.

![Top Paying Roles](im1.png)

## 2. Skills for Top Paying Jobs
To understand what skills are required for the top-paying jobs, I joined the job postings with the skills data, providing insights into what employers value for high-compensation roles.
```sql
WITH top_paaying_jobs AS(
    SELECT
        job_id,
        job_title,
        salary_year_avg,
        name AS company_name
    FROM
        job_postings_fact
    LEFT JOIN company_dim ON job_postings_fact.company_id=company_dim.company_id
    WHERE
        job_title_short='Data Analyst' AND
        job_location='Anywhere' AND
        salary_year_avg IS NOT NULL
    ORDER BY
        salary_year_avg DESC
    LIMIT 10
)
```
## Insights from the Analysis of the tOP 10 Skills for Data Analyst jobs:

1. **Top Skills**:
   - **SQL** is the most frequently mentioned skill, appearing 8 times in the dataset. This indicates a high demand or prevalence of SQL skills for the job positions in this dataset.
   - **Python** is also highly demanded, appearing 7 times, making it a critical skill for these roles.

2. **Data Tools and Technologies**:
   - **Tableau** (6 mentions) and **Snowflake** (3 mentions) suggest a strong focus on data visualization and cloud-based data warehousing tools.
   - **Excel** (3 mentions) remains a popular tool, despite the presence of more advanced data tools.

3. **Programming Languages**:
   - Apart from Python, **R** (4 mentions) and **Go** (2 mentions) are other notable programming languages required, indicating diverse programming needs across different roles.

4. **Cloud and DevOps**:
   - **Azure** (2 mentions) and **AWS** (2 mentions) highlight the need for cloud computing skills.
   - Tools like **Bitbucket**, **GitLab**, **Jenkins**, and **Git** suggest that version control and CI/CD pipelines are important in these roles.

5. **Collaborative and Project Management Tools**:
   - Tools like **Confluence**, **Jira**, and **Atlassian** (each with 2 mentions) suggest that collaboration and project management tools are essential in these roles.

6. **Less Frequent but Specialized Skills**:
   - Skills like **Hadoop**, **PySpark**, and **Databricks** appear only once, indicating that they might be required for specific roles or projects.

### Overall Insights:
- The analysis shows a strong emphasis on data analysis, data engineering, and cloud computing skills, with SQL, Python, and Tableau leading the pack.
- There's a significant demand for tools and technologies that support data management, visualization, and cloud-based solutions.
- The presence of collaboration and DevOps tools highlights the importance of teamwork and continuous integration in these roles.
- The diversity in skills also suggests that candidates need a mix of programming, data handling, and project management skills to be competitive in these roles.

![Top Skills](im2.png)
