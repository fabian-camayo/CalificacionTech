# ADR-0003: Base de datos relacional PostgreSQL centralizada (AWS RDS)

| Campo | Valor |
| --- | --- |
| Número | ADR-0003 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] Problema y necesidades; [A4] Diagrama de componentes (paquete «Datos»), BPMN 2 (carril «Base de Datos (PostgreSQL / AWS RDS)») y diagrama de arquitectura |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- Situación actual: cada docente usa hojas de cálculo independientes, lo que genera inconsistencias por diferentes archivos y copias, y dificulta mantener información centralizada entre sedes, jornadas y grupos [A2].
- El sistema debe organizar las notas por estudiante, asignatura, grupo y periodo académico, y permitir la consulta «rápida y centralizada» [A2].
- La postcondición de CU.0002 exige que la calificación quede «almacenada de forma centralizada en un tiempo máximo de 2 segundos» [A2].

## 2. Decisión

Usar una **única base de datos relacional PostgreSQL**, gestionada en **AWS RDS**, como almacenamiento centralizado de usuarios, estructura académica, calificaciones e historial de cambios [A4].

## 3. Alternativas consideradas

| Alternativa | Motivo por el que no se eligió |
| --- | --- |
| Hojas de cálculo independientes por docente (situación actual) | Causa inconsistencias, errores de cálculo y falta de trazabilidad [A2]. |

No se documentan otros motores de base de datos evaluados.

## 4. Consecuencias

**Positivas**
- Una fuente única de las calificaciones de todas las sedes (atiende P1 de la estrategia).
- Soporte para relacionar estudiante, asignatura, grupo, sede, jornada y periodo.

**Negativas / trade-offs**
- La base de datos se convierte en un componente crítico: su indisponibilidad detiene registro y consulta.

**Riesgos y pendientes**
- **No documentado:** modelo de datos (entidades, atributos, relaciones), política de copias de seguridad y retención del historial.
- **Pendiente de confirmación:** cómo se relacionan los datos locales de estudiantes y grupos con el sistema de matrículas ([ADR-0008](0008-integracion-con-sistema-de-matriculas-existente.md)).

## 5. Enlaces y referencias

- Specs: [0006](../03-specs/0006-registrar-y-modificar-calificaciones.md), [0007](../03-specs/0007-consultar-calificaciones.md), [0009](../03-specs/0009-trazabilidad-de-cambios.md).
- ADR relacionados: [ADR-0002](0002-despliegue-en-nube-aws.md), [ADR-0010](0010-historial-de-cambios-en-base-de-datos.md).
