# Sales Overview Dashboard

## Snapshot of the Dashboard
  ![power bi project data to](https://github.com/user-attachments/assets/aa0d8843-ffe9-424b-91a2-05da59c19899)
## STEPS IN PROJECT

- Step 1 :  Requirement Gathering/ Business Requirements.

- Step 2 : Data Walkthrough

- Step 3 : Data Connection
 
- Step 4 : Data Cleaning / Quality Check 
- Step 5 : Data Modeling
 
- Step 6 : Data Processing
 
- Step 7 : DAX Calculations
  
- Step 8 : Dashboard Background
 
- Step 9 : Dashboard Lay outing
 
- Step 10 : Charts Development and Formatting
 
- Step 11 : Dashboard / Report Development

- Step 12 : Insights Generation
  
## BUSINESS REQUIREMENT
 
 Design a dynamic Power BI dashboard that tracks key metrics—Sales, Profit, and Quantity—across four regions: Central, East, South, and West. The dashboard should allow users to filter by year and dynamically switch between the three metrics (Sales, Profit, and Quantity). Additionally, it should include a comparison with the previous year's (PY) sales for the selected year.

### KPI’s Requirements
#### Central Region:

Display Sales, Profit, and Quantity as per the selected year filter.

Allow dynamic selection between Sales, Profit, and Quantity.

Show Sales for the previous year based on the selected year.

Create a bar sparkline for monthly data, including an average line for better trend analysis.

#### East Region:

Display Sales, Profit, and Quantity as per the selected year filter.

Allow dynamic selection between Sales, Profit, and Quantity.

Show Sales for the previous year based on the selected year.

Create a bar sparkline for monthly data, including an average line for better trend analysis.

#### South Region:

Display Sales, Profit, and Quantity as per the selected year filter.

Allow dynamic selection between Sales, Profit, and Quantity.

Show Sales for the previous year based on the selected year.

Create a bar sparkline for monthly data, including an average line for better trend analysis.
 
#### West Region:

Display Sales, Profit, and Quantity as per the selected year filter.

Allow dynamic selection between Sales, Profit, and Quantity.

Show Sales for the previous year based on the selected year.

Create a bar sparkline for monthly data, including an average line for better trend analysis.

### Chart’s Requirements

#### Sales by State:

Bubble Map: Display a bubble map to visualize sales distribution across different states. The size of each bubble should correspond to the sales volume, allowing users to quickly identify states with high or low sales.

Bar Chart: Place a bar chart alongside the bubble map to provide a detailed breakdown of sales by state. This chart should allow for easy comparison between states, with bars sorted either in ascending or descending order of sales.


Create a table/grid to display key metrics for both current and previous years. The table should include the following columns:


CY Sales: Current Year Sales

PY Sales: Previous Year Sales

YoY Sales: Year-over-Year Sales growth or decline

CY Profit: Current Year Profit

PY Profit: Previous Year Profit

YoY Profit: Year-over-Year Profit growth or decline

CY Qty: Current Year Quantity

PY Qty: Previous Year Quantity

YoY Qty: Year-over-Year Quantity growth or decline

 
 ### Following DAX expression was written 
 
    Total sales = SUM('Sales Data'[Sales]) 

    CY sales = 
    VAR selectedyear = SELECTEDVALUE('Calender table'[Year])
    VAR currentyearsales = CALCULATE([Total sales],'Calender table'[Year]=selectedyear)
    RETURN currentyearsales

    PY sales = 
    VAR selectedyear = SELECTEDVALUE('Calender table'[Year])
    VAR Previousyearsales = CALCULATE([Total sales],'Calender table'[Year]=selectedyear-1)
    RETURN Previousyearsales

    YoY sales = 
    VAR currentyearsales = [CY sales]
    VAR previousyearsales = [PY sales]
    VAR YoYchange = DIVIDE(currentyearsales - previousyearsales,previousyearsales)
    VAR print = 
    IF(YoYchange>0,UNICHAR(9650) & " " & FORMAT(YoYchange,"0%"),
    UNICHAR(9660) & " " & FORMAT(YoYchange,"0%"))
    RETURN print
    
