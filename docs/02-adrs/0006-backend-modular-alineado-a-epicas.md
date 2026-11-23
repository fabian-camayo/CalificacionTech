# ADR-0006: Backend organizado en módulos alineados con las épicas

| Campo | Valor |
| --- | --- |
| Número | ADR-0006 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A3] Árbol de épicas EP-01–EP-06; [A4] Diagrama de componentes y diagrama de arquitectura |

> **Estado:** la descomposición en componentes está en [A4]. El estilo de despliegue de esos componentes **no está decidido** en las fuentes (ver §4). Se mantiene como *Propuesto*.

## 1. Contexto

- El alcance se organizó en seis épicas [A3].
- [A4] indica que «los componentes del backend y de reportes se alinean con las seis épicas definidas en la Actividad 3».

## 2. Decisión

Organizar el backend en componentes con responsabilidades separadas, uno por área funcional [A4]:

| Paquete | Componente | Épica | Responsabilidad [A4] |
| --- | --- | --- | --- |
| Transaccional | Seguridad y acceso | EP-01 | Inicio de sesión, recuperación de contraseña, roles y permisos, bloqueo por intentos fallidos y log de accesos. |
| Transaccional | Gestión académica | EP-02 | Sedes, jornadas, grupos, asignaturas, asignación de docentes, apertura y cierre de periodos. |
| Transaccional | Gestión de calificaciones | EP-03 | Registro y modificación de notas, validación de la escala 0.0–5.0, cálculo de promedios y definitivas. |
| Transaccional | Trazabilidad | EP-06 | Historial de cambios: usuario, fecha, valor anterior y nuevo. |
| Reportes | Consulta de calificaciones | EP-04 | Consultas con filtros según el rol. |
| Reportes | Boletines y reportes | EP-05 | Boletines por estudiante; reportes por grupo y periodo. |
| Reportes | Generador de PDF | EP-05 | Exportación de boletines y reportes a PDF. |

## 3. Alternativas consideradas

No documentadas.

## 4. Consecuencias

**Positivas**
- Trazabilidad directa entre épica, componente y Spec.
- Separación entre operaciones transaccionales y de consulta/reportes.

**Negativas / trade-offs**
- Información insuficiente para evaluar el costo operativo, porque el estilo de despliegue no está definido.

**Riesgos y pendientes**
- **Decisión no identificada:** microservicios o monolito modular. [A4] menciona «los microservicios y módulos principales del sistema» ejecutados en EC2/ECS, sin elegir uno de los dos estilos.
- **Inconsistencia de fuentes:** el diagrama de despliegue agrupa «Reportes EP-04 / EP-05» en un módulo; el de componentes los separa en tres componentes.
- **Decisión no identificada:** lenguaje y framework del backend.

## 5. Enlaces y referencias

- Specs: [03-specs](../03-specs/) (cada Spec indica su componente).
- ADR relacionados: [ADR-0002](0002-despliegue-en-nube-aws.md), [ADR-0007](0007-boletines-pdf-almacenados-en-s3.md), [ADR-0010](0010-historial-de-cambios-en-base-de-datos.md).
