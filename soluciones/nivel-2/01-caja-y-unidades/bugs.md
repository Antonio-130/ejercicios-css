# Bugs — Nivel 2, ejercicio 1 (caja y unidades)

Cuatro bugs, todos de modelo de caja o de unidades. Cada uno tiene un síntoma visible: si no se ve roto en el navegador, no cuenta como resuelto.

## Bug 1 — `box-sizing: content-box` en el reset

- **Dónde:** regla `*`.
- **Por qué rompe:** con `content-box`, el `width` no incluye `padding` ni `border`. La cabecera (padding horizontal 2.5rem + 2.5rem = 80px) y las tarjetas (padding 1.25rem + 1.25rem = 40px, más 2px de borde) terminan más anchas que la columna.
- **Síntoma:** el encabezado marrón queda más ancho que las tarjetas blancas y todo se sale hacia la derecha (aparece scroll horizontal en pantallas angostas).
- **Arreglo:** `box-sizing: border-box;`.

## Bug 2 — `.panaderia` sin centrar

- **Dónde:** regla `.panaderia`.
- **Por qué rompe:** tiene `max-width: 640px` pero no `margin: 0 auto`, así que la columna queda pegada a la izquierda.
- **Síntoma:** en pantallas anchas, todo el contenido se va a la izquierda en vez de quedar centrado como en la referencia.
- **Arreglo:** `margin: 0 auto;`.

## Bug 3 — `.logo` con `font-size: 4vw`

- **Dónde:** regla `.logo`.
- **Por qué rompe:** `vw` es relativo al ancho de la ventana, no al tamaño de fuente raíz. El título debería tener un tamaño estable (como el resto: en `rem`).
- **Síntoma:** "Panadería La Espiga" se ve enorme y cambia de tamaño al ensanchar o angostar la ventana (en pantallas chicas se achica, en grandes se agranda y hasta puede desbordar el encabezado).
- **Arreglo:** `font-size: 1.5rem;`.

## Bug 4 — `.etiqueta` con `width: 70px`

- **Dónde:** regla `.etiqueta`.
- **Por qué rompe:** un ancho fijo fuerza un tamaño menor al que necesita el texto "Recién horneado". La caja no crece con el contenido.
- **Síntoma:** el texto de la etiqueta se sale del recuadro naranja.
- **Arreglo:** quitar `width` (que el ancho lo defina el contenido).

## Notas de corrección

- Cualquier solución que deje el resultado igual a `referencia.svg` es válida (hay más de una forma).
- Si arregló `box-sizing` pero no el centrado (o al revés), quedan síntomas: revisar que la página quede centrada **y** con encabezado y tarjetas del mismo ancho.
- El bug del `vw` es conceptual, no un typo: vale la pena preguntar por qué `vw` no es lo mismo que `rem`.
