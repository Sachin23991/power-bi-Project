# UPI Transaction Analytics Dashboard – Power BI

This project is an interactive **Power BI** dashboard built to analyze UPI (Unified Payments Interface) transaction data across India, with a focus on digital payment behavior, system performance, and fraud monitoring. It converts raw transactional data into clear, visual, and actionable insights for stakeholders such as banks, analysts, and decision-makers.

## Project Overview

With the rapid growth of digital payments in India, UPI has emerged as a dominant platform for real-time transactions, generating large volumes of data that require systematic analysis. This project uses Power BI to design a multi-page UPI Transaction Dashboard that helps users explore trends by time, region, bank, device, transaction type, and status (success/failure and fraud).

Key capabilities:
- Monitor overall UPI transaction volume and value
- Analyze temporal trends and peak usage periods
- Compare bank-wise and transaction-type-wise performance
- Understand regional behavior (North vs South, state-wise distribution)
- Track success, failure, and fraud patterns to support reliability and risk management

---

## Dataset

The dashboard is built on a structured UPI transaction dataset that captures detailed digital payment activities across different users, banks, regions, and time periods.

### Dataset Fields

Major columns used in the model include:
- **Transaction details**
  - Transaction_ID
  - Transaction_Date
  - Transaction_Time
- **User & bank information**
  - Sender_Bank
  - Receiver_Bank
  - Sender_State / Receiver_State (where applicable)
  - Region (North, South, etc.)
- **Payment attributes**
  - Transaction_Type (P2P, P2M, Bill Payment, Recharge)
  - Payment_Mode / Channel
  - Device_Type (Android, iOS, Web)
- **Financial & status metrics**
  - Transaction_Amount
  - Transaction_Status (Success / Failed)
  - Fraud_Flag
  - Merchant_Category (Shopping, Utilities, Grocery, Fuel, Education, Food, Entertainment, Healthcare, Transport, etc.)

### Data Source

- **Public dataset:** UPI Transactions 2024 Dataset on Kaggle
  - Link: https://www.kaggle.com/datasets/skullagos5246/upi-transactions-2024-dataset

The dataset supports time-based analysis, bank-wise comparison, transaction-type breakdown, fraud analysis, and regional insights.

---

## Dashboard Architecture

The UPI Transaction Dashboard is organized into multiple pages, each built to answer specific analytical questions. The layout follows a top-level KPI section followed by detailed charts and interactive slicers to drill into the data.

### Pages Overview

- **Overview** – High-level summary and KPIs
- **Time-Based Analysis** – Temporal trends and patterns
- **Bank-Wise Performance** – Bank comparisons and rankings
- **Transaction Type Analysis** – Payment preference breakdown
- **Transaction Status Analysis** – Reliability and failure patterns
- **North Region Deep Dive** – State-wise and category insights (North)
- **South Region Deep Dive** – State-wise and category insights (South)

Each page uses combinations of cards, bar/column charts, line charts, donut/pie charts, treemaps, maps, waterfall charts, and slicers to create a comprehensive analytical experience.

---

## Dashboard Pages (Detailed)

### 1. Overview Page

The **Overview** page provides a high-level summary of digital transactions across India, allowing stakeholders to quickly understand overall volume, value, regional performance, transaction types, and merchant-wise spending.

**Key KPIs:**
- **Total Transactions**
  - Measure: `COUNT(Transaction_ID)`
  - Example value shown: 250K (illustrative)
  - Purpose: Indicates the total number of UPI/digital transactions in the selected period
- **Total Amount**
  - Measure: `SUM(Transaction_Amount)`
  - Example value shown: 328M
  - Purpose: Represents the total monetary value of transactions
- **Transaction Success Rate**
  - Measure: Successful_Transactions / Total_Transactions
- **Transaction Failure Rate**
  - Measure: Failed_Transactions / Total_Transactions

**Visuals & Insights:**
- **Total Amount by Region (Column Chart)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: Region (North, South)
  - Insight: Shows which region contributes more to total transaction value and helps compare regional economic activity.
- **Total Amount by Transaction Type (Donut Chart)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: Transaction_Type (P2P, P2M, Bill Payment, Recharge)
  - Insight: P2P and P2M dominate, while Recharge contributes relatively less, reflecting user payment behavior.
- **Total Amount by Merchant Category (Bar Chart)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: Merchant_Category (Shopping, Utilities, Grocery, Fuel, Education, Food, Entertainment, Healthcare, Transport)
  - Insight: Shopping and Utilities show the highest spend, while Healthcare and Transport are relatively lower, helping identify high-revenue segments.
- **State-wise Transaction Distribution (Map Visual)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimensions: State, Region
  - Insight: Displays geographic concentration of transaction value, color-coded by region, useful for regional targeting and policy analysis.

**Filters / Slicers:**
- Sender Bank (e.g., HDFC)
- Receiver Bank (e.g., ICICI)
- Device Type (Android, iOS, Web)

---

### 2. Time-Based Analysis Page

The **Time-Based Analysis** page focuses on transaction behavior across different time intervals, such as daily, monthly, and yearly patterns. It helps identify when users transact the most and how adoption grows over time.

**Key Elements:**
- Line and bar charts of transaction volume and value over time
- Detection of peak usage periods and seasonal variations in UPI usage
- Growth trends reflecting increasing adoption of digital payments

This page is essential for capacity planning, performance monitoring, and understanding periodic behavior in transactions.

---

### 3. Bank-Wise Performance Page

The **Bank-Wise Performance** page presents a comparative analysis of participating banks in the UPI ecosystem. It helps evaluate performance, contribution, and reliability at the bank level.

**Metrics & Visuals:**
- Bank-wise Transaction Volume (count of transactions per bank)
- Bank-wise Transaction Value (sum of amount per bank)
- Bank-wise Success and Failure Rates

This view highlights top-performing banks in terms of transaction volume/value and surfaces banks with higher failure rates, indicating potential operational or infrastructure issues.

---

### 4. Transaction Type Analysis Page

The **Transaction Type Analysis** page analyzes UPI usage across different payment categories, such as person-to-person and merchant payments. It focuses on how users utilize UPI across various scenarios.

**Key Insights:**
- Proportion of P2P vs P2M vs Bill Payment vs Recharge
- Transaction volume and value by type
- Dominant use cases for UPI in the dataset

This helps businesses and banks understand customer behavior and prioritize features or offers for high-usage categories.

---

### 5. Transaction Status Analysis Page

The **Transaction Status Analysis** page is dedicated to transaction reliability and completion behavior. It examines successful and failed transactions, along with failure patterns.

**Components:**
- Successful vs Failed Transactions (counts and percentages)
- Success and Failure Rates over time
- Time periods, transaction types, or banks where failures spike

This page is helpful for identifying potential system load issues, technical bottlenecks, or process gaps that impact transaction completion.

---

### 6. North Region Deep Dive

The **North Region** page offers a focused view of transaction behavior in northern states.

**Visuals & Interpretations:**
- **Total Amount by Sender State (Donut Chart)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: States such as Maharashtra, Uttar Pradesh, Delhi, Rajasthan, Gujarat
  - Insight: Shows state-wise contribution to overall transaction value, with certain states (e.g., Maharashtra) contributing the highest share.
- **Total Amount by Merchant Category (Waterfall Chart)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: Merchant_Category
  - Insight: Shows incremental contributions of each category (e.g., Shopping, Grocery, Utilities) to the total amount, helping understand value buildup.
- **Fraud Transactions by Merchant Category (Bar Chart)**
  - Measure: `COUNT(Fraud_Flag)`
  - Dimension: Merchant_Category
  - Insight: Highlights categories such as Entertainment and Shopping with higher fraud counts, while Grocery and Healthcare show relatively fewer frauds.

This page is valuable for both revenue optimization and fraud risk assessment in the North region.

---

### 7. South Region Deep Dive

The **South Region** page analyzes behavior and risk in southern states.

**Visuals & Interpretations:**
- **Hourly Behavior by Device Type (Line / Area Chart)**
  - Measure: `COUNT(Transaction_ID)`
  - Dimensions: Hour_of_Day, Device_Type (Android, iOS, Web)
  - Insight: Shows hourly activity patterns, with peak transaction activity between approximately 10 AM and 9 PM and Android dominating transaction volume, useful for capacity planning and peak-hour optimization.
- **Total Amount by Merchant Category (Treemap)**
  - Measure: `SUM(Transaction_Amount)`
  - Dimension: Merchant_Category
  - Insight: Shopping and Grocery contribute the highest transaction value, followed by Utilities and Education, while Healthcare and Entertainment contribute less.
- **Fraud Transactions by Merchant Category (Bar Chart)**
  - Measure: `COUNT(Fraud_Flag)`
  - Dimension: Merchant_Category
  - Insight: Shopping shows the highest fraud count, with Utilities and Fuel also showing noticeable fraud activity, while Education has relatively fewer fraud cases.

This view helps in profiling high-risk segments and understanding revenue drivers in South India.

---

## KPIs and Measures

The dashboard uses several calculated measures to quantify system performance and user behavior.

**Core KPIs:**
- **Total Transactions**
  - `Total Transactions = COUNT(Transaction_ID)`
- **Total Transaction Value**
  - `Total Transaction Value = SUM(Transaction_Amount)`
- **Average Transaction Amount**
  - `Average Transaction Amount = AVERAGE(Transaction_Amount)`
- **Successful Transactions**
  - Count of transactions with Transaction_Status = "Success"
- **Failed Transactions**
  - Count of transactions with Transaction_Status = "Failed"
- **Transaction Success Rate**
  - `Transaction Success Rate = Successful Transactions / Total Transactions`
- **Transaction Failure Rate**
  - `Transaction Failure Rate = Failed Transactions / Total Transactions`
- **Bank-wise Transaction Volume**
  - Transaction count per bank
- **Transaction Growth Trend**
  - Time-based measure evaluating changes in transaction volume over selected periods.

These measures power both high-level KPIs and detailed visuals, enabling rich monitoring and analysis.

---

## Insights & Findings

The analysis highlights several key patterns in digital payment behavior and system performance:
- Noticeable growth in UPI transaction volume and value indicates increasing adoption of digital payments over time.
- Time-based analysis reveals peak transaction periods and seasonal trends reflecting user behavior.
- Bank-wise comparisons show variability in transaction counts and success rates, identifying top-performing banks and those needing operational improvements.
- Status and fraud analysis uncover specific periods, types, or categories where failures or frauds are more frequent, suggesting potential system load, risk, or process issues.

These insights help in improving reliability, optimizing operations, and supporting strategic planning around digital payments.

---

## Future Enhancements

Potential future improvements to this project include:
- Integrating real-time UPI transaction streams for live monitoring
- Adding predictive models (e.g., forecasting transaction volume, fraud detection)
- Including deeper customer-level segmentation and behavior analysis
- Enhancing regional drill-downs (more granular state/city level)
- Integrating additional financial datasets for broader ecosystem analysis.

---

## How to Run the Project

1. **Clone the repository**
   ```bash
   git clone https://github.com/Sachin23991/power-bi-Project.git
   cd power-bi-Project
   ```

2. **Open the Power BI file**
   - Open `sachindashboard.pbix` in **Power BI Desktop**.

3. **Connect or refresh data**
   - Ensure the dataset is available locally or connected via the Kaggle link.
   - Update the data source path in Power BI if required.

4. **Explore the dashboard**
   - Use slicers (date, bank, region, device type, transaction type, status) to filter and analyze specific scenarios.
   - Navigate through Overview, Time, Bank, Type, Status, North, and South pages to derive insights.

Repository: https://github.com/Sachin23991/power-bi-Project

---

## Author

- **Name:** Sachin Yadav
- **Program:** B.Tech, Computer Science and Engineering – Lovely Professional University
- **LinkedIn:** https://www.linkedin.com/posts/sachin6_powerbi-dataanalytics-businessintelligence-activity-7405634258419179520-jfVa

---

## License

This project is open source and available for educational and analytical purposes.

---

**Last Updated:** January 2, 2026
