# Date & Special Function Queries (Using EMPLOYEE Table)

---

## 1. Display empno, ename, deptno. Instead of deptno display department name (Using CASE instead of DECODE)

### Query
```sql
SELECT EMPNO, ENAME,
CASE DEPTNO
    WHEN 10 THEN 'RESEARCH'
    WHEN 20 THEN 'ACCOUNTING'
    WHEN 30 THEN 'SALES'
    WHEN 40 THEN 'OPERATIONS'
END AS DEPARTMENT_NAME
FROM EMPLOYEE;
```

---

## 2. Display your age in days

### Query
```sql
SELECT DATEDIFF(CURDATE(), '2005-10-26') AS AGE_IN_DAYS;
```

---

## 3. Display your age in months

### Query
```sql
SELECT TIMESTAMPDIFF(MONTH, '2005-10-26', CURDATE()) AS AGE_IN_MONTHS;
```

---

## 4. Display the current date in formatted style

### Query
```sql
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS FORMATTED_DATE;
```

---

## 5 & 6. Display sentence format for each employee

Example Output:
Scott has joined the company on Wednesday 13th August 1990

### Query
```sql
SELECT CONCAT(
ENAME, 
' has joined the company on ',
DATE_FORMAT(HIREDATE, '%W %D %M %Y')
) AS EMPLOYEE_INFO
FROM EMPLOYEE;
```

---

## 7. Find the nearest Saturday after current date

### Query
```sql
SELECT DATE_ADD(CURDATE(), 
INTERVAL (7 - DAYOFWEEK(CURDATE())) DAY) AS NEXT_SATURDAY;
```

---

## 8. Display current time

### Query
```sql
SELECT CURTIME() AS CURRENT_TIME;
```

---

## 9. Display date three months before current date

### Query
```sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS THREE_MONTHS_BEFORE;
```

---

## 10. Display employees who joined in the month of December

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE MONTH(HIREDATE) = 12;
```

---

## 11. Display employees whose first 2 characters from hiredate match last 2 digits of salary

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE RIGHT(SAL,2) = LEFT(DATE_FORMAT(HIREDATE,'%y'),2);
```

---

## 12. Display employees whose 10% of salary equals year of joining

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE (SAL * 0.10) = YEAR(HIREDATE);
```

---

## 13. Display employees who joined before 15 months from today

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < DATE_SUB(CURDATE(), INTERVAL 15 MONTH);
```

---

## 14. Display employees who joined before 15th of the month

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE DAY(HIREDATE) < 15;
```

---

## 15. Display employees whose joining year equals deptno

### Query
```sql
SELECT *
FROM EMPLOYEE
WHERE YEAR(HIREDATE) = DEPTNO;
```

---

## Result
All date and special function queries executed successfully in MySQL (XAMPP).