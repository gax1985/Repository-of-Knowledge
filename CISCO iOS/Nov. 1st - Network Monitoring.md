




Network represents a choke point where we can see intruders entering and exiting.

  

Five Tuple - Source IP, Destination IP, Source Port, Destination Port, Protocol [TCP or UDP]

  

Computer 1 - 

	Source IP xxx.xxx.xxx.123

	Destination IP xxx.xxx.xxx.456

	Source Port 48000

	Destination Port 22

	Protocol TCP [6] or UDP [17]

	ICMP [1]

  

  

16 bit number - > Ports 65536 0-65536

  

Computer 2 SIP xxx.xxx.xxx.456

         DIP xxx.xxx.xxx.123

         Source Port 22

         Destination Port 48000

         Protocal TCP 6

         ICMP [1]

  

Computer 3 SIP xxx.xxx.xxx.789

         DIP xxx.xxx.xxx.456

         Source Port 50000

         Destination Port 22

           Protocol TCP 6

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

A single packet sent on a network will have Five Tuple - Source IP, Destination IP, Source Port,

Destination Port, Protocol [TCP or UDP] and the payload.

  

Flow

  

-Unidirectional set of packets. Above we had computer one talking to computer two.  

  

Packet 1 provides us with the five tuple and will stay the same when its communicating

with computer 2.

  

The very first packet will have the syn flag.

The second from computer one will be the ack flag

Push flags will be sent until the fin flag is sent to singnal the end of the conversation.

  

1st packet is 64 bytes

2nd packet is 65 bytes

3rd packet is 500 bytes

Fin packet is 32 bytes

  

Total 660 bytes sent.

Start time at 00:00:01

End time at 00:10:00

  

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

Our Flow database will have the flow for c1

  

The five tuple and all the flags such as syn flag, ack, push, and fin.

  

We will record the size of the packet in bytes. 660 bytes

  

Start time and end time of this flow

  

The Router will build a flow database for any packet that comes through.

  

How does a router know when to finish the flow database? If it sees a fin or a reset flag.

Passive time out, No packets sent in a specified time.

  

Active timeout: Communication won't stop. Fear of running out of storage space.

  

We tell the router that we would like to see these database entries. Have the router send the DB

to a specified location also known as a flow collector.

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

The other half of this conversation is happening on Computer 2.

  

Starts a new flow record for computer 2. Starts a 5 tuples. First flag it will recieve will be

syn ack, pushs and a fin ack.

  

600 bytes are being sent back to computer 1

  

A start time and end time using the same conditions as computer 1.

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

That was the basic for flow records.

  

-Netflow is a standard created by cisco

 Version 5 and Version 9

most generic routers speak with netflow

  

-Juniper produces SFLOW

  

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

C1 and C2  How many flow records are their between the two computers?

  

1 Flow from C1 to C2

1 Flow from C2 to C1

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

Full packet capture  

  

The top level of the packet has a header where the five tuple is and is only recorded once.

Contains Size, flags, times. Small amount of data.

  

The contents of the packet is in the payload.

  

Computer one has wireshark (wireshark is a packet tracker)

  

It uses full packet tracker. Packet one is saved by wired shark. Everything is included.

Packet two is saved by wired shark. Everything is included. Now thats a lot of data.

  

When you have too much full packet tracker data it becomes increasingly harder to navigate through

the data as opposed to the previous flow 1 and flow 2 tracking.

  

  

Collect data over a month. Start with flow leveling collectingNetwork represents a choke point where we can see intruders entering and exiting.

  

Five Tuple - Source IP, Destination IP, Source Port, Destination Port, Protocol [TCP or UDP]

  

Computer 1 - Source IP xxx.xxx.xxx.123

           Destination IP xxx.xxx.xxx.456

           Source Port 48000

           Destination Port 22

           Protocol TCP [6] or UDP [17]

           ICMP [1]

  

  

16 bit number - > Ports 65536 0-65536

  

Computer 2 

		SIP xxx.xxx.xxx.456

		DIP xxx.xxx.xxx.123

		Source Port 22

		Destination Port 48000

		Protocal TCP 6


		ICMP [1]

  

Computer 3 SIP xxx.xxx.xxx.789

         DIP xxx.xxx.xxx.456

         Source Port 50000

         Destination Port 22

           Protocol TCP 6

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

A single packet sent on a network will have Five Tuple - Source IP, Destination IP, Source Port,

Destination Port, Protocol [TCP or UDP] and the payload.

  

Flow

  

-Unidirectional set of packets. Above we had computer one talking to computer two.  

  

Packet 1 provides us with the five tuple and will stay the same when its communicating

with computer 2.

  

The very first packet will have the syn flag.

The second from computer one will be the ack flag

Push flags will be sent until the fin flag is sent to singnal the end of the conversation.

  

1st packet is 64 bytes

2nd packet is 65 bytes

3rd packet is 500 bytes

Fin packet is 32 bytes

  

Total 660 bytes sent.

Start time at 00:00:01

End time at 00:10:00

  

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

Our Flow database will have the flow for c1

  

The five tuple and all the flags such as syn flag, ack, push, and fin.

  

We will record the size of the packet in bytes. 660 bytes

  

Start time and end time of this flow

  

The Router will build a flow database for any packet that comes through.

  

How does a router know when to finish the flow database? If it sees a fin or a reset flag.

Passive time out, No packets sent in a specified time.

  

Active timeout: Communication won't stop. Fear of running out of storage space.

  

We tell the router that we would like to see these database entries. Have the router send the DB

to a specified location also known as a flow collector.

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

The other half of this conversation is happening on Computer 2.

  

Starts a new flow record for computer 2. Starts a 5 tuples. First flag it will recieve will be

syn ack, pushs and a fin ack.

  

600 bytes are being sent back to computer 1

  

A start time and end time using the same conditions as computer 1.

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

That was the basic for flow records.

  

-Netflow is a standard created by cisco

 Version 5 and Version 9

most generic routers speak with netflow

  

-Juniper produces SFLOW

  

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

C1 and C2  How many flow records are their between the two computers?

  

1 Flow from C1 to C2

1 Flow from C2 to C1

  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  

Full packet capture  

  

The top level of the packet has a header where the five tuple is and is only recorded once.

Contains Size, flags, times. Small amount of data.

  

The contents of the packet is in the payload.

  

Computer one has wireshark (wireshark is a packet tracker)

  

It uses full packet tracker. Packet one is saved by wired shark. Everything is included.

Packet two is saved by wired shark. Everything is includeded. Now thats a lot of data.

  

When you have too much full packet tracker data it becomes increasingly harder to navigate through

the data as opposed to the previous flow 1 and flow 2 tracking.

  

  

Collect data over a month. Start with flow leveling collecting