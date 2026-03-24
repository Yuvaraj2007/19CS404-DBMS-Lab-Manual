# Experiment 2: DDL Commands

## NAME : YUVARAJ M
## REG NO : 212224040377
# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

```sql
UPDATE Products SET reorder_lvl = 20 
WHERE quantity < 10 AND category = 'Snacks'
```

**Output:**
<img width="926" height="355" alt="image" src="https://github.com/user-attachments/assets/7473665a-cb31-44ee-91c9-cd10bff37634" />


**Question 2**
---
```
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

```sql
UPDATE Employees 
SET email = 'Unavailable'

```

**Output:**

<img width="768" height="229" alt="image" src="https://github.com/user-attachments/assets/6ad5c43a-186a-4f0d-b8bb-39274a8a0600" />

**Question 3**
---
```
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.
PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```

```sql
UPDATE PRODUCTS 
SET reorder_lvl = 40 
WHERE category = 'Grocery'
```

**Output:**

<img width="932" height="282" alt="image" src="https://github.com/user-attachments/assets/60eaafdc-771d-41ad-ac6c-5f3b9aef0169" />


**Question 4**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.
sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id =15 AND sale_date = '2023-01-31'
```

**Output:**

<img width="928" height="289" alt="image" src="https://github.com/user-attachments/assets/e2b88db2-96c7-4316-ae12-7c4769c4beea" />


**Question 5**
---
```
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

```sql
UPDATE Employees 
SET salary = salary + 500, email='updated'
WHERE job_id = "SA_REP" AND commission_pct > 0.15
```

**Output:**

<img width="937" height="334" alt="image" src="https://github.com/user-attachments/assets/1c36ac0c-c272-48fa-af76-45babf662867" />


**Question 6**

````
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

````

```sql
delete from customer
where grade >2 AND payment_amt<(select avg(payment_amt) from customer) OR outstanding_amt>8000
```

**Output:**

<img width="927" height="418" alt="image" src="https://github.com/user-attachments/assets/30622531-eefc-49f2-a8cd-8c1f86be3ee0" />


**Question 7**
---
```
Write a SQL query to Select all patients who were admitted for one day.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT
```

```sql
SELECT 
   patient_id,
   first_name,
   admission_date,
   discharge_date
FROM Patients
WHERE admission_date = discharge_date
```

**Output:**

<img width="716" height="220" alt="image" src="https://github.com/user-attachments/assets/de69cc38-2c3d-4d15-b04d-633d68172afd" />

**Question 8**
---
```
Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```

```sql
select id,
value1,
CASE 
when value1%2==0 THEN 'Even'
ELSE 'Odd'
end as parity
from Calculations
```

**Output:**

<img width="485" height="286" alt="image" src="https://github.com/user-attachments/assets/3c9188eb-0957-4db5-b9a0-dc8493977a28" />


**Question 9**
---
```
Write a SQL query to round the decimal column to 3 decimal places from the Calculations table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```

```sql
select id,ROUND(decimal,3) AS rounded_value
from Calculations
```

**Output:**

<img width="389" height="193" alt="image" src="https://github.com/user-attachments/assets/5551a30e-5bf8-44a7-86cd-dd5f91247135" />


**Question 10**
---
```
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.

Sample table: Products

product_id | discounted_price | discount_percentage
 ------------+------------------+---------------------
 101        | 45.00           | 0.10 

 102        | 63.75           | 0.15 

 103        | 80.00           | 0.20
```

```sql
select 
product_id,
discounted_price,
discount_percentage,
discounted_price/(1-discount_percentage) AS original_price
from Products

```

**Output:**

<img width="732" height="174" alt="image" src="https://github.com/user-attachments/assets/17a714a7-223d-4a31-90f7-f55e8162ff63" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

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
Create a table named Departments with the following columns:DepartmentID as INTEGER,DepartmentName as TEXT

```sql
  CREATE TABLE Departments(
   DepartmentID INTEGER,
   DepartmentName TEXT);
```

**Output:**

<img width="871" height="258" alt="image" src="https://github.com/user-attachments/assets/966167f8-f6be-4c33-83bb-55bc634c18fc" />


**Question 2**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
   CREATE TABLE item(
   item_id TEXT PRIMARY KEY,
   item_desc TEXT NOT NULL,
   rate INTEGER NOT NULL,
   icom_id TEXT CHECK(LENGTH(icom_id)=4),
    FOREIGN KEY(icom_id) REFERENCES company(com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
);
```

**Output:**

<img width="902" height="273" alt="image" src="https://github.com/user-attachments/assets/3bea9042-feb5-49b5-8369-8386b86acda1" />



**Question 3**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
ALTER TABLE customers
ADD column email TEXT
```

**Output:**

<img width="897" height="227" alt="image" src="https://github.com/user-attachments/assets/65106054-40ef-4f76-9572-05db0462aeca" />


**Question 4**
---
Insert all employees from Former_employees into Employee
Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee(EmployeeID ,Name ,Department ,Salary)
SELECT * FROM Former_employees
```

**Output:**

<img width="906" height="212" alt="image" src="https://github.com/user-attachments/assets/6048f28a-e71c-49ad-9758-faced8f2df20" />


**Question 5**
---
Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'

```sql
ALTER TABLE Employees 
ADD column Date_of_joining Date;
ALTER TABLE Employees
RENAME job_title to Designation;
```

**Output:**

<img width="905" height="270" alt="image" src="https://github.com/user-attachments/assets/99569cac-50db-49d4-8da6-76cd660142a4" />


**Question 6**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK (DueDate>InvoiceDate),
Amount REAL  CHECK(Amount>0)
);
```

**Output:**

<img width="915" height="220" alt="image" src="https://github.com/user-attachments/assets/026b6881-db74-4ab7-9f46-821445373eb6" />


**Question 7**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science

```sql
INSERT INTO student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(205,"Olivia Green",'F',NULL,NULL);
INSERT INTO student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(207,"Liam Smith","M","Mathematics",85);
INSERT INTO student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(208,"Sophia Johnson","F","Science",NULL);
```

**Output:**

<img width="928" height="233" alt="image" src="https://github.com/user-attachments/assets/6aae8954-9a82-4682-af65-be4148418781" />


**Question 8**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK (DueDate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="900" height="227" alt="image" src="https://github.com/user-attachments/assets/f4a4603b-b6d7-426d-842b-f58a43fa49de" />

**Question 9**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.


```sql
INSERT INTO  Products(ProductID,Name,Category,Price,Stock)
VALUES(101,"Laptop","Electronics",1500,50);
```

**Output:**

<img width="910" height="205" alt="image" src="https://github.com/user-attachments/assets/fa782c91-afa3-4e31-aae3-12bb7bcdb2f2" />

**Question 10**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT NOT NULL UNIQUE,
Location TEXT 
)
```

**Output:**

<img width="917" height="235" alt="image" src="https://github.com/user-attachments/assets/ee8f3abf-4ed2-4ff1-ba48-2064beb221e9" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
