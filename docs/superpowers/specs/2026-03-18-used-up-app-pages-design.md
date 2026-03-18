# Used Up App Pages — Design Spec

**Goal:** Add two standalone pages to vivianlobo.com for the Used Up app: a landing page and a privacy policy subpage.

**Constraint:** Zero changes to any existing homepage files. The new pages are completely isolated.

---

## URLs

| Page | URL |
|------|-----|
| App landing page | `vivianlobo.com/used-up/` |
| Privacy policy | `vivianlobo.com/used-up/privacy-policy/` |

---

## Visual Style

Inherits the existing site's aesthetic — no new design system introduced:

- **Background:** `#000000`
- **Primary text:** `#585656`
- **Accent / links:** `#6dcc9e`
- **Font:** `Roboto Mono` (Google Fonts, same as homepage)
- **Border colour:** `#111` / `#1a1a1a`
- No animations, no JS dependencies

The pages feel like they belong to vivianlobo.com without sharing any code with the homepage's animation framework.

---

## File Structure

```
used-up/
├── index.html              ← landing page
├── privacy-policy/
│   └── index.html          ← privacy policy page
└── screenshots/
    ├── home.png            ← home screen (active trackers)
    ├── details.png         ← tracker statistics view
    └── create.png          ← create tracker screen
```

Screenshots are committed into the repo so the page is fully self-contained.

---

## Landing Page (`used-up/index.html`)

### Sections (top to bottom)

#### 1. Nav bar
- Left: `← vivianlobo.com` link (href `../` or `https://vivianlobo.com`) — colour `#585656`, hover `#6dcc9e`
- Right: `used-up` in `#6dcc9e`, letter-spacing 3px
- Bottom border: `1px solid #111`
- Padding: `20px 48px`

#### 2. Hero
- App name: `used-up` — large (clamp 36–64px), `#fff`, bold, tight letter-spacing
- Tagline: `track what matters. always know what's left.` — `#585656`, 13px, letter-spacing 2px
- Badge: `coming soon on android & ios` — bordered box `1px solid #333`, colour `#444`
- Sub-badge: `free · no account required` — `#333`, 9px
- Text-align: center
- Bottom border: `1px solid #111`

#### 3. Screenshots
- Three phone screenshots in a row, centred, `gap: 24px`
- Each image: `width: 28%`, `max-width: 220px`, `border-radius: 16px`, `box-shadow: 0 8px 40px rgba(0,0,0,0.6)`
- Order: Home screen → Statistics → Create tracker
- On mobile (≤600px): stack vertically, `width: 80%`
- Alt text: `"Home screen showing active trackers"`, `"Tracker statistics and usage history"`, `"Create a new tracker"`

#### 4. Features grid
- Section label: `what it does` — 9px, `#333`, letter-spacing 3px, centred
- 6 feature cards in a responsive CSS grid (`auto-fit, minmax(180px, 1fr)`), max-width 720px, centred
- Each card: `border: 1px solid #1a1a1a`, `border-radius: 3px`, `padding: 16px`
  - Title: 11px, `#6dcc9e`, letter-spacing 1px
  - Description: 10px, `#484545`, line-height 1.6

| Feature title | Description |
|---------------|-------------|
| countdown | start with a total and track what you use — pills, credits, sessions, data |
| accumulate | build up entries toward a goal — gym sessions, savings, dog-sitting days |
| cost tracking | attach a cost per unit and see exactly what you owe or have spent |
| past dates | add entries for historical dates — backfill anything you missed |
| private & offline | everything stays on your device — no account, no cloud, no tracking |
| reminders | weekly notifications so you never forget to log your usage |

#### 5. Footer
- Left: `© vivian lobo` — `#333`
- Right: `privacy policy` link → `./privacy-policy/` — `#585656`, hover `#6dcc9e`
- `padding: 24px 48px`
- The `<section class="features">` carries `border-bottom: 1px solid #111`; the `<footer>` has no top border

### Meta / head

Both pages must include the full boilerplate in this order:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Used Up — Track What Matters</title>
  <meta name="description" content="Used Up is a mobile app for tracking prepaid resources and usage goals. Always know what's left.">
  <link rel="canonical" href="https://vivianlobo.com/used-up/">
  <!-- OG tags (landing page only) -->
  <meta property="og:title" content="Used Up — Track What Matters">
  <meta property="og:description" content="A mobile app for tracking prepaid resources and usage goals. Always know what's left.">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://vivianlobo.com/used-up/">
  <meta property="og:image" content="https://vivianlobo.com/used-up/screenshots/home.png">
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500;700&display=swap" rel="stylesheet">
</head>
```

Privacy policy page uses the same boilerplate with `<title>Privacy Policy — Used Up</title>`, updated canonical, no OG tags.

---

## Privacy Policy Page (`used-up/privacy-policy/index.html`)

### Structure
- Nav: `← used-up` (href `../`) on left — links back to `vivianlobo.com/used-up/`; `privacy policy` label on right
- Heading: `privacy policy` — 24px, `#fff`
- Sub: `used-up · last updated march 2026`
- Body text: `#585656`, 13px, `line-height: 1.8`, max-width 640px, margin auto
- Footer: `← used-up` (href `../`) + `© vivian lobo` — note: this links back to the app page, not the main site root

### Policy content

**1. Overview**
Used Up is a mobile application for tracking prepaid resources and usage goals. This policy explains what data the app handles.

**2. Data stored on your device**
All tracker data (names, entries, settings) is stored locally in a SQLite database on your device. This data never leaves your device and is not accessible to us.

**3. Diagnostics**
The app sends anonymous diagnostic data (crash reports and performance metrics) to a private server operated by the developer (`collector.vivianlobo.dev`). This data is used solely to improve app stability. It is not shared with any third party.

**4. No account required**
Used Up does not require you to create an account. No personal information (name, email, location) is collected.

**5. Third-party services**
This website (vivianlobo.com/used-up) loads fonts from Google Fonts, which means your browser makes a request to Google's servers when you visit this page. The Used Up app itself does not use Google Fonts and makes no requests to Google.

**6. Data deletion**
All tracker data is stored locally on your device. You can delete it at any time by clearing the app's data in your device settings, or by uninstalling the app. No data is held on any server that would need to be deleted remotely.

**7. Contact**
Questions? Email `vivian@vivianlobo.com`.

---

## What changes in the repo

| Action | File |
|--------|------|
| Create | `used-up/index.html` |
| Create | `used-up/privacy-policy/index.html` |
| Create | `used-up/screenshots/home.png` |
| Create | `used-up/screenshots/details.png` |
| Create | `used-up/screenshots/create.png` |
| No changes | Everything else (homepage, CSS, JS, img) |

---

## Future updates (not in scope now)

- Replace "coming soon" badge with real Google Play / App Store badges + links once the app is live
- Add a tablet/iPad screenshot section if iOS version ships
