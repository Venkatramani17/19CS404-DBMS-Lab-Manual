# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

How many prescriptions were written by each doctor?

Sample tablePrescriptions Table
```
SELECT DoctorID, COUNT(*)AS
TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```
**Output:**

![image](https://github.com/user-attachments/assets/c5ecb054-0dcb-4489-baa4-2b30c8238a73)

**Question 2**

How many patients are covered by each insurance company?

Sample table:Insurance Table

name type

InsuranceID INTEGER PatientID INTEGER InsuranceCompany TEXT PolicyNumber TEXT PolicyHolder TEXT ValidityPeriod TEXT

```
SELECT InsuranceCompany,
COUNT ( DISTINCT PatientID )AS
TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```
**Output:**

![image](https://github.com/user-attachments/assets/02784127-99c3-429f-ad06-d69b605a5c7b)

**Question 3**

How many patients are there in each city?

```
SELECT Address, COUNT(*)AS
TotalPatients
FROM Patients
GROUP BY Address;
```
**Output:**

![image](https://github.com/user-attachments/assets/38f989b2-c1f9-4278-8f02-1497e0eebb7a)


**Question 4**

Write a SQL query to find the minimum purchase amount.

Sample table: orders
![image](https://github.com/user-attachments/assets/b45b235a-cc86-420d-84ac-4c4a3aefb6d5)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
