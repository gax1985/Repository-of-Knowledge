

> [!todo] 
> - [x] Create a database AbcCorp
> - [x] Create a table in the database called employee that has four columns called empid (integer, primarykey) name (varchar), salary (decimal), and phonenumber (varchar).
>- [x] Create a role called clerk and grant privileges to this role that will allow SELECT privilege on employee.empid, employee.name and employee.phonenumber but no access to employee.salary
>- [ ] Create a role called supervisor and grant SELECT on employee.empid, and SELECT and UPDATE on all other columns in the employee table
>- [ ] Create a role called dba and GRANT all privileges with GRANT option on all tables in the database.
>- [ ] Create one user for each role (i.e. 3 users).
>- [ ] Populate the Employee table with these users, including name salary and phone number for each.
>- [ ] Assign the appropriate role to each user. 



# Database Commands : 


"Create a database AbcCorp"

## Create a Database 


	CREATE DATABASE database_name;


## Use a Database 


	USE database_name;



---------------------------------


# Tables Commands


"Create a table in the database called employee that has four columns called empid (integer, primary  key) name (varchar), salary (decimal), and phonenumber (varchar)."

## Create a Table 


	CREATE TABLE table_name ( column1 datatype, column2 datatype, column3 datatype, ); 


>CREATE TABLE employee(
>empid int NOT NULL,
>name VARCHAR(255),
>salary decimal,
>phonenumber VARCHAR(255),
>PRIMARY KEY (empid) 
>);


----------------------------------




# Roles 



"Create a role called clerk ... "


## Create a Role (Clerk)


	CREATE ROLE clerk; 



## Grant Privileges to a Role 


" ... and grant privileges to this role that will allow SELECT privilege on  
employee.empid, employee.name and employee.phonenumber but no access to employee.salary"


	 GRANT SELECT (empid, name, phonenumber) ON AbcCorp.employee TO 'clerk'; 


#### GRANT Command Information 


>GRANT priv_type [(column_list)] [, priv_type [(column_list)]] ON [object_type] priv_level TO user_or_role;



## Create another Role (Supervisor)


"Create a role called supervisor ... "


	CREATE ROLE supervisor; 




## Grant Privileges to a Role (Supervisor)



""... and grant SELECT on employee.empid, and SELECT and UPDATE on all other columns in the employee table"


	GRANT SELECT, UPDATE ON abccorp.employee to 'supervisor'



	GRANT SELECT ON abccorp.employee(empid) TO 'supervisor'; 




### Another Method : 


1. Create the role Supervisor : 

	CREATE ROLE supervisor;


2. Grant SELECT and UPDATE privileges on abccorp.employee to 'supervisor':

	GRANT SELECT, UPDATE ON abccorp.employee to 'supervisor'


3. Drop the UPDATE privilege on the empid column of the employee table : 

-

4. Grant SELECT privilege only to the Supervisor role.


