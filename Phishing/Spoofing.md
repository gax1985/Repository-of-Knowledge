	


# Chapter 7


## Objectives

§Understand the mechanics of spoofing
§Describe the consequences of spoofing
§Define various types of spoofing
§List and describe some spoofing tools

## Spoofing

- [ ] The act of falsifying the source address or identity of data packets in order to impersonate another entity or deceive a recipient.
- [ ] It's a common tactic used in cyber attacks to gain unauthorized access, bypass security measures, or launch various forms of attacks.



§Spoofing (continued)

§Spoofing (continued)

### Trust

The relationship between machines that are authorized to connect to one another.

### Authentication

The process those machines use to identify each other.



#### Generally, **Authentication** and **Trust** have an inverse relationship: 
If a high degree of trust exists between two machines, the amount of authentication is low.
If little trusts exists between the machines, a great deal of authentication is required.

![[Pasted image 20250301155307.png]]

### Email Spoofing
Email spoofing takes advantage of the fact that email, in many ways, is not very different from regular mail. 

#### Elements of Emails
Each email has three elements: 

an envelope,

 a message header, 
 
 and a message body. 
 
 
 An email spoofer puts whatever they want into each of those fields, not just the body and “To:” fields. This means they can customize the information to their advantage.

§[[Penetration Testing/Assignments/Assignment 3 - Spoofing/How to Spoof Email for FREE — Guide  by XIT  Medium]]


§https://x-it.medium.com/how-to-spoof-email-for-free-guide-a5fe0c6ee631


![[Pasted image 20250301155954.png]]
### How to stop email spoofing
Email filters that use DNS authentication services like SPF, DKIM and DMARC can help to block potentially fraudulent email



### Sender Policy Framework (SPF)
A DNS-based mechanism for authorizing IPs to send from a specific domain



§Email Spoofing (continued)

### Domain Keys Identified Mail (DKIM)

Similar to SPF, it verifies the sender through the use of PKI (Public Key Infrastructure)

![[Pasted image 20250301160249.png]]
wA private key that the server uses to cryptographically sign all outgoing emails and a public key that recipients can use to verify that the domain’s real private key signed an email.

§

§

§Email Spoofing (continued)

§Domain-based Message Authentication Reporting & Conformance (DMARC)

wDMARC verifies email senders by building on DNS, DKIM, and SPF. It will tell your receiving servers what to do with messages that don’t pass SPF or DKIM.

wDMARC is configured entirely in DNS, so no additional server-side work is necessary. DMARC involves two separate functions: reporting and enforcement.

Enforcement refers to what should happen when an email fails DMARC validation.

Reporting offers visibility into what kind of mail is being rejected because of DKIM and SPF. It’s useful for intrusion detection because we can review reports for signs of spoofing attacks that have occurred. It’s also helpful for debugging because we can see if we are rejecting mail that actually should be accepted.

§Email Spoofing (continued)

§Caller ID Spoofing

§Your caller identification display (Caller ID) normally indicates the phone number and name associated with the line used to call you. Caller ID spoofing is the act of altering the Caller ID displayed to the person receiving the call. Caller ID spoofing in Canada & (most of) the US can be used for legitimate and illegitimate purposes.

§

§For example, a doctor calling to discuss a patient’s lab results may want to display the hospital’s general call back number as their Caller ID to direct all future inquiries appropriately.

§

§Alternatively, a ‘telemarketer’ that changes their Caller ID information to misrepresent themselves in an effort to defraud the target is illegal.

§Caller ID Spoofing (continued)

§There are various apps/services that allow you to spoof your number with one that can be inputted.

wNote that this is not the same as a burner number, which gives you a number that is legitimate. Anyone with that number could call you.

§Caller ID Spoofing (continued)

§VoIP services can be used as well. Various apps, like Asterisk, give you the ability to spoof numbers.

whttps://www.rapid7.com/blog/post/2018/05/24/how-to-build-your-own-caller-id-spoofer-part-1/

§

§

§There are also devices you can buy/build to allow you to perform the same function. They are generally referred to as Orange Boxes.

§SMS Spoofing

§Texting, or SMS, spoofing uses the same infrastructure as cellular spoofing, but easier to accomplish as it's just a one-way message.

§Several websites support this capability.

wNote that this isn't the same as using a simple 'Web to SMS' message service. Which could allow for scamming of course, but these typically identify themselves as a service.

§Biometric Spoofing

§Biometrics are biological measurements — or physical characteristics — that can be used to identify individuals. For example, fingerprint mapping, facial recognition, and retina scans are all forms of biometric technology, but these are just the most recognized options.

§Other options include, but aren't limited to:

wDNA

wVoice

wEar - shape and features of the human ear

wIris - the coloured circular segment at the front of the eye

wFinger/Hand geometry - captures features beyond fingerprints

wGait - every human has a specific way of walking and running

wHeartbeat - individuals produce a distinctive heartbeat

wKeystrokes - the actions involved in typing on a keyboard

wOdour - individuals have been studied to determine it is distinctive

wSignatures  - Handwriting can be used to verify an individual

w

§Biometric Spoofing (continued)

§Biometrics are still just stored data. If that data can be accessed, or replayed, the security can be defeated.

§Works best when combined with other security measures (MFA)

§Biometric Spoofing (continued)

§By either hacking the database with the stored data, or capturing the data, we can establish a replay attack.

§Biometric Spoofing (continued)

§Fingerprints can be duplicated and used easily

§Voice recognition can be recorded and replayed

§Other methods are not so easy to 'fake'

§Website Spoofing

§A website with the intention of misleading visitors that it's legitimate would be a spoofed website

§

§Creating a spoofed website is not illegal if the aim is to parody another brand. 

o[http://appleplugs.com/](http://appleplugs.com/)

§

§Normally, the spoofed website will adopt the design of the target website, and it may have a similar URL

§

§

§

§Website Spoofing (continued)

§By using similar spelled names, either by substituting characters or even creating what sounds to be the genuine website, a human can fall for the deception. Especially if there appears to be a legitimate reason to click the link such as an e-mail notification that requires the individuals 'immediate' attention

§Website Spoofing (continued)

§Homoglyphs (from the Greek “homo” = same, and “glyph” = character), and Punycode, are both able to be used by DNS.

§

§The associated Homoglyph Lab in Brightspace will demonstrate how you can use these characters and even have it registered, albeit with some difficulty.

§Website Spoofing (continued)

§In 2020, a flaw in several mobile browsers allowed for a malicious website, running a few lines of JavaScript, to alter the actual address in the address bar.

§[https://www.rafaybaloch.com/2020/10/multiple-address-bar-spoofing-vulnerabilities.html](https://www.rafaybaloch.com/2020/10/multiple-address-bar-spoofing-vulnerabilities.html)[](https://www.rafaybaloch.com/2020/10/multiple-address-bar-spoofing-vulnerabilities.html)

§

§IP Spoofing

§IP spoofing is the creation of IP packets which have a modified source address to either hide the identity of the sender, to impersonate another computer system, or both

§IP Spoofing (continued) 

§Non-Blind Spoofing

wThis type of attack takes place when the attacker is on the same subnet as the victim. The sequence and acknowledgement numbers can be sniffed, eliminating the potential difficulty of calculating them accurately. The biggest threat of spoofing in this instance would be session hijacking. By corrupting the data stream of an established connection, then reestablishing it based on correct sequence and acknowledgement numbers with the attack machine an attacker could effectively bypass any authentication measures to build the connection.

§Blind Spoofing 

wThis is a more sophisticated attack, because the sequence and acknowledgement numbers are unreachable. So, the hacker would be unaware of how the transmissions take place on this network therefore he needs to coax the machine into responding to his own requests so that he can analyze the sequence numbers. Then the attacker can inject data into the stream of packets without having authenticated himself when the connection was first established.

§IP Spoofing (continued) 

§Distributed Denial-of-Service 

oTo keep a large-scale attack on a machine or group of machines from being detected, spoofing is often used by the malefactors responsible for the event to disguise the source of the attacks and make it difficult to shut down. Spoofing takes on a whole new level of severity when multiple hosts are sending constant streams of traffic to the DDoS target. In that case, all the transmissions are generally spoofed, making it very difficult to track down the sources of the attack.

§ARP Spoofing

§An attacker can send falsified Address Resolution Protocol (ARP) messages over a local area network (LAN). ARP being the protocol used by network devices to map IP addresses to the physical MAC addresses of devices within the same network segment.

§In a typical ARP spoofing attack, the attacker aims to associate their own MAC address with the IP address of another network device, such as the default gateway or another host on the network. 

§This allows for such attacks as Man-in-the-Middle, which can include session hijacking, as well as DoS attacks.

§

§Spoofing Tools

§This section covers the following spoofing tools and their uses:

wMAC Spoofers

wColasoft Packet Builder

wEttercap

§MAC Spoofers

§maccchanger is included with Kali, it can change the MAC address to any desired address until the next reboot. hw ether is another that accomplishes the same result

§

§Other tools are available, even for Windows; SMAC https://smac.soft32.com/

§

§Colasoft Packet Builder

§Windows based Spoofing app

§Free and easy to use

§Allows users to create custom network packets at different layers of the OSI model, including Ethernet, IP, TCP, UDP, ICMP, and more

§Can specify various parameters of the packets they create, such as source and destination IP addresses, port numbers, packet size, payload data, and other relevant fields

§Supports a wide range of network protocols and allows users to manipulate packet headers and payloads according to their requirements.

§

§Colasoft Packet Builder (continued)

§Ettercap

§Ettercap is a free and open-source network security tool for MITM attacks. While it does employ spoofing, through ARP Poisoning, it’s worth noting that it is a fully functional suite.

wPacket Sniffing: It can capture packets transmitted over a network, allowing the attacker to analyze the data being transmitted.

wProtocol Support: Ettercap supports the dissection of various network protocols, including Ethernet, ARP, IP, TCP, UDP, and others.

wContent Filtering: It can filter and modify the content of packets in real-time, enabling attackers to manipulate the data being transmitted.

wPlugin Support: Ettercap supports plugins, which extend its functionality and allow for custom packet manipulation and analysis.

§

§Ettercap (continued)

§Prevention and Mitigation

§To avoid and/or defend against IP spoofing:

wWherever possible, avoid trust relationships that rely upon IP or MAC addresses only.

wIngress filtering involves configuring network devices, such as routers and firewalls, to filter incoming traffic based on the source IP addresses and invalid IPs can be blocked

wLikewise egress filtering involves filtering outgoing traffic to ensure that packets leaving your network have valid source IP addresses. This helps prevent your network from being the source of IP spoofing attacks.

wUse encrypted and secured protocols like IPSec

wRegularly monitor network traffic for signs of IP spoofing or other suspicious activity. Intrusion detection systems (IDS) and intrusion prevention systems (IPS) can help detect and respond to potential attacks in real-time.

§Tangible Costs

§Economic Loss

wMay occur when valuable data is lost or duplicated

wShare price can be affected when made public, either by the company itself, or by the attackers.

w

§Strategic Loss

wLoss of strategic data that outlines events planned for the future

wCould lead to loss of both money and goodwill for the hacked company

§Summary (continued)

§What spoofing is

§The different types of spoofing

wEmail, Caller ID, SMS, Biometric, Website, IP & MAC

§Homoglyphs

§Spoofing tools

§Methods to prevent spoofing

§