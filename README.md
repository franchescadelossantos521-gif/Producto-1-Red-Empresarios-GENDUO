# Producto-1-Red-Empresarial-GENDUO
Implementación de red empresarial dual-stack (IPv4/IPv6) bajo metodología Scrum (3 sprints y retrospectiva) en Cisco Modeling Labs (CML), con segmentación VLAN/VTP, EtherChannel LACP, inter-VLAN routing, enrutamiento estático y administración segura por SSH.
# Implementación de Red Empresarial — GENDUO

Repositorio correspondiente al proyecto **Producto 1** de la asignatura **Fundamentos de Enrutamiento (TI-202)** en el **Instituto Tecnológico de las Américas (ITLA)**, bajo la guía del profesor **Onel Luis Pelegrino**. El proyecto se desarrolló aplicando una estructura de trabajo ágil tipo **Scrum** organizada en **tres sprints** más su **retrospectiva**, y se implementó y validó en **Cisco Modeling Labs (CML)**.

## Introducción

El objetivo del proyecto fue diseñar, implementar y validar una topología de red empresarial dividida en dos segmentos principales interconectados mediante un enlace punto a punto (P2P) enrutado: un lado gestionado con un router (**R1**) bajo un enfoque *router-on-a-stick* y otro lado administrado mediante un switch multicapa (**SWM1**) con interfaces virtuales conmutadas (**SVI**).

La red opera en modo **dual stack (IPv4 e IPv6)** sobre los bloques asignados al **Equipo 2** (`172.18.0.0/15` y `2001:25:18::/48`), aplicando **VLSM** para optimizar el espacio de direcciones y asignando prefijos `/64` en IPv6 en correspondencia con el tamaño de las redes IPv4[cite: 1, 2, 3]. Para la segmentación lógica y la administración escalable se configuraron **VLANs**, dominios **VTP** independientes por lado, **EtherChannel (LACP)** entre switches para redundancia y mayor ancho de banda, **enrutamiento estático** entre ambos lados a través del enlace P2P y acceso administrativo remoto seguro mediante **SSH** (deshabilitando Telnet).

Durante la ejecución se tomaron decisiones técnicas y de depuración documentadas en el cierre del proyecto—como asignar el gateway de la **VLAN 31 (Gestión 2)** a la SVI correspondiente en **SWM1** (al pertenecer a su lado de la red), aislar las VLANs *Blackhull* (`99` y `199`) sin gateway para puertos apagados/sin uso y tráfico nativo, y ajustar detalles de exportación y configuración en CML para asegurar la reproducibilidad de la topología.

---

## Estructura del Repositorio

El repositorio está organizado para separar la documentación del producto, las configuraciones por dispositivo y el archivo de topología en CML:

```text
├── <carpeta-del-producto>/
│   ├── Sprints/
│   │   ├── Sprint-1/
│   │   ├── Sprint-2/
│   │   └── Sprint-3-y-Retrospectiva/
│   ├── Configuraciones/
│   │   ├── R1.txt (o .cfg)
│   │   ├── SWM1.txt (o .cfg)
│   │   ├── SW.txt (o .cfg)
│   │   ├── SW3.txt (o .cfg)
│   │   ├── SW4.txt (o .cfg)
│   │   └── SW5.txt (o .cfg)
│   └── topologia.yaml          # Archivo de topología exportado desde Cisco Modeling Labs (CML)
└── README.md
