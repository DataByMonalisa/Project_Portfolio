# Question 1 : Retrieve all employee details from the Employees table.
           SELECT * FROM employee_data;
# Question 2 : Get the total number of employees in each department.
           SELECT dpt.Department_Name, COUNT(emp.Employee_ID) AS Employee_Count
           FROM employee_data AS emp
           JOIN managers AS mng
           ON emp.Manager_ID = mng.Manager_ID
           JOIN department AS dpt
           ON mng.Department_ID = dpt.Department_ID
           GROUP BY dpt.Department_Name;
# Question 3: Find all employees who work under a specific manager (e.g., Manager_ID = 5).
           SELECT mng.Manager_Name , COUNT(emp.Employee_ID) AS Employee_Count
           FROM employee_data AS emp
           JOIN managers AS mng
           ON emp.Manager_ID = mng.Manager_ID
           WHERE emp.Manager_ID = 5
           GROUP BY mng.Manager_Name;
# Question 4: List employees along with their department names using a JOIN between Employees and Departments.
            SELECT emp.First_Name , emp.Last_Name , dpt.Department_Name
            FROM employee_data AS emp
            JOIN managers AS mng
            ON emp.Manager_ID = mng.Manager_ID
            JOIN department AS dpt
            ON mng.Department_ID = dpt.Department_ID; 
 # Question 5: Show the count of employees per country.
            ELECT Country , COUNT(Employee_ID)
            FROM employee_data
            GROUP BY Country;
# Question 6: Retrieve all employees who have the designation "Software Engineer"
            SELECT *
            FROM employee_data
            WHERE Designation = 'Software Engineer';
# Question 7: Find the manager names for each employee by joining the Employees table with Managers.
