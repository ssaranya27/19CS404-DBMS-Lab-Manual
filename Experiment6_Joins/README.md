
## AIM
To study and implement different types of joins.

## NAME: SARANYA S.
## REG NO: 212223220101
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

<img width="1232" height="466" alt="image" src="https://github.com/user-attachments/assets/7e0b1cc8-6c7c-4569-89f3-19caa104153a" />

**SQL**
```
SELECT s.name AS salesman_name,
       c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id;

```
**Output:**

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d5b1ae7e-5a05-469f-9bff-42b694e3aa1a" />

**Question 2**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6036f637-84e2-4bca-ae79-0eb97de60976" />

**SQL**
```
SELECT p.*, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id;
```

**Output:**

<img width="1241" height="516" alt="image" src="https://github.com/user-attachments/assets/5ed1fa38-764d-4983-81f1-2d48f118dd19" />

**Question 3**

<img width="1884" height="876" alt="image" src="https://github.com/user-attachments/assets/84b4f1f6-492f-4f3d-bc12-92f80a0006d5" />
**SQL**
```
SELECT p.*, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id;
```
**Output:**

![Output3](output.png)

**Question 4**
---
<img width="1827" height="851" alt="image" src="https://github.com/user-attachments/assets/849f7398-37e3-4427-bd7d-be7102042f22" />

**SQL**
```
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```

**Output:**
<img width="911" height="493" alt="image" src="https://github.com/user-attachments/assets/9acf7b16-7e0f-4bb1-885c-5b8578968917" />

**Question 5**

<img width="1919" height="1062" alt="image" src="https://github.com/user-attachments/assets/bf04e571-df6b-4bb3-b7f5-d44a7fe630d3" />

**SQL**
```
SELECT o.ord_no,
       o.purch_amt,
       c.cust_name,
       c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

```
**Output:**

<img width="1288" height="448" alt="image" src="https://github.com/user-attachments/assets/0eb88655-0f64-411e-b47b-3f041bef0966" />

**Question 6**

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/27ce0bf1-5331-44a4-bd31-80c10247e5fe" />

**SQL**
```

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
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1792" height="866" alt="image" src="https://github.com/user-attachments/assets/61c9ba07-761d-4cd2-847f-4f9ca6912b4c" />

**Question 7**

<img width="1382" height="774" alt="image" src="https://github.com/user-attachments/assets/6b45e65b-ef9a-4088-b27d-df9b007ff131" />

**SQL**
```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**

<img width="1788" height="785" alt="image" src="https://github.com/user-attachments/assets/81169e31-1ef1-49ad-8ec1-283121ccc0c8" />

**Question 8**

<img width="1797" height="557" alt="image" src="https://github.com/user-attachments/assets/ee68fbef-5228-4c07-91b6-9ea67237eb1c" />

**SQL**
```
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;

```

**Output:**

<img width="1262" height="557" alt="image" src="https://github.com/user-attachments/assets/ba89f3b5-d483-47f4-9306-b20d2928110b" />

**Question 9**

<img width="1127" height="740" alt="image" src="https://github.com/user-attachments/assets/f26c9a97-628c-4ca1-b96f-593ea4fa23f0" />
**SQL**
```
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM salesman s
JOIN customer c ON s.city = c.city;
```

**Output:**

<img width="919" height="580" alt="image" src="https://github.com/user-attachments/assets/16f31314-81db-4114-8b84-590f04595941" />

**Question 10**
---
<img width="1353" height="845" alt="image" src="https://github.com/user-attachments/assets/b18cb314-f69f-4182-8797-6666390c8dbb" />

**SQL**
```
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1271" height="843" alt="image" src="https://github.com/user-attachments/assets/8bf3284d-39c6-4ab1-8d8a-00cf3847ac7b" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
