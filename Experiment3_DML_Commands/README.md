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
-- Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
-- update products set availability=2*availability where product_id=1;
```

**Output:**

![image](https://github.com/user-attachments/assets/3bb9ba82-a274-41d9-b19f-6debf7f30bd2)

**Question 2**
---
-- Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
-- update suppliers set supplier_name='A1 Suppliers' where supplier_id=8;
```

**Output:**

![image](https://github.com/user-attachments/assets/a3964af3-33a9-4c38-b494-41050fe62af6)

**Question 3**
---
-- Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

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

```sql
-- update Employees set email='not available',commission_pct=0.55 where department_id=110;
```

**Output:**

![image](https://github.com/user-attachments/assets/f58d4c73-b50b-419a-a0ca-42efaa243cae)

**Question 4**
---
-- Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

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

```sql
-- update Employees set salary=salary+500,email='updated' where job_id='SA_REP' and commission_pct>0.15;
```

**Output:**

![image](https://github.com/user-attachments/assets/dd6da570-e5ab-4ada-8135-1cbf457e9ef9)

**Question 5**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
-- delete from Customer where CUST_COUNTRY not in('India','USA');
```

**Output:**

![image](https://github.com/user-attachments/assets/133b8fc0-4252-4f0a-8a1a-d235d2310e2b)

**Question 6**
---
-- Write a SQL query to Delete a Specific Surgery whose ID is 3

```sql
-- delete from Surgeries where surgery_id=3;
```

**Output:**

![image](https://github.com/user-attachments/assets/99b7e2b2-b9a2-48a0-b471-b050518a19fb)

**Question 7**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

```sql
-- delete from Customer where GRADE<2;
```

**Output:**

![image](https://github.com/user-attachments/assets/4a68caa1-f1e8-498e-a09d-14291831bce9)

**Question 8**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

```sql
-- delete from Customer where GRADE>=2;
```

**Output:**

![image](https://github.com/user-attachments/assets/a79f43f4-e931-4dad-8dbd-75d74588a14d)

**Question 9**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
-- delete from Customer where CUST_CITY<>'New York' and OUTSTANDING_AMT>5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/e8599715-52d7-46f6-a102-e10530834595)

**Question 10**
---
-- 1.    Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
-- select * from customer where grade>100; 
```

**Output:**

![image](https://github.com/user-attachments/assets/eb757446-0578-4807-b44e-8c9ad74bb284)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
