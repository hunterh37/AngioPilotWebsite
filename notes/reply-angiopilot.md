# AngioPilot site — status

Repo `hunterh37/AngioPilot` already exists, public, Pages legacy build from `main /`.
Live URL: https://hunterh37.github.io/AngioPilot/

## Changed
- `index.html`: boarding-pass hero (Femoral Artery departure, Splenic Artery arrival), visionOS run flow, field kit, spec table, Book Demo mailto.
- `assets/css/style.css`: `#b0cae8` / `#8f2926`, SF Pro + Good Times stack, ticket/stub/QR/badge styles, responsive + reduced-motion.

## Design mapping from image
Ticket, takeoff stub, window badge, keychain kit, color codes, fonts carried over. No new dependencies.

## Verification
- `gh repo view` + `gh api repos/.../pages`: public, status built.
- Local `bundle exec jekyll build` not run: system ruby 2.6.10 incompatible with current github-pages ffi requirement. Remote Pages build remains the test path.
- Working tree: 2 files modified, uncommitted for review.

## MedVR footer logo
Source: `Mar2025CodeBlue/research/assets/medvr-logo.png` (also in `menu-medvr-logo.imageset`).
Copied to `assets/img/medvr-logo.png`, wired into maroon footer with `alt="MedVR"`, height 28px. Uncommitted.

## Maroon page background
Body now `#8f2926` with white text; ticket/stops/QR stay light for contrast; headings white; spec dividers translucent white. Uncommitted.

## Next
Review diff, then commit + push to `main` to deploy via Pages.
