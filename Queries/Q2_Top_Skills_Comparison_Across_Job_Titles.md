### Top Skills Comparison Across Job Titles

```python
# Create a copy of the dataset
DF_SKILLS = df.copy()

# Explode skills column to create row per skill
DF_SKILLS = DF_SKILLS.explode('job_skills')

# Count skills by job title
skills_count = DF_SKILLS.groupby(['job_skills', 'job_title_short']).size()
df_skills_count = skills_count.reset_index(name='skill_count')

# Sort by skill count in descending order
df_skills_count.sort_values(by='skill_count', ascending=False, inplace=True)

# Define job titles to compare
job_titles = ['Data Analyst', 'Data Engineer', 'Data Scientist']

# Create subplots for each job title
fig, ax = plt.subplots(3, 1, figsize=(10, 10))

for i, job_title in enumerate(job_titles):
    # Filter top 5 skills for current job title
    df_plot = df_skills_count[df_skills_count['job_title_short'] == job_title].head(5)
    
    # Create horizontal bar chart
    df_plot.plot(kind='barh', x='job_skills', y='skill_count', ax=ax[i], title=job_title, legend=False)
    
    # Invert y-axis to show highest demand at top
    ax[i].invert_yaxis()
    
    # Set consistent x-axis limits
    ax[i].set_xlim(0, 120_000)
    ax[i].set_xlabel('Skill Count')

# Add overall title
fig.suptitle('Top 5 Skills by Job Title', fontsize=15, fontweight='bold')
fig.tight_layout()
plt.show()
```