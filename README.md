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

