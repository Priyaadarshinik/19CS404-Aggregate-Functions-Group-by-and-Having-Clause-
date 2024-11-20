# 19CS404-Aggregate-Functions-Group-by-and-Having-Clause-
# AIM: 
To study and implement aggregate functions, group by and having clause with suitable 
examples. 
 
# THEORY: 
An aggregate function is a function that performs a calculation on a set of values, and returns a 
single value. 
Aggregate functions are often used with the GROUP BY clause of the SELECT statement. The 
GROUP BY clause splits the result-set into groups of values and the aggregate function can be 
used to return a single value for each group. 
The most commonly used SQL aggregate functions are: 
 
MIN() - returns the smallest value within the selected column 
Syntax: 
SELECT MIN(column_name) FROM table_name 
WHERE condition; 
Example: SELECT MIN (Sal) FROM emp; 
 
MAX() - returns the largest value within the selected column 
Syntax: 
NAME: ANU VARSHINI M B   REG NO: 212223240010
SELECT MAX(column_name) FROM table_name 
WHERE condition; 
Example: SELECT MAX (Sal) FROM emp; 
 
COUNT() - returns the number of rows in a set 
Syntax: 
SELECT COUNT(column_name) FROM table_name 
WHERE condition; 
Example: SELECT COUNT (Sal) FROM emp; 
 
SUM() - returns the total sum of a numerical column 
Syntax: 
SELECT SUM(column_name) 
 
FROM table_name WHERE condition; 
Example: SELECT SUM (Sal) From emp; 
 
AVG() - returns the average value of a numerical column 
Syntax: 
SELECT AVG(column_name) FROM table_name 
WHERE condition; 
Example: Select AVG (10, 15, 30) FROM DUAL; 
 
GROUP BY: 
This query is used to group all the records in a relation together for each and every value of a 
specific key(s) and then display them for a selected set of fields in the relation. 
 
Syntax: 
SELECT column_name(s) FROM table_name WHERE condition 
GROUP BY column_name(s) 
ORDER BY column_name(s); 
Example: SQL> SELECT EMPNO, SUM (SALARY) FROM EMP GROUP BY EMPNO; 
 
GROUP BY-HAVING: 
The HAVING clause was added to SQL because the WHERE keyword could not be used with 
aggregate functions. The HAVING clause must follow the GROUP BY clause in a query and 
must also precede the ORDER BY clause if used. 
 
Syntax: 
SELECT column_name(s) FROM table_name WHERE condition 
GROUP BY column_name(s) 
HAVING condition 
ORDER BY column_name(s); 
 
# Question 1: 
 Sample table:Appointments Table 
 
![image](https://github.com/user-attachments/assets/5af7314e-c787-4162-9d05-f9685938a66c)

Answer: 
SELECT strftime('%H',AppointmentDateTime) 
AS HourOfDay, 
COUNT(*) AS 
TotalAppointments 
FROM Appointments 
GROUP BY strftime('%H',AppointmentDateTime) 
ORDER BY HourOfDay; 
 
Output:

![image](https://github.com/user-attachments/assets/5a512c7b-eb13-488b-b371-265a519d34af)
 
# Question 2: 
How many patients are there in each age group category (e.g., under 20, 20-30, 30-40, etc.)? 
Sample table: Patients Table 
 
Answer: 
WITH PatientAges AS ( 
    SELECT  
        (strftime('%Y', 'now') - strftime('%Y', DateOfBirth) -  
         (strftime('%m', 'now') < strftime('%m', DateOfBirth)) -  
         ((strftime('%m', 'now') = strftime('%m', DateOfBirth))  
          AND (strftime('%d', 'now') < strftime('%d', DateOfBirth)))) AS Age 
    FROM Patients 
) 
SELECT  
    CASE 
        WHEN Age < 20 THEN 'Under 20' 
        WHEN Age BETWEEN 20 AND 29 THEN '20-30' 
        WHEN Age BETWEEN 30 AND 39 THEN '31-40'
        WHEN Age BETWEEN 40 AND 49 THEN '41-50' 
        ELSE 'Above 50' 
    END AS AgeGroup, 
    COUNT(*) AS TotalPatients 
FROM PatientAges 
GROUP BY AgeGroup 
ORDER BY AgeGroup; 
 
Output: 
![image](https://github.com/user-attachments/assets/8c162ac8-2420-44c1-ac5e-e9cfb08607c7)
 
 
# Question 3: 
How many prescriptions were written in each frequency category (e.g., once daily, twice 
daily)? 
Sample tablePrescriptions Table 
 
Answer: 
SELECT  
    Frequency, 
    COUNT(*) AS TotalPrescriptions 
FROM Prescriptions 
GROUP BY Frequency 
NAME: ANU VARSHINI M B   REG NO: 212223240010
ORDER BY Frequency; 
 
Output: 
 
 
# Question 4: 
Write a SQL query to Calculate the average income of the employees with names starting with 
'A':  
Table: employee 
name        type 
----------  ---------- 
id          INTEGER 
name        TEXT 
age         INTEGER 
city        TEXT 
income      INTEGER 
 
Answer: 
SELECT  
    AVG(income) AS avg_income 
FROM employee 
WHERE name LIKE 'A%'; 
 
Output: 
![image](https://github.com/user-attachments/assets/acfc28ee-bd83-4018-9108-f01d006b1264)

 
# Question 5: 
Write a SQL query to calculate the total number of working hours of all employees 
Sample table: employee1 
 
Answer: 
SELECT  
    SUM(workhour) AS "Total working hours" 
FROM employee1; 
 
Output: 
 
 
# Question 6: 
Write a SQL query to calculate total purchase amount of all orders. Return total purchase 
amount. 

Sample table: orders 
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  ----------- 
70001       150.5       2012-10-05  3005         5002 
70009       270.65      2012-09-10  3001         5005 
70002       65.26       2012-10-05  3002         5001 
 
Answer: 
SELECT SUM(purch_amt) AS TOTAL FROM orders; 
Output: 
 
 
# Question 7: 
Write a SQL query to count the number of customers. Return number of customers. 
Sample table: customer 
customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+------------- 
        3002 | Nick Rimando   | New York   |   100 |        5001 
        3007 | Brad Davis     | New York   |   200 |        5001 
        3005 | Graham Zusi    | California |   200 |        5002 
 
Answer: 
SELECT COUNT(cust_name) AS COUNT FROM customer;
Output: 
 
 
# Question 8: 
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates 
the minimum work hours for each date, and excludes dates where the minimum work hour is not 
less than 10. 
 
Answer: 
SELECT jdate,MIN(workhour) AS "MIN(workhour)" FROM 
employee1 GROUP BY jdate 
HAVING MIN(workhour)<10; 
 
Output: 
 
# Question 9: 
Write the SQL query that achieves the grouping of data by age intervals using the expression 
(age/5)5, calculates the average age for each group, and excludes groups where the average age 
is not less than 24. 
 
Answer: 
SELECT (age -(age%5)) AS age_group, AVG(age) AS "AVG(age)" 
FROM customer1  
GROUP BY age_group 
HAVING AVG(age)<=24; 
 
Output: 
 
 
# Question 10: 
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum 
work hours for each occupation, and excludes occupations where the minimum work hour is not 
greater than 8. 
 
Answer: 
SELECT occupation, MIN(workhour) AS "MIN(workhour)" 
FROM employee1 
group by occupation 
having min(workhour)>8; 
 
Output:  
 
 
 
Result: 
 
Thus , the SQL queries to implement aggregate functions have been executed successfully
