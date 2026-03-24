# Experiment 6: Joins

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
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1294" height="631" alt="image" src="https://github.com/user-attachments/assets/493cd13c-7cb8-4604-ace8-6012db719abb" />

```sql
SELECT p.*
FROM patients p, test_results t
WHERE p.patient_id = t.patient_id
  AND t.test_name IN ('Blood Test','Blood Pressure')
  AND t.result NOT LIKE '%Normal%';
```

**Output:**
<img width="1352" height="261" alt="image" src="https://github.com/user-attachments/assets/efbc8320-2432-4c69-8149-790d99577a64" />


**Question 2**
---
<img width="1349" height="465" alt="image" src="https://github.com/user-attachments/assets/46ec0e90-74c9-43cd-861c-091bb2f7316d" />


```sql
SELECT p.first_name AS patient_name, d.first_name AS doctor_name
FROM patients p
JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;

```

**Output:**

<img width="1362" height="251" alt="image" src="https://github.com/user-attachments/assets/84015a68-fb03-4e2c-8636-e8370ceb3099" />

**Question 3**
---
<img width="1353" height="546" alt="image" src="https://github.com/user-attachments/assets/462444e7-f3f6-4622-a81f-ce6c5544a609" />


```sql
SELECT c.cust_name AS "Customer Name", c.city AS "city",
       s.name AS "Salesman", s.city AS "city", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city AND s.commission > 0.12;

```

**Output:**

<img width="1360" height="383" alt="image" src="https://github.com/user-attachments/assets/641adbd8-4981-4b8e-b303-02268ef4b2d9" />


**Question 4**
---
<img width="1353" height="192" alt="image" src="https://github.com/user-attachments/assets/b98e17ba-55b7-4c36-b4d4-b779508f6573" />


```sql
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';

```

**Output:**

<img width="1366" height="251" alt="image" src="https://github.com/user-attachments/assets/f38f2e43-dc3f-4278-83f0-bf0acb74c969" />

**Question 5**
---
<img width="1350" height="554" alt="image" src="https://github.com/user-attachments/assets/ef3ad1b2-6dcf-4321-bcb1-569648896f7d" />


```sql
SELECT c.cust_name AS "Customer Name", c.city AS "city",
       s.name AS "Salesman", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="1361" height="474" alt="image" src="https://github.com/user-attachments/assets/252b4ddb-c4db-4181-b33a-6c5d380bdc8d" />


**Question 6**
---
<img width="1358" height="289" alt="image" src="https://github.com/user-attachments/assets/32d9cc7c-14d8-4c30-93c2-3c66535ac0f0" />

```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**
<img width="1359" height="518" alt="image" src="https://github.com/user-attachments/assets/edbf2a76-2039-4fbe-ae9b-dd9dc18bfdbe" />




**Question 7**
---
<img width="1372" height="594" alt="image" src="https://github.com/user-attachments/assets/90ee3d60-d79b-4fd7-8a29-fd76dfa497e5" />


```sql
SELECT a.cust_name, a.city, b.ord_no,
       b.ord_date, b.purch_amt AS "Order Amount", 
       c.name, c.commission 
-- Specifying the tables to retrieve data from ('customer' as 'a', 'orders' as 'b', and 'salesman' as 'c')
FROM customer a 
-- Performing a left outer join based on the customer_id, including unmatched rows from 'customer'
LEFT OUTER JOIN orders b 
ON a.customer_id = b.customer_id 
-- Performing another left outer join with the result of the previous join and the 'salesman' table based on salesman_id
LEFT OUTER JOIN salesman c 
ON c.salesman_id = b.salesman_id;
```

**Output:**

<img width="1366" height="740" alt="image" src="https://github.com/user-attachments/assets/0ab675f4-eb68-41cf-b2b5-6096c9f5426e" />

**Question 8**
---
<img width="1337" height="598" alt="image" src="https://github.com/user-attachments/assets/2616465e-d9f5-4ed6-8000-e86b346caba8" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1408" height="496" alt="image" src="https://github.com/user-attachments/assets/57bee1b2-4fc6-449a-82e4-2236051bc7bf" />

**Question 9**
---
<img width="1328" height="586" alt="image" src="https://github.com/user-attachments/assets/c6774075-45a3-4b05-b8da-241927faf332" />


```sql
SELECT a.cust_name, a.city, a.grade, 
       b.name AS "Salesman", b.city 
FROM customer a 
LEFT JOIN salesman b 
ON a.salesman_id = b.salesman_id 
ORDER BY a.customer_id;
```

**Output:**

<img width="1368" height="561" alt="image" src="https://github.com/user-attachments/assets/d0481b4b-1399-4515-be00-4f3a58530634" />


**Question 10**
---
<img width="1358" height="434" alt="image" src="https://github.com/user-attachments/assets/69916690-9fd3-4c36-90a1-84b6eac4bffe" />


```sql
SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM patients p
INNER JOIN test_results t 
    ON p.patient_id = t.patient_id;

```

**Output:**

<img width="1369" height="341" alt="image" src="https://github.com/user-attachments/assets/167ab83f-f348-45e6-97db-cb2ee621dd19" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
