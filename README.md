# The Analysis

## 1. What are the most demamnd skills for the top 3 most popular data roles? 

To find the most demamnded skills for the 3 top most popular data roles. I filtered out those positionsby which one were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job tittles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_Skills_Count.ipynb](3_Project/2_Skills_Count.ipynb)

## Visualize Data

``` python
fig, ax = plt.subplots(len(job_titles), 1)


for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')

plt.show()
```

### Results

![Visialization of Top Skills Datata Analysts](3_Project/images/skill_demand_all_data_roles.png)
Bar graph visualizing the salary for the top 3 data roles and their top 5 skills associated with each.

### Insights
* SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the second most sought-after skill, appearing in 65% of job postings.
* Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
*Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).

## 2. How are in-demand skills trending for Data Analysts?

### Visualize Date

``` python

from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, legend='full', palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```

### Results

![Trending Top Skills for Data Analyst in the US](3_Project/images/skill_trend_DA.png)
*Bar Graph visualizing the trending top skills for data analysts in the US in 2023.*

### Insights:

* SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.

* Excel experienced a significant increase in demand starting around September, surpassing both Python and Tableau by the end of the year.

* Both Python and Tableau show relatively stable demand throughout the year with some fluctuations but remain essential skills for data analysts. Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.
