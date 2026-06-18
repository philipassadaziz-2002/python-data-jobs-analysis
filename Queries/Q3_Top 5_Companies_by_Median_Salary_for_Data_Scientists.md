### Top 5 Companies by Median Salary for Data Scientists (US)

```python
# Filter for Data Scientists in United States with available salary data
df_DA_US = df[(df['job_title_short'] == 'Data Scientist') & 
              (df['job_country'] == 'United States')].copy()

# Remove rows with missing salary information
df_DA_US = df_DA_US.dropna(subset=['salary_year_avg'])

# Calculate median salary by company and get top 5
top5_companies = df_DA_US.groupby('company_name')['salary_year_avg'].median().nlargest(5).reset_index()

# Create interactive horizontal bar chart using Plotly
fig = px.bar(
    top5_companies,
    x='salary_year_avg',
    y='company_name',
    orientation='h',
    title='Top 5 Companies by Median Salary',
    color_continuous_scale='Viridis',  # Color palette based on salary value
    color='salary_year_avg',  # Color bars by salary amount
    text_auto=True,  # Display values on bars
    width=800,  # Chart width
)

# Customize layout
fig.update_layout(
    xaxis_tickformat='$,.0f',  # Format x-axis as currency (USD)
    yaxis_title='',  # Remove y-axis title
    xaxis_title='Median Salary (USD)',  # Set x-axis label
    title_font_size=16,  # Increase title font size
    plot_bgcolor='white'  # Set background to white
)

fig.show()
```