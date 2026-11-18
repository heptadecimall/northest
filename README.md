# Northest

Moon phases, tonight's sky and constellations.

## Web app (GitHub Pages)

The web app lives at the repository root (`index.html`, `sw.js`, `manifest.webmanifest`, icons).
To publish: **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / `(root)`**.

Once deployed it is installable from the browser (Android Chrome: menu → *Install app*; iPhone Safari: Share → *Add to Home Screen*) and works offline after the first visit.

## Android app

`android/` is a small native wrapper that bundles the web app (with fonts) inside the APK, so it works offline from the first launch.
The bundled copy is in `android/app/src/main/assets/www/` — copy changed web files there before rebuilding.

Build a signed release (needs the Android SDK; the keystore is not in this repo):

```bash
cp /path/to/northest-release.jks android/
cd android
NORTHEST_KS_PASS=... ./gradlew assembleRelease
```

The APK is written to `android/app/build/outputs/apk/release/app-release.apk`.
Bump `versionCode` in `android/app/build.gradle` for each release.
