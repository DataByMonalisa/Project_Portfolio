# Question 1
## Find the total sales amount per country from the last 6 months.
           SELECT ct.Country, SUM(s.sale_Amount) AS Total_Sales
           FROM customers AS ct
           JOIN sales AS s
           ON s.Customer_ID = ct.Customer_ID
           WHERE s.Order_Date >= DATE_SUB(CURDATE(), INTERVAL 6 MONTH)
           GROUP BY ct.Country;

# Question 2
## Find the top 5 customers who have spent the most in the last 1 year. 
    SELECT ct.Name, SUM(s.Sale_Amount) AS Total_Sales
    FROM customers AS ct
    JOIN sales AS s
    ON s.Customer_ID = ct.Customer_ID
    WHERE s.Order_Date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR)
    GROUP BY ct.Name
    ORDER BY Total_Sales DESC
    LIMIT 5;

# Question 3
## Find the top 3 best-selling product categories based on total sales in the last 6 months.
    SELECT p.Category, SUM(s.Sale_Amount) AS Total_Sales
    FROM sales AS s
    JOIN products AS p
    ON p.Product_ID = s.Product_ID
    WHERE s.Order_Date >= DATE_SUB(CURDATE(), INTERVAL 6 MONTH)
    GROUP BY p.Category
    ORDER BY Total_Sales DESC
    LIMIT 3;

# Question 4
## Find the employee who processed the highest number of orders in the last 3 months.
     SELECT emp.Name, COUNT(s.Order_ID) AS Total_Orders
     FROM sales AS s
     JOIN employees_order AS e
     ON e.Order_ID = s.Order_ID
     JOIN employees AS emp
     ON emp.Employee_ID = e.Employee_ID
     WHERE s.Order_Date >= DATE_SUB(CURDATE(), INTERVAL 3 MONTH)
     GROUP BY emp.Name
     ORDER BY Total_Orders DESC
     LIMIT 1;

# Question 5
## Find the month-over-month percentage growth in total sales for the last 6 months.


















