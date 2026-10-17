# OmniFood — Responsive Food Delivery Landing Page

A single-page, responsive landing site for a food-delivery brand, built as the
"OmniFood Demo" assignment. The page recreates the reference screenshots:
header + hero, how-it-works, cities grid, testimonials, pricing plans and a
footer — at desktop, tablet and mobile sizes.

## How to run

```
double-click index.html          (or)
open index.html
```

## Files

```
omnifood-landing/
├── index.html          # all six page sections (semantic HTML)
├── style.css           # all styling — plain CSS, desktop-first
├── README.md
└── assets/
    ├── logo.svg            # circular crossed cutlery logo (hand-drawn SVG)
    ├── favicon.svg         # tab icon
    ├── hero-food.jpg       # hero background
    ├── phone-screen.jpg    # photo inside the CSS phone mockup
    ├── city-lisbon.jpg
    ├── city-london.jpg
    ├── city-berlin.jpg
    ├── city-san-francisco.jpg
    ├── testimonials-bg.jpg # testimonials background
    ├── avatar-alberto.jpg / avatar-joana.jpg / avatar-milton.jpg
    └── fonts/              # self-hosted Lato (woff2, weights 300/400/700)
```

## Sections

1. **Header + Hero** — circular logo, nav (Food delivery / How it works /
   Our cities / Sign-up), headline "Goodbye junk food — Hello super healthy
   food", primary + ghost CTA buttons, background photo with a dark gradient
   overlay for readability.
2. **How it works** — pure-CSS phone mockup on the left, three numbered steps
   on the right, Google Play + App Store badges below.
3. **Our cities** — 4-column grid (Lisbon, London, Berlin, San-Francisco),
   each card with a photo, city name and happy-eaters / chefs / handle list.
4. **Testimonials** — three quotes with quote marks, avatars and names over a
   photo background with a dark overlay.
5. **Pricing plans** — Premium ($399/month), Pro ($199/month), Starter
   ($19$/meal), feature lists with check/cross icons and Sign-up buttons.
6. **Footer** — links (About us, Blog, Press, iOS App, Android App), social
   icons and a copyright line.

## Responsive breakpoints

Desktop-first media queries in `style.css` (matching the assignment spec):

| Breakpoint | Target | Behaviour |
|---|---|---|
| base (≥ 1200 px intent) | Desktop | Full grid: 4-col cities, 3-col pricing, 3-col testimonials, two-column how-it-works, full navbar |
| `max-width: 834px` | Tablet | Navbar collapses to a hamburger, sections stack, **grids become 2 columns** (cities 2×2, pricing 2 + 1 centred, testimonials 2 + 1 centred), how-it-works stacks to one column |
| `max-width: 390px` | Mobile | **Single column everywhere**, smaller titles/padding, hero + buttons resize, footer stacks |

Verified requirements:

- ✅ No horizontal scrolling at 1400 px, 834 px or 390 px
  (`document.scrollWidth == clientWidth` at all three widths)
- ✅ Images scale with `object-fit: cover` + `aspect-ratio` (never overflow)
- ✅ Text and buttons stay readable and aligned at every size

## Implementation notes

- **Mobile navigation:** a visually-hidden `<checkbox>` + `<label>` hamburger —
  the menu opens/closes with pure CSS (`:checked ~ …`), and a 5-line inline
  script closes it after a link is tapped. No other JavaScript.
- **Phone mockup:** drawn entirely in CSS (frame, speaker, camera, home
  button, status bar) around a photo — no mockup image needed.
- **Icons:** all inline SVG (checks, cross, star, smiley, socials, store
  badges) — they inherit colour and stay sharp at any size.
- **Typography:** self-hosted Lato (300/400/700) with `@font-face`, so the page
  renders identically offline.
- **Design tokens:** colours, container width and padding live in `:root`
  custom properties — change the brand orange once and it updates everywhere.
- **Accessibility:** semantic landmarks (`header/nav/main sections/footer`),
  alt text on meaningful images, `aria-hidden` on decorative SVGs, visible
  `:focus-visible` styles, and a `prefers-reduced-motion` rule.
