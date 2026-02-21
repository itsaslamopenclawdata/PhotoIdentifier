# PRD: Calo — AI Food Calorie Counter
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Calo: AI Food Calorie Counter — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Registered Dietitian Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Calo** is an AI-powered food recognition and nutrition tracking application that allows users to photograph any meal and instantly receive a detailed calorie count, macronutrient breakdown, and personalized dietary insights. The global digital health and nutrition market is valued at **$24.4 billion in 2025**, with food-logging being the highest-engagement feature in health apps. Yet most users abandon manual food logging within days because it requires too much effort.

Calo eliminates that friction entirely — a photo replaces hundreds of manual taps — and layers sophisticated dietary intelligence (AI nutritionist chatbot, glucose modeling, lab integration) on top to serve both wellness consumers and clinical use cases.

**Proposed Brand Name:** NutriLens AI

---

## 3. Problem Statement

- Manual food logging requires 45–90 seconds per meal entry — users abandon this within 3–5 days.
- Existing food photo apps have poor accuracy for mixed dishes, restaurant meals, and non-Western cuisines.
- No single app combines food photo recognition + portion estimation + AI nutritionist chatbot + clinical data integration.
- Diabetics and dieters lack real-time glycemic impact feedback for their meals.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 150,000 | 2,000,000 |
| Meals Logged / Day | 75,000 | 1,000,000 |
| Food Recognition Accuracy | ≥ 90% top-1 | ≥ 96% top-3 |
| 30-Day Retention | 38% | 55% |
| Premium Conversion | 10% | 18% |
| Clinical B2B Partnerships | 5 (dietitian clinics) | 50 |

---

## 5. Target Users & Personas

### Persona 1 — Lisa, The Weight-Loss Tracker
- **Age:** 28 | **Occupation:** Nurse | **Location:** Chicago, IL
- **Goal:** Track calories effortlessly while working long shifts; lose 20 lbs.
- **Pain Points:** Tried MyFitnessPal; abandoned it in 5 days — too much manual entry.
- **Willingness to Pay:** $9.99/month if it works and doesn't require too much effort.

### Persona 2 — Arjun, The Type 2 Diabetic
- **Age:** 51 | **Occupation:** Engineer | **Location:** Bangalore, India
- **Goal:** Understand glycemic impact of every meal to manage blood sugar.
- **Pain Points:** Doctor told him to watch carbs but he has no idea which foods spike his glucose.
- **Willingness to Pay:** $14.99/month for medical-grade nutritional feedback.

### Persona 3 — Emma, The Fitness Enthusiast
- **Age:** 24 | **Occupation:** Personal Trainer | **Location:** London, UK
- **Goal:** Hit precise macro targets (protein/carb/fat split) for bodybuilding competition prep.
- **Pain Points:** Current apps don't separate macros accurately for complex home-cooked meals.
- **Willingness to Pay:** $7.99/month; already pays for MyFitnessPal Premium.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Food Photo Recognition | Photograph any food item/meal → AI returns food name + cal estimate | Top-1 accuracy ≥ 88%; Top-3 accuracy ≥ 95% on test dataset |
| Macronutrient Breakdown | Display protein, carbohydrates, fat, fiber, sugar per serving | Values sourced from USDA FoodData Central; ± 15% accuracy |
| Manual Food Search | Text search for 1,000,000+ foods in database | Search returns in < 500ms |
| Barcode Scanner | Scan packaged food barcode → return exact nutritional label | Coverage: UPC codes in Open Food Facts DB (3M+ products) |
| Daily Calorie Log | Track total calories consumed and remaining vs. daily goal | Goal set during onboarding; adjustable in settings |
| Meal History | Timeline of photos and calorie entries per meal per day | Photos stored in user account history |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Personalized Targets | Goal-based macro targets: cut/bulk/maintain/medical | Uses Harris-Benedict equation + goal modifier |
| Multi-item Meal Detection | Identify 5+ foods on one plate simultaneously | Bounding box + individual item recognition per dish region |
| Restaurant Menu Estimator | Photo of restaurant menu → AI estimates calorie ranges | Covers top 500 US/UK/Indian/Italian chain menus at launch |
| Water Intake Tracker | Log water/liquid consumption; reminder notifications | Integrates with device push/browser notifications |
| Weekly Nutrition Summary | Auto-generated micro/macronutrient gap report | Highlights top 3 nutritional deficiencies for the week |
| Recipe Builder | Input ingredients + quantities → auto-calculate calories | Per-ingredient and per-serving calculation; shareable recipe card |
| Micronutrient Display | Vitamins (A, B, C, D, K), minerals (iron, calcium, zinc, magnesium) | Sourced from USDA database; daily requirement % shown |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Portion Size AI | AI estimates portion size using plate size calibration technique | Error < 25% for standard dish sizes in lab testing |
| Glycemic Index Scoring | Display GI, GL, insulin load per meal | GI data sourced from International GI Database |
| Allergy Flagging | Flag allergens and suggest substitutions | 14 major allergens tracked (EU Allergen Regulation standard) |
| AI Nutritionist Chatbot | Conversational AI for personalized meal planning questions | Powered by GPT-4o fine-tuned on nutrition guidelines |
| CGM Integration | Sync with Dexcom/FreeStyle Libre API for glucose response overlay | Requires user to link CGM device account; EU/US models supported |
| Predictive Hunger Model | Alert user 1 hour before likely overeating window | Based on meal timing history and caloric deficit patterns |
| Lab Test Integration | Upload blood panel PDF → AI adjusts nutrition targets | Extracts key biomarkers: cholesterol, HbA1c, ferritin, Vitamin D |

---

## 7. User Stories & Use Cases

### Epic 1 — Food Logging
- **US-101:** As a busy professional, I want to photograph my meal and get calories in under 5 seconds without touching a keyboard.
- **US-102:** As a calorie tracker, I want to scan a packaged food barcode to get exact nutritional data.
- **US-103:** As a home cook, I want to input my recipe ingredients to calculate total and per-serving calories.

### Epic 2 — Nutrition Intelligence
- **US-201:** As a diabetic, I want to see the glycemic index of my meal before eating it.
- **US-202:** As a bodybuilder, I want to see my exact protein/carb/fat totals vs. my daily target at a glance.
- **US-203:** As a health-conscious user, I want to know what vitamins I'm consistently missing week-over-week.

### Epic 3 — AI Guidance
- **US-301:** As a user on a weight loss plan, I want an AI nutritionist to suggest a healthy dinner based on what I've eaten today.
- **US-302:** As a CGM user, I want to see how today's meals affected my blood glucose so I can make smarter choices tomorrow.
- **US-303:** As a user with lab results, I want the app to adjust my iron and vitamin D targets based on my blood test.

### Epic 4 — Platform Integration
- **US-401:** As a LazyFit user, I want my workout calories automatically deducted from my daily calorie budget.
- **US-402:** As a Fruit Identifier user, I want the nutritional content of a fruit I scan to be auto-added to my daily log.

---

## 8. Technical Architecture

```
┌────────────────────────────────────────────────────┐
│                 Calo Frontend                      │
│       Next.js 14 + TypeScript + TailwindCSS        │
│    Camera API │ Barcode Scanner │ PWA              │
└────────────────────┬───────────────────────────────┘
                     │ REST API / WebSocket
┌────────────────────▼───────────────────────────────┐
│             API Gateway (Kong)                     │
└────────┬──────────────┬──────────────┬─────────────┘
         │              │              │
┌────────▼──────┐ ┌─────▼──────┐ ┌───▼───────────┐
│  Food ID      │ │  Nutrition  │ │  AI Chatbot   │
│  Service      │ │  Service    │ │  Service      │
│  (FastAPI)    │ │  (FastAPI)  │ │  (FastAPI/    │
│               │ │             │ │   GPT-4o)     │
└──────┬────────┘ └─────┬───────┘ └───────────────┘
       │                │
┌──────▼────────────────▼────────────┐
│  AI Food Recognition Engine        │
│  Custom CNN + CLIP + USDA API      │
│  Open Food Facts │ GI Database     │
└────────────────────────────────────┘
       │
┌──────▼───────────────────────────────────┐
│  PostgreSQL │ Redis │ AWS S3             │
│  Dexcom API (CGM) │ Stripe (billing)    │
└──────────────────────────────────────────┘
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Food Image Classification | Custom EfficientNet-B5 fine-tuned on Food-101 + custom 500k image dataset |
| Multi-item Detection | YOLOv8 object detection for plate segmentation |
| Portion Size Estimation | Depth estimation model (MiDaS) + geometric plate calibration |
| Chatbot | GPT-4o fine-tuned on 10,000 dietitian Q&A sessions |
| Allergen Detection | Rule-based mapping from food ID to allergen lookup table |

---

## 9. Data Model

**FoodItem**
```
food_id          UUID PK
name             VARCHAR(200)
brand            VARCHAR(200)
usda_id          VARCHAR(50)
barcode          VARCHAR(50)
calories_per_100g DECIMAL(8,2)
protein_g        DECIMAL(8,2)
carbs_g          DECIMAL(8,2)
fat_g            DECIMAL(8,2)
fiber_g          DECIMAL(8,2)
glycemic_index   INTEGER
allergens        TEXT[] (enum values)
```

**MealLog**
```
log_id           UUID PK
user_id          UUID FK
meal_type        ENUM(breakfast, lunch, dinner, snack)
logged_at        TIMESTAMP
items            JSONB (array of {food_id, quantity_g, calories})
total_calories   DECIMAL(8,2)
total_protein_g  DECIMAL(8,2)
total_carbs_g    DECIMAL(8,2)
total_fat_g      DECIMAL(8,2)
photo_url        TEXT
```

**UserNutritionGoal**
```
goal_id          UUID PK
user_id          UUID FK UNIQUE
daily_calories   INTEGER
protein_g        INTEGER
carbs_g          INTEGER
fat_g            INTEGER
goal_type        ENUM(cut, bulk, maintain, medical)
updated_at       TIMESTAMP
```

---

## 10. API Design

#### POST `/api/v1/identify-food`
```json
// Request (multipart)
{ "image": "<binary>", "meal_type": "lunch" }

// Response
{
  "items": [
    {
      "food_name": "Grilled Chicken Breast",
      "confidence": 0.96,
      "estimated_weight_g": 150,
      "calories": 247,
      "protein_g": 46.5,
      "carbs_g": 0,
      "fat_g": 5.4,
      "allergens": [],
      "glycemic_index": 0
    },
    {
      "food_name": "White Rice",
      "confidence": 0.91,
      "estimated_weight_g": 200,
      "calories": 260,
      "protein_g": 4.8,
      "carbs_g": 56.2,
      "fat_g": 0.4
    }
  ],
  "meal_total": { "calories": 507, "protein_g": 51.3, "carbs_g": 56.2, "fat_g": 5.8 }
}
```

#### GET `/api/v1/logs/daily?date=2026-02-21`
Return all meal entries, totals vs. goals, and water intake for a given day.

#### POST `/api/v1/chatbot/query`
Send a natural language nutrition question; receive GPT-4o response with cited guidance.

---

## 11. UI/UX Requirements

### Screens
1. **Home / Daily Log** — Calorie ring, macro bars, meal cards for the day
2. **Snap Screen** — Camera viewfinder; AI scanning animation; overlay detection boxes
3. **Food Detail** — Full nutritional breakdown; serving size adjuster slider
4. **Weekly Report** — Radar chart (micronutrients), trend graphs, deficiency highlights
5. **AI Nutritionist Chat** — Chat interface; food photo attachments supported
6. **Recipe Builder** — Ingredient add card; auto-calorie calculation; save/share
7. **CGM Connect** — Glucose overlay chart on meal timeline

### Design System
- **Font:** DM Sans (300/500/700)
- **Color:** Vibrant Green `#3DDC84` primary, Dark Charcoal `#1C1C2E` background
- **Calorie Ring:** Animated SVG ring — fills as user logs; color shifts green→amber→red at 90%→100%→110% of goal
- **Snap Animation:** Particle scan effect over food photo during AI processing

---

## 12. Security & Compliance

- Camera/photo data: processed server-side; raw images deleted within 1 hour unless user saves
- **Medical Disclaimer:** App is not a medical device; cannot diagnose or treat medical conditions
- CGM data: encrypted in transit and at rest; user revocable device link
- Lab result PDFs: processed and immediately deleted; extracted data only stored
- GDPR/HIPAA awareness compliance documentation maintained
- Rate limits: Free (10 logs/day), Premium (unlimited)

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| USDA FoodData Central | Nutrition database (2M+ foods) |
| Open Food Facts | Barcode-linked packaged food nutrition data |
| International GI Database | Glycemic index / glycemic load data |
| Dexcom API | CGM blood glucose overlay |
| FreeStyle Libre (LibreView) API | CGM alternative device support |
| LazyFit (Internal API) | Calorie burn data import |
| Fruit Identifier (Internal API) | Auto-log fruit nutrition on scan |
| Stripe | Subscription management |
| OpenAI GPT-4o | AI nutritionist chatbot engine |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Food identification response ≤ 3 seconds p95; UI renders log in < 500ms |
| **Accuracy** | Food recognition ≥ 90% top-1; nutrition values ≤ 15% deviation from lab-measured |
| **Availability** | 99.9% uptime; offline mode allows viewing previous logs |
| **Scalability** | Support 500,000 simultaneous food scans during peak meal hours (12pm–1pm local) |
| **Localization** | 12 languages; international food databases for India, Japan, Italy, Mexico, UK |
| **Accessibility** | Full screen reader support; color-blind safe palette; WCAG 2.1 AA |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–4)
- Food photo recognition (top 5,000 foods)
- Macronutrient breakdown
- Barcode scanner (Open Food Facts)
- Daily calorie log with goal-setting
- Manual food search

### Phase 2 — Enhanced (Month 5–8)
- Multi-item plate detection
- Micronutrient tracking
- Water intake tracker
- Weekly nutrition summary
- Recipe builder
- Premium subscription launch

### Phase 3 — Advanced (Month 9–18)
- Portion size AI estimation
- AI nutritionist chatbot (GPT-4o)
- Glycemic index scoring
- CGM integration (Dexcom, FreeStyle Libre)
- Lab result upload integration
- Clinical B2B dietitian portal

---

*Document Version 1.0 — Calo PRD — PhotoIdentifier Platform | 2026-02-21*
