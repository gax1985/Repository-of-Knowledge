
### VLAN 20's Switchport Mode and VLAN Configuration

	- enable
- config terminal
- vlan 20
- name Sales
- vlan 30
- name Admin
- int fa 0/1`
- switchport mode access
- switchport access vlan 20
- exit
- exit
- show vlan


------------


[confirm vlan 20 (Sales) has FA 0/1] [repeat for fa 0/3] **VLAN30**

### VLAN 30's Switchport Mode

- enable
- config terminal
- int fa 0/2
- switchport mode access
- switchport access vlan 30
- exit
- exit
- show vlan