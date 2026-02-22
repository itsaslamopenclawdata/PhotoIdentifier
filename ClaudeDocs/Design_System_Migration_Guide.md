# PhotoIdentifier Platform
# Unified Design System Migration Guide

**Version:** 1.0.0
**Last Updated:** 2026-02-21
**Status:** Implementation Ready

---

## Table of Contents

1. [Overview of Design System Changes](#1-overview-of-design-system-changes)
2. [Before/After Comparison Table](#2-beforeafter-comparison-table)
3. [Typography Migration Guide](#3-typography-migration-guide)
4. [Color Migration Guide](#4-color-migration-guide)
5. [Component Updates](#5-component-updates)
6. [Tailwind CSS Configuration Template](#6-tailwind-css-configuration-template)
7. [Step-by-Step Implementation Plan](#7-step-by-step-implementation-plan)
8. [Testing Checklist](#8-testing-checklist)
9. [Rollback Procedures](#9-rollback-procedures)
10. [Appendices](#10-appendices)

---

## 1. Overview of Design System Changes

### 1.1 Migration Objectives

The Unified Design System establishes a consistent visual and functional experience across all 17 PhotoIdentifier sub-applications while allowing individual brand expression through controlled variations.

**Primary Goals:**
- Achieve visual consistency across all 17 applications
- Reduce development time through reusable components (60% code reduction target)
- Ensure WCAG 2.1 AA accessibility compliance platform-wide
- Enable faster onboarding for new developers
- Create a scalable foundation for future applications

### 1.2 Design Philosophy Principles

| Principle | Description | Implementation |
|-----------|-------------|----------------|
| **Camera First** | Every sub-app's primary action is camera capture | Consistent PhotoCapture module across all apps |
| **3-Second Rule** | All AI identifications complete within 3 seconds p95 | Unified AI Processing Indicator component |
| **Safety Guardrails** | Mushroom, plant, pet apps biased toward safety warnings | Unified alert/pattern for critical safety UI |
| **Progressive Disclosure** | Essential data immediately; advanced data on demand | Consistent card expansion patterns |
| **Unified Consistency** | Standardized tokens with sub-app brand expression | Platform tokens + per-app accent colors |

### 1.3 What's Changing

| Category | Before | After |
|----------|--------|-------|
| **Typography** | Mixed fonts (Roboto, Open Sans, SF Pro, custom) | Unified Inter across all apps |
| **Colors** | Inconsistent color palettes per app | Unified Indigo primary + per-app accent colors |
| **Border Radius** | Various values (4px, 6px, 10px, 16px) | Standardized scale (4/8/12/16/24px) |
| **Spacing** | Inconsistent spacing patterns | 4px base unit scale |
| **Shadows** | Custom shadow definitions | 5-level unified shadow system |
| **Components** | Custom implementations per app | Shared component library |

### 1.4 What's NOT Changing

- Sub-app brand accent colors (each app retains unique identity)
- Domain-specific UI patterns (camera interfaces remain specialized)
- Business logic and feature functionality
- API contracts and data models
- Content and copy (unless inconsistent with new patterns)

---

## 2. Before/After Comparison Table

### 2.1 All 17 Applications Migration Overview

| # | App Name | Brand Name | Current Font | Target Font | Current Primary | Target Primary | Accent Color | Priority |
|---|----------|------------|--------------|-------------|-----------------|----------------|--------------|----------|
| 01 | CoinPrismora | CoinPrismora AI | Roboto | Inter | #3B82F6 (Blue) | #6366F1 (Indigo) | #F59E0B (Amber) | **HIGH** |
| 02 | FitPrismora | FitPrismora | Open Sans | Inter | #10B981 (Green) | #6366F1 (Indigo) | #10B981 (Green) | **HIGH** |
| 03 | VinylPrismora | VinylVault AI | SF Pro Display | Inter | #8B5CF6 (Purple) | #6366F1 (Indigo) | #8B5CF6 (Violet) | MEDIUM |
| 04 | NutriPrismora | NutriLens AI | System UI | Inter | #EF4444 (Red) | #6366F1 (Indigo) | #10B981 (Green) | **HIGH** |
| 05 | RockPrismora | GeoLens AI | Montserrat | Inter | #78350F (Brown) | #6366F1 (Indigo) | #D97706 (Amber) | MEDIUM |
| 06 | ShroomPrismora | ForageSafe AI | Lato | Inter | #059669 (Green) | #6366F1 (Indigo) | #EF4444 (Red - safety) | **HIGH** |
| 07 | MusclePrismora | MusclePrismora | Oswald | Inter | #DC2626 (Red) | #6366F1 (Indigo) | #F97316 (Orange) | MEDIUM |
| 08 | InsectPrismora | InsectPrismora | Source Sans Pro | Inter | #2563EB (Blue) | #6366F1 (Indigo) | #84CC16 (Lime) | LOW |
| 09 | BirdPrismora | BirdPrismora Pro | Merriweather | Inter | #0EA5E9 (Sky) | #6366F1 (Indigo) | #06B6D4 (Cyan) | MEDIUM |
| 10 | NotePrismora | NotePrismora | Helvetica Neue | Inter | #059669 (Green) | #6366F1 (Indigo) | #A855F7 (Purple) | LOW |
| 11 | AquaPrismora | AquaPrismora Pro | Nunito | Inter | #0284C7 (Blue) | #6366F1 (Indigo) | #38BDF8 (Sky) | MEDIUM |
| 12 | CardPrismora | CardPrismora AI | Poppins | Inter | #F59E0B (Amber) | #6366F1 (Indigo) | #EAB308 (Yellow) | LOW |
| 13 | FloraPrismora | FloraLens AI | Raleway | Inter | #22C55E (Green) | #6366F1 (Indigo) | #F59E0B (Amber) | **HIGH** |
| 14 | FruitPrismora | FruitPrismora | Quicksand | Inter | #F97316 (Orange) | #6366F1 (Indigo) | #FB923C (Orange) | MEDIUM |
| 15 | AutoPrismora | AutoPrismora AI | Exo 2 | Inter | #4F46E5 (Indigo) | #6366F1 (Indigo) | #EF4444 (Red) | MEDIUM |
| 16 | PawPrismora | PawPrismora AI | Nunito | Inter | #F59E0B (Amber) | #6366F1 (Indigo) | #D97706 (Amber) | **HIGH** |
| 17 | MeowPrismora | MeowPrismora AI | Nunito | Inter | #8B5CF6 (Purple) | #6366F1 (Indigo) | #A855F7 (Purple) | **HIGH** |

**Migration Priority Legend:**
- **HIGH**: Phase 1 (Weeks 7-10) - Core user-facing apps
- **MEDIUM**: Phase 2 (Weeks 11-12) - Important secondary apps
- **LOW**: Phase 3 (Weeks 13-14) - Remaining apps

### 2.2 Component Migration Summary

| Component | Before State | After State | Affected Apps |
|-----------|-------------|-------------|---------------|
| **Button** | 17 different implementations | Unified Button component (6 variants, 5 sizes) | All 17 |
| **Card** | Mixed padding, borders, shadows | Unified Card (3 variants, consistent padding) | All 17 |
| **Input** | Custom inputs per app | Unified Input (8 types, 3 sizes) | All 17 |
| **Modal** | Various modal libraries | Unified Modal component | All 17 |
| **Navigation** | Custom nav implementations | Unified Navbar/Sidebar components | All 17 |
| **Badge** | Inline styles, span tags | Unified Badge (7 variants, 3 sizes) | All 17 |
| **Alert** | Custom alert banners | Unified Alert (4 variants) | All 17 |
| **Table** | Custom table implementations | Unified Table component | 10 data-heavy apps |
| **PhotoCapture** | 17 camera implementations | 1 shared PhotoCapture module | All 17 |
| **AI Processing Indicator** | Various spinners/loaders | Unified scanning animation | All 17 |

---

## 3. Typography Migration Guide

### 3.1 Font Replacement Mapping

#### Unified Font Family: **Inter**

| App # | App Name | Old Font(s) | Old Weights Used | New Font | Migration Notes |
|-------|----------|-------------|------------------|----------|-----------------|
| 01 | CoinPrismora | Roboto | 400, 500, 700 | Inter | Direct replacement, line-height may need adjustment |
| 02 | FitPrismora | Open Sans | 400, 600, 800 | Inter | Matches well, reduce font-weight by 100 for visual parity |
| 03 | VinylPrismora | SF Pro Display | 300, 400, 600 | Inter | Slightly narrower, adjust letter-spacing on headings |
| 04 | NutriPrismora | System UI | 400, 500, 700 | Inter | Will be more consistent, check number rendering |
| 05 | RockPrismora | Montserrat | 400, 600, 700 | Inter | Montserrat is wider, adjust container widths |
| 06 | ShroomPrismora | Lato | 400, 700 | Inter | Direct replacement, minimal changes needed |
| 07 | MusclePrismora | Oswald | 400, 600, 700 | Inter | Oswald is condensed, expect text reflow |
| 08 | InsectPrismora | Source Sans Pro | 400, 600 | Inter | Very similar, minimal changes |
| 09 | BirdPrismora | Merriweather | 400, 700 | Inter | Merriweather is serif, major visual change |
| 10 | NotePrismora | Helvetica Neue | 400, 500, 700 | Inter | Very similar metrics, direct swap |
| 11 | AquaPrismora | Nunito | 400, 600, 700 | Inter | Nunito is rounded, expect visual personality change |
| 12 | CardPrismora | Poppins | 400, 600, 700 | Inter | Poppins is geometric, slight adjustment needed |
| 13 | FloraPrismora | Raleway | 400, 600 | Inter | Raleway has distinctive style, major change |
| 14 | FruitPrismora | Quicksand | 400, 600, 700 | Inter | Quicksand is rounded, visual change expected |
| 15 | AutoPrismora | Exo 2 | 400, 600, 700 | Inter | Exo 2 is geometric/tech, minimal impact |
| 16 | PawPrismora | Nunito | 400, 600, 700 | Inter | Same as AquaPrismora |
| 17 | MeowPrismora | Nunito | 400, 600, 700 | Inter | Same as AquaPrismora |

### 3.2 Typography Scale Mapping

#### Font Size Migration

| Old Usage | New Token | Value (rem) | Value (px) | Usage |
|-----------|-----------|-------------|------------|-------|
| 11px | `text-xs` | 0.75rem | 12px | Captions, fine print |
| 13px | `text-sm` | 0.875rem | 14px | Secondary text, labels |
| 14px, 15px | `text-base` | 1rem | 16px | Body text, default |
| 16px, 17px | `text-lg` | 1.125rem | 18px | Subheadings |
| 18px, 19px | `text-xl` | 1.25rem | 20px | Section headings |
| 20px, 21px | `text-2xl` | 1.5rem | 24px | Page headings |
| 24px | `text-3xl` | 1.875rem | 30px | Large headings |
| 28px, 30px | `text-4xl` | 2.25rem | 36px | Display headings |
| 36px, 40px | `text-5xl` | 3rem | 48px | Hero text |
| 48px+ | `text-6xl` | 3.75rem | 60px | Large display |

#### Font Weight Migration

| Old Weight | New Token | Value | Migration Notes |
|------------|-----------|-------|-----------------|
| Light (300) | `font-light` | 300 | Use sparingly for secondary text |
| Regular (400) | `font-normal` | 400 | Default body text |
| Medium (500) | `font-medium` | 500 | Emphasized text, labels |
| SemiBold (600) | `font-semibold` | 600 | Headings, important labels |
| Bold (700) | `font-bold` | 700 | Primary headings |
| ExtraBold (800) | `font-extrabold` | 800 | Display text, CTAs |

#### Line Height Migration

| Context | Old Value | New Token | Value |
|---------|-----------|-----------|-------|
| Headings | 1.1-1.3 | `leading-tight` | 1.25 |
| Subheadings | 1.3-1.4 | `leading-snug` | 1.375 |
| Body text | 1.4-1.6 | `leading-normal` | 1.5 |
| Long content | 1.6-1.8 | `leading-relaxed` | 1.625 |
| Data tables | 1.8-2.0 | `leading-loose` | 2.0 |

### 3.3 CSS Implementation Examples

#### HTML/CSS (Plain CSS)

```css
/* BEFORE - App-specific typography */
.coin-snap-heading {
  font-family: 'Roboto', sans-serif;
  font-size: 24px;
  font-weight: 600;
  line-height: 1.2;
}

/* AFTER - Unified typography */
.coin-snap-heading {
  font-family: 'Inter', system-ui, -apple-system, sans-serif;
  font-size: 1.5rem; /* 24px */
  font-weight: 600; /* semibold */
  line-height: 1.25; /* tight */
  letter-spacing: -0.025em; /* tight */
}
```

#### Tailwind CSS Implementation

```tsx
/* BEFORE - Mixed typography */
<h1 className="text-2xl font-semibold font-roboto leading-tight">
  Coin Identification Result
</h1>

/* AFTER - Unified typography */
<h1 className="text-2xl font-semibold leading-tight tracking-tight">
  Coin Identification Result
</h1>

/* Or using design tokens */
<h1 className="heading-lg">
  Coin Identification Result
</h1>
```

#### Styled Components / CSS-in-JS

```tsx
/* BEFORE */
const Heading = styled.h1`
  font-family: 'Roboto', sans-serif;
  font-size: 24px;
  font-weight: 600;
  line-height: 1.2;
`;

/* AFTER */
import { typography } from '@photoidentifier/design-system/tokens';

const Heading = styled.h1`
  font-family: ${typography.fontFamily.base};
  font-size: ${typography.fontSize['2xl']};
  font-weight: ${typography.fontWeight.semibold};
  line-height: ${typography.lineHeight.tight};
  letter-spacing: ${typography.letterSpacing.tight};
`;
```

### 3.4 Font Loading Strategy

#### Google Fonts (Recommended)

```html
<!-- Add to <head> of all applications -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
```

#### Self-Hosted (For Production)

```css
/* For self-hosted Inter (recommended for performance) */
@font-face {
  font-family: 'Inter';
  font-style: normal;
  font-weight: 300 800; /* Variable font support */
  font-display: swap;
  src: url('/fonts/inter-variable.woff2') format('woff2-variations'),
       url('/fonts/inter-variable.woff2') format('woff2');
}
```

### 3.5 Per-App Typography Variations

While Inter is the unified font, apps may use brand fonts for headings only:

| App | Brand Font Exception | Usage Scope |
|-----|---------------------|-------------|
| CoinPrismora | None | Inter everywhere |
| BirdPrismora | Merriweather (headings only) | H1-H3 only |
| MusclePrismora | Oswald (numbers/headings) | Stats and H1 only |
| VinylPrismora | None | Inter everywhere |

---

## 4. Color Migration Guide

### 4.1 Color System Overview

The unified color system consists of:
- **Primary Palette**: Indigo (#6366F1) - platform-wide primary actions
- **Secondary Palette**: Violet (#8B5CF6) - complementary accents
- **Semantic Colors**: Success (Green), Warning (Amber), Error (Red), Info (Blue)
- **Neutral Palette**: Gray scale for backgrounds, borders, text
- **Per-App Accent Colors**: Each app retains unique accent for brand identity

### 4.2 Primary Color Mapping

| Old Primary Color | Hex | New Token | New Hex | Usage |
|-------------------|-----|-----------|---------|-------|
| Various blues | #3B82F6, #2563EB, #0EA5E9, #0284C7 | `primary-500` | #6366F1 | Primary actions, links |
| Various greens | #10B981, #059669, #22C55E | `primary-500` | #6366F1 | Primary actions, links |
| Various reds | #EF4444, #DC2626, #F97316 | `primary-500` | #6366F1 | Primary actions, links |
| Various purples | #8B5CF6, #A855F7 | `primary-500` | #6366F1 | Primary actions, links |
| Various oranges | #F59E0B, #F97316 | `primary-500` | #6366F1 | Primary actions, links |
| Existing Indigo | #4F46E5, #6366F1 | `primary-500` | #6366F1 | No change needed |

### 4.3 Complete Color Token Reference

#### Primary Colors (Indigo)

```css
--primary-50:  #EEF2FF;  /* Background tints */
--primary-100: #E0E7FF;  /* Hover states */
--primary-200: #C7D2FE;  /* Active states */
--primary-300: #A5B4FC;  /* Light accents */
--primary-400: #818CF8;  /* Medium accents */
--primary-500: #6366F1;  /* Primary brand color */
--primary-600: #4F46E5;  /* Hover/pressed */
--primary-700: #4338CA;  /* Active/focused */
--primary-800: #3730A3;  /* Dark overlays */
--primary-900: #312E81;  /* Darkest accents */
```

#### Semantic Colors

```css
/* Success (Green) */
--success-50:  #ECFDF5;
--success-100: #D1FAE5;
--success-200: #A7F3D0;
--success-300: #6EE7B7;
--success-400: #34D399;
--success-500: #10B981;  /* Success default */
--success-600: #059669;
--success-700: #047857;
--success-800: #065F46;
--success-900: #064E3B;

/* Warning (Amber) */
--warning-50:  #FFFBEB;
--warning-100: #FEF3C7;
--warning-200: #FDE68A;
--warning-300: #FCD34D;
--warning-400: #FBBF24;
--warning-500: #F59E0B;  /* Warning default */
--warning-600: #D97706;
--warning-700: #B45309;
--warning-800: #92400E;
--warning-900: #78350F;

/* Error (Red) */
--error-50:  #FEF2F2;
--error-100: #FEE2E2;
--error-200: #FECACA;
--error-300: #FCA5A5;
--error-400: #F87171;
--error-500: #EF4444;  /* Error default */
--error-600: #DC2626;
--error-700: #B91C1C;
--error-800: #991B1B;
--error-900: #7F1D1D;

/* Info (Blue) */
--info-50:  #EFF6FF;
--info-100: #DBEAFE;
--info-200: #BFDBFE;
--info-300: #93C5FD;
--info-400: #60A5FA;
--info-500: #3B82F6;  /* Info default */
--info-600: #2563EB;
--info-700: #1D4ED8;
--info-800: #1E40AF;
--info-900: #1E3A8A;
```

#### Neutral Palette (Gray)

```css
--gray-50:  #F9FAFB;  /* Background lightest */
--gray-100: #F3F4F6;  /* Background lighter */
--gray-200: #E5E7EB;  /* Border light */
--gray-300: #D1D5DB;  /* Border default */
--gray-400: #9CA3AF;  /* Text muted */
--gray-500: #6B7280;  /* Text secondary */
--gray-600: #4B5563;  /* Text primary */
--gray-700: #374151;  /* Text dark */
--gray-800: #1F2937;  /* Text darker */
--gray-900: #111827;  /* Text darkest */
```

### 4.4 Per-App Accent Color Configuration

Each app retains a unique accent color for brand identity within the unified system:

| App | Accent Name | Accent Token | Hex Value | Usage |
|-----|-------------|--------------|-----------|-------|
| CoinPrismora | Amber | `accent-500` | #F59E0B | Rarity badges, highlights |
| FitPrismora | Green | `accent-500` | #10B981 | Progress, achievements |
| VinylPrismora | Violet | `accent-500` | #8B5CF6 | Genre tags, collection |
| NutriPrismora | Green | `accent-500` | #10B981 | Nutrition scores |
| Rock ID | Amber | `accent-500` | #D97706 | Gemstone highlights |
| Mushroom | Red | `accent-500` | #EF4444 | Toxicity warnings |
| MusclePrismora | Orange | `accent-500` | #F97316 | Intensity levels |
| Insect | Lime | `accent-500` | #84CC16 | Beneficial insects |
| Bird | Cyan | `accent-500` | #06B6D4 | Migration alerts |
| NotePrismora | Purple | `accent-500` | #A855F7 | Currency badges |
| Fish | Sky | `accent-500` | #38BDF8 | Water parameters |
| CardPrismora | Yellow | `accent-500` | #EAB308 | Card rarity |
| FloraPrismora | Amber | `accent-500` | #F59E0B | Care reminders |
| Fruit ID | Orange | `accent-500` | #FB923C | Ripeness indicator |
| Vehicle ID | Red | `accent-500` | #EF4444 | Damage alerts |
| Dog ID | Amber | `accent-500` | #D97706 | Breed traits |
| Cat ID | Purple | `accent-500` | #A855F7 | Breed traits |

### 4.5 CSS Variable Definitions

```css
/* Add to :root in all applications */
:root {
  /* Primary - Indigo */
  --color-primary-50: #EEF2FF;
  --color-primary-100: #E0E7FF;
  --color-primary-200: #C7D2FE;
  --color-primary-300: #A5B4FC;
  --color-primary-400: #818CF8;
  --color-primary-500: #6366F1;
  --color-primary-600: #4F46E5;
  --color-primary-700: #4338CA;
  --color-primary-800: #3730A3;
  --color-primary-900: #312E81;

  /* Secondary - Violet */
  --color-secondary-50: #F5F3FF;
  --color-secondary-100: #EDE9FE;
  --color-secondary-200: #DDD6FE;
  --color-secondary-300: #C4B5FD;
  --color-secondary-400: #A78BFA;
  --color-secondary-500: #8B5CF6;
  --color-secondary-600: #7C3AED;
  --color-secondary-700: #6D28D9;
  --color-secondary-800: #5B21B6;
  --color-secondary-900: #4C1D95;

  /* Semantic - Success */
  --color-success-50: #ECFDF5;
  --color-success-100: #D1FAE5;
  --color-success-200: #A7F3D0;
  --color-success-300: #6EE7B7;
  --color-success-400: #34D399;
  --color-success-500: #10B981;
  --color-success-600: #059669;
  --color-success-700: #047857;
  --color-success-800: #065F46;
  --color-success-900: #064E3B;

  /* Semantic - Warning */
  --color-warning-50: #FFFBEB;
  --color-warning-100: #FEF3C7;
  --color-warning-200: #FDE68A;
  --color-warning-300: #FCD34D;
  --color-warning-400: #FBBF24;
  --color-warning-500: #F59E0B;
  --color-warning-600: #D97706;
  --color-warning-700: #B45309;
  --color-warning-800: #92400E;
  --color-warning-900: #78350F;

  /* Semantic - Error */
  --color-error-50: #FEF2F2;
  --color-error-100: #FEE2E2;
  --color-error-200: #FECACA;
  --color-error-300: #FCA5A5;
  --color-error-400: #F87171;
  --color-error-500: #EF4444;
  --color-error-600: #DC2626;
  --color-error-700: #B91C1C;
  --color-error-800: #991B1B;
  --color-error-900: #7F1D1D;

  /* Semantic - Info */
  --color-info-50: #EFF6FF;
  --color-info-100: #DBEAFE;
  --color-info-200: #BFDBFE;
  --color-info-300: #93C5FD;
  --color-info-400: #60A5FA;
  --color-info-500: #3B82F6;
  --color-info-600: #2563EB;
  --color-info-700: #1D4ED8;
  --color-info-800: #1E40AF;
  --color-info-900: #1E3A8A;

  /* Neutral - Gray */
  --color-gray-50: #F9FAFB;
  --color-gray-100: #F3F4F6;
  --color-gray-200: #E5E7EB;
  --color-gray-300: #D1D5DB;
  --color-gray-400: #9CA3AF;
  --color-gray-500: #6B7280;
  --color-gray-600: #4B5563;
  --color-gray-700: #374151;
  --color-gray-800: #1F2937;
  --color-gray-900: #111827;

  /* Semantic mapping */
  --color-bg: #FFFFFF;
  --color-bg-alt: #F9FAFB;
  --color-bg-elevated: #FFFFFF;
  --color-border: #E5E7EB;
  --color-border-strong: #D1D5DB;
  --color-text-primary: #111827;
  --color-text-secondary: #6B7280;
  --color-text-tertiary: #9CA3AF;
  --color-text-inverse: #FFFFFF;
  --color-link: #6366F1;
  --color-link-hover: #4F46E5;
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg: #111827;
    --color-bg-alt: #1F2937;
    --color-bg-elevated: #1F2937;
    --color-border: #374151;
    --color-border-strong: #4B5563;
    --color-text-primary: #F9FAFB;
    --color-text-secondary: #9CA3AF;
    --color-text-tertiary: #6B7280;
    --color-text-inverse: #111827;
    --color-link: #818CF8;
    --color-link-hover: #6366F1;
  }
}
```

### 4.6 Color Migration Examples

#### Button Color Migration

```css
/* BEFORE - App-specific button colors */
.coin-snap-button {
  background-color: #3B82F6; /* Custom blue */
  color: #FFFFFF;
}

.lazyfit-button {
  background-color: #10B981; /* Custom green */
  color: #FFFFFF;
}

/* AFTER - Unified primary button */
.unified-button-primary {
  background-color: var(--color-primary-500); /* #6366F1 */
  color: var(--color-text-inverse);
}

.unified-button-primary:hover {
  background-color: var(--color-primary-600); /* #4F46E5 */
}
```

#### Tailwind Color Migration

```tsx
/* BEFORE */
<button className="bg-blue-500 hover:bg-blue-600 text-white">
  Identify Coin
</button>

<button className="bg-green-500 hover:bg-green-600 text-white">
  Start Workout
</button>

/* AFTER */
<button className="bg-primary-500 hover:bg-primary-600 text-white">
  Identify Coin
</button>

/* Using accent for app-specific highlights */
<button className="bg-accent-500 hover:bg-accent-600 text-white">
  Start Workout
</button>
```

### 4.7 Dark Mode Color Mapping

| Light Mode Token | Dark Mode Value | Usage |
|------------------|-----------------|-------|
| `--color-bg` | #111827 | Main background |
| `--color-bg-alt` | #1F2937 | Alternate backgrounds |
| `--color-border` | #374151 | Borders |
| `--color-text-primary` | #F9FAFB | Primary text |
| `--color-text-secondary` | #9CA3AF | Secondary text |
| `--color-link` | #818CF8 | Links (lighter for dark mode) |

---

## 5. Component Updates

### 5.1 Button Updates

#### Button Variants

| Variant | Background | Text | Border | Usage |
|---------|------------|------|--------|-------|
| **Primary** | `#6366F1` | `#FFFFFF` | none | Primary CTAs, main actions |
| **Secondary** | `#FFFFFF` | `#6366F1` | `#E5E7EB` | Alternative actions |
| **Ghost** | transparent | `#6366F1` | none | Tertiary actions, inline |
| **Danger** | `#EF4444` | `#FFFFFF` | none | Destructive actions |
| **Success** | `#10B981` | `#FFFFFF` | none | Confirm actions |
| **Link** | transparent | `#6366F1` | none | Navigation |

#### Button Sizes

| Size | Height | Padding H | Font Size | Icon Size |
|------|--------|-----------|-----------|-----------|
| **xs** | 28px | 10px | 12px | 14px |
| **sm** | 32px | 14px | 14px | 16px |
| **md** | 40px | 16px | 14px | 18px |
| **lg** | 48px | 20px | 16px | 20px |
| **xl** | 56px | 24px | 18px | 22px |

#### Button Implementation

```tsx
// Button Component Specification
interface ButtonProps {
  variant?: 'primary' | 'secondary' | 'ghost' | 'danger' | 'success' | 'link';
  size?: 'xs' | 'sm' | 'md' | 'lg' | 'xl';
  disabled?: boolean;
  loading?: boolean;
  fullWidth?: boolean;
  iconLeft?: React.ReactNode;
  iconRight?: React.ReactNode;
  onClick?: () => void;
  children: React.ReactNode;
}

// BEFORE - App-specific button
<button className="bg-blue-500 text-white px-4 py-2 rounded-lg">
  Submit
</button>

// AFTER - Unified button
<Button variant="primary" size="md">
  Submit
</Button>
```

#### Button State Styles

| State | Primary | Secondary | Ghost |
|-------|---------|-----------|-------|
| Default | `bg-primary-500` | `bg-white text-primary-500 border-gray-200` | `bg-transparent text-primary-500` |
| Hover | `bg-primary-600` | `bg-gray-50 text-primary-600` | `bg-primary-50 text-primary-600` |
| Active | `bg-primary-700` | `bg-gray-100 text-primary-700` | `bg-primary-100 text-primary-700` |
| Disabled | `bg-gray-300 text-gray-500` | `bg-gray-100 text-gray-400` | `bg-transparent text-gray-400` |
| Loading | `bg-primary-600 + spinner` | Same as disabled | Same as disabled |

### 5.2 Card Updates

#### Card Variants

| Variant | Background | Border | Shadow | Usage |
|---------|------------|--------|--------|-------|
| **Default** | White | Gray-200 | sm | Standard content grouping |
| **Elevated** | White | none | md | Emphasized content |
| **Bordered** | White | Gray-300 | none | Form sections |
| **Interactive** | White | Indigo-200 (hover) | sm (hover) | Clickable cards |
| **Filled** | Gray-50 | none | none | Alternate sections |

#### Card Spacing Standards

| Element | Value |
|---------|-------|
| Card padding | 24px |
| Header padding | 16px 24px (top only) |
| Footer padding | 16px 24px (bottom only) |
| Card gap | 16px |
| Border radius | 12px (default), 8px (compact) |

#### Card Implementation

```tsx
// Card Component Specification
interface CardProps {
  variant?: 'default' | 'elevated' | 'bordered' | 'interactive' | 'filled';
  padding?: 'none' | 'sm' | 'md' | 'lg';
  hoverable?: boolean;
  header?: React.ReactNode;
  footer?: React.ReactNode;
  children: React.ReactNode;
}

// BEFORE - App-specific card
<div className="bg-white rounded-lg shadow-md p-4">
  <h3>Title</h3>
  <p>Content</p>
</div>

// AFTER - Unified card
<Card variant="default" padding="md" header={<h3>Title</h3>}>
  <p>Content</p>
</Card>
```

### 5.3 Navigation Updates

#### Top Navigation Standards

| Element | Height | Padding | Font Size |
|---------|--------|---------|-----------|
| Nav bar | 64px | 0 24px | 14px |
| Logo area | 64px | 0 16px 0 0 | - |
| Nav items | 64px | 0 12px | 14px |

#### Nav Item States

| State | Text | Background | Border |
|-------|------|------------|--------|
| Default | Gray-600 | transparent | none |
| Hover | Gray-900 | Gray-50 | none |
| Active | Indigo-600 | transparent | Indigo-500 bottom (2px) |
| Disabled | Gray-400 | transparent | none |

#### Sidebar Navigation Standards

| Element | Width (collapsed) | Width (expanded) | Item Height |
|---------|-------------------|------------------|-------------|
| Sidebar | 72px | 256px | 40px |

#### Sidebar Item States

| State | Icon | Text | Background |
|-------|------|------|------------|
| Default | Gray-400 | Gray-600 | transparent |
| Hover | Gray-600 | Gray-900 | Gray-50 |
| Active | Indigo-500 | Indigo-600 | Indigo-50 |

### 5.4 Form Component Updates

#### Input Types to Migrate

1. **Text** - Standard text input
2. **Email** - Email with validation
3. **Password** - Password with show/hide
4. **Number** - Numeric input
5. **Tel** - Phone number input
6. **URL** - URL input
7. **Search** - Search with icon
8. **Date** - Date picker
9. **Time** - Time picker
10. **DateTime** - Combined date/time
11. **Textarea** - Multi-line text
12. **Select** - Dropdown selection
13. **Multi-select** - Multiple selection
14. **File upload** - File input
15. **Checkbox** - Boolean selection
16. **Radio** - Single choice
17. **Switch** - Toggle switch
18. **Slider** - Range input

#### Input Sizes

| Size | Height | Padding | Font Size |
|------|--------|---------|-----------|
| **sm** | 32px | 6px 12px | 14px |
| **md** | 40px | 8px 14px | 16px |
| **lg** | 48px | 12px 16px | 16px |

#### Input States

| State | Border | Background | Text | Shadow |
|-------|--------|------------|------|--------|
| Default | Gray-300 | White | Gray-900 | none |
| Focus | Indigo-500 | White | Gray-900 | 0 0 0 3px rgba(99, 102, 241, 0.1) |
| Hover | Gray-400 | White | Gray-900 | none |
| Error | Red-500 | White | Gray-900 | 0 0 0 3px rgba(239, 68, 68, 0.1) |
| Success | Green-500 | White | Gray-900 | 0 0 0 3px rgba(16, 185, 129, 0.1) |
| Disabled | Gray-200 | Gray-50 | Gray-400 | none |

#### Input Border Radius

All inputs use `radius-md` (8px) by default.

#### Input Implementation

```tsx
// Input Component Specification
interface InputProps {
  type?: 'text' | 'email' | 'password' | 'number' | 'tel' | 'url' | 'search';
  size?: 'sm' | 'md' | 'lg';
  state?: 'default' | 'error' | 'success';
  disabled?: boolean;
  placeholder?: string;
  label?: string;
  helperText?: string;
  errorText?: string;
  required?: boolean;
  iconLeft?: React.ReactNode;
  iconRight?: React.ReactNode;
}

// BEFORE - App-specific input
<input className="border border-gray-300 rounded px-3 py-2" />

// AFTER - Unified input
<Input type="text" size="md" label="Email" placeholder="Enter email" />
```

### 5.5 Additional Component Updates

#### Badge Updates

| Variant | Background | Text | Border |
|---------|------------|------|--------|
| Default | Gray-100 | Gray-700 | none |
| Primary | Indigo-100 | Indigo-700 | none |
| Secondary | Violet-100 | Violet-700 | none |
| Success | Green-100 | Green-700 | none |
| Warning | Amber-100 | Amber-700 | none |
| Error | Red-100 | Red-700 | none |
| Info | Blue-100 | Blue-700 | none |
| Outline | White | Gray-600 | Gray-300 |

#### Alert Updates

| Variant | Background | Border | Icon | Text |
|---------|------------|--------|------|------|
| Info | Blue-50 | Blue-200 | Blue-500 | Blue-700 |
| Success | Green-50 | Green-200 | Green-500 | Green-700 |
| Warning | Amber-50 | Amber-200 | Amber-500 | Amber-700 |
| Error | Red-50 | Red-200 | Red-500 | Red-700 |

#### Modal Updates

| Size | Width | Max Width |
|------|-------|-----------|
| sm | 90% | 400px |
| md | 90% | 544px |
| lg | 90% | 768px |
| xl | 90% | 1024px |
| full | 100% | 100% |

Modal specifications:
- Backdrop: `rgba(0, 0, 0, 0.5)`
- Border radius: 12px
- Shadow: `xl`
- Header padding: 20px 24px
- Body padding: 24px
- Footer padding: 16px 24px

---

## 6. Tailwind CSS Configuration Template

### 6.1 Base Configuration

```javascript
// tailwind.config.js
module.exports = {
  content: [
    './src/**/*.{js,jsx,ts,tsx}',
    './components/**/*.{js,jsx,ts,tsx}',
    './app/**/*.{js,jsx,ts,tsx}',
    './pages/**/*.{js,jsx,ts,tsx}',
  ],
  darkMode: 'class', // Enable class-based dark mode
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'system-ui', '-apple-system', 'BlinkMacSystemFont', 'sans-serif'],
        mono: ['JetBrains Mono', 'Fira Code', 'Consolas', 'monospace'],
      },
      fontSize: {
        xs: ['0.75rem', { lineHeight: '1rem' }],      // 12px
        sm: ['0.875rem', { lineHeight: '1.25rem' }],   // 14px
        base: ['1rem', { lineHeight: '1.5rem' }],      // 16px
        lg: ['1.125rem', { lineHeight: '1.75rem' }],   // 18px
        xl: ['1.25rem', { lineHeight: '1.75rem' }],    // 20px
        '2xl': ['1.5rem', { lineHeight: '2rem' }],     // 24px
        '3xl': ['1.875rem', { lineHeight: '2.25rem' }], // 30px
        '4xl': ['2.25rem', { lineHeight: '2.5rem' }],  // 36px
        '5xl': ['3rem', { lineHeight: '1' }],          // 48px
        '6xl': ['3.75rem', { lineHeight: '1' }],       // 60px
      },
      fontWeight: {
        light: '300',
        normal: '400',
        medium: '500',
        semibold: '600',
        bold: '700',
        extrabold: '800',
      },
      colors: {
        // Primary - Indigo
        primary: {
          50: '#EEF2FF',
          100: '#E0E7FF',
          200: '#C7D2FE',
          300: '#A5B4FC',
          400: '#818CF8',
          500: '#6366F1',
          600: '#4F46E5',
          700: '#4338CA',
          800: '#3730A3',
          900: '#312E81',
        },
        // Secondary - Violet
        secondary: {
          50: '#F5F3FF',
          100: '#EDE9FE',
          200: '#DDD6FE',
          300: '#C4B5FD',
          400: '#A78BFA',
          500: '#8B5CF6',
          600: '#7C3AED',
          700: '#6D28D9',
          800: '#5B21B6',
          900: '#4C1D95',
        },
        // Semantic - Success
        success: {
          50: '#ECFDF5',
          100: '#D1FAE5',
          200: '#A7F3D0',
          300: '#6EE7B7',
          400: '#34D399',
          500: '#10B981',
          600: '#059669',
          700: '#047857',
          800: '#065F46',
          900: '#064E3B',
        },
        // Semantic - Warning
        warning: {
          50: '#FFFBEB',
          100: '#FEF3C7',
          200: '#FDE68A',
          300: '#FCD34D',
          400: '#FBBF24',
          500: '#F59E0B',
          600: '#D97706',
          700: '#B45309',
          800: '#92400E',
          900: '#78350F',
        },
        // Semantic - Error
        error: {
          50: '#FEF2F2',
          100: '#FEE2E2',
          200: '#FECACA',
          300: '#FCA5A5',
          400: '#F87171',
          500: '#EF4444',
          600: '#DC2626',
          700: '#B91C1C',
          800: '#991B1B',
          900: '#7F1D1D',
        },
        // Semantic - Info
        info: {
          50: '#EFF6FF',
          100: '#DBEAFE',
          200: '#BFDBFE',
          300: '#93C5FD',
          400: '#60A5FA',
          500: '#3B82F6',
          600: '#2563EB',
          700: '#1D4ED8',
          800: '#1E40AF',
          900: '#1E3A8A',
        },
        // Neutral - Gray
        gray: {
          50: '#F9FAFB',
          100: '#F3F4F6',
          200: '#E5E7EB',
          300: '#D1D5DB',
          400: '#9CA3AF',
          500: '#6B7280',
          600: '#4B5563',
          700: '#374151',
          800: '#1F2937',
          900: '#111827',
        },
      },
      borderRadius: {
        '4': '4px',
        '8': '8px',
        '12': '12px',
        '16': '16px',
        '24': '24px',
      },
      spacing: {
        '18': '4.5rem',
        '88': '22rem',
        '128': '32rem',
      },
      boxShadow: {
        'xs': '0 1px 2px 0 rgb(0 0 0 / 0.05)',
        'sm': '0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)',
        'md': '0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)',
        'lg': '0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)',
        'xl': '0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)',
        '2xl': '0 25px 50px -12px rgb(0 0 0 / 0.25)',
      },
      zIndex: {
        'base': '0',
        'above': '10',
        'dropdown': '100',
        'sticky': '200',
        'overlay': '300',
        'modal': '400',
        'popover': '500',
        'maximum': '9999',
      },
      animation: {
        'spin-slow': 'spin 3s linear infinite',
        'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite',
      },
    },
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/aspect-ratio'),
  ],
};
```

### 6.2 Per-App Accent Color Extension

```javascript
// tailwind.config.js - App-specific accent extension
// Example for FitPrismora (green accent)

module.exports = {
  theme: {
    extend: {
      colors: {
        // Add app-specific accent color
        accent: {
          50: '#ECFDF5',
          100: '#D1FAE5',
          200: '#A7F3D0',
          300: '#6EE7B7',
          400: '#34D399',
          500: '#10B981', // Main accent
          600: '#059669',
          700: '#047857',
          800: '#065F46',
          900: '#064E3B',
        },
      },
    },
  },
};
```

### 6.3 Global CSS Setup

```css
/* app/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  /* Import Inter font */
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500&display=swap');

  /* Base styles */
  * {
    @apply border-gray-200;
  }

  html {
    @apply text-gray-900 bg-white;
    font-feature-settings: 'cv11', 'ss01';
    font-variation-settings: 'opsz' 32;
  }

  body {
    @apply antialiased;
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  /* Focus ring for accessibility */
  *:focus-visible {
    @apply outline-none ring-2 ring-primary-500 ring-offset-2;
  }

  /* Selection color */
  ::selection {
    @apply bg-primary-100 text-primary-900;
  }
}

@layer components {
  /* Heading component classes */
  .heading-display {
    @apply text-5xl font-extrabold tracking-tight leading-tight;
  }

  .heading-1 {
    @apply text-4xl font-bold tracking-tight leading-tight;
  }

  .heading-2 {
    @apply text-2xl font-semibold tracking-tight leading-tight;
  }

  .heading-3 {
    @apply text-xl font-semibold tracking-tight;
  }

  .heading-4 {
    @apply text-lg font-semibold;
  }

  /* Text component classes */
  .body-large {
    @apply text-base font-normal;
  }

  .body {
    @apply text-sm font-normal;
  }

  .body-small {
    @apply text-xs font-normal text-gray-600;
  }

  /* Card component */
  .card {
    @apply bg-white rounded-lg shadow-sm border border-gray-200;
  }

  .card-interactive {
    @apply card cursor-pointer transition-shadow duration-200 hover:shadow-md;
  }

  /* Button base */
  .btn {
    @apply inline-flex items-center justify-center font-medium transition-colors duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary-500 focus-visible:ring-offset-2 disabled:opacity-50 disabled:cursor-not-allowed;
  }
}

@layer utilities {
  /* Scrollbar styling */
  .scrollbar-thin {
    scrollbar-width: thin;
    scrollbar-color: theme('colors.gray.300') theme('colors.gray.100');
  }

  .scrollbar-thin::-webkit-scrollbar {
    width: 8px;
    height: 8px;
  }

  .scrollbar-thin::-webkit-scrollbar-track {
    @apply bg-gray-100;
  }

  .scrollbar-thin::-webkit-scrollbar-thumb {
    @apply bg-gray-300 rounded-full;
  }

  .scrollbar-thin::-webkit-scrollbar-thumb:hover {
    @apply bg-gray-400;
  }
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
  @layer base {
    html {
      @apply text-gray-100 bg-gray-900;
    }
  }
}

/* Dark mode class-based */
.dark {
  @layer base {
    html {
      @apply text-gray-100 bg-gray-900;
    }
  }
}
```

### 6.4 TypeScript Types for Design Tokens

```typescript
// src/types/design-tokens.ts

export type Color = {
  50: string;
  100: string;
  200: string;
  300: string;
  400: string;
  500: string;
  600: string;
  700: string;
  800: string;
  900: string;
};

export type Colors = {
  primary: Color;
  secondary: Color;
  success: Color;
  warning: Color;
  error: Color;
  info: Color;
  gray: Color;
};

export type FontSize = 'xs' | 'sm' | 'base' | 'lg' | 'xl' | '2xl' | '3xl' | '4xl' | '5xl' | '6xl';

export type FontWeight = 'light' | 'normal' | 'medium' | 'semibold' | 'bold' | 'extrabold';

export type Spacing = 0 | 1 | 2 | 3 | 4 | 5 | 6 | 8 | 10 | 12 | 16 | 20 | 24;

export type BorderRadius = 4 | 8 | 12 | 16 | 24 | 'full';

export type ShadowSize = 'xs' | 'sm' | 'md' | 'lg' | 'xl' | '2xl' | 'none';

export type ButtonVariant = 'primary' | 'secondary' | 'ghost' | 'danger' | 'success' | 'link';

export type ButtonSize = 'xs' | 'sm' | 'md' | 'lg' | 'xl';

export type InputSize = 'sm' | 'md' | 'lg';

export type CardVariant = 'default' | 'elevated' | 'bordered' | 'interactive' | 'filled';
```

---

## 7. Step-by-Step Implementation Plan

### 7.1 Migration Phases Overview

| Phase | Duration | Apps | Focus |
|-------|----------|------|-------|
| **Phase 0** | Week 0 | Platform | Design system package setup |
| **Phase 1** | Weeks 1-2 | Platform | Core components development |
| **Phase 2** | Weeks 3-4 | Platform | Navigation & layout components |
| **Phase 3** | Weeks 5-6 | Platform | Component library finalization |
| **Phase 4** | Weeks 7-10 | 4 High-Priority Apps | App migrations |
| **Phase 5** | Weeks 11-12 | 6 Medium-Priority Apps | App migrations |
| **Phase 6** | Weeks 13-14 | 7 Low-Priority Apps | App migrations |
| **Phase 7** | Weeks 15-16 | All | Polish, testing, launch |

### 7.2 Detailed Phase 0: Platform Foundation (Week 0)

**Objective:** Set up the design system as a standalone package

#### Tasks:

1. **Create Design System Package Structure**
```bash
mkdir -p packages/design-system
cd packages/design-system
npm init -y
```

2. **Install Core Dependencies**
```bash
npm install react react-dom
npm install -D tailwindcss typescript @types/react @types/react-dom
npm install -D @tailwindcss/forms @tailwindcss/typography @tailwindcss/aspect-ratio
```

3. **Configure Package Exports**
```json
{
  "name": "@photoidentifier/design-system",
  "version": "1.0.0",
  "main": "dist/index.js",
  "module": "dist/index.esm.js",
  "types": "dist/index.d.ts",
  "exports": {
    ".": "./dist",
    "./components": "./dist/components",
    "./tokens": "./dist/tokens",
    "./styles": "./dist/styles.css"
  }
}
```

4. **Create Component Directory Structure**
```
packages/design-system/
├── src/
│   ├── components/
│   │   ├── buttons/
│   │   ├── forms/
│   │   ├── cards/
│   │   ├── navigation/
│   │   ├── feedback/
│   │   └── overlays/
│   ├── tokens/
│   │   ├── colors.ts
│   │   ├── typography.ts
│   │   ├── spacing.ts
│   │   └── index.ts
│   ├── styles/
│   │   └── globals.css
│   └── index.ts
├── tailwind.config.js
└── tsconfig.json
```

### 7.3 Phase 1: Core Components (Weeks 1-2)

#### Week 1: Component Foundation

**Day 1-2: Button Component**
- Create Button base component
- Implement all 6 variants (primary, secondary, ghost, danger, success, link)
- Implement 5 sizes (xs, sm, md, lg, xl)
- Add loading state
- Add icon support (left/right)
- Write stories for all combinations

**Day 3-4: Input Components**
- Create Input base component
- Implement Text, Email, Password, Number inputs
- Implement Textarea
- Implement Select
- Add validation states (default, error, success)
- Write stories

**Day 5: Card Component**
- Create Card base component
- Implement 5 variants
- Add header/footer slots
- Write stories

#### Week 2: Form & Feedback Components

**Day 1-2: Additional Form Components**
- Checkbox component
- Radio component
- Switch component
- Slider component
- File upload component

**Day 3-4: Feedback Components**
- Alert component (4 variants)
- Badge component (7 variants)
- Progress/Spinner component
- Toast notification component

**Day 5: Component Documentation**
- Document all props
- Create usage examples
- Set up Storybook

### 7.4 Phase 2: Navigation & Layout (Weeks 3-4)

#### Week 3: Navigation

**Day 1-3: Navigation Components**
- Navbar component (top navigation)
- Sidebar component (collapsible)
- Breadcrumbs component
- Pagination component
- Tab component

**Day 4-5: Overlay Components**
- Modal component (all sizes)
- Dropdown component
- Tooltip component
- Popover component

#### Week 4: Layout

**Day 1-3: Layout Components**
- Container component
- Grid system
- Stack component (flex spacing)
- Separator/Divider component

**Day 4-5: Data Display**
- Table component
- Avatar component
- Tag/Chip component

### 7.5 Phase 3: Component Library Finalization (Weeks 5-6)

#### Week 5: Platform Components

**PhotoCapture Module** (Shared across all 17 apps)
- Camera viewfinder
- Image preview
- Crop and zoom
- Flash toggle
- Gallery fallback

**AI Processing Indicator**
- Unified scanning animation
- Progress feedback
- Cancellation support

**Identification Result Card**
- Base card structure
- Confidence display
- Action buttons
- Expandable details

#### Week 6: Testing & Documentation

- Accessibility audit (all components)
- Cross-browser testing
- Mobile responsiveness testing
- Dark mode testing
- Documentation completion
- Storybook publication

### 7.6 Phase 4: High-Priority App Migrations (Weeks 7-10)

#### App Migration Order (High Priority)

| Week | App | Current Stack | Migration Complexity |
|------|-----|---------------|---------------------|
| 7 | CoinPrismora | Next.js + Custom CSS | Medium |
| 7-8 | FitPrismora | Next.js + Tailwind | Low |
| 8-9 | NutriPrismora | Next.js + Custom CSS | Medium |
| 9-10 | FloraPrismora | Next.js + Custom CSS | Medium |

#### Week 7: CoinPrismora Migration

**Day 1: Setup**
```bash
cd apps/coinsnap
npm install @photoidentifier/design-system
```

**Day 1-2: Tailwind Configuration**
- Replace existing Tailwind config
- Add Inter font
- Update global styles

**Day 3-4: Component Replacement**
- Replace Button components
- Replace Input components
- Replace Card components

**Day 5: Testing**
- Visual regression testing
- Functional testing
- Bug fixes

#### Week 7-8: FitPrismora Migration

**Day 1: Setup**
- Install design system package
- Update Tailwind config

**Day 2-3: Component Replacement**
- Replace Button components
- Replace Card components
- Replace Progress indicators

**Day 4: App-Specific Components**
- Migrate workout timer UI
- Migrate streak tracker

**Day 5: Testing**

#### Week 8-9: NutriPrismora Migration

**Day 1-2: Setup & Configuration**
- Install design system
- Update Tailwind config
- Add calorie ring component styles

**Day 3-4: Component Replacement**
- Replace forms
- Replace cards
- Migrate food logging UI

**Day 5: Testing**

#### Week 9-10: FloraPrismora Migration

**Day 1-2: Setup & Configuration**
- Install design system
- Update Tailwind config
- Add toxicity badge styles

**Day 3-4: Component Replacement**
- Replace cards
- Replace alerts (safety warnings)
- Migrate "My Garden" UI

**Day 5: Testing**

### 7.7 Phase 5: Medium-Priority Apps (Weeks 11-12)

| Week | Apps |
|------|------|
| 11 | VinylPrismora, RockPrismora, MusclePrismora |
| 12 | BirdPrismora, AquaPrismora, AutoPrismora |

Follow the same 5-day pattern per app group:
- Day 1: Setup
- Day 2-3: Component replacement
- Day 4: App-specific components
- Day 5: Testing

### 7.8 Phase 6: Low-Priority Apps (Weeks 13-14)

| Week | Apps |
|------|------|
| 13 | InsectPrismora, NotePrismora, CardPrismora, FruitPrismora |
| 14 | PawPrismora, MeowPrismora |

### 7.9 Phase 7: Polish & Launch (Weeks 15-16)

#### Week 15: Final Polish

**Monday-Wednesday: Cross-App Testing**
- Test SSO flow across all apps
- Test cross-app features
- Test navigation between apps

**Thursday-Friday: Performance**
- Bundle size optimization
- Code splitting
- Lazy loading

#### Week 16: Launch

**Monday-Tuesday: Documentation**
- Update all app READMEs
- Create migration guide for developers
- Record training videos

**Wednesday: Staged Rollout**
- Deploy to staging
- Final smoke testing

**Thursday: Production Launch**
- Deploy to production (25% traffic)
- Monitor metrics

**Friday: Full Rollout**
- Increase to 100% traffic
- Monitor and address issues

### 7.10 Daily Migration Checklist

For each app being migrated:

**Setup**
- [ ] Install `@photoidentifier/design-system` package
- [ ] Update `tailwind.config.js`
- [ ] Add Inter font to `index.html`
- [ ] Update global CSS

**Components**
- [ ] Replace Button components
- [ ] Replace Input components
- [ ] Replace Card components
- [ ] Replace Modal components
- [ ] Replace Alert components
- [ ] Replace Badge components
- [ ] Replace Navigation components

**Testing**
- [ ] Visual regression testing
- [ ] Functional testing
- [ ] Accessibility testing
- [ ] Browser compatibility testing
- [ ] Mobile responsive testing

**Cleanup**
- [ ] Remove old component files
- [ ] Remove unused CSS
- [ ] Update imports
- [ ] Update documentation

---

## 8. Testing Checklist

### 8.1 Visual Regression Testing

#### Tools Recommended

- **Percy** or **Chromatic** for screenshot testing
- **Storybook** for component isolation
- **Jest** + **Testing Library** for unit tests

#### Visual Testing Checklist

| Component | Test Cases | Screenshot Points |
|-----------|------------|-------------------|
| **Button** | All variants × all sizes | 30 combinations |
| **Input** | All states × all sizes | 18 combinations |
| **Card** | All variants | 5 variants |
| **Modal** | All sizes | 5 sizes |
| **Alert** | All variants | 4 variants |
| **Navigation** | Top nav, sidebar | 2 states each |
| **Badge** | All variants × sizes | 21 combinations |

### 8.2 Functional Testing Checklist

#### Button Component

```typescript
describe('Button', () => {
  it('renders with correct variant styles', () => {
    const variants = ['primary', 'secondary', 'ghost', 'danger', 'success', 'link'];
    variants.forEach(variant => {
      const { getByRole } = render(<Button variant={variant}>Click</Button>);
      const button = getByRole('button');
      expect(button).toHaveClass(`btn-${variant}`);
    });
  });

  it('calls onClick handler when clicked', () => {
    const handleClick = jest.fn();
    const { getByRole } = render(<Button onClick={handleClick}>Click</Button>);
    fireEvent.click(getByRole('button'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it('does not call onClick when disabled', () => {
    const handleClick = jest.fn();
    const { getByRole } = render(<Button onClick={handleClick} disabled>Click</Button>);
    fireEvent.click(getByRole('button'));
    expect(handleClick).not.toHaveBeenCalled();
  });

  it('shows loading state when loading prop is true', () => {
    const { getByRole, getByTestId } = render(<Button loading>Loading</Button>);
    expect(getByTestId('spinner')).toBeInTheDocument();
    expect(getByRole('button')).toBeDisabled();
  });

  it('renders icon left and right correctly', () => {
    const { container } = render(
      <Button iconLeft={<span data-testid="left" />} iconRight={<span data-testid="right" />}>
        Button
      </Button>
    );
    expect(container.querySelector('[data-testid="left"]')).toBeInTheDocument();
    expect(container.querySelector('[data-testid="right"]')).toBeInTheDocument();
  });
});
```

#### Input Component

```typescript
describe('Input', () => {
  it('renders with correct label', () => {
    const { getByLabelText } = render(<Input label="Email" />);
    expect(getByLabelText('Email')).toBeInTheDocument();
  });

  it('displays error message when error prop is provided', () => {
    const { getByText } = render(<Input error="Email is required" />);
    expect(getByText('Email is required')).toBeInTheDocument();
  });

  it('applies error styles when state is "error"', () => {
    const { getByRole } = render(<Input state="error" />);
    expect(getByRole('textbox')).toHaveClass('border-error-500');
  });

  it('shows helper text when provided', () => {
    const { getByText } = render(<Input helperText="Enter your email address" />);
    expect(getByText('Enter your email address')).toBeInTheDocument();
  });
});
```

### 8.3 Accessibility Testing

#### WCAG 2.1 AA Compliance Checklist

**Keyboard Navigation**
- [ ] All interactive elements are keyboard accessible
- [ ] Tab order follows visual layout
- [ ] No keyboard traps
- [ ] Visible focus indicators on all interactive elements
- [ ] Skip navigation link available

**Screen Reader Support**
- [ ] All images have alt text
- [ ] Form inputs have associated labels
- [ ] Error messages are announced
- [ ] ARIA labels on icon-only buttons
- [ ] Semantic HTML used throughout

**Color Contrast**
- [ ] Normal text: Minimum 4.5:1 contrast ratio
- [ ] Large text (18px+): Minimum 3:1 contrast ratio
- [   ] UI components: Minimum 3:1 contrast ratio
- [ ] Focus indicators: Minimum 3:1 contrast ratio

**Forms**
- [ ] Required fields indicated
- [ ] Error messages clearly associated with inputs
- [ ] Instructions provided before inputs
- [ ] Clear validation feedback

#### Automated Accessibility Testing

```bash
# Install axe-core
npm install --save-dev @axe-core/react

# Run accessibility tests
npm run test:a11y
```

```typescript
// Example accessibility test
import { axe, toHaveNoViolations } from 'jest-axe';

expect.extend(toHaveNoViolations);

describe('Accessibility', () => {
  it('should not have accessibility violations', async () => {
    const { container } = render(<App />);
    const results = await axe(container);
    expect(results).toHaveNoViolations();
  });
});
```

### 8.4 Cross-Browser Testing

#### Browser Support Matrix

| Browser | Minimum Version | Testing Priority |
|---------|-----------------|------------------|
| Chrome | 110+ | Required |
| Safari | 16+ | Required |
| Firefox | 115+ | Required |
| Edge | 110+ | Required |
| Samsung Internet | 21+ | Important |
| Opera | 96+ | Nice to have |

#### Mobile Browser Testing

| Platform | Browser | Testing Priority |
|----------|---------|------------------|
| iOS | Safari 16+ | Required |
| iOS | Chrome 110+ | Important |
| Android | Chrome 110+ | Required |
| Android | Firefox 115+ | Important |

### 8.5 Responsive Design Testing

#### Breakpoints to Test

| Breakpoint | Width | Devices |
|------------|-------|---------|
| `xs` | 375px | iPhone SE, small phones |
| `sm` | 640px | Large phones, small tablets |
| `md` | 768px | Tablets portrait |
| `lg` | 1024px | Tablets landscape, small laptops |
| `xl` | 1280px | Desktops |
| `2xl` | 1536px | Large desktops |

#### Testing Checklist

- [ ] All components render correctly at all breakpoints
- [ ] Navigation works on mobile (hamburger menu)
- [ ] Touch targets minimum 44x44px on mobile
- [ ] Text is readable without zooming
- [ ] Horizontal scrolling is avoided
- [ ] Images scale appropriately

### 8.6 Dark Mode Testing

```typescript
describe('Dark Mode', () => {
  beforeEach(() => {
    document.documentElement.classList.add('dark');
  });

  afterEach(() => {
    document.documentElement.classList.remove('dark');
  });

  it('applies dark mode styles correctly', () => {
    const { container } = render(<Button variant="primary">Test</Button>);
    expect(container.querySelector('button')).toHaveClass('dark:bg-primary-500');
  });

  it('maintains contrast ratios in dark mode', async () => {
    const { container } = render(<App />);
    const results = await axe(container);
    expect(results).toHaveNoViolations();
  });
});
```

### 8.7 Performance Testing

#### Performance Budgets

| Metric | Budget | Measurement |
|--------|--------|-------------|
| First Contentful Paint | < 1.5s | Lighthouse |
| Largest Contentful Paint | < 2.5s | Lighthouse |
| Cumulative Layout Shift | < 0.1 | Lighthouse |
| First Input Delay | < 100ms | Lighthouse |
| Time to Interactive | < 3.5s | Lighthouse |
| Bundle Size | < 200KB | webpack-bundle-analyzer |

#### Performance Testing Commands

```bash
# Run Lighthouse CI
npm run lighthouse

# Analyze bundle size
npm run analyze:bundle

# Run performance tests
npm run test:performance
```

---

## 9. Rollback Procedures

### 9.1 Rollback Triggers

Rollback should be considered if any of the following occur:

| Trigger | Threshold | Action |
|---------|-----------|--------|
| Error rate increase | > 2x baseline | Immediate rollback |
| Page load time increase | > 50% | Evaluate, rollback if needed |
| User complaints | > 10 per hour | Evaluate, rollback if needed |
| Critical functionality broken | Any | Immediate rollback |
| Accessibility violations | WCAG AA fail | Fix within 24h or rollback |
| Visual regression score | < 90% match | Evaluate, rollback if needed |

### 9.2 Pre-Migration Backup Checklist

Before migrating any application:

```bash
# Create migration branch
git checkout -b migration/design-system-<app-name>

# Tag pre-migration state
git tag pre-migration-<app-name>-<date>

# Create backup of current styles
cp -R src/styles src/styles.backup

# Export current component library
npm run build:backup
```

### 9.3 Automated Rollback Script

```bash
#!/bin/bash
# rollback-migration.sh <app-name>

APP_NAME=$1
BACKUP_TAG="pre-migration-${APP_NAME}-$(date +%Y%m%d)"

echo "Rolling back ${APP_NAME} to ${BACKUP_TAG}"

# Reset to backup tag
git checkout tags/${BACKUP_TAG}

# Remove design system package
npm uninstall @photoidentifier/design-system

# Restore backup styles
if [ -d "src/styles.backup" ]; then
  rm -rf src/styles
  mv src/styles.backup src/styles
fi

# Reinstall original dependencies
rm -rf node_modules package-lock.json
npm install

# Rebuild
npm run build

echo "Rollback complete. Review changes before committing."
```

### 9.4 Manual Rollback Steps

1. **Stop the deployment** (if in progress)
2. **Revert the migration commit**
```bash
git revert <migration-commit-hash>
```

3. **Restore previous dependencies**
```bash
git checkout HEAD~1 -- package.json package-lock.json
npm install
```

4. **Restore previous styles**
```bash
git checkout HEAD~1 -- src/styles/
```

5. **Rebuild and test**
```bash
npm run build
npm run test
```

6. **Deploy rollback**
```bash
npm run deploy:rollback
```

7. **Verify production**
```bash
# Run smoke tests
npm run test:smoke:prod

# Check error rates
# Check user feedback
# Monitor for 1 hour
```

### 9.5 Feature Flags for Gradual Rollout

Implement feature flags to enable gradual migration:

```typescript
// src/config/featureFlags.ts
export const featureFlags = {
  useUnifiedDesignSystem: process.env.NEXT_PUBLIC_USE_UNIFIED_DESIGN === 'true',
  useUnifiedButtons: process.env.NEXT_PUBLIC_USE_UNIFIED_BUTTONS === 'true',
  useUnifiedInputs: process.env.NEXT_PUBLIC_USE_UNIFIED_INPUTS === 'true',
};

// Usage in components
import { featureFlags } from '@/config/featureFlags';

const MyComponent = () => {
  if (featureFlags.useUnifiedDesignSystem) {
    return <UnifiedButton>Click</UnifiedButton>;
  }
  return <LegacyButton>Click</LegacyButton>;
};
```

### 9.6 A/B Testing Strategy

Run old and new versions in parallel:

| Metric | Control | Variant | Success Criteria |
|--------|---------|---------|------------------|
| Conversion rate | Baseline | >= Baseline | No significant decrease |
| Page load time | Baseline | <= 1.1x Baseline | Within 10% |
| Error rate | Baseline | <= 1.2x Baseline | Within 20% |
| User satisfaction | Baseline | >= Baseline | No significant decrease |

### 9.7 Post-Rollback Analysis

If rollback occurs, document:

1. **Root Cause Analysis**
   - What went wrong?
   - Why wasn't it caught in testing?
   - What could have been done differently?

2. **Impact Assessment**
   - Number of users affected
   - Duration of issue
   - Business impact

3. **Prevention Measures**
   - Update testing checklist
   - Add new test cases
   - Improve monitoring

---

## 10. Appendices

### 10.1 Quick Reference Card Migration

```tsx
// BEFORE
<div class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600">
  Submit
</div>

// AFTER
<Button variant="primary" size="md">
  Submit
</Button>
```

### 10.2 Common Migration Patterns

#### Color Replacement Map

| Find | Replace With |
|------|--------------|
| `bg-blue-` | `bg-primary-` |
| `bg-green-` | `bg-success-` |
| `bg-yellow-` | `bg-warning-` |
| `bg-red-` | `bg-error-` |
| `text-gray-` | `text-gray-` (unchanged) |
| `border-blue-` | `border-primary-` |

#### Font Replacement Map

| Find | Replace With |
|------|--------------|
| `font-roboto` | `font-sans` |
| `font-open-sans` | `font-sans` |
| `font-sf-pro` | `font-sans` |
| `font-lato` | `font-sans` |
| `font-montserrat` | `font-sans` |

#### Spacing Replacement Map

| Find | Replace With |
|------|--------------|
| `p-3` (12px) | `p-3` (unchanged) |
| `p-5` (20px) | `p-5` (unchanged) |
| Custom px values | Use spacing scale |

### 10.3 Design System Package Installation

```bash
# For each application
cd apps/<app-name>

# Install the design system
npm install @photoidentifier/design-system

# Or if using yarn
yarn add @photoidentifier/design-system

# Or if using pnpm
pnpm add @photoidentifier/design-system
```

### 10.4 Import Examples

```typescript
// Import components
import { Button, Input, Card, Modal } from '@photoidentifier/design-system';

// Import tokens
import { colors, spacing, typography } from '@photoidentifier/design-system/tokens';

// Import styles
import '@photoidentifier/design-system/styles';

// Import specific component categories
import { Button } from '@photoidentifier/design-system/components/buttons';
import { Input } from '@photoidentifier/design-system/components/forms';
import { Card } from '@photoidentifier/design-system/components/cards';
```

### 10.5 Tailwind Plugin Integration

```javascript
// tailwind.config.js
const { fontFamily, colors } = require('@photoidentifier/design-system/tokens');

module.exports = {
  theme: {
    extend: {
      fontFamily,
      colors,
    },
  },
  presets: [
    require('@photoidentifier/design-system/tailwind-preset'),
  ],
};
```

### 10.6 Contact & Support

| Role | Name | Contact |
|------|------|---------|
| Design System Lead | [Name] | design-system@photoidentifier.ai |
| Engineering Lead | [Name] | eng-lead@photoidentifier.ai |
| Migration Coordinator | [Name] | migration@photoidentifier.ai |

### 10.7 Additional Resources

**Internal Documentation**
- Component Storybook: https://storybook.photoidentifier.ai
- Design Tokens API: https://tokens.photoidentifier.ai
- Figma Design System: https://figma.com/file/photoidentifier-design-system

**External References**
- Tailwind CSS Documentation: https://tailwindcss.com/docs
- WCAG 2.1 Guidelines: https://www.w3.org/WAI/WCAG21/quickref/
- Inter Font: https://rsms.me/inter/

---

## Document Control

| Field | Information |
|-------|-------------|
| **Document Title** | PhotoIdentifier Unified Design System Migration Guide |
| **Version** | 1.0.0 |
| **Status** | Implementation Ready |
| **Author** | PhotoIdentifier Platform Team |
| **Date Created** | 2026-02-21 |
| **Last Updated** | 2026-02-21 |
| **Reviewers** | Design Team, Engineering Team, Product Management |

---

**End of Document**
