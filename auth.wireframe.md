# MOTO Auth Wireframe Spec

Mobile-first (430px max-width), dark default, 8 views toggled via JS.

## Layout

```
+--[430px shell]-----------------------------+
|                                             |
|  View 1: WELCOME (full-screen landing)      |
|  View 2: SIGN UP (form)                     |
|  View 3: SIGN UP ERROR (form + validation)  |
|  View 4: SIGN UP SUCCESS (confirmation)     |
|  View 5: SIGN IN (form)                     |
|  View 6: SIGN IN ERROR (form + error banner)|
|  View 7: FORGOT PASSWORD (form)             |
|  View 8: FORGOT SUCCESS (confirmation)      |
|                                             |
+---------------------------------------------+
```

One view visible at a time. JS `showView(name)` hides all, shows target.

## Welcome Screen

```
+---------------------------------------+
|                          [theme-toggle]|
|                                        |
|          ( O   O )                     |
|       interlocking circles             |
|                                        |
|            M O T O                     |
|      VALUES-ALIGNED DATING             |
|                                        |
|      Not more choice.                  |
|      Better alignment.    (serif h1)   |
|                                        |
|  A dating platform built around shared |
|  values, life timelines, and the       |
|  vision to build something that lasts. |
|                                        |
|  [====== Begin Your Story ======] 56px |
|                                        |
|   Already have an account? Sign in     |
|                                        |
|   Terms of Service · Privacy Policy    |
+---------------------------------------+
```

- Logo: 56px, font-weight 700, gradient text (accent -> #c4b5fd)
- Wordmark: 13px uppercase, letter-spacing 0.2em, text-tertiary
- Headline: Cormorant Garamond serif, 34px, weight 500
- Thesis: 16px, text-secondary, max-width 320px, centered
- Background: abstract constellation (radial gradients, dot pattern SVG)
- No stock photos, no couple imagery

## Form Header

```
+---------------------------------------+
| [<- back]              [theme-toggle] |
+---------------------------------------+
```

- Back button: 40px square, rounded-[10px], ghost style
- Theme toggle: 36px square, same as welcome

## Sign Up Form

```
+---------------------------------------+
| [<-]                     [sun/moon]   |
|                                        |
| Create your account          28px/600  |
| This is the beginning of...  16px/sec  |
|                                        |
| [G  Continue with Google    ] 52px     |
| [   Continue with Apple     ] 52px     |
|                                        |
| ---------- or continue ----------      |
|                                        |
| First name        Last name            |
| [Sarah         ]  [Mitchell       ]    |
|                                        |
| Email address                          |
| [sarah@example.com              ]      |
|                                        |
| Password                               |
| [At least 8 characters      ] [eye]   |
| [==][==][  ][  ] Medium strength       |
|                                        |
| Date of birth                          |
| [Month v] [Day v] [Year v]            |
| You must be 18 or older                |
|                                        |
| [======= Create Account =======]      |
|                                        |
| By creating an account, you agree...   |
|                                        |
| Already have an account? Sign in       |
+---------------------------------------+
```

## Input Specs

| Element | Height | Radius | Font |
|---------|--------|--------|------|
| Text input | 48px | 10px | 16px/400 |
| Social btn | 52px | 12px | 15px/500 |
| Submit btn | 52px | 12px | 16px/600 |
| Begin btn | 56px | 12px | 16px/600 |

## Password Strength

4 bars, 3px height, 4px gap. Colors:

| Level | Bar color | Label |
|-------|-----------|-------|
| Weak | --negative (#ef4444) | "Too weak" |
| Medium | --warning (#d97706) | "Medium strength" |
| Strong | --positive (#16a34a) | "Strong password" |

## Validation Errors

- Input border: --negative
- Focus ring: 0 0 0 3px --negative-muted
- Error text: 13px, --negative, flex with X-circle icon (14px)
- Form-level error: card with --negative-muted bg, 1px border rgba(239,68,68,0.2), rounded-[10px], alert icon + title + description

## Success States

```
+---------------------------------------+
|                          [theme-toggle]|
|                                        |
|            ( checkmark )               |
|         64px circle, green bg          |
|                                        |
|        Check your email                |
|                                        |
|    We sent a verification link to      |
|    sarah.mitchell@gmail.com            |
|                                        |
|    Click the link in the email to...   |
|                                        |
|    [======= Resend Email ========]     |
|                                        |
|    Wrong email? Go back                |
+---------------------------------------+
```

- Icon container: 64px circle, --positive-muted bg
- Checkmark: 28px, stroke-width 2.5, --positive color
- Email: --text-primary, font-weight 500

## Forgot Password

Form with single email field + "Send Reset Link" CTA. Below: info card with 3 numbered steps (check inbox, click link valid 60 min, create new password). Step numbers: 24px circles, --accent-muted bg, --accent text, 12px/600 tabular-nums.

## Theme Toggle

Sun icon in dark mode, moon icon in light. Located in header right-side on every view. 36px tap target, rounded-[8px], ghost hover.

## Colors (Warm Luxury)

| Token | Dark | Light |
|-------|------|-------|
| bg-page | #0c0a09 | #faf9f7 |
| surface-1 | #141210 | #ffffff |
| surface-2 | #1c1a17 | #f5f4f1 |
| accent | #a78bfa | #7c3aed |
| accent-hover | #8b5cf6 | #6d28d9 |

## Typography

- Headlines: Inter 600, -0.02em to -0.03em
- Welcome headline: Cormorant Garamond 500, 34px (serif differentiator)
- Logo: Inter 700, 56px, gradient fill
- Body: Inter 400, 16px
- Labels: Inter 500, 14px
- Hints: Inter 400, 13px, text-tertiary
- Errors: Inter 400, 13px, --negative

## Interactions

- View switch: JS toggles .active class (display:flex vs none)
- Password toggle: switches input type text/password, swaps eye/eye-off icon
- Notification bar: slides down from top, auto-hides after 3s
- All buttons: scale(0.98) on :active
- All focusable: double-ring focus-visible pattern
- Reduced motion: @media query kills all animation/transition durations

## Navigation Bar (Design Review Only)

Fixed bottom bar with 8 buttons for jumping between views. Not part of production UI.
