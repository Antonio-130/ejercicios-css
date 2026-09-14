# Bugs — Nivel 2, ejercicio 7 (funciones y selectores modernos)

Cuatro bugs. En DevTools, una propiedad escrita mal suele aparecer tachada o con advertencia; es el mejor punto de partida.

## Bug 1 — `clamp()` con los argumentos desordenados

- **Dónde:** `.titulo { font-size: clamp(3rem, 4vw, 1.75rem); }`.
- **Por qué rompe:** `clamp(minimo, ideal, maximo)` espera primero el mínimo y al final el máximo. Acá el "mínimo" (3rem) es mayor que el "máximo" (1.75rem), así que la regla devuelve el mínimo casi siempre.
- **Síntoma:** el título queda enorme y no se achica al reducir la ventana.
- **Arreglo:** ordenar de menor a mayor: `clamp(1.75rem, 4vw, 3rem)`.

## Bug 2 — `calc()` sin espacios alrededor del operador

- **Dónde:** `.video { width: calc(33.333%-14px); }`.
- **Por qué rompe:** en `calc()`, `+` y `-` **necesitan** espacios. Sin ellos, `33.333%-14px` se interpreta como una unidad rara y toda la declaración es inválida.
- **Síntoma:** el `width` se ignora; los videos no toman el ancho de un tercio y se desacomoda la fila.
- **Arreglo:** `calc(33.333% - 14px)`.

## Bug 3 — `aspect-ratio` con dos puntos

- **Dónde:** `.pantalla { aspect-ratio: 16:9; }`.
- **Por qué rompe:** la relación de aspecto se escribe con barra (`16 / 9`), no con dos puntos. `16:9` es sintaxis inválida.
- **Síntoma:** la propiedad se ignora y, como `.pantalla` no tiene altura, el recuadro queda sin alto (no se ve el video).
- **Arreglo:** `aspect-ratio: 16 / 9;`.

## Bug 4 — `:has()` con el argumento equivocado

- **Dónde:** `.plan:has(.precio) { border: 2px solid #c0392b; }`.
- **Por qué rompe:** `:has(.precio)` selecciona todo `.plan` que contenga un `.precio`, ¡y **todos** los planes tienen precio! No distingue el plan de la promo.
- **Síntoma:** los 3 planes quedan con borde rojo, cuando solo debería llevarlo el del medio (el que tiene la etiqueta PROMO).
- **Arreglo:** apuntar a lo que distingue al plan: `.plan:has(.etiqueta)`.

## Notas de corrección

- El bug 2 es el clásico de `calc`: vale la pena que lo recuerden ("los operadores necesitan aire").
- Para el bug 4, `document.querySelectorAll(".plan:has(.precio)").length` devuelve 3; con `.etiqueta` devuelve 1. Buen experimento para mostrar en consola.
