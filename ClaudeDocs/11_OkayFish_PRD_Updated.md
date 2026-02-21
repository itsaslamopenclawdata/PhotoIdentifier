# PRD: Okay Fish — Fish Care & Health
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Okay Fish: Fish Care & Health — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Aquatic Veterinarian Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Okay Fish** is a comprehensive AI-powered aquarium companion platform that covers the entire lifecycle of freshwater and marine fishkeeping. The app identifies fish species from photos, diagnoses diseases and health conditions, monitors water parameters, designs aquascapes, and connects users with veterinary telehealth — all in one unified platform.

The global ornamental fish market is valued at **$7.5 billion annually** with over 700 million ornamental fish sold per year. Aquarium keeping is the world's second most popular hobby after stamp collecting, with ~150 million participants globally. Despite this scale, fish disease kills an estimated **30–50% of new aquarium fish within the first year** — largely preventable with better information access.

**Proposed Brand Name:** AquaIQ Pro

---

## 3. Problem Statement

- Most new fishkeepers rely on pet store staff who frequently provide incorrect care advice.
- Fish disease diagnosis requires identifying subtle visual symptoms — no AI tool exists for this in a web-based format.
- Water chemistry management is complex (pH, ammonia, nitrite, nitrate, GH, KH, temperature cycling) — most hobbyists don't test regularly and don't know how to interpret results.
- There is no 3D aquascape planning tool accessible as a web app — existing tools are desktop software from the 2000s.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 55,000 | 400,000 |
| Fish Identified / Day | 20,000 | 150,000 |
| Identification Accuracy | >= 90% | >= 96% |
| Disease Diagnoses / Day | 5,000 | 50,000 |
| Tanks Registered on Platform | 25,000 | 400,000 |
| Premium Conversion | 9% | 16% |
| Vet Telehealth Sessions / Month | 500 | 10,000 |

---

## 5. Target Users & Personas

### Persona 1 — Alex, The Beginner Hobbyist
- **Age:** 26 | **Occupation:** IT Support | **Location:** Toronto, Canada
- **Goal:** Keep his first community tank alive and thriving; stop losing fish.
- **Pain Points:** Lost 5 fish in 3 months to unknown disease; pet store blamed him.

### Persona 2 — Yuki, The Advanced Aquascaper
- **Age:** 38 | **Occupation:** Landscape Architect | **Location:** Osaka, Japan
- **Goal:** Design award-quality planted tanks; manage complex multi-species ecosystems.
- **Pain Points:** No good browser-based 3D aquascape planning tool; wants to previsualize before buying plants/hardscape.

### Persona 3 — Dr. Amara, The Aquatic Vet
- **Age:** 44 | **Occupation:** Aquatic Veterinarian | **Location:** Cape Town, South Africa
- **Goal:** Offer remote consultation services to global fishkeepers through a telehealth platform.
- **Pain Points:** No existing telehealth platform specifically designed for aquatic veterinary consultations.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Fish Photo Identification | Photo -> species identification (freshwater + saltwater) | Accuracy >= 88% across 3,000 common aquarium species |
| Care Card | Min/max tank size, temperature (C/F), pH range, diet, compatibility group | All fields populated from FishBase database |
| Disease Symptom Checker | Describe symptom -> list of probable diagnoses | Coverage of 50 most common aquarium diseases with differential diagnosis |
| My Aquarium Logger | Register tank: name, volume, setup date, filtration, substrate | Unlimited tanks per user |
| Feeding Reminder | Set feeding schedule per tank; push notification | Browser push notification or email reminder |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Disease Diagnosis from Photo | Submit photo of sick fish -> AI returns top-3 diagnoses with treatment protocols | Accuracy >= 80% on 20 most common diseases using photographic symptom dataset |
| Water Parameter Tracker | Log pH, ammonia, nitrite, nitrate, GH, KH, temperature per tank | Line graph per parameter; safe zone highlighted in green |
| Tank Compatibility Checker | Input list of fish -> AI returns compatibility report | Data from FishBase + Seriously Fish compatibility matrices |
| Planted Tank Guide | CO2 requirements, lighting Kelvin and PAR levels, fertilizer dosing for planted setups | Covers 300 popular aquatic plants |
| Equipment Recommender | Input tank volume -> suggest filter flow rate, heater wattage, air pump | Recommendations based on turnover rate best practices |
| Breeding Setup Guide | Species-specific breeding tank requirements and conditioning tips | Coverage for 100 commonly bred species |
| Water Change Reminder | Auto-calculate based on tank size, bio-load, and stocking level | Reminder sent 1 day before and on due date |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| IoT Water Quality Integration | Connect Seneye/API Aqua sensors -> live data feed into platform | Bi-directional RSS feed; alerts when parameters outside safe range |
| 3D Aquascape Designer | Browser-based 3D aquarium layout tool: place rocks, wood, plants, fish | WebGL Three.js; minimum 200 hardscape items + 300 plants in asset library |
| Disease Progression Tracker | Log treatment steps; track symptom improvement over time | Treatment timeline with daily entry; reminders for medication dosing |
| Behavioral Analysis | Link optional webcam/tank camera feed -> AI flags abnormal behavior | Motion analysis detects: clamped fins, surface gasping, lethargy, erratic swimming |
| Fish Marketplace | Buy/sell rare species; seller must provide water param test results | Health certification required from verified sellers |
| AI Stocking List | Input tank dimensions and intent -> AI generates complete compatible stocking list | Based on inches-per-gallon + territorial + chemistry compatibility |
| Aquatic Vet Telehealth | Book video consultation with registered aquatic veterinarian | Network of 30+ registered aquatic vets; 30/60 min session options |

---

## 7. User Stories & Use Cases

### Epic 1 — Species & Care
- **US-101:** As a beginner, I want to photograph a fish at the pet store to know if it will fit in my tank before buying.
- **US-102:** As a hobbyist, I want to know if two fish I like are compatible before putting them together.
- **US-103:** As a planted tank keeper, I want to know the exact CO2 and lighting requirements for my plant species.

### Epic 2 — Disease & Health
- **US-201:** As a fish owner, I want to photograph my sick fish and get a probable diagnosis and treatment plan.
- **US-202:** As a worried hobbyist, I want to track my fish's recovery day by day with treatment protocol reminders.
- **US-203:** As a serious hobbyist with a sick rare fish, I want to book a video call with an aquatic vet.

### Epic 3 — Water Chemistry
- **US-301:** As a hobbyist, I want to log my weekly water test results and see trends over time.
- **US-302:** As an IoT user, I want live water parameter alerts from my Seneye sensor when something goes out of range.
- **US-303:** As a beginner, I want to know when to do my next water change based on my tank's bio-load.

### Epic 4 — Design & Planning
- **US-401:** As an aquascaper, I want a 3D tool to plan my tank layout and see how it will look before purchasing.
- **US-402:** As a beginner, I want the AI to tell me what fish would look good together and fit my specific tank size.

---

## 8. Technical Architecture

```
+-------------------------------------------------------------+
|              AquaIQ Pro Frontend                           |
|    Next.js 14 + TypeScript + TailwindCSS                   |
|    Camera | WebGL (3D) | WebSocket | PWA                   |
+-------------------------+-----------------------------------+
                         | REST / WebSocket
+-------------------------+-----------------------------------+
|            API Gateway (Kong)                              |
+----+--------------+--------------+--------------+----------+
     |              |              |              |
+----+------+ +-----+----------+ +--+----------+ +----------+
| Fish ID   | | Disease Engine | | Tank Mgmt / | |
| Service   | | Service        | | IoT Connector| |
| (FastAPI) | | (FastAPI)      | | (Node.js)   | |
+----+------+ +----------------+ +-------------+ +
     |
+----+-------------------------------------------------------+
|  AI: EfficientNet (fish vision) + Disease CNN             |
|  FishBase API | Seneye REST API | Stripe                  |
|  PostgreSQL | Redis | TimescaleDB (water params)         |
|  Three.js (3D WebGL aquascape tool)                       |
+------------------------------------------------------------+
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Fish Species Identification | Custom CNN fine-tuned on FishBase + iNaturalist fish images |
| Disease Diagnosis from Photo | YOLOv8 for lesion/symptom detection; classification head for disease type |
| Behavioral Analysis | Motion analysis via OpenCV — runs on backend with tank camera RTSP stream |
| Compatibility Engine | Rule-based expert system with FishBase + Seriously Fish data |

---

## 9. Data Model

**FishSpecies**
```
species_id       UUID PK
common_name      VARCHAR(200)
scientific_name  VARCHAR(200)
fishbase_id      INTEGER
water_type       ENUM(freshwater, saltwater, brackish)
min_tank_gallons INTEGER
temp_min_c       DECIMAL(4,1)
temp_max_c       DECIMAL(4,1)
ph_min           DECIMAL(4,2)
ph_max           DECIMAL(4,2)
max_size_cm      DECIMAL(5,1)
temperament      ENUM(peaceful, semi_aggressive, aggressive)
diet             ENUM(herbivore, carnivore, omnivore)
schooling_min    INTEGER
```

**UserTank**
```
tank_id          UUID PK
user_id          UUID FK
name             VARCHAR(100)
volume_gallons   DECIMAL(7,1)
water_type       ENUM(freshwater, saltwater, brackish)
setup_date       DATE
filtration       VARCHAR(200)
substrate        VARCHAR(200)
is_planted       BOOLEAN
livestock        JSONB (array of {species_id, count})
```

**WaterParameter**
```
param_id         UUID PK
tank_id          UUID FK
logged_at        TIMESTAMP
temperature_c    DECIMAL(4,1)
ph               DECIMAL(4,2)
ammonia_ppm      DECIMAL(5,3)
nitrite_ppm      DECIMAL(5,3)
nitrate_ppm      DECIMAL(6,2)
kh_dkh           DECIMAL(5,2)
gh_dgh           DECIMAL(5,2)
```

**AquaticDiseaseLog**
```
log_id           UUID PK
tank_id          UUID FK
fish_species_id  UUID FK
diagnosed_at     TIMESTAMP
disease_name     VARCHAR(200)
confidence       DECIMAL(5,4)
symptoms         TEXT[]
treatment_protocol TEXT
resolved_at      TIMESTAMP
```

---

## 10. API Design

#### POST `/api/v1/identify`
Returns species with care requirements and compatibility group.

#### POST `/api/v1/disease/diagnose`
```json
// Request: image of sick fish
// Response
{
  "diagnosis_confidence": 0.87,
  "top_diagnosis": "Ich (White Spot Disease)",
  "causative_agent": "Ichthyophthirius multifiliis",
  "symptoms_matched": ["white salt-grain spots on fins and body", "affected fish rubbing against surfaces"],
  "treatment_protocol": {
    "medication": "Ich-X or Methylene Blue",
    "dosage": "5ml per 10 gallons daily for 7 days",
    "temperature_adjust": "Raise to 30C to speed parasite lifecycle",
    "water_change": "30% every other day during treatment"
  },
  "prognosis": "Good if treated within 48 hours",
  "differential_diagnoses": ["Velvet Disease", "Epistylis"]
}
```

#### POST `/api/v1/tanks/{tank_id}/compatibility-check`
Submit list of species -> return compatibility matrix and conflict explanations.

---

## 11. UI/UX Requirements

### Screens
1. **Dashboard** — Tank summary cards; water parameter status; health alerts
2. **Identify Screen** — Camera capture; species result with care card
3. **Disease Check** — Photo upload + symptom checklist; diagnosis card + treatment protocol
4. **Water Log** — Line charts per parameter; safe zone bands; log new reading CTA
5. **3D Aquascape Designer** — WebGL canvas with drag-drop assets; export render as PNG/share
6. **Compatibility Checker** — Search + select fish; compatibility matrix output
7. **Telehealth Booking** — Vet profiles; availability calendar; video session launcher

### Design System
- **Font:** Inter (400/700) — modern, readable interface
- **Primary Color:** Indigo `#6366F1` — primary actions, links, brand identity
- **Alerts:** Red `#EF4444` — error states, critical health alerts
- **Accents:** Teal `#14B8A6` — success states, secondary actions, highlights
- **Border Radius:** 12px for cards, 8px for buttons
- **Spacing:** 4px base unit (all multiples of 4: 8px, 12px, 16px, 24px, 32px, 48px)
- **Shadows:** 5-level shadow system
  - Level 1: `0 1px 2px 0 rgb(0 0 0 / 0.05)` — subtle elevation
  - Level 2: `0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)` — cards default
  - Level 3: `0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)` — dropdowns, popovers
  - Level 4: `0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)` — modals, panels
  - Level 5: `0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)` — tooltips, tooltips
- **3D Designer:** Top-down + perspective toggle; real-time fish swimming animation in preview
- **Water Parameter Chart:** Critical zone shown in red band; safe zone in green band

---

## 12. Security & Compliance

- All disease diagnosis advice includes veterinary disclaimer: "consult a qualified aquatic veterinarian for critical cases"
- Telehealth vets: verified credentials required; RCVS/AVMA registration validation
- Tank camera feed: if connected, processed server-side in real-time; no recording without explicit user consent
- GDPR/CCPA: tank data and health logs fully exportable; account deletion removes all data

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| FishBase API | Species database (35,000+ fish species) |
| Seriously Fish | Aquarium species care and compatibility |
| Seneye REST API | IoT water parameter sensor integration |
| API Aqua / Neptune Systems | Advanced IoT controller integration |
| Stripe | Premium subscription and telehealth payments |
| Three.js | 3D aquascape design tool |
| Daily.co / Whereby | Video infrastructure for vet telehealth |
| iNaturalist | Community fish sighting contributions |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Fish identification <= 3 seconds; 3D designer loads < 4 seconds |
| **3D Performance** | WebGL aquascape designer runs at 30+ FPS on mid-range laptop |
| **IoT Latency** | Seneye sensor alerts delivered within 2 minutes of parameter breach |
| **Availability** | 99.9% uptime; tank feeding reminders must be highly reliable |
| **Offline** | Fish care cards and disease fact sheets cached for offline use |
| **Localization** | 8 languages; temperature in C or F (user-selectable) |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Fish identification (3,000 common aquarium species)
- Basic care cards (FishBase)
- Disease symptom checker
- My Aquarium tank logger
- Feeding reminder

### Phase 2 — Enhanced (Month 5–8)
- AI disease diagnosis from photo
- Water parameter tracker with trend charts
- Tank compatibility checker
- Equipment recommender
- Water change reminder calculator
- Premium subscription launch

### Phase 3 — Advanced (Month 9–16)
- 3D aquascape designer (WebGL)
- IoT sensor integration (Seneye)
- Aquatic vet telehealth marketplace
- AI stocking list generator
- Fish behavioral analysis (camera feed)
- Global fish marketplace with health certification

---

*Document Version 1.0 — Okay Fish PRD — PhotoIdentifier Platform | 2026-02-21*
