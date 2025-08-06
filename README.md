# HR-Data
HR Data Analysis and Performance Report Generation
1. HR_Data_Analysis_(Cleaning).ipynb: This Google Colab Notebook documents the data cleaning process for an HR dataset obtained from Kaggle, detailing steps taken to preprocess and refine the data for analysis.
2. HR_Data_Analysis.ipynb: This Google Colab Notebook conducts comprehensive HR data analysis, likely including exploratory data analysis, visualization, and statistical analysis to derive insights and trends from the dataset.
3. HR_Performance_Analysis.ipynb: This Google Colab Notebook focuses specifically on analyzing HR performance metrics, likely examining factors such as employee productivity, retention rates, and other performance indicators to assess organizational effectiveness.
4. HR Data I.csv: This CSV file contains the original dataset obtained from Kaggle, likely comprising various HR-related variables such as employee demographics, job roles, and performance metrics.
5. HR Data II.csv: This CSV file contains the cleaned version of the HR dataset, likely processed and refined in the "HR_Data_Analysis_(Cleaning).ipynb" notebook to remove inconsistencies, missing values, or errors.
6. Performance Analysis Report: HR Data.pdf: This PDF report provides insights and findings from the performance analysis conducted on the HR dataset, likely summarizing key metrics, trends, and recommendations for improving organizational performance.

Human Resource Data Analysis Project
Dataset: Kaggle – Human Resources Data Set
Tools: Python, Pandas, NumPy, Matplotlib, Seaborn
Goal: To perform exploratory data analysis (EDA) on HR data to extract actionable insights related to employee attrition, performance, diversity, recruitment efficiency, and satisfaction.

🔍 1. Employee Attrition Analysis
Objective:
To analyze the reasons why employees leave the organization and visualize the frequency of each reason.

Approach:
Removed employees who are still employed ('N/A-StillEmployed' in TermReason).
Used a bar chart (via Seaborn countplot) to visualize the termination reasons.

Insight:
This chart identifies the top causes of employee attrition, allowing HR to investigate and address patterns like voluntary resignations, misconducts, layoffs, etc.

data = data[data['TermReason'] != 'N/A-Stillemployed']
sns.countplot(data=data, x='TermReason', order=data['TermReason'].value_counts().index)

💰 2. Salary Analysis by Department
Objective:
To examine the salary distribution across departments and identify any disparities or outliers.

Approach:
Used a boxplot grouped by Department.
Box plots show median, IQR, and outliers for salary per department.

Insight:
This helps detect salary inequality, high-paying departments, and if some roles are under- or over-compensated compared to others.
data.boxplot(column='Salary', by='Department')

📈 3. Engagement vs. Performance
Objective:
To explore if there is any correlation between employee engagement (survey results) and performance scores.

Approach:
Used a scatter plot to visualize the relationship between EngagementSurvey and PerfScoreID.

Insight:
This analysis helps assess whether engaged employees are also top performers, which can inform future engagement strategies.

plt.scatter(data['EngagementSurvey'], data['PerfScoreID'])

👫 4. Diversity and Inclusion – Gender Distribution
Objective:
To assess gender diversity in the workforce.

Approach:
Used a pie chart to visualize the distribution of the Sex column.

Insight:
Shows gender imbalance (if any), helping HR take action to improve diversity.
data['Sex'].value_counts().plot(kind='pie', autopct='%1.1f%%')

😊 5. Satisfaction and Absenteeism
Objective:
To analyze employee satisfaction levels in relation to absenteeism.

Approach:
Overlaid histograms of EmpSatisfaction and Absences.

Insight:
Lower satisfaction levels may correlate with higher absenteeism. This can help target wellness or engagement programs.

plt.hist(data['EmpSatisfaction'], bins=5, alpha=0.5)
plt.hist(data['Absences'], bins=10, alpha=0.5)

🎯 6. Recruitment Source Effectiveness
Objective:
To evaluate how different recruitment sources impact employee performance.

Approach:
Mapped textual performance scores to numeric values.

Grouped data by RecruitmentSource and plotted average PerformanceScore.

Insight:
Helps HR prioritize the most effective recruitment channels that bring in top performers.

score_mapping = {'Exceeds': 4, 'Fully Meets': 3, 'Needs Improvement': 2, 'PIP': 1}
data['PerformanceScore'] = data['PerformanceScore'].map(score_mapping)
data.groupby('RecruitmentSource')['PerformanceScore'].mean().plot(kind='bar')

👔 7. Manager Performance Overview
Objective:
To compare performance scores of employees under different managers.

Approach:
Used a boxplot of PerfScoreID grouped by ManagerName.

Insight:
Shows which managers consistently lead high-performing teams — a key factor for performance evaluations and mentorship opportunities.

data.boxplot(column='PerfScoreID', by='ManagerName')

📊 8. Special Projects vs. Performance
Objective:
To determine if involvement in special projects correlates with better performance.

Approach:
Used a violin plot to visualize distribution of PerfScoreID across SpecialProjectsCount.

Insight:
Higher project involvement may lead to better performance scores, or vice versa. Good for promoting high-potential employees.

sns.violinplot(x='SpecialProjectsCount', y='PerfScoreID', data=data)

💵 9. Salary Distribution
Objective:
To get a general sense of salary distribution.

Approach:
Used a simple histogram on the Salary column.

Insight:
Identifies common salary ranges, skewness, and potential outliers (e.g., underpaid or overpaid employees).

plt.hist(data['Salary'], bins=20)

💍 10. Marital Status Distribution
Objective:
To observe the distribution of employees by marital status.

Approach:
Used a bar chart of MaritalDesc value counts.

Insight:
Can be useful for internal HR campaigns like flexible scheduling, parental support, and benefits targeting.

data['MaritalDesc'].value_counts().plot(kind='bar')

📌 Overall Project Summary
This end-to-end HR data analysis project delved into several critical HR metrics and employee attributes to extract practical business insights. Through a variety of visualizations and exploratory analysis, we addressed:
Reasons behind employee attrition
Pay disparities across departments
The connection between engagement, performance, and absenteeism
Diversity metrics like gender and marital status
Managerial and recruitment source effectiveness
Employee satisfaction and special project participation
Business Impact:
This kind of analysis allows HR and leadership to:
Retain top talent
Address diversity and equity gaps
Improve recruitment strategies
Support data-informed managerial decisions
Promote employee engagement and development
