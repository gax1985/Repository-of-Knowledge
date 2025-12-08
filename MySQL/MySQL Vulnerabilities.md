




# Common Weaknesses : 




1. Leaving everything as *default settings* : 
   
   
>[!note]
>
>The default *username* for MySQL is "*sa*" or **system admin**. This means that for hackers, half of the battle is won!


2. **No Lockouts**!
   

>[!note]
>
 >It means that we can *brute-force* MySQL to our hearts' content! 


3. **Active-Directory Related Information** 
   
   
   
   > [!note]
   > 
   > If the hacker gets inside the *MySQL Database*, they may be able to get information about **Active Directory Accounts**!
   > 



4. **The *xp_cmdshell* Vulnerability**


>[!note]
>
>This provides the MySQL user the ability to run system commands from the MySQL terminal


5. ***Hard-Coding* Credentials into Configuration files** 
   
   


