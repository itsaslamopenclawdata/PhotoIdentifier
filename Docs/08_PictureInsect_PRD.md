# PRD: Picture Insect — Bug Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Picture Insect: Bug Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Entomology Research Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Picture Insect** is an AI-powered arthropod identification application serving entomologists, gardeners, farmers, pest control professionals, parents, and curious nature enthusiasts. With over **5.5 million described insect species** and approximately **10 quintillion individual insects on Earth**, the identification space is vast and underserved by digital tools. Beyond recreation, the app delivers critical agricultural value — helping farmers detect crop pests early and invasive species managers track new infestations before they become economic disasters.

**Proposed Brand Name:** EntomIQ

---

## 3. Problem Statement

- Insect identification requires specialised entomological expertise — there are fewer than 10,000 professional entomologists worldwide to serve a global citizen population.
- Invasive species cause **$70 billion+ in agricultural damage annually** in the US alone; early digital detection tools could significantly reduce this.
- No web-based app combines visual species identification + pest risk assessment + citizen science reporting + educational gamification in one accessible platform.
- Agricultural extension services lack real-time field data from farmers about pest pressure in their area.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 70,000 | 700,000 |
| Insects Identified / Day | 30,000 | 250,000 |
| Identification Accuracy | ≥ 90% (order); ≥ 80% (species) | ≥ 95% (order); ≥ 88% (species) |
| Citizen Science Reports | 10,000/month | 200,000/month |
| Agricultural User Segment | 15% of users | 20% of users |
| Premium Conversion | 7% | 13% |

---

## 5. Target Users & Personas

### Persona 1 — Grace, The Home Gardener
- **Age:** 52 | **Occupation:** Retired School Principal | **Location:** Georgia, USA
- **Goal:** Identify insects in her vegetable garden; know which are pests vs. beneficial.
- **Pain Points:** Google Image search is unreliable; can't tell a beneficial ground beetle from a destructive stink bug.

### Persona 2 — Ahmed, The Cotton Farmer
- **Age:** 42 | **Occupation:** Large-Scale Cotton Farmer | **Location:** Punjab, Pakistan
- **Goal:** Identify pest species affecting crops; know when to spray and with what.
- **Pain Points:** Extension officers visit quarterly; needs in-the-moment pest identification and treatment guidance.

### Persona 3 — Lily, The Curious Child (with Parent)
- **Age:** 9 | **Occupation:** Student | **Location:** Tokyo, Japan
- **Goal:** Learn about insects found in the school garden; collect points for species observed.
- **Pain Points:** Books are complex; adults have no easy tool to guide children's nature curiosity.
- **Parent Willingness to Pay:** $4.99/month for an educational, safe, engaging tool.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Identify insect/spider/arthropod from photo | Accuracy ≥ 87% at order level; ≥ 75% at species level on 200k-species test set |
| Danger Assessment | 4-level system: Harmless / Mildly Venomous / Venomous / Dangerous | Safety classification manually curated by entomologist advisors |
| Species Profile | Name, order, family, habitat, diet, geographic range | From iNaturalist / GBIF taxonomy database |
| Personal Sighting Log | Photo log with date, time, and optional GPS | Stored per-user; searchable by species/date |
| First Aid Tips | Display bite/sting first aid for venomous species | Medically reviewed; includes "seek medical attention" guidance for high-danger species |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Pest Management Advisor | Is this insect harmful to my crop/garden/home? → management options | Advice covers organic, IPM, and chemical control; dosage links to EPA/EFSA |
| Beneficial Insect Guide | Pollinators, pest predators, decomposers highlighted with "protect this" badge | Database of 200+ globally important beneficial insects |
| Geographic Distribution Map | GBIF-sourced range map per species | Interactive MapLibre GL map with observation density layer |
| Community Sighting Map | See what insects others are spotting within configurable radius | Real-time; refreshed every hour |
| Life Cycle Diagram | Egg → larva → pupa → adult with stage-specific identification tips | Illustrated for all 100 most commonly identified species |
| Lookalike Guide | Show visually similar species alongside key differentiating features | Minimum 1 lookalike shown per species identified |
| Photography Guide | In-app tips for capturing sharp macro insect photos | Illustrated guide with lighting and focus tips per device type |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Invasive Species Alert | Automatic flag when identified species is invasive in user's location | Mapped to CABI Invasive Species Compendium; geofenced alerts |
| Citizen Science Sync | Submit verified sightings to iNaturalist | Requires user confirmation; iNaturalist OAuth integration |
| Biodiversity Index | Track insect species richness in user's area over time → biodiversity score | Calculated from user's own sighting history by location |
| Pest Infestation Predictor | Multiple sightings of same pest → infestation severity estimate | K-nearest neighbors model on historical outbreak data |
| AR Overlay | Point camera at insect → floating info panel in-browser | WebXR API; field usability tested on outdoor devices |
| Agricultural Extension Integration | Direct reporting to regional agricultural authority alert systems | API connections to USDA APHIS, EU pest reporting portals |
| Kids Mode | Gamified learning: species collection, bug facts quizzes, achievement badges | COPPA compliant; no personal data collected from under-13 users |

---

## 7. User Stories & Use Cases

### Epic 1 — Quick Identification
- **US-101:** As a gardener, I want to photograph a bug on my tomato plant and know within 3 seconds if it will damage my crop.
- **US-102:** As a parent, I want to know immediately if the spider my child found is dangerous.
- **US-103:** As a farmer, I want to identify a pest I've never seen before and get treatment recommendations immediately.

### Epic 2 — Scientific & Environmental
- **US-201:** As a citizen scientist, I want to submit my sightings to iNaturalist so that I contribute to biodiversity research.
- **US-202:** As an educator, I want my students to track which insects they discover this semester so that we build a class biodiversity report.
- **US-203:** As an environmental monitor, I want to track biodiversity in my garden over time to detect ecological changes.

### Epic 3 — Agricultural
- **US-301:** As a farmer, I want to know when pest pressure near me is increasing so that I can prepare spray schedules proactively.
- **US-302:** As an agricultural extension officer, I want farmers in my district to report pest sightings automatically to our alert dashboard.

### Epic 4 — Kids Education
- **US-401:** As a child, I want to earn badges for each new bug I discover so that exploring nature is exciting.
- **US-402:** As a teacher, I want a classroom leaderboard showing how many species each student has found.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│             EntomIQ Frontend                       │
│    Next.js 14 + TypeScript + TailwindCSS           │
│    Camera │ Geolocation │ WebXR │ PWA              │
└────────────────────┬───────────────────────────────┘
                     │ REST API
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└────┬───────────────┬───────────────┬───────────────┘
     │               │               │
┌────▼──────┐ ┌──────▼──────────┐ ┌─▼──────────────┐
│ Identify  │ │ Pest Risk       │ │ Community      │
│ Service   │ │ Advisory Svc    │ │ / Map Svc      │
│ (FastAPI) │ │ (FastAPI)       │ │ (Node.js)      │
└────┬──────┘ └─────────────────┘ └────────────────┘
     │
┌────▼──────────────────────────────────────────────┐
│  AI: EfficientNet-V2 + species classification head│
│  iNaturalist taxonomy | GBIF | CABI Invasive DB   │
│  PostgreSQL │ Redis │ S3 │ MapLibre GL tiles      │
└────────────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Species Classification | EfficientNetV2-L fine-tuned on iNaturalist insect dataset (2.7M images) |
| Danger Classification | Rule-based + human-curated expert mapping |
| Pest Risk Advisory | Decision tree trained on crop × pest × region data from CABI |
| Infestation Predictor | Gradient Boost model on historical regional outbreak density data |

---

## 9. Data Model

**InsectSpecies**
```
species_id       UUID PK
common_name      VARCHAR(200)
scientific_name  VARCHAR(200)
order_name       VARCHAR(100)
family           VARCHAR(100)
danger_level     ENUM(harmless, mild, venomous, dangerous)
is_invasive      BOOLEAN
is_beneficial    BOOLEAN
is_agricultural_pest BOOLEAN
habitat          TEXT[]
distribution     TEXT
life_cycle_stages JSONB
diet             TEXT
inaturalist_id   INTEGER
gbif_id          INTEGER
```

**Sighting**
```
sighting_id      UUID PK
user_id          UUID FK
species_id       UUID FK
latitude         DECIMAL(10,7)
longitude        DECIMAL(10,7)
photo_urls       TEXT[]
ai_confidence    DECIMAL(5,4)
submitted_to_inaturalist BOOLEAN
spotted_at       TIMESTAMP
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Response
{
  "species_id": "uuid",
  "common_name": "Spotted Lanternfly",
  "scientific_name": "Lycorma delicatula",
  "confidence": 0.94,
  "order": "Hemiptera",
  "danger_level": "harmless_to_humans",
  "is_invasive": true,
  "INVASIVE_ALERT": {
    "message": "This is an INVASIVE species in your region. Please report to authorities.",
    "report_url": "https://www.aphis.usda.gov/slf-report"
  },
  "is_agricultural_pest": true,
  "pest_risk": {
    "crops_affected": ["grapes", "apples", "hops", "peaches"],
    "severity": "HIGH",
    "management_options": ["Contact USDA APHIS", "Sticky band traps", "Insecticidal soap spray"]
  }
}
```

---

## 11. UI/UX Requirements

### Screens
1. **Identify Screen** — Camera with "stabilise and hold" guidance overlay
2. **Species Result** — Danger badge, invasive alert banner, pest risk panel, life cycle illustrated
3. **My Sightings** — Map + list view; biodiversity score widget
4. **Community Map** — Regional sighting heatmap; filter by date/species/danger
5. **Pest Management Hub** — Search by crop → pest list; treatment cards
6. **Kids Mode** — Mascot-guided simplified UI; collection binder; badge wall
7. **Citizen Science** — iNaturalist submission queue with verification step

### Design System
- **Font:** Nunito (kids mode) / Inter (adult mode)
- **Color:** Leaf Green `#4CAF50` primary; Safety Orange `#FF9800` for pest alerts; Red for invasive species
- **Kids Mode:** High contrast, large text, animated mascot guide, achievement confetti
- **AR Mode:** Semi-transparent panel floating above live camera feed

---

## 12. Security & Compliance

- **Kids Mode (COPPA):** No account required in Kids Mode; no personal data collected; no social features
- All community sightings associated with pseudonymous user IDs on public map
- Invasive species reports trigger a legally compliant notification chain to relevant authority APIs
- Rate limits: Free (30 IDs/day), Premium (unlimited), Agricultural Enterprise (API access)

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| iNaturalist API | Insect taxonomy + citizen science submission |
| GBIF | Global biodiversity data and range maps |
| CABI Invasive Species Compendium | Invasive species detection data |
| USDA APHIS | US agricultural pest reporting |
| EPPO (EU Plant Protection) | EU pest notification network |
| MapLibre GL | Community sighting maps |
| WebXR Device API | AR species overlay |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Species identification ≤ 3 seconds; map loads < 1.5 seconds |
| **Accuracy** | ≥ 90% correct order, ≥ 80% correct species on 200k species test set |
| **Kids Mode Safety** | Zero personal data retention for COPPA-protected users |
| **Availability** | 99.9% uptime |
| **Offline** | Top-500 agricultural pest profiles downloadable for offline use |
| **Localization** | 10 languages; pest management advice regionally adapted |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Photo identification (200,000 species)
- Danger assessment
- Bite/sting first aid
- Personal sighting log
- Basic species profiles

### Phase 2 — Enhanced (Month 4–7)
- Pest management advisor
- Beneficial insect guide
- Community sighting map
- Invasive species alerting
- Citizen science (iNaturalist)

### Phase 3 — Advanced (Month 8–14)
- Biodiversity index tracker
- AR species overlay
- Kids Mode gamification
- Agricultural extension API integration
- Infestation predictor
- Premium and Agricultural Enterprise tiers

---

*Document Version 1.0 — Picture Insect PRD — PhotoIdentifier Platform | 2026-02-21*
