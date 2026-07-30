# TFB — Diseño y segmentación de red Zero Trust para Legal JBA y Asesores

**Autor:** Joel Balboa
**Tutor:** Francisco Manuel Collazos Gámiz
**Titulación:** Bàtxelor en Informàtica — Universitat Carlemany
**Edición:** 2510 (2025-2026)

## Descripción

Trabajo Final de Bàtxelor centrado en el diseño, implementación y validación de una arquitectura de red segura basada en principios Zero Trust. 
Incluye segmentación mediante VLANs, políticas de firewall de mínimo privilegio, sistema de detección de intrusiones (Suricata) y auditorías de seguridad pre/post implementación.

**Entorno técnico:** GNS3 · OPNsense · Debian · VMware Fusion Pro (macOS, Intel)

## Estructura del repositorio

TFB/
├── Auditorias/
│ ├── Pre/ # Resultados Nmap y verificaciones manuales — red plan (situación inicial)
│ └── Post/ # Resultados Nmap y verificaciones manuales — red segmentada
├── Documentacion/ # Documentos administrativos del TFB (calendario, compromiso tutor, plan docente...)
├── Entregables/
│ ├── Entregable1/ Documentos e información relacionada con el Entregable1
│ └── Entregable2/ Documentos e información relacionada con el Entregable2
│ └── Entregable3/ Documentos e información relacionada con el Entregable3
├── FW-Config/ # Backups de config.xml de OPNsense
├── FW-Rules/ # Reglas de firewall exportadas en CSV
├── gns3-project/ # Proyecto GNS3 exportado (topología, sin imágenes base — ver enlace de descarga)
├── Imagenes/ # Capturas de evidencia (consola OPNsense, GNS3, resultados de auditoría...)
├── .gitignore
└── README.md

## Proyecto GNS3 completo y máquina virtual

Por su tamaño, estos archivos **no se alojan en este repositorio** (están excluidos vía `.gitignore`):

| Archivo | Tamaño aprox. | Descarga |
|---|---|---|
| `TFB-JoelBalboa-GNS3.gns3project` | *(https://drive.google.com/drive/folders/1fusnXwhiPQ4gHdwgDWkHe63tafWOeTSN?usp=share_link)* |

| `GNS3 VM (VMware Fusion)` |  *(https://drive.google.com/file/d/1BVATUqAd60bHmadnbH9cUI2mWH2O_RBW/view?usp=share_link)* |


## Cómo reproducir el laboratorio

1. Instalar VMware Fusion y GNS3 (cliente + GNS3 VM oficial) — ver Anexo A de la memoria.
2. Importar los appliances OPNsense y Debian desde el Marketplace de GNS3 — ver Anexo B.
3. Importar la VM GNS3 y el proyecto en GNS3 (`gns3-project/TFB-JoelBalboa-GNS3.gns3project`) desde el enlace de descarga anterior.
4. Restaurar la configuración de OPNsense desde el backup más reciente de `FW-Config/` (System → Configuration → Backups → Restore).
5. Consultar `FW-Rules/` para las reglas de firewall aplicadas por interfaz.
