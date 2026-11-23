# ADR-0002: Despliegue en la nube de Amazon Web Services (AWS)

| Campo | Valor |
| --- | --- |
| Número | ADR-0002 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A3] §1.5 Recursos adicionales; [A4] Diagrama de arquitectura y despliegue (AWS) |

> **Estado:** [A4] describe que el sistema «se despliega sobre una arquitectura basada en la nube de Amazon Web Services». Las fuentes no registran una aprobación formal por parte de la institución; por eso se mantiene como *Propuesto*.

## 1. Contexto

- La operación abarca 3 sedes, 4 jornadas por sede y aproximadamente 90 grupos [A4].
- El sistema debe estar disponible desde un navegador y centralizar la información de las sedes [A2].
- [A4] justifica la elección en la búsqueda de «alta disponibilidad, seguridad por roles y rendimiento óptimo».
- La estimación incluye la suscripción «AWS (EC2, RDS, S3) — Cloud para desarrollo y pruebas» por $ 1.200.000 [A3].

## 2. Decisión

Desplegar el sistema en AWS con la siguiente topología [A4]:

| Capa | Servicio |
| --- | --- |
| Red y entrada | AWS API Gateway / ALB (ver [ADR-0004](0004-api-gateway-rest-https-punto-unico-de-entrada.md)) |
| Aplicación | AWS EC2 / ECS (backend; ver [ADR-0006](0006-backend-modular-alineado-a-epicas.md)) |
| Datos | AWS RDS con PostgreSQL (ver [ADR-0003](0003-base-de-datos-postgresql-centralizada.md)) |
| Archivos | AWS S3 para boletines y reportes PDF (ver [ADR-0007](0007-boletines-pdf-almacenados-en-s3.md)) |

## 3. Alternativas consideradas

No documentadas. Las fuentes no registran la evaluación de otros proveedores ni de un despliegue local en la institución.

## 4. Consecuencias

**Positivas**
- Infraestructura centralizada accesible desde las 3 sedes.
- Servicios gestionados para base de datos (RDS) y almacenamiento de archivos (S3).

**Negativas / trade-offs**
- Dependencia de un proveedor externo y de su disponibilidad.
- Costo recurrente de suscripción [A3].

**Riesgos y pendientes**
- **Inconsistencia de fuentes:** [A3] presupuesta AWS «para desarrollo y pruebas»; [A4] lo presenta como infraestructura de despliegue. **Pendiente de confirmación:** el costo y el entorno de producción.
- **Decisión no identificada:** EC2 o ECS para el backend ([A4] indica «EC2 / ECS»; el diagrama muestra «Backend AWS EC2»).
- **Decisión no identificada:** API Gateway o ALB ([A4] indica «API Gateway / ALB»).
- **No documentado:** región, alta disponibilidad multizona, copias de seguridad y objetivos de disponibilidad (RTO/RPO).

## 5. Enlaces y referencias

- ADR relacionados: [ADR-0003](0003-base-de-datos-postgresql-centralizada.md), [ADR-0004](0004-api-gateway-rest-https-punto-unico-de-entrada.md), [ADR-0006](0006-backend-modular-alineado-a-epicas.md), [ADR-0007](0007-boletines-pdf-almacenados-en-s3.md).
- Estrategia: [strategy.md §4](../01-strategy/strategy.md#4-amenazas-y-erosión) (dependencia de terceros).
