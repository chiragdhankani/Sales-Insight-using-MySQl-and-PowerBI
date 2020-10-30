# Sales-Insight-using-MySQl-and-PowerBI
This Case study was based on Computer hardware business which is facing challenges in dynamically changing market. Sales director decides to invest in Data Analysis project and he would like to build a Power BI Dashboard that can give him real time sales insights. Operations performed: AIMS Grid for Planning, Exploring Data insights using MySQL, Data Cleaning And ETL(Extract, Transform, Load) in PowerBI, Building Dashboard.  

## Data Analysis using My-SQl

1. Show all Customer records
```
SELECT * FROM CUSTOMER;
```
2. Show total number of customers
```
SELECT count(*) FROM customers;
```
3. Show transactions for Mumbai market(Market Code = "Mark002")
```
SELECT * FROM transaction WHERE market_code="Mark002";
```
4. Show Distinct product Codes that were sold in Mumbai 
```
SELECT DISTINCT product_code FROM transactions WHERE market_code="Mark002";
```
5. Show Transactions Where Currency is in US Dollars
```
SELECT * FROM transactions WHERE Currency="USD";
```
6. Using INNER JOIN showing transactions in the year 2020 By Inner Joining two 
tables on using Date Column as a Primary key in Transaction Table and a Foreign key in Date Table
```
SELECT transactions.*,date.* From transactions INNER JOIN date on 
transactions.order_date = date.date WHERE sales.date.year='2020';
```
7. Finding the total sales revenue of the year 2020
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON 
transactions.order_date = date.date WHERE date.year='2020';
```
8. Show total revenue in the month of January 2020
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transaction.order_date = date.date 
 WHERE date.year = 2020 and date.month_name="January" 
 and (transactions.currency= "INR" or transaction.currency= "USD");
``` 
9. SHow total revenue in year 2020 in Mumbai
```
SELECT SUM(transactions.sales_amount) FROM transactioc INNER JOIN date ON transactions.order_date = date.date 
   WHERE date.year=2020 and transactions.market_code="Mark002";
```

#Data Analysis Using Power BI
```
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or
[currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
```  
