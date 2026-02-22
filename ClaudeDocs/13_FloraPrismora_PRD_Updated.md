# PRD: FloraPrismora
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | FloraPrismora — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Botanist / Horticulture Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**FloraPrismora** is an AI-powered botanical identification and garden management platform serving home gardeners, hikers, botanists, farmers, parents, and nature enthusiasts. Users photograph any plant, flower, tree, shrub, or succulent and immediately receive the species name, care instructions, toxicity warnings, medicinal uses, propagation guides, and seasonal care calendars.

The global plant identification app market is estimated at **$400M+ annually**, growing rapidly alongside the houseplant boom driven by younger demographics. FloraPrismora differentiates by combining the world's largest plant database (400,000+ species) with AI garden design, disease diagnosis, smart home water system integration, and a medicinal ethnobotanical knowledge layer.

**Proposed Brand Name:** FloraLens AI

---

## 3. Problem Statement

- Plant owners lose plants regularly due to incorrect care — overwatering, wrong light, wrong soil — all preventable with accurate species-specific guidance.
- Toxicity awareness is critical: 50,000+ children and pets are exposed to toxic plants annually in the US.
- No single platform combines identification + disease diagnosis + AR garden planning + smart watering integration.
- Invasive plant species are spreading rapidly with no accessible real-time citizen science reporting tool for the general public.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|
| Monthly Active Users | 200,000 | 2,000,000 |
| Plants Identified / Day | 80,000 | 700,000 |
| Identification Accuracy | >= 92% | >= 97% |
| Disease Diagnoses / Day | 20,000 | 200,000 |
| Plants in "My Garden" | 1M plants registered | 20M plants |
| Premium Conversion | 10% | 18% |
| Smart Home Integrations | 10,000 | 200,000 |

---

## 5. Target Users & Personas

### Persona 1 — Rachel, The Indoor Plant Parent
- **Age:** 29 | **Occupation:** Graphic Designer | **Location:** Brooklyn, NY
- **Goal:** Keep her 40-plant collection alive with correct watering and light; identify market purchases.
- **Pain Points:** Keeps killing plants — no tool tells her exactly when and how much to water per species.

### Persona 2 — Carlos, The Vegetable Gardener
- **Age:** 55 | **Occupation:** Retired | **Location:** Seville, Spain
- **Goal:** Identify diseases on his tomato and pepper plants before they spread to the whole crop.
- **Pain Points:** Cannot tell early blight from septoria leaf spot; spray selection requires knowing the fungal species.

### Persona 3 — Dr. Priya, The Ethnobotanist
- **Age:** 42 | **Occupation:** University Researcher | **Location:** Pune, India
- **Goal:** Identify wild plants in the field; access medicinal/ethnobotanical data rapidly.
- **Pain Points:** No single field tool combines taxonomy + ethnobotanical database + citizen science contribution.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Photo -> plant species with common + scientific name | Accuracy >= 90% top-1; >= 97% top-3 on PlantNet test set |
| Toxicity Alert | Immediate flag: safe / toxic to pets / toxic to children / toxic to humans | Safety rating sourced from ASPCA + Poison Control databases |
| Basic Care Guide | Watering frequency, sunlight level, soil type, humidity preference | Per-species data from RHS + Missouri Botanical Garden |
| My Garden | Register plants; set custom names; browse collection | Supports unlimited plants; photo per plant |
| Watering Reminder | Push notification at user-set watering schedule per plant | Browser push + email fallback |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Disease Diagnosis | Upload leaf photo -> AI returns disease name + treatment | Accuracy >= 85% on PlantVillage disease dataset (54 classes) |
| Seasonal Care Calendar | Month-by-month guide: prune, fertilize, repot, divide | Adapts to user's climate zone (Koppen classification zone input) |
| Companion Planting Guide | Which plants grow better together / which inhibit | Database of 300 companion planting relationships |
| Soil pH & Nutrients | Display required soil pH, nitrogen/phosphorus/potassium needs | Optional soil pH meter integration (Bluetooth) |
| Invasive Species Warning | If identified species is invasive in user's location -> alert + report tool | Mapped to GBIF invasive species registry + USFS iMap Invasives |
| Propagation Guide | Methods: cuttings, seeds, division, air layering — with step-by-step | Coverage for 5,000 most popular species |
| Local Nursery Finder | Map of nearest nurseries stocking identified plant | Google Places API; filtered by plant type tags |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Plant Health Score | Upload leaf -> AI scores overall plant health 0-100 | Assesses: leaf color, spot coverage, wilting angle |
| Time-Lapse Growth Tracker | Periodic photo comparison visualizes growth over weeks/months | Side-by-side or animated transition view |
| AR Garden Planner | Point camera at garden space -> overlay chosen plants in realistic scale | WebXR; plants sized to species mature dimensions |
| Personalized Garden Designer | Input: climate zone, sun hours, space dimensions, budget -> AI generates complete planting plan | Uses species compatibility + seasonal color + size data |
| Medicinal Plant Database | Ethnobotanical uses, traditional medicine systems, preparation methods | Covers 10,000 plants with medicinal history; sourced from Dr. Duke's Phytochemical DB |
| Biodiversity Contribution | Submit sightings to iNaturalist / GBIF global databases | iNaturalist OAuth; GBIF Darwin Core submission format |
| Smart Watering Integration | Connect to Xiaomi/Govee/Gardena smart watering systems | REST API-to-device bridge via IFTTT or direct brand API |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification & Safety
- **US-101:** As a parent, I want to photograph a houseplant and know immediately if it's toxic to my child.
- **US-102:** As a hiker, I want to identify a wild flower and learn if it's edible or medicinal.
- **US-103:** As a plant shopper, I want to photograph a plant at a nursery to see the exact care requirements before buying.

### Epic 2 — Disease & Care
- **US-201:** As a vegetable gardener, I want to photograph a diseased leaf and get a fungicide or treatment recommendation.
- **US-202:** As a plant owner, I want a monthly calendar of exactly what to do for each of my plants.
- **US-203:** As a gardener, I want to know which vegetable plants I can grow together to improve yield.

### Epic 3 — Advanced Garden Management
- **US-301:** As a garden designer, I want to use AR to visualize a new plant in my garden before purchasing.
- **US-302:** As a tech-savvy plant owner, I want my smart watering system to auto-schedule based on each plant's species requirements.
- **US-303:** As a researcher, I want to search medicinal plant uses and filter by traditional medicine system (Ayurveda, TCM, etc.).

---

## 8. Technical Architecture

```
|             FloraLens AI Frontend                  |
|    Next.js 14 + TypeScript + TailwindCSS           |
|    Camera | Geolocation | WebXR | Bluetooth | PWA  |
|                     | REST API
|            API Gateway (Kong)                      |
|               |               |
| FloraPrismora  | Disease Diagnosis Service      |
| Service   | + Garden Planner AI             |
| (FastAPI) | (FastAPI / GPT-4o planning)    |
|
|  AI: PlantNet CNN + custom fine-tune              |
|  Disease: PlantVillage CNN (54-class)             |
|  PlantNet API | iNaturalist | GBIF               |
|  ASPCA Toxicity DB | Dr. Duke Phytochemical DB    |
|  PostgreSQL | Redis | S3 | Three.js (AR/3D)      |
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Plant Identification | PlantNet custom API + EfficientNet-B7 fine-tuned on 400k species dataset |
| Disease Diagnosis | PlantVillage-trained CNN (98.3% accuracy on 54 plant disease classes) |
| Health Score | Multi-metric CNN assessing color deviation, spot area, leaf geometry |
| Garden Planner | GPT-4o with plant compatibility constraint system + species data RAG |
| AR Garden Overlay | Three.js + WebXR with species-scaled 3D plant models |

---

## 9. Data Model

**PlantSpecies**
```
species_id         UUID PK
common_name        VARCHAR(200)
scientific_name    VARCHAR(200)
family             VARCHAR(100)
origin_region      VARCHAR(200)
plant_type         ENUM(tree, shrub, perennial, annual, succulent, fern, vine, aquatic)
toxicity_humans    ENUM(safe, mild, moderate, severe)
toxicity_pets      ENUM(safe, mild, moderate, severe)
toxicity_pets_type VARCHAR(100)
watering_frequency VARCHAR(100)
sunlight           ENUM(full_sun, partial_shade, full_shade)
soil_type          VARCHAR(200)
humidity_pref      ENUM(low, medium, high)
hardiness_zone_min INTEGER
hardiness_zone_max INTEGER
mature_height_cm   INTEGER
mature_spread_cm   INTEGER
bloom_months       INTEGER[]
medicinal_uses     TEXT
```

**UserPlant**
```
user_plant_id      UUID PK
user_id            UUID FK
species_id         UUID FK
nickname           VARCHAR(100)
location           VARCHAR(100)
acquired_date      DATE
pot_size_cm        INTEGER
soil_last_changed  DATE
last_repotted      DATE
watering_interval_days INTEGER
photo_url          TEXT
health_score       DECIMAL(4,1)
notes              TEXT
```

**PlantDiseaseLog**
```
log_id             UUID PK
user_plant_id      UUID FK
diagnosed_at       TIMESTAMP
disease_name       VARCHAR(200)
severity           ENUM(mild, moderate, severe)
treatment          TEXT
resolved_at        TIMESTAMP
photo_url          TEXT
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Response
{
  "species_id": "uuid",
  "common_name": "Monstera Deliciosa",
  "scientific_name": "Monstera deliciosa",
  "confidence": 0.96,
  "family": "Araceae",
  "toxicity": {
    "humans": "mild",
    "pets": "moderate",
    "pet_note": "Toxic to cats and dogs — causes oral irritation, drooling, vomiting"
  },
  "care_summary": {
    "water": "Every 7-10 days; allow top 2 inches to dry",
    "light": "Bright indirect light",
    "soil": "Well-draining peat-based mix",
    "humidity": "High (60%+)"
  },
  "is_invasive_in_user_region": false
}
```

#### POST `/api/v1/disease/diagnose`
Submit leaf photo -> returns disease name, severity, treatment, and prevention steps.

#### POST `/api/v1/garden/design`
Input: climate zone, space, sun hours, style preference -> returns AI-generated planting plan (species list with placement map).

#### POST `/api/v1/sightings`
Log GPS sighting; optionally sync to iNaturalist.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera/upload; real-time leaf scan overlay
2. **Plant Result** — Species card; toxicity badge; care summary; "Add to My Garden" CTA
3. **My Garden** — Grid of plant tiles with health indicators; watering countdown
4. **Disease Check** — Photo upload; disease result card + treatment protocol
5. **Seasonal Calendar** — Month-by-month care table per plant
6. **AR Garden Planner** — WebXR camera mode; plant placement with scale
7. **Medicinal Encyclopedia** — Search by plant or condition; traditional use cards

### Design System
- **Font:** Inter for all text — clean, modern, highly legible
- **Primary Color:** Indigo `#6366F1` — modern, trustworthy, tech-forward
- **Accent Color:** Amber `#F59E0B` — warm attention-grabbing highlight
- **Background:** White `#FFFFFF` and light gray `#F9FAFB` — clean canvas
- **Border Radius:** 12px for cards, 8px for buttons — consistent rounded aesthetic
- **Spacing:** 4px base unit (4, 8, 12, 16, 20, 24, 32, 40, 48px) — consistent rhythm
- **Shadows:** 5-level system:
  - `sm: 0 1px 2px 0 rgb(0 0 0 / 0.05)`
  - `DEFAULT: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)`
  - `md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)`
  - `lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)`
  - `xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)`
- **Toxicity Badge:** Color-coded pill: Green (safe) -> Yellow (mild) -> Orange (moderate) -> Red (severe)
- **Health Score Wheel:** Animated SVG circular gauge; color shifts green->amber->red
- **Watering Indicator:** Blue droplet fill-level animation on plant card

---

## 12. Security & Compliance

- Toxicity warnings include ASPCA and Poison Control hotline numbers
- Medicinal plant data: not medical advice disclaimer on every record
- Smart watering integration: OAuth consent required; read/write permissions explicitly shown
- GDPR/CCPA: My Garden data fully exportable as JSON/CSV

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| PlantNet API | Open-source plant identification backbone |
| iNaturalist API | Citizen science sighting submission |
| GBIF | Invasive species and distribution data |
| ASPCA Toxic Plant Database | Pet toxicity database |
| Dr. Duke's Phytochemical DB | Medicinal/ethnobotanical plant data |
| RHS Plant Finder | UK horticultural care data |
| Missouri Botanical Garden | Plant care reference data |
| Google Places API | Local nursery finder |
| Gardena smart watering API | IoT irrigation integration |
| WebXR Device API | AR garden planner |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Identification <= 2.5 seconds; disease diagnosis <= 3 seconds |
| **Database Size** | 400,000+ species at launch; updated monthly from PlantNet contributions |
| **Offline** | My Garden plant profiles and care cards cached offline |
| **Smart Home** | Watering trigger latency < 30 seconds from schedule event |
| **Availability** | 99.9% uptime |
| **Localization** | 14 languages; plant common names localized where available |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1-4)
- Plant identification (400,000 species)
- Toxicity warning (ASPCA database)
- Basic care guide per species
- My Garden with watering reminders

### Phase 2 — Enhanced (Month 5-8)
- AI disease diagnosis from leaf photo
- Seasonal care calendar (climate-zone aware)
- Companion planting guide
- Propagation guide
- Invasive species warning + reporting
- Premium subscription launch

### Phase 3 — Advanced (Month 9-16)
- AR garden planner (WebXR)
- AI garden design generator
- AI plant health score
- Smart watering integration (Gardena, Xiaomi)
- Medicinal plant encyclopedia
- iNaturalist citizen science sync
- Time-lapse growth tracker

---

*Document Version 1.0 — FloraPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
