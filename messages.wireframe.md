# MOTO — Messages (Conversations) Wireframe Spec

## Shell Layout — Conversation List

```
+------------------------------------------+
| [Logo] MOTO         [Search] | [Theme]   |  <- 56px header
+------------------------------------------+
| [Search messages...                    ] |  <- 44px pill input
+------------------------------------------+
| [All 7] [New 2] [Getting to Know 3] [Mtg]|  <- Stage filter pills
+------------------------------------------+
|  YOUR TURN                               |
|  +------+  Emma Chen           2m        |
|  | rect |  [92%*] Family & Spirit align  |
|  | photo|  I've been thinking about...   |
|  +------+                                |
|  ----------------------------------------|
|  +------+  Sophia Reyes         18m      |
|  | rect |  [84%*] Lifestyle & Geo match  |
|  | photo|  Hey! I loved your mood board  |
|  +------+                                |
|  ----------------------------------------|
|  THEIR TURN                              |
|  +------+  Olivia Laurent        1h      |
|  | rect |  [95%*] Extraordinary match    |
|  | photo|  You: That coffee spot sounds  |
|  +------+                                |
|  ... (7 total conversations)             |
+------------------------------------------+
| Discover  Matches  [Messages*]  Act  Me  |  <- 60px tab bar
+------------------------------------------+
```

## Shell Layout — Conversation Thread

```
+------------------------------------------+
| [<] [photo] Emma Chen     [Phone] [...]  |  <- Thread header
|             [92%*] San Francisco         |
+------------------------------------------+
| CONNECTION CARD (expandable on tap)      |
| [Family 94%] [Spirit 96%] [Geo 90%]     |
| [Lifestyle 88%] [Social 85%] [Pol 76%]  |
| check Both want 2-3 children in 3yr     |
| check Shared Christian faith            |
| ~ Minor education difference            |
+------------------------------------------+
|  DEPTH PROMPT (gradient warm bg)         |
|  [layers] You both value family highly.  |
|           Ask about her child-raising.   |
+------------------------------------------+
|           --- Mar 28, 2026 ---           |
|                                          |
|  [Emma] Hey! I noticed we have an       |
|         incredibly high match score...   |
|                                          |
|        That poem means so much [You] |
|        to me too... What draws you   |
|        to Berry specifically?        |
|                                          |
|  [Emma] Honestly, it's his philosophy   |
|         of rootedness...                 |
|                                          |
|        I completely resonate with    |
|        that. San Francisco feels     |
|        right but ultimately...  [You]|
|                                          |
|  [Emma] That's actually on my mood      |
|         board! Mill Valley...     [heart]|
|                                          |
|  [Emma] Speaking of which, I see we're  |
|         aligned on wanting 2-3 kids...   |
|                                          |
|           --- Mar 29, 2026 ---           |
|                                          |
|        [Voice Note: 1:42]       [You]|
|        [>> waveform bars >>>>]       |
|                                          |
|  [Emma] I loved hearing your voice!     |
|  [Emma] I've been thinking about what   |
|         you said about your faith...     |
|                                          |
|  [...]  (typing indicator)               |
|                                          |
+------------------------------------------+
| [Depth] [Mic] [Write something...] [->] |  <- Input area
+------------------------------------------+
| Discover  Matches  [Messages*]  Act  Me  |  <- 60px tab bar
+------------------------------------------+
```

Max-width: 430px centered. Height: 100vh. Two switchable views.

## Header

- Height: 56px, surface-1 bg, border-bottom faint
- Left: MOTO logo (22px/700, gradient text purple-to-lavender)
- Right: search icon btn (40px) + divider + theme toggle

## Conversation List View

### Search Input
- Pill shape: 44px height, border-radius 22px, surface-2 bg
- Search icon (16px) at left 12px
- Placeholder: "Search messages..."

### Stage Filter Tabs (MOTO Unique)
- Horizontal scroll row, 8px gap
- Pill buttons: 34px height, rounded-full, border-default
- Active: accent-muted bg, accent border, accent text
- Labels: "All", "New Connections", "Getting to Know", "Planning to Meet"
- Count badges: 11px/600, surface-2 bg, rounded, tabular-nums

### Conversation Items
- Full-width button, 14px 20px padding
- Unread indicator: 6px accent dot at left:8px

**Avatar (MOTO Differentiation — NOT circular):**
- 56x64px rounded-rectangle (10px radius)
- Shows more of person than circular crop
- Gradient placeholder with initial letter

**Content Layout:**
- Top row: name (15px/500) + timestamp (12px/tertiary, tabular-nums)
- Meta row: compatibility chip + top domain tag
- Preview: last message (14px/secondary, single line ellipsis)
- Unread items: name 600 weight, preview primary color, time accent color

**Compatibility Chip (MOTO Unique):**
- Inline pill: 18px height, rounded-full, 11px/600
- Star icon (10px) + percentage
- Color tiers: high (green-muted), medium (accent-muted), good (info-muted)

**Domain Tag:**
- 11px tertiary text after compat chip
- Shows top matching domains: "Family & Spirituality align"

### Turn-Based Grouping
- Group labels: "Your Turn" / "Their Turn"
- 11px/600 uppercase, 0.06em letter-spacing, tertiary
- Dividers: 1px faint, indented 90px from left

## Conversation Thread View

### Thread Header
- Back button: 36px, accent color chevron
- Profile tap zone: avatar (40x46px rounded-rect) + name + meta
- Name: 15px/600, hover transitions to accent
- Meta: compatibility chip (green) + dot separator + location
- Actions: phone icon btn + more (vertical dots) icon btn

### Connection Card (MOTO Unique — Expandable)
- Toggles on profile tap in header
- Gradient warm bg, border-bottom faint
- Animated max-height transition (300ms ease-out)
- Title: 12px/600 uppercase accent "Your Connection"
- Domain chips: 28px height pills, surface-1 bg, border-faint
  - Score colored: strong=green, moderate=accent, fair=warning
- Alignment items: checkmark/dash icon + description text

### Depth Prompt (MOTO Unique)
- Gradient warm bg with accent-tinted border
- 14px border-radius
- Icon: 28px rounded-md, accent-muted bg, layers icon
- Label: 11px/600 uppercase accent "Conversation Depth"
- Text: 13px secondary, contextual prompt tied to matching domains
- Dismiss X button at top-right

### Message Bubbles

| Property | Sent | Received |
|---|---|---|
| Background | bubble-sent (accent 18% alpha) | surface-2 |
| Border | bubble-sent-border (accent 25% alpha) | border-faint |
| Radius | 18px 18px 4px 18px | 18px 18px 18px 4px |
| Sequential | 18px 4px 4px 18px | 4px 18px 18px 4px |
| Seq-last | 18px 4px 18px 18px | 4px 18px 18px 18px |
| Max-width | 80% | 80% |
| Padding | 12px 16px | 12px 16px |
| Font | 15px/1.45 primary | 15px/1.45 primary |

### Message Reactions
- Absolute positioned at bottom of bubble
- Small pill: surface-1 bg, border-faint, 13px emoji
- Sent messages: positioned left. Received: positioned right

### Voice Notes
- Inline in bubble: play btn (28px circle accent) + waveform bars + duration
- Waveform: 3px wide bars, varying heights, tertiary color
- Played bars: accent color. Duration: 12px tertiary tabular-nums

### Date Separators
- Centered pill: surface-2 bg, 12px/500 tertiary
- 16px top padding, 12px bottom

### Typing Indicator
- Three dots animation (7px circles, tertiary color)
- Pulse keyframes: 1.4s infinite, 0.2s stagger
- In received-style bubble

### Message Input Area
- Surface-1 bg, border-top faint, 8px 12px 10px padding
- Left actions: depth prompt toggle (layers icon) + voice note (mic icon)
  - 36px ghost buttons, tertiary color
- Text input: flex-1, pill shape (20px radius), surface-2 bg
  - 15px font, min-height 40px, max-height 120px
  - Placeholder: "Write something meaningful..."
- Send button: 40px circle, accent bg, white arrow icon
  - Active: scale 0.93

## Bottom Tab Bar

- 60px height, surface-1 bg, border-top faint
- 5 tabs: Discover (compass), Matches (heart), Messages (chat), Activity (pulse), Profile (user)
- Active: accent color, Messages tab active
- Each: 22px icon + 11px/500 label, flex-column, 2px gap
- Messages badge: pink bg, white 9px/700 count "3", 16px pill

## Atmosphere

Warm Luxury (Atmosphere 3): purple accent (#a78bfa dark / #7c3aed light), stone warm tones.
Dark default. Light toggle available. Matches discover.html design system.

## Key Differentiations from Tinder/Hinge/Bumble

1. **Rounded-rectangle avatars** (56x64px) instead of circular — shows more of the person
2. **Compatibility score chips** inline on every conversation — always visible context
3. **Intent-stage grouping** (New / Getting to Know / Planning to Meet) instead of recency-only
4. **Connection Card** expandable in thread header — domain scores + alignment items
5. **Depth Prompts** — AI-driven conversation suggestions tied to matching domains
6. **Voice notes** with waveform visualization in chat thread
7. **Sent bubble styling** uses accent-tinted alpha (not solid color) for warm luxury feel

## Interactions

- Conversation items: tap to open thread view
- Back button: returns to list view, collapses connection card
- Profile tap in thread header: toggles connection card expand/collapse
- Stage filter tabs: filters conversation list by intent stage
- Search input: filters by name/content
- Message input: auto-resize textarea, send on button tap
- Theme toggle: swaps dark/light via data-theme attribute
- All interactive elements: focus-visible double-ring pattern
- Depth prompt: dismiss button removes from view
