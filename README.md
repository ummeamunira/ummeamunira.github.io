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

## About

**Umme Amunira** is a Senior Data Scientist with 10+ years in energy analytics across ATCO Gas, Suncor Energy, and the Alberta Energy Regulator. She builds end-to-end ML systems — time-series forecasting, anomaly detection, predictive optimisation — on Azure Databricks and Microsoft Fabric.

Writing weekly on energy analytics and AI at [The Energy Signal](#).

Connect on [LinkedIn](https://linkedin.com/in/uamunira).

---

*Built with zero dependencies. Deployed on GitHub Pages. Maintained by one person between a full-time job and a cross-border relocation.*
