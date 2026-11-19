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
- Nine original Christmas instrumental MP3 tracks bundled in the APK and available offline.
- Background playback handled by one Android Media3 media session service; playback continues when navigating between Home, Music, Themes, Location, and Settings.
- Persistent mini-player above the bottom navigation with current title, play/pause, stop, previous/next, seek, elapsed/remaining/duration, and volume slider.
- Android media session notification and lock-screen controls while music is playing.
- Last selected track and volume are saved locally.
- Additional audio files can still be imported with Android's document picker; original imported file references remain local to the device.

## Music and licensing
The nine bundled instrumentals are newly generated for this app by `tools/generate_music.py`. They do not use the commercial recordings uploaded in the chat, samples, or copied melodies. Those commercial artist recordings are not included in the APK. The generated music is encoded as MP3 resources and can be played without an internet connection.

## Holiday data
- Main source: [Kultusministerkonferenz (KMK) holiday calendar](https://www.kmk.org/service/ferienregelung/ferienkalender.html)
- Hesse 2026/27 statewide Christmas holidays: 23 December 2026–12 January 2027.
- Kassel's local movable school-free days are displayed separately from statewide holidays.
- Future dates without verified official sources are not invented; manual entry is available.

## Build
GitHub Actions reconstructs the archived base project, applies the original local music picker patch and the isolated background-music patch, generates nine MP3 resources, runs `gradle assembleDebug`, verifies the APK contains all nine audio resources, and uploads the APK artifact.

## Verification and limitations
- CI verified all nine generated MP3 files by decoding them with FFmpeg, compiled the Android project successfully, checked the APK contains each of the nine MP3 resources, and uploaded the APK artifact.
- minSdk 26; target/compile SDK 35.
- Uses Media3 1.9.4 to retain compile SDK 35 compatibility.
- Debug-signed APK only; a signed release requires a user-owned keystore configured with GitHub Secrets.
- Playback has not yet been tested on a physical Android device. Actual audio behavior may vary by device.
- The GitHub repository is public. Do not store credentials, signing keys, or personal data in it.
