# MOTO — My Profile Wireframe Spec

## Shell Layout

```
+------------------------------------------+
| [Logo] MOTO          [Settings] | [Theme]|  <- 56px header
+------------------------------------------+
|                                          |
|  [ My Profile | Preview as Others See ]  |  <- toggle
|                                          |
|  Sophia Martinez, 28                     |
|  [Verified badge]                        |
|                                          |
|  +-- IDENTITY STRENGTH CARD ----------+  |
|  | [82% ring]  Complete your Literary  |  |
|  |             Expression...           |  |
|  |  [======] Family 100%              |  |
|  |  [======] Geography 100%           |  |
|  |  [====  ] Politics 75%             |  |
|  |  [      ] Literary 0%             |  |
|  +------------------------------------+  |
|                                          |
|  PHOTOS  [Edit]                          |
|  +--------+------+                       |
|  | Main   | Sm 1 |  <- 2fr 1fr grid     |
|  | (tall) +------+     3 visible + count |
|  |        | Sm 2 |                       |
|  +--------+------+                       |
|                                          |
|  FAMILY ARCHITECTURE [Edit]  25% weight  |
|  [gradient top stripe]                   |
|  [Children] [Marriage]   <- 2-col grid   |
|  [Timeline] [Education]                  |
|                                          |
|  GEOGRAPHY [Edit]  15% weight            |
|  [From] [Lives] [Long-term] [Relocate?]  |
|                                          |
|  SPIRITUALITY [Edit]  15% weight         |
|  [Icon] Faith + Practice level           |
|  [Importance bars] + personal reflection |
|                                          |
|  LIFESTYLE [Edit]  15% weight            |
|  [Wealth] [Environment] + tag chips      |
|                                          |
|  POLITICAL PHILOSOPHY [Edit]  10% weight |
|  [Belief chips] [Importance] [Non-neg]   |
|                                          |
|  SOCIAL INTERESTS [Edit]  10% weight     |
|  [Interest chips - top 3 highlighted]    |
|  [Frequency] [Social style]              |
|                                          |
|  MY VIBE — MOOD BOARD [Edit]             |
|  [tall]  [sq]  [sq]   <- masonry grid   |
|         [sq]  [+4]                       |
|  "Sundress, children, open land..."      |
|                                          |
|  AUDIO IDENTITY [Spotify badge] [Edit]   |
|  [EQ] Holocene - Bon Iver (playing)     |
|  [2] The Night We Met - Lord Huron      |
|  [3] Lost in the Light - Bahamas        |
|  [4] First Day of My Life - Bright Eyes |
|  [5] Youth - Daughter                   |
|  "View full playlist (12 songs)"         |
|                                          |
|  LITERARY EXPRESSION [Add]               |
|  [Empty state: dashed border]            |
|  [Book icon] Share Your Words            |
|  [Description + CTA button]              |
|                                          |
|  ABOUT ME [Edit]  10% weight             |
|  [Height] [Ethnicity] [Education] [Job]  |
|                                          |
|  [Privacy & Safety Settings]             |
|  [Sign Out]                              |
|  MOTO v1.0.0 - Member since Mar 2026    |
|                                          |
+------------------------------------------+
| Discover  Matches  Messages  Activity  Me|  <- 60px tab bar
+------------------------------------------+
```

Max-width: 430px centered. Height: 100vh. Dark-first.

## Header

- Height: 56px, surface-1 bg, border-bottom faint
- Left: MOTO logo (28px SVG mark + gradient text, purple to pink)
- Right: settings gear icon btn (40px), divider, theme toggle

## Preview Toggle

- Segmented control: surface-2 bg, 3px padding, 10px radius
- Two buttons: "My Profile" (active) / "Preview as Others See"
- Active: surface-1 bg, shadow-xs, primary text. Inactive: tertiary text
- Preview mode hides all Edit buttons

## Identity Strength Card

- gradient-warm background, accent-tinted border
- Left: SVG completion ring (100px, 6px stroke, accent fill)
- Ring center: 22px/700 accent percentage + 11px "Complete" label
- Right: h3 title, 13px description, "Complete Now" btn-primary btn-sm pill
- Below: 2-col grid of domain mini-bars (10 domains)
- Each bar: emoji (14px) + name (11px tertiary) + percent (11px colored) + 4px track

## Domain Bar Colors

| Domain | Bar Color | Token |
|---|---|---|
| Family Goals | pink | accent-pink |
| Geography | blue | info |
| Spirituality | purple | special |
| Lifestyle | gold | accent-gold |
| Photos | pink | accent-pink |
| Politics | amber | warning |
| Mood Board | purple | accent |
| Audio Identity | green | #1DB954 |
| Literary Expression | red (0%) | negative |
| Social Interests | green | positive |

## Photos Section

- section-label (11px/600 uppercase) + section-edit-btn
- Photo grid: 2fr 1fr columns, 2 rows, 3px gap, 16px radius, 4:3 aspect
- Main photo spans both rows (left column)
- Placeholder gradients with emoji + label
- Below: "6 photos" count + "View all" accent link

## Family Architecture Section

- 25% weight badge (pink)
- Card with 4px gradient top stripe (pink to purple to gold)
- 2-col grid of life-plan-cards (surface-2 bg, 12px radius, 16px padding)
- Each: emoji + label (12px tertiary) + value (14px/500) + optional importance tag

## Geography Section

- 15% weight badge (blue)
- geo-row items: 36px icon container (10px radius, tinted bg) + label/value stack
- 3 rows: From, Currently, Long-term goal
- Bottom divider + "Open to relocating?" with green answer

## Spirituality Section

- 15% weight badge (purple)
- 40px icon container + belief system + practice level
- Importance bars: 4 segments (20px x 4px), filled = special color, empty = border-default 40%
- Personal reflection in surface-2 container, italic, secondary text

## Lifestyle Section

- 15% weight badge (gold)
- 2-col grid: Material Wealth Importance + Preferred Environment
- value-chip pills: highlighted = accent-muted bg + accent text. Default = surface-2

## Political Philosophy Section

- 10% weight badge (amber)
- Belief chips (same value-chip pattern), importance bars, non-negotiables text

## Social Interests Section

- 10% weight badge (green)
- Interest pills: top 3 = highlighted, others = default
- Footer: frequency + social style in 2-col layout

## Mood Board Section

- No weight badge (cultural aesthetic domain)
- 3-col masonry grid: first item spans 2 rows (tall), 4px gap
- Last item: "+4 more" dark overlay
- Below: italic vibe description centered (13px tertiary)

## Audio Identity Section

- Spotify badge (green #1DB954, 11px/600, rounded-full)
- 5 tracks: playing track has accent-muted bg + EQ animation + accent text
- Track item: 10px 12px padding, 8px radius, hover surface-hover
- Track art: 40px square, 6px radius. Title: 14px/500. Artist: 12px tertiary
- Duration: 12px tertiary tabular-nums
- "View full playlist" accent link centered

## Literary Expression Section (Empty State)

- Dashed border card, centered content
- 36px icon (40% opacity) + 16px/500 heading + 14px tertiary description
- CTA: btn-primary btn-sm pill "Add Literary Expression"

## About Me Section

- 10% weight badge (pink)
- 2-col grid: Height, Ethnicity, Education, Occupation

## Account Actions

- Two full-width btn-secondary (12px radius): Privacy & Safety, Sign Out
- Footer: 12px disabled text with version + member since

## Bottom Tab Bar

- 60px height, surface-1 bg, border-top faint
- 5 tabs: Discover (compass), Matches (heart), Messages (chat + pink badge "3"), Activity (pulse), Profile (user, ACTIVE)
- Active: accent color. Inactive: tertiary
- Each: 22px icon + 11px/500 label

## Edit Sheets (11 total)

All edit sheets share: overlay (fixed, black 50%), bottom-anchored sheet (surface-1, 20px radius top, max 85vh), handle bar, h2 title + close X, form fields, Cancel (ghost) + Save (primary) buttons.

| Sheet | Key Fields |
|---|---|
| Family Architecture | children select, importance toggle, marriage timeline chips, start family select, education chips |
| Photos | 3x2 grid with numbered slots, delete buttons, add slot (dashed), tip box |
| Literary Expression | type toggle (poem/personal), title input, passage textarea, reflection textarea |
| Geography | from input, current input, long-term chips, international toggle, relocate toggle |
| Spirituality | upbringing input, belief select, importance 3-btn, practice select, reflection textarea |
| Lifestyle | wealth 3-btn, environment 3-btn, lifestyle tag chips (multi-select) |
| Politics | belief chips (multi-select, max 3), importance 3-btn, non-negotiables textarea |
| Social Interests | interest chips (tap to rank top 3), add new input, frequency select, social preference 3-btn |
| Mood Board | 3x2 image grid with delete + add slot, vibe description input |
| Audio Identity | Spotify connection card, playlist select dropdown, description |
| About Me | height input, ethnicity select, education select + field input, occupation input |

## Atmosphere

Warm Luxury (Atmosphere 3) with MOTO custom tokens: accent-pink, accent-gold, gradient-warm, gradient-hero. Purple accent (#a78bfa dark / #7c3aed light). Dark default.

## Interactions

- Preview toggle: switches between edit and view-only modes (hides edit buttons)
- Edit buttons: open corresponding bottom sheet overlay
- Sheet overlay: click outside to close, X button to close
- Photo grid items: hover opacity 0.85
- Mood board items: hover opacity 0.85
- Track items: hover surface-hover bg, playing track has EQ animation
- All interactive elements: focus-visible double-ring, 150ms transitions
