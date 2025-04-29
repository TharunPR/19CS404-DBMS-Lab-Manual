# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

Write a SQL query to find how many patients are there in each city.  
&emsp;Sample table: Patients  

![image](https://github.com/user-attachments/assets/48415b92-dc8b-4a17-b95a-47c08ff22346)

```sql
select substr(Address,instr(Address,',')+1) as Address,count(*) as TotalPatients from Patients group by Address;
```

**Output:**

![image](https://github.com/user-attachments/assets/b6dc5a66-7eb6-4a56-9631-0fddbefc0072)

**Question 2**

**Write a SQL query to find how many prescriptions were written in each frequency category (e.g., once daily, twice daily).**
**Sample table: Prescriptions**

![image](https://github.com/user-attachments/assets/047f6028-aed5-433b-84e4-46ec6d2eae99)


```sql
select Frequency,count(*) as TotalPrescriptions from Prescriptions group by Frequency;
```

**Output:**

![image](https://github.com/user-attachments/assets/470baa64-2fbd-4153-a12f-50943f4dbe7c)


**Question 3**

**Write a SQL query to find how many patients have expired insurance coverage for each insurance company.**  
**Sample table: Insurance**  

![image](https://github.com/user-attachments/assets/b750f1bf-25bb-4ac1-8a9b-8bad2602abc3)

```sql
select InsuranceCompany, count(*) as TotalExpiredPatients from insurance group by InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/1006307b-666b-4d82-81c4-9433d54da2fc)

**Question 4**

**Write a SQL query to calculate the average email length (in characters) for people who live in Mumbai city.**

**Table: customer**

| name  | type     |
|-------|----------|
| id    | INTEGER  |
| name  | TEXT     |
| city  | TEXT     |
| email | TEXT     |
| phone | INTEGER  |

```sql
select avg(length(email)) as avg_email_length_below_30 from customer where city = 'Mumbai';
```

**Output:**

![image](https://github.com/user-attachments/assets/32c7713a-b9ce-47ba-845b-0c409fc65539)

**Question 5**

**Write a SQL query to find the difference between the maximum and minimum price of fruits.**

**Table: fruits**

| name      | type    |
|-----------|---------|
| id        | INTEGER |
| name      | TEXT    |
| unit      | TEXT    |
| inventory | INTEGER |
| price     | REAL    |

```sql
select max(price) - min(price) as price_diff from fruits;
```

**Output:**

![image](https://github.com/user-attachments/assets/cf6bd116-726c-4a8f-be27-70a15caeecb0)

**Question 6**

**Write a SQL query to find the youngest employee in the company.**

**Table: employee**

| name   | type     |
|--------|----------|
| id     | INTEGER  |
| name   | TEXT     |
| age    | INTEGER  |
| city   | TEXT     |
| income | INTEGER  |

```sql
select name as Employee_Name, min(Age) as Age from employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/0bfd2401-4258-484f-be93-7c470d836830)

**Question 7**
**Write a SQL query to calculate the total number of working hours of all employees.**

**Sample table: employee1**

![image](https://github.com/user-attachments/assets/96e8f415-06bb-4366-8fa0-c33cb45bd625)


```sql
select sum(workhour) as 'Total working hours' from employee1;
```

**Output:**

![image](https://github.com/user-attachments/assets/1280f4ff-f047-4626-b6c6-77858eb1f5d5)

**Question 8**
**Write a SQL query that accomplishes the grouping of data by age intervals using the expression `(age/5)*5`, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.**

**Sample table: customer1**

![image](https://github.com/user-attachments/assets/ec5c494c-0705-46d5-9fff-aad6deee7ac2)

```sql
select (age/5)*5 as age_group ,MIN(age) from customer1 group by age_group having min(age) < 25;
```

**Output:**

![image](https://github.com/user-attachments/assets/7c20e410-ff8a-4b32-b049-2ac99c80e00c)

**Question 9**

**Write a SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.**

**Sample table: employee1**

![image](https://github.com/user-attachments/assets/722d8dd1-ccc0-47c5-9026-a31e9f13fb58)

```sql
select occupation, SUM(workhour) from employee1 group by occupation having sum(workhour) > 20;
```

**Output:**

![image](https://github.com/user-attachments/assets/4249004a-20b0-41f3-83e1-822722db36ed)

**Question 10**

**Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.**

**Table: customer1**

![image](https://github.com/user-attachments/assets/275c23b8-2e9a-43d2-aae2-db3d327d1ae9)

```sql
select (age/5)*5 as age_group , MIN(salary) from customer1 group by age_group having min(salary) < 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/fdc9f1f4-fa28-4c7a-a4fe-50127788c23b)


**MODULE-3 GRADE**

![image](https://github.com/user-attachments/assets/e13ef081-4576-4f76-b6c0-d437f756aea7)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
