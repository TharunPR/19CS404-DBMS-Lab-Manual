# Experiment 6: Joins

## AIM
To study and implement different types of joins.

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

**Write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.**

**Sample table: customer**

| customer_id | cust_name    | city      | grade | salesman_id |
|-------------|--------------|-----------|-------|-------------|
| 3002        | Nick Rimando | New York  | 100   | 5001        |
| 3007        | Brad Davis   | New York  | 200   | 5001        |
| 3005        | Graham Zusi  | California| 200   | 5002        |
| 3008        | Julian Green | London    | 300   | 5002        |
| 3004        | Fabian Johnson| Paris    | 300   | 5006        |
| 3009        | Geoff Cameron| Berlin    | 100   | 5003        |
| 3003        | Jozy Altidor | Moscow    | 200   | 5007        |
| 3001        | Brad Guzan   | London    |       | 5005        |

**Sample table: orders**

| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
|--------|-----------|------------|-------------|-------------|
| 70001  | 150.5     | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.5     | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.5     | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.6    | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760      | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.4    | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.6    | 2012-04-25 | 3002        | 5001        |

```sql
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/9e8127a6-2cd9-4519-8eeb-ca75cddd9e20)

**Question 2**

**Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.**

**PATIENTS TABLE:**

![image](https://github.com/user-attachments/assets/63c6eb3f-86d1-466d-9648-031ab9d1bc35)

**DOCTORS TABLE:**

![image](https://github.com/user-attachments/assets/66d1c3e5-a143-47bf-be7c-5badf1dfeaee)

```sql
SELECT 
    patients.first_name AS patient_name, 
    doctors.first_name AS doctor_name
FROM 
    patients
INNER JOIN 
    doctors ON patients.doctor_id = doctors.doctor_id
WHERE 
    patients.date_of_birth > '1990-01-01';

```

**Output:**

![image](https://github.com/user-attachments/assets/ad2d34ed-be0f-4ac5-be61-01545dc78879)

**Question 3**

**Write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, and commission.**

**Sample table: customer**

| customer_id | cust_name    | city       | grade | salesman_id |
|-------------|--------------|------------|-------|-------------|
| 3002        | Nick Rimando | New York   | 100   | 5001        |
| 3007        | Brad Davis   | New York   | 200   | 5001        |
| 3005        | Graham Zusi  | California | 200   | 5002        |
| 3008        | Julian Green | London     | 300   | 5002        |
| 3004        | Fabian Johnson| Paris     | 300   | 5006        |
| 3009        | Geoff Cameron| Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan   | London     |       | 5005        |

**Sample table: salesman**

| salesman_id | name        | city       | commission |
|-------------|-------------|------------|------------|
| 5001        | James Hoog  | New York   | 0.15       |
| 5002        | Nail Knite  | Paris      | 0.13       |
| 5005        | Pit Alex    | London     | 0.11       |
| 5006        | Mc Lyon     | Paris      | 0.14       |
| 5007        | Paul Adam   | Rome       | 0.13       |
| 5003        | Lauson Hen  | San Jose   | 0.12       |

```sql
SELECT 
    c.cust_name as 'Customer Name', 
    c.city AS city, 
    s.name AS Salesman, 
    s.commission
FROM 
    customer AS c
INNER JOIN 
    salesman AS s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/939bd878-9f77-4e98-8f62-ad92c016f28e)

**Question 4**

**Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-08-01' and '2012-08-30'.**

**CUSTOMER TABLE:**  

![image](https://github.com/user-attachments/assets/e6d94eac-795b-41de-9b1c-c583f828eba2)

**ORDERS TABLE:**  

![image](https://github.com/user-attachments/assets/a1e5068c-0939-42ed-a534-029bcb4ab137)

```sql
SELECT 
    c.*
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

![image](https://github.com/user-attachments/assets/f8bdd7fe-e52c-4441-933e-15de5e5b3333)

**Question 5**

**Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.**

**NURSES TABLE:**  

![image](https://github.com/user-attachments/assets/0cb94824-76fb-4e0b-80b2-ff077c9c9adb)

**DEPARTMENTS TABLE:**  

![image](https://github.com/user-attachments/assets/027670e2-147f-46a9-89d3-8b45c81d3d2d)

```sql
SELECT 
    n.nurse_id,
    d.department_name
FROM 
    nurses AS n
INNER JOIN 
    departments AS d ON n.department_id = d.department_id
WHERE 
    n.first_name = 'David'
    AND n.last_name = 'Moore';
```

**Output:**

![image](https://github.com/user-attachments/assets/34d20650-63d9-4d4a-a7ac-e2165e00b49f)

**Question 6**

**From the following tables, write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.**

**Sample table: customer**

| customer_id | cust_name       | city       | grade | salesman_id |
|-------------|------------------|------------|--------|--------------|
| 3002        | Nick Rimando     | New York   | 100    | 5001         |
| 3007        | Brad Davis       | New York   | 200    | 5001         |
| 3005        | Graham Zusi      | California | 200    | 5002         |
| 3008        | Julian Green     | London     | 300    | 5002         |
| 3004        | Fabian Johnson   | Paris      | 300    | 5006         |
| 3009        | Geoff Cameron    | Berlin     | 100    | 5003         |
| 3003        | Jozy Altidor     | Moscow     | 200    | 5007         |
| 3001        | Brad Guzan       | London     |        | 5005         |

**Sample table: salesman**

| salesman_id | name        | city       | commission |
|-------------|-------------|------------|-------------|
| 5001        | James Hoog  | New York   | 0.15        |
| 5002        | Nail Knite  | Paris      | 0.13        |
| 5005        | Pit Alex    | London     | 0.11        |
| 5006        | Mc Lyon     | Paris      | 0.14        |
| 5007        | Paul Adam   | Rome       | 0.13        |
| 5003        | Lauson Hen  | San Jose   | 0.12        |

```sql
SELECT C.cust_name ,C.city,C.grade,S.name AS "Salesman",S.city FROM CUSTOMER C
JOIN SALESMAN S ON C.SALESMAN_ID=S.SALESMAN_ID where C.grade < 300
order by c. customer_id  ASC ;
```

**Output:**

![image](https://github.com/user-attachments/assets/642b4921-6b59-4ab9-93b7-8ef86637ee6f)

**Question 7**

**From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.**

**Sample table: `customer`**

| customer_id | cust_name       | city        | grade | salesman_id |
|-------------|------------------|-------------|-------|-------------|
| 3002        | Nick Rimando     | New York    | 100   | 5001        |
| 3007        | Brad Davis       | New York    | 200   | 5001        |
| 3005        | Graham Zusi      | California  | 200   | 5002        |
| 3008        | Julian Green     | London      | 300   | 5002        |
| 3004        | Fabian Johnson   | Paris       | 300   | 5006        |
| 3009        | Geoff Cameron    | Berlin      | 100   | 5003        |
| 3003        | Jozy Altidor     | Moscow      | 200   | 5007        |
| 3001        | Brad Guzan       | London      |       | 5005        |

---

**Sample table: `salesman`**

| salesman_id | name        | city       | commission |
|-------------|-------------|------------|------------|
| 5001        | James Hoog  | New York   | 0.15       |
| 5002        | Nail Knite  | Paris      | 0.13       |
| 5005        | Pit Alex    | London     | 0.11       |
| 5006        | Mc Lyon     | Paris      | 0.14       |
| 5007        | Paul Adam   | Rome       | 0.13       |
| 5003        | Lauson Hen  | San Jose   | 0.12       |

```sql
SELECT C.cust_name AS "Customer Name",C.city,S.name AS Salesman,S.city,S.commission FROM CUSTOMER C
JOIN SALESMAN S ON C.SALESMAN_ID = S.SALESMAN_ID
WHERE C.CITY != S.CITY AND S.COMMISSION >0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/683bf90e-f91e-4baf-939c-7136fe328dd7)


**Question 8**

**Write a SQL statement to join the tables `salesman`, `customer`, and `orders` so that the same column of each table appears once and only the relational rows are returned.**

**Sample table: `orders`**

| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
|--------|-----------|------------|-------------|-------------|
| 70001  | 150.5     | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.5     | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.5     | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.6    | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760      | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.4    | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.6    | 2012-04-25 | 3002        | 5001        |

**Sample table: `customer`**

| customer_id | cust_name       | city        | grade | salesman_id |
|-------------|------------------|-------------|-------|-------------|
| 3002        | Nick Rimando     | New York    | 100   | 5001        |
| 3007        | Brad Davis       | New York    | 200   | 5001        |
| 3005        | Graham Zusi      | California  | 200   | 5002        |
| 3008        | Julian Green     | London      | 300   | 5002        |
| 3004        | Fabian Johnson   | Paris       | 300   | 5006        |
| 3009        | Geoff Cameron    | Berlin      | 100   | 5003        |
| 3003        | Jozy Altidor     | Moscow      | 200   | 5007        |
| 3001        | Brad Guzan       | London      |       | 5005        |

**Sample table: `salesman`**

| salesman_id | name        | city       | commission |
|-------------|-------------|------------|------------|
| 5001        | James Hoog  | New York   | 0.15       |
| 5002        | Nail Knite  | Paris      | 0.13       |
| 5005        | Pit Alex    | London     | 0.11       |
| 5006        | Mc Lyon     | Paris      | 0.14       |
| 5007        | Paul Adam   | Rome       | 0.13       |
| 5003        | Lauson Hen  | San Jose   | 0.12       |

```sql
SELECT O.ord_no,O.purch_amt,O.ord_date,C.cust_name,C.city AS customer_city,C.grade,S.name AS salesman_name,S.city AS salesman_city,S.commission FROM ORDERS O
LEFT JOIN CUSTOMER C ON O.CUSTOMER_ID = C.CUSTOMER_ID
LEFT JOIN SALESMAN S ON C.SALESMAN_ID =S.SALESMAN_ID;
```

**Output:**

![image](https://github.com/user-attachments/assets/9ddc8993-05ef-4056-8ed7-1492f5805184)

**Question 9**

**Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.**

**CUSTOMER TABLE:**

![image](https://github.com/user-attachments/assets/89fd7db2-930d-4741-ba3c-96607dfd296a)

**ORDERS TABLE:**

![image](https://github.com/user-attachments/assets/7d8c60fc-64e9-4bda-bd8f-4082a0b2bf00)

```sql
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id
WHERE 
    o.purch_amt < 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/316541a5-a708-4424-b09f-71f4449d39fb)

**Question 10**

**Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.**

**PATIENTS TABLE:**

![image](https://github.com/user-attachments/assets/abd1f803-10aa-4028-a64a-a828699399fc)

**DOCTORS TABLE:**

![image](https://github.com/user-attachments/assets/39273cd0-ea2c-402a-85de-cb4dfb78741a)

```sql
SELECT 
    p.first_name AS patient_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d ON p.doctor_id = d.doctor_id
WHERE 
    d.first_name = 'Emily'
    AND d.last_name = 'Johnson'
    AND p.discharge_date IS NOT NULL;

```

**Output:**

![image](https://github.com/user-attachments/assets/115ffaa3-2da2-4fde-8d20-7ea053c77def)

**MODULE-5 GRADE**

![image](https://github.com/user-attachments/assets/0669210e-c852-4de5-b0ef-5f9b32e883df)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
