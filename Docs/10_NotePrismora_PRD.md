# PRD: NotePrismora — Banknote Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | NotePrismora: Banknote Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Numismatics & Finance Compliance Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**NotePrismora** is an AI-powered banknote identification, authentication, and collector portfolio management platform. Users photograph any banknote from any country and receive instant identification, exchange rate lookup, authentication guidance, cultural/historical context, and collector market valuation. The app serves three distinct segments: **travelers** needing exchange rate intelligence, **currency collectors** (notaphilists) managing portfolios, and **businesses** needing counterfeit detection tools.

Counterfeit currency causes **$80 million+ in losses annually** in the US alone. Globally, the numismatic currency collection market exceeds $3 billion. NotePrismora uniquely addresses both the safety/verification need and the collector hobby market in one unified platform.

**Proposed Brand Name:** NotePrismora

---

## 3. Problem Statement

- Travelers receiving foreign currency cannot easily verify notes or understand denominations in unfamiliar scripts.
- Currency collectors rely on static printed catalogues (Pick World Paper Money) with no real-time valuation data.
- Small businesses and market traders lack affordable tools to detect counterfeit notes.
- No single platform combines photo-based note recognition + counterfeit detection + collector portfolio + exchange rate tracking.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 35,000 | 280,000 |
| Banknotes Identified / Day | 12,000 | 100,000 |
| Recognition Accuracy | ≥ 90% | ≥ 97% |
| Counterfeit Detection Accuracy | ≥ 88% | ≥ 95% |
| Premium Conversion | 6% | 12% |
| Business Tier Customers | 200 | 3,000 |

---

## 5. Target Users & Personas

### Persona 1 — Sarah, The Frequent Traveler
- **Age:** 34 | **Occupation:** Consultant | **Location:** Global traveler
- **Goal:** Quickly understand foreign currency received; avoid getting shortchanged.
- **Pain Points:** Cannot read Arabic/Thai/Chinese numerals on notes; no quick exchange tool.

### Persona 2 — Victor, The Notaphilist Collector
- **Age:** 58 | **Occupation:** Retired Bank Manager | **Location:** Paris, France
- **Goal:** Catalog complete 20th century collection; track values vs. purchase prices.
- **Pain Points:** Valuation requires checking multiple auction houses; catalogue books outdated.

### Persona 3 — Rita, The Market Trader
- **Age:** 45 | **Occupation:** Market Stall Owner | **Location:** Lagos, Nigeria
- **Goal:** Detect counterfeit notes before accepting them in transactions.
- **Pain Points:** UV lamp is the only tool she has; doesn't know all the security features of every note.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Photograph note → return country, denomination, currency, year series | Accuracy ≥ 88% on 10,000-note test set across 190+ countries |
| Denomination Display | Show value in user's local currency at live exchange rate | Exchange rate updated hourly from Open Exchange Rates API |
| Authentication Guide | Display key security features specific to identified note | Features: watermark, security thread, microprint, color-shifting ink |
| Collection Catalog | Save identified notes to personal collection | Condition (UNC/EF/VF/F/VG/G) stored per note |
| Historical Context | Brief history of the note's issuing era and imagery | 100+ word description per note series |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Security Feature Checklist | Interactive checklist: tap each feature as verified | Checklist tailored per specific note series |
| Collector Valuation | Out-of-circulation note estimated value for collectors | Data from PMG Price Guide and Heritage Auctions |
| Series Set Tracker | Which notes are needed to complete a full set for a given country/era | Visual grid showing owned vs. missing notes in series |
| Currency Gain/Loss Calculator | Enter amount and purchase date → see FX gain/loss | Historical FX data from OANDA API |
| Polymer vs. Paper Filter | Categorize collection by printing substrate | Filter in collection manager |
| Travel Wallet | Multi-currency live value dashboard for active travelers | Shows up to 10 currencies simultaneously; sortable |
| Note Variant Tracking | Track design variants within same denomination | Year/series/signature variety differentiation |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Counterfeit Detection | Texture, ink distribution, and color analysis to flag suspect notes | False positive rate < 3%; sensitivity ≥ 92% on verified fake dataset |
| UV Light Simulation | Phone flashlight + camera exposure analysis simulates UV feature check | Experimental; supplementary to physical verification; disclaimer displayed |
| Digital Authentication Certificate | Generate PDF cert for authenticated collector notes | QR-code verifiable certificate; stored on platform |
| Auction Portfolio Tracker | Track banknote auction results on Stack's Bowers, Spink & Son | Portfolio performance dashboard with price trend charts |
| Expert Appraisal | Remote appraisal by certified notaphilist from IBNS member list | Response within 5 business days; paid service |
| AR Historical Overlay | Point camera at note → AR overlay shows historical scene related to note design | WebXR; educational mode |
| NFT Certificate (Optional) | Issue blockchain-verifiable ownership certificate for rare notes | Optional paid feature; Ethereum / Polygon smart contract |

---

## 7. User Stories & Use Cases

### Epic 1 — Travel & Exchange
- **US-101:** As a traveler, I want to photograph a foreign banknote to see its value in my home currency instantly.
- **US-102:** As a traveler, I want to see the key security features of a note I've received so that I can verify it's genuine.
- **US-103:** As a tourist, I want a wallet showing all my foreign currencies and their current combined value.

### Epic 2 — Collection Management
- **US-201:** As a notaphilist, I want to scan my entire collection and see its current total value.
- **US-202:** As a collector, I want to see which notes are missing from a complete series so that I can target my buying.
- **US-203:** As a collector, I want to track auction prices for notes in my portfolio over time.

### Epic 3 — Counterfeit Detection
- **US-301:** As a market trader, I want to scan a suspect note to get a counterfeit risk score before accepting it.
- **US-302:** As a business owner, I want a paid subscription that gives unlimited counterfeit checks per day.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│            NotePrismora Frontend                   │
│    Next.js 14 + TypeScript + TailwindCSS           │
│    Camera │ Flashlight API │ WebXR │ PWA           │
└────────────────────┬───────────────────────────────┘
                     │ REST API
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└─────┬──────────────┬──────────────────────────────┘
      │              │
┌─────▼──────┐ ┌─────▼──────────────────────────┐
│ Identify   │ │ Counterfeit Detection Service   │
│ Service    │ │ + FX Rate Service               │
│ (FastAPI)  │ │ (FastAPI)                       │
└──────┬─────┘ └────────────────────────────────┘
       │
┌──────▼──────────────────────────────────────────┐
│  AI: Custom CNN (banknote recognition)          │
│  Counterfeit: Texture anomaly detection CNN     │
│  Open Exchange Rates | OANDA FX API             │
│  PMG Price Guide | Heritage Auctions            │
│  PostgreSQL │ Redis │ S3                        │
└──────────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Banknote Recognition | Custom ResNet-50V2 trained on 200k banknote images across 190 countries |
| Counterfeit Detection | Anomaly detection CNN + texture statistical analysis |
| OCR | Google Vision API for serial number, signature, and year extraction |

---

## 9. Data Model

**Banknote**
```
note_id          UUID PK
country          VARCHAR(100)
currency_name    VARCHAR(100)
currency_code    CHAR(3)
denomination     DECIMAL(15,2)
year_series      VARCHAR(20)
polymer_or_paper ENUM(polymer, paper, hybrid)
security_features TEXT[]
front_image_url  TEXT
back_image_url   TEXT
pick_catalogue_no VARCHAR(50)
collector_value_usd DECIMAL(12,2)
```

**UserNote**
```
user_note_id     UUID PK
user_id          UUID FK
note_id          UUID FK
condition        ENUM(UNC, EF, VF, F, VG, G)
purchase_price   DECIMAL(10,2)
purchase_date    DATE
serial_number    VARCHAR(50)
certified        BOOLEAN
certification_no VARCHAR(100)
notes            TEXT
is_for_sale      BOOLEAN
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Response
{
  "note_id": "uuid",
  "confidence": 0.95,
  "country": "United Kingdom",
  "denomination": 50.00,
  "currency_code": "GBP",
  "currency_name": "Pound Sterling",
  "year_series": "2011 Series",
  "current_exchange_rate": { "to_USD": 1.27, "updated_at": "2026-02-21T14:00:00Z" },
  "value_in_usd": 63.50,
  "security_features_guide": ["Hologram strip", "Metallic thread", "Watermark portrait of Queen"],
  "collector_value_usd": null,
  "is_current_legal_tender": true
}
```

#### POST `/api/v1/counterfeit/analyze`
Submit image + metadata → receive counterfeit risk score (0–100) and flagged anomalies.

#### GET `/api/v1/collections/{user_id}/value`
Total collection value in user's preferred currency.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera viewfinder; guidance outline for flat note capture
2. **Note Result** — Country flag, denomination, exchange value, security features checklist
3. **Collection** — Grid by country flag; filter by era/denomination/condition
4. **Portfolio Dashboard** — Total value; gain/loss vs. purchase price; top 5 most valuable
5. **Counterfeit Check** — Risk score meter; flagged anomaly annotations on photo
6. **Travel Wallet** — Live multi-currency dashboard for travelers
7. **Series Tracker** — Visual set completion tracker per country/era

### Design System
- **Font:** IBM Plex Serif (headings) + IBM Plex Sans (body) — financial professionalism
- **Color:** Midnight Navy `#0F172A`, Emerald `#059669` for authentic, Crimson for suspect
- **Counterfeit Score Meter:** Traffic-light animated gauge: green → amber → red
- **Note Photography Guidance:** Animated border appears to flatten perspective distortion

---

## 12. Security & Compliance

- **Legal:** App must not assist in creating counterfeit currency — API rate limits and ToS prohibition
- **AML/FinCEN:** Platform does not process currency transactions; purely informational
- **Data:** Counterfeit check images retained for 7 days for model improvement (anonymized); user configurable
- **Business Tier:** KYB (Know Your Business) verification required for high-volume API access

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| Open Exchange Rates API | Real-time FX rates (170+ currencies) |
| OANDA API | Historical FX data for gain/loss calculation |
| PMG (Paper Money Guaranty) | Collector grade and valuation data |
| Heritage Auctions | Banknote auction history |
| Stack's Bowers | Additional auction price data |
| Google Vision API | OCR for serial numbers and signatures |
| Stripe | Subscription and business tier billing |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Note identification ≤ 3 seconds; FX lookup ≤ 500ms |
| **Accuracy** | ≥ 90% recognition; ≥ 88% counterfeit detection sensitivity |
| **FX Data Freshness** | Rates updated every 60 minutes |
| **Offline** | Collection browsable offline; last known FX rates cached |
| **Localization** | 12 languages; denominations displayed with correct locale formatting |
| **Availability** | 99.9% uptime |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Banknote identification (190+ countries)
- Live exchange rate display
- Security feature guide
- Note collection catalog

### Phase 2 — Enhanced (Month 4–7)
- Collector valuation (PMG integration)
- Series set tracker
- Travel wallet (multi-currency live view)
- Currency gain/loss calculator
- Premium subscription

### Phase 3 — Advanced (Month 8–14)
- AI counterfeit detection module
- Expert appraisal network
- AR historical overlay (WebXR)
- Auction portfolio tracker
- NFT authentication certificate
- Business tier API for merchants

---

*Document Version 1.0 — NotePrismora PRD — PhotoIdentifier Platform | 2026-02-21*
