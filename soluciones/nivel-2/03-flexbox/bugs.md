# Bugs — Nivel 2, ejercicio 3 (Flexbox)

Cuatro bugs, todos de Flexbox. En DevTools conviene mirar el panel Elements: al seleccionar un contenedor, al lado de `display` se ve una etiqueta `flex` si realmente es flex.

## Bug 1 — `.barra` sin `display: flex`

- **Dónde:** regla `.barra`.
- **Por qué rompe:** tiene `justify-content: space-between` y `align-items: center`, pero sin `display: flex` esas propiedades no hacen nada (el contenedor sigue siendo block).
- **Síntoma:** el logo y los links quedan uno arriba del otro, y el `space-between` no separa nada.
- **Arreglo:** `display: flex;`.

## Bug 2 — `.links` sin `display: flex`

- **Dónde:** regla `.links`.
- **Por qué rompe:** `gap` solo funciona en contenedores flex (o grid). Sin `display: flex`, los `<a>` siguen siendo inline y el `gap` se ignora.
- **Síntoma:** los links quedan pegados entre sí, sin separación.
- **Arreglo:** `display: flex;`.

## Bug 3 — `.clase` con contenido en fila

- **Dónde:** regla `.clase`.
- **Por qué rompe:** tiene `display: flex` pero le falta `flex-direction: column`; por defecto los flex items van en fila (`row`). `align-items: center` centra en el eje cruzado, que en fila es vertical.
- **Síntoma:** el ícono, el título y el horario aparecen uno al lado del otro, en vez de apilados y centrados.
- **Arreglo:** `flex-direction: column;`.

## Bug 4 — `.clases` sin `flex-wrap`

- **Dónde:** regla `.clases`.
- **Por qué rompe:** sin `flex-wrap: wrap`, los items se quedan en una sola fila y se comprimen para entrar (por el `flex: 1 1 200px`).
- **Síntoma:** al achicar la ventana, las 4 tarjetas se aplastan en vez de bajar a la fila siguiente.
- **Arreglo:** `flex-wrap: wrap;`.

## Notas de corrección

- Bug 1 y 2 son "falta `display: flex`", pero en contenedores distintos: verificar que estén **los dos**.
- El bug 3 es sutil porque `align-items: center` *parece* que debería centrar todo; el punto es que en fila centra verticalmente, no horizontalmente.
