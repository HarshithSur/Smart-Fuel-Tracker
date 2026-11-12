SMART FUEL TRACKER — INSTALLABLE PWA

WHAT IS INCLUDED
- index.html: existing tracker frontend adapted for PWA hosting
- manifest.webmanifest + service-worker.js + icons/: install metadata and app-shell caching
- Code.gs: Apps Script backend with API bridge while preserving the original Apps Script page route

IMPORTANT
This is a PWA package, not an APK. It must be hosted over HTTPS (GitHub Pages is a free option). The Google Apps Script backend must be redeployed as a Web App.

SETUP
1. In Apps Script, replace your current Code.gs with the supplied Code.gs. Keep the existing Index.html in Apps Script so the old /exec page remains available as a fallback. Save.
2. Deploy > Manage deployments > Edit (pencil) > New version > Deploy. Keep the access setting appropriate for your use. Copy the Web app URL ending in /exec.
3. Open this package's index.html and find GAS_API_URL near the top of the first script block. Replace PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE with the exact deployed /exec URL. Do not add ?api=... to the saved URL.
4. Upload the CONTENTS of this folder to a GitHub repository (root of repository). Enable GitHub Pages: Settings > Pages > Deploy from a branch > main > /(root). Wait for the HTTPS site URL.
5. Open the GitHub Pages URL in Chrome on Android. Use Chrome menu > Install app (or Add to Home screen).

BACKEND NOTES
- Dashboard uses JSONP GET. Extract/save use a hidden iframe POST bridge because Apps Script ContentService does not provide configurable CORS headers.
- The service worker caches the app shell. Fuel extraction, GPS, Groq, and Google Sheets operations still require an internet connection.
- Keep your Apps Script deployment access configured so the signed-in user can access the spreadsheet. Do not publish API keys in the frontend; GROQ_API_KEY stays in Apps Script Script Properties.
- Test dashboard, fuel-only extraction, fuel+UPI extraction, save, duplicate rejection, and both motorcycle tabs before relying on it.
