# Yuva Interns Task 1 – Logistics Data Analysis

## 📌 Project Overview

This project was completed as part of **Yuva Interns – Task 1** and focuses on analyzing e-commerce logistics and delivery performance using data science techniques.

The project uses the **Brazilian Olist E-Commerce dataset** to investigate delivery times, late deliveries, order processing, carrier handling, delivery-stage performance, and factors associated with overall delivery duration.

The objective is to transform raw e-commerce logistics data into meaningful business insights and recommendations that can support improved delivery efficiency and customer satisfaction.

---

## 🎯 Objectives

The main objectives of this project are:

* Analyze historical e-commerce delivery data.
* Clean and preprocess logistics-related data.
* Calculate important delivery performance KPIs.
* Analyze late deliveries and their severity.
* Identify monthly and yearly delivery trends.
* Analyze different stages of the delivery process.
* Identify potential logistics bottlenecks.
* Perform correlation analysis between delivery-related variables.
* Build a preliminary predictive model for delivery time.
* Provide data-driven business recommendations.

---

## 📊 Dataset

The project uses the **Brazilian Olist E-Commerce Dataset**, which contains information about orders and their delivery process.

Important fields used in the analysis include:

* Order ID
* Customer ID
* Order Status
* Order Purchase Timestamp
* Order Approval Timestamp
* Order Delivered Carrier Date
* Order Delivered Customer Date
* Estimated Delivery Date

Only successfully delivered orders were used for the main delivery-performance analysis.

### Dataset Size

**96,470 delivered orders** were analyzed.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Scikit-learn**
* **Google Colab**
* **GitHub**

---

## 🔄 Project Workflow

The project follows an end-to-end data science workflow:

```text
Data Collection
      ↓
Data Cleaning
      ↓
Data Preprocessing
      ↓
Feature Engineering
      ↓
Exploratory Data Analysis
      ↓
KPI Calculation
      ↓
Delivery Stage Analysis
      ↓
Correlation Analysis
      ↓
Predictive Modeling
      ↓
Model Evaluation
      ↓
Business Insights
      ↓
Recommendations
```

---

## 📈 Key Performance Indicators

The following logistics KPIs were calculated:

| KPI                             |     Result |
| ------------------------------- | ---------: |
| Delivered Orders                |     96,470 |
| Average Delivery Time           | 12.56 days |
| Delivered by Estimated Date     |     91.89% |
| Late Delivery Rate              |      8.11% |
| Late Orders                     |      7,826 |
| Average Delay Among Late Orders |  9.55 days |
| Severe Delays (>14 days)        |      1,555 |
| Deliveries Taking >30 Days      |      4,550 |

The **91.89%** figure represents orders delivered by their estimated delivery date, including orders delivered early.

---

## 🚚 Delivery Stage Analysis

The delivery process was divided into major stages.

| Delivery Stage      | Average Time |
| ------------------- | -----------: |
| Approval → Carrier  |    2.85 days |
| Carrier → Customer  |    9.36 days |
| Purchase → Customer |   12.62 days |

The **Carrier → Customer stage** was identified as the largest contributor to total delivery time.

This suggests that transportation and last-mile delivery operations should be a major focus for logistics improvement.

---

## ⚠️ Late Delivery Analysis

A total of **7,826 orders** were delivered late.

The average delay among late orders was **9.55 days**, while the maximum observed delay was approximately **188.98 days**.

Late orders were classified according to severity:

| Severity            | Orders | Percentage |
| ------------------- | -----: | ---------: |
| Minor (0–3 days)    |  2,662 |     34.01% |
| Moderate (3–7 days) |  1,819 |     23.24% |
| High (7–14 days)    |  1,790 |     22.87% |
| Severe (>14 days)   |  1,555 |     19.87% |

Approximately **20% of late orders experienced severe delays of more than 14 days**.

---

## 📅 Monthly and Yearly Analysis

Monthly analysis identified periods with higher delivery risk.

Among months with at least 500 orders:

* **March 2018** recorded the highest late-delivery rate at **21.36%**.
* **February 2018** recorded **15.99%**.
* **November 2017** recorded **14.31%**.

Yearly analysis showed:

| Year | Orders | Average Delivery Time | Late Delivery Rate |
| ---- | -----: | --------------------: | -----------------: |
| 2016 |    267 |            19.68 days |              1.50% |
| 2017 | 43,426 |            13.03 days |              6.63% |
| 2018 | 52,777 |            12.14 days |              9.37% |

The 2016 dataset contains relatively few orders and should therefore be interpreted cautiously.

An important finding is that average delivery time improved between 2017 and 2018, while the late-delivery rate increased.

---

## 🤖 Predictive Modeling

A **Linear Regression** model was developed to investigate whether selected operational variables could predict total delivery time.

### Features Used

* Approval time in hours
* Carrier handling time in days

### Target Variable

* Total delivery time in days

### Dataset Split

* Training records: **76,084**
* Testing records: **19,021**

### Model Performance

| Metric |    Result |
| ------ | --------: |
| MAE    | 5.77 days |
| RMSE   | 8.93 days |
| R²     |    0.1726 |

The model explains approximately **17.26% of the variation** in delivery time.

This indicates that additional factors are required to build a stronger predictive model.

---

## 🔍 Target Leakage Handling

An initial regression model produced an R² score of 1.0.

However, this result was identified as **target leakage** because the `carrier_to_customer_days` variable is directly related to the calculation of total delivery time.

Therefore, this variable was removed from the final predictive model.

This ensured that the final model represented a more realistic prediction scenario.

---

## 📌 Correlation Analysis

Important correlations identified were:

| Variable Relationship                     | Correlation |
| ----------------------------------------- | ----------: |
| Approval Time vs Total Delivery Time      |        0.10 |
| Carrier Handling vs Total Delivery Time   |        0.39 |
| Carrier → Customer vs Total Delivery Time |        0.93 |

The strong correlation of **0.93** between carrier-to-customer time and total delivery time highlights the importance of transportation and last-mile operations.

Correlation indicates association and does not establish causation.

---

## 💡 Key Business Insights

The analysis identified several important findings:

1. Most delivered orders reached customers by their estimated delivery dates.
2. **8.11% of delivered orders were late.**
3. Some late orders experienced extremely long delays.
4. Nearly **20% of late orders were severely delayed by more than 14 days**.
5. The carrier-to-customer stage is the largest contributor to total delivery time.
6. Delivery reliability worsened from 2017 to 2018 despite an improvement in average delivery duration.
7. Certain months experienced significantly higher late-delivery rates.
8. Carrier handling time has a stronger relationship with total delivery time than approval processing time.
9. The preliminary regression model demonstrates that additional logistics variables are required for better prediction.

---

## 💼 Business Recommendations

Based on the analysis, the following improvements are recommended:

### 1. Improve Last-Mile Delivery

Focus on route optimization, carrier allocation, local distribution, and reducing unnecessary delivery handoffs.

### 2. Monitor High-Risk Orders

Develop a system to identify orders with unusually long processing or transportation times.

### 3. Improve Carrier Performance Monitoring

Track carrier handling time and delivery performance regularly to identify underperforming routes or carriers.

### 4. Prepare for High-Risk Periods

Increase logistics capacity during periods that historically experience higher delivery delays.

### 5. Improve Order Processing

Investigate orders requiring more than 24 hours for approval and identify opportunities for process automation.

### 6. Develop Advanced Predictive Models

Future models can incorporate:

* Customer location
* Seller location
* Geographic distance
* Product category
* Freight value
* Carrier information
* Historical seller performance
* Seasonal demand
* Regional delivery performance

---

## 📁 Repository Contents

```text
yuva-interns-task-1-logistics-analysis/
│
├── README.md
├── Yuva_Interns_Task_1_Logistics_Analysis.ipynb
├── Yuva_Interns_Task_1_Report.docx
│
└── images/
    ├── delivery_performance.png
    ├── late_delivery_severity.png
    ├── monthly_late_delivery_rate.png
    └── yearly_late_delivery_rate.png
```

---

## 📓 Notebook

The Jupyter Notebook contains the complete Python implementation, including:

* Data preprocessing
* Date and time calculations
* KPI analysis
* Late-delivery analysis
* Monthly and yearly analysis
* Delivery-stage analysis
* Correlation analysis
* Linear Regression
* Model evaluation
* Business insights

---

## 📄 Project Report

The accompanying Word report provides a detailed explanation of the:

* Business scenario
* Problem statement
* Objectives
* Dataset
* Methodology
* KPIs
* Exploratory analysis
* Predictive modeling
* Findings
* Recommendations
* Expected business impact

---

## 🏆 Expected Business Impact

The proposed analytics approach can help e-commerce organizations:

* Reduce late deliveries
* Identify logistics bottlenecks
* Improve carrier management
* Improve last-mile efficiency
* Detect high-risk orders
* Improve logistics planning
* Increase customer satisfaction
* Support data-driven decision making

---

## 👩‍💻 Project Author

**Shamini S.**

B.Tech – Artificial Intelligence & Data Science

This project was developed as part of the **Yuva Interns Data Science / Analytics Internship – Task 1**.

---

## 📌 Conclusion

This project demonstrates how data science can be applied to real-world e-commerce logistics problems.

By combining data cleaning, KPI analysis, exploratory data analysis, correlation analysis, visualization, and predictive modeling, the project identifies key delivery bottlenecks and provides actionable recommendations.

The analysis indicates that **transportation and last-mile delivery are the most important areas for improving overall delivery performance**. Future work can incorporate additional geographic, product, seller, carrier, and seasonal variables to develop more accurate predictive models.
