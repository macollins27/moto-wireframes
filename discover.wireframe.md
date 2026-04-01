# MOTO Discover — Wireframe Spec

## Shell Layout (430px mobile)

```
+----------------------------------+
|  HEADER  [Logo] 3/8  [F] [T]    |  56px, surface-1
+----------------------------------+
| [ForYou] [Ready] [Near] [Fam].. |  filter-row, scroll-x
+----------------------------------+
|                                  |
|   IMMERSIVE PROFILE SCROLL       |  flex:1, overflow-y:auto
|   (one person at a time)         |
|                                  |
|   Ch1: Photo + Identity          |
|   Ch2: Alignment Bars            |
|   Ch3: Life Architecture         |
|   Ch4: Values & Beliefs          |
|   Ch5: Audio Identity            |
|   Ch6: Mood Board                |
|   Ch7: Literary Expression       |
|   Ch8: Lifestyle Details         |
|                                  |
+----------------------------------+
|  [X]   [Bookmark]   [Heart]     |  action-bar, surface-1
+----------------------------------+
| Disc  Match  Msg  Activity  Me  |  tab-bar, 60px, surface-1
+----------------------------------+
```

## Header

- 56px height, surface-1 bg, border-bottom border-faint
- Left: MOTO logo (gradient SVG circle + gradient text), profile counter "3 of 8" in text-tertiary
- Right: filter icon btn (36x36) + divider + theme toggle (36x36)

## Intent Filter Row

- Horizontally scrollable pills, 13px font, rounded-full (20px radius)
- Active pill: accent border + accent-muted bg + accent text
- Inactive: border-default + surface-1 bg + text-secondary
- Filters: "For You" (active), "Ready Now", "Near You", "Family-Focused", "Same Timeline"
- Each pill has leading SVG icon (14x14)

## Chapter 1: Photo + Identity

- Full-bleed photo area, aspect-ratio 3:4
- Photo dot indicators at top center (6px dots, active=20px wide pill, white)
- Top gradient overlay for status bar
- Bottom gradient overlay with identity info:
  - Name: Playfair Display serif, 28px/600, white
  - Meta row: age + height + location + verified badge, 14px, white/75%
  - Compatibility ring: 48x48 SVG circle, stroke-dasharray for score arc, score number centered 13px/700
  - Ring label: "89% Life Alignment" bold + description below

## Chapter 2: Alignment Bars

- Chapter label: 11px/600 uppercase, accent color, 0.1em letter-spacing
- Chapter title: Playfair Display 20px/600
- 7 domain rows, each with:
  - Icon: 28x28 rounded-md, domain-color-muted bg, domain-color icon
  - Name + weight label: 13px/500 + 11px/text-disabled
  - Track: 4px height, surface-2 bg, domain-color fill
  - Percentage: 13px/600 tabular-nums, color-coded (green >80%, amber 60-79%, red <60%)

| Domain | Color var | Weight |
|--------|-----------|--------|
| Family Goals | --domain-family (#f472b6) | 25% |
| Geography | --domain-geography (#3b82f6) | 15% |
| Spirituality | --domain-spirituality (#8b5cf6) | 15% |
| Lifestyle | --domain-lifestyle (#fbbf24) | 15% |
| Attraction | --domain-attraction (#f472b6) | 10% |
| Philosophy | --domain-politics (#d97706) | 10% |
| Social | --domain-social (#16a34a) | 10% |

## Chapter 3: Life Architecture

- Timeline rows with 32x32 rounded-lg colored icons
- Each row: label (13px/500), value (14px/text-secondary), match indicator pill
- Match indicator: rounded-full, 12px/600, semantic bg+text
  - "Aligned with you": compat-high-muted bg, compat-high text
  - "Close to yours": compat-medium-muted bg, compat-medium text
  - "Different from yours": compat-medium-muted bg, compat-medium text
- Data: marriage timeline, children count + non-negotiable flag, family start age, location preference, education philosophy

## Chapter 4: Values & Beliefs

- Spiritual life: denomination + importance level + free-text expression
- Core values: flex-wrap chip grid, 13px/500, rounded-full (20px)
  - `.aligned`: compat-high border + muted bg + text
  - `.partial`: accent-gold border + muted bg + text
  - default: border-default + surface-1 bg
- Lifestyle values: same chip pattern

## Chapter 5: Audio Identity

- Now-playing bar: 44x44 album art placeholder + title/artist + waveform animation
- Playlist card: surface-1 bg, rounded-xl, Spotify icon + playlist name + song count
- Song list: 3 preview rows (number, title, artist, duration), all tabular-nums

## Chapter 6: Mood Board

- 2-column CSS grid, 4px gap, rounded-xl overflow hidden
- First item spans 2 rows (`.tall`), rest are 1:1 squares
- Each item has gradient overlay caption at bottom (11px/500 white)
- Archetype quote below grid: 14px italic text-secondary

## Chapter 7: Literary Expression

- Passage block: surface-1 bg, border-faint, rounded-xl
- Large quote mark: Playfair Display 44px, accent color, 0.3 opacity
- Poem text: Playfair Display italic 16px/1.7
- Source: Inter 13px text-tertiary
- Reflection: 14px text-secondary, border-top separator

## Chapter 8: Lifestyle Details

- Detail rows: icon (16px text-tertiary) + label (13px text-tertiary, 90px min) + value (14px/500 text-primary)
- Rows separated by border-top border-faint
- Data: daily rhythm, activity, social style, wealth view, work style, environment

## Action Bar

- 3 buttons centered with 16px gap
- Pass: 56x56 circle, surface-2 bg, border-default, X icon. Hover: negative-muted bg, negative border+icon
- Bookmark: 56x56 circle, surface-2 bg, border-default, bookmark icon. Hover: gold-muted bg, gold border+icon
- Interested: 64x64 circle (larger = primary), accent bg, white heart icon, accent box-shadow glow. Hover: accent-hover + stronger glow

## Bottom Tab Bar

- 60px height, surface-1, border-top border-faint
- 5 tabs: Discover (active), Matches, Messages (badge "3"), Activity, Profile
- Active: accent color fill. Inactive: text-tertiary stroke
- Tab: flex-column, 22x22 icon + 11px/500 label

## Key Differentiators from Competitors

1. NOT a swipe card — full vertical scroll narrative per person
2. Compatibility ring + 7-domain bars visible BEFORE detailed content
3. Serif typography (Playfair Display) for headings — editorial feel
4. Mood board grid embedded in profile scroll
5. Audio identity with waveform animation
6. Literary expression with reflection
7. Intent-based filter pills (marriage readiness, family timeline)
8. Three-action model (pass/bookmark/interested) not binary swipe
