# Administración de Servicios en Red - ASR
Este repositorio contiene prácticas, ejercicios y proyecto final de la materia de ***Administración de Servicios en Red*** dada en la ***Escuela Superior de Cómputo*** del ***Instituto Politécnico Nacional.***

Hasta el momento, este repositorio contiene 1 práctica.
## PRÁCTICA 01: Implementación de un Sistema de Administración de Red usando *SNMP*.
### Objetivo: Implementar la arquitectura básica del protocolo SNMP
- Implementar la comunicación (intercambio de mensajes) entre el agente y el gestor usando
SNMP.
- Implementar la persistencia de información de una manera eficiente.
- Generar reportes para controlar y vigilar los agentes.
- Implementar un modelo de administración de red.

#### Arquitectura SNMP
![snmp](https://user-images.githubusercontent.com/22998708/53384543-e0940d00-3940-11e9-832a-7fc16d052b61.PNG)

### Configuración de la Arquitectura SNMP en la práctica 01.
- **Manager = Observium (using virual machine)**

- **Manager instructions:**
    - Install Observium in a virtual manager
    - Configure /etc/hosts (This file is only to add agents)
	
- **Windows Agent:**
  - Install SNMP service
  - Configure SNMP service, using a community 

- **Linux Agent:**
  - Install package: snmp, snmpd
  - Configure snmpd.conf using snmpconfig

- **Instalation of Obervium stepts:**
  - In VB you have to choose Linux and Debian64 bits
	- Create a virtual disk 
	- Use VDI
	- Dimanic allocated 
	- Choose 4 gb
	- In storage put IDE Primary master
	- In network you have to change NAT to Bridged adapter (Wi-fi) but if you wanna use eth cable select eth0 and you have to enable in advanced mode the Promiscous mode (Allow all).
  - Install hd 
  - Select Second option in partition (use entire disk)
	- And you have to put yes (GRUB)
	- After the instalation you have to put your credentials:
  - LaQueQuieres (password for all the users)

	- Were not using API so click skip
  - After that login into the url direction and the user is admin and Pepechido2 (http://10.100.64.162/)
  - And quit the console
  - When youre only in terminal mode put: root and enter key

- **Windows Agent:**
  - In vb you have to put the same as Observium in Network mode (check Linux network configuration)
	- Go to panelcontrol/Programs/Turn on off features/ and turn on SNMP and second option 
	- After that you have to search "local services" 
	- You have to start SNMP trap manually always 
	- You have to edit SNMP Service, (right clic and properties) 
     - Clic on traps, put a community name (its like an authentication level) (grupo4cm3)
	- In security option clic add, READ/WRITE and in a community name put grupo4cm2
	- And put SNMP packet from any hosts 
	- And after that, you have yo restart the service
	- Disable the firewall (both options)
	- Check your ip with ipconfig (ipconfig) Remember you have to always be in the same network 
	- If you wanna retrieve information you have to install NET-SNMP:
      - snmpget -v2c -c grupo4cm3 10.100... 1.3.6.1.2.1.1.1.0
      - snmpset -v2c -c grupo4cm3 10.100... 1.3.6.1.2.1.1.6.0 s "Merica"

- **Observium**
  - In nano /etc/hosts/ put the ip of windows and the name you wanna use ping nameofthe device
  - Now in the panel put skip ICMP, v2c, UDP, and community you have to put the same name in windows grupo4cm3 and remember the hostname is the name that is on the nano file

- **Linux**
  - sudo apt update
  - sudo apt-get install snmp snmpd(listen the port with a demon) 
  - sudo gedit /etc/snmp/snmpd.conf
  - snmpconf -r none -g basic_setup
  - y
  - location of the system: "lab. escom. ipn. "
  - sys contact: buscadordebugs
  - n
  - Dou you want to configure the agents acces control: y
  - Dou you want to allow SNMPv3: n
  - Dou you ...: n
  - Dou you want to allow SNMPv1 ... read-write: y
  - Comunity_name: gr_4cm3
  - Put RETURN for all (Enter)
  - OID: RETURN for all (Enter)
  - And finally write no (and so on ...) 
  - move the /usr/share/snmp 
  - sudo mv snmpd.conf /etc/snmp/snmpd.conf
  - sudo service snmpd restart
	_Remember to add the new machine on observium (to see the ip on linux is "ip addr show")
	_If youre on linux you could use "sudo tcpdump -i any -nn port snmp"

### Interfaz principal - Práctica 01
![interfaz principal](https://user-images.githubusercontent.com/22998708/53431587-198bba80-39f1-11e9-99b6-d3f4fe84d366.png)

