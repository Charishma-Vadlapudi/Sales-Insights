# Sales-Insights
**SQL STATEMENTS TO ANALYSE SALES OF A COMPANY AND PROVIDING INSIGHTS**
**Tables & Columns in our data-** customers-{customer_code,custmer_name,customer_type},                                     date-{date,cy_date,year,month_name,date_yy_mm},markets-{markets_code,markets_name,zone},products-{product_code,product_type},transactions-{product_code,customer_code,market_code,order_date,sales_qty,sales_amount,currency,profit_margin_percentage,profit_margin,cost_price}
## DATA ANALYSIS USING SQL ##
**Show all customer records**: SELECT * FROM customers;
**Show total number of customers**: SELECT COUNT(*) FROM customers;
**Show transactions for Chennai Market**:                                                                                 SELECT * FROM transactions join markets on market_code=markets_code WHERE markets_name='Chennai';
**Show distinct product codes sold in Chennai**:                                                                          SELECT DISTINCT COUNT(product_code) FROM transactions join markets on market_code=markets_code WHERE markets_name='Chennai'
**Show transactions where currency is US dollars**: SELECT * FROM transactions WHERE currency='USD'
**Show transactions in 2020 join by date table**: SELECT * FROM transactions join date ON transactions.order_date=date.date;
**Show Total revenue in 2020**:
