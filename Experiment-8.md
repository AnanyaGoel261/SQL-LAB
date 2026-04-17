# SQL Lab – Experiment 8

## Aim

To perform SQL queries using JOIN, subqueries, and aggregate functions on EMPLOYEE, DEPARTMENT, and SALGRADE tables.

---

## Question 1

Display all employees with their department name.

### Query

```sql
SELECT e.ename, d.dname
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno;
```

### Output

| ename | dname      |
| ----- | ---------- |
| SMITH | ACCOUNTING |
| ALLEN | SALES      |
| ...   | ...        |

---

## Question 2

Display employees whose manager is JONES along with manager name.

### Query

```sql
SELECT e.ename AS employee, m.ename AS manager
FROM EMPLOYEE e
JOIN EMPLOYEE m ON e.mgr = m.empno
WHERE m.ename = 'JONES';
```

### Output

| employee | manager |
| -------- | ------- |
| SCOTT    | JONES   |
| FORD     | JONES   |

---

## Question 3

Display employee details with job, department, manager, and grade.

### Query

```sql
SELECT e.ename, e.job, d.dname, m.ename AS manager, s.grade
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
LEFT JOIN EMPLOYEE m ON e.mgr = m.empno
JOIN SALGRADE s ON e.sal BETWEEN s.losal AND s.hisal;
```

### Output

| ename | job   | dname      | manager | grade |
| ----- | ----- | ---------- | ------- | ----- |
| SMITH | CLERK | ACCOUNTING | FORD    | 1     |

---

## Question 4

List employees except CLERK with salary, grade, and department sorted by highest salary.

### Query

```sql
SELECT e.ename, e.job, e.sal, s.grade, d.dname
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
JOIN SALGRADE s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.job <> 'CLERK'
ORDER BY e.sal DESC;
```

### Output

| ename | job       | sal  | grade | dname      |
| ----- | --------- | ---- | ----- | ---------- |
| KING  | PRESIDENT | 5000 | 5     | ACCOUNTING |

---

## Question 5

Display employee name, job, and manager (including no manager).

### Query

```sql
SELECT e.ename, e.job, m.ename AS manager
FROM EMPLOYEE e
LEFT JOIN EMPLOYEE m ON e.mgr = m.empno;
```

### Output

| ename | job       | manager |
| ----- | --------- | ------- |
| KING  | PRESIDENT | NULL    |

---

## Question 6

Employees earning 36000 annually OR not clerks.

### Query

```sql
SELECT e.ename, e.job, (e.sal*12) AS annual_sal, d.dname
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE (e.sal*12) = 36000 OR e.job <> 'CLERK';
```

---

## Question 7

Employees earning 30000 annually AND not clerks.

### Query

```sql
SELECT e.ename, e.job, (e.sal*12) AS annual_sal, d.dname
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE (e.sal*12) = 30000 AND e.job <> 'CLERK';
```

---

## Question 8

Display employee and manager details with “NO MANAGER”.

### Query

```sql
SELECT e.empno, e.ename,
IFNULL(m.empno, 'NO MANAGER') AS mgr_no,
IFNULL(m.ename, 'NO MANAGER') AS mgr_name
FROM EMPLOYEE e
LEFT JOIN EMPLOYEE m ON e.mgr = m.empno;
```

---

## Question 9

Display department name, number, and total salary.

### Query

```sql
SELECT d.deptno, d.dname, SUM(e.sal) AS total_sal
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
GROUP BY d.deptno, d.dname;
```

---

## Question 10

Display employee number, name, and department location.

### Query

```sql
SELECT e.empno, e.ename, d.location
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno;
```

---

## Question 11

Display employee name with department name.

### Query

```sql
SELECT e.ename, d.dname
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno;
```

---

## Result

Successfully performed SQL queries using joins, subqueries, and aggregate functions and documented them using Markdown format.
