# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](3_Project/2_Skill_Demand.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    
plt.show()
```

### Results

![Visualization of Top Skills for Data Nerds](3_Project/images/skill_demand_all_data_roles.png)

### Insights

- Python: Highly requested across all roles, with 72% for Data Scientist, 65% for Data Engineer, and 27% for Data Analyst. It's crucial for programming, data manipulation, and machine learning.

- SQL: Essential for all roles, with the highest demand for Data Engineer (68%), Data Scientist (51%), and Data Analyst (51%). Key for data querying and relational database management.

- Python and SQL are fundamental skills across all data roles.

- Data Analysts focus more on tools for data manipulation and visualization (Excel, Tableau).

- Data Engineers require cloud platform knowledge (AWS, Azure) and big data tools (Spark).

- Data Scientists need expertise in statistical analysis (R, SAS) and visualization tools (Tableau).

## 2. How are in-demand skills trending for Data Analysts?

To find how skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by the month of the job postings. This got me the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.

View my notebook with detailed steps here: [3_Skills_Trend.iypnb](3_Project/3_Skills_Trend.ipynb).

### Visualize Data

```python
from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:,:5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```

### Results

![Trending Top Skills for Data Analysts in the US](
3_Project/images/skill_trend_DA.png)

*Bar graph visualizing the trending top skills for Data Analysts in the US in 2023.*

### Insights

- SQL remains the most consistently demanded skill throughout the year, though it shows a gradual decline from January to November before a slight rebound in December.

- Excel shows a significant increase in demand starting around September, eventually surpassing Python and Tableau by the end of the year.

- Python and Tableau demonstrate relatively stable trends with minor fluctuations, highlighting their continued relevance for data analysts despite not being the top-most skills.

- SAS maintains the lowest demand throughout the year, showing only slight movement—suggesting it is increasingly niche or industry-specific.