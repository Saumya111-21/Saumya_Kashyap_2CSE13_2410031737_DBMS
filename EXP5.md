# EXPERIMENT-5
# 01. Display the total number of employee working in the company.
 Query
~~~sql   
SELECT COUNT(EMPNO) FROM EMPLOYEE;
~~~
 Output
~~~SQL
+--------------+
| COUNT(EMPNO) |
+--------------+
|           14 |
+--------------+
~~~
# 02. Display the total salary being paid to all employees.
 Query
~~~sql   
SELECT SUM(SAL) FROM EMPLOYEE;
~~~
 Output
~~~SQL
+----------+
| SUM(SAL) |
+----------+
|    31368 |
+----------+
~~~
# 03. Display the maximum salary from employee table.
 Query
~~~sql   
 SELECT MAX(SAL) FROM EMPLOYEE;
~~~
 Output
~~~SQL
+----------+
| MAX(SAL) |
+----------+
|     5500 |
+----------+
~~~
# 04. Display the minimum salary from employee table.
 Query
~~~sql   
SELECT MIN(SAL) FROM EMPLOYEE;
~~~
 Output
~~~SQL
+----------+
| MIN(SAL) |
+----------+
|      880 |
+----------+
~~~
# 05. Display the average salary from employee table
 Query
~~~sql   
SELECT AVG(SAL) FROM EMPLOYEE;
~~~
 Output
~~~SQL
+-----------+
| AVG(SAL)  |
+-----------+
| 2240.5714 |
+-----------+
~~~
# 06. Display the maximum salary being paid to clerk.
 Query
~~~sql   
SELECT AVG(SAL) FROM EMPLOYEE WHERE JOB="CLERK";
~~~
 Output
~~~SQL
+-----------+
| AVG(SAL)  |
+-----------+
| 1141.2500 |
+-----------+
~~~
# 07. Display the maximum salary being paid in dept no 20.
 Query
~~~sql   
SELECT MAX(SAL) FROM EMPLOYEE
    -> WHERE DEPTNO=20;
~~~
 Output
~~~SQL
+----------+
| MAX(SAL) |
+----------+
|     5500 |
+----------+
~~~
# 08. Display the minimum salary paid to any salesman.
 Query
~~~sql   
SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB="SELESMAN";
~~~
 Output
~~~SQL
+----------+
| MAX(SAL) |
+----------+
|     1600 |
+----------+
~~~
# 09. Display the average salary drawn by managers.
 Query
~~~sql   
SELECT AVG(SAL) FROM EMPLOYEE WHERE JOB="MANAGER";
~~~
 Output
~~~SQL
+-----------+
| AVG(SAL)  |
+-----------+
| 3034.3333 |
+-----------+
~~~
# 10. Display the total salary drawn by analyst working in dept no 40.
 Query
~~~sql   
SELECT SUM(SAL) FROM EMPLOYEE WHERE JOB="ANALYST" AND DEPTNO=40;
~~~
 Output
~~~SQL
+----------+
| SUM(SAL) |
+----------+
|     3300 |
+----------+
~~~
# 11. Display the names of the employee in Uppercase.
 Query
~~~sql   
SELECT UCASE(ENAME) AS NAME  FROM EMPLOYEE;
~~~
 Output
~~~SQL
+--------+
| NAME   |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| BLAKE  |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
~~~
# 12. Display the names of the employee in Lowercase.
 Query
~~~sql   
SELECT LCASE(ENAME) AS NAME  FROM EMPLOYEE;
~~~
 Output
~~~SQL
+--------+
| NAME   |
+--------+
| smith  |
| allen  |
| ward   |
| jones  |
| martin |
| blake  |
| clark  |
| scott  |
| king   |
| turner |
| adams  |
| james  |
| ford   |
| miller |
+--------+

~~~
# 13. Display the names of the employee in Proper case.
 Query
~~~sql   
SELECT CONCAT(
    -> UPPER(SUBSTR(ENAME, 1, 1)),
    -> LOWER(SUBSTR(ENAME, 2))
    -> ) AS PROPER_CASE_NAME
    -> FROM EMPLOYEE;
~~~
 Output
~~~SQL
+------------------+
| PROPER_CASE_NAME |
+------------------+
| Smith            |
| Allen            |
| Ward             |
| Jones            |
| Martin           |
| Blake            |
| Clark            |
| Scott            |
| King             |
| Turner           |
| Adams            |
| James            |
| Ford             |
| Miller           |
+------------------+
~~~
# 14. Display the length of Your name using appropriate function.
 Query
~~~sql   
SELECT LENGTH("Saumya Kashyap");
~~~
 Output
~~~SQL
+-------------------------+
| LENGTH("Saumya Kashyap") |
+-------------------------+
|                      14 |
+-------------------------+
~~~
# 15. Display the length of all the employee names.
 Query
~~~sql   
SELECT LENGTH(ENAME) AS NAME_LENGTH  FROM EMPLOYEE;
~~~
 Output
~~~SQL
+-------------+
| NAME_LENGTH |
+-------------+
|           5 |
|           5 |
|           4 |
|           5 |
|           6 |
|           5 |
|           5 |
|           5 |
|           4 |
|           6 |
|           5 |
|           5 |
|           4 |
|           6 |
+-------------+
~~~
