# Spec 0009: Trazabilidad de cambios de calificaciones

| Campo | Valor |
| --- | --- |
| ID | SPEC-0009 |
| Épica | EP-06 Trazabilidad de cambios |
| Historias de usuario | HU-17 Registrar modificaciones (L, 36,83 h); HU-18 Consultar historial de notas (M, 26,00 h); HU-19 Identificar responsable y fecha (XS, 8,22 h) |
| Caso de uso | No hay caso de uso propio; la regla se origina en CU.0002 |
| Actores | Sistema (registro automático). Quién consulta el historial: **Pendiente de confirmación** |
| Prioridad | **No documentado** |
| Componente | Trazabilidad (EP-06) |
| ADR relacionados | [ADR-0003](../02-adrs/0003-base-de-datos-postgresql-centralizada.md), [ADR-0010](../02-adrs/0010-historial-de-cambios-en-base-de-datos.md) |
| Mockup | No definido: las fuentes no describen la pantalla del historial |
| Estado | Borrador — el registro está definido; la consulta tiene información insuficiente |

## 1. Resumen y objetivo

Mantener un historial de toda creación o modificación de calificaciones que permita identificar quién hizo el cambio, cuándo y qué valor cambió, atendiendo el problema de falta de trazabilidad [A2][A3][A4].

## 2. Alcance

**Dentro**
- Registro automático de cada creación y modificación de nota [A2][A3 HU-17].
- Identificación del responsable y la fecha [A3 HU-19].
- Consulta del historial de notas [A3 HU-18].

**Fuera**
- Log de accesos e inicios de sesión ([Spec 0001](0001-inicio-de-sesion.md)).

## 3. Requisitos

### 3.1. Requisitos funcionales

| ID | Requisito | Fuente |
| --- | --- | --- |
| RF-0009-01 | El sistema debe registrar en el historial toda creación o modificación de una calificación. | [A2] CU.0002; [A3] HU-17 |
| RF-0009-02 | Cada registro debe contener el usuario responsable, la fecha, el valor anterior y el valor nuevo. | [A3] HU-02 CA-6; [A4] |
| RF-0009-03 | El sistema debe permitir consultar el historial de notas. | [A3] HU-18 |

### 3.2. Reglas de negocio

| ID | Regla | Fuente |
| --- | --- | --- |
| RN-0009-01 | No hay creación ni modificación de nota sin registro en el historial. | [A2] CU.0002 |

### 3.3. Requisitos no funcionales

| ID | Categoría | Requisito y métrica | Fuente |
| --- | --- | --- | --- |
| RNF-0009-01 | Rendimiento | El guardado de la calificación, que incluye el registro de la traza en BPMN 1, no supera 2 segundos. | [A2]; [A4] BPMN 1 paso 8 |

## 4. Datos y contratos

| Entidad | Atributos | Fuente |
| --- | --- | --- |
| Registro de historial | Usuario responsable, fecha, valor anterior, valor nuevo, calificación afectada | [A2][A3][A4] |

Hora exacta además de la fecha, motivo del cambio y referencia a la autorización en periodo cerrado: **No documentado**.

## 5. Flujos y estados

El registro ocurre dentro del flujo de guardado de [Spec 0006](0006-registrar-y-modificar-calificaciones.md) (BPMN 1, paso 8). El flujo de consulta del historial: **No documentado**.

## 6. Casos borde y errores

| Caso | Comportamiento esperado | Fuente |
| --- | --- | --- |
| Primera creación de una nota | Valor anterior: **No documentado** (vacío o nulo). | — |
| Falla el guardado | La nota anterior no cambia [A2]; el efecto sobre el historial: **Pendiente de confirmación**. | [A2] CU.0002 error 4 |

## 7. Criterios de aceptación

```gherkin
Escenario: Modificación registrada
  Dado una nota guardada de 3,0
  Cuando un docente la modifica a 3,5 y confirma
  Entonces el historial registra el usuario responsable, la fecha, el valor anterior 3,0 y el valor nuevo 3,5

Escenario: Creación registrada
  Dado un estudiante sin nota en una asignatura y periodo
  Cuando el docente registra una nota y guarda
  Entonces el historial registra el usuario responsable, la fecha y el valor nuevo
```

**Pendiente de definición:** criterios de aceptación de la consulta del historial (HU-18).

## 8. Riesgos y pendientes

| ID | Tipo | Descripción |
| --- | --- | --- |
| P-0009-01 | No documentado | Roles que pueden consultar el historial y filtros disponibles. |
| P-0009-02 | No documentado | Inmutabilidad y retención del historial. |
| P-0009-03 | Pendiente de confirmación | Atomicidad entre guardado de la nota y registro de la traza. |
