

```python
# Filter for Data Analyst positions only
DF_DA = df[df['job_title_short'] == 'Data Analyst'].copy()

# Extract month from job posting date
DF_DA['job_posted_month'] = DF_DA['job_posted_date'].dt.strftime('%b')

# Define month order for proper sequencing
month_order = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 
               'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
DF_DA['job_posted_month'] = pd.Categorical(
    DF_DA['job_posted_month'], 
    categories=month_order, 
    ordered=True
)

# Explode skills column and identify top 5 in-demand skills
df_exploded = DF_DA.explode('job_skills')
top_5_skills = df_exploded['job_skills'].value_counts().head(5).index.tolist()

# Filter to top 5 skills only
df_top_5 = df_exploded[df_exploded['job_skills'].isin(top_5_skills)]

# Group by skill and month to count postings
skills_monthly = df_top_5.groupby(['job_posted_month', 'job_skills']).size().reset_index(name='count')

# Pivot to create month × skills matrix
pivot_data = skills_monthly.pivot_table(
    index='job_posted_month',
    columns='job_skills',
    values='count'
)

# Plot trend lines for each skill
plt.figure(figsize=(12, 6))
for skill in top_5_skills:
    plt.plot(pivot_data.index, pivot_data[skill], marker='o', linewidth=2, label=skill)

plt.xlabel('Month', fontsize=12)
plt.ylabel('Job Postings Count', fontsize=12)
plt.title('Data Analyst Skills Demand Trends (2024)', fontsize=14, fontweight='bold')
plt.legend(title='Job Skills', loc='best')
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```