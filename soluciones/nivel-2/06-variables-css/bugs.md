# Bugs — Nivel 2, ejercicio 6 (variables CSS)

Cuatro bugs, todos alrededor de cómo se definen y usan las variables. La pista general: si `var(--algo)` no resuelve, la propiedad **entera** se ignora (no toma un valor "parecido").

## Bug 1 — Variable usada pero nunca definida

- **Dónde:** `--color-acento` se usa en `.precio` y en `.destacada`, pero no está declarada en ningún lado.
- **Por qué rompe:** `var(--color-acento)` no encuentra valor, así que `color` y `border` se descartan.
- **Síntoma:** los precios no salen naranjas y la tarjeta destacada no tiene el borde naranja.
- **Arreglo:** definirla, por ejemplo `--color-acento: #e08e08;` en `:root`.

## Bug 2 — Variable definida fuera de alcance

- **Dónde:** `--radio` está declarada dentro de `.catalogo`, pero se usa también en `.pie`.
- **Por qué rompe:** una variable existe solo en el elemento donde se declara y en sus descendientes. El `.pie` está **fuera** de `.catalogo`, así que para él la variable no existe.
- **Síntoma:** el pie queda con las esquinas rectas en vez de redondeadas (a las tarjetas sí les funciona, porque están dentro de `.catalogo`).
- **Arreglo:** mover `--radio` a `:root` para que esté disponible en todo el documento.

## Bug 3 — Nombre de variable mal escrito

- **Dónde:** `.detalle` usa `var(--texto-suave)`, pero la variable declarada se llama `--color-texto-suave`.
- **Por qué rompe:** son nombres distintos; `--texto-suave` no existe.
- **Síntoma:** el texto "Interior / Exterior..." queda del color normal, no en el gris verdoso suave.
- **Arreglo:** usar el nombre correcto: `var(--color-texto-suave)`.

## Bug 4 — Valor sin unidad

- **Dónde:** `--espacio: 16;` (un número, sin `px`).
- **Por qué rompe:** `padding: var(--espacio)` termina siendo `padding: 16`, que no es una medida válida, así que se ignora. Lo mismo con `gap`.
- **Síntoma:** el hero, las tarjetas y el pie quedan sin espacio interno, y las tarjetas pegadas entre sí.
- **Arreglo:** `--espacio: 16px;`. (La unidad va en la variable, no en el `var()`.)

## Notas de corrección

- El bug 4 suele aparecer como `var(--espacio)px`, que también es inválido. La unidad debe estar dentro del valor de la variable.
- Vale la pena preguntar por el bug 2: ¿por qué a las tarjetas les funciona `--radio` y al pie no?
