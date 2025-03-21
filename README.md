USE Sales;

       
SELECT *
FROM ChocolateSales;

USE sales;

-- Total saleS amount

SELECT SUM(Amount) As Total_Sales
FROM Chocolatesales;


-- Average sales amount per transaction

SELECT AVG(Amount) As Average_sales
FROM Chocolatesales;


-- Total number of sales transactions

SELECT COUNT(*) As Total_Transactions
FROM Chocolatesales;


-- Total number of Boxes shipped

SELECT SUM(BoxesShipped) As Total_Boxes
FROM Chocolatesales;


-- Total revenue generated per country

SELECT Country, SUM(Amount) As Total_Revenue
FROM Chocolatesales
Group by Country
Order by Total_Revenue DESC;


-- Total number of sales made by each salesperson

SELECT Salesperson, SUM(Amount) As Total_sales
FROM Chocolatesales
Group by SalesPerson
Order by Total_sales DESC;


-- What is the highest and lowest sales amount recorded

SELECT MAX(Amount) As Highest_sales, MIN(Amount) As Lowest_sale
FROM Chocolatesales;


-- Number of transactions for each product

SELECT Product, COUNT(*) As Transaction_count
FROM Chocolatesales
Group by Product
Order by Transaction_count;


 -- Number of boxes shipped per country
 
 SELECT country, SUM(BoxesShipped) As Total_Boxes
 FROM Chocolatesales 
 Group by Country
 Order by Total_Boxes DESC;
 
 
 -- Top 3 salesperson based on total sales
 
 SELECT Salesperson, SUM(Amount) As Total_sales
 From Chocolatesales
 Group by Salesperson
 Order by Total_sales DESC
 Limit 3;
 
 
 -- Salespersons who sold more than $50,000 in total
 
 SELECT Salesperson, SUM(Amount) As Total_sales
 FROM Chocolatesales
 Group by Salesperson
 HAVING Total_sales > 200000;
 
 
-- Show sales amount grouped by Month

 SELECT MONTH (Salesdate) As Month, SUM(Amount) As Total_sales
 FROM Chocolatesales
 Group by Month(Salesdate)
 Order by Month DESC;
 
 
 -- Salesperson with the highest sales in the month of May
 
 SELECT Salesperson, SUM(Amount) As Total_sales
FROM Chocolatesales
WHERE Month (Salesdate) = 5
Group by Salesperson
Order by Total_sales DESC
 Limit 1;


-- Sales that occurred on weekends

SELECT *
FROM Chocolatesales
WHERE DAYOFWEEK(Salesdate) IN (1, 7); -- 1 = Sunday, 7 = Saturday


-- Product that generated the most revenue

SELECT Product, SUM(Amount) As TotalRevenue
FROM Chocolatesales
Group by Product
Order by TotalRevenue DESC
Limit 1;


-- Country with the most sales transaction

SELECT Country, COUNT(*) As Transaction_Count
FROM Chocolatesales
Group by Country
Order by Transaction_Count
Limit 1;


-- Month with the highest sales amount

SELECT MONTH (Salesdate) As Month, SUM(Amount) As Total_sales
FROM Chocolatesales
group by Month(salesdate)
Order  by Total_sales DESC
Limit 1;
