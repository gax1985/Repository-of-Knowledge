

# Database Commands : 


## Create a Database 


	CREATE DATABASE database_name;



## Use a Database 


	USE database_name;



# Tables Commands


"Two tables (Relations) called R and S with the fields R.A, R.B, R.C and S.D, S.D, S.E (all integer types) with the values shown below."

## Create a Table 


	CREATE TABLE table_name ( column1 datatype, column2 datatype, column3 datatype, ); 


>CREATE TABLE r (
>A int, 
>B int,
>C int
>);



>CREATE TABLE s (
>A int,
>D int,
>E int
>);



## Insert Data into a Table 


>INSERT INTO r 
>VALUES (2, 4, 6),
>(4, 6, 8),
>(6, 8, 10);


INSERT INTO s 
>VALUES (2, 8, 10),
>(4, 10, 12),
>(6, 12, 14);


## Left-Join JOIN Command



#### Manual : 


### SQL LEFT JOIN Keyword

The `LEFT JOIN` keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

### LEFT JOIN Syntax

SELECT _column_name(s)_  
FROM _table1_  
LEFT JOIN _table2  
ON table1.column_name_ = table2.column_name_;

**Note:** In some databases LEFT JOIN is called LEFT OUTER JOIN.

![SQL LEFT JOIN](https://www.w3schools.com/sql/img_left_join.png)

---

##### Demo Database

In this tutorial we will use the well-known Northwind sample database.

Below is a selection from the "Customers" table:

|CustomerID|CustomerName|ContactName|Address|City|PostalCode|Country|
|---|---|---|---|---|---|---|
|1|Alfreds Futterkiste|Maria Anders|Obere Str. 57|Berlin|12209|Germany|
|2|Ana Trujillo Emparedados y helados|Ana Trujillo|Avda. de la Constitución 2222|México D.F.|05021|Mexico|
|3|Antonio Moreno Taquería|Antonio Moreno|Mataderos 2312|México D.F.|05023|Mexico|

And a selection from the "Orders" table:

|OrderID|CustomerID|EmployeeID|OrderDate|ShipperID|
|---|---|---|---|---|
|10308|2|7|1996-09-18|3|
|10309|37|3|1996-09-19|1|
|10310|77|8|1996-09-20|2|

---

#### SQL LEFT JOIN Example

The following SQL statement will select all customers, and any orders they might have:

### Example[Get your own SQL Server](https://www.w3schools.com/sql/sql_server.asp "W3Schools Spaces")

SELECT Customers.CustomerName, Orders.OrderID  
FROM Customers  
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID  
ORDER BY Customers.CustomerName;




[Try it Yourself »](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join_left)

**Note:** The `LEFT JOIN` keyword returns all records from the left table (Customers), even if there are no matches in the right table (Orders).




-----------------



## SQL INNER JOIN



The `INNER JOIN` keyword selects records that have matching values in both tables.

Let's look at a selection of the [**Products**](https://www.w3schools.com/sql/trysql.asp?filename=trysql_products) table:

|ProductID|ProductName|CategoryID|Price|
|---|---|---|---|
|1|Chais|1|18|
|2|Chang|1|19|
|3|Aniseed Syrup|2|10|

And a selection of the [**Categories**](https://www.w3schools.com/sql/trysql.asp?filename=trysql_categories) table:

|CategoryID|CategoryName|Description|
|---|---|---|
|1|Beverages|Soft drinks, coffees, teas, beers, and ales|
|2|Condiments|Sweet and savory sauces, relishes, spreads, and seasonings|
|3|Confections|Desserts, candies, and sweet breads|

We will join the Products table with the Categories table, by using the `CategoryID` field from both tables:

### Example[Get your own SQL Server](https://www.w3schools.com/sql/sql_server.asp "W3Schools Spaces")

Join Products and Categories with the INNER JOIN keyword:

SELECT ProductID, ProductName, CategoryName  
FROM Products  
INNER JOIN Categories ON Products.CategoryID = Categories.CategoryID;

[Try it Yourself »](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join_inner_prod)

![SQL INNER JOIN](https://www.w3schools.com/sql/img_inner_join.png)

**Note:** The `INNER JOIN` keyword returns only rows with a match in both tables. Which means that if you have a product with no CategoryID, or with a CategoryID that is not present in the Categories table, that record would not be returned in the result.

---

#### Syntax

`SELECT _column_name(s)_   FROM _table1_   INNER JOIN _table2   _ON _table1.column_name_ = _table2.column_name_;`

---

---

#### Naming the Columns

It is a good practice to include the table name when specifying columns in the SQL statement.

### Example

Specify the table names:

SELECT Products.ProductID, Products.ProductName, Categories.CategoryName  
FROM Products  
INNER JOIN Categories ON Products.CategoryID = Categories.CategoryID;

[Try it Yourself »](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join_inner_prod2)

The example above works without specifying table names, because none of the specified column names are present in both tables. If you try to include `CategoryID` in the `SELECT` statement, you will get an error if you do not specify the table name (because `CategoryID` is present in both tables).

---

## JOIN or INNER JOIN

`JOIN` and `INNER JOIN` will return the same result.

`INNER` is the default join type for `JOIN`, so when you write `JOIN` the parser actually writes `INNER JOIN`.

### Example

JOIN is the same as INNER JOIN:

SELECT Products.ProductID, Products.ProductName, Categories.CategoryName  
FROM Products  
JOIN Categories ON Products.CategoryID = Categories.CategoryID;

[Try it Yourself »](https://www.w3schools.com/sql/trymysql.asp?filename=trysql_select_join_inner_prod3)

---

## JOIN Three Tables

The following SQL statement selects all orders with customer and shipper information:

### Example

SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName  
FROM ((Orders  
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)  
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);

[Try it Yourself »](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join_inner2)

---

#### Test Yourself With Exercises

##### Exercise:

Choose the correct `JOIN` clause to select all records from the two tables where there is a match in both tables.

SELECT *
FROM Orders

ON Orders.CustomerID=  
Customers.CustomerID;

[Start the Exercise](https://www.w3schools.com/sql/exercise.asp?filename=exercise_join2)


   [![Get Certified](https://www.w3schools.com/images/img_spaces_up_generic_sql_300.pn



---------------



## SQL UPDATE Statement


The `UPDATE` statement is used to modify the existing records in a table.

### UPDATE Syntax

`UPDATE _table_name_   SET _column1_ = _value1_, _column2_ = _value2_, ...   WHERE _condition_;`

**Note:** Be careful when updating records in a table! Notice the `WHERE` clause in the `UPDATE` statement. The `WHERE` clause specifies which record(s) that should be updated. If you omit the `WHERE` clause, all records in the table will be updated!

---

## Demo Database

Below is a selection from the [**Customers**](https://www.w3schools.com/sql/trysql.asp?filename=trysql_customers) table used in the examples:

|CustomerID|CustomerName|ContactName|Address|City|PostalCode|Country|
|---|---|---|---|---|---|---|
|1|Alfreds Futterkiste|Maria Anders|Obere Str. 57|Berlin|12209|Germany|
|2|Ana Trujillo Emparedados y helados|Ana Trujillo|Avda. de la Constitución 2222|México D.F.|05021|Mexico|
|3|Antonio Moreno Taquería|Antonio Moreno|Mataderos 2312|México D.F.|05023|Mexico|
|4|Around the Horn|Thomas Hardy|120 Hanover Sq.|London|WA1 1DP|UK|
|5|Berglunds snabbköp|Christina Berglund|Berguvsvägen 8|Luleå|S-958 22|Sweden|

---

## UPDATE Table

The following SQL statement updates the first customer (CustomerID = 1) with a new contact person _and_ a new city.

### Example[Get your own SQL Server](https://www.w3schools.com/sql/sql_server.asp "W3Schools Spaces")

UPDATE Customers  
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'  
WHERE CustomerID = 1;

The selection from the "Customers" table will now look like this:

|CustomerID|CustomerName|ContactName|Address|City|PostalCode|Country|
|---|---|---|---|---|---|---|
|1|Alfreds Futterkiste|Alfred Schmidt|Obere Str. 57|Frankfurt|12209|Germany|
|2|Ana Trujillo Emparedados y helados|Ana Trujillo|Avda. de la Constitución 2222|México D.F.|05021|Mexico|
|3|Antonio Moreno Taquería|Antonio Moreno|Mataderos 2312|México D.F.|05023|Mexico|
|4|Around the Horn|Thomas Hardy|120 Hanover Sq.|London|WA1 1DP|UK|
|5|Berglunds snabbköp|Christina Berglund|Berguvsvägen 8|Luleå|S-958 22|Sweden|

---

---

## UPDATE Multiple Records

It is the `WHERE` clause that determines how many records will be updated.

The following SQL statement will update the ContactName to "Juan" for all records where country is "Mexico":

### Example

UPDATE Customers  
SET ContactName='Juan'  
WHERE Country='Mexico';

The selection from the "Customers" table will now look like this:

|CustomerID|CustomerName|ContactName|Address|City|PostalCode|Country|
|---|---|---|---|---|---|---|
|1|Alfreds Futterkiste|Alfred Schmidt|Obere Str. 57|Frankfurt|12209|Germany|
|2|Ana Trujillo Emparedados y helados|Juan|Avda. de la Constitución 2222|México D.F.|05021|Mexico|
|3|Antonio Moreno Taquería|Juan|Mataderos 2312|México D.F.|05023|Mexico|
|4|Around the Horn|Thomas Hardy|120 Hanover Sq.|London|WA1 1DP|UK|
|5|Berglunds snabbköp|Christina Berglund|Berguvsvägen 8|Luleå|S-958 22|Sweden|

---

## Update Warning!

Be careful when updating records. If you omit the `WHERE` clause, ALL records will be updated!

### Example

UPDATE Customers  
SET ContactName='Juan';

The selection from the "Customers" table will now look like this:

|CustomerID|CustomerName|ContactName|Address|City|PostalCode|Country|
|---|---|---|---|---|---|---|
|1|Alfreds Futterkiste|Juan|Obere Str. 57|Frankfurt|12209|Germany|
|2|Ana Trujillo Emparedados y helados|Juan|Avda. de la Constitución 2222|México D.F.|05021|Mexico|
|3|Antonio Moreno Taquería|Juan|Mataderos 2312|México D.F.|05023|Mexico|
|4|Around the Horn|Juan|120 Hanover Sq.|London|WA1 1DP|UK|
|5|Berglunds snabbköp|Juan|Berguvsvägen 8|Luleå|S-9|