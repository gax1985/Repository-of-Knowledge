


The tool used: 

**Aircrack-NG**


airodump is for monitoring current WIFI networks, where we capture the MAC Address, type of device they have, and then select your target. 


>[!command]
>>`sudo aerodump-ng wlan1 --band abg --essid "WIFI Network"`



try implanting the device in the morning. This way, instead of deauthorizing everyone, just wait for them to come in the morning, where you can capture the WIFI handshake, or when they get back from lunch. 

>[!tips]
Try getting a full 24-hours battery, you want small form factor and long battery device
>
>if you are going to target server racks, you can plug it into the power underneath. 
>
>>[!Ron]
>>if you are in an office tower, if there is an AC plug in the hallway, it will be used by the cleaning crew, and they will notice it. If you are in a standalone building, you can access the external plug used for hedge trimmers etc. The same problem happens ...
>>
>>Double-sided tape can be used, but you need it to be strong enough. Coridor is the property of the building not the client, so choose the weight of the device, create a tube to the **Conduit Box**.
>>Consider how important **reconnaissance** for this. We have to do passive scanning, but no deauthorization. We would have to get there in significantly earlier time before they get there. Reconnaissance tells us when the employees show up for work. If you have a time line, where you can tell when the office is open to you, ccheck if the building is locked during supper time , etc. You would need significant reconnaissance to figure it out. The same approach for mounting and concealing wireless devices can be used to disguise wireless cameras, microphones, etc. There would be wireless cameras doing shoulder surfing of employees etc. Once you enter the building, you would have to have at least one believable reason in case you get confronted by someone from the client's side that does not know. One example : Overalls, mop and broom --> office towers have their own crew, so it would be bad. Carry the contract with you in your pocket in case you get arrested. The police is often not happy with interrupting people on a penetration test. 90% of your time will be dedicated to reconnaissance. 
>>
>>Using the building's AC to monitor the client's network : you are looking for close proximity for an unused ethernet jack and AC plugs (power). You will most likely find them in board rooms. You have an AC plug next to ethernet jack. You take Ethernet-over-Power adapter, plug it into the AC, short network cable, add your WIFI device, and place a **Conduit Box** over the whole thing to hide the AC and Ethernet ports. 
>>
>>If you have a long fixed antenna, remember the tube, which becomes the housing for the antenna. 
>>
>>For best results, mornings and lunch hours are best. Because the time line for the battery life of the device would likely cover both activity periods. 
>>
>>It is all about context. If you are practicing lock picking in a coffee shop, and you get asked by the police, you can mention you are a Cybersecurity student. But if you are after hours at the place with a lock picking kit, that is a different story. 
>>
>>Ron mentioned to get a Raspberry pi , Shields, mini computer, put it together in a hobby fashion, and that is the best way to learn! 
>
>
>Command strips do not leave any marks!
>
>
>Being remotely connected can be done. Dragging the laptop and  standing around looks suspicious. If you dress in a suit, look the part, and use Termux on the phone, and complete these steps, that would be the best part. You are not James Bond, but you are trying to blend in. 

TP-Link Archer Antenna -- flat antenna, you can route it around the device. 

Disable the DHCP server on the Wireless device, so this way, the clients who try to connect to it will fail to connect. You would have to enter your IP address manually. 

Raspberry Pi 4s will do nicely, as they would run a full Kali-Linux. 

It could be convenient for those people who have their own locked washrooms to have you come before they come in to work, go inside , set everything up after locking the door. You can run the device all day if you want, walk around the building , go to the parkade pretending you forgot something etc. Once you get access, you can go back and use Kali to do the rest of the reconnaissance work. If the building is closed to normal people, and the front door is locked, and there is a sign indicating to go to the back, and when you arrive there, do not pick the locks, and if there is a card reader, wait for someone to go in, or check if the card reader is working. 


If you have lockpicks on you , and you get stopped by the police, they would consider having lockpicks as intent.  

Intel NUCs are great starters for WIFI hacking devices. You have to figure out where your risk is. 

USB drops would involve USB drives that you do not want to see again. Rubber Duckys from Hak5 is meant to be left behind. 

You have to learn by yourself!

>[!hint]
>
>Wednesday at 1300 is Erik's session. Active Directory training! 




Profiles of each of the employees, any physical reconnaissance work with reports, network recon with reports, server team and reports , etc


USB Drops is difficult, due to the difficulty of grabbing information from Windows.  Ron would like to have the grades in before March break. 

>[!critical]
Evaluation on Friday morning for the USB drop

