# DEPA PIG and Friends — Landing Page

Un sitio web estático para el club secreto de videojuegos y juegos de mesa.

## Archivos

- `index.html` — Sitio completo (HTML + CSS + JS embebido, zero dependencies)
- `SPEC.md` — Spec de diseño, sistema de diseño, decisiones creativas

## Editar el próximo evento

Buscar en `index.html` el bloque `<!-- EVENT CARD -->` y cambiar los valores ahí. El archivo es self-contained — no hay archivos externos de datos.

Valores a cambiar:
- Línea ~270: `<div class="event-label">NEXT QUEST</div>`
- Línea ~271: `<h2 class="event-title">Noche de videojuegos...`
- Línea ~274: `<p class="event-desc">La próxima reunión...`
- Línea ~283: `<div class="meta-value">Sábado 18 de mayo · 8:00 PM</div>`
- Línea ~290: `<div class="meta-value">Videojuegos · D&D · Juegos de mesa</div>`
- Línea ~298: ubicación secreta

## Stack

- HTML5 + CSS3 + Vanilla JS
- Google Fonts: Press Start 2P, Cinzel, Nunito
- Zero frameworks, zero build, zero dependencies
- Responsive: mobile-first, breakpoints en 768px y 1024px

## Deploy

### Opción 1: GitHub Pages
```bash
cd ~/github/depa-pig
git init && git remote add origin https://github.com/monoet/depa-pig.git
git add . && git commit -m "init" && git push -u origin main
# Activa GitHub Pages en Settings > Pages > Source: main
```

### Opción 2: Vercel
```bash
npm i -g vercel && vc deploy
```

### Opción 3: Netlify
```bash
npm i -g netlify-cli && netlify deploy --dir . --prod
```

## Escalar a React

Si el proyecto crece a múltiples eventos y páginas dinámicas, migrar a:
- Vite + React 18 + TypeScript
- `src/data/event.ts` como single source of truth
- Mantener el mismo sistema de diseño (CSS custom properties)

## Contacto / WhatsApp

El botón de WhatsApp usa un número placeholder (`5215512345678`). Reemplazarlo con el número real en la función `handleSubmit()` dentro del `<script>` al final del body.

## Paleta de colores

| Token | Hex | Uso |
|---|---|---|
| `--void` | #0D0A0C | Fondo más oscuro |
| `--charcoal` | #1A1215 | Fondo secciones |
| `--gold` | #C9963A | Acento principal |
| `--parchment` | #F5E6C8 | Texto sobre oscuro |
| `--cream` | #FBF5E6 | Texto brillante |
| `--red-accent` | #C94A4A | stamps / danger |
| `--emerald` | #3A7D5C | D&D accent |

## Tipografía

- **Logo / headings pixel**: `Press Start 2P` (Google Fonts)
- **Títulos / subtitles medieval**: `Cinzel` (Google Fonts)
- **Body / UI**: `Nunito` (Google Fonts)