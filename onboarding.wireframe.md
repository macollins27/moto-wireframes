# MOTO Onboarding — Wireframe Spec

## Layout: Mobile-First Step Wizard (430px max-width)

```
+------------------------------+
| [===progress-bar=========  ] | 3px track, accent fill, width% = step/total
+------------------------------+
| < Back     MOTO      [sun]  | 56px top-bar, logo center, theme toggle right
+------------------------------+
| o o [===] o o o o o o o o o  | Domain rail: 13 dots, active=pill, complete=green
+------------------------------+
|                              |
|  CHAPTER {N}                 | 12px uppercase accent label
|  Serif Heading               | Lora 28px/600
|  Italic subtitle             | Lora 16px/400 italic, text-secondary
|                              |
|  [ form content area ]       | Scrollable, 24px horizontal padding
|  [ inputs / cards / pills ]  |
|  [ sliders / grids ]         |
|                              |
+------------------------------+
| Skip for now     [Continue]  | 56px bottom bar, skip=ghost, continue=primary-lg
+------------------------------+
```

## Atmosphere: Custom Warm Dark Luxury

- Dark default, warm stone undertones (NOT cool zinc)
- Accent: rose-gold/copper `#d4a574` (dark) / `#b07d4f` (light)
- Surfaces: `#0c0a09` page, `#151311` card, `#1e1b18` recessed
- Typography: Inter body + Lora serif for chapter headings
- Button primary: accent bg with dark text `#1c1917`

## 13 Steps (0-12)

| Step | Domain | Key Components |
|------|--------|----------------|
| 0 | Welcome | Domain preview list, time estimate callout, "Begin" CTA |
| 1 | Identity | Text input (name), date picker, gender pills, height selects, ethnicity pills, preference pills |
| 2 | Photos | 6-slot photo grid (primary 2x2 + 4 small), labeled contexts (face/body/lifestyle/social), verification CTA card |
| 3 | Geography | 3 text inputs (from/current/longterm), 4 image-option cards (urban/suburban/rural/coastal), relocation pills, international pills, importance bar |
| 4 | Spiritual | 2 select dropdowns (upbringing/current), importance bar (4 levels), 3 option-cards (cultural/practicing/devout), free-text textarea |
| 5 | Political | Multi-select philosophy pills (10 options), importance bar, non-negotiables textarea, privacy note card |
| 6 | Social | Ranked interest pills with numbered badges, 3 frequency option-cards, social preference range slider |
| 7 | Family | Counter input (children count), range pills, importance bar, 2 timeline grids (marriage/children, 2x2), financial readiness pills, 4 education option-cards |
| 8 | Lifestyle | Wealth range slider, career text input, income select, daily-life multi-pills, 3 finance-approach option-cards |
| 9 | Mood Board | Info callout, 2x2+2wide mood-grid upload slots (labeled), description textarea, style archetype pills |
| 10 | Audio | Spotify connect card (green icon), 5 song slots (3 filled, 2 empty dashed), genre multi-pills |
| 11 | Literary | Literary textarea (Lora serif, 1.8 line-height), reflection textarea, 2 book text inputs, quote card |
| 12 | Complete | Check circle, "Blueprint Is Ready" heading, 11-row domain status list (green dots + status text), 92% completeness card |

## Component Catalog

### Pill Selector
- h-10, rounded-full (20px), border-default, 14px/400
- Selected: accent-muted bg, accent border, accent text, 500 weight
- Multi-select: toggle independently. Single-select: radio behavior

### Option Card
- 16px 18px padding, rounded-xl, border-default
- Left: 40px icon square (rounded-lg, surface-2 bg). Center: title 15px/500 + desc 13px/tertiary. Right: 20px radio circle
- Selected: accent-muted bg, accent border, filled radio dot

### Importance Bar
- Flex row, 4 equal segments, h-9, rounded-md each, 12px/500
- Selected: accent-muted bg, accent border+text, 600 weight

### Timeline Grid
- 2x2 grid, 16px padding, rounded-xl, border-default
- Value: 18px/600 tabular-nums. Label: 12px/tertiary
- Selected: accent-muted bg, accent border, accent value text

### Image Option
- 2x2 grid, rounded-xl, 2px border
- Top: 90px visual area (emoji icon, surface-2 bg). Bottom: 13px/500 label
- Selected: accent border, accent label text

### Photo Grid
- 3-col grid, 10px gap. Primary slot spans col 1-2, row 1-2 (no aspect-ratio constraint on primary)
- Empty: dashed border, + icon, context label. Hover: accent dashed border, accent-soft bg

### Mood Grid
- 2-col grid. Some slots span full width (wide). 10px gap
- Same empty-state pattern as photo grid but with labeled contexts

### Counter Input
- Centered row: 44px circle - button, 32px/600 value, 44px circle + button
- tabular-nums on value display

### Literary Textarea
- Lora serif, 16px, 1.8 line-height, 18px padding
- Distinct from standard Inter textareas -- signals the literary nature of this field

### Range Slider
- 6px track (surface-2), 24px thumb (accent, 3px bg-page border)
- 3-label row below: left/center/right, 12px/tertiary

## Navigation Logic

- Continue/Back buttons advance/retreat step index
- Progress bar width = (currentStep / 12) * 100%
- Domain dots: complete=green, active=accent pill (24px wide), pending=default
- Skip button visible only on optional steps (5, 9, 10, 11)
- Step 0 hides Back button, shows "Begin" instead of "Continue"
- Step 12 shows "Start Matching" as CTA
- Content area scrolls to top on step change
- All selectors (pills, cards, options) are interactive via click handlers

## Differentiation from Competitors

1. **Chapter-based narrative** with Lora serif headings + philosophical subtitles (vs flat linear forms)
2. **Warm copper/rose-gold on dark stone** (vs Tinder pink-neon, Bumble gold, Hinge yellow)
3. **Domain-organized structure** with named chapters and progress rail (vs anonymous step counter)
4. **Photos after values** -- Step 2 comes after identity, before 8 values-based domains
5. **Rich input variety** -- mood board, Spotify integration, literary textarea, image-option cards, ranked pills
6. **No swipe-culture aesthetic** -- serif typography + warm tones + deliberate pacing signal intentionality
