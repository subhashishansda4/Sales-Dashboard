## Problem Statement
"**AltiQ Technologies**" is a company which supplies hardware peripherals to different clients such as "Nomad Stores", "Excel Stores", "Surge Stores", "Electricalsara Stores". It's a hardware company which will supply computers, networking equipments and other peripherals to them.__
They have head office in Delhi, India__
And regional offices in different states of India__

**Bhavin Patel**, as the Sales Director working from the main office doesn't have a clear idea of what is happening at the ground level of this business. He has data from his regional offices but as a human, we are not so good at consuming numbers and excel sheets.

## What? Where? When?
* Top 5 customers by revenue and sales quantity
* Top 5 products by revenue number
* Revenue breakdown by cities
* Revenue breakdown by years and months
* Aggregate revenue in last year

## Solution
What AtliQ Technologies need are **Sales Insights** and a **Data Visualization Dashboard** taking in real time transactional data. That way the company can see insights from the data on the go and will help them make better business decisions.

## Process
#### AIMS' grid & Project Planning
1. Purpose__
    To unlock sales insights that are not visible before, for sales team & decision support. Also to automate them to reduce manual time spent in data gathering.
2. Stakeholders
    * Sales Director
    * Marketing Team
    * Customer Service Team
    * Data & Analytics Team
    * IT
3. End Result__
    An automated dashboard providing quick and latest sales insights in order to support data driven decision making.
4. Success Criteria
    * Dashboard covering sales order insights with latest data available
    * Sales team able to take better decisions and improve 10% of cost savings of total spend
    * Sales Analyst stop data gathering manually in order to save 20% of their business time and reinvest it

#### Pipeline
![Goku](https://www.google.com/url?sa=i&url=)

#### Data Analysis
* Show total number of transactions__
'''SELECT COUNT(*) FROM sales.transactions;'''

* Show sum of total transactions performed in Ahmedabad__
''''SELECT COUNT(*) FROM sales.transactions WHERE market_code = "Mark003";'''

* Show transactions with USD__
''''SELECT * from sales.transactions WHERE currency = "USD";'''

* Show total revenue in year 2020__
'''SELECT SUM(sales.transactions.sales_amount)
FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date = sales.date.date
WHERE sales.date.year = 2020;'''

* Show total revenue in Ahmedabad,2020__
'''SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date = sales.date.date
WHERE sales.date.year = 2020 AND sales.transactions.market_code = "Mark003";'''

* Show distinct products sold in Ahmedabad__
SELECT DISTINCT product_code FROM sales.transactions WHERE market_code = "Mark003";

#### Data Modelling
STAR SCHEMA:__
fact table - transactions__
dimensions table - customers, products, markets, date__
![Goku](https://www.google.com/url?sa=i&url=)

#### Data Cleaning
* markets_name with no zones__
    ''''SELECT * FROM sales.markets where sales.zone = "";'''
* transactions with null values in sales_amount__
    ''''SELECT * FROM sales.transactions WHERE sales_amount <= 0;'''
* normalizing currency by adding a column in Power BI (USD to INR)
* filtering out all duplicate transactions in Power BI
* filtering out product_code with no product_type__
    ''''SELECT * FROM sales.products WHERE product_type = "";'''
    
## Results
![Goku](https://www.google.com/url?sa=i&url=)

## Conclusion
"**AtliQ Technologies**" will now get a lot of transparency in the business. They will also get lots of insights from the dashboard which will help **Bhavin Patel** make a business decision.
Bhavin can also configure **Power BI** such that it sends him a daily or monthly report in PDF format which has different diagrams, charts and revenue trends for him to get an idea.
