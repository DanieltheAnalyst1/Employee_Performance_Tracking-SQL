# Employee Performance Tracking: SQL Project

### Overview  
This project aims to track employee performance over time, analyzing data to identify top performers and measure overall performance trends. The insights derived from this analysis can help HR teams make data-driven decisions regarding employee development, rewards, and organizational effectiveness.

### Business Purpose  
In today's competitive business landscape, tracking employee performance is essential for understanding talent distribution, recognizing top performers, and identifying areas for improvement. This SQL-based analysis transforms qualitative performance evaluations into quantifiable metrics, giving businesses an objective view of their workforce's productivity.

### Target Audience
- **Human Resources (HR)**: To monitor employee performance over time and recognize top contributors.
- **Management**: To inform decisions around promotions, salary increments, and performance improvement plans (PIPs).
- **Business Executives**: To understand overall organizational performance and implement company-wide strategies for talent management.

### My Contribution  
As a **Data Analyst**, I applied SQL queries to convert subjective performance ratings into measurable scores, uncovering insights that support more objective performance evaluations. This work helps businesses implement fairer, data-driven HR processes.

### Key SQL Code

#### Performance Score Mapping  
One of the main challenges in analyzing performance data is converting textual feedback into quantifiable metrics. This SQL snippet does just that:
```sql
SELECT 
    EmpID,
    Employee_Name,
    AVG(CASE 
            WHEN PerformanceScore = 'Exceeds' THEN 4
            WHEN PerformanceScore = 'Fully Meets' THEN 3
            WHEN PerformanceScore = 'Needs Improvement' THEN 2
            WHEN PerformanceScore = 'PIP' THEN 1
        END) AS avg_score,
    COUNT(LastPerformanceReview_Date) AS review_count
FROM 
    hrdataset_v14
GROUP BY 
    EmpID, Employee_Name
ORDER BY 
    avg_score DESC;
```
- **Objective**: Translate qualitative performance scores into numbers for better comparison.
- **Outcome**: Averages these scores for each employee to identify top performers, assisting HR in making data-backed decisions on promotions or employee development.

#### Top Performers Over Time  
Tracking performance trends over time allows organizations to recognize consistent top performers and those who may need additional support:
```sql
SELECT 
    EmpID, 
    Employee_Name,
    YEAR(STR_TO_DATE(LastPerformanceReview_Date, '%m/%d/%Y')) AS year, 
    AVG(CASE 
            WHEN PerformanceScore = 'Exceeds' THEN 4
            WHEN PerformanceScore = 'Fully Meets' THEN 3
            WHEN PerformanceScore = 'Needs Improvement' THEN 2
            WHEN PerformanceScore = 'PIP' THEN 1
        END) AS avg_score
FROM 
    hrdataset_v14
GROUP BY 
    EmpID, Employee_Name, year
ORDER BY 
    year, avg_score DESC;
```
- **Purpose**: Determine which employees consistently perform well, making it easier for HR to identify potential leaders.
- **Result**: A year-by-year performance view for employees, guiding HR in decisions regarding promotions and rewards.

### Why This Matters  
Employee performance is critical to a company's success. Organizations that can identify and reward top talent are better positioned to retain high-performing individuals and ensure company growth. This analysis helps organizations take a more quantitative approach to human resources, making performance reviews less biased and more aligned with company goals.

### Real-World Impact  
By quantifying performance data, this SQL analysis enables:
- **Objective Employee Evaluation**: Easily identify top performers and those who need improvement, creating a fairer work environment.
- **Informed Decision Making**: Managers can use this information to decide on promotions, salary increases, and performance improvement strategies.
- **Talent Retention**: By recognizing and rewarding high performers, businesses can reduce turnover and keep top talent.

### My Role in the Process  
As a **Data Analyst**, I designed the queries and processes to convert HR performance data into actionable insights. My work ensures that HR and management teams have the tools to evaluate employee performance objectively, aligning performance with business outcomes.

---
