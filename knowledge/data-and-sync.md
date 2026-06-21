# Data and sync

How to store data on a mobile app and whether to sync it. SwiftData vs Core Data, and CloudKit vs Firebase vs a custom backend. Current as of 2026.

Two separate decisions live here: how data is stored on the device, and whether and how it syncs across devices or users. Keep them separate in the spec.

## SwiftData vs Core Data

### SwiftData is production-ready in 2026, with one asterisk

As of iOS 18, and especially iOS 26, SwiftData is stable and production-ready. It is no longer the rough framework it was at launch. The gap-closing arrived in two waves:

iOS 18 (2024) fixed the biggest early omissions:

- `#Unique` compound uniqueness constraints, with upsert on collision
- `#Index` for query performance
- Custom data stores and `Codable` / custom-type persistence

iOS 26 (2025) added more:

- History tracking through `HistoryObserver`, which gives you an audit or sync change feed
- Sectioned queries for SwiftUI
- Class inheritance for models

### The honest history

You will read a lot of "I ditched SwiftData" posts. Most of them describe the 2023-era, iOS 17.0 version, which was genuinely rough: no uniqueness constraints, no indexing, no history, brittle migrations. That verdict was correct for 2024 SwiftData. The framework has materially improved since. So do not carry a stale "SwiftData is not ready" conclusion into a 2026 decision.

### Pitfalls still worth knowing

- **Migrations.** SwiftData reliably handles lightweight migrations. Heavyweight and custom migrations are still weaker than Core Data's mature migration tooling, and model inheritance introduced new migration sharp edges in iOS 26. Do not assume painless complex schema evolution.
- **Very large datasets.** Performance under heavy load is still being watched by the community. Fine for typical app-sized data, not yet the obvious pick for massive local datasets where Core Data's tuning knobs matter.
- **OS floor.** The features that make SwiftData competitive arrived in stages: uniqueness constraints and indexing need iOS 18, and history tracking and model inheritance need iOS 26. iOS 17 shipped SwiftData but without these. If you must support older iOS, plan around what you do not get.

### The 2026 recommendation

- **New iOS-only app, SwiftUI-based, modern OS floor:** start with SwiftData. It removes Core Data's thread-unsafety footguns and stringly-typed runtime errors, and it is where Apple is investing.
- **Complex or custom migrations, very large datasets, or you need fine-grained control:** Core Data is still fully supported and the safer pick. You can also drop down to Core Data underneath a SwiftData stack if needed.
- **Existing Core Data app:** no urgency to migrate. It is stable and supported.

## Sync: CloudKit vs Firebase vs custom backend

| Option | Cost reality (2026) | Fits when | Watch out for |
| --- | --- | --- | --- |
| **CloudKit** (incl. SwiftData + CloudKit) | Private-database storage comes out of the user's iCloud quota, not yours, so it is effectively free to you for per-user data. Public-database usage is metered. | iOS or Apple-only app, per-user data that should just sync across the user's own devices with no account system. | Apple-ecosystem lockout (no Android or web), limited server-side querying, opaque public-database pricing, harder to debug than Firebase. |
| **Firebase (Firestore)** | Spark free tier is roughly 1 GB stored and about 50k reads, 20k writes, 20k deletes per day. Blaze is pay-as-you-go beyond that. | Cross-platform (iOS, Android, web), or you want auth, realtime, push, and analytics in one SDK and a fast start. | Read-heavy apps can get expensive on Blaze (billed per operation), Google-ecosystem dependency, and Firebase SDKs need a privacy manifest (see [app-store-reality](app-store-reality.md)). |
| **Custom backend** | Hosting cost plus your time. | You need full control, your own auth, cross-platform, or the data has outgrown BaaS pricing. | The most engineering effort. Usually overkill for an MVP. |

### The indie default

- **iOS only:** CloudKit. Often free, native, and it needs no account system.
- **Cross-platform, or you want auth and realtime out of the box:** Firebase.
- **Outgrowing BaaS economics, or you need control:** a custom backend, and usually only after validation.

## What this means for your spec

In section 8, name the main entities and their relationships, pick a storage option, decide on sync (and why), and state the offline behavior. The most common mistake is reaching for sync and accounts when the data lives happily on one device. If you do not actually need a user's data on a second device, skip sync entirely for the MVP. If you are iOS-only and do want cross-device sync, CloudKit gets you there without building or paying for a backend, and without forcing users to create an account.
