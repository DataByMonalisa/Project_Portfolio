## 1. What is the age distribution of customers ?
        SELECT 
      CASE 
         WHEN age BETWEEN 18 AND 24 THEN '18-24'
         WHEN age BETWEEN 25 AND 34 THEN '25-34'
         WHEN age BETWEEN 35 AND 44 THEN '35-44'
         WHEN age BETWEEN 45 AND 54 THEN '45-54'
         WHEN age BETWEEN 55 AND 64 THEN '55-64'
         WHEN age >= 65 THEN '65+'
         ELSE 'Under 18' 
    END AS age_group,
    COUNT(*) AS customer_count
    FROM bakery
    GROUP BY age_group
    ORDER BY age_group;

# 2. What is the gender distribution of customers ?
           SELECT 
              Gender,
              COUNT(*) AS customer_count
            FROM bakery
            GROUP BY gender
            ORDER BY gender;

# 3. How many loyalty members are there?
    SELECT 
      Loyalty_Member,
      COUNT(*) AS member_count
    FROM bakery
    GROUP BY loyalty_member
    ORDER BY loyalty_member;

# 4. Which age group contributes the most to revenue?
         SELECT 
            CASE 
              WHEN age BETWEEN 18 AND 24 THEN '18-24'
              WHEN age BETWEEN 25 AND 34 THEN '25-34'
              WHEN age BETWEEN 35 AND 44 THEN '35-44'
              WHEN age BETWEEN 45 AND 54 THEN '45-54'
              WHEN age BETWEEN 55 AND 64 THEN '55-64'
              WHEN age >= 65 THEN '65+'
              ELSE 'Under 18' 
           END AS age_group,
           SUM(Amount_Spent) AS total_revenue
    FROM bakery
    GROUP BY age_group
    ORDER BY total_revenue DESC
    LIMIT 1;

# 5. What is the average amount spent per transaction?
      SELECT 
         AVG(Amount_Spent) AS average_spent_per_transaction
      FROM bakery;

# 6. How many items are purchased on average per transaction?
    SELECT 
      AVG(Items_Purchased) AS average_items_per_transaction
    FROM bakery;

# 7. Which payment method is most commonly used?
         SELECT 
            Payment_Method,
            COUNT(*) AS usage_count
         FROM bakery
         GROUP BY Payment_Method
         ORDER BY usage_count DESC
         LIMIT 1;
# 8. What is the correlation between items purchased and amount spent?
         SELECT 
            (SUM(Items_Purchased * Amount_Spent) - 
            (SUM(Items_Purchased) * SUM(Amount_Spent) / COUNT(*))) /
            (SQRT(SUM(POWER(Items_Purchased, 2)) - 
                   POWER(SUM(Items_Purchased), 2) / COUNT(*)) *
            SQRT(SUM(POWER(Amount_Spent, 2)) - 
                   POWER(SUM(Amount_Spent), 2) / COUNT(*))
           ) AS correlation
        FROM bakery;

# 9. Which items are purchased together most frequently?
        WITH SplitItems AS (
        SELECT 
        Bakery_ID,
        Customer_ID,
        Purchase_Date,
        TRIM(SUBSTRING_INDEX(SUBSTRING_INDEX(Items_Purchased, ',', n.n), ',', -1)) AS Item
        FROM Bakery
           CROSS JOIN (SELECT 1 AS n UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5) n
           WHERE n.n <= LENGTH(Items_Purchased) - LENGTH(REPLACE(Items_Purchased, ',', '')) + 1
         )
        SELECT 
        a.Item AS Item1, 
        b.Item AS Item2, 
        COUNT(*) AS Frequency
        FROM SplitItems a
        JOIN SplitItems b
        ON a.Bakery_ID = b.Bakery_ID 
        AND a.Item < b.Item
        GROUP BY Item1, Item2
        ORDER BY Frequency DESC
        LIMIT 10;

# 10. What are the busiest times of day for purchases?
     SELECT 
        Time_of_Purchase AS Time_Period,
        COUNT(*) AS Total_Purchases
    FROM Bakery
    GROUP BY Time_of_Purchase
    ORDER BY Total_Purchases DESC;
