

- en
- conf t
- int gigabitEthernet 0/0/0.99
- encapsulation dot1Q 99
- ip address 192.168.99.1 255.255.255.0
- no shut
- exit
- int gigabitEthernet 0/0/0.20
- encapsulation dot1Q 20
- ip address 192.168.20.1 255.255.255.0
- no shut 
- exit
- int gigabitEthernet 0/0/0.30
- encapsulation dot1Q 30
- ip address 192.168.30.1 255.255.255.0
- end
- copy run start