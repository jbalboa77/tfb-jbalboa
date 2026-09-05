# TFB — Diseño y segmentación de red Zero Trust para Legal JBA y Asesores

**Autor:** Joel Balboa
**Tutor:** Francisco Manuel Collazos Gámiz
**Titulación:** Bàtxelor en Informàtica — Universitat Carlemany
**Edición:** 2510 (2025-2026)

## Descripción

Trabajo Final de Bàtxelor centrado en el diseño, implementación y validación de una arquitectura de red segura basada en principios Zero Trust.
Incluye segmentación mediante VLANs, políticas de firewall de mínimo privilegio, sistema de detección de intrusiones (Suricata), acceso remoto mediante WireGuard y auditorías de seguridad pre/post implementación.

La memoria completa (PDF) se encuentra en `Entregables/Entregable3/`.

## Estructura del repositorio

```
TFB/
├── Auditorias/
│   ├── Pre/            # Resultados Nmap y verificaciones manuales — red plana (situación inicial)
│   └── Post/           # Resultados Nmap y verificaciones manuales — red segmentada
├── Documentacion/       # Documentos administrativos del TFB (calendario, compromiso tutor, plan docente...)
├── Entregables/
│   ├── Entregable1/     # Documentos e información relacionada con el Entregable 1
│   ├── Entregable2/     # Documentos e información relacionada con el Entregable 2
│   └── Entregable3/     # Documentos e información relacionada con el Entregable 3
├── FW-Config/           # Backups de config.xml de OPNsense, por fecha
├── FW-Rules/            # Reglas de firewall exportadas en CSV, por nivel de configuración
├── gns3-project/        # Proyecto GNS3 exportado (topología, sin imágenes base — ver enlace de descarga)
├── Imagenes/            # Capturas de evidencia (consola OPNsense, GNS3, resultados de auditoría...)
├── .gitignore
└── README.md
```

## Especificaciones técnicas

| Elemento | Descripción |
|---|---|
| Equipo anfitrión | MacBook Pro (Intel) |
| Virtualización | VMware Fusion Pro |
| Emulación de red | GNS3 (cliente + GNS3 VM) |
| Firewall / Router | OPNsense 26.1 (1 vCPU / 1 GB RAM) |
| Sistema de detección de intrusiones | Suricata 8.0.3 (integrado en OPNsense), ruleset ET Open |
| VPN de acceso remoto | WireGuard (integrado en OPNsense), autenticación por clave Curve25519 + PSK |
| Switches | 2 × switch virtual, enlace trunk 802.1Q entre ambos |
| Endpoints | Debian 12 — servidor de expedientes (Samba, vsftpd, SSH) y endpoint con Xrdp + Samba |
| Endpoint de auditoría | Debian 12 (Nmap 7.93, smbclient, ssh, dig/nslookup) |
| Nodos ligeros | VPCS (pila IP mínima, sin servicios) |
| Herramienta de escaneo | Nmap 7.93 |

*(Tabla equivalente a la del apartado 13 de la memoria — Especificaciones técnicas.)*

## Proyecto GNS3 completo y máquina virtual

Por su tamaño, estos archivos **no se alojan en este repositorio** (excluidos vía `.gitignore`):

| Archivo | Enlace de descarga |
|---|---|
| `TFB-JoelBalboa-GNS3.gns3project` | [Descargar](https://drive.google.com/file/d/1Wi-_sEu1OSPlOyXjBQqvOZco2IwG-a_c/view?usp=sharing) |
| `TFB-JoelBalboa-GNS3.gns3project` | [Descargar](https://drive.google.com/file/d/1jjKgcSabthOYQC5ekeTaH0IFmdD0Sn3l/view?usp=share_link) |
| GNS3 VM INICIAL(VMware Fusion) | [Descargar](https://drive.google.com/file/d/1BVATUqAd60bHmadnbH9cUI2mWH2O_RBW/view?usp=share_link) |
| GNS3 VM FINAL(VMware Fusion) | [Descargar](https://drive.google.com/file/d/1wqhBpTFEzdGamy4tmoIwIUeXjxAJvDAo/view?usp=share_link) |

## Cómo reproducir el laboratorio

1. Instalar VMware Fusion y GNS3 (cliente + GNS3 VM oficial) — ver Anexo A de la memoria.
2. Importar los appliances OPNsense y Debian desde el Marketplace de GNS3 — ver Anexo B.
3. Importar la VM GNS3 y el proyecto en GNS3 (`gns3-project/TFB-JoelBalboa-GNS3.gns3project`) desde el enlace de descarga anterior.
4. Restaurar la configuración de OPNsense desde el backup más reciente de `FW-Config/` (System → Configuration → Backups → Restore).
5. Consultar `FW-Rules/` para las reglas de firewall aplicadas por interfaz.
