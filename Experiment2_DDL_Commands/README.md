# Experiment 2: DDL Commands

# Name : RAJASHRI I

# Register Numbwe : 212224040261

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
```
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
```

```sql
-CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER REFERENCES Employees(EmployeeID),
ProjectID INTEGER REFERENCES Projects(ProjectID),
AssignmentDate DATE NOT NULL);
```

**Output:**

<img width="1233" height="342" alt="image" src="https://github.com/user-attachments/assets/9836226c-a8fb-479d-ace5-c33aed22f496" />


**Question 2**
---
```
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'
```

```sql
ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dept varchar(30);
```

**Output:**

<img width="1258" height="485" alt="image" src="https://github.com/user-attachments/assets/6f14476d-72dc-488d-b627-2b20320407f0" />


**Question 3**
---
```
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
```

```sql
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID));
```

**Output:**

<img width="1245" height="383" alt="image" src="https://github.com/user-attachments/assets/1f7631df-0de7-44a0-950d-561267027ca2" />


**Question 4**
---
```
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default
```

```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(104,'Tablet','Electronics',100,50);
```

**Output:**

<img width="1255" height="321" alt="image" src="https://github.com/user-attachments/assets/2dfa8987-b25e-4b1f-84f8-5194aeb4c054" />


**Question 5**
---
```
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME
```

```sql
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME);
```

**Output:**

<img width="1250" height="456" alt="image" src="https://github.com/user-attachments/assets/f8bdbe23-9cfa-4b64-b171-8c3b9d70e222" />


**Question 6**
---
```
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```

```sql
INSERT INTO Products(Name,Category,Price,Stock)
VALUES('Smartphone','Electronics',800,150);
INSERT INTO Products(Name,Category,Price,Stock)
VALUES('Headphones','Accessories',200,300);
```

**Output:**

<img width="1229" height="426" alt="image" src="https://github.com/user-attachments/assets/6eaebf4e-7322-488c-bab4-c57fa708ab84" />


**Question 7**
---
```
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT
```

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT);
```

**Output:**

<img width="1225" height="416" alt="image" src="https://github.com/user-attachments/assets/bbafbfff-9c54-4a14-9412-53e13716b265" />


**Question 8**
---
```
Write an SQL query to change the name of the column id to employee_id in the table employee.
```

```sql
ALTER TABLE employee RENAME COLUMN id TO employee_id;
```

**Output:**

<img width="1292" height="437" alt="image" src="https://github.com/user-attachments/assets/b9c93fdb-7842-45e6-883e-ed52f70235c1" />


**Question 9**
---
```
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001
```

```sql
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode)
VALUES
(302, 'Laura Croft', '456 Elm St' , 'Seattle' , 98101),
(303, 'Bruce Wayne', '789 Oak St', 'Gotham' , 10001);
```

**Output:**
<img width="1245" height="388" alt="image" src="https://github.com/user-attachments/assets/e1788c32-0993-4c61-bcd3-f195fc0e84c6" />


**Question 10**
---
```
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
```

```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID));
```

**Output:**

<img width="1242" height="418" alt="image" src="https://github.com/user-attachments/assets/dc19790f-4812-4f83-80f0-2b1ad0c6f35e" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
