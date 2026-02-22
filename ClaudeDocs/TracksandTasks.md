# TracksandTasks — Parallel Build Plan for SuperWebApp
## Subagent-Driven Development with Maximum Concurrency

> **How to use this document:** Each Track is assigned to one subagent. Each Task within a Track takes 10–20 minutes. Tracks are designed so that tasks within a track are **sequential** (each builds on the previous), but **entire tracks run in parallel** with other tracks. The Execution Order at the bottom defines concurrency waves.

---

# TRACK 1: Monorepo & Project Scaffolding

**Purpose:** Create the foundational project structure that all other tracks depend on.
**Subagent scope:** File system setup, package.json configs, tooling, no business logic.

## Task 1.1 — Initialize Turborepo Monorepo (15 min)
**What:** Create a Turborepo monorepo at `f:\PhotoIdentifier` with the standard workspace structure.
**How:**
1. Run `npx -y create-turbo@latest ./` with TypeScript template
2. Create workspace directories: `apps/web`, `packages/ui`, `packages/config`, `packages/types`, `packages/utils`
3. Configure `turbo.json` with pipelines: `build`, `dev`, `lint`, `test`, `type-check`
4. Set up root `package.json` with workspaces pointing to `apps/*` and `packages/*`
**Why:** Turborepo enables incremental builds and parallel task execution across 17+ sub-apps. Without this, builds would take hours instead of minutes.

## Task 1.2 — Initialize Next.js 14 App (15 min)
**What:** Create the main Next.js 14 application in `apps/web` with App Router.
**How:**
1. Run `npx -y create-next-app@latest apps/web --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"` (non-interactive)
2. Configure `next.config.js` with `transpilePackages` for workspace packages
3. Set up path aliases in `tsconfig.json` to reference `@photoidentifier/ui`, `@photoidentifier/types`, `@photoidentifier/utils`
4. Create base layout at `apps/web/src/app/layout.tsx` with Inter font from `next/font/google`
**Why:** Next.js 14 App Router provides SSR, ISR, and file-based routing essential for 17 sub-app navigation.

## Task 1.3 — Configure TailwindCSS with Design Tokens (10 min)
**What:** Set up TailwindCSS 3.x with the unified design token system from the PRDs.
**How:**
1. Create `packages/config/tailwind.config.ts` as the shared Tailwind preset
2. Define custom colors: primary `#6366F1`, emerald `#10B981`, amber `#F59E0B`, red `#EF4444`, rose `#F43F5E`, teal `#14B8A6`
3. Define spacing scale (4px base), border-radius (4/8/12/16px), and 5-level shadow system
4. Set Inter as default sans font family
5. Export preset and consume it in `apps/web/tailwind.config.ts` via `presets: [sharedConfig]`
**Why:** Shared design tokens ensure visual consistency across all 17 sub-apps without duplicating CSS.

## Task 1.4 — Configure ESLint, Prettier, and TypeScript (10 min)
**What:** Set up shared linting and formatting configs for the entire monorepo.
**How:**
1. Create `packages/config/eslint-config.js` extending `next/core-web-vitals` and `@typescript-eslint/recommended`
2. Create `packages/config/.prettierrc` with: `semi: true`, `singleQuote: true`, `tabWidth: 2`, `trailingComma: 'es5'`
3. Create `packages/config/tsconfig.base.json` with strict mode, ES2022 target, module resolution bundler
4. Each workspace `tsconfig.json` extends the base config
**Why:** Enforces code quality and consistency across all sub-apps and packages developed by different subagents.

## Task 1.5 — Set Up Package: @photoidentifier/types (15 min)
**What:** Create the shared TypeScript types package used by all sub-apps.
**How:**
1. Create `packages/types/src/index.ts` as barrel export
2. Define core types: `User`, `UserProfile`, `Subscription`, `AppPermission`, `AuthToken`
3. Define shared AI types: `IdentificationResult`, `ConfidenceScore`, `PhotoUpload`, `AIModel`
4. Define per-app type namespaces: `CoinSnap`, `PlantID`, `DogBreed`, etc. (empty initially, filled by app tracks)
5. Add `package.json` with `name: "@photoidentifier/types"`, `main: "./src/index.ts"`
**Why:** Centralised types prevent drift between frontend and backend, and enable auto-completion for all subagents.

## Task 1.6 — Set Up Package: @photoidentifier/utils (10 min)
**What:** Create shared utility functions package.
**How:**
1. Create `packages/utils/src/index.ts`
2. Add utility functions: `formatCurrency()`, `formatDate()`, `formatConfidence()`, `truncateText()`, `slugify()`
3. Add image utilities: `compressImage()`, `resizeForAI()`, `toBase64()`
4. Add API utilities: `fetcher()` (for SWR/React Query), `handleApiError()`, `buildApiUrl()`
5. Write unit tests in `packages/utils/__tests__/` for each function using Vitest
**Why:** Shared utilities reduce code duplication across 17 sub-apps and ensure consistent formatting.

## Task 1.7 — Create Sub-App Route Structure (15 min)
**What:** Create the file-based routing skeleton for all 17 sub-apps inside Next.js.
**How:**
1. Create route groups in `apps/web/src/app/`: `(platform)/`, plus one folder per app:
   `coinsnap/`, `lazyfit/`, `vinylsnap/`, `calo/`, `rockid/`, `mushroom/`, `musclefit/`, `insectid/`, `birdid/`, `notesnap/`, `fishcare/`, `cardvault/`, `plantid/`, `fruitid/`, `vehicleid/`, `dogbreed/`, `catbreed/`
2. Each sub-app folder gets: `page.tsx` (landing), `identify/page.tsx` (main scan page), `layout.tsx` (sub-app shell)
3. Create `apps/web/src/app/(platform)/layout.tsx` with shared sidebar navigation and sub-app switcher
4. Create placeholder pages that render the app name and a "Coming Soon" badge
**Why:** Establishes the URL structure (`/plantid`, `/coinsnap`, etc.) and enables parallel development of each sub-app.

## Task 1.8 — Docker Compose for Local Development (15 min)
**What:** Create a Docker Compose file for the full local development stack.
**How:**
1. Create `docker-compose.yml` at project root with services:
   - `postgres` (PostgreSQL 16, port 5432, with health check)
   - `redis` (Redis 7, port 6379)
   - `minio` (MinIO, ports 9000/9001, with default bucket `uploads`)
   - `kong` (Kong OSS, ports 8000/8001, declarative config)
   - `kafka` + `zookeeper` (Apache Kafka, port 9092)
2. Create `.env.example` with all environment variables
3. Create `docker-compose.override.yml` for volume mounts
4. Add `scripts/setup-local.sh` that runs `docker compose up -d` and waits for health checks
**Why:** Every subagent needs a consistent local environment to test their work against real services.

## Task 1.9 — Environment Configuration System (10 min)
**What:** Create a centralized environment configuration management system.
**How:**
1. Create `packages/config/env.ts` using `zod` for environment variable validation
2. Define schemas: `DatabaseConfig`, `RedisConfig`, `MinioConfig`, `KongConfig`, `KafkaConfig`, `StripeConfig`, `SupabaseConfig`
3. Create `.env.local.example` for Next.js env vars (NEXT_PUBLIC_ prefix for client)
4. Create `apps/web/src/lib/config.ts` that validates and exports typed env vars
**Why:** Typed environment configs prevent runtime failures from missing or malformed env vars, critical when 15+ tracks run in parallel.

## Task 1.10 — README and Developer Documentation (10 min)
**What:** Create developer onboarding documentation for subagents.
**How:**
1. Create `README.md` with: project overview, tech stack, getting started, folder structure diagram
2. Create `CONTRIBUTING.md` with: branch naming (`track-N/task-description`), commit message format, PR template
3. Create `docs/ARCHITECTURE.md` linking to the SuperWebApp_Nextsteps.md sections
4. Document the subagent workflow: pull latest → work on task → test → commit
**Why:** Subagents need clear documentation to work independently without conflicting with other tracks.

---

# TRACK 2: Design System & UI Component Library

**Purpose:** Build the shared `@photoidentifier/ui` component library used by all 17 sub-apps.
**Subagent scope:** React components, Storybook, no backend, no business logic.
**Depends on:** Track 1 Tasks 1.1–1.3 (monorepo + TailwindCSS tokens)

## Task 2.1 — Initialize UI Package with Storybook (15 min)
**What:** Set up the `@photoidentifier/ui` package with Storybook for component development.
**How:**
1. Create `packages/ui/package.json` with React 18, TypeScript, TailwindCSS as peer deps
2. Run `npx -y storybook@latest init` inside `packages/ui`
3. Configure Storybook to use the shared Tailwind config from `packages/config`
4. Create `packages/ui/src/index.ts` barrel export
5. Create folder structure: `components/`, `hooks/`, `icons/`, `lib/`
**Why:** Storybook enables isolated component development and visual testing, critical when 17 apps consume the library.

## Task 2.2 — Button, Input, and Form Components (15 min)
**What:** Build foundational form components following the unified design system.
**How:**
1. Create `Button.tsx`: variants (primary/secondary/outline/ghost/danger), sizes (sm/md/lg), loading state with spinner
2. Create `Input.tsx`: text/email/password/number with label, helper text, error state, icon prefix
3. Create `Select.tsx`: native select wrapper with custom chevron, error state
4. Create `Textarea.tsx`: auto-resize, character counter
5. Create `FormField.tsx`: wrapper that composes label + input + error message
6. All components use `cn()` utility (clsx + tailwind-merge) for class merging
7. Write Storybook stories for each component showing all variants
**Why:** Every sub-app form (login, settings, collection entry) depends on these primitives.

## Task 2.3 — Card, Badge, and Alert Components (15 min)
**What:** Build content display components used across all sub-apps.
**How:**
1. Create `Card.tsx`: base card with 5 shadow levels, optional header/footer slots, hover effect
2. Create `Badge.tsx`: variants (success/warning/danger/info/neutral), sizes (sm/md), pill shape
3. Create `SafetyBadge.tsx`: color-coded safety indicator (Safe=green, Mild=yellow, Moderate=orange, Severe/Deadly=red) with icon
4. Create `Alert.tsx`: full-width banner with icon, dismiss button, variants matching badge colors
5. Create `Tooltip.tsx`: positioned tooltip using `@floating-ui/react`
6. Write Storybook stories for each
**Why:** SafetyBadge is critical for MycoSafe (mushrooms), PlantIdentifier (toxicity), PictureInsect (danger), and EntomIQ.

## Task 2.4 — PhotoCapture Universal Component (20 min)
**What:** Build the most important shared component — the camera/upload interface used by ALL 17 sub-apps.
**How:**
1. Create `PhotoCapture.tsx` with two modes: Camera (using `navigator.mediaDevices.getUserMedia`) and Upload (drag-and-drop + file picker)
2. Camera mode: live viewfinder, capture button, flash toggle, front/back camera switch
3. Upload mode: drag zone with dashed border, file type validation (JPEG/PNG/HEIC/WebP), max size 10MB
4. After capture/upload: show preview thumbnail with Retake and Confirm buttons
5. On confirm: compress image to max 1024px width using canvas, convert to base64 or Blob
6. Props: `onCapture(file: File)`, `onCancel()`, `aspectRatio`, `overlay` (optional guide overlay component)
7. Add custom overlays: circular (for coins/fruits), rectangular (for cards/banknotes), freeform
8. Write Storybook story showing camera and upload modes
**Why:** This is the #1 interaction for every sub-app — the entire platform's UX hinges on a smooth photo capture flow.

## Task 2.5 — ConfidenceCard and IdentificationResult Components (15 min)
**What:** Build the AI result display components shown after every identification.
**How:**
1. Create `ConfidenceBar.tsx`: horizontal bar 0–100% with color gradient (red<50, amber 50–80, green>80), animated fill
2. Create `ConfidenceCard.tsx`: species/object name, scientific name, confidence bar, photo thumbnail, action buttons (Save, Share, Learn More)
3. Create `IdentificationResult.tsx`: full-page result layout with hero image, confidence card, detail tabs (Info, Care, Safety, Market)
4. Create `TopMatchesList.tsx`: ordered list of top-3 AI matches with confidence percentages
5. All components accept generic props so they work across coins, plants, dogs, birds, etc.
**Why:** Consistent result display across all 17 apps creates platform coherence and reduces per-app development time.

## Task 2.6 — Navigation and Layout Components (15 min)
**What:** Build the platform-level navigation shell.
**How:**
1. Create `Sidebar.tsx`: collapsible sidebar with app icons for all 17 sub-apps, grouped by category (Nature, Collectibles, Health, Automotive)
2. Create `TopBar.tsx`: logo, search bar, notification bell, user avatar dropdown
3. Create `AppShell.tsx`: combines Sidebar + TopBar + main content area, responsive (sidebar collapses to bottom nav on mobile)
4. Create `SubAppHeader.tsx`: per-app header with brand name, brand color accent, back button
5. Create `BottomNav.tsx`: mobile 5-tab navigation (Home, Scan, Collection, Profile, More)
6. Write Storybook story for full layout composition
**Why:** Users must be able to switch between sub-apps seamlessly; the navigation is the glue layer.

## Task 2.7 — Data Visualization Components (15 min)
**What:** Build chart and metric display components for analytics across all apps.
**How:**
1. Create `HealthMetricRing.tsx`: circular SVG gauge (used for BCS, calories, fitness scores) with animated fill and center value
2. Create `TrendChart.tsx`: wrapper around Recharts `AreaChart` with preset styling matching design system
3. Create `StatCard.tsx`: large number + label + trend arrow (up/down/flat) + sparkline
4. Create `DataTable.tsx`: sortable, filterable table with pagination, using `@tanstack/react-table`
5. Create `DonutChart.tsx`: breed composition display (used for DogBreed/CatBreed mixed breed %)
**Why:** Portfolio dashboards, health trackers, and analytics views across every sub-app need consistent visualizations.

## Task 2.8 — Map and Location Components (15 min)
**What:** Build map components for sighting logs, range maps, and community maps.
**How:**
1. Install `maplibre-gl` and `react-map-gl` (MapLibre fork)
2. Create `MapView.tsx`: wrapper with default style (OpenStreetMap tiles), zoom/pan controls
3. Create `SightingMarker.tsx`: custom map marker with species icon, confidence badge
4. Create `HeatmapLayer.tsx`: density visualization for community sighting data
5. Create `RangeOverlay.tsx`: GeoJSON polygon overlay for species ranges (birds, insects, plants)
6. Write Storybook story with example markers and heatmap
**Why:** 8+ sub-apps use maps: Bird (range/hotspots), Insect (pest maps), Plant (invasive alerts), Rock (geology maps), Fish (sighting maps).

## Task 2.9 — Modal, Dialog, and Overlay Components (10 min)
**What:** Build overlay UI components.
**How:**
1. Create `Modal.tsx`: centered modal with backdrop blur, close button, responsive sizing (sm/md/lg/full)
2. Create `Drawer.tsx`: slide-from-right panel for detail views on mobile
3. Create `ConfirmDialog.tsx`: "Are you sure?" dialog with Cancel/Confirm buttons
4. Create `ImageLightbox.tsx`: full-screen image viewer with zoom, pinch, and swipe
5. All modals trap focus, close on Escape, and use `createPortal` for proper stacking
**Why:** Collection details, photo zoom, delete confirmations, and telehealth booking all need modal overlays.

## Task 2.10 — Loading, Empty, and Error State Components (10 min)
**What:** Build state feedback components for consistent UX patterns.
**How:**
1. Create `Spinner.tsx`: animated spinner in 3 sizes using CSS animation
2. Create `Skeleton.tsx`: content placeholder shimmer for loading states (text, card, image variants)
3. Create `EmptyState.tsx`: illustration + heading + description + CTA button
4. Create `ErrorBoundary.tsx`: React error boundary with fallback UI and retry button
5. Create `OfflineBanner.tsx`: detects `navigator.onLine` and shows yellow bar when offline
**Why:** Consistent loading/error states across 17 apps prevent a fragmented user experience.

---

# TRACK 3: Authentication & User Management

**Purpose:** Build the complete auth system (registration, login, SSO, profiles, subscriptions).
**Subagent scope:** Supabase Auth integration, auth pages, user profile CRUD.
**Depends on:** Track 1 Tasks 1.1–1.2, Track 2 Tasks 2.1–2.2 (for form components)

## Task 3.1 — Supabase Client Configuration (10 min)
**What:** Set up the Supabase client SDK for authentication in the Next.js app.
**How:**
1. Install `@supabase/supabase-js` and `@supabase/ssr`
2. Create `apps/web/src/lib/supabase/client.ts` — browser client using `createBrowserClient()`
3. Create `apps/web/src/lib/supabase/server.ts` — server client using `createServerClient()` with cookie handling
4. Create `apps/web/src/lib/supabase/middleware.ts` — middleware helper for auth session refresh
5. Add `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY` to `.env.local`
**Why:** Supabase Auth provides the open-source SSO layer for all 17 sub-apps; the client must be configured correctly for both client and server components.

## Task 3.2 — Auth Middleware for Route Protection (10 min)
**What:** Create Next.js middleware that protects authenticated routes and refreshes sessions.
**How:**
1. Create `apps/web/src/middleware.ts` using `@supabase/ssr` `createServerClient`
2. Define public routes: `/`, `/login`, `/register`, `/forgot-password`, `/auth/callback`
3. All other routes redirect to `/login` if no valid session
4. Middleware refreshes the auth token cookie on every request
5. Add `matcher` config to exclude static assets and API routes
**Why:** Without middleware, users could access premium features and personal data without authentication.

## Task 3.3 — Login Page (15 min)
**What:** Build the login page with email/password and Google OAuth.
**How:**
1. Create `apps/web/src/app/(auth)/login/page.tsx`
2. Build form with: email input, password input, "Remember me" checkbox, "Forgot password?" link
3. Add "Continue with Google" button using `supabase.auth.signInWithOAuth({ provider: 'google' })`
4. Add "Continue with Magic Link" option using `supabase.auth.signInWithOtp({ email })`
5. On success: redirect to `/dashboard` or the URL stored in `redirectTo` query param
6. Show error toast on invalid credentials
7. Style with unified design system (Indigo primary, Inter font, 12px card radius)
**Why:** The login page is the entry point for ALL users of ALL 17 sub-apps — it must be polished and reliable.

## Task 3.4 — Registration Page (15 min)
**What:** Build the registration page with profile creation.
**How:**
1. Create `apps/web/src/app/(auth)/register/page.tsx`
2. Form fields: display name, email, password, confirm password, preferred unit system (metric/imperial)
3. Password validation: min 8 chars, 1 uppercase, 1 number, 1 special character (show strength meter)
4. On register: call `supabase.auth.signUp()`, then insert into `user_profiles` table via Supabase
5. Send email verification (Supabase handles this automatically)
6. Show success page: "Check your email to verify your account"
7. Include Google OAuth alternative: "Or sign up with Google"
**Why:** Registration creates the unified identity that spans all 17 sub-apps.

## Task 3.5 — Auth Callback and OAuth Handler (10 min)
**What:** Handle OAuth redirects and email verification callbacks.
**How:**
1. Create `apps/web/src/app/auth/callback/route.ts` (Route Handler)
2. Extract `code` from URL search params
3. Exchange code for session using `supabase.auth.exchangeCodeForSession(code)`
4. On first-time OAuth login: auto-create `user_profiles` row with Google profile data
5. Redirect to `/dashboard` on success, `/login?error=auth_failed` on failure
**Why:** OAuth callback handling must be correct or users get stuck in a redirect loop after Google login.

## Task 3.6 — User Profile Page (15 min)
**What:** Build the user profile settings page.
**How:**
1. Create `apps/web/src/app/(platform)/profile/page.tsx`
2. Sections: Avatar upload (to MinIO), display name edit, email (read-only), preferred units, locale/language selector
3. Subscription status card: current plan, renewal date, upgrade CTA
4. Connected accounts section: Google status, link/unlink
5. Danger zone: "Delete my account" with confirmation dialog
6. All changes save via Supabase `update()` on `user_profiles` table
**Why:** Users need control over their identity and preferences, and the profile page is where subscription upsell happens.

## Task 3.7 — Auth Context Provider and Hooks (15 min)
**What:** Create React context and hooks for auth state management across the app.
**How:**
1. Create `apps/web/src/providers/AuthProvider.tsx` using React Context
2. On mount: call `supabase.auth.getSession()` to hydrate user state
3. Listen to `supabase.auth.onAuthStateChange()` for real-time session updates
4. Create hooks: `useUser()` (returns user or null), `useRequireAuth()` (redirects if not logged in), `useSubscription()` (returns plan tier)
5. Create `usePermissions(appId)` hook that checks `user_app_permissions` table
6. Wrap the root layout with `<AuthProvider>`
**Why:** Every component in every sub-app needs to know who the current user is and what they can access.

## Task 3.8 — Password Reset Flow (10 min)
**What:** Build forgot password and reset password pages.
**How:**
1. Create `apps/web/src/app/(auth)/forgot-password/page.tsx` — email input → calls `supabase.auth.resetPasswordForEmail()`
2. Create `apps/web/src/app/(auth)/reset-password/page.tsx` — new password + confirm → calls `supabase.auth.updateUser({ password })`
3. Show success/error toasts appropriately
4. Auto-redirect to login after successful reset
**Why:** Password reset is a mandatory auth feature; if it's broken, users are permanently locked out.

## Task 3.9 — Subscription & Payment Integration (20 min)
**What:** Integrate Stripe for subscription management (freemium model).
**How:**
1. Install `stripe` (server) and `@stripe/stripe-js` (client)
2. Create `apps/web/src/app/api/stripe/checkout/route.ts` — creates Stripe Checkout session for selected plan
3. Create `apps/web/src/app/api/stripe/webhook/route.ts` — handles `checkout.session.completed`, `customer.subscription.updated`, `customer.subscription.deleted`
4. On webhook: update `subscriptions` table and `user_profiles.subscription` field
5. Create pricing page at `apps/web/src/app/(platform)/pricing/page.tsx` showing 3 tiers: Free ($0), Single App Premium ($4.99/mo), Platform Pass ($14.99/mo)
6. Each tier card shows feature comparison table
**Why:** Monetization is the business model — without Stripe, there's no revenue from premium features.

## Task 3.10 — Rate Limiting and Usage Tracking (15 min)
**What:** Implement per-user usage tracking for free tier limits.
**How:**
1. Create `usage_tracking` table: `user_id`, `app_id`, `action_type`, `count`, `period_start`, `period_end`
2. Create `apps/web/src/lib/usage.ts` with `checkUsageLimit(userId, appId, action)` and `incrementUsage()`
3. Free tier limits: 20 identifications/day per app, 5 grade predictions/month (CardVault), 30 insect IDs/day
4. When limit reached: show upgrade modal with pricing CTA
5. Premium users: skip all limit checks (return `{ allowed: true }` immediately)
**Why:** Freemium conversion depends on enforcing free-tier limits while making the upgrade path frictionless.

---

# TRACK 4: Backend Services & API Gateway

**Purpose:** Build the FastAPI microservices backbone and Kong API Gateway configuration.
**Subagent scope:** Python backend, API endpoints, Kong config, no frontend.
**Depends on:** Track 1 Task 1.8 (Docker Compose), Track 3 Task 3.1 (Supabase config for JWT validation)

## Task 4.1 — FastAPI Project Template (15 min)
**What:** Create a reusable FastAPI service template that all 17 sub-app services will follow.
**How:**
1. Create `services/template/` with: `main.py`, `config.py`, `models.py`, `schemas.py`, `routes/`, `services/`, `Dockerfile`
2. `main.py`: FastAPI app with CORS, health check endpoint `/health`, structured JSON logging
3. `config.py`: Pydantic `BaseSettings` loading from env vars (DB_URL, REDIS_URL, MINIO_URL, KAFKA_BROKER)
4. `Dockerfile`: Python 3.12-slim, pip install from requirements.txt, uvicorn server
5. Create `requirements-base.txt`: fastapi, uvicorn, sqlalchemy, asyncpg, redis, pydantic, python-multipart
**Why:** A consistent template ensures all 17 services have the same structure, making debugging and maintenance uniform.

## Task 4.2 — Kong API Gateway Configuration (15 min)
**What:** Configure Kong OSS with declarative config for routing to all backend services.
**How:**
1. Create `infrastructure/kong/kong.yml` (declarative DB-less config)
2. Define services and routes for each sub-app: `/api/v1/coinsnap/*` → coinsnap-service:8000, etc.
3. Add JWT plugin globally: validates Supabase JWT on all routes
4. Add rate-limiting plugin: 100 req/min free tier, 1000 req/min premium
5. Add CORS plugin: allow `localhost:3000` (dev) and production domain
6. Add request-size-limiting plugin: 10MB max (for photo uploads)
7. Update `docker-compose.yml` to mount `kong.yml` into Kong container
**Why:** Kong centralizes auth, rate limiting, and routing so individual services don't need to implement these cross-cutting concerns.

## Task 4.3 — Shared Database Connection Module (10 min)
**What:** Create a shared Python package for PostgreSQL and Redis connections used by all services.
**How:**
1. Create `services/shared/database.py`: async SQLAlchemy engine factory with connection pooling (pool_size=10, max_overflow=20)
2. Create `services/shared/redis_client.py`: async Redis client factory using `redis.asyncio`
3. Create `services/shared/minio_client.py`: MinIO client wrapper for file upload/download
4. Create `services/shared/kafka_producer.py`: async Kafka producer for publishing cross-app events
5. Package as `services/shared/` importable by all service Dockerfiles via COPY
**Why:** Every service needs DB/Redis/MinIO/Kafka — centralizing connection logic prevents 17 copies of the same boilerplate.

## Task 4.4 — Image Upload & Processing Service (15 min)
**What:** Build the centralized image upload endpoint used by all 17 sub-apps.
**How:**
1. Create `services/upload-service/` from template
2. `POST /api/v1/upload`: accepts multipart image, validates type (JPEG/PNG/HEIC/WebP), max 10MB
3. Process: resize to max 1024px, convert HEIC→JPEG, strip EXIF (privacy), generate UUID filename
4. Upload to MinIO bucket `uploads/{user_id}/{uuid}.jpg`
5. Return: `{ "image_url": "...", "image_id": "uuid", "width": N, "height": N }`
6. Store metadata in `public.uploaded_images` table
**Why:** Centralizing upload logic ensures consistent image preprocessing (size, format, privacy) before any AI model sees the image.

## Task 4.5 — Notification Service (15 min)
**What:** Build the shared notification microservice for push, email, and in-app notifications.
**How:**
1. Create `services/notification-service/` (Node.js + Express)
2. Kafka consumer: listens to `notification.send` topic
3. Channels: email (via Resend API or SMTP), browser push (Web Push API), in-app (stored in DB)
4. `POST /api/v1/notifications/send`: `{ user_id, channel, title, body, action_url }`
5. `GET /api/v1/notifications/{user_id}`: list in-app notifications with read/unread status
6. Create `notifications` and `notification_preferences` tables
**Why:** Watering reminders (Plant), vaccine reminders (Dog/Cat), rare bird alerts, pest alerts — 10+ sub-apps need notifications.

## Task 4.6 — Search Service (Elasticsearch) (15 min)
**What:** Build a cross-app search service using Elasticsearch.
**How:**
1. Add Elasticsearch 8.x to `docker-compose.yml`
2. Create `services/search-service/` (FastAPI)
3. Define indices: `species` (shared across plant/bird/insect/fish/mushroom), `collectibles` (coin/vinyl/card/note), `vehicles`
4. `POST /api/v1/search`: accepts query string + optional app filter, returns results with source app label
5. Indexing: Kafka consumer listens to `*.identified` events and indexes results into ES
6. Add autocomplete with edge-ngram tokenizer for species name search
**Why:** Users should be able to search "puffin" and find results across Bird (Atlantic Puffin), Plant (Puffin flower), etc.

## Task 4.7 — Analytics & Event Tracking Service (15 min)
**What:** Build the platform analytics service for usage metrics and business intelligence.
**How:**
1. Create `services/analytics-service/` (FastAPI)
2. Kafka consumer: listens to ALL events (*.identified, *.collection.added, user.*, payment.*)
3. Store events in TimescaleDB hypertable: `analytics_events(event_type, user_id, app_id, metadata JSONB, created_at)`
4. Aggregate queries: DAU/MAU per app, identifications/day, conversion funnels
5. `GET /api/v1/analytics/dashboard`: returns platform-wide KPIs (admin only)
6. Create materialized views for daily/weekly/monthly rollups
**Why:** Business decisions (which app to prioritize, where conversion drops) require analytics; can't improve what you don't measure.

## Task 4.8 — Marketplace Service (20 min)
**What:** Build the shared marketplace backend for buying/selling across collectible sub-apps.
**How:**
1. Create `services/marketplace-service/` (Node.js + Express)
2. Tables: `listings` (item, price, seller, status), `transactions` (buyer, seller, amount, stripe_payment_id)
3. `POST /api/v1/marketplace/listings`: create listing with photos, description, price, condition
4. `GET /api/v1/marketplace/listings`: search/filter listings by app, category, price range
5. `POST /api/v1/marketplace/purchase`: initiate Stripe payment intent, create transaction
6. Seller verification: require email confirmation before listing goes live
7. Platform fee: 10% commission on each transaction (configured via env var)
**Why:** CoinSnap, VinylSnap, CardVault, OkayFish, and RockID all have marketplace features — one shared service serves all.

## Task 4.9 — Telehealth Booking Service (15 min)
**What:** Build the shared video consultation booking backend for vet and coaching telehealth.
**How:**
1. Create `services/telehealth-service/` (Node.js + Express)
2. Tables: `providers` (name, credentials, specialties, hourly_rate), `availability_slots`, `bookings`, `sessions`
3. `GET /api/v1/telehealth/providers`: list vets/coaches with availability
4. `POST /api/v1/telehealth/book`: create booking, charge via Stripe, generate Daily.co room URL
5. `POST /api/v1/telehealth/start`: return Daily.co room token for video call
6. Pre-triage form: store symptom/question data attached to booking for provider review
**Why:** BarkIQ, MeowIQ (vet telehealth) and MuscleFit (coaching) all need video consultation — one service handles bookings and video rooms.

## Task 4.10 — API Documentation with OpenAPI (10 min)
**What:** Generate and serve unified API documentation for all services.
**How:**
1. Each FastAPI service auto-generates OpenAPI schema at `/docs` (built-in Swagger UI)
2. Create `infrastructure/api-docs/` with a merged OpenAPI spec aggregating all services
3. Use `openapi-merge-cli` to combine all service specs into one `openapi.yaml`
4. Serve merged docs at `/api/docs` via Kong route to a static file server
5. Add API versioning header: `X-API-Version: v1`
**Why:** Developers and B2B API consumers need complete documentation to integrate with the platform.

---

# TRACK 5: Database Schema & Migrations

**Purpose:** Create all PostgreSQL schemas, tables, and migration files for the entire platform.
**Subagent scope:** SQL DDL, Alembic migrations, seed data. No application code.
**Depends on:** Track 1 Task 1.8 (Docker Compose with PostgreSQL running)

## Task 5.1 — Alembic Migration Setup (10 min)
**What:** Initialize Alembic for database migrations across all schemas.
**How:**
1. Create `database/` directory at project root
2. Run `alembic init database/migrations`
3. Configure `alembic.ini`: `sqlalchemy.url` from env var `DATABASE_URL`
4. Edit `env.py` to import all models and set `target_metadata`
5. Create initial migration: `alembic revision --autogenerate -m "initial_schema"`
6. Add `scripts/migrate.sh` that runs `alembic upgrade head`
**Why:** Alembic tracks schema changes as version-controlled migrations, preventing manual SQL chaos across environments.

## Task 5.2 — Platform Core Tables (15 min)
**What:** Create the shared platform tables: user_profiles, subscriptions, notifications, uploads.
**How:**
1. Migration creates: `user_profiles`, `subscriptions`, `user_app_permissions`, `uploaded_images`, `notifications`, `notification_preferences`, `usage_tracking`, `analytics_events`
2. Add indexes: `user_profiles(username)`, `subscriptions(user_id, status)`, `usage_tracking(user_id, app_id, period_start)`
3. Add `updated_at` trigger function for automatic timestamp updates
4. Add Row Level Security (RLS) policies: users can only read/write their own data
**Why:** These tables are the foundation referenced by all 17 sub-app schemas via foreign keys.

## Task 5.3 — Nature Apps Schemas (Plant, Mushroom, Bird, Insect) (20 min)
**What:** Create database schemas for the 4 nature/biology identification sub-apps.
**How:**
1. `plantid` schema: `plant_species`, `user_plants`, `plant_disease_logs`, `watering_schedules`
2. `mushroom` schema: `mushroom_species` (with `safety_classification ENUM`), `sightings`, `safety_flags`
3. `birdid` schema: `bird_species`, `user_sightings`, `life_lists`, `audio_recordings`
4. `insectid` schema: `insect_species`, `sightings`, `pest_alerts`, `invasive_flags`
5. All species tables include: `common_name`, `scientific_name`, `family`, `description`, `image_url`
6. All sighting tables include: `user_id FK`, `species_id FK`, `latitude`, `longitude`, `photo_urls`, `ai_confidence`, `created_at`
7. Add GiST index on (latitude, longitude) for geographic queries
**Why:** Consistent species + sighting table structure enables shared query patterns and cross-app species search.

## Task 5.4 — Collectibles Apps Schemas (Coin, Vinyl, Card, Banknote) (20 min)
**What:** Create database schemas for the 4 collectible/valuation sub-apps.
**How:**
1. `coinsnap` schema: `coins`, `user_coins`, `coin_market_prices`, `coin_grades`
2. `vinylsnap` schema: `vinyl_records`, `pressings`, `user_vinyl`, `vinyl_market_prices`
3. `cardvault` schema: `sport_cards`, `user_cards`, `price_history`, `grading_submissions`
4. `notesnap` schema: `banknotes`, `user_notes`, `fx_rates_cache`, `counterfeit_checks`
5. All collection tables include: `user_id FK`, `item_id FK`, `condition ENUM`, `purchase_price`, `purchase_date`, `photo_urls`
6. All market price tables use TimescaleDB hypertables with `time` column for efficient time-series queries
7. Add `marketplace_listings` table in shared schema for cross-app marketplace
**Why:** Consistent collectible schema enables shared portfolio dashboards and a unified marketplace service.

## Task 5.5 — Health & Fitness Apps Schemas (Calo, Fruit, LazyFit, MuscleFit) (20 min)
**What:** Create database schemas for the 4 health/fitness sub-apps.
**How:**
1. `calo` schema: `foods`, `meal_logs`, `daily_summaries`, `nutrition_goals`
2. `fruitid` schema: `fruits`, `ripeness_assessments`, `fruit_logs`, `fruit_prescriptions`
3. `lazyfit` schema: `workouts`, `workout_sessions`, `form_analysis_logs`, `user_fitness_level`
4. `musclefit` schema: `training_programs`, `workout_sessions`, `exercise_sets`, `body_composition_logs`, `coach_clients`
5. All session/log tables use TimescaleDB hypertables for time-series analytics
6. Add cross-reference: `fruit_logs.calo_log_id FK` → `calo.meal_logs.log_id` for nutrition sync
**Why:** Fitness and nutrition data is inherently time-series; TimescaleDB hypertables enable efficient trend queries.

## Task 5.6 — Pet & Vehicle Apps Schemas (Dog, Cat, Vehicle, Fish) (20 min)
**What:** Create database schemas for the remaining 4 sub-apps.
**How:**
1. `dogbreed` schema: `dog_breeds`, `user_pets`, `health_records`, `telehealth_sessions`, `training_plans`
2. `catbreed` schema: `cat_breeds`, `user_cats`, `health_logs`, `daily_checkins`, `bcs_assessments`
3. `vehicleid` schema: `vehicles`, `user_garages`, `damage_reports`, `vehicle_recalls`, `insurance_quotes`
4. `fishcare` schema: `fish_species`, `user_tanks`, `water_parameters` (hypertable), `disease_logs`, `tank_livestock`
5. Pet tables include: `breed_composition JSONB` for mixed breed data
6. Vehicle includes: full spec fields (engine, transmission, drivetrain, fuel economy)
**Why:** Each domain has unique data requirements (water chemistry for fish, VIN for vehicles) requiring tailored schemas.

## Task 5.7 — Seed Data Scripts (15 min)
**What:** Create scripts to populate reference data tables with initial records.
**How:**
1. Create `database/seeds/` directory
2. `seed_dog_breeds.py`: Insert 500+ dog breeds from AKC dataset (CSV → SQL INSERT)
3. `seed_cat_breeds.py`: Insert 100+ cat breeds from TICA dataset
4. `seed_plant_species.py`: Insert top 1,000 most common plants with toxicity data
5. `seed_bird_species.py`: Insert 10,000 bird species with eBird codes
6. `seed_fish_species.py`: Insert 3,000 aquarium species from FishBase
7. Create `scripts/seed-all.sh` that runs all seed scripts in order
**Why:** Sub-app developers need reference data in their local DB to build and test features — empty species tables are useless.

## Task 5.8 — Database Performance & Indexing (10 min)
**What:** Add performance indexes and query optimizations across all schemas.
**How:**
1. Add composite indexes on all `(user_id, created_at DESC)` columns for user timeline queries
2. Add GIN index on all `JSONB` columns (breed_composition, measurements, metadata)
3. Add partial indexes: `WHERE is_for_sale = true` on collection tables for marketplace queries
4. Configure connection pooling: PgBouncer in front of PostgreSQL (add to docker-compose)
5. Set `shared_preload_libraries = 'timescaledb'` in PostgreSQL config
6. Create `EXPLAIN ANALYZE` test script for the top 20 most frequent queries
**Why:** Without proper indexing, queries degrade from <100ms to >5s as data grows past 1M rows.

---

# TRACK 6: AI Inference Infrastructure

**Purpose:** Set up the model serving pipeline, model registry, and inference APIs that all 17 sub-apps call.
**Subagent scope:** Python ML services, TensorFlow Serving, ONNX, model config. No frontend.
**Depends on:** Track 1 Task 1.8 (Docker Compose), Track 4 Task 4.1 (FastAPI template)

## Task 6.1 — TensorFlow Serving Docker Setup (15 min)
**What:** Deploy TensorFlow Serving in Docker for server-side model inference.
**How:**
1. Add `tensorflow/serving:latest` to `docker-compose.yml`
2. Create `models/` directory at project root with subdirectories per model
3. Configure TF Serving `models.config` protobuf: define model names and base paths
4. Mount models directory as volume `/models` in container
5. Expose gRPC port 8500 and REST port 8501
6. Create health check script that hits `GET /v1/models/{model_name}`
**Why:** TF Serving handles batching, versioning, and GPU routing — reimplementing this in Python would be slow and fragile.

## Task 6.2 — ONNX Runtime Service Setup (15 min)
**What:** Deploy ONNX Runtime as a secondary inference engine for non-TensorFlow models.
**How:**
1. Create `services/onnx-inference/` with FastAPI wrapper
2. Load ONNX models using `onnxruntime.InferenceSession`
3. Implement `POST /api/v1/inference/onnx`: accepts `{ model_name, input_tensor }`, returns predictions
4. Add model caching: load models once on startup, keep in memory
5. Add Dockerfile with `onnxruntime-gpu` (falls back to CPU if no GPU)
**Why:** Some models (ResNet from PyTorch, custom CNNs) export better to ONNX than TF SavedModel format.

## Task 6.3 — AI Gateway Service (15 min)
**What:** Build a unified AI inference API that routes requests to the correct model backend.
**How:**
1. Create `services/ai-gateway/` (FastAPI)
2. `POST /api/v1/ai/identify`: accepts `{ app_id, image_url }` → routes to correct model
3. Model routing table: `{ "plantid": "plant-efficientnet-b7", "dogbreed": "dog-efficientnet-b5", ... }`
4. Pre-process image: download from MinIO, resize, normalize pixel values (ImageNet mean/std)
5. Post-process: apply softmax, map indices to class labels, return top-K results
6. Add response caching in Redis: same image hash → cached result for 24 hours
**Why:** A single API gateway simplifies frontend code — every sub-app calls the same endpoint with its app_id.

## Task 6.4 — Image Preprocessing Pipeline (15 min)
**What:** Build a standardized image preprocessing module used before every AI inference.
**How:**
1. Create `services/shared/preprocessing.py`
2. Functions: `load_image(url_or_bytes)`, `resize_for_model(img, target_size)`, `normalize_imagenet(img)`, `to_tensor(img)`
3. Model-specific configs: `{ "plant-b7": {"size": 600, "crop": "center"}, "coin-b4": {"size": 380, "crop": "none"} }`
4. Handle all input formats: JPEG, PNG, WebP, HEIC (convert HEIC using pillow-heif)
5. Add EXIF orientation correction (auto-rotate based on EXIF tag)
**Why:** Inconsistent preprocessing is the #1 cause of accuracy drops — a penny misidentified because the image was rotated.

## Task 6.5 — Model Version Registry (15 min)
**What:** Create a model versioning system using MLflow for tracking model deployments.
**How:**
1. Add MLflow server to `docker-compose.yml` (port 5000, PostgreSQL backend, MinIO artifact store)
2. Create `scripts/register-model.py`: uploads model file to MLflow, tags with accuracy metrics
3. Create `scripts/promote-model.py`: moves model from "Staging" to "Production" stage
4. Configure TF Serving to auto-reload when model files change (polling interval 30s)
5. Add rollback script: reverts to previous model version if accuracy drops
**Why:** Without versioning, a bad model deployment could silently degrade accuracy for millions of users.

## Task 6.6 — Placeholder Model Creation (20 min)
**What:** Create lightweight placeholder models for all 17 sub-apps so frontend development can proceed.
**How:**
1. Create `scripts/create-placeholder-models.py`
2. For each sub-app: create a tiny MobileNetV2 model with random weights, export as SavedModel
3. Each model: input shape `(1, 224, 224, 3)`, output: class probabilities array with correct class count
4. Class counts: Plant (1000), Dog (500), Cat (100), Bird (10000), Insect (200000), Coin (10000), etc.
5. Create corresponding class label JSON files: `models/{app}/labels.json`
6. Deploy all placeholders to `models/` directory for TF Serving
**Why:** Frontend sub-app tracks need working AI endpoints to develop result pages — placeholder models return random but structurally correct responses.

## Task 6.7 — TensorFlow.js Browser Models Setup (15 min)
**What:** Set up browser-side AI inference for LazyFit and MuscleFit (MoveNet pose estimation).
**How:**
1. Create `packages/ai-browser/` package
2. Install `@tensorflow/tfjs` and `@tensorflow-models/pose-detection`
3. Create `PoseDetector.ts`: loads MoveNet SinglePose Lightning model, runs inference on video frames
4. Create `FormAnalyzer.ts`: takes keypoints, calculates joint angles, checks against exercise rules
5. Exercise rules object: `{ squat: { knee_angle_min: 70, hip_angle_min: 80 }, ... }`
6. Export as `@photoidentifier/ai-browser` package
**Why:** Pose estimation must run in-browser for real-time feedback — server round-trip would add unacceptable latency.

## Task 6.8 — Audio Inference for BirdNET (15 min)
**What:** Set up the audio analysis pipeline for WingWatch Pro bird song identification.
**How:**
1. Create `services/audio-inference/` (FastAPI)
2. Install `birdnetlib` (Python wrapper for Cornell Lab BirdNET model)
3. `POST /api/v1/ai/audio/identify`: accepts audio file (WAV/MP3/OGG, max 60s)
4. Process: convert to WAV 48kHz, run BirdNET analyzer, return species + confidence
5. Return top-5 species matches with confidence scores and range map data
6. Add audio file storage to MinIO bucket `audio-uploads/`
**Why:** WingWatch Pro's differentiator is audio bird ID — birders can identify birds they hear but can't see.

---

# TRACK 7: Nature & Biology Sub-Apps (6 Apps)

**Purpose:** Build the frontend pages and API routes for Plant, Mushroom, Bird, Insect, Dog, and Cat sub-apps.
**Subagent scope:** Next.js pages, React components, API route handlers for 6 nature apps.
**Depends on:** Track 1 (routes), Track 2 (UI components), Track 5 (DB schemas), Track 6 (AI endpoints)

## Task 7.1 — Plant Identifier: Scan & Result Pages (20 min)
**What:** Build the Plant Identifier scan page and identification result page.
**How:**
1. Create `apps/web/src/app/plantid/identify/page.tsx`: uses `<PhotoCapture>` component
2. On photo confirm: call `POST /api/v1/ai/identify { app_id: "plantid", image_url }` 
3. Result page `apps/web/src/app/plantid/result/[id]/page.tsx`: shows `<ConfidenceCard>` + `<SafetyBadge>` for toxicity
4. Detail tabs: Overview (common name, scientific name, family), Care Guide (water, light, soil), Toxicity (ASPCA data), Gallery
5. "Save to My Garden" button → inserts into `plantid.user_plants`
6. Always show toxicity warning before any other content if plant is toxic
**Why:** Plant Identifier is the highest-demand sub-app — it must be the first fully functional app to validate the platform.

## Task 7.2 — Plant Identifier: My Garden & Care Features (15 min)
**What:** Build the My Garden collection and plant care tracking pages.
**How:**
1. Create `apps/web/src/app/plantid/garden/page.tsx`: grid of user's saved plants with photo, name, last watered
2. Plant detail page with watering schedule using `<Timeline>` component
3. "Water Now" button updates `plantid.watering_schedules` with current timestamp
4. Disease diagnosis page: upload leaf photo → AI identifies disease from PlantVillage model
5. Notifications: schedule watering reminders via notification service (Kafka event `notification.send`)
**Why:** Retention depends on users returning daily to care for their tracked plants — the garden is the sticky feature.

## Task 7.3 — Mushroom Identifier: Safety-Critical Scan (20 min)
**What:** Build the MycoSafe mushroom identification interface with MANDATORY safety features.
**How:**
1. Create `apps/web/src/app/mushroom/identify/page.tsx`: uses `<PhotoCapture>` with freeform overlay
2. Result page: ALWAYS shows `<SafetyBadge>` as the FIRST element — before name, before photo, before anything
3. Safety classification ENUM: `Edible`, `Edible_With_Caution`, `Inedible`, `Toxic`, `Deadly`
4. If `Toxic` or `Deadly`: show red full-width alert with Poison Control number (US: 1-800-222-1222)
5. MANDATORY disclaimer on EVERY result: "NEVER eat a wild mushroom based solely on AI identification"
6. "Similar Toxic Species" section showing lookalikes that are dangerous
7. If confidence < 70%: show "Unable to identify safely — seek expert mycologist advice"
**Why:** MycoSafe is the only sub-app where a mistake could kill someone. Safety-first design is non-negotiable.

## Task 7.4 — Bird Identifier: Photo & Audio Scan (20 min)
**What:** Build the WingWatch Pro bird identification with dual photo+audio input.
**How:**
1. Create `apps/web/src/app/birdid/identify/page.tsx` with TWO tabs: Photo ID and Audio ID
2. Photo tab: `<PhotoCapture>` → `POST /api/v1/ai/identify { app_id: "birdid" }`
3. Audio tab: record button using `navigator.mediaDevices.getUserMedia({ audio: true })`, max 60s
4. Audio → `POST /api/v1/ai/audio/identify` → species results with sonogram visualization
5. Result page: species name, photo gallery, range map (using `<MapView>` + `<RangeOverlay>`), song player
6. "Add to Life List" button → inserts into `birdid.life_lists`
7. "Submit to eBird" button (Phase 2 placeholder)
**Why:** Dual photo+audio identification is WingWatch Pro's killer feature that no other birding web app offers.

## Task 7.5 — Bird Identifier: Life List & Sighting Map (15 min)
**What:** Build the life list tracker and community sighting map.
**How:**
1. Create `apps/web/src/app/birdid/lifelist/page.tsx`: species list with checkmarks, total count, rarity badges
2. Sighting map page: `<MapView>` with `<SightingMarker>` components for user's sightings
3. Community heatmap layer showing popular birding spots (aggregated anonymous data)
4. Species profile page: description, habitat, diet, migration pattern, calls, conservation status
5. Filters: by date range, location, family, order
**Why:** Life listing is the core gamification mechanic in birding — it drives long-term engagement.

## Task 7.6 — Insect Identifier: Scan & Danger System (20 min)
**What:** Build the EntomIQ insect identification with 4-level danger classification.
**How:**
1. Create `apps/web/src/app/insectid/identify/page.tsx`: `<PhotoCapture>` with freeform overlay
2. Result page: species name, order, family + `<SafetyBadge>` for danger level
3. 4-level system: Harmless (green), Mildly Venomous (yellow), Venomous (orange), Dangerous (red)
4. If invasive species detected: show alert with local authority reporting link
5. Pest Management tab: for agricultural pests, show organic + chemical treatment options
6. "Report Sighting" button → GPS-tagged log to `insectid.sightings`
7. Kids Mode toggle: simplified language, fun facts, badge earning system (no personal data for COPPA)
**Why:** EntomIQ serves both curious naturalists AND farmers needing pest identification — the danger system protects both.

## Task 7.7 — Dog Breed Identifier: Scan & Breed Profile (20 min)
**What:** Build the BarkIQ dog breed identification with mixed-breed composition.
**How:**
1. Create `apps/web/src/app/dogbreed/identify/page.tsx`: `<PhotoCapture>`
2. Result: top-3 breed matches + `<DonutChart>` showing breed composition percentages
3. Breed profile page: energy level, trainability, shedding, size bars + health risk accordion
4. "Add to My Dogs" button → creates `dogbreed.user_pets` entry with breed_composition JSONB
5. Health screening: list breed-specific genetic conditions (hip dysplasia, cardiac, eye)
6. Exercise needs: daily minutes recommendation based on breed energy classification
**Why:** 53M rescue dogs in the US have unknown heritage — BarkIQ's mixed breed analysis is its unique value proposition.

## Task 7.8 — Dog Breed: My Dogs & Health Tracker (15 min)
**What:** Build the My Dogs profile manager and health record tracker.
**How:**
1. Create `apps/web/src/app/dogbreed/mydogs/page.tsx`: pet profile cards with photo, name, breed, age
2. Pet detail page: weight chart (`<TrendChart>`), vaccination timeline (`<Timeline>`), medication log
3. "Add Vaccine" form: vaccine name, date administered, next due date, vet name
4. Vaccine reminder: sends notification 7 days and 1 day before `next_due_date`
5. Training Center placeholder: 12-week breed-appropriate training plan (Phase 2 feature)
**Why:** The health tracker creates switching costs — once a user enters all vaccination records, they won't leave.

## Task 7.9 — Cat Breed Identifier: Scan & Profile (20 min)
**What:** Build the MeowIQ cat breed identification with feline-specific features.
**How:**
1. Create `apps/web/src/app/catbreed/identify/page.tsx`: `<PhotoCapture>`
2. Result: breed matches + composition chart + trait bars (vocality, affection, independence, grooming)
3. Breed profile: TICA/CFA data, health risks (HCM, PKD, FIP), shedding, indoor/outdoor suitability
4. "Add to My Cats" → `catbreed.user_cats` entry
5. Behavior interpreter library page: 60 behaviors with illustrated explanations (slow blink, kneading, etc.)
**Why:** MeowIQ differentiates by understanding feline-specific traits that dog apps ignore.

## Task 7.10 — Cat Breed: My Cats & Daily Check-In (15 min)
**What:** Build the My Cats manager and daily health check-in feature.
**How:**
1. Create `apps/web/src/app/catbreed/mycats/page.tsx`: cat card carousel with BCS status indicator
2. Daily Check-In page: photo upload + mood slider (1–5) + notes field
3. On submit: AI compares today's photo against baseline → flags deviations (coat change, posture, face)
4. BCS (Body Condition Score) assessment: submit multi-angle photos → AI returns 1-9 BCS score
5. Weight trend chart + health reminders
**Why:** Cats hide illness — the daily check-in with AI deviation detection is MeowIQ's breakthrough feature.

---

# TRACK 8: Collectibles & Finance Sub-Apps (4 Apps)

**Purpose:** Build CoinSnap, VinylSnap, CardVault, and NoteSnap sub-apps.
**Subagent scope:** Next.js pages, collection management, market data integration.
**Depends on:** Track 1 (routes), Track 2 (UI components), Track 5 (DB schemas), Track 6 (AI endpoints)

## Task 8.1 — CoinSnap: Scan & Coin Profile (20 min)
**What:** Build the CoinLens coin identification and profile display.
**How:**
1. Create `apps/web/src/app/coinsnap/identify/page.tsx`: `<PhotoCapture>` with circular overlay guide
2. Result: country, denomination, year, mint mark, metal composition, diameter
3. Market value section: current eBay sold prices, PCGS price guide range, grade estimate
4. Historical context tab: minting info, historical significance, mintage numbers
5. "Save to Collection" button → `coinsnap.user_coins`
6. Visual similarity search: "Similar Coins" section using CLIP embeddings from Qdrant
**Why:** Coin collectors need instant valuation at coin shows — speed and accuracy drive premium conversion.

## Task 8.2 — CoinSnap: Collection & Portfolio (15 min)
**What:** Build the coin collection manager and portfolio value dashboard.
**How:**
1. Create `apps/web/src/app/coinsnap/collection/page.tsx`: grid of collected coins with photos, grades, values
2. Portfolio dashboard: total value (`<StatCard>`), value trend chart, top-5 most valuable coins
3. Add coin form: manual entry with grade (AG/G/VG/F/VF/EF/AU/MS), purchase price, purchase date
4. CSV export: download collection as spreadsheet
5. Sort/filter: by country, year range, value, grade
**Why:** The portfolio tracker is the premium stickiness feature — collectors won't rebuild a 500-coin catalog elsewhere.

## Task 8.3 — VinylSnap: Scan & Record Profile (20 min)
**What:** Build the VinylSnap label recognition and record detail page.
**How:**
1. Create `apps/web/src/app/vinylsnap/identify/page.tsx`: `<PhotoCapture>` with circular overlay
2. On identify: OCR on label text + visual CNN → match against Discogs database
3. Result: artist, album, pressing variant, year, label, catalog number
4. Market data: Discogs median/low/high price, recent sales chart
5. Condition grading guidance: visual reference for VG/VG+/NM/M grading with example photos
6. "Save to Collection" → `vinylsnap.user_vinyl`
**Why:** VinylSnap's unique value is identifying exact pressing variants — a 1972 UK first press is worth 10x a 1985 reissue.

## Task 8.4 — VinylSnap: Collection & Wishlist (15 min)
**What:** Build the vinyl collection manager and want list.
**How:**
1. Create `apps/web/src/app/vinylsnap/collection/page.tsx`: album art grid, artist, condition, value
2. Wishlist page: add records you're seeking, get notification when marketplace listing matches
3. Collection value chart: total portfolio value over time
4. Integration: "List for sale on Discogs" link (redirect to Discogs with pre-filled data)
5. Statistics: total records, by genre, by decade, by label
**Why:** The Want List with marketplace alerts creates a reason to return daily — "your grail was just listed."

## Task 8.5 — CardVault: Scan & Card Profile (20 min)
**What:** Build the CardVault AI sports card scanner and result display.
**How:**
1. Create `apps/web/src/app/cardvault/identify/page.tsx`: `<PhotoCapture>` with rectangular overlay
2. AI pipeline: OCR (player name, year, set) + visual model (parallel, color variant detection)
3. Result: player name, year, set, parallel/variant, card number
4. Market data: eBay 90-day sales history chart, PSA population report numbers
5. AI Grade Predictor: multi-image upload (front/back/edges/corners) → estimated PSA grade (1-10)
6. "Save to Vault" → `cardvault.user_cards`
**Why:** Grade prediction before spending $50 on PSA submission is CardVault's $400B market differentiator.

## Task 8.6 — CardVault: Collection & Portfolio (15 min)
**What:** Build the sports card collection manager and investment portfolio.
**How:**
1. Create `apps/web/src/app/cardvault/collection/page.tsx`: card grid with photos, player, grade, value
2. Portfolio analytics: total value, ROI %, top gainers/losers, value trend chart
3. Price alerts: set target price → notification when market crosses threshold
4. Batch scan mode: streamlined UI for scanning 50+ cards at a card show (rapid-fire photo)
5. Export: CSV export of entire collection
**Why:** CardVault targets the $40B sports card market — portfolio tracking with ROI analytics appeals to card investors.

## Task 8.7 — NoteSnap: Scan & Currency Info (20 min)
**What:** Build the CurrencyLens banknote identification and exchange rate display.
**How:**
1. Create `apps/web/src/app/notesnap/identify/page.tsx`: `<PhotoCapture>` with rectangular overlay
2. Result: country, denomination, series/year, current value in user's home currency
3. Live exchange rate: fetch from Open Exchange Rates API, update hourly, cache in Redis
4. Security features guide: watermark, security thread, hologram locations for the identified note
5. Collector mode: PMG-style grading reference, mintage data, collectible premium
6. "Save to Collection" → `notesnap.user_notes`
**Why:** 190+ country coverage makes NoteSnap indispensable for international travelers and currency collectors.

## Task 8.8 — NoteSnap: Collection & Exchange Calculator (15 min)
**What:** Build the banknote collection manager and currency conversion tools.
**How:**
1. Create `apps/web/src/app/notesnap/collection/page.tsx`: notes grid with photos, countries, values
2. Exchange calculator: multi-currency converter with live rates
3. Travel mode: "I'm going to Japan" → shows all JPY denominations with security features
4. Collection statistics: by country, by continent, total face value
5. Counterfeit awareness section: common counterfeiting techniques per currency (informational only)
**Why:** The travel mode feature creates utility beyond collecting — business travelers use NoteSnap before every international trip.

---

# TRACK 9: Health & Fitness Sub-Apps (4 Apps)

**Purpose:** Build Calo, Fruit Identifier, LazyFit, and MuscleFit sub-apps.
**Subagent scope:** Next.js pages, health tracking UI, fitness features, nutrition logging.
**Depends on:** Track 1 (routes), Track 2 (UI components), Track 5 (DB schemas), Track 6 (AI endpoints + TF.js)

## Task 9.1 — Calo: Food Scan & Nutrition Display (20 min)
**What:** Build the Calo food identification and nutritional information display.
**How:**
1. Create `apps/web/src/app/calo/identify/page.tsx`: `<PhotoCapture>` for food photo
2. Result: food name, portion estimate (grams), calorie count, macro breakdown (protein/carb/fat)
3. Macro display: horizontal stacked bar chart + individual macro cards
4. "Log to Diary" button with portion size adjuster (slider: 0.5x → 3x serving)
5. Manual search fallback: text search against USDA FoodData Central
6. Barcode scan mode (Phase 2 placeholder): scan packaged food barcode for instant nutrition
**Why:** Calo is the daily-use health hub — users log every meal, creating the highest engagement frequency in the platform.

## Task 9.2 — Calo: Daily Diary & Goal Tracking (15 min)
**What:** Build the food diary and daily calorie/macro goal tracking.
**How:**
1. Create `apps/web/src/app/calo/diary/page.tsx`: meals grouped by Breakfast/Lunch/Dinner/Snacks
2. Daily summary: calorie ring (`<HealthMetricRing>`), macro bars, water intake tracker
3. Goal setting: target calories, protein/carb/fat ratio based on goal (lose/maintain/gain)
4. Weekly trend chart showing daily calorie intake vs target
5. Meal history: past 7 days viewable, tap any day to see detail
6. Cross-app integration: listen for `fruit.scanned` Kafka event → auto-suggest adding to diary
**Why:** The diary + goals create accountability — visualizing progress is the #1 motivator for diet adherence.

## Task 9.3 — Fruit Identifier: Scan & Nutrition (20 min)
**What:** Build the OrchardIQ fruit identification with ripeness and nutrition.
**How:**
1. Create `apps/web/src/app/fruitid/identify/page.tsx`: `<PhotoCapture>` with circular overlay
2. Result: fruit name, variety, ripeness assessment (Unripe/Nearly Ripe/Ripe/Overripe), season
3. Nutrition panel: calories, vitamins, mineral content, glycemic index from USDA FoodData Central
4. Ripeness guide: visual timeline showing optimal eating window
5. "How to eat" section: preparation instructions for exotic fruits
6. "Add to Calo" button: publishes `fruit.scanned` Kafka event → Calo auto-logs nutrition
**Why:** The Calo integration is the key cross-app synergy — fruit scans auto-flow into the daily calorie diary.

## Task 9.4 — Fruit Identifier: Seasonal Guide & Allergies (15 min)
**What:** Build the seasonal availability guide and allergy information features.
**How:**
1. Create `apps/web/src/app/fruitid/seasonal/page.tsx`: monthly calendar showing peak season fruits
2. Regional adaptation: user selects country → shows locally available seasonal fruits
3. Allergy information: cross-reactivity warnings (latex-fruit syndrome, birch pollen-apple, etc.)
4. Storage guide: refrigerator vs counter, ethylene producers/sensitives chart
5. Compare mode: select 2 fruits side-by-side → nutritional comparison table
**Why:** Seasonal guides drive repeat visits — users check what's in season each month.

## Task 9.5 — LazyFit: Workout Browser & Player (20 min)
**What:** Build the LazyFit beginner workout browser and video workout player.
**How:**
1. Create `apps/web/src/app/lazyfit/page.tsx`: workout card grid filtered by duration (5/10/15/20 min), body part, difficulty
2. Workout detail page: title, duration, exercises list with rep/time, difficulty badge
3. Workout player page: full-screen exercise display with timer, rep counter, rest periods
4. Exercise demo: animated GIF or video for each exercise (generate placeholder images)
5. MoveNet integration: enable camera for real-time form correction overlay using `@photoidentifier/ai-browser`
6. Session complete: show summary card with duration, calories, form score
**Why:** LazyFit targets the 80% of people who find fitness apps intimidating — simplicity is the product.

## Task 9.6 — LazyFit: Progress Tracking & Streaks (15 min)
**What:** Build the LazyFit progress dashboard and streak motivation system.
**How:**
1. Create `apps/web/src/app/lazyfit/progress/page.tsx`
2. Streak counter: consecutive days worked out, with fire emoji animation 🔥
3. Weekly calendar: color-coded blocks (green=completed, gray=rest day, red=missed)
4. Stats: total workouts, total minutes, average form score, most worked body part
5. Level system: Beginner → Intermediate → Advanced based on sessions completed + form scores
6. "Ready for more?" CTA: when user hits Advanced level → link to MuscleFit/AthleteOS
**Why:** The streak system creates daily habit formation; the AthleteOS handoff converts power users to the premium fitness app.

## Task 9.7 — MuscleFit: Program Builder & Set Logger (20 min)
**What:** Build the AthleteOS program builder and workout set logging interface.
**How:**
1. Create `apps/web/src/app/musclefit/programs/page.tsx`: 12 pre-built program templates (PPL, 5/3/1, Arnold, GZCLP, nSuns, PHUL, etc.)
2. Program detail: weekly schedule view, exercise list per day, volume targets
3. Active workout page: exercise name → set logger (weight × reps × RPE), rest timer
4. Set logging: < 200ms response time, swipe to delete set, auto-populate from last session
5. PR detection: compare every logged set against historical max → confetti animation on new PR 🎉
6. Offline mode: localStorage backup of active workout, sync when back online
**Why:** Set logging speed is the #1 usability requirement — if it's slower than pen-and-paper, users won't adopt it.

## Task 9.8 — MuscleFit: Analytics & Body Composition (15 min)
**What:** Build the training analytics dashboard and body composition tracking.
**How:**
1. Create `apps/web/src/app/musclefit/analytics/page.tsx`
2. Volume analytics: weekly volume per muscle group bar chart, volume trend over 12 weeks
3. Strength progression: line chart of 1RM estimates per exercise over time
4. Body composition logger: weight, body fat % (manual or AI photo estimate), measurements
5. AI body composition: upload front/side/back photos → CNN estimates body fat % (±3%)
6. Calo integration: display daily calorie intake alongside training volume for body recomp planning
**Why:** Athletes need data — volume tracking and strength progression charts are the retention hooks.

---

# TRACK 10: Technical & Specialty Sub-Apps (3 Apps)

**Purpose:** Build Vehicle Identifier, Rock Identifier, and OkayFish sub-apps.
**Subagent scope:** Next.js pages, specialized domain features, external API integrations.
**Depends on:** Track 1 (routes), Track 2 (UI components), Track 5 (DB schemas), Track 6 (AI endpoints)

## Task 10.1 — Vehicle Identifier: Scan & Spec Sheet (20 min)
**What:** Build the AutoLens car identification and vehicle specification display.
**How:**
1. Create `apps/web/src/app/vehicleid/identify/page.tsx`: `<PhotoCapture>` + VIN text input option
2. Photo result: make, model, year, trim, body style, confidence %
3. VIN decode: if VIN entered, use NHTSA VIN Decoder API for exact specifications
4. Spec sheet: engine, transmission, drivetrain, fuel economy (EPA data), MSRP, safety rating
5. Market value: KBB/Edmunds estimated value range by condition (Fair/Good/Excellent)
6. "Save to My Garage" → `vehicleid.user_garages`
**Why:** AutoLens serves the $2.3T automotive market — instant identification + valuation at dealer lots drives premium signups.

## Task 10.2 — Vehicle: Recall Check & Damage Estimator (15 min)
**What:** Build the NHTSA recall checker and AI damage cost estimator.
**How:**
1. Create `apps/web/src/app/vehicleid/recalls/page.tsx`: enter make/model/year → fetch NHTSA recalls
2. Display: recall number, component, summary, remedy, whether completed
3. Damage estimator page: upload damage photos → Mask R-CNN detects damage areas
4. Cost estimate: XGBoost regression model predicts repair cost range + labor hours
5. Disclaimer: "AI estimate — not a certified appraisal. Get professional assessment before filing claims."
6. Insurance quote CTA: pre-fill vehicle specs → redirect to insurance partner page
**Why:** Recall checking alone creates massive utility — any car buyer can check if a used car has unresolved safety recalls.

## Task 10.3 — Vehicle: My Garage & Maintenance Log (15 min)
**What:** Build the personal vehicle garage and maintenance tracking.
**How:**
1. Create `apps/web/src/app/vehicleid/garage/page.tsx`: vehicle card carousel with photos and key specs
2. Maintenance log: oil changes, tire rotations, inspections with date + mileage
3. Maintenance reminders: based on manufacturer-recommended intervals
4. Service cost tracker: total spend, cost per mile, depreciation curve
5. Fuel economy log: track fill-ups, calculate real-world MPG vs EPA estimate
**Why:** The garage + maintenance log creates daily utility beyond identification — it's a permanent car management tool.

## Task 10.4 — Rock Identifier: Scan & Mineral Profile (20 min)
**What:** Build the RockVision mineral identification and geological profile.
**How:**
1. Create `apps/web/src/app/rockid/identify/page.tsx`: `<PhotoCapture>` with freeform overlay
2. Result: mineral name, rock type (igneous/sedimentary/metamorphic), chemical formula, crystal system
3. Mohs hardness scale: visual indicator showing where the specimen falls (1-10)
4. Identification guide: streak color, luster, cleavage/fracture characteristics
5. Gemstone valuation: if identified as precious/semi-precious → estimated value range
6. "Log Specimen" → GPS-tagged entry in `rockid.geolocations`
**Why:** Field geologists and gem hunters need instant identification — the Mohs + chemical formula display is essential.

## Task 10.5 — Rock Identifier: Collection & Geology Map (15 min)
**What:** Build the rock specimen collection and geological survey map.
**How:**
1. Create `apps/web/src/app/rockid/collection/page.tsx`: specimen grid with photos, names, locations
2. Geology map: `<MapView>` with specimen locations as pins, colored by rock type
3. Geological context: regional geology information based on GPS coordinates
4. Rock vs Mineral vs Fossil classification tabs
5. Specimen compare: select 2 specimens → side-by-side property comparison table
**Why:** GPS-tagged specimen mapping creates a personal geological survey — invaluable for field researchers and hobbyists.

## Task 10.6 — OkayFish: Scan & Species Profile (20 min)
**What:** Build the AquaIQ fish identification and species care profile.
**How:**
1. Create `apps/web/src/app/fishcare/identify/page.tsx`: `<PhotoCapture>`
2. Result: species name, family, maximum size, natural habitat, temperature/pH range
3. Care guide: tank size minimum, diet (herbivore/omnivore/carnivore), aggression level, lifespan
4. Compatibility checker: "Is this fish compatible with my tank?" based on current tank inhabitants
5. "Add to My Tank" → `fishcare.tank_livestock`
6. Disease symptom checker: select visual symptoms → AI suggests diagnosis + treatment protocol
**Why:** Pet store fish buyers need instant compatibility checking — one aggressive fish can destroy a $500 community tank.

## Task 10.7 — OkayFish: Tank Manager & Water Parameters (15 min)
**What:** Build the aquarium tank manager and water chemistry tracker.
**How:**
1. Create `apps/web/src/app/fishcare/tanks/page.tsx`: tank cards with photo, name, volume, livestock count
2. Tank detail: current inhabitants list with compatibility matrix
3. Water parameter logger: pH, ammonia, nitrite, nitrate, temperature (form entry)
4. Water quality chart: `<TrendChart>` showing parameter history over 30 days
5. Alerts: if ammonia > 0.25 ppm or nitrite > 0 → red warning with water change recommendation
6. IoT placeholder: Seneye sensor auto-import (Phase 3)
**Why:** Water quality monitoring is life-or-death for aquarium fish — visual trend charts catch problems before fish show symptoms.

---
