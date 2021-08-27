```sql 
/* create database, table, insert values */
create database test;
create table employees(id int, name varchar(255), city varchar(255));
insert into employees values(1,'sri','toronto'),(2,'vin','liverpool'),
                            (3,'cat','lapaz'),(4,'ism','toluca'),
                            (5,'rak','banglore'),(6,'dad','hyderabad');
alter table employees add cloulmn salary int;
update employees set salary=254868 where id =1;
update employees set salary=287868 where id =2;
update employees set salary=358868 where id =3;
update employees set salary=15878 where id =4;
update employees set salary=583588 where id =5;
update employees set salary=583588 where id =5;
``` 
```sql
/* MAX SALARY IN A TABLE */
select max(salary) as salary from employees;
```
```sql
/* 2nd MAX SALARY */
 select max(salary) as salary from employees where salary not in  select max(salary) from employees;
```
```sql
/* CHECK FOR DUPLICARE SALARY*/
 select salary from employees group by salary having count(*)>1;
```
```sql
/* STORED PROCEDURE FOR GETTING SALARY FROM ID */
 delimiter //
    create procedure salaries (in ids int, out sl int)
    begin
      select count(*) into sl from employees.salary
      where ids = id;
    end //
delimiter ;
----------------------
call (@2, @sl);
```
