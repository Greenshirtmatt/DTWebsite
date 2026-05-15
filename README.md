# downwindtracker-site

Single-page marketing and compliance site for the DownwindTracker iOS + watchOS app, hosted at https://www.downwindtracker.com.

## Stack

Pure static HTML + CSS. No build step, no JavaScript framework, no dependencies. Designed to drop straight onto Netlify (drag-and-drop or Git deploy).

## File layout

```
.
├── index.html        # Landing page
├── privacy.html      # Privacy Policy
├── terms.html        # Terms of Use / EULA
├── 404.html          # Not-found page
├── styles.css        # All styles (Wind Tracer dark theme)
├── favicon.svg       # SVG favicon
├── robots.txt
├── sitemap.xml
└── netlify.toml      # Netlify config (redirects, headers, caching)
```

## Deploying to Netlify (drag-and-drop, no Git yet)

1. Zip the contents of this folder (not the folder itself, the contents).
2. Go to https://app.netlify.com/drop and drop the zip.
3. In **Site settings → Domain management**, add `www.downwindtracker.com` and `downwindtracker.com` as custom domains.
4. Netlify will issue a Let's Encrypt certificate automatically.

## Deploying to Netlify via GitHub (recommended for future updates)

1. Create a new GitHub repo and push these files.
2. In Netlify: **Add new site → Import from Git → GitHub**, pick the repo.
3. Build settings: leave **Build command** blank, set **Publish directory** to `.` (the repo root). The `netlify.toml` already declares this.
4. Connect the custom domain as above.

## Design notes

- Colors and typography match the in-app Wind Tracer design tokens defined in `DesignTokens.swift` (`#0A0A0B` base, `#2B7A8C` teal, `#F59E0B` amber, etc).
- Display type: Fraunces (Google Fonts).
- Body type: Inter Tight (Google Fonts).
- Mono type: JetBrains Mono (Google Fonts).

## App Store / TestFlight compliance checklist

When you submit to TestFlight or the App Store, point Apple to:

- **Support URL** → `https://www.downwindtracker.com/` (or directly to `#support` anchor)
- **Marketing URL** → `https://www.downwindtracker.com/`
- **Privacy Policy URL** → `https://www.downwindtracker.com/privacy.html`
- **EULA URL (optional)** → `https://www.downwindtracker.com/terms.html`

You will still need to fill in the App Privacy questionnaire in App Store Connect. The Privacy Policy on this site is written to reflect what the project knowledge shows the app actually collects (email via Supabase, location, motion, HealthKit workout, basic session metadata). Mirror these in App Store Connect or Apple will reject the build.

## Things to update before launch

- `privacy.html` and `terms.html` carry a placeholder `Last updated: May 15, 2026` and a publisher-jurisdiction blank in the Terms governing-law clause. Fill these in with your actual jurisdiction and have the Terms reviewed by counsel before public App Store launch.
- The hero block says "TestFlight beta, App Store launch in progress" and the CTA button is disabled. When you go live, change the CTA in `index.html` to a real App Store badge / URL and update the status pill text.
- Replace the placeholder `<em>These Terms are a starting template...</em>` note in `terms.html` once you have final reviewed copy.

## License

All site source is © DownwindTracker. The Fraunces, Inter Tight, and JetBrains Mono fonts are loaded from Google Fonts under the SIL Open Font License.
