# SINIKAT PRODUCTIONS Calculator

Offline service and rates calculator: quotations, history, PDF export, Android sharing, admin dashboard.

## Files
- `src/index.html` – the whole app (HTML/CSS/JS). Open it in a browser to use it.
- `assets/` – logo-based launcher icon and splash screen sources.
- `capacitor.config.json`, `package.json` – Android (Capacitor) setup.
- `.github/workflows/android.yml` – builds the APK in the cloud.

## Get the APK (no coding, free)
1. Create a free GitHub account and a new repository (private is fine).
2. Upload the contents of this folder to it (keep the `.github` folder).
3. Open the **Actions** tab → **Build Android APK** → **Run workflow** (it also runs on every push).
4. When the run is green (about 5–8 minutes), open it and download **SINIKAT-PRODUCTIONS-APK** under *Artifacts*. Unzip it to get `app-debug.apk`.
5. Send the APK to your Android phone, open it, and allow "Install unknown apps" when asked.

## Build on your own computer
Requires Node 20 and JDK 17 with the Android SDK.
```
npm install
mkdir www && cp src/index.html www/ && cp node_modules/jspdf/dist/jspdf.umd.min.js www/
sed -i 's#https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js#jspdf.umd.min.js#' www/index.html
npx cap add android && npx capacitor-assets generate --android && npx cap sync android
cd android && ./gradlew assembleDebug
```
APK: `android/app/build/outputs/apk/debug/app-debug.apk`

## Using the app
- Default admin password: `sinikat2026` (Admin settings, bottom of the screen). Change it right away.
- Data (prices, password, quotation history) is stored on the device only. Uninstalling the app erases it.
- On Android, "Download as PDF" creates the file and opens the share sheet (save to Files, WhatsApp, email).
- The APK is a debug build: installable and fully working, but not signed for Google Play.
