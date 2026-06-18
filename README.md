# Python Data Jobs Analysis

# Overview

This project analyzes job market demand for data professionals across three key dimensions:
skill trends throughout the year, skill requirements by job role, and compensation for
Data Scientists in the United States.

The goal is to move beyond surface-level job postings and uncover the underlying patterns
that drive hiring decisions, skill priorities, and salary benchmarks across the data industry.

---

# Business Questions

- 1. **Skill Demand Analysis**

 Which data analyst job skills are most in-demand, and how do they trend seasonally throughout the year?
- 2. **Top Skills Comparison Across Job Titles**

 How do skill requirements differ across Data Analyst, Data Engineer, and Data Scientist roles?
- 3. **Top 5 Companies by Median Salary For Data Scientists**

 Which companies offer the highest median salaries for Data Scientists in the United States?

# **Skill Demand Analysis**

### 1. Which data analyst job skills are most in-demand, and how do they trend seasonally throughout the year?

**Analysis Approach:**
- Filter for Data Analyst job postings only
- Extract top 5 in-demand skills
- Track monthly trends across all months
- Visualize seasonality patterns

**🐍 Script:** [Skill Demand Analysis](/Queries/Q1_Skill_Demand_analysis.md)

**📊 Visualization:**

![Skill Demand Analysis](/images/Q1_Skill_Demand_analysis.png)

**📊 Key Findings:**
- SQL dominates demand (~10,000 postings in Jan, declining to ~6,000 by Nov)
- Excel demand drops sharply (8,000 → 5,000) — steepest decline among top 5
- Python maintains consistent demand (~5,000 postings throughout the year)
- Tableau shows stable but lower demand (~4,000 range)
- Power BI remains supplementary skill (~3,000-4,000 range)



---

# **Top Skills Comparison Across Job Titles**

### 2. How do skill requirements differ across Data Analyst, Data Engineer, and Data Scientist roles?

**Analysis Approach:**
- Count skill frequency for each job title separately
- Extract top 5 skills for each role
- Compare skill overlap and unique requirements
- Identify role-specific differentiators

**🐍 Script:** [Top Skills Comparison Across Job Titles](/Queries/Q2_Top_Skills_Comparison_Across_Job_Titles.md)

**📊 Visualization:**

![Q2](/images/Q2_Top_Skills_Comparison_Across_Job_Titles.png)

**📊 Key Findings:**
- SQL is universal across all three roles — mandatory skill for all
- Python is highest for Data Scientists, critical for Engineers, important for Analysts
- Cloud skills (AWS, Azure) unique to Data Engineer roles
- Statistics tools (R, SAS) exclusive to Data Scientists



---

# **Top 5 Companies by Median Salary For Data Scientists**

### 3. Which companies offer the highest median salaries for Data Scientists in the United States?

**Analysis Approach:**
- Filter for Data Scientist positions in United States only
- Remove records with missing salary data
- Calculate median salary by company
- Identify top 5 highest-paying companies

**🐍 Script:** [Top 5 Companies by Median Salary for Data Scientists](/Queries/Q3_Top%205_Companies_by_Median_Salary_for_Data_Scientists.md)

**📊 Visualization:**

![Q3](/images/Q3_Top%205_Companies_by_Median_Salary_for_Data_Scientists.png)

**📊 Key Findings:**
- ReServe leads with $585,000 median salary
- East River Electric Power Cooperative offers $537,000
- Three companies tied at $375,000 (Blue Cross/Blue Shield, Big Lots, Analog Devices)
- Salary range: $375,000 - $585,000 (56% premium between lowest and highest)
- Top payer (ReServe) offers $210,000+ more than bottom tier





## Technical Details

- **Data Source:** Luke Barousse's Data Jobs Dataset ([HuggingFace](https://huggingface.co/datasets/lukebarousse/data_jobs))
- **Analysis Tools:** Python, Pandas, Matplotlib, Plotly
- **Visualization:** Matplotlib (static analysis), Plotly (interactive dashboards)
