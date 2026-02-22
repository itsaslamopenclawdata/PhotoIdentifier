# PRD: AutoPrismora
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | AutoPrismora — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Automotive Industry Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**AutoPrismora** is an AI-powered automotive identification, valuation, and intelligence platform. Users photograph any car, motorcycle, truck, van, or specialty vehicle and instantly receive the make, model, year, trim, full technical specifications, current market valuation from multiple sources, open recall database status, and ownership cost analytics. The platform then deepens this data layer with AI damage estimation, stolen vehicle alerts, dealer negotiation intelligence, and an AR paint and wheel customizer.

The global used car market is valued at **$1.5 trillion annually**, and car buyers are increasingly researching digitally. Yet no single consumer-facing web app combines visual AI recognition with VIN decoding, real-time multi-source valuation, recall safety data, damage assessment, and insurance quote aggregation in one unified tool. AutoPrismora AI fills this white space for enthusiasts, buyers, fleet managers, restorers, and automotive professionals.

**Proposed Brand Name:** AutoPrismora AI

---

## 3. Problem Statement

- Used car buyers cannot determine exact trim levels, installed options, or manufacturer histories from visual inspection alone — authorized dealers exploit this knowledge asymmetry to inflate prices and conceal defects.
- AI-powered vehicle damage repair estimation is currently locked behind expensive proprietary enterprise tools (CCC, Mitchell, Audatex) not accessible to consumers — a buyer at a used car lot cannot quickly estimate damage repair cost.
- No single consumer web platform combines: vehicle recognition + VIN decode + live multi-source market value + NHTSA recall database + damage assessment + insurance quote aggregation + AR customization.
- Fleet managers managing 100+ vehicles lack a lightweight, web-based visual assessment tool — they rely on manual spreadsheets or expensive enterprise fleet SaaS tools.
- Classic and exotic car enthusiasts have no AI tool capable of identifying rare model years, limited-edition variants, and production-year specification changes purely from a photograph.

---

## 4. Goals & Success Metrics

### Business Goals
- Capture consumer automotive intelligence market with a free-to-start, premium upsell model
- Generate B2B revenue through fleet tier and developer API licensing
- Revenue sharing with insurance quote partners and dealer ad integrations

### Key Performance Indicators (KPIs)

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 80,000 | 700,000 |
| Vehicles Identified / Day | 35,000 | 300,000 |
| ID Accuracy (make/model) | ≥ 90% | ≥ 96% |
| ID Accuracy (trim level) | ≥ 75% | ≥ 88% |
| AI Damage Reports / Month | 5,000 | 100,000 |
| Insurance Quotes Sent / Month | 2,000 | 50,000 |
| Premium Conversion | 8% | 15% |
| B2B Fleet Accounts | 50 | 1,000 |
| B2B Developer API Customers | 10 | 150 |

### OKRs (Quarter 1 Post-Launch)
- **O1:** Establish AutoPrismora AI as the most data-rich consumer vehicle intelligence tool
  - KR: 1M vehicle identifications in first 90 days
  - KR: Partnership agreements with 3 insurance carriers by Month 6
- **O2:** Build a defensible fleet management B2B moat
  - KR: 50 fleet accounts (avg. 100 vehicles each) by Month 6
  - KR: SOC 2 Type II certification initiated by Year 1

---

## 5. Target Users & Personas

### Persona 1 — James, The Used Car Buyer
- **Age:** 33 | **Occupation:** Teacher | **Location:** Birmingham, UK
- **Goal:** Know the true market value and history of every car he test drives; avoid being tricked by dealers.
- **Pain Points:** Dealers give conflicting spec information; confused by trim levels; scared of hidden damage.
- **Tech Comfort:** High mobile user; comfortable with web apps.
- **Willingness to Pay:** $7.99/month if the tool saves him money on his next car purchase.

### Persona 2 — Sofia, The Car Enthusiast
- **Age:** 26 | **Occupation:** Mechanical Engineer | **Location:** Stuttgart, Germany
- **Goal:** Identify classic and exotic cars she encounters; build a wishlist; get detailed spec histories.
- **Pain Points:** Cannot identify rare limited-edition trim variants or year-specific changes from photos alone.
- **Tech Comfort:** Very high; expects polished, fast web experiences.
- **Willingness to Pay:** $9.99/month as an enthusiast tool.

### Persona 3 — Raj, The Fleet Manager
- **Age:** 48 | **Occupation:** Logistics Operations Manager | **Location:** Dubai, UAE
- **Goal:** Rapidly photograph and assess 200 fleet vehicles quarterly; track depreciation; pre-screen for damage.
- **Pain Points:** Fleet SaaS tools cost $10K+ per year; needs a flexible, low-overhead visual assessment solution.
- **Willingness to Pay:** $299/month for a 200-vehicle fleet tier.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Photograph vehicle → return make, model, year, body style, trim | Accuracy ≥ 88% make/model on 500k vehicle image test set |
| Spec Display | Engine type, displacement, horsepower, torque, fuel type, transmission, drivetrain | Sourced from NHTSA / AutoData API |
| Market Value | Current retail and private sale estimated value | KBB / MarketCheck API; updated weekly |
| Color & Trim Detection | Identify factory paint color code and trim package name | Matches to official manufacturer color codes |
| My Garage | Save identified vehicles; add mileage, purchase price | Max 50 vehicles (free), unlimited (premium) |
| Fuel Economy Display | EPA-rated MPG / WLTP range for identified vehicle | EPA Fuel Economy API; city / highway / combined |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| VIN Plate OCR Decoder | Photograph VIN plate → decode full spec and history | OCR + NHTSA VIN API; ≥ 95% accuracy on clear VIN plates |
| Vehicle Comparison | Side-by-side comparison of up to 3 vehicles | All spec fields with up/down/equal indicator per row |
| Total Cost of Ownership | Annual fuel, insurance average, depreciation, maintenance | EPA MPG + insurance industry averages + KBB depreciation |
| Open Recall Database | Does this vehicle have any active NHTSA safety recalls? | Results in < 2 seconds; cached 24 hours |
| Trim Level Differentiator | All trim levels for identified model; what each adds | AutoData / Vehicle Smart API sourced |
| Depreciation Curve | 10-year projected resale value chart | iSeeCars / MarketCheck depreciation model |
| EV Range Calculator | For electric vehicles: real-world range with weather correction | EPA range × temperature correction algorithm (based on ambient temp) |
| Maintenance Schedule | Recommended service intervals for identified vehicle | OEM-sourced via ALLDATA / Mitchell ProDemand |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Damage Assessment | Submit photos of damaged vehicle → estimated repair cost by damage zone | Within ±20% of actual estimate on validated damage test dataset |
| Stolen Vehicle Alert | Photograph license plate → cross-check against national registers | US (NICB), UK (DVLA), Australia (NEVDIS), UAE (MOI) |
| Predictive Reliability Score | Historical failure rate + reliability score per model year | Consumer Reports + JD Power annual reliability survey data |
| Dealer Negotiation AI | AI-generated negotiation talking points specific to this listing | GPT-4o with vehicle market data RAG; factors in days-on-lot, comp sales |
| AR Paint & Wheel Customizer | Live camera mode: change paint color, wheel style, body kit | WebXR + Three.js; official manufacturer color/wheel palettes |
| Insurance Quote Aggregator | Vehicle profile → 5+ insurance quotes from partner carriers | All quotes returned within 10 seconds; apply button links to carrier |
| Fleet Management Dashboard | Multi-vehicle: bulk VIN import, mileage tracking, depreciation, service schedule | Business tier; CSV upload; REST API; per-vehicle PDF condition report |
| Classic & Exotic Variant ID | Fine-grained identification for limited editions, factory options, barn finds | Specialty dataset covering 50,000+ rare US/EU/JDM variants |

---

## 7. User Stories & Use Cases

### Epic 1 — Vehicle Intelligence
- **US-101:** As a car buyer, I want to photograph a car on a dealer lot and instantly see its market value and any open safety recalls so that I can negotiate from a position of knowledge.
- **US-102:** As an enthusiast, I want to identify a rare car I see on the road — down to the specific trim, model year, and any factory options — so I can research its history.
- **US-103:** As a fleet manager, I want to photograph a vehicle and get a standardised condition report in under 30 seconds so that I can process my entire fleet in a day.

### Epic 2 — Buying Intelligence
- **US-201:** As a buyer, I want to see the total 5-year cost of ownership for this specific car so that I can compare the true cost beyond the sticker price.
- **US-202:** As a price negotiator, I want the app to generate talking points based on current market data so that I have leverage at the dealership.
- **US-203:** As a safety-focused buyer, I want to scan the VIN before test driving so that I know about any outstanding recall campaigns.

### Epic 3 — Advanced Automotive Tools
- **US-301:** As an insurance buyer, I want to photograph my car and receive 5 competing insurance quotes within 2 minutes so that I get the best possible rate.
- **US-302:** As a car restorer, I want to digitally preview 20 different classic paint colors on my project car before committing to an expensive respray.
- **US-303:** As a worried citizen, I want to photograph a suspicious vehicle's plate and check if it appears on the stolen vehicle register.
- **US-304:** As a fleet manager, I want to bulk-import 200 VINs via CSV and receive a complete fleet value and depreciation report overnight.

---

## 8. Technical Architecture

### System Overview

```
┌────────────────────────────────────────────────────────┐
│                 AutoPrismora AI Frontend                   │
│        Next.js 14 + TypeScript + TailwindCSS           │
│  Camera API │ WebXR (AR) │ VIN OCR │ PWA Service Worker│
└──────────────────────┬─────────────────────────────────┘
                       │ HTTPS / REST / WebSocket
┌──────────────────────▼─────────────────────────────────┐
│              API Gateway (Kong + AWS API GW)           │
│        Auth | Rate Limiting | SSL | Routing            │
└──────────┬──────────────┬──────────────┬───────────────┘
           │              │              │
┌──────────▼───┐ ┌────────▼──────┐ ┌───▼──────────────┐
│  Vehicle ID  │ │  Damage Est.  │ │  VIN Decode /    │
│  Service     │ │  Service      │ │  Valuation Svc   │
│  (FastAPI    │ │  (FastAPI +   │ │  (Node.js)       │
│   Python)    │ │   ONNX)       │ │                  │
└──────┬───────┘ └──────┬────────┘ └──────────────────┘
       │                │
┌──────▼────────────────▼────────────────────────────┐
│  AI Inference Layer                                │
│  ResNet-101 (vision) | Mask R-CNN (damage)         │
│  Google Vision API (OCR) | ALPR.js (plates)        │
└────────────────────────────────────────────────────┘
       │
┌──────▼────────────────────────────────────────────┐
│  Data & External APIs                             │
│  PostgreSQL 16 | Redis 7 | AWS S3 | Three.js     │
│  NHTSA API | KBB API | MarketCheck | CarFax      │
│  NICB Stolen API | DVLA API | EPA Fuel Economy   │
│  Progressive / Geico / Direct Line (insurance)   │
└───────────────────────────────────────────────────┘
```

### AI / ML Stack

| Component | Technology |
|---|---|
| Vehicle Recognition | ResNet-101 fine-tuned on 1.5M labeled vehicle images (Stanford Cars + proprietary) |
| Trim Level Detection | Classification head added to ResNet-101 base; trained on trim-level annotated dataset |
| Classic/Exotic Variants | Dedicated specialist CNN trained on 50,000 rare model variant images |
| Damage Segmentation | Mask R-CNN for per-panel damage zone detection + severity classification |
| Repair Cost Regression | XGBoost model mapping panel × severity → repair cost estimate |
| License Plate OCR | Google Vision API + ALPR.js real-time plate reading module |
| VIN Plate OCR | Tesseract + NHTSA VIN-17 format post-processing validation |
| Color Identification | HSV color space analysis + nearest-neighbor match to manufacturer color codes |
| Dealer Negotiation AI | GPT-4o with vehicle market data RAG (days on lot, comparable sales, regional pricing) |

---

## 9. Data Model

**Vehicle**
```
vehicle_id         UUID PK
make               VARCHAR(100)
model              VARCHAR(100)
year               INTEGER
trim               VARCHAR(200)
body_style         ENUM(sedan, coupe, suv, truck, van, hatchback, convertible, wagon, motorcycle)
engine_type        ENUM(petrol, diesel, hybrid, phev, electric, hydrogen)
engine_cc          INTEGER
horsepower         INTEGER
torque_nm          INTEGER
transmission       ENUM(manual, automatic, cvt, dct, amt)
drivetrain         ENUM(fwd, rwd, awd, 4wd)
fuel_economy_mpg   DECIMAL(4,1)
wltp_range_km      INTEGER
ev_real_range_km   INTEGER
base_msrp_usd      DECIMAL(12,2)
cargo_liters       DECIMAL(6,1)
seating_capacity   INTEGER
created_at         TIMESTAMP
```

**UserGarage**
```
garage_id          UUID PK
user_id            UUID FK
vehicle_id         UUID FK
vin                VARCHAR(17)
nickname           VARCHAR(100)
purchase_price     DECIMAL(12,2)
purchase_date      DATE
current_mileage    INTEGER
annual_mileage     INTEGER
color              VARCHAR(100)
license_plate      VARCHAR(20)
insurance_expiry   DATE
next_service_date  DATE
notes              TEXT
created_at         TIMESTAMP
```

**DamageReport**
```
report_id          UUID PK
user_id            UUID FK
vehicle_id         UUID FK (nullable)
vin                VARCHAR(17)
photo_urls         TEXT[]
damage_zones       JSONB
  -- [{panel: "front_bumper", severity: "moderate", est_cost_usd: 1200}, ...]
total_repair_cost_usd DECIMAL(10,2)
confidence         DECIMAL(5,4)
generated_at       TIMESTAMP
```

**VehicleRecall**
```
recall_id          UUID PK
nhtsa_id           VARCHAR(50)
make               VARCHAR(100)
model              VARCHAR(100)
model_year_start   INTEGER
model_year_end     INTEGER
component          VARCHAR(200)
summary            TEXT
consequences       TEXT
remedy             TEXT
reported_at        DATE
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Request (multipart)
{ "image": "<binary>" }

// Response
{
  "vehicle_id": "uuid",
  "confidence": 0.93,
  "make": "BMW",
  "model": "M3",
  "year": 2023,
  "trim": "Competition xDrive",
  "body_style": "sedan",
  "engine": "3.0L Twin-Turbo Inline-6",
  "horsepower": 503,
  "torque_nm": 650,
  "transmission": "automatic",
  "drivetrain": "awd",
  "fuel_economy_mpg": { "city": 16, "highway": 23, "combined": 19 },
  "market_value": {
    "retail_usd": 79500,
    "private_usd": 76000,
    "trade_in_usd": 71000,
    "data_source": "KBB",
    "updated_at": "2026-02-21"
  },
  "open_recalls": 0,
  "depreciation_5yr_pct": 38.5,
  "total_cost_5yr_usd": 62400
}
```

#### POST `/api/v1/vin/decode`
```json
// Request
{ "vin": "WBS8M9C5XJ5K39217" }
// OR multipart with VIN plate photo

// Response: full vehicle spec + open recalls list + reported mileage history
```

#### POST `/api/v1/damage/assess`
```json
// Request (multipart, multiple angles)
{ "images": ["<binary_front>", "<binary_rear>", "<binary_side_left>"] }

// Response
{
  "damage_zones": [
    { "panel": "front_bumper", "severity": "severe", "est_cost_usd": 2800 },
    { "panel": "hood", "severity": "moderate", "est_cost_usd": 1100 },
    { "panel": "right_headlight", "severity": "severe", "est_cost_usd": 900 }
  ],
  "total_estimate_usd": 4800,
  "confidence": 0.82,
  "disclaimer": "Estimate is indicative only. Consult a licensed auto body repair shop for a binding quote."
}
```

#### GET `/api/v1/insurance/quotes?vehicle_id={id}&zip=B1+1BB&annual_mileage=12000`
Returns quotes from 5 partner carriers within 10 seconds.

#### GET `/api/v1/vehicles/{vehicle_id}/comparable-sales`
Returns last 90 days of private and dealer sales for same make/model/trim.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera viewfinder with vehicle framing guides; license plate scan mode toggle; upload from gallery option
2. **Vehicle Detail** — Hero image; make/model badge; spec table; market value card; recall status banner; comparable sales tab; depreciation chart
3. **Comparison Tool** — Choose up to 3 vehicles; side-by-side spec table; differences highlighted in color
4. **Damage Report** — Multi-photo upload; SVG vehicle outline with annotated damage zones (color-coded); cost breakdown by panel
5. **My Garage** — Vehicle tile grid; each tile shows value trend, next service date, recall alert badge
6. **AR Customizer** — Live camera mode; floating paint swatch panel; wheel style selector; real-time re-render
7. **Fleet Dashboard** (B2B) — Data table; bulk VIN import; depreciation heatmap; export to XLS/PDF
8. **Insurance Hub** — Pre-filled vehicle profile; quote comparison table; apply deeplinks

### Design System
- **Font:** Rajdhani (700 condensed headers — race-inspired authority) + Inter (body — clarity)
- **Color Palette:**
  - Carbon Black `#1A1A2E` — primary background (dark automotive theme)
  - Racing Red `#E63946` — primary CTA, recall alerts
  - Chrome Silver `#B0B0B0` — secondary UI elements
  - Electric Blue `#0077FF` — EV and tech indicators
  - Amber `#F59E0B` — warning states (minor damage, moderate recall)
- **Vehicle Spec Table:** Comparison bars show this vehicle vs. class average
- **Damage Map:** SVG car blueprint overlay; damage zones flash red/amber before settling to static color
- **AR Customizer:** Three.js WebGL renderer; paint color rendered with PBR metallic shading
- **Market Value Card:** Animated counter on price load; retail/private/trade-in displayed as range band

---

## 12. Security & Compliance

- **Stolen vehicle checks:** Terms of Service explicitly prohibit use to facilitate vehicle theft or fraud. All plate check queries rate-limited to 20/day free, 200/day premium. Anomaly detection flags bulk plate queries.
- **Damage reports:** Clearly labeled "AI estimate — not a certified appraisal." Legal advisory in ToS that reports are not admissible in insurance claims without adjuster review.
- **Insurance quote aggregation:** Compliant with GDPR Article 6 data minimization. Explicit user consent to share vehicle data with insurer partners. Opt-out preserves local data only. Stripe for payment; no card data touches platform servers.
- **Fleet data:** Enterprise tier: SOC 2 Type II audit in Year 1. Data residency in region of fleet HQ.
- **VIN data:** No speculative VIN queries. Each decode requires an associated user-submitted image or explicit VIN entry. Anti-fraud VIN query throttle.
- **GDPR/CCPA:** Full My Garage data exportable as JSON/CSV. Account deletion removes all vehicle and assessment records within 30 days.

---

## 13. Integration Requirements

| Provider | Purpose | Auth Method |
|---|---|---|
| NHTSA Vehicle API | VIN decode + open recall database | Public REST |
| KBB (Kelley Blue Book) API | Market valuation (US) | API Key |
| AutoTrader Valuation API | Market valuation (UK/EU) | API Key |
| MarketCheck API | Used car listing aggregation & comparable sales | API Key |
| iSeeCars API | Depreciation curve data | API Key |
| NICB API | US stolen vehicle register | Vetted API partner |
| DVLA Vehicle Enquiry API | UK stolen vehicle and MOT check | API Key |
| EPA Fuel Economy API | Official MPG ratings | Public REST |
| ALLDATA (Mitchell) | Maintenance schedule and service intervals | B2B License |
| Progressive / Geico | Insurance quote partner (US) | Affiliate API |
| Direct Line / Admiral | Insurance quote partner (UK) | Affiliate API |
| Google Vision API | VIN plate and license plate OCR | API Key |
| ALPR.js | Real-time browser license plate reading | OSS Library |
| Three.js + WebXR | AR paint/wheel customizer | OSS Library |
| Stripe | Subscription + B2B billing | OAuth + Webhook |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Vehicle identification ≤ 2.5 seconds p95; VIN decode ≤ 1.5 seconds; damage report ≤ 8 seconds |
| **Insurance Quotes** | All 5 quotes returned within 10 seconds via parallel async requests |
| **AR Customizer** | WebGL render at 30+ FPS on MacBook Pro M1 / modern Windows laptop |
| **Recall Lookup** | < 2 seconds; NHTSA results cached 24 hours per VIN |
| **Availability** | 99.9% uptime; My Garage browsable offline with cached vehicle data |
| **Scalability** | Auto-scale AI inference pods; support 50,000 concurrent identifications during peak hours |
| **Data Freshness** | Market valuation refreshed weekly; comparable sales refreshed daily |
| **Fleet Batch** | Process 1,000-vehicle VIN batch overnight report in < 60 minutes |
| **Localization** | 8 languages; mph/kph, USD/GBP/EUR/AED unit toggle; right-hand/left-hand drive damage maps |
| **Accessibility** | WCAG 2.1 AA; screen reader support on all screens; keyboard-navigable comparison tool |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Vehicle photo identification (make, model, year, body style)
- Spec display (engine, horsepower, fuel type, transmission, drivetrain)
- KBB market value estimate
- EPA fuel economy display
- Color and trim detection
- My Garage (save up to 50 vehicles, free)
- Stripe subscription billing foundation

### Phase 2 — Enhanced (Month 4–7)
- VIN OCR decoder (NHTSA + plate photo scan)
- Open safety recall lookup (NHTSA)
- Vehicle comparison tool (3-way side-by-side)
- Total cost of ownership calculator
- 10-year depreciation curve
- Trim level differentiator
- EV real-world range calculator
- Maintenance schedule reminder
- Premium subscription launch ($9.99/month)
- Fleet B2B tier invite-only beta

### Phase 3 — Advanced (Month 8–14)
- AI damage assessment with per-panel repair cost estimate
- Stolen vehicle plate check (US, UK, AU)
- Dealer negotiation AI assistant (GPT-4o)
- Predictive reliability score (Consumer Reports + JD Power)
- AR paint and wheel customizer (WebXR + Three.js)
- Insurance quote aggregator (5 carriers)
- Classic and exotic variant identification specialist model
- Fleet management dashboard — general availability
- B2B developer API portal (vehicle identification as a service)

---

*Document Version 1.0 — AutoPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
