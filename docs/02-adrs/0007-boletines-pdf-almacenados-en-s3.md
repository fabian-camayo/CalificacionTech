# ADR-0007: Boletines y reportes generados en PDF y almacenados en AWS S3

| Campo | Valor |
| --- | --- |
| Número | ADR-0007 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] Necesidades y alcance; [A4] Diagrama de componentes («Generador de PDF», «Almacenamiento de archivos (AWS S3)») y diagrama de arquitectura |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- El sistema debe generar boletines y reportes de calificaciones [A2].
- La generación de boletines (HU-14) se estimó como talla L, de módulo transversal o integración compleja [A3].

## 2. Decisión

1. El componente **Generador de PDF** exporta boletines y reportes en formato **PDF** [A4].
2. Los archivos PDF generados se guardan en **AWS S3** [A4]. La base de datos relacional no almacena los archivos.

## 3. Alternativas consideradas

No documentadas.

## 4. Consecuencias

**Positivas**
- Separa el almacenamiento de archivos del de datos transaccionales.
- Formato PDF de amplia lectura para estudiantes y acudientes.

**Negativas / trade-offs**
- Un PDF guardado puede quedar desactualizado si después se modifica una nota. **Pendiente de confirmación:** si los boletines se regeneran, se versionan o se generan bajo demanda.

**Riesgos y pendientes**
- **No documentado:** librería o servicio de generación de PDF, política de retención en S3 y control de acceso a los archivos.

## 5. Enlaces y referencias

- Specs: [0008](../03-specs/0008-generar-boletines-y-reportes.md).
- ADR relacionados: [ADR-0002](0002-despliegue-en-nube-aws.md), [ADR-0006](0006-backend-modular-alineado-a-epicas.md).
