# library_website_tailwindCSS

Greenwood Public Library — Landing Page

A minimal, modern, editorial-style landing page for the fictional Greenwood Public Library. It showcases the library's sections, spaces, events and membership plans using large light-weight typography, soft pastel cards, hover transformations and staggered entry animations.

Built with plain HTML and Tailwind CSS (CDN). There is no build step, no custom CSS framework and no custom fonts (it uses the system font stack, with Segoe UI first).

Preview

Open index.html in any modern browser. An internet connection is needed for the Tailwind CDN script and the placeholder images.

project/
├── index.html
└── README.md
Features
Section	What it does
Navbar	Sticky, backdrop-blur-md, "Open Sat" badge, centered links with an animated underline (after:w-0 hover:after:w-full), "Visit Us" pill that inverts on hover. Links are hidden on mobile.
Hero	Two-column layout with a large light headline, a solid and an outlined CTA, a feature image with hover:scale-105, and a 4-column stats row.
Sections	1-column (mobile) / 2-column (desktop) grid of six cards. Each card has its own hover background (emerald, amber, sky, rose, violet, cyan) and its text colour shifts via group-hover.
Gallery	2×2 image grid with overflow-hidden rounded-lg, zoom on hover, a title and a rounded floor tag.
Why Greenwood	Pastel card grid (slate, emerald, amber, rose, violet, zinc) with hover colour changes.
About	Large light heading with newspaper-style text columns (columns-1 sm:columns-2).
Membership	Intro card plus Basic, Student and Family cards. Images use brightness-95 and zoom on hover. The Student card has an absolutely positioned "Popular" badge.
Testimonial	Quote with a circular avatar that goes from grayscale to full colour on hover (transition-all duration-500).
Contact	Emerald-tinted rounded block with the address, opening hours, a "Get Directions" button and a mailto link.
Events	4-column grid of cards with an image zoom on hover, a title and a date.
Footer	Four columns (Brand, Pages, Sections, Details), social icon circles with hover fills, and a bordered bottom bar with copyright and legal links.
Animations

A small Tailwind config extension in index.html defines a fadeUp keyframe and a fade-up animation:

js
tailwind.config = {
  theme: { extend: {
    keyframes: {
      fadeUp: {
        '0%':   { opacity: '0', transform: 'translateY(20px)' },
        '100%': { opacity: '1', transform: 'translateY(0)' }
      }
    },
    animation: { 'fade-up': 'fadeUp .7s ease-out both' }
  } }
}
Hero: elements use animate-fade-up with staggered delays such as [animation-delay:150ms].
Lower sections: a short IntersectionObserver script adds an .in class to .reveal elements as they scroll into view, which plays the same fade-up animation.
Customising
Images: all images are random placeholders from picsum.photos. Replace each src with your own files, for example images/hero.jpg.
Content: library name, address, phone, email, prices (₹) and events are sample data. Search index.html for 42 Elm Street or hello@greenwoodlibrary.org to update them.
Colours: hover and pastel colours are standard Tailwind utilities such as hover:bg-emerald-50 and bg-amber-50. Swap them for any other Tailwind colour.
Layout width: content is constrained with max-w-7xl mx-auto.
Responsiveness
Mobile: nav links are hidden, and most grids collapse to 1 column.
sm (640px+): 2-column grids for the gallery, membership and events, and 2-column text in About.
md (768px+): the nav links appear, and the hero and sections grids switch to 2 columns.
lg (1024px+): membership and events use 4 columns.
Tech stack
HTML5
Tailwind CSS via the Play CDN (https://cdn.tailwindcss.com)
Vanilla JavaScript (only for the scroll-reveal observer)
Notes
The Tailwind Play CDN is intended for prototyping. For production, install Tailwind with its CLI or PostCSS build so unused styles are purged.
Placeholder images require network access. For offline use, download the images and reference them locally.
License

Free to use and modify for learning and demonstration purposes.
