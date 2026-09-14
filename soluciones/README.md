# Soluciones — Ejercicios de CSS

Clave de corrección de los ejercicios de `ejercicios-css`, mantenida en la rama **`soluciones`** del repo.

> Solo para el docente. Los alumnos trabajan sobre `main`, donde estas soluciones no existen. Ojo: al ser un repo público, la rama es visible en GitHub.

## Estructura

Espeja la del repo, con la versión correcta de cada `styles.css` roto y una explicación de los bugs:

```
soluciones/nivel-2/01-caja-y-unidades/
├── styles.css   Versión correcta del archivo roto
└── bugs.md      Qué rompió cada bug, qué síntoma da y cómo se arregla
```

## Cómo trabajar con la rama

```sh
git checkout soluciones   # ver las soluciones
git checkout main         # volver al repo de los alumnos
```

## Mantenimiento

- Al agregar un ejercicio a `main`, agregar acá su solución.
- Si se cambia el HTML o los bugs de un ejercicio, actualizar el `styles.css` y el `bugs.md` de esta rama a la vez.
- Los cambios se commitean y pushean en la rama `soluciones`.
