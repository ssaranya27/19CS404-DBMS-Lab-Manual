# Experiment 2: DDL Commands

### Name: SARANYA S.
### Reg.No.: 212223220101

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
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

```
insert into Customers (CustomerID,Name,Address)
values(304,'Peter Parker','Spider St');
```

**Output:**

<img width="1186" height="398" alt="image" src="https://github.com/user-attachments/assets/f54661bb-9637-4831-82d3-790940c81cd3" />

**Question 2**
---
In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```
insert into Customers (CustomerID,Name,Address,City,ZipCode)
values(306,'Diana Prince','Themyscira',NULL,NULL);
insert into Customers (CustomerID,Name,Address,City,ZipCode)
values(307,'Bruce Wayne','Wayne Manor','Gotham',10007);
insert into Customers(CustomerID,Name,Address,City,ZipCode)
values(308,'Peter Parker','Queens',NULL,11375);
```

**Output:**

<img width="1223" height="274" alt="image" src="https://github.com/user-attachments/assets/3610e794-c90e-4463-88f2-b4c44267cbae" />

**Question 3**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```
create table Bonuses(
BonusID integer primary key,
EmployeeID integer,
BonusAmount real check (BonusAmount > 0),
BonusDate date,
Reason text not null,
foreign key (EmployeeID) references Employees(EmployeeID)
);
```

**Output:**

<img width="1311" height="177" alt="image" src="https://github.com/user-attachments/assets/44825cfd-0710-499c-9de7-e8c4643b0801" />

**Question 4**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```
insert into products(ProductID,ProductName,Price,Stock)
select ProductID,ProductName,Price,Stock
from Discontinued_products;
```

**Output:**

<img width="1098" height="259" alt="image" src="https://github.com/user-attachments/assets/9a6887f5-4b6f-47f4-a451-5ecce7dd602f" />

**Question 5**
---
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.


```
alter table Student_details add ParentsNumber number;
alter table Student_Details add Adhar_Number number;
```

**Output:**

<img width="1253" height="354" alt="image" src="https://github.com/user-attachments/assets/1c7b1edb-ad5c-4884-88ad-0b16a3625b47" />

**Question 6**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```
create table Products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**

<img width="1237" height="269" alt="image" src="https://github.com/user-attachments/assets/aa6407d8-ef0f-4991-9c00-07f22462bae8" />

**Question 7**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.


```
alter table Student_details add MobileNumber NUMBER;
alter table Student_details add Address VARCHAR(100);
```

**Output:**

<img width="1237" height="348" alt="image" src="https://github.com/user-attachments/assets/1dac8177-49f0-4c14-8297-8cc8a1ad62db" />

**Question 8**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```
create table Shipments(
ShipmentID integer primary key,
ShipmentDate date,
SupplierID integer,
OrderID integer,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID)
);
```

**Output:**

<img width="1250" height="233" alt="image" src="https://github.com/user-attachments/assets/81f0c2cd-6f84-4388-9356-db4c171fb584" />

**Question 9**
---
Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

```sql
CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT
);
```

**Output:**

<img width="1289" height="362" alt="image" src="https://github.com/user-attachments/assets/feb6948e-06cc-4318-9313-3fa8052b7739" />

**Question 10**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER ,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1296" height="269" alt="image" src="https://github.com/user-attachments/assets/60c7ce80-e59b-4e3f-92e1-87f1d4613fb1" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
