# OmniFood — Responsive Food Delivery Landing Page

A single-page, responsive landing site for a food-delivery brand, built as the
"OmniFood Demo" assignment. The page recreates the reference screenshots:
header + hero, how-it-works, cities grid, testimonials, pricing plans and a
footer — at desktop, tablet and mobile sizes.

**Built with plain HTML + CSS only.** No Bootstrap, no Tailwind, no build step,
no backend. The only JavaScript is ~5 lines that close the mobile menu after a
link is tapped (explicitly allowed for the navbar toggle).

## How to run

No installation or server needed — just open the file:

```
double-click index.html          (or)
open index.html
```

Everything (CSS, fonts, images) is local, so the page works fully offline.
If your browser blocks local font files, serve the folder instead:

```
python3 -m http.server 8000      # then visit http://localhost:8000
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

## Image & font credits

Photographs were downloaded into `assets/` so the page works offline.

| File | Author | License | Source |
|---|---|---|---|
| `hero-food.jpg` | Tomwsulcer | CC0 | [Chicken, asparagus and mashed potatoes (Wikimedia Commons)](https://commons.wikimedia.org/wiki/File:Chicken_and_asparagus_and_mashed_potatoes_served_on_a_plate_at_a_restaurant_in_Maryland.JPG) |
| `testimonials-bg.jpg` | Nenad Stojkovic | CC BY 2.0 | [Pizza vegetariana on a wooden rustic table](https://commons.wikimedia.org/wiki/File:Pizza_vegetariana_on_a_wooden_rustic_table_(49255624582).jpg) |
| `city-lisbon.jpg` | Berthold Werner | CC BY-SA 4.0 | [Lisbon Praça do Comércio](https://commons.wikimedia.org/wiki/File:Lisbon_Pra%C3%A7a_do_Com%C3%A9rcio_BW_2018-10-08_17-42-58.jpg) |
| `city-london.jpg` | Diliff | CC BY-SA 3.0 | [Tower Bridge London Dusk](https://commons.wikimedia.org/wiki/File:Tower_Bridge_London_Dusk_Feb_2006.jpg) |
| `city-berlin.jpg` | Thomas Wolf (foto-tw.de) | CC BY-SA 3.0 | [Brandenburger Tor morgens](https://commons.wikimedia.org/wiki/File:Brandenburger_Tor_morgens.jpg) |
| `city-san-francisco.jpg` | Cary Bass | CC BY-SA 3.0 | [Golden Gate Bridge Yang Ming Line](https://commons.wikimedia.org/wiki/File:Golden_Gate_Bridge_Yang_Ming_Line.jpg) |
| `phone-screen.jpg` | Shixart1985 | CC BY 2.0 | [Healthy meal planning with fresh fruits and vegetables](https://commons.wikimedia.org/wiki/File:Healthy_meal_planning_with_fresh_fruits_and_vegetables_in_a_bright_kitchen_setting.jpg) |
| `avatar-*.jpg` | randomuser.me | Free demo portraits | [randomuser.me](https://randomuser.me) |

CC BY-SA images may be used with attribution (this table) and share-alike
licensing applies if you redistribute them.

- **Logo / favicon:** original SVG created for this project.
- **Font:** [Lato](https://fonts.google.com/specimen/Lato) by Łukasz Dziedzic,
  licensed under the SIL Open Font License 1.1, self-hosted in `assets/fonts/`.
