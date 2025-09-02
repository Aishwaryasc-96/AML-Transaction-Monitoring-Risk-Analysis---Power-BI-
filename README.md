
# AML Transaction Monitoring & Risk Analysis


## Project Overview
Financial institutions must comply with Anti-Money Laundering (AML) regulations to prevent illicit activities such as money laundering, terrorist financing, and fraud. Detecting suspicious transactions early is critical to avoid regulatory penalties and reputational damage.

This project simulates a real-world AML compliance workflow — from gathering customer and transaction data, detecting suspicious patterns, categorizing risk levels, and producing a compliance-ready dashboard for monitoring.

Objective: Build a data analytics solution that helps AML teams identify high-risk customers, monitor unusual transaction activity, and prioritize investigations.
## Tools & Technologies
•	Power BI – Data visualization & dashboarding

•	Power Query – Data cleaning & transformation

•	Data Modeling – Star schema (Customers ↔ Transactions ↔ SAR Filings)

•	DAX – Custom measures & KPIs

•	Excel – Source data

## Features & What’s Included
•	KPI Cards: Total Transactions, Total Customers, Total Amount, SAR Filed, Laundering Cases

•	Slicers: Transaction Date, Country, Risk Category, Customer Segment, Channel

•	Visuals on the page:

    Map: Top 10 Countries by High-Risk Customer Transactions
    Line Chart: Trend of Transaction Amount by Risk Category
    Donut Chart: Transactions by Risk Category (High / Medium / Low)
    Bar chart: Transaction Distribution by Type & Risk Category (Card, Cash Deposit, Cheque, Crypto, Wire)
    Table: Suspicious Transactions (Txn ID, Customer ID, Date, Risk Category, Channel, Amount)
    Column Chart: Channel-wise Distribution of Transaction Value (Online, Mobile, ATM, Branch)

## DAX Highlights

    Total Transactions = COUNTROWS(Transactions)

    Total Customers = DISTINCTCOUNT(Customers[CustomerID])

    Total Amount = SUM(Transactions[Amount])

    SAR Filed = 
    CALCULATE(COUNTROWS('SAR Filings'),
    'SAR Filings'[SARFilingStatus] = "Filed")

    Laundering Cases = 
    CALCULATE(COUNTROWS(Transactions),
    Transactions[IsLaundering] = 1)

    HighRisk_Customers = 
    CALCULATE(DISTINCTCOUNT(Transactions [CustomerID]),
    Transactions[RiskCategory] = "High Risk")

    Total Transactions % = DIVIDE(COUNTROWS(Transactions),
    CALCULATE(COUNTROWS(Transactions), ALL(Transactions)),
    0)

    Transaction Date (dd mmm yyyy) =
    FORMAT(Transactions[TransactionDate], "DD MMM YYYY")

## Insights & Outcomes (from the dashboard)
•	Online contributes the largest share of transaction value, followed by Mobile; Branch is minimal — focus monitoring on digital channels.

•	Risk mix shows Low Risk ~44%, Medium ~34%, High ~22% (values change with slicers) — overall risk is concentrated but stable.

•	High-risk hotspots visible on the map include Cayman Islands, Singapore, UAE, and India.

•	Transaction types like Crypto & Wire Transfers show a higher share of high-risk segments compared to Cheque/Card.

•	The trend line indicates declining high-risk amounts YoY, suggesting improved controls or shifts in behavior.
