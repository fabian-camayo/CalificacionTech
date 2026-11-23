# Sistema de Notas Académicas — Artefactos de ingeniería de requisitos

Documentación de definición, requisitos y diseño del **Sistema de Notas Académicas**, un sistema web para el registro, la consulta y el seguimiento de calificaciones de una institución educativa con 3 sedes, 4 jornadas por sede y alrededor de 30 grupos por sede.

Proyecto académico de la asignatura **Ingeniería de Requisitos** (grupo 700303002-2, Instituto Tecnológico Metropolitano — ITM, 2026).

Autores: Leidy Melissa Trejos Pamplona, Alejandro José Acosta Fernandez y Fabian Andres Muñoz Camayo. Docente: Enrique José Gonzalez De La Rosa.

## Estructura

```text
docs/
├── 01-strategy/   Por qué existe el proyecto y cuál es su dirección
├── 02-adrs/       Por qué se tomaron las decisiones de arquitectura
├── 03-specs/      Qué hace cada funcionalidad y cómo se verifica
└── 04-mockups/    Cómo se ve y se navega cada funcionalidad (HTML)
```

| Carpeta | Contenido |
| --- | --- |
| [01-strategy](docs/01-strategy/) | [strategy.md](docs/01-strategy/strategy.md), [vision.md](docs/01-strategy/vision.md) |
| [02-adrs](docs/02-adrs/) | 10 ADR (0001–0010) + [template.md](docs/02-adrs/template.md) |
| [03-specs](docs/03-specs/) | 9 Specs (0001–0009) + [template.md](docs/03-specs/template.md) |
| [04-mockups](docs/04-mockups/) | 4 mockups HTML (0001, 0002, 0006, 0007) + [template.md](docs/04-mockups/template.md) |

Los mockups son archivos HTML autocontenidos: se abren directamente en el navegador, sin instalar dependencias.

## Fuentes

Toda la documentación se deriva exclusivamente de los entregables del proyecto:

| Código | Fuente |
| --- | --- |
| **[A2]** | *Actividad 2: Casos de Uso* (FDE 089, v05): descripción, problema, necesidades, alcance y casos de uso CU.0001–CU.0003. |
| **[A3]** | *Actividad 3: Estimación* (v01, 20-10-2026): árbol de épicas EP-01–EP-06, historias de usuario HU-01–HU-19, tallas, costos y recursos. |
| **[A4]** | *Actividad 4: UI – UML* (v01, 10-11-2026): mockups en Figma, BPMN 1 y 2, diagrama de componentes y diagrama de arquitectura y despliegue (AWS). |
| **[VIS]** | *Vistas*: pantallas «Registrar calificaciones» (docente) y «Mis calificaciones» (estudiante). |
| **[MET]** | *Requisitos de Software — Artefactos Strategy, ADR, Specs, Mockups* (referencia metodológica; no es fuente de requisitos). |

Cuando una fuente no aporta información suficiente, los documentos lo indican de forma explícita como **No documentado**, **Pendiente de confirmación**, **Decisión no identificada** o **Información insuficiente**. Ningún vacío se completa con suposiciones.

## Relación entre artefactos

```text
Strategy ──prioriza──▶ ADRs ──fundamentan──▶ Specs ──definen──▶ Mockups
```

## Matriz de trazabilidad

| Spec | Épica | HU [A3] | CU [A2] | Proceso [A4] | ADR | Mockup |
| --- | --- | --- | --- | --- | --- | --- |
| [0001 Inicio de sesión](docs/03-specs/0001-inicio-de-sesion.md) | EP-01 | HU-01 | CU.0001 | — | 0001, 0004, 0005 | [0001](docs/04-mockups/0001-inicio-de-sesion.html) |
| [0002 Recuperar contraseña](docs/03-specs/0002-recuperar-contrasena.md) | EP-01 | HU-04 | CU.0001 (alt.) | — | 0005, 0009 | [0002](docs/04-mockups/0002-recuperar-contrasena.html) |
| [0003 Usuarios, roles y permisos](docs/03-specs/0003-administrar-usuarios-roles-y-permisos.md) | EP-01 | HU-05 | — | — | 0005 | No definido |
| [0004 Estructura académica](docs/03-specs/0004-gestionar-estructura-academica.md) | EP-02 | HU-06, HU-07 | — | — | 0006, 0008 | No definido |
| [0005 Periodos académicos](docs/03-specs/0005-configurar-periodos-academicos.md) | EP-02 | HU-08 | — | — | 0006 | No definido |
| [0006 Registrar y modificar calificaciones](docs/03-specs/0006-registrar-y-modificar-calificaciones.md) | EP-03 | HU-02, HU-09, HU-11 | CU.0002 | BPMN 1 | 0003, 0006, 0010 | [0006](docs/04-mockups/0006-registrar-y-modificar-calificaciones.html) |
| [0007 Consultar calificaciones](docs/03-specs/0007-consultar-calificaciones.md) | EP-04 | HU-03, HU-12, HU-13 | CU.0003 | BPMN 2 | 0003, 0005, 0006 | [0007](docs/04-mockups/0007-consultar-calificaciones.html) |
| [0008 Boletines y reportes](docs/03-specs/0008-generar-boletines-y-reportes.md) | EP-05 | HU-14, HU-15, HU-16 | — | — | 0006, 0007 | No definido |
| [0009 Trazabilidad de cambios](docs/03-specs/0009-trazabilidad-de-cambios.md) | EP-06 | HU-17, HU-18, HU-19 | — | — | 0003, 0010 | No definido |

Las 18 historias de usuario estimadas en [A3] quedan cubiertas. [A3] no incluye una HU-10 (la numeración pasa de HU-09 a HU-11).

## Discrepancias entre fuentes

| Tema | Discrepancia | Dónde se registra |
| --- | --- | --- |
| Autorización en periodo cerrado | «Coordinador o administrador» [A2][A3] frente a solo «coordinador académico» [A4] | Spec 0006, P-0006-01 |
| Selectores del registro de notas | CU.0002 exige sede y jornada; la vista de Figma solo muestra periodo, asignatura y grupo | Spec 0006, P-0006-05 |
| Origen de los grupos | Se configuran en EP-02 y también se toman del sistema de matrículas | ADR-0008; Spec 0004 |
| Uso de AWS | Presupuestado «para desarrollo y pruebas» [A3]; presentado como despliegue [A4] | ADR-0002 |
| Backend | «Microservicios y módulos» sin elegir estilo [A4] | ADR-0006 |
| Estado de los ADR | Las decisiones están en el diseño [A4] sin aprobación formal registrada; todos los ADR están en estado *Propuesto* | 02-adrs |

## Verificación de calidad (rúbrica)

1. **Coherencia con las fuentes:** cada requisito, regla y decisión cita su fuente ([A2], [A3], [A4], [VIS]). No se añadieron funcionalidades, actores, integraciones ni tecnologías fuera de ellas.
2. **Completitud por artefacto:** Strategy (6 secciones de la plantilla + visión), ADR (título y número, estado, contexto, decisión, alternativas, consecuencias, enlaces), Specs (resumen, alcance, RF/RN/RNF, datos, flujos, casos borde, criterios de aceptación Gherkin, pendientes) y Mockups (objetivo, flujo, estados, componentes, responsive, interacción, pendientes). Donde una fuente no aporta un campo, se declara como no documentado.
3. **Ausencia de ambigüedad:** las métricas presentes en las fuentes se expresan de forma cuantitativa (guardado ≤ 2 s, escala 0.0–5.0, 403,10 h). Las que faltan quedan como pendientes con ID.
