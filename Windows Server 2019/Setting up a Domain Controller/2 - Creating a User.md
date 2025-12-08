



# Steps :


1. Launch the **Server Manager** application. 
2. Select *Tools*
3. Select *Active Directory Users and Computers*. 
   
   >[!note]
   >
   >The **Active Directory Users and Computers** section is the place to manage *Users*, *Groups* and *Computers*.

4. Find your *Username*.
5. Right-Click on your *Username*, Right-Click on the **username** , select "*Add to Group*" then enter "**Domain Admins**" in the *Object Name* field.
6. Create a non-privileged **Domain User**. You can do this by Right-Clicking on the **User** folder, selecting *New*, followed by **User**.
7. Enable the option for the new *Non-Privileged Domain User* to **change their password on the next login**. 

>[!hint]
>
>With your users all set up, we can get rid of the local administrator account. Having a local administrator account with the same credentials on each machine within a domain is a common practice. However, if one machine is compromised, it’s very easy for a hacker to compromise your DC with the local admin credentials (or NTLMv1 hash). Therefore, limiting the total amount of administrator accounts is advised. To do so, please issue the following command as an *Adminstrator* : 
>
>	net user Administrator /active:no
>
>If you would like to double-check the status of the *Local Administrator's account* :
>
>	net user Administrator
>	


8. If you would like to see the other users on your domain : 
   
	net user /domain

... It might be a good idea to check the groups in which the user belongs to : 

	 net user <username> /domain

... and if you would like to see information on every group that is present on the Domain :

	net group /domain

... and for more information on one group : 

	net group <groupname> /domain


9. Let us create the new *Organizational Unit* for our user : 
   
   
>1. Select **Active Directory Users and Computers** from under *Tools*.
>2. Right-Click on the Domain, and then select *New* and then **Organizational Unit**. 
>3. Please select the **Global Scope**. For the **Group Type**, please select "*Security"
>4. After successfully creating the new group, we should add the *Non-Privileged User* to the group. Right-Click on the *Non-Privileged User's Username*, and then select **Add to Group**. 









