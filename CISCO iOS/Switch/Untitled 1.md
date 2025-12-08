
### Setting up Trunking Mode on the Switch Port


en 
>conf t 
>int fa 0/5 
>switchport mode trunk 
>switchport trunk allowed vlan 1-30 
>exit   
>show interface trunk 