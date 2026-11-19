# Christmas Countdown – Weihnachtsferien 🎄

Native Android app built with Kotlin, Jetpack Compose, and Material Design 3.

## Download
Open **Actions → Build Weihnachtsferien Countdown APK** and download the latest **WeihnachtsferienCountdown-APK** artifact. The artifact is a debug-signed APK for testing.

## Features
- Live Christmas-holiday countdown.
- All 16 German federal states and city selection.
- Official KMK holiday data for the bundled years, offline cache, last-check timestamp, and manual fallback dates.
- Weekly Monday reminder at a configurable local time; reboot and time-change re-scheduling.
- Ten Christmas themes with saved selection and reduced-motion option.
- Snow animation.
- Local music picker for audio files chosen by the user with Android's document picker.
- Mini-player stays visible above the bottom navigation while moving through Home, Music, Themes, Location, and Settings.
- Mini-player controls: track title, play/pause, stop, previous/next, seek slider, elapsed time, track duration, and remaining time.
- Imported file references are stored locally on the device.

## Music and licensing
The APK does not contain the commercial recordings provided in the chat or any other copyrighted music copies. Choose audio files already stored on your phone under **Musik → Musik vom Gerät auswählen**. The app stores only the selected file references and reads them locally.

Playback continues while navigating inside the app. This version is not a foreground media service, so it does not guarantee playback after leaving the app, locking the phone, or process termination. Android notification and lock-screen media controls, shuffle, repeat, and volume control are not included.

## Holiday data
- Main source: [Kultusministerkonferenz (KMK) holiday calendar](https://www.kmk.org/service/ferienregelung/ferienkalender.html)
- Hesse 2026/27 statewide Christmas holidays: 23 December 2026–12 January 2027.
- Kassel's local movable school-free days are displayed separately from statewide holidays.
- Future dates without verified official sources are not invented; manual entry is available.

## Build
GitHub Actions reconstructs the archived base project, applies `patches/music-player.patch.gz.b64`, runs `gradle assembleDebug`, checks the APK package metadata and SHA-256, and uploads the APK artifact.

## Verification and limitations
- CI build, package metadata check, and artifact upload passed.
- minSdk 26; target/compile SDK 35.
- Debug-signed APK only; a signed release requires a user-owned keystore configured with GitHub Secrets.
- Playback has not been tested on a physical Android device. Actual audio codec support can vary by device.
- The GitHub repository is public. Do not store credentials, signing keys, or personal data in it.
