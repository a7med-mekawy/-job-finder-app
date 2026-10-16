# Job Finder — Arabic PWA starter

This is a working front-end prototype (not yet connected to a live job-search API). It includes:
- Arabic RTL responsive layout
- Seed listings with original external links
- Save jobs and track application status
- Local profile fields and CSV export
- Job-board sign-in helper links (never collects or stores passwords)
- PWA manifest and service worker for installation after HTTPS hosting

## Run locally
Install Node.js 22+ and then from this directory:

```bash
npx --yes serve .
```

Open the local URL shown in the terminal. Service-worker/PWA features may require localhost or HTTPS.

## Host it as an installable Android PWA
Upload these files to an HTTPS host (for example, a static site host). Open the HTTPS URL in Chrome on Android, then choose **⋮ > Install app** or **Add to Home screen**.

## Package as an Android APK with Capacitor
Requirements: Node.js 22+, Android Studio, Android SDK.

```bash
npm init -y
npm install @capacitor/core @capacitor/android
npm install -D @capacitor/cli
npx cap init "Job Finder" "com.ahmedmekawy.jobfinder" --web-dir .
npx cap add android
npx cap sync android
npx cap open android
```

In Android Studio, wait for Gradle sync, then use Build > Build Bundle(s) / APK(s) > Build APK(s). For a release APK, use Build > Generate Signed Bundle / APK.

## Important next steps before real use
1. Add a backend endpoint and a licensed/authorized job-search source. Do not scrape sites against their terms or bypass access controls.
2. Add server-side deduplication, last-checked timestamps, and a closed-job check.
3. Add secure authentication if syncing data across devices. Never store job-board passwords in this app or its backend. Use official OAuth when supported; otherwise open the official site in the system browser and let the site manage its own session.
4. Current profile and tracking data use browser localStorage on this device. They are not encrypted or synced and can be cleared with browser data.
