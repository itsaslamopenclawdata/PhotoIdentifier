# PRD: VinylPrismora — Scan & Value Record
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | VinylPrismora: Scan & Value Record — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Music Industry Consultant |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**VinylPrismora** is an AI-powered vinyl record identification and valuation platform. Users photograph a record label or disc, and the system returns full album metadata, pressing variant information, current collector market value, and portfolio management tools for serious collectors. The vinyl revival — with global sales exceeding **$1.7 billion in 2024** — has created an enormous new population of collectors who lack efficient digital tools to manage their collections.

VinylPrismora aims to be the definitive digital companion for vinyl enthusiasts, dealers, and casual thrift-shop diggers alike.

**Proposed Brand Name:** VinylIQ

---

## 3. Problem Statement

- Existing vinyl cataloging apps are clunky, slow, and have poor image recognition for label identification.
- Collectors rely on Discogs — a powerful but complex database-focused platform not designed for casual use.
- No existing tool combines visual label recognition + audio fingerprinting + live market price in one web-based interface.
- Many valuable first-pressings go unidentified because collectors cannot distinguish them from common reissues.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 30,000 | 250,000 |
| Records Scanned / Day | 15,000 | 120,000 |
| Label Recognition Accuracy | >= 88% | >= 96% |
| Premium Conversion Rate | 6% | 14% |
| Marketplace GMV / Month | $20,000 | $500,000 |

---

## 5. Target Users & Personas

### Persona 1 — Greg, The Serious Collector
- **Age:** 38 | **Occupation:** Graphic Designer | **Location:** Portland, OR
- **Goal:** Catalog his 1,200-record collection with accurate valuations to know what to insure.
- **Pain Points:** Manually entering records into Discogs takes hours; often unsure about pressing variants.

### Persona 2 — Sofia, The Thrift Hunter
- **Age:** 26 | **Occupation:** Barista + DJ | **Location:** Berlin, Germany
- **Goal:** Scan records at flea markets to instantly know if they're worth buying.
- **Pain Points:** No fast, mobile-friendly tool for on-the-spot identification while digging.

### Persona 3 — Ray, The Vinyl Dealer
- **Age:** 55 | **Occupation:** Record Store Owner | **Location:** Nashville, TN
- **Goal:** Quickly assess estate sale lots; identify rare pressings; price inventory accurately.
- **Pain Points:** Employs staff time for what should be an automated task.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Label Photo Recognition | Scan record label -> return album metadata | Accuracy >= 85% on test set of 20,000 record labels |
| Metadata Return | Artist, album, year, label name, catalog number, tracklist | All fields populated from MusicBrainz / Discogs DB |
| Condition Input | User rates condition: M / NM / VG+ / VG / G | Condition stored per record in collection |
| Collection Catalog | Save records to personal collection with cover art | Cover art fetched from Last.fm / MusicBrainz image API |
| Streaming Preview | Link to Spotify / Apple Music to preview tracks | Opens streaming service in new tab |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Live Discogs Pricing | Real-time market price from Discogs API | Price refreshes every 6 hours; shows low/median/high sold |
| Collection Value Dashboard | Total portfolio value with breakdown by artist/genre | Value calculated from median Discogs sold price x condition modifier |
| Pressing Variant Detection | Identify 1st press vs. reissue from label visual cues | Accuracy >= 80% on 1st press vs. common reissue sets |
| Barcode Scan | Scan barcode for instant identification of modern pressings | Resolves to catalog entry in < 2 seconds |
| Sales History Chart | Graph of average sold prices over 24 months | Sourced from Discogs sold history API |
| Duplicate Alert | Warns when adding a record already in collection | Match on exact catalog number; alert shown before save |
| Wishlist / Have-it/Want-it | Toggle records as owned or desired | Wishlist visible; shareable via public link |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Audio Fingerprinting | Hum or play record -> identify via acoustic fingerprint | Uses ACRCloud API; accuracy >= 90% on clean audio |
| Price Trend Forecasting | ML model predicts price trajectory over next 6 months | Trend model retrained weekly on Discogs sold data |
| Direct Listing to Discogs/eBay | Create listing on external marketplace from within app | OAuth-linked; listing live within 30 seconds |
| Community Trading Hub | Peer-to-peer record trade/sell marketplace within platform | User ratings and trust scores visible |
| Rarity Alerts | Push notification when a wishlist record appears at target price | Alert latency < 5 minutes from new Discogs listing |
| Unlabeled Record AI | Identify records with no visible label using disc grooves/artwork | Separate model; accuracy >= 70% on unlabeled test set |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification
- **US-101:** As a digger, I want to photograph a record label and get album details instantly so that I can decide if it's worth buying.
- **US-102:** As a collector, I want to know if a record is a first pressing so that I don't pay reissue prices for originals.
- **US-103:** As a DJ, I want to hum a melody to find what record it's on so that I can source it for my set.

### Epic 2 — Valuation
- **US-201:** As a seller, I want to see what a record sold for on Discogs last month so that I price it fairly.
- **US-202:** As an investor, I want price trend forecasts so that I know which artists are appreciating in value.
- **US-203:** As an insurer, I want my entire collection valued instantly so that I can file for adequate coverage.

### Epic 3 — Collection Management
- **US-301:** As a collector, I want to see my entire collection organized by artist and label so that I can manage it efficiently.
- **US-302:** As a dealer, I want to export my inventory to a CSV so that I can use it in my accounting system.

---

## 8. Technical Architecture

```
┌──────────────────────────────────────────────┐
│            VinylPrismora Frontend                │
│     Next.js 14 + TypeScript + TailwindCSS    │
│     Camera API │ Audio API │ PWA             │
└─────────────────────┬────────────────────────┘
                      │ REST API
┌─────────────────────▼────────────────────────┐
│     API Gateway (Kong / AWS API Gateway)      │
└─────┬──────────────┬──────────────┬──────────┘
      │              │              │
┌─────▼─────┐ ┌──────▼──────┐ ┌───▼──────────┐
│ Identify  │ │ Valuation   │ │ Audio        │
│ Service   │ │ Service     │ │ Fingerprint  │
│ (FastAPI) │ │ (Node.js)   │ │ Service      │
└─────┬─────┘ └──────┬──────┘ └──────────────┘
      │              │
┌─────▼──────────────▼─────────────────────┐
│  PostgreSQL + Redis + Pinecone            │
│  Discogs API | MusicBrainz | ACRCloud     │
│  AWS S3 (cover art cache)                │
└───────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Label Recognition | Custom CNN (ResNet-50) fine-tuned on 300k record label images |
| Pressing Variant Detection | Visual attribute classifier; trained on Discogs pressing data |
| Audio Fingerprinting | ACRCloud API (industry standard) |
| Price Forecasting | Facebook Prophet time-series model on Discogs sold price history |
| OCR | Google Vision API for artist/title/catalog text extraction |

---

## 9. Data Model

**Record**
```
record_id        UUID PK
discogs_id       INTEGER (foreign key reference)
artist           VARCHAR(300)
album_title      VARCHAR(300)
label            VARCHAR(200)
catalog_number   VARCHAR(100)
year             INTEGER
country          VARCHAR(100)
genre            VARCHAR(100)
format           ENUM(LP, EP, Single, 10inch, 7inch)
cover_art_url    TEXT
created_at       TIMESTAMP
```

**UserRecord**
```
user_record_id   UUID PK
user_id          UUID FK
record_id        UUID FK
condition        ENUM(M, NM, VG_PLUS, VG, G_PLUS, G)
purchase_price   DECIMAL(10,2)
purchase_date    DATE
notes            TEXT
is_for_sale      BOOLEAN
is_for_trade     BOOLEAN
asking_price     DECIMAL(10,2)
created_at       TIMESTAMP
```

**PriceHistory**
```
price_id         UUID PK
record_id        UUID FK
condition        ENUM
price_usd        DECIMAL(10,2)
sold_date        DATE
source           VARCHAR(50)
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Request (multipart)
{ "image": "<binary>", "type": "label" }

// Response
{
  "record_id": "uuid",
  "confidence": 0.94,
  "artist": "Miles Davis",
  "album": "Kind of Blue",
  "year": 1959,
  "label": "Columbia",
  "catalog_number": "CL 1355",
  "pressing": "US Original Mono 1st Press",
  "market_value": { "low": 180, "median": 280, "high": 420 },
  "condition_modifiers": { "NM": 1.0, "VG+": 0.75, "VG": 0.50 }
}
```

#### POST `/api/v1/audio/fingerprint`
Submit audio clip; returns matched record metadata.

#### GET `/api/v1/records/{record_id}/price-history`
Returns 24-month price history with condition filter.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Page** — Camera/upload + audio fingerprint tabs; real-time viewfinder
2. **Record Detail** — Album art, metadata, pressing info, price history chart
3. **My Collection** — Grid/list view; filter by genre/era/condition/value
4. **Portfolio Dashboard** — Total value, top 10 most valuable records, value change graph
5. **Marketplace** — List records for sale/trade; browse community listings
6. **Wishlist** — Records wanted; price alert settings

### Design System

#### Typography
- **Font Family:** Inter for all text (headings, body, UI elements)
- **Font Weights:** 400 (regular), 500 (medium), 600 (semibold), 700 (bold)
- **Line Heights:** 1.5 for body text, 1.2 for headings
- **Sizes:** 12px (small), 14px (base), 16px (body), 18px (large), 24px (h3), 32px (h2), 40px (h1)

#### Color Palette
| Category | Token | Value | Usage |
|---|---|---|---|
| **Primary** | `--color-primary` | Indigo #6366F1 | Main CTAs, links, active states |
| **Primary Hover** | `--color-primary-hover` | #4F46E5 | CTA hover states |
| **Secondary** | `--color-secondary` | #8B5CF6 | Secondary actions, badges |
| **Background** | `--color-bg` | White #FFFFFF | Main backgrounds, cards |
| **Background Alt** | `--color-bg-alt` | Light Gray #F9FAFB | Section backgrounds, surfaces |
| **Text Primary** | `--color-text` | #111827 | Headings, body text |
| **Text Secondary** | `--color-text-muted` | #6B7280 | Labels, secondary info |
| **Border** | `--color-border` | #E5E7EB | Dividers, borders |
| **Success** | `--color-success` | #10B981 | Positive states, growth |
| **Warning** | `--color-warning` | #F59E0B | Alerts, pending states |
| **Error** | `--color-error` | #EF4444 | Errors, destructive actions |

#### Border Radius
- **Cards:** 12px
- **Buttons:** 8px
- **Inputs:** 8px
- **Badges/Pills:** 999px (fully rounded)
- **Modals/Dialogs:** 16px

#### Spacing (4px base unit)
| Token | Value | Usage |
|---|---|---|
| `--spacing-1` | 4px | Tight spacing, icon gaps |
| `--spacing-2` | 8px | Small padding, button padding |
| `--spacing-3` | 12px | Card inner padding, form gaps |
| `--spacing-4` | 16px | Standard padding, section spacing |
| `--spacing-6` | 24px | Large padding, container gaps |
| `--spacing-8` | 32px | Section margins, large gaps |
| `--spacing-12` | 48px | Page-level spacing |

#### Shadow System
| Level | Token | Value | Usage |
|---|---|---|---|
| 1 | `--shadow-sm` | 0 1px 2px rgba(0,0,0,0.05) | Subtle elevation, inputs |
| 2 | `--shadow-md` | 0 4px 6px -1px rgba(0,0,0,0.1) | Cards, buttons |
| 3 | `--shadow-lg` | 0 10px 15px -3px rgba(0,0,0,0.1) | Dropdowns, popovers |
| 4 | `--shadow-xl` | 0 20px 25px -5px rgba(0,0,0,0.1) | Modals, panels |
| 5 | `--shadow-2xl` | 0 25px 50px -12px rgba(0,0,0,0.25) | High elevation, focus states |

#### Component Specifications
- **Cards:** White background, 12px border radius, shadow-md on hover
- **Buttons:** Indigo primary, 8px border radius, medium font weight, 8px vertical padding
- **Album Art:** Prominently displayed with condition badge overlay (top-right corner)
- **Sound Visualization:** Waveform animation during audio fingerprinting
- **Price Charts:** Indigo line with gradient fill under curve
- **Condition Badges:** Pill-shaped, color-coded (M=green, NM=blue, VG+=yellow, VG=orange, G=red)

---

## 12. Security & Compliance

- OAuth2 for Discogs and eBay seller API integrations
- Marketplace payments via Stripe; no financial data stored server-side
- GDPR: data export and deletion portal
- Rate limiting: Free (20 scans/day), Premium (500 scans/day), Business (unlimited)
- Copyright: No audio playback hosted; linking only to licensed streaming services

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| Discogs API | Record database, market pricing, listing creation |
| MusicBrainz | Open music metadata database |
| ACRCloud | Audio fingerprinting engine |
| Spotify API | Track preview links |
| Apple Music API | Track preview links |
| eBay Trading API | Direct listing creation |
| Last.fm | Album cover art API |
| Stripe | Marketplace payments |
| Facebook Prophet | Price trend forecasting model |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Label identification response <= 3 seconds at p95 |
| **Audio Fingerprint** | Audio match returned <= 5 seconds for 10-second clip |
| **Availability** | 99.9% uptime; offline browsing of saved collection |
| **Scalability** | Support 5,000 concurrent scan sessions |
| **Data Sync** | Discogs price data refreshed every 6 hours |
| **Internationalization** | 8 languages; prices shown in user's local currency |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1-3)
- Label photo recognition (top 50,000 most-collected records)
- Collection catalog with cover art
- Discogs price lookup via manual catalog number entry
- Free tier: 20 scans/day

### Phase 2 — Enhanced (Month 4-7)
- Live Discogs pricing integration with condition modifiers
- Pressing variant detection
- Barcode scan
- Portfolio value dashboard
- Wishlist with basic price alerts

### Phase 3 — Advanced (Month 8-14)
- Audio fingerprinting
- Community marketplace with ratings
- Price trend forecasting
- Direct eBay/Discogs listing integration
- Dealer/Business tier

---

*Document Version 1.0 — VinylPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
