# ummeamunira.github.io

Personal site and practitioner platform for **Umme Amunira** — Senior Data Scientist specialising in energy analytics and ML systems.

Live at → [ummeamunira.com](https://ummeamunira.com)

---

## What This Site Is

A no-dependency, single-file static site built for three purposes that run in parallel:

1. **Establish technical credibility** with hiring managers and peers in the energy data science space
2. **Generate side income** through DS interview prep products and fractional consulting
3. **Plant the foundation** for a forecasting-as-a-service startup targeting mid-market gas distribution utilities

The design philosophy: dark, technical, minimal. No frameworks. No build step. No CMS. One `index.html` file that deploys in seconds and loads instantly anywhere.

---

## Site Structure

The site has 6 modules, each serving a distinct purpose:

| Module | URL | Purpose |
|--------|-----|---------|
| Home | `/` | Identity, trust signals, navigation |
| Writing | `/writing` (SPA tab) | Thought leadership — energy analytics & ML |
| Interview Prep | `/prep` (SPA tab) | Free + paid DS interview prep with live SQL sandbox |
| Projects | `/projects` (SPA tab) | ML portfolio — energy domain, production constraints |
| Consulting | `/consulting` (SPA tab) | Fractional DS engagements for energy companies |
| Building | `/building` (SPA tab) | Startup thesis — forecasting infrastructure for utilities |

Navigation is handled client-side via JavaScript tab switching. The site is a single-page application contained entirely in `index.html` — no routing library required.

---

## Tech Stack

| Layer | Tool | Why |
|-------|------|-----|
| Markup | HTML5 | No build step, instant deploy |
| Styling | CSS3 (custom properties, grid, flexbox) | Full control, zero dependencies |
| Interactivity | Vanilla JavaScript | No framework overhead |
| Fonts | Google Fonts CDN | Syne · JetBrains Mono · Fraunces |
| Hosting | GitHub Pages | Free, fast, version-controlled |
| Newsletter | Beehiiv (embed) | Email list — The Energy Signal |
| Products | Gumroad (overlay) | Interview prep digital products |
| Booking | Calendly (embed) | Coaching and consulting sessions |
| Forms | Formspree | Consulting inquiry → email |
| SQL Sandbox | SQLiteOnline.com (iframe) | Live SQL practice environment |

No npm. No node_modules. No webpack. No React. The entire site is one file.

---

## Interview Prep Module

The prep module implements a free/paid tier model with a live SQL practice environment.

### Free Tier
- Questions 1–3: open access, no signup
- Questions 4–10: unlocked after email capture (feeds Beehiiv list tagged `interview-prep-free`)
- Live SQL sandbox with 4 preloaded tables: `orders`, `order_items`, `customers`, `products`
- Synthetic retail dataset — e-commerce/sales domain, ~50 rows per table
- Each question includes: difficulty badge, concept tags, hint toggle, full solution toggle

### Paid Tier (4 tracks)
| Track | Content | Price |
|-------|---------|-------|
| SQL Mastery | 100 questions, energy domain tables, concept index | $39 CAD |
| A/B Testing & Causal Inference | Experiment design, uplift modeling, 40 problems | $49 CAD |
| DS Interview Playbook | ML fundamentals, system design, 60-page PDF | $69 CAD |
| Data Architecture for DS | Medallion architecture, pipeline patterns, templates | $59 CAD |

### 1:1 Coaching
| Session | Duration | Price |
|---------|----------|-------|
| Interview Audit | 30 min mock + written feedback | $75 CAD |
| Full Prep Session | 60 min deep dive | $150 CAD |
| 3-Session Package | Full interview arc | $350 CAD |

---

## SQL Practice Dataset

The sandbox uses a synthetic retail dataset. Schema:

```sql
-- Orders
CREATE TABLE orders (
  order_id     TEXT PRIMARY KEY,
  customer_id  TEXT,
  order_date   DATE,
  region       TEXT,
  sales_rep_id TEXT,
  status       TEXT
);

-- Order Items
CREATE TABLE order_items (
  item_id    TEXT PRIMARY KEY,
  order_id   TEXT,
  product_id TEXT,
  quantity   INTEGER,
  unit_price REAL,
  discount   REAL
);

-- Customers
CREATE TABLE customers (
  customer_id TEXT PRIMARY KEY,
  name        TEXT,
  segment     TEXT,
  city        TEXT,
  country     TEXT,
  join_date   DATE
);

-- Products
CREATE TABLE products (
  product_id  TEXT PRIMARY KEY,
  name        TEXT,
  category    TEXT,
  subcategory TEXT,
  cost_price  REAL
);
```

Concepts covered across 10 free questions: `GROUP BY`, `ORDER BY`, `JOIN`, `DATE_TRUNC`, `WINDOW FUNCTIONS`, `LAG`, `ROLLING AVERAGE`, `NOT EXISTS`, `CTE`, `ANOMALY DETECTION PATTERN`.

---

## Third-Party Integration Points

Each integration is a placeholder in the current build. Replace with your live credentials before launch:

### Beehiiv (Newsletter)
Find all three newsletter form instances and replace with your Beehiiv embed code:
```html
<!-- Replace this input + button pair with your Beehiiv embed -->
<input type="email" placeholder="your@email.com" id="nl-home">
<button class="btn" onclick="handleSubscribe('nl-home')">Subscribe →</button>
```
Get embed code: Beehiiv dashboard → Grow → Forms → Embed

### Formspree (Contact Form)
Add your Formspree endpoint to the consulting form:
```html
<!-- Change the form tag to: -->
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```
Setup: formspree.io → New form → copy endpoint

### Gumroad (Products)
Replace each product button's `onclick` with a Gumroad overlay call:
```html
<!-- Replace onclick with: -->
<a href="https://gumroad.com/l/YOUR_PRODUCT_ID" class="gumroad-button">Get Track 01</a>
```
Add Gumroad's script tag once in the `<head>`:
```html
<script src="https://gumroad.com/js/gumroad.js"></script>
```

### Calendly (Booking)
Replace coaching and consulting booking buttons with your Calendly inline embed:
```html
<!-- Replace button with Calendly inline widget -->
<div class="calendly-inline-widget"
  data-url="https://calendly.com/YOUR_USERNAME/session-name"
  style="min-width:320px;height:630px;">
</div>
<script src="https://assets.calendly.com/assets/external-widget.js"></script>
```

### SQLiteOnline Sandbox
Replace the sandbox link with your pre-configured session URL:
```html
<!-- Update href to your pre-loaded SQLiteOnline session -->
<a href="https://sqliteonline.com/#YOUR_SESSION" target="_blank">
```

---

## Local Development

No build tools required. Open directly in a browser:

```bash
# Clone the repo
git clone https://github.com/yourusername/yourusername.github.io.git
cd yourusername.github.io

# Open in browser — pick any of these
open index.html                        # macOS
start index.html                       # Windows
python -m http.server 8000             # any OS — then visit localhost:8000
npx serve .                            # if you have Node installed
```

Python local server is recommended if you're testing form embeds or iframes — some embed providers block `file://` protocol.

---

## Deployment

This site deploys automatically via GitHub Pages on every push to `main`.

### First-time setup
1. Create a repo named `yourusername.github.io`
2. Push `index.html` and `README.md` to `main`
3. Go to repo **Settings → Pages → Source → Deploy from branch → main → / (root)**
4. Your site is live at `https://yourusername.github.io` within 1–3 minutes

### Custom domain setup
1. Buy domain (Namecheap or Google Domains)
2. Add DNS A records pointing to GitHub Pages IPs:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
3. Add CNAME record: `www` → `yourusername.github.io`
4. In repo Settings → Pages → Custom domain → enter your domain → Save
5. Enable **Enforce HTTPS** once available (up to 24 hours for DNS propagation)

### Making changes
```bash
# Edit index.html locally
# Then push to deploy

git add index.html
git commit -m "Update consulting pricing"
git push origin main

# Live within ~60 seconds
```

---

## Content Roadmap

Planned additions tracked here as the LinkedIn content calendar progresses:

- [ ] Week 1 article: *You're Measuring Forecast Accuracy Wrong*
- [ ] Week 6: Streamlit app embed — Load Forecast Error Explorer
- [ ] Month 2: Gas anomaly detection project writeup
- [ ] Month 2: Forecasting benchmark comparison notebook (GitHub link)
- [ ] Month 3: Energy data pipeline template repo
- [ ] Month 3: Energy domain SQL tables added to paid prep track
- [ ] Month 4: Consulting inquiry form connected to Formspree
- [ ] Month 6: Beehiiv newsletter fully connected across all signup points

---

## Design System

```css
/* Color palette */
--bg:           #080810   /* near black background */
--bg2:          #0e0e1a   /* section backgrounds */
--bg3:          #141422   /* card hover states */
--card:         #0f0f1e   /* card backgrounds */
--border:       #1e1e35   /* all borders */
--cyan:         #00e5cc   /* primary accent */
--purple:       #9b6dff   /* secondary accent */
--gold:         #f0c040   /* intermediate difficulty */
--text:         #c8c8e0   /* body text */
--text-dim:     #6b6b90   /* secondary text */
--text-bright:  #eeeef8   /* headings */

/* Typography */
--font-display: 'Syne', sans-serif          /* headings, nav, prices */
--font-mono:    'JetBrains Mono', monospace /* body, labels, code */
--font-body:    'Fraunces', serif           /* taglines, italics */
```

---

## About

**Umme Amunira** is a Senior Data Scientist with 10+ years in energy analytics across ATCO Gas, Suncor Energy, and the Alberta Energy Regulator. She builds end-to-end ML systems — time-series forecasting, anomaly detection, predictive optimisation — on Azure Databricks and Microsoft Fabric.

Writing weekly on energy analytics and AI at [The Energy Signal](#).

Connect on [LinkedIn](https://linkedin.com/in/uamunira).

---

*Built with zero dependencies. Deployed on GitHub Pages. Maintained by one person between a full-time job and a cross-border relocation.*
