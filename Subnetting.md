@C1:
conf t
vlan 20
name ACCENTURE.COM
Interface vlan 20
 desc ACCENTURE.COM
 no shut
 ip add 10.0.0.129 255.255.255.128
ip dhcp excluded-add 10.0.0.129 10.0.0.139
ip dhcp pool ACCENTURE.COM
 network 10.0.0.128 255.255.255.128
 default-router 10.0.0.129
 domain-name ACCENTURE.COM
interface e1/0
no shut
switchport mode access
switch access vlan 20

@S1
conf t
interface e1/0
no shut
ip add dhcp
do bp

*********CHEVON*********
conf t
vlan 21
name CHEVON.COM
Interface vlan 21
 desc CHEVON.COM
 no shut
 ip add 10.0.8.1 255.255.248.0
ip dhcp excluded-add 10.0.8.1 10.0.8.100
ip dhcp pool CHEVON.COM
 network 10.0.8.0 255.255.248.0
 default-router 10.0.8.1
 domain-name CHEVON.COM

@A1
conf t
interface e0/0
no shut
switchport mode access
switch access vlan 21

@P1
conf t
interface e0/0
no shut
ip add dhcp
do bp

*********SHELL*********
conf t
vlan 22
name SHELL.COM
Interface vlan 22
 desc SHELL.COM
 no shut
 ip add 10.0.16.1 255.255.240.0
ip dhcp excluded-add 10.0.16.1 10.0.16.100
ip dhcp pool SHELL.COM
 network 10.0.16.0 255.255.240.0
 default-router 10.0.16.1
 domain-name SHELL.COM
do sh run | sec dhcp

@A2
conf t
interface e1/0
no shut
switchport mode access
switch access vlan 22

@P2
conf t
interface e1/0
no shut
ip add dhcp
do bp


*********FuelSave*********
@C1
conf t
vlan 23
name FuelSave.COM
Interface vlan 23
 desc FuelSave.COM
 no shut
 ip add 10.0.2.1 255.255.254.0
ip dhcp excluded-add 10.0.2.1 10.0.2.100
ip dhcp pool FuelSave.COM
 network 10.0.2.0 255.255.254.0
 default-router 10.0.2.1
 domain-name FuelSave.COM
do sh run | sec dhcp

@C2
conf t
interface e1/0
no shut
switchport mode access
switch access vlan 23

@S2
conf t
interface e1/0
no shut
ip add dhcp
do bp
