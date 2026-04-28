# RETRIEVING DATA - SET 9 (SUBQUERIES)

## 1. Employee who earns highest salary
```sql
SELECT ename
FROM employee
WHERE sal = (SELECT MAX(sal) FROM employee);
```

## 2. Clerk with highest salary among clerks
```sql
SELECT empno, ename
FROM employee
WHERE job = 'CLERK'
AND sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'CLERK'
);
```

## 3. Salesman earning more than highest clerk salary
```sql
SELECT ename
FROM employee
WHERE job = 'SALESMAN'
AND sal > (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'CLERK'
);
```

## 4. Clerks earning more than JAMES and less than SCOTT
```sql
SELECT ename
FROM employee
WHERE job = 'CLERK'
AND sal > (
    SELECT sal FROM employee WHERE ename = 'JAMES'
)
AND sal < (
    SELECT sal FROM employee WHERE ename = 'SCOTT'
);
```
## 5. Employees earning more than JAMES OR more than SCOTT
```sql
SELECT ename
FROM employee
WHERE sal > (
    SELECT sal FROM employee WHERE ename = 'JAMES'
)
OR sal > (
    SELECT sal FROM employee WHERE ename = 'SCOTT'
);
```

## 6. Employees with highest salary in each department
```sql
SELECT ename, deptno, sal
FROM employee e
WHERE sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE deptno = e.deptno
);
```
## Correlated subquery (very important)

## 7. Employees with highest salary in each job group
```sql
SELECT ename, job, sal
FROM employee e
WHERE sal = (
    SELECT MAX(sal)
    FROM employee
    WHERE job = e.job
);
```
## 8. Employees working in ACCOUNTING department
```sql
SELECT ename
FROM employee
WHERE deptno = (
    SELECT deptno
    FROM department
    WHERE dname = 'ACCOUNTING'
);
```

## 9. Employees working in CHICAGO
```sql
SELECT ename
FROM employee
WHERE deptno = (
    SELECT deptno
    FROM department
    WHERE loc = 'CHICAGO'
);
```
### (Assuming loc column exists in department)

## 10. Job groups having total salary > max salary of managers
```sql
SELECT job, SUM(sal) AS total_salary
FROM employee
GROUP BY job
HAVING SUM(sal) > (
    SELECT MAX(sal)
    FROM employee
    WHERE job = 'MANAGER'
);
```
