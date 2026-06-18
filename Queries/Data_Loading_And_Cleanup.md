{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "\n",
    "\n",
    "# Filter for Data Analyst positions only\n",
    "DF_DA = df[df['job_title_short'] == 'Data Analyst'].copy()\n",
    "\n",
    "# Extract month from job posting date\n",
    "DF_DA['job_posted_month'] = DF_DA['job_posted_date'].dt.strftime('%b')\n",
    "\n",
    "# Define month order for proper sequencing\n",
    "month_order = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', \n",
    "               'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']\n",
    "DF_DA['job_posted_month'] = pd.Categorical(\n",
    "    DF_DA['job_posted_month'], \n",
    "    categories=month_order, \n",
    "    ordered=True\n",
    ")\n",
    "\n",
    "# Explode skills column and identify top 5 in-demand skills\n",
    "df_exploded = DF_DA.explode('job_skills')\n",
    "top_5_skills = df_exploded['job_skills'].value_counts().head(5).index.tolist()\n",
    "\n",
    "# Filter to top 5 skills only\n",
    "df_top_5 = df_exploded[df_exploded['job_skills'].isin(top_5_skills)]\n",
    "\n",
    "# Group by skill and month to count postings\n",
    "skills_monthly = df_top_5.groupby(['job_posted_month', 'job_skills']).size().reset_index(name='count')\n",
    "\n",
    "# Pivot to create month × skills matrix\n",
    "pivot_data = skills_monthly.pivot_table(\n",
    "    index='job_posted_month',\n",
    "    columns='job_skills',\n",
    "    values='count'\n",
    ")\n",
    "\n",
    "# Plot trend lines for each skill\n",
    "plt.figure(figsize=(12, 6))\n",
    "for skill in top_5_skills:\n",
    "    plt.plot(pivot_data.index, pivot_data[skill], marker='o', linewidth=2, label=skill)\n",
    "\n",
    "plt.xlabel('Month', fontsize=12)\n",
    "plt.ylabel('Job Postings Count', fontsize=12)\n",
    "plt.title('Data Analyst Skills Demand Trends (2024)', fontsize=14, fontweight='bold')\n",
    "plt.legend(title='Job Skills', loc='best')\n",
    "plt.grid(True, alpha=0.3)\n",
    "plt.tight_layout()\n",
    "plt.show()\n",
    "\n"
   ]
  }
 ],
 "metadata": {
  "language_info": {
   "name": "python"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
