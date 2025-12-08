

## Show Tables 


	SHOW TABLES; 


## Analyze a Table 


	DESCRIBE table_name 



## Create a Table 


	CREATE TABLE table_name ( column1 datatype, column2 datatype, column3 datatype, ); 



DROP TABLE table_name; 



ALTER TABLE table_name 


ADD column_name datatype; 


ALTER TABLE table_name 


DROP COLUMN column_name; 


ALTER TABLE table_name MODIFY COLUMN column_name datatype; SELECT * FROM table_name; SELECT column1, column2 ... FROM table_name; SELECT DISTINCT column1, column2, ... FROM table_name; SELECT column1, column2, ... FROM table_name WHERE condition; SELECT column1, column2, ... FROM table_name WHERE condition; ORDER BY column1 ASC/DESC; SELECT column1, column2, ... FROM table_name WHERE condition; GROUP BY column1 SELECT column1, column2, ... FROM table_name WHERE condition; LIMIT number_of_results; SELECT column1, column2, ... FROM table1 INNER JOIN* table2 ON table1.column_name = table2.column_name; *LEFT JOIN / RIGHT JOIN / FULL JOIN / SELF JOIN




