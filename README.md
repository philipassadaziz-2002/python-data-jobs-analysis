# Python Data Jobs Analysis

## Overview

This project analyzes job market demand for data professionals across three key dimensions:
skill trends throughout the year, skill requirements by job role, and compensation for
Data Scientists in the United States.

The goal is to move beyond surface-level job postings and uncover the underlying patterns
that drive hiring decisions, skill priorities, and salary benchmarks across the data industry.

---

## Business Questions

### 1. Which data analyst job skills are most in-demand, and how do they trend seasonally throughout the year?

**Analysis Approach:**
- Filter for Data Analyst job postings only
- Extract top 5 in-demand skills
- Track monthly trends across all months
- Visualize seasonality patterns

**🐍 Script:** [Skill Demand Analysis](/Queries/Q1_Skill_Demand_analysis.ipynb)

**📊 Visualization:**

![Skill Demand Analysis](/images/Q1_Skill_Demand_analysis.png)

**📊 Key Findings:**
- SQL dominates demand (~10,000 postings in Jan, declining to ~6,000 by Nov)
- Excel demand drops sharply (8,000 → 5,000) — steepest decline among top 5
- Python maintains consistent demand (~5,000 postings throughout the year)
- Tableau shows stable but lower demand (~4,000 range)
- Power BI remains supplementary skill (~3,000-4,000 range)

**💡 Business Insights:**
- SQL is non-negotiable for Data Analyst roles — invest heavily
- Excel remains critical despite declining demand
- Python + SQL combination is the minimum competitive requirement
- Power BI & Tableau are supplementary, not primary requirements

---

### 2. How do skill requirements differ across Data Analyst, Data Engineer, and Data Scientist roles?

**Analysis Approach:**
- Count skill frequency for each job title separately
- Extract top 5 skills for each role
- Compare skill overlap and unique requirements
- Identify role-specific differentiators

**🐍 Script:** [Top Skills Comparison Across Job Titles](/Queries/Q2_Top_Skills_Comparison_Across_Job_Titles.ipynb)

**📊 Visualization:**

![Q2](/images/Q2_Top_Skills_Comparison_Across_Job_Titles.png)

**📊 Key Findings:**
- **Data Analyst:** SQL (100k+), Excel (75k), Python (60k), Tableau (45k), Power BI (40k)
- **Data Engineer:** Python (105k+), SQL (95k), AWS (60k), Azure (55k), Spark (50k)
- **Data Scientist:** Python (115k+), SQL (85k), R (65k), SAS (40k), Tableau (25k)
- SQL is universal across all three roles — mandatory skill for all
- Python is highest for Data Scientists, critical for Engineers, important for Analysts
- Cloud skills (AWS, Azure) unique to Data Engineer roles
- Statistics tools (R, SAS) exclusive to Data Scientists

**💡 Business Insights:**
- Different roles require different skill stacks — tailor learning paths accordingly
- Data Engineers focus on infrastructure (cloud, big data tools) — more specialized
- Data Scientists need statistical depth (R, SAS) beyond just programming
- SQL + Python combination is the bridge skill across all three roles
- Data Analysts need business tools (Excel, Tableau) for communication and dashboards

---

### 3. Which companies offer the highest median salaries for Data Scientists in the United States?

**Analysis Approach:**
- Filter for Data Scientist positions in United States only
- Remove records with missing salary data
- Calculate median salary by company
- Identify top 5 highest-paying companies

**🐍 Script:** [Top 5 Companies by Median Salary for Data Scientists](/Queries/Q3_Top%205_Companies_by_Median_Salary_for_Data_Scientists.ipynb)

**📊 Visualization:**

![Q3](/images/Q3_Top%205_Companies_by_Median_Salary_for_Data_Scientists.png)

**📊 Key Findings:**
- ReServe leads with $585,000 median salary
- East River Electric Power Cooperative offers $537,000
- Three companies tied at $375,000 (Blue Cross/Blue Shield, Big Lots, Analog Devices)
- Salary range: $375,000 - $585,000 (56% premium between lowest and highest)
- Top payer (ReServe) offers $210,000+ more than bottom tier

**💡 Business Insights:**
- Significant salary variation exists among data scientist employers — strategic job selection matters
- Tech-adjacent companies (ReServe, utilities) offer premium compensation
- ReServe's premium suggests high-impact data science responsibilities or specialized domain knowledge
- Career progression opportunity: moving to top-tier companies can increase salary by 56%
- Geographic concentration may indicate cost-of-living adjustments — verify location details

---

## Strategic Recommendations

1. **Develop SQL + Python mastery first**
   
   Both skills are universal across Data Analyst, Engineer, and Scientist roles.
   Master these before specializing in role-specific tools to maintain flexibility.

2. **Specialize based on career path**
   
   - Data Analyst: Excel + Tableau for dashboards and communication
   - Data Engineer: Python + AWS/Azure for infrastructure and automation
   - Data Scientist: Python + R/SAS for statistical depth and modeling

3. **Target high-paying companies strategically**
   
   Salary variation of 56% between top and bottom tier companies suggests
   researching employer compensation is critical for career advancement.

---

## Technical Details

- **Data Source:** Luke Barousse's Data Jobs Dataset ([HuggingFace](https://huggingface.co/datasets/lukebarousse/data_jobs))
- **Analysis Tools:** Python, Pandas, Matplotlib, Plotly
- **Visualization:** Matplotlib (static analysis), Plotly (interactive dashboards)
