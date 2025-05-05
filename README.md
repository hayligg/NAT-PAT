# NAT-PAT
# Proyecto de NAT Estática, NAT Dinámica y PAT con VLANs

## 🧾 Descripción
Este laboratorio simula una pequeña red empresarial utilizando 3 VLANs conectadas a un router que implementa:
- **Segmentación con VLANs**
- NAT Estática (para asignar manualmente una IP pública a un servidor interno).
- NAT Dinámica (mediante un pool de direcciones públicas).
- PAT (Port Address Translation) para compartir una sola IP pública entre múltiples dispositivos internos.

## 📌 Objetivos de Aprendizaje
- Configurar NAT estática, dinámica y PAT en un entorno simulado.
- Configurar y conectar múltiples VLANs a un router (router-on-a-stick).
- Analizar cómo se comporta la traducción de direcciones en diferentes escenarios.

## Topologia

![image alt](https://github.com/hayligg/NAT-PAT/blob/c160069e70a07f5fd37aea2485aaa39ea6dd6f66/TopologiaD.png)
 **Dispositivo**        | **Función**                | **Configuraciones Clave**           |
|-----------------------|----------------------------|-------------------------------------|
| **Router Cisco     ** | Gateway/NAT/PAT            | Subinterfaces VLANs, NAT/PAT, Rutas |
| **Switch Cisco     ** | Core (Routing Inter-VLAN)  | VLANs 10/20/30, Trunking            |
| **Router Genérico**   | Simulación de Internet     | IP: 200.100.50.1/24

## ⚙️ Tecnologías Utilizadas
- Cisco Packet Tracer
- Cisco IOS CLI
- Comandos: `ip nat inside`, `ip nat outside`, `ip nat pool`, `ip nat inside source`, `access-lists`
## ⚙️ Configuraciones Clave

### 1. Switch SW1 (VLANs + Routing)
vlan 10
 name ADMIN
vlan 20
 name Cont
vlan 30
 name Ing

ip routing
interface FastEthernet 0/1
 switchport mode trunk
 
### 2. Router R1 (NAT/PAT + Routing) 
interface Gig0/0.10
 encapsulation dot1Q 10
 ip nat inside
interface Gig0/0.20
 encapsulation dot1Q 20
 ip nat inside
interface Gig0/1
 ip nat outside

! NAT Estática
ip nat inside source static 192.168.10.100 200.100.50.100

! NAT Dinámica
ip nat pool NAT-DYN 200.100.50.101 200.100.50.150 netmask 255.255.255.0
ip nat inside source list 1 pool NAT-DYN

! PAT
ip nat inside source list 2 interface Gig0/1 overload
## Capturas
![image alt](https://github.com/hayligg/NAT-PAT/blob/1eafd94a04704d403313660844915257310a1ea5/NAT%20translation.PNG)
 
## 👤 Autor

- **Carlos Saldaña**
- **Correo**: [c.a.saldana20@gmail.com](mailto:c.a.sadlana20@gmail.com)
- **LinkedIn**: [linkedin.com/in/carlos-saldana](www.linkedin.com/in/carlos-saldaña-candanedo-720426183)


