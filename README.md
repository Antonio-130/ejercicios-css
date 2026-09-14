# Práctica de CSS — Ejercicios por tema

Bienvenido a la ejercitación de CSS. Acá no vas a encontrar ejercicios de manual: cada carpeta es un encargo real. El HTML ya está hecho; tu trabajo es escribir CSS.

## Cómo funciona

Cada carpeta de ejercicio contiene exactamente dos archivos:

```
nombre-del-ejercicio/
├── index.html    La estructura. NO la modificás (salvo el ejercicio 01).
└── styles.css    Acá escribís todo tu CSS.
```

La consigna está al principio de `styles.css`, como comentario. Las tareas están marcadas con `TODO`.

## Cómo abrir un ejercicio

1. Abrí la carpeta del repo en VS Code.
2. Clic derecho sobre el `index.html` del ejercicio  **"Open with Live Server"**.
3. Editá `styles.css`, guardá con `Ctrl+S` y mirá el navegador (Live Server recarga solo).

Si no tenés Live Server, también podés hacer doble clic en el `index.html` y abrirlo directo en el navegador.

## Nivel 1 — 13 ejercicios por tema

| # | Carpeta | Tema | Teoría |
|---|---------|------|--------|
| 1 | `01-formas-de-aplicar-css/` | CSS en línea, interno y externo | §2 |
| 2 | `02-selectores-especificidad/` | Selectores y especificidad | §3 |
| 3 | `03-texto-y-colores/` | `color`, `background-color`, fuentes, alineación | §4.1–4.3 |
| 4 | `04-modelo-de-caja/` | `padding`, `margin`, `border`, `border-radius`, `box-shadow` | §4.4–4.6 y §6 |
| 5 | `05-tamanos-y-unidades/` | `width`/`height`, px, %, em, rem, vw, vh | §4.6 |
| 6 | `06-background/` | `background-image`, `size`, `position`, `repeat` | §4.7 |
| 7 | `07-filtros-y-transformaciones/` | `filter` y `transform` | §5 |
| 8 | `08-posicionamiento/` | `relative`, `absolute`, `fixed`, `sticky` | §7 |
| 9 | `09-pseudoclases-pseudoelementos/` | `:hover`, `:focus`, `:nth-child`, `::before`, `::after` | §8 |
| 10 | `10-flexbox/` | Flexbox: contenedor e ítems | §9 |
| 11 | `11-grid/` | Grid: columnas, filas, span | §10 |
| 12 | `12-media-queries/` | Diseño responsivo | §11 |
| 13 | `13-animaciones-transiciones/` | `transition` y `@keyframes` | §12 |

Hacelos en orden: cada uno se apoya en el anterior.

## Nivel 2 — Arreglar CSS roto

En [`nivel-2/`](./nivel-2/) no hay TODOs ni valores para copiar: cada ejercicio es una página **rota a propósito** que hay que diagnosticar y arreglar, comparando contra una referencia visual. Requiere haber hecho los 13 ejercicios de arriba. Empezá por [`nivel-2/README.md`](./nivel-2/README.md).

## Reglas

-  Leé la consigna completa antes de escribir una línea
-  Mirá la página en el navegador antes y después de cada cambio
-  Solo editás `styles.css` (el ejercicio 01 es la única excepción: ahí también completás el HTML)
-  No modifiques la estructura del HTML ni los nombres de clase
-  No uses librerías de estilos (Tailwind, Bootstrap, etc.) — solo CSS puro

Teoría de referencia: `teoria.md`. Cualquier duda, consultá con el docente.
