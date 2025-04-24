# MY-SQL-QUERY-ON-A-SUPERMARKET-SALES-ANALYSIS
Analyzed supermarket sales data using SQL to uncover insights on revenue trends, top-selling products, payment methods, and customer behavior. This project highlights my skills in data cleaning, aggregation, filtering, and querying to support data-driven decisions.
### Questions
1. This command means Select what ur output table will look like from sale database, input the range ( which is why the date was used), then group by name( which means SQl should display the profit according to each item showed at the supermarket). Then order by profit ‘DESC’ means  the output shud show the profit from the highest to the lowest.
```Mysql
SELECT name, date, sum(total)- sum(originalprice*quantity) as profit FROM `sale` where date BETWEEN '2021-02-01' and '2021-02-28' GROUP by name order by profit DESC
```
2. TO count items and the total number of times a customer bought at least 1, when using “as” in SQL you will need ‘_” if the word is more than one
```Mysql
SELECT name, count(name)as nos_of_patronage FROM `sale` GROUP by name order by nos_of_patronage DESC
```
```Mysql
SELECT name, sold_by, quantity FROM `sale` WHERE name = 'BUTTER BREAD 5.00' and quantity BETWEEN '0' AND '1'
```
This is to see the total number of times customers bought just 1 butter bread from the store.
3. LET SAY I WANT TO FILTER THE NAME OF PRODUC TO SOLDBY TWO ITEMS
What command will I use.
```Mysql
SELECT quantity, name, sold_by, barcode FROM `sale` WHERE name ='BUTTER BREAD 5.00' AND sold_by ='vitalis' and 'SUPER GLUE'
```
You can use “and” as much as possible in SQL
```Mysql
SELECT * FROM `sale` GROUP BY name
```Mysql
```Mysql
SELECT * FROM `sale` WHERE name='BUTTER BREAD 5.00'
SELECT * FROM `sale` WHERE name='BUTTER BREAD 5.00' and sold_by='vitalis'
SELECT * FROM `sale` where date BETWEEN '2021-02-01' and '2021-02-28'
SELECT sum(total) FROM `sale` where date BETWEEN '2021-02-01' and '2021-02-28'
SELECT AVG(total) FROM `sale` where date BETWEEN '2021-02-01' and '2021-02-28'
SELECT sum(total) FROM `sale`
SELECT SUM(total)/ COUNT(total) FROM `sale` or SELECT avg(total) FROM `sale` ( this is to get the average of all sales)
SELECT sum(total) FROM `sale` WHERE date BETWEEN '2021-03-01' and '2021-03-30'
SELECT * from sale where name ='BUTTER BREAD 5.00' and date BETWEEN '2021-03-01' and '2021-03-31'
SELECT sum(total) from sale where name ='BUTTER BREAD 5.00' and date BETWEEN '2021-03-01' and '2021-03-31'
To get distinct items on a record (NB : you will need to add group by command to your SQl to perform this operation)
SELECT * FROM `sale` group by name
To list the distinct number of items in the record  and the prices
SELECT name, sum(total) FROM `sale` group by name
SELECT * FROM `sale`  WHERE trim(name)= 'RED PLANTAIN CHIPS 1.00'
Trying to get the profit per items sold
SELECT name, sum(total), sum(originalprice), sum(total)- sum(originalprice) FROM `sale` group by name
SELECT name, date, sum(total) -sum(originalprice*quantity) as profit FROM `sale` group by date order by profit DESC
```
GROUP BY is to select the format that you want your result to follow and it is used mostly with average, count, min,max,…
ORDER BY : IS to select the order that you want your result to follow , maybe in ascending or descending order (ASC means ascending)  while  (DESC or DSC means descending)
```Mysql
SELECT sold_by,sum(total)-sum(originalprice*quantity) FROM `sale` group by sold_by
```
```Mysql
SELECT sold_by,sum(total)-sum(originalprice*quantity) as profit FROM `sale` group by sold_by ORDER by profit DESC
```
4. TO SEE THE ITEM WITH THE HIGHEST PROFIT
```Mysql
SELECT name, sum(total)-sum(originalprice*quantity) as profit FROM `sale` GROUP by name order by profit DESC
```
<> means “is not” e.g <> 9 means is not 9 , u casn type any of the two in SQL but u need to type “IS NOT” In capital letter
```Mysql
SELECT * FROM `employees` where department = 'service' or department = 'support' and vacation_taken >=6.8 or vacation_taken <=17.9
```
5. what is the total number of product in the Supermarket ?
```Mysql
SELECT DISTINCT(name)  FROM `sale`
```
6. What is the QUANTITY OF SALES FROM HIGHEST TO LOWEST
```Mysql
SELECT name, quantity FROM sale order by quantity DESC
```
7. To see the product that 50 of it was bought at once
```Mysql
SELECT * FROM `sale` where quantity >= 50
```
```Mysql
SELECT * FROM `employees` WHERE department = 'services' OR department = 'sales'
```
```Mysql
SELECT * FROM `employees` WHERE department = 'marketing' AND tshirt_size = 'L'
```
8. This command isn’t bringing result on mysql, and it is on DB-SQL
   ```Mysql
SELECT * FROM `employees` WHERE department IS NOT 'sales'
```
```Mysql
SELECT * FROM `employees` WHERE not department = 'sales'
```
Not Department means employees that doesn’t belong to sales department
```Mysql
SELECT * FROM `employees` WHERE department!= 'sales'
```
! is the symbol for ‘not’ in SQL
9.  This command is use to limit data output on SQL
```Mysql
SELECT * FROM `employees` LIMIT 10
```
i.e it will return the total number of output to the first 10 and keep the rest
### UPPER, LOWER AND LENGTH FOR TEXT IN SQL
```Mysql
SELECT upper(first_name) FROM `employees`
```
10. This command will return all first name in capital letter (sumtn like this ADEOYE)
```Mysql
SELECT lower(first_name) FROM `employees`
```
11. This command will return all first name in small letter (sumtn like this adeoye)
```Mysql
SELECT length(first_name) FROM `employees`
```
12. This command will return the length of all first name (i.e the total number of letters, for adeoye now it will return 6,…
```Mysql
SELECT first_name FROM `employees` WHERE length(first_name) >= 8
```
13. This command will return all first name that are atleast 8 letters
- The difference between order by and group by in SQL
Order by is to have your data in ascending or descending order, orderby is sorting in SQL
Group by is use wen u are doing calculation and u want ur output to be understandable by a particular qualities of the data. To organize data in a specific way.
Group by is a way of summarizing you data in tabular form. Just like pivot table in excel
Limit and offset
```Mysql
SELECT first_name, last_name, tshirt_size FROM employees ORDER BY first_name
```
```Mysql
SELECT * FROM `employees` WHERE tshirt_size = 'L' LIMIT 15
```
14. This will limit the output to 15 and keep the rest
```Mysql
SELECT * FROM `employees` WHERE tshirt_size = 'L' LIMIT 1 OFFSET 10
```
15. This command above is telling SQL to look for employee that wears ‘L’ T-shirt, Then “offset 10” means that SQL shud keep the first 10 result of this command and display the 11th result.
So if there are 11 employees in all that wear ‘L’ t-shirt, SQL WILL ONLY DISPLAY THE LAST ONE CAUSE OF THE ‘OFFSET’
### Comparison operators in SQL are >, <, <=,>=, =,…
### Like Operator ; Finding Text in SQl Query
```Mysql
SELECT * FROM `employees` WHERE last_name LIKE 'T%'
```
16. This command is to Return all Employees that their last name begin with T
```Mysql
SELECT first_name FROM `employees` WHERE first_name LIKE 'T%%'
```
17. When T is in the beginning
```Mysql
SELECT first_name FROM `employees` WHERE first_name LIKE '_T%'
```
18. When T is in the middle
```Mysql
SELECT * FROM `employees` WHERE last_name LIKE '%t%'
```
19. This command is to Return all Employees that their last name has ‘T’ in it, be it in the beginning, middle or at the end of the name
```Mysql
SELECT * FROM `employees` WHERE last_name LIKE '_a%'
```
20. This command will return all the surname with ‘a’ as their 2nd character
### Calculating SUM with conditions
```Mysql
SELECT sum(num_desks) FROM `departments` where office_manager_id >=1 and office_manager_id <=5
SELECT sum(num_desks) FROM `departments` where id >=1 and id <=5
```
21. Thus will sum data from when id = 1 to id =5.
```Mysql
SELECT COUNT(id) from employees where vacation_taken > 20
```
22. TO get distinct Values from a data set (like the range of a data, to better understand what u r working with)
```Mysql
SELECT DISTINCT(tshirt_size) FROM `employees`
SELECT last_name,department,tshirt_size FROM `employees` WHERE department= 'legal' or department = 'support' LIMIT 1
‘LIMIT’ AND ‘OFFSET’ QUERY
The ‘LIMIT 1’ in this code  is saying I want to see just the first output of this query, for e.g if the output is meant to be 10, limit 1 will display just the first 1
SELECT last_name,department,tshirt_size FROM `employees` WHERE department= 'legal' or department = 'support' LIMIT 1 OFFSET 10
The ‘LIMIT 1’   and ‘OFFSET 10’ in this code  is saying I want to see the 11TH output of this query, for e.g if the output is meant to be 11, OFFSET 10 will display just the LAST ONE, Which is nos 11 output
SELECT last_name,department,tshirt_size FROM `employees` WHERE department= 'legal' or department = 'support' LIMIT 5 OFFSET 10
```
23. This will show 5 output after the first 10 that has been offset
```Mysql
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` WHERE `tshirt_size` = 'L' or tshirt_size = 'XL' ORDER BY first_name ASC, tshirt_size ASC
ORDER BY IS FOR ARRANGEMENT(Just like sort in Excel): It is for a data output to be in ascending or descending order. 

SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` WHERE `tshirt_size` = 'L' ORDER BY first_name LIMIT 1 OFFSET 10
This means; order by first_name in ascending order, limit the output to 1 and offset the first 10 output.
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` WHERE `tshirt_size` = 'L' ORDER BY first_name
order by first_name in ascending order
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` WHERE `tshirt_size` = 'L' ORDER BY first_name DESC, tshirt_size
order by first_name in descending order,  and  tshirt_size in ascending order
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` WHERE `tshirt_size` = 'L' ORDER BY first_name ASC, tshirt_size
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` ORDER BY first_name ASC, tshirt_size
SELECT `first_name`, `last_name`, `department`, `tshirt_size` FROM `employees` ORDER BY first_name, tshirt_size DESC
```
### Group by :TO ORGANIZE UR DATA IN A SPECIFIC WAY
```Mysql
SELECT department, count(department) FROM `employees` GROUP by department
This command is to count the total number of employees in each department , displaying the result per department. Count has to always follow by ‘group by’
SELECT department, count(department) FROM `employees` GROUP by department ORDER by department
```
24. This command is to count the total number of employees in each department and display department in ascending order
### ‘HAVING COUNT’ COMMAND
```Mysql
SELECT department, COUNT(department) FROM `employees` GROUP by department HAVING COUNT(department) < 10 ORDER by department
```
25. This command is to count the total number of employees in each department and display department  that their number of employees are less than 10.
```Mysql
SELECT tshirt_size, count(tshirt_size) as NosOfPersons FROM `employees` GROUP by tshirt_size
```
27. This command will display the total number of employees and their tshirt sizes
```Mysql
SELECT tshirt_size, count(tshirt_size) as NosOfPersons FROM `employees` GROUP by tshirt_size HAVING NOT tshirt_size = ''
```
28. This command will display the total number  and their tshirt size then remove the output for employees that disnt specify their sizes


### MORE QUERIES

SELECT first_name, last_name, department,tshirt_size FROM `employees` WHERE first_name LIKE '%t%' and department = 'services' or department = 'sales' and tshirt_size = 'L'
SELECT tshirt_size, count(tshirt_size) as NosOfPersons FROM `employees` GROUP by tshirt_size DESC
SUBQUERY; there is subquery for the same table and also from 2diff or more tables
SELECT * FROM `employees` WHERE vacation_taken = (SELECT MAX(vacation_taken) FROM employees)
This is to return the maximum value from the vacation taken column
NOT IN
This command is to Display the total number of items that are in store but have not been sold at the supermarket
SELECT * from item where name NOT IN (SELECT DISTINCT(name) from `sale`)
This gave 145items in all 
SELECT * FROM `item` WHERE `name` NOT IN (SELECT `name` FROM `sale`)
This gave 145items in all too
SELECT * from item where `barcode` NOT IN (SELECT `barcode` from `sale`)
I tried this and it gave result. It was giving 130items as result. Is it that the NAMES aren’t distinct?
Because I was expecting 145 items just like the result I have from using name
SELECT * FROM `item` WHERE `barcode` NOT IN (SELECT DISTINCT(barcode) FROM `sale`)
This gave 130items in all too
SELECT count(DISTINCT(barcode)) FROM `item`
To return distinct barcode (unique barcode) in SQL. Also, you can use the advance filter to get the range / uniqueness of your data on excel
COMBINING MORE THAN A TABLE
SELECT * FROM `employees` WHERE department = (SELECT name FROM departments WHERE state ='CA')
This command will return all the employees that are from “CA” California by checking the employee and Departments table to display result. The employees all belong to the business development department. THIS IS TO GET THE DETAILS OF WORKERS IN CARLIFORNIA.
SELECT name FROM departments WHERE state ='CA'
MAKE SURE YOU ALWAYS RUN THE SUBQUERY SEPARATELY, TO CONFIRM THAT SQL IS RETURNING A CORRECT INFORMATION
SELECT * FROM `employees` WHERE department IN (SELECT name FROM departments WHERE state ='MO')
This command will return all the employees that are from “MO” Mount Zoin regardless of the number of department that the employees are. This will be done by checking the employee and Departments table to display result. This is cos the ‘=’ in the 1st query was changed to ‘IN’
“=” IS THE SAME AS “IS”
SELECT * FROM `employees` WHERE department IN (SELECT name FROM departments WHERE state ='MO') ORDER BY department
Order by is to display the department in Alphabetical order
JOIN
SELECT first_name, last_name,name FROM `employees` JOIN departments ON employees.id = departments.office_manager_id
To join columns from two different tables to give a result
SELECT first_name, last_name, name FROM `employees` JOIN departments ON employees.id = departments.HeadOfDepartment_Id
Attaching the Head of the Department name using their id from another table.
The two joinings above are known as inner joining
SELECT first_name, last_name,date_complete FROM `employees` INNER JOIN compliance_training ON employees.id = compliance_training.employee_id
This will return only the employees that has completed their training
LEFT JOIN
SELECT first_name, last_name, date_complete FROM `employees` LEFT JOIN compliance_training ON compliance_training.date_complete =employees.id
This is to show the date each employee completed their training. And left join display all the result regardless of if employee has completed the training or not. It gives the report of the total number of employees in the dataset and returns value for the employees that have completed the training
I don’t know the difference between inner join and left join yet
Supported Types of Joins in MySQL
INNER JOIN: Returns records that have matching values in both tables
LEFT JOIN: Returns all records from the left table, and the matched records from the right table
RIGHT JOIN: Returns all records from the right table, and the matched records from the left table
CROSS JOIN: Returns all records from both tables
      

VLOOKUP, HLOOKUP & XLOOKUP IN SQL
SELECT first_name,last_name,state,department FROM `employees` JOIN departments ON employees.department =departments.name
I don’t understand how this is vlookup
Joining more than 2 Table
SELECT first_name, last_name, date_complete,state FROM employees JOIN compliance_training1 ON employees.id=compliance_training1.Employee_id JOIN departments ON employees.department = departments.name
DELETING IN SQL
DROP TABLE `table 1`
To delete a table from a database
ALTER TABLE purchaseofcloth DROP COLUMN Price
To Delete a column out of an existing table in SQL
Learning point: learn more on Queries with subquery
You can learn Alias as well
DELETING A ROW IN SQL
delete from student_biodata where MATRIC_NOS ='20100909' LIMIT 1
We can only alter a column in sql . we can only delete a row. Ie delete iS for row, Alter is for column.
Primary Key in SQL
The primary key is a column which uniquely defines a row in a database. The primary key is always going to be unique for each row in the table. Surrogate key isa primary key that doesn’t add any value to a database, it has no mapping to the real world. Natural key is a key that has a mapping to the real world. Eg SSN,..
A foregin key is a way we can define relationship btw tables; It’s a link between 2tables
ALTER TABLE `student_biodata` ADD PRIMARY KEY(`MATRIC_NOS`);
To change a column to Primary Key in SQL. Using a Primary key implies that you have a column in your dataset that is distinct. For E.g. ‘Matric number’ is distinct for student record.
Declaring a Primary Key makes it possible to edit your data just like you can do freely in SQL. Primary Key is what is used to delete and update and perform major operations on data in SQL
UPDATE `student_biodata` SET `GENDER` = 'Female' WHERE `MATRIC_NOS` = '21990117';
UPDATE `sale` SET `NAME` = 'Sugar Bread 2.00' WHERE `Barcode` = 'a5499e69be7ebe141cd627c2b6d258a1'
To Add Drop down to a column in SQL (Adding options like 'Satisfied','Unsatisfied', 'Dissatisfied)
Enum is to restrict Entry in SQL, to make the entry to have restricted options
This is to Modify an existing column
ALTER TABLE `student_biodata` CHANGE `SATISFACTORY_LEVEL` `SATISFACTORY_LEVEL` ENUM('Satisfied','Unsatisfied', 'Dissatisfied') CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT NULL
WHERE
WHERE GOES WITH <,>, <=,>=, <>
FOREIGN KEY
‘ON DELETE SET NULL’ This helps us to manage our foreign key
DESCRIBE sale
To see the details of a particular table in sql.
TO ADD AN EXTRA COLUM TO AN EXISTING TABLE
ALTER TABLE student ADD GPA decimal (3,2)
This will add a new column name GPA to the student table. (3,2) MEANS 3 TOTAL DIGIT, WHILE 2 OF THE DIGIT WILL BE AFTER THE DECIMAL.
TO REMOVE A COLUM FROM AN EXISTING TABLE
ALTER TABLE student DROP GPA 
 Exercise
My next line of action is to learn how to input data manually and also by using code.
NB: WHEN TRYING TO INPUT DATA IN SQL, NOT THAT THE FIRST LINE AND THE NEXT LINE WILL NOT START ON THE SAME WIDTH. SUMTN LIKE THIS
CREATE TABLE employee (
   emp_id INT PRIMARY KEY,
THE SPACE BEFORE “  emp_id INT PRIMARY KEY” IS REQUIRED FOR THE QUERY TO RUN SUCCEFULLY ON SQL. THIS APPLIES TO EVERY OTHER LINE THAT WILL BE AFTER “  emp_id INT PRIMARY KEY” AS WELL.
INSERTING VALUES INTO TABLES
INSERT INTO student VALUES (1, 'JACK', 'BIOLOGY',3.25)
'JACK' WAS IN QUOTE COS STUDENT NAME WAS DECLARE AS VARCHAR
If I want to add just two out of the parameters to the table, all I will need to do is to declare the parmeters that I am adding , then add.
INSERT INTO student (student_id,name) VALUES (2, 'claire')
NB: YOU CANT INSERT THE SAME PRIMARY KEY TWICE (ie the same name twice,…)

NOT NULL, UNIQUE AND DEFAULT ARE A WAY OF CONTROLLING YOUR DATA SET
NOT NULL
  first_name VARCHAR(40) NOT NULL,
NULL means no value. So it cant be null. The not null in this command means the first name cannot be empty. There must be an inputed value.
UNIQUE
  first_name VARCHAR(40) UNIQUE,
Unique here means the first name has to be unique for each row in the table.
DEFAULT
  first_name VARCHAR(40) DEFAULT ‘undecided’,
This command will return “undecided” for every first name that is not specified while inputing the student details.
AUTO_INCREMENT
Matric_number VARCHAR(40) AUTO_INCREMENT,
This will automatically give numbers to your values. For example
I have declare Matric_number as AUTO_INCREMENT, that means every other time I input a value in the SQL TABLE, SQL will automatically count and give the Matric_number column a number. In series say 1,2,3,4,…
UPDATING AND DELETING ROWS IN SQL
Updating means changing.
UPDATE `student_biodata` SET DEPT='WMA' WHERE DEPT='Water Resources and Agrometeorology'
This command will change 'Water Resources and Agrometeorology' to WMA
ALTER TABLE `student_biodata` CHANGE `GPA` `GPA` DECIMAL(3) NOT NULL;
This can be use to change from a data type to another data type
UPDATE `student_biodata` SET DEPT='Edu' WHERE First_Name ='Rebecca'
This command will is to change a detail for a specific entry. The condition will just be one of the details for that specific row.
WHERE is a command for filter in SQL
< > MEANS NOT EQUAL TO IN SQL
FEMI CALL TO EXPLAIN THIS
ALTER TABLE `student_biodata` CHANGE `GPA` `GPA` DECIMAL(3) NOT NULL
I HAD TO COPY THIS ON SQL AND RUN IT MANUALLY 
ALTER TABLE `student_biodata` CHANGE `GPA` `GPA` DECIMAL(3,2) NOT NULL
I HAD TO COPY THIS ON SQL AND RUN IT MANUALLY, THEN I ADDED  “2” FOR THE GPA TO SHOW MANUALLY ON  THE DATA I INPUTTED MANUALLY FOR STUDENT_BIODATA


ADVANCED DATA ENTRY IN SQL
ON DELETE SET NULL Is used to declare a foreign key in sql
Just as it is used here 
While declaring a key as foreign key, the key must have been created. For example to declare “mgr_id” as foreign key, the table with manager details must already exist.
The table have to exit before u can declare a foreign key from it.
“ON DELETE CASCADE”
CREATE TABLE branch (
  branch_id INT PRIMARY KEY,
  branch_name VARCHAR(40),
  mgr_id INT,
  mgr_start_date DATE,
  FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL


SQL FULL COURSE  DATABASE CODE
CREATE TABLE employee (
  emp_id INT PRIMARY KEY,
  first_name VARCHAR(40),
  last_name VARCHAR(40),
  birth_day DATE,
  sex VARCHAR(1),
  salary INT,
  super_id INT,
  branch_id INT
);

CREATE TABLE branch (
  branch_id INT PRIMARY KEY,
  branch_name VARCHAR(40),
  mgr_id INT,
  mgr_start_date DATE,
  FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);

ALTER TABLE employee
ADD FOREIGN KEY(branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL;

ALTER TABLE employee
ADD FOREIGN KEY(super_id)
REFERENCES employee(emp_id)
ON DELETE SET NULL;

CREATE TABLE client (
  client_id INT PRIMARY KEY,
  client_name VARCHAR(40),
  branch_id INT,
  FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
);

CREATE TABLE works_with (
  emp_id INT,
  client_id INT,
  total_sales INT,
  PRIMARY KEY(emp_id, client_id),
  FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
  FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);

CREATE TABLE branch_supplier (
  branch_id INT,
  supplier_name VARCHAR(40),
  supply_type VARCHAR(40),
  PRIMARY KEY(branch_id, supplier_name),
  FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);


-- -----------------------------------------------------------------------------

-- Corporate
INSERT INTO employee VALUES(100, 'David', 'Wallace', '1967-11-17', 'M', 250000, NULL, NULL);

INSERT INTO branch VALUES(1, 'Corporate', 100, '2006-02-09');

UPDATE employee
SET branch_id = 1
WHERE emp_id = 100;

INSERT INTO employee VALUES(101, 'Jan', 'Levinson', '1961-05-11', 'F', 110000, 100, 1);

-- Scranton
INSERT INTO employee VALUES(102, 'Michael', 'Scott', '1964-03-15', 'M', 75000, 100, NULL);

INSERT INTO branch VALUES(2, 'Scranton', 102, '1992-04-06');

UPDATE employee
SET branch_id = 2
WHERE emp_id = 102;

INSERT INTO employee VALUES(103, 'Angela', 'Martin', '1971-06-25', 'F', 63000, 102, 2);
INSERT INTO employee VALUES(104, 'Kelly', 'Kapoor', '1980-02-05', 'F', 55000, 102, 2);
INSERT INTO employee VALUES(105, 'Stanley', 'Hudson', '1958-02-19', 'M', 69000, 102, 2);

-- Stamford
INSERT INTO employee VALUES(106, 'Josh', 'Porter', '1969-09-05', 'M', 78000, 100, NULL);

INSERT INTO branch VALUES(3, 'Stamford', 106, '1998-02-13');

UPDATE employee
SET branch_id = 3
WHERE emp_id = 106;

INSERT INTO employee VALUES(107, 'Andy', 'Bernard', '1973-07-22', 'M', 65000, 106, 3);
INSERT INTO employee VALUES(108, 'Jim', 'Halpert', '1978-10-01', 'M', 71000, 106, 3);


-- BRANCH SUPPLIER
INSERT INTO branch_supplier VALUES(2, 'Hammer Mill', 'Paper');
INSERT INTO branch_supplier VALUES(2, 'Uni-ball', 'Writing Utensils');
INSERT INTO branch_supplier VALUES(3, 'Patriot Paper', 'Paper');
INSERT INTO branch_supplier VALUES(2, 'J.T. Forms & Labels', 'Custom Forms');
INSERT INTO branch_supplier VALUES(3, 'Uni-ball', 'Writing Utensils');
INSERT INTO branch_supplier VALUES(3, 'Hammer Mill', 'Paper');
INSERT INTO branch_supplier VALUES(3, 'Stamford Lables', 'Custom Forms');

-- CLIENT
INSERT INTO client VALUES(400, 'Dunmore Highschool', 2);
INSERT INTO client VALUES(401, 'Lackawana Country', 2);
INSERT INTO client VALUES(402, 'FedEx', 3);
INSERT INTO client VALUES(403, 'John Daly Law, LLC', 3);
INSERT INTO client VALUES(404, 'Scranton Whitepages', 2);
INSERT INTO client VALUES(405, 'Times Newspaper', 3);
INSERT INTO client VALUES(406, 'FedEx', 2);

-- WORKS_WITH
INSERT INTO works_with VALUES(105, 400, 55000);
INSERT INTO works_with VALUES(102, 401, 267000);
INSERT INTO works_with VALUES(108, 402, 22500);
INSERT INTO works_with VALUES(107, 403, 5000);
INSERT INTO works_with VALUES(108, 403, 12000);
INSERT INTO works_with VALUES(105, 404, 33000);
INSERT INTO works_with VALUES(107, 405, 26000);
INSERT INTO works_with VALUES(102, 406, 15000);
INSERT INTO works_with VALUES(105, 406, 130000);


FOREIGN KEY DECLARATION MANUALLY
CLICK YPUR DATABASE NAME in front of local database, then click on operations then  type, Then change the affected table type from MyISAM to InnoDB
THE COMMANDS TO ADD FOREIGN KEY WITHIN A TABLE AND OUTSIDE OF A TABLE
 when the foreign key is a primary key else where.

ALTER TABLE `works_with` ADD FOREIGN KEY (`Emp_id`) REFERENCES `employee`(`emp_id`) ON DELETE RESTRICT ON UPDATE RESTRICT; 
ALTER TABLE `works_with` ADD FOREIGN KEY (`client_id`) REFERENCES `client`(`client_id`) ON DELETE RESTRICT ON UPDATE RESTRICT;
THIS COMMAND IS USED TO ADD FOREIGN KEY WITHIN A TABLE: when the foreign key isn’t a primary key else where
  FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);


Underscore ( _) represent one character in excel
% represent any character
So something like this command “ like % LLC” is to return a value that have LLC in it.
Also “____-10” is to return a value with 10  as the month of October in it
UNION
You can use Union to add 2 tables together on a single column in SQL.
SELECT client_name from client UNION SELECT supplier_name FROM branch_supplier
JOINS
ANALYSIS IN SQL ON THE 4HOURS TUTORIAL VIDEO THAT I HAVE
QUESTION: The names and the sales of employees that sold more than 30000
SELECT first_name,Last_name,total_sales FROM employee JOIN works_with on employee.emp_id=works_with.Emp_id WHERE total_sales>30000
SELECT first_name,Last_name,total_sales FROM employee JOIN works_with on employee.emp_id=works_with.Emp_id WHERE total_sales>30000
NESTED QUERIES (I can use nested queries to get this same result above)
SELECT employee.first_name, employee.last_name FROM employee WHERE employee.emp_id IN ( SELECT works_with.Emp_id FROM `works_with` WHERE total_sales>30000 )

QUESTION: Find all clients who are handled by the branch that micheal scott manages, assuming you know the Micheal’s ID 
Answering this question using the nested queries
SELECT client.client_name FROM client WHERE client.branch_id="2" WHERE client.client_id IN ( SELECT branch.branch_name FROM branch WHERE branch_name = "scranton" WHERE branch.branch_name IN ( SELECT employee.first_name,employee.last_name FROM `employee` WHERE employee.emp_id="102" ))
Answering this question using the regular shortcut method
SELECT client_name FROM client JOIN branch ON client.branch_id=branch.branch_id WHERE branch.branch_id = "2"

ON DELETE SET NULL
This is about deleting entries in database when they have foreign keys
For on delete set null;
Example
  FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
If a foreign key is deleted, it set the entire value associated to NULL. If a foreign key is deleted it set the entire values like the primary key associated with this foreign key to NULL
FOR ON DELETE CASCADE
ONCE A FOREIGN KEY IS deleted, it delete the entire row of the data.
This is useful when we are interested in deleting a primary key. Cos a primary keel cannot have a NULL value. a primary key is crucial for the values in a row.
TRIGGERS (I DON’T UNDERSTAND)
BUT it’s a way of controlling what you input in your database
Chatgpt questions for intermediate SQL(question 1)
SELECT PatientVisit.PatientID, COUNT(PatientVisit.PatientID) AS NoofVisit, Patienttable.FirstName, Patienttable.LastName FROM appointments AS PatientVisit LEFT JOIN patients AS Patienttable ON PatientVisit.PatientID = Patienttable.PatientID GROUP BY PatientVisit.PatientID HAVING NoofVisit > 1



ADDING A NEW COLUMN TO AN EXISTING TABLE IN EXCEL
The Template is 
ALTER TABLE table_name
ADD column_name data_type;
ALTER TABLE employees ADD dEPARTMENT VARCHAR(255)

To add multiple column at once
ALTER TABLE employees ADD COLUMN department VARCHAR(100), ADD COLUMN hire_date DATE;
INPUTTING DATA TO A NEW COLUMN ADDED TO AN EXISTING TABLE IN EXCEL
The Template is 
UPDATE table_name SET column_name = value WHERE condition;
UPDATE employees SET Age = 25 WHERE EmployeeID = 1
UPDATE employees SET dEPARTMENT = 'Sales' WHERE EmployeeID = 1
INPUTTING DATA INTO MULTIPLE COLUMN ADDED TO AN EXISTING TABLE IN EXCEL
UPDATE employees SET Age = 30, department = 'Marketing' WHERE EmployeeID = 2
Addition in SQL
UPDATE `employees` set Age = Age + 2 WHERE EmployeeID =2

NYSC DATA ANALYSIS FROM DAYO
Highest nos of student from university
SELECT university_attended,COUNT(university_attended)AS UniNos FROM `nysc_data` GROUP by university_attended ORDER by university_attended desc limit 1
COMPARISON
COMPARISON  entails : We have greater than, less than, greater than =, Less than =, Not equal to
On numbers
!=           <>  represent Not equal to
SELECT fullname,year_of_graduation FROM `nysc_data` WHERE year_of_graduation <> 2020
SELECT fullname,year_of_graduation FROM `nysc_data` WHERE year_of_graduation != 2020
COMPARISON
On string 
SELECT fullname,university_attended FROM `nysc_data` WHERE university_attended !='Imo State University'
LOGICAL
And, or, Not

OR
SELECT * FROM `NYSC_Data` WHERE state_of_origin = 'ekiti' or state_of_origin ='ogun' or state_of_origin = 'lagos'
SHORTCUT FOR “OR”
SELECT * FROM `NYSC_Data` WHERE state_of_origin IN ('lagos','ekiti','ogun')
SHORTCUT FOR “NOT IN”
SELECT * FROM `NYSC_Data` WHERE state_of_origin NOT IN ('lagos','ekiti','ogun')
Not in
SELECT * FROM `NYSC_Data` WHERE university_attended NOT in ('Delta State University','Imo State University', 'Nnamdi Azikiwe University')

Wildcard Characters
Symbol 	Description
% 	Represents zero or more characters
_ 	Represents a single character
[] 	Represents any single character within the brackets *
^ 	Represents any character not in the brackets *
- 	Represents any single character within the specified range *
{} 	Represents any escaped character **
NOTE FROM TUTORIAL WITH DAYO
Dayo taught me that if I mistakenly type Delete on SQL, it will delete all data records.
Also, He mentioned to me that when you use “Update” I should always specify the column and row I want to update. If not properly stated. SQL will update all
Drop is for Database and Table
Alter is for Column and Row
WHERE is Where is used when you have a specific request on SQL
GROUPBY: When you are trying to find a result that you aren’t specific about, you use groupby 
Having - it to add more condition : Like condition from a condition . .Like there is already a condition, like groupby, order or another condition like where,… Like you already use a condition, but you want sql to perform another condition with having before giving the final result 

I now understand why a table name is attached to each if the column e.g appointment.Patientid
This is the reason why I was seeing this ambiguous error. 
I understand why my join formulae didn’t work. This was cos the data that I used it in before has a unique column name all through.


When SQl declares that a column is ambiguous. It means that the column name isn’t a distinct name, there are many column from another table with that same name
I get to know that I can a particular database or table jn new tab 
2ND day tutorial
You can drop Database and table while you can delete row and column
Varchar accomodate number, symbol and words. It is also known as strings
Data type generally talks about the data structure 

Koko SQL
Logical reasoning 
Conditional reasoning 
Comparison 

Type of Errors
Logical Error ; You code give result but the answer isn’t corrent
Syntax Error: code no run

And, or, not
And: Daddy and mummy from Iwo. These conditions have to be met for SQL to give result
Or : one of them is from iwo. Once one of the conditions is met. Then it gives result
Not: none of them is from iwo. Or not Ileogbo

Not in
SELECT * FROM `NYSC_Data` WHERE university_attended NOT in ('Delta State University','Imo State University', 'Nnamdi Azikiwe University')

NOTE
UPDATE IS TO EDIT
INSERT IS TO ADD NEW ROW

