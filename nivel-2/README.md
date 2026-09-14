# Nivel 2 — Arreglar CSS roto

Acá la cosa cambia. En el Nivel 1 cada `TODO` te decía la propiedad y el valor; resolver era escribir lo que decía el comentario. En el Nivel 2 no hay TODOs ni valores: cada ejercicio es una página **rota a propósito** y tu trabajo es descubrir por qué y arreglarla.

> Prerequisito: haber hecho los 13 ejercicios del Nivel 1. Acá se combinan y se ponen a prueba los temas que ya viste.

## Cómo funciona

Cada carpeta de ejercicio contiene:

```
NN-nombre/
├── index.html      La estructura. NO se modifica.
├── styles.css      Acá está el problema. Es el único archivo que editás.
└── referencia.svg  Cómo debería verse la página terminada.
```

La consigna está al principio de `styles.css` y te dice **qué debería pasar** y **cuántos bugs hay** — pero no dónde están ni cómo se arreglan.

## Cómo abrir un ejercicio

1. Abrí la carpeta del repo en VS Code.
2. Clic derecho sobre el `index.html` del ejercicio y elegí **"Open with Live Server"**.
3. Abrí `referencia.svg` (o abrilo en el navegador) para tener el objetivo a la vista.
4. Editá `styles.css`, guardá con `Ctrl+S` y compará.

## Ejercicios

| # | Carpeta | Qué se practica | Bugs |
|---|---------|-----------------|------|
| 1 | `01-caja-y-unidades/` | `box-sizing`, `padding`, `width`/`max-width`, centrado, unidades (`px`, `vw`, `rem`) | 4 |
| 2 | `02-cascada-y-especificidad/` | cascada, especificidad, `:is()`, `:not()`, `!important` | 4 |
| 3 | `03-flexbox/` | contenedor e ítems flex, ejes, `flex-wrap` | 4 |
| 4 | `04-posicionamiento/` | `relative`, `absolute`, `fixed`, `z-index` | 4 |
| 5 | `05-responsive/` | media queries: `min`/`max`, ancho/alto | 4 |
| 6 | `06-variables-css/` | `var()`, alcance, unidades | 4 |
| 7 | `07-funciones-y-selectores/` | `calc()`, `clamp()`, `aspect-ratio`, `:has()` | 4 |
| 8 | `08-integrador/` | todo lo anterior mezclado | 8 |

Hacelos en orden: cada ejercicio suma temas y el último los mezcla todos.

## Estrategia sugerida

1. Leé la consigna completa antes de tocar nada.
2. Abrí la página y la referencia al lado. Anotá **todas** las diferencias que veas.
3. Inspeccioná con las DevTools (`F12`): el panel de estilos y el de la caja (Computed) muestran el tamaño real de cada elemento.
4. Arreglá **de a un bug por vez** y volvé a comparar. Si arreglás todo junto, no vas a saber qué causaba qué.
5. Si algo no cambia como esperabas, preguntate por qué antes de probar al azar.

## Reglas

- Solo editás `styles.css`. El HTML no se toca.
- No uses librerías de estilos — CSS puro.
- No hay una única solución, pero el resultado tiene que parecerse a `referencia.svg`.

Teoría de referencia: `../teoria.md`. Cualquier duda, consultá con el docente.
