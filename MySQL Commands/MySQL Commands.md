

## Roles 


#### Create a User :  


>CREATE USER myname;



>SHOW GRANTS for myname@localhost;




>SELECT *  FROM mysql.user;



>grant grant option on * . *  to 'myname'@'localhost';



>Select * from mysql.user;



>drop user myname@localhost;



>select * from mysql.user where user = 'myname' \G



>create user 'myname'@'localhost' identified by 'mypassword';


>grant ALL on * . * to 'myname'@'localhost' with GRANT Options;


>drop user myname@localhost;


> CREATE role customerservice;



>CREATE ROLE customerservice; 



>USE store; 


>SHOW tables;




>DESCRIBE customer; 




>DROP TABLE customer;



>DROP DATABASE store;





>CREATE DATABASE store;


>CREATE DATABASE store;



>CREATE TABLE customer (name VARCHAR(40));


>SHOW TABLES; (to check:)


>DESCRIBE customer;




>GRANT select(to view the information), update (to change the phone number), insert(to add new customers into the database, this will come from the customer rules, where the boss could need the customer service representative to do certain tasks, and they want them to have rights to a specific table) on store.customer to customerservice; 


>SELECT FROM mysql.user where user="myname" \G




>SELECT FROM mysql.user where user="myname" \G


>CREATE USER 'myname'@'localhost' identified by 'mypassword';



>SHOW GRANTS for myname@localhost;