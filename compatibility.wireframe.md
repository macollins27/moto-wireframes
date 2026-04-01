# MOTO Compatibility Deep Dive — Wireframe Spec

## Shell Layout (Mobile-First, 430px max-width)

```
+------------------------------+
| [<] Compatibility [sun][...] |  56px top header
+------------------------------+
|                              |
|     (scrollable content)     |  flex:1, overflow-y:auto
|                              |
+------------------------------+
| Discover Matches Msgs Profile|  60px bottom tab bar
+------------------------------+
```

- Max-width: 430px, centered, height: 100vh
- Dark mode default (data-theme="dark")
- Bottom tab bar: 4 tabs, Matches active (gold accent)
- Header: back arrow left, "Compatibility" center, theme toggle + more right

## Custom Atmosphere: Warm Intentional

Based on Warm Luxury (#3) with key changes:

| Token | Dark | Light | Why |
|-------|------|-------|-----|
| accent | `#d4a054` (amber gold) | `#b8862e` | Warmth + intention, avoids Tinder coral / Bumble yellow / Badoo purple |
| bg-page | `#0c0a09` | `#faf8f6` | Warm stone, not neutral gray |
| surface-1 | `#151311` | `#ffffff` | Subtle warm tint |

Custom tokens for compatibility scoring:
- `--compat-high` (green): 90-100 scores
- `--compat-good` (lime): 75-89 scores
- `--compat-moderate` (yellow): 50-74 scores
- `--compat-low` (red): 0-49 scores

## Match Hero Section

```
+------------------------------+
|      [A-avatar] 87 [S-avatar]|  Rounded-square avatars (72px, r-16)
|                              |  Score badge centered between (40px circle)
|    You & Sarah Mitchell      |  20px/600
|    Charlotte, NC - 28        |  14px/text-secondary
|    [check] Strong Alignment  |  Pill badge, green tinted
+------------------------------+
```

- Avatars: 72x72px, border-radius 16px (NOT circular — differentiation from competitors)
- Score ring: 40px circle, accent bg, dark text, shadow glow
- Gradient background: accent-soft to transparent (top-down)
- Compatibility level badge: pill shape with icon + text

## View Switcher (3 views)

```
+----------+----------+----------+
| Overview | Domains  | Compare  |
+----------+----------+----------+
```

- Segmented control: surface-2 bg, 3px padding, rounded-10
- Active: surface-1 bg + shadow-xs + text-primary
- Inactive: transparent bg + text-tertiary
- Each button: 36px height, 13px/500 font, icon + label

## View 1: Overview

### Radar Chart
- SVG 280x280, centered
- 10 axes (one per domain), 4 concentric rings
- Two overlapping polygons: You (gold fill 12% + solid stroke) and Sarah (blue fill 10% + dashed stroke)
- Dots at each vertex for both users
- Labels outside chart: 10px/500 text-tertiary

### Legend Row
- 3 items centered: You (gold dot), Sarah (blue dot), Overlap (dashed line)
- 12px/500 text-secondary

### Scale Legend
- 4 items: 90-100 (green), 75-89 (lime), 50-74 (yellow), 0-49 (red)
- 10px text, colored dots

### Key Insight Callout
- accent-soft bg + accent-muted border, rounded-12, 16px padding
- "KEY INSIGHT" label: 11px/600 uppercase accent color
- Body: 14px text-secondary with bold highlights

### Algorithm Transparency Box
- surface-2 bg, rounded-10, 14px padding
- "HOW YOUR SCORE IS CALCULATED" label
- 7 horizontal bar rows: label (80px) + bar track + percentage value
- Bar fill: accent color, width proportional to weight
- Footer note: 11px text-disabled explaining weighted average

### Domain Snapshot List
- 10 rows, 6px gap, vertical stack
- Each row: surface-1 bg, border-faint, rounded-10
- Content: emoji icon + domain name (14px/500) + score (15px/600 colored) + bar (40px track)
- Bars color-coded by score range

## View 2: Domains (Expandable Cards)

### Domain Card (collapsed)
```
+------------------------------------------+
| [icon-bg] Family Goals  25%    95 [===] v|
|           Highest weighted              |
+------------------------------------------+
```
- 12px card radius, surface-1 bg, border-faint
- Icon: 40x40 rounded-10, tinted bg matching domain color
- Name: 14px/600 + weight pill (10px accent badge)
- Subtitle: 12px text-tertiary
- Score: 16px/600, color-coded + 48px bar track
- Chevron: rotates 180deg on expand

### Domain Card (expanded) — adds detail panel below header
```
+------------------------------------------+
| [icon-bg] Family Goals  25%    95 [===] ^|
|           Highest weighted               |
|------------------------------------------|
|   YOU              |   SARAH             |
|   Children: 3-4    |   Children: 3-5     |
|   Marriage: < 3yr  |   Marriage: < 3yr   |
|   Start: 2 yrs    |   Start: 2 yrs     |
|   Edu: Homeschool  |   Edu: Homeschool   |
|                                          |
|   [check] Near-perfect alignment         |
+------------------------------------------+
```

- Detail panel: border-top separator, 16px padding
- Two-column grid for comparison
- Column headers: 11px/600 uppercase, You = accent, Sarah = blue
- Field labels: 11px/500 uppercase text-tertiary
- Field values: 14px/500 text-primary
- Match indicator pill: colored bg + icon + description text
- Variants: aligned (green), partial (yellow), differs (red)

### All 10 Domains (each with full expanded content)

| Domain | Score | Status | Key Detail |
|--------|-------|--------|------------|
| Family Goals | 95 | aligned | 3-4 vs 3-5 children, same marriage timeline |
| Geography | 92 | aligned | Both in Charlotte, both want suburban South |
| Spirituality | 91 | aligned | Both non-denom Christian, high importance |
| Lifestyle | 84 | aligned | 2 shared hobbies, compatible social energy, shared tags |
| Attraction | 88 | aligned | Photo verified, 3 context images, height shown |
| Politics | 82 | aligned | Both tradition-oriented, minor individualism/community diff |
| Social | 79 | partial | Different hobbies but similar energy levels |
| Economic | 68 | partial | High vs medium wealth priority, suburb vs rural/suburb |
| Cultural | 85 | aligned | Shared mood board themes, warm home + outdoor space |
| Literary | 86 | aligned | Both value depth and patience, complementary passages |

## View 3: Compare (Side-by-Side)

### Header Row
```
   [A]        vs       [S]
   You                Sarah
```
- 48px rounded-12 avatar squares
- 13px/600 name labels
- "vs" text: 12px text-disabled

### Comparison Rows (per domain)
```
+--Domain Title-----------score--+
| +----------+    +----------+   |
| | Label    | () | Label    |   |
| | Value    |    | Value    |   |
| +----------+    +----------+   |
```
- Domain title bar: dot (8px, domain color) + name (14px/600) + score (13px/600 colored)
- Row grid: 1fr | 32px | 1fr
- Cells: surface-1 bg, border-faint, rounded-8, 8px 10px padding
- Center column: match dot (10px circle with glow shadow)
  - Aligned: green + green glow
  - Partial: yellow + yellow glow
  - Differs: red + red glow

### Alignment Legend
- 3 items centered: Aligned (green), Partial (yellow), Differs (red)
- 11px text-tertiary

## Bottom CTA (all views)

```
+------------------------------+
| [bookmark] | Express Interest |
+------------------------------+
```
- Sticky bottom, gradient fade bg
- Bookmark: 48x48 secondary button
- Express Interest: flex-1 primary button, 48px height, 16px/600 font

## Interaction Model

| Interaction | Behavior |
|-------------|----------|
| View switch | Segmented control swaps content, scrolls to top |
| Domain expand | Toggle card expanded class, chevron rotates |
| Theme toggle | Swaps dark/light via data-theme attribute |
| Express Interest | Primary CTA — navigates to interest flow |
| Bookmark | Save match for later review |
| Back arrow | Returns to matches list |

## Badge Color System

| Range | Color Token | Text | Background |
|-------|------------|------|------------|
| 90-100 | compat-high | green `#4ade80` / `#16a34a` | `rgba(74,222,128,0.08)` |
| 75-89 | compat-good | lime `#a3e635` / `#65a30d` | `rgba(163,230,53,0.08)` |
| 50-74 | compat-moderate | yellow `#facc15` / `#ca8a04` | `rgba(250,204,21,0.08)` |
| 0-49 | compat-low | red `#f87171` / `#dc2626` | `rgba(248,113,113,0.08)` |

## Key Differentiation from Competitors

1. **Values-first, not photo-first** — Radar chart and domain scores are the hero content
2. **10 domains visible, not 1 number** — Transparent, explorable scoring
3. **Algorithm transparency** — Weight visualization shows HOW scores are calculated
4. **Warm amber palette** — Grounded and intentional, not playful/dopamine-driven
5. **Rounded-square avatars** — Not circular (every dating app uses circles)
6. **Active exploration** — Expandable cards and 3 view modes vs passive scroll
