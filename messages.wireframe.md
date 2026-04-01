# MOTO — Messages / Conversations Wireframe Spec

## Shell Layout

```
+------------------------------------------+
| [Logo] MOTO        [NewMsg] | [Theme]    |  <- 56px header
+------------------------------------------+
| [Q Search conversations...]              |  <- search bar, rounded-full
+------------------------------------------+
| [ All (7) | Unread (3) | Archived ]      |  <- filter tabs
+------------------------------------------+
| NEW MATCHES (horizontal scroll)          |
| (o) (o) (o) (o)  <- gradient-bordered    |
| Isa  Rac  Nao  Pri    avatar circles     |
+------------------------------------------+
| CONVERSATIONS                            |
| [avatar] Emma Chen          2m ago       |
|          That poem by Mary Oliver...  *  |
|          [Your turn] [92% match]         |
|------------------------------------------|
| [avatar] James Rivera       28m ago      |
|          I actually grew up on a...   *  |
|------------------------------------------|
| [avatar] Sophia Williams    1h ago       |
|          [mic] Voice note - 0:42         |
|------------------------------------------|
| [avatar] Daniel Park        3h ago       |
|          [music] Shared playlist...   *  |
|------------------------------------------|
| [avatar] Olivia Martinez    Yesterday    |
|          You: That sounds like an...     |
|------------------------------------------|
| [avatar] Marcus Thompson    Mar 29       |
|          You: Definitely! Let's plan...  |
|------------------------------------------|
| [avatar] Ava Nakamura       Mar 27       |
|          That Rilke passage you shared...|
+------------------------------------------+
| Discover  Matches  Messages* Activity  Me|  <- 60px tab bar
+------------------------------------------+
```

Max-width: 430px centered. Height: 100vh. Two views: list + thread.

## Header

- Height: 56px, surface-1 bg, border-bottom faint
- Left: MOTO logo mark (28px SVG) + gradient text (accent to accent-pink)
- Right: new-message icon btn (40px) + divider + theme toggle

## Search Bar

- Rounded-full (20px radius), surface-2 bg, transparent border
- 40px height, 16px left icon padding
- Focus: bg-page bg, accent border

## Filter Tabs

- 3 tabs: All, Unread, Archived — equal width
- Active: accent text, 500 weight, 2px accent bottom border
- Count badges: accent-muted bg, accent text, pill (9px radius)
- Panels switch on click (JS)

## New Matches Row

- Horizontal scroll, 16px padding
- Each: 60px circle with gradient border (accent to accent-pink, 2px)
- Inner circle: gradient photo placeholder
- Label: 12px/500 secondary text

## Conversation Item

- 52px avatar (circle), 12px gap, 14px/16px padding
- Name: 15px/500. Time: 12px tertiary, tabular-nums
- Preview: 14px secondary, ellipsis overflow
- Unread: dot (10px accent circle), name 600 weight, preview primary color, time accent
- Your-turn badge: 20px height pill, accent-muted bg, accent text, 11px/600
- Compatibility mini: 11px/600 accent, tabular-nums
- Voice note preview: mic icon + "Voice note - 0:42"
- Playlist preview: music icon + "Shared a playlist"
- Online indicator: 12px green dot on avatar, surface-1 border

## Thread View Layout

```
+------------------------------------------+
| [<] (av) Emma Chen             [Ph] [..] |  <- 60px thread header
|          Online now                       |
+------------------------------------------+
| [compat ring] 92% Compatible        [>]  |  <- tappable compat banner
| Strong alignment in family & spirituality |
+------------------------------------------+
|                                           |
|  SCROLLABLE MESSAGES                      |
|                                           |
|       (Match intro card)                  |
|       [avatar] You matched with Emma      |
|       SF, CA - Matched Mar 28             |
|       "She liked your prompt..."          |
|                                           |
|  --- March 28 ---                         |
|                                           |
|  [prompt ref card]                        |
|  "The moment I knew..."                   |
|  [bubble-theirs] I loved your answer...   |
|                                6:42 PM    |
|           [bubble-own] Thank you!         |
|           7:15 PM                         |
|  [bubble-theirs] I was living in NYC...   |
|                                7:28 PM    |
|           [bubble-own] That's incredible  |
|           7:45 PM                         |
|  [bubble-theirs] Speaking of mood boards  |
|  [playlist-card] Quiet Evenings           |
|    1. Holocene - Bon Iver                 |
|    2. The Night We Met - Lord Huron       |
|    3. Mystery of Love - Sufjan Stevens    |
|    View full playlist                     |
|                                8:03 PM    |
|           [bubble-own] Bon Iver AND...    |
|           8:12 PM                         |
|                                           |
|  --- March 29 ---                         |
|                                           |
|  [voice-note bubble]                      |
|  [play] [||||||||||||] 1:24              |
|                               10:15 AM    |
|           [bubble-own] I love that you... |
|           11:30 AM                        |
|           [bubble-own] By the way...      |
|           [check] Read                    |
|                                           |
|  --- Today ---                            |
|                                           |
|  [bubble-theirs] That poem by Mary...     |
|                               Just now    |
|  [...] (typing indicator)                 |
|                                           |
+------------------------------------------+
| [input field...          [img][music]]   |
| [mic / send]                              |
+------------------------------------------+
```

## Thread Header

- Height: 60px, surface-1 bg, border-bottom faint
- Back chevron (left), 36px avatar (tappable), name 16px/600, status 12px tertiary
- Online status: positive green text "Online now"
- Right: phone icon btn + more-options (vertical dots) btn

## Compatibility Banner

- Gradient-warm bg, accent-muted border, 12px radius
- SVG ring: 44px, 3px stroke, accent fill, dasharray animated
- Score: 14px/600 accent. Label: 12px tertiary
- Tappable: opens profile quick-view sheet
- Right chevron icon

## Message Bubbles

- Own: bubble-own bg (accent 18% alpha), accent 25% border, right-aligned
- Theirs: surface-2 bg, border-faint border, left-aligned
- Radius: 18px default, 6px on tail corner
- Consecutive same-sender: 6px radius on adjacent corners
- Font: 15px, 1.45 line-height
- Max width: 82% of container
- Timestamps: 11px tertiary, tabular-nums, below bubble
- Read receipt: 11px accent, checkmark icon + "Read"

## Special Message Types

### Prompt Reference
- Gradient-warm bg, accent-muted border, 12px radius
- Label: 11px/600 accent, uppercase
- Quote: 14px primary

### Voice Note
- Play button: 28px accent circle, white play icon
- Waveform: 3px bars, varying heights, played = accent, unplayed = tertiary
- Duration: 12px tertiary, tabular-nums

### Shared Playlist
- Surface-2 card, 12px radius
- Header: Spotify green tint bg, logo + title + song count
- Track list: numbered, 13px secondary, ellipsis overflow
- "View full playlist" link: accent text

## Message Input

- Surface-2 bg wrapper, 22px radius (pill), border-faint
- Input: 15px, no border, transparent bg
- Actions inside pill: photo + music icons (32px touch targets)
- Outside pill: voice-note btn (40px) when empty, send btn (40px accent circle) when typing
- Focus-within: accent border on wrapper

## Profile Quick-View Sheet

- Bottom sheet: surface-1, rounded-t-2xl (20px), max 75vh
- Overlay: black 50%
- Handle bar: 36px wide, 4px height, border-strong color
- Content: 64px avatar + name/age/location + verified badge
- Compatibility card: gradient-warm bg, 2x2 grid of life plan items
- Life architecture: stacked rows (surface-2 bg, 8px radius)
- CTA: full-width primary btn "View Full Profile" (48px, 12px radius)

## Bottom Tab Bar

- 60px height, surface-1 bg, border-top faint
- 5 tabs: Discover (compass), Matches (heart), Messages (chat), Activity (pulse), Profile (user)
- Active: accent color (Messages on this screen)
- Each: 22px icon + 11px/500 label
- Messages badge: pink bg, white 9px/700 count, 16px pill

## Atmosphere

Warm Luxury (Atmosphere 3): purple accent (#a78bfa dark / #7c3aed light), stone warm tones.
Custom tokens: bubble-own (accent 18% alpha), bubble-theirs (surface-2), accent-pink, accent-gold.
Dark default. Light toggle available.

## Interactions

- Tap conversation: navigates to thread view (JS view toggle)
- Back button: returns to list view
- Filter tabs: switch between All/Unread/Archived panels
- Typing indicator: 3-dot bounce animation
- Voice/send toggle: input listener swaps mic for send button
- Profile sheet: tap avatar/name/compat-banner to open bottom sheet
- Sheet overlay: tap overlay to dismiss
- All interactive elements: focus-visible double-ring pattern
- Input wrapper: focus-within accent border
