
# **HR Analytics Project**  

![Dashboard Preview](ER1.jpg)  
*Dynamic Power BI Dashboard*  

---

## **Overview**  
The HR Analytics Project focuses on processing HR data to generate actionable insights. The project covers data cleaning, SQL database integration, and dynamic visualization using Power BI. The dashboard updates automatically, ensuring real-time insights for effective decision-making.

---

## **Features**  
- **Dynamic Power BI Dashboard:** Automatically updated to reflect real-time SQL database changes.  
- **Key Insights:**
  - Attrition by Education, Age, Salary, and Job Role.  
  - Employee satisfaction trends over time.  
  - Department-wise performance and demographics.  
- **SQL Integration:** Seamless data storage and processing with MySQL.  
- **Python Automation:** Automates data cleaning and SQL integration tasks.  

---

## **Tech Stack**  
- **Languages & Tools:** Jupyter Notebook, Python, Power BI.  
- **Database:** MySQL.  
- **Libraries:** `pandas`, `sqlalchemy`, `datetime`.  

---

## **Setup Guide**  

### **Step 1: Dataset Preparation**  
1. **Connect to Google Drive:** Use Python to programmatically access the dataset.  
   ```python
   url1 = "https://drive.google.com/file/d/1ehMkFolQmCyCRO73LoWM78c4uVzj_VnI/view?usp=drive_link"
   url1 = 'https://drive.google.com/uc?id=' + url1.split('/')[-2]
   SatisfiedLevel = pd.read_csv(url1)
   ```  
2. **Data Cleaning:** Handle missing values, normalize fields, and prepare the dataset for analysis.  

### **Step 2: MySQL Database Integration**  
1. **Install MySQL Driver:**  
   ```bash
   pip install pymysql
   ```  
2. **Create SQL Connection in Python:**  
   ```python
   from sqlalchemy import create_engine
   engine = create_engine("mysql+pymysql://root:Mysql#1@127.0.0.1:3306/electric")
   conn = engine.connect()
   ```  
3. **Load Cleaned Data into MySQL:**  
   ```python
   data1 = pd.read_csv('PerformanceRating.csv')
   data1.to_sql('PerformanceRating', engine, index=False, if_exists='replace')
   conn.close()
   ```  

### **Step 3: Power BI Integration**  
1. **Connect to MySQL Database:** Configure Power BI to fetch data from the SQL database.  
2. **Design the Dashboard:** Build visualizations to showcase KPIs like:  
   - Attrition rates.  
   - Employee satisfaction trends.  
   - Demographic analysis.  

### **Step 4: DimDate Table Creation**  
Generate a `DimDate` table to manage time-series data:  
```python
from datetime import datetime, timedelta
dates = pd.date_range(start="2000-01-01", end="2023-12-31", freq='D')
# ... Add required time columns ...
df.to_sql('DimDate', conn, index=False, if_exists='replace')
```  

---

## **Key Visualizations**  

1. **Home Dashboard**  
   - Total Employees: **1,470**  
   - Attrition Rate: **16.1%**  
   - Gender Ratio: **Male (651) | Female (675)**  

![Dashboard Preview](ER2.jpg)  

2. **Attrition Summary**  
   - Attrition by Education, Salary, and Job Role.  
   - Trends in employee attrition over the years.  

3. **Employee Summary**  
   - Job satisfaction levels by department.  
   - Monthly performance trends.  

---

## **Usage**  
Run the project through Power BI to explore interactive dashboards and real-time analytics.  

---

## **Contributors**  
- **Ankit Kumar (Team Lead)**  
- **Varad Pemare**  
- **Anurag Chakrabarty**  

---

## **License**  
This project is licensed under the MIT License.  

---
