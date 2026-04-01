# MOTO — Discover (Profile Browsing) Wireframe Spec

## Shell Layout

```
+------------------------------------------+
| [Logo] MOTO    [Filter] [Bell*] | [Theme]|  <- 56px header
+------------------------------------------+
|                                          |
|  +----- SCROLLABLE CONTENT AREA ------+  |
|  |                                    |  |
|  |  PHOTO CAROUSEL (3:4 aspect)       |  |
|  |  [dots]  [<tap left] [tap right>]  |  |
|  |  Gradient overlay at bottom:       |  |
|  |  "Emma Chen 28"                    |  |
|  |  [Verified] San Francisco, CA      |  |
|  |                                    |  |
|  +------------------------------------+  |
|  | MUSIC PLAYER (sticky top, blur bg) |  |
|  | [Art] Title / Artist [EQ] [Play]   |  |
|  | [====-------] progress bar         |  |
|  +------------------------------------+  |
|  | QUICK TAGS row (pill chips)        |  |
|  +------------------------------------+  |
|  | COMPATIBILITY CARD (gradient bg)   |  |
|  | [87% ring] "Extraordinary Match"   |  |
|  | [Expand v] -> domain bars          |  |
|  +------------------------------------+  |
|  | LIFE PLANS (2-col card grid)       |  |
|  | [Marriage] [Children]              |  |
|  | [Location] [Education]             |  |
|  | [Spirit]   [Finance]              |  |
|  +------------------------------------+  |
|  | VALUES & BELIEFS (icon+text list)  |  |
|  +------------------------------------+  |
|  | SOCIAL INTERESTS (tag pills)       |  |
|  +------------------------------------+  |
|  | MOOD BOARD (pinterest grid)        |  |
|  | [tall]  [sq]  [sq]                |  |
|  | [tall]  [sq]  [+4]               |  |
|  +------------------------------------+  |
|  | AUDIO IDENTITY (track list)        |  |
|  +------------------------------------+  |
|  | WRITTEN EXPRESSION (poem card)     |  |
|  | Quote + attribution + reflection   |  |
|  +------------------------------------+  |
|  | GEOGRAPHY (icon+detail list)       |  |
|  +------------------------------------+  |
|                                          |
+------------------------------------------+
| [X Pass] [* Super] [<3 LIKE] [Bookmark] |  <- Action bar
+------------------------------------------+
| Discover  Matches  Messages  Activity  Me|  <- 60px tab bar
+------------------------------------------+
```

Max-width: 430px centered. Height: 100vh.

## Header

- Height: 56px, surface-1 bg, border-bottom faint
- Left: MOTO logo (28px SVG mark + gradient text)
- Right: filter icon btn (40px), bell icon btn (40px, pink notification dot), theme toggle

## Photo Carousel

- Aspect ratio: 3:4, full width, surface-2 bg
- 5 dot indicators at top (3px height bars, 32px wide, white translucent)
- Left/right tap zones (40% width each, invisible)
- Bottom gradient overlay: transparent to bg-page
- Name: 28px/700, white. Age: 24px/300, white 70%
- Verified badge: green-muted bg, pill shape, checkmark + "Verified"
- Location: 14px, white 70%, map-pin icon

## Music Player (Sticky)

- Sticks to top of scroll area, z-index 10
- Blur backdrop: 12px, surface-1 at 85% alpha
- Album art: 40px square, rounded-md
- Track title: 13px/500. Artist: 12px tertiary
- Spotify badge: green #1DB954, 10px
- Animated equalizer bars (4 bars, varying heights)
- Play/pause button: 36px circle, accent bg
- 2px progress bar at absolute bottom

## Compatibility Score Card

- Gradient warm background, accent-tinted border
- SVG ring: 72px, 4px stroke, accent fill, animated dashoffset
- Score: 20px/700 accent. Percent: 11px tertiary
- Match label: "Extraordinary Match" pill with star icon, accent-muted bg
- Description: 14px secondary
- Expand button toggles domain breakdown (max-height transition)

## Domain Score Breakdown (Expandable)

| Domain | Weight | Bar Color | Example Score |
|---|---|---|---|
| Family Goals | 25% | accent-pink | 92 |
| Geography | 15% | info blue | 88 |
| Spirituality | 15% | special purple | 94 |
| Lifestyle | 15% | gold | 85 |
| Physical Attraction | 10% | accent-pink | 80 |
| Politics | 10% | warning amber | 72 |
| Social Interests | 10% | positive green | 90 |

- Each row: 28px icon (rounded-md, tinted bg) + name/weight + 4px bar + numeric score
- Alignment chips below: green "Both want 2-3 children", amber "Moderate political difference"

## Life Plans

- Section header: 13px/600 uppercase tertiary + 14px secondary subtitle
- 2-column grid, 12px gap
- Each card: surface-2 bg, border-faint, rounded-xl, 16px padding
- Content: emoji (20px) + label (12px tertiary) + value (14px/500 primary)

## Values & Beliefs

- Icon + text list, 16px vertical gap
- Icon: 36px rounded-lg, tinted bg, centered emoji
- Title: 14px/500 primary. Quote: 14px secondary, 1.5 line-height

## Social Interests

- Flex-wrap tag pills, 8px gap
- Top interests: accent-muted bg, accent text, 500 weight
- Others: surface-2 bg, border-faint, secondary text
- Footer note: 13px tertiary

## Mood Board

- 3-col x 2-row grid, 4px gap, 3:2 container aspect
- First item: spans full left column (grid-row 1/3)
- Last item: "+4 more" overlay (black 50%, white text)
- All items: rounded-lg, overflow hidden, hover opacity

## Audio Identity (Playlist)

- Spotify badge in section header
- Currently playing: accent-muted bg, eq animation, accent text
- Other tracks: numbered, hover surface-hover, 10px padding
- Duration: 12px tertiary, tabular-nums

## Written Expression

- Poem card: surface-2 bg, rounded-2xl, 32px padding
- Top gradient stripe: 3px, accent to pink
- Large quote mark: 48px Georgia, accent 30% opacity
- Poem text: 16px italic, 1.8 line-height
- Attribution: 13px tertiary, 500 weight
- Reflection section: border-top divider, 12px uppercase accent label, 14px secondary text

## Geography

- Icon + detail list, 12px gap
- 36px icon containers (rounded-lg, surface-2 or accent-muted bg)
- Label: 12px tertiary. Value: 14px/500 primary
- Distance: positive green color, tabular-nums

## Action Bar

- Fixed above tab bar, surface-1 blur backdrop
- 4 buttons centered with 20px gap
- Pass: 52px circle, surface-2, X icon. Hover: red tint
- Super Like: 44px circle, gold-muted, star fill. Hover: gold glow
- Like (primary): 64px circle, purple-to-pink gradient, heart fill, 20px shadow. Hover: scale 1.05 + stronger shadow
- Save: 44px circle, surface-2, bookmark outline. Hover: blue tint

## Bottom Tab Bar

- 60px height, surface-1 bg, border-top faint
- 5 tabs: Discover (compass), Matches (heart), Messages (chat + badge), Activity (pulse), Profile (user)
- Active: accent color. Inactive: tertiary
- Each: 22px icon + 11px/500 label, flex-column, 2px gap
- Messages badge: pink bg, white 9px/700 count, 16px pill

## Filter Sheet (Bottom Modal)

- Overlay: fixed, black 50%, z-100
- Sheet: bottom-anchored, rounded-t-2xl, surface-1, max 80vh
- Handle bar: 36px wide, 4px, centered
- Groups: Marriage Readiness, Family Timeline, Geographic Commitment, Spirituality, Min Compatibility
- Chips: 36px height, rounded-full, border-default. Selected: accent-muted bg + accent border
- Range slider: accent color, 14px/600 accent value label
- Apply button: full-width primary lg

## Atmosphere

Warm Luxury (Atmosphere 3): purple accent (#a78bfa dark / #7c3aed light), stone warm tones.
Dark default. Light toggle available.

## Interactions

- Photo carousel: tap left/right zones or dots to navigate
- Music player: sticky on scroll, play/pause toggle
- Compatibility: expand/collapse domain breakdown with animated max-height
- Filter sheet: opens from header button, closes on overlay click or Done
- Filter chips: toggle selected state on click
- Action buttons: scale on press, hover color transitions
- All interactive elements: focus-visible double-ring pattern
