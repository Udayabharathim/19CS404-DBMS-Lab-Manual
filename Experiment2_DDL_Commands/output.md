# AIM: 
To study and implement DDL commands and different types of constraints.

THEORY: 
1.CREATE: 
This is used to create a new relation (table) 
Syntax: 
CREATETABLE(field_1 data_type(size),field_2 data_type(size), .. . ); 
2.ALTER: 
This is used to add some extra fields into existing relation. 
Syntax: 
ALTERTABLErelation_name ADD(new field_1 data_type(size) ); 
(a)ALTERTABLE...ADD...: ALTERTABLEstdADD(AddressCHAR(10)); 
(b) ALTERTABLE...MODIFY...: ALTERTABLErelation_nameMODIFY(field_1 newdata_type(Size) 
(c) ALTERTABLE..DROP.... ALTERTABLErelation_nameDROPCOLUMN(field_name); 
(d) ALTERTABLE..RENAME...: 
ALTERTABLErelation_name RENAMECOLUMN(OLDfield_name) to(NEW field_name); 
3.DROP TABLE: 
This is used to delete the structure of a relation. It permanently deletes the records in the table. 
Syntax: 
DROPTABLErelation_name;

4.RENAME: 
It is used to modify the name of the existing database object. 
Syntax: 
RENAMETABLEold_relation_nameTOnew_relation_name; 
CONSTRAINTS: 
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE statement) or after the table is created (using ALTER TABLE statement). 
1.NOT NULL: 
When a column is defined as NOTNULL, then that column becomes a mandatory column. It implies that a value must be entered into the column if the record is to be accepted for storage in the table. 
Syntax:
CREATETABLETable_Name(column_namedata_type (size) NOT NULL, ); 
2.UNIQUE: 
The purpose of a unique key is to ensure that information in the column(s) is unique i.e. a value entered in column(s) defined in the unique constraint must not be repeated across the column(s). Atable may have many unique keys. 
Syntax: 
CREATETABLETable_Name(column_namedata_type(size)UNIQUE,….); 
3.CHECK:
Specifies a condition that each row in the table must satisfy. To satisfy the constraint, each row in the table must make the condition either TRUE or unknown (due to a null). 
Syntax: 
CREATE TABLE Table_Name(column_name data_type(size) CHECK(logical expression), ….); 


4.PRIMARY KEY: 
A field which is used to identify a record uniquely. A column or combination of columns can be created as primary key, which can be used as a reference from other tables. A table contains primary key is known as Master Table.
● It must uniquely identify each record in a table. 
● It must contain unique values. 
● It cannot be a null field. 
● It cannot be a multi port field. 
● It should contain a minimum number of fields necessary to be called unique.
Syntax: 
CREATETABLE Table_Name(column_name data_type(size) PRIMARY KEY, ….); 
5.FOREIGN KEY: 
It is a table level constraint. We cannot add this at column level. To reference any primary key column from other table this constraint can be used. The table in which the foreign key is defined is called a detail table. The table that defines the primary key and is referenced by the foreign key is called the master table. 
Syntax: 
CREATE TABLE  Table_Name(column_namedata_type(size)FOREIGN KEY(column_name) REFERENCEStable_name);
6.DEFAULT: 
The DEFAULT constraint is used to insert a default value into a column. The default value will be added to all new records, if no other value is specified. 
Syntax: 
CREATETABLE Table_Name(col_name1,col_name2,col_name3 DEFAULT ‘’);
Question 1:
Create a table named Department with the following constraints: 
•	DepartmentID as INTEGER should be the primary key. 
•	DepartmentName as TEXT should be unique and not NULL. 
•	Location as TEXT.

Answer:
CREATE TABLE Department(DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL, Location TEXT);
Output:
 
Question 2:
Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'.
Answer:
ALTER TABLE Employees ADD COLUMN Date_of_joining Date;
ALTER TABLE Employees RENAME job_title to Designation;
Output:
 
Question 3:
Insert the following customers into the Customers table:
CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

Answer:
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode) VALUES(302, "Laura Croft", "456 Elm St", "Seattle", 98101);
INSERT INTO Customers VALUES(303, "Bruce Wayne", "789 Oak St", "Gotham", 10001);
Output:
 
Question 4:
Create a table named Bonuses with the following constraints:
•	BonusID as INTEGER should be the primary key.
•	EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
•	BonusAmount as REAL should be greater than 0.
•	BonusDate as DATE.
•	Reason as TEXT should not be NULL.
Answer:
CREATE TABLE Bonuses(BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER, BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID));

Output:
 
Question 5:
Insert all employees from Former_employees into Employee
Table attributes are EmployeeID, Name, Department, Salary
Answer:
INSERT INTO Employee
SELECT * FROM Former_employees
Output:
 
Question 6:
Create a table named Shipments with the following constraints:
•	ShipmentID as INTEGER should be the primary key.
•	ShipmentDate as DATE.
•	SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
•	OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
Answer:
CREATE TABLE Shipments(ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE, SupplierID INTEGER, OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
Output:
 
Question 7:
Create a table named Invoices with the following constraints:
•	InvoiceID as INTEGER should be the primary key.
•	InvoiceDate as DATE.
•	Amount as REAL should be greater than 0.
•	DueDate as DATE should be greater than the InvoiceDate.
•	OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
Answer:
CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE, Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(DueDate>InvoiceDate), OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
Output:
 

Question 8:
Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

Answer:
ALTER TABLE employee ADD COLUMN first_name varchar(50);
ALTER TABLE employee ADD COLUMN last_name varchar(50);


Output:
 
Question 9:
Create a table named Events with the following columns:
•	EventID as INTEGER
•	EventName as TEXT
•	EventDate as DATE

Answer:
CREATE TABLE Events(EventID INTEGER, EventName TEXT,
EventDate DATE);
Question 10:
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

Answer:
INSERT INTO Student_details
(RollNo,Name,Gender,Subject,MARKS)
VALUES(201, "David Lee", "M", "Physics", 92);

Output:


















RESULT:
Thus the SQL queries to implement different types of constraints and DDL commands have been executed successfully.


