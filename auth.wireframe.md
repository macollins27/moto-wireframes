# MOTO Auth Wireframe Spec

Composition: **Step Wizard (D)** — full-page centered, no shell chrome, 430px max-width.
Atmosphere: **Warm Luxury** — purple accent on warm stone, Cormorant Garamond display + Inter body.

## Layout

```
+------------------------------------------+
| [< Back]                   [Theme Toggle] |  topbar: 72px
|                                          |
|         +------------------+             |
|         |   VIEW CONTENT   |             |  centered, 430px max
|         |   (4 states)     |             |
|         +------------------+             |
|                                          |
| Terms of Service · Privacy Policy        |  legal footer
+------------------------------------------+
```

Background: constellation dots (2px, accent color, pulsing animation) + warm radial glow (purple-to-pink gradient, 6% opacity).

## 4 View States (JS-toggled)

### Welcome (default)

```
        MOTO                    serif 56px/600, 0.12em tracking
   ─── gradient bar ───        48px wide, purple-to-pink

  "The future of dating        serif 22px/400 italic
   is not more choice —        text-secondary
   it is better alignment."

  Values-first thesis text     14px, text-tertiary, 340px max

  [ Create Your Profile ]      pill 52px, accent bg, white text
  [      Sign In        ]      pill 52px, transparent, border

        — or continue with —

  [ Apple icon  Continue with Apple  ]   pill 48px, surface-1 bg
  [ Google icon Continue with Google ]   pill 48px, surface-1 bg
```

### Sign Up

```
     Begin Your Journey         serif 32px/600
     Subtitle text              16px text-secondary

  Email address                 label 14px/500
  [ you@example.com        ]   input 48px, surface-1 bg

  Password                      label 14px/500
  [ At least 8 characters  👁 ] input 48px + toggle

  Confirm password              label 14px/500
  [ Re-enter your password 👁 ] input 48px + toggle
  (error: "Passwords do not match")

  [    Create Account    ]      pill 52px primary

        — or continue with —

  [ Continue with Apple  ]
  [ Continue with Google ]

  Already have an account? Sign in
```

### Sign In

```
     Welcome Back               serif 32px/600
     Subtitle text              16px text-secondary

  Email address
  [ you@example.com        ]

  Password
  [ Enter your password    👁 ]
                    Forgot password?   accent link, right-aligned

  [      Sign In       ]        pill 52px primary

        — or continue with —

  [ Continue with Apple  ]
  [ Continue with Google ]

  Don't have an account? Create one
```

### Forgot Password

Form state:
```
     Reset Your Password        serif 32px/600
     Instruction text           16px text-secondary

  Email address
  [ you@example.com        ]

  [   Send Reset Link    ]      pill 52px primary

       < Back to sign in        accent link with chevron
```

Success state:
```
       ( envelope icon )        64px circle, accent-muted bg
     Check Your Email           serif 28px/600
     We've sent a reset link to
     you@example.com            accent color, 500 weight

     Didn't receive it?
     Check spam or try again    text link

  [   Return to Sign In  ]     pill 52px secondary
```

## Component Specs

### Pill Buttons
- Primary: h-52px, rounded-full (26px), accent bg, white text, 16px font, 500 weight
- Secondary: h-52px, rounded-full (26px), transparent bg, border-default, text-primary
- Social: h-48px, rounded-full (24px), surface-1 bg, border-default, 15px font
- All: scale(0.98) on :active, focus-ring on :focus-visible

### Inputs
- h-48px, rounded-[10px], surface-1 bg, border-default, 16px font
- Focus: accent border + 3px accent-muted glow
- Error: negative border + negative-muted glow + 13px error text below

### Password Toggle
- 40px square, transparent bg, positioned absolute right inside input
- Eye open (default) / eye closed (revealed) SVG swap
- Toggles input type between password/text

### Back Button
- 40px square, rounded-[10px], transparent bg, text-secondary
- Hidden (visibility) on welcome, visible on all other states
- Chevron-left SVG icon

## Typography

| Element | Font | Size | Weight | Color |
|---------|------|------|--------|-------|
| Logo "MOTO" | Cormorant Garamond | 56px | 600 | text-primary |
| Tagline | Cormorant Garamond | 22px | 400 italic | text-secondary |
| Thesis | Inter | 14px | 400 | text-tertiary |
| View headings | Cormorant Garamond | 32px | 600 | text-primary |
| View subtitles | Inter | 16px | 400 | text-secondary |
| Labels | Inter | 14px | 500 | text-secondary |
| Inputs | Inter | 16px | 400 | text-primary |
| Buttons | Inter | 16px | 500 | varies |
| Links | Inter | 14px | 500 | accent |
| Legal | Inter | 12px | 400 | text-disabled |
| Divider text | Inter | 13px | 500 | text-disabled |

## Navigation Flow

```
Welcome ──> Sign Up ──> (submit: onboarding)
   │
   └──> Sign In ──> (submit: app home)
            │
            └──> Forgot Password ──> Success ──> Sign In
```

Back button pops view history stack. All transitions use 350ms fadeSlideIn animation (opacity 0->1, translateY 12px->0).

## Tokens (custom beyond Warm Luxury base)

- `--gradient-warm`: 135deg purple-to-pink gradient at low opacity
- `--accent-pink`: #f472b6 (dark) / #ec4899 (light)
- `--accent-gold`: #fbbf24 (dark) / #d97706 (light)
- `--constellation-opacity`: 0.12 (dark) / 0.08 (light)

## Accessibility

- All interactive elements have focus-visible (double-ring)
- Password toggles have aria-label that updates on state
- Back button has aria-label
- Theme toggle has aria-label
- prefers-reduced-motion disables all animations
- Inputs use autocomplete attributes (email, new-password, current-password)
- Form validation via native HTML required + custom error display
