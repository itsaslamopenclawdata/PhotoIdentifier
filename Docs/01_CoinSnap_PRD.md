# PRD: Coin Snap — AI Coin Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Coin Snap: AI Coin Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Legal Counsel |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Coin Snap** is an AI-powered numismatic identification and portfolio management web application within the PhotoIdentifier Super Web Application platform. Users photograph any coin — ancient, modern, world, or commemorative — and instantly receive the coin's identity, historical context, rarity classification, and real-time market valuation.

The global coin collecting market exceeds **$10 billion USD annually**, yet no dominant web-based AI tool exists for the casual collector. Coin Snap targets this underserved gap by combining computer vision, numismatic databases, and live auction feeds to serve collectors at all levels — from children finding coins in their grandparents' jars to serious investors managing six-figure numismatic portfolios.

**Proposed Brand Name:** CoinLens AI

---

## 3. Problem Statement

### Current Pain Points
- Coin collectors must manually cross-reference printed catalogues (Red Book, Standard Catalog of World Coins) to identify finds — a slow, expert-gated process.
- Existing apps are mobile-only, have limited species databases, and lack live market data.
- Counterfeit coins are prevalent; amateur collectors lose money buying fakes without expert verification tools.
- Portfolio valuation requires manual price lookups across multiple marketplace sources (eBay, Heritage Auctions, PCGS Price Guide).

### Market Opportunity
- 140 million+ global coin collectors (professional to casual).
- Growing youth interest in "coin roll hunting" drives new user acquisition.
- Numismatic investment as an alternative asset class grew 23% YoY in 2024.

---

## 4. Goals & Success Metrics

### Business Goals
- Capture 2% of active online coin collectors within 18 months of launch.
- Generate recurring revenue through freemium subscription and marketplace transaction fees.
- Achieve App Store / platform ratings of 4.7+ stars.

### Key Performance Indicators (KPIs)

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users (MAU) | 50,000 | 500,000 |
| Coins Identified per Day | 20,000 | 200,000 |
| Identification Accuracy | ≥ 92% | ≥ 97% |
| Subscription Conversion Rate | 5% | 12% |
| Marketplace GMV / Month | $50,000 | $1,000,000 |
| Avg. Session Duration | 4 min | 7 min |

### OKRs (Quarter 1 Post-Launch)
- **O1:** Establish Coin Snap as the most-used web-based coin identifier.
  - KR: 100,000 coins identified in first 90 days.
  - KR: Featured in 3 numismatic publications.
- **O2:** Build a defensible coin database moat.
  - KR: 500,000+ coin variants in database by launch.
  - KR: Partner with PCGS and NGC for data feeds.

---

## 5. Target Users & Personas

### Persona 1 — Marcus, The Enthusiast Collector (Primary)
- **Age:** 45 | **Occupation:** Accountant | **Location:** Midwest USA
- **Goal:** Identify and value coins from estate sales and coin shows quickly.
- **Pain Points:** Spends hours with reference books; frequently unsure if a coin is genuine.
- **Tech Comfort:** Moderate — uses smartphone and web browser daily.
- **Willingness to Pay:** $9.99/month for premium features.

### Persona 2 — Aisha, The Curious Discoverer (Secondary)
- **Age:** 22 | **Occupation:** University Student | **Location:** London, UK
- **Goal:** Identify old coins found while traveling and understand their history.
- **Pain Points:** No background in numismatics; wants instant answers.
- **Tech Comfort:** High — power user of web apps.
- **Willingness to Pay:** Free tier user; may upgrade for collection tracking.

### Persona 3 — David, The Professional Dealer (Tertiary)
- **Age:** 57 | **Occupation:** Coin Dealer | **Location:** New York, USA
- **Goal:** Quickly assess customer walk-in inventory, detect fakes, estimate lot value.
- **Pain Points:** Needs fast, accurate appraisals at scale; existing tools are too slow.
- **Tech Comfort:** Low-to-moderate — needs a simple, fast interface.
- **Willingness to Pay:** $49.99/month for business-tier plan.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Image Capture | Upload photo or use live camera to capture coin | Supports JPEG, PNG, HEIC; min 512×512px resolution |
| AI Coin Recognition | Identify coin by country, denomination, year, mint mark | Accuracy ≥ 90% on test set of 10,000 world coins |
| Coin Info Display | Show name, country, year, material, ruler/figure on coin | All fields populated within 3 seconds of image submission |
| Rarity Rating | 4-tier system: Common / Uncommon / Rare / Very Rare | Rating sourced from mint population data |
| Collection Save | User can save identified coin to personal collection | Saved to user account; visible in Collection Manager |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Live Market Valuation | Real-time price from PCGS, NGC, eBay sold listings | Price refreshes hourly; sourced from ≥ 3 data providers |
| Coin Grading Assistant | Display Sheldon grading scale (1–70) with condition tips | Grading guide displays images of each grade level for comparison |
| Collection Manager | Organize coins by country, era, denomination, value | Sorting and filtering works across all dimensions |
| Historical Context | Series timeline, rulers, minting history | Minimum 100-word historical note per coin type |
| Barcode/QR Scan | Scan PCGS/NGC slab barcodes to auto-identify graded coins | Barcode scan resolves coin to database entry in < 2 seconds |
| Wishlist/Trade Board | Users can list coins they want or are willing to trade | Trade listings visible to all logged-in users |
| Search & Filter DB | Search 500,000+ world coins by any attribute | Search returns results in < 1 second |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Multi-Angle Grading AI | Submit obverse + reverse photos → AI estimates Sheldon grade | Grading prediction within ±3 points of professional grade 80% of the time |
| Counterfeit Detection | Micro-texture and weight-ratio analysis flags potential fakes | False positive rate < 2%; tested on verified fake dataset |
| Price Trend Charts | 12-month auction price history graph per coin | Charts powered by Heritage Auctions + eBay sold listings API |
| AR Metadata Overlay | Point camera at coin → overlay shows floating data in browser | Works via WebXR API in supported browsers (Chrome, Safari) |
| Community Marketplace | Bid/offer interface for peer-to-peer coin sales | Escrow payment system integrated; dispute resolution workflow defined |
| Expert Appraisal Request | Submit coin for paid remote appraisal by certified numismatist | Response within 72 hours; expert network of ≥ 50 certified numismatists |
| Portfolio Dashboard | Total collection value with gain/loss tracking vs. purchase price | Daily valuation update; exportable as PDF/CSV |

---

## 7. User Stories & Use Cases

### Epic 1 — Coin Identification
- **US-101:** As a collector, I want to photograph a coin and receive its identity in under 3 seconds so that I can quickly assess a find.
- **US-102:** As a dealer, I want to scan a graded slab barcode so that I can instantly retrieve that coin's PCGS population data.
- **US-103:** As a new user, I want to see the rarity of my coin so that I understand if it has collector value.

### Epic 2 — Valuation & Grading
- **US-201:** As an investor, I want to see real-time market prices from multiple sources so that I can make informed buy/sell decisions.
- **US-202:** As a seller, I want an AI grade prediction before sending to PSA/NGC so that I can decide whether grading is worthwhile.
- **US-203:** As a collector, I want to see price trend charts so that I can identify coins whose value is rising.

### Epic 3 — Collection Management
- **US-301:** As a collector, I want to organize my collection by country and era so that I can see my portfolio at a glance.
- **US-302:** As a portfolio investor, I want daily valuation updates so that I can track my asset performance.
- **US-303:** As a dealer, I want to export my inventory as a CSV so that I can use it in external accounting tools.

### Epic 4 — Community & Marketplace
- **US-401:** As a collector, I want to list coins I'm willing to trade so that I can grow my collection without spending cash.
- **US-402:** As a buyer, I want to bid on coins in an auction format so that I can acquire rare coins at fair market value.
- **US-403:** As a user uncertain about a coin, I want to request a paid expert appraisal so that I get a certified opinion.

---

## 8. Technical Architecture

### System Overview

```
┌─────────────────────────────────────────────────────┐
│                  CoinSnap Frontend                   │
│         Next.js 14 + TypeScript + TailwindCSS        │
│   Camera API │ WebXR (AR) │ PWA Service Worker       │
└──────────────────────┬──────────────────────────────┘
                       │ HTTPS / REST / WebSocket
┌──────────────────────▼──────────────────────────────┐
│               API Gateway (Kong / AWS API GW)        │
└──────────┬──────────────┬──────────────┬────────────┘
           │              │              │
┌──────────▼───┐ ┌────────▼──────┐ ┌───▼────────────┐
│  Identify    │ │  Valuation    │ │  Marketplace   │
│  Service     │ │  Service      │ │  Service       │
│  (Python/    │ │  (Node.js)    │ │  (Node.js)     │
│  FastAPI)    │ └──────┬────────┘ └────────────────┘
└──────┬───────┘        │
       │                │
┌──────▼───────┐ ┌──────▼──────────────┐
│  AI Engine   │ │  Pricing Aggregator │
│  (CNN Model  │ │  PCGS / NGC / eBay  │
│  + Google    │ │  Heritage Auctions  │
│  Vision API) │ │  API Connectors     │
└──────┬───────┘ └─────────────────────┘
       │
┌──────▼───────────────────────────────┐
│  PostgreSQL (coins, users, collections) │
│  Redis (session cache, price cache)    │
│  Pinecone (visual similarity search)   │
│  AWS S3 / Cloudinary (image storage)  │
└────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Primary Identification Model | Custom Fine-tuned EfficientNet-B4 (trained on 500k+ coin images) |
| Visual Similarity Search | Pinecone vector DB with CLIP embeddings |
| Counterfeit Detection | Separate anomaly-detection CNN (texture analysis) |
| Multi-angle Grading AI | ResNet-50 ensemble with confidence scoring |
| OCR (date/mint marks) | Google Vision API + Tesseract |

### Tech Stack
| Layer | Technology |
|---|---|
| Frontend | Next.js 14, TypeScript, TailwindCSS, WebXR |
| Backend Services | FastAPI (Python 3.12), Node.js 20 (microservices) |
| AI Inference | TensorFlow Serving, Google Cloud AI Platform |
| Database | PostgreSQL 16, Redis 7, Pinecone |
| Media Storage | AWS S3 + CloudFront CDN |
| Auth | Supabase Auth (JWT + OAuth2) |
| Deployment | Docker + Kubernetes (GKE) |
| Messaging | Apache Kafka (marketplace events) |
| Monitoring | Datadog, Sentry |

---

## 9. Data Model

### Core Entities

**Coin**
```
coin_id          UUID PK
name             VARCHAR(200)
country          VARCHAR(100)
denomination     VARCHAR(100)
year_from        INTEGER
year_to          INTEGER
mint_mark        VARCHAR(10)
material         VARCHAR(100)
weight_grams     DECIMAL(8,4)
diameter_mm      DECIMAL(6,2)
edge_type        VARCHAR(50)
rarity_tier      ENUM(common, uncommon, rare, very_rare)
series_id        UUID FK → CoinSeries
obverse_image_url TEXT
reverse_image_url TEXT
created_at       TIMESTAMP
updated_at       TIMESTAMP
```

**UserCollection**
```
collection_id    UUID PK
user_id          UUID FK → Users
coin_id          UUID FK → Coins
condition_grade  INTEGER (1–70 Sheldon scale)
purchase_price   DECIMAL(12,2)
purchase_date    DATE
notes            TEXT
images           TEXT[] (array of S3 URLs)
is_for_sale      BOOLEAN
is_for_trade     BOOLEAN
created_at       TIMESTAMP
```

**CoinPriceHistory**
```
price_id         UUID PK
coin_id          UUID FK → Coins
source           VARCHAR(50) (pcgs/ngc/ebay/heritage)
grade            INTEGER
price_usd        DECIMAL(12,2)
recorded_at      TIMESTAMP
```

**MarketplaceListing**
```
listing_id       UUID PK
seller_user_id   UUID FK → Users
collection_id    UUID FK → UserCollection
listing_type     ENUM(fixed_price, auction, trade)
asking_price_usd DECIMAL(12,2)
auction_end_time TIMESTAMP
status           ENUM(active, sold, expired, cancelled)
created_at       TIMESTAMP
```

---

## 10. API Design

### Key REST Endpoints

#### POST `/api/v1/identify`
Identify a coin from an uploaded image.
```json
// Request (multipart/form-data)
{
  "image": "<binary>",
  "include_valuation": true,
  "include_history": true
}

// Response 200 OK
{
  "coin_id": "uuid",
  "confidence": 0.97,
  "name": "Morgan Silver Dollar",
  "country": "United States",
  "year": 1921,
  "denomination": "1 Dollar",
  "mint_mark": "D",
  "material": "90% Silver, 10% Copper",
  "rarity": "uncommon",
  "estimated_value_usd": 42.00,
  "grade_suggestion": "VF-30",
  "historical_summary": "...",
  "processing_time_ms": 1240
}
```

#### GET `/api/v1/coins/{coin_id}/price-history`
```json
// Response 200 OK
{
  "coin_id": "uuid",
  "data_points": [
    { "date": "2025-01-01", "price_usd": 38.50, "source": "pcgs", "grade": 30 },
    { "date": "2025-06-01", "price_usd": 41.00, "source": "ebay", "grade": 30 }
  ]
}
```

#### POST `/api/v1/collections`
Save a coin to a user's collection.

#### GET `/api/v1/collections/{user_id}`
Retrieve all coins in a user's collection with current valuations.

#### POST `/api/v1/marketplace/listings`
Create a new buy/sell/trade listing.

#### GET `/api/v1/marketplace/listings`
Query marketplace with filters (country, denomination, grade range, price range).

---

## 11. UI/UX Requirements

### Screen List
1. **Home / Dashboard** — Collection value summary, recent identifications, market movers
2. **Identify Page** — Camera capture interface with live preview and upload fallback
3. **Coin Detail Page** — Full coin profile, price history chart, grading guide
4. **Collection Manager** — Grid/list view of all owned coins; sort/filter/search
5. **Marketplace** — Browse listings; create listing; bid/buy interface
6. **Portfolio Analytics** — Value charts, gain/loss, performance vs. gold/silver
7. **Expert Appraisal** — Request form; upload multiple images; appraisal status tracker
8. **Settings** — Account, subscription, notification preferences

### Key UX Flows
**Primary Flow (Identification):**
Camera/Upload → AI Processing (spinner with estimated time) → Coin Identified Card → Add to Collection CTA / View Market Price CTA

**Design System**
- **Font:** Inter (300/500/700)
- **Primary Color:** Deep Navy `#1A2744` with Gold accent `#C9A84C`
- **Border Radius:** 12px cards, 8px buttons
- **Motion:** 200ms ease-in-out transitions; skeleton loaders for AI processing state
- **Camera UI:** Full-bleed viewfinder with coin alignment overlay ring

### Accessibility
- WCAG 2.1 AA compliant
- Screen reader support for all coin data
- High-contrast mode available

---

## 12. Security & Compliance

### Authentication & Authorization
- JWT-based session tokens (15-minute expiry + refresh tokens)
- OAuth2.0 social login: Google, Apple
- Role-based access: Free / Premium / Business / Admin
- Rate limiting: 10 identifications/hour (Free), 500/day (Premium), unlimited (Business)

### Data Privacy
- **GDPR Compliant:** Data processing agreements, right-to-erasure endpoint
- **CCPA Compliant:** Opt-out of data sale; data portability export
- Uploaded coin images are deleted from processing servers within 30 minutes; only retained if user explicitly saves to collection
- Payment data handled entirely by Stripe (PCI-DSS Level 1); no card data stored server-side

### Financial Compliance
- Marketplace transactions comply with FinCEN money service business regulations
- All transactions above $10,000 require KYC verification (AML compliance)
- Tax reporting: 1099-K issuance for US sellers above IRS thresholds

---

## 13. Integration Requirements

| Provider | Purpose | API Type |
|---|---|---|
| PCGS Price Guide | Graded coin pricing | REST API (Partner Agreement) |
| NGC Coin Explorer | Population reports, graded values | REST API (Partner Agreement) |
| eBay Finding API | Sold listing prices (market data) | REST API (OAuth2) |
| Heritage Auctions | Historical auction data | REST API |
| Numismatic News / CDN | Editorial content for historical context | RSS + REST |
| Stripe | Marketplace payments, subscriptions | REST SDK |
| Cloudinary | Image optimization, CDN delivery | SDK |
| Supabase | Auth, realtime collection sync | SDK |
| Google Maps | Coin show / dealer locator | Maps JavaScript API |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Coin identification API response ≤ 3 seconds at p95 under 1,000 concurrent requests |
| **Availability** | 99.9% uptime SLA (≤ 8.7 hours downtime/year) |
| **Scalability** | Horizontal auto-scaling on GKE; handle 10x traffic spikes during major coin show events |
| **Image Processing** | Support images up to 20MB; auto-compress and resize on upload |
| **Offline (PWA)** | Collection browsing and cached coin data must work offline |
| **Internationalization** | Support 10 languages at launch; coin names in local language where available |
| **Accessibility** | WCAG 2.1 AA; keyboard navigable; screen reader compatible |
| **Browser Support** | Chrome 110+, Safari 16+, Firefox 115+, Edge 110+ |
| **Mobile Responsive** | Fully responsive from 375px (iPhone SE) to 2560px (4K desktop) |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
**Goal:** Launch core identification and collection features.
- AI model training complete with 500k+ coin dataset
- Image capture and identification API live
- Basic coin info display (name, country, year, rarity)
- User account creation + collection save
- Freemium tier with 10 identifications/day free
- PWA installable on mobile

**Exit Criteria:** 1,000 beta users; identification accuracy ≥ 90%; p95 latency ≤ 3s.

### Phase 2 — Enhanced (Month 5–9)
**Goal:** Add market intelligence and collection management depth.
- Live market valuation (PCGS + eBay integration)
- Coin grading assistant
- Collection manager with portfolio valuation dashboard
- Price history charts
- Barcode scan for graded slabs
- Wishlist and trade board
- Premium subscription tier launch ($9.99/month)

**Exit Criteria:** 50,000 MAU; 5% subscription conversion; $50k MRR.

### Phase 3 — Advanced (Month 10–18)
**Goal:** AI superiority and marketplace launch.
- Multi-angle AI grading prediction
- Counterfeit detection module
- AR metadata overlay (WebXR)
- Full peer-to-peer marketplace with bid/offer
- Expert appraisal network launch
- Business tier for dealers ($49.99/month)
- International expansion (EU, Japan, UK focus)

**Exit Criteria:** 500,000 MAU; marketplace GMV $1M/month; counterfeit detection accuracy ≥ 98%.

---

*Document Version 1.0 — CoinSnap PRD — PhotoIdentifier Platform | 2026-02-21*
