# downwindtracker-site

Single-page marketing and compliance site for the DownwindTracker iOS + watchOS app, hosted at https://www.downwindtracker.com.

## Stack

Pure static HTML + CSS. No build step, no JavaScript framework, no dependencies. Designed to drop straight onto Netlify (drag-and-drop or Git deploy).

The landing page (`index.html`) is **self-contained** — its styles live in an inline `<style>` block and it carries its own small progressive-enhancement `<script>`. The shared `styles.css` now covers **only** the legal/utility pages (`privacy.html`, `terms.html`, `404.html`), which link to it via `/styles.css`.

## File layout

```
.
├── index.html        # Landing page (inline styles + inline script, self-contained)
├── privacy.html      # Privacy Policy       → links /styles.css
├── terms.html        # Terms of Use / EULA  → links /styles.css
├── 404.html          # Not-found page       → links /styles.css
├── blog/             # "The Bump Log" — writing section (each page links /styles.css)
│   ├── index.html    # Post listing (add one <li class="bumplog-item"> per post)
│   └── claim-gating.html
├── styles.css        # Shared styles for the legal/utility/blog pages
├── logo.svg          # App logo (used in the hero)
├── favicon.svg       # SVG favicon
├── robots.txt
├── sitemap.xml
└── netlify.toml      # Netlify config (404 fallback, security headers, caching)
```

## Deploying to Netlify (drag-and-drop, no Git yet)

1. Zip the contents of this folder (not the folder itself, the contents).
2. Go to https://app.netlify.com/drop and drop the zip.
3. In **Site settings → Domain management**, add `www.downwindtracker.com` and `downwindtracker.com` as custom domains.
4. Netlify will issue a Let's Encrypt certificate automatically.

## Deploying to Netlify via GitHub (recommended for future updates)

1. Push this repo to GitHub.
2. In Netlify: **Add new site → Import from Git → GitHub**, pick the repo.
3. Build settings: leave **Build command** blank, set **Publish directory** to `.` (the repo root). The `netlify.toml` already declares this.
4. Connect the custom domain as above.

## Design notes

- Colors and typography match the in-app Wind Tracer design tokens. Core palette: `#0A0A0B` base, `#2B7A8C` teal (`--teal-bright #3E9DB2`), `#2DD4BF` "ride" accent, `#F97316` "dead water" accent, `#FAFAFA` text.
- Display type: Fraunces (Google Fonts).
- Body type: Inter Tight (Google Fonts).
- Mono type: JetBrains Mono (Google Fonts).
- Fonts are loaded from `fonts.googleapis.com` / `fonts.gstatic.com` (the one external dependency). `index.html` `preconnect`s to both.

## App Store / TestFlight compliance checklist

When you submit to TestFlight or the App Store, point Apple to:

- **Support URL** → `https://www.downwindtracker.com/` (support is handled via the `mailto:support@downwindtracker.com` links / `#beta` section)
- **Marketing URL** → `https://www.downwindtracker.com/`
- **Privacy Policy URL** → `https://www.downwindtracker.com/privacy.html`
- **EULA URL (optional)** → `https://www.downwindtracker.com/terms.html`

You will still need to fill in the App Privacy questionnaire in App Store Connect. The Privacy Policy on this site is written to reflect what the project knowledge shows the app actually collects (email via Supabase, location, motion, HealthKit workout, basic session metadata). Mirror these in App Store Connect or Apple will reject the build.

## Things to update before launch

- `privacy.html` and `terms.html` carry `Last updated: July 23, 2026`. Bump these whenever the policies change.
- `terms.html` Section 12 (Governing law) uses a generic clause; replace with your actual jurisdiction and have the Terms reviewed by counsel before public App Store launch.
- The site is in **TestFlight beta** mode: the hero status pill reads "TestFlight beta · Garmin FIT · Apple Watch" and CTAs point to `#beta` / `mailto:support@downwindtracker.com`. When you go live, swap the CTAs in `index.html` for a real App Store badge / URL and update the status pill and beta copy.

## License

All site source is © DownwindTracker. The Fraunces, Inter Tight, and JetBrains Mono fonts are loaded from Google Fonts under the SIL Open Font License.
