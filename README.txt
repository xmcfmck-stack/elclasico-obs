EL CLASICO OBS WEBSITE — CLOUDFLARE PAGES PACKAGE

FILES
index.html — landing page
overlay.html — transparent 1920 x 1080 OBS overlay
control.html — manual dashboard
style.css, common.js, overlay.js, control.js — website assets
functions/api/live-clasico.js — Cloudflare Pages Function proxy for unofficial ESPN match feed

DEPLOYMENT (IMPORTANT)
This ZIP contains a Cloudflare Pages Function. The Cloudflare dashboard's simple drag-and-drop upload may not deploy the functions folder. For FULL automatic score functionality, deploy the entire project through GitHub-connected Cloudflare Pages or Wrangler CLI.

EASIEST RELIABLE ROUTE
1. Unzip this package.
2. Create a GitHub repository and upload ALL extracted files, including functions/api/live-clasico.js.
3. In Cloudflare dashboard > Workers & Pages > Create > Pages > Connect to Git.
4. Select repository. Framework preset: None. Build command: leave blank. Build output directory: / (repository root; if Cloudflare rejects '/', use '.').
5. Deploy. Wait for the *.pages.dev URL.
6. Test https://YOUR-SITE.pages.dev/api/live-clasico — it should return JSON.
7. OBS Studio > Sources > + > Browser. URL: https://YOUR-SITE.pages.dev/overlay.html. Width 1920; Height 1080.

IMPORTANT LIMITATIONS
- This package is static and can be deployed publicly without Higgsfield login.
- Live score, period and match clock are fetched independently by OBS through the included Pages Function every ~20 seconds, subject to ESPN endpoint availability and third-party use rights. This is not a licensed, guaranteed production sports feed.
- Manual score, events, branding and stats in control.html are stored in localStorage; OBS Browser Source is isolated, so dashboard manual changes DO NOT synchronize into OBS. A shared authenticated server backend is needed for that feature.
- Match event animations are available for preview in the same browser profile as the dashboard.
- The scoreboard uses the fixture found on the current UTC date, with October 25, 2026 fallback. Do not rely on the fallback for later matches.
- No actual match footage, copyrighted crest assets, or licensed sports API keys are included.
- This package is an independently deployable version of the overlay, not a full export of the Higgsfield source application.
- Verify the public overlay URL in a private/incognito browser before adding to OBS.
