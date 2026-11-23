# ADR-0004: API Gateway REST/HTTPS como punto único de entrada al backend

| Campo | Valor |
| --- | --- |
| Número | ADR-0004 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] CU.0001 (restricción por IP pública); [A4] Diagrama de componentes («API Gateway (REST / HTTPS)») y diagrama de arquitectura («AWS API Gateway / ALB») |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- Los tres portales web consumen los servicios del backend ([ADR-0001](0001-aplicacion-web-con-portales-por-rol.md)).
- CU.0001 establece que «el sistema maneja restricción por IP pública» [A2].
- Las peticiones deben ejecutarse con una sesión válida y con permisos por rol [A2].

## 2. Decisión

Exponer el backend mediante un **API Gateway con estilo REST sobre HTTPS** como **punto único de entrada**, que [A4]:

1. enruta las peticiones hacia los módulos del backend;
2. valida el token de sesión (JWT, ver [ADR-0005](0005-autenticacion-jwt-y-autorizacion-por-roles.md));
3. aplica la restricción por IP pública.

## 3. Alternativas consideradas

No documentadas. Las fuentes no registran la evaluación de otros estilos de API (por ejemplo, GraphQL).

## 4. Consecuencias

**Positivas**
- Un solo lugar para aplicar validación de sesión y restricción por IP.
- Comunicación cifrada entre navegador y backend.

**Negativas / trade-offs**
- El gateway es un punto único de fallo si no se despliega con redundancia (**no documentado**).

**Riesgos y pendientes**
- **Decisión no identificada:** AWS API Gateway o Application Load Balancer ([A4] indica «API Gateway / ALB»).
- **Información insuficiente:** qué significa «restricción por IP pública» (lista de IP permitidas, IP de las sedes, aplicación a todos los roles o solo a algunos). Afecta directamente a estudiantes y acudientes, que consultan desde fuera de la institución.
- **No documentado:** catálogo de endpoints, versionado de la API y formato de errores.

## 5. Enlaces y referencias

- Specs: [0001](../03-specs/0001-inicio-de-sesion.md).
- ADR relacionados: [ADR-0001](0001-aplicacion-web-con-portales-por-rol.md), [ADR-0002](0002-despliegue-en-nube-aws.md), [ADR-0005](0005-autenticacion-jwt-y-autorizacion-por-roles.md).
