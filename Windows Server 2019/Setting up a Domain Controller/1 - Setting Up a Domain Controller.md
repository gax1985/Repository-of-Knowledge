




# Steps : 




1. Launch **Server Manager**
2. Select "**Add Roles of Features**"
3. During the installation steps, please select *Role-Based Installation*.
4. Choose the **server**!
5. When you reach the **Server Roles** screen, please select "*Active Directory Domain Services*".
6. After completing the **Active Directory Installation**, please select the *Warning Triangle* on the top, which should read : "*Promote this server to a domain controller*".
7. Select "*Add to a **New Forest**".
8. Enter a new **Domain Name**. This name ***Should Not*** match any *External Domain's Name*. You can use :
   
	   server.local

9. When reaching the "**Domain Controller Options**" screen, please install the *DNS Server* as well, so this **Domain Controller** can act as a **DNS Server** as well!
   
   10. If you decided to use a **DSRM Password**, it would be a good idea to be aware of it, as it is a back door for the Administrator to use in case something goes wrong.

11. Please select a **NetBIOS Name**, which should be the *Domain Name sans le ".local"*.
12. After the process is done, the local administrator account gets promoted to the *Domain Administrator Role*!
13. After the wizard checks for errors, it will report a few. Namely, we would need to change the **Administrator** user's *password* :


>	net user Administrator <new password> 



>[!note]
>
>You will be warned about the server needing a *Static IP Address* in order to act as a **DNS Server**. You can do so from the following section :
>
>![[Pasted image 20240208152435.png]]
>
>









