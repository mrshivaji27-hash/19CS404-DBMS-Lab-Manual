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

## PROGRAM
```
CREATE OR REPLACE PROCEDURE find_square(n NUMBER)
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || n*n);
END;
SET SERVEROUTPUT ON;
EXEC FIND_SQUARE(6);
```

**Expected Output:**  
Square of 6 is 36

## OUTPUT
<img width="816" height="246" alt="image" src="https://github.com/user-attachments/assets/4e3e8e04-0733-4a4d-9a2c-fcd8c96f22c8" />


---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

## PROGRAM
```
CREATE OR REPLACE FUNCTION get_factorial(n NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..n LOOP
        fact := fact * i;
    END LOOP;
    RETURN fact;
END;
SELECT get_factorial(5) FROM DUAL;
```

**Expected Output:**  
Factorial of 5 is 120

## OUTPUT
<img width="742" height="277" alt="image" src="https://github.com/user-attachments/assets/96f566cb-6266-4b5a-bb41-bfd3cdedcdc2" />


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

## PROGRAM
```
CREATE OR REPLACE PROCEDURE check_even_odd(n NUMBER)
IS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
EXEC check_even_odd(12);
```

**Expected Output:**  
12 is Even

## OUTPUT
<img width="785" height="302" alt="image" src="https://github.com/user-attachments/assets/022eaea7-e6a5-4972-b93f-15614b0dfb54" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

## PROGRAM
```
CREATE OR REPLACE FUNCTION reverse_number(n NUMBER)
RETURN NUMBER
IS
    rev NUMBER := 0;
    temp NUMBER := n;
BEGIN
    WHILE temp > 0 LOOP
        rev := rev * 10 + MOD(temp, 10);
        temp := TRUNC(temp / 10);
    END LOOP;

    RETURN rev;
END;
SELECT reverse_number(1234) FROM DUAL;
```

**Expected Output:**  
Reversed number of 1234 is 4321

## OUTPUT
<img width="823" height="332" alt="image" src="https://github.com/user-attachments/assets/59069d5d-2af8-4906-a1c7-905fe1dcddb9" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

## PROGRAM
```
CREATE OR REPLACE PROCEDURE print_table(n NUMBER)
IS
BEGIN
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || n*i);
    END LOOP;
END;
EXEC print_table(5);
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## OUTPUT
<img width="666" height="340" alt="image" src="https://github.com/user-attachments/assets/a4b4b84f-087b-42e0-802e-8d4152b830d2" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
