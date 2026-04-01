# MOTO — Matches (Compatibility Stories) Wireframe Spec

## Shell Layout — Match List

```
+------------------------------------------+
| [Logo] MOTO             [Sort] | [Theme] |  <- 56px header
+------------------------------------------+
| [H1] Matches                  12 matches |  <- Title row
+------------------------------------------+
| [NEW MATCH BANNER]                       |
| [ava][ava] 2 New Matches — Emma & Sophia |
+------------------------------------------+
| [All 12] [Deep 3] [Strong 5] [Explore 4] |  <- Filter pills
+------------------------------------------+
|  * DEEP ALIGNMENT (85%+)       3 matches |  <- Tier header
|  ----------------------------------------|
|  o +------+ Emma Chen 28          2h     |
|    | rect | San Francisco, CA            |
|    | photo| [92% ring] Extraordinary     |
|    | mood | [fam][geo][spi][life][soc].. |
|    +------+                              |
|  ----------------------------------------|
|    +------+ Olivia Laurent 26       1d   |
|    | rect | Napa Valley, CA              |
|    | photo| [95% ring] Extraordinary     |
|    | mood | [fam][spi][life][geo][soc].. |
|    +------+                              |
|  ----------------------------------------|
|    +------+ Isabella Reyes 30       3d   |
|    | rect | Austin, TX                   |
|    | photo| [88% ring] Deep Alignment    |
|    +------+                              |
|  ----------------------------------------|
|  STRONG POTENTIAL (70-84%)     5 matches  |
|  ----------------------------------------|
|    +------+ Sophia Nakamura 27      5h   |
|    | rect | Portland, OR                 |
|    | photo| [81% ring] Strong Potential  |
|    +------+                              |
|  ... (4 more Strong Potential matches)   |
|  ----------------------------------------|
|  EXPLORING (<70%)             4 matches   |
|  ----------------------------------------|
|    +------+ Natalie Park 26         6d   |
|    | rect | Seattle, WA                  |
|    | photo| [68% ring] Exploring         |
|    +------+                              |
|  ... (3 more Exploring matches)          |
+------------------------------------------+
| Discover  [Matches*]  Messages  Act  Me  |  <- 60px tab bar
+------------------------------------------+
```

## Shell Layout — Match Detail (on card tap)

```
+------------------------------------------+
| [<] [ava] Emma Chen   [Profile] [More]   |  <- 56px detail header
|           92%* San Francisco, CA         |
+------------------------------------------+
|  +--------- HERO PHOTO (4:3) ---------+ |
|  | gradient overlay at bottom:         | |
|  | "Emma Chen, 28"                     | |
|  | pin San Francisco, CA . 12mi away   | |
|  +-------------------------------------+ |
|  +--- COMPATIBILITY CARD (overlapping) -+|
|  | [92% RING]  star Extraordinary Match ||
|  |              "You and Emma align..." ||
|  | ------------------------------------ ||
|  | fam [====94%====]  spi [====96%===] ||
|  | geo [====90%====]  soc [====90%===] ||
|  | life[====88%====]  att [===82%====] ||
|  | pol [===78%====]                    ||
|  | ------------------------------------ ||
|  | check Both want 2-3 children (3yr)  ||
|  | check Shared Christian faith        ||
|  | check Both prefer suburban living   ||
|  | ~ Moderate education difference     ||
|  +--------------------------------------+|
|  [Life Plans] [Values] [Interests]       |
|  [Mood Board] [Expression] [Audio]       |
|  +--- ACTIVE TAB CONTENT BELOW --------+|
|  |  (6 fully-populated tabs)           | |
|  +-------------------------------------+ |
+------------------------------------------+
| [X] [Send Message (primary CTA)] [Save] |  <- CTA bar
+------------------------------------------+
| Discover  [Matches*]  Messages  Act  Me  |  <- 60px tab bar
+------------------------------------------+
```

Max-width: 430px centered. Height: 100vh. Two switchable views (list/detail).

## Header

- Height: 56px, surface-1 bg, border-bottom faint
- Left: MOTO logo (24px SVG ring + 18px/700 gradient text)
- Right: sort icon btn (36px) + divider + theme toggle

## New Match Banner

- Gradient warm bg, accent-tinted border, 14px border-radius
- Stacked rounded-rect avatars (36x42px, 8px radius, border 2px surface-1)
- Title: 14px/600 accent "2 New Matches"
- Subtitle: 12px secondary with names
- Chevron right arrow in accent

## Filter Pills

- Horizontal scroll row, 8px gap, 12px 20px padding
- Pill buttons: 34px height, rounded-full (17px), border-default
- Active: accent-muted bg, accent border, accent text
- Count badges: 11px/600, surface-2 bg (active: accent 20% alpha)
- Labels: "All", "Deep Alignment", "Strong Potential", "Exploring", "New"

## Tier Sections

| Tier | Score Range | Icon | Color |
|---|---|---|---|
| Deep Alignment | 85%+ | Star (filled) | positive green |
| Strong Potential | 70-84% | Circle-check | accent purple |
| Exploring | <70% | Info circle | warning amber |

- Each tier: 28px icon (rounded-lg, tinted bg) + label (12px/600 uppercase) + count + divider line

## Match Card (MOTO Unique — Compatibility Story Card)

**Avatar (Rounded Rectangle — NOT circular):**
- 72x88px, 12px radius, overflow hidden
- Mood board glimpse strip at bottom: 24px height, 3 strips from user's mood board images
- Background: surface-2 when loading

**Content Layout:**
- Name row: name (15px/500) + age (14px/300 secondary) + time (12px/tertiary, tabular-nums, right-aligned)
- Location: 13px tertiary, map-pin icon (12px)
- Compatibility ring inline: 32px SVG ring + score (11px/600) + tier label (12px/500 secondary)
- Domain dots: 7 dots (18px each, 5px radius, 4px gap), emoji icon, tinted bg

**Domain Dot Opacity States:**
- Strong (80%+): opacity 1
- Moderate (60-79%): opacity 0.6
- Weak (<60%): opacity 0.35

**New Match Indicator:**
- 8px circle, accent color, absolute left:8px top:24px
- Pulse animation: 2s infinite opacity

## Detail View Header

- Back button: 36px, accent chevron
- Avatar: 36x42px rounded-rect
- Name: 15px/600. Meta: 12px tertiary (score + dot + location)
- Actions: profile icon btn + more (dots) icon btn, 36px each

## Detail Hero Photo

- Aspect ratio: 4/3, full width
- Bottom gradient overlay (hero gradient)
- Name: 24px/700 white. Subtitle: 14px white 70%

## Compatibility Card (Full — overlapping hero)

- margin: -24px 20px 0, z-index 2
- Gradient warm bg, accent-tinted border (20% alpha), 16px radius
- SVG ring: 64px, 4px stroke, score + pct text centered
- Tier label: 14px/600 accent with star icon
- Description: 13px secondary

**Domain Breakdown Bars (7 domains):**

| Domain | Weight | Bar Color | Icon |
|---|---|---|---|
| Family Goals | 25% | domain-family (pink) | baby emoji |
| Spirituality | 15% | domain-spirituality (purple) | dove emoji |
| Geography | 15% | domain-geography (blue) | pin emoji |
| Social Interests | 10% | domain-social (green) | target emoji |
| Lifestyle | 15% | domain-lifestyle (gold) | leaf emoji |
| Physical Attraction | 10% | domain-attraction (pink) | sparkle emoji |
| Political Philosophy | 10% | domain-politics (amber) | balance emoji |

- Each: 26px icon (7px radius, tinted bg) + name (12px/500 secondary) + score (12px/600 colored, tabular-nums) + 4px bar track

**Alignment Insights:**
- Border-top divider (accent 12% alpha)
- Check items: 18px green circle + text (13px secondary)
- Warning items: 18px amber circle + dash icon + text

## Detail Tabs (6 tabs, ALL populated)

### Life Plans
- 2-column grid, 10px gap
- Cards: surface-2 bg, border-faint, 12px radius, 14px padding
- Content: emoji (18px) + label (11px tertiary) + value (14px/500 primary)
- 6 cards: Marriage Timeline, Children, Long-term Location, Education, Lifestyle, Financial Readiness

### Values & Beliefs
- Icon + text list, 12px gap
- Icon: 36px rounded-lg (10px radius), tinted bg, centered emoji
- Label: 13px/500 primary. Description: 13px tertiary, 1.4 line-height
- 4 items: Spirituality, Family Orientation, Political Philosophy, Growth Mindset

### Interests
- Shared interests: accent-muted bg pills with accent border
- Unique interests: surface-2 bg pills with border-faint
- Social preference card: surface-2 bg, 12px radius

### Mood Board
- Descriptive paragraph (14px secondary)
- 3-col grid, 4px gap, first item spans 2 rows
- Last item: "+3 more" overlay (black 50%, white text)

### Written Expression
- Poem card: surface-2 bg, 16px radius, 24px padding
- Top gradient stripe: 3px, accent to pink
- Quote mark: 48px Georgia, accent 25% opacity
- Poem: 15px italic, 1.7 line-height
- "Why this resonates" section: border-top divider, 11px/600 uppercase accent label, 14px secondary text

### Audio Identity
- Spotify badge: green #1DB954, 10px/600
- Playing track: accent-muted bg, 8px radius, play icon, accent title
- Other tracks: number + art (36px square, 6px radius) + title/artist + duration (tabular-nums)
- Shared artists note: surface-2 bg card, accent text for count

## CTA Bar

- 12px 20px padding, border-top faint, surface-1 bg
- Pass: 48px circle, surface-2, X icon
- Message (primary): flex-1, 48px height, 24px radius, accent bg, white text + chat icon
- Save: 48px circle, surface-2, bookmark icon

## Bottom Tab Bar

- 60px height, surface-1 bg, border-top faint
- 5 tabs: Discover (compass), Matches (heart filled), Messages (chat + badge), Activity (pulse), Profile (user)
- Active: accent color (Matches tab active)
- Each: 22px icon + 11px/500 label, flex-column, 2px gap
- Messages badge: pink bg, white 9px/700 count "3", 16px pill

## Atmosphere

Warm Luxury (Atmosphere 3): purple accent (#a78bfa dark / #7c3aed light), stone warm tones.
Dark default. Light toggle available. Matches discover.html and messages.html design system.

## Key Differentiations from Tinder/Hinge/Bumble

1. **Tier-based organization** (Deep/Strong/Exploring) instead of chronological — reinforces values-first matching
2. **Rounded-rectangle avatars** (72x88px) with mood board glimpse strip — shows aesthetic identity at-a-glance
3. **Domain alignment dots** on every card — 7 emoji dots with opacity indicating strength per domain
4. **Compatibility ring** with tier labels inline — not just a number, a named tier with meaning
5. **Full compatibility story** on detail view — domain breakdown bars + alignment insights explain WHY they match
6. **6 deep tabs** (Life Plans, Values, Interests, Mood Board, Expression, Audio) — profiles are immersive identity experiences, not photo cards
7. **New match banner** groups new matches for intentional review, not just adding to a grid

## Interactions

- Match cards: tap to open detail view (list hides, detail shows)
- Back button: returns to list view
- Filter pills: toggle active state, single-select
- Detail tabs: 6 clickable tabs with content switching
- Theme toggle: swaps dark/light via data-theme attribute
- New match banner: tappable, navigates to first new match detail
- All interactive elements: focus-visible double-ring pattern
- Domain dots: hover scale 1.15 for tooltip preview
