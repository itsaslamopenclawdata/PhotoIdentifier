# PRD: CardPrismora — Sports Card Scanner
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | CardPrismora: Sports Card Scanner — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Sports Trading Card Industry Consultant |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**CardPrismora** is an AI-powered sports trading card identification, valuation, and investment management platform. Users photograph any sports card and instantly receive card identity, real-time market price from multiple sources, AI-powered grade prediction before professional grading, counterfeit/reprint detection, and investment ROI analytics.

The sports card industry underwent a dramatic revival — its market reached **$5.4 billion in 2022** and continues growing. Yet collectors and investors still rely on tedious manual lookups across eBay, PSA, and marketplace apps. CardPrismora consolidates this intelligence into one AI-first platform with features that no existing app provides — particularly AI grade prediction before sending to professional graders (a major cost-saving tool).

**Proposed Brand Name:** CardPrismora AI

---

## 3. Problem Statement

- Identifying a sports card (player, year, set, variation, parallel) requires expert knowledge — there are thousands of card sets released annually.
- Card grading (PSA/BGS submission) costs $20–$150 per card — collectors need pre-screening to avoid submitting cards that won't grade high.
- Market lookups require switching between eBay, PSA, and PWCC — no single consolidated price aggregator with trend analysis exists.
- Counterfeit and trimmed cards are rampant in the secondary market — AI detection tools can protect buyers.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 65,000 | 500,000 |
| Cards Scanned / Day | 40,000 | 350,000 |
| Recognition Accuracy | >= 90% | >= 97% |
| AI Grade Prediction Submissions | 10,000/month | 150,000/month |
| Grade Prediction Accuracy (+/-1 PSA grade) | >= 70% | >= 80% |
| Premium Conversion | 10% | 18% |
| Portfolio GMV Tracked | $10M/month | $200M/month |

---

## 5. Target Users & Personas

### Persona 1 — Kevin, The Collector/Investor
- **Age:** 32 | **Occupation:** Sales Manager | **Location:** Dallas, TX
- **Goal:** Build a valuable card portfolio; know when to buy/sell/grade for maximum ROI.
- **Pain Points:** Spends 3 hours per weekend looking up prices across multiple sites.

### Persona 2 — Jordan, The Card Show Dealer
- **Age:** 48 | **Occupation:** Full-Time Card Dealer | **Location:** Chicago, IL
- **Goal:** Rapidly price and assess condition of hundreds of cards at shows; detect fakes.
- **Pain Points:** Existing apps too slow for high-throughput dealer use cases.

### Persona 3 — Mia, The New Collector
- **Age:** 19 | **Occupation:** College Student | **Location:** Los Angeles, CA
- **Goal:** Start collecting modern rookie cards as an investment; avoid overpaying or buying fakes.
- **Pain Points:** Overwhelmed by card grading, parallels, print runs, and authentication terminology.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Card Photo Recognition | Identify: player name, year, set, card number, parallel variant | Accuracy >= 88% including parallel detection on 1M-card test scan |
| Market Price Lookup | Show current prices: raw and graded (PSA 9/10) | Price data from eBay sold listings + Comc.com |
| Sales History | Last 90 days sales price trend per card/grade | Chart shows individual sold comparables |
| Condition Self-Grading Guide | Interactive visual guide for raw card grading (1-10 PSA scale) | 10 grade levels with side-by-side example images |
| Collection Catalog | Save cards; organize by sport/player/year/set | CSV export |
| Wishlist | Add cards with target buy price; alert when available | Browser push notification |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Multi-Marketplace Price Aggregator | Aggregate prices from eBay, PWCC, MySlabs, CollX APIs | Price comparison table updated every 6 hours |
| Pop Report Viewer | PSA/BGS/SGC population report (how many graded at each tier) | Data refreshed daily |
| Rookie Card Highlighter | Flags RC (Rookie Card) designation + investment score | Investment score model based on player trajectory and SP/population data |
| Set Completion Tracker | Visual grid showing owned vs. needed cards to complete a set | Filter by year, set, sport |
| Portfolio Dashboard | Total portfolio value (raw + graded); day/week/month change % | Historical valuation based on daily price snapshot |
| Grading Submission Tracker | Log cards sent to PSA/BGS/SGC; track status; record return grade | Status stages: Submitted -> Received -> Grading -> Shipped -> Received Back |
| Duplicate Detector | Alerts when user scans a card already in collection | Match by card ID + parallel type |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI PSA Grade Predictor | Submit obverse + reverse photo -> predicted PSA grade 1-10 | +/-1 grade accuracy >= 70% on validated PSA-graded test set |
| Counterfeit / Trimmed Card Detection | Analyze print pattern, edge uniformity, ink distribution | Sensitivity >= 85% on known altered card test dataset |
| Price Trend Forecasting | ML model: predict card value direction over 30/90 days | Factored inputs: player performance, news sentiment, recent comp velocity |
| Breaking News Integration | Sports news events spike card value -> push alert to holders of affected player | Latency: < 5 minutes from news event to price alert |
| 3D Card Viewer | Zoom on serial #, holo refractor, autograph detail | PhotoSphere-style interactive viewer |
| Auction Sniping Alert | Notify when target card lists below user-defined price threshold | Scans eBay listings every 5 minutes |
| Tax Reporting Export | Generate IRS Schedule D / UK HMRC CGT report from trading history | Exports gains/losses per card; buyer/seller dates and prices |

---

## 7. User Stories & Use Cases

### Epic 1 — Card Identification
- **US-101:** As a collector, I want to scan a card to know instantly what it is, what parallel it is, and what it's worth.
- **US-102:** As a dealer at a card show, I want to scan 50 cards in an hour to price them for my case.
- **US-103:** As a new collector, I want to understand the difference between a base card and a refractor before buying.

### Epic 2 — Grading Intelligence
- **US-201:** As an investor, I want an AI grade prediction before spending $50 to send a card to PSA.
- **US-202:** As a collector, I want to track all my submitted cards and their return grades in one place.
- **US-203:** As a buyer, I want the app to tell me if a card I'm considering appears to have trimmed edges.

### Epic 3 — Investment & Portfolio
- **US-301:** As an investor, I want to see my entire portfolio's value change daily so that I can make informed trading decisions.
- **US-302:** As a seller, I want to know when news about a player spikes so that I can list my cards at the peak.
- **US-303:** As a card trader, I want to export a tax report of all my transactions at year end.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│             CardPrismora AI Frontend                  │
│    Next.js 14 + TypeScript + TailwindCSS           │
│    Camera │ PhotoSphere │ PWA                      │
└────────────────────┬───────────────────────────────┘
                     │ REST / WebSocket
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└────┬───────────────┬───────────────┬───────────────┘
     │               │               │
┌────▼──────┐ ┌──────▼──────────┐ ┌─▼──────────────┐
│ Card ID   │ │ Market Price    │ │ Grade Predict  │
│ Service   │ │ Aggregator Svc  │ │ Service (AI)   │
│ (FastAPI) │ │ (Node.js)       │ │ (FastAPI/ONNX) │
└────┬──────┘ └─────────────────┘ └────────────────┘
     │
┌────▼──────────────────────────────────────────────┐
│  AI: OCR + Card Classification CNN               │
│  Grade Prediction: Multi-input CNN (obv + rev)   │
│  News: sports RSS + NLP sentiment analysis       │
│  PostgreSQL │ Redis │ TimescaleDB │ S3           │
│  eBay API │ PWCC │ MySlabs │ PSA Pop API        │
└────────────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Card Identification | Custom CNN (ResNet-50) + OCR pipeline for text extraction (player, year, card#) |
| Grade Prediction | Multi-image ResNet-101 model trained on 500k PSA-graded card photos |
| Counterfeit Detection | Edge uniformity analysis + print pattern anomaly detector |
| Price Forecasting | LSTM model trained on 5-year eBay/PWCC price history per card |
| News -> Price Correlation | BERT sentiment model on sports news headlines |

---

## 9. Data Model

**SportCard**
```
card_id          UUID PK
player_name      VARCHAR(200)
sport            ENUM(baseball, basketball, football, hockey, soccer, other)
year             INTEGER
set_name         VARCHAR(200)
card_number      VARCHAR(50)
parallel_type    VARCHAR(100) (base, refractor, gold, prizm, etc.)
print_run        INTEGER (null = unlimited)
is_rookie_card   BOOLEAN
front_image_url  TEXT
back_image_url   TEXT
```

**UserCard**
```
user_card_id     UUID PK
user_id          UUID FK
card_id          UUID FK
raw_grade        DECIMAL(3,1)
psa_grade        INTEGER
grading_company  ENUM(PSA, BGS, SGC, IPG, ungraded)
cert_number      VARCHAR(50)
purchase_price   DECIMAL(10,2)
purchase_date    DATE
is_for_sale      BOOLEAN
asking_price     DECIMAL(10,2)
```

**PriceHistory**
```
price_id         UUID PK
card_id          UUID FK
grade            INTEGER
source           VARCHAR(50)
sale_price_usd   DECIMAL(10,2)
sale_date        DATE
platform         ENUM(ebay, pwcc, comc, goldin, other)
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Response
{
  "card_id": "uuid",
  "confidence": 0.95,
  "player": "Michael Jordan",
  "year": 1986,
  "set": "Fleer Basketball",
  "card_number": "57",
  "parallel": "Base",
  "is_rookie_card": true,
  "print_run": null,
  "market_prices": {
    "raw_average": 4200.00,
    "psa_8": 8500.00,
    "psa_9": 35000.00,
    "psa_10": 240000.00
  },
  "pop_report": {
    "psa_10": 310,
    "psa_9": 2840,
    "psa_8": 4100
  }
}
```

#### POST `/api/v1/grade-predict`
Submit front + back image -> return predicted PSA grade with confidence intervals.

#### GET `/api/v1/portfolio/{user_id}/value`
Return portfolio total value with day/week/month change and top 5 movers.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera with alignment overlay; scan history ribbon
2. **Card Detail** — Card image 3D viewer; price comparison table; pop report; price chart
3. **My Collection** — Grid view; filter by sport/player/grade; portfolio value ticker
4. **Grade Predictor** — Upload front + back images; receive AI grade with confidence
5. **Portfolio Analytics** — Value trend chart; top movers; ROI per card
6. **Grading Tracker** — Kanban-style board: Submitted -> Grading -> Returned
7. **Market Alerts** — Watchlist; price drop/spike notifications; news correlated alerts

### Design System
- **Font:** Inter (700 headers, 400 body) — sports energy aesthetic
- **Colors:**
  - Primary: Indigo `#6366F1`
  - Accent: Amber `#F59E0B`
  - Background: White `#FFFFFF`
- **Border Radius:** 12px cards, 8px buttons
- **Spacing:** 4px base unit (all multiples of 4)
- **Shadows:** 5-level shadow system
  - Level 1: `0 1px 2px rgba(0,0,0,0.05)`
  - Level 2: `0 1px 3px rgba(0,0,0,0.1), 0 1px 2px rgba(0,0,0,0.06)`
  - Level 3: `0 4px 6px rgba(0,0,0,0.1), 0 2px 4px rgba(0,0,0,0.06)`
  - Level 4: `0 10px 15px rgba(0,0,0,0.1), 0 4px 6px rgba(0,0,0,0.05)`
  - Level 5: `0 20px 25px rgba(0,0,0,0.15), 0 10px 10px rgba(0,0,0,0.04)`
- **Card Viewer:** Three.js PhotoSphere viewer — pinch/zoom on surface details; holographic parallax on refractors
- **Portfolio Chart:** Recharts area chart with interpolated daily valuation

---

## 12. Security & Compliance

- AI grade prediction: clearly labeled "AI estimate, not a professional grade" on all outputs
- Counterfeit detection: results are advisory only; legal disclaimer in ToS
- **Tax feature:** Not legal/tax advice; user responsibility confirmed at export
- Portfolio sharing: public portfolio URLs are opt-in; cards/values can be hidden
- Rate limiting: Free (20 scans/day, 5 grade predictions/month), Premium (unlimited)

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| eBay Finding API | Sold listing price data |
| PWCC Marketplace | Premium auction data |
| CollX / MySlabs API | Community price data |
| PSA Population Report | Graded card population data |
| BGS Population API | Beckett population data |
| Sports news RSS feeds | Breaking news -> price alert trigger |
| SportRadar / ESPN API | Live player stats for performance-correlated value |
| Stripe | Subscriptions |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Scan Speed** | Card identified <= 2 seconds |
| **Price Freshness** | Market prices updated every 6 hours |
| **Grade Prediction** | Response within 5 seconds |
| **Availability** | 99.9% uptime; portfolio valuation must be reliable |
| **Scalability** | Handle 10x traffic spikes during major card show weekends |
| **Offline** | Collection browsable offline; last known prices cached |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1-3)
- Card photo identification (top 5M most collected cards)
- eBay price lookup and 90-day sales history
- Self-grading guide
- Collection catalog with CSV export

### Phase 2 — Enhanced (Month 4-7)
- Multi-marketplace price aggregator
- PSA/BGS pop report viewer
- Grading submission tracker
- Portfolio value dashboard
- Premium subscription launch

### Phase 3 — Advanced (Month 8-14)
- AI PSA grade prediction
- Counterfeit/trimmed card detection
- Auction sniping alerts
- Price trend forecasting
- Sports news integration
- 3D card viewer
- Tax report export

---

*Document Version 1.0 — CardPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
