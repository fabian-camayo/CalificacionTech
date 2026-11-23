# ADR-0008: Consultar el sistema de matrículas existente como fuente de estudiantes y grupos

| Campo | Valor |
| --- | --- |
| Número | ADR-0008 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] Alcance («No reemplazará el sistema de matrículas existente»); [A4] Diagrama de componentes («Sistema de matrículas (existente)») y diagrama de arquitectura («Conexión vía API») |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- La institución cuenta con un sistema de matrículas existente [A2].
- El sistema de notas **no** gestionará matrículas ni procesos de inscripción, ni reemplazará ese sistema [A2].
- CU.0002 requiere listar «los estudiantes del grupo» para registrar sus notas [A2].

## 2. Decisión

El Sistema de Notas Académicas **consulta vía API** el sistema de matrículas existente como **fuente de estudiantes y grupos matriculados**, sin reemplazarlo [A4].

## 3. Alternativas consideradas

No documentadas.

## 4. Consecuencias

**Positivas**
- Evita duplicar la gestión de matrículas, que está fuera de alcance.

**Negativas / trade-offs**
- Dependencia de la disponibilidad y la calidad de datos de un sistema externo ([strategy.md §4](../01-strategy/strategy.md#4-amenazas-y-erosión), A1).

**Riesgos y pendientes**
- **Información insuficiente:** contrato de la API del sistema de matrículas (endpoints, formato, autenticación).
- **Pendiente de confirmación:** consulta en línea o sincronización periódica; qué ocurre si el sistema de matrículas no responde.
- **Inconsistencia de fuentes:** [A3] estima la HU-07 «Gestionar grupos y asignaturas» y [A4] asigna al componente de Gestión académica la «configuración de … grupos», mientras que este ADR toma los grupos del sistema de matrículas. **Pendiente de confirmación:** qué sistema es dueño del dato «grupo».

## 5. Enlaces y referencias

- Specs: [0004](../03-specs/0004-gestionar-estructura-academica.md), [0006](../03-specs/0006-registrar-y-modificar-calificaciones.md).
- ADR relacionados: [ADR-0003](0003-base-de-datos-postgresql-centralizada.md).
