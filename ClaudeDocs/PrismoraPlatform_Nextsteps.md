# Prismora Platform — Comprehensive Build & Integration Plan
*All open-source technologies | Full-stack plan from design to deployment*

---

## Table of Contents

1. [Executive Overview](#executive-overview)
2. [Open-Source Technology Stack](#open-source-technology-stack)
3. [Platform Architecture](#platform-architecture)
4. [Unified Design System](#unified-design-system)
5. [Authentication & User Management](#authentication--user-management)
6. [Database Architecture](#database-architecture)
7. [Phase 1: Foundation (Months 1–4)](#phase-1-foundation-months-14)
8. [Phase 2: Expansion (Months 5–8)](#phase-2-expansion-months-58)
9. [Phase 3: Full Platform (Months 9–16)](#phase-3-full-platform-months-916)
10. [Phase 4: Scale & AI (Months 17–24)](#phase-4-scale--ai-months-1724)
11. [Sub-App Build Plans (All 17)](#sub-app-build-plans-all-17)
12. [Cross-App Integration Patterns](#cross-app-integration-patterns)
13. [Testing Strategy](#testing-strategy)
14. [Deployment & DevOps](#deployment--devops)
15. [Security & Compliance](#security--compliance)

---

## Executive Overview

The **PhotoIdentifier Prismora Platformlication** is a unified platform integrating **17 specialized AI identification sub-applications** under one authentication system, shared design language, and data platform. Each sub-app is independently valuable, but cross-app integration creates compounding value that no single competitor can match.

**17 Sub-Applications:**

| # | Brand Name | Domain | Core AI |
|---|---|---|---|
| 01 | CoinPrismora AI | Numismatics | EfficientNet-B4 coin classification |
| 02 | FitPrismora | Beginner Fitness | MoveNet pose estimation (TensorFlow.js) |
| 03 | VinylPrismora | Vinyl Records | CNN label recognition + Discogs API |
| 04 | NutriPrismora | Food Nutrition | Food detection + portion estimation CNN |
| 05 | RockPrismora AI | Geology | EfficientNet mineral identification |
| 06 | ShroomPrismora AI | Mycology (Safety) | Classification with safety bias |
| 07 | MusclePrismora | Advanced Fitness | MoveNet + RP-Strength periodization |
| 08 | InsectPrismora | Entomology | EfficientNetV2-L insect classification |
| 09 | BirdPrismora Pro | Birding | EfficientNet-B6 + BirdNET audio |
| 10 | NotePrismora | Banknotes | ResNet-50V2 banknote recognition |
| 11 | AquaPrismora Pro | Aquarium | EfficientNet fish + YOLOv8 disease |
| 12 | CardPrismora AI | Sports Cards | ResNet-50 card ID + PSA grade predictor |
| 13 | FloraLens AI | Plants | PlantNet API + EfficientNet-B7 |
| 14 | FruitPrismora | Fruit | EfficientNet-B4 + ripeness CNN |
| 15 | AutoPrismora AI | Vehicles | ResNet-101 + Mask R-CNN damage |
| 16 | PawPrismora AI | PawPrismoras | EfficientNet-B5 canine classification |
| 17 | MeowPrismora AI | MeowPrismoras | EfficientNet-B5 feline classification |

---

## Open-Source Technology Stack

All technologies below are open-source or have a generous free tier with no vendor lock-in.

### Frontend
| Layer | Technology | Rationale |
|---|---|---|
| Framework | Next.js 14 (App Router) | SSR, SSG, ISR, file-based routing |
| Language | TypeScript 5.x | Type safety across 17 sub-apps |
| Styling | TailwindCSS 3.x | Utility-first, shared design tokens |
| State | Zustand + React Query | Lightweight global state + server caching |
| 3D/AR | Three.js + WebXR Device API | Browser-native AR overlays |
| AI (browser) | TensorFlow.js + ONNX Runtime Web | Client-side inference (pose, plants) |
| Maps | MapLibre GL JS | Open-source Mapbox alternative |
| Charts | Recharts + Observable Plot | Data visualization |
| Video | Daily.co (open WebRTC) | Telehealth sessions |
| PWA | next-pwa | Offline support, installable |

### Backend
| Layer | Technology | Rationale |
|---|---|---|
| API Gateway | Kong (OSS) | Rate limiting, routing, auth plugins |
| Services | FastAPI (Python) | AI/ML microservices |
| Services | Node.js (Express) | Real-time, marketplace services |
| Auth | Supabase Auth | Open-source Firebase alternative |
| ORM | SQLAlchemy (Python), Prisma (Node) | Schema management |
| Queue | Apache Kafka | Event streaming between services |
| Cache | Redis 7 | Sessions, rate limiting, hot data |
| Search | Elasticsearch | Full-text search across all apps |

### AI Infrastructure
| Component | Technology |
|---|---|
| Model Serving | TensorFlow Serving + ONNX Runtime |
| Training | PyTorch + Hugging Face Transformers |
| Experiment Tracking | MLflow (OSS) |
| Feature Store | Feast (OSS) |
| Model Registry | MLflow Model Registry |
| Vector DB | Qdrant (OSS, self-hosted alternative to Pinecone) |

### Data Platform
| Component | Technology |
|---|---|
| Primary DB | PostgreSQL 16 |
| Time-Series | TimescaleDB extension |
| Object Storage | MinIO (OSS S3-compatible) |
| Data Warehouse | Apache Iceberg + Trino |
| Stream Processing | Apache Flink |

### DevOps
| Component | Technology |
|---|---|
| Containers | Docker + Docker Compose |
| Orchestration | Kubernetes (K8s) |
| CI/CD | GitHub Actions |
| IaC | Terraform |
| Monitoring | Grafana + Prometheus |
| Logging | Loki + Grafana |
| Tracing | Jaeger (OpenTelemetry) |
| Secrets | HashiCorp Vault |

---

## Platform Architecture

### High-Level System Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                     Next.js 14 PWA (Frontend)                      │
│   TypeScript + TailwindCSS + Zustand + React Query                 │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │  Sub-App Shell Router + Shared Layout & Navigation          │   │
│   │  CoinPrismora | FitPrismora | VinylPrismora | NutriPrismora | RockPrismora | ...   │   │
│   └─────────────────────────────────────────────────────────────┘   │
└───────────────────────────────┬─────────────────────────────────────┘
                                │ HTTPS/REST/WebSocket/gRPC
┌───────────────────────────────▼─────────────────────────────────────┐
│                   Kong API Gateway (OSS)                            │
│        JWT Auth | Rate Limiting | SSL | Routing | Logging          │
└──────┬──────────┬──────────┬──────────┬──────────┬─────────────────┘
       │          │          │          │          │
  ┌────▼───┐ ┌───▼────┐ ┌───▼────┐ ┌───▼────┐ ┌──▼───────────────┐
  │Auth    │ │Sub-App │ │AI Infra│ │Market  │ │Analytics &       │
  │Service │ │Svcs    │ │Service │ │place   │ │Notifications     │
  │(Supa.) │ │(17x)   │ │(Infer.)│ │Service │ │Service           │
  └────┬───┘ └───┬────┘ └───┬────┘ └────────┘ └──────────────────┘
       │         │          │
┌──────▼─────────▼──────────▼──────────────────────────────────────┐
│                    Shared Data Platform                           │
│  PostgreSQL 16 | Redis 7 | MinIO | TimescaleDB                    │
│  Qdrant (vector) | Elasticsearch | Apache Kafka                   │
└──────────────────────────────────────────────────────────────────┘
```

### Microservices Architecture

Each sub-app has its own microservice(s) following this pattern:
- **Identify Service** — photo upload → AI inference → result
- **Domain Service** — business logic (portfolio, tracker, marketplace)
- **Data Service** — CRUD for domain entities

Shared platform services:
- **Auth Service** — Supabase Auth + custom JWT claims
- **Notification Service** — push + email (using Resend OSS)
- **Analytics Service** — event tracking, usage metrics
- **AI Inference Service** — model serving hub (TensorFlow Serving)
- **Marketplace Service** — shared commerce backend
- **Search Service** — Elasticsearch cross-app search

---

## Unified Design System

All 17 sub-apps share one consistent design system. This is the critical differentiator of the platform feel.

### Design Tokens

```css
/* Typography */
--font-sans: 'Inter', system-ui, sans-serif;
--font-weight-regular: 400;
--font-weight-semibold: 600;
--font-weight-bold: 700;

/* Color Palette */
--color-primary: #6366F1;      /* Indigo — brand identity */
--color-emerald: #10B981;      /* Success, PRs, authentic */
--color-amber: #F59E0B;        /* Warning, alerts, highlights */
--color-red: #EF4444;          /* Error, danger, counterfeit */
--color-rose: #F43F5E;         /* Cat app accent */
--color-teal: #14B8A6;         /* Aquarium app accent */
--color-background: #FFFFFF;
--color-surface: #F9FAFB;

/* Spacing (4px base unit) */
--space-1: 4px;   --space-2: 8px;   --space-3: 12px;
--space-4: 16px;  --space-6: 24px;  --space-8: 32px;
--space-12: 48px; --space-16: 64px;

/* Border Radius */
--radius-sm: 4px;   /* badges */
--radius-md: 8px;   /* buttons, inputs */
--radius-lg: 12px;  /* cards */
--radius-xl: 16px;  /* modals */
--radius-full: 9999px; /* pills */

/* Shadows (5-level elevation) */
--shadow-1: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow-2: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
--shadow-3: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
--shadow-4: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
--shadow-5: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
```

### Universal Components (Shared Library)
- `PhotoCapture` — camera/upload with AI-guided overlays
- `ConfidenceCard` — species/object result with confidence bar
- `SafetyBadge` — color-coded safety/toxicity indicator
- `MarketCard` — collectible valuation card
- `HealthMetricRing` — circular progress for health/fitness metrics
- `MapView` — MapLibre GL wrapper for range/sighting maps
- `Timeline` — chronological log for health records, collections
- `TelehealthModal` — WebRTC video call launcher

---

## Authentication & User Management

### Architecture: Supabase Auth (Self-Hosted)

```
User → Next.js Login Page → Supabase Auth → JWT Token
                                          ↓
                              Kong validates JWT on every request
                                          ↓
                              Microservices use user_id from JWT claims
```

### Authentication Flows
1. **Email/Password** — Supabase built-in bcrypt hashing
2. **Google OAuth 2.0** — Supabase OAuth provider
3. **Apple Sign-In** — for iOS-adjacent web users
4. **Magic Link (passwordless)** — email OTP
5. **SSO across all sub-apps** — single JWT, platform-wide session

### User Roles & Permissions

| Role | Capabilities |
|---|---|
| `free` | Access to all sub-apps with usage limits |
| `premium_single` | Unlimited access to one chosen sub-app |
| `premium_platform` | Unlimited access to all 17 sub-apps |
| `coach` | MusclePrismora/FitPrismora coach panel + client management |
| `vet` | PawPrismora/MeowPrismora telehealth dashboard |
| `fleet_manager` | AutoPrismora fleet bulk operations |
| `admin` | Platform administration |

### Database Tables: Auth Domain

```sql
-- Core user table (extends Supabase auth.users)
CREATE TABLE user_profiles (
  user_id        UUID PRIMARY KEY REFERENCES auth.users(id),
  display_name   VARCHAR(100),
  username       VARCHAR(50) UNIQUE,
  avatar_url     TEXT,
  preferred_unit ENUM('metric', 'imperial') DEFAULT 'metric',
  locale         VARCHAR(10) DEFAULT 'en',
  subscription   ENUM('free', 'premium_single', 'premium_platform') DEFAULT 'free',
  premium_app    VARCHAR(50),  -- which app if premium_single
  created_at     TIMESTAMPTZ DEFAULT NOW(),
  updated_at     TIMESTAMPTZ DEFAULT NOW()
);

-- Subscription tracking
CREATE TABLE subscriptions (
  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id         UUID REFERENCES user_profiles(user_id),
  plan            VARCHAR(50),
  stripe_sub_id   VARCHAR(100),
  status          VARCHAR(20),
  current_period_start TIMESTAMPTZ,
  current_period_end   TIMESTAMPTZ,
  canceled_at     TIMESTAMPTZ
);

-- User app permissions (which apps user has activated)
CREATE TABLE user_app_permissions (
  user_id    UUID REFERENCES user_profiles(user_id),
  app_id     VARCHAR(50),
  tier       VARCHAR(20),
  granted_at TIMESTAMPTZ DEFAULT NOW(),
  PRIMARY KEY (user_id, app_id)
);
```

---

## Database Architecture

### Design Principles
1. **Schema-per-app isolation** — each sub-app has its own PostgreSQL schema
2. **Shared user identity** — all schemas reference `public.user_profiles`
3. **Event sourcing via Kafka** — cross-app events (e.g., NutriPrismora ↔ FruitPrismora sync)
4. **TimescaleDB for time-series** — all health/tracking data uses hypertables
5. **Qdrant for vectors** — CLIP embeddings for visual similarity search

### PostgreSQL Schema Organization

```sql
-- Platform schemas
CREATE SCHEMA public;       -- user_profiles, subscriptions
CREATE SCHEMA auth;         -- Supabase auth tables

-- Sub-app schemas
CREATE SCHEMA coinsnap;     -- coins, collections, market data
CREATE SCHEMA lazyfit;      -- workouts, sessions, form_logs
CREATE SCHEMA vinylsnap;    -- records, collections, valuations
CREATE SCHEMA calo;         -- foods, meals, nutrition_logs
CREATE SCHEMA rockid;       -- specimens, identifications, geolocations
CREATE SCHEMA mushroom;     -- species, sightings, safety_classifications
CREATE SCHEMA musclefit;    -- programs, sessions, exercises, sets
CREATE SCHEMA insectid;     -- species, sightings, pest_alerts
CREATE SCHEMA birdid;       -- species, sightings, life_lists
CREATE SCHEMA notesnap;     -- banknotes, collections, fx_rates
CREATE SCHEMA fishcare;     -- species, tanks, water_params, diseases
CREATE SCHEMA cardvault;    -- cards, collections, price_history
CREATE SCHEMA plantid;      -- species, user_plants, disease_logs
CREATE SCHEMA fruitid;      -- fruits, ripeness_assessments, fruit_logs
CREATE SCHEMA vehicleid;    -- vehicles, garages, recalls, damage_reports
CREATE SCHEMA dogbreed;     -- breeds, user_pets, health_records
CREATE SCHEMA catbreed;     -- breeds, user_cats, daily_checkins
```

---

## Phase 1: Foundation (Months 1–4)

### Sprint Structure (2-week sprints)

**Sprint 1–2: Platform Infrastructure**
- [ ] Set up monorepo (Turborepo) with Next.js 14 shell
- [ ] Configure Kong API Gateway with JWT authentication plugin
- [ ] Deploy self-hosted Supabase (Auth + Postgres) on Kubernetes
- [ ] Set up MinIO for object storage
- [ ] Configure Redis 7 cluster (sessions + caching)
- [ ] Set up Apache Kafka for event streaming
- [ ] Build CI/CD pipeline (GitHub Actions → Docker → K8s)
- [ ] Configure Grafana + Prometheus monitoring

**Sprint 3–4: Design System & Shared Components**
- [ ] Create `@photoidentifier/ui` shared component library
- [ ] Implement all design tokens in TailwindCSS config
- [ ] Build PhotoCapture universal component
- [ ] Build ConfidenceCard, SafetyBadge, HealthMetricRing components
- [ ] Build global navigation (sub-app switcher)
- [ ] Build notification center (shared)
- [ ] Auth flows: Login/Register/Magic Link/OAuth

**Sprint 5–6: AI Inference Infrastructure**
- [ ] Deploy TensorFlow Serving on K8s
- [ ] Deploy ONNX Runtime for browser-compatible model serving
- [ ] Set up MLflow for experiment tracking
- [ ] Build model upload + version registry workflow
- [ ] Create AI service base class (FastAPI template)
- [ ] Implement image preprocessing pipeline (resize, normalize)

**Sprint 7–8: First 4 Sub-Apps (MVP)**
- [ ] **NutriPrismora** — Food identification + nutrition display
- [ ] **PlantIdentifier** — PlantNet integration + toxicity
- [ ] **PawPrismora** — Dog breed classification
- [ ] **MeowPrismora** — Cat breed classification

### Phase 1 Acceptance Criteria
- All 4 MVP apps handle photo upload → AI result in < 3 seconds
- Authentication works across all apps with single sign-on
- 99.9% uptime on platform infrastructure
- Mobile-responsive PWA installable on iOS/Android

---

## Phase 2: Expansion (Months 5–8)

**Launch 8 more sub-apps:**

| App | Key Phase 2 Features |
|---|---|
| **CoinPrismora** | Coin ID + collection management + eBay valuation |
| **VinylPrismora** | Label recognition + Discogs market prices |
| **RockPrismora** | Mineral ID + Mohs hardness + geological context |
| **ShroomPrismora** | Mushroom ID + mandatory safety warnings + offline toxic species |
| **InsectPrismora** | Insect ID + pest risk + invasive species alert |
| **BirdPrismora Pro** | Bird photo + audio ID + eBird submission |
| **NotePrismora** | Banknote ID + live exchange rates |
| **FruitPrismora** | Fruit ID + nutrition + ripeness + NutriPrismora sync |

**Cross-App Integration Sprint (Month 7–8):**
- [ ] NutriPrismora ↔ FruitPrismora nutrition sync (Kafka event: `fruit.logged`)
- [ ] PawPrismora ↔ MeowPrismora shared vet telehealth booking system
- [ ] PlantIdentifier → ShroomPrismora lookalike warnings
- [ ] InsectPrismora → PlantIdentifier invasive species cross-alert

**Monetization Sprint (Month 8):**
- [ ] Stripe integration (subscriptions + one-time purchases)
- [ ] Freemium limits: 20 IDs/day free; unlimited premium
- [ ] Premium single-app ($4.99/month) + Platform Pass ($14.99/month)
- [ ] PayPal as alternative payment method

---

## Phase 3: Full Platform (Months 9–16)

**Launch final 5 sub-apps:**

| App | Key Features |
|---|---|
| **FitPrismora** | Beginner workouts + MoveNet form correction (in-browser) |
| **MusclePrismora** | Advanced periodization + volume analytics + coaching marketplace |
| **AquaPrismora Pro** | Fish ID + disease diagnosis + 3D aquascape designer |
| **CardPrismora AI** | Sports card scan + PSA grade predictor + portfolio |
| **AutoPrismora AI** | Vehicle ID + VIN decode + NHTSA recall check + damage estimation |

**Advanced Cross-App Integrations:**
- [ ] FitPrismora → MusclePrismora level upgrade (beginner → intermediate handoff)
- [ ] MusclePrismora ↔ NutriPrismora calorie/macro sync for body recomposition
- [ ] AutoPrismora → insurance quote aggregator
- [ ] PawPrismora/MeowPrismora → vet telehealth platform (shared Daily.co infrastructure)

---

## Phase 4: Scale & AI (Months 17–24)

- [ ] AR features: Plant planner, Vehicle customizer, Insect overlay (WebXR)
- [ ] AI personalization engine (cross-app recommendations)
- [ ] Global B2B API portal (white-label AI identification)
- [ ] Open marketplace for community content across all apps
- [ ] Advanced analytics dashboard (admin)
- [ ] Multi-data-center deployment (EU region for GDPR)

---

## Sub-App Build Plans (All 17)

### 01 CoinPrismora / CoinPrismora AI

**User Stories:**
- *As a coin collector, I want to photograph a coin and see its country, denomination, year, and current value.*
- *As a numismatist, I want to track my collection portfolio with purchase vs. current value.*
- *As a buyer, I want AI counterfeit detection before purchasing an expensive rare coin.*

**Acceptance Criteria (MVP):**
- ≥90% accuracy on 10,000 world coin test set
- Identifies: country, denomination, year, mint mark
- Shows current eBay/PCGS market value
- Collection save within 1 second of identification

**Key Technical Components:**
- Model: EfficientNet-B4 fine-tuned on 500k+ coin images
- Visual similarity: Qdrant vector search with CLIP embeddings
- Integrations: PCGS API, NGC API, eBay Finding API
- Database schema: `coinsnap.coins`, `coinsnap.user_collection`, `coinsnap.market_prices`

**API Endpoints:**
```
POST /api/v1/coinsnap/identify          # Photo → coin identification
GET  /api/v1/coinsnap/coins/{id}        # Coin detail + market value
POST /api/v1/coinsnap/collection        # Add coin to collection
GET  /api/v1/coinsnap/portfolio         # Portfolio value summary
POST /api/v1/coinsnap/counterfeit-check # Counterfeit analysis (Phase 3)
```

---

### 02 FitPrismora

**User Stories:**
- *As a beginner, I want a 10-minute workout with no equipment that shows me exactly how to do each exercise.*
- *As a new exerciser, I want real-time form correction via my laptop camera.*
- *As a user, I want the app to automatically increase difficulty as I get fitter.*

**Acceptance Criteria (MVP):**
- 50+ workouts; 5–20 min; tagged by duration, body part, difficulty
- Form error detection < 1 second feedback via MoveNet
- Workout completion rate tracked; adaptive difficulty engine

**Key Technical Components:**
- Model: MoveNet (TensorFlow.js — runs entirely in-browser, no server upload)
- Form analysis: Rule-based joint angle thresholds on MoveNet keypoints
- Integration: MusclePrismora handoff when user reaches intermediate readiness
- Database: `lazyfit.workouts`, `lazyfit.sessions`, `lazyfit.form_logs`

---

### 03 VinylPrismora

**User Stories:**
- *As a record collector, I want to photograph a vinyl label and see the pressing variant and current Discogs market value.*
- *As a seller, I want condition grading guidance before listing on Discogs.*
- *As a DJ, I want audio fingerprinting to identify a record by playing 10 seconds of it.*

**Acceptance Criteria (MVP):**
- ≥85% label recognition accuracy
- Discogs market data displayed within 2 seconds of identification
- Collection management with CSV export

**Key Components:**
- Model: Custom CNN for label recognition + Discogs API for market data
- Audio fingerprinting: AcoustID / Chromaprint for audio identification
- Database: `vinylsnap.records`, `vinylsnap.pressings`, `vinylsnap.user_collection`

---

### 04 NutriPrismora

**User Stories:**
- *As a dieter, I want to photograph my plate and see calorie and macro breakdown instantly.*
- *As a diabetic, I want to see carbohydrate content before eating.*
- *As a FruitPrismora user, I want fruit scans to auto-add to my NutriPrismora diary.*

**Acceptance Criteria (MVP):**
- ≥85% top-1 accuracy on 1,000 common dishes
- Portion estimate within ±20% weight
- NutriPrismorarie ring UI showing daily progress
- Macro breakdown (protein/carbs/fat) displayed per meal

**Key Components:**
- Model: Custom food detection CNN + portion regression model
- Integration: USDA FoodData Central API, FruitPrismora (fruit sync via Kafka)
- Database: `calo.foods`, `calo.meal_logs`, `calo.daily_summaries`

---

### 05 RockPrismora AI / RockPrismora

**User Stories:**
- *As a geologist, I want to photograph a rock sample and identify the mineral with Mohs hardness and chemical formula.*
- *As a gemstone buyer, I want AI valuation before purchasing at a gem show.*
- *As a field researcher, I want GPS-tagged rock sample logs for my survey.*

**Acceptance Criteria (MVP):**
- ≥88% accuracy on 1,000 mineral/rock test set
- Mohs hardness, chemical formula, crystal system displayed
- GPS sighting log with offline capability

**Key Components:**
- Model: EfficientNet fine-tuned on Mindat.org dataset
- Integrations: Mindat.org API, GeoJSON maps (MapLibre GL)
- Database: `rockid.specimens`, `rockid.identifications`, `rockid.geolocations`

---

### 06 ShroomPrismora AI / ShroomPrismora

**User Stories:**
- *As a forager, I want to photograph a mushroom and see its edibility and toxic lookalikes with clear safety warnings.*
- *As a hiker, I want offline access to the 20 most deadly species so I can identify them without internet.*
- *As a parent, I want an immediate poison control hotline link if a dangerous mushroom is identified.*

**Acceptance Criteria — SAFETY CRITICAL:**
- Classification model biased toward safety (false positive warnings preferred over false negatives)
- Mandatory disclaimer displayed on EVERY identification result
- Poison Control hotline numbers displayed on all Toxic/Deadly results
- Offline database of top 50 deadly species bundled with app
- External safety audit by certified mycologist required before production launch

**Key Components:**
- Model: EfficientNet with safety-biased classification head
- Offline data: Service worker caches deadly species dataset
- Database: `mushroom.species`, `mushroom.sightings`, `mushroom.safety_classifications`

---

### 07 MusclePrismora / MusclePrismora

**User Stories:**
- *As a powerlifter, I want a 16-week periodized program with automatic deload week scheduling.*
- *As a physique athlete, I want AI body composition estimation from photos without expensive DEXA scans.*
- *As an online coach, I want a dashboard to manage 30 clients and push program updates.*

**Acceptance Criteria (MVP):**
- 12 pre-built program templates (PPL, 5/3/1, Arnold Split, GZCLP, etc.)
- Set logging < 200ms from tap to confirmation
- PR detection on every logged set
- Offline workout session logging

**Key Components:**
- Periodization: RP-Strength volume landmark algorithmic model
- Body comp: Custom CNN trained on physique photos + DEXA ground truth
- Integration: NutriPrismora (calorie/macro sync), FitPrismora (beginner handoff)
- Coaching: Stripe Connect for coach marketplace payments
- Database: `musclefit.programs`, `musclefit.sessions`, `musclefit.exercise_sets`, `musclefit.body_comp_logs`

---

### 08 InsectPrismora / InsectPrismora

**User Stories:**
- *As a farmer, I want to photograph a pest on my crop and get immediate treatment recommendations.*
- *As a gardener, I want to know if the insect I found is beneficial or harmful.*
- *As a child, I want to earn badges for each new insect species I discover (Kids Mode).*

**Acceptance Criteria (MVP):**
- ≥90% correct order, ≥80% correct species on 200k species test set
- 4-level danger system (Harmless/Mildly Venomous/Venomous/Dangerous)
- Invasive species alert with authority reporting link
- COPPA-compliant Kids Mode (zero personal data)

**Key Components:**
- Model: EfficientNetV2-L fine-tuned on iNaturalist 2.7M insect images
- Integrations: iNaturalist API, GBIF, CABI Invasive Species Compendium
- Database: `insectid.species`, `insectid.sightings`, `insectid.pest_alerts`

---

### 09 BirdPrismora Pro / BirdPrismora

**User Stories:**
- *As a birder, I want photo AND song identification so I can identify birds I hear but can't see.*
- *As a life-lister, I want my sightings to automatically integrate with eBird.*
- *As a teacher, I want a classroom mode where students can log sightings for a school project.*

**Acceptance Criteria (MVP):**
- Photo ID: ≥90% top-1 on 10,000 species (Cornell Lab test set)
- Audio ID: ≥80% accuracy on Xeno-canto test clips
- eBird sighting submission via OAuth
- Life list tracker with species count

**Key Components:**
- Photo model: EfficientNet-B6 fine-tuned on 140M Cornell Lab bird images
- Audio model: BirdNET (Cornell Lab open-source model)
- Integrations: Cornell eBird API, BirdCast migration API, Xeno-canto API
- Database: `birdid.species`, `birdid.sightings`, `birdid.life_lists`

---

### 10 NotePrismora / NotePrismora

**User Stories:**
- *As a traveler, I want to photograph foreign currency and see the value in my home currency instantly.*
- *As a market trader, I want counterfeit detection before accepting a high-value banknote.*
- *As a collector, I want to catalog my banknote collection with PMG valuation data.*

**Acceptance Criteria (MVP):**
- ≥90% recognition on 190+ country banknotes
- Live exchange rate displayed (hourly update)
- Security feature guide per identified note
- Collection catalog with condition grading

**Key Components:**
- Model: ResNet-50V2 trained on 200k banknote images
- Counterfeit: Texture anomaly detection CNN (Phase 3)
- Integrations: Open Exchange Rates API, PMG Price Guide, OCR for serial numbers
- Database: `notesnap.banknotes`, `notesnap.user_notes`, `notesnap.fx_cache`

---

### 11 AquaPrismora Pro / AquaPrismora

**User Stories:**
- *As a beginner, I want to photograph a fish at the pet store and know if it will fit in my tank.*
- *As a hobbyist, I want to photograph my sick fish and get a disease diagnosis with treatment protocol.*
- *As an aquascaper, I want a 3D browser-based tool to plan my aquarium layout before buying plants.*

**Acceptance Criteria (MVP):**
- ≥88% fish species identification across 3,000 aquarium species
- Disease symptom checker covers 50 most common diseases
- Tank compatibility checker from FishBase data
- Water parameter log with line charts

**Key Components:**
- Fish ID: EfficientNet fine-tuned on FishBase + iNaturalist
- Disease: YOLOv8 for lesion detection + classification head
- 3D Designer: Three.js WebGL aquascape editor
- Integrations: FishBase API, Seneye IoT API, Daily.co (vet telehealth)
- Database: `fishcare.species`, `fishcare.tanks`, `fishcare.water_params`, `fishcare.disease_logs`

---

### 12 CardPrismora AI / CardPrismora

**User Stories:**
- *As a collector, I want to scan a sports card and know its exact parallel, set, and current market value.*
- *As an investor, I want an AI grade predictor before spending $50 on PSA submission.*
- *As a dealer, I want to scan 50 cards per hour at a card show.*

**Acceptance Criteria (MVP):**
- ≥88% card identification (player, year, set, parallel) on 1M card test scan
- Card identified < 2 seconds
- eBay 90-day sales history chart
- Collection catalog with CSV export

**Key Components:**
- Model: ResNet-50 + OCR pipeline for text extraction
- Grade predictor: Multi-image ResNet-101 trained on 500k PSA-graded photos
- Integrations: eBay Finding API, PSA Population Report, PWCC Marketplace
- Database: `cardvault.cards`, `cardvault.user_cards`, `cardvault.price_history`

---

### 13 FloraLens AI / FloraPrismora

**User Stories:**
- *As a parent, I want to photograph any houseplant and know immediately if it's toxic to my child or pet.*
- *As a gardener, I want AI leaf disease diagnosis before choosing a fungicide.*
- *As a plant parent, I want watering reminders customized per species.*

**Acceptance Criteria (MVP):**
- ≥90% top-1 identification on PlantNet test set (400,000 species)
- Toxicity warning (ASPCA + Poison Control database)
- Care guide: watering, sunlight, soil, humidity
- My Garden with unlimited plant tracking and reminders

**Key Components:**
- Model: PlantNet API backbone + EfficientNet-B7 fine-tune
- Disease: PlantVillage CNN (54 disease classes, 98.3% accuracy)
- Integrations: PlantNet API, ASPCA Toxic Plant DB, iNaturalist, Gardena smart watering
- Database: `plantid.species`, `plantid.user_plants`, `plantid.disease_logs`

---

### 14 FruitPrismora / FruitPrismora

**User Stories:**
- *As a traveler, I want to photograph an exotic fruit and learn what it is and how to eat it.*
- *As a diabetic, I want glycemic index data for any fruit before eating.*
- *As a NutriPrismora user, I want fruit scans to auto-sync to my daily calorie diary.*

**Acceptance Criteria (MVP):**
- ≥90% identification on 1,000+ fruit varieties
- Nutritional profile from USDA FoodData Central
- Ripeness assessment: ≥78% agreement with expert visual panel
- NutriPrismora integration active for nutrition sync

**Key Components:**
- Model: EfficientNet-B4 fine-tuned on Fruits-360 + 50k exotic image set
- Ripeness: Color histogram analysis + CNN regression
- Integrations: USDA FoodData Central, International GI Database, NutriPrismora Internal API
- Database: `fruitid.fruits`, `fruitid.ripeness_assessments`, `fruitid.fruit_logs`

---

### 15 AutoPrismora AI / AutoPrismora

**User Stories:**
- *As a car buyer, I want to photograph a car on a dealer lot and see its market value and any open safety recalls.*
- *As an enthusiast, I want to identify a rare classic car down to the specific trim and year variant.*
- *As a fleet manager, I want to bulk-import 200 VINs and receive a depreciation report.*

**Acceptance Criteria (MVP):**
- ≥88% make/model accuracy on 500k vehicle image test set
- KBB market value displayed
- EPA fuel economy shown
- My Garage saves up to 50 vehicles (free)

**Key Components:**
- Model: ResNet-101 fine-tuned on 1.5M labeled vehicle images
- Damage: Mask R-CNN + XGBoost repair cost regression
- Integrations: NHTSA API, KBB API, MarketCheck, EPA Fuel Economy, NICB Stolen Vehicle
- Database: `vehicleid.vehicles`, `vehicleid.garages`, `vehicleid.damage_reports`, `vehicleid.recalls`

---

### 16 PawPrismora AI / PawPrismora

**User Stories:**
- *As a rescue adopter, I want to photograph my dog and see its breed composition with a pie chart breakdown.*
- *As a first-time owner, I want a 12-week training plan designed for my specific breed.*
- *As a worried owner at midnight, I want AI symptom triage to know if I need an emergency vet.*

**Acceptance Criteria (MVP):**
- ≥88% top-1 breed accuracy on Stanford Dogs dataset (120 breeds)
- Mixed breed composition shown (visual pie chart)
- Breed profile: energy, shedding, trainability, health risks
- My Dog profile with vaccination tracker

**Key Components:**
- Model: EfficientNet-B5 fine-tuned on 2M images across 500+ breeds
- Mixed breed: Ensemble with breed probability vector output
- Behavior analysis: MoveNet Multipose + custom behavior classification
- Integrations: AKC/FCI breed standards, Embark DNA API, Whistle GPS API
- Database: `dogbreed.breeds`, `dogbreed.user_pets`, `dogbreed.health_records`, `dogbreed.telehealth_sessions`

---

### 17 MeowPrismora AI / MeowPrismora

**User Stories:**
- *As a rescue cat owner, I want to photograph my cat and see its breed composition and whether its behaviors are breed-typical.*
- *As a multi-cat owner, I want a daily photo check-in that flags any unusual physical changes.*
- *As a cat owner, I want a body condition score (BCS) from a photo to catch obesity early.*

**Acceptance Criteria (MVP):**
- ≥88% breed accuracy (80+ breeds + mixed)
- My Cats profile: name, DOB, breed, weight, photo
- Health record tracker: vaccines, vet visits, medications
- BCS photo analysis (Phase 2): ≥80% agreement with vet assessment

**Key Components:**
- Model: EfficientNet-B5 fine-tuned on Oxford Cats + 400k proprietary images
- BCS: Multi-angle CNN regression (1-9 BCS scale)
- Illness detection: LSTM time-series on daily photo + behavioral log delta
- Integrations: TICA/CFA breed standards, Basepaws DNA API, Daily.co
- Database: `catbreed.breeds`, `catbreed.user_cats`, `catbreed.health_logs`, `catbreed.daily_checkins`

---

## Cross-App Integration Patterns

### Event-Driven Architecture (Apache Kafka)

All cross-app communication uses Kafka events. Services subscribe only to topics relevant to them.

```
Topic: food.logged
  Publisher: calo-service
  Subscriber: fruitid-service (if fruit was source)
  Payload: { user_id, food_id, quantity_g, calories, macros, source_app }

Topic: fruit.scanned
  Publisher: fruitid-service
  Subscriber: calo-service (auto-log nutrition)
  Payload: { user_id, fruit_id, quantity_g, ripeness_stage }

Topic: fitness.session.completed
  Publisher: lazyfit-service OR musclefit-service
  Subscriber: calo-service (calorie burn sync)
  Payload: { user_id, duration_min, calories_burned, session_type }

Topic: plant.identified
  Publisher: plantid-service
  Subscriber: mushroom-service (toxic lookalike check)
  Payload: { user_id, species_id, is_edible, toxicity_level }

Topic: pet.health.alert
  Publisher: dogbreed-service OR catbreed-service
  Subscriber: notification-service (push alert to user)
  Payload: { user_id, pet_id, alert_type, severity, message }
```

### Key Cross-App Synergies

| Integration | Trigger | Result |
|---|---|---|
| NutriPrismora ↔ FruitPrismora | Fruit scan | Auto-log fruit nutrition to NutriPrismora diary |
| NutriPrismora ↔ MusclePrismora | Workout session completed | NutriPrismorarie burn added to NutriPrismora daily total |
| MusclePrismora ↔ NutriPrismora | Body recomposition goal | NutriPrismorarie target adjusted per training phase |
| FitPrismora → MusclePrismora | User completion streak | Beginner-to-intermediate level handoff prompt |
| PlantIdentifier → ShroomPrismora | Plant identified as mushroom-adjacent | Cross-reference toxic lookalike warning |
| PawPrismora ↔ MeowPrismora | Telehealth booking | Shared vet scheduling backend (same Daily.co room system) |
| AutoPrismora → Insurance | Vehicle identified | Pre-fill insurance quote form with full spec |
| InsectPrismora → PlantIdentifier | Invasive insect found on plant | Cross-alert: plant pest warning |

---

## Testing Strategy

### Unit Testing
- **Frontend:** Vitest + React Testing Library
- **Backend Python:** pytest + pytest-asyncio
- **Backend Node:** Jest + Supertest
- **Coverage targets:** ≥80% line coverage on business logic; 100% on safety-critical paths (ShroomPrismora, toxicity warnings)

### Integration Testing
- **API contract tests:** Pact (consumer-driven contract testing)
- **Database integration:** pytest-postgresql (isolated test DB per test suite)
- **Kafka integration:** Embedded Kafka (kafka-python) for event flow tests
- **AI inference mocking:** Recorded fixture responses for deterministic test runs

### End-to-End Testing
- **Framework:** Playwright (TypeScript)
- **Browser matrix:** Chrome, Firefox, Safari, Edge, Mobile Chrome
- **Key E2E flows per sub-app:**
  - Photo upload → AI result displayed
  - Authentication (login, logout, session persistence)
  - Cross-app data sync (e.g., NutriPrismora ↔ FruitPrismora)
  - Payment flow (Stripe test mode)
  - Offline functionality (PWA service worker)

### AI Model Testing
- **Accuracy benchmarking:** Automated nightly test on held-out validation sets
- **Bias testing:** Evaluate performance across geographic regions and demographics
- **Regression testing:** No new model deployed if accuracy drops >1% vs. baseline
- **Safety testing (ShroomPrismora):** Zero tolerance for misclassifying deadly species as safe

### Performance Testing
- **Load testing:** k6 (JavaScript, open-source)
- **Target thresholds:**
  - API p95 latency < 500ms (non-AI)
  - AI identification p95 < 3 seconds
  - 10,000 concurrent users without degradation
- **Chaos engineering:** Chaos Monkey (K8s pod failure simulation)

### Security Testing
- **SAST:** Semgrep (OSS) on every CI push
- **DAST:** OWASP ZAP automated scan on staging
- **Dependency scanning:** Dependabot + Snyk
- **Penetration testing:** Annual third-party pentest (quarterly for Phase 3+)
- **OWASP Top 10:** Automated checks in CI pipeline

### Test Automation Pipeline
```yaml
# GitHub Actions workflow (simplified)
on: [push, pull_request]
jobs:
  test:
    steps:
      - unit-tests      # Vitest + pytest + Jest
      - integration     # Pact + pytest-postgresql
      - security-scan   # Semgrep + Snyk
      - build           # Docker image build
  e2e:
    steps:
      - deploy-staging  # Kubernetes deploy
      - playwright-tests
      - k6-load-test
      - report          # Allure test report
```

---

## Deployment & DevOps

### Infrastructure Architecture

```
GitHub Actions CI/CD
    │
    ▼ on merge to main
Docker Registry (GitHub Container Registry)
    │
    ▼
Kubernetes Cluster (Production)
    ├── Namespace: platform (auth, gateway, notification)
    ├── Namespace: sub-apps (17 service namespaces)
    ├── Namespace: ai-inference (TF Serving, ONNX)
    ├── Namespace: data (Postgres, Redis, Kafka, MinIO)
    └── Namespace: monitoring (Grafana, Prometheus, Loki)
```

### Kubernetes Deployment Pattern (per sub-app)

```yaml
# Example: coinsnap-service Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: coinsnap-service
  namespace: sub-apps
spec:
  replicas: 2
  selector:
    matchLabels:
      app: coinsnap-service
  template:
    spec:
      containers:
      - name: coinsnap-service
        image: ghcr.io/photoidentifier/coinsnap-service:latest
        resources:
          requests:
            memory: "256Mi"
            cpu: "200m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secrets
              key: coinsnap-url
```

### Deployment Environments

| Environment | Purpose | Update Frequency |
|---|---|---|
| Development | Local Docker Compose | Per developer |
| Staging | K8s cluster (1 replica) | Every PR merge |
| Production | K8s cluster (2+ replicas, auto-scale) | Manual approval after staging |
| Canary | 5% of production traffic to new version | Rolling deployments |

### CI/CD Pipeline (GitHub Actions)

```
Feature Branch Push:
  → Run unit + integration tests
  → Security scan (Semgrep + Snyk)
  → Build Docker image
  → Push to container registry

PR to main:
  → All above + E2E tests on preview environment
  → Pact contract verification
  → Load test on staging

Merge to main:
  → Deploy to staging
  → Run smoke tests
  → Await manual approval
  → Blue/green deploy to production
  → Automated rollback if error rate > 1%
```

### Monitoring & Observability

```
Metrics:     Prometheus → Grafana dashboards
Logs:        Loki (structured JSON logs) → Grafana Explore
Traces:      Jaeger (OpenTelemetry) → distributed request tracing
Alerts:      AlertManager → PagerDuty / Slack
Uptime:      Grafana Synthetic Monitoring (external probes)
Error tracking: GlitchTip (OSS Sentry alternative)
```

### Key Dashboards to Build
1. **Platform Overview** — active users, identification/day per app, error rates
2. **AI Performance** — accuracy trends per model, inference latency, model drift
3. **Business Metrics** — subscription conversions, revenue by app, feature adoption
4. **Infrastructure** — pod CPU/memory, DB connections, Kafka consumer lag
5. **Safety Dashboard** — ShroomPrismora warning display rate, safety path adherence

---

## Security & Compliance

### Core Security Controls

| Control | Implementation |
|---|---|
| Authentication | Supabase Auth + JWT (RS256) |
| Authorization | Kong JWT plugin + per-route RBAC |
| Secrets | HashiCorp Vault + K8s Secrets |
| Encryption at rest | AES-256 (PostgreSQL, MinIO) |
| Encryption in transit | TLS 1.3 everywhere |
| Rate limiting | Kong rate-limit plugin per user/IP |
| Input validation | Pydantic (Python), Zod (TypeScript) |
| SQL injection | SQLAlchemy ORM (parameterized queries only) |
| XSS | Next.js automatic escaping + CSP headers |
| CSRF | SameSite=Strict cookies + CSRF tokens |
| File upload | Type validation + max size + antivirus scan (ClamAV) |

### Compliance Requirements

| Standard | Scope | Implementation |
|---|---|---|
| GDPR | EU users | Data export API, right to deletion, DPA agreements |
| CCPA | California users | Privacy notice, opt-out, data deletion |
| COPPA | InsectPrismora Kids Mode | Zero PII collection for under-13 users |
| HIPAA-adjacent | Pet health, body comp photos | Role-based access, audit logging |
| FERPA | BirdPrismora classroom tier | Student data isolation |
| PCI DSS | Stripe integration only | No card data on platform servers |

### Safety-Critical App Protocols

**ShroomPrismora AI (Mushroom Identifier):**
1. Every result page displays mandatory disclaimer: *"NEVER eat a wild mushroom based solely on AI identification. Consult an expert mycologist."*
2. Poison Control hotlines displayed (US: 1-800-222-1222, EU links)
3. Accuracy threshold: if confidence < 70%, display "Unable to identify safely — seek expert advice"
4. External mycologist safety audit required before launch
5. Offline toxic species database cached by service worker

**FloraLens AI (FloraPrismora):**
1. Toxicity badge visible before any other content on plant result page
2. ASPCA and Poison Control links for severe toxicity classifications
3. Disclaimer: *"Do not consume any wild plant based solely on AI identification"*

**AutoPrismora AI (damage, stolen vehicle):**
1. Rate limit: 20 plate checks/day (free), 200/day (premium)
2. Anomaly detection flags bulk plate queries
3. Damage reports labeled: *"AI estimate — not a certified appraisal"*

---

## Immediate Next Steps (Action Items)

### Week 1–2 (Start Now)
1. **Set up monorepo** — Initialize Turborepo with Next.js 14 root app
2. **Spin up local dev stack** — Docker Compose with Postgres, Redis, MinIO, Kong
3. **Deploy Supabase self-hosted** — Auth service with email + Google OAuth
4. **Create design system** — `packages/ui` with TailwindCSS tokens + core components
5. **Scaffold first sub-app** — PlantIdentifier (highest user demand; clearest AI pipeline)

### Week 3–4
6. **Integrate PlantNet API** — First AI identification endpoint live
7. **Build PhotoCapture component** — Universal camera/upload UI for all 17 apps
8. **Set up AI inference pipeline** — Docker container with model serving + FastAPI wrapper
9. **Configure Kong gateway** — JWT auth plugin, rate limiting
10. **Set up GitHub Actions CI** — Unit test + build pipeline

### Month 2
11. **Launch 4 Phase 1 apps** — NutriPrismora, FloraPrismora, PawPrismora, MeowPrismora in MVP state
12. **Set up Stripe billing** — Subscription plans, webhook handler
13. **Deploy staging K8s cluster** — Full environment parity with production
14. **Begin model training** — Food detection CNN, dog/cat breed CNN
15. **Conduct security audit** — OWASP ZAP scan on staging environment

---

*Document Version 2.0 — Prismora Platform Next Steps — PhotoIdentifier Platform | 2026*
*Generated from analysis of all 17 sub-app PRDs and Master PRD*
