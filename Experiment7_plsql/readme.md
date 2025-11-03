# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.

**NAME  :**   SARANYA S.

**REGNO :**  212223220101

## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**PL/SQL**
```
DECLARE
    num1 NUMBER := 45;
    num2 NUMBER := 80;
    greatest NUMBER;
BEGIN
    IF num1 > num2 THEN
        greatest := num1;
    ELSE
        greatest := num2;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Greater number is: ' || greatest);
END;
/
```
**Expected Output:**  
Greater number is: 80
<img width="362" height="129" alt="image" src="https://github.com/user-attachments/assets/ac8e280e-7cdd-4f86-8ef9-d8995c5482b7" />


## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**PL/SQL**
```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```
**Expected Output:**  
Sum of first 10 natural numbers is: 55

<img width="369" height="149" alt="image" src="https://github.com/user-attachments/assets/bf9da6d4-c6dd-429e-9dfc-7fa317cfe0a8" />

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**PL/SQL**
```
DECLARE
  n NUMBER := 7;
  a NUMBER := 0;
  b NUMBER := 1;
  c NUMBER;
BEGIN
  DBMS_OUTPUT.PUT_LINE('Fibonacci sequence (' || n || ' terms):');
  DBMS_OUTPUT.PUT_LINE(a);
  DBMS_OUTPUT.PUT_LINE(b);
  FOR i IN 3..n LOOP
    c := a + b;
    DBMS_OUTPUT.PUT_LINE(c);
    a := b;
    b := c;
  END LOOP;
END;
/

```

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
<img width="371" height="285" alt="image" src="https://github.com/user-attachments/assets/fbd2e6b9-dce6-4fc7-affc-a466a1263fbe" />


## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**PL/SQL**
```
SET SERVEROUTPUT ON;
DECLARE
  n NUMBER := 1535;
  rev NUMBER := 0;
  rem NUMBER;
  temp NUMBER;
BEGIN
  temp := n;
  WHILE temp > 0 LOOP
    rem := MOD(temp, 10);
    rev := rev * 10 + rem;
    temp := FLOOR(temp / 10);
  END LOOP;
  DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```
**Expected Output:**  
n = 1535  
Reversed number is 5351
<img width="448" height="176" alt="image" src="https://github.com/user-attachments/assets/cdd8ea83-ff47-4795-910e-352fa5d42f0e" />
---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**PL/SQL**
```
SET SERVEROUTPUT ON;
DECLARE
  a NUMBER := 10;
  b NUMBER := 9;
  c NUMBER := 15;
  largest NUMBER;
BEGIN
  IF a > b AND a > c THEN
    largest := a;
  ELSIF b > c THEN
    largest := b;
  ELSE
    largest := c;
  END IF;
  DBMS_OUTPUT.PUT_LINE('Largest of three numbers is ' || largest);
END;
/
```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

<img width="634" height="262" alt="image" src="https://github.com/user-attachments/assets/c39a2db1-8498-4ef1-9d78-c24741755971" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

