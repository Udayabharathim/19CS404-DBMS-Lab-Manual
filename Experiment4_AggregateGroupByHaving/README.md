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
--
-- How many patients are there in each city?

```sql
-- select Address,count(*) as TotalPatients from Patients group by Address;
```

**Output:**

![image](https://github.com/user-attachments/assets/563fdfb0-c75a-48a4-9567-fcbf0226d731)

**Question 2**
---
-- How many medical records were created in each month?

```sql
-- SELECT Date,count(*) as TotalRecords from MedicalRecords group by Date;
```

**Output:**

![image](https://github.com/user-attachments/assets/273353b3-331f-4ec5-9499-4b3f4b4a471b)

**Question 3**
---
-- How many appointments are scheduled for each patient?

Sample table: Appointments Table

name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT

```sql
-- SELECT PatientID,COUNT(*) AS TotalAppointments from Appointments group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/ab14be11-eda9-4d04-a371-25530579aa34)

**Question 4**
---
-- Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
-- select name,max(income) as 'max(income)' from employee where city='California';
```

**Output:**

![image](https://github.com/user-attachments/assets/282175b2-68ef-41fe-984d-88ee5f16c669)

**Question 5**
---
-- Write a SQL query to find the number of employees whose age is greater than 32.

```sql
-- select count(*) as COUNT from employee where age>32;
```

**Output:**

![image](https://github.com/user-attachments/assets/c430cf54-401e-4678-9427-a528300c2c6d)

**Question 6**
---
-- Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

```sql
-- select count(distinct age) as COUNT from employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/f8b50084-3312-4b19-ac7b-e9a0c265f9b7)

**Question 7**
---
-- Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
-- select avg(length(email)) as avg_email_length from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/0680d0a5-08d7-4140-b1ac-b8afea321822)

**Question 8**
---
-- Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

```sql
-- select category_id,count(*) as 'count(product_name)' from products group by category_id having category_id<3;
```

**Output:**

![image](https://github.com/user-attachments/assets/c49823ee-b959-4736-9710-60e97450c619)

**Question 9**
---
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

```sql
-- select age,income as Income from employee group by age having min(income)<1000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/37c6c20e-ac7c-4c96-8b3d-f642b60eca78)

**Question 10**
---
-- Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.



```sql
--select category_id,count(*) as 'COUNT' from products group by category_id having category_id>2;
```

**Output:**

![image](https://github.com/user-attachments/assets/58306407-bc19-4db2-abf9-214150f5b7a2)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
