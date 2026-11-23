# Strategy — Sistema de Notas Académicas

| Campo | Valor |
| --- | --- |
| Producto | Sistema de Notas Académicas |
| Tipo | Sistema web institucional de registro, consulta y seguimiento de calificaciones |
| Fuentes | [A2] Actividad 2 · [A3] Actividad 3 · [A4] Actividad 4 · [VIS] Vistas |
| Documento relacionado | [vision.md](vision.md) |
| Revisión | Al cambiar el alcance, la estimación o el contexto institucional |

> **Nota de alcance.** La plantilla metodológica de Strategy [MET] está orientada a la defensibilidad comercial de un producto (moat, cuota, LTV/CAC, NPS). Las fuentes del proyecto describen un **sistema para una única institución educativa** y no contienen información de mercado, competidores, clientes adicionales ni métricas comerciales. Las secciones correspondientes se mantienen y se señala de forma explícita qué no está documentado, en lugar de completarlas con hipótesis.

---

## 1. Resumen ejecutivo

El Sistema de Notas Académicas sustituye las hojas de cálculo independientes que hoy usa cada docente por una plataforma web centralizada, en la que se registran, calculan y consultan las calificaciones de una institución con **3 sedes, 4 jornadas por sede y alrededor de 30 grupos por sede** [A2].

La dirección del proyecto se resume en tres compromisos que recorren todas las fuentes:

1. **Centralizar** las calificaciones por sede, jornada, grupo, asignatura y periodo académico [A2].
2. **Calcular automáticamente** promedios y notas definitivas, eliminando el cálculo manual [A2].
3. **Dejar trazabilidad** de cada cambio: quién lo hizo, cuándo y qué valor modificó [A2][A3].

El sistema se limita deliberadamente al proceso de calificaciones: no gestiona matrículas, asistencia, finanzas ni nómina [A2].

Datos de planeación documentados [A3]:

| Indicador | Valor |
| --- | --- |
| Épicas | 6 (EP-01 a EP-06) |
| Historias de usuario estimadas | 18 |
| Esfuerzo estimado | 403,10 horas |
| Duración estimada | 10,08 semanas (2,52 meses) |
| Equipo | 4 personas (2 desarrolladores full stack, 1 Product Owner, 1 QA/Tester) |
| Valor total para el cliente | $ 87.170.934 |

## 2. Mercado y problema

### 2.1. Cliente y segmento

| Aspecto | Información documentada |
| --- | --- |
| Cliente | Una institución educativa con 3 sedes, 4 jornadas por sede y ~30 grupos por sede (~90 grupos en total) [A2][A4]. |
| Usuarios | Administrador, coordinador, docente, estudiante y acudiente [A2]. |
| Mercado más amplio | **No documentado.** Las fuentes no plantean comercializar el sistema a otras instituciones. |
| Competidores o soluciones alternativas del mercado | **No documentado.** |

### 2.2. Problema

El registro y el seguimiento de calificaciones se hacen mediante hojas de cálculo independientes de cada docente, lo que impide mantener información centralizada, consistente y actualizada entre sedes, jornadas y grupos [A2]. Las consecuencias documentadas son:

| ID | Problema | Necesidad que lo atiende [A2] |
| --- | --- | --- |
| P1 | Inconsistencias en las calificaciones por el uso de diferentes archivos y copias. | Gestionar las notas de las 3 sedes, jornadas y grupos; consulta centralizada. |
| P2 | Errores en el cálculo de promedios y notas definitivas, hecho manualmente. | Cálculo automático de promedios y notas definitivas. |
| P3 | Falta de trazabilidad: no se identifica quién cambió qué y cuándo. | Registro de los cambios realizados sobre las calificaciones. |
| P4 | Dificultad de consulta, sobre todo para estudiantes y acudientes. | Consulta de notas con usuario y contraseña, desde un navegador web. |
| P5 | Mayor esfuerzo administrativo por mantener múltiples archivos manualmente. | Generación de boletines y reportes de calificaciones. |

### 2.3. Propuesta de valor

Una única fuente de verdad de las calificaciones, accesible por navegador y con permisos por rol, donde la nota definitiva se calcula automáticamente y cada modificación queda registrada [A2][A4].

## 3. Defensibilidad: tipos y evidencia

Las fuentes no formulan una tesis de defensibilidad. La tabla siguiente revisa los tipos de defensibilidad del índice metodológico [MET] y deja constancia de la evidencia disponible.

| Tipo | Evidencia en las fuentes | Estado |
| --- | --- | --- |
| Efectos de red | Ninguna. | No documentado |
| Costos de cambio | Las fuentes describen la centralización de calificaciones e historial en una base de datos [A4], pero no analizan el costo de cambiar de sistema. | Información insuficiente |
| Escala | Ninguna, más allá del tamaño de la institución (3 sedes, ~90 grupos). | No documentado |
| Marca | Ninguna. | No documentado |
| Datos | El sistema acumula calificaciones e historial de cambios de la institución [A2][A4]. No existe evidencia de que esto se plantee como ventaja competitiva. | Información insuficiente |
| Plataforma | Ninguna. | No documentado |
| Regulación | Ninguna. | No documentado |

**Conclusión:** no existe evidencia que permita atribuir al proyecto un *moat*. Según la propia metodología, «una ventaja sin evidencia es solo una hipótesis» [MET]; por eso este documento no declara ninguna.

## 4. Amenazas y erosión

Las fuentes no contienen un análisis de amenazas competitivas. Sí documentan dependencias y restricciones que pueden afectar el valor del sistema:

| ID | Factor documentado | Fuente | Efecto sobre el valor |
| --- | --- | --- | --- |
| A1 | Dependencia del **sistema de matrículas existente** como fuente de estudiantes y grupos matriculados; el sistema de notas no lo reemplaza, solo lo consulta. | [A2][A4] | Si la fuente no está disponible o es inconsistente, el listado de estudiantes por grupo se ve afectado. Las condiciones de la integración están **pendientes de confirmación** (ver [ADR-0008](../02-adrs/0008-integracion-con-sistema-de-matriculas-existente.md)). |
| A2 | Dependencia de servicios de terceros: AWS (EC2, RDS, S3) y un servicio de correo transaccional SaaS. | [A3][A4] | Su indisponibilidad afecta la operación o la recuperación de contraseñas. |
| A3 | Exclusiones de alcance (matrículas, asistencia, finanzas, nómina, comunicación completa con acudientes, procesos administrativos generales). | [A2] | Las necesidades fuera de alcance seguirán resolviéndose fuera del sistema. |
| A4 | Persistencia del uso de hojas de cálculo. | — | **No documentado.** Las fuentes no analizan el riesgo de adopción. |

## 5. Plan para profundizar

Las fuentes no definen un plan para profundizar una ventaja. Lo que sí documentan es el **plan de entrega** por épicas [A3]:

| Épica | Nombre | HU | Horas | % del esfuerzo |
| --- | --- | --- | --- | --- |
| EP-01 | Gestión de usuarios y acceso | 3 | 75,91 | 18,83 % |
| EP-02 | Gestión académica | 3 | 52,16 | 12,94 % |
| EP-03 | Gestión de calificaciones | 3 | 75,91 | 18,83 % |
| EP-04 | Consulta de calificaciones | 3 | 52,16 | 12,94 % |
| EP-05 | Reportes académicos | 3 | 75,91 | 18,83 % |
| EP-06 | Trazabilidad de cambios | 3 | 71,05 | 17,63 % |
| **Total** | | **18** | **403,10** | **100 %** |

- Las historias de mayor prioridad documentadas son HU-01 (Inicio de sesión), HU-02 (Registrar y modificar calificaciones) y HU-03 (Consultar calificaciones), todas con prioridad **Alta** [A3]; sus casos de uso tienen importancia **MUY IMPORTANTE** [A2].
- El orden de los sprints y las fechas de los hitos: **No documentado.** [A3] indica que el trabajo quedó registrado en Jira «listo para su seguimiento en los siguientes sprints».
- Fases posteriores a esta entrega: **No documentado.**

## 6. Métricas

### 6.1. Métricas de defensibilidad

Retención, LTV/CAC, cuota de mercado y NPS [MET]: **No documentado.** No aplican de forma verificable a un sistema de una sola institución sin modelo comercial descrito.

### 6.2. Métricas verificables documentadas

| ID | Métrica | Objetivo | Fuente |
| --- | --- | --- | --- |
| M1 | Tiempo de guardado de una calificación | ≤ 2 segundos | [A2] Necesidades, CU.0002; [A3] HU-02 CA-4 |
| M2 | Calificaciones con trazabilidad de cambio (usuario, fecha, valor anterior y nuevo) | 100 % de creaciones y modificaciones | [A2] CU.0002; [A3] HU-02 CA-6 |
| M3 | Notas registradas fuera de la escala 0.0–5.0 | 0 | [A2] CU.0002 |
| M4 | Esfuerzo de construcción | 403,10 h | [A3] |
| M5 | Duración | 2,52 meses | [A3] |
| M6 | Valor para el cliente | $ 87.170.934 | [A3] |

### 6.3. Métricas de resultado

La reducción de errores de cálculo, de inconsistencias o del esfuerzo administrativo **no tiene línea base ni meta cuantificada** en las fuentes. Queda **pendiente de definición** con la institución.

## 7. Pendientes

| ID | Pendiente |
| --- | --- |
| PS-1 | Definir con la institución métricas de resultado con línea base (errores de cálculo, tiempos de consulta, esfuerzo administrativo). |
| PS-2 | Confirmar si existe una intención de uso más allá de la institución; sin ella, las secciones de mercado y defensibilidad se mantienen como no aplicables. |
| PS-3 | Documentar el orden de entrega por sprint y los hitos. |

## Trazabilidad

- ADRs que materializan esta estrategia: [02-adrs](../02-adrs/).
- Funcionalidades derivadas: [03-specs](../03-specs/).
