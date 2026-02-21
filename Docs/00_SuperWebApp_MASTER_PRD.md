# MASTER PRD: PhotoIdentifier Super Web Application
### Platform Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | PhotoIdentifier Super Web Application — Master Platform PRD |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | CPO, CTO, CFO, Platform Architect, Legal Counsel, UX Director |
| **Classification** | Internal — Confidential — Board Distribution |

---

## 2. Executive Summary

The **PhotoIdentifier Super Web Application** is a unified, AI-first identification and intelligence platform integrating 17 specialized sub-applications under one authenticated, single-sign-on Progressive Web Application. Users access a curated suite of AI identification engines — spanning numismatics, fitness, nature, food, vehicles, pets, and collectibles — through a single account, shared data layer, and coherent design system.

The platform's singular competitive advantage is **cross-app AI synergy**: a user's activity in one sub-app enriches intelligence in others. A Calo user's nutrition goals inform LazyFit's workout recovery recommendations. A Plant Identifier user's toxicity scan triggers a relevant alert in Okay Fish when an identified toxic plant is common in their region. The unified data model enables personalization loops that no single-domain app can replicate.

**Total Addressable Market (TAM):** Combined TAM across all 17 domains exceeds **$150 billion annually**.

**Revenue Model:** Freemium subscription (per sub-app or platform-wide bundle); B2B API licensing; marketplace transaction fees; affiliate partnerships.

**Platform Vision:** To be the world's most complete AI-powered visual intelligence platform — making expert-level identification and domain knowledge accessible to every person with a camera.

---

## 3. Problem Statement

### Platform-Level Problems
- Domain-specific AI tools exist in silos — users manage 10+ separate app subscriptions for identification needs.
- No unified AI platform provides cross-domain value: a healthier user who tracks food, exercise, foraging, and pet care has fragmented data across 5+ apps.
- Building each domain AI independently is capital-inefficient — shared infrastructure (auth, storage, AI inference gateway, payment) reduces total engineering cost by 40–60%.
- Consumer trust requires sophisticated safety and security compliance frameworks that SMEs building single-domain tools cannot afford independently.

### Market Opportunity
- **Multi-vertical subscription bundling** reduces churn vs. single-domain apps
- **Cross-app data network effects** create a defensible moat
- **B2B API monetization** of individual domain engines to third-party developers

---

## 4. Goals & Success Metrics

### Platform KPIs

| Metric | Month 6 | Month 12 | Month 24 |
|---|---|---|---|
| Registered Users | 500,000 | 2,000,000 | 10,000,000 |
| Monthly Active Users (MAU) | 200,000 | 1,000,000 | 5,000,000 |
| Platform Subscription Revenue | $800K/mo | $4M/mo | $25M/mo |
| Sub-apps with 50K+ MAU | 5 | 12 | 17 |
| API Developer Partners | 20 | 100 | 500 |
| Cross-app Feature Usage | 15% of users | 35% | 60% |
| Platform NPS | 50 | 62 | 70 |
| Marketplace GMV | $200K/mo | $2M/mo | $15M/mo |

### Platform OKRs (Year 1)
- **O1:** Establish PhotoIdentifier as the dominant multi-domain AI identification platform
  - KR: 2M registered users by Month 12
  - KR: Top 3 in App Store/Google Play across 5 identification categories
- **O2:** Build the most defensible cross-app AI data layer
  - KR: 500M+ identifications logged across all sub-apps by Year 1
  - KR: Launch 3 cross-app intelligence features in H2

---

## 5. Platform Architecture

### 5.1 High-Level System Architecture

```
╔════════════════════════════════════════════════════════════════════╗
║                    PhotoIdentifier PWA                            ║
║           Next.js 14 + TypeScript + TailwindCSS                   ║
║   ┌──────────────────────────────────────────────────────────┐    ║
║   │  Sub-App Shell: CoinSnap | LazyFit | VinylSnap | Calo.. │    ║
║   │  Shared: Auth | Navigation | Notifications | Search      │    ║
║   └──────────────────────────────────────────────────────────┘    ║
╚══════════════════════════╦═════════════════════════════════════════╝
                           ║ HTTPS / REST / WebSocket / gRPC
╔══════════════════════════▼═════════════════════════════════════════╗
║                      API Gateway Layer                            ║
║                    Kong + AWS API Gateway                         ║
║   Auth | Rate Limiting | SSL Termination | Routing | Logging      ║
╚══════╦════════╦════════╦═════════╦════════╦════════╦══════════════╝
       ║        ║        ║         ║        ║        ║
   ┌───▼──┐ ┌──▼───┐ ┌──▼───┐ ┌───▼──┐ ┌──▼───┐ ┌──▼──────────┐
   │ AI   │ │Auth  │ │Sub-  │ │Market│ │Notif │ │Analytics   │
   │Infra │ │Svc   │ │App   │ │place │ │Svc   │ │& Telemetry │
   │(Inf.)│ │(SSO) │ │Svcs  │ │Svc   │ │      │ │            │
   └──┬───┘ └──────┘ └──┬───┘ └──────┘ └──────┘ └────────────┘
      │                 │
╔═════▼═════════════════▼════════════════════════════════════════════╗
║                    Shared Data Platform                           ║
║  PostgreSQL 16 (primary) | Redis 7 (cache/sessions)               ║
║  Pinecone (vector search) | TimescaleDB (time-series)             ║
║  Apache Kafka (event streaming) | ElasticSearch (full-text)       ║
╚══════════════════════════════════════════════════════════════════╦═╝
                                                                   ║
╔══════════════════════════════════════════════════════════════════▼═╗
║                    AI Inference Platform                          ║
║  TensorFlow Serving | ONNX Runtime | Google Cloud AI Platform     ║
║  Model Registry | A/B Testing | Feature Store | Shadow Deployments║
╚════════════════════════════════════════════════════════════════════╝
```

### 5.2 Sub-Application Catalog

| # | App Name | Brand Name | Domain |
|---|---|---|---|
| 01 | Coin Snap | CoinLens AI | Numismatics |
| 02 | LazyFit | LazyFit | Beginner Fitness |
| 03 | Vinyl Snap | VinylVault AI | Record Collecting |
| 04 | Calo | NutriLens AI | Food & Nutrition |
| 05 | Rock Identifier | GeoLens AI | Geology & Gemology |
| 06 | Picture Mushroom | ForageSafe AI | Mycology & Foraging |
| 07 | MuscleFit | AthleteOS | Advanced Fitness |
| 08 | Picture Insect | EntomIQ | Entomology |
| 09 | Picture Bird | WingWatch Pro | Ornithology |
| 10 | Note Snap | CurrencyLens | Banknote Collecting |
| 11 | Okay Fish | AquaIQ Pro | Aquarium Keeping |
| 12 | Star Snap | CardVault AI | Sports Cards |
| 13 | Plant Identifier | FloraLens AI | Botany & Gardening |
| 14 | Fruit Identifier | OrchardIQ | Fruit & Nutrition |
| 15 | Vehicle Identifier | AutoLens AI | Automotive |
| 16 | Dog Breed Identifier | BarkIQ AI | Canine Intelligence |
| 17 | Cat Breed Identifier | MeowIQ AI | Feline Intelligence |

---

## 6. Unified Design System

### 6.1 Design Philosophy
- **"Camera First"** — every sub-app's primary action is a camera capture
- **"3-Second Rule"** — all AI identifications must complete within 3 seconds p95
- **"Safety Guardrails"** — mushroom, plant toxicity, and pet health apps architecturally biased toward safety warnings
- **"Progressive Disclosure"** — show essential data immediately; advanced data on demand

### 6.2 Shared Design Tokens

| Token | Value |
|---|---|
| **Primary Background** | Configurable per sub-app (each has distinct identity) |
| **Unified Nav Bar** | Platform hub icon; sub-app switcher bottom nav / side nav |
| **Platform Primary Accent** | Vibrant Indigo `#6366F1` (platform-level elements only) |
| **Typography System** | Inter (platform UI); sub-apps may use additional brand fonts |
| **Border Radius** | 12px cards; 8px inputs; 24px pill buttons |
| **Scan Overlay** | Consistent AI scanning animation across all 17 apps |

### 6.3 Universal UX Components
- **PhotoCapture Module** — shared camera component (crop, zoom, flash, HEIC support) used by all 17 apps
- **AI Processing Indicator** — consistent scanning animation with sub-app color palette
- **Identification Result Card** — shared base card; sub-app extends with domain-specific fields
- **Premium Gate Modal** — consistent upgrade prompt across all sub-apps
- **Cross-App Suggestion Banner** — contextual suggestion to open a related sub-app

---

## 7. Cross-App Integration Features

These features represent the platform's unique AI synergy — value multipliers created by combining data across sub-apps:

| Integration | Sub-Apps Involved | Description |
|---|---|---|
| **Nutrition Sync** | Calo ↔ Fruit Identifier | Fruit scan auto-logs to Calo daily diary |
| **Workout × Calories** | LazyFit / MuscleFit ↔ Calo | Calorie burn from workouts deducted from Calo daily budget |
| **Beginner → Advanced Pathway** | LazyFit → MuscleFit | AI detects when LazyFit user has graduated to intermediate level and suggests MuscleFit |
| **Plant × Fish Safety** | Plant Identifier ↔ Okay Fish | If plant in user's home is toxic to fish species in their Okay Fish tank, alert is triggered |
| **Pet × Nutrition** | Dog/Cat Breed ↔ Calo | Dietary needs of identified breed push guided nutrition log to Calo for the owner |
| **Wild Foraging Safety** | Picture Mushroom ↔ Picture Insect | Combined foraging outing log with safety summary for both fungi and insects found |
| **Nature Discovery Feed** | Bird + Plant + Insect + Mushroom + Rock | Unified "Nature Walk Log" — all identifications from a session aggregated with GPS map |

---

## 8. Unified Authentication & Authorization

### 8.1 SSO Architecture
- **Provider:** Supabase Auth (JWT + OAuth2)
- **Social Login:** Google, Apple, Facebook, GitHub
- **MFA:** TOTP (Google Authenticator) for premium users; SMS fallback
- **Session Management:** JWT refresh cycle (15-min access token, 7-day refresh)
- **Cross-App Session:** Single JWT grants access to all sub-apps within the platform

### 8.2 Permission Model

| Role | Description |
|---|---|
| `free_user` | Access to all sub-apps at free tier limits |
| `premium_user` | Unlimited access to all sub-apps + premium features |
| `premium_single` | Premium for one specific sub-app only |
| `coach` | MuscleFit/LazyFit coaching dashboard + client management |
| `vet` | Dog/Cat telehealth provider account |
| `expert` | Sub-app-specific expert (numismatist, gemologist, mycologist) |
| `b2b_developer` | API key access; rate limits per contract |
| `platform_admin` | Internal staff; full access |

---

## 9. Subscription & Monetization Architecture

### 9.1 Pricing Tiers

| Tier | Price | Access |
|---|---|---|
| **Free** | $0 | All sub-apps with daily usage limits |
| **Single App Premium** | $6.99–$14.99/mo | Full premium features for one sub-app |
| **Platform Pass** | $24.99/mo | Full premium across all 17 sub-apps |
| **Family Plan** | $39.99/mo | Platform Pass for up to 5 family members |
| **B2B Developer API** | $299–$999/mo | API access; volume pricing for enterprise |
| **Enterprise / Fleet** | Custom | White-label, SLA, dedicated infrastructure |

### 9.2 Revenue Streams

| Stream | Mechanism |
|---|---|
| Subscription | Recurring monthly/annual; Stripe Billing |
| Marketplace Fees | 10–15% transaction fee on Coin, Vinyl, Mineral, Card, Fish marketplaces |
| Expert Appraisals | Platform takes 20% of appraisal fee |
| Coaching / Telehealth | Platform takes 20% of session fee |
| Affiliate | Pet insurance, car insurance referral fees; pet DNA test affiliate |
| B2B API Licensing | Per-call pricing or monthly seat contracts |
| Conservation Donations | 2% platform-matching contribution on opt-in donations |

---

## 10. Shared Technical Infrastructure

### 10.1 Platform Technology Stack

| Layer | Technology | Notes |
|---|---|---|
| **Frontend** | Next.js 14, TypeScript, TailwindCSS | SSR + CSR hybrid; App Router |
| **PWA** | Service Workers, Web App Manifest | Offline capabilities per sub-app |
| **Camera** | MediaDevices API, WebRTC | Shared PhotoCapture module |
| **Auth** | Supabase Auth + JWT | Platform-wide SSO |
| **API Gateway** | Kong + AWS API Gateway | Rate limiting, auth, routing |
| **Backend Microservices** | FastAPI (Python 3.12) + Node.js 20 | Per-sub-app services |
| **AI Inference** | TensorFlow Serving + ONNX Runtime | GPU cluster on GKE |
| **Primary DB** | PostgreSQL 16 (Google Cloud SQL) | Per-sub-app schema namespaces |
| **Cache** | Redis 7 (Upstash) | Sessions + AI result cache |
| **Vector DB** | Pinecone | Visual similarity search cross-app |
| **Time-Series** | TimescaleDB | Health, price, fitness metrics |
| **Event Streaming** | Apache Kafka (Confluent Cloud) | Cross-app events; marketplace |
| **Search** | Elasticsearch 8 | Full-text across sub-app content |
| **Media Storage** | AWS S3 + CloudFront CDN | Images, audio, video; signed URLs |
| **AI Platform** | Google Cloud Vertex AI | Model training + serving |
| **Container Orchestration** | Kubernetes (GKE) | Auto-scaling AI inference pods |
| **CI/CD** | GitHub Actions + ArgoCD | Blue-green deployment |
| **Monitoring** | Datadog + Sentry + PagerDuty | APM, error tracking, alerting |
| **Payments** | Stripe (subscriptions) + Stripe Connect (marketplace) | Multi-party payouts |

### 10.2 AI Infrastructure

```
Model Registry (Vertex AI)
  └── Model versions tracked; A/B test traffic splitting
  └── Shadow deployment: new model runs in parallel before promotion
  └── Rollback < 5 minutes via canary release system

AI Inference Routing:
  └── Low-latency models (< 200ms): Run at edge (Cloudflare Workers AI)
  └── Heavy models (> 1s): Run on GPU pods (NVIDIA A100, GKE)
  └── Cache: Identical image hashes return cached result for 24h

Feature Store:
  └── User trait vectors updated in real-time (purchase history, identification patterns, preferences)
  └── Consumed by: subscription AI pricing, cross-app recommendation engine, personalization
```

---

## 11. Data Architecture

### 11.1 Shared User Data Model

```
user_id             UUID PK
email               VARCHAR(255) UNIQUE
display_name        VARCHAR(100)
avatar_url          TEXT
plan                ENUM(free, premium_single, platform_pass, family, b2b, enterprise)
subscription_id     VARCHAR(100) (Stripe)
plan_expiry         TIMESTAMP
registered_at       TIMESTAMP
last_active_at      TIMESTAMP
country             CHAR(2)
preferred_currency  CHAR(3)
preferred_units     ENUM(metric, imperial)
language            CHAR(5)
```

### 11.2 Cross-App Event Logs (Kafka)

Every significant user action across all sub-apps emits a standardized event:
```json
{
  "event_type": "identification.completed",
  "platform": "photo_identifier",
  "sub_app": "plant_identifier",
  "user_id": "uuid",
  "session_id": "uuid",
  "timestamp": "ISO8601",
  "payload": {
    "species_id": "uuid",
    "confidence": 0.96,
    "toxicity_alert": true,
    "lat": 51.5074, "lon": -0.1278
  }
}
```

These events power cross-app intelligence features, the unified Nature Discovery Feed, analytics dashboards, and the personalization engine.

### 11.3 Privacy & Data Retention

| Data Category | Retention | User Control |
|---|---|---|
| Identification images | 30 days (unless saved) | Delete anytime |
| Saved identifications | Until account deletion | Export as ZIP |
| Health / fitness logs | 5 years or account deletion | Export as CSV |
| Payment records | 7 years (legal requirement) | View only |
| Location data | 90 days (aggregated after) | Opt-out available |
| AI model training opt-in | Opt-in only; anonymized | Revoke at any time |

---

## 12. Security & Compliance Framework

### 12.1 Security Controls
- **Encryption at rest:** AES-256 for all databases; field-level encryption for PII
- **Encryption in transit:** TLS 1.3 everywhere; HSTS with preload
- **Vulnerability scanning:** Snyk (daily dependencies), Semgrep (SAST), Burp Suite (DAST quarterly)
- **Pen testing:** Annual third-party penetration test; bug bounty program (HackerOne)
- **SIEM:** Datadog Security Monitoring; PagerDuty P0/P1 alert escalation
- **Secrets management:** HashiCorp Vault

### 12.2 Compliance

| Standard | Applicability | Status |
|---|---|---|
| **GDPR** | EU users | Compliant — DPO appointed; DPIA completed |
| **CCPA** | California users | Compliant — Privacy Policy updated |
| **COPPA** | Kids Mode (Insect sub-app) | Compliant — no under-13 data collection |
| **HIPAA-adjacent** | Telehealth (Dog/Cat/Fish) | HIPAA-aware practices; not a covered entity |
| **PCI DSS** | Payment processing | Stripe handles all card data; no PAN on platform |
| **SOC 2 Type II** | B2B enterprise clients | Year 2 certification target |
| **App Safety** | Mushroom, Plant toxicity | Safety audit required before each major release |

---

## 13. Platform Integration Ecosystem

### 13.1 External API & Data Partners

| Category | Partners |
|---|---|
| **Scientific Databases** | iNaturalist, GBIF, PlantNet, Mindat, FishBase, MycoBank, RRUFF, AKC, TICA, Cornell Lab |
| **Market Data** | PCGS, PMG, KBB, eBay API, Xeno-canto, PWCC, Carfax, USDA FoodData |
| **Government / Safety** | NHTSA, USDA APHIS, EPPO, GBIF Invasive, Poison Control APIs, BirdLife International |
| **Health / Wearables** | Dexcom CGM, Seneye, Whistle, Tractive, Garmin, Fitbit |
| **Payment** | Stripe, Stripe Connect |
| **Communication** | Twilio (SMS), Daily.co (video telehealth), SendGrid (email) |
| **AI Services** | OpenAI GPT-4o, Google Vertex AI, TensorFlow Serving |
| **Infrastructure** | AWS S3, CloudFront, GKE, Kong, Redis, Kafka, Pinecone, Elasticsearch |

### 13.2 B2B API Program

Developers can access individual sub-app AI engines via REST API:

```
Base URL: https://api.photoidentifier.ai/v1/{sub_app}/
Auth: Bearer API key (issued via developer portal)
Rate limits: 1,000 calls/day (free tier); custom (paid)

Published APIs:
  - /coinsnap/identify
  - /nutrilens/identify-food
  - /floralens/identify
  - /orchardiq/identify
  - /autolens/identify
  - /barkiq/identify
  - (all 17 sub-apps)
```

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Global Performance** | p95 API response < 3s from any region; CDN delivered from 8 global PoPs |
| **AI Latency** | Core identification < 3 seconds; edge deployable models < 500ms |
| **Availability** | Platform SLA: 99.9%; Telehealth SLA: 99.95% |
| **Scalability** | Auto-scale inference pods to 10x peak in < 90 seconds |
| **Data Sovereignty** | EU user data stored in EU regions; US user data in US region |
| **Offline** | PWA service worker enables offline access to saved data in all sub-apps |
| **Accessibility** | WCAG 2.1 AA across all sub-apps; full keyboard access; screen reader support |
| **Localization** | Platform available in 14 languages at launch |
| **Mobile** | Fully responsive; tested on iOS Safari, Chrome Android, Samsung Browser |
| **Performance Budget** | Lighthouse score ≥ 90 on all core pages; < 2s First Contentful Paint |

---

## 15. Platform Release Roadmap

### Phase 1 — Foundation (Month 1–4)
**Milestone: 5 sub-apps live on unified platform**

- Platform infrastructure: Auth (Supabase), API Gateway (Kong), PostgreSQL, Redis, S3
- Shared design system + PhotoCapture module deployed
- Sub-apps launched: CoinSnap, Calo, Plant Identifier, LazyFit, Dog Breed Identifier
- Basic free tier with daily usage limits
- Stripe subscription billing (single-app premium)

### Phase 2 — Expansion (Month 5–8)
**Milestone: 12 sub-apps live; Platform Pass launched**

- Sub-apps added: VinylSnap, MuscleFit, Picture Bird, Picture Mushroom, Rock Identifier, Fruit Identifier, Okay Fish
- Platform Pass subscription tier launched ($24.99/mo)
- Cross-app feature: Nutrition Sync (Calo ↔ Fruit Identifier)
- Cross-app feature: Workout × Calories (LazyFit/MuscleFit ↔ Calo)
- Marketplace MVP (Coin, Vinyl)
- PWA offline capabilities for all active sub-apps
- B2B Developer API portal opens (invite-only beta)

### Phase 3 — Full Platform (Month 9–14)
**Milestone: All 17 sub-apps live; cross-app intelligence deployed**

- Sub-apps added: NoteSnap, StarSnap, PictureInsect, VehicleIdentifier, CatBreedIdentifier
- Nature Discovery Feed (Bird + Plant + Insect + Mushroom cross-app log)
- Telehealth marketplace: Dog/Cat/Fish veterinary consultations live
- All marketplace modules operational (all 5)
- B2B API program open to all developers
- Family Plan subscription tier
- SOC 2 Type II audit initiated

### Phase 4 — Scale & AI (Month 15–24)
**Milestone: 5M MAU; Enterprise tier**

- Enterprise / White-label tier
- Advanced cross-app AI: personalized intelligence recommendations
- Platform AI: unified user interest graph — "Your Outdoors Profile", "Your Pet Health Score"
- International expansion: launch in 10 additional language markets
- AR features across all eligible sub-apps (WebXR)
- Platform API revenue reaches $500K/mo MRR
- Exploration of native iOS/Android apps leveraging the existing Next.js codebase

---

## 16. Organizational & Team Structure

| Team | Scope |
|---|---|
| **Platform Core** | Auth, API Gateway, shared infrastructure, design system |
| **AI Platform** | Model training, inference infrastructure, feature store, model registry |
| **Sub-App Teams (pods)** | 3–5 engineers per sub-app cluster (grouped by domain: Nature, Health, Collectibles, Pets, Auto) |
| **Marketplace** | Transaction processing, trust & safety, fraud detection |
| **Data & Analytics** | Cross-app event pipeline, BI, A/B testing framework |
| **Security & Compliance** | AppSec, GDPR, SOC 2, pen testing coordination |
| **Growth** | SEO, paid acquisition, App Store optimization, influencer/creator partnerships |

---

*Document Version 1.0 — Super Web Application Master PRD — PhotoIdentifier Platform | 2026-02-21*  
*This document is the authoritative platform-level reference. All 17 sub-app PRDs are subordinate specifications.*
