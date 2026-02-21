# DBMS LAB

---

## Experiment 01 – Create Department & Employee Table

### Create Database
```sql
CREATE DATABASE 2cse19_1489;
SHOW DATABASES;
USE 2cse19_1489;
```

### Create Department Table
```sql
CREATE TABLE Department(
    DEPTNO INT PRIMARY KEY,
    DNAME VARCHAR(50) NOT NULL
);

INSERT INTO Department VALUES
(10,'RESEARCH'),
(20,'ACCOUNTING'),
(30,'SALES'),
(40,'OPERATIONS');

SELECT * FROM Department;
```

### Create Employee Table
```sql
CREATE TABLE Employee(
    EMPNO INT PRIMARY KEY,
    ENAME VARCHAR(20) NOT NULL,
    JOB VARCHAR(20),
    MGR INT,
    HIREDATE DATE,
    SAL INT,
    COMM INT,
    DEPTNO INT,
    FOREIGN KEY (DEPTNO) REFERENCES Department(DEPTNO)
);
```

### Insert Records
```sql
INSERT INTO Employee VALUES
(7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20),
(7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30),
(7521,'WARD','SALESMAN',7698,'1981-02-22',1250,500,30),
(7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20),
(7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30),
(7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30),
(7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10),
(7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20),
(7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10),
(7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30),
(7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20),
(7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30),
(7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20),
(7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);

SELECT * FROM Employee;
```

---

## Experiment 02 – Queries

### 1. List all distinct jobs
```sql
SELECT DISTINCT JOB FROM Employee;
```

### 2. Employees in dept 30
```sql
SELECT * FROM Employee
WHERE DEPTNO = 30;
```

### 3. Department number > 20
```sql
SELECT DEPTNO, DNAME FROM Department
WHERE DEPTNO > 20;
```

### 4. Managers and Clerks in dept 30
```sql
SELECT * FROM Employee
WHERE DEPTNO = 30
AND JOB IN ('MANAGER','CLERK');
```

### 5. Employee name, number & dept of all clerks
```sql
SELECT ENAME, EMPNO, DEPTNO FROM Employee
WHERE JOB = 'CLERK';
```

### 6. Managers not in dept 30
```sql
SELECT * FROM Employee
WHERE JOB='MANAGER'
AND DEPTNO <> 30;
```

### 7. Employees in dept 10 not manager/clerk
```sql
SELECT * FROM Employee
WHERE DEPTNO=10
AND JOB NOT IN ('MANAGER','CLERK');
```

### 8. Employees earning between 1200 and 1400
```sql
SELECT ENAME, JOB FROM Employee
WHERE SAL BETWEEN 1200 AND 1400;
```

### 9. Name & dept of clerk, analyst & salesman
```sql
SELECT ENAME, DEPTNO FROM Employee
WHERE JOB IN ('CLERK','ANALYST','SALESMAN');
```

### 10. Names starting with M
```sql
SELECT ENAME, DEPTNO FROM Employee
WHERE ENAME LIKE 'M%';
```
