# PRD: Workout Planner MusclePrismora
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Workout Planner MusclePrismora — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Certified Strength & Conditioning Specialist |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Workout Planner MusclePrismora** is a science-backed, advanced fitness planning and tracking platform for intermediate-to-advanced gym-goers and athletes. Unlike its companion app FitPrismora (which targets beginners), MusclePrismora is built for serious lifters who care about periodization, progressive overload, volume analytics, body composition measurement, and data-driven performance optimization.

The global gym and fitness club market is valued at **$96 billion in 2025**, with digital fitness supplements being the fastest-growing revenue category. MusclePrismora addresses the gap for lifters who have outgrown basic step trackers and need an intelligent programming system equivalent to having a certified strength coach in their pocket.

**Proposed Brand Name:** MusclePrismora

---

## 3. Problem Statement

- Most fitness apps treat all users the same — beginners with advanced athletes. There is no web-based platform specifically designed for intermediate+ lifters with proper periodization science.
- Progressive overload tracking across hundreds of exercises is tedious manually; no intelligent auto-suggestion system exists.
- Body composition tracking currently requires expensive DEXA scans or unreliable home scales — a photo-based AI alternative has huge adoption potential.
- Coaching marketplace platforms (Trainerize, TrueCoach) are B2B SaaS products; there is no consumer-friendly marketplace for hiring evidence-based coaches.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 80,000 | 600,000 |
| Workouts Logged / Day | 40,000 | 350,000 |
| Premium Conversion | 12% | 22% |
| AI Periodization Plans Generated | 5,000/month | 80,000/month |
| Coaching Marketplace GMV | $10,000/month | $500,000/month |
| NPS | 55 | 68 |
| 90-Day Retention | 38% | 52% |

---

## 5. Target Users & Personas

### Persona 1 — Ryan, The Dedicated Lifter
- **Age:** 27 | **Occupation:** Software Developer | **Location:** San Francisco, CA
- **Goal:** Run a proper 16-week powerlifting peaking program; track every set with minimal friction.
- **Pain Points:** Current apps don't understand periodization; has to manually plan deload weeks in a spreadsheet.
- **Willingness to Pay:** $14.99/month for a smart, lifter-focused platform.

### Persona 2 — Fatima, The Physique Competitor
- **Age:** 30 | **Occupation:** Pharmacist | **Location:** Dubai, UAE
- **Goal:** Cut to stage condition with 12-week structured program; track body fat % changes.
- **Pain Points:** Hired an online coach but no good tracking tool that her coach can access.
- **Willingness to Pay:** $19.99/month; her coach would also need access.

### Persona 3 — Marcus, The Online Fitness Coach
- **Age:** 35 | **Occupation:** Certified PT & Online Coach | **Location:** London, UK
- **Goal:** Manage 30+ remote coaching clients; view their logs and adjust programs weekly.
- **Pain Points:** Uses Google Sheets + Trainerize but wants an all-in-one premium solution.
- **Willingness to Pay:** $49.99/month (coach tier); clients on their own plan.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Program Templates | 12 pre-built programs: PPL, PHUL, 5/3/1, Arnold Split, GZCLP, StrongLifts, etc. | Each program fully programmable for 8–16 weeks |
| Exercise Library | 700+ exercises with HD video demos, muscle diagram, and cue descriptions | Videos load < 2 seconds via CDN |
| Workout Session Logger | Log sets × reps × weight; RPE optional; rest timer built-in | Sub-second UI response for set logging |
| Personal Records Tracker | Auto-detects and celebrates new PRs in any exercise | PR detection runs on every set logged |
| Weekly Schedule View | Visual 7-day planner with drag-and-drop session reordering | Sessions saved and synced across devices |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Progressive Overload Engine | Suggests weight/rep increase each session based on previous performance | Recommendations based on double-progression model; adjustable |
| Volume Heatmap | Weekly volume (sets × reps × RIR) visualized per muscle group | Color-coded: undertrained / optimal / overtrained thresholds from Israetel's model |
| 1RM Calculator & Tracker | Epley formula-based 1RM estimate from any set; historical trend | Chart shows estimated 1RM over time per lift |
| Split Generator | AI generates optimal training split based on days/week + goals | Generates both frequency-2 and frequency-3 options for each split |
| Body Measurement Tracker | Log: weight, chest, arms, waist, hips, thighs, neck | Line graphs per measurement; goal comparison line |
| Rest Timer | Configurable countdown per exercise type (compound: 180s default, isolation: 90s) | Timer persists if browser tab is switched |
| Equipment Filter | Filter exercises and programs by available equipment | 6 equipment tiers: bodyweight, bands, dumbbells, barbell, cable machine, full gym |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Periodization Planner | Generates 12/16/20-week mesocycles with volume landmarks and deload weeks | Based on Mike Israetel's RP-strength volume principles; user inputs MRV estimates |
| Real-Time Form Analysis | Webcam pose estimation during workout detects form breakdown | Detects: squat depth, knee cave, elbow flare, hinge pattern on 15 primary movements |
| Fatigue & Recovery Score | Daily score based on volume, sleep, HRV input | User inputs sleep quality; HRV from wearable; volume from session log |
| Smart Gym Equipment Sync | Sync with connected gym equipment (Peloton ERG, Life Fitness API) | Bidirectional: push planned workout to equipment; pull actual output back |
| AI Body Composition Estimate | Upload front/side/back photos → AI estimates body fat % + muscle mass distribution | Accuracy target: ±3% BF vs DEXA scan; clearly labeled as estimate |
| Supplement Stack Optimizer | Based on goals + training phase → evidence-based supplement suggestions | All suggestions cite peer-reviewed sources; no affiliate bias disclosure required |
| Coaching Marketplace | Hire certified coaches; coaches access client logs and push adjusted programs | Stripe Connect for coach payments; coach profile verification process |

---

## 7. User Stories & Use Cases

### Epic 1 — Programming
- **US-101:** As a lifter, I want an AI to design a 16-week periodized program for me so that I have a structured plan to follow.
- **US-102:** As a powerlifter, I want deload weeks automatically scheduled so that I don't need to think about recovery planning.
- **US-103:** As a coach, I want to send a custom program directly to my client's MusclePrismora account.

### Epic 2 — Session Logging
- **US-201:** As a lifter, I want to log a set in under 3 taps so that I don't lose momentum between sets.
- **US-202:** As a competitive lifter, I want to see my estimated 1RM trend over 6 months so that I can validate my strength progress.
- **US-203:** As a data-driven athlete, I want to see if a muscle group is being under- or over-trained this week.

### Epic 3 — Body Composition
- **US-301:** As a physique athlete, I want to submit periodic photos for AI body fat estimation so that I can track my body composition without expensive tests.
- **US-302:** As a cutter, I want to see my body measurement trend alongside my calorie data from NutriPrismora so that I understand my recomposition.

### Epic 4 — Coaching
- **US-401:** As a coach, I want to manage all my clients from one dashboard and push program updates to any client's app.
- **US-402:** As an athlete, I want to hire a certified coach through the marketplace and have them view my exact training logs.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│             MusclePrismora Frontend                     │
│    Next.js 14 + TypeScript + TailwindCSS           │
│    Camera (pose) │ WebSocket (live session) │ PWA  │
└────────────────────┬───────────────────────────────┘
                     │ REST / WebSocket
┌────────────────────▼───────────────────────────────┐
│            API Gateway (Kong)                      │
└────┬───────────────┬───────────────┬───────────────┘
     │               │               │
┌────▼──────┐ ┌──────▼──────┐ ┌─────▼────────────┐
│ Program   │ │ Volume &    │ │  Body Comp AI    │
│ Service   │ │ Analytics   │ │  Service         │
│ (FastAPI) │ │ Service     │ │  (Python/ONNX)   │
└────┬──────┘ └─────────────┘ └──────────────────┘
     │
┌────▼───────────────────────────────────────────┐
│  AI Engine: MoveNet (form) | Body Comp CNN     │
│  RP-Strength volume models (periodization)     │
│  PostgreSQL │ Redis │ TimescaleDB (time series)│
│  S3 (photos) │ Kafka (realtime events)         │
└────────────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Form Analysis | MoveNet (TensorFlow.js in-browser) + rule-based joint angle thresholds |
| Body Composition Estimation | Custom CNN trained on labeled physique photos + DEXA ground truth |
| Periodization Logic | Algorithmic (RP-Strength volume landmark model) + ML personalization |
| Recovery Score | Linear regression on sleep, HRV, and training load inputs |

---

## 9. Data Model

**TrainingProgram**
```
program_id       UUID PK
user_id          UUID FK (null if template)
coach_id         UUID FK (null if self-programmed)
name             VARCHAR(200)
duration_weeks   INTEGER
goal             ENUM(strength, hypertrophy, endurance, fat_loss, peaking)
frequency        INTEGER (days/week)
sessions         JSONB (array of workout day definitions)
is_template      BOOLEAN
created_at       TIMESTAMP
```

**WorkoutSession**
```
session_id       UUID PK
user_id          UUID FK
program_id       UUID FK
session_date     DATE
duration_seconds INTEGER
total_volume_kg  DECIMAL(10,2)
total_sets       INTEGER
avg_rpe          DECIMAL(3,1)
recovery_score   DECIMAL(4,2)
exercises_logged JSONB
```

**ExerciseSet**
```
set_id           UUID PK
session_id       UUID FK
exercise_id      UUID FK
set_number       INTEGER
weight_kg        DECIMAL(6,2)
reps             INTEGER
rpe              DECIMAL(3,1)
is_pr            BOOLEAN
form_score       DECIMAL(4,2)
```

**BodyCompositionLog**
```
log_id           UUID PK
user_id          UUID FK
log_date         DATE
weight_kg        DECIMAL(5,2)
body_fat_pct     DECIMAL(4,2)
muscle_mass_kg   DECIMAL(5,2)
measurements     JSONB (chest, arms, waist, hips, thighs)
photo_urls       TEXT[]
method           ENUM(manual, ai_estimate, scale_impedance)
```

---

## 10. API Design

#### POST `/api/v1/programs/generate`
```json
// Request
{
  "goal": "hypertrophy",
  "days_per_week": 5,
  "experience": "intermediate",
  "duration_weeks": 12,
  "equipment": "full_gym",
  "weak_points": ["back", "shoulders"]
}
// Response: Full 12-week program with daily sessions
```

#### POST `/api/v1/sessions/{session_id}/sets`
Log an individual set; returns updated volume and PR flag.

#### GET `/api/v1/analytics/volume-heatmap?week=2026-W08`
Returns per-muscle-group weekly volume with over/under-training classification.

---

## 11. UI/UX Requirements

### Screens
1. **Dashboard** — Today's workout card, weekly volume heatmap, recovery score
2. **Workout Player** — Set logging with auto-advance; rest timer; PR celebration animation
3. **Program Builder** — Drag-and-drop exercise blocks; periodization timeline view
4. **Analytics Hub** — Volume charts, 1RM trends, body composition progress
5. **Coach Dashboard** — Multi-client switcher; program push tool
6. **Body Scan Portal** — Photo upload flow with AI analysis result overlay

### Design System
- **Font:** Inter (700 headers, 400/600 body)
- **Colors:** White background, Indigo `#6366F1` primary, Emerald `#10B981` for PRs
- **Border Radius:** 12px cards, 8px buttons
- **Spacing:** 4px base unit
- **Shadows:** 5-level shadow system
- **Animations:** Weight plate loading animation on workout start; firework burst on PR achievement

---

## 12. Security & Compliance

- Coach-client relationship requires explicit in-app consent from client
- Body composition photos encrypted at rest (AES-256); user-only access
- Coach marketplace: ID verification (Stripe Identity) required for all coaches
- Revenue share: 20% platform fee on all coaching transactions
- **Disclaimer:** Body fat percentage estimates clearly marked as approximations; not medical advice

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| TensorFlow.js / MoveNet | Real-time in-browser pose estimation |
| Peloton API | Smart equipment sync |
| Life Fitness Digital Connect | Commercial gym equipment integration |
| Garmin / Fitbit (Health APIs) | HRV and sleep data for recovery score |
| NutriPrismora (Internal API) | NutriPrismorarie data for body recomposition tracking |
| FitPrismora (Internal API) | Fitness level handoff (beginner → intermediate promotion) |
| Stripe Connect | Coach marketplace payment processing |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Set Logging Latency** | < 200ms from tap to confirmation |
| **Pose Analysis** | < 1 second form feedback (in-browser, no upload) |
| **Offline Mode** | Active workout session loggable without internet |
| **Availability** | 99.9% uptime; auto-save every 30 seconds during session |
| **Data Export** | Export full training history as CSV/JSON |
| **Localization** | 8 languages; metric / imperial unit toggle |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- 12 program templates, 700+ exercise library
- Session logger with rest timer and PR detection
- Weekly schedule view
- Progressive overload engine

### Phase 2 — Enhanced (Month 5–8)
- Volume analytics heatmap
- AI periodization plan generator
- Body measurement tracker
- 1RM trend charts
- Split generator
- Premium subscription launch

### Phase 3 — Advanced (Month 9–16)
- Real-time form analysis via webcam
- AI body composition photo estimation
- Recovery score (HRV + sleep + volume)
- Coach marketplace launch
- Smart gym equipment integration
- Supplement stack optimizer

---

*Document Version 1.0 — MusclePrismora PRD — PhotoIdentifier Platform | 2026-02-21*
