# Spec 0004: Gestionar estructura académica (sedes, jornadas, grupos y asignaturas)

| Campo | Valor |
| --- | --- |
| ID | SPEC-0004 |
| Épica | EP-02 Gestión académica |
| Historias de usuario | HU-06 Gestionar sedes y jornadas (S, 13,08 h); HU-07 Gestionar grupos y asignaturas (M, 26,00 h) |
| Caso de uso | No hay caso de uso detallado |
| Actores | Coordinador / administrador (según «Portal Coordinación / Admin.» [A4]) |
| Prioridad | **No documentado** |
| Componente | Gestión académica (EP-02) |
| ADR relacionados | [ADR-0006](../02-adrs/0006-backend-modular-alineado-a-epicas.md), [ADR-0008](../02-adrs/0008-integracion-con-sistema-de-matriculas-existente.md) |
| Mockup | No definido: las fuentes no describen pantallas para esta funcionalidad |
| Estado | Borrador — información insuficiente |

> HU-06 y HU-07 se agrupan en una sola Spec porque [A4] las asigna a un mismo componente («configuración de sedes, jornadas, grupos, asignaturas, asignación de docentes») y ninguna de las dos tiene caso de uso ni criterios de aceptación propios. Si se documentan, pueden separarse en Specs distintas.

## 1. Resumen y objetivo

Mantener la estructura académica sobre la que se organizan las calificaciones —sedes, jornadas, grupos y asignaturas— y la asignación de docentes a grupos y asignaturas [A3][A4].

## 2. Alcance

**Dentro**
- Configuración de sedes y jornadas [A3 HU-06; A4].
- Configuración de grupos y asignaturas [A3 HU-07; A4].
- Asignación de docentes a grupos y asignaturas [A4].

**Fuera**
- Matrícula e inscripción de estudiantes en grupos [A2].
- Periodos académicos ([Spec 0005](0005-configurar-periodos-academicos.md)).

## 3. Requisitos

### 3.1. Requisitos funcionales

| ID | Requisito | Fuente |
| --- | --- | --- |
| RF-0004-01 | El sistema debe permitir configurar las sedes y sus jornadas. | [A3] HU-06; [A4] |
| RF-0004-02 | El sistema debe permitir configurar grupos y asignaturas. | [A3] HU-07; [A4] |
| RF-0004-03 | El sistema debe permitir asignar docentes a grupos y asignaturas. | [A4] componente EP-02 |

### 3.2. Reglas de negocio

| ID | Regla | Fuente |
| --- | --- | --- |
| RN-0004-01 | La institución tiene 3 sedes, 4 jornadas por sede y alrededor de 30 grupos por sede. | [A2] |
| RN-0004-02 | Un grupo pertenece a una sede y a una jornada (se valida la consistencia de esta combinación al consultar). | [A2] CU.0003 error 2; [A4] BPMN 2 |
| RN-0004-03 | Un docente solo registra notas de los grupos y asignaturas que tiene asignados. | [A2] CU.0002 |

### 3.3. Requisitos no funcionales

No documentados para esta funcionalidad.

## 4. Datos y contratos

| Entidad | Atributos y relaciones mencionados | Fuente |
| --- | --- | --- |
| Sede | 3 sedes; tiene jornadas | [A2] |
| Jornada | 4 por sede | [A2] |
| Grupo | Pertenece a una sede y jornada; ejemplo «10 - 1» | [A2]; [VIS] |
| Asignatura | Ejemplos: Matemáticas, Física, Inglés | [VIS] |
| Asignación docente | Docente ↔ grupo ↔ asignatura | [A2][A4] |

Nombres de jornadas, atributos detallados y contratos de API: **No documentado**.

## 5. Flujos y estados

**No documentado.**

## 6. Casos borde y errores

| Caso | Comportamiento esperado | Fuente |
| --- | --- | --- |
| Combinación grupo–sede–jornada inconsistente en una consulta | El sistema solicita corregir la selección ([Spec 0007](0007-consultar-calificaciones.md)). | [A2] CU.0003 |
| Eliminar una sede, grupo o asignatura con calificaciones | **No documentado**. | — |

## 7. Criterios de aceptación

```gherkin
Escenario: Docente solo ve sus asignaciones
  Dado un docente asignado al grupo "10 - 1" en la asignatura "Matemáticas"
  Cuando abre el registro de calificaciones
  Entonces solo puede seleccionar los grupos y asignaturas que tiene asignados
```

**Pendiente de definición:** criterios de aceptación de la configuración de sedes, jornadas, grupos y asignaturas.

## 8. Riesgos y pendientes

| ID | Tipo | Descripción |
| --- | --- | --- |
| P-0004-01 | Información insuficiente | Faltan casos de uso y criterios de aceptación de HU-06 y HU-07. |
| P-0004-02 | Inconsistencia de fuentes | Los grupos se «configuran» en EP-02 [A3][A4], pero también se toman del sistema de matrículas existente [A4]. Ver [ADR-0008](../02-adrs/0008-integracion-con-sistema-de-matriculas-existente.md). |
| P-0004-03 | Pendiente de confirmación | Qué rol (coordinador o administrador) realiza cada operación. |
