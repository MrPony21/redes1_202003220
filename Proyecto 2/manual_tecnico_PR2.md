# Manual Tecnico 
### Jonatan Leonel Garcia Arana - 202000424
### Marco Antonio Solis Gonzalez - 202003220
Una reconocida empresa de venta de línea blanca y electrodomésticos lo contrató para que trabaje en la red regional, interconectando de momento las sedes entre Jutiapa y la central de la ciudad capital.

## Objetivos
- Poner en práctica lo aprendido en el proyecto 1 y prácticas 1 y 2.
- Demostrar el conocimiento adquirido sobre el enrutamiento entre VLANS usando Router on a stick e interfaces virtuales.
- Demostrar el conocimiento adquirido sobre VLSM (Variable Length Subnet Mask) y FLSM (Fixed Length Subnet Mask).
- Demostrar el conocimiento adquirido sobre los protocolos de enrutamiento estático.

## Software
- Packet Tracer

## Topología de la red

## Direcciones IP


## Resumen de Comandos
### Sede de Jutiapa

#### LACP 
##### Switch 2-3
- enable
- configure terminal
- interface range f0/2-3
- channel-group 1 mode active
- exit
- interface port-channel 1
- switchport mode trunk
- end
- wr

#### Configuracion de ip de cada router
#### J1
1. 
- enable
- configure terminal
- inteface f1/0
- ip address 192.167.40.2 255.255.255.0
- no shutdown 
- exit
2. 
- enable
- configure terminal
- interface f0/0
- ip address 11.0.0.2 255.255.255.252
- no shutdown
- exit
- end
- wr

#### J2
1. 
- enable
- configure terminal
- inteface f1/0
- ip address 192.167.40.3 255.255.255.0
- no shutdown 
- exit
2. 
- enable
- configure terminal
- interface f0/0
- ip address 12.0.0.2 255.255.255.252
- no shutdown
- exit
- end
- wr

#### Configuracion de HSRP J1-J2
##### J1
- enable
- configure terminal
- interface fa1/0
- standby version 2
- standby 21 192.167.40.1
- standby 21 priority 109
- standby 21 preempt
- end
- wr

##### J2
- enable
- configure terminal
- interface fa1/0
- standby version 2
- standby 21 192.167.40.1
- standby priority 100
- end
- wr

#### Configuracion del VTP Y RSTP ESW1 SW2 SW3
Falta por terminar
##### ESW1
- enable
- configure terminal
- vtp mode server
- vtp domain P40
- vtp password usac40
- vtp version 2
- exit
- wr

##### SW2 - SW3
- enable
- configure terminal
- vtp mode client
- vtp domain P40
- vtp password usac40
- exit
- wr

##### Creacion de VLANs ESW1
- enable
- configure terminal
- vlan 14
- name RRHH
- vlan 24
- name contabilidad
- vlan 34
- name ventas
- vlan 44
- name informatica
- end 
- wr

#### Truncar los switches
##### ESW1
- enable
- configure terminal
- interface range f0/1-2
- switchport trunk encapsulation dot1q
- switchport mode trunk
- switchport trunk allowed vlan all
- end
- wr

##### SW2 - SW3
- enable
- configure terminal
- interface range f0/1-3
- switchport mode trunk
- switchport trunk allowed vlan all
- end
- wr

#### Configuracion del modo acceso 
##### SW2
- enable
- configure terminal
- interface f0/11
- switchport mode access 
- switchport access vlan 14
- exit
- interface f0/12
- switchport mode access 
- swithcport access vlan 24
- exit
- interface f0/13
- switchport mode access
- switchport access vlan 24
- exit
- end
- wr

##### SW3
- enable
- configure terminal
- interface f0/11
- switchport mode access 
- switchport access vlan 34
- exit
- interface f0/12
- switchport mode access 
- swithcport access vlan 14
- exit
- interface f0/13
- switchport mode access
- switchport access vlan 44
- exit
- end
- wr

##### RSTP
FALTA

### Sede de Escuintla

#### Configuracion del VTP Switch2
- enable
- configure terminal
- vtp mode server
- vtp domain P40
- vtp password usac40
- vtp version 2
- exit
- wr

#### Creacion de las VLANs Switch2
- enable
- configure terminal
- vlan 14 
- name RRHH
- vlan 34
- name ventas
- end
- wr

#### configuracion del modo acceso Switch2
- enable
- configure terminal
- interface f0/11 
- switchport mode access
- switchport access vlan 14
- exit
- interface f0/12
- switchport mode access
- switchport access vlan 34
- end
- wr

#### RSTP
Falta por terminar


### Sede Peten








### Comandos para verificar la configuracion
- show running-config
- show standby
- show startup-config





