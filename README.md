# CV-generator
create table employee(
Emp_no int,
E_name char(50),
E_address varchar(100),
E_ph_no varchar(20),
Dept_no int,
Dept_name char(20),
Job_ID int,
Salary int);

Alter table employee
Add Hiredate date;

Alter table employee
Modify Job_ID varchar(10);

Alter table employee
change Emp_no E_no int;

ALter table employee
Modify Job_ID varchar(20);

insert into employee(E_no, E_name, E_address, E_ph_no, Dept_no, Dept_name, Job_ID, Salary) values
(1, 'John Doe', '123 Main St', '123-456-7890', 101, 'Marketing', 'Manager', 60000),
(2, 'Jane Smith', '456 Oak St', '987-654-3210', 102, 'HR', 'HR Specialist', 50000),
(3, 'Bob Johnson', '789 Pine St', '555-123-4567', 101, 'Marketing', 'Sales Representative', 45000),
(4, 'Alice Brown', '987 Cedar St', '777-888-9999', 103, 'Finance', 'Accountant', 55000),
(5, 'Charlie Lee', '654 Birch St', '444-555-6666', 102, 'HR', 'HR Manager', 70000);

select*from employee;

select*from employee where Dept_name = 'Marketing'; 

update employee
set Dept_name = 'HR' where E_no = 3;

select E_name, Salary from employee where Dept_name = 'HR';

delete from employee where Dept_name = 'Finance';

Alter table employee
Add Designation varchar(50);

insert into employee(Designation) values
('Manager'),
('Head'),
('Intern'),
('Senior'),
('Junior');

select*from employee;

select E_name, E_no, Salary from employee where Designation = 'Manager';

select Salary from employee order by Salary ASC;

select designation, Salary/30 as Daily_Salary from employee;

select E_name, E_no, Salary from employee where Designation='Manager' or Designation= 'Junior';

select Designation from employee where Designation LIKE 'J%';

select E_name, left (E_name, 5) as first_five_chars from employee where E_name like 'C%';

select E_no, E_name, Salary from employee where Dept_name = 'Manager';

select E_name, Salary from employee order by Salary asc;
select E_name, Dept_name from employee order by Dept_name asc;

select Dept_name, Salary/30 as Daily_Salary from employee;

select*from employee where E_no in (2, 3, 4);

select E_name, Dept_no from employee where Dept_no = 101 or Dept_no = 102;

select E_name from employee where E_name like 'C%';

select E_name, left(E_name, 5) as first_five_characters from employee where E_name like 'A%'or E_name like 'B%';

select E_no, E_name, Dept_name, Salary from employee where Dept_name not in('Marketing','Accountant') order by Salary asc;

drop table emp;
drop table dept;

create table dept(
Dept_no int,
Dept_name varchar(50));

insert into dept(Dept_no) values
(101), (103), (105), (109);

select Dept_no from employee
union
select Dept_no from dept;

select Dept_no from employee
union all 
select Dept_no from dept;

select distinct employee.dept_no from employee
left join dept on employee.dept_no = dept.dept_no where dept.dept_no is null;

select distinct dept.dept_no from dept
left join employee on employee.dept_no = dept.dept_no where employee.dept_no is null;

select dept_no from dept where not exists (select*from employee where employee.dept_no = dept.dept_no);
select dept_no from employee where not exists(select*from dept where employee.dept_no = dept.dept_no);

create table emp(
Emp_no int not null,
E_name varchar (20),
Job varchar (10),
Dept_no int not null,
Salary int not null);

Alter table emp 
Add constraint check (Emp_no > 100);
Alter table emp
Add constraint check (Salary > 10000);

Alter table emp
Add constraint unique (Dept_no);

Alter table emp
Add constraint Primary key (Emp_no);

create table Sailors(
Sid int primary key,
Sname varchar(10),
Rating decimal,
Age int);

create table boats(
bid int primary key,
bname varchar(10),
color varchar(10));

create table reserves(
Sid int,
bid int,
day date,
primary key(Sid, bid),
foreign key (Sid) references Sailors(Sid),
foreign key (bid) references boats(bid));

create view Current_Products_List as select product_id, product_name from products;
create view Students as select StudentID, StudentName from student;

select*from current_product_list;

select count(*) as Totalproducts from current_product_list;
select count(*) StudentID from student;

select product_id, product_name from current_product_list where product_name like 'A%';

select StudentName from student where StudentID in (select StudentID from studentdepartments);

select StudentName from student where StudentID not in (select StudentID from studentdepartments);

select Dept_name from dept where Dept_no not in (select DepartmentID from studentdepartments);

select StudentName from Student where StudentID in (select StudentID from studentdepartments);

select*from Student where StudentID =( select StudentID from Student where StudentName ='Ali');

select d.DepartmentName, (select count(*) from studentdepartments sd where sd.DepartmentID=d.DepartmentID) as StudentCount from departments d;

****
