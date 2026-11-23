# ADR-0005: Autenticación con token JWT y autorización por roles

| Campo | Valor |
| --- | --- |
| Número | ADR-0005 |
| Estado | Propuesto |
| Fecha | 2026-11-10 (fecha de [A4]) |
| Fuentes | [A2] CU.0001, CU.0002, CU.0003; [A3] EP-01; [A4] Diagrama de componentes («Seguridad y acceso (EP-01)») y diagrama de arquitectura («valida los tokens de autenticación JWT») |

> **Estado:** decisión presente en el diseño de [A4] sin registro de aprobación formal; se mantiene como *Propuesto*.

## 1. Contexto

- Cinco roles con alcances distintos: administrador, coordinador, docente, estudiante y acudiente [A2].
- El usuario se autentica con su documento de identidad y contraseña desde un formulario web [A2].
- Las restricciones de alcance dependen del rol y de las asignaciones (grupos y asignaturas del docente; estudiantes a cargo del acudiente) [A2].
- Los accesos e intentos fallidos deben registrarse [A2][A3].

## 2. Decisión

1. Tras validar usuario, contraseña, rol y estado, el módulo **Seguridad y acceso (EP-01)** emite un **token JWT** que identifica la sesión [A4].
2. El API Gateway **valida el token** en cada petición ([ADR-0004](0004-api-gateway-rest-https-punto-unico-de-entrada.md)).
3. Los permisos se asignan **por rol** (control de acceso basado en roles) y el módulo EP-01 gestiona roles y permisos, bloqueo por intentos fallidos y log de accesos [A4].

## 3. Alternativas consideradas

No documentadas.

## 4. Consecuencias

**Positivas**
- La validación de la sesión se centraliza en el punto de entrada.
- Un modelo de permisos único para los cinco roles.

**Negativas / trade-offs**
- Información insuficiente: las fuentes no describen la estrategia de expiración ni de revocación del token.

**Riesgos y pendientes**
- **No documentado:** duración de la sesión y del token, cierre de sesión, renovación.
- **No documentado:** número de intentos fallidos permitidos y duración del bloqueo temporal.
- **Información insuficiente:** la matriz completa de permisos por rol. Solo se documentan los alcances de CU.0002 y CU.0003.

## 5. Enlaces y referencias

- Specs: [0001](../03-specs/0001-inicio-de-sesion.md), [0002](../03-specs/0002-recuperar-contrasena.md), [0003](../03-specs/0003-administrar-usuarios-roles-y-permisos.md).
- ADR relacionados: [ADR-0004](0004-api-gateway-rest-https-punto-unico-de-entrada.md).
