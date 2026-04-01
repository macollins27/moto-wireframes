# MOTO Activity Feed — Wireframe Spec

## Shell Layout (Mobile-First, 430px)

```
+----------------------------------+
|  HEADER  [Activity]    [theme]   |  56px, surface-1
+----------------------------------+
|  [Connections] [Views] [Reson.]  |  Segment control, surface-2 bg
+----------------------------------+
|                                  |
|  SCROLLABLE CONTENT AREA         |  flex:1, overflow-y:auto
|  (segment panels switch here)    |
|                                  |
+----------------------------------+
| Discover Matches Activity Msg Me |  64px bottom tab bar, surface-1
+----------------------------------+
```

- Phone frame: 430px max-width, 100vh, centered
- Dark mode default, warm stone palette (NOT cold zinc)
- Accent: dusty rose `#d4917a` (dark) / `#b06b52` (light)

## Bottom Tab Bar

5 tabs: Discover, Matches, **Activity** (active), Messages, Profile

| Tab | Icon | Active State |
|-----|------|-------------|
| Discover | Compass | accent color |
| Matches | Users | text-tertiary |
| Activity | Bell + notif dot | accent color |
| Messages | Chat bubble | text-tertiary |
| Profile | User | text-tertiary |

- Height: 64px, icon 22px, label 11px/500
- Active: accent color on icon + label
- Notification dot: 8px circle, accent bg, 2px surface-1 border

## Segment Control

3 segments in rounded pill container (surface-2 bg, 10px radius, 3px padding):

| Segment | Content Type |
|---------|-------------|
| Connections | Rich engagement cards from people who expressed interest |
| Views | Compact list of profile viewers with depth metrics |
| Resonances | Grouped by expression type (literary, mood board, audio) |

- Active: surface-1 bg, shadow-xs, text-primary
- Inactive: transparent bg, text-tertiary

## Summary Stats Row

Each segment has a 3-column stat row below the segment control:

- Connections: `7 This Week` | `92% Avg Alignment` | `3 Family Match`
- Views: `23 This Week` | `4.2min Avg Time` | `68% Scrolled Deep`
- Resonances: `5 Poem` | `8 Mood Board` | `12 Audio`

Values: 20px/600, tabular-nums. Labels: 11px/500/uppercase, text-tertiary.

## Activity Card (Connections Segment)

```
+----------------------------------+
| [avatar]  Name         time      |  Header row
|           Action description     |
+----------------------------------+
| [poem tag] [family tag]          |  Engagement type tags
+----------------------------------+
| | "I want to be with those..."   |  Content preview (varies by type)
| |  — Rainer Maria Rilke          |
+----------------------------------+
| Alignment ====████====  94%      |  Compatibility bar
+----------------------------------+
| [Family 98%] [Spirit 91%] [Geo]  |  Domain alignment chips
+----------------------------------+
| [♥ Connect]  [View Profile]      |  Action buttons
+----------------------------------+
```

### Card Components

**Avatar**: 52px square, 14px radius, placeholder gradient or photo

**Engagement Tags** (pill badges, 24px height, 12px radius):

| Tag | Color Token | Icon |
|-----|------------|------|
| Literary | `--engagement-poem` / blue-gray | Book icon |
| Mood Board | `--engagement-mood` / purple | Image icon |
| Audio Identity | `--engagement-music` / teal | Music note |
| Lifestyle/Values | `--engagement-values` / amber | Home icon |
| Family Goals | `--compatibility-high` / green | Users icon |
| Photo | `--accent` / rose | Image icon |

**Content Previews** (surface-2 bg, 12px radius):
- Poem: left 3px border in poem color, italic text, attribution
- Mood Board: 3 thumbnail images in flex row, 64px height, 8px radius
- Music: album art (44x44, 8px radius) + title/artist + EQ bars animation
- Values: checkmark list of shared family/lifestyle goals

**Compatibility Bar**:
- Track: 4px height, surface-3 bg, 2px radius
- Fill: colored by score (green >80%, amber 60-80%)
- Score: 13px/600, tabular-nums, colored same as fill

**Domain Chips** (26px height, 13px pill radius):
- Strong (>80%): compatibility-high-bg, green text
- Moderate (60-80%): compatibility-mid-bg, amber text
- Each shows icon + domain name + percentage

**Action Buttons** (36px height, 18px pill radius):
- Connect: accent bg, white text, heart icon
- View Profile: surface-2 bg, text-secondary
- Send Message: surface-2 bg (for mutual connections)

## View Item (Views Segment)

```
+----------------------------------+
| [avatar]  Name           time    |
|           What they viewed  ★86% |
+----------------------------------+
```

- Compact row: 14px vertical padding, 20px horizontal
- Avatar: 48px, 14px radius
- Name: 15px/500
- Detail: 13px, text-tertiary
- Mini compatibility: star icon + percentage, colored by score
- Separated by 1px border-faint

## Resonance Card (Resonances Segment)

Grouped under category headers (Literary Expression, Mood Board, Audio Identity).
Similar structure to activity cards but with full-width CTA:

- "See her literary expression"
- "Compare mood boards"
- "Listen to her playlist"

CTAs: full-width action-btn-secondary, surface-2 bg.

## Custom Tokens (beyond standard atmosphere)

```
--compatibility-high: #7ec89b (green, >80%)
--compatibility-mid: #d4b77a (amber, 60-80%)
--engagement-poem: #a8b4d4 (blue-gray)
--engagement-mood: #c4a8d4 (purple)
--engagement-music: #7ec8b8 (teal)
--engagement-values: #d4a87a (amber)
```

Each has a `-bg` variant at 10% opacity for tag/chip backgrounds.

## Empty State (Resonances)

- Book icon, 48px, text-disabled
- "No resonances yet" heading (16px/500)
- Description explaining what triggers resonances (14px, text-tertiary, 300px max)
- "Enrich Your Profile" CTA button (accent bg)

## Key Design Decisions (from research)

1. Activity items show ALIGNMENT data, not just attraction — every card has compatibility bar + domain chips
2. No gamification counters or urgency timers — each person is treated as meaningful, not a number
3. Content previews surface what was engaged with (poem snippet, mood board images, playlist overlap)
4. Warm dark palette (stone undertones #0e0c0b) instead of cold charcoal (#191919)
5. Dusty rose accent differentiates from blue (tech) and hot pink (casual dating)
