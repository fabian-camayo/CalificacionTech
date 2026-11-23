# Spec 0003: Administrar usuarios, roles y permisos

| Campo | Valor |
| --- | --- |
| ID | SPEC-0003 |
| Épica | EP-01 Gestión de usuarios y acceso |
| Historias de usuario | HU-05 Administrar roles y permisos (talla L, 36,83 h) |
| Caso de uso | No hay caso de uso detallado |
| Actores | Administrador (según el componente «Portal Coordinación / Admin.» [A4]); participación del coordinador: **Pendiente de confirmación** |
| Prioridad | **No documentado** |
| Componente | Seguridad y acceso (EP-01) |
| ADR relacionados | [ADR-0005](../02-adrs/0005-autenticacion-jwt-y-autorizacion-por-roles.md) |
| Mockup | No definido: las fuentes no describen pantallas para esta funcionalidad |
| Estado | Borrador — información insuficiente |

> Esta funcionalidad figura en el alcance («Manejar usuarios y permisos según su rol» [A2]) y en la estimación (HU-05 [A3]), pero no tiene caso de uso, historia redactada ni criterios de aceptación en las fuentes. La Spec recoge solo lo documentado.

## 1. Resumen y objetivo

Administrar los usuarios del sistema y sus permisos según los cinco roles, de forma que cada usuario acceda solo a las opciones que le corresponden [A2][A3][A4].

## 2. Alcance

**Dentro**
- Administración de usuarios [A4, Portal Coordinación / Admin.].
- Gestión de roles y permisos [A3 HU-05; A4 componente EP-01].
- Asociación del usuario con un rol y con un estado activo o inactivo (precondición de CU.0001 [A2]).
- Asociación del acudiente con los estudiantes a su cargo (necesaria según CU.0003 [A2]): mecanismo **No documentado**.

**Fuera**
- Gestión de matrículas, nómina o información laboral de docentes [A2].
- Asignación de docentes a grupos y asignaturas ([Spec 0004](0004-gestionar-estructura-academica.md)).

## 3. Requisitos

### 3.1. Requisitos funcionales

| ID | Requisito | Fuente |
| --- | --- | --- |
| RF-0003-01 | El sistema debe permitir administrar usuarios. | [A4] Portal Coordinación / Admin. |
| RF-0003-02 | El sistema debe permitir administrar roles y permisos. | [A3] HU-05; [A4] componente EP-01 |
| RF-0003-03 | Cada usuario debe estar asociado a un rol y tener un estado (activo/inactivo). | [A2] CU.0001 precondición |
| RF-0003-04 | El sistema debe permitir asociar un acudiente con los estudiantes a su cargo. | [A2] CU.0003 restricciones y error 3 |

### 3.2. Reglas de negocio

| ID | Regla | Fuente |
| --- | --- | --- |
| RN-0003-01 | Roles: administrador, coordinador, docente, estudiante y acudiente. | [A2] |
| RN-0003-02 | El usuario se identifica con su documento de identidad (cédula o tarjeta de identidad). | [A2] CU.0001 |
| RN-0003-03 | Alcances documentados por rol: ver [Spec 0006 §3.2](0006-registrar-y-modificar-calificaciones.md#32-reglas-de-negocio) y [Spec 0007 §3.2](0007-consultar-calificaciones.md#32-reglas-de-negocio). | [A2] |

### 3.3. Requisitos no funcionales

| ID | Categoría | Requisito y métrica | Fuente |
| --- | --- | --- | --- |
| RNF-0003-01 | Seguridad | Control de acceso por roles. | [A2] CU.0001; [ADR-0005](../02-adrs/0005-autenticacion-jwt-y-autorizacion-por-roles.md) |

## 4. Datos y contratos

| Entidad | Atributos mencionados | Fuente |
| --- | --- | --- |
| Usuario | Documento de identidad, contraseña, correo registrado, rol, estado | [A2] |
| Rol | Nombre (cinco valores) | [A2] |
| Permiso | **No documentado** | — |
| Relación acudiente–estudiante | **No documentado** (solo se exige su existencia) | [A2] |

## 5. Flujos y estados

Estados del usuario documentados: **activo** e **inactivo** [A2]; **bloqueado temporalmente** por intentos fallidos [A2]. Las transiciones administrativas entre estados no están documentadas.

## 6. Casos borde y errores

| Caso | Comportamiento esperado | Fuente |
| --- | --- | --- |
| Usuario inactivo intenta ingresar | Acceso negado ([Spec 0001](0001-inicio-de-sesion.md)). | [A2] |
| Acudiente sin asociación válida | No se muestran calificaciones ([Spec 0007](0007-consultar-calificaciones.md)). | [A2] CU.0003 error 3 |
| Resto de casos (duplicados, desactivación, cambio de rol) | **No documentado**. | — |

## 7. Criterios de aceptación

```gherkin
Escenario: Usuario con rol y estado
  Dado un administrador autenticado
  Cuando registra un usuario
  Entonces el usuario queda asociado a uno de los roles administrador, coordinador, docente, estudiante o acudiente
  Y tiene un estado activo o inactivo

Escenario: Acudiente asociado
  Dado un acudiente asociado a un estudiante
  Cuando consulta calificaciones
  Entonces solo ve las calificaciones de ese estudiante
```

**Pendiente de definición:** el resto de criterios de aceptación, que requieren el caso de uso de HU-05.

## 8. Riesgos y pendientes

| ID | Tipo | Descripción |
| --- | --- | --- |
| P-0003-01 | Información insuficiente | Falta el caso de uso y los criterios de aceptación de HU-05. |
| P-0003-02 | No documentado | Matriz de permisos por rol y si los permisos son configurables o fijos. |
| P-0003-03 | Pendiente de confirmación | Si los usuarios se crean manualmente o se obtienen del sistema de matrículas ([ADR-0008](../02-adrs/0008-integracion-con-sistema-de-matriculas-existente.md)). |
| P-0003-04 | Pendiente de confirmación | Si el coordinador puede administrar usuarios o solo el administrador. |
