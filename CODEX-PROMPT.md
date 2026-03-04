# ChatGPT Codex Prompt: Build a New State for Commercial Roof Guide

Copy everything below the line into Codex as your prompt. Replace `[STATE]` placeholders with the state you're building.

---

## YOUR TASK

You are building the **[STATE]** section of **commercialroofguide.com**, a national commercial roofing authority site for building owners and facility managers. You must create:

1. A **state page** at `states/[state-slug]/index.html`
2. **City pages** at `states/[state-slug]/[city-slug]/index.html` for every major city in the state
3. Update the **states hub** (`states/index.html`), **homepage** (`index.html`), **all navigation and footers** across every HTML file, **sitemap**, **llms.txt**, and **llms-full.txt`

This is a static HTML site — no build step, no framework. Each page is a self-contained `.html` file with inline CSS, inline JS, and all content. Deployed on Netlify via GitHub (`minyona/commercial-roof-guide`).

**CRITICAL DIFFERENCE FROM RESIDENTIAL:** This site is about **commercial roofing** — flat and low-slope systems for offices, warehouses, retail, restaurants, and industrial buildings. NOT residential shingles. The audience is building owners, facility managers, property managers, and commercial property investors. All content must use commercial terminology.

---

## STEP 1: RESEARCH THE STATE

Before writing any code, research and compile this data for [STATE]:

### State-Level Research
- **Climate zones** (IECC/ASHRAE) and how they affect commercial roofing (hurricanes, hail belt, snow load, extreme heat, ponding water, freeze-thaw, etc.)
- **Commercial building code framework** (IBC adoption, state-specific amendments, energy code version — IECC 2021/2024, ASHRAE 90.1 compliance)
- **Energy code requirements** — cool roof mandates, minimum insulation R-values by climate zone, Title 24 (if CA)
- **Average commercial roofing costs** for the state vs national average (per square foot installed)
- **Popular roofing systems** for the climate (TPO in hot climates, EPDM in cold, PVC near coast/restaurants, metal in hurricane zones, etc.)
- **Insurance/wind requirements** — FM Global ratings, TWIA in Texas, Citizens in Florida, IBHS FORTIFIED, etc.

### City Selection
Pick **every city with significant commercial real estate** — county seats, cities with 50,000+ population, notable commercial/industrial hubs even if smaller. Group them by metro area. For a large state like Florida or California, this could be 60-100 cities. For a smaller state like Connecticut, 25-40 cities.

### Per-City Research (for each city)
- **Population** (approximate, current)
- **Commercial building landscape** — major commercial districts, industrial parks, business corridors, notable developments
- **5 commercial areas/districts** — real neighborhood or district names with:
  - Building era (e.g., "Developed 1980s-2000s")
  - Commercial building types (strip malls, office parks, warehouses, mixed-use, industrial)
  - Roofing-relevant details (flat roof prevalence, ponding issues, wind exposure, chemical exposure from nearby industry, rooftop HVAC units)
- **4 weather/climate stats:**
  - Stat 1: Hail days per year OR hurricane risk level OR snow load (psf)
  - Stat 2: Average summer high temperature
  - Stat 3: Annual rainfall OR humidity level
  - Stat 4: Wind exposure OR freeze-thaw cycles OR unique climate threat
- **7-row cost table** with these commercial roofing systems:
  - TPO (60 mil) — most popular
  - EPDM (60 mil) — budget option
  - PVC (60 mil) — chemical resistant
  - Modified Bitumen — walkable
  - Built-Up Roofing (BUR) — multi-layer
  - Spray Foam (SPF) — seamless
  - Standing Seam Metal — premium/long-life
  - Each row needs: System name, Cost/Sq Ft range, Lifespan, "Best For" description
  - Costs are PER SQUARE FOOT (not total project cost) — commercial roofs range from 5,000 to 500,000+ sq ft
- **2 permit/regulation cards:**
  - Card 1: Building permits and commercial code requirements (city-specific permit office, IBC compliance, energy code)
  - Card 2: Insurance, wind ratings, or special requirements (FM Global, IBHS, cool roof mandates, etc.)
- **4-5 nearby cities** (must be other cities in YOUR state that also have pages on the site)
- **4 FAQ questions** that are genuinely city-specific:
  - Q1: "How much does a commercial roof cost in [City], [State abbrev]?"
  - Q2: Something about the city's specific climate threat to commercial roofs
  - Q3: Something about systems or regulations specific to that city's commercial buildings
  - Q4: Something unique to that city (growth corridors, industrial districts, energy codes, etc.)
- **Lat/Long coordinates** for geo meta tags
- **City intro paragraphs** (2 paragraphs): Explain the city's commercial real estate landscape, building stock, growth patterns, and why commercial roofing matters there. Reference specific business districts, industrial parks, highways, and local details. This is NOT generic content — it must read like someone who knows the city's commercial market wrote it.

---

## STEP 2: CITY PAGE TEMPLATE

Every city page must be a **self-contained HTML file** with **ALL CSS inline** in `<style>` tags and **ALL JS inline** in `<script>` tags. No external CSS or JS files (except Google Fonts). Each page should be **650-800 lines**.

### Exact Structure (15 sections in this order)

```
1. <head> — SEO meta, geo meta, OG tags, Twitter cards, schema JSON-LD, inline CSS
2. <header> — Fixed nav with logo, Guides/States/Calculator links, CTA button
3. Mobile nav overlay
4. Breadcrumb — Home > States > [State] > [City], [ST]
5. Location Hero — H1, 3 stat cards, 2 CTA buttons
6. City Intro — Section label, H2, 2 paragraphs, freshness badge
7. Commercial Districts — 5 district/area cards in a grid
8. Weather/Climate — Navy background, left content + right 4-stat grid
9. Cost Table — 7-row table with System, Cost/Sq Ft, Lifespan, Best For
10. Permits & Building Codes — 2-card grid with bullet lists
11. Nearby Cities — Grid of links to other city pages on the site
12. FAQ — 4 accordion items
13. CTA — Terracotta gradient, H2, paragraph, 2 buttons
14. Footer — 4-column grid
15. JavaScript — Year, scroll header, mobile nav, FAQ accordion, IntersectionObserver, cost table mobile labels
```

### Critical Design Tokens (CSS Custom Properties)

```css
:root {
  --navy: #1B3A5C;
  --navy-light: #2D5F8A;
  --slate: #3d4f5f;
  --charcoal: #2c3e50;
  --terracotta: #C45C3E;
  --terracotta-dark: #A84832;
  --copper: #B87333;
  --gold: #C9A959;
  --cream: #FAF8F5;
  --warm-gray: #F5F3F0;
  --stone: #E8E4DF;
  --white: #ffffff;
  --text: #3A3A3A;
  --text-light: #6b6b6b;
  --text-muted: #8a8a8a;
  --shadow-sm: 0 2px 8px rgba(27,58,92,0.06);
  --shadow-md: 0 8px 30px rgba(27,58,92,0.08);
  --shadow-lg: 0 20px 60px rgba(27,58,92,0.12);
  --ease-out: cubic-bezier(0.25,0.46,0.45,0.94);
  --ease-smooth: cubic-bezier(0.4,0,0.2,1);
}
```

### Fonts
- **Headings:** `'Playfair Display', Georgia, serif` — weights 400, 500, 600, 700
- **Body:** `'DM Sans', -apple-system, BlinkMacSystemFont, sans-serif` — weights 400, 500, 600, 700
- Load via: `<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=DM+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">`

### CRITICAL DESIGN RULES (Follow Exactly)

These rules are non-negotiable. Codex has repeatedly gotten these wrong — follow them precisely.

**Body & Layout:**
```css
body { background: var(--white); }  /* WHITE, not cream */
.container { max-width: 1320px; margin: 0 auto; padding: 0 40px; }
section { padding: 100px 0; }  /* 100px desktop, 80px mobile */
```

**Hero Section (City Pages):**
```css
.location-hero {
  background: var(--cream);  /* Clean cream background — NEVER dark gradient overlays */
  padding: 48px 0 72px;
}
.location-hero h1 { color: var(--navy); }  /* Navy text — NOT white */
.location-hero .subtitle { color: var(--text-light); }  /* NOT rgba(255,255,255,...) */
.hero-stats { display: flex; gap: 40px; }  /* gap: 40px — NOT 18px */
.hero-stat {
  background: var(--white);  /* White cards with shadow — NOT glass/transparent */
  box-shadow: 0 2px 12px rgba(27,58,92,0.08);
  border-radius: 12px;
  padding: 24px 20px;
  text-align: center;
}
.hero-stat .stat-value {
  color: var(--navy);  /* Navy — NOT gold */
  font-size: 2rem;  /* 2rem — NOT 1.62rem */
  font-weight: 700;
}
.hero-stat .stat-label {
  color: var(--text-light);  /* text-light — NOT white */
  font-size: 0.85rem;
}
```

**Spacing Minimums (DO NOT go smaller):**
```css
/* Commercial district cards */
.district-card { padding: 32px 28px; }  /* NOT 26px 22px */

/* Weather section */
.weather-grid { gap: 80px; }  /* NOT 50px */
.weather-stat { padding: 32px 28px; }  /* NOT 24px 18px */
.weather-stat .stat-value { font-size: 2.25rem; }  /* NOT 1.65rem */

/* Permits section */
.permits-grid { gap: 40px; }  /* NOT 24px */
.permit-card { padding: 36px 32px; }  /* NOT 30px 26px */

/* FAQ section */
.faq-grid { gap: 20px; }  /* NOT 16px */
.faq-question { padding: 24px 28px; }  /* NOT 20px 22px */

/* Other grid gaps */
.city-cards-grid { gap: 16px; }
.nearby-grid { gap: 16px; }
```

**Breadcrumbs:**
```css
/* Clean inline list — NO pill/badge styling, no borders, no box-shadow, no background */
.breadcrumb a { color: var(--text-muted); text-decoration: none; }
.breadcrumb a:hover { color: var(--terracotta); }
```

**IntersectionObserver (JavaScript):**
```javascript
// threshold MUST be 0, NOT 0.1 — 0.1 causes blank sections on tall mobile pages
// rootMargin MUST be '0px 0px -40px 0px' — NOT -50px
const observerOptions = { threshold: 0, rootMargin: '0px 0px -40px 0px' };
```

### Schema Markup (JSON-LD in `<head>`)

**ONLY these two schemas per city page — no others:**

1. **BreadcrumbList:**
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://commercialroofguide.com/" },
    { "@type": "ListItem", "position": 2, "name": "States", "item": "https://commercialroofguide.com/states/" },
    { "@type": "ListItem", "position": 3, "name": "[State Name]", "item": "https://commercialroofguide.com/states/[state-slug]/" },
    { "@type": "ListItem", "position": 4, "name": "[City], [ST]", "item": "https://commercialroofguide.com/states/[state-slug]/[city-slug]/" }
  ]
}
```

2. **FAQPage:**
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Question text here?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Detailed answer with specific local data, commercial district names, and cost figures."
      }
    }
  ]
}
```

**DO NOT use LocalBusiness, RoofingContractor, or Service schema. We are a publisher, not a contractor.**

### SEO Meta Tags (in `<head>`)

```html
<title>Commercial Roofing in [City] [ST] | Costs, Systems & Codes (2026)</title>
<!-- Title must be 50-60 characters -->

<meta name="description" content="[City], [ST] commercial roofing guide for 2026. Compare TPO, EPDM, PVC, and metal costs per sq ft for offices, warehouses, and retail. Local building codes and energy requirements.">
<!-- Description must be 150-160 characters -->

<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1">
<link rel="canonical" href="https://commercialroofguide.com/states/[state-slug]/[city-slug]/">

<!-- Geo -->
<meta name="geo.region" content="US-[ST]">
<meta name="geo.placename" content="[City], [State]">
<meta name="geo.position" content="[lat];[long]">
<meta name="ICBM" content="[lat], [long]">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://commercialroofguide.com/states/[state-slug]/[city-slug]/">
<meta property="og:title" content="Commercial Roofing in [City] [ST] | Costs, Systems & Codes (2026)">
<meta property="og:description" content="[City], [ST] commercial roofing costs per sq ft for TPO, EPDM, PVC, metal. Local codes and energy requirements.">
<meta property="og:site_name" content="Commercial Roof Guide">
<meta property="og:locale" content="en_US">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Commercial Roofing in [City] [ST] | Commercial Roof Guide">
<meta name="twitter:description" content="[City], [ST] commercial roofing guide for 2026. Compare system costs, codes, and requirements.">
```

### Navigation (Desktop Header)

```html
<header class="header" id="header">
  <div class="container">
    <div class="header-inner">
      <a href="/" class="logo" aria-label="Commercial Roof Guide">
        <svg class="logo-icon" width="36" height="29" viewBox="0 0 40 32" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 0L40 30H33L20 10L7 30H0L20 0z" fill="currentColor"/></svg>
        <div class="logo-text">Commercial Roof Guide<span>Independent Commercial Roofing Resource</span></div>
      </a>
      <nav>
        <ul class="nav-links">
          <li><a href="/guides/">Guides</a></li>
          <li><a href="/states/">States</a></li>
          <li><a href="/calculator/">Calculator</a></li>
        </ul>
      </nav>
      <div class="header-cta">
        <a href="/free-estimate/" class="btn btn-primary">Free Estimate</a>
      </div>
      <button class="nav-toggle" aria-label="Menu" aria-expanded="false"><span></span><span></span><span></span></button>
    </div>
  </div>
</header>
```

### Mobile Navigation

```html
<div class="mobile-nav">
  <a href="/">Home</a>
  <div>
    <button class="mobile-nav-accordion-trigger" data-accordion>
      Guides
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
    </button>
    <div class="mobile-nav-accordion-content">
      <a href="/guides/">All Guides</a>
      <a href="/guides/commercial-roof-cost/">Commercial Roof Costs</a>
      <a href="/guides/tpo-roofing/">TPO Roofing</a>
      <a href="/guides/epdm-roofing/">EPDM Roofing</a>
      <a href="/guides/pvc-roofing/">PVC Roofing</a>
      <a href="/guides/modified-bitumen/">Modified Bitumen</a>
      <a href="/guides/built-up-roofing/">Built-Up Roofing</a>
      <a href="/guides/spray-foam-roofing/">Spray Foam Roofing</a>
      <a href="/guides/metal-roofing-commercial/">Commercial Metal Roofing</a>
      <a href="/guides/roof-maintenance/">Roof Maintenance</a>
      <a href="/guides/roof-coatings/">Roof Coatings</a>
      <a href="/guides/cool-roofs/">Cool Roofs</a>
      <a href="/guides/roof-inspections/">Roof Inspections</a>
      <a href="/guides/warranties/">Warranties</a>
      <a href="/guides/green-roofs/">Green Roofs</a>
    </div>
  </div>
  <div>
    <button class="mobile-nav-accordion-trigger" data-accordion>
      States
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
    </button>
    <div class="mobile-nav-accordion-content">
      <a href="/states/">All States</a>
      <a href="/states/[state-slug]/">[State] ([N] cities)</a>
      <!-- ADD ALL ACTIVE STATES HERE -->
    </div>
  </div>
  <a href="/calculator/">Calculator</a>
  <a href="/about/">About</a>
  <a href="/free-estimate/" class="btn btn-primary">Get Free Estimate</a>
</div>
```

**IMPORTANT:** Add your new state to the mobile nav ON EVERY HTML FILE IN THE ENTIRE SITE. All existing pages (guides, homepage, calculator, etc.) must also get the new state link in their mobile nav.

### Footer (same on every page)

```html
<footer class="footer">
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <a href="/" style="display:inline-flex;align-items:center;gap:10px;text-decoration:none;">
          <svg width="32" height="26" viewBox="0 0 40 32" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 0L40 30H33L20 10L7 30H0L20 0z" fill="#C45C3E"/></svg>
          <span style="font-family:'DM Sans',sans-serif;font-weight:700;font-size:1rem;color:#fff;">Commercial Roof Guide</span>
        </a>
        <p>Independent commercial roofing resource for building owners and facility managers across America.</p>
      </div>
      <div>
        <h4>Guides</h4>
        <ul>
          <li><a href="/guides/commercial-roof-cost/">Commercial Roof Costs</a></li>
          <li><a href="/guides/tpo-roofing/">TPO Roofing</a></li>
          <li><a href="/guides/epdm-roofing/">EPDM Roofing</a></li>
          <li><a href="/guides/pvc-roofing/">PVC Roofing</a></li>
          <li><a href="/guides/roof-maintenance/">Roof Maintenance</a></li>
          <li><a href="/guides/warranties/">Warranties</a></li>
        </ul>
      </div>
      <div>
        <h4>Tools</h4>
        <ul>
          <li><a href="/calculator/">Cost Calculator</a></li>
          <li><a href="/free-estimate/">Free Estimate</a></li>
        </ul>
        <h4 style="margin-top:24px;">Company</h4>
        <ul>
          <li><a href="/about/">About Us</a></li>
          <li><a href="/approved/">Approved Contractors</a></li>
          <li><a href="/states/">All States</a></li>
        </ul>
      </div>
      <div>
        <h4>States</h4>
        <ul>
          <li><a href="/states/[state-slug]/">[State] ([N] cities)</a></li>
          <!-- ADD ALL ACTIVE STATES HERE -->
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; <span id="year"></span> Commercial Roof Guide. Independent commercial roofing resource.</p>
      <p><a href="/about/">How we make money</a> | Website by <a href="https://minyona.com" target="_blank" rel="noopener">Minyona</a></p>
    </div>
  </div>
</footer>
```

**IMPORTANT:** The footer States section must list ALL active states. Update the footer on EVERY HTML file in the entire site to add the new state.

### Required JavaScript (bottom of `<body>`, before `</body>`)

```html
<script>
  // Year
  document.getElementById('year').textContent = new Date().getFullYear();

  // Header scroll effect
  const header = document.getElementById('header');
  window.addEventListener('scroll', () => { header.classList.toggle('scrolled', window.scrollY > 50); });

  // Mobile nav toggle
  const navToggle = document.querySelector('.nav-toggle');
  const mobileNav = document.querySelector('.mobile-nav');
  navToggle.addEventListener('click', () => {
    const isExpanded = navToggle.getAttribute('aria-expanded') === 'true';
    navToggle.setAttribute('aria-expanded', !isExpanded);
    navToggle.classList.toggle('active');
    mobileNav.classList.toggle('active');
    document.body.style.overflow = mobileNav.classList.contains('active') ? 'hidden' : '';
  });
  mobileNav.querySelectorAll('a').forEach(link => {
    link.addEventListener('click', () => {
      navToggle.classList.remove('active');
      mobileNav.classList.remove('active');
      navToggle.setAttribute('aria-expanded', 'false');
      document.body.style.overflow = '';
    });
  });

  // Mobile nav accordions
  document.querySelectorAll('.mobile-nav-accordion-trigger').forEach(trigger => {
    trigger.addEventListener('click', () => {
      const content = trigger.nextElementSibling;
      const isOpen = trigger.classList.contains('active');
      document.querySelectorAll('.mobile-nav-accordion-trigger').forEach(t => {
        t.classList.remove('active');
        t.nextElementSibling.style.maxHeight = '0';
      });
      if (!isOpen) {
        trigger.classList.add('active');
        content.style.maxHeight = content.scrollHeight + 'px';
      }
    });
  });

  // FAQ accordion (exclusive open)
  document.querySelectorAll('.faq-question').forEach(button => {
    button.addEventListener('click', () => {
      const faqItem = button.parentElement;
      const isExpanded = button.getAttribute('aria-expanded') === 'true';
      document.querySelectorAll('.faq-item').forEach(item => {
        item.classList.remove('active');
        item.querySelector('.faq-question').setAttribute('aria-expanded', 'false');
        item.querySelector('.faq-answer').style.maxHeight = '0';
      });
      if (!isExpanded) {
        faqItem.classList.add('active');
        button.setAttribute('aria-expanded', 'true');
        const answer = faqItem.querySelector('.faq-answer');
        answer.style.maxHeight = answer.scrollHeight + 'px';
      }
    });
  });

  // Scroll-triggered animations
  // CRITICAL: threshold MUST be 0, NOT 0.1 — threshold 0.1 causes blank sections on tall mobile pages
  const observerOptions = { threshold: 0, rootMargin: '0px 0px -40px 0px' };
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, observerOptions);
  document.querySelectorAll('main section:not(.location-hero):not(.breadcrumb)').forEach(section => {
    section.style.opacity = '0';
    section.style.transform = 'translateY(30px)';
    section.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
    observer.observe(section);
  });

  // NOTE: Do NOT add page-view beacons. sendBeacon only fires from form submissions.
</script>

<!-- Cost table mobile card labels -->
<script>document.querySelectorAll(".cost-table").forEach(t=>{const h=[...t.querySelectorAll("th")].map(th=>th.textContent.trim());t.querySelectorAll("tbody tr").forEach(r=>{[...r.querySelectorAll("td")].forEach((td,i)=>{if(h[i])td.dataset.label=h[i]})})});</script>
```

### Responsive Breakpoints (in the `<style>` block)

```css
@media (max-width: 1200px) {
  .container { padding: 0 32px; }
}
@media (max-width: 1024px) {
  .districts-grid { grid-template-columns: repeat(2, 1fr); }
  .weather-grid { grid-template-columns: 1fr; gap: 48px; }
  .permits-grid { grid-template-columns: 1fr; }
  .nearby-grid { grid-template-columns: repeat(2, 1fr); }
  .footer-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 768px) {
  .container { padding: 0 24px; }
  section { padding: 80px 0; }
  body { font-size: 16px; }
  .nav-links, .header-cta { display: none; }
  .nav-toggle { display: flex; }
  .breadcrumb { padding: 100px 0 0; }
  .location-hero { padding: 32px 0 60px; }
  .hero-stats { flex-direction: column; gap: 16px; }
  .hero-stat { min-width: auto; }
  .hero-btns { flex-direction: column; }
  .hero-btns .btn { width: 100%; text-align: center; }
  .districts-grid { grid-template-columns: 1fr; }
  .weather-stats { grid-template-columns: 1fr 1fr; gap: 16px; }
  .faq-grid { grid-template-columns: 1fr; }
  .nearby-grid { grid-template-columns: 1fr; }
  .cta-btns { flex-direction: column; align-items: center; }
  .cta-btns .btn { width: 100%; max-width: 320px; }
  .footer-grid { grid-template-columns: 1fr; gap: 32px; }
  .footer-bottom { flex-direction: column; text-align: center; }
  /* Mobile cost table cards */
  .cost-table { box-shadow: none; min-width: 0 !important; }
  .cost-table thead { display: none; }
  .cost-table tbody { display: block; }
  .cost-table tr { display: block; padding: 20px; margin-bottom: 12px; border-radius: 10px; border-bottom: none; box-shadow: var(--shadow-sm); background: var(--white); }
  .cost-table td { display: block; padding: 4px 0; border-bottom: none; font-size: 0.95rem; }
  .cost-table td::before { content: attr(data-label); display: block; font-size: 0.7rem; font-weight: 600; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 2px; }
  .cost-table td:first-child { font-size: 1.1rem; font-weight: 700; color: var(--navy); margin-bottom: 8px; padding-bottom: 10px; border-bottom: 1px solid var(--stone); }
  .cost-table td:first-child::before { display: none; }
  .cost-table .price { font-size: 1rem; }
}
@media (max-width: 480px) {
  .weather-stats { grid-template-columns: 1fr; }
}
```

---

## STEP 3: STATE PAGE TEMPLATE

The state page at `states/[state-slug]/index.html` is a longer page (~800-1200 lines) that serves as the hub for all city pages. Structure:

1. **Head** — Same meta pattern as city pages but state-level. Title: "Commercial Roofing in [State]: Costs & Systems for [N] Cities (2026)"
2. **Header + Mobile Nav** — Same as city pages
3. **Breadcrumb** — Home > States > [State]
4. **State Hero** — H1, 4 stat cards (avg cost/sq ft, cities covered, climate zones, building code standard)
5. **State Overview** — 2-3 paragraphs about the state's commercial roofing landscape (building stock, growth areas, dominant systems)
6. **Climate & Weather section** — How the state's climate affects commercial roofing systems (navy background)
7. **Cost Overview** — State average cost table (same 7-system format as city pages, costs per sq ft)
8. **Building Codes & Energy Requirements** — State-specific IBC adoption, IECC version, ASHRAE 90.1 compliance, cool roof mandates
9. **Insurance & Wind Requirements** — FM Global ratings, special state programs, wind uplift requirements
10. **City Grid** — ALL cities organized by metro area, each as a clickable card linking to the city page. Group cities under subheadings like "Houston Metro (15 cities)", "DFW Metro (18 cities)", etc.
11. **FAQ** — 4-6 state-level FAQ questions about commercial roofing
12. **CTA section**
13. **Footer**
14. **JavaScript**

Schema: `BreadcrumbList` + `FAQPage` (same as city pages)

---

## STEP 4: UPDATE SITE-WIDE INFRASTRUCTURE

After creating all city and state pages, you MUST update these files:

### 4a. States Hub (`states/index.html`)
- Change the state's tile from `coming-soon` to `active` with the city count
- Update meta description to include the new state

### 4b. Homepage (`index.html`)
- Change the state's tile from `coming-soon` to `active` in the States Coverage grid

### 4c. ALL Existing HTML Files (bulk update)
Every `.html` file in the repo needs:
- **Mobile nav States accordion:** Add `<a href="/states/[state-slug]/">[State] ([N] cities)</a>` inside the States accordion content
- **Footer States section:** Add `<li><a href="/states/[state-slug]/">[State] ([N] cities)</a></li>` in the States list (replace "Coming soon" placeholder if it's the first state)

Use `find . -name "*.html" -exec sed ...` to bulk-update these.

### 4d. Sitemap
- Create `sitemap-[state-slug].xml` with all city page URLs + the state page URL
- Update `sitemap.xml` index to reference the new sub-sitemap

### 4e. `llms.txt`
Update the llms.txt file to add:
- The new state and all its cities in a coverage section
- State-specific cost data
- All new page URLs in the URL listing
- Update any total counts

### 4f. `llms-full.txt`
Add a new section for the state with detailed per-city data:
```
## [State] City Pages ([N])

### [Metro Area] Metro ([N] cities)

**[City], [ST]** (pop. XXX,XXX)
- Commercial districts: [Name 1], [Name 2], [Name 3], [Name 4], [Name 5]
- Known for: [1-2 sentences about commercial building stock, climate threats, notable features]
```

### 4g. `search/index.json`
Add entries for the new state page and all city pages to the search index.

---

## STEP 5: SEO & LLM OPTIMIZATION RULES

### For Google Search
- **Title tags:** 50-60 characters. Format: "Commercial Roofing in [City] [ST] | Costs, Systems & Codes (2026)"
- **Meta descriptions:** 150-160 characters. Include year, cost/sq ft range, roofing systems, and "building codes."
- **H1 tags:** Include city name, state abbreviation, year. "Commercial Roofing in [City], [ST] (2026)"
- **Internal linking:** Every city page links to its state page, 4-5 nearby city pages, relevant guide pages, and the calculator
- **Breadcrumbs:** Rendered in HTML AND in BreadcrumbList schema
- **Geo meta tags:** Include lat/long for every city
- **Freshness signals:** "Updated March 2026" badge on every page
- **Canonical URLs:** Every page has `<link rel="canonical" ...>` with trailing slash

### For LLM Citation (ChatGPT, Claude, Perplexity, Gemini)
- **Explicit data tables:** Cost-per-sq-ft tables with clear headers that LLMs can parse
- **Q&A format FAQs:** Both in HTML AND in FAQPage schema — LLMs love pulling from these
- **Specific numbers:** Always include dollar/sq ft ranges, temperatures, percentages, years
- **Source citations in content:** Reference building codes by name ("Per IBC 2021...", "ASHRAE 90.1-2022 requires...", "IECC 2024 Climate Zone 2...")
- **Structured sentences:** "Commercial roofing in [City] costs $X.XX-$X.XX per square foot installed for TPO (60 mil) on a typical 15,000 sq ft office building."
- **Year in content:** Include "2026" in titles, H1s, cost table headers, and freshness badges
- **llms.txt and llms-full.txt:** These are special files that AI crawlers read directly. Keep them comprehensive with ALL city data, ALL costs, ALL FAQs

---

## STEP 6: CONTENT QUALITY RULES

### Commercial Terminology (USE THESE)
- "building owner" / "facility manager" / "property manager" — NOT "homeowner"
- "roofing system" / "membrane" / "single-ply" — NOT "shingles"
- "per square foot installed" — NOT "total project cost for a home"
- "commercial building" / "office" / "warehouse" / "retail" — NOT "house" / "home"
- "IBC" / "IECC" / "ASHRAE 90.1" — NOT "IRC"
- "TPO, EPDM, PVC, modified bitumen, BUR, SPF, standing seam metal" — NOT "3-tab, architectural, impact-resistant"
- "NDL warranty" / "manufacturer warranty" — NOT "workmanship warranty"
- Reference NRCA, SPRI, CRRC, FM Global, UL standards

### DO:
- Use real commercial district and business park names (verify they exist)
- Use realistic cost-per-sq-ft ranges based on the regional market
- Mention real highways, geographic features, industrial corridors, and local landmarks
- Reference real building codes, energy codes, and regulations (IBC, IECC, ASHRAE)
- Make each city page feel locally researched, not templated
- Vary the FAQ questions — don't use the same 4 questions for every city
- Adjust recommended systems to the climate (TPO in sun belt, EPDM in cold, PVC near coast/restaurants, metal in hurricane zones)
- Reference how building age and type affects roofing needs (1970s office parks with BUR vs new construction with TPO)

### DO NOT:
- Use LocalBusiness or RoofingContractor schema (we are a publisher)
- Include phone numbers or contractor names
- Use residential terminology (shingles, homeowner, house, IRC)
- Use generic content that could apply to any city
- Skip the cost table or use round/identical numbers across cities
- Use the same commercial district descriptions across cities
- Forget to update ALL nav/footer references across the entire site
- Quote "total project cost" — always use per-square-foot pricing

---

## STEP 7: VERIFICATION CHECKLIST

After completing all files, verify:

- [ ] Every city page is 650+ lines and self-contained
- [ ] Every page has BreadcrumbList + FAQPage schema (and nothing else)
- [ ] Every page has correct canonical URL with trailing slash
- [ ] Every page has geo meta tags with correct lat/long
- [ ] Every mobile nav lists ALL active states with correct city counts
- [ ] Every footer lists ALL active states with correct city counts
- [ ] State page city grid lists every city with working links
- [ ] States hub and homepage have the state tile changed from coming-soon to active
- [ ] Nearby city links on each page point to real city pages that exist
- [ ] FAQ questions are city-specific, not generic
- [ ] Cost ranges are realistic per-square-foot pricing for the local market
- [ ] Commercial districts are real places with accurate descriptions
- [ ] All content uses commercial terminology — NO residential language
- [ ] All internal links use relative paths starting with /
- [ ] Sitemap includes all new URLs
- [ ] llms.txt and llms-full.txt are updated with all new data
- [ ] search/index.json includes all new pages
- [ ] Title tags are 50-60 characters
- [ ] Meta descriptions are 150-160 characters
- [ ] Year "2026" appears in titles, H1s, and freshness badges
- [ ] No LocalBusiness or RoofingContractor schema anywhere
- [ ] Cost table has 7 rows: TPO, EPDM, PVC, Mod Bit, BUR, SPF, Standing Seam Metal
- [ ] Cost table columns: System, Cost/Sq Ft, Lifespan, Best For
- [ ] Mobile cost table CSS converts table to card layout at 768px
- [ ] No page-view beacons — sendBeacon only fires from form submissions

---

## CURRENT SITE STATUS (as of March 2026)

- **Active states:** 0 (all states show "Coming soon")
- **Guide pages:** 14 (TPO, EPDM, PVC, Mod Bit, BUR, SPF, Metal, Cost, Maintenance, Coatings, Cool Roofs, Inspections, Warranties, Green Roofs)
- **Total pages:** ~25 HTML files (guides + utility pages)
- **States with pages:** 0 (you're building the first one!)

When you add the first state:
- Replace the footer "Coming soon — expanding nationwide" placeholder with the actual state link
- Update the mobile nav States accordion to include the state link
- The states hub and homepage just need the tile changed from `coming-soon` to `active`

---

## EXAMPLE: Adding a First State (e.g., Texas)

If building Texas:
1. Research 50-80 TX cities (Houston metro, DFW metro, Austin, San Antonio, El Paso, etc.)
2. Create `states/texas/index.html` (state page)
3. Create `states/texas/houston/index.html`, `states/texas/dallas/index.html`, etc.
4. TX-specific: mention TWIA wind insurance, IECC 2015 adoption (behind national), extreme heat + TPO dominance, hail belt in DFW/Panhandle (impact-resistant systems), hurricane coast (metal + PVC), massive warehouse/distribution corridor along I-35/I-10
5. Update ALL ~25 existing HTML files with new nav/footer entries
6. Create `sitemap-texas.xml`, update `sitemap.xml`
7. Update llms.txt, llms-full.txt, search/index.json

---

## FILE NAMING CONVENTIONS

- State slugs: lowercase, hyphenated → `new-jersey`, `new-york`, `north-carolina`
- City slugs: lowercase, hyphenated → `jersey-city`, `cherry-hill`, `atlantic-city`
- Every page is `index.html` inside its directory
- Trailing slashes on all canonical URLs

---

## APPENDIX A: EXACT SITEMAP FORMAT

### Sitemap Index (`sitemap.xml`)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap><loc>https://commercialroofguide.com/sitemap-main.xml</loc></sitemap>
  <sitemap><loc>https://commercialroofguide.com/sitemap-guides.xml</loc></sitemap>
  <!-- ADD YOUR NEW STATE HERE -->
  <sitemap><loc>https://commercialroofguide.com/sitemap-[state-slug].xml</loc></sitemap>
</sitemapindex>
```

### State Sub-Sitemap (`sitemap-[state-slug].xml`)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://commercialroofguide.com/states/[state-slug]/</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://commercialroofguide.com/states/[state-slug]/[city-slug]/</loc>
    <changefreq>monthly</changefreq>
    <priority>0.7</priority>
  </url>
  <!-- One <url> block per city, alphabetically -->
</urlset>
```

State pages get priority `0.8`, city pages get `0.7`.

---

## APPENDIX B: EXACT llms.txt UPDATE FORMAT

When adding a new state, add these sections to `llms.txt`:

```
## [State] Commercial Roofing Data
- TPO (60 mil): $X.XX – $X.XX/sq ft
- EPDM (60 mil): $X.XX – $X.XX/sq ft
- PVC (60 mil): $X.XX – $X.XX/sq ft
- Modified Bitumen: $X.XX – $X.XX/sq ft
- Standing Seam Metal: $X.XX – $X.XX/sq ft
- [State-specific energy code or regulation info]
- [State-specific climate/insurance note]
- [N] city guides across [metro areas]
```

Add all new URLs to the "All Page URLs" section.

---

## APPENDIX C: EXACT llms-full.txt UPDATE FORMAT

Add a new section for the state with detailed per-city data:

```
## [State] City Pages ([N])

### [Metro Area #1] Metro ([N] cities)

**[City], [ST]** (pop. XXX,XXX)
- Commercial districts: [Name 1], [Name 2], [Name 3], [Name 4], [Name 5]
- Known for: [1-2 sentences — commercial building types, climate threats, notable features]

**[City 2], [ST]** (pop. XXX,XXX)
- Commercial districts: [Name 1], [Name 2], [Name 3], [Name 4], [Name 5]
- Known for: [1-2 sentences]

### [Metro Area #2] Metro ([N] cities)
...

### Other Major Cities ([N] cities)
...
```

---

## APPENDIX D: CALCULATOR UPDATE (`calculator/index.html`)

The calculator at `calculator/index.html` uses inline JavaScript with regional pricing tiers. It maps ZIP codes to regions using the first 3 digits of the ZIP code.

If your new state's pricing differs significantly from the existing regional tier it falls into, you may want to add a dedicated pricing tier.

**Current regional tiers (8 regions):**
- `northeast` — CT, MA, ME, NH, VT, RI, NY, NJ ZIP prefixes
- `midatlantic` — PA, MD, VA, DC, DE, WV ZIP prefixes
- `southeast` — GA, NC, SC, FL, AL, TN, MS, KY, LA, AR ZIP prefixes
- `midwest` — OH, IL, MI, IN, MN, WI, IA, MO, KS, NE, ND, SD, OK ZIP prefixes
- `texas` — TX ZIP prefixes 750-799
- `mountain` — CO, AZ, UT, NV, MT, WY, NM, ID, AK ZIP prefixes
- `westcoast` — CA, WA, OR, HI ZIP prefixes
- `national` — fallback for any unmatched ZIP

**To add a state-specific tier:**
1. Add a new entry in `REGIONAL_COSTS` object with pricing for: `tpo`, `epdm`, `pvc`, `modbit`, `bur`, `spf`, `metal` — each with `low`, `avg`, `high` per sq ft
2. Add ZIP prefix mapping in `getRegionFromZip()` function
3. Add a `label` property like `'Florida Pricing'`

Only add a dedicated tier if the state's costs are meaningfully different from its current regional tier.

---

## APPENDIX E: STATES HUB TILE FORMAT (`states/index.html`)

Active state tiles use this HTML format:

```html
<div class="state-tile active">
  <a href="/states/[state-slug]/">
    <h3>[State Name]</h3>
    <span class="city-count">[N] city guides</span>
    <span class="explore-arrow">Explore <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg></span>
  </a>
</div>
```

Replace the corresponding `coming-soon` tile with this `active` tile for your new state.

Coming-soon tiles look like this:
```html
<div class="state-tile coming-soon">
  <h3>[State Name]</h3>
  <span class="coming-label">Coming soon</span>
</div>
```

---

## APPENDIX F: HOMEPAGE STATE TILE UPDATE (`index.html`)

On the homepage, find the matching `coming-soon` tile in the States Coverage grid and replace it with the `active` format (same as Appendix E).

---

## APPENDIX G: LEAD CAPTURE (DO NOT CHANGE)

Lead capture fires ONLY when a user submits a form (free estimate form or calculator). The endpoint and token are:

- **Endpoint:** `https://partners.minyona.com/api/webhooks/intake`
- **Token:** `d8250591bb879e8ded29510a25cc2e32`
- **Method:** `navigator.sendBeacon()` with URLSearchParams

The free estimate form at `/free-estimate/` and calculator at `/calculator/` use this token. Do NOT create new tokens or change the endpoint.

**CRITICAL: Do NOT add page-view tracking beacons.** Never fire `sendBeacon` on page load. The beacon must ONLY fire when a user explicitly submits a form. Every beacon call creates a lead record — firing on page load creates phantom "Unknown" leads that pollute the system. No tracking scripts, no analytics beacons, no page-view pings to the intake endpoint.

---

## APPENDIX H: COMPLETE FILE TREE

```
commercialroofguide.com/
├── index.html                              ← Homepage (update state tile)
├── 404.html                                ← 404 page (update nav/footer)
├── favicon.svg                             ← No changes needed
├── robots.txt                              ← No changes needed
├── _headers                                ← No changes needed
├── sitemap.xml                             ← Add new sub-sitemap reference
├── sitemap-main.xml                        ← No changes needed
├── sitemap-guides.xml                      ← No changes needed
├── sitemap-[new-state].xml                 ← CREATE this
├── llms.txt                                ← Update with new state data
├── llms-full.txt                           ← Update with new state city details
├── CODEX-PROMPT.md                         ← This file (reference only)
├── about/index.html                        ← Update nav/footer only
├── approved/index.html                     ← Update nav/footer only
├── calculator/index.html                   ← Maybe add regional tier + update nav/footer
├── free-estimate/index.html                ← Update nav/footer only
├── thank-you/index.html                    ← Update nav/footer only
├── search/
│   ├── index.html                          ← Update nav/footer only
│   └── index.json                          ← Add new pages to search index
├── guides/
│   ├── index.html                          ← Update nav/footer only
│   ├── commercial-roof-cost/index.html     ← Update nav/footer only
│   ├── tpo-roofing/index.html              ← Update nav/footer only
│   ├── epdm-roofing/index.html             ← Update nav/footer only
│   ├── pvc-roofing/index.html              ← Update nav/footer only
│   ├── modified-bitumen/index.html         ← Update nav/footer only
│   ├── built-up-roofing/index.html         ← Update nav/footer only
│   ├── spray-foam-roofing/index.html       ← Update nav/footer only
│   ├── metal-roofing-commercial/index.html ← Update nav/footer only
│   ├── roof-maintenance/index.html         ← Update nav/footer only
│   ├── roof-coatings/index.html            ← Update nav/footer only
│   ├── cool-roofs/index.html               ← Update nav/footer only
│   ├── roof-inspections/index.html         ← Update nav/footer only
│   ├── warranties/index.html               ← Update nav/footer only
│   └── green-roofs/index.html              ← Update nav/footer only
├── states/
│   ├── index.html                          ← Update tile from coming-soon to active
│   └── [new-state]/                        ← CREATE all of this
│       ├── index.html                      ← State page
│       ├── [city-1]/index.html             ← City page
│       ├── [city-2]/index.html             ← City page
│       └── ...
```

---

## APPENDIX I: BULK UPDATE COMMANDS

To update ALL existing HTML files with the new state in nav/footer, use these sed commands (adjust for your state):

```bash
# Add new state to mobile nav States accordion content (after "All States" link)
find . -name "*.html" -exec sed -i '' 's|<a href="/states/">All States</a>|<a href="/states/">All States</a>\n      <a href="/states/[state-slug]/">[State] ([N] cities)</a>|g' {} \;

# Replace footer "Coming soon" placeholder with actual state link (first state only)
find . -name "*.html" -exec sed -i '' 's|<li style="color: rgba(255,255,255,0.5); font-size: 0.85rem; font-style: italic;">Coming soon — expanding nationwide</li>|<li><a href="/states/[state-slug]/">[State] ([N] cities)</a></li>|g' {} \;

# For subsequent states, add after existing state links:
# find . -name "*.html" -exec sed -i '' 's|<li><a href="/states/[prev-state]/">[Prev State] ([N] cities)</a></li>|<li><a href="/states/[prev-state]/">[Prev State] ([N] cities)</a></li>\n          <li><a href="/states/[state-slug]/">[State] ([N] cities)</a></li>|g' {} \;
```

**IMPORTANT:** After running these commands, verify the changes look correct by spot-checking a few files. The sed patterns may need adjustment depending on exact whitespace in the files.

---

## APPENDIX J: COMMERCIAL ROOFING REFERENCE DATA

### National Cost Benchmarks (2026, per sq ft installed)
| System | Low | Average | High |
|--------|-----|---------|------|
| TPO (60 mil) | $5.50 | $7.00 | $8.50 |
| EPDM (60 mil) | $4.50 | $6.00 | $7.50 |
| PVC (60 mil) | $6.50 | $8.25 | $10.00 |
| Modified Bitumen | $5.00 | $6.75 | $8.50 |
| Built-Up Roofing (BUR) | $6.00 | $8.00 | $10.00 |
| Spray Foam (SPF) | $5.50 | $7.50 | $9.50 |
| Standing Seam Metal | $9.00 | $12.50 | $16.00 |

### Regional Multipliers
| Region | Multiplier | States |
|--------|-----------|--------|
| Northeast | 1.15x | NY, NJ, CT, MA, ME, NH, RI, VT |
| Mid-Atlantic | 1.10x | PA, MD, VA, DC, DE, WV |
| Southeast | 0.90x | GA, FL, NC, SC, TN, AL, MS, KY, LA, AR |
| Midwest | 0.95x | OH, IL, MI, WI, MN, IN, IA, MO, KS, NE, ND, SD, OK |
| Texas | 0.95x | TX |
| Mountain West | 1.00x | CO, AZ, UT, NV, MT, WY, NM, ID |
| West Coast | 1.20x | CA, WA, OR, HI |

Apply these multipliers to national benchmarks when setting city-level pricing. Then adjust ±5-10% based on the specific city's market (urban premium, labor availability, etc.).

### Market Share (2026)
- TPO: ~40% of new commercial installations
- EPDM: ~20%
- PVC: ~10%
- Modified Bitumen: ~10%
- Metal: ~10%
- BUR: ~5%
- SPF: ~3%
- Other: ~2%

### Key Standards Referenced
- **IBC** (International Building Code) — commercial building code standard
- **IECC** (International Energy Conservation Code) — energy efficiency requirements
- **ASHRAE 90.1** — energy standard for commercial buildings
- **Title 24** — California's energy code (strictest in the nation)
- **NRCA** (National Roofing Contractors Association) — industry guidelines
- **SPRI** (Single Ply Roofing Industry) — single-ply membrane standards
- **CRRC** (Cool Roof Rating Council) — reflectivity ratings
- **FM Global** — wind uplift and fire ratings for commercial roofs
- **UL** — fire and wind resistance classifications

---

## APPENDIX K: `robots.txt`

The `robots.txt` does NOT need to change when adding new states. It already allows all crawlers site-wide:

```
User-agent: *
Allow: /
Disallow: /thank-you/

User-agent: GPTBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: Claude-Web
Allow: /

User-agent: anthropic-ai
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: Amazonbot
Allow: /

User-agent: Applebot-Extended
Allow: /

Sitemap: https://commercialroofguide.com/sitemap.xml
```

Plus references to `llms.txt` and `llms-full.txt`.

---

That's everything. Build it right, make every page feel locally researched with real commercial building data, and make it the best commercial roofing resource an LLM or Google searcher could find. Remember: this is commercial roofing — building owners and facility managers, not homeowners.
