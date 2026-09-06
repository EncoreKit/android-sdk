# Encore SDK for Android

[![Maven Central](https://img.shields.io/maven-central/v/com.encorekit/encore.svg?label=Maven%20Central)](https://central.sonatype.com/artifact/com.encorekit/encore)
[![Platform](https://img.shields.io/badge/Platform-Android%2024+-lightgrey.svg)](https://developer.android.com)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.9+-blueviolet.svg)](https://kotlinlang.org)

A lightweight, non-invasive SDK for presenting targeted retention offers and managing promotional entitlements in Android apps.

This repository is the public home for the SDK's **release notes, changelog, and integration reference**. The SDK itself is distributed as a prebuilt AAR on Maven Central; its source is not published here.

---

## Installation

```kotlin
dependencies {
    implementation("com.encorekit:encore:2.1.0")
}
```

`mavenCentral()` is all that is required; no additional repository configuration.

## Requirements

| | Minimum |
|:--|:--|
| Android | API 24 (Android 7.0) |
| Kotlin | 1.9 (the SDK declares `kotlin-stdlib` at this floor) |
| Google Play Billing | 8.0.0 (declared by the SDK; only relevant if you register a purchase controller) |

Gradle resolves the highest version of each dependency in your graph, so the SDK's declared versions are floors, not pins. If your app already uses a newer Play Billing, that version is used.

## Tracking changes

- **Releases:** every published version has a tagged [GitHub Release](https://github.com/EncoreKit/android-sdk/releases) with notes.
- **Changelog:** [`CHANGELOG.md`](CHANGELOG.md), in Keep-a-Changelog form.
- **Compatibility:** all published guarantees are within a major version. Public API signatures are baselined and checked in CI on every change.

Watch this repository's releases to be notified of new versions.

## Support

- **Documentation:** [docs.encorekit.com](https://docs.encorekit.com)
- **Email:** sdk-bot@encorekit.com
- **Issues:** [github.com/EncoreKit/android-sdk/issues](https://github.com/EncoreKit/android-sdk/issues)
