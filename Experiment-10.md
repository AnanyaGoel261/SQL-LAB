# SQL Lab – Experiment 10

## Aim

To perform SQL queries using subqueries, ANY, ALL, and joins involving employee and manager relationships.

---

## Question 1

Display employees from dept 10 earning more than ANY employee in other departments.

### Query

```sql id="7t9a9q"
SELECT ename
FROM EMPLOYEE
WHERE deptno = 10
AND sal > ANY (
    SELECT sal FROM EMPLOYEE WHERE deptno <> 10
);
```

---

## Question 2

Display employees from dept 10 earning more than ALL employees in other departments.

### Query

```sql id="8dxmbd"
SELECT ename
FROM EMPLOYEE
WHERE deptno = 10
AND sal > ALL (
    SELECT sal FROM EMPLOYEE WHERE deptno <> 10
);
```

---

## Question 3

Display employees in SALES dept with grade 3.

### Query

```sql id="fsj92b"
SELECT e.*
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
JOIN SALGRADE s ON e.sal BETWEEN s.losal AND s.hisal
WHERE d.dname = 'SALES' AND s.grade = 3;
```

---

## Question 4

Display employees who are not managers.

### Query

```sql id="9lq6m2"
SELECT ename
FROM EMPLOYEE
WHERE job <> 'MANAGER';
```

---

## Question 5

Display employees whose manager is JONES.

### Query

```sql id="mzzr0w"
SELECT e.ename
FROM EMPLOYEE e
JOIN EMPLOYEE m ON e.mgr = m.empno
WHERE m.ename = 'JONES';
```

---

## Question 6

Display employees working in SALES department.

### Query

```sql id="g9s1s8"
SELECT e.ename
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE d.dname = 'SALES';
```

---

## Question 7

Display employee name, dept name, salary and commission for those earning between 2000 and 5000 and working in CHICAGO.

### Query

```sql id="ykc3t1"
SELECT e.ename, d.dname, e.sal, e.comm
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.deptno = d.deptno
WHERE e.sal BETWEEN 2000 AND 5000
AND d.location = 'CHICAGO';
```

---

## Question 8

Display employees whose salary is greater than their manager’s salary.

### Query

```sql id="g3fqmx"
SELECT e.ename
FROM EMPLOYEE e
JOIN EMPLOYEE m ON e.mgr = m.empno
WHERE e.sal > m.sal;
```

---

## Question 9

Display employees working in the same department as their manager.

### Query

```sql id="8ckw1l"
SELECT e.ename
FROM EMPLOYEE e
JOIN EMPLOYEE m ON e.mgr = m.empno
WHERE e.deptno = m.deptno;
```

---

## Conclusion

Successfully performed SQL queries using subqueries, joins, and relational comparisons.
