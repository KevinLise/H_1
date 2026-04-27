# Fusion Gourmet — Gastronomic Festival Landing Page

A responsive landing page for **Fusión Gourmet**, an avant-garde gastronomic festival that brings together the world's top chefs for a unique culinary experience.

---

## Description

This project is a single-page website (landing page) built entirely with **HTML5**, **CSS3**, and **vanilla JavaScript**. It was designed to promote the Fusión Gourmet festival, allowing visitors to explore the schedule, gallery, and general festival information, and to reserve their tickets.

---

## Technologies Used

| Technology | Purpose |
|---|---|
| HTML5 | Semantic page structure (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`) |
| CSS3 | Layout (Flexbox + CSS Grid), animations, transitions, responsive design |
| JavaScript (ES6) | Hamburger menu toggle, outside-click detection, active link highlighting via Intersection Observer |
| Google Fonts | `Playfair Display` (headings) + `Lato` (body text) |
| Unsplash | Free gourmet food images for the gallery |
| YouTube Image API | Auto-fetched video thumbnail for the multimedia section |

---

## Project Structure

```
fusion-gourmet/
│
├── index.html          # Main HTML file — all page sections
├── style.css           # All styles — layout, colors, animations, responsive
├── script.js           # Interactive behavior — menu, scroll highlight
│
├── img/
│   ├── logo.png        # Festival logo shown in the header
│   ├── fondo.jpg       # Hero background photo
│   └── imagen.png      # Kirby cooking character (Festin Gourmet section)
│
└── README.md           # This file
```

---

## Page Sections

### 1. Header
- Festival logo and site title on the left.
- Navigation links on the right (desktop).
- Hamburger button (☰ / ✕) on mobile that toggles a vertical dropdown menu.

### 2. Hero (`#inicio`)
- Full-width background photo with an overlaid headline and a **"Reservar ticket"** call-to-action button.

### 3. Schedule (`#chefs`)
- HTML table (`<thead>` + `<tbody>`) listing 6 chef sessions with time, chef name, topic, and ticket count.
- Horizontally scrollable on small screens to prevent overflow.

### 4. Festín Gourmet (`#festival`)
- Two-column layout: description text + feature list on the left, Kirby cooking character image on the right.
- Includes a `<ul>` list of festival highlights and sponsors.

### 5. Gallery (`#galeria`)
- CSS Grid with 6 gourmet food images from Unsplash.
- Each card has a **zoom effect** and a **label overlay** that fades in on hover.

### 6. Multimedia
- YouTube video thumbnail that links directly to YouTube in a new tab when clicked.
- Custom circular play button overlaid on the thumbnail.

### 7. Footer (`#contacto`)
- Three-column grid: brand blurb, contact info, and social media links.

---

## Responsive Design

Media queries handle three breakpoints:

| Breakpoint | Behavior |
|---|---|
| `> 1024px` | Full desktop layout — 3-column gallery and footer |
| `≤ 1024px` | Tablet — gallery and footer switch to 2 columns |
| `≤ 768px` | Mobile — hamburger menu activates, festival section stacks vertically, footer becomes 1 column |
| `≤ 480px` | Small mobile — gallery becomes 1 column, hero and headings are scaled down |

---

## JavaScript Features (`script.js`)

### Hamburger Menu Toggle
- Clicking ☰ opens the mobile dropdown and swaps the icon to ✕.
- Clicking ✕ closes it and restores ☰.
- The page body scroll is locked while the menu is open (`overflow: hidden`).

### Close on Outside Click
- Tapping anywhere outside the header while the menu is open automatically closes it.
- Uses `event.target.closest('header')` to detect outside clicks efficiently.

### Close on Link Click
- Tapping any nav link closes the mobile menu so the user lands directly on the section.

### Active Link Highlight (Intersection Observer)
- As the user scrolls, the nav link matching the currently visible section gets the `.nav-active` class (plum background).
- Uses `IntersectionObserver` instead of a scroll event listener for better performance on mobile.

---

## Color Palette

| Name | Value | Usage |
|---|---|---|
| `lightslategray` | `#778899` | Header, schedule section, gallery section, footer |
| `plum` | `#DDA0DD` | Accent — separator line, button, table header, play button, active nav link |
| White | `#ffffff` | Card backgrounds, text on dark sections |
| Dark text | `#333` – `#555` | Body text on light backgrounds |

---

## How to View Locally

1. Download or clone the project folder.
2. Make sure the `img/` folder is in the same directory as `index.html`.
3. Open `index.html` in any modern browser (Chrome, Firefox, Edge, Safari).

> No build tools, no dependencies, no server required. Just open the file.

---

## External Resources

- **Gallery images** — [Unsplash](https://unsplash.com) (free for personal and commercial use)
- **Video thumbnail** — YouTube Image API: `https://img.youtube.com/vi/{VIDEO_ID}/maxresdefault.jpg`
- **Fonts** — [Google Fonts](https://fonts.google.com) (Playfair Display + Lato)
