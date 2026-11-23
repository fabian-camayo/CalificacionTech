# Visión del producto — Sistema de Notas Académicas

## Declaración de visión

> Centralizar en un sistema web el registro, la consulta y el seguimiento de las calificaciones de la institución, para que la información sea consistente entre sus 3 sedes, sus jornadas y sus grupos, que las notas definitivas se calculen sin errores manuales, que cada cambio sea trazable y que estudiantes y acudientes puedan consultar los resultados con su usuario y contraseña.

La declaración resume, sin añadir objetivos, la descripción, el problema y las necesidades de [A2], reiterados en [A3] y [A4].

## Para quién

| Rol | Qué obtiene del sistema | Fuente |
| --- | --- | --- |
| Docente | Registrar, modificar y consultar las calificaciones de sus grupos y asignaturas asignados. | [A2] CU.0002, CU.0003 |
| Estudiante | Consultar sus propias calificaciones, promedios y notas definitivas. | [A2] CU.0003 |
| Acudiente | Consultar las calificaciones de los estudiantes a su cargo. | [A2] CU.0003 |
| Coordinador | Consultar por sede, jornada, grupo, asignatura y periodo; autorizar modificaciones en periodos cerrados. | [A2] CU.0002, CU.0003; [A4] BPMN 1 |
| Administrador | Consultar globalmente; administrar usuarios, sedes, jornadas, grupos y periodos. | [A2] CU.0003; [A4] componentes |

## Qué problema resuelve

El uso de hojas de cálculo independientes por docente provoca inconsistencias, errores de cálculo, falta de trazabilidad, dificultad de consulta y esfuerzo administrativo adicional [A2]. Ver el detalle en [strategy.md §2](strategy.md#2-mercado-y-problema).

## Objetivos del producto

| ID | Objetivo | Necesidad de origen [A2] |
| --- | --- | --- |
| OB-1 | Acceso según el rol del usuario (administrador, coordinador, docente, estudiante, acudiente). | Acceso según rol |
| OB-2 | Notas organizadas por estudiante, asignatura, grupo y periodo académico, para las 3 sedes y sus jornadas. | Gestión de notas de las 3 sedes; organización de notas |
| OB-3 | Cálculo automático de promedios y notas definitivas. | Cálculo automático |
| OB-4 | Consulta rápida y centralizada de las calificaciones registradas. | Consulta centralizada |
| OB-5 | Generación de boletines y reportes de calificaciones. | Boletines y reportes |
| OB-6 | Registro de los cambios realizados sobre las calificaciones. | Registro de cambios |
| OB-7 | Disponibilidad desde un navegador web y guardado de una calificación en un máximo de 2 segundos. | Navegador web; tiempo máximo de 2 s |

## Qué no es el producto

El sistema está enfocado **exclusivamente** en calificaciones [A2]. No:

- gestionará matrículas ni procesos de inscripción, ni reemplazará el sistema de matrículas existente;
- administrará información financiera;
- gestionará asistencia ni inasistencias;
- gestionará nómina ni información laboral de docentes;
- incluirá un sistema completo de comunicación con acudientes;
- gestionará todos los procesos administrativos de la institución.

## Principios que se derivan de las fuentes

1. **Una fuente de verdad.** Las calificaciones se almacenan de forma centralizada, no en archivos por docente [A2][A4].
2. **Cálculo por el sistema, no por la persona.** Promedios y definitivas se calculan al guardar [A2].
3. **Ningún cambio sin rastro.** Toda creación o modificación de nota queda en el historial [A2].
4. **Cada rol ve lo que le corresponde.** El alcance de consulta y edición depende del rol y de las asignaciones [A2].
5. **La consulta no altera los datos.** Consultar es una operación de solo lectura [A2][A4].

## Fuera de esta visión

Las fuentes no documentan una visión de largo plazo más allá de esta entrega (expansión a otras instituciones, nuevas funcionalidades, modelo comercial). No se añade ninguna.
