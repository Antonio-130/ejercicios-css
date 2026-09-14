# Bugs — Nivel 2, ejercicio 8 (integrador)

Ocho bugs, uno o dos por cada tema del nivel. Recomendación para corregir: ir de a uno y agruparlos por tema.

| # | Tema | Bug | Síntoma | Arreglo |
|---|------|-----|---------|---------|
| 1 | Caja | `box-sizing: content-box` | Encabezado y tarjetas más anchos que el contenedor; scroll horizontal | `border-box` |
| 2 | Variables | `--color-marca` declarada en `.contenedor` y usada en `.barra` y `.pie` | La barra y el pie quedan sin fondo azul | Mover `--color-marca` a `:root` |
| 3 | Flex | `.barra` sin `display: flex` | El logo y las secciones quedan apilados | `display: flex` |
| 4 | Position | `.destacada` sin `position: relative` | La cinta "ÚLTIMO MOMENTO" se va a la esquina de la ventana | `position: relative` |
| 5 | Funciones | `clamp(2rem, 3vw, 1.4rem)` invertido | El título de la destacada queda enorme y no se adapta | `clamp(1.4rem, 3vw, 2rem)` |
| 6 | Flex | `.notas` sin `flex-wrap` | Las notas se aplastan en vez de bajar de fila | `flex-wrap: wrap` |
| 7 | Funciones | `calc(33.333%-16px)` sin espacios | El `flex` de `.nota` se invalida; las notas no toman su tamaño | `calc(33.333% - 16px)` |
| 8 | Responsive | `@media (min-width: 700px)` | Los estilos de celular se aplican en escritorio (y no en celular) | `max-width: 700px` |

## Detalle de los menos obvios

### Bug 1 — `box-sizing`
Con `content-box`, el `padding` y el `border` se suman al ancho. El `.barra`, la `.destacada` y las `.nota` (que ocupan el 100% o casi) terminan sobresaliendo del contenedor.

### Bug 2 — alcance de la variable
`--color-marca` está declarada dentro de `.contenedor`, así que solo existe ahí y en sus hijos. La `.barra` y el `.pie` están fuera: no la ven. Se arregla moviéndola a `:root`.

### Bug 5 — `clamp`
Los argumentos van en orden `minimo, ideal, maximo`. Con el mínimo mayor que el máximo, la función devuelve el mínimo y el título no se achica.

### Bug 7 — `calc`
`calc(33.333%-16px)` es inválido: los operadores `+` y `-` necesitan espacios. Al ser inválido el `flex` completo, `.nota` pierde su tamaño flexible.
