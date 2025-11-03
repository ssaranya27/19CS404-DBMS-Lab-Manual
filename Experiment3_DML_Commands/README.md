# Experiment 3: DML Commands
```
Developed by;
Name : SARANYA S.
Reg No : 212223220101
```

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
![image](https://github.com/user-attachments/assets/c4e1528c-df57-4948-b92b-393999033dbe)

**Program:**
```sql
DELETE FROM Doctors
WHERE (specialization='Pediatrics' OR specialization='Cardiology')
AND last_name='Brown';
```

**Output:**

![image](https://github.com/user-attachments/assets/c138c53c-eddb-4ed1-8bf9-87dd949919d6)


**Question 2**
---
![image](https://github.com/user-attachments/assets/fdcfc8b9-1e00-46e7-ade0-a5a78cd0fb4e)

**Program:**
```sql
DELETE FROM Customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
```

**Output:**

![image](https://github.com/user-attachments/assets/a97d92f6-6b0a-40a7-9e03-02d0e507df5c)


**Question 3**
---
![image](https://github.com/user-attachments/assets/ec4f3118-9615-4fda-87e5-50a27a712cb1)

**Program:**
```sql
SELECT COUNT(*)
FROM EmployeeInfo
WHERE Department='HR';
```

**Output:**

![image](https://github.com/user-attachments/assets/bd47906f-8db3-4f5c-8e60-defe536b1c1a)

**Question 4**
---
![image](https://github.com/user-attachments/assets/2b159c26-9e2d-4ee2-afe9-9b462ef35d4e)

**Program:**
```sql
SELECT ename,hiredate,JULIANDAY('2024-12-31')-JULIANDAY(hiredate) AS days_worked
FROM emp;
```

**Output:**

![image](https://github.com/user-attachments/assets/48a283b5-61e5-4846-b03e-9eba01baf494)


**Question 5**
---
![image](https://github.com/user-attachments/assets/2d1bd1d4-4f86-494d-b750-aa3a65c8a778)

**Program:**
```sql
UPDATE sales
SET sell_price= sell_price+3
WHERE product_id IN (SELECT product_id
                        FROM Products
                        WHERE supplier_id=4);
```

**Output:**

![image](https://github.com/user-attachments/assets/043200f3-b64a-4929-8820-b17beff5c02f)


**Question 6**
---
![image](https://github.com/user-attachments/assets/859f5f60-73be-4bae-9b8b-68d511c8f0d8)

**Program:**
```sql
SELECT *
FROM emp
WHERE hiredate >= DATE('2024-09-01','-6 months');
```

**Output:**

![image](https://github.com/user-attachments/assets/91133ef7-b6a3-4579-9e96-4394b3ed3f5e)


**Question 7**
---
![image](https://github.com/user-attachments/assets/d28c8320-380f-4caa-8365-51f0ad4f802e)

**Program:**
```sql
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

![image](https://github.com/user-attachments/assets/2806ae32-e7e5-4ef6-b189-38aaac0939fa)


**Question 8**
---
![image](https://github.com/user-attachments/assets/fc2bf715-a56f-4e11-869e-26b82b2cae5b)

**Program:**
```sql
DELETE FROM customer
WHERE cust_country='India' AND cust_city!='Chennai';
```

**Output:**

![image](https://github.com/user-attachments/assets/54786eb0-8242-4671-9fdc-283b3a674fa8)


**Question 9**
---
![image](https://github.com/user-attachments/assets/2fe4b958-a9cd-4df3-abdc-7e1f005d1ec3)

**Program:**
```sql
DELETE FROM Customer
WHERE WORKING_AREA='New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/723c3a6c-d418-4a72-ba27-683bb20bb4dc)


**Question 10**
---
![image](https://github.com/user-attachments/assets/9c73c386-b78e-44da-a9f7-4679aa3d052b)

**Program:**
```sql
UPDATE Suppliers
SET address='58 Lakeview, Magnolia'
WHERE supplier_id=5;
```

**Output:**

![image](https://github.com/user-attachments/assets/4c7d2cb5-8f25-4b71-937b-3622dd93660c)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

## Module Completion
![image](https://github.com/user-attachments/assets/019e1995-68ba-4afd-90e9-a8bbff812abb)
