# MP0373 – U1 AC4 – Respostes Tasca 2 i Tasca 3

Alumne: Víctor Martínez

## Tasca 2 – Propietats CSS utilitzades a `styles.css`

| # | Què determina | Propietat CSS | Exemple a `styles.css` |
|---|---|---|---|
| 1 | Color del text | `color` | Regla 03 `body`: `color: var(--text-light);` |
| 2 | Mida del text | `font-size` | Regla 07 `.navegacio a`: `font-size: 0.85rem;` i regla 16 amb `clamp(2.5rem, 5vw, 4rem)` |
| 3 | Gruix del text (pes) | `font-weight` | Regla 04 `h1, h2, h3`: `font-weight: 800;` |
| 4 | Font del text | `font-family` | Regla 03 `body`: `font-family: var(--font-sans);` |
| 5 | Color del fons | `background-color` | Regla 03 `body`: `background-color: var(--bg-main);` |
| 6 | Marge per cada costat | `margin` (i les individuals `margin-top`, `margin-right`, `margin-bottom`, `margin-left`, `margin-inline`) | Regla 02 `html`: `margin: 0;` · regla 05 `#inici`: `margin-inline: auto;` · regla 17: `margin-bottom: 4rem;` · regla 12: `margin-right: 8px;` |
| 7 | Vora del component | `border` (i `border-top`, `border-bottom`, `border-left`, `border-color`, `border-style`, `outline`) | Regla 06 `.capcalera`: `border-bottom: 2px solid var(--border-stiff);` · regla 32: `border-left: 4px solid ...;` · regla 33: `border-color` · regla 19: `outline: 4px solid ...;` |
| 8 | Tipus de cursor del ratolí | `cursor` | Regla 10 `a[target]`: `cursor: crosshair;` · regla 37: `cursor: not-allowed;` / `cursor: pointer;` |
| 9 | Ample de l'element | `width` (i `max-width`) | Regla 12: `width: 10px;` · regla 24: `width: 290px;` · regla 05: `max-width: 1400px;` |
| 10 | Alt de l'element | `height` | Regla 12: `height: 10px;` · regla 24: `height: 290px;` · regla 35: `height: 20px;` |
| 11 | Ombra de l'element | `box-shadow` | Regla 29: `box-shadow: 4px 4px 0px var(--accent-blue);` · regla 42: `box-shadow: var(--shadow-block);` · regla 12 (ombra lluminosa): `box-shadow: 0 0 10px var(--accent-green);` |
| 12 | Opacitat / transparència | `opacity` | Regla 37 `button:disabled`: `opacity: 0.2;` · regla 38: `opacity: 0.4;` |
| 13 | Efectes de moviment | `transition`, `transform` i `animation` (amb `@keyframes`) | Regla 07: `transition: var(--transition-fast);` · regla 48: `transform: translate(-3px, -3px);` · regla 53 `:target`: `animation: flashNeat 1s steps(2, start);` definida amb `@keyframes flashNeat` |

## Tasca 3 – Ús de les variables globals (custom properties)

Les variables globals es declaren una sola vegada dins de la regla `:root`, que selecciona l'element arrel del document (`<html>`). Com que estan definides a l'arrel, s'hereten i són accessibles des de qualsevol regla del full d'estils.

La sintaxi per declarar-les és `--nom-variable: valor;`. Per exemple:

```css
:root {
  --bg-main: #0d0e0d;
  --bg-accent: #ccff00;
  --text-light: #f5f5f0;
  --font-sans: "Space Grotesk", system-ui, -apple-system, sans-serif;
  --transition-fast: all 0.15s cubic-bezier(0.2, 0, 0, 1);
  --shadow-block: 6px 6px 0px #000000;
}
```

Per donar valor a una propietat amb una variable s'utilitza la funció `var()`, posant el nom de la variable dins:

```css
body {
  background-color: var(--bg-main);   /* equival a #0d0e0d */
  color: var(--text-light);           /* equival a #f5f5f0 */
  font-family: var(--font-sans);
}

.marca-punt {
  color: var(--bg-accent);            /* groc neó #ccff00 */
}

.navegacio a {
  transition: var(--transition-fast); /* una variable pot guardar un valor complex */
}

.projecte:is([data-estat="destacat"]) {
  box-shadow: var(--shadow-block);    /* també ombres completes */
}
```

Punts clau observats al full d'estils:

- Una variable pot contenir qualsevol tipus de valor: un color (`--bg-main`), una llista de fonts (`--font-serif`), una transició sencera (`--transition-fast`) o una ombra (`--shadow-block`).
- La mateixa variable es reutilitza en moltes regles (`--bg-accent` apareix a les regles 09, 11, 13, 14, 18, 19, 21, 22, 24, 26, 28, 30, 36, 41, 47, 48, 49, 50 i 53). Si es canvia el valor a `:root`, canvia a tot el web alhora.
- `var()` admet un valor de reserva opcional: `var(--bg-main, #000)` faria servir `#000` si la variable no existís.
- Les variables poden anar dins d'altres funcions, com a `box-shadow: 0 0 10px var(--accent-green);`.
