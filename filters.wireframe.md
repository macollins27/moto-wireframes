# MOTO — Intent Filters Wireframe Spec

Machine-readable implementation spec for AI coding agents.

## Layout

```
┌──────────────────────────────┐  430px max-width, 100vh
│  HEADER (56px fixed)         │  Back | "Intent Filters" | Reset All | Theme
├──────────────────────────────┤
│  SCROLLABLE CONTENT          │  flex:1, overflow-y:auto
│                              │
│  ┌─ Page Intro ────────────┐ │  h1 + subtitle paragraph
│  └─────────────────────────┘ │
│  ┌─ Match Quality Card ───┐ │  Icon + "Match precision: 78%"
│  └─────────────────────────┘ │
│  ── Core Domains ────────── │  Section divider label
│  ┌─ Domain Card (expand) ─┐ │  Accordion cards, one per domain
│  │  Icon | Title | Weight  │ │  40px icon, weight badge, chevron
│  │  ───────────────────── │ │
│  │  Filter Row 1           │ │  Label + question + control + importance
│  │  Filter Row 2           │ │  Each filter has 3-level importance
│  │  Filter Row N           │ │
│  └─────────────────────────┘ │
│  ... repeat per domain ...   │
│  ── Secondary Domains ───── │  Section divider
│  ... more domain cards ...   │
│  ── Expression Domains ──── │  Section divider
│  ┌─ Info Card ─────────────┐ │  "These domains work differently"
│  └─────────────────────────┘ │
│  ┌─ Automatic Domain ─────┐ │  Non-expandable, "Automatic" badge
│  └─────────────────────────┘ │  x3 (Vibe, Audio, Literary)
├──────────────────────────────┤
│  APPLY BAR (sticky)          │  Reset btn | Apply Filters (lg) + count
├──────────────────────────────┤
│  BOTTOM TABS (64px fixed)    │  Discover | Filters* | Matches | Msgs | Profile
└──────────────────────────────┘
```

## Mobile Shell

- **Max-width:** 430px centered, 100vh, border-left/right
- **Header:** 56px, back arrow + title left, reset + theme right
- **Bottom tabs:** 64px, 5 tabs, icon 22px + label 11px, active = accent
- **Apply bar:** sticky above tabs, Reset secondary + Apply primary lg + count badge

## Color Atmosphere — "Intimate Warmth"

Custom atmosphere based on Warm Luxury. Warm stone surfaces, rose accent.

| Token | Dark | Light |
|-------|------|-------|
| bg-page | `#0c0a09` | `#faf8f6` |
| surface-1 | `#141210` | `#ffffff` |
| surface-2 | `#1c1a17` | `#f5f3f0` |
| accent | `#e8836a` | `#c9623e` |
| accent-muted | `rgba(232,131,106,0.12)` | `rgba(201,98,62,0.10)` |

## Domain Section Card

Accordion pattern. Each card = one matching domain.

- **Header:** 40px icon (unique color per domain) + title (15px/600) + weight badge + chevron
- **Weight badge:** 12px/600 tabular-nums, accent bg, rounded-md (6px)
- **Body:** hidden by default, border-top separator, 20px padding
- **Expanded:** `.expanded` class shows body, rotates chevron 180deg
- **Expression domains:** opacity 0.7, non-expandable, "Automatic" neutral badge

### Domain icon colors

| Domain | Icon bg | Icon color |
|--------|---------|------------|
| Family Goals (25%) | `rgba(239,136,104,0.12)` | `#ef8868` |
| Geography (15%) | `rgba(59,130,246,0.12)` | `#3b82f6` |
| Spirituality (15%) | `rgba(168,130,250,0.12)` | `#a882fa` |
| Lifestyle (15%) | `rgba(34,197,94,0.12)` | `#22c55e` |
| Physical (10%) | `rgba(244,114,182,0.12)` | `#f472b6` |
| Politics (10%) | `rgba(251,191,36,0.12)` | `#fbbf24` |
| Social (10%) | `rgba(56,189,248,0.12)` | `#38bdf8` |
| Expression (auto) | `rgba(232,131,106,0.08)` | text-tertiary |

## Filter Controls

### Single Select (Radio)
- Option items: 10px 14px padding, rounded-xl (10px), border-faint
- Selected: accent-subtle bg, accent border, primary text
- Radio circle: 18px, 2px border; dot 8px, accent fill on selected

### Multi-Select (Chips)
- Pill shape: h-36px, rounded-full (18px), border-default
- Selected: accent-muted bg, accent border, accent text, font-weight 500

### Range Slider
- Track: 6px height, rounded-sm, surface-3 bg
- Fill: accent color
- Thumb: 22px circle, accent bg, 3px surface-1 border, shadow-sm
- Labels: value (13px/500/primary), bounds (13px/disabled)

### Toggle Switch
- 44x24px, rounded-full, surface-3 bg; active = accent bg
- Knob: 20px white circle, 2px inset, translateX(20px) when active

### Importance Selector (3-level)
- Row of 3 equal buttons below each filter
- States: Must match (rose tint), Important (amber tint), Flexible (gray tint)
- Each 32px height, rounded-md (8px), 11px/500 text
- "Must match" shows small triangle icon

| Level | Active bg | Active border | Active text |
|-------|-----------|---------------|-------------|
| Must match | `rgba(239,136,104,0.15)` | `#ef8868` | `#ef8868` |
| Important | `rgba(212,165,116,0.12)` | `#d4a574` | `#d4a574` |
| Flexible | surface-hover | border-strong | text-secondary |

## Match Quality Card

- Gradient warm bg + accent-muted border, rounded-xl
- 36px icon box (accent-muted bg, check icon)
- Label: "Match precision: 78%" with accent-colored percentage
- Desc: "Set 2 more filters to reach high precision"

## Section Dividers

- Flex row: line + label + line
- Label: 11px/600 uppercase, 0.08em tracking, text-disabled

## Key Interactions

- Click domain header: toggle expanded/collapsed (except expression domains)
- Click chip: toggle selected state
- Click option-item: select single option (radio behavior)
- Click importance btn: select importance level (radio within group)
- Click toggle switch: toggle on/off
- Drag range thumb: adjust value
- Click Apply: apply all filters, return to discovery
- Click Reset All: clear all filter selections
- Click Reset (apply bar): same as Reset All
- Theme toggle: swap dark/light

## Domains & Filters Summary

| Domain | Weight | Filters |
|--------|--------|---------|
| Family Goals | 25% | Marriage timeline, Children count, Family timeline, Education philosophy |
| Geography | 15% | Max distance (range), Long-term location (chips), Relocation openness (radio) |
| Spirituality | 15% | Belief system (chips), Faith importance (radio) |
| Lifestyle | 15% | Material ambition (radio), Substance preferences (chips), Social energy (chips) |
| Physical | 10% | Age range (dual range), Height range (dual range), Verified photos (toggle) |
| Politics | 10% | Core beliefs (chips), Non-negotiable values (chips) |
| Social | 10% | Shared interests (chips), Require 2+ shared (toggle) |
| Vibe | auto | No filter — algorithmic via mood board |
| Audio | auto | No filter — algorithmic via Spotify |
| Literary | auto | No filter — algorithmic via written expression |

## Bottom Tab Bar

5 tabs: Discover (search icon), Filters (funnel, active), Matches (heart), Messages (chat), Profile (user)
Active tab: accent color. Inactive: text-tertiary. Icon 22px, label 11px/500.
