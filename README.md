# Power BI Sales Dashboard

## 📊 Dashboard Preview
Overview
<img width="773" height="435" alt="image" src="https://github.com/user-attachments/assets/97ad6bb0-e483-416f-9365-232a4805620f" />
Product
<img width="677" height="383" alt="image" src="https://github.com/user-attachments/assets/892faf02-bb5a-41c0-9182-3f636a3f593c" />
Seller
<img width="680" height="386" alt="image" src="https://github.com/user-attachments/assets/0502e871-c609-425e-b847-fac48bb145a4" />

## 📌 Project Overview
This project focuses on building a tabular semantic model using the AdventureWorks dataset, available through a Lakehouse in Microsoft Fabric.
The goal is to analyze sales performance and support decision-making by developing a structured and optimized data model. The solution includes data preparation, modeling, and the creation of key business metrics using DAX to track sales KPIs and compare performance across different dimensions.
To improve usability and performance, advanced features such as perspectives, partitions, and role-based security were implemented.
A Power BI report was also developed on top of the semantic model, providing an interactive dashboard to explore sales insights and key performance indicators.

## Data Model
The semantic model was built in Visual Studio using the Tabular model (SQL Server Analysis Services extension), connected to a Lakehouse in Microsoft Fabric via Azure SQL connection.

### 🔗 Data Modeling & Relationships

- Relationships were created between fact and dimension tables to enable a consistent analytical model  
- Data types were adjusted where necessary to ensure compatibility between related columns  
- Selected relationships were configured as bidirectional to support more flexible filtering across SalesTerritory and Geography  

A dedicated Date table was defined and configured as the model's date table, enabling proper use of time intelligence functions.

### 🧩 Model Optimization & Usability

To improve usability and performance:

- Hierarchies were created to support drill-down analysis:
  - Date: Year → Quarter → Month  
  - Product: Category → Subcategory → Product  
  - Geography: Country → State → City  
  - Sales Territory: Group → Country → Region  

- Unnecessary columns and tables were hidden to simplify the user experience  
- Calculated columns were added to improve readability (e.g., short month and weekday names)  
- A concatenated column was created for salesperson names  

### 📈 Measures & KPIs (DAX)

A set of DAX measures was developed to analyze sales performance:

- **Sales, Cost, Profit, and Profit Margin (%)**
- **Number of Orders and Distinct Products**
- **Year-to-Date (YTD) metrics** based on both order and shipping dates  
- **Average shipping time (days)**  

To support performance tracking:

- A **Quota measure** was created to distribute quarterly targets into monthly values  
- **Variance and Variance %** were calculated to compare actual sales vs targets  

### ⏳ Time Intelligence

A calculation group was implemented to enable dynamic time-based analysis across all measures, including:

- MTD (Month-to-Date)  
- QTD (Quarter-to-Date)  
- YTD (Year-to-Date)  
- Previous Year (PY)  
- Year-over-Year growth (%)  

This approach allows flexible analysis without the need to create multiple versions of each measure.

### 🔐 Security & Performance

- Role-based security was implemented to control data access  
- Partitions were used to improve model performance  
- Perspectives were created to provide simplified views for different users

## 📈 Key Insights

- **Strong sales growth over time**  
  Sales show a clear upward trend across the years, indicating consistent business growth.

- **Performance below targets**  
  Despite high total sales (~80M), the business is underperforming against targets, with a negative variance of around -15%.

- **Low profit margin**  
  Profit margin is relatively low (~0.5–0.6%), suggesting tight margins and potential inefficiencies in cost management.

- **Top-performing category: Bikes**  
  Bikes generate the highest sales volume but still fall short of targets, indicating missed revenue potential.

- **High variance across product categories**  
  Most categories show significant negative variance, especially Accessories and Clothing, highlighting areas for improvement.

- **Regional performance differences**  
  Europe is the top-performing region in terms of sales, followed by North America, while other regions contribute significantly less.

- **Sales driven by specific reseller types**  
  Warehouse resellers generate the highest number of orders, making them key contributors to overall sales.

- **Shipping performance is stable**  
  Average order-to-shipping time remains consistent (~7 days), indicating stable operational efficiency.

- **Product-level variability**  
  The product analysis shows a wide dispersion between order volume and profitability, suggesting opportunities to optimize the product mix.

## 🛠️ Tools Used
- SQL Server Analysis Services - Tabular Mode
- Microsoft Fabric
- DAX
- Power BI
