# Christmas Countdown – Weihnachtsferien 🎄

Native Android app built with **Kotlin**, **Jetpack Compose**, and **Material Design 3**.

## Download the APK

Open **Actions → Build Weihnachtsferien Countdown APK → Run #4** and download the artifact named **WeihnachtsferienCountdown-APK**. The current build is a debug-signed APK for testing.

## Included features

- Live countdown, updated every second.
- All 16 German federal states, with city selection and optional on-device location lookup.
- Official Christmas-holiday dates for school years 2026/27 and 2027/28, bundled for offline use.
- Refresh from the official KMK holiday calendar and show the last successful check time.
- Manual date entry when official data for a future year is not available.
- Kassel's additional movable days for 2026/27 are shown separately from Hesse's statewide holidays.
- Weekly Monday reminder, default 08:00, configurable time, notification permission, and reboot/time-change re-scheduling.
- Ten selectable and saved Christmas themes, snow animation, reduced-motion setting.
- Ten-song list linking to official YouTube Music search results.

## Music and licensing limitation

This version does **not** stream copyrighted tracks inside the app. Song entries open the official YouTube Music search page/app. In-app audio playback, lock-screen/media-session controls, background audio, progress/seek, volume controls, shuffle, and repeat are **not implemented**. Cover art is represented by emoji placeholders rather than copyrighted album artwork.

## Holiday data

- Main source: [Kultusministerkonferenz (KMK) holiday calendar](https://www.kmk.org/service/ferienregelung/ferienkalender.html)
- The bundled dates cover 2026/27 and 2027/28 (KMK source stand: 09 October 2025).
- Hesse 2026/27 statewide Christmas holidays: 23 December 2026–12 January 2027.
- The official KMK table lists the first and last holiday day. Local movable non-school days may differ by school authority.
- No generic Christmas date is invented for a future year with no verified source; manual entry is available instead.

## Build

The repository stores the complete source as a compressed, base64-split archive under `archive/chunk-*.b64`. GitHub Actions reconstructs it, then runs:

```bash
gradle --no-daemon --stacktrace assembleDebug
```

The workflow verifies the generated APK package metadata and SHA-256, then publishes the `WeihnachtsferienCountdown-APK` artifact.

To work locally, download the source ZIP attached to the conversation or restore the archive by concatenating the chunks in numeric filename order, base64-decoding, then extracting the resulting `.tar.xz` archive.

## Compatibility and known limitations

- minSdk 26; target/compile SDK 35.
- Monday alarms are deliberately inexact and idle-aware. Android battery optimisation may delay delivery.
- Runtime installation/device testing has not been performed in this workflow; CI verified that Gradle compiled the app, the APK package metadata was readable, and the artifact upload succeeded.
- Only a debug signing key is used. A signed release build requires an owner-provided release keystore stored securely in GitHub Secrets.
- The repository is currently public. Do not place private credentials, signing keys, or personal data in it.

## Project privacy

Settings, selected location, manual dates, and reminder preferences are stored locally. GPS is optional and requested only after the user chooses it; reverse geocoding is performed on-device. The KMK webpage is fetched from the device when online refresh is performed. Song links open a third-party provider.
