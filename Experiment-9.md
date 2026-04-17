# SQL Lab – Experiment 9

## Aim

To perform SQL queries using subqueries, ANY, ALL, and aggregate functions.

---

## Question 1

Display the name of employee who earns highest salary.

### Query

```sql
SELECT ename
FROM EMPLOYEE
WHERE sal = (SELECT MAX(sal) FROM EMPLOYEE);
```

---

## Question 2

Display empno and name of clerk earning highest salary among clerks.

### Query

```sql
SELECT empno, ename
FROM EMPLOYEE
WHERE job = 'CLERK'
AND sal = (SELECT MAX(sal) FROM EMPLOYEE WHERE job = 'CLERK');
```

---

## Question 3

Display the names of the salesman who earns more than highest clerk salary.

### Query

```sql
SELECT ename
FROM EMPLOYEE
WHERE job = 'SALESMAN'
AND sal > (SELECT MAX(sal) FROM EMPLOYEE WHERE job = 'CLERK');
```

---

## Question 4

Display clerks earning more than JAMES and less than SCOTT.

### Query

```sql
SELECT ename
FROM EMPLOYEE
WHERE job = 'CLERK'
AND sal > (SELECT sal FROM EMPLOYEE WHERE ename = 'JAMES')
AND sal < (SELECT sal FROM EMPLOYEE WHERE ename = 'SCOTT');
```

---

## Question 5

Display employees earning more than JAMES or more than SCOTT.

### Query

```sql
SELECT ename
FROM EMPLOYEE
WHERE sal > (SELECT sal FROM EMPLOYEE WHERE ename = 'JAMES')
OR sal > (SELECT sal FROM EMPLOYEE WHERE ename = 'SCOTT');
```

---

## Question 6

Display employees earning highest salary in their departments.

### Query

```sql
SELECT ename, deptno, sal
FROM EMPLOYEE e
WHERE sal = (
    SELECT MAX(sal)
    FROM EMPLOYEE
    WHERE deptno = e.deptno
);
```

---

## Question 7

Display employees earning highest salary in their job groups.

### Query

```sql
SELECT ename, job, sal
FROM EMPLOYEE e
WHERE sal = (
    SELECT MAX(sal)
    FROM EMPLOYEE
    WHERE job = e.job
);
```

---

## Question 8

Display employees working in ACCOUNTING department.

### Query

```sql
SELECT e.ename
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE d.dname = 'ACCOUNTING';
```

---

## Question 9

Display employees working in CHICAGO.

### Query

```sql
SELECT e.ename
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE d.location = 'CHICAGO';
```

---

## Question 10

Display job groups having total salary greater than max salary of managers.

### Query

```sql
SELECT job, SUM(sal) AS total_sal
FROM EMPLOYEE
GROUP BY job
HAVING SUM(sal) > (
    SELECT MAX(sal)
    FROM EMPLOYEE
    WHERE job = 'MANAGER'
);
```

---

## Conclusion

Successfully executed SQL queries using subqueries and aggregate functions.
