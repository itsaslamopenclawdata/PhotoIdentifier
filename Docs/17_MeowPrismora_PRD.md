# PRD: MeowPrismora
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | MeowPrismora — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Feline Veterinary Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**MeowPrismora** is the feline counterpart to PawPrismora — a complete AI-powered cat intelligence and ownership platform. It identifies cat breeds from photos, profiles feline temperament and health risks, provides vet telehealth, analyzes body condition score and coat health from photos, and features a feline behavior interpreter.

Cats are the world's most popular pet by number — with **600 million+ domestic cats globally** and 45 million households owning cats in the US alone. The platform differentiates by solving distinctly feline problems: cats are more private creatures than dogs, their health conditions (UTI, kidney disease, hyperthyroidism) present subtly, and feline nutrition requirements are highly specific. No existing web-based platform provides a complete AI care ecosystem dedicated to cats.

**Proposed Brand Name:** MeowPrismora AI

---

## 3. Problem Statement

- Cats disguise illness until advanced — owners have few early warning tools beyond "the cat seems off."
- Mixed-breed or "domestic shorthair" owners have no breed heritage context for health and temperament planning.
- Feline-specific nutrition (obligate carnivore requirements, food sensitivities) is poorly communicated in mainstream pet apps.
- No AI tool exists that can assess feline body condition score from a photo — a critical indicator of obesity and underlying disease.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 130,000 | 1,200,000 |
| Breed Identifications / Day | 55,000 | 500,000 |
| Identification Accuracy | ≥ 90% pure breed | ≥ 96% pure breed |
| Body Condition Score Accuracy | ≥ 80% (vs. vet assessment) | ≥ 88% |
| Vet Telehealth Sessions / Month | 800 | 25,000 |
| Premium Conversion | 12% | 20% |

---

## 5. Target Users & Personas

### Persona 1 — Yumi, The Rescue Cat Owner
- **Age:** 26 | **Occupation:** UX Designer | **Location:** Tokyo, Japan
- **Goal:** Identify her rescue cat's likely breed mix; understand if the behavior she's seeing is normal for that breed.
- **Pain Points:** Can't tell if her cat's aloofness or vocality is a breed trait or a sign of stress.

### Persona 2 — Michael, The Multi-Cat Household
- **Age:** 48 | **Occupation:** Accountant | **Location:** London, UK
- **Goal:** Monitor the weight and health of 4 cats; manage different dietary needs per cat.
- **Pain Points:** Vet appointments are expensive and stressful for cats; wants proactive monitoring tools.

### Persona 3 — Dr. Lin, The Feline Specialist Vet
- **Age:** 39 | **Occupation:** Feline Specialist DVM | **Location:** Singapore
- **Goal:** Offer expert remote consultations globally; reach underserved cat owners in countries with few feline specialists.
- **Pain Points:** No telehealth platform specifically designed for feline specialist practice.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Breed Identification | Photo → top-3 breed matches with confidence % | Accuracy ≥ 88% on 80-breed test dataset |
| Mixed Breed Composite | Estimated percentage breakdown of breed components | Visual composition display |
| Breed Profile | Origin, size, personality traits, vocality, independence, indoor/outdoor suitability | Data from TICA / CFA breed standards |
| Health Screening Alerts | Breed-specific genetic conditions (HCM, PKD, FIP susceptibility, PRA) | Coverage for all 100+ TICA-recognized breeds |
| My Cats Profile | Register cat with name, DOB, breed, photo, weight | Multi-cat support |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Body Condition Score (BCS) | Photo assessment: underweight / ideal / overweight / obese | BCS 1–9 scale; ≥ 80% agreement with vet assessment |
| Coat Health Analysis | Assess coat quality: glossy/dull/patchy/overgroomed | Visual analysis; triggers vet consultation recommendation |
| Feline Nutrition Guide | Obligate carnivore requirements; wet vs. dry; taurine/arginine; ingredient avoidance | Sourced from AAFCO + feline nutritionists |
| Vaccination & Health Tracker | Core vaccine schedule, rabies, FeLV/FIV, vet visits, deworming | Feline-specific schedule; pop-up reminders |
| Behavioral Interpreter | Select behavior → feline meaning + context | 60 behaviors: slow blink, trilling, kneading, tail position, spraying |
| Indoor Enrichment Planner | Breed-specific enrichment activities + DIY toy guides | Activity cards adapted to energy level per breed |
| Weight Management Program | Set target weight; weekly weigh-in tracker; diet adjustment suggestions | NutriPrismorarie calculation based on current vs. ideal BCS |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Early Illness Detector | Daily photo + behavioral check-in → AI flags deviations suggesting illness | Detects: coat condition change, posture change, face expression asymmetry |
| Urinary Health Monitor | Track water intake + litter box patterns; alerts if frequency changes | Manual log or IoT litter box integration (PetSafe ScoopFree) |
| AI Body Fat Estimator | Multi-angle photo → estimated body fat % + BCS | ±1 BCS scale accuracy target vs. vet palpation |
| Feline Telehealth | Book video call with licensed feline specialist vet | Network of 30+ ABVP board-certified feline specialists |
| DNA Test Integration | Import Basepaws or Optimal Selection DNA results | Enrich breed profile with genomic health markers |
| Wearable Integration | Sync Tractive/Catit GPS and activity collar data | Activity, sleep, calories burned, location safety |
| AI Purr Pattern Analysis | Audio analysis of purr → frequency mapping; stress vs. contentment signal | Experimental feature; disclaimer displayed; 75% accuracy target |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification
- **US-101:** As a rescue owner, I want to photograph my cat and see its likely breed composition and whether its behaviors are normal for those breeds.
- **US-102:** As a breeder, I want to verify a kitten's breed characteristics match the parent breed standard.
- **US-103:** As a potential adopter, I want to find which breed best suits my quiet apartment lifestyle.

### Epic 2 — Health Monitoring
- **US-201:** As a multi-cat owner, I want to log each cat's weekly weight and see a trend chart so I can catch obesity early.
- **US-202:** As a worried owner, I want to photograph my cat and get an AI body condition score so I know if they need a vet.
- **US-203:** As a cat owner, I want to track my cat's litter box patterns and be alerted if something changes significantly.

### Epic 3 — Veterinary Care
- **US-301:** As an owner in a country with few vets, I want to video-call a feline specialist for an expert opinion.
- **US-302:** As an owner with Basepaws DNA results, I want them imported so the app knows my cat's specific health risks.
- **US-303:** As an early illness detection user, I want a daily 30-second photo check-in that alerts me to subtle changes before they become crises.

---

## 8. Technical Architecture

```
Frontend: Next.js 14 + TypeScript + TailwindCSS
         Camera | Audio API (purr) | WebRTC (telehealth) | PWA
         |
API Gateway (Kong)
     |              |               |
MeowPrismora ID   Health Monitor   Telehealth
Service        Service          Booking
(FastAPI)      (FastAPI)        (Node.js)
     |
AI: EfficientNet-B5 (cat breed)
    BCS: Body condition regression CNN
    Illness: Temporal deviation detector
    TICA/CFA data | Basepaws API | Tractive API
    PostgreSQL | Redis | S3 | Daily.co (video)
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Breed Classification | EfficientNet-B5 fine-tuned on 80+ cat breed dataset (Oxford Cats + proprietary 400k images) |
| Body Condition Score | Multi-angle CNN regression (1–9 BCS scale) |
| Coat Health Assessment | Texture analysis CNN (glossiness, patchiness, overgrooming indicators) |
| Early Illness Flag | LSTM time-series model on daily photo + behavioral log delta |
| Purr Analysis | Audio FFT + frequency centroid analysis (experimental) |

---

## 9. Data Model

**CatBreed**
```
breed_id, breed_name, tica_code, cfa_code,
origin_country, size_class, avg_weight_kg,
avg_lifespan_years, temperament[], vocality (1-5),
affection_level (1-5), independence (1-5),
grooming_needs (1-5), indoor_only (bool),
health_risks[], shedding (1-5)
```

**UserCat**
```
cat_id, user_id, name, date_of_birth, weight_kg,
gender, is_spayed_neutered, breed_id,
breed_composition (JSONB), photo_url,
microchip_no, insurance_policy_no
```

**HealthLog**
```
log_id, cat_id, log_type (weight/bcs/vaccine/vet/medication/litter),
value (JSONB), logged_at, next_reminder_at, notes
```

**DailyCheckIn**
```
checkin_id, cat_id, photo_url, bcs_score,
coat_assessment, behavior_notes,
ai_flag (bool), ai_flag_reason, checked_in_at
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
{
  "breed_results": [
    {"breed": "Siamese", "confidence": 0.71},
    {"breed": "Oriental Shorthair", "confidence": 0.19},
    {"breed": "Domestic Shorthair", "confidence": 0.10}
  ],
  "top_breed_profile": {
    "vocality": 5, "affection_level": 4, "independence": 2,
    "health_risks": ["Hypertrophic Cardiomyopathy", "Progressive Retinal Atrophy"],
    "grooming_needs": 2, "indoor_only": true
  }
}
```

#### POST `/api/v1/health/bcs`
Submit multi-angle photos → body condition score + weight management recommendation.

#### POST `/api/v1/health/daily-checkin`
Photo + mood notes → AI deviation flag vs. baseline.

#### POST `/api/v1/telehealth/book`
Select vet + time slot + pet profile → creates booking + pre-fills pre-triage form.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera; breed result with composition donut chart
2. **Breed Profile** — Trait bars (vocality, affection, independence, grooming); health risks accordion
3. **My Cats** — Cat card carousel; BCS trend; upcoming health reminders
4. **Daily Check-In** — Photo + mood slider; AI assessment result card
5. **Health Tracker** — Weight/BCS line chart; vaccine timeline; litter log heatmap
6. **Behavior Library** — Search behaviors; illustrated cards; normal vs. concerning guides
7. **Telehealth Hub** — Specialist vet profiles; booking calendar; pre-triage form

### Design System
- **Font:** Quicksand (soft, rounded) + Nunito — cozy, cat-friendly feel
- **Color:** Lavender `#7C6BCA` primary, Warm Pink `#F06292` accent, Ivory `#FAFAF7` background
- **BCS Wheel:** Illustrated cat silhouette overlaid with BCS zone coloring
- **Daily Check-In:** Polaroid-style photo card with mood emoji timeline
- **Breed Composition:** Animated layered donut chart with breed color key

---

## 12. Security & Compliance

- Telehealth vet: RCVS (UK), AVMA, WSAVA-member vets only; license verified at onboarding
- Daily photo check-in images: processed and stored; user can delete all data at any time
- DNA import: read-only OAuth; no genomic data sold to third parties explicitly in Privacy Policy
- Cat audio recordings (purr analysis): processed server-side; deleted immediately after FFT transform
- GDPR/CCPA: full export and deletion; pet health records are user property

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| TICA / CFA Breed Standards | Official breed profile data |
| Basepaws Feline DNA API | Cat DNA test import |
| Optimal Selection | Additional genomic health marker import |
| Tractive / Catit GPS API | Wearable activity + location data |
| PetSafe ScoopFree | Smart litter box integration |
| Daily.co | Telehealth video infrastructure |
| Pet insurance partners | Cat insurance quote comparison |
| AAFCO | Feline nutritional standards |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Breed ID Speed** | ≤ 2.5 seconds |
| **BCS Analysis** | ≤ 4 seconds for multi-angle assessment |
| **Telehealth** | < 3 seconds video connection time |
| **Daily Check-In** | AI deviation flag response ≤ 2 seconds |
| **Offline** | Cat profiles and care cards cached offline |
| **Availability** | 99.95% uptime (telehealth critical path) |
| **Localization** | 10 languages; weight in kg/lbs toggle |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Cat breed identification (80+ breeds + mixed)
- Breed profile + health risk alerts
- My Cats profile manager
- Health record tracker

### Phase 2 — Enhanced (Month 5–8)
- Body condition score (BCS) from photo
- Coat health analysis
- Weight management program
- Daily check-in with AI deviation flag
- Behavior interpreter library
- Indoor enrichment planner
- Premium subscription launch

### Phase 3 — Advanced (Month 9–16)
- Feline telehealth marketplace (specialist vets)
- AI early illness detector (temporal pattern)
- Urinary health + litter box monitoring
- DNA test import (Basepaws)
- Wearable integration (Tractive/Catit)
- AI purr frequency analysis (experimental)
- Cat insurance comparison aggregator

---

*Document Version 1.0 — MeowPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
