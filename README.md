# sqlqueries


Requirement : Find 100 employee details for sampling from 5000 records of employee.
We will use WITH clause and RAND() for the same , and also use ROW_NUMBER()

Explanation : WITH clause essentially makes it easier to write complex queries by breaking them down into manageable subqueries.  
              ROW_NUMBER()OVER (ORDER BY RAND()) generates a random row number for each row. This ensures that the rows are ordered randomly before assigning numbers.

WITH Emprow AS (
    SELECT *,
           ROW_NUMBER() OVER (ORDER BY RAND()) AS row_num
    FROM EMPLOYEETABLE
)
SELECT *
FROM Emprow
WHERE row_num <= 100;

Requirement : Find all employees, ID, Name, and Salary whose salary is higher than the average salary of all employees in the from EMPLOYEETABLE
We will use AVG () along with WITH Clause, We will also create a temp table to store the value of Avg Salary and then join from main table 


WITH temporaryTable AS (
    SELECT AVG(Salary) AS averageValue
    FROM EMPLOYEETABLE
)
SELECT EmployeeID, Name, Salary
FROM Employee
CROSS JOIN temporaryTable
WHERE Employee.Salary > temporaryTable.averageValue;
