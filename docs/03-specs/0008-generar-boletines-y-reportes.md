# Spec 0008: Generar boletines y reportes de calificaciones

| Campo | Valor |
| --- | --- |
| ID | SPEC-0008 |
| Épica | EP-05 Reportes académicos |
| Historias de usuario | HU-14 Generar boletines (L, 36,83 h); HU-15 Generar reportes por grupo (M, 26,00 h); HU-16 Consultar reportes por periodo (S, 13,08 h) |
| Caso de uso | No hay caso de uso detallado (CU.0003 alt. 4 enlaza con esta funcionalidad) |
| Actores | «Usuario autorizado» [A2]. Estudiante y acudiente consultan boletines propios o de los estudiantes a cargo [A4]; coordinación y administración gestionan reportes [A4]. Matriz completa: **Pendiente de confirmación** |
| Prioridad | **No documentado** |
| Componente | Boletines y reportes (EP-05); Generador de PDF; Almacenamiento de archivos (AWS S3) |
| ADR relacionados | [ADR-0006](../02-adrs/0006-backend-modular-alineado-a-epicas.md), [ADR-0007](../02-adrs/0007-boletines-pdf-almacenados-en-s3.md) |
| Mockup | No definido: las fuentes no describen la pantalla de reportes (el menú «Reportes» de [VIS] no tiene vista asociada) |
| Estado | Borrador — información insuficiente |

## 1. Resumen y objetivo

Generar boletines de calificaciones por estudiante y reportes por grupo y periodo, exportados en PDF, para reducir el esfuerzo administrativo de mantener archivos manuales [A2][A3][A4].

## 2. Alcance

**Dentro**
- Boletines por estudiante [A3 HU-14; A4].
- Reportes por grupo [A3 HU-15; A4].
- Consulta de reportes por periodo [A3 HU-16; A4].
- Exportación a PDF y almacenamiento en S3 [A4].

**Fuera**
- Envío de boletines por correo o comunicación con acudientes: el alcance excluye un «sistema completo de comunicación con acudientes» [A2].

## 3. Requisitos

### 3.1. Requisitos funcionales

| ID | Requisito | Fuente |
| --- | --- | --- |
| RF-0008-01 | El sistema debe generar boletines por estudiante. | [A2]; [A3] HU-14; [A4] |
| RF-0008-02 | El sistema debe generar reportes por grupo. | [A3] HU-15; [A4] |
| RF-0008-03 | El sistema debe permitir consultar reportes por periodo. | [A3] HU-16; [A4] |
| RF-0008-04 | El sistema debe exportar boletines y reportes en PDF. | [A4] Generador de PDF |
| RF-0008-05 | El sistema debe guardar los PDF generados en el almacenamiento de archivos (AWS S3). | [A4] |
| RF-0008-06 | El usuario autorizado debe poder llegar a esta funcionalidad desde el resultado de una consulta de calificaciones. | [A2] CU.0003 alt. 4 |

### 3.2. Reglas de negocio

| ID | Regla | Fuente |
| --- | --- | --- |
| RN-0008-01 | Estudiantes y acudientes acceden a boletines propios o de los estudiantes a cargo. | [A4] Portal Estudiante / Acudiente |

### 3.3. Requisitos no funcionales

No documentados (tiempo de generación, tamaño, formato del PDF).

## 4. Datos y contratos

| Elemento | Información | Fuente |
| --- | --- | --- |
| Boletín | Por estudiante; PDF | [A4] |
| Reporte | Por grupo y periodo; PDF | [A4] |
| Contenido del boletín y del reporte | **No documentado** | — |

## 5. Flujos y estados

**No documentado** más allá del acceso desde la consulta (CU.0003 alt. 4).

## 6. Casos borde y errores

| Caso | Comportamiento esperado | Fuente |
| --- | --- | --- |
| Generar un boletín sin notas registradas | **No documentado**. | — |
| Nota modificada después de generar el PDF | **No documentado** (ver [ADR-0007](../02-adrs/0007-boletines-pdf-almacenados-en-s3.md)). | — |
| Fallo de la generación o del almacenamiento | **No documentado**. | — |

## 7. Criterios de aceptación

```gherkin
Escenario: Boletín en PDF
  Dado un estudiante con calificaciones registradas en un periodo
  Cuando un usuario autorizado genera su boletín
  Entonces el sistema produce un archivo PDF
  Y lo guarda en el almacenamiento de archivos

Escenario: Acceso desde la consulta
  Dado un usuario autorizado viendo el resultado de una consulta de calificaciones
  Cuando elige continuar a boletines y reportes
  Entonces el sistema lo lleva a la generación de boletines y reportes
```

**Pendiente de definición:** contenido del boletín y del reporte, roles autorizados y criterios de los reportes por grupo y periodo.

## 8. Riesgos y pendientes

| ID | Tipo | Descripción |
| --- | --- | --- |
| P-0008-01 | Información insuficiente | Faltan caso de uso y criterios de aceptación de HU-14, HU-15 y HU-16. |
| P-0008-02 | No documentado | Contenido y formato del boletín y de los reportes. |
| P-0008-03 | Pendiente de confirmación | Roles que pueden generar cada tipo de documento. |
| P-0008-04 | No documentado | Pantallas; necesarias antes de elaborar el mockup. |
