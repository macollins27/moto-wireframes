# MOTO Settings — Wireframe Spec

Mobile-first settings page. 430px max-width centered. Sub-page off Profile.

## Layout

```
+----------------------------------+
| [<-Back]   Settings   [sun/moon] |  <- 56px sticky header
+----------------------------------+
| Account | Matching | Notif | ... |  <- Horizontal scrollable tabs
+----------------------------------+
|                                  |
|   (scrollable content area)      |
|                                  |
|   Section groups with            |
|   icon + label headers           |
|   Toggle rows                    |
|   Chevron drill-down rows        |
|   Slider controls                |
|   Chip selection groups          |
|                                  |
+----------------------------------+
```

## Shell

- **Container**: max-width 430px, centered, min-height 100vh, left/right border-faint borders
- **Header**: 56px height, sticky top, surface-1 bg, border-bottom faint
  - Left: back arrow button (36x36, rounded-lg, ghost)
  - Center: "Settings" label (16px/600)
  - Right: theme toggle (36x36)
- **Tabs**: horizontal scrollable row, surface-1 bg, border-bottom faint
  - 5 tabs: Account, Matching, Notifications, Privacy, Plan
  - Active: accent color text + 2px bottom border
  - Inactive: text-tertiary, no border
  - Font: 13px/500, no-wrap, 12px 14px padding
- **Content**: flex-1, overflow-y auto, padding-bottom 40px

## Atmosphere — MOTO Warm Intimacy (Custom)

Based on Warm Luxury (Atmosphere 3), customized with amber/gold accent.

| Token | Dark | Light |
|---|---|---|
| bg-page | #0d0b09 | #f9f6f2 |
| surface-1 | #161310 | #ffffff |
| surface-2 | #1e1a16 | #f3efe9 |
| accent | #d4a54a | #b8862e |
| text-primary | #ede9e3 | #1c1812 |

Additional tokens: `--danger`, `--success`, `--premium-gradient`, `--premium-bg`.

## Section Pattern

Every section follows this structure:

```
+-------------------------------------+
| [icon]  SECTION TITLE               |  <- 13px/600 uppercase, accent color
|         Description text             |  <- 14px, text-tertiary, 28px left pad
+-------------------------------------+
| Setting label              [toggle] |  <- 14px row, border-bottom faint
| Hint text                           |
+-------------------------------------+
| Setting label              [>]      |  <- Chevron drill-down row
| Current value                       |
+-------------------------------------+
```

- Section icon: 18px, accent color
- Section title: 13px/600, uppercase, 0.06em letter-spacing, accent color
- Section description: 14px, text-tertiary, left-padded 28px
- Rows: 14px vertical padding, border-bottom faint between rows

## Tab: Account

1. **Avatar section** — centered 72px circle (accent border), name 18px/600, email 13px/text-tertiary, member-since 12px/text-disabled
2. **Profile completeness** — card with progress bar (6px height, accent fill), percentage 13px/600 accent, hint text
3. **Personal Information** — 4 chevron rows: display name, DOB (with age), gender, height
4. **Security & Login** — email (verified badge), phone (verified badge), password, photo verification status
5. **Connected Accounts** — 3 service rows (Spotify connected, Instagram not, Pinterest connected) each with 36px icon box, name, status, link/unlink button
6. **Danger Zone** — red-themed section at bottom with pause and delete buttons

## Tab: Matching

1. **Discovery** — distance slider (5-100mi), age range slider, gender chip group (Men/Women/Non-binary/Everyone), location chevron, long-term location goal chevron
2. **Intent Filters** — marriage readiness chips (<3yr/3-5/5-10/Open), family timeline chips (Within 3yr/3-5/Someday/No children), children count chevron, education philosophy chevron
3. **Compatibility Weights** — 7 domain bars showing algorithm weights (Family 25%, Geography 15%, Spiritual 15%, Lifestyle 15%, Physical 10%, Political 10%, Social 10%)
4. **Non-Negotiables** — 4 toggle rows as hard dealbreaker filters

## Tab: Notifications

1. **Push Notifications** — 5 toggles: new matches, messages, high compatibility alerts, profile views, weekly report
2. **Email** — 4 toggles: monthly digest, community events, product updates, pre-marital resources
3. **Quiet Hours** — enable toggle + start/end time display rows

## Tab: Privacy

1. **Profile Visibility** — 4 toggles: active, show distance, show active status, incognito (premium badge)
2. **Content Privacy** — 5 chevron rows controlling visibility per content type (mood board, literary, values, family, Spotify) with Public/Matches-only labels
3. **Safety** — blocked profiles (count), hidden profiles (count), block contacts toggle, date check-in toggle
4. **Data & Privacy** — download data, privacy policy, terms links

## Tab: Plan

1. **Premium card** — accent-tinted bg, gradient top border, "MOTO Devotion" badge, price $29.99/mo, renewal date, manage button
2. **Plan Features** — 6 feature rows with green "Active" checkmark badges
3. **Billing** — payment method, next/last charge, billing history link, update payment link
4. **Manage** — change plan (secondary) + cancel subscription (danger) buttons

## Component Specs

### Toggle Switch
- 44x24px, rounded-full (12px radius)
- Off: border-strong bg, white 18px circle at left:3px
- On: accent bg, circle translated 20px right
- Transition: 200ms ease-out

### Slider (Range Input)
- 4px track height, border-default bg, rounded
- 22px thumb, accent bg, 2px surface-1 border, shadow

### Chip
- 32px height, 16px radius (pill), 14px horizontal padding
- Default: transparent bg, border-default, text-secondary
- Active: accent-muted bg, accent border, accent text

### Chevron Row
- Full-bleed (negative margin to section padding), hover surface-hover
- Right side: optional value text (14px/text-tertiary) + 16px chevron icon

### Premium Card
- accent-soft bg, accent border at 15% opacity
- 2px top gradient bar (premium-gradient)
- Premium badge: 11px/600 uppercase, accent-muted bg, accent text

## Badge Color Map

| State | Text | Background |
|---|---|---|
| Verified/Active | #4aba7a | rgba(74,186,122,0.10) |
| Premium | #8b5cf6 | rgba(139,92,246,0.08) |
| Public | success color | — |
| Matches only | accent color | — |

## Interactions

- Tabs switch visible panel; danger zone visible only on Account tab
- Toggles click to flip active/inactive state
- Chips are single-select within their group
- Chevron rows navigate to drill-down sub-pages (not implemented in wireframe)
- Sliders adjust value in real-time
- Theme toggle swaps dark/light
