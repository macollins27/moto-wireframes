# MOTO Auth Wireframe Spec

## Layout

Full-page centered, no shell chrome. Mobile-first, max-width 430px.

```
+----------------------------------+
| [MOTO logo]        [theme toggle]|  <- fixed top bar
|                                  |
|         (ambient glow)           |
|                                  |
|     +------------------------+   |
|     |   [content area]       |   |
|     |   430px max, centered  |   |
|     +------------------------+   |
|                                  |
+----------------------------------+
```

## States (JS view switching)

5 states, switched via `showView(name)`. Each is a `div.auth-view`.

| State | ID | Entry Point |
|---|---|---|
| Welcome | `view-welcome` | Default / back buttons |
| Sign Up | `view-signup` | "Create Account" on welcome |
| Sign In | `view-signin` | "Sign In" on welcome |
| Forgot Password | `view-forgot` | "Forgot password?" on sign in |
| Sign In Error | `view-signin-error` | Demo: "Sign In" button on sign-in |

## Atmosphere: Warm Luxury

- Accent: `#a78bfa` (dark), `#7c3aed` (light)
- Bg: `#0c0a09` (dark), `#faf9f7` (light)
- Surface-1: `#141210` (dark), `#ffffff` (light)
- Stone-toned text hierarchy, 4 levels

## Welcome State

```
        [gradient ring]
         [heart icon]

           MOTO
   (56px, gradient text,
    700 weight, -0.04em)

  "Find someone to build
       a life with"
   (20px, text-secondary)

  [====Create Account====]  <- 52px, gradient bg, white text
  [======Sign In=========]  <- 52px, surface-1, border

  ----  or continue with  ----

  [Apple icon  Continue with Apple ]  <- 48px, bordered
  [Google icon Continue with Google]  <- 48px, bordered

  Terms of Service | Privacy Policy
       (13px, text-disabled)
```

- Logo ring: 120px circle, gradient border, bg-page inner, heart SVG
- Gradient: `linear-gradient(135deg, #a78bfa, #c084fc, #e879f9)`
- Ambient glow: radial-gradient pseudo-elements on shell

## Sign Up State

```
  [<-] Create your account
       Start your journey...

  Email address
  [________________]  <- 48px, 10px radius

  Password
  [________________] [eye]
  [====][====][====][    ]  <- strength bars
  Good -- add a special character

  Confirm password
  [________________] [eye]

  [====Create Account====]

  ----  or continue with  ----

  [Apple]  [Google]  <- side-by-side

  Already have an account? Sign in
```

- Back button: 40px square, 10px radius, border-faint
- Password toggle: eye/eye-off SVG swap
- Strength bars: 4 segments, color-coded (red/amber/green/purple)

## Sign In State

```
  [<-] Welcome back
       Sign in to continue...

  Email address
  [________________]

  Password
  [________________] [eye]
                Forgot password?

  [========Sign In========]

  ----  or continue with  ----

  [Apple]  [Google]

  Don't have an account? Create one
```

- "Forgot password?" right-aligned, 13px, accent color
- Sign In button triggers error demo state

## Forgot Password State

### Form view:
```
  [<-] Reset your password
       We'll send a reset link...

  Email address
  [________________]

  [===Send Reset Link====]

  Remember your password? Back to sign in
```

### Success view:
```
  +----------------------------+
  |                            |
  |     [green circle]         |
  |     [email icon]           |
  |                            |
  |   Check your email         |
  |   We sent a password       |
  |   reset link...            |
  |                            |
  |   Don't see it? Check      |
  |   your spam folder.        |
  |                            |
  |   [Back to Sign In]        |
  +----------------------------+
```

- Success card: surface-1, border-faint, 16px radius, 40px/32px padding
- Icon: 64px circle, success-bg, email SVG in success-text color

## Error State (Sign In variant)

```
  [<-] Welcome back
       Sign in to continue...

  [!] Invalid email or password.
      Please try again.
      (error-bg + error-border + X icon)

  Email address
  [sarah.johnson@gmail.com]  <- red border, error-bg

  Password
  [wrongpassword___] [eye]  <- red border, error-bg
                Forgot password?

  [========Sign In========]

  ----  or continue with  ----
  [Apple]  [Google]
```

- Error banner: error-bg, error-border, 10px radius, X circle icon
- Inputs: `.input-error` class adds red border + red tinted bg

## Component Specs

| Component | Height | Radius | Font |
|---|---|---|---|
| Primary auth button | 52px | 12px | 16px/500 |
| Secondary auth button | 52px | 12px | 16px/500 |
| Social auth button | 48px | 10px | 14px/500 |
| Input field | 48px | 10px | 16px/400 |
| Back button | 40px | 10px | -- |
| Password toggle | 36px | 6px | -- |
| Theme toggle | 36px | 8px | -- |

## Transitions

- View switch: `fadeSlideIn` 300ms (opacity 0->1, translateY 12px->0)
- Button hover: `opacity 150ms ease-out`
- Input focus: `border-color 150ms, box-shadow 150ms`
- Theme: `background-color 200ms, color 200ms`

## Demo Navigation

Fixed bottom pill bar for wireframe review:
`[Welcome] [Sign Up] [Sign In] [Forgot] [Error]`
Active pill: accent-muted bg, accent text. 12px radius, shadow-lg.
