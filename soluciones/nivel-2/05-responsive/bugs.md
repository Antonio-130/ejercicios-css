# Bugs — Nivel 2, ejercicio 5 (diseño responsivo)

Cuatro bugs. Conviene probarlos con la vista de dispositivo de DevTools (Ctrl+Shift+M) o arrastrando el borde de la ventana.

## Bug 1 — Media query con `min-width` en vez de `max-width`

- **Dónde:** `@media (min-width: 900px)`.
- **Por qué rompe:** `min-width: 900px` se cumple en pantallas **grandes**, al revés de lo que se busca ("hasta 900px").
- **Síntoma:** en escritorio las tarjetas se muestran de a 2 (layout de tablet) y en el celular no se aplica ningún ajuste.
- **Arreglo:** `@media (max-width: 900px)`.

## Bug 2 — Media query con `max-height` en vez de `max-width`

- **Dónde:** `@media (max-height: 600px)`.
- **Por qué rompe:** usa el **alto** de la ventana como condición, no el ancho. En un celular común (alto > 600px) nunca se activa.
- **Síntoma:** el ajuste de celular (barra en columna, tarjetas de a una) no aparece en un teléfono; en cambio aparece si achicás el alto de la ventana.
- **Arreglo:** `@media (max-width: 600px)`.

## Bug 3 — `.contenedor` con ancho fijo

- **Dónde:** `.contenedor { width: 900px; }`.
- **Por qué rompe:** un `width` fijo no baja de 900px, así que en pantallas más angostas el contenido desborda.
- **Síntoma:** aparece scroll horizontal y el contenido se corta en celulares y tablets.
- **Arreglo:** `max-width: 900px;` (permite encogerse; con `margin: 0 auto` sigue centrado en pantallas grandes).

## Bug 4 — `.gusto` con tamaño rígido

- **Dónde:** `.gusto { flex: 0 0 220px; }`.
- **Por qué rompe:** `flex: 0 0 220px` impide crecer (`grow: 0`) y encogerse (`shrink: 0`): la tarjeta mide siempre 220px.
- **Síntoma:** las tarjetas no se reparten el ancho ni se adaptan; en pantallas chicas sobresalen y no se acomodan en una columna real.
- **Arreglo:** `flex: 1 1 200px;` (puede crecer y encogerse).

## Notas de corrección

- Los bugs 1 y 2 son los más formativos: preguntar siempre "¿esto mira el ancho o el alto, y aplica a pantallas grandes o chicas?".
- Si el alumno cambia `min-width` por `max-width` pero deja el tamaño rígido, en celular las tarjetas no quedan de a una: los dos arreglos hacen falta.
