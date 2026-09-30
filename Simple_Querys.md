## Select
select * from students;

select first_name,marks from students;

select first_name,marks from students where marks >90; 

select first_name from students where city="Chennai";

select first_name,gender from students where department="Computer Science";
## Where & operators
select first_name from students where age>20;

select first_name from students where student_id=25;

select first_name,department from students where department <> "Computer Science";

select first_name,department from students where department != "Computer Science";


## And OR NOT
select first_name,department,age from students where age between 20 and 21;

select first_name,department,age from students where age = 20 or department="Computer Science";

select first_name,department,age from students where not age=20;

select first_name,department,age from students where gender="female" and (age=20 or department='Computer Science') and city='Chennai';

## Order by
select first_name,department,age from students where age between 20 and 21 order by first_name;

select first_name,department,age from students where age between 20 and 21 order by first_name desc;

select first_name,department,age from students where age between 20 and 21 order by first_name,department desc;

## LIMIT and DISTINCT

select first_name,department,age from students where age between 20 and 21 order by first_name limit 2;

select distinct city from students;

select distinct department,city from students;

## Aggregate Functions
**Aggregate functions are used to perform calculations on multiple rows and return a single result**

select count(*) from students;

select count(*) as total_students from students;

select count(email) as total_email from students;

select count(*) as total_students,sum(marks) as total_mark from students where department='Computer Science';

select avg(marks) as avg_mark from students where department='Computer Science';

select min(marks) as min_mark from students where department='Computer Science';

select max(marks) as max_mark from students where department='Computer Science';

## GROUP BY

GROUP BY is used to group rows that have the same value, so that we can perform aggregate calculations for each group

select count(*) as total ,department from students group by department;

select avg(marks) as average_mark,department from students group by department;

select department,gender,count(*) as total from students group by department,gender;

select department,count(*) as total from students where city='Chennai' group by department;

## HAVING

HAVING is used to filter groups after GROUP BY

WHERE  → filters rows  -  Filters individual rows before grouping
HAVING → filters groups  - Filters groups after grouping.

select department,count(*) as total from students where city='Chennai' group by department having count(*) >3;

select department,gender,count(*) as total from students where city='Chennai' group by department,gender having count(*)>2 and gender='male';

## LIKE, IN, BETWEEN

select department,first_name from students where first_name like 'a%';

select department,first_name from students where first_name like 'a%n';

**Names containing a anywhere.

select department,first_name from students where first_name like '%a%';

SELECT * FROM students WHERE first_name LIKE 'A_u%';

**IN — Match multiple values

SELECT * FROM students WHERE city = 'Chennai' OR city = 'Madurai' OR city = 'Salem';

select first_name from students where city in('chennai','selam');

select first_name from students where city not in('chennai','selam');

## NULL, IS NULL, IS NOT NULL

What is NULL?

NULL means no value / missing value / unknown value.

It is not the same as:

0 '' 'NULL

and we cannot use =null !=null

select * from students where email  is null;

select * from students where email is not null;

**select first_name,marks,marks+10 as new_mark from students;**

## CASE Statement

CASE is used to create IF / ELSE logic in SQL.

select first_name,department,marks,case when marks >= 90 then 'Exellent' when marks >= 80 then 'good' when marks>=70 then 'better'
else 'try improve' end as performance from students; 

| first_name | marks | performance       |
| ---------- | ----: | ----------------- |
| Arun       |    95 | Excellent         |
| Anitha     |    84 | Good              |
| Ravi       |    75 | Average           |
| Kumar      |    65 | Needs Improvement |


WHEN → condition
THEN → result if true
ELSE → result if none are true
END → closes the CASE

## JOINS

CREATE TABLE students_join (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    age INT,
    gender VARCHAR(10),
    department_id INT,
    marks DECIMAL(5,2),
  
    FOREIGN KEY (department_id)
        
        REFERENCES departments(department_id)
);

A JOIN lets you combine data from two or more tables using a related column

select s.student_name,s.marks,d.department_name from students_join as s inner join departments as d on s.department_id = d.department_id; 

## What is LEFT JOIN?

All rows from the left table + matching rows from the right table.

If there is no match in the right table, MySQL returns NULL

If a student's department_id doesn't exist in departments, the department columns become NULL

select s.student_name,s.age,d.department_name from students_join as s left join departments as d on s.department_id=d.department_id;

## RIGHT JOIN

RIGHT JOIN keeps every row from the RIGHT table.

select s.student_name,s.age,d.department_name from students_join as s right join departments as d on s.department_id=d.department_id;

## Multiple JOINs

**ALTER TABLE departments ADD COLUMN hod_id INT;**

**UPDATE departments SET hod_id = 101 WHERE department_id = 1;**

select s.student_name,s.age,d.department_name,h.teacher_name from students_join as s inner join departments as d on s.department_id=d.department_id inner join teachers as h on h.teacher_id=d.hod_id;

## SELF JOIN

A SELF JOIN means joining a table with itself.

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(50),
    manager_id INT
);

INSERT INTO employees (employee_id, employee_name, manager_id)
VALUES
(1, 'Arun', NULL),
(2, 'Priya', 1),
(3, 'Ravi', 1),
(4, 'Karthik', 2),
(5, 'Sneha', 2),
(6, 'Vijay', 3);


select e.employee_name as employee,m.employee_name as manager from employees as e left join employees as m on e.employee_id = m.manager_id;

select e.employee_name as employee,m.employee_name as manager from employees as e inner join employees as m on e.employee_id = m.manager_id;

SELECT e.employee_name FROM employees AS e INNER JOIN employees AS m ON e.manager_id = m.employee_id WHERE m.employee_name = 'Arun';

## Subqueries

A subquery is a query written inside another query.

First query gets a result → outer query uses that result

select student_name,age,marks from students_join where marks > (select avg(marks) from students_join);

select student_name,age,marks from students_join where marks =(select max(marks) from students_join);

## Correlated Subqueries

A correlated subquery is a subquery that depends on the current row of the outer query.

Unlike a normal subquery, the inner query can run once for each row of the outer query.

normal query -> The average is calculated once, then compared with every student.

select s.student_name,s.age from students_join AS s where s.marks>(select avg(s1.marks) from students_join as s1 where s.department_id=s1.department_id);

s1.department_id means the department of rows being examined by the inner query.
