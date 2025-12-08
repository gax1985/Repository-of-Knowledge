
### Denial of Access to Entire Subnet

TO DENY whole 0.20 network :


- access-list 1 deny 192.168.20.0 0.0.0.255  *(deny a subnet)*
- access-list 1 deny 192.168.20.100 0.0.0.0  *(deny a single IP)*

- int gig 0/0/0.30 *(define that single IP can't access VLAN 30)*
- ip access-group 1 out *(make this ACL a router to network denial)*

----------
## Longer Version






There are two types of ACLs or Access Control Lists : 


1. Standard ACL : 
Placed on the interface closest to the destination. Has the numbers 1-99. When we were numbering the VLANs , they did not mean anything. With ACL, they DO! With a Standard Access Control List , it is given a number of 1-99. The router would recognize the number, and grant the capabilities closest to its type. 

		It is closest to the destination. For example , members of the group is the source :  
		
		
		
		
		![[Pasted image 20231027121307.png]]
		
		
		Source 
If we wqsnt to deny 10.0 network from accessing 30.  We will use a standard ACL (give it a number of 1-99), and place it the closest to the destination. This works really well because we need the second network from getting to this network. 




		
1. Extended 100-199 : 


		We place it closest to the source, so in nthat case, we would put it on this interface : 

![[Pasted image 20231027121513.png]]



We want it to be specific , and we want to make sure it does not exit the interface and access the second network. 



What we will do in the example is to deny one single computer. We will do two examples where we will deny an entire network as well. 


> [!caution] 
> The Most  Prohibitive RuleApplies First 



We would deny 192.168.10.100 and PERMIT ANY (permit any network or PC or IP) through this ACL. In this case, we would deny the single IP first due to it being the most prohibitive:


![[Pasted image 20231027122029.png]]



WHat we first have to do on the router is :


1. Build an access list , not initially associated with an interface on the router : 

	conf t
	access-list 1 (standard ACL) deny 192.168.20.100 0.0.0.0



He has his access list defined. He goes into sub-interface 0/0/0.30 to get to the config tree, and to put access list there, he refers to it as : 


	ip access-list 1 out (direction is out) 


What does this direction mean ? 

In this case, we are coming from the source (192.168.10.0), it means the packet travels through the router, and can't get out of the interface (it is blocked) 


OUT --> Leaving the interface



If we are to say "IN", it would means any traffic going IN, which is NOT what we want to do. We do not want to block the other netwrok from communicating, but it will prevent the second network from sending a packet through the router to the first subnet

In and Out of the Interface (router) 



question : Can you put both an extended and Standard ACL on the same interface ? 


Answer : Yes, but it will be different ACL numbers, and it would affect different people. 



(When Ron has the issue of not being able to PING, each interface has to have NO SHUTDOWN added, so we would cancel the shutdown sequence for the interface. NO SHUT means for the interface it is on)



He is NOT trying to block all computers from 20 VALN, he is blocking one computer from the 20 VLAN. 



Question : WHy doesnt the communication through the Switch and not the router? 


Answer : The router governs communications between VLAN. The only reason the switch is there to attach multiple machines to the network.  ACLs are placed on routers and not switches. 





If we apply this : 


Standard ACL 1-99

applied closest to the destination.

denies or permits source IP address

Extended ACL 100-199

Applied closest to the source

denies or permits source IP address

denies or permits destination address

denies or permits dport

outer0(config)# access-list 1 deny 192.168.20.100 0.0.0.0

outer0(config)# access-list 1 permit any

outer0(config)#int giq 0/0/0.30

outer0(config-if)#ip access-group 1 out




20.100 would be able to communicate with 30.




We are blocking : 


![[Pasted image 20231027123600.png]]



From communicating with :


192.168.30.200





And it cant do it and it gets the message back "Host Unreachable.". If there is NO ACL there, and no routing between two VLANS, we get "Request Time Out". If it has no way to talk to the other vlan, "Request Time Out". "Host Unreachable" ACL is blocking the connection. We know that there is an ACL keeping us from transferring packets from the router to get there. 


Let us try pinging VLAN 20. 



192.168.30.60 : 


ping 192.168.30.60 


DESTINATION HOST UNREACHABLE


We cant get to VLAN 30 from VLAN 20. 



We can configure the ACL : 


		access-list 1 deny 192.168.20.100 


Whenever typing an IP address in a command, we need to see if we need to add the subnet. 

		access-list 1 deny 192.168.20.100 ?


It is looking for a a WildCard bit. 



What is a Wild Card bit? 

It is the inverse of the netmask , so in binary : 


255.255.255.0
1111111.11111111.11111111.00000000



The wild card is the inverse of the netmask : 

0.0.0.255
000000.0000000.000000.111111111



Question : Why use the inverse and not use the netmask ? 

Answer : it does not matter. Are we blocking a whole network/vlan or an individual ip ? If we are blocking a whole vlan , this is what the whole vlan : 



0.0.0.255 


What it means is , we are only talking about the host that is defined in the network. We are blocking ALL the hosts. Our rule is not blocking the whole vlan. We simply need to block one IP address. To do so, we do not need the wild card bits. We write them in, but the actual command does not include them. We are givingh it the IP address to block. If we are blocking a single IP address, the wild card bits are : 


0.0.0.0 


Because they are not used. This is the equivalent of saying "Ignore the wildcard bits"


When you type the command, and see the actual command executed by the router, it does NOT include them


We want to issue this command :


		access-list 1 deny 192.168.20.100 0.0.0.0


If instead of that:


		access-list 1 deny 192.168.20.0 0.0.0.255 (we are blocking the whole VLAN)
		# The netmask is 255.255.255.0, so we do the inverse 0.0.0.255. We do not need that when blocking a single IP address




TO CONTINUE THE CLASS EXERCISE : 


		1. block one IP : 

		access-list 1 deny 192.168.20.100 0.0.0.0
		access-list 1 permit any

		The fact that we chose subinterface 30, it does not 30 VLAN, but it is just notes. 
		
		We have to from global config to interface :
		
		
		int gig 0/0/0.30
		access-group 1 out  
		 # it applies Access List 1 (acces-group 1 ) applies it to the interface, but remember , access list can be applied on the "in" and "out". 

		# We are putting it on the 0.30 interface, which goes out to the VLAN 30, 
		
		# We have the router, and for example we have two interfaces : 0/0/0
		20 leading to VLAN 20, and we have interface 0/0/0.30 leaving to VLAN 30. We need to stop 1 person on VLAN 20 from getting out of the interface and going to VLAN 30. We are saying " You can not go out of the interface". If we put the same rule on the inbound interface it would be waiting from the 20 vlan to come in, but since there is no VLAN 20 plugged in in the interface VLAN 30 is plugged into it. 

		 int gig 0/0/0
		no shut

		any time 20.100 is trying to get out of 0.20 interfacem it can not do so
		
		
		ping 192.168.30.200
		
		
		DESTINATION HOST UNREACHABLE
		
		
		# What about 20.50, should that person be able to get to VLAN 20 ? 
		
		It would communicate successfully!
		
		What we have done to 20.100, it can not leave the router's 0.30 interface to get to the VLAN 30. Regardless of the switches on the VLAN 30, it tries to get to 0.30 to get to VLAN 20, and not be able to do so. Ron noticed some issues when people tried to ping
		
		




![[Pasted image 20231027100848.png]]

We are blocking VLAN 20 from VLAN 30


Question : What if we are blocking a subset




