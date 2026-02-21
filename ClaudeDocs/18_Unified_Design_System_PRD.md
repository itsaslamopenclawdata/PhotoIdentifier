# Unified Design System PRD
## Product Requirements Document

---

## 1. Document Control

| Field | Information |
|-------|-------------|
| **Document Title** | Unified Design System PRD |
| **Version** | 1.0.0 |
| **Last Updated** | 2026-02-21 |
| **Status** | Draft |
| **Project** | PhotoIdentifier Platform |
| **Stakeholders** | Design Team, Development Team, Product Management |
| **Related Documents** | 01_Platform_Overview_PRD.md, 02_Technical_Architecture_PRD.md |

### Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0.0 | 2026-02-21 | System | Initial unified design system specification |

---

## 2. Executive Summary

### 2.1 Purpose

This document defines the Unified Design System for the PhotoIdentifier platform - a comprehensive set of design standards, reusable components, and implementation guidelines that ensure visual and functional consistency across all 17 applications in the platform.

### 2.2 Scope

This design system applies to:
- **Web Applications**: 11 React/Next.js applications
- **Desktop Applications**: 1 Electron app
- **Mobile Applications**: 3 React Native apps
- **Backend Services**: 2 API services (admin dashboards)

### 2.3 Business Value

- **Reduced Development Time**: Reusable components reduce duplicate code by 60%
- **Consistent User Experience**: Unified interface patterns across all applications
- **Faster Onboarding**: New developers can work with familiar patterns
- **Easier Maintenance**: Centralized design tokens simplify global updates
- **Accessibility Compliance**: Built-in WCAG 2.1 AA compliance

### 2.4 Target Applications

1. PhotoIdentifier (Main App)
2. PhotoIdentifier-Pro
3. PhotoIdentifier-Admin
4. PhotoIdentifier-API
5. PhotoIdentifier-Batch
6. PhotoIdentifier-Mobile
7. PhotoIdentifier-Cloud
8. PhotoIdentifier-Templates
9. PhotoIdentifier-Reports
10. PhotoIdentifier-Archive
11. PhotoIdentifier-Plugin
12. PhotoIdentifier-Integrations
13. PhotoIdentifier-Desktop
14. PhotoIdentifier-Mobile-Admin
15. PhotoIdentifier-API-Pro
16. PhotoIdentifier-Batch-Pro
17. PhotoIdentifier-Cloud-Pro

---

## 3. Design Philosophy

### 3.1 Core Principles

| Principle | Description |
|-----------|-------------|
| **Clarity** | Design should be self-evident. Users should never question what an element does or how to interact with it. |
| **Consistency** | Visual and interaction patterns remain uniform across all applications and contexts. |
| **Efficiency** | Design reduces friction and enables users to accomplish tasks with minimal effort. |
| **Accessibility** | All interfaces are perceivable, operable, understandable, and robust for all users. |
| **Responsiveness** | Design adapts gracefully across devices, screen sizes, and input methods. |
| **Modularity** | Components are independent, reusable, and composable. |

### 3.2 Design Language

Our design language is:

- **Modern**: Contemporary aesthetics with current design trends
- **Clean**: Minimal distractions with focus on content
- **Professional**: Suitable for enterprise and consumer contexts
- **Approachable**: Friendly and unintimidating for users of all skill levels
- **Purposeful**: Every design decision serves a functional purpose

---

## 4. Design Tokens

Design tokens are the visual atoms of the design system - the named entities that store visual design attributes. These tokens are used in place of hard-coded values to maintain consistency and enable systematic updates.

### 4.1 Typography System

#### Font Family

| Token | Value | Usage |
|-------|-------|-------|
| `font-family-base` | `'Inter', system-ui, -apple-system, sans-serif` | All UI text |
| `font-family-mono` | `'JetBrains Mono', 'Fira Code', monospace` | Code, data values |

#### Font Weights

| Token | Value | CSS Value | Usage |
|-------|-------|-----------|-------|
| `font-weight-light` | 300 | 300 | Secondary text, labels |
| `font-weight-normal` | 400 | 400 | Body text, default |
| `font-weight-medium` | 500 | 500 | Emphasized text, labels |
| `font-weight-semibold` | 600 | 600 | Headings, important labels |
| `font-weight-bold` | 700 | 700 | Primary headings |
| `font-weight-extrabold` | 800 | 800 | Display text |

#### Font Sizes

| Token | Value | rem | px | Usage |
|-------|-------|-----|----|-------|
| `font-size-xs` | 12px | 0.75rem | 12 | Captions, fine print |
| `font-size-sm` | 14px | 0.875rem | 14 | Secondary text, helper text |
| `font-size-base` | 16px | 1rem | 16 | Body text, default |
| `font-size-lg` | 18px | 1.125rem | 18 | Subheadings, emphasized text |
| `font-size-xl` | 20px | 1.25rem | 20 | Section headings |
| `font-size-2xl` | 24px | 1.5rem | 24 | Page headings |
| `font-size-3xl` | 30px | 1.875rem | 30 | Large headings |
| `font-size-4xl` | 36px | 2.25rem | 36 | Display headings |
| `font-size-5xl` | 48px | 3rem | 48 | Hero text |
| `font-size-6xl` | 60px | 3.75rem | 60 | Large display |

#### Line Heights

| Token | Value | Usage |
|-------|-------|-------|
| `line-height-tight` | 1.25 | Headings, compact text |
| `line-height-snug` | 1.375 | Subheadings |
| `line-height-normal` | 1.5 | Body text, default |
| `line-height-relaxed` | 1.625 | Long-form content |
| `line-height-loose` | 2 | Spaced text, data tables |

#### Letter Spacing

| Token | Value | Usage |
|-------|-------|-------|
| `letter-spacing-tighter` | -0.05em | Large headings |
| `letter-spacing-tight` | -0.025em | Medium headings |
| `letter-spacing-normal` | 0 | Body text, default |
| `letter-spacing-wide` | 0.025em | Labels, buttons |
| `letter-spacing-wider` | 0.05em | Small text, caps |

### 4.2 Color System

#### Primary Colors

| Token | Hex | RGB | HSL | Usage |
|-------|-----|-----|-----|-------|
| `color-primary-50` | #EEF2FF | rgb(238, 242, 255) | hsl(239, 100%, 97%) | Primary background light |
| `color-primary-100` | #E0E7FF | rgb(224, 231, 255) | hsl(239, 100%, 94%) | Primary background |
| `color-primary-200` | #C7D2FE | rgb(199, 210, 254) | hsl(239, 96%, 89%) | Primary border |
| `color-primary-300` | #A5B4FC | rgb(165, 180, 252) | hsl(239, 96%, 82%) | Primary hover |
| `color-primary-400` | #818CF8 | rgb(129, 140, 248) | hsl(239, 89%, 74%) | Primary active |
| `color-primary-500` | #6366F1 | rgb(99, 102, 241) | hsl(239, 78%, 67%) | Primary default |
| `color-primary-600` | #4F46E5 | rgb(79, 70, 229) | hsl(239, 76%, 59%) | Primary pressed |
| `color-primary-700` | #4338CA | rgb(67, 56, 202) | hsl(239, 72%, 51%) | Primary dark |
| `color-primary-800` | #3730A3 | rgb(55, 48, 163) | hsl(243, 54%, 41%) | Primary darker |
| `color-primary-900` | #312E81 | rgb(49, 46, 129) | hsl(243, 47%, 34%) | Primary darkest |

#### Secondary Colors (Violet)

| Token | Hex | RGB | HSL |
|-------|-----|-----|-----|
| `color-secondary-50` | #F5F3FF | rgb(245, 243, 255) |
| `color-secondary-100` | #EDE9FE | rgb(237, 233, 254) |
| `color-secondary-200` | #DDD6FE | rgb(221, 214, 254) |
| `color-secondary-300` | #C4B5FD | rgb(196, 181, 253) |
| `color-secondary-400` | #A78BFA | rgb(167, 139, 250) |
| `color-secondary-500` | #8B5CF6 | rgb(139, 92, 246) |
| `color-secondary-600` | #7C3AED | rgb(124, 58, 237) |
| `color-secondary-700` | #6D28D9 | rgb(109, 40, 217) |
| `color-secondary-800` | #5B21B6 | rgb(91, 33, 182) |
| `color-secondary-900` | #4C1D95 | rgb(76, 29, 149) |

#### Semantic Colors

##### Success (Green)

| Token | Hex | Usage |
|-------|-----|-------|
| `color-success-50` | #ECFDF5 | Success background light |
| `color-success-100` | #D1FAE5 | Success background |
| `color-success-200` | #A7F3D0 | Success border |
| `color-success-300` | #6EE7B7 | Success hover |
| `color-success-400` | #34D399 | Success active |
| `color-success-500` | #10B981 | Success default |
| `color-success-600` | #059669 | Success pressed |
| `color-success-700` | #047857 | Success dark |
| `color-success-800` | #065F46 | Success darker |
| `color-success-900` | #064E3B | Success darkest |

##### Warning (Amber)

| Token | Hex | Usage |
|-------|-----|-------|
| `color-warning-50` | #FFFBEB | Warning background light |
| `color-warning-100` | #FEF3C7 | Warning background |
| `color-warning-200` | #FDE68A | Warning border |
| `color-warning-300` | #FCD34D | Warning hover |
| `color-warning-400` | #FBBF24 | Warning active |
| `color-warning-500` | #F59E0B | Warning default |
| `color-warning-600` | #D97706 | Warning pressed |
| `color-warning-700` | #B45309 | Warning dark |
| `color-warning-800` | #92400E | Warning darker |
| `color-warning-900` | #78350F | Warning darkest |

##### Error (Red)

| Token | Hex | Usage |
|-------|-----|-------|
| `color-error-50` | #FEF2F2 | Error background light |
| `color-error-100` | #FEE2E2 | Error background |
| `color-error-200` | #FECACA | Error border |
| `color-error-300` | #FCA5A5 | Error hover |
| `color-error-400` | #F87171 | Error active |
| `color-error-500` | #EF4444 | Error default |
| `color-error-600` | #DC2626 | Error pressed |
| `color-error-700` | #B91C1C | Error dark |
| `color-error-800` | #991B1B | Error darker |
| `color-error-900` | #7F1D1D | Error darkest |

##### Info (Blue)

| Token | Hex | Usage |
|-------|-----|-------|
| `color-info-50` | #EFF6FF | Info background light |
| `color-info-100` | #DBEAFE | Info background |
| `color-info-200` | #BFDBFE | Info border |
| `color-info-300` | #93C5FD | Info hover |
| `color-info-400` | #60A5FA | Info active |
| `color-info-500` | #3B82F6 | Info default |
| `color-info-600` | #2563EB | Info pressed |
| `color-info-700` | #1D4ED8 | Info dark |
| `color-info-800` | #1E40AF | Info darker |
| `color-info-900` | #1E3A8A | Info darkest |

#### Neutral Palette (Gray)

| Token | Hex | Usage |
|-------|-----|-------|
| `color-neutral-50` | #F9FAFB | Background lightest |
| `color-neutral-100` | #F3F4F6 | Background lighter |
| `color-neutral-200` | #E5E7EB | Border light |
| `color-neutral-300` | #D1D5DB | Border default |
| `color-neutral-400` | #9CA3AF | Text muted |
| `color-neutral-500` | #6B7280 | Text secondary |
| `color-neutral-600` | #4B5563 | Text primary |
| `color-neutral-700` | #374151 | Text dark |
| `color-neutral-800` | #1F2937 | Text darker |
| `color-neutral-900` | #111827 | Text darkest |

#### Semantic Color Mapping

| Intent | Light Mode | Dark Mode |
|--------|------------|-----------|
| Background | `#FFFFFF` | `#111827` |
| Background Alt | `#F9FAFB` | `#1F2937` |
| Background Elevated | `#FFFFFF` | `#1F2937` |
| Border | `#E5E7EB` | `#374151` |
| Border Strong | `#D1D5DB` | `#4B5563` |
| Text Primary | `#111827` | `#F9FAFB` |
| Text Secondary | `#6B7280` | `#9CA3AF` |
| Text Tertiary | `#9CA3AF` | `#6B7280` |
| Text Inverse | `#FFFFFF` | `#111827` |
| Link | `#6366F1` | `#818CF8` |
| Link Hover | `#4F46E5` | `#6366F1` |

### 4.3 Spacing System

Base unit: 4px. All spacing values are multiples of this base.

| Token | Value | Usage Example |
|-------|-------|---------------|
| `spacing-0` | 0 | No spacing |
| `spacing-1` | 4px | Tight spacing between related elements |
| `spacing-2` | 8px | Default spacing for small components |
| `spacing-3` | 12px | Compact section spacing |
| `spacing-4` | 16px | Default section spacing |
| `spacing-5` | 20px | Medium spacing |
| `spacing-6` | 24px | Large section spacing |
| `spacing-8` | 32px | Component grouping |
| `spacing-10` | 40px | Section separation |
| `spacing-12` | 48px | Major section separation |
| `spacing-16` | 64px | Page level spacing |
| `spacing-20` | 80px | Hero/feature spacing |

#### Spacing Usage Guidelines

| Context | Spacing |
|---------|---------|
| Button padding (vertical) | 8px - 12px |
| Button padding (horizontal) | 16px - 24px |
| Card padding | 24px |
| Form field gap | 16px |
| List item gap | 8px - 12px |
| Section margin | 32px - 48px |
| Container padding (mobile) | 16px |
| Container padding (desktop) | 24px - 32px |

### 4.4 Border Radius System

| Token | Value | Usage |
|-------|-------|-------|
| `radius-none` | 0 | Containers, dividers |
| `radius-sm` | 4px | Small elements, pills, tags |
| `radius-md` | 8px | Default for buttons, inputs, cards |
| `radius-lg` | 12px | Large cards, modals |
| `radius-xl` | 16px | Hero cards, featured elements |
| `radius-2xl` | 24px | Special containers, tooltips |
| `radius-full` | 9999px | Circular elements, avatars |

#### Border Radius Guidelines

| Component | Radius |
|-----------|--------|
| Button | 8px |
| Input | 8px |
| Card | 8px - 12px |
| Modal | 12px - 16px |
| Dropdown | 8px |
| Tooltip | 8px |
| Badge | 9999px (pill) or 4px |
| Avatar | 9999px (circular) or 12px |
| Alert | 8px |
| Toast | 8px - 12px |

### 4.5 Shadow System

5-level shadow system for depth and hierarchy.

| Token | Value | Usage |
|-------|-------|-------|
| `shadow-xs` | `0 1px 2px 0 rgb(0 0 0 / 0.05)` | Subtle borders, dividers |
| `shadow-sm` | `0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)` | Cards, buttons hover |
| `shadow-md` | `0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)` | Dropdowns, popovers |
| `shadow-lg` | `0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)` | Modals, elevated cards |
| `shadow-xl` | `0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)` | Hero elements, tooltips |
| `shadow-2xl` | `0 25px 50px -12px rgb(0 0 0 / 0.25)` | Full-screen overlays |

#### Dark Mode Shadows

For dark mode, use lighter shadows with reduced opacity:

| Token | Dark Mode Value |
|-------|-----------------|
| `shadow-xs` | `0 1px 2px 0 rgb(0 0 0 / 0.3)` |
| `shadow-sm` | `0 1px 3px 0 rgb(0 0 0 / 0.4), 0 1px 2px -1px rgb(0 0 0 / 0.4)` |
| `shadow-md` | `0 4px 6px -1px rgb(0 0 0 / 0.4), 0 2px 4px -2px rgb(0 0 0 / 0.4)` |
| `shadow-lg` | `0 10px 15px -3px rgb(0 0 0 / 0.5), 0 4px 6px -4px rgb(0 0 0 / 0.5)` |
| `shadow-xl` | `0 20px 25px -5px rgb(0 0 0 / 0.5), 0 8px 10px -6px rgb(0 0 0 / 0.5)` |

### 4.6 Z-Index Scale

| Token | Value | Usage |
|-------|-------|-------|
| `z-base` | 0 | Default content |
| `z-above` | 10 | Sticky elements |
| `z-dropdown` | 100 | Dropdowns, popovers |
| `z-sticky` | 200 | Fixed headers |
| `z-overlay` | 300 | Backdrops |
| `z-modal` | 400 | Modals |
| `z-popover` | 500 | Tooltips, toasts |
| `z-maximum` | 9999 | Critical overlays |

---

## 5. Component Standards

### 5.1 Buttons

#### Button Variants

| Variant | Background | Text | Border | Usage |
|---------|------------|------|--------|-------|
| Primary | `#6366F1` | `#FFFFFF` | none | Primary actions, CTAs |
| Secondary | `#FFFFFF` | `#6366F1` | `#E5E7EB` | Alternative actions |
| Ghost | transparent | `#6366F1` | none | Secondary actions, inline |
| Danger | `#EF4444` | `#FFFFFF` | none | Destructive actions |
| Success | `#10B981` | `#FFFFFF` | none | Confirm actions |
| Link | transparent | `#6366F1` | none | Navigation, tertiary actions |

#### Button States

| State | Primary | Secondary | Ghost |
|-------|---------|-----------|-------|
| Default | `#6366F1` bg | White bg, indigo text | Transparent, indigo text |
| Hover | `#4F46E5` bg | Gray-50 bg, indigo-600 text | Indigo-50 bg, indigo-600 text |
| Active | `#4338CA` bg | Gray-100 bg, indigo-700 text | Indigo-100 bg, indigo-700 text |
| Disabled | Gray-300 bg, gray-500 text | Gray-100 bg, gray-400 text | Transparent, gray-400 text |
| Loading | Indigo-600 bg + spinner | Same as disabled | Same as disabled |

#### Button Sizes

| Size | Height | Padding | Font Size | Icon Size |
|------|--------|---------|-----------|-----------|
| xs | 28px | 4px 10px | 12px | 14px |
| sm | 32px | 6px 14px | 14px | 16px |
| md | 40px | 8px 16px | 14px | 18px |
| lg | 48px | 12px 20px | 16px | 20px |
| xl | 56px | 16px 24px | 18px | 22px |

#### Button with Icon

| Configuration | Spacing |
|---------------|---------|
| Icon left | gap: 8px |
| Icon right | gap: 8px |
| Icon only | padding: based on size (square) |

#### Button Border Radius

All buttons use `radius-md` (8px) by default.

### 5.2 Cards

#### Card Structure

```
┌─────────────────────────────────────┐
│ ┌─────────────────────────────────┐ │
│ │           Header (Optional)      │ │
│ │    Title, actions, menu          │ │
│ └─────────────────────────────────┘ │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │                                  │ │
│ │           Body                   │ │
│ │     Content, forms, lists        │ │
│ │                                  │ │ │
│ └─────────────────────────────────┘ │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │          Footer (Optional)       │ │
│ │     Actions, pagination          │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘
```

#### Card Variants

| Variant | Background | Border | Shadow | Usage |
|---------|------------|--------|--------|-------|
| Default | White | Gray-200 | sm | Standard content grouping |
| Elevated | White | none | md | Emphasized content |
| Bordered | White | Gray-300 | none | Form sections |
| Interactive | White | Indigo-200 (hover) | sm (hover) | Clickable cards |
| Filled | Gray-50 | none | none | Alternate sections |

#### Card Spacing

| Element | Value |
|---------|-------|
| Card padding | 24px |
| Header padding | 16px 24px (top only) |
| Footer padding | 16px 24px (bottom only) |
| Card gap | 16px |
| Header border | 1px solid #E5E7EB |

#### Card Border Radius

All cards use `radius-lg` (12px) by default.

#### Card Shadow

- Default: `shadow-sm`
- Hover: `shadow-md`
- Elevated: `shadow-lg`

### 5.3 Form Inputs

#### Input Types

- Text
- Email
- Password
- Number
- Tel
- URL
- Search
- Date
- Time
- DateTime
- Textarea
- Select
- Multi-select
- File upload
- Checkbox
- Radio
- Switch
- Slider

#### Input States

| State | Border | Background | Text | Shadow |
|-------|--------|------------|------|--------|
| Default | Gray-300 | White | Gray-900 | none |
| Focus | Indigo-500 | White | Gray-900 | 0 0 0 3px rgba(99, 102, 241, 0.1) |
| Hover | Gray-400 | White | Gray-900 | none |
| Error | Red-500 | White | Gray-900 | 0 0 0 3px rgba(239, 68, 68, 0.1) |
| Success | Green-500 | White | Gray-900 | 0 0 0 3px rgba(16, 185, 129, 0.1) |
| Disabled | Gray-200 | Gray-50 | Gray-400 | none |

#### Input Sizes

| Size | Height | Padding | Font Size |
|------|--------|---------|-----------|
| sm | 32px | 6px 12px | 14px |
| md | 40px | 8px 14px | 16px |
| lg | 48px | 12px 16px | 16px |

#### Input Spacing

| Element | Value |
|---------|-------|
| Label gap | 6px |
| Input gap (between inputs) | 16px |
| Helper text gap | 4px |
| Error message gap | 4px |

#### Input Border Radius

All inputs use `radius-md` (8px).

#### Input Labels

| Property | Value |
|----------|-------|
| Font weight | 500 (medium) |
| Font size | 14px |
| Color | Gray-700 |
| Required indicator | Red-500 asterisk |

#### Helper Text

| Property | Value |
|----------|-------|
| Font size | 12px |
| Color | Gray-500 |
| Margin top | 4px |

#### Error Messages

| Property | Value |
|----------|-------|
| Font size | 12px |
| Color | Red-600 |
| Margin top | 4px |
| Icon | Warning circle icon |

### 5.4 Modals

#### Modal Structure

```
┌────────────────────────────────────────┐
│              Backdrop                  │
│  ┌──────────────────────────────────┐ │
│  │  ┌────────────────────────────┐  │ │
│  │  │         Header             │  │ │
│  │  │  Title  ────   [Close]     │  │ │
│  │  └────────────────────────────┘  │ │
│  │                                  │ │
│  │  ┌────────────────────────────┐  │ │
│  │  │                            │  │ │
│  │  │          Body              │  │ │
│  │  │   Content, forms, etc      │  │ │
│  │  │                            │  │ │
│  │  └────────────────────────────┘  │ │
│  │                                  │ │
│  │  ┌────────────────────────────┐  │ │
│  │  │      Footer (Optional)     │  │ │
│  │  │   [Cancel]    [Confirm]    │  │ │
│  │  └────────────────────────────┘  │ │
│  └──────────────────────────────────┘ │
└────────────────────────────────────────┘
```

#### Modal Sizes

| Size | Width | Max Width |
|------|-------|-----------|
| sm | 90% | 400px |
| md | 90% | 544px |
| lg | 90% | 768px |
| xl | 90% | 1024px |
| full | 100% | 100% |

#### Modal Spacing

| Element | Value |
|---------|-------|
| Backdrop | rgba(0, 0, 0, 0.5) |
| Border radius | 12px |
| Header padding | 20px 24px |
| Body padding | 24px |
| Footer padding | 16px 24px |
| Gap (sections) | 24px |

#### Modal Shadow

`shadow-xl` (0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1))

#### Modal Close Button

| Property | Value |
|----------|-------|
| Size | 32px |
| Icon | X (close) |
| Color | Gray-400 |
| Hover color | Gray-600 |

### 5.5 Badges

#### Badge Variants

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

#### Badge Sizes

| Size | Height | Padding | Font Size |
|------|--------|---------|-----------|
| sm | 20px | 2px 8px | 11px |
| md | 24px | 4px 10px | 12px |
| lg | 28px | 6px 12px | 14px |

#### Badge Border Radius

| Shape | Radius |
|-------|--------|
| Pill (default) | 9999px |
| Rounded | 4px |

#### Badge with Icon

| Configuration | Spacing |
|---------------|---------|
| Icon left | gap: 4px |
| Icon right | gap: 4px |
| Dot indicator | 4px from left |

### 5.6 Navigation

#### Top Navigation

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

#### Sidebar Navigation

| Element | Width | Padding |
|---------|-------|---------|
| Sidebar (collapsed) | 72px | 12px |
| Sidebar (expanded) | 256px | 16px |
| Nav item height | 40px | 8px 12px |

#### Sidebar Item States

| State | Icon | Text | Background |
|-------|------|------|------------|
| Default | Gray-400 | Gray-600 | transparent |
| Hover | Gray-600 | Gray-900 | Gray-50 |
| Active | Indigo-500 | Indigo-600 | Indigo-50 |

#### Breadcrumbs

| Property | Value |
|----------|-------|
| Font size | 14px |
| Separator | "/" (Gray-400) |
| Link color | Gray-500 |
| Link hover | Gray-700 |
| Current | Gray-900 (font weight: 500) |

### 5.7 Alerts

#### Alert Variants

| Variant | Background | Border | Icon | Text |
|---------|------------|--------|------|------|
| Info | Blue-50 | Blue-200 | Blue-500 | Blue-700 |
| Success | Green-50 | Green-200 | Green-500 | Green-700 |
| Warning | Amber-50 | Amber-200 | Amber-500 | Amber-700 |
| Error | Red-50 | Red-200 | Red-500 | Red-700 |

#### Alert Sizes

| Size | Padding | Font Size |
|------|---------|-----------|
| sm | 12px 16px | 14px |
| md | 16px | 16px |

#### Alert Structure

```
┌────────────────────────────────────────────┐
│ [Icon]  Title (optional)     [Close]      │
│         Description text...                │
└────────────────────────────────────────────┘
```

#### Alert Border Radius

`radius-md` (8px)

#### Alert Dismissible

Close button top-right, 16px padding on all sides.

### 5.8 Tables

#### Table Structure

| Element | Style |
|---------|-------|
| Background | White |
| Border | 1px solid Gray-200 |
| Border radius | 8px (top only) |
| Header background | Gray-50 |
| Header border | 1px solid Gray-200 (bottom) |
| Row border | 1px solid Gray-200 (bottom) |
| Row hover background | Gray-50 |

#### Table Typography

| Element | Font Size | Font Weight | Color |
|---------|-----------|-------------|-------|
| Header | 12px | 600 (semi-bold) | Gray-500 (uppercase) |
| Body | 14px | 400 | Gray-900 |
| Secondary | 12px | 400 | Gray-500 |

#### Table Spacing

| Element | Value |
|---------|-------|
| Cell padding | 12px 16px |
| Cell gap | 16px |

#### Table States

| State | Background | Usage |
|-------|------------|-------|
| Default | White | Normal rows |
| Hover | Gray-50 | Interactive rows |
| Selected | Indigo-50 | Selected rows |
| Disabled | Gray-50 | Disabled rows |

### 5.9 Dropdowns

#### Dropdown Structure

```
┌────────────────────────────────┐
│ Trigger Button                 │
└────────────────────────────────┘
          ┌──────────────────┐
          │ ───────────────── │  Header (Optional)
          │ Option 1      ────│  Option
          │ Option 2      ✓  │  Option (selected)
          │ ───────────────── │  Divider
          │ Option 3          │  Option
          └──────────────────┘
```

#### Dropdown Styles

| Property | Value |
|----------|-------|
| Background | White |
| Border | 1px solid Gray-200 |
| Border radius | 8px |
| Shadow | md |
| Padding | 8px |
| Min width | 180px |

#### Dropdown Item States

| State | Background | Text |
|-------|------------|------|
| Default | transparent | Gray-700 |
| Hover | Gray-50 | Gray-900 |
| Active | Indigo-50 | Indigo-600 |
| Disabled | transparent | Gray-400 |

#### Dropdown Item Height

32px with 8px padding on left/right.

### 5.10 Tooltips

#### Tooltip Styles

| Property | Value |
|----------|-------|
| Background | Gray-900 |
| Text | White |
| Font size | 12px |
| Padding | 6px 10px |
| Border radius | 6px |
| Max width | 240px |
| Shadow | md |
| Arrow | 4px triangle |

#### Tooltip Positions

- Top (default)
- Bottom
- Left
- Right

#### Tooltip Z-Index

`z-popover` (500)

---

## 6. Tailwind CSS Configuration

### 6.1 Base Configuration

```javascript
// tailwind.config.js
module.exports = {
  content: [
    './src/**/*.{js,jsx,ts,tsx}',
    './components/**/*.{js,jsx,ts,tsx}',
  ],
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'system-ui', '-apple-system', 'sans-serif'],
        mono: ['JetBrains Mono', 'Fira Code', 'monospace'],
      },
      colors: {
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
    },
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/aspect-ratio'),
  ],
}
```

### 6.2 Dark Mode Configuration

```javascript
// tailwind.config.js - Dark Mode Extension
module.exports = {
  darkMode: 'class', // or 'media' for system preference
  theme: {
    extend: {
      colors: {
        dark: {
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
    },
  },
}
```

---

## 7. Accessibility Standards

### 7.1 WCAG 2.1 AA Compliance

Our design system meets WCAG 2.1 Level AA requirements:

#### Color Contrast Ratios

| Element | Minimum Contrast | Target Contrast |
|---------|------------------|-----------------|
| Normal text | 4.5:1 | 7:1 |
| Large text (18px+) | 3:1 | 4.5:1 |
| UI components | 3:1 | 3:1 |
| Graphical objects | 3:1 | 3:1 |

#### Verified Contrast Pairs

| Foreground | Background | Ratio | Pass (AA) |
|------------|------------|-------|-----------|
| #111827 (Gray-900) | #FFFFFF | 16.4:1 | Yes |
| #6366F1 (Primary) | #FFFFFF | 4.6:1 | Yes |
| #10B981 (Success) | #FFFFFF | 3.4:1 | Yes |
| #F59E0B (Warning) | #FFFFFF | 2.9:1 | No - use darker text |
| #EF4444 (Error) | #FFFFFF | 3.9:1 | Yes |
| #6B7280 (Gray-500) | #FFFFFF | 4.7:1 | Yes |
| #9CA3AF (Gray-400) | #FFFFFF | 2.9:1 | No - avoid for text |

### 7.2 Keyboard Navigation

#### Tab Order

- All interactive elements must be keyboard accessible
- Logical tab order follows visual layout
- No keyboard traps
- Visible focus indicators

#### Focus Styles

| Element | Focus Style |
|---------|-------------|
| Buttons | Indigo-500 outline, 2px offset |
| Inputs | Indigo-500 border, ring offset |
| Links | Indigo-500 outline, 2px offset |

```css
/* Focus indicator */
.focus-ring:focus {
  outline: 2px solid #6366F1;
  outline-offset: 2px;
}

/* For inputs with ring */
.focus-ring-input:focus {
  border-color: #6366F1;
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
}
```

#### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Next focusable element | Tab |
| Previous focusable element | Shift + Tab |
| Activate | Enter / Space |
| Escape | Escape |
| Submit form | Ctrl/Cmd + Enter |

### 7.3 Screen Reader Support

#### ARIA Attributes

| Component | Required ARIA |
|-----------|---------------|
| Modal | `role="dialog"`, `aria-modal="true"`, `aria-labelledby` |
| Dropdown | `role="menu"`, `aria-expanded` |
| Alert | `role="alert"`, `aria-live` |
| Tabs | `role="tablist"`, `role="tab"`, `aria-selected` |
| Form inputs | `aria-label`, `aria-describedby`, `aria-invalid` |
| Loading states | `aria-busy="true"`, `aria-live="polite"` |

#### Semantic HTML

- Use proper heading hierarchy (h1-h6)
- Use landmark elements (header, nav, main, footer, aside)
- Use list elements for lists (ul, ol, li)
- Use button for actions, a for navigation

### 7.4 Text Scaling

Support text scaling up to 200% without loss of content or functionality:

- Use relative units (rem, em, %)
- Avoid fixed heights for text containers
- Ensure containers expand with content
- Test at 200% browser zoom

### 7.5 Motion & Animation

#### Reduced Motion Preference

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

#### Animation Guidelines

- Avoid auto-playing animations
- Provide pause controls for animations > 5 seconds
- No flashing content (more than 3 times per second)
- Keep animations purposeful and subtle

### 7.6 Form Accessibility

| Requirement | Implementation |
|-------------|----------------|
| Labels | All inputs have visible or aria labels |
| Required fields | Indicated with asterisk and aria-required |
| Error messages | Associated with aria-describedby |
| Instructions | Clear, visible before the input |
| Validation | Clear, specific error messages |

---

## 8. Component Library Specifications

### 8.1 Component Architecture

```
@photoidentifier/design-system
├── src
│   ├── components
│   │   ├── buttons
│   │   │   ├── Button.tsx
│   │   │   ├── ButtonGroup.tsx
│   │   │   └── IconButton.tsx
│   │   ├── forms
│   │   │   ├── Input.tsx
│   │   │   ├── Select.tsx
│   │   │   ├── Checkbox.tsx
│   │   │   ├── Radio.tsx
│   │   │   ├── Switch.tsx
│   │   │   ├── Textarea.tsx
│   │   │   └── FormField.tsx
│   │   ├── cards
│   │   │   ├── Card.tsx
│   │   │   ├── CardHeader.tsx
│   │   │   ├── CardBody.tsx
│   │   │   └── CardFooter.tsx
│   │   ├── navigation
│   │   │   ├── Navbar.tsx
│   │   │   ├── Sidebar.tsx
│   │   │   ├── Breadcrumbs.tsx
│   │   │   └── Pagination.tsx
│   │   ├── feedback
│   │   │   ├── Alert.tsx
│   │   │   ├── Toast.tsx
│   │   │   ├── Progress.tsx
│   │   │   └── Spinner.tsx
│   │   ├── overlays
│   │   │   ├── Modal.tsx
│   │   │   ├── Tooltip.tsx
│   │   │   └── Dropdown.tsx
│   │   ├── data-display
│   │   │   ├── Table.tsx
│   │   │   ├── Badge.tsx
│   │   │   ├── Tag.tsx
│   │   │   └── Avatar.tsx
│   │   └── layout
│   │       ├── Container.tsx
│   │       ├── Grid.tsx
│   │       └── Stack.tsx
│   ├── tokens
│   │   ├── colors.ts
│   │   ├── typography.ts
│   │   ├── spacing.ts
│   │   ├── borderRadius.ts
│   │   └── shadows.ts
│   ├── hooks
│   │   ├── useTheme.ts
│   │   ├── useBreakpoint.ts
│   │   └── useFocusTrap.ts
│   └── utils
│       ├── cn.ts
│       └── accessibility.ts
├── stories
│   └── *.stories.tsx
└── index.ts
```

### 8.2 Component Props Standards

All components follow these prop conventions:

```typescript
interface ComponentProps {
  // Visual
  variant?: 'primary' | 'secondary' | 'ghost';
  size?: 'sm' | 'md' | 'lg';
  color?: 'primary' | 'success' | 'warning' | 'error';

  // Behavior
  disabled?: boolean;
  loading?: boolean;
  required?: boolean;

  // Layout
  fullWidth?: boolean;
  className?: string;

  // Events
  onClick?: () => void;
  onFocus?: () => void;
  onBlur?: () => void;

  // Children
  children?: React.ReactNode;

  // Accessibility
  ariaLabel?: string;
  id?: string;
}
```

### 8.3 Component Naming Convention

| Type | Convention | Example |
|------|------------|---------|
| Components | PascalCase | `Button.tsx` |
| Props interfaces | PascalCase + Props | `ButtonProps` |
| Hooks | camelCase with 'use' prefix | `useTheme` |
| Utilities | camelCase | `formatDate` |
| Constants | SCREAMING_SNAKE_CASE | `MAX_FILE_SIZE` |
| CSS Modules | camelCase | `.buttonContainer` |

---

## 9. Migration Guidelines

### 9.1 General Migration Strategy

1. **Audit existing components** - Document current styling approach
2. **Install design system** - Add as dependency
3. **Configure Tailwind** - Update configuration
4. **Migrate incrementally** - Component by component
5. **Test thoroughly** - Visual and functional testing
6. **Remove old styles** - Clean up deprecated code

### 9.2 Application-Specific Guidelines

#### 9.2.1 PhotoIdentifier (Main App)

**Current State**: React with custom CSS modules

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Update `tailwind.config.js` with unified tokens
3. Replace Button components with design system Button
4. Replace Input components with design system Input
5. Update Card components to use design system styles
6. Migrate navigation to design system Navbar/Sidebar

**Priority**: High - Reference implementation

---

#### 9.2.2 PhotoIdentifier-Pro

**Current State**: React with styled-components

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Add Tailwind CSS to build process
3. Create styled-components wrapper for design tokens
4. Migrate Pro-specific components (license validation, premium features)
5. Update theme provider to use unified colors

**Priority**: High

---

#### 9.2.3 PhotoIdentifier-Admin

**Current State**: Next.js with custom CSS

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Configure Tailwind for Next.js
3. Migrate admin dashboard components
4. Update data tables to use design system Table
5. Migrate forms (user management, settings)

**Priority**: High

---

#### 9.2.4 PhotoIdentifier-API

**Current State**: Express with admin UI

**Migration Steps**:
1. Build admin UI with React + design system
2. Replace custom admin interface
3. Use design system for API documentation UI
4. Migrate authentication screens

**Priority**: Medium

---

#### 9.2.5 PhotoIdentifier-Batch

**Current State**: React with inline styles

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Migrate batch processing UI components
3. Update progress indicators to design system Progress
4. Replace file upload components

**Priority**: Medium

---

#### 9.2.6 PhotoIdentifier-Mobile

**Current State**: React Native with custom styles

**Migration Steps**:
1. Create React Native version of design system
2. Map web tokens to React Native equivalents
3. Migrate mobile-specific components
4. Adapt touch targets (minimum 44px)

**Priority**: High

---

#### 9.2.7 PhotoIdentifier-Cloud

**Current State**: Next.js with Tailwind (custom config)

**Migration Steps**:
1. Replace custom Tailwind config with unified config
2. Update cloud storage UI components
3. Migrate file browser component
4. Update upload/progress components

**Priority**: Medium

---

#### 9.2.8 PhotoIdentifier-Templates

**Current State**: React with CSS modules

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Migrate template gallery components
3. Update template preview cards
4. Replace template editor UI components

**Priority**: Low

---

#### 9.2.9 PhotoIdentifier-Reports

**Current State**: React with custom chart library styles

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Migrate report generation UI
3. Update chart components to use design system colors
4. Replace data export components

**Priority**: Low

---

#### 9.2.10 PhotoIdentifier-Archive

**Current State**: React with custom styles

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Migrate archive browser components
3. Update search/filter UI
4. Replace archive management components

**Priority**: Low

---

#### 9.2.11 PhotoIdentifier-Plugin

**Current State**: Vanilla JS (plugin framework)

**Migration Steps**:
1. Create CSS bundle from design tokens
2. Provide plugin-compatible components
3. Document plugin styling guidelines
4. Create plugin development kit

**Priority**: Low

---

#### 9.2.12 PhotoIdentifier-Integrations

**Current State**: React with custom UI

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Migrate integration setup UI
3. Update API key management components
4. Replace integration status displays

**Priority**: Medium

---

#### 9.2.13 PhotoIdentifier-Desktop

**Current State**: Electron with React

**Migration Steps**:
1. Install `@photoidentifier/design-system`
2. Configure for Electron environment
3. Migrate desktop-specific UI (menu bar, window controls)
4. Adapt native OS integration components

**Priority**: Medium

---

#### 9.2.14 PhotoIdentifier-Mobile-Admin

**Current State**: React Native

**Migration Steps**:
1. Use React Native design system (from 9.2.6)
2. Migrate admin-specific mobile components
3. Adapt data tables for mobile

**Priority**: Low

---

#### 9.2.15 PhotoIdentifier-API-Pro

**Current State**: Express with admin UI

**Migration Steps**:
1. Follow same approach as PhotoIdentifier-API
2. Add Pro-specific styling (license management)
3. Use design system for enhanced admin features

**Priority**: Low

---

#### 9.2.16 PhotoIdentifier-Batch-Pro

**Current State**: React with inline styles

**Migration Steps**:
1. Follow same approach as PhotoIdentifier-Batch
2. Add Pro-specific components (priority queues, advanced options)

**Priority**: Low

---

#### 9.2.17 PhotoIdentifier-Cloud-Pro

**Current State**: Next.js with Tailwind

**Migration Steps**:
1. Follow same approach as PhotoIdentifier-Cloud
2. Add Pro-specific cloud features UI
3. Update storage management components

**Priority**: Medium

---

### 9.3 Migration Checklist

For each application:

- [ ] Install `@photoidentifier/design-system` package
- [ ] Update Tailwind CSS configuration
- [ ] Add Inter font to project
- [ ] Replace button components
- [ ] Replace form input components
- [ ] Replace card components
- [ ] Replace modal components
- [ ] Replace navigation components
- [ ] Update color usage to design tokens
- [ ] Update typography to design tokens
- [ ] Update spacing to design tokens
- [ ] Test all components for accessibility
- [ ] Test dark mode (if applicable)
- [ ] Remove deprecated styles
- [ ] Update documentation

### 9.4 Breaking Changes to Communicate

| Change | Impact | Mitigation |
|--------|--------|------------|
| Primary color change | All brand-colored elements | Global find/replace with new tokens |
| Font family change | All text elements | Update font imports and config |
| Border radius changes | Component shapes | Component-level updates |
| Shadow system changes | Elevation depth | Component-level updates |
| Spacing scale | Layout gaps | May require layout adjustments |

---

## 10. Implementation Timeline

### Phase 1: Foundation (Weeks 1-2)

- Create design system package structure
- Define and document all design tokens
- Create Tailwind configuration
- Set up component library foundation
- Create Storybook/preview environment

### Phase 2: Core Components (Weeks 3-4)

- Implement Button component and variants
- Implement Input components (all types)
- Implement Card components
- Implement Modal component
- Implement Badge component
- Write component documentation

### Phase 3: Navigation & Layout (Weeks 5-6)

- Implement Navigation components
- Implement Table component
- Implement Alert/Toast components
- Implement Dropdown component
- Implement Tooltip component

### Phase 4: Migration - Priority Apps (Weeks 7-10)

- Migrate PhotoIdentifier (Main App)
- Migrate PhotoIdentifier-Pro
- Migrate PhotoIdentifier-Admin
- Migrate PhotoIdentifier-Mobile

### Phase 5: Migration - Remaining Apps (Weeks 11-14)

- Migrate PhotoIdentifier-Cloud
- Migrate PhotoIdentifier-Batch
- Migrate PhotoIdentifier-Integrations
- Migrate PhotoIdentifier-Desktop
- Migrate remaining applications

### Phase 6: Polish & Launch (Weeks 15-16)

- Complete accessibility audit
- Performance optimization
- Final documentation
- Developer training materials
- Launch design system v1.0

---

## 11. Success Metrics

### 11.1 Adoption Metrics

- Design system installed in: 17/17 applications
- Component usage: >80% of UI elements using system components
- Developer satisfaction: >4/5 in surveys

### 11.2 Quality Metrics

- Accessibility compliance: 100% WCAG 2.1 AA
- Design consistency: Visual consistency score >90%
- Code duplication: >60% reduction in styling code

### 11.3 Efficiency Metrics

- Component development time: >50% reduction
- Design review time: >40% reduction
- Onboarding time: New developers productive in <1 week

---

## 12. Maintenance & Governance

### 12.1 Versioning

Design system follows Semantic Versioning:

- **Major**: Breaking changes to components or tokens
- **Minor**: New components or features
- **Patch**: Bug fixes, documentation updates

### 12.2 Release Process

1. Create feature branch
2. Implement changes with tests
3. Update documentation
4. Create PR with design review
5. Merge to main
6. Tag release
7. Publish to npm/private registry
8. Communicate changes to teams

### 12.3 Contribution Guidelines

1. Check existing issues/PRs
2. Create issue for proposal
3. Design review with team
4. Implementation with tests
5. Documentation update
6. PR for review
7. Approval required: Design lead + Tech lead

### 12.4 Design System Team

| Role | Responsibilities |
|------|------------------|
| Design Lead | Token management, component design, design reviews |
| Tech Lead | Architecture, code quality, technical reviews |
| Component Developer | Component implementation, testing |
| Documentation | Documentation maintenance, examples |

---

## 13. Appendix

### 13.1 Color Palette Reference

#### Full Color Swatches

```
PRIMARY (Indigo)
50  #EEF2FF  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #E0E7FF  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #C7D2FE  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #A5B4FC  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #818CF8  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #6366F1  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ PRIMARY
600 #4F46E5  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #4338CA  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #3730A3  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #312E81  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SECONDARY (Violet)
50  #F5F3FF  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #EDE9FE  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #DDD6FE  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #C4B5FD  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #A78BFA  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #8B5CF6  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ SECONDARY
600 #7C3AED  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #6D28D9  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #5B21B6  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #4C1D95  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SUCCESS (Green)
50  #ECFDF5  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #D1FAE5  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #A7F3D0  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #6EE7B7  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #34D399  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #10B981  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ SUCCESS
600 #059669  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #047857  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #065F46  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #064E3B  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

WARNING (Amber)
50  #FFFBEB  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #FEF3C7  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #FDE68A  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #FCD34D  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #FBBF24  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #F59E0B  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ WARNING
600 #D97706  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #B45309  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #92400E  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #78350F  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ERROR (Red)
50  #FEF2F2  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #FEE2E2  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #FECACA  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #FCA5A5  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #F87171  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #EF4444  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ ERROR
600 #DC2626  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #B91C1C  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #991B1B  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #7F1D1D  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

INFO (Blue)
50  #EFF6FF  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
100 #DBEAFE  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
200 #BFDBFE  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
300 #93C5FD  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
400 #60A5FA  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
500 #3B82F6  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ INFO
600 #2563EB  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
700 #1D4ED8  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
800 #1E40AF  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
900 #1E3A8A  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 13.2 Typography Scale Reference

```
┌─────────────────────────────────────────────────────────────┐
│ DISPLAY                                                     │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 6xl / 60px / 3.75rem                                       │
│ Heading 1 - Hero titles                                    │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 5xl / 48px / 3rem                                          │
│ Heading 2 - Page titles                                    │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 4xl / 36px / 2.25rem                                       │
│ Heading 3 - Section headings                               │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ HEADING                                                     │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 3xl / 30px / 1.875rem                                      │
│ Heading 4 - Subsection headings                            │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 2xl / 24px / 1.5rem                                        │
│ Heading 5 - Card titles                                    │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ xl / 20px / 1.25rem                                        │
│ Heading 6 - Small headings                                 │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ BODY                                                        │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ lg / 18px / 1.125rem                                       │
│ Lead text, emphasized body                                 │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ base / 16px / 1rem                                         │
│ Default body text                                          │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ sm / 14px / 0.875rem                                       │
│ Secondary text, helper text                                │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ xs / 12px / 0.75rem                                        │
│ Captions, fine print                                       │
└─────────────────────────────────────────────────────────────┘
```

### 13.3 Icon Library

#### Recommended Icon Set

**Heroicons** (MIT License) - Primary icon library

- Consistent 24px default size
- Optimized SVG paths
- Outline and solid variants
- Compatible with React

#### Icon Usage Guidelines

| Property | Value |
|----------|-------|
| Default size | 20px (sm), 24px (md) |
| Stroke width | 2px |
| Color | Inherit from text color |
| Alignment | Middle/center |

---

## 14. Related Documents

- 01_Platform_Overview_PRD.md - Platform architecture
- 02_Technical_Architecture_PRD.md - Technical specifications
- 03_Component_Library_PRD.md - Component library details
- 04_Accessibility_Standards_PRD.md - Accessibility requirements

---

**Document End**

---

*This document is part of the PhotoIdentifier Platform Product Requirements Documentation. For the latest version and related documents, refer to the ClaudeDocs directory.*
