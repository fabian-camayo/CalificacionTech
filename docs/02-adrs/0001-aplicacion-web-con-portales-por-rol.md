# ADR-0001: Aplicación web accesible por navegador, organizada en portales por rol

| Campo | Valor |
| --- | --- |
| Número | ADR-0001 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] Necesidades y restricciones de CU.0001–CU.0003; [A4] Diagrama de componentes (paquete «Presentación – Aplicación web (navegador)») |

> **Estado:** la decisión figura en el diseño de [A4]. Las fuentes no registran una aprobación formal; por eso se mantiene como *Propuesto*.

## 1. Contexto

- La institución necesita que el sistema esté disponible desde un navegador web [A2, Necesidades]. Los tres casos de uso fijan como restricción que «el acceso es web, desde un navegador» [A2].
- Cinco roles con alcances distintos de operación y consulta: administrador, coordinador, docente, estudiante y acudiente [A2].
- Estudiantes y acudientes deben consultar las notas con usuario y contraseña [A2].

## 2. Decisión

La capa de presentación es una **aplicación web (navegador)** compuesta por tres portales [A4]:

| Portal | Responsabilidad [A4] |
| --- | --- |
| Portal Docente | Seleccionar grupo y asignatura, registrar y modificar calificaciones y consultar las notas de sus grupos. |
| Portal Estudiante / Acudiente | Consultar notas, promedios y boletines propios o de los estudiantes a cargo. |
| Portal Coordinación / Admin. | Administrar usuarios, sedes, jornadas, grupos y periodos; autorizar cambios en periodos cerrados; reportes. |

Los clientes acceden por **HTTPS** [A4, diagrama de despliegue].

## 3. Alternativas consideradas

No documentadas. Las fuentes no registran la evaluación de otros canales (por ejemplo, aplicación móvil nativa o de escritorio).

## 4. Consecuencias

**Positivas**
- Cumple la necesidad de acceso desde navegador sin instalación en los equipos de la institución.
- La separación por portal se alinea con la restricción de permisos por rol.

**Negativas / trade-offs**
- Información insuficiente: las fuentes no describen costos asociados a esta decisión.

**Riesgos y pendientes**
- **Decisión no identificada:** tecnología o framework del frontend.
- **Pendiente de confirmación:** navegadores y versiones soportados.
- **Pendiente de confirmación:** si los tres portales son aplicaciones separadas o una sola aplicación con menú por rol. Las vistas de [VIS] muestran el mismo menú lateral (Inicio, Grupos, Calificaciones, Reportes) para docente y estudiante.

## 5. Enlaces y referencias

- Specs: [0001](../03-specs/0001-inicio-de-sesion.md), [0006](../03-specs/0006-registrar-y-modificar-calificaciones.md), [0007](../03-specs/0007-consultar-calificaciones.md).
- ADR relacionados: [ADR-0004](0004-api-gateway-rest-https-punto-unico-de-entrada.md), [ADR-0005](0005-autenticacion-jwt-y-autorizacion-por-roles.md).
