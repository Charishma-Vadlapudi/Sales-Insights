# Sales-Insights
##SQL STATEMENTS TO ANALYSE SALES OF A COMPANY AND PROVIDING INSIGHTS##
##Tables & Columns in our data-##
customers-{customer_code,custmer_name,customer_type},                                     date-{date,cy_date,year,month_name,date_yy_mm},markets-{markets_code,markets_name,zone},products-{product_code,product_type},transactions-{product_code,customer_code,market_code,order_date,sales_qty,sales_amount,currency,profit_margin_percentage,profit_margin,cost_price}
## DATA ANALYSIS USING SQL ##
**Show all customer records**:
SELECT * FROM customers;
**Show total number of customers**: 
SELECT COUNT(*) FROM customers;
**Show transactions for Chennai Market**:                                                                                 SELECT * FROM transactions join markets on market_code=markets_code WHERE markets_name='Chennai';
**Show distinct product codes sold in Chennai**:                                                                          SELECT DISTINCT COUNT(product_code) FROM transactions join markets on market_code=markets_code WHERE markets_name='Chennai'
**Show transactions where currency is US dollars**:
SELECT * FROM transactions WHERE currency='USD'
**Show transactions in 2020 join by date table**: 
SELECT * FROM transactions join date ON transactions.order_date=date.date;
**Show Total revenue in 2020**:
SELECT SUM(sales_amount) FROM transactions join date ON transactions.order_date=date.date WHERE year=2020
**Show total revenue in 2020 in the month of January**
SELECT SUM(sales_amount) FROM transactions join date ON transactions.order_date=date.date WHERE year=2020 and month_name='January';
**Show total revenue in 2020 in the month of January for Chennai region**:
SELECT SUM(sales_amount) FROM transactions join date ON transactions.order_date=date.date JOIN markets ON markets.markets_code=transactions.market_code WHERE year=2020 and month_name='January' and markets_name='Chennai';
**Show Top 5 Customers with highest contribtuion to Revenue**:
SELECT custmer_name,SUM(sales_amount) as revenue FROM transactions join customers ON transactions.customer_code=customers.customer_code group by custmer_name order by revenue desc LIMIT 5;
**Show Top 5 products selling**
SELECT product_code,SUM(sales_qty) as saleqty FROM transactions GROUP BY product_code order by saleqty desc LIMIT 5;
**Show Top 5 Customers in terms of profit contribution**
SELECT markets_name, (SUM(profit_margin)/SUM(sales_amount)) as profit_margin_percentage FROM transactions join markets on transactions.market_code=markets.markets_code group by markets_name order by profit_margin_percentage desc LIMIT 5;
