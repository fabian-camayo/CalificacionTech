# Spec NNNN: [Nombre de la funcionalidad]

> Plantilla de especificación funcional y técnica. Copiar como `NNNN-nombre-funcionalidad.md` con el siguiente número consecutivo. Una Spec por funcionalidad.
>
> Reglas:
> - Sin criterios de aceptación, la Spec no está lista.
> - Cada requisito cita su fuente. Lo que no esté en las fuentes se marca como **No documentado**, **Pendiente de confirmación**, **Decisión no identificada** o **Información insuficiente**; no se completa con suposiciones.
> - Referencia los ADR que la fundamentan.
> - No sobre-especificar: lo visual va al mockup (`04-mockups/NNNN-nombre-funcionalidad.html`).

| Campo | Valor |
| --- | --- |
| ID | SPEC-NNNN |
| Épica | EP-XX |
| Historias de usuario | HU-XX |
| Caso de uso | CU.XXXX |
| Actores | … |
| Prioridad | Según la fuente (no inventar) |
| Componente | Componente del backend ([ADR-0006](../02-adrs/0006-backend-modular-alineado-a-epicas.md)) |
| ADR relacionados | … |
| Mockup | `../04-mockups/NNNN-….html` o «No aplica / no definido» |
| Estado | Borrador / En revisión / Acordada |

## 1. Resumen y objetivo

Qué hace la funcionalidad y qué problema atiende.

## 2. Alcance

**Dentro**
- …

**Fuera**
- …

## 3. Requisitos

### 3.1. Requisitos funcionales

| ID | Requisito | Fuente |
| --- | --- | --- |
| RF-NNNN-01 | El sistema debe … | … |

### 3.2. Reglas de negocio

| ID | Regla | Fuente |
| --- | --- | --- |
| RN-NNNN-01 | … | … |

### 3.3. Requisitos no funcionales

| ID | Categoría | Requisito y métrica | Fuente |
| --- | --- | --- | --- |
| RNF-NNNN-01 | Rendimiento / Seguridad / … | … | … |

## 4. Datos y contratos

Entidades y atributos que la fuente menciona; contratos de API si están documentados.

## 5. Flujos y estados

Secuencia normal, alternativa y de error. Diagrama Mermaid opcional.

## 6. Casos borde y errores

| Caso | Comportamiento esperado | Fuente |
| --- | --- | --- |

## 7. Criterios de aceptación

```gherkin
Escenario: …
  Dado …
  Cuando …
  Entonces …
```

## 8. Riesgos y pendientes

| ID | Tipo | Descripción |
| --- | --- | --- |
| P-NNNN-01 | No documentado / Pendiente de confirmación / … | … |
