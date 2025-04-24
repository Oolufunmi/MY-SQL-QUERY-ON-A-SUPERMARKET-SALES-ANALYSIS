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
- You can use “and” as much as possible in SQL
```Mysql
SELECT * FROM `sale` GROUP BY name
```
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
```
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
```Mysql
SELECT first_name, last_name, department,tshirt_size FROM `employees` WHERE first_name LIKE '%t%' and department = 'services' or department = 'sales' and tshirt_size = 'L'
SELECT tshirt_size, count(tshirt_size) as NosOfPersons FROM `employees` GROUP by tshirt_size DESC
SUBQUERY; there is subquery for the same table and also from 2diff or more tables
SELECT * FROM `employees` WHERE vacation_taken = (SELECT MAX(vacation_taken) FROM employees)
```
29. This is to return the maximum value from the vacation taken column
NOT IN
30. This command is to Display the total number of items that are in store but have not been sold at the supermarket
```Mysql
SELECT * from item where name NOT IN (SELECT DISTINCT(name) from `sale`)
```
This gave 145items in all 
```Mysql
SELECT * FROM `item` WHERE `name` NOT IN (SELECT `name` FROM `sale`)
```
This gave 145items in all too
```Mysql
SELECT * from item where `barcode` NOT IN (SELECT `barcode` from `sale`)
```
- I tried this and it gave result. It was giving 130items as result. Is it that the NAMES aren’t distinct?
- Because I was expecting 145 items just like the result I have from using name
```
SELECT * FROM `item` WHERE `barcode` NOT IN (SELECT DISTINCT(barcode) FROM `sale`)
```
This gave 130items in all too
```Mysql
SELECT count(DISTINCT(barcode)) FROM `item`
```
31. To return distinct barcode (unique barcode) in SQL. Also, you can use the advance filter to get the range / uniqueness of your data on excel

### COMBINING MORE THAN A TABLE
```Mysql
SELECT * FROM `employees` WHERE department = (SELECT name FROM departments WHERE state ='CA')
```
32. This command will return all the employees that are from “CA” California by checking the employee and Departments table to display result. The employees all belong to the business development department. THIS IS TO GET THE DETAILS OF WORKERS IN CARLIFORNIA.
```Mysql
SELECT name FROM departments WHERE state ='CA'
```
- MAKE SURE YOU ALWAYS RUN THE SUBQUERY SEPARATELY, TO CONFIRM THAT SQL IS RETURNING A CORRECT INFORMATION
  ```Mysql
SELECT * FROM `employees` WHERE department IN (SELECT name FROM departments WHERE state ='MO')
```
33. This command will return all the employees that are from “MO” Mount Zoin regardless of the number of department that the employees are. This will be done by checking the employee and Departments table to display result. This is cos the ‘=’ in the 1st query was changed to ‘IN’
“=” IS THE SAME AS “IS”
```Mysql
SELECT * FROM `employees` WHERE department IN (SELECT name FROM departments WHERE state ='MO') ORDER BY department
```
Order by is to display the department in Alphabetical order
### JOIN
```Mysql
SELECT first_name, last_name,name FROM `employees` JOIN departments ON employees.id = departments.office_manager_id
```
34. To join columns from two different tables to give a result
```Mysql
SELECT first_name, last_name, name FROM `employees` JOIN departments ON employees.id = departments.HeadOfDepartment_Id
```
Attaching the Head of the Department name using their id from another table.
The two joinings above are known as inner joining
```Mysql
SELECT first_name, last_name,date_complete FROM `employees` INNER JOIN compliance_training ON employees.id = compliance_training.employee_id
```
35. This will return only the employees that has completed their training
### LEFT JOIN
```Mysql
SELECT first_name, last_name, date_complete FROM `employees` LEFT JOIN compliance_training ON compliance_training.date_complete =employees.id
```
36. This is to show the date each employee completed their training. And left join display all the result regardless of if employee has completed the training or not. It gives the report of the total number of employees in the dataset and returns value for the employees that have completed the training
I don’t know the difference between inner join and left join yet

Supported Types of Joins in MySQL
INNER JOIN: Returns records that have matching values in both tables
LEFT JOIN: Returns all records from the left table, and the matched records from the right table
RIGHT JOIN: Returns all records from the right table, and the matched records from the left table
CROSS JOIN: Returns all records from both tables
      

### VLOOKUP, HLOOKUP & XLOOKUP IN SQL
```Mysql
SELECT first_name,last_name,state,department FROM `employees` JOIN departments ON employees.department =departments.name
```
I don’t understand how this is vlookup

```Mysql
SELECT first_name, last_name, date_complete,state FROM employees JOIN compliance_training1 ON employees.id=compliance_training1.Employee_id JOIN departments ON employees.department = departments.name
```
### DELETING IN SQL
```Mysql
DROP TABLE `table 1`
```
To delete a table from a database
ALTER TABLE purchaseofcloth DROP COLUMN Price
To Delete a column out of an existing table in SQL
Learning point: learn more on Queries with subquery
You can learn Alias as well

### DELETING A ROW IN SQL
delete from student_biodata where MATRIC_NOS ='20100909' LIMIT 1
We can only alter a column in sql . we can only delete a row. Ie delete iS for row, Alter is for column.
Primary Key in SQL
The primary key is a column which uniquely defines a row in a database. The primary key is always going to be unique for each row in the table. Surrogate key isa primary key that doesn’t add any value to a database, it has no mapping to the real world. Natural key is a key that has a mapping to the real world. Eg SSN,..
A foregin key is a way we can define relationship btw tables; It’s a link between 2tables
```Mysql
ALTER TABLE `student_biodata` ADD PRIMARY KEY(`MATRIC_NOS`);
```
37. To change a column to Primary Key in SQL. Using a Primary key implies that you have a column in your dataset that is distinct. For E.g. ‘Matric number’ is distinct for student record.
Declaring a Primary Key makes it possible to edit your data just like you can do freely in SQL. Primary Key is what is used to delete and update and perform major operations on data in SQL
```Mysql
UPDATE `student_biodata` SET `GENDER` = 'Female' WHERE `MATRIC_NOS` = '21990117';
UPDATE `sale` SET `NAME` = 'Sugar Bread 2.00' WHERE `Barcode` = 'a5499e69be7ebe141cd627c2b6d258a1'
To Add Drop down to a column in SQL (Adding options like 'Satisfied','Unsatisfied', 'Dissatisfied)
```
Enum is to restrict Entry in SQL, to make the entry to have restricted options

### This is to Modify an existing column
```Mysql
ALTER TABLE `student_biodata` CHANGE `SATISFACTORY_LEVEL` `SATISFACTORY_LEVEL` ENUM('Satisfied','Unsatisfied', 'Dissatisfied') CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT NULL
```

WHERE
WHERE GOES WITH <,>, <=,>=, <>
FOREIGN KEY
‘ON DELETE SET NULL’ This helps us to manage our foreign key
DESCRIBE sale
To see the details of a particular table in sql.

38. TO ADD AN EXTRA COLUM TO AN EXISTING TABLE
```Mysql
ALTER TABLE student ADD GPA decimal (3,2)
```
This will add a new column name GPA to the student table. (3,2) MEANS 3 TOTAL DIGIT, WHILE 2 OF THE DIGIT WILL BE AFTER THE DECIMAL.. 
39. TO REMOVE A COLUM FROM AN EXISTING TABLE
ALTER TABLE student DROP GPA 
 
 ### Exercise
My next line of action is to learn how to input data manually and also by using code.
NB: WHEN TRYING TO INPUT DATA IN SQL, NOT THAT THE FIRST LINE AND THE NEXT LINE WILL NOT START ON THE SAME WIDTH. SUMTN LIKE THIS



Underscore ( _) represent one character in excel
% represent any character
So something like this command “ like % LLC” is to return a value that have LLC in it.
Also “____-10” is to return a value with 10  as the month of October in it
UNION
You can use Union to add 2 tables together on a single column in SQL.
SELECT client_name from client UNION SELECT supplier_name FROM branch_supplier
JOINS

