# PRD: Picture Mushroom — AI Mushroom Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Picture Mushroom: Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Mycology & Safety Expert |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Picture Mushroom** is a safety-critical AI-powered mushroom and fungi identification application. It serves foragers, hikers, mycology students, survivalists, and culinary enthusiasts who need to quickly and accurately identify wild mushrooms in the field. Critically, the app's primary design principle is **"Safety First"** — the system is architecturally biased toward warning rather than confidence when identification certainty falls below defined thresholds.

Wild mushroom poisoning hospitalizes **~2,000 people annually in the US alone**, and globally causes significant fatalities from misidentified deadly species. Picture Mushroom can save lives by providing reliable edibility guidance directly to field users. The mycology app market is also booming alongside a global foraging revival — an estimated 30+ million people forage wild foods in North America and Europe.

**Proposed Brand Name:** ForageSafe AI

> [!CAUTION]
> All user-facing communications must include legally compliant disclaimers. The app must never be presented as a substitute for expert mycological verification for consumption decisions. This is a mandatory legal and ethical requirement throughout the product.

---

## 3. Problem Statement

- No web-based mushroom identifier achieves both the accuracy and safety guardrails necessary to be trusted in life-critical field decisions.
- Many look-alike species (e.g., Amanita phalloides vs. Amanita caesarea) differ subtly and require multi-angle image analysis.
- Foragers in remote areas often lack cell coverage — offline access to dangerous species database is a safety imperative.
- Seasonal/regional variation means static databases quickly become outdated without community sighting systems.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 60,000 | 500,000 |
| Identifications / Day | 25,000 | 200,000 |
| Overall Identification Accuracy | ≥ 92% (edible/toxic classification) | ≥ 97% |
| False "Safe" Rate (critical error) | < 0.1% | < 0.05% |
| Premium Conversion | 8% | 15% |
| Community Sightings Reported | 5,000/month | 100,000/month |
| Partnerships (Poison Control) | 3 national emergency lines integrated | 20 (multi-country) |

---

## 5. Target Users & Personas

### Persona 1 — Helen, The Food Forager
- **Age:** 44 | **Occupation:** Chef + Outdoor Enthusiast | **Location:** Pacific Northwest, USA
- **Goal:** Safely identify chanterelles, morels, and porcini while foraging.
- **Pain Points:** Existing apps too slow; uncertain about confidence levels provided.
- **Willingness to Pay:** $11.99/month for a reliable safety tool she trusts with food decisions.

### Persona 2 — Ivan, The Mycology Student
- **Age:** 21 | **Occupation:** Biology Student | **Location:** Prague, Czech Republic
- **Goal:** Identify species in field practicals; contribute sightings to national fungal survey.
- **Pain Points:** Field guides heavy and hard to use in rain; wants digital note-taking integrated.
- **Willingness to Pay:** Student discount tier; $4.99/month.

### Persona 3 — Carmen, The Hiker & Survivalist
- **Age:** 35 | **Occupation:** Park Ranger | **Location:** Spain
- **Goal:** Know which mushrooms in her patrol area are deadly to warn hikers about.
- **Pain Points:** Does not have time to study mycology in depth; needs quick reliable reference.
- **Willingness to Pay:** Will advocate for park authority bulk licensing.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Single photo → species identification | Accuracy ≥ 88% on curated 50,000-image test set |
| Edibility Classification | Edible / Toxic / Deadly / Unknown — never defaults to Edible on uncertainty | System returns "Unknown/Do Not Eat" when confidence < 80% |
| Species Profile | Cap shape, color, gill structure, stem type, spore color, habitat | All fields populated from MycoBank / Index Fungorum |
| Safety Warning | Prominent display of lookalike deadly species when edible is identified | At minimum 1 lookalike warning shown for any "Edible" classification |
| Sighting Journal | Log sighting with GPS, date, habitat notes, and growth stage photo | GPS via browser Geolocation API |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Multi-Angle Analysis | Upload cap (top), gills (underside), stem (base) → composite ID | Accuracy improvement ≥ 12% over single-angle on lookalike pairs |
| Lookalike Comparison | Side-by-side visual comparison with most dangerous lookalike | High-resolution reference photos shown at same viewing angle |
| Seasonal Foraging Calendar | Which species appear in user's region this week/month | Data from community sightings + historical phenology records |
| Regional Habitat Map | Heatmap of community sightings in last 7/30/90 days | User location based; shows sighting density clusters |
| Recipe Suggestions | For confirmed edible species: link to curated recipe collection | Recipes sourced from vetted culinary database; sourced from chefs |
| Expert Review Flag | Submit photo to human mycologist community for review | Response within 48 hours (free: 1/month; premium: unlimited) |
| Spore Print Guide | AR-enabled spore print color simulation | Simulated based on known spore colors; instructional video provided |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Toxin Risk Score | Quantified toxin risk: numerical score + primary toxin type identified | Toxin classification sourced from TOXBASE / Poisonous Plants DB |
| Emergency Poison Control Integration | One-tap call/chat to national poison control (US: 1-800-222-1222, EU 112-linked) | Country-specific routing based on user geolocation |
| Citizen Science Contribution | Submit verified finds to iNaturalist and national fungal surveys | OAuth integration with iNaturalist API |
| Lookalike Disambiguation AI | When two species are equally likely, AI provides probability split + differentiating feature list | User shown differentiating checklist: does yours have this? Y/N |
| Mycelium Network Visualizer | 3D visualization of fungal habitat ecosystem relationships | Educational feature; Three.js visualization |
| Invasive Species Alert | Warn when an identified species is invasive in user's region | Mapped to GBIF invasive species registry |
| Offline Deadly Species DB | Download top-150 deadly/toxic species for offline field reference | Works fully without internet; stored in IndexedDB |

---

## 7. User Stories & Use Cases

### Epic 1 — Field Safety (CRITICAL)
- **US-101:** As a forager, I want to immediately know if a mushroom is deadly so that I never accidentally consume a toxic species.
- **US-102:** As a user who gets an "Edible" result, I want to always see the most dangerous lookalike so that I double-check before eating.
- **US-103:** As a hiker in a remote area with no signal, I want access to the 150 most dangerous mushroom profiles offline.

### Epic 2 — Advanced Identification
- **US-201:** As a forager uncertain about a chanterelle vs. false chanterelle, I want a multi-angle guided photo process for maximum accuracy.
- **US-202:** As an expert user, I want a toxin risk score to understand how dangerous an unknown mushroom is.
- **US-203:** As a student, I want to submit uncertain finds to a human mycologist network for expert review.

### Epic 3 — Community & Science
- **US-301:** As a citizen scientist, I want to upload my verified finds to iNaturalist from within the app.
- **US-302:** As a user, I want to see a heat map of what others are finding nearby this season.
- **US-303:** As a chef, I want recipe ideas for edible species I find during foraging.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│          ForageSafe AI Frontend                    │
│    Next.js 14 + TypeScript + TailwindCSS           │
│    Camera │ Geolocation │ WebXR │ PWA              │
└────────────────────┬───────────────────────────────┘
                     │ REST / WebSocket
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└─────────┬──────────────┬───────────────────────────┘
          │              │
┌─────────▼──────┐ ┌─────▼──────────────────────┐
│  Identify      │ │  Safety Classification      │
│  Service       │ │  Service (separate module)  │
│  (FastAPI)     │ │  Safety-biased logic layer  │
└────────┬───────┘ └────────────────────────────┘
         │
┌────────▼──────────────────────────────────────────┐
│  Multi-Fungi CNN (EfficientNet-B7)                │
│  Trained: 500,000+ labeled mushroom images        │
│  MycoBank API | Index Fungorum | iNaturalist      │
│  TOXBASE (toxin classification DB)                │
└───────────────────────────────────────────────────┘
         │
┌────────▼──────────────────────────┐
│  PostgreSQL │ Redis │ IndexedDB   │
│  MapLibre GL (community map)     │
│  iNaturalist API (science sync)   │
└────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology | Safety Notes |
|---|---|---|
| Main Classification | EfficientNet-B7 fine-tuned on 500k mushroom images | Conservative threshold: requires 80%+ confidence to report Edible |
| Multi-angle Fusion | Bayesian ensemble across 3 angle predictions | Lowest-confidence angle score weighted highest for safety |
| Lookalike Disambiguation | Pairwise contrastive classifier for 50 dangerous lookalike pairs | Rigorously tested against Death Cap vs. edible look-alike cases |
| Toxin Classification | Rule-based lookup: scientific name → TOXBASE toxin registry | Rule-based (not ML) for safety-critical classification |

---

## 9. Data Model

**MushroomSpecies**
```
species_id       UUID PK
common_name      VARCHAR(200)
scientific_name  VARCHAR(200)
edibility        ENUM(edible, toxic, deadly, unknown, inedible)
toxin_type       VARCHAR(200)  -- e.g., amatoxins, muscarine, gyromitrin
toxin_risk_score INTEGER (0–10)
cap_color        VARCHAR(200)
cap_shape        VARCHAR(100)
gill_type        VARCHAR(100)
stem_type        VARCHAR(100)
spore_color      VARCHAR(100)
season           TEXT[]
habitat          TEXT[]
description      TEXT
lookalike_ids    UUID[]
mycobank_id      VARCHAR(50)
created_at       TIMESTAMP
```

**Sighting**
```
sighting_id      UUID PK
user_id          UUID FK
species_id       UUID FK (nullable if unconfirmed)
ai_confidence    DECIMAL(5,4)
latitude         DECIMAL(10,7)
longitude        DECIMAL(10,7)
elevation_m      INTEGER
photo_urls       TEXT[]
growth_stage     ENUM(button, cap, mature, senescent)
weather          VARCHAR(100)
habitat_notes    TEXT
expert_reviewed  BOOLEAN
expert_verdict   VARCHAR(100)
spotted_at       TIMESTAMP
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Request (multipart)
{
  "images": ["<binary_cap>", "<binary_gills>", "<binary_stem>"],
  "latitude": 47.606,
  "longitude": -122.332
}

// Response
{
  "species_id": "uuid",
  "common_name": "Chanterelle",
  "scientific_name": "Cantharellus cibarius",
  "confidence": 0.91,
  "edibility": "edible",

  "SAFETY_WARNING": {
    "message": "BEFORE CONSUMING: Verify against false chanterelle (Hygrophoropsis aurantiaca) which is TOXIC.",
    "lookalike": {
      "name": "False Chanterelle",
      "scientific_name": "Hygrophoropsis aurantiaca",
      "edibility": "toxic",
      "key_differences": ["True chanterelle has forked ridges, not true gills", "Cap edge is wavy, not rolled under"]
    }
  },
  "toxin_risk_score": 0,
  "poison_control": {
    "us": "1-800-222-1222",
    "uk": "+44 (0)344 892 0111"
  }
}
```

**Note:** The API always returns a `SAFETY_WARNING` block for any edible species containing at minimum one dangerous lookalike.

---

## 11. UI/UX Requirements

### Screens
1. **Identify Screen** — Camera with multi-angle guidance overlay (frame for cap, gills, stem)
2. **Result Screen** — Edibility badge (color-coded: green/amber/red/gray), toxin risk meter, SAFETY WARNING banner
3. **Lookalike Comparison** — Side-by-side image + differentiating feature checklist
4. **My Sightings** — Map view with edibility color coding
5. **Foraging Calendar** — Species × month grid for user's region
6. **Expert Review** — Submit + status tracker
7. **Offline Mode** — Deadly species flashcard browser

### Design System
- **Font:** Nunito (rounded, approachable) — conveys safety-friendliness
- **Color:** Forest Green `#2D6A40` primary, Safety Red `#C0392B` for toxic warnings, Amber `#E67E22` for uncertain
- **Safety Banner:** Fixed-position, high-contrast red banner appears ANY time edibility is Edible — never dismissible without user acknowledgment
- **Confidence Meter:** Visual gauge — below 80% shows gray "Unknown — Do Not Eat" card regardless of top classification

---

## 12. Security & Compliance

- **Legal Disclaimer:** Prominent, non-skippable disclaimer on first launch; re-confirmed every 90 days
- **AI Liability:** Terms of Service explicitly state app is not a substitute for expert mycological opinion; consumption at user's own risk
- **Safety Model Auditing:** External audit of safety classification model required before every major release
- **Children:** No targeted features for under-13; parental guidance recommended
- **Emergency Integration:** Poison control contacts stored statically (not from external API) to ensure availability offline
- **GDPR:** Location data used only for regional sighting map; never sold to third parties

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| MycoBank API | Scientific species nomenclature database |
| Index Fungorum | Fungal taxonomy reference |
| iNaturalist API | Citizen science sighting contribution |
| TOXBASE | Toxin classification reference |
| GBIF (Global Biodiversity) | Invasive species registry |
| MapLibre GL | Community sighting maps |
| Poison Control APIs | Emergency contact routing by country |
| Three.js | Mycelium network 3D visualization |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Safety** | False "Edible" classification rate < 0.1%; external safety audit before each major release |
| **Performance** | Identification response ≤ 3 seconds; multi-angle results ≤ 5 seconds |
| **Offline** | Top-150 deadly species fully accessible offline (no network required) |
| **Availability** | 99.95% uptime; higher SLA than other sub-apps due to safety-critical nature |
| **Accuracy** | Multi-angle: ≥ 95% on dangerous lookalike test pairs |
| **Localization** | 12 languages at launch (critical for EU + North American foraging markets) |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Single-photo identification (top 5,000 species)
- Edibility classification with mandatory safety warnings
- Lookalike display for all edible identifications
- Offline deadly species database (top 150)
- Legal disclaimers and poison control contacts

### Phase 2 — Enhanced (Month 4–7)
- Multi-angle guided analysis
- Community sighting map
- Seasonal foraging calendar
- Expert review submission
- Premium subscription launch

### Phase 3 — Advanced (Month 8–14)
- Toxin risk score
- One-tap poison control integration
- iNaturalist citizen science sync
- Lookalike disambiguation AI
- 3D mycelium ecosystem visualizer
- Foraging regulation and protected species alerts (region-specific)

---

*Document Version 1.0 — Picture Mushroom PRD — PhotoIdentifier Platform | 2026-02-21*
