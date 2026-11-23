# ADR-0010: Historial de cambios de calificaciones como componente propio con persistencia en la base de datos

| Campo | Valor |
| --- | --- |
| Número | ADR-0010 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] Problema, necesidades y CU.0002; [A3] EP-06; [A4] Diagrama de componentes («Trazabilidad (EP-06)»), BPMN 1 (tarea «Guardar notas … y registrar traza») y diagrama de arquitectura («historial de auditoría») |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- Hoy no se puede identificar quién cambió una calificación, cuándo lo hizo ni qué modificó [A2].
- «Toda creación o cambio debe quedar en el historial de calificaciones» [A2, CU.0002].
- Cada modificación debe registrar usuario responsable, fecha, valor anterior y valor nuevo [A3, HU-02 CA-6].

## 2. Decisión

1. La trazabilidad es un **componente transaccional propio (Trazabilidad, EP-06)** [A4].
2. El historial se guarda en la **base de datos PostgreSQL centralizada** junto con las calificaciones [A4].
3. El registro de la traza forma parte del mismo paso de guardado de las notas [A4, BPMN 1, paso 8].

## 3. Alternativas consideradas

| Alternativa | Motivo por el que no se eligió |
| --- | --- |
| Hojas de cálculo sin registro de cambios (situación actual) | No permite identificar responsable, fecha ni valor modificado [A2]. |

No se documentan otras alternativas técnicas.

## 4. Consecuencias

**Positivas**
- Atiende directamente el problema de trazabilidad (P3).
- Consultable con el mismo motor que las calificaciones.

**Negativas / trade-offs**
- El historial crece con cada cambio. **No documentado:** política de retención.

**Riesgos y pendientes**
- **Pendiente de confirmación:** si el guardado de la nota y su traza son atómicos (CU.0002 indica que, si falla el guardado, «no altera la nota anterior», pero no menciona la traza).
- **No documentado:** si el historial es inmutable y quién puede consultarlo (HU-18).

## 5. Enlaces y referencias

- Specs: [0006](../03-specs/0006-registrar-y-modificar-calificaciones.md), [0009](../03-specs/0009-trazabilidad-de-cambios.md).
- ADR relacionados: [ADR-0003](0003-base-de-datos-postgresql-centralizada.md), [ADR-0006](0006-backend-modular-alineado-a-epicas.md).
