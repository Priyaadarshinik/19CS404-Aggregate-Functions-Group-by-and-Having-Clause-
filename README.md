# 19CS404-Aggregate-Functions-Group-by-and-Having-Clause- Registration number: 212223240126
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

![image](https://github.com/user-attachments/assets/dbb134af-b597-48c3-aec5-01155fb4fef7)
 
 
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

![image](https://github.com/user-attachments/assets/acfc28ee-bd83-4018-9108-f01d006b1264)

 
# Question 4: 
Write a SQL query to Calculate the average income of the employees with names starting with 
'A':  
Table: employee 

![image](https://github.com/user-attachments/assets/4cbc3e0a-90cf-4025-ad70-a1d9a9c0e700)

Answer: 
SELECT  
    AVG(income) AS avg_income 
FROM employee 
WHERE name LIKE 'A%'; 
 
Output: 

 ![image](https://github.com/user-attachments/assets/5012277d-8220-4a47-96d9-aa7ecb4e9164)

# Question 5: 
Write a SQL query to calculate the total number of working hours of all employees 
Sample table: employee1 
 
Answer: 

SELECT  
    SUM(workhour) AS "Total working hours" 
FROM employee1; 
 
Output: 

![image](https://github.com/user-attachments/assets/bec63914-878d-45f4-ac28-c88108319019)
 
 
# Question 6: 
Write a SQL query to calculate total purchase amount of all orders. Return total purchase 
amount. 

Sample table: orders 
![image](https://github.com/user-attachments/assets/87353c88-49fc-46c6-80ca-02c40cce10d3)

Answer: 
SELECT SUM(purch_amt) AS TOTAL FROM orders; 

Output: 
 
![image](https://github.com/user-attachments/assets/fda1da94-3236-4d66-8553-1cef020ca502)

# Question 7: 
Write a SQL query to count the number of customers. Return number of customers. 
Sample table: customer 

![image](https://github.com/user-attachments/assets/b5c6fd34-0bbd-47cb-906e-e34dbe57c0d2)

Answer: 

SELECT COUNT(cust_name) AS COUNT FROM customer;

Output: 
 ![image](https://github.com/user-attachments/assets/dec9cd56-24f7-46b3-a428-839f06ad480f)

 
# Question 8: 
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates 
the minimum work hours for each date, and excludes dates where the minimum work hour is not 
less than 10. 
 
Answer: 

SELECT jdate,MIN(workhour) AS "MIN(workhour)" FROM 
employee1 GROUP BY jdate 
HAVING MIN(workhour)<10; 
 
Output: 

![image](https://github.com/user-attachments/assets/fb564fdf-915d-422a-9468-af38485ca6e7)

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

![image](https://github.com/user-attachments/assets/5d6a081a-6fe8-4226-86b3-2d2b8687ac6e)

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

![image](https://github.com/user-attachments/assets/5d373c34-f7be-4cef-8b36-3b41766309a3)

# Result: 
 
Thus , the SQL queries to implement aggregate functions have been executed successfully
