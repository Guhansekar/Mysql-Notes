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

A JOIN lets you combine data from two or more tables using a related column

select s.student_name,s.marks,d.department_name from students_join as s inner join departments as d on s.department_id = d.department_id; 
