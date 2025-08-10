## HabitDaddy Web Support/Marketing Page Requirements

### Goals
- **Primary**: Provide a compliant App Store Support URL with clear support contact and privacy policy.
- **Secondary**: Lightweight marketing landing to describe HabitDaddy and drive App Store installs.
- **Constraints**: Static site, no backend, fast to ship, host on GitHub Pages, privacy-friendly.

### URLs
- **Marketing/Support landing (index)**: `/` (GitHub Pages root)
- **Privacy policy**: `/privacy.html` (can also be an anchor section if you prefer single-page)
- Optional: `/terms.html` (simple plain-english terms), `/press.html`

If using GitHub Pages “Deploy from branch”, set source to `main` branch and folder to `/docs` and place site files there. Otherwise, serve from root with GitHub Actions.

### Target audience
- iOS users looking to build habits with reminders, a lightweight timer, and clear analytics.

### Key product points to reflect
- **Create tasks/habits** with custom icons.
- **Smart reminders/notifications** to keep you on track. If all tasks are completed, no more notifications are scheduled that day [[memory:5240764]].
- **Timer** with Lock Screen Live Activity and widget support (via `TimerWidget` target).
- **History & Analytics** including a “Consistency Index”.
- **On‑device data**; works offline. No accounts, no ads, no tracking.
- Pleasant **completion sound**.

### Information architecture & sections
- **Header**
  - App icon + name: HabitDaddy
  - Primary CTA: “Download on the App Store” (placeholder link: `https://apps.apple.com/app/idXXXXXXXXX`)
  - Secondary CTA: “Get Support” (anchor to Support section)

- **Hero**
  - Tagline: “Build consistent habits, one day at a time.”
  - Short sub-copy: “Create tasks, get timely reminders, and track your consistency with simple analytics.”
  - Screenshot mockup (use `SupportWebPage/resources/ConsistencyIndex.png` → deployed as `./resources/ConsistencyIndex.png`)

- **Features**
  - Bullets with short one‑liners:
    - Create habits with icons
    - Smart reminders
    - Timer + Lock Screen Live Activity/Widget
    - Consistency Index & history
    - On‑device, private by default

- **How it works**
  - 3 steps: Create a habit → Get reminders → Mark done / Run timer → See progress.

- **Support**
  - Email: `mailto:support@yourdomain.com` (placeholder)
  - GitHub issues: `https://github.com/nambui/habit-daddy-cursor/issues`
  - FAQ (see below)

- **Privacy**
  - Short privacy summary (see “Privacy policy content” below)
  - Link to full policy page `/privacy.html`

- **FAQ**
  - “I’m not receiving notifications”
    - Ensure notifications are allowed in Settings
    - Check Focus/Scheduled Summary settings
    - Open app once after install/update to ensure schedules refresh
    - Notifications are only scheduled for pending due tasks; if everything’s completed you won’t receive more alerts that day [[memory:5240764]]
  - “Is my data synced or shared?”
    - Data is stored on-device only; no external sync or sharing.
  - “Does HabitDaddy track me?”
    - No tracking, no ads, no third-party analytics by default.

- **Footer**
  - Links: Privacy, Support, GitHub Repo
  - Copyright and app version

### Visual/brand assets
- **All assets (source of truth)**: `SupportWebPage/resources/`
- **On deploy**: copy to `docs/resources/` so the site can reference `./resources/...`
- **App icon**: `SupportWebPage/resources/icon.png` (optional; you can use the emoji favicon instead)
- **Screenshots**: e.g., `SupportWebPage/resources/ConsistencyIndex.png`, `TaskList.png`, `Timer.png`

### Copy (baseline)
- Title: HabitDaddy — Build consistent habits
- Meta description: A simple habit tracker with smart reminders, a focused timer, and clear analytics to build consistency. Private by design. iOS only.
- CTAs: “Download on the App Store”, “Get Support”

### SEO/metadata
- Title tag and meta description as above
- Open Graph/Twitter cards using `screenshots/ConsistencyIndex.png`
- Canonical URL set to your GitHub Pages URL
- Optional JSON-LD “SoftwareApplication” schema

Example head tags:
```html
<meta name="description" content="A simple habit tracker with smart reminders, a focused timer, and clear analytics to build consistency. Private by design. iOS only.">
<meta property="og:title" content="HabitDaddy — Build consistent habits">
<meta property="og:description" content="A simple habit tracker with smart reminders, a focused timer, and clear analytics.">
<meta property="og:image" content="https://<your-gh-pages-domain>/resources/ConsistencyIndex.png">
<meta name="twitter:card" content="summary_large_image">
<link rel="canonical" href="https://<your-gh-pages-domain>/">
```

Optional JSON-LD:
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "HabitDaddy",
  "operatingSystem": "iOS",
  "applicationCategory": "LifestyleApplication",
  "offers": { "@type": "Offer", "price": "0", "priceCurrency": "USD" },
  "url": "https://<your-gh-pages-domain>/",
  "image": "https://<your-gh-pages-domain>/screenshots/ConsistencyIndex.png"
}
</script>
```

### Accessibility
- WCAG 2.1 AA contrast; use system-like colors from assets
- Semantic landmarks: header, main, footer, nav
- Keyboard focus states
- Alt text for images/screenshots
- Prefers-reduced-motion support for any animations (optional)

### Performance
- Single static HTML page
- Inline critical CSS, no frameworks
- Defer any non-critical JS (ideally none)

### Privacy policy content (short)
- HabitDaddy does not collect, sell, or share personal data.
- All habit data is stored locally on your device.
- Notifications are scheduled on-device.
- No third-party analytics or tracking.
- Contact: `support@yourdomain.com`

You can host the full text at `/privacy.html` with the above points expanded into short paragraphs.

### Support policy
- Response target: 3 business days via `support@yourdomain.com`
- Public issue tracker: `https://github.com/nambui/habit-daddy-cursor/issues` for bug reports/feature requests
- Include app version, iOS version, and reproduction steps when contacting support.

### Deployment to GitHub Pages
- Easiest: create a `docs/` folder at repo root and put `index.html`, `privacy.html`, assets there. In GitHub: Settings → Pages → Deploy from branch → Branch: `main`, Folder: `/docs`.
- Alternative: use GitHub Actions to deploy from any folder (e.g., `/SupportWebPage/site`).

Before committing, copy resources for deployment:
mkdir -p docs/resources
cp -R SupportWebPage/resources/* docs/resources/

### Deliverables checklist
- index.html with sections above
- privacy.html
- Resources copied to `docs/resources/` (from `SupportWebPage/resources/`)
- App icon image for favicon and header
- OG/Twitter meta tags
- App Store link (replace placeholder ID)
- Support email/links wired

### Minimal index.html skeleton (copy-paste ready)
```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>HabitDaddy — Build consistent habits</title>
<meta name="description" content="A simple habit tracker with smart reminders, a focused timer, and clear analytics to build consistency. Private by design. iOS only.">
<meta property="og:title" content="HabitDaddy — Build consistent habits">
<meta property="og:description" content="A simple habit tracker with smart reminders, a focused timer, and clear analytics.">
<meta property="og:image" content="./resources/ConsistencyIndex.png">
<meta name="twitter:card" content="summary_large_image">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ctext y='.9em' font-size='90'%3E%E2%9C%85%3C/text%3E%3C/svg%3E">
<style>
:root{--bg:#0b0b0f;--text:#e7e7ea;--muted:#a1a1aa;--accent:#8b5cf6}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font:16px/1.6 system-ui,-apple-system,Segoe UI,Roboto}
a{color:var(--accent);text-decoration:none}a:hover{text-decoration:underline}
.header,.section,.footer{max-width:900px;margin:0 auto;padding:24px}
.nav{display:flex;justify-content:space-between;align-items:center}
.cta{display:inline-block;background:var(--accent);color:#fff;padding:12px 16px;border-radius:10px}
.hero{padding:48px 24px;text-align:center}
.hero h1{font-size:40px;margin:0 0 8px}
.grid{display:grid;gap:16px;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))}
.card{background:#14141a;border:1px solid #22232b;border-radius:12px;padding:16px}
img{max-width:100%;height:auto;border-radius:12px}
.small{color:var(--muted);font-size:14px}
hr{border:0;border-top:1px solid #22232b;margin:32px 0}
.app-emoji{display:inline-flex;align-items:center;justify-content:center;width:32px;height:32px;font-size:20px;line-height:1;background:#14141a;border-radius:8px}
</style>
</head>
<body>
<header class="header">
  <div class="nav">
    <div style="display:flex;gap:12px;align-items:center">
      <span class="app-emoji" role="img" aria-label="HabitDaddy icon">✅</span>
      <strong>HabitDaddy</strong>
    </div>
    <nav>
      <a href="#support">Support</a>
      <a class="cta" href="https://apps.apple.com/app/idXXXXXXXXX">Download</a>
    </nav>
  </div>
</header>

<main>
  <section class="hero">
    <h1>Build consistent habits</h1>
    <p class="small">Create tasks, get timely reminders, and track your consistency with simple analytics.</p>
    <p><a class="cta" href="https://apps.apple.com/app/idXXXXXXXXX">Download on the App Store</a></p>
    <img src="./resources/ConsistencyIndex.png" alt="HabitDaddy Consistency Index screenshot">
  </section>

  <section class="section">
    <h2>Why HabitDaddy?</h2>
    <div class="grid">
      <div class="card"><strong>Create habits with icons</strong><br><span class="small">Make tasks visual and clear.</span></div>
      <div class="card"><strong>Smart reminders</strong><br><span class="small">Stay on track without nagging.</span></div>
      <div class="card"><strong>Timer + Live Activity</strong><br><span class="small">Focus with Lock Screen support.</span></div>
      <div class="card"><strong>Consistency Index</strong><br><span class="small">See progress over time.</span></div>
      <div class="card"><strong>Private by design</strong><br><span class="small">On-device data. No tracking.</span></div>
    </div>
  </section>

  <section id="support" class="section">
    <h2>Support</h2>
    <p>Email: <a href="mailto:support@yourdomain.com">support@yourdomain.com</a></p>
    <p>GitHub issues: <a href="https://github.com/nambui/habit-daddy-cursor/issues">Report a bug or request a feature</a></p>
    <h3>FAQ</h3>
    <p><strong>Not receiving notifications?</strong><br>
    Allow notifications in iOS Settings, check Focus/Scheduled Summary, and open the app after install/update. If all tasks are complete, no further notifications are scheduled for that day.</p>
    <p><strong>Is my data synced or shared?</strong><br>Data stays on your device. No external sync or sharing.</p>
  </section>

  <section class="section">
    <h2>Privacy</h2>
    <p>HabitDaddy does not collect, sell, or share personal data. All data is stored on your device, and notifications are scheduled on-device. No third-party analytics.</p>
    <p><a href="./privacy.html">Read the full privacy policy</a></p>
  </section>
</main>

<footer class="footer small">
  <hr>
  <div style="display:flex;justify-content:space-between;gap:16px;flex-wrap:wrap">
    <div>© <span id="y"></span> HabitDaddy</div>
    <div><a href="./privacy.html">Privacy</a> · <a href="#support">Support</a> · <a href="https://github.com/nambui/habit-daddy-cursor">GitHub</a></div>
  </div>
  <script>document.getElementById('y').textContent=new Date().getFullYear()</script>
</footer>
</body>
</html>
```

### Minimal privacy.html skeleton
```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>HabitDaddy Privacy Policy</title></head>
<body style="max-width:800px;margin:40px auto;padding:0 16px;font:16px/1.6 system-ui,-apple-system,Segoe UI,Roboto;color:#222">
<h1>Privacy Policy</h1>
<p>HabitDaddy does not collect, sell, or share personal data. All habit data is stored locally on your device. Notifications are scheduled on-device. We do not use third-party analytics or tracking.</p>
<p>For questions, contact <a href="mailto:support@yourdomain.com">support@yourdomain.com</a>.</p>
<p>Effective date: 2025‑01‑01</p>
</body></html>
```

### Implementation notes
- Place `index.html`, `privacy.html`, `icon.png`, and the `screenshots/` folder into `/docs` and enable GitHub Pages (Settings → Pages → Deploy from branch → `main`/`docs`).
- Replace the App Store link when you have the app ID.
- Replace `support@yourdomain.com` with your real support address or keep only the GitHub Issues link.

### Emoji icon option (no image assets needed)
- Favicon: use an SVG data URL with an emoji.
- Header icon: render an emoji with accessible markup and minimal styling.

Head favicon (replace the `icon.png` line in the skeleton):
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ctext y='.9em' font-size='90'%3E%E2%9C%85%3C/text%3E%3C/svg%3E">

Header icon (replace the <img ...> in the skeleton):
<span class="app-emoji" role="img" aria-label="HabitDaddy icon">✅</span>

Add CSS to the skeleton’s <style>:
.app-emoji{display:inline-flex;align-items:center;justify-content:center;width:32px;height:32px;font-size:20px;line-height:1;background:#14141a;border-radius:8px}

Notes:
- Keep the OG/Twitter image as your screenshot for link previews.
- You can switch the emoji (e.g., 📅, ⏱️, 📈) by changing the character in both places and updating the encoded value in the favicon if desired.

Status: Updated the requirements to reference `SupportWebPage/resources` as the asset source, switched HTML references to `./resources/...`, and added a deploy copy step to `docs/resources`. 

- Updated `Visual/brand assets` to use `SupportWebPage/resources`.
- Adjusted SEO OG image and HTML skeleton to `./resources/...`.
- Added shell commands to copy assets into `docs/resources` for GitHub Pages.
