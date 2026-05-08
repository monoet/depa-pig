# DEPA PIG and Friends — Website Spec

## Concept & Vision

Un sitio web para el "club secreto" de videojuegos y juegos de mesa más real que existe. Se siente como entrar a la taberna de un RPG indie — oscuro, cálido, con personalidad. Cada sección es una "habitación" del depa: el evento próximo, la sala de juegos, las reglas sagradas, el álbum de memorias y la puerta de entrada para nuevos miembros.

El tono es **cozy dungeon party** — no corporate, no infantil, no genérico SaaS. Más "cantina de adventurers" que "landing page de app".

---

## Component Grammar (Discrete Microsite Identity)

### 1. Layout Rhythm
Vertical stack. Cada sección es una "room" con padding generoso (48px-80px vertical). Las secciones alternan — algunas con fondo oscuro profundo, otras con fondo medio (vino/carbón). El contraste crea la sensación de moverse entre espacios dentro del depa.

### 2. Hero Composition
Full-bleed atmospheric. Fondo escuro cálido con imagen/ilustración de la sala gamer-taberna. Overlay gradiente oscuro en la parte superior para legibilidad del logo. Card del evento centrado en la parte inferior del hero. Logo "DEPA PIG" grande arriba, subtítulo "and Friends" debajo. Todo dentro del hero, centrado.

### 3. Button Language
Bordes redondeados (radio 12px). Fondo oscuro cálido con borde dorado/ámbar. Hover: glow cálido, escala sutil (1.03). Sin sombras planas — el glow es la profundidad. Font: uppercase, tracking amplio (0.12em), bold.

### 4. Card Anatomy
Son "RPG UI panels" — fondo `--bg-card` (#1A1215 con 85% opacity), borde `--border-gold` (#C9963A) doble (2px, luego 1px con gap de 4px, efecto "inset panel"). Esquinas con pequeños adornos tipo pixel-corner (CSS triangles en las esquinas). Pueden tener un "label tag" en la esquina superior izquierda estilo category badge.

### 5. Typography Mood
- Display/Logo: **"Press Start 2P"** (Google Fonts) — pixel font para el logo principal "DEPA PIG" y headings de sección.
- Subtítulos y labels: **"Cinzel"** — elegante, medieval, no Times New Roman.
- Body y UI: **"Nunito"** — friendly, rounded, legible, no genérica.
- Escala: 12px labels → 16px body → 24px subtitles → 42-64px hero title.

### 6. Decorative System
- Esquinas de tarjetas: pequeños triángulos CSS en las 4 esquinas (color `--gold`, 8x8px).
- Separadores de sección: línea horizontal con ornamento central tipo RPG divider (diamante + líneas).
- Badges: estilo "CLASSIFIED" — borde punteado, tipografía typewriter, stamps.
- Iconos: inline SVG custom, stroke 2px, estilo pixel/RPG (d20, controller, sword, shield, dice).
- Fondo de secciones: subtle noise texture via CSS + gradiente radial oscuro.
- Acentos: chispas/dots dorados decorativos en backgrounds.

### 7. Object/Icon Visual System
Inline SVG para:
- D20 (dado de 20 lados)
- Control de NES/SNES
- Espada
- Escudo
- Mapa enrollado
- Vaso/bebida
- Dados (par)
- Botón de "X" style
- Flecha/chevron

Todos stroke-based, 2px, color `--gold` default, `--cream` para secciones claras.

### 8. CTA Treatment
- Primario: fondo `--gold` sólido (#C9963A), texto oscuro (#1A0F00), borde none, glow amber en hover.
- Secundario: fondo transparent, borde 2px `--gold`, texto `--gold`, hover fill `--gold` con texto oscuro.
- Tamaño: grande, padding 16px 32px, font-size 14px uppercase, tracking 0.12em.
- Ubicación: centrado debajo del contenido relevante, nunca en línea con otros CTAs.

### 9. Navigation Treatment
- Sticky top, blur backdrop (glass morphism).
- Fondo: rgba(26, 18, 21, 0.85) con backdrop-filter blur(12px).
- Logo a la izquierda, links centrados (o hamburger en mobile).
- Links: Nunito 14px, uppercase tracking. Hover: color `--gold`.
- No underline en nav links.

### 10. Section Dividers
RPG divider: tres partes — línea izquierda + diamante central + línea derecha. Color `--gold` a 40% opacity. Padding vertical 24px.

### 11. Interaction/Hover
- Cards: translateY(-4px), box-shadow con glow ámbar, border-color más brillante.
- Buttons: scale(1.03) + box-shadow glow.
- Links: color transition a `--gold`.
- Images: opacity 0.85 → 1, scale sutil 1.02.

---

## Design Tokens (CSS Variables)

```css
:root {
  /* Palette — cozy dungeon */
  --void:      #0D0A0C;       /* Fondo más oscuro */
  --charcoal:  #1A1215;       /* Fondo de secciones */
  --espresso:  #261B1E;       /* Fondo de cards */
  --wine:      #3D2127;       /* Acento vino oscuro */
  --mahogany:  #5C323A;       /* secondary accent */

  /* Gold system */
  --gold:      #C9963A;       /* Primary accent */
  --gold-lt:   #E8C06A;       /* Gold highlight */
  --gold-dk:   #8B6520;       /* Gold shadow */
  --parchment: #F5E6C8;       /* Text on dark */
  --cream:     #FBF5E6;       /* Text bright */
  --muted:     #9C8878;       /* Secondary text */

  /* Functional */
  --red-accent:  #C94A4A;     /* Danger / important */
  --emerald:     #3A7D5C;     /* Success / D&D green */

  /* Surfaces */
  --bg-dark:   #0D0A0C;
  --bg-section:#1A1215;
  --bg-card:   rgba(38, 27, 30, 0.9);
  --border-gold: #C9963A;
  --border-lt:  rgba(201, 150, 58, 0.3);

  /* Typography */
  --font-pixel:  'Press Start 2P', monospace;
  --font-title:  'Cinzel', serif;
  --font-body:   'Nunito', sans-serif;

  /* Spacing */
  --sp-xs: 4px; --sp-sm: 8px; --sp-md: 16px;
  --sp-lg: 24px; --sp-xl: 40px; --sp-2xl: 64px;

  /* Borders */
  --r-sm: 6px; --r-md: 12px; --r-lg: 20px;
  --r-pill: 999px;
}
```

---

## Page Structure

```
[HEADER]          Logo + Nav, sticky glass
[HERO]             Full-bleed: Logo + event card + secret location
[ABOUT]            "¿Qué es Depa Pig?" — explica el club
[ACTIVITIES]       "Qué se juega" — 6 cards de actividades
[RULES]            "Reglas de la casa" — tono divertido, no autoritario
[GALLERY]          Moodboard / placeholder de fotos del lugar
[CONTACT/RSVP]     Formulario o botón WhatsApp
[FOOTER]           Logo + links + "¿quieres unirte?"
```

---

## Sections Detail

### Header
- Logo: "DEPA PIG" (Press Start 2P, 16px) + "and Friends" (Cinzel, 12px, muted)
- Nav: Events | Juegos | Reglas | Galería | Contacto
- Sticky, glass blur, z-index alto

### Hero
- Background: gradient oscuro + imagen filtrada de sala gamer / taberna
- Badge: "PRÓXIMO EVENTO" pixel-font pequeño, dorado
- Título: "Next Quest" (Press Start 2P, 28px mobile / 48px desktop)
- Subtítulo: "La próxima reunión de Depa Pig and Friends"
- Event card: fecha destacada, tipo de actividad, locación secreta
- CTAs: "Confirmar asistencia" (primary) + "Ver reglas de la casa" (ghost)
-Decoración: dados flotantes, bordes de pixel art

### About ("¿Qué es Depa Pig?")
- Título sección
- Párrafo corto y cálido
- Tres mini-stat blocks (como en D&D) con datos curiosos
- Fondo oscuro, layout centrado

### Activities ("Qué se juega")
- Título sección
- Grid 2x3 en mobile, 3x2 en desktop
- Cards con icono + nombre + descripción corta
- Hover lift effect
- Actividades: Videojuegos | Dungeons & Dragons | Juegos de Mesa | Party Games | Retas Casuales | Sesiones Especiales

### Rules ("Reglas de la Casa")
- Título con icono de escudo
- Lista de reglas con iconos de dados
- Tono divertido — cada regla es un "mandamiento" del club
- No suena areglamento corporativo
- Badge: "TOP SECRET" en esquina
- Fondo diferenciado (más oscuro o con patrón)

### Gallery
- Título: "Memoria del Depa"
- Masonry o grid de imágenes placeholder
- Imágenes: dados, mesa, snacks, pantallas, personajes, mapas
- Placeholder con mensajes como "foto del último game night" o "mapa de la campaña"
- Filter-style por categoría (placeholder)

### Contact / RSVP
- "¿Quieres caer?"
- Formulario: Nombre | ¿Vienes solo o con alguien? | ¿Qué quieres jugar?
- Botón WhatsApp o "Enviar mensaje"
- Info de contacto: Instagram / WhatsApp

### Footer
- Logo pequeño
- Links
- "Ubicación secreta · Solo por invitación"
- Tagline: "El verdadero tesoro son los amigos que se hacen jugando"

---

## Event Data (Single Source of Truth)

El archivo `src/data/event.ts` contiene todos los datos del próximo evento:

```typescript
export const nextEvent = {
  title: "Next Quest",
  subtitle: "La próxima reunión de Depa Pig and Friends",
  description: "Noche de videojuegos, dados y juegos de mesa",
  date: "Sábado 18 de mayo",
  time: "8:00 PM",
  location: "Ubicación secreta · Se comparte por invitación",
  ctaPrimary: "Confirmar asistencia",
  ctaSecondary: "Ver reglas de la casa",
}
```

Cambiar el evento = editar este archivo. No hay más cambios necesarios en el HTML.

---

## File Structure

```
depa-pig/
  index.html          # Single page, todas las secciones
  SPEC.md             # Este spec
  README.md           # Notas de implementación y deploy
```

---

## Anti-Reskin Comparison (vs discco-coffee)

| Layer | Discco Coffee | DEPA PIG | Same/Diff |
|---|---|---|---|
| Layout | Editorial, 3-col menu | Vertical dungeon rooms | **DIFFERENT** |
| Hero | Photo + overlay + badge | Full-bleed pixel-taberna + event card | **DIFFERENT** |
| Typography | Fraunces + DM Sans | Press Start 2P + Cinzel + Nunito | **DIFFERENT** |
| Cards | 3-col grid, border-radius | RPG panels, corner triangles, double border | **DIFFERENT** |
| Buttons | Olive fill, rounded | Gold fill with glow, pixel-style | **DIFFERENT** |
| Decorative | Tape, grain, editorial | Pixel corners, RPG dividers, stamps | **DIFFERENT** |
| Nav | Sticky olive underline | Sticky glass blur, gold hover | **DIFFERENT** |
| Section dividers | None | RPG diamond dividers | **DIFFERENT** |
| Icon system | Lucide icons | Custom SVG pixel/RPG icons | **DIFFERENT** |
| Color system | Cream + olive | Void + wine + gold | **DIFFERENT** |

**Result: PASS — 0 layers substantially same. This is a distinct visual identity.**

---

## Implementation Notes

- Single HTML file con CSS embebido y JS mínimo para interactividad del nav.
- Google Fonts: Press Start 2P, Cinzel, Nunito.
- Mobile-first CSS — breakpoints en 768px y 1024px.
- No frameworks — vanilla HTML/CSS/JS para máxima portabilidad.
- Imágenes placeholder via Unsplash con temática gamer/taberna.
- Ready para escalar a React/Vite si el proyecto crece.
- Deploy: gh-pages, Vercel, o cualquier host de archivos estáticos.