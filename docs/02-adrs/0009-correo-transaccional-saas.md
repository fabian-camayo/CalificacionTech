# ADR-0009: Servicio de correo transaccional externo (SaaS)

| Campo | Valor |
| --- | --- |
| Número | ADR-0009 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] CU.0001 secuencia alternativa; [A3] §1.5 («Servicio de correo transaccional — API / SaaS», $ 60.000); [A4] Diagrama de componentes y diagrama de arquitectura |

> **Estado:** decisión presente en la estimación [A3] y en el diseño [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- La recuperación de contraseña envía un enlace de restablecimiento al correo asociado al usuario [A2].
- Cuando el coordinador rechaza una solicitud de modificación en periodo cerrado, «se notifica al docente» [A4, BPMN 1].

## 2. Decisión

Usar un **servicio de correo transaccional externo (SaaS, vía API)** —es decir, comprar el servicio en lugar de construirlo— para enviar los enlaces de recuperación de contraseña y las notificaciones del sistema [A3][A4].

## 3. Alternativas consideradas

No documentadas.

## 4. Consecuencias

**Positivas**
- No se opera infraestructura propia de correo.

**Negativas / trade-offs**
- Dependencia de un proveedor externo para recuperar contraseñas.

**Riesgos y pendientes**
- **Decisión no identificada:** proveedor del servicio.
- **Información insuficiente:** catálogo de notificaciones. Solo se documenta el rechazo de la autorización en periodo cerrado; el canal de esa notificación no se especifica.
- **Inconsistencia de fuentes:** [A4] habla de «envío masivo», mientras que el alcance excluye «un sistema completo de comunicación con acudientes» [A2]. El uso documentado es transaccional.

## 5. Enlaces y referencias

- Specs: [0002](../03-specs/0002-recuperar-contrasena.md), [0006](../03-specs/0006-registrar-y-modificar-calificaciones.md).
- ADR relacionados: [ADR-0002](0002-despliegue-en-nube-aws.md).
