# PRD: FitPrismora — Workout For Beginners
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | FitPrismora: Workout For Beginners — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Fitness Domain Expert |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**FitPrismora** is a beginner-oriented fitness web application that removes every barrier to starting a workout routine. It is designed for sedentary individuals who feel overwhelmed by complex fitness apps, crowded gyms, and unrealistic workout programs. FitPrismora delivers short, no-equipment workouts with AI form correction, adaptive difficulty progression, and motivational psychology principals — turning the "laziest" users into consistent movers.

The global digital fitness market is valued at **$14.64 billion in 2025**, growing at 26% CAGR. Beginners represent the largest underserved segment — most fitness apps are built for people who are already fit. FitPrismora captures this market with radical simplicity, science-backed programming, and delightful UX.

**Proposed Brand Name:** ZeroToFit

---

## 3. Problem Statement

### Current Pain Points
- Most fitness apps assume users have prior knowledge of exercises, leading to high churn within 7 days for beginners.
- Beginners frequently injure themselves by performing exercises with poor form — there is no AI real-time coach accessible to them.
- Complex logging systems (sets × reps × weight) intimidate non-athletes.
- Motivational gaps cause fitness streaks to collapse within 2–3 weeks.

### Market Opportunity
- 1.4 billion physically inactive adults globally (WHO, 2024).
- 70% of new gym members quit within 12 weeks.
- Web-based fitness tools growing faster than native apps among 18–35 demographics.

---

## 4. Goals & Success Metrics

### Business Goals
- Be the #1 rated beginner fitness web app within 12 months of launch.
- Achieve 30-day retention rate of 45% (industry avg for fitness apps: 18%).

### Key Performance Indicators (KPIs)

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 100,000 | 1,000,000 |
| 7-Day Retention Rate | 55% | 65% |
| 30-Day Retention Rate | 35% | 50% |
| Workouts Completed / Day | 30,000 | 300,000 |
| AI Form Correction Sessions | 10,000 | 150,000 |
| Premium Conversion | 8% | 15% |
| NPS Score | 52 | 65 |

---

## 5. Target Users & Personas

### Persona 1 — Sarah, The Desk-Bound Professional (Primary)
- **Age:** 31 | **Occupation:** Software Engineer | **Location:** Austin, TX
- **Goal:** Start exercising without going to a gym; fit workouts into busy schedule.
- **Pain Points:** Tried 3 fitness apps and quit all within 2 weeks; overwhelmed by complexity.
- **Tech Comfort:** High — uses web apps and PWAs; prefers browser over native app.
- **Willingness to Pay:** $7.99/month for an app that actually makes her exercise.

### Persona 2 — James, The Post-Recovery Beginner (Secondary)
- **Age:** 52 | **Occupation:** Teacher | **Location:** Manchester, UK
- **Goal:** Regain fitness after health issues; start gently without risk of injury.
- **Pain Points:** Afraid of hurting himself; doctor said "start exercising" but gave no guidance.
- **Tech Comfort:** Moderate — uses smartphone and basic web tools.
- **Willingness to Pay:** $5.99/month; needs to see health benefits quickly.

### Persona 3 — Priya, The Busy Parent (Tertiary)
- **Age:** 38 | **Occupation:** Marketing Manager | **Location:** Mumbai, India
- **Goal:** Exercise at home with children nearby; 15-minute sessions maximum.
- **Pain Points:** No time, no equipment, no dedicated space.
- **Tech Comfort:** High — uses mobile web apps extensively.
- **Willingness to Pay:** Free tier preferred; will upgrade if core results appear.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Beginner Workout Library | 50+ workouts; 5–20 min; no equipment required | Workouts tagged by duration, body part, and difficulty |
| Animated Exercise Demos | GIF/video demonstration for each exercise | All 200+ exercises have high-quality visual demos |
| Step-by-Step Instructions | Written + visual cues for every exercise set | Read aloud compatible (screen reader + text-to-speech) |
| Workout Timer | Countdown for work/rest intervals | Audible beep + visual flash at interval end |
| NutriPrismorarie Burn Estimate | Estimated calories burned per session based on weight/age | Estimate within 15% of MET-based calculation |
| Streak Tracker | Daily streak counter with calendar view | Streak resets at midnight local time if no workout logged |
| Workout Log | History of completed sessions | Log shows duration, exercises, and date |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Personalized Plan | Goal-based plan: weight loss / tone / flexibility / stamina | Plan generated in < 10 seconds based on onboarding questionnaire |
| Body Part Filter | Filter exercises by targeted region | Eight body part categories available |
| Rest Day Scheduling | System plans rest days and active recovery | Recovery day suggestions include stretching routines |
| Progress Photos | Upload before/after photos with timeline comparison | Photos stored privately; comparison slider UI |
| Step Counter Integration | Optional pedometer data from browser/device | Uses DeviceMotion API; accuracy >= 85% on smooth surfaces |
| Weekly Fitness Report | Auto-generated PDF/in-app summary of weekly performance | Report includes volume, calories, streak, progress insight |
| BMI & Body Metrics Tracker | Input weight, height, body measurements | Visual line graph showing change over time |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Real-Time Form Correction | Use device camera + pose estimation to detect bad form | Detects 10 most common beginner form errors per exercise; feedback within 1 second |
| Adaptive Workout Engine | Difficulty auto-adjusts based on completion history and speed | Engine increases difficulty 10% when user completes 3 sessions at 90%+ pace |
| Voice Coach Mode | Audio cues during workout: reps counted, encouragement, corrections | Customizable voice; works without looking at screen |
| Wearable Sync | Sync heart rate and activity data from wearable devices | Supports Fitbit, Garmin (via OAuth) and Apple Health (Web API) |
| Social Challenges | Friend challenges and leaderboard by workout streak/calories | Leaderboard refreshes daily; challenge invite via link |
| Nutrition Pairing | Synced calorie suggestions from NutriPrismora sub-app integration | Pulls daily calorie burn into NutriPrismora daily budget automatically |
| Mindfulness Cool-Down | Guided breathing and body scan sessions post-workout | 10 guided session templates (2–5 min each); custom timer adjustable |

---

## 7. User Stories & Use Cases

### Epic 1 — Onboarding & Plan Generation
- **US-101:** As a new user, I want to answer 5 quick questions so that I get a personalized beginner plan that fits my life.
- **US-102:** As a beginner, I want to see a weekly schedule so that I know exactly when and what to do each day.
- **US-103:** As a user with no equipment, I want all exercises to require zero equipment so that I can start immediately.

### Epic 2 — Workout Execution
- **US-201:** As a user, I want a clear timer between exercises so that I know exactly when to rest and when to move.
- **US-202:** As a user, I want animated demos for each exercise so that I know I'm doing it correctly.
- **US-203:** As a user training at home, I want the app to use my camera to check my form so that I avoid injuries.

### Epic 3 — Progress & Motivation
- **US-301:** As a user, I want to see my workout streak every day so that I'm motivated to maintain it.
- **US-302:** As a user, I want a weekly report so that I can see how much I've improved.
- **US-303:** As a user, I want to compare my before/after photos so that I see visible progress.

### Epic 4 — Social & Accountability
- **US-401:** As a competitive user, I want to challenge a friend to a 7-day workout streak so that we motivate each other.
- **US-402:** As a premium user, I want a voice coach so that I don't have to watch the screen while exercising.

---

## 8. Technical Architecture

### System Overview
```
+---------------------------------------------------+
|              FitPrismora Frontend                     |
|      Next.js 14 + TypeScript + TailwindCSS        |
|  Camera API (Pose) | DeviceMotion | PWA            |
+-------------------+-------------------------------+
                    | REST / WebSocket
+-------------------+-------------------------------+
|            API Gateway (Kong)                     |
+---------+-----------------+------------------------+
          |                 |
+---------+----------+  +---+--------------+
|  Workout          |  |  AI Pose Engine  |
|  Service          |  |  Service         |
|  (FastAPI)        |  |  (Python/ONNX)   |
+--------------------+  +------------------+
          |
+---------+----------------------------------------+
|  PostgreSQL (users, workouts, plans)            |
|  Redis (session, streak cache)                  |
|  S3 (progress photos, video demos)              |
+-------------------------------------------------+
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Pose Estimation | MoveNet (TensorFlow.js — runs in-browser, no upload needed) |
| Form Error Detection | Rule-based joint angle analysis on MoveNet keypoints |
| Adaptive Engine | Collaborative filtering + rule-based difficulty adjustment |
| NutriPrismorarie Estimation | MET-based formula with user profile variables |

### Tech Stack
| Layer | Technology |
|---|---|
| Frontend | Next.js 14, TypeScript, TailwindCSS, TensorFlow.js |
| Backend | FastAPI (Python 3.12) |
| Database | PostgreSQL 16, Redis 7 |
| Media | AWS S3 (progress photos), Cloudinary (exercise video/GIF CDN) |
| Auth | Supabase Auth |
| Deployment | Docker + GKE |
| Monitoring | DataDog, Sentry |

---

## 9. Data Model

**WorkoutPlan**
```
plan_id          UUID PK
user_id          UUID FK
goal             ENUM(weight_loss, tone, flexibility, stamina, general)
days_per_week    INTEGER (3–6)
session_duration ENUM(5min, 10min, 15min, 20min)
level            ENUM(beginner, early_intermediate)
created_at       TIMESTAMP
```

**Exercise**
```
exercise_id      UUID PK
name             VARCHAR(200)
body_part        ENUM(abs, arms, chest, back, glutes, legs, full_body)
equipment        ENUM(none, resistance_band, dumbbells)
difficulty       INTEGER (1–3)
video_url        TEXT
gif_url          TEXT
instructions     TEXT[]
met_value        DECIMAL(4,2)
```

**WorkoutSession**
```
session_id       UUID PK
user_id          UUID FK
plan_id          UUID FK
completed_at     TIMESTAMP
duration_seconds INTEGER
calories_burned  DECIMAL(6,2)
exercises_done   JSONB
form_score       DECIMAL(4,2) (0–100)
```

**UserStreak**
```
streak_id        UUID PK
user_id          UUID FK UNIQUE
current_streak   INTEGER
longest_streak   INTEGER
last_active_date DATE
```

---

## 10. API Design

#### POST `/api/v1/workout-plans/generate`
```json
// Request
{
  "goal": "weight_loss",
  "days_per_week": 4,
  "session_duration": "15min",
  "equipment": "none",
  "injuries": ["lower_back"]
}
// Response 200 OK
{
  "plan_id": "uuid",
  "weekly_schedule": {
    "monday": { "workout_id": "uuid", "name": "Full Body Burn", "duration_min": 15 },
    "tuesday": { "type": "rest" },
    ...
  }
}
```

#### POST `/api/v1/sessions/{session_id}/start`
Start a workout session timer and tracking.

#### POST `/api/v1/sessions/{session_id}/complete`
Mark session complete; calculate calories; update streak.

#### POST `/api/v1/pose/analyze`
Send base64 keypoints from TensorFlow.js MoveNet -> receive form feedback JSON.

---

## 11. UI/UX Requirements

### Screen List
1. **Onboarding Flow** — 5-question goal-setting wizard (name, goal, days, duration, equipment)
2. **Dashboard** — Today's workout card, streak, recent achievements
3. **Workout Player** — Full-screen exercise mode: video, timer, instructions, form camera overlay
4. **Exercise Library** — Browse all exercises by body part / difficulty
5. **Progress Hub** — Streak calendar, weight chart, before/after photo timeline
6. **Community** — Friend leaderboard, active challenge cards
7. **Nutrition Bridge** — Summary panel linking to NutriPrismora sub-app daily calorie goals

### Design System

**Typography**
- Font Family: Inter
- Weights: 400 (Regular), 600 (SemiBold), 800 (ExtraBold)
- Usage: Body text (400), Headers/Buttons (600), Emphasis/Hero (800)

**Colors**
- Primary: Indigo `#6366F1`
- Background: White `#FFFFFF` / Gray `#F9FAFB`
- Text: Slate `#1E293B` (primary), `#64748B` (secondary)
- Accent: Success `#10B981`, Warning `#F59E0B`, Error `#EF4444`

**Spacing**
- Base Unit: 4px
- Scale: 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px

**Border Radius**
- Cards: 12px
- Buttons: 8px
- Inputs: 8px
- Badges/Pills: 9999px (full)

**Shadows**
- Level 1: `0 1px 2px rgba(0, 0, 0, 0.05)`
- Level 2: `0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06)`
- Level 3: `0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06)`
- Level 4: `0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)`
- Level 5: `0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04)`

### Key Design Decisions
- **Font:** Inter (400/600/800) — clean, modern, highly readable
- **Color:** Indigo `#6366F1` primary, White/Gray background
- **Workout Player:** No clutter — blurred background, one exercise at a time, massive timer
- **Gamification:** XP points, achievement badges, level-up animations (Lottie)
- **Accessibility:** WCAG 2.1 AA; voice-only mode for workout execution

---

## 12. Security & Compliance

- JWT auth with 30-minute expiry + secure refresh token rotation
- Progress photos encrypted at rest (AES-256) in S3; accessible only to owning user
- **HIPAA awareness:** App does not qualify as a medical device; disclaimers present
- Camera access for pose estimation runs 100% in-browser (TensorFlow.js); no video sent to server
- GDPR/CCPA: full data export and deletion endpoints
- Children under 13 blocked by ToS; age gate on registration

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| TensorFlow.js / MoveNet | In-browser pose estimation |
| Fitbit Web API | Wearable heart rate sync |
| Garmin Connect IQ API | Garmin device data sync |
| Apple Health (Web) | Step count and active calorie sync (iOS Safari) |
| NutriPrismora (Internal API) | NutriPrismorarie budget data sharing |
| Stripe | Premium subscription billing |
| Cloudinary | Video/GIF CDN for exercise demos |
| SendGrid | Workout reminder and weekly report emails |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Workout player loads in < 2 seconds; pose analysis feedback latency < 1 second (in-browser) |
| **Availability** | 99.9% uptime; workout sessions must work even during brief connectivity loss (PWA offline mode) |
| **Video/GIF Delivery** | Exercise demo content served from CDN with global p95 load < 800ms |
| **Scalability** | Auto-scale API services; support 50,000 concurrent workout sessions |
| **Data Retention** | Progress photos retained for account lifetime; deleted within 30 days of account closure |
| **Accessibility** | Voice coach mode ensures full workout possible without vision; WCAG 2.1 AA |
| **Localization** | 8 languages at launch |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Workout library (50 beginner workouts; no equipment)
- Animated exercise demos
- Session timer and completion logging
- Streak tracker and basic dashboard
- Onboarding plan generator
- Free tier: 3 workouts/day; Premium: unlimited

### Phase 2 — Enhanced (Month 4–7)
- AI pose estimation form correction (10 exercises)
- Progress photos, BMI tracker, weekly reports
- Social challenges and leaderboard
- Wearable sync (Fitbit, Garmin)
- NutriPrismora integration for calorie balancing

### Phase 3 — Advanced (Month 8–14)
- Full exercise library with AI form on all exercises
- Voice coach mode
- Adaptive workout engine
- Mindfulness cool-downs
- Nutritionist AI chatbot recommendation engine

---

*Document Version 1.0 — FitPrismora PRD — PhotoIdentifier Platform | 2026-02-21*
