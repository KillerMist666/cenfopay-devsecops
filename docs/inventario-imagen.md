# Inventario y clasificación de vulnerabilidades del contenedor · CenfoPay (semana 2)

## 1. Inventario (SBOM)
- Archivo: `reportes/sbom-cyclonedx.json`   · Componentes totales: 512
- Imagen base: ________________  · Digest: `sha256:________________`
- Sistema operativo y versión: __________  · Paquetes del SO: ____  · Librerías Python: ____

## 2. Clasificación (antes / después del endurecimiento)
| Origen | Severidad | Antes | Después | Con corrección | Sin corrección | En CISA KEV |
|--------|-----------|------:|--------:|---------------:|---------------:|------------:|
| SO (trivy-so) | CRITICAL | 235 | | | | |
| SO (trivy-so) | HIGH | 2599 | | | | |
| Dependencias (trivy-dependencias) | CRITICAL | 1 | | | | |
| Dependencias (trivy-dependencias) | HIGH | 16 | | | | |
| Configuración (trivy-config / hadolint) | ALTA | | | | | |

## 3. Top 5 para priorizar
| CVE           | Paquete         | CVSS | EPSS | ¿KEV? |¿Se usa la función vulnerable?| Prioridad           |
|---------------|-----------------|------|------|-------|------------------------------|---------------------|
|CVE-2026-109518| APT             | 7.7  |1.151 |  No   |  Si                          |Actualizar componente|
|CVE-2026-53612 |bsdutils         | 7    |0.152 |  No   |  Si                          |Actualizar componente|
|CVE-2025-14087 |gir1.2-glib-2.0  | 9.8  |0.886 |  No   |  Si                          |Actualizar componente|
|CVE-2023-30861 |Flask (METADATA) | 7.5  |1.25  |  No   |  Si                          |Actualizar componente|
|CVE-2020-14343 |PyYAML (METADATA)| 9.8  |6.4   |  No   |  Si                          |Actualizar componente|



## 4. Selección de la imagen base
| Criterio                             | Opción A             | Opción B           | Opción C                                   |
|--------------------------------------|--------------------- |--------------------|--------------------------------------------|
| Imagen                               |`python:3.9` (actual) |python:3.9-bookworm |python:3.9-slim-bookworm                    |
| Mantenida / con soporte              |       No             |     No             |    No                                      |
| Tamaño (MB)                          |                      |                    | De 1 GB a 150 MB:menos piezas,menos fallas |
| Vulnerabilidades C/H                 |                      |                    |                                            |
| Tiene shell / gestor de paquetes     |                      |                    |                                            |
| Origen verificado (oficial, firmado) |                      |                    |                                            |
| Compatibilidad con la app            |                      |                    |                                            |
| **Decisión y justificación**         |                      |                    |                                            |

## 5. Verificación post-endurecimiento
Pega aquí la salida de `bash scripts/verificar-endurecimiento.sh cenfopay:local cenfopay-app-1`.
