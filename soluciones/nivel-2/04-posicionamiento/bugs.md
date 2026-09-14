# Bugs — Nivel 2, ejercicio 4 (posicionamiento)

Cuatro bugs de posicionamiento. Dos aparecen en pantalla apenas se abre la página; los otros se notan al scrollear o al arreglar los primeros.

## Bug 1 — `.pelicula` sin `position: relative`

- **Dónde:** regla `.pelicula`.
- **Por qué rompe:** el `.sello` es `position: absolute`, así que se ubica respecto de su ancestro posicionado más cercano. Si ningún ancestro tiene `position`, se va hasta el borde de la página.
- **Síntoma:** la etiqueta "ESTRENO" aparece en la esquina superior derecha de la ventana, no sobre el póster.
- **Arreglo:** `position: relative;` en `.pelicula` (establece el punto de referencia).

## Bug 2 — `.barra` sin `position: fixed`

- **Dónde:** regla `.barra`.
- **Por qué rompe:** la barra está escrita como si fuera fija, pero le falta `position: fixed` (y sus coordenadas `top`/`left` y el `width: 100%`).
- **Síntoma:** al scrollear, la barra se va para arriba con el contenido; no queda pegada.
- **Arreglo:** `position: fixed; top: 0; left: 0; width: 100%; z-index: 10;`.

## Bug 3 — `.cartelera` sin `padding-top`

- **Dónde:** regla `.cartelera`.
- **Por qué rompe:** al fijar la barra (bug 2), la barra sale del flujo y el contenido sube. Sin un `padding-top` que la compense, el título queda debajo de la barra.
- **Síntoma:** el título "Estrenos de la semana" queda tapado por la barra oscura. (Este síntoma se ve recién después de arreglar el bug 2.)
- **Arreglo:** `padding-top: 96px;` (o el alto de la barra + un poco de aire).

## Bug 4 — `.comprar` sin `position: fixed`

- **Dónde:** regla `.comprar`.
- **Por qué rompe:** le falta `position: fixed` y las coordenadas que lo anclan abajo a la derecha.
- **Síntoma:** "Comprar entradas" aparece como un link común al final de la página, no como botón flotante.
- **Arreglo:** `position: fixed; bottom: 24px; right: 24px; z-index: 10;`.

## Notas de corrección

- El bug 3 depende del bug 2: está bien que el alumno lo note recién después de fijar la barra.
- Preguntar: ¿por qué `position: fixed` saca al elemento del flujo? ¿Y por qué hace falta `width: 100%` si ya tiene `left: 0`?
