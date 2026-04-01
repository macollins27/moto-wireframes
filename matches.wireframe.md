# MOTO Matches Page — Implementation Spec

## Shell Layout (Mobile-First, 430px)

```
+----------------------------------+
|  HEADER (h-14)                   |
|  [Matches (24)]    [Sort] [Theme]|
+----------------------------------+
|  FILTER BAR                      |
|  [All] [New] [Favorites] [Arch.] |
+----------------------------------+
|                                  |
|  SCROLLABLE CONTENT              |
|  "24 matches - 3 new"           |
|                                  |
|  +----------------------------+  |
|  | MATCH CARD                 |  |
|  | [Photo] Name, Age   [Score]|  |
|  |         Location    Ring   |  |
|  |         Timestamp          |  |
|  | [Chip] [Chip] [Chip]      |  |
|  | [Message] [Profile] [Fav] |  |
|  +----------------------------+  |
|  (repeats 6-8x)                 |
|                                  |
+----------------------------------+
|  TAB BAR (h-15)                  |
|  Disc  Match  Msg  Act  Profile  |
+----------------------------------+
```

## Top Header

- Height: h-14 (56px), surface-1 bg, border-b border-faint
- Left: "Matches" title (22px/700/-0.03em) + count badge (accent-muted bg, accent text)
- Right: sort/filter icon button (36px) + divider + theme toggle (36px)
- Sort dropdown: absolute positioned, surface-1, border-default, rounded-xl, shadow-lg, 220px wide

## Filter Bar

- Horizontal scroll, no visible scrollbar, surface-1 bg, border-b
- Pill buttons: h-8, px-3.5, rounded-full (20px), border-default, 13px/500
- Active pill: accent-muted bg, accent border, accent text
- Icons: 12px inline SVG for New (dot) and Favorites (heart outline)

## Match Card

```
+----------------------------------------------+
| [64x64 Photo]  Name, Age    [56px Score Ring]|
|  (rnd-2xl)     Location pin                  |
|  online dot    Timestamp                     |
+----------------------------------------------+
| [Family 96%] [Spirit 94%] [Geo 91%]         |
+----------------------------------------------+
| [==== Message ====] [Profile] [Heart]        |
+----------------------------------------------+
```

### Card Container
- surface-1 bg, border-faint, rounded-2xl (16px), p-5 (20px)
- Hover: surface-hover bg, border-default, shadow-sm, scale(0.99) on active
- New variant: accent border, accent-muted gradient overlay, subtle glow

### Profile Photo
- 64x64px, rounded-2xl (16px), surface-2 bg placeholder
- Online indicator: 12px green dot, bottom-right, 2px surface-1 border

### Info Section
- Name: 16px/600/-0.02em, text-primary, truncate
- "New" badge: 20px height, 11px/600, uppercase, 0.04em tracking, special-bg/special color
- Location: 13px, text-tertiary, with 12px map-pin icon
- Timestamp: 12px, text-disabled

### Score Ring (SVG)
- 56px diameter, 3.5px stroke, -90deg rotation
- Track: border-default stroke
- Fill: stroke-dasharray 113.1, dashoffset varies by percentage
- Score text: 15px/700, tabular-nums, centered absolute

| Score Range | Ring Color | Text Color |
|-------------|-----------|------------|
| 87%+        | #16a34a (positive) | positive |
| 70-86%      | #a78bfa (accent)   | accent   |
| Below 70%   | #3b82f6 (info)     | info     |

### Domain Chips
- mt-3, flex-wrap, gap-1.5
- Each: h-6, px-2.5, rounded-xl (12px), 12px/500, tabular-nums

| Chip Score | Background | Text Color |
|-----------|-----------|------------|
| 90%+      | positive-bg | positive |
| 80-89%    | accent-muted | accent |
| Below 80% | info-bg | info |

### Message Preview
- mt-3, surface-2 bg, rounded-lg+ (10px), p-2.5 px-3.5
- 16px accent chat icon + 14px text-secondary, truncate single line

### Action Buttons Row
- mt-3.5, flex, gap-2
- Base: h-9, px-3.5, rounded-lg+ (10px), border-default, surface-2, 13px/500
- Message/Reply btn: accent bg, white text, flex:1 (fills remaining space)
- Profile btn: person icon only
- Favorite btn: heart outline; when active: filled heart, red-tinted bg/border

## Bottom Tab Bar

- h-15 (60px), surface-1, border-t border-faint, space-around
- 5 tabs: Discover (compass), Matches (heart, active), Messages (chat), Activity (bell), Profile (person)
- Each: column flex, 22px icon + 11px/500 label, 2px gap
- Active: accent color; Inactive: text-tertiary
- Badge: min-w-4 h-4, accent bg, white 10px/600 text, absolute top-right

## Card Variants

| Variant | Visual Differences |
|---------|-------------------|
| New match | accent border, gradient overlay, "NEW" badge next to name |
| High compat (87%+) | Green score ring, green domain chips |
| Mid compat (70-86%) | Purple score ring, purple domain chips |
| Favorited | Filled red heart, red-tinted button bg |
| Has message | Message preview block between chips and actions, "Reply" instead of "Message" |
| Online | Green dot on photo bottom-right |

## Empty State (no matches)

- Centered column, 80px vertical padding
- 48px heart icon (text-disabled)
- "No matches yet" (16px/500)
- "Complete your profile and explore Discover to find your person." (14px/text-tertiary, max-w-[360px])
- "Go to Discover" primary button (accent, h-12, rounded-xl)

## Atmosphere

- Warm Luxury (Atmosphere 3): stone-based neutrals, purple accent (#a78bfa dark / #7c3aed light)
- Dark mode default, light mode via toggle
- All colors via CSS custom properties on `[data-theme]`

## Interactions

- Filter pills: tap to activate (single-select), deactivates siblings
- Sort dropdown: toggle on filter icon tap, close on outside click
- Match cards: tap navigates to full profile detail
- Action buttons: Message opens chat, Profile opens detail, Heart toggles favorite
- Theme toggle: swaps data-theme attribute on html element
