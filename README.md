--One way to understand how a city government works is by looking at who it employs and how its employees are compensated. This data contains the names, job title, and compensation for San Francisco city employees on an annual basis from 2011. source: Kaggle


#1.-- How have salaries changed over time between different groups of people?

SELECT 
    EmployeeName, 
    JobTitle, 
    Year, 
    AVG(BasePay) as average_salary
FROM 
    BIT_DB1."SF_Salaries
"
GROUP BY 
    year, JobTitle, EmployeeName
ORDER BY 
    year, JobTitle, EmployeeName;
    

#2. -- Write a query to fetch the number of employees working in the department Health/Nurse.

SELECT *
FROM BIT_DB1."SF_Salaries
" 
WHERE JobTitle LIKE "%NURSE%";


#3.-- query to find all the employees whose salary is between 10000 to 50000.

SELECT EmployeeName, JobTitle, TotalPay
FROM BIT_DB1."SF_Salaries
" 
WHERE TotalPay BETWEEN '10000' AND '50000';

#4.---Write a query to find the names of employees that begin with ‘A’

SELECT * 
FROM BIT_DB1."SF_Salaries
"
 WHERE EmployeeName LIKE 'A%';


#5.-- Write a query to find the third-highest salary from the SF SALAARIES table.

SELECT TOP 1 TotalPay
FROM (SELECT TOP 3 TotalPay
FROM BIT_DB1."SF_Salaries
"
ORDER BY TotalPay DESC) AS emp
ORDER BY TotalPay ASC;

#6.-- find the second highest salary of Employeename & Jobtitle

SELECT MAX(TotalPay) 
 FROM BIT_DB1."SF_Salaries
"
 WHERE TotalPay NOT IN (select MAX(TotalPay) from BIT_DB1."SF_Salaries
" ); 

#7.-- find Max Salary from each department.

SELECT JobTitle, MAX(TotalPay) 
FROM BIT_DB1."SF_Salaries
"  
GROUP BY JobTitle;
