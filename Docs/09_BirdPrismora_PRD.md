# PRD: BirdPrismora — Bird Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | BirdPrismora: Bird Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Ornithology Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**BirdPrismora** is an AI-powered avian identification and birdwatching companion that combines photo and audio recognition to help users identify any of the world's **10,000+ bird species** from both visual and auditory cues. Birdwatching is the **world's most popular outdoor hobby** with over 45 million active participants in the US alone and 120 million globally, generating a $40 billion annual economic impact. Despite this enormous market, no dominant web-based birding platform with dual photo + audio AI exists for desktop users.

BirdPrismora fills this gap with predictive sighting intelligence, eBird citizen science integration, a global competition layer, and conservation funding features.

**Proposed Brand Name:** BirdPrismora Pro

---

## 3. Problem Statement

- Leading birding apps (Merlin, eBird) are mobile-only apps, not web applications — leaving desktop users and classroom environments underserved.
- Audio identification of bird songs involves significant expertise — even experienced birders struggle with song IDs in crowded acoustic environments.
- Migration prediction is done informally (word of mouth in birding communities) — no AI-powered predictive sighting system exists for the consumer market.
- Conservation donation mechanisms are scattered across dozens of separate charity websites — there is no direct link between a birding identification event and a funding action.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 90,000 | 800,000 |
| Species Identified / Day | 45,000 | 400,000 |
| Photo Accuracy (top-1) | ≥ 92% | ≥ 97% |
| Audio Accuracy | ≥ 85% | ≥ 92% |
| Life List Species Logged | 300 avg/user | 600 avg/user |
| Rare Bird Alerts Sent | 50,000/month | 500,000/month |
| Conservation Donations Facilitated | $5,000/month | $200,000/month |

---

## 5. Target Users & Personas

### Persona 1 — Barbara, The Avid Birder
- **Age:** 62 | **Occupation:** Retired Teacher | **Location:** Cornwall, UK
- **Goal:** Complete her life list; identify the warbler she heard singing but couldn't see in the hedge.
- **Pain Points:** Cannot install mobile apps (uses desktop primarily); existing tools have poor audio ID.
- **Willingness to Pay:** £9.99/month for a comprehensive birding platform.

### Persona 2 — Jake, The Nature Photographer
- **Age:** 34 | **Occupation:** Freelance Photographer | **Location:** Costa Rica
- **Goal:** Identify every bird he photographs; get species name immediately for caption and metadata.
- **Pain Points:** Field guides cover one region only; he photographs globally.
- **Willingness to Pay:** $12.99/month; needs global species database.

### Persona 3 — Ms. Chen, The Science Teacher
- **Age:** 46 | **Occupation:** High School Biology Teacher | **Location:** Singapore
- **Goal:** Run a 6-week citizen science project where students use the app to log local species.
- **Pain Points:** Needs a web-based tool usable on school computers; needs a classroom reporting dashboard.
- **Willingness to Pay:** School license: $200/year for up to 30 students.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Upload or camera capture → species identification | Accuracy ≥ 90% top-1 on Cornell Lab test set (10,000 species) |
| Audio Identification | Record bird call/song → species match | Accuracy ≥ 80% on Xeno-canto test clips |
| Species Profile | Name, family, size, plumage description, habitat, diet | All fields from Cornell Lab eBird / Birds of the World database |
| Range Map | Year-round, breeding, wintering, and migration range | GeoJSON overlaid on MapLibre interactive map |
| Life List Tracker | Log species observed; searchable list | Sorted by taxonomy, date, location; total count displayed |
| Audio Playback | Play bird call and song recordings per species | Sourced from Xeno-canto API (500,000+ recordings) |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Regional Hotspot Map | Top birding locations near user with species count per site | Data from eBird hotspot API; updated daily |
| Migration Forecast | Which migratory species are expected in user's area this week | Powered by eBird migration data + Cornell Lab BirdCast model |
| Rare Bird Alert | Push/email notification when a rare species is reported near user | Alert latency < 10 minutes from eBird report |
| Photo EXIF Log | Automatically read date/time/GPS from uploaded photo EXIF data | Works for JPG/HEIC/RAW formats; GPS displayed on map |
| eBird Submission | Submit sightings directly to eBird from app | OAuth-linked eBird account; checklist format |
| Behavior Glossary | Describe observed behavior → get behavioral trait interpretation | 50+ behavior terms defined with examples |
| Breeding Calendar | Show breeding season windows and nesting behavior per species | Data from Cornell Lab regional breeding atlases |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Real-Time Flock Identification | Submit video clip → identify moving species in flock | Accuracy ≥ 75% at common flock species level;  processing < 10 seconds |
| Predictive Sighting AI | "Tomorrow at 7am at X location, you may see Y species" | Model trained on eBird time/location/species occurrence data; accuracy ≥ 70% for common species |
| Scope Camera Integration | Bluetooth/WiFi connection to digiscoping adapters | Supports Swarovski dSX and Kowa PROMINAR adapters |
| 3D Species Model Viewer | Interactive 3D bird model with anatomy labels | Powered by Three.js; 200 most common species at launch |
| AI Field Sketch Generator | Upload photo → AI draws stylized pencil field sketch | Artistic filter pipeline; downloadable PNG |
| Conservation Integration | Identify threatened species → one-click charity donation | Links to BirdLife International species-matched donation pages |
| Global Birding Competition | Monthly competition: most species spotted wins; point and badge system | Leaderboard segmented by country and skill level |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification
- **US-101:** As a birder, I want to photograph a bird and know its species in under 3 seconds.
- **US-102:** As a user who heard a bird but couldn't see it, I want to record the song and identify it by audio.
- **US-103:** As a nature photographer, I want GPS and date from my photo EXIF data auto-filled in my sighting log.

### Epic 2 — Life Listing & Tracking
- **US-201:** As a life-lister, I want a clean list of every species I've ever seen, sorted by taxonomy.
- **US-202:** As a competitive birder, I want to see how my life list compares to others in my country this year.
- **US-203:** As a teacher, I want my class's sightings auto-compiled into a regional species report.

### Epic 3 — Conservation
- **US-301:** As an environmentally conscious birder, I want to donate to a conservation fund for the specific endangered species I just identified.
- **US-302:** As a conservationist, I want to export all my sightings in a format compatible with national ornithological societies.

### Epic 4 — Advanced Birding Tools
- **US-401:** As a birder, I want to know which rare species might pass through my area in the next 7 days based on migration models.
- **US-402:** As a scope user, I want to connect my Bluetooth digiscoping adapter to capture and identify birds from a distance.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│             BirdPrismora Pro Frontend                 │
│    Next.js 14 + TypeScript + TailwindCSS           │
│  Camera │ Audio API │ WebBluetooth │ WebXR │ PWA  │
└────────────────────┬───────────────────────────────┘
                     │ REST / WebSocket
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└────┬───────────────┬───────────────────────────────┘
     │               │
┌────▼──────┐ ┌──────▼──────────────────┐
│ Photo ID  │ │ Audio ID Service        │
│ Service   │ │ (BirdNET / Xeno-canto)  │
│ (FastAPI) │ │ + Migration Forecast    │
└────┬──────┘ └─────────────────────────┘
     │
┌────▼──────────────────────────────────────────────┐
│  AI Vision: EfficientNet-B6 (Cornell bird dataset) │
│  Audio: BirdNET neural net (Cornell Lab)           │
│  eBird API │ BirdCast Migration API                │
│  Xeno-canto API │ MapLibre GL                     │
│  PostgreSQL │ Redis │ S3 │ TimescaleDB             │
└────────────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Photo Identification | EfficientNet-B6 fine-tuned on Cornell Lab 140M bird image dataset |
| Audio Identification | BirdNET (Cornell Lab open-source model) adapted for web |
| Flock Video Analysis | YOLOv8 frame-by-frame + temporal tracking for species sequence detection |
| Predictive Sighting | Random Forest classifier trained on eBird time/location/species occurrence matrix |
| Field Sketch Generator | Stable Diffusion fine-tuned on pencil bird field sketches |

---

## 9. Data Model

**BirdSpecies**
```
species_id       UUID PK
common_name      VARCHAR(200)
scientific_name  VARCHAR(200)
order_name       VARCHAR(100)
family           VARCHAR(100)
ebird_code       VARCHAR(20)
iucn_status      ENUM(LC, NT, VU, EN, CR, EW, EX)
size_cm          DECIMAL(5,1)
wingspan_cm      DECIMAL(5,1)
habitat          TEXT[]
range_geojson    JSONB
breeding_months  INTEGER[]
primary_song_url TEXT
calls_urls       TEXT[]
description      TEXT
```

**UserSighting**
```
sighting_id      UUID PK
user_id          UUID FK
species_id       UUID FK
latitude         DECIMAL(10,7)
longitude        DECIMAL(10,7)
sighted_at       TIMESTAMP
count            INTEGER
behavior_notes   TEXT
photo_urls       TEXT[]
audio_url        TEXT
ebird_submitted  BOOLEAN
ebird_checklist_id VARCHAR(50)
life_list_entry  BOOLEAN
```

**LifeList**
```
lifelist_id      UUID PK
user_id          UUID FK UNIQUE
species_count    INTEGER
first_updated    TIMESTAMP
last_updated     TIMESTAMP
species_ids      UUID[] (array of all observed species IDs)
```

---

## 10. API Design

#### POST `/api/v1/identify/photo`
```json
// Response
{
  "species_id": "uuid",
  "common_name": "Atlantic Puffin",
  "scientific_name": "Fratercula arctica",
  "confidence": 0.97,
  "family": "Alcidae",
  "iucn_status": "VU",
  "CONSERVATION_NOTE": {
    "status": "Vulnerable",
    "donate_url": "https://www.birdlife.org/atlantic-puffin",
    "donate_label": "Support Atlantic Puffin Conservation"
  },
  "range_map_url": "...",
  "song_url": "...",
  "description": "..."
}
```

#### POST `/api/v1/identify/audio`
Submit base64 audio clip (5–30 seconds) → return top-3 species matches with confidence.

#### GET `/api/v1/forecast?lat=51.5&lon=-2.5&days=7`
Returns predicted species sightings for given location over next 7 days.

#### GET `/api/v1/alerts/rare?radius_km=50&lat=51.5&lon=-2.5`
Returns rare bird reports from eBird within radius in last 24 hours.

---

## 11. UI/UX Requirements

### Screens
1. **Home** — Today's forecast species, recent sightings, rare alerts banner
2. **Identify Screen** — Photo upload / audio record tabs; live camera mode
3. **Species Detail** — Photo gallery, range map, audio player, 3D model, life stats, conservation status
4. **Life List** — Paginated list with search; map view; export to eBird
5. **Migration Map** — Full-screen interactive map with week-by-week migration layer
6. **Birding Hotspots** — Nearby hotspot cards with expected species + user reports
7. **Competition** — Monthly leaderboard; point system; badge wall
8. **Conservation Hub** — Threatened species in user's region; donation pathways

### Design System
- **Font:** Spectral (serif for species names) + Inter (UI)
- **Color:** Sky Blue `#0EA5E9` primary, Forest Green `#15803D` accent, Cream `#FEF3C7` background
- **Range Maps:** Seasonal layer toggle (breeding=orange, winter=blue, year-round=purple)
- **Audio Player:** Spectrogram visualization of bird song playback

---

## 12. Security & Compliance

- eBird OAuth: user controls data sharing scope
- GDPR: location data used for regional forecasting; user opt-out removes from community map
- Conservation donation: BirdLife payment processing; platform does not handle funds directly
- School tier: FERPA compliant; no personal data visible in student accounts

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| Cornell Lab eBird API | Species database, sighting submission, hotspot data |
| Cornell Lab BirdCast | Migration prediction data |
| BirdNET (Cornell Lab) | Audio species identification model |
| Xeno-canto API | Bird call and song recordings library |
| BirdLife International | IUCN conservation status + donation links |
| MapLibre GL | Range maps and hotspot maps |
| Three.js | 3D bird species models |
| Web Bluetooth API | Digiscoping camera scope adapter |
| Stripe | Premium subscription payments |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Photo ID Speed** | ≤ 3 seconds p95 |
| **Audio ID Speed** | ≤ 5 seconds for 10-second audio clip |
| **Migration Forecast** | Updated nightly from BirdCast model |
| **Rare Bird Alerts** | < 10 minutes from eBird report to user notification |
| **Offline** | Life list and cached species profiles work offline |
| **Availability** | 99.9% uptime |
| **Localization** | 10 languages; bird common names in local language where available |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Photo identification (10,000 species)
- Audio identification (3,000 most common species)
- Species detail with range map
- Life list tracker
- eBird sighting submission

### Phase 2 — Enhanced (Month 5–8)
- Migration forecast integration
- Rare bird alerts
- Regional birding hotspot map
- Photo EXIF log
- Breeding season calendar

### Phase 3 — Advanced (Month 9–16)
- Flock video identification
- Predictive sighting AI
- 3D species model viewer
- AI field sketch generator
- Global birding competition
- Conservation donation integration
- Education classroom license tier
- Digiscoping adapter Bluetooth connection

---

*Document Version 1.0 — BirdPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
