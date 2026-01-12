## Freelance Job Market Annual Openings (BLS) Analysis
This is an analysis of the top freelance job market annual job openings according to BLS (Bureau of Labor Statistics).

Annual openings refer to the total number of job vacancies expected each year in a specific occupation or across the economy, calculated by combining new job creation (growth) and replacement needs (workers leaving for other jobs or retiring).

## Objective
The main objective on taking on this project was:

To analyze and compare annual freelance job openings across different roles, providing insight into demand concentration and market opportunities within the freelance economy.


## Dataset
Source: [Top Freelance Job Roles and Demand Statistics](https://www.kaggle.com/datasets/hammadfarooq470/top-freelance-job-roles-and-demand-statistics)

Record: 25 rows

File type: CSV

## Methdology & Tools
- Programming Language: Python
- Key Libraries:
    - Pandas
    - Matplotlib
    - Seaborn
- Jupyter Notebook: Important for executing python scripts.
- Git & Github: Essential for version control and project tracking.

## Data Preparation & Cleanup
```
# import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.ticker import FuncFormatter
import seaborn as sns

# load the dataset
df = pd.read_csv("top-freelance-job-roles-and-demand-statistics/freelance_jobs_2025.csv")

# clean the 'Annual openings (BLS)' column
df['Annual openings (BLS)'] = df['Annual openings (BLS)'].str.replace(',', '').astype(int)
```
## Sort & Select Top 10 Roles
```
df.sort_values(by='Annual openings (BLS)', ascending=False, inplace=True)
df_top10 = df.head(10)
```
## Top 10 Freelance jobs by Annual Openings (BLS) Barplot
```
sns.barplot(data=df_top10, y='Job title', x='Annual openings (BLS)',hue='Annual openings (BLS)', palette="flare", legend=False)
plt.title("Top 10 Freelance Job Roles by Annual Openings (BLS)")
plt.xlabel("Annual Openings (BLS)")
plt.ylabel("Job Title")


def xticks_format(x, pos):
    """Format x-axis ticks to show in K (thousands) and M (millions)."""
    if x >= 1_000_000:
        return f'{x/1_000_000:.1f}M'
    elif x >= 1_000:
        return f'{x/1_000:.0f}K'
    else:
        return str(int(x))
    
ticks_x  =  plt.FuncFormatter(xticks_format) # Create the formatter

plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```
![Barplot](images\output.png)

## Insights drawn
1. Virtual assistants account for the highest number of annual freelance openings by a significant margin. This highlights the growing reliance of businesses on remote administrative support, particularly among startups, small businesses, and solo entrepreneurs seeking cost-effective operational assistance.

2. Blockchain developers and mobile app developers rank among the top roles, reflecting sustained demand for advanced technical skills. Although these roles have fewer openings than virtual assistants, they likely command higher compensation due to their specialized nature and higher skill barriers.

3. Accountants, business consultants, and project managers continue to see substantial demand. This suggests that organizations increasingly outsource strategic planning, financial management, and execution oversight rather than hiring full-time staff.

4. SEO specialists, media buyers, and digital marketing consultants show comparatively lower openings. This may indicate market saturation or a tendency for companies to require fewer marketing freelancers relative to administrative or development roles.

5. The sharp decline in openings after the top roles suggests a concentration of freelance opportunities in specific job categories. This indicates a competitive landscape where freelancers in high-demand roles benefit from more consistent opportunities.

## Summary

The freelance job market strongly favors remote support and technical development roles, while maintaining steady demand for business and marketing expertise. Freelancers face a trade-off between roles with high opportunity volume but lower barriers to entry and roles with lower volume but higher earning potential due to specialized skills.
