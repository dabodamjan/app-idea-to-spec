# Platform choice

Native Swift vs Expo vs Flutter vs Kotlin Multiplatform, and how to pick as a solo or indie dev. Current as of 2026.

The platform decision is the most expensive one to reverse, so it belongs in the spec early. The good news: for most indie apps the answer is simpler than the debate makes it sound.

## The options in 2026

### Swift and SwiftUI (native iOS)

The mature default for an iOS-first app. SwiftUI is the assumed starting point now, and UIKit is the escape hatch for the rare case, not the foundation. Native gives you the deepest, day-one access to new OS APIs (the iOS 26 design language, App Intents, widgets, Live Activities). Cross-platform frameworks lag those by months.

The tradeoff has not changed: it is iOS only. A second platform means a second codebase.

### React Native with Expo

The biggest shift of the last couple of years: the New Architecture (Fabric, TurboModules, JSI, Bridgeless) is now the only architecture. From React Native 0.82 it is always on and cannot be disabled, and the legacy architecture was frozen in June 2025.

Two things matter for an indie:
- **Expo is now the recommended way to build React Native.** The framework-first approach won. "Bare" React Native is the niche path now, a full inversion of the old advice that treated Expo as the beginner option.
- **Continuous Native Generation** means you do not commit `ios/` and `android/` folders. They are regenerated from your config. This removes most of the historical "I had to eject" pain. EAS handles cloud builds, submission, and over-the-air JavaScript updates.

If you come from the web, this is your lowest-friction path to both platforms.

### Flutter

The strongest single-codebase story for pixel-identical UI across iOS, Android, web, and desktop, using its own rendering engine and the richest built-in widget library. It uses Dart, not JavaScript.

The friction for an indie is the same as it always was: a Flutter app looks like a Flutter app unless you invest in making it feel native on each platform, and it is a separate language and ecosystem from the web stack most newcomers already know.

### Kotlin Multiplatform (KMP)

The momentum story. Compose Multiplatform for iOS reached stable and production-ready in May 2025 (Compose Multiplatform 1.8.0), so you can now optionally share the UI too, not just business logic.

KMP's defining trait is graduated code sharing: share only networking and business logic and keep native SwiftUI and Jetpack Compose UIs, or share the UI through Compose Multiplatform, or share specific modules. That is more architectural decisions than Flutter or React Native, which push maximum sharing by default. It fits best when native UX is non-negotiable on both platforms, or when there is already Android and Kotlin investment.

## A decision framework

1. **iOS only, want best-in-class native feel and the newest Apple APIs, and you already know Swift.** Use Swift and SwiftUI. Do not pay a cross-platform tax you will not use. This is the indie iOS default.
2. **You come from web, React, or vibe-coding and want both platforms from one codebase, fast.** Use Expo (React Native). Lowest ramp for a JavaScript or TypeScript background, and EAS removes most of the build-infrastructure pain.
3. **Both platforms, UI-heavy, you want one pixel-perfect codebase, and you have no existing JavaScript investment.** Use Flutter. Best when the design is custom and branded rather than trying to mimic each OS.
4. **Native UX is non-negotiable on both platforms, or you already have Android and Kotlin.** Use KMP. Share the logic, and optionally share the UI with Compose Multiplatform now that it is stable.

## Comparison

| | Swift / SwiftUI | Expo (React Native) | Flutter | KMP |
| --- | --- | --- | --- | --- |
| Platforms | iOS only | iOS + Android (+ web) | iOS + Android + web + desktop | iOS + Android (+ more) |
| Language | Swift | TypeScript / JS | Dart | Kotlin |
| New OS APIs | Day one | Lags, via libraries | Lags, via plugins | Lags for shared UI |
| Best for | iOS-first indies | Web devs wanting both | One custom UI everywhere | Native UX + shared logic |

## The honest take for a true solo indie

For your first one or two apps, "pick one platform and go native, or pick Expo if you genuinely need both" beats agonizing over the matrix. Cross-platform earns its keep when maintaining two native codebases is your actual bottleneck, and that is rarely the bottleneck at MVP stage. Shipping one good app on one platform teaches you more than splitting your effort across two.

A note on market share: the 2026 figures floating around for Flutter, React Native, and KMP adoption are inconsistent across sources and survey methods, so treat any precise percentage with suspicion. The safe read is that Flutter and React Native remain the two dominant cross-platform choices with comparable large shares, and KMP is the fastest-growing newcomer.

## What this means for your spec

Write down the platform, the approach, the reason, and the minimum OS version in section 4 of the spec. The minimum OS version is not a throwaway: it decides which APIs and which storage options ([data-and-sync](data-and-sync.md)) you can use. If you are unsure, default to one platform and the native or Expo path that matches your background, and revisit only if a real constraint forces it.
