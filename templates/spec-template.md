# App Spec: [App Name]

Generated with app-idea-to-spec. An app idea turned into a build-ready spec for Claude Code.

---

## 1. One-liner

One sentence: what the app does and who it is for.

## 2. Problem and target user

- **Problem:** the specific pain this solves.
- **Target user:** who has this pain. Be concrete, not "everyone".
- **Why now / why you:** optional, the wedge or unfair advantage.

## 3. Core loop

The single thing a user opens the app to do, start to finish. If you cannot state it in one or two sentences, the scope is not clear yet. Everything in the MVP serves this loop.

## 4. Platform and tech approach

- **Platform(s):** iOS only / iOS + Android / other.
- **Approach:** Swift and SwiftUI (native) / Expo (React Native) / Flutter / Kotlin Multiplatform.
- **Reason:** tie the choice to the decision framework in [platform-choice](../knowledge/platform-choice.md).
- **Minimum OS version:** affects which APIs and which storage options you get.

## 5. MVP features (must-have)

The shortest list that delivers the core loop. For each: name, one-line description, why it is essential.

- [ ] **[Feature name]**: [one-line description]. Why essential: [reason].
- [ ] ...

## 6. Explicitly cut for later

Features that are not in the MVP. Naming them here is how you protect scope. See the over-scoping traps in [mvp-scope](../knowledge/mvp-scope.md).

- **[Feature]**: [why it is deferred].
- ...

## 7. Screens and navigation

The screens and how the user moves between them. Code generation needs this. A simple list plus a navigation pattern is enough.

- **[Screen]**: [purpose]. Key actions: [...].
- **Navigation:** tab bar / navigation stack / modal flow / other.

## 8. Data and persistence

- **Data model:** main entities and their relationships.
- **Storage:** SwiftData / Core Data / local files / other. See [data-and-sync](../knowledge/data-and-sync.md).
- **Sync:** none / CloudKit / Firebase / custom backend, and why.
- **Offline behavior:** what works without a connection.

## 9. Monetization

- **Model:** free / freemium / one-time purchase / subscription. See [monetization](../knowledge/monetization.md).
- **Paywall:** soft / hard / none, and exactly what is gated.
- **Tiers and price points:** the actual options you will offer.
- **Tooling:** StoreKit 2 / RevenueCat, and why.

## 10. Validation goal

- **What the MVP tests:** the one hypothesis this version exists to check.
- **Validated when:** a concrete, measurable signal. Not "people like it".

## 11. Store readiness

Things that block submission or cause rejection. Fill in what applies. See [app-store-reality](../knowledge/app-store-reality.md).

- **Accounts?** If users can create an account, in-app account deletion is required.
- **Third-party SDKs** (Firebase, analytics, ads)? A privacy manifest is required.
- **Privacy policy URL and data-collection disclosure:** ...
- **Demo account or test path for review:** reviewers need to reach the core feature.

## 12. ASO starter

- **Working title** (with the main keyword): ...
- **Subtitle:** ...
- **Keyword direction:** ... See [aso-basics](../knowledge/aso-basics.md).

## 13. Open questions

Anything still undecided. app-idea-to-spec turns these into specific follow-ups.

- ...

## 14. Build handoff (for Claude Code)

A short, ordered build plan generated from the spec above. Filled in by `/app-idea-to-spec:build-plan`.

- ...
