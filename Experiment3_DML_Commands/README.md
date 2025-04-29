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

Increase quantity of all products by 10% to adjust for surplus stock counted:

&emsp;**product_id**  
&emsp;**product_name**  
&emsp;**category**  
&emsp;**cost_price**  
&emsp;**sell_price**  
&emsp;**reorder_lvl**  
&emsp;**quantity**  
&emsp;**supplier_id**

```sql
update products set quantity = quantity * 1.10;
```

**Output:**

![image](https://github.com/user-attachments/assets/de0772c8-c30f-41b6-911a-4aebfb7dca2f)

**Question 2**

Certainly! Here's the formatted version with `&emsp;` and bold where necessary:

**Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.**

&emsp;**Products Table** 
&emsp;**product_id**     INT PRIMARY KEY  
&emsp;**product_name**   VARCHAR(10)  
&emsp;**category**       VARCHAR(50)  
&emsp;**cost_price**     DECIMAL(10)  
&emsp;**sell_price**     DECIMAL(10)  
&emsp;**reorder_lvl**    INT  
&emsp;**quantity**       INT  
&emsp;**supplier_id**    INT  

```sql
update products set reorder_lvl = reorder_lvl * 0.70 where cost_price > 50 and quantity < 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/9b573123-e329-4cb2-b4eb-4ac425f988c0)

**Question 3**

**Write a SQL statement to change the first_name column of the employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.**

&emsp;**Employees table**

&emsp;employee_id  
&emsp;first_name  
&emsp;last_name  
&emsp;email  
&emsp;phone_number  
&emsp;hire_date  
&emsp;job_id  
&emsp;salary  
&emsp;commission_pct  
&emsp;manager_id  
&emsp;department_id  

```sql
update employees set first_name = 'John' where department_id = 80 and commission_pct < 0.35;
```

**Output:**

![image](https://github.com/user-attachments/assets/189216d8-d114-429c-b154-a930abdf5bed)


**Question 4**

**Write a SQL statement to update the grade of all customers in Chennai city as 5.**

&emsp;**Customer table**  

&emsp;customer_id  
&emsp;cust_name  
&emsp;city  
&emsp;grade  
&emsp;salesman_id  

```sql
update customer set grade = 5 where city = 'Chennai';
```

**Output:**

![image](https://github.com/user-attachments/assets/e351e590-d120-433d-8756-7b213929b298)


**Question 5**

**Write a SQL statement to find all those customers with all information whose names are ending with the letter 'n'.**

**Customer table:**

| cid | name         | type | notnu | dflt_value | pk |
|-----|--------------|------|-------|------------|----|
| 0   | customer_id  | int  | 0     | 0          | 0  |
| 1   | cust_name    | text | 0     | 0          | 0  |
| 2   | city         | text | 0     | 0          | 0  |
| 3   | grade        | int  | 0     | 0          | 0  |

```sql
select * from customer where cust_name like ('%n');
```

**Output:**

![image](https://github.com/user-attachments/assets/ca506248-83f7-45f2-a074-a351c70c81ac)

**Question 6**

**Write a query to select all the records from the EmployeeInfo table, where the departments are either HR or Account.**

**EmployeeInfo table:**

| EmpID | EmpFname | EmpLname | Department | Project | Address        | DOB        | Gender |
|-------|----------|----------|------------|---------|----------------|------------|--------|
| 1     | Sanjay   | Mehra    | HR         | P1      | Hyderabad(HYD) | 01/12/1976 | M      |
| 2     | Ananya   | Mishra   | Admin      | P2      | Delhi(DEL)     | 02/05/1968 | F      |

```sql
select * from employeeInfo where department in ('HR', 'Account');
```

**Output:**

![image](https://github.com/user-attachments/assets/c03ab94f-3196-4f26-822e-61f1e322a7a4)

**Question 7**

**Write a SQL query to classify base in the Calculations table as 'Provided' if it is not NULL, otherwise 'Not Provided'.**

**Calculations table:**

| cid | name      | type     | notnull | dflt_value | pk |
|-----|-----------|----------|---------|------------|----|
| 0   | id        | INTEGER  | 0       |            | 1  |
| 1   | value1    | REAL     | 0       |            | 0  |
| 2   | value2    | REAL     | 0       |            | 0  |
| 3   | base      | INTEGER  | 0       |            | 0  |
| 4   | exponent  | INTEGER  | 0       |            | 0  |
| 5   | number    | REAL     | 0       |            | 0  |
| 6   | decimal   | REAL     | 0       |            | 0  |

```sql
select id,base,
    case 
        when base is not null then 'Provided'
        else 'Not Provided'
    end as base_status 
from calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/93cc3165-1dcf-4f05-aacb-d8bcbe5fa94b)

**Question 8**

**Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.**

**Calculations table:**

| cid | name      | type     | notnull | dflt_value | pk |
|-----|-----------|----------|---------|------------|----|
| 0   | id        | INTEGER  | 0       |            | 1  |
| 1   | value1    | REAL     | 0       |            | 0  |
| 2   | value2    | REAL     | 0       |            | 0  |
| 3   | base      | INTEGER  | 0       |            | 0  |
| 4   | exponent  | INTEGER  | 0       |            | 0  |
| 5   | number    | REAL     | 0       |            | 0  |
| 6   | decimal   | REAL     | 0       |            | 0  |

```sql
select id,value1,abs(value1) as absolute_value from calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/76a51146-4cc6-40ff-9bc3-ac182f48a792)

**Question 9**

**Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.**

**Sample table: customer**

| customer_id |   cust_name    |    city    | grade | salesman_id |
|-------------|----------------|------------|-------|-------------|
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |

```sql
select * from customer where city == 'New York' or grade <= 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/5d1e3f50-af73-4067-ad56-acd8c9501c92)

**Question 10**

**Write a SQL query to calculate the discounted price for products whose original price is between $50 and $150. Return product_id, original_price, discount_percentage, and discounted_price.**

**Sample table: Products**

| product_id | original_price | discount_percentage |
|------------|----------------|---------------------|
| 101        | 50.00          | 0.10                |
| 102        | 125.00         | 0.15                |
| 103        | 200.00         | 0.20                |

```sql
select product_id,original_price,discount_percentage,(original_price - (original_price * discount_percentage)) as discounted_price from products; 
```

**Output:**

![image](https://github.com/user-attachments/assets/2c3cd1c9-87f8-4eb0-b64d-4e45b7b12eb4)

**MODULE-2 GRADE**

![image](https://github.com/user-attachments/assets/23bd43f7-03ce-4f1a-9753-91387168b508)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
