# Goal-clock-counter
An app i made to use old phone as an clock which counts days till a certain fate on which i set the specific goal is grate for aspraints trying  for exam date (vibe code )
# Wall Clock (Android 5.0+, tested design target: Android 7)

One app, three full-screen displays that rotate forever:

1. Flip clock (HH:MM, white on black, split-flap animation)
2. Countdown ("142 DAYS REMAINING", your title + target date)
3. Today's date (SATURDAY / 21 NOVEMBER / 2026)

Long-press the screen = settings (title, date, seconds per screen, 12/24 h, orientation lock). Tap = skip to next screen.
No ads, no internet permission, no accounts, no dependencies.

## Get the APK (pick one)

### A. GitHub Actions (no installs on your PC)
1. Create a new GitHub repo, upload everything in this folder (keep the `.github` folder).
2. Open the repo's **Actions** tab -> "Build APK" -> run it (it also runs on every push).
3. When it finishes, download the **wallclock-apk** artifact -> unzip -> `app-debug.apk`.

### B. Android Studio
Open this folder as a project, let it sync, then **Build > Build APK(s)**.
APK: `app/build/outputs/apk/debug/app-debug.apk`

### C. Command line (JDK 17 + Android SDK with platform 34)
`gradle assembleDebug`

## Install on the old phone
Copy the APK over, allow "install unknown apps" for your file manager, open the APK.
Or: `adb install app-debug.apk`

## No-build alternative
`wallclock.html` is the same screen as a single offline file. Load it in a kiosk browser such as Webview Kiosk (free, Android 5+).

## Notes
* The app sets FLAG_KEEP_SCREEN_ON, hides the system bars, and starts again after a reboot (BootReceiver).
* Settings live in the WebView's localStorage; clearing app data resets them.
* Needs a WebView based on Chrome 51+ (the default on Android 7.0; updatable via Play Store/system updates).
* A phone left on a charger 24/7 can have its battery swell with age. Check the battery now and then, and consider a charge limiter or removing a removable battery.
