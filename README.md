# VertexPro Appliance Repair — Premium Landing Page (v4)

A **premium, client-presentable, animated** landing page for **VertexPro Appliance Repair** (Denver, CO),
fully **optimized for Facebook Ads traffic** — fast, mobile-first, conversion-focused, with a lead-capture
form wired to the RESTful Table API and **dynamic per-appliance detail pages**.

## 1. Completed Features

### 🦸 Hero (v4 — 2 clean columns)
- **Left column:** pill badge, gradient headline, dual CTAs (gold CALL + navy BOOK), Google-badge review
  line, animated stat counters (5,000+ repairs · 600+ reviews · 98% same-day). Vertically centered.
- **Right column:** the **"Why Denver Trusts VertexPro" trust panel — widened and stretched to match the
  left column height** (`align-items: stretch`), with gold award icon header, "Rated 4.9/5 by 600+
  homeowners" subtitle, and **8 auto-scrolling trust points** (seamless infinite loop, pause on
  hover/touch/wheel, resume after 1.8 s, masked fade edges, `prefers-reduced-motion` safe).
- Technician photo removed from hero per client request.

### 📍 Service Area (merged — one section, top placement)
- The two duplicate "Proudly Serving Denver & Nearby Areas" sections were **merged**: kept the richer
  2nd design (16-neighborhood list + map), placed at the 1st position (directly after hero).
- Polished: boxed light-blue neighborhood grid, gold CTA + live "technicians available" dot,
  map with ripple pin + **"Avg. arrival: under 2 hours"** floating tag.

### 🏷️ Brands & Models We Repair (redesigned)
- Two **opposing-direction marquee rows** of premium brand chips — each chip has a colored monogram
  tile (blue/navy/gold/red variants) + brand name + certification tagline (16 brands total).
- Feature strip below: Factory-Trained · Genuine OEM Parts · All Models — Old & New.
- Pause on hover; reduced-motion safe.

### 🧊 Appliances We Repair (real photos)
- 8 **AI-generated studio product photos** (Nano Banana Pro, compressed to 40–80 KB each):
  `images/appliance-{refrigerator,washer,dryer,dishwasher,oven,range,cooktop,microwave}.jpg`.
- Each card: photo (zoom-on-hover, links to detail page) + dual CTAs — **"View Details"**
  (→ `service.html?s=X`) and **"Book Now"** (→ `#book`).

### 📄 Per-Appliance Detail Pages (`service.html`)
- Single dynamic page driven by `?s=` query param (8 appliances; defaults to refrigerator).
- Breadcrumbs, hero with photo, **7 common issues** (staggered animation), 4-step "How Our Repair
  Visit Works", optional expert note, **sticky sidebar** (book card, trust chips, links to all
  other services).
- All "Book" buttons carry `index.html?appliance=X#book` → the lead-form **appliance dropdown is
  pre-selected** automatically.
- Every service section on index.html (Refrigerator Repair, Washer Repair, …) has a
  `.service-cta-row`: navy Book button + arrow "…repair details" link. Footer service links also
  point to detail pages.

### 👥 About VertexPro (rebuilt layout)
- Proper hierarchy: eyebrow label → 34px/900 title → paragraphs → checkmark list → actions → reviews,
  perfectly aligned 2-col grid; **3 feature cards** (Licensed & Insured, Warranty, Background-Checked)
  in a clean grid **below** the two columns.

### 📞 Dark CTA banner (redesigned — clean professional panel, no photo)
- Structured navy panel with subtle radial glows (photo background removed per client feedback).
- **Left:** eyebrow pill → "Speak directly with a **certified technician**" (gold gradient accent)
  → description → action row: boxed phone card (gold icon tile + "Call now — 24/7" label + number)
  · "or" · gold **BOOK ONLINE & SAVE $35** button → live-availability note.
- **Right:** credentials column behind a vertical divider — 3 credential cards
  (Top Pro on Thumbtack ×3 yrs, Google Verified 4.9/5, SuperPro on Housecall Pro) with colored
  icon tiles and hover slide.
- **Bottom trust strip:** darkened bar with 4 proof points (4.9/5 reviews · Warranty ·
  Same-day · Upfront pricing).
- Eyebrow label, enlarged phone number, gold Top Pro year badges, book button.

### 🎨 Brand & Imagery (all AI-generated, compressed)
- Transparent-background logo + white footer variant; OG/FB ad creative (1376×768);
  8 service-section photos; 8 appliance product photos; team photo; Denver map.

### 📣 Facebook Ads Optimization
- Open Graph + Twitter Card meta, **LocalBusiness JSON-LD**, lead form → `POST tables/leads`
  with automatic **utm_source / utm_campaign / fbclid** capture, mobile sticky action bar,
  top offer bar, lazy loading, width/height attrs (no CLS), all images kept lightweight.

### ✨ Polish & Animations
- Scroll-reveal (IntersectionObserver) with variants + stagger, animated counters, dual marquees,
  map ripple, floating badges, button shine sweep, pulsing call button, live-availability dot,
  mobile hamburger menu — all with `prefers-reduced-motion` guards.

## 2. Functional Entry URIs

| Path | Description |
|------|-------------|
| `/` or `/index.html` | Main landing page |
| `/index.html?appliance=Washer#book` | Lead form with appliance pre-selected |
| `/service.html?s=refrigerator` | Detail page — also: washer, dryer, dishwasher, oven, range, cooktop, microwave |
| In-page anchors | `#services`, `#reviews`, `#area`, `#faq`, `#about`, `#book`, `#footer` |
| `tel:+17206076361` | Click-to-call (nav, hero, CTA, floating & mobile bars) |
| `POST tables/leads` | Lead capture API (name, phone, appliance, message, source) |
| Query params | `?utm_source=…&utm_campaign=…` or `?fbclid=…` → stored on the lead |

## 3. Data Model

**Table `leads`** — `id`, `name` (text), `phone` (text), `appliance` (enum: Refrigerator…Other),
`message` (text), `source` (text; e.g. `facebook-ad / summer-sale`). Stored via the built-in RESTful Table API.

## 4. Not Yet Implemented
- Real Facebook Pixel / Conversions API snippet (add pixel ID when available).
- Live Google reviews feed; official brand logo SVGs (brand chips use styled monograms).
- Interactive Google Map embed (static map image used).

## 5. Recommended Next Steps
1. Add the client's **Meta Pixel** + fire a `Lead` event on form success.
2. Set absolute URLs in `og:image` after deploy (FB scraper needs absolute URLs).
3. Add a lightweight admin page to view captured leads (`GET tables/leads`).
4. A/B test hero headline & offer copy for ad campaigns.

## 6. Project Info
- **Fonts:** Inter (400–900) · **Icons:** Font Awesome 6.4.0
- **Colors:** navy `#0a1f56`/`#071640`, gold `#fdb913`, blue `#2563eb`, light bg `#eef3fc`
- **Phone:** (720) 607-6361 · **Email:** info@vertexprorepair.com

## 7. Public URLs
Not yet deployed — use the **Publish tab** to go live.

## 8. File Structure
```
index.html     # Landing page: 2-col hero, area, brands marquee, services, about, CTA, form
service.html   # Dynamic per-appliance detail page (?s=refrigerator … microwave)
index.css      # Premium animated responsive stylesheet (shared by both pages)
images/        # logo.png, logo-white.png, og-cover.jpg, about-team.jpg,
               # service-*.jpg (8 section photos), appliance-*.jpg (8 product photos),
               # image-16.jpg (Denver map)
README.md
```

## 9. Testing
- `PlaywrightConsoleCapture` on **index.html** and **service.html** (v4): both load with
  **zero console errors/warnings**.
