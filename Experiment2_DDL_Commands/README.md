# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
ALTER TABLE customer ADD birth_date timestamp;
```

**Output:**
<img width="687" height="166" alt="Screenshot 2026-11-25 152333" src="https://github.com/user-attachments/assets/926195d8-5267-46c6-b7aa-1d2b5c87dbaa" />


**Question 2**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```sql
CREATE TABLE Invoices (
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK (Amount> 0),
DueDate DATE CHECK (DueDate > InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);



```

**Output:**

<img width="422" height="101" alt="Screenshot 2026-11-25 152529" src="https://github.com/user-attachments/assets/5b12eda3-60d0-4639-8fbd-bde9ae75569f" />



**Question 3**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
);
```

**Output:**
<img width="376" height="102" alt="Screenshot 2026-11-25 152700" src="https://github.com/user-attachments/assets/acf00fee-1fd9-4a29-9553-2f51c95cbfa6" />


**Question 4**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO Student_details (RollNo,Name,Gender,Subject,MARKS) VALUES(201,'David Lee','M','Physics','92');
```

**Output:**

<img width="430" height="70" alt="Screenshot 2026-11-25 152753" src="https://github.com/user-attachments/assets/1760d27c-dc22-4e2f-aaa7-40b93a54c3fc" />



**Question 5**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.


```sql
CREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="431" height="106" alt="Screenshot 2026-11-25 152855" src="https://github.com/user-attachments/assets/9e216a9f-80c5-417b-9f48-9a24e685950c" />



**Question 6**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science


```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (205, 'Olivia Green', 'F', NULL, NULL);

INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (207, 'Liam Smith', 'M', 'Mathematics', 85);

INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (208, 'Sophia Johnson', 'F', 'Science', NULL);
```

**Output:**


<img width="447" height="110" alt="Screenshot 2026-11-25 153017" src="https://github.com/user-attachments/assets/6bf4eed6-33cf-4638-8e25-95d9184befb0" />


**Question 7**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

```sql
ALTER TABLE books ADD ISBN varchar(30);
ALTER TABLE books ADD domain_dept varchar(30);
```

**Output:**

<img width="510" height="190" alt="Screenshot 2026-11-25 153131" src="https://github.com/user-attachments/assets/80b3c6dd-2c09-4558-9f53-4d9ec82d8b8c" />



**Question 8**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="385" height="107" alt="Screenshot 2026-11-25 153426" src="https://github.com/user-attachments/assets/387e52fe-75a4-40a2-9aab-21a91fe268ab" />




**Question 9**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql

CREATE TABLE Employees (
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);

```

**Output:**

<img width="451" height="122" alt="Screenshot 2026-11-25 153619" src="https://github.com/user-attachments/assets/ac5e9e8d-7fca-4c2c-9027-a7c0732161bd" />




**Question 10**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books
SELECT * FROM Out_of_print_books;
```

**Output:**


<img width="593" height="106" alt="Screenshot 2026-11-25 153702" src="https://github.com/user-attachments/assets/436b9bad-d608-4632-8cb7-ef7e32dcaa02" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
