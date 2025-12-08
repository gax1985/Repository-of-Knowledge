




# Steps : 




1. Please make sure that **Networking** is set to *NAT* in VMWare Workstation Pro. 
2. Let us set up the **Domain Controller** to be the *DNS Server* for our Workstation : 
   
   
	   1. Launch Control Panel ( or aka... Settings fromn the Start Menu)
	   2. Select Network and Internet 
	   3. Select Network and Sharing Center 
	   4. Click on Change Adapter Settings on the left panel
	   5. Select Internet Protocol Version 4 (TCP/IPv4)
	   6. Enter the IP Address of the Domain Controller in the "Preferred DNS Server" field
	   7. Let us give the Workstation a new name by selecting "System and Security", selecting the "System" (with a PC with a checkmark icon) and then selecting "Rename this PC"
	   8. Enter a name for the Workstation, and then add the Domain Name in the Domain field
	   9. Enter your password!


3. Let us double-check on the **Windows Server 2019** Virtual Machine to see if the *Workstation* Virtual Machine has been added to the Domain: 
   
	   1. Launch Server Manager
	   2. Select "Tools"
	   3. Select "Active Directory Users and Computers"
	   4. Select "domain.local"
	   5. Select the "Computers" Folder
	   6. Check if the name of the Workstation is present!

4. On the "**Windows Server 2019**" Virtual Machine, let us add the *Workstation* to the new *Organizational Unit* :
   
   
	   1. On the Server Manager application, Select "Active Directory Users and Computers"
	   2. Select the "domain.local" Domain
	   3. Select the "Computers" folder
	   4. Right-Click on "Workstation"
	   5. Select "Move"
	   6. At the "Move" screen, please select the "OrganizationalUnit" Organizational Unit
	   7. 