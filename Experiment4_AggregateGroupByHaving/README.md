# Experiment 4: Aggregate Functions, Group By and Having Clause

## NAME : YUVARAJ M
## REG NO : 212224040377


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
--
What is the total number of appointments scheduled by each doctor?
Sample table:Appointments Table

```sql
select DoctorID , count(*) AS TotalAppointments
from Appointments
group by DoctorID
```

**Output:**

<img width="603" height="507" alt="image" src="https://github.com/user-attachments/assets/8d9961a7-dd14-489f-8df9-11b4fa2f265b" />


**Question 2**
---
How many doctors specialize in each medical specialty?
Sample table:Doctors Table

```sql
select specialty, count(*) AS TotalDocto
from Doctors 
group by specialty
```

**Output:**

<img width="638" height="582" alt="image" src="https://github.com/user-attachments/assets/aabd1086-d925-48a6-8f71-dde7a2db3dbb" />

**Question 3**
---
How many medical records are there for each patient?

```sql
select patientID, count(*) AS TotalRecords
from MedicalRecords
group by patientID
```

**Output:**

<img width="534" height="534" alt="image" src="https://github.com/user-attachments/assets/6188d4a9-183a-4871-802e-66488c39d6d0" />


**Question 4**
---
```
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```

```sql
select avg(length(email)) as avg_email_length_below_30
from customer
where city = 'Mumbai'
```

**Output:**

<img width="587" height="307" alt="image" src="https://github.com/user-attachments/assets/97564ecc-3cc7-438e-98a7-6e95754e33a7" />


**Question 5**
---
```
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.
Note: Inventory attribute contains amount of fruits
Table: fruits
name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 
```

```sql
select sum(inventory) as total
from fruits
where unit = 'LB'

```

**Output:**

<img width="430" height="316" alt="image" src="https://github.com/user-attachments/assets/12f229ee-2b6c-4363-998f-6ceec9190487" />


**Question 6**
---
```
Write a SQL query to find the minimum purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```

```sql
select min(purch_amt) as MINIMUM
from orders
```

**Output:**

<img width="375" height="311" alt="image" src="https://github.com/user-attachments/assets/f077f043-dd65-4c66-a7d5-49d8d15ae5a1" />

**Question 7**
---
```
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```

```sql
select sum(purch_amt) as TOTAL
from orders

```

**Output:**

<img width="293" height="318" alt="image" src="https://github.com/user-attachments/assets/3c499b99-a421-470e-a204-226cf130f5d7" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.
Sample table: employee

```sql
select age, min(income) AS 'MIN(income)'
from employee
group by age
having min(income) < 400000
```

**Output:**

<img width="691" height="424" alt="image" src="https://github.com/user-attachments/assets/bc6e9298-461f-4365-9c7a-689d5cbd3c6d" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.
Sample table: employee1

```sql
select jdate,avg(workhour) as 'AVG(workhour)'
from employee1
group by jdate
having avg(workhour) < 10
```

**Output:**

<img width="534" height="338" alt="image" src="https://github.com/user-attachments/assets/0c627839-a819-42c2-8e65-406e086ae1bf" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.
Sample table: employee

```sql
select city, sum(income) as Income
from employee
group by city
having sum(income) > 200000
```

**Output:**

<img width="479" height="469" alt="image" src="https://github.com/user-attachments/assets/889dc298-07c7-4cb7-9c3f-55346f1d986c" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
