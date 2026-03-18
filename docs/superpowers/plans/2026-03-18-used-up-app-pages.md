# Used Up App Pages Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a `used-up/` app landing page and `used-up/privacy-policy/` subpage to the vivianlobo.com GitHub Pages site.

**Architecture:** Two self-contained HTML files in a new `used-up/` directory. No build tools, no frameworks, no JS. Each page is a complete standalone HTML document using Roboto Mono from Google Fonts and the site's existing mono-dark colour palette (`#000` bg, `#6dcc9e` accent). Zero changes to any existing files.

**Tech Stack:** Plain HTML5 + CSS (inline `<style>` in each file), GitHub Pages (static hosting), Google Fonts CDN

---

## Files to Create

| File | Purpose |
|------|---------|
| `.gitignore` | Ignore `.DS_Store` and `.superpowers/` |
| `used-up/index.html` | App landing page |
| `used-up/privacy-policy/index.html` | Privacy policy page |
| `used-up/screenshots/home.png` | Home screen screenshot |
| `used-up/screenshots/details.png` | Statistics screenshot |
| `used-up/screenshots/create.png` | Create tracker screenshot |

**No existing files are modified.**

---

## Task 1: Create feature branch and .gitignore

**Files:**
- Create: `.gitignore` *(housekeeping — no .gitignore currently exists in the repo; `.superpowers/` and `.DS_Store` are present and would otherwise be tracked)*

- [ ] **Step 1: Create the feature branch**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git checkout -b feature/used-up-pages
```

Expected: `Switched to a new branch 'feature/used-up-pages'`

- [ ] **Step 2: Create .gitignore**

Create file `.gitignore` with this content:

```
.DS_Store
.superpowers/
```

- [ ] **Step 3: Verify .DS_Store is now ignored**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git check-ignore -v .DS_Store
```

Expected: `.gitignore:1:.DS_Store`

- [ ] **Step 4: Commit**

```bash
git add .gitignore
git commit -m "chore: add .gitignore"
```

---

## Task 2: Add screenshots

**Files:**
- Create: `used-up/screenshots/home.png`
- Create: `used-up/screenshots/details.png`
- Create: `used-up/screenshots/create.png`

- [ ] **Step 1: Create the directory and copy screenshots**

```bash
mkdir -p /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/screenshots

cp /Users/vivian/Desktop/Used_Up_Homepage.png \
   /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/screenshots/home.png

cp /Users/vivian/Desktop/Used_Up_Details.png \
   /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/screenshots/details.png

cp /Users/vivian/Desktop/Used_Up_Create.png \
   /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/screenshots/create.png
```

- [ ] **Step 2: Verify all three files exist**

```bash
ls -lh /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/screenshots/
```

Expected: three `.png` files listed with non-zero sizes.

- [ ] **Step 3: Commit**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git add used-up/screenshots/
git commit -m "feat: add Used Up app screenshots"
```

---

## Task 3: Create the landing page

**Files:**
- Create: `used-up/index.html`

- [ ] **Step 1: Create the file**

Create `used-up/index.html` with the following complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Used Up — Track What Matters</title>
  <meta name="description" content="Used Up is a mobile app for tracking prepaid resources and usage goals. Always know what's left.">
  <link rel="canonical" href="https://vivianlobo.com/used-up/">
  <meta property="og:title" content="Used Up — Track What Matters">
  <meta property="og:description" content="A mobile app for tracking prepaid resources and usage goals. Always know what's left.">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://vivianlobo.com/used-up/">
  <meta property="og:image" content="https://vivianlobo.com/used-up/screenshots/home.png">
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: #000;
      color: #585656;
      font-family: 'Roboto Mono', monospace;
      -webkit-font-smoothing: antialiased;
    }

    a { text-decoration: none; }

    /* ── nav ── */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 48px;
      border-bottom: 1px solid #111;
    }
    .nav-back { font-size: 11px; color: #585656; letter-spacing: 1px; }
    .nav-back:hover { color: #6dcc9e; }
    .nav-title { font-size: 11px; color: #6dcc9e; letter-spacing: 3px; }

    /* ── hero ── */
    .hero {
      text-align: center;
      padding: 72px 24px 56px;
      border-bottom: 1px solid #111;
    }
    .hero-name {
      font-size: clamp(36px, 6vw, 64px);
      color: #fff;
      letter-spacing: -1px;
      font-weight: 700;
    }
    .hero-tagline {
      margin-top: 16px;
      font-size: 13px;
      color: #585656;
      letter-spacing: 2px;
      line-height: 1.8;
    }
    .hero-badge {
      display: inline-block;
      margin-top: 32px;
      border: 1px solid #333;
      border-radius: 3px;
      padding: 12px 24px;
      font-size: 11px;
      color: #444;
      letter-spacing: 2px;
    }
    .hero-badge-sub {
      margin-top: 10px;
      font-size: 9px;
      color: #333;
      letter-spacing: 1px;
    }

    /* ── screenshots ── */
    .screenshots {
      display: flex;
      justify-content: center;
      align-items: flex-start;
      gap: 24px;
      padding: 56px 48px;
      border-bottom: 1px solid #111;
    }
    .screenshots img {
      width: 28%;
      max-width: 220px;
      border-radius: 16px;
      display: block;
      box-shadow: 0 8px 40px rgba(0,0,0,0.6);
    }

    /* ── features ── */
    .features {
      padding: 56px 48px;
      border-bottom: 1px solid #111;
    }
    .features-label {
      font-size: 9px;
      color: #333;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 28px;
      text-align: center;
    }
    .features-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 16px;
      max-width: 720px;
      margin: 0 auto;
    }
    .feature-item {
      border: 1px solid #1a1a1a;
      border-radius: 3px;
      padding: 16px;
    }
    .feature-title {
      font-size: 11px;
      color: #6dcc9e;
      letter-spacing: 1px;
      margin-bottom: 6px;
    }
    .feature-desc {
      font-size: 10px;
      color: #484545;
      line-height: 1.6;
    }

    /* ── footer ── */
    footer {
      padding: 24px 48px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 9px;
      color: #333;
      letter-spacing: 1px;
    }
    footer a { color: #585656; }
    footer a:hover { color: #6dcc9e; }

    /* ── responsive ── */
    @media (max-width: 600px) {
      nav { padding: 16px 20px; }
      .hero { padding: 48px 20px 40px; }
      .screenshots {
        flex-direction: column;
        align-items: center;
        padding: 40px 20px;
      }
      .screenshots img { width: 80%; max-width: 300px; }
      .features { padding: 40px 20px; }
      footer { flex-direction: column; gap: 12px; text-align: center; padding: 20px; }
    }
  </style>
</head>
<body>

  <nav>
    <a class="nav-back" href="https://vivianlobo.com">← vivianlobo.com</a>
    <span class="nav-title">used-up</span>
  </nav>

  <section class="hero">
    <div class="hero-name">used-up</div>
    <div class="hero-tagline">
      track what matters.<br>
      always know what's left.
    </div>
    <div>
      <div class="hero-badge">coming soon on android &amp; ios</div>
      <div class="hero-badge-sub">free · no account required</div>
    </div>
  </section>

  <section class="screenshots">
    <img src="screenshots/home.png" alt="Home screen showing active trackers">
    <img src="screenshots/details.png" alt="Tracker statistics and usage history">
    <img src="screenshots/create.png" alt="Create a new tracker">
  </section>

  <section class="features">
    <div class="features-label">what it does</div>
    <div class="features-grid">
      <div class="feature-item">
        <div class="feature-title">countdown</div>
        <div class="feature-desc">start with a total and track what you use — pills, credits, sessions, data</div>
      </div>
      <div class="feature-item">
        <div class="feature-title">accumulate</div>
        <div class="feature-desc">build up entries toward a goal — gym sessions, savings, dog-sitting days</div>
      </div>
      <div class="feature-item">
        <div class="feature-title">cost tracking</div>
        <div class="feature-desc">attach a cost per unit and see exactly what you owe or have spent</div>
      </div>
      <div class="feature-item">
        <div class="feature-title">past dates</div>
        <div class="feature-desc">add entries for historical dates — backfill anything you missed</div>
      </div>
      <div class="feature-item">
        <div class="feature-title">private &amp; offline</div>
        <div class="feature-desc">everything stays on your device — no account, no cloud, no tracking</div>
      </div>
      <div class="feature-item">
        <div class="feature-title">reminders</div>
        <div class="feature-desc">weekly notifications so you never forget to log your usage</div>
      </div>
    </div>
  </section>

  <footer>
    <span>© vivian lobo</span>
    <a href="./privacy-policy/">privacy policy</a>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Open the file in a browser and verify it looks correct**

```bash
open /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/index.html
```

Check:
- Black background, mono font, green accent
- Three screenshots appear in a row
- Six feature cards render in a grid
- "← vivianlobo.com" nav link visible top-left
- "privacy policy" link in footer bottom-right
- Resize the browser window narrow — screenshots should stack vertically at ≤600px

- [ ] **Step 3: Commit**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git add used-up/index.html
git commit -m "feat: add Used Up app landing page"
```

---

## Task 4: Create the privacy policy page

**Files:**
- Create: `used-up/privacy-policy/index.html`

- [ ] **Step 1: Create the directory and file**

```bash
mkdir -p /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/privacy-policy
```

Create `used-up/privacy-policy/index.html` with the following complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Privacy Policy — Used Up</title>
  <meta name="description" content="Privacy policy for the Used Up mobile app.">
  <link rel="canonical" href="https://vivianlobo.com/used-up/privacy-policy/">
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: #000;
      color: #585656;
      font-family: 'Roboto Mono', monospace;
      -webkit-font-smoothing: antialiased;
    }

    a { text-decoration: none; }

    /* ── nav ── */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 48px;
      border-bottom: 1px solid #111;
    }
    .nav-back { font-size: 11px; color: #585656; letter-spacing: 1px; }
    .nav-back:hover { color: #6dcc9e; }
    .nav-label { font-size: 11px; color: #333; letter-spacing: 2px; }

    /* ── content ── */
    .content {
      max-width: 640px;
      margin: 0 auto;
      padding: 64px 24px 80px;
    }

    h1 {
      font-size: 24px;
      color: #fff;
      font-weight: 700;
      letter-spacing: -0.5px;
      margin-bottom: 8px;
    }

    .meta {
      font-size: 10px;
      color: #333;
      letter-spacing: 2px;
      margin-bottom: 48px;
    }

    h2 {
      font-size: 11px;
      color: #6dcc9e;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin: 32px 0 10px;
    }

    p {
      font-size: 13px;
      color: #585656;
      line-height: 1.8;
    }

    code {
      font-family: 'Roboto Mono', monospace;
      font-size: 12px;
      color: #484545;
    }

    /* ── footer ── */
    footer {
      padding: 24px 48px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 9px;
      color: #333;
      letter-spacing: 1px;
    }
    footer a { color: #585656; }
    footer a:hover { color: #6dcc9e; }

    @media (max-width: 600px) {
      nav { padding: 16px 20px; }
      .content { padding: 40px 20px 60px; }
      footer { flex-direction: column; gap: 12px; text-align: center; padding: 20px; }
    }
  </style>
</head>
<body>

  <nav>
    <a class="nav-back" href="../">← used-up</a>
    <span class="nav-label">privacy policy</span>
  </nav>

  <div class="content">
    <h1>privacy policy</h1>
    <div class="meta">used-up · last updated march 2026</div>

    <h2>1. Overview</h2>
    <p>Used Up is a mobile application for tracking prepaid resources and usage goals. This policy explains what data the app handles.</p>

    <h2>2. Data stored on your device</h2>
    <p>All tracker data (names, entries, settings) is stored locally in a SQLite database on your device. This data never leaves your device and is not accessible to us.</p>

    <h2>3. Diagnostics</h2>
    <p>The app sends anonymous diagnostic data (crash reports and performance metrics) to a private server operated by the developer (<code>collector.vivianlobo.dev</code>). This data is used solely to improve app stability. It is not shared with any third party.</p>

    <h2>4. No account required</h2>
    <p>Used Up does not require you to create an account. No personal information (name, email, location) is collected.</p>

    <h2>5. Third-party services</h2>
    <p>This website (vivianlobo.com/used-up) loads fonts from Google Fonts, which means your browser makes a request to Google's servers when you visit this page. The Used Up app itself does not use Google Fonts and makes no requests to Google.</p>

    <h2>6. Data deletion</h2>
    <p>All tracker data is stored locally on your device. You can delete it at any time by clearing the app's data in your device settings, or by uninstalling the app. No data is held on any server that would need to be deleted remotely.</p>

    <h2>7. Contact</h2>
    <p>Questions? Email <code>vivian@vivianlobo.com</code>.</p>
  </div>

  <footer>
    <a href="../">← used-up</a>
    <span>© vivian lobo</span>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Open the file in a browser and verify**

```bash
open /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/privacy-policy/index.html
```

Check:
- Black background, mono font
- "← used-up" nav link top-left
- All 7 policy sections render with green headings
- Section numbers and text are legible
- "← used-up" in footer links back to the app page

- [ ] **Step 3: Verify the privacy policy link from the landing page works**

```bash
open /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io/used-up/index.html
```

Click "privacy policy" in the footer — it should navigate to the privacy policy page. (Browser file:// navigation respects relative links.)

- [ ] **Step 4: Commit**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git add used-up/privacy-policy/
git commit -m "feat: add Used Up privacy policy page"
```

---

## Task 5: Push and create pull request

- [ ] **Step 1: Push the feature branch**

```bash
cd /Users/vivian/Downloads/dev/MyWebsites/vnl.github.io
git push -u origin feature/used-up-pages
```

- [ ] **Step 2: Create a pull request**

```bash
gh pr create --title "feat: add Used Up app landing page and privacy policy" --body "$(cat <<'EOF'
Adds vivianlobo.com/used-up/ and vivianlobo.com/used-up/privacy-policy/

## Changes
- New directory `used-up/` — completely isolated, zero changes to existing files
- Landing page with hero, 3 app screenshots, 6 feature cards
- Privacy policy page (required for Google Play Store submission)
- .gitignore added

## Preview
Open `used-up/index.html` locally to preview before merging.
EOF
)" --base master
```

- [ ] **Step 3: Merge the PR**

Review the PR on GitHub, then merge it.

- [ ] **Step 4: Verify the live pages**

GitHub Pages deploys ~60–90 seconds after merge. Check deployment status first:

```bash
gh run list --repo vnl/vnl.github.io --limit 1
```

Wait until the status shows `completed` / `success`, then open:

- `https://vivianlobo.com/used-up/` — landing page
- `https://vivianlobo.com/used-up/privacy-policy/` — privacy policy

Check both pages render correctly on the live site.

- [ ] **Step 5: Copy the privacy policy URL for Google Play Console**

The URL to submit in Play Console → "App content" → "Privacy policy" is:

```
https://vivianlobo.com/used-up/privacy-policy/
```
