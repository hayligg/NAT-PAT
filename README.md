# NAT-PAT
# Proyecto de NAT Estática, NAT Dinámica y PAT con VLANs

## 🧾 Descripción
Este laboratorio simula una pequeña red empresarial utilizando 3 VLANs conectadas a un router que implementa:
- NAT Estática (para asignar manualmente una IP pública a un servidor interno).
- NAT Dinámica (mediante un pool de direcciones públicas).
- PAT (Port Address Translation) para compartir una sola IP pública entre múltiples dispositivos internos.

El objetivo es demostrar cómo cada tipo de NAT funciona en una red segmentada con VLANs.

## Topologia

![image alt](https://github.com/hayligg/NAT-PAT/blob/c160069e70a07f5fd37aea2485aaa39ea6dd6f66/TopologiaD.png)

## ⚙️ Tecnologías Utilizadas
- Cisco Packet Tracer
- Cisco IOS CLI
- Comandos: `ip nat inside`, `ip nat outside`, `ip nat pool`, `ip nat inside source`, `access-lists`

## 📌 Objetivos de Aprendizaje
- Configurar NAT estática, dinámica y PAT en un entorno simulado.
- Configurar y conectar múltiples VLANs a un router (router-on-a-stick).
- Analizar cómo se comporta la traducción de direcciones en diferentes escenarios.


