# EXPERIMENT- 7
# 01.Compute the no. of days remaining in this year. 
 Query
~~~sql   
SELECT DATEDIFF("2026-12-31",CURDATE())AS DAYS_REMAINING;
~~~
 Output
~~~SQL
+----------------+
| DAYS_REMAINING |
+----------------+
|            308 |
+----------------+
~~~
# 02. Find the highest and lowest salaries and the difference between of them.
 Query
~~~sql   
SELECT MAX(SAL) AS highest_salary,
    -> MIN(SAL) AS lowest_salary,
    -> MAX(SAL) - MIN(SAL) AS difference
    -> FROM EMPLOYEE;
~~~
 Output
~~~SQL
+----------------+---------------+------------+
| highest_salary | lowest_salary | difference |
+----------------+---------------+------------+
|           5500 |           880 |       4620 |
+----------------+---------------+------------+
~~~
# 03. List employee whose commission is greater than 25 % of their salaries.
 Query
~~~sql   
SELECT ENAME, SAL, COMM
    -> FROM EMPLOYEE
    -> WHERE COMM > 0.25 * SAL;
~~~
 Output
~~~SQL
+--------+------+------+
| ENAME  | SAL  | COMM |
+--------+------+------+
| MARTIN | 1250 | 1400 |
+--------+------+------+
~~~
# 04.Make a query that displays salary in dollar format. 
 Query
~~~sql   
SELECT ename,
    -> CONCAT('$', FORMAT(sal,2)) AS salary_in_dollar
    -> FROM employee;
~~~
 Output
~~~SQL
+--------+------------------+
| ename  | salary_in_dollar |
+--------+------------------+
| SMITH  | $880.00          |
| ALLEN  | $1,600.00        |
| WARD   | $1,250.00        |
| JONES  | $3,273.00        |
| MARTIN | $1,250.00        |
| BLAKE  | $3,135.00        |
| CLARK  | $2,695.00        |
| SCOTT  | $3,300.00        |
| KING   | $5,500.00        |
| TURNER | $1,500.00        |
| ADAMS  | $1,210.00        |
| JAMES  | $1,045.00        |
| FORD   | $3,300.00        |
| MILLER | $1,430.00        |
+--------+------------------+
~~~
# 05. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.
 Query
~~~sql   
SELECT JOB,
    -> SUM(CASE DEPTNO WHEN 10 THEN SAL ELSE 0 END) AS DEPT10,
    -> SUM(CASE DEPTNO WHEN 20 THEN SAL ELSE 0 END) AS DEPT20,
    -> SUM(CASE DEPTNO WHEN 30 THEN SAL ELSE 0 END) AS DEPT30,
    -> SUM(CASE DEPTNO WHEN 40 THEN SAL ELSE 0 END) AS DEPT40,
    -> SUM(SAL) AS TOTAL_SAL
    -> FROM EMPLOYEE
    -> GROUP BY JOB;

~~~
 Output
~~~SQL
+-----------+--------+--------+--------+--------+-----------+
| JOB       | DEPT10 | DEPT20 | DEPT30 | DEPT40 | TOTAL_SAL |
+-----------+--------+--------+--------+--------+-----------+
| ANALYST   |      0 |   3300 |      0 |   3300 |      6600 |
| CLERK     |   1430 |   2090 |   1045 |      0 |      4565 |
| MANAGER   |      0 |   5968 |   3135 |      0 |      9103 |
| PRESIDENT |      0 |   5500 |      0 |      0 |      5500 |
| SELESMAN  |      0 |      0 |   5600 |      0 |      5600 |
+-----------+--------+--------+--------+--------+-----------+
~~~
# 06. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading.
 Query
~~~sql   
SELECT COUNT(*) AS TOTAL_EMP,
    -> SUM(CASE YEAR(HIREDATE) WHEN 1980 THEN 1 ELSE 0 END) AS YEAR_1980,
    -> SUM(CASE YEAR(HIREDATE) WHEN 1981 THEN 1 ELSE 0 END) AS YEAR_1981,
    -> SUM(CASE YEAR(HIREDATE) WHEN 1982 THEN 1 ELSE 0 END) AS YEAR_1982,
    -> SUM(CASE YEAR(HIREDATE) WHEN 1983 THEN 1 ELSE 0 END) AS YEAR_1983
    -> FROM EMPLOYEE;
~~~
 Output
~~~SQL
+-----------+-----------+-----------+-----------+-----------+
| TOTAL_EMP | YEAR_1980 | YEAR_1981 | YEAR_1982 | YEAR_1983 |
+-----------+-----------+-----------+-----------+-----------+
|        14 |         1 |        10 |         2 |         1 |
+-----------+-----------+-----------+-----------+-----------+
~~~
# 07. Query to get the last Sunday of Any Month.
 Query
~~~sql   
 SELECT DATE_SUB(
    -> LAST_DAY('2026-02-01'),
    -> INTERVAL (WEEKDAY(LAST_DAY('2026-02-01')) + 1) DAY
    -> ) AS LAST_SUNDAY;
~~~
 Output
~~~SQL
+-------------+
| LAST_SUNDAY |
+-------------+
| 2026-02-22  |
+-------------+
~~~
# 08. Display department numbers and total number of employees working in each department.
 Query
~~~sql   
SELECT COUNT(*)DEPTNO, DEPTNO FROM EMPLOYEE  GROUP BY DEPTNO;
~~~
 Output
~~~SQL
+--------+--------+
| DEPTNO | DEPTNO |
+--------+--------+
|      1 |     10 |
|      6 |     20 |
|      6 |     30 |
|      1 |     40 |
+--------+--------+

~~~
# 09. Display the various jobs and total number of employees within each job group.
 Query
~~~sql   
SELECT COUNT(JOB),JOB FROM EMPLOYEE GROUP BY JOB;
~~~
 Output
~~~SQL
+------------+-----------+
| COUNT(JOB) | JOB       |
+------------+-----------+
|          2 | ANALYST   |
|          4 | CLERK     |
|          3 | MANAGER   |
|          1 | PRESIDENT |
|          4 | SELESMAN  |
+------------+-----------+
~~~
# 10. Display the depart numbers and total salary for each department.
 Query
~~~sql   
 SELECT DEPTNO,
    -> SUM(sal) AS total_salary
    -> FROM EMPLOYEE
    -> GROUP BY DEPTNO
    -> ORDER BY DEPTNO;
~~~
 Output
~~~SQL
+--------+--------------+
| DEPTNO | total_salary |
+--------+--------------+
|     10 |         1430 |
|     20 |        16858 |
|     30 |         9780 |
|     40 |         3300 |
+--------+--------------+
~~~