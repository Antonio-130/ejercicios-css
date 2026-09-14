# Bugs — Nivel 2, ejercicio 2 (cascada, especificidad y selectores modernos)

Cuatro bugs. Todos se diagnostican con el panel **Styles** de las DevTools: ahí se ve qué regla gana y cuál queda tachada.

## Bug 1 — Selector inválido en una lista agrupada

- **Dónde:** regla `.etiqueta, 2026-ofertas { ... }`.
- **Por qué rompe:** un selector de tipo no puede empezar con un número, así que `2026-ofertas` es inválido. En una lista normal, **un selector inválido invalida toda la regla**: `.etiqueta` también pierde sus estilos.
- **Síntoma:** la etiqueta "OFERTA" se ve como texto común, sin fondo rojo ni padding.
- **Arreglo:** borrar `2026-ofertas` (o agrupar con `:is(.etiqueta, 2026-ofertas)`, que es tolerante y no se cae). DevTools marca el selector con "invalid selector".

## Bug 2 — `:not()` apuntando a un selector demasiado amplio

- **Dónde:** regla `.lista :not(.oferta) { color: #2a9d8f; }`.
- **Por qué rompe:** `:not(.oferta)` coincide con **todos** los elementos de `.lista` que no tienen esa clase (los `.item`, los `.nombre`, los `.precio`...). La intención era colorear solo los precios que no están en oferta.
- **Síntoma:** los nombres de los productos quedan en verde en vez de gris oscuro.
- **Arreglo:** acotar el selector al precio: `.item:not(.oferta) .precio { color: #2a9d8f; }`.

## Bug 3 — Orden de reglas con la misma especificidad

- **Dónde:** `.destacado` está definido **antes** que `.item`.
- **Por qué rompe:** `.destacado` (0,1,0) y `.item` (0,1,0) tienen la misma especificidad, así que gana la que aparece **después**. El `border` de `.item` (que reescribe los cuatro bordes) pisa el `border-left` de `.destacado`.
- **Síntoma:** el producto destacado no tiene la franja marrón a la izquierda.
- **Arreglo:** poner `.destacado` después de `.item` (o subir su especificidad, por ejemplo `.item.destacado`).

## Bug 4 — `!important` que frena la cascada

- **Dónde:** regla `.precio { color: #2a9d8f !important; }`.
- **Por qué rompe:** `!important` gana casi cualquier pelea, así que `.oferta .precio` no puede cambiarle el color aunque sea más específico.
- **Síntoma:** el precio en oferta queda verde, sin tachado rojo.
- **Arreglo:** quitar el `!important`. Con el color base verde solo para los precios sin oferta, no hace falta.

## Notas de corrección

- El bug 4 se puede arreglar de varias formas; lo importante es que **no** quede `!important` bloqueando `.oferta .precio`.
- Vale la pena preguntar: ¿por qué `.lista :not(.oferta)` colorea los nombres? (herencia + selector amplio).
