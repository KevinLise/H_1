#  Guía: Cómo construir cualquier Landing Page desde cero
### Metodología aplicada en el proyecto Sashi & Kent

---

## PASO 1 — LEE EL ENUNCIADO Y EXTRAE LOS REQUISITOS

Antes de escribir una sola línea de código, subraya o lista:
- ¿Qué secciones son OBLIGATORIAS?
- ¿Qué etiquetas HTML específicas piden?
- ¿Hay puntos EXTRA (tabla, animaciones, secciones adicionales)?
- ¿Qué archivos debo entregar? (README, carpeta img/, etc.)

**En el proyecto Sashi & Kent extraje:**
| Obligatorio | Punto extra |
|---|---|
| header, main, section, article, nav, footer | Tabla con thead/tbody |
| ul + li semántica | Animaciones CSS/JS |
| Flexbox y/o Grid | Sección "Nuestros Chefs" |
| Media Queries (mobile + >1024px) | Sección "Mapa del Evento" |
| README.md en inglés | |

---

## PASO 2 — DIBUJA EL ESQUELETO EN PAPEL (o mentalmente)

Antes de abrir el editor, piensa en bloques:

```
┌─────────────────────────────────┐
│  <header>  logo + <nav>         │
├─────────────────────────────────┤
│  <main>                         │
│  ┌───────────────────────────┐  │
│  │  <section> HERO           │  │
│  ├───────────────────────────┤  │
│  │  <section> EVENTOS/TABLA  │  │
│  ├───────────────────────────┤  │
│  │  <section> SOBRE NOSOTROS │  │
│  │    <article> card 1       │  │
│  │    <article> card 2       │  │
│  ├───────────────────────────┤  │
│  │  <section> MULTIMEDIA     │  │
│  └───────────────────────────┘  │
├─────────────────────────────────┤
│  <footer>                       │
└─────────────────────────────────┘
```

**Regla de oro para elegir la etiqueta correcta:**
- ¿Es navegación? → `<nav>`
- ¿Es un bloque temático con título? → `<section>`
- ¿Es contenido que puede existir SOLO (carta, producto, chef)? → `<article>`
- ¿Es solo estructura visual sin significado? → `<div>`

---

## PASO 3 — ESCRIBE EL HTML PRIMERO (sin CSS)

Orden recomendado:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
  <title>Nombre del Proyecto</title>
</head>
<body>

  <header>
    <!-- logo + nav -->
  </header>

  <main>

    <section class="hero">
      <!-- imagen de impacto + texto + botón -->
    </section>

    <section class="events">
      <!-- tabla de horarios -->
    </section>

    <section class="about">
      <!-- info + lista ul/li -->
      <article class="card">...</article>
    </section>

    <section class="multimedia">
      <!-- galería + video -->
    </section>

  </main>

  <footer>
    <!-- contacto + redes -->
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

---

## PASO 4 — ESTRUCTURA CSS EN ORDEN LÓGICO

Siempre organiza tu CSS así:

```css
/* 1. Variables globales */
:root {
  --color-primario: #c9a84c;
  --color-fondo: #0a0a0a;
  --fuente-titulo: 'Playfair Display', serif;
}

/* 2. Reset */
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

/* 3. Estilos base del body */
body { background: var(--color-fondo); font-family: ...; }

/* 4. Header */
header { ... }

/* 5. Cada sección en orden de aparición */
.hero { ... }
.events { ... }
.about { ... }
.multimedia { ... }

/* 6. Footer */
footer { ... }

/* 7. Animaciones y utilidades */
.reveal { opacity: 0; transform: translateY(40px); transition: ...; }

/* 8. Media Queries AL FINAL */
@media (max-width: 768px) { ... }
@media (max-width: 1024px) { ... }
```

---

## PASO 5 — PATRONES QUE SE REPITEN EN CUALQUIER PÁGINA

### Hero Section (siempre igual)
```css
.hero {
  height: 100vh;
  background: url('img/foto.jpg') center/cover no-repeat;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
/* Overlay oscuro encima de la imagen */
.hero::before {
  content: '';
  position: absolute;
  inset: 0;  /* equivale a top:0; right:0; bottom:0; left:0 */
  background: rgba(0,0,0,0.6);
}
/* El contenido va encima del overlay */
.hero-content { position: relative; z-index: 1; }
```

### Cards en Grid (chefs, productos, etc.)
```css
.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);  /* 3 columnas iguales */
  gap: 2rem;
}
/* En móvil: 1 columna */
@media (max-width: 768px) {
  .cards-grid { grid-template-columns: 1fr; }
}
```

### Tabla HTML correcta
```html
<table>
  <thead>               <!-- ← encabezado -->
    <tr>
      <th>Hora</th>
      <th>Chef</th>
    </tr>
  </thead>
  <tbody>               <!-- ← filas de datos -->
    <tr>
      <td>14:00</td>
      <td>Chef Ana</td>
    </tr>
  </tbody>
</table>
```

### Nav + Hamburger (mobile)
```html
<!-- En HTML -->
<button class="hamburger" id="btn-menu">☰</button>
<nav id="main-nav">
  <ul><li><a href="#">Inicio</a></li></ul>
</nav>
```
```css
/* En CSS: oculto por defecto en mobile */
@media (max-width: 768px) {
  nav { display: none; }
  nav.open { display: block; }
  .hamburger { display: block; }
}
```
```js
// En JS: toggle al hacer click
document.getElementById('btn-menu').addEventListener('click', () => {
  document.getElementById('main-nav').classList.toggle('open');
});
```

---

## PASO 6 — CHECKLIST ANTES DE ENTREGAR

```
 ¿Tiene DOCTYPE, charset, viewport?
 ¿Usé <main> como contenedor?
 ¿Cada sección temática usa <section>?
 ¿Los elementos independientes usan <article>?
 ¿Hay al menos una <ul> con <li> semántica?
 ¿La tabla tiene <thead>, <tbody>, <th>, <td>?
 ¿El CSS tiene variables :root?
 ¿Usé Flexbox O Grid (no solo margin/padding)?
 ¿Hay media queries para mobile (768px) y desktop (1024px)?
 ¿El script.js está al final del <body>?
 ¿Existe el README.md?
 ¿Las imágenes están en la carpeta img/?
```

---

## ¿Cambia la temática? Cambia SOLO esto:

Si mañana te dan "Agencia de viajes" en vez de restaurante:

| Qué cambias | Qué NO cambias |
|---|---|
| Colores (azul oceano, verde selva) | La estructura: header/main/footer |
| Fuentes (más aventurera) | Los patrones: hero, grid de cards, tabla |
| Imágenes | Las media queries |
| Textos y nombres de secciones | El JS (hamburger, scroll reveal, tabs) |
| Nombre de clases CSS | La lógica de cómo funciona todo |

**La estructura mental siempre es la misma. Solo cambia la ropa.**
