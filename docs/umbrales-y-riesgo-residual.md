# Justificación de umbrales de bloqueo y riesgos residuales · CenfoPay

> Este documento acompaña a `security/politica-umbrales.yml`. Cada número de la
> política debe tener aquí su razón. Se evalúa en el criterio 4 de la rúbrica del proyecto.

## 1. Contexto de riesgo de la aplicación
- Tipo de datos que maneja (ficticios en el curso, pero tratados como si fueran reales):
- Exposición (Internet / red interna / solo laboratorio):
- Marco de referencia aplicable (p. ej. PCI-DSS 6.2-6.3, Ley 8968, normativa SUGEF de TI):

## 2. Umbrales por herramienta
| Herramienta | Severidad | Umbral | Modo  | Por qué este número (impacto, explotabilidad, ruido, costo de bloquear) |
|-------------|-----------|-------:|--------|------------------------------------------------------------------------|
| semgrep     | ERROR     | 14     |Bloquear| Ruido por duplicidad de reglas y línea base.                           |
| zap         | High      | 0      |Bloquear| Confirmación de explotabilidad real.                                   |
| zap         | Medium    | 3      |Bloquear| Tolerancia a configuraciones de entorno.                               |
| hadolint    | error     |        |        |                                                                        |
| trivy-so    | CRITICAL / HIGH |  |        |                                                                        |
| trivy-dependencias | CRITICAL / HIGH | |  |                                                                        |
| bandit      | HIGH      |        |        |                                                                        |
| gitleaks    | SECRETO   | 0      |        |                                                                        |
| endurecimiento | ALTA   |        |        |                                                                        |
| registros   | ALTA      | 0      |        |                                                                        |
 
## 3. Disparadores
| Evento | Qué corre | Por qué |
|--------|-----------|---------|
| pull_request a main | Análisis estático|Detiene la integración antes de hacer merge si se superan los 14 errores.|
| push a main |Pipeline completo | Confirma que el código integrado funciona de forma segura en ejecución.         |
| schedule semanal |Escaneo profundo | garantiza que una vulnerabilidad recién descubierta no pase desapercibida.  |
| workflow_dispatch |Ejecución manual | Auditoría, verificación de parches y control operativo.                    | 

## 4. Riesgos residuales (lo que queda abierto después de corregir)
| # | Riesgo | Origen (hallazgo/huella) | Por qué no se corrige ahora | Control compensatorio | Dueño | Revisión |
|---|--------|--------------------------|-----------------------------|-----------------------|-------|----------|
| 1 | | | | | | |

## 5. Excepciones aprobadas
| Herramienta | ID | Justificación | Responsable | Vence |
|-------------|----|---------------|-------------|-------|
| | | | | |
