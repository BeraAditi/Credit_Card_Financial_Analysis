# Credit_Card_Financial_Analysis
CREDIT CARD WEEKLY STATUS REPORT
CONTENT:
1. Project objective
 2. Data from POWER BI
3. Data processing & DAX
 4. Dashboard & insights 
5. Export & share project
Project Objective: 
 To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.
Import Data to POWER BI Database:
1.	Prepare csv file
2.	Import csv file in Power BI
DAX Queries
AgeGroup = SWITCH(
    TRUE(),
    customer[Customer_Age] < 30,"20-30",
    customer[Customer_Age] > 30 && customer[Customer_Age] < 40,"30-40",
    customer[Customer_Age] > 40 && customer[Customer_Age] < 50,"40-50",
    customer[Customer_Age] > 50 && customer[Customer_Age] < 60,"50-60",
    customer[Customer_Age] >= 60, "60+"
    )

IncomeGroup = SWITCH(
    TRUE(),
    customer[Income] < 35000,"Low",
    customer[Income] >= 35000 && customer[Income] < 70000,"Med",
    customer[Income] >= 70000, "High"
    )

Week_num2 = WEEKNUM(credit_card[Week_Start_Date])

Revenue = credit_card[Annual_Fees]+ credit_card[Interest_Earned]+ credit_card[Total_Trans_Amt]

DAX Queries

Current_week_revenue = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_Num] = MAX(credit_card[Week_num2])))

Previous_Week_revenue = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_Num] = MAX(credit_card[Week_num2])-1))


Project Insights- 

• Overall revenue is 55M 
• Total interest is 8M 
• Total transaction amount is 45M
• Male customers are contributing more in revenue 30M, female 25M 
• Blue & Silver credit card are contributing to 93% of overall transactions 
• TX, NY & CA is contributing to 68% 
• Overall Activation rate is 57.5% 
• Overall Delinquent rate is 6.06%
