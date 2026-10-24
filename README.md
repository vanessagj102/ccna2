# ccna2
imagen de topologia

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/05911c32-a19f-4826-85f7-d980a7108deb" />

### Tabla A: Dispositivos Intermedios (Routers y Switches)

| Dispositivo / Interfaz | VLAN | Segmento de Red Base | Dirección IP a Calcular / Configurar | Máscara de Subred | Gateway por Defecto |
|---|---:|---|---|---|---|
| R1-Core-ELO `G0/0/0.10` | 10 | `192.168.10.0/24` | `192.168.10.254` | `255.255.255.0` | No aplica |
| R1-Core-ELO `G0/0/0.20` | 20 | `192.168.20.0/24` | `192.168.20.254` | `255.255.255.0` | No aplica |
| R1-Core-ELO `G0/0/0.30` | 30 | `192.168.30.0/24` | `192.168.30.254` | `255.255.255.0` | No aplica |
| R1-Core-ELO `G0/0/0.99` | 99 | `192.168.99.0/24` | `192.168.99.254` | `255.255.255.0` | No aplica |
| SW-Core `VLAN 99` | 99 | `192.168.99.0/24` | `192.168.99.2` | `255.255.255.0` | `192.168.99.254` |
| SW-Lab1 `VLAN 99` | 99 | `192.168.99.0/24` | `192.168.99.3` | `255.255.255.0` | `192.168.99.254` |
| SW-Lab2 `VLAN 99` | 99 | `192.168.99.0/24` | `192.168.99.4` | `255.255.255.0` | `192.168.99.254` |
| Enlace troncal | 111 | VLAN Nativa | No aplica | No aplica | No aplica |
| Puertos inactivos | 999 | VLAN Blackhole | No aplica | No aplica | No aplica |

### Tabla B: Dispositivos Finales (PCs de Usuario y Gestión)

| Dispositivo Final | Puerto del Switch | VLAN | Dirección IP (Formato CIDR) | Gateway por Defecto |
|---|---|---:|---|---|
| PC-Administración-1 | SW-Lab1 → Fa0/1 | 10 | `192.168.10.10/24` | `192.168.10.254` |
| PC-Administración-2 | SW-Lab1 → Fa0/2 | 10 | `192.168.10.11/24` | `192.168.10.254` |
| PC-Administración-3 | SW-Lab1 → Fa0/3 | 10 | `192.168.10.12/24` | `192.168.10.254` |
| PC-Laboratorio-1 | SW-Lab1 → Fa0/4 | 20 | `192.168.20.10/24` | `192.168.20.254` |
| PC-Laboratorio-2 | SW-Lab1 → Fa0/5 | 20 | `192.168.20.11/24` | `192.168.20.254` |
| PC-Laboratorio-3 | SW-Lab1 → Fa0/6 | 20 | `192.168.20.12/24` | `192.168.20.254` |
| PC-Dirección-1 | SW-Lab1 → Fa0/7 | 30 | `192.168.30.10/24` | `192.168.30.254` |
| PC-Gestión | SW-Core → Fa0/9 | 99 | `192.168.99.10/24` | `192.168.99.254` |


## asignar los nombres a los sw y roter
```bash
configure terminal
hostname R1-CORE-VSGJ
```
```bash
configure terminal 
hostname SW-lab1VSGJ
```
```bash
configure terminal 
hostname SW-lab2VSGJ
```
```bash
configure terminal
hostname SW-COREvsgj 
```
## Configuración de sw y router(contraseñas)

### SW-Core
```bash
enable
configure terminal
enable secret proyecto2711
line console 0
password proyecto2711
login
end
copy running-config startup-config
```

## SW-Lab1
```bash
enable
configure terminal
enable secret proyecto2711
line console 0
password proyecto2711
login
end
copy running-config startup-config
```

## SW-Lab2
```bash
enable
configure terminal
enable secret proyecto2711
line console 0
password proyecto2711
login
end
copy running-config startup-config
```
## router
```bash
enable
configure terminal
enable secret proyecto2711
line console 0
password proyecto2711
login
end
copy running-config startup-config
```
## CREAR LAS VLANs

### SW-COREvsgj

```bash
enable
configure terminal

vlan 10
name Administracion
exit

vlan 20
name Laboratorios
exit

vlan 30
name Direccion
exit

vlan 99
name Gestion
exit

vlan 111
name Nativa
exit

end
copy running-config startup-config
```
### SW-Lab1VSGJ

```bash
enable
configure terminal

vlan 10
name Administracion
exit

vlan 20
name Laboratorios
exit

vlan 30
name Direccion
exit

vlan 99
name Gestion
exit

vlan 111
name Nativa
exit

end
copy running-config startup-config
```
### SW-lab2VSGJ

```bash
enable
configure terminal

vlan 10
name Administracion
exit

vlan 20
name Laboratorios
exit

vlan 30
name Direccion
exit

vlan 99
name Gestion
exit

vlan 111
name Nativa
exit

end
copy running-config startup-config
```
## ASIGNAR LOS PUERTOS A LAS VLANs

### SW-COREvsgj
```bash
enable
configure terminal

interface fa0/9
switchport mode access
switchport access vlan 99
exit

end
copy running-config startup-config
```
### SW-Lab1VSGJ

```bash
enable
configure terminal

interface fa0/1
switchport mode access
switchport access vlan 10
exit

interface fa0/2
switchport mode access
switchport access vlan 10
exit

interface fa0/3
switchport mode access
switchport access vlan 10
exit

interface fa0/4
switchport mode access
switchport access vlan 20
exit

interface fa0/5
switchport mode access
switchport access vlan 20
exit

interface fa0/6
switchport mode access
switchport access vlan 20
exit

interface fa0/7
switchport mode access
switchport access vlan 30
exit

end
copy running-config startup-config
```
### SW-lab2VSGJ

```bash
enable
configure terminal

interface fa0/1
switchport mode access
switchport access vlan 10
exit

interface fa0/2
switchport mode access
switchport access vlan 10
exit

interface fa0/3
switchport mode access
switchport access vlan 10
exit

interface fa0/4
switchport mode access
switchport access vlan 20
exit

interface fa0/5
switchport mode access
switchport access vlan 20
exit

interface fa0/6
switchport mode access
switchport access vlan 20
exit

interface fa0/7
switchport mode access
switchport access vlan 30
exit

end
copy running-config startup-config

```
### Verificación en los switches

```bash
show vlan brief
```
### HABILITAR LOS ENLACES TRONCALES
### SW-COREvsgj

```bash

enable
configure terminal

interface fa0/1
switchport mode trunk
switchport trunk native vlan 111
switchport trunk allowed vlan 10,20,30,99,111
no shutdown
exit

interface gi0/1
switchport mode trunk
switchport trunk native vlan 111
switchport trunk allowed vlan 10,20,30,99,111
no shutdown
exit

interface gi0/2
switchport mode trunk
switchport trunk native vlan 111
switchport trunk allowed vlan 10,20,30,99,111
no shutdown
exit

end
copy running-config startup-config
```
