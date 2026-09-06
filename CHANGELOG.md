# Changelog

All notable changes to the Encore Android SDK. The SDK is distributed as a prebuilt AAR on Maven Central as `com.encorekit:encore`; each entry below corresponds to a published version and a tagged GitHub Release in this repository.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Versions follow [Semantic Versioning](https://semver.org/); all published compatibility guarantees are within a major.

## [2.1.0] - 2026-09-06

### Changed

- **Play Billing floor raised to 8.0.0.** The SDK now declares `com.android.billingclient:billing:8.0.0` (previously `billing-ktx:7.1.1`). Apps already resolving Billing 8.x or 9.x see no change other than the fix below. Apps on Billing 7.x are raised to 8.0.0 by Gradle's highest-wins resolution; Google Play stopped accepting Billing 7.x submissions on 2026-08-31, so this move is required regardless.
- Built with the Kotlin 2.1 compiler. The language floor stays 1.9, and `kotlin-stdlib` is declared at that floor in the POM rather than stripped.

### Fixed

- `NoSuchMethodError` in the purchase reconciler when the host app's dependency graph resolved Play Billing 8.x or 9.x. The SDK's prebuilt bytecode called an `enablePendingPurchases()` overload that Billing 8.0.0 removed. Claim and entitlement paths were never affected; the reconciler ran in a contained scope.
- SDUI: the offer footer's copy column is capped so the claim button always lays out.
- Outbox: a transient failure retires only its own target rather than the whole pass.

### Added

- Users handshake: the SDK announces the user record on identity creation (`POST /publisher/sdk/v1/users`) and announces aliases on `identify()`.
- Error reporting from silent degradation paths, with full stack traces.
- SDUI: snapped carousel cards centre on any viewport width (`scrollAlignment: center`).
- Outbox: a non-suspending submit for callers that cannot await the persist.

### Notes for claim-only integrations

A claim-only integration with no `purchaseController` registered is a supported configuration. With none registered, an offer configured for in-app purchase resolves `PublisherOutcome.NotAttempted`, a warning is logged, and nothing is charged. Billing is a runtime-scope dependency that the claim and entitlement paths do not touch; stripping `com.android.vending.BILLING` from the merged manifest with `tools:node="remove"` is fine in that configuration.

[2.1.0]: https://github.com/EncoreKit/android-sdk/releases/tag/v2.1.0
