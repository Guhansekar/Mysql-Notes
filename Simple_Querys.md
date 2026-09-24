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
