# Manual Tecnico
### Marco Antonio Solis Gonzalez - 202003220


## Resumen de Comandos
### Creacion del PortChannel PAGP Y LACP
#### PAGP switch0
- enable
- configure terminal
- interface range f0/11-12
- channel-group 1 mode desirable
- exit 
- interface port-channel 1
- switchport mode trunk
- end
- wr

#### switch1
- enable
- configure terminal
- interface range f0/11-12
- channel-group 1 mode auto
- exit 
- interface port-channel 1
- switchport mode trunk
- end
- wr

#### LACP Switch2-3
- enable
- configure terminal
- interface range f0/11-12
- channel-group 1 mode active
- exit
- interface port-channel 1
- switchport mode trunk
- end
- wr

### Configuracion de ip a cada router
#### R1
1. 
- enable
- configure terminal
- interface fa0/1
- ip address 102.168.2.2 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.168.1.2 255.255.255.248
- no shutdown
3. 
- enable
- configure terminal
- interface se1/0
- ip address 10.0.0.1 255.255.255.252
- no shutdown

#### R2
1. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.168.1.1 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/1
- ip address 102.168.0.2 255.255.255.0
- no shutdown


#### R3
1. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.168.2.1 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/1
- ip address 102.168.0.3 255.255.255.0
- no shutdown

#### R4
1. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.178.1.1 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/1
- ip address 102.178.2.1 255.255.255.248
- no shutdown
3. 
- enable
- configure terminal
- interface se1/0
- ip address 10.0.0.2 255.255.255.252
- no shutdown

#### R5
1. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.178.1.2 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.178.0.2 255.255.255.0
- no shutdown
#### R6
1. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.178.2.2 255.255.255.248
- no shutdown
2. 
- enable
- configure terminal
- interface fa0/0
- ip address 102.178.0.3 255.255.255.0
- no shutdown

### Configuracion HSRP R2-R3 R5-R6
#### R2
- enable
- configure terminal
- interface 
- standby version 2
- standby 