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
-- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
-- ALTER TABLE Companies ADD COLUMN designation varchar(50);
ALTER TABLE Companies ADD COLUMN net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/6bf5bb88-9241-4cc5-aac1-309c4ee55a04)


**Question 2**
---
-- Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
-- CREATE TABLE Events(EventID INTEGER,EventName TEXT,EventDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/45d7272c-8c14-480e-a55c-f8f9c4358fb4)


**Question 3**
---
-- Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
-- CREATE TABLE item(item_id TEXT PRIMARY KEY,item_desc TEXT,rate INTEGER,icom_id TEXT(4),FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE SET NULL ON DELETE SET NULL);
```

**Output:**

![image](https://github.com/user-attachments/assets/97b35b1a-1de8-4142-8c32-aa8c5615647c)

**Question 4**
---
-- Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
-- CREATE TABLE Orders(OrderID INTEGER PRIMARY KEY,OrderDate DATE NOT NULL,CustomerID INTEGER,FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));
```

**Output:**

![image](https://github.com/user-attachments/assets/9edeff25-8169-42e2-8f88-6febdf96f126)

**Question 5**
---
-- Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
-- ALTER TABLE Student_details ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details ADD COLUMN Adhar_Number number;
```

**Output:**

![image](https://github.com/user-attachments/assets/b69f0725-af81-4289-812e-9529213aa084)

**Question 6**
---
-- Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
-- CREATE TABLE products(product_id INTEGER PRIMARY KEY,product_name TEXT NOT NULL,list_price DECIMAL(10,2) NOT NULL CHECK(list_price>=0),discount DECIMAL(10,2) NOT NULL DEFAULT 0 CHECK(discount>=0),check(list_price>=discount));
```

**Output:**

![image](https://github.com/user-attachments/assets/8b49bb1c-1bb7-46bf-933d-fe2a129a7817)

**Question 7**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- CREATE TABLE Products(ProductID INTEGER PRIMARY KEY,ProductName TEXT UNIQUE NOT NULL,Price REAL check(Price>0),StockQuantity INTEGER check(StockQuantity>0));
```

**Output:**

![image](https://github.com/user-attachments/assets/35a7563e-29ad-458b-82c7-111194adb41d)

**Question 8**
---
-- Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

```sql
-- INSERT INTO Student_details(RollNo,Name,Gender)VALUES(204,'Samuel Black','M');
```

**Output:**

![image](https://github.com/user-attachments/assets/cd4ea076-d468-4d5c-a261-68bf93d899b5)

**Question 9**
---
-- Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
-- INSERT INTO Books(ISBN, Title, Author, Publisher, YearPublished) select * from Out_of_print_books;
```

**Output:**

![image](https://github.com/user-attachments/assets/134a6ce4-3f60-4c6a-8a14-7a81c112c726)

**Question 10**
---
-- Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000
 

```sql
-- INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY)VALUES(1,'Ramesh',32,'Ahmedabad',2000),(2,'Khilan',25,'Delhi',1500),(3,'Kaushik',23,'Kota',2000);
```

**Output:**

![image](https://github.com/user-attachments/assets/ae7d0558-88f3-4a40-b908-143e41583c00)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
