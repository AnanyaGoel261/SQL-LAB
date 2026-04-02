# More Retrieving & Update Queries (Using EMPLOYEE Table)

---

## 1. Display the list of employees who joined before 30-June-1980 or after 31-Dec-1981

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
OR HIREDATE > '1981-12-31';
```

---

## 2. Display the names of employees whose names have second alphabet A

### Query
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

---

## 3. Display the names of employees whose name is exactly five characters in length

### Query
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;
```

---

## 4. Display the names of employees whose names have second alphabet A

### Query
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

---

## 5. Display the names of employees who are not working as salesman or clerk or analyst

### Query
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

---

## 6. Display the name of the employee along with their annual salary (sal*12). Highest salary first.

### Query
```sql
SELECT ENAME, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY SAL DESC;
```

---

## 7. Display name, sal, hra, pf, da, totalsal for each employee

### Query
```sql
SELECT 
ENAME,
SAL,
(SAL * 0.15) AS HRA,
(SAL * 0.10) AS DA,
(SAL * 0.05) AS PF,
((SAL + (SAL * 0.15) + (SAL * 0.10)) - (SAL * 0.05)) AS TOTALSAL
FROM EMPLOYEE
ORDER BY TOTALSAL;
```

---

## 8. Update the salary of each employee by 10% increment who are not eligible for commission

### Query
```sql
UPDATE EMPLOYEE
SET SAL = SAL + (SAL * 0.10)
WHERE COMM IS NULL OR COMM = 0;
```

---

## 9. Display those employees whose salary is more than 3000 after giving 20% increment

### Query
```sql
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE (SAL + (SAL * 0.20)) > 3000;
```

---

## 10. Display those employees whose salary contains at least 3 digits

### Query
```sql
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL >= 100;
```

---

## Result
All queries executed successfully in XAMPP.