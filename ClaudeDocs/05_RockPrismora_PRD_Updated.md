# PRD: RockPrismora — Stone ID
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | RockPrismora: Stone ID — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Geological Science Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**RockPrismora: Stone ID** is an AI-powered geological specimen identification application for rockhounds, geology students, hikers, prospectors, and gemstone collectors. Users photograph any rock, mineral, or gemstone and receive instant scientific classification, physical properties, geological formation context, Mohs hardness, geographic distribution, and commercial valuation. The global gem and mineral collecting hobby market exceeds **$6 billion annually**, and the app also serves a growing student and educational market.

**Proposed Brand Name:** GeoLens AI

---

## 3. Problem Statement

- Geology students and hobbyists carry heavy reference books into the field; there is no accurate, fast digital alternative for in-situ identification.
- No existing web app combines visual mineral identification + GPS field logging + gemstone valuation + AR terrain overlay.
- Gemstone fraud is widespread; amateur buyers cannot distinguish synthetic or treated stones from naturals without expert tools.
- Citizen science geological data is fragmented across hundreds of national survey databases with no unified interface.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 40,000 | 300,000 |
| Specimens Identified / Day | 15,000 | 100,000 |
| Identification Accuracy | >= 88% | >= 95% |
| Premium Conversion | 7% | 13% |
| University Partnerships | 5 | 40 |
| Marketplace GMV / Month | $10,000 | $200,000 |

---

## 5. Target Users & Personas

### Persona 1 — Tom, The Rockhound
- **Age:** 62 | **Occupation:** Retired Engineer | **Location:** Arizona, USA
- **Goal:** Identify minerals found during hikes in the SW desert; add to collection.
- **Pain Points:** Eyesight limits reference book use outdoors; hard to carry field guides.

### Persona 2 — Neha, The Geology Student
- **Age:** 20 | **Occupation:** BSc Geology Student | **Location:** Edinburgh, UK
- **Goal:** Identify hand specimens for lab practicals and fieldwork assessments quickly.
- **Pain Points:** Limited access to physical reference collections; exam prep requires fast identification.

### Persona 3 — Marco, The Gem Dealer
- **Age:** 44 | **Occupation:** Gemstone & Jewelry Trader | **Location:** Jaipur, India
- **Goal:** Verify stone authenticity; avoid being sold synthetic or treated stones.
- **Pain Points:** Needs lab-grade verification tools accessible in the field at gem shows.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Upload or capture specimen photo -> AI returns mineral ID | Accuracy >= 85% on 3,000-mineral test database |
| Property Display | Show: name, mineral family, crystal system, color, luster, streak, transparency | All properties from Mindat.org / RRUFF database |
| Mohs Hardness Scale | Display hardness with visual scale and comparable household reference | Interactive visual Mohs scale |
| Formation Description | Explain geological formation type (igneous/sedimentary/metamorphic) | Minimum 80-word description per specimen type |
| Field Journal | Save specimens with GPS coordinates and personal notes | GPS captured from browser Geolocation API |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Gemstone Valuation | Estimate value per carat/specimen; shows quality range | Data sourced from GemVal and JTV auction references |
| Geological Map | Interactive map showing where identified mineral type forms globally | Uses MapLibre GL; mineralogy overlay data from USGS |
| Multi-Angle Analysis | Allow 3 photos from different angles for composite identification | Accuracy improvement >= 8% over single-image baseline |
| Field Journal GPS | Log find site on map; view personal discovery history | All finds displayed on interactive map with timeline filter |
| Side-by-Side Comparison | Compare two specimens for classification differences | Compare UI shows both specimens with property diff table |
| Offline Mode | Download top 1,000 minerals for offline identification | Offline DB stored as IndexedDB in browser |
| Cleavage & Crystal Guide | Visual diagrams of cleavage planes and crystal systems | Illustrated guide with 3D crystal models (WebGL) |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Spectral Simulation | Simulate mineral spectral properties via camera color calibration | Experimental feature; accuracy caveat clearly displayed |
| AR Terrain Overlay | Point camera at rock face -> AR overlay shows probable mineral zones | Uses WebXR + geological survey raster data from USGS |
| AI Gemstone Grading | Assess clarity, inclusions, cut potential from macro photos | Grading for top 20 gemstones (diamond, ruby, sapphire, emerald, etc.) |
| Specimen Marketplace | Buy/sell/trade minerals with optional appraisal certificate | Third-party escrow payment; dispute resolution flow |
| Citizen Science Sync | Upload verified finds to global mineralogy databases | Integration with Mindat.org contributor API |
| Expert Consultation | Request remote assessment from certified gemologist | Network of 30+ FGA/GIA-certified gemologists |
| Gem Show / Mineral Fair Alerts | Notify user of events within configurable radius | Aggregates events from AGTA, GPEX, and regional calendars |

---

## 7. User Stories & Use Cases

### Epic 1 — Field Identification
- **US-101:** As a hikers, I want to photograph a rock I found and know what it is within 3 seconds.
- **US-102:** As a geology student, I want multi-angle photo analysis for difficult specimens to improve accuracy.
- **US-103:** As a field researcher, I want my finds automatically tagged with GPS coordinates so I can map my survey area.

### Epic 2 — Scientific & Educational
- **US-201:** As a student, I want to see crystal system diagrams alongside my identification so I can study the theory.
- **US-202:** As an enthusiast, I want an offline mineral database for areas without cell service.
- **US-203:** As a researcher, I want to contribute my field finds to Mindat.org directly from the app.

### Epic 3 — Commercial
- **US-301:** As a gem dealer, I want an AI grading estimate for a stone I'm considering buying at a show.
- **US-302:** As a collector, I want to sell a rare specimen through the app's marketplace with an appraisal certificate.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────┐
│             GeoLens AI Frontend                │
│    Next.js 14 + TypeScript + TailwindCSS       │
│    Camera │ Geolocation │ WebXR │ PWA          │
└──────────────────────┬─────────────────────────┘
                       │ REST API
┌──────────────────────▼─────────────────────────┐
│          API Gateway (Kong)                    │
└─────────┬─────────────┬──────────────┬─────────┘
          │             │              │
┌─────────▼───┐ ┌───────▼──────┐ ┌───▼──────────┐
│  Identify   │ │  Valuation   │ │  Mapping     │
│  Service    │ │  Service     │ │  Service     │
│  (FastAPI)  │ │  (Node.js)   │ │  (Node.js)   │
└──────┬──────┘ └──────────────┘ └──────────────┘
       │
┌──────▼──────────────────────────────────────┐
│  AI Engine: ResNet-101 + Mineral CNN        │
│  Mindat.org API | RRUFF Database            │
│  USGS Geological Survey API                 │
└──────────────────────────────────────────────┘
       │
┌──────▼──────────────────────────────────────┐
│  PostgreSQL │ Redis │ S3 (specimen photos)  │
└──────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Mineral Identification | Custom ResNet-101 trained on RockNet dataset (87,000 specimens) |
| Gemstone Grading | Specialized CNN for inclusions, clarity assessment (macro photo input) |
| Spectral Simulation | Color calibration algorithm using known white balance reference |
| Multi-angle Fusion | Ensemble voting across 3 image predictions |

---

## 9. Data Model

**MineralSpecimen**
```
mineral_id       UUID PK
name             VARCHAR(200)
chemical_formula VARCHAR(100)
mineral_class    VARCHAR(100)
crystal_system   ENUM(cubic, hexagonal, tetragonal, orthorhombic, monoclinic, triclinic, amorphous)
mohs_hardness    DECIMAL(3,1)
specific_gravity DECIMAL(5,2)
luster           VARCHAR(100)
streak_color     VARCHAR(100)
cleavage         VARCHAR(100)
fracture         VARCHAR(100)
transparency     ENUM(transparent, translucent, opaque)
geological_type  ENUM(igneous, sedimentary, metamorphic, meteorite)
common_locations TEXT
description      TEXT
is_gemstone      BOOLEAN
value_per_carat_usd DECIMAL(10,2)
```

**FieldFind**
```
find_id          UUID PK
user_id          UUID FK
mineral_id       UUID FK
latitude         DECIMAL(10,7)
longitude        DECIMAL(10,7)
elevation_m      INTEGER
photo_urls       TEXT[]
notes            TEXT
found_at         TIMESTAMP
is_public        BOOLEAN
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Request (multipart)
{ "image": "<binary>", "num_angles": 1 }

// Response
{
  "mineral_id": "uuid",
  "name": "Amethyst",
  "confidence": 0.93,
  "chemical_formula": "SiO₂",
  "mohs_hardness": 7.0,
  "crystal_system": "hexagonal",
  "luster": "vitreous",
  "geological_type": "igneous",
  "is_gemstone": true,
  "estimated_value_per_carat_usd": 2.50,
  "description": "Amethyst is a violet variety of quartz used in jewelry...",
  "common_locations": ["Brazil", "Uruguay", "Zambia", "South Korea"]
}
```

#### GET `/api/v1/minerals/{mineral_id}/map-data`
Returns GeoJSON of worldwide formation sites for overlaying on geological map.

#### POST `/api/v1/field-journal`
Save a new find with GPS, photos, and notes.

---

## 11. UI/UX Requirements

### Screens
1. **Identify Screen** — Camera/upload; multi-angle upload tabs
2. **Specimen Detail** — Scientific properties, value estimate, geological map, 3D crystal model
3. **Field Journal** — Map view of personal finds; timeline filter
4. **Mineral Gallery** — Searchable database browser with filtering
5. **Gem Grading** — Upload macro gems; receive clarity/cut potential assessment
6. **Marketplace** — List/browse/buy specimens
7. **Expert Consultation** — Request form + appraisal status tracker

### Design System

#### Typography
- **Font Family:** Inter (all text — headings, body, UI elements)
- **Font Weights:** 400 (regular), 500 (medium), 600 (semibold), 700 (bold)
- **Line Height:** 1.5 for body text, 1.2 for headings
- **Letter Spacing:** -0.01em for headings, 0 for body text

#### Color Palette
- **Primary:** Indigo `#6366F1`
- **Primary Hover:** `#4F46E5`
- **Primary Light:** `#818CF8`
- **Secondary:** Slate `#64748B`
- **Background:** White `#FFFFFF` and Light Gray `#F9FAFB`
- **Surface:** White `#FFFFFF`
- **Text Primary:** `#111827`
- **Text Secondary:** `#6B7280`
- **Border:** `#E5E7EB`
- **Success:** Emerald `#10B981`
- **Warning:** Amber `#F59E0B`
- **Error:** Rose `#F43F5E`
- **Info:** Sky `#0EA5E9`

#### Border Radius
- **Cards:** 12px
- **Buttons:** 8px
- **Input Fields:** 8px
- **Modals/Dialogs:** 16px
- **Pills/Badges:** 9999px (fully rounded)

#### Spacing System
- **Base Unit:** 4px
- **Scale:** 4px, 8px, 12px, 16px, 20px, 24px, 32px, 40px, 48px, 64px
- **Section Padding:** 48px vertical
- **Card Padding:** 24px
- **Button Padding:** 12px horizontal, 8px vertical (small), 16px horizontal, 12px vertical (medium)

#### Shadow System
- **Shadow XS:** `0 1px 2px 0 rgb(0 0 0 / 0.05)`
- **Shadow SM:** `0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)`
- **Shadow MD:** `0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)`
- **Shadow LG:** `0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)`
- **Shadow XL:** `0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)`

#### Component Standards
- **3D Crystal Models:** Three.js WebGL viewer embedded in specimen detail card
- **Cards:** White background, 12px border-radius, shadow-md on hover
- **Buttons:** 8px border-radius, primary indigo background, white text
- **Inputs:** 8px border-radius, border-gray-200, focus ring with indigo

---

## 12. Security & Compliance

- Public geological field data (GPS finds marked public) attributed to user; private by default
- Gemstone appraisal certificates stored on-chain (optional NFT certificate minting for collectors)
- Marketplace: Stripe payments; KYC for sellers above $1,000/month threshold
- **Educational license tier:** Universities get bulk seat access with LDAP/SSO integration

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| Mindat.org API | Comprehensive mineral database |
| RRUFF Database | Raman spectroscopy reference data |
| USGS National Geological Map | Geological map layer data |
| GemVal API | Gemstone valuation estimates |
| MapLibre GL | Interactive geological mapping |
| Three.js | 3D crystal system models |
| WebXR Device API | AR terrain overlay |
| Stripe | Payment processing |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Identification response <= 3 seconds; geological map tiles load < 1 second |
| **Offline** | Top 1,000 mineral profiles cached via IndexedDB for offline use |
| **Availability** | 99.9% uptime; offline mode for field use |
| **3D Models** | Crystal model renders within 2 seconds on mid-range hardware |
| **Localization** | 6 languages at launch; mineral names in Latin/scientific notation universally |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Photo identification (3,000 minerals/rocks)
- Property display (hardness, formation, luster, streak)
- Field journal with GPS
- Personal collection catalog

### Phase 2 — Enhanced (Month 5–8)
- Gemstone valuation
- Multi-angle analysis
- Geological map with specimen distribution
- Offline mode (top 1,000 minerals)
- 3D crystal system models

### Phase 3 — Advanced (Month 9–15)
- AR terrain overlay (WebXR)
- AI gemstone grading
- Specimen marketplace
- Expert consultation network
- Citizen science Mindat.org integration
- University/educational licensing portal

---

*Document Version 1.0 — RockPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
