# PRD: Fruit Identifier
### Product Requirements Document | Version 1.0

---

## 1. Document Control

| Field | Details |
|---|---|
| **Document Title** | Fruit Identifier — Product Requirements Document |
| **Version** | 1.0 |
| **Status** | Approved for Development |
| **Author** | Senior AI Architect — PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Product Lead, Engineering Lead, UX Director, Nutritionist & Food Science Advisor |
| **Classification** | Internal — Confidential |

---

## 2. Executive Summary

**Fruit Identifier** is a nutrition-led AI platform that identifies any fruit or berry from a photograph, delivers complete nutritional intelligence, assesses ripeness, projects shelf life, and provides personalized health-aligned fruit recommendations. It serves health-conscious consumers, dietitians, parents, diabetics, travelers discovering exotic fruits, and farmers optimizing harvest timing.

The global fruit market is valued at **$800 billion**, yet consumers receive minimal nutritional or quality information at point of purchase. Fruit Identifier bridges this gap by making fruit intelligence instant, visual, and personalized. It integrates deeply with the Calo calorie counter sub-app to form a complete nutritional intelligence layer within the Super Web Application.

**Proposed Brand Name:** OrchardIQ

---

## 3. Problem Statement

- Consumers encounter unknown fruit varieties (especially exotic or tropical) with no accessible identification tool at point of purchase.
- Ripeness assessment is subjective — shoppers waste money buying unripe or overripe fruit with no objective measure.
- Diabetics and health-conscious consumers need glycemic index data per fruit to make informed selections — no existing quick-reference tool provides this visually.
- There is no farm-to-table traceability tool accessible to the general consumer market.

---

## 4. Goals & Success Metrics

| Metric | Target (Month 6) | Target (Month 18) |
|---|---|---|
| Monthly Active Users | 120,000 | 1,200,000 |
| Fruits Identified / Day | 50,000 | 500,000 |
| Identification Accuracy | >= 92% | >= 97% |
| Ripeness Prediction Accuracy | >= 80% (vs. manual assessment) | >= 88% |
| Calo Integration Active Users | 30% of Calo users | 50% of Calo users |
| Premium Conversion | 8% | 15% |

---

## 5. Target Users & Personas

### Persona 1 — Elena, The Health Conscious Shopper
- **Age:** 35 | **Occupation:** Yoga Instructor | **Location:** Barcelona, Spain
- **Goal:** Understand nutritional content of every fruit she buys; avoid high GI foods during her low-carb phase.
- **Pain Points:** No quick reference for glycemic load; can't identify tropical fruit at the local market.

### Persona 2 — Thomas, The Type 1 Diabetic
- **Age:** 28 | **Occupation:** Graphic Designer | **Location:** Melbourne, Australia
- **Goal:** Know the exact glycemic impact of any fruit before eating it; dose insulin correctly.
- **Pain Points:** Existing glucose management apps have poor fruit coverage (particularly wild and tropical varieties).

### Persona 3 — Fatou, The Market Farmer
- **Age:** 40 | **Occupation:** Fruit Farmer | **Location:** Ghana
- **Goal:** Identify optimal harvest timing; know which variety of mango reaches peak ripeness first.
- **Pain Points:** No tool to objectively assess ripeness stage across a large orchard without expensive lab equipment.

---

## 6. Feature Specifications

### Phase 1 — Basic Features (MVP)

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Photo Identification | Identify fruit/berry from photo | Accuracy >= 90% on 1,000+ variety dataset including exotic tropicals |
| Nutritional Profile | Calories, protein, carbs, fat, fiber, vitamins (A/B/C/E/K), minerals | USDA FoodData Central sourced |
| Ripeness Assessment | Unripe / Nearly Ripe / Ripe / Overripe classification from color + texture | >= 78% agreement with visual expert assessment |
| Flavor Profile | Sweet / Tart / Bitter / Umami / Neutral description | Flavor data from curated tasting notes database |
| Daily Fruit Log | Track daily fruit consumption; view totals | Integrates with Calo via shared nutrition API |

### Phase 2 — Intermediate Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| Exotic Fruit Discovery Guide | Taste comparison to familiar fruits for 200+ exotic varieties | "Tastes like: mango + lemon with floral notes" style descriptions |
| Glycemic Index & Load | GI and GL per fruit variety per 100g serving | Data from International GI Database; portion-adjustable |
| Allergy & Cross-Reactivity | Flag known allergens; latex-fruit syndrome warnings | 8 major fruit allergens tracked (kiwi, peach, strawberry, etc.) |
| Seasonal Availability Calendar | When is this fruit in season in user's region? | Adapted to user's country/climate; sourced from FAO data |
| Recipe Suggestion Engine | Identified fruit -> curated recipe cards | 5+ recipes per fruit from vetted culinary database |
| Smoothie & Juice Builder | Combine multiple fruits -> nutritional breakdown of custom blend | Supports up to 8 ingredients; scaling by portion weight |
| Organic vs. Conventional | Environmental impact comparison per production method | Data from Environmental Working Group (EWG) Clean 15/Dirty Dozen |

### Phase 3 — Advanced Features

| Feature | Description | Acceptance Criteria |
|---|---|---|
| AI Ripeness Prediction from Color | Color channel analysis predicts exact ripeness stage | Error < 1 ripeness tier on 80% of test samples |
| Shelf Life Estimator | Based on ripeness stage -> estimated days to peak + days until spoil | Model trained on post-harvest science data per variety |
| Price Comparison Integration | Scan barcode on packaged fruit -> compare across local retailer APIs | Integration with grocery APIs where available (Kroger, Walmart, Carrefour) |
| Farm-to-Table Traceability | Scan barcode -> trace farm origin, transport route, certification | Support for QR trace standards (GS1 TraceLink) |
| Personalized Fruit Prescription | Based on health goal (immunity, weight loss, diabetes, energy) -> daily recommended fruits | GPT-4o with nutritional guideline RAG |
| Preservation & Fermentation Guide | Instructions for jam, wine, dehydration, pickling per fruit | 500+ preservation method cards in recipe library |
| Cross-App Nutrition Sync | Auto-log fruit nutrition to Calo daily diary on scan | Internal API; user opt-in per fruit scan |

---

## 7. User Stories & Use Cases

### Epic 1 — Identification & Discovery
- **US-101:** As a traveler, I want to photograph a fruit in a Bangkok market and learn what it is and how to eat it.
- **US-102:** As a shopper, I want to photograph a punnet of strawberries and know if they're at peak ripeness before buying.
- **US-103:** As a parent, I want to discover new fruits my children might enjoy based on flavors they already like.

### Epic 2 — Nutrition & Health
- **US-201:** As a diabetic, I want to know the glycemic load of a mango before eating it to manage my insulin dose.
- **US-202:** As a Calo user, I want my fruit scan to automatically add to my daily nutrition diary.
- **US-203:** As a person with OAS (oral allergy syndrome), I want to be warned if a fruit may trigger my birch pollen allergy.

### Epic 3 — Farm & Commerce
- **US-301:** As a farmer, I want to photograph my crop and get objective ripeness stage data so I time harvest correctly.
- **US-302:** As an ethical consumer, I want to scan a packaged fruit and trace it back to the farm of origin.
- **US-303:** As a price-conscious shopper, I want to compare the price of this specific fruit variety across nearby stores.

---

## 8. Technical Architecture

```
+-------------------------------------------------------------+
|             OrchardIQ Frontend                              |
|    Next.js 14 + TypeScript + TailwindCSS                    |
|    Camera | Barcode Scanner | PWA                           |
+-----------------------+-------------------------------------+
                        | REST API
+-----------------------v-------------------------------------+
|            API Gateway (Kong)                              |
+------+----------------+--------------------+----------------+
       |                |                    |
+------v------+  +------v-----------------------+             |
| Fruit ID    |  | Ripeness + Shelf Life Engine |             |
| Service     |  | (FastAPI + color CNN)         |             |
| (FastAPI)   |  +------------------------------+             |
+------+------+                                              |
       |                                                     |
+------v------------------------------------------------------+
|  AI: EfficientNet-B4 (fruit classification)                |
|  Ripeness: Color channel analysis + regression              |
|  USDA FoodData | International GI DB                        |
|  GS1 TraceLink | Kroger/Walmart Grocery APIs                |
|  PostgreSQL | Redis | S3 | Calo Internal API                |
+-------------------------------------------------------------+
```

### AI / ML Stack
| Component | Technology |
|---|---|
| Fruit Classification | EfficientNet-B4 fine-tuned on Fruits-360 dataset + custom 50k exotic image set |
| Ripeness Detection | Color histogram analysis + CNN regression model per fruit category |
| Shelf Life Estimation | Linear regression model per fruit family (post-harvest science based) |
| Personalized Recommendation | GPT-4o with nutritional science RAG for health goal alignment |

---

## 9. Data Model

**Fruit**
```
fruit_id           UUID PK
common_name        VARCHAR(200)
scientific_name    VARCHAR(200)
family             VARCHAR(100)
origin_region      VARCHAR(200)
flavor_profile     VARCHAR(300)
season_global      TEXT
calories_per_100g  DECIMAL(6,2)
protein_g          DECIMAL(5,2)
carbs_g            DECIMAL(5,2)
fat_g              DECIMAL(5,2)
fiber_g            DECIMAL(5,2)
vitamin_c_mg       DECIMAL(6,2)
glycemic_index     INTEGER
glycemic_load      DECIMAL(4,1)
allergens          TEXT[]
shelf_life_days_ripe INTEGER
```

**RipenessAssessment**
```
assessment_id      UUID PK
user_id            UUID FK
fruit_id           UUID FK
photo_url          TEXT
ripeness_stage     ENUM(unripe, nearly_ripe, ripe, overripe)
confidence         DECIMAL(5,4)
estimated_peak_days INTEGER
estimated_spoil_days INTEGER
assessed_at        TIMESTAMP
```

**FruitLog**  *(linked to Calo MealLog)*
```
log_id             UUID PK
user_id            UUID FK
fruit_id           UUID FK
quantity_g         DECIMAL(7,2)
calories           DECIMAL(7,2)
logged_at          TIMESTAMP
calo_log_id        UUID FK (nullable; set if pushed to Calo)
```

---

## 10. API Design

#### POST `/api/v1/identify`
```json
// Response
{
  "fruit_id": "uuid",
  "common_name": "Rambutan",
  "scientific_name": "Nephelium lappaceum",
  "confidence": 0.94,
  "origin": "Southeast Asia",
  "flavor_profile": "Sweet, juicy, floral — similar to lychee with mild tartness",
  "nutrition_per_100g": {
    "calories": 68, "carbs_g": 16.0, "fiber_g": 0.9, "vitamin_c_mg": 4.9
  },
  "glycemic_index": 51,
  "glycemic_load": 8.4,
  "allergens": [],
  "ripeness": { "stage": "ripe", "peak_days_remaining": 2, "spoil_estimate_days": 4 }
}
```

#### POST `/api/v1/ripeness/analyze`
Submit fruit photo -> return ripeness stage + shelf life estimate.

#### POST `/api/v1/log`
Log fruit to daily intake; optionally push to Calo.

#### GET `/api/v1/prescription?goal=diabetes_management&weight_kg=75`
Returns personalized daily fruit recommendations.

---

## 11. UI/UX Requirements

### Screens
1. **Scan Screen** — Camera with round scan overlay for fruit; ripeness indicator animation
2. **Fruit Result** — Large fruit photo; flavor profile tags; ripeness meter; full nutrition card
3. **Daily Log** — Fruit intake chart; sync indicator with Calo
4. **Exotic Discovery** — Curated exotic fruit catalog; region filter; taste comparison cards
5. **Smoothie Builder** — Ingredient picker; live nutrition total; save/share recipe
6. **Personalized Prescription** — Daily fruit goals card based on health profile
7. **Traceability Viewer** — Farm origin map; certification badges; transport timeline

### Design System
- **Font:** Inter (400/700)
- **Primary Color:** Indigo `#6366F1`
- **Accent Color:** Emerald `#10B981`
- **Background:** White/light gray
- **Border Radius:** 12px cards, 8px buttons
- **Spacing:** 4px base unit
- **Shadows:** 5-level shadow system
- **Ripeness Meter:** Color gradient bar from green (unripe) -> gold (ripe) -> brown (overripe)
- **Nutrition Cards:** Radial chart for macro split; vitamin/mineral grid with daily % badges

---

## 12. Security & Compliance

- Glycemic health data: not medical advice; always recommend consulting dietitian for clinical decisions
- Allergy information: sourced from peer-reviewed databases; emergency allergy disclaimer for anaphylaxis risk fruits
- Farm traceability: barcode scan only; no location beyond country-level stored server-side
- GDPR: full dietary history export and deletion

---

## 13. Integration Requirements

| Provider | Purpose |
|---|---|
| USDA FoodData Central | Nutritional database |
| International GI Database | Glycemic index and load values |
| Fruits-360 Dataset (open) | Fruit classification training data |
| GS1 TraceLink | Farm-to-table QR traceability |
| Kroger API / Walmart Open API | Grocery price comparison |
| EWG (Environmental Working Group) | Pesticide load / organic comparison |
| Calo (Internal API) | Calorie log synchronization |
| OpenAI GPT-4o | Personalized fruit prescription engine |
| Stripe | Premium subscription billing |

---

## 14. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Performance** | Fruit identification <= 2.5 seconds; ripeness analysis <= 3 seconds |
| **Accuracy** | Identification >= 92% top-1; ripeness >= 80% agreement with expert panel |
| **Database** | 1,000+ fruit varieties at launch; updated quarterly |
| **Offline** | Cached profiles for 100 most scanned fruits accessible offline |
| **Localization** | 10 languages; seasonal calendar region-adapted |
| **Availability** | 99.9% uptime |

---

## 15. Release Roadmap

### Phase 1 — MVP (Month 1–3)
- Photo identification (1,000+ fruit varieties)
- Nutritional profile (USDA sourced)
- Ripeness assessment (basic color analysis)
- Daily fruit intake log
- Calo integration for nutrition sync

### Phase 2 — Enhanced (Month 4–7)
- Glycemic index display
- Exotic fruit discovery guide
- Seasonal availability calendar
- Recipe suggestion engine
- Smoothie builder
- Allergy flagging
- Premium subscription launch

### Phase 3 — Advanced (Month 8–14)
- AI shelf life estimator
- Personalized fruit prescription (GPT-4o)
- Farm-to-table barcode traceability
- Grocery price comparison integration
- Preservation & fermentation guide
- Farmer harvest timing tool

---

*Document Version 1.0 — Fruit Identifier PRD — PhotoIdentifier Platform | 2026-02-21*
