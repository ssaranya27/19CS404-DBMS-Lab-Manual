# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE find_square(p_num IN NUMBER) AS
    v_square NUMBER;
BEGIN
    v_square := p_num * p_num;

    DBMS_OUTPUT.PUT_LINE('Square of ' || p_num || ' is ' || v_square);
END;
/

BEGIN
    find_square(6);
END;
/

**Expected Output:**  
Square of 6 is 36
```
## OUTPUT:

<img width="928" height="260" alt="image" src="https://github.com/user-attachments/assets/82d4352c-3d3f-4ed7-8973-08b3b8f54144" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION get_factorial(p_num IN NUMBER)
RETURN NUMBER
AS
    v_fact NUMBER := 1;
    v_i NUMBER;
BEGIN
    IF p_num < 0 THEN
        DBMS_OUTPUT.PUT_LINE('Factorial not defined for negative numbers.');
        RETURN NULL;
    ELSIF p_num = 0 THEN
        RETURN 1;
    ELSE
        FOR v_i IN 1..p_num LOOP
            v_fact := v_fact * v_i;
        END LOOP;
        RETURN v_fact;
    END IF;
END;
/

DECLARE
    v_num NUMBER := 5;
    v_result NUMBER;
BEGIN
    v_result := get_factorial(v_num);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || v_num || ' is ' || v_result);
END;
/

```
**Expected Output:**  
Factorial of 5 is 120

## OUTPUT:

<img width="937" height="277" alt="image" src="https://github.com/user-attachments/assets/abdc3d2b-5552-4c79-9783-0f6cfb282f6d" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd(p_num IN NUMBER) AS
BEGIN
    IF MOD(p_num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(12);
END;
/
```

**Expected Output:**  
12 is Even

## OUTPUT:

<img width="920" height="259" alt="image" src="https://github.com/user-attachments/assets/c9f8779d-b159-460e-aecc-4b7afe4b5793" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.
## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION reverse_number(p_num IN NUMBER)
RETURN NUMBER
AS
    v_rev NUMBER := 0;
    v_rem NUMBER;
    v_temp NUMBER := p_num;
BEGIN
    WHILE v_temp > 0 LOOP
        v_rem := MOD(v_temp, 10);
        v_rev := (v_rev * 10) + v_rem;
        v_temp := TRUNC(v_temp / 10);
    END LOOP;
    RETURN v_rev;
END;
/

DECLARE
    v_num NUMBER := 1234;
    v_result NUMBER;
BEGIN
    v_result := reverse_number(v_num);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || v_num || ' is ' || v_result);
END;
/

```
**Expected Output:**  
Reversed number of 1234 is 4321
## OUTPUT:
<img width="918" height="282" alt="image" src="https://github.com/user-attachments/assets/ab43d5cd-d699-4687-aca3-5bc945573cb7" />

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.
## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE print_table(p_num IN NUMBER)
AS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || p_num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(p_num || ' x ' || i || ' = ' || (p_num * i));
    END LOOP;
END;
/

BEGIN
    print_table(5);
END;
/
```
**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## OUTPUT:
<img width="944" height="305" alt="image" src="https://github.com/user-attachments/assets/d6759831-da14-4e60-b1e5-c364de1cda4e" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
