# Plant Performance Dashboard

## Overview
This documentation provides a detailed description of the data integration process, calculations, key insights, and recommendations derived from the Plant Performance Dashboard created for MAS plants for the year 2023. The dashboard consists of two pages: the first page focuses on KPIs and bar charts, while the second page includes Earning per Hour (EPH), Cost per Hour (CPH), and EPH forecast. The dashboard allows the user to filter data by year, month, Division and plant. additionally, a scatter plot analysis identifies profit and loss based on EPH and CPH.

![image](https://github.com/user-attachments/assets/de278a21-1827-4a7b-83e4-0f1d1ac1ba67)
![image](https://github.com/user-attachments/assets/aa733c99-97a4-4517-a2fa-818f2397c9df)


## Data Integration Process
### Step 1: Importing Datasets
1.	Capacity Status 2023:
o	Imported fields: Division, Plant, Month, Product Type, Budget Hours, Actual Hours.
2.	Plant wise KPIs 2023:
o	Imported fields: Division, Plant, Month, KPI, Budget Value, Actual Value.
3.	Plant wise Financials 2023:
o	Imported fields: Division, Plant, Month, Budget Financials, Actual Financials.
### Step 2: Data Cleaning and Transformation
1.	Consistency Check:
o	Ensured that fields like Division, Plant, and Month have consistent naming conventions across all datasets.
2.	Data Transformation:
o	Merged datasets based on Plant Financials table (Division, Plant, KPI) to create a unified data model.
3.	Relationship 
create new Master tables(Date,Division,Plant) and make relationship .
 ![image](https://github.com/user-attachments/assets/2eda5af9-26bd-4683-80d9-12897b513b52)


## Calculations and Insights
Calculated Measures
### 1.	Cost per Hour (CPH):
DAX
Cost per Hour (Manufacturing) = CALCULATE( DIVIDE(SUM('Plant Financials 2023'[KPI Actual]), SUM('Plant Capacity Status 2023'[Actual Hours])),FILTER('Plant Financials 2023','Plant Financials 2023'[KPIs Name]="Manufacturing OH ($)"))


### 2.	Earning per Hour (EPH):
DAX
Earning per Hour = CALCULATE( DIVIDE(SUM('Plant Financials 2023'[KPI Actual]), SUM('Plant Capacity Status 2023'[Actual Hours])),FILTER('Plant Financials 2023','Plant Financials 2023'[KPIs Name]="Earnings ($)"))


## EPH Analysis
##### 1.	EPH Forecast:
o	Utilized historical EPH data to forecast future.
o	Forecasted values are visualized to identify potential future performance trends.
##### 2.	scatter plot -identify loss or a profit plants or divisions
A scatter plot has been created to show the relationship between Actual Earning and Earning per Hour (EPH). The main goal is to identify whether each plant is operating at a loss or a profit.

### Dashboard Description
o	The dashboard allows the user to filter data by year, month, Division and plant.
 ![image](https://github.com/user-attachments/assets/771998af-054b-4cd0-8dc9-cf65c2d4f636)


#### Page 1: KPIs and Bar Chart
##### 1.	KPIs:
o	Displayed key KPIs such as PTP %, LTO %, Factory FTT %, Efficiency %, Absenteeism %, OTD %, DIFOT, and OFF %.
o	Used cards and KPI visualizations for a clear and concise view of performance metrics.
 ![image](https://github.com/user-attachments/assets/c260bf73-82a4-4030-a1ad-84075d68acba)

#### 2.	Bar Chart and Line Chart:
o	Compared Budget vs. Actual Hours and Financials for each plant.
o	Highlighted underperforming areas with conditional formatting.
 ![image](https://github.com/user-attachments/assets/1aba5156-6475-45f5-b675-ca07e6728d4d)


#### Page 2: EPH, CPH, and EPH Forecast
##### 1.	Earning per Hour (EPH), Cost per Hour (CPH):
![image](https://github.com/user-attachments/assets/70eff848-2206-4ed3-9dfe-8af3a4447d26)
 

##### 2.	Scatter plot:

![image](https://github.com/user-attachments/assets/623cb840-8fbf-41d2-aa16-389c3be1ea1c)

 .
A scatter plot with x-axis Actual Earning and y-axis representing EPH shows the relationship between Actual Earning and EPH .Each data point contains information about Plant ,division,earning, EPH, and CPH values.

Apply Colors: Use conditional formatting to color the points:
Red if EPH is less than CPH (losing).
Green if EPH is greater than or equal to CPH (earning).
![image](https://github.com/user-attachments/assets/1f864d10-d909-445d-9f44-dbda0efeb03b)

 
The scatter plot provides a clear visual representation of the relationship between Actual Earning and EPH. By using conditional formatting to distinguish between profit and loss, the plot makes it easy to identify which plants are operating efficiently and which are not. This visualization aids stakeholders in making data-driven decisions to improve plant performance.

##### 3.	EPH Forecast :
o	Showed the forecasted EPH values for future periods.
o	Used line charts to visualize the trend and potential future performance.
 ![image](https://github.com/user-attachments/assets/0b66b273-b1ae-4d41-b8fa-9cdce8ce4c2a)

## Key Insights
##### 1.	Monthly Performance:
o	Identified months with significant deviations between budget and actual performance.
o	Highlighted plants that consistently underperformed or overperformed.
##### 2.	KPI Impact Analysis:
o	Analyzed how different KPIs impact plant performance in terms of hours and financials.
o	Identified KPIs with the most significant impact on overall performance.
##### 3.	Cost and Earning Efficiency:
o	Evaluated the cost efficiency of each plant through CPH.
o	Assessed the earning efficiency using EPH and compared it with budgeted values.
##### 4.	Profit and Loss Identification:
o	The scatter plot analysis clearly identifies plants operating at a loss or profit, providing actionable insights for decision-making.
## Conclusion
The Plant Performance Dashboard for MAS plants in 2023 provides a comprehensive view of the plant's performance through detailed KPIs, financial analysis, and forecasts. The actionable insights and recommendations aim to drive performance improvement, enhance cost efficiency, and support future planning efforts.
Appendix
•	Data Sources: Details of the datasets used.
•	DAX Formulas: List of DAX formulas used for calculations.
•	Visualizations: Description of each visualization used in the dashboard.


