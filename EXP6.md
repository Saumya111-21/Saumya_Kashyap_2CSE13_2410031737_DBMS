# EXPERIMENT-6
# 01. Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name (Use decode function).
 Query
~~~sql   
SELECT ENAME,EMPNO,  
    -> CASE DEPTNO WHEN 10 THEN 'RESEARCH' 
    -> WHEN 20 THEN 'ACCOUNTING' 
    -> WHEN 30 THEN 'SALES' 
    -> WHEN 40 THEN 'OPERATIONS' 
    -> END AS DEPT_NAME  FROM EMPLOYEE;
~~~
 Output
~~~SQL
+--------+-------+------------+
| ENAME  | EMPNO | DEPT_NAME  |
+--------+-------+------------+
| SMITH  |  7369 | ACCOUNTING |
| ALLEN  |  7499 | SALES      |
| WARD   |  7521 | SALES      |
| JONES  |  7566 | ACCOUNTING |
| MARTIN |  7654 | SALES      |
| BLAKE  |  7698 | SALES      |
| CLARK  |  7782 | ACCOUNTING |
| SCOTT  |  7788 | OPERATIONS |
| KING   |  7839 | ACCOUNTING |
| TURNER |  7844 | SALES      |
| ADAMS  |  7876 | ACCOUNTING |
| JAMES  |  7900 | SALES      |
| FORD   |  7902 | ACCOUNTING |
| MILLER |  7934 | RESEARCH   |
+--------+-------+------------+
~~~
# 02. Display your age in days.
 Query
~~~sql   
SELECT DATEDIFF(CURDATE(), '2003-08-15') AS age_in_days;
~~~
 Output
~~~SQL
+-------------+
| age_in_days |
+-------------+
|        8220 |
+-------------+
~~~
# 03. Display your age in months.
 Query
~~~sql   
SELECT TIMESTAMPDIFF(MONTH, '2003-12-07', CURDATE()) AS age_in_months;
~~~
 Output
~~~SQL
+---------------+
| age_in_months |
+---------------+
|           266 |
+---------------+
~~~
# 04. Display the current date as 15th August Friday Nineteen Ninety-Seven.
 Query
~~~sql   

~~~
 Output
~~~SQL

~~~
# 05. Display the following output for each row from employee table.
 Query
~~~sql   
SELECT ENAME, DATE_FORMAT(HIREDATE,'%D %M %W %Y')AS HIRE_DATE FROM EMPLOYEE;
~~~
 Output
~~~SQL
+--------+------------------------------+
| ENAME  | HIRE_DATE                    |
+--------+------------------------------+
| SMITH  | 17th December Wednesday 1980 |
| ALLEN  | 20th February Friday 1981    |
| WARD   | 22nd February Sunday 1981    |
| JONES  | 2nd April Thursday 1981      |
| MARTIN | 28th September Monday 1981   |
| BLAKE  | 1st March Sunday 1981        |
| CLARK  | 9th June Tuesday 1981        |
| SCOTT  | 9th December Thursday 1982   |
| KING   | 17th November Tuesday 1981   |
| TURNER | 8th September Tuesday 1981   |
| ADAMS  | 12th January Wednesday 1983  |
| JAMES  | 3rd December Thursday 1981   |
| FORD   | 3rd December Thursday 1981   |
| MILLER | 23rd January Saturday 1982   |
+--------+------------------------------+
~~~
# 06.Scott has joined the company on Wednesday 13th August Nineteen Ninety 
 Query
~~~sql   
SELECT DATE_FORMAT(CURDATE(), '%D %M %W');
~~~
 Output
~~~SQL
+------------------------------------+
| DATE_FORMAT(CURDATE(), '%D %M %W') |
+------------------------------------+
| 22nd February Sunday               |
+------------------------------------+
~~~
# 07. Find the date for nearest Saturday after current date.
 Query
~~~sql   
 SELECT DATE_ADD(CURDATE(),INTERVAL(5-WEEKDAY(CURDATE()))DAY) AS NEXT_SATURDAY;
~~~
 Output
~~~SQL
+---------------+
| NEXT_SATURDAY |
+---------------+
| 2026-02-14    |
+---------------+
~~~
# 08. Display current time.
 Query
~~~sql   
SELECT CURTIME();
~~~
 Output
~~~SQL
+-----------+
| CURTIME() |
+-----------+
| 19:59:36  |
+-----------+
~~~
# 09. Display the date three months Before the current date
 Query
~~~sql   
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH);
~~~
 Output
~~~SQL
+---------------------------------------+
| DATE_SUB(CURDATE(), INTERVAL 3 MONTH) |
+---------------------------------------+
| 2025-11-15                            |
+---------------------------------------+
~~~
# 10. Display those employees who joined in the company in the month of Dec.
 Query
~~~sql   
SELECT ENAME, HIREDATE  FROM employee WHERE MONTH(hiredate) = 12;
~~~
 Output
~~~SQL
+-------+------------+
| ENAME | HIREDATE   |
+-------+------------+
| SMITH | 1980-12-17 |
| SCOTT | 1982-12-09 |
| JAMES | 1981-12-03 |
| FORD  | 1981-12-03 |
+-------+------------+
~~~
# 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.
 Query
~~~sql   
SELECT *
    -> FROM employee
    -> WHERE LEFT(DATE_FORMAT(hiredate,'%d%m%Y'),2) =
    ->       RIGHT(sal,2);
~~~
 Output
~~~SQL
Empty set (0.003 sec)
~~~
# 12. Display those employees whose 10% of salary is equal to the year of joining.
 Query
~~~sql   
SELECT *
    -> FROM employee
    -> WHERE sal * 0.10 =
    ->       YEAR(hiredate);
~~~
 Output
~~~SQL
Empty set (0.005 sec)
~~~
# 13. Display those employees who joined the company before 15 of the months.
 Query
~~~sql   
SELECT *
    -> FROM employee
    -> WHERE DAY(hiredate) < 15;
~~~
 Output
~~~SQL
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-03-01 | 3135 | NULL |     30 |
|  7782 | CLARK  | MANAGER  | 7839 | 1981-06-09 | 2695 | NULL |     20 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3300 | NULL |     40 |
|  7844 | TURNER | SELESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3300 | NULL |     20 |
+-------+--------+----------+------+------------+------+------+--------+

~~~
# 14. Display those employees who has joined before 15th of the month.
 Query
~~~sql   
SELECT * FROM employee WHERE DAY(hiredate) > 15;
~~~
 Output
~~~SQL
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SELESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SELESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7654 | MARTIN | SELESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
~~~
# 15. Display those employees whose joining DATE is available in deptno
 Query
~~~sql   
SELECT ENAME, HIREDATE FROM EMPLOYEE WHERE HIREDATE !="";
~~~
 Output
~~~SQL
+--------+------------+
| ENAME  | HIREDATE   |
+--------+------------+
| SMITH  | 1980-12-17 |
| ALLEN  | 1981-02-20 |
| WARD   | 1981-02-22 |
| JONES  | 1981-04-02 |
| MARTIN | 1981-09-28 |
| BLAKE  | 1981-03-01 |
| CLARK  | 1981-06-09 |
| SCOTT  | 1982-12-09 |
| KING   | 1981-11-17 |
| TURNER | 1981-09-08 |
| ADAMS  | 1983-01-12 |
| JAMES  | 1981-12-03 |
| FORD   | 1981-12-03 |
| MILLER | 1982-01-23 |
+--------+------------+
~~~