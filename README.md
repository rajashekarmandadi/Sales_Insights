# Sales Insights Data Analysis Project
## Data Analysis Using SQL
1. Show all customer records
   >SELECT * FROM customers;
2. Show all transaction records
   >SELECT * FROM transactions;
3. Show total number of customers
   >SELECT count(*) FROM customers;
4. Show transactions for chennai market ( Market code for chennai is Mark001)
   >SELECT * FROM  transactions WHERE market_code = "Mark001";
5. Show distinct product_code that where sold in chennai
   >SELECT distinct product_code FROM  transactions WHERE market_code = "Mark001";
6. Show transactions where currency is US dollars
   >SELECT * FROM transactions WHERE currency="USD"
7. Show transactions in 2020 join by date table
   >SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020;
8. Show total revenue in year 2020,
   >SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";
9. Show total revenue in year 2020, January Month,
    >SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");
10. Show total revenue in year 2020 in Chennai
    >SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 and transactions.market_code="Mark001";
## Data Analysis Using Power BI 
  1. Formula for creating norm_sales_amount
     
     >=Table.AddColumn(#"Filtered Rows", "norm_sales_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
