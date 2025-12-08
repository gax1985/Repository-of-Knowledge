



 


The first data model shown to a client for whom you are designing a database, after first analyzing their business rules, is usually a detailed description of the MYSQL tables with their attributes and data types defined.  
  
TRUE     ---> Correct Answer :  **FALSE**


"Describe your business to me". you work on the design, and say "is this what you meant? " you have no idea what type of database you will use. You will not show the client "VARCHAR(40)". You will  show the ERD diagram. You are not at that time decidingf the 
  
  

  
  
  
Field refers to a collection of related records.  
  
TRUE   ---> Correct Answer :  **FALSE**
  
  
  
One disadvantage of using a DBMS is that it increases the risk of data security breaches.  
  
TRUE  ---> Correct Answer :  **FALSE**


There are all types of security implemented on top of your data. It does not matter what data you use. Rules and privileges, where one person can access it, all of which is inherit in DMBSes. 
  
  
  
In the example done in class, the relationship of STUDENT to COURSE is described in an initial ERD diagram as a _____________ relationship.  
  
  
One to Many ---> Correct Answer :  **Many to Many** 


1. ________ is the result of processing and revealing the meaning of raw facts.

**Information**


Data is the result of processing raw facts to reveal the meaning.  
  
TRUE   ---> Correct Answer :  **FALSE** 

Why ? The result of processing raw facts to reveal meaning is **information**.  What reweals the meaning? 




A frield is collectopm pf re;lated records --> **FALSE**



A set of one of more fields describing a person, place or thing ---> **Record**. 
(What is your record in the school's database? )


Metadata describes data characteristics --> True


___________ are the result of formatting disorganized facts in order to facilitate use and generation of information. --->  **Structured Data**


Given 3 entities, FACULTY, DEPARTMENT and COURSE and the following business rules: "There are many Departments. There are many Faculty . Each Department has many courses. Department Chairs are chosen from the Faculty. A Faculty member may only chair one Department. A Department may only have one  Chair."; the relationship of FACULTY to DEPARTMENT is described as a ________________ relationship.

--> One to One






## Common Threats 



We spoke about the threats last day. 


Today, we are using ROOT, we log in to MySQL, we have to create users to use the database. We want to create user accounts. Teh thing to remember : just like a phone number or email address : the login account name (username) is only half of the database username. The other half is where you are coming from. LOCALHOST when talking to the database server via LOOPBACK, so it would be username@localhost. It can be an IP address, where you restrict access to only that IP address. 




If you make the username as such as the username is "myname@'%' "




CREATE USER 'my name' '@' Localhost identified by 'mypassword';


This is how you create a user to allow access to the DBMS. as Root you can log in everywhere, but at this point , the user you create can access to the database you define. 


The privilege/access is done with GRANTS. 


SHOW GRANTSS for myname@localhost;  ---> grants access to that database. 



Sometimes you have to use quotes, and sometimes you do not. 


![[Pasted image 20231026095416.png]]



USE MYSQL;  --> use the database MYSQL


If you want to SELECT * FROM mysql.user WHERE user = 'myname'\G 



Once we have a user created : 







GRANT ALLL on *.* TO 'myname'@'localhost'; they get all rights except for one , which privilege is missing ? practice until Tuesday. 


By default when you say grant all , they get all the privileges except the privilege to grant privileges to other users. 


![[Pasted image 20231026095847.png]]



So , there is something wrong with what Ron is doing here : 


GRANT ALL ON *.* to 'myname'@'localhost'


GRANT GRANT ON * . *  , they get the ability to assign privileges to a database. You should not grant privileges to users. We are setting up an account, we grant privileges to a user. We should never do so. We should have a role called "Warehouse clerk"



We can DROP a user, to get him out of the database :


![[Pasted image 20231026100140.png]]



![[Pasted image 20231026100151.png]]


We can grant privileges on a specific database to all the tables : 



GRANT [ privilege ] ON *.* TO ['user@host'] ; # all databases all tables








We should be dooing this : 


CReate a role :

CREATE ROLE customerservice;

GRANT SELECT, UPDATE, INSERT ON [database.customertable] TO customerservice;


(like Groups in Linux)


GRANT customerservice to myname@localhost;


SHOW GRANTS FOR myname@localhost;



![[Pasted image 20231026100424.png]]







HOMEWORK : 




Check out the slides : 







![[Pasted image 20231026100921.png]]
