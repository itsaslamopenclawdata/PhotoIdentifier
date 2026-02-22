# PRD: PawPrismora
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | PawPrismora — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Veterinary Science Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**PawPrismora** is an AI-powered canine intelligence platform that identifies dog breeds from photos, provides breed-specific care, health, and training profiles, interprets dog behavior from photos and webcam feeds, connects owners to veterinary telehealth, and delivers a complete digital dog ownership companion ecosystem.

The global pet care market is valued at **$261 billion in 2025**, with dogs being the most popular pet worldwide (900 million+ dogs globally). Yet millions of owners — especially rescue adopters who receive mixed-breed dogs — have no tool to understand their dog's heritage, traits, or optimal care needs. PawPrismora addresses this with the most complete web-based canine intelligence platform available.

**Proposed Brand Name:** PawPrismora AI

---

## 3. Problem Statement

- 53 million shelter/rescue dogs in the US have unknown breed heritage — owners lack guidance for breed-appropriate care, training, and health screening.
- Breed-specific legislation (BSL) affects owners of dogs misidentified as restricted breeds — accurate AI identification can provide supporting documentation.
- No single web platform combines breed identification + health screening alerts + behavior analysis + vet telehealth + training programs.
- Insurance and adoption platforms lack integrated AI tools to assess breed and temperament for underwriting/matching decisions.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 150,000 | 1,500,000 |
| Breed Identifications / Day | 60,000 | 600,000 |
| Accuracy (top-1 breed) | ≥ 90% | ≥ 96% |
| Mixed Breed Composite Accuracy | ≥ 80% | ≥ 90% |
| Vet Telehealth Sessions / Month | 1,000 | 30,000 |
| Premium Conversion | 11% | 19% |
| Pet Insurance Referrals | 500/month | 20,000/month |

---

## 5. Target Users & Personas

### Persona 1 — Jessica, The Rescue Adopter
- **Age:** 31 | **Occupation:** Marketing Manager | **Location:** Austin, TX
- **Goal:** Understand her newly adopted mixed-breed dog's heritage so she can choose the right training approach.
- **Pain Points:** Shelter listed dog as "Labrador mix" — she suspects there's more to the story.

### Persona 2 — Marcus, The First-Time Owner
- **Age:** 24 | **Occupation:** Graduate Student | **Location:** Berlin, Germany
- **Goal:** Choose the right dog breed for his apartment; then get a complete training and care plan once he adopts.
- **Pain Points:** Overwhelmed by the number of breeds; has no experience reading breed characteristics.

### Persona 3 — Dr. Sarah, The Veterinarian
- **Age:** 42 | **Occupation:** Small Animal Veterinarian | **Location:** Melbourne, Australia
- **Goal:** Offer telehealth consultations to dog owners globally; use AI pre-triage to screen cases.
- **Pain Points:** No platform designed specifically for pet telehealth with AI pre-screening.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Breed Identification | Photograph dog → top-3 breed matches with confidence % | Top-1 accuracy ≥ 88% on Stanford Dogs dataset (120 breeds) |
| Mixed Breed Composite | Percentage breakdown of detected breed components | Visual pie chart of breed composition |
| Breed Profile | Size class, lifespan, temperament, energy level, shedding, trainability | Data from AKC / FCI breed standards |
| Health Screening Alerts | Breed-specific genetic health risks (hip dysplasia, cardiac, eye conditions) | Coverage for all 500+ recognized breeds |
| Exercise Needs Guide | Daily exercise requirement; activity type recommendation | Adapted to breed energy classification |
| My Dog Profile | Add pet: name, DOB, weight, breed, photo | Unlimited pets per account |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Breed Compatibility Checker | Is this breed compatible with my living situation, family, other pets? | Input: home type, children Y/N, other pets; returns suitability score |
| Training Program | 12-week breed-appropriate training plan (puppy to adult) | Covers: sit, stay, recall, leash, socialization at minimum; reward-based methodology |
| Vaccination & Health Tracker | Log vaccines, vet visits, medications, weight history | Generates vet-visit reminder notifications |
| Food & Nutrition Guide | Breed-appropriate diet type, portion size by weight, ingredients to avoid | Coverage: dry, wet, raw, fresh cooked food types |
| Behavior Decoder | Describe or photograph a behavior → AI explains what it means | Coverage of 50 common behaviors: zoomies, resource guarding, play bowing, etc. |
| Breed Finder Quiz | Lifestyle questionnaire → top-5 recommended breeds for adoption | 20-question quiz with weighted matching algorithm |
| Dog Park Finder | Map of nearest dog parks + user-submitted reviews | Google Places API; filter by off-leash area, size restrictions |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Webcam Behavior Analysis | Live camera analysis detects: pain signals, lethargy, aggression signs, anxiety | MoveNet animal pose estimation + behavior classification model |
| AI Vet Pre-Triage | Symptom checker: input symptom → urgency level + possible causes | Coverage of 200 common dog symptoms; severity classification |
| Vet Telehealth | Book video call with licensed vet | Network of 50+ licensed small animal vets; 15/30/60 min sessions |
| Breed-Specific Legislation Check | Input dog's breed composition + location → flag any BSL restrictions | Covers US state/city BSL laws; EU breed restriction directives |
| DNA Test Integration | Upload Embark/Wisdom Panel results → enrich breed profile | OAuth/CSV import from major DNA test providers |
| Wearable Integration | Sync GPS/health data from Whistle/Fi trackers | Activity, sleep, GPS fence alerts in platform |
| Pet Insurance Comparison | Based on dog profile → compare pet insurance quotes from 5+ providers | Revenue share model with insurance partners |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification & Understanding
- **US-101:** As a rescue adopter, I want to photograph my dog and see its breed composition so I understand its temperament and needs.
- **US-102:** As a prospective owner, I want a quiz to tell me which breed suits my lifestyle and apartment.
- **US-103:** As an owner subject to BSL concern, I want to check if my dog's breed composition triggers any local restrictions.

### Epic 2 — Care & Health
- **US-201:** As a first-time owner, I want a complete 12-week training plan designed for my specific breed.
- **US-202:** As a dog owner, I want to log my dog's vaccination record and get reminders for upcoming boosters.
- **US-203:** As a concerned owner, I want to describe symptoms and get an AI urgency triage before deciding to call the vet.

### Epic 3 — Veterinary
- **US-301:** As a dog owner with a sick pet at midnight, I want to book an emergency vet telehealth session.
- **US-302:** As a vet, I want an AI pre-screening summary before video calls so I can be prepared.
- **US-303:** As an owner with Embark DNA results, I want to import them and have the app generate a full care plan from exact breed %.

---

## 8. Technical Architecture

```
Frontend: Next.js 14 + TypeScript + TailwindCSS
         Camera | WebRTC (telehealth) | Webcam (behavior AI) | PWA
         |
API Gateway (Kong)
     |              |               |
Breed ID       Health/Training   Telehealth
Service        Service           Booking Service
(FastAPI)      (FastAPI)         (Node.js)
     |
AI: EfficientNet-B5 (dog breed)
    Behavior: MoveNet + animal pose estimation
    AKC / FCI data | Embark API | Whistle API
    PostgreSQL | Redis | S3 | Daily.co (video)
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Breed Classification | EfficientNet-B5 fine-tuned on Stanford Dogs + 2M labeled images across 500+ breeds |
| Mixed Breed Detection | Ensemble with breed probability vector output (sums to 100%) |
| Behavior Analysis | MoveNet Multipose + custom behavior classification head |
| Symptom AI Triage | Decision tree + LLM hybrid (GPT-4o) for symptom → urgency scoring |

---

## 9. Data Model

**DogBreed**
```
breed_id, breed_name, akc_group, fci_group,
size_class (toy/small/medium/large/giant),
avg_weight_kg, avg_lifespan_years,
temperament[], energy_level (1-5),
shedding (1-5), trainability (1-5),
grooming_needs (1-5), good_with_children (bool),
good_with_other_dogs (bool), apartment_suitable (bool),
health_risks[], exercise_minutes_daily (int)
```

**UserPet**
```
pet_id, user_id, name, date_of_birth, weight_kg,
gender, is_neutered, breed_id (nullable),
breed_composition (JSONB), photo_url,
microchip_no, insurance_policy_no
```

**HealthRecord**
```
record_id, pet_id, record_type (vaccine/vet_visit/medication/weight),
description, administered_date, next_due_date, notes, vet_name
```

**TelehealthSession**
```
session_id, user_id, pet_id, vet_id,
scheduled_at, duration_minutes, status,
pre_triage_summary, session_notes, recording_url
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
{
  "breed_results": [
    {"breed": "Border Collie", "confidence": 0.62},
    {"breed": "Australian Shepherd", "confidence": 0.24},
    {"breed": "Jack Russell Terrier", "confidence": 0.14}
  ],
  "top_breed_profile": {
    "energy_level": 5, "trainability": 5, "shedding": 3,
    "exercise_daily_min": 90,
    "health_risks": ["Collie Eye Anomaly", "Hip Dysplasia", "MDR1 Gene Mutation"],
    "bsl_risk": false
  }
}
```

#### POST `/api/v1/triage`
Input symptoms + pet profile → urgency level (emergency/vet today/monitor/normal).

#### GET `/api/v1/training-plan?breed_id={id}&pet_age_months=4`
Returns full 12-week training plan structure with daily exercises.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera; breed result with pie chart composition overlay
2. **Breed Profile** — Energy/trainability/shedding bar indicators; health risks; exercise guide
3. **My Dogs** — Pet profile cards; health status indicator; upcoming reminders
4. **Training Center** — Week-by-week program; video tutorial cards; progress checkboxes
5. **Health Tracker** — Vaccine timeline; weight chart; medication log
6. **Symptom Triage** — Step-by-step symptom selector; urgency result with vet booking CTA
7. **Telehealth Hub** — Vet listing cards; available slots calendar; video room

### Design System
- **Font:** Nunito (700) + DM Sans — warm, approachable, pet-friendly
- **Color:** Golden `#F59E0B` primary, Warm Brown `#92400E`, Cream `#FFFBEB`
- **Breed Composition Chart:** Animated donut chart with breed flag colors
- **Energy Level Indicator:** Animated paw print progress bar

---

## 12. Security & Compliance

- Telehealth vet: license verification required per jurisdiction; malpractice insurance confirmed
- BSL report: advisory only; not a legal document; recommend legal counsel for dispute
- DNA import: OAuth token exchange with Embark/Wisdom Panel; read-only scope
- Wearable data: HIPAA-adjacent best practices; user-revokable connection
- COPPA/GDPR: pet profiles owned by account holder; fully deletable

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| AKC / FCI Breed Standards | Breed profile database |
| Embark / Wisdom Panel | DNA test result import |
| Whistle / Fi GPS Tracker API | Wearable health and location data |
| Google Places API | Dog park and vet clinic finder |
| Daily.co | Telehealth video infrastructure |
| Pet insurance partners (Healthy Paws, Trupanion) | Insurance quote comparison |
| USDA APHIS / EU BSL registries | Breed-specific legislation data |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Breed ID Speed** | ≤ 2.5 seconds |
| **Webcam Behavior** | Real-time analysis at 15 FPS in browser |
| **Telehealth** | < 3 seconds video call connection time |
| **Vaccine Reminders** | Push + email; 7-day and 1-day advance notice |
| **Offline** | Pet profiles and care cards cached offline |
| **Availability** | 99.95% uptime (telehealth SLA) |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Breed identification (500+ breeds, mixed-breed composition)
- Breed profile + health alerts
- My Dog profile manager
- Vaccination + health record tracker

### Phase 2 — Enhanced (Month 5–8)
- Training program (12-week breed-appropriate)
- Symptom triage (AI urgency checker)
- Behavior decoder
- Breed compatibility quiz
- Nutrition guide
- Premium subscription launch

### Phase 3 — Advanced (Month 9–16)
- Vet telehealth marketplace
- Webcam behavior/pain analysis
- DNA test import (Embark/Wisdom Panel)
- Wearable GPS integration (Whistle/Fi)
- BSL checker by location
- Pet insurance comparison aggregator

---

*Document Version 1.0 — PawPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
