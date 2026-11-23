# Plantilla y convenciones de mockups HTML

Los mockups de este repositorio son **archivos HTML autocontenidos y navegables**. No son imágenes, PDF ni descripciones en Markdown.

## Convenciones

| Regla | Detalle |
| --- | --- |
| Nombre | `NNNN-nombre-funcionalidad.html`, con el **mismo número y nombre que su Spec** en `03-specs/`. |
| Cuándo existe | Solo para Specs cuya pantalla o flujo esté descrito en las fuentes. Una Spec sin pantallas documentadas no tiene mockup hasta que se documenten. |
| Autocontenido | CSS en `<style>` y JavaScript en `<script>` dentro del mismo archivo. Sin CDN, fuentes web, imágenes externas ni dependencias. Se abre con doble clic en cualquier navegador. |
| Alcance | Solo representa lo especificado en su Spec. No añade pantallas, campos, botones, menús ni operaciones. Lo que aparece en el diseño pero no está documentado se marca como **pendiente**. |
| Lógica | La interacción sirve para recorrer el flujo y ver los estados. No hay backend, integración real ni persistencia: los datos se reinician al recargar. |
| Datos | Ficticios y de ejemplo; se indica en la ficha del mockup. |
| Controles de demostración | Franja amarilla superior, rotulada «no forman parte del producto», para forzar estados (error, vacío, bloqueo…) que en el producto dependerían del servidor. |

## Estructura de cada archivo

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Mockup NNNN · Nombre — Sistema de Notas Académicas</title>
  <style>/* estilos base compartidos + estilos propios */</style>
</head>
<body>
  <div class="demo">…controles de demostración + enlace a la Spec…</div>
  <!-- Pantallas del flujo (secciones que se muestran u ocultan) -->
  <details class="spec">…ficha del mockup (7 secciones)…</details>
  <script>/* navegación y estados de demostración */</script>
</body>
</html>
```

## Ficha del mockup (obligatoria, dentro del HTML)

Cada mockup incluye un bloque `<details class="spec">` con:

1. **Objetivo y pantalla**: qué valida y qué pantallas contiene; CU/HU de origen.
2. **Flujo y navegación**: cómo se pasa de una pantalla a otra; enlaces a otros mockups.
3. **Estados**: vacío, carga, error y éxito, cuando correspondan a la Spec.
4. **Componentes reutilizados**: primitivas compartidas (ver abajo).
5. **Responsive**: comportamiento en móvil y escritorio.
6. **Notas de interacción**: reglas visibles (formato de números, cuándo se calcula algo, qué es simulado).
7. **Pendientes de aprobación**: diferencias con las fuentes y decisiones abiertas, con su ID de pendiente de la Spec.

## Sistema visual (tomado de las vistas de Figma del proyecto)

| Primitiva | Uso |
| --- | --- |
| Barra superior azul marino con título «Sistema de Notas Académicas» y usuario/rol a la derecha | Todas las pantallas autenticadas |
| Menú lateral azul marino: Inicio, Grupos, Calificaciones, Reportes | Navegación principal; los elementos sin pantalla documentada quedan inactivos |
| Saludo «Bienvenido, *Nombre Usuario*» y subtítulo | Cabecera de contenido |
| Tarjeta con título azul marino | Contenedor de la funcionalidad |
| Selectores con borde azul marino | Filtros y contexto académico |
| Tabla con cabecera celeste y separadores celestes | Listados de notas |
| Insignia verde | Nota definitiva |
| Botón secundario (blanco) y primario (azul marino) | Acciones Cancelar / Guardar |
| Mensajes: error (rojo), advertencia (ámbar), información (celeste), éxito (verde) | Estados |

## Responsive y accesibilidad

- Punto de corte en **860 px**: el menú lateral pasa a panel desplegable con el botón ⋮; los botones de acción ocupan todo el ancho.
- Tablas dentro de un contenedor con desplazamiento horizontal.
- Etiquetas `<label>` asociadas a cada campo, foco visible, mensajes con `role="alert"` o `role="status"`.

## Índice de mockups

| Mockup | Spec | Origen visual |
| --- | --- | --- |
| [0001-inicio-de-sesion.html](0001-inicio-de-sesion.html) | [Spec 0001](../03-specs/0001-inicio-de-sesion.md) | CU.0001 (sin vista de Figma; usa las primitivas de las vistas) |
| [0002-recuperar-contrasena.html](0002-recuperar-contrasena.html) | [Spec 0002](../03-specs/0002-recuperar-contrasena.md) | CU.0001 secuencia alternativa |
| [0006-registrar-y-modificar-calificaciones.html](0006-registrar-y-modificar-calificaciones.html) | [Spec 0006](../03-specs/0006-registrar-y-modificar-calificaciones.md) | Vista «Registrar calificaciones» (docente) |
| [0007-consultar-calificaciones.html](0007-consultar-calificaciones.html) | [Spec 0007](../03-specs/0007-consultar-calificaciones.md) | Vista «Mis calificaciones» (estudiante) |

Specs 0003, 0004, 0005, 0008 y 0009 no tienen mockup porque las fuentes no describen sus pantallas.
