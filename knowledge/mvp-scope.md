# MVP scope

What a mobile MVP really includes, and the over-scoping traps that kill more indie apps than bad code does. This is the doc app-idea-to-spec leans on hardest, because scope is the decision you most need help making.

## What a realistic mobile MVP includes

- **One core loop, done well.** The single job the app exists to do, end to end, polished, plus the minimum scaffolding around it.
- A typical honest surface: minimal onboarding, the core feature, local persistence (or a backend only if sync is the point), basic settings, and, only if you are charging, a single paywall with one subscription (often plus a lifetime option).
- **Crash-free and review-compliant**, because the store gate is real: no dead buttons, a working demo account, a privacy policy, account deletion if you have accounts, privacy manifests for any third-party SDKs (see [app-store-reality](app-store-reality.md)).
- **Enough store presence to convert:** a real icon, three to five good screenshots, a tight title and subtitle (see [aso-basics](aso-basics.md)). The product and its listing ship together.

## The over-scoping traps

These are the ones to watch for, especially if you come from the web where shipping more feels free:

- **Building both platforms before validating one.** Ship iOS-native or one cross-platform target first. Do not carry two native codebases before you know the app is worth it.
- **Accounts, auth, and cloud sync when local-only would do.** A login system drags in account deletion, password reset, a backend, and privacy disclosures. If the data lives on one device, skip it. For Apple-only sync, CloudKit avoids an account system entirely (see [data-and-sync](data-and-sync.md)).
- **A custom backend before you need one.** A managed service or local storage covers most MVPs. A bespoke API is usually post-validation work.
- **The "real app" trappings layered on early.** Settings screens, theming, multiple subscription tiers, social and sharing, push notifications, widgets, a watch app, analytics dashboards. Each one adds review surface, bugs, and time before the core loop has a single happy user.
- **Treating "ship" as the finish line** instead of the start of the ASO and iteration loop.

Web reflexes worth unlearning: assuming instant deploys (there is a review gate), assuming a webview wrapper will pass (it gets rejected under the minimum-functionality rule), and underestimating the native asset and store-listing work.

## The rule of thumb

One platform, one core loop, local-first unless sync is the point, one paywall if monetized, and store-compliant. Everything else is a deliberate post-launch addition, not table stakes.

## What this means for your spec

This is why the spec separates "MVP features" (section 5) from "Explicitly cut for later" (section 6). The cut list is not a parking lot you feel bad about. It is the most important scope-protection tool you have, because a feature that is named and deferred stops haunting the build. When app-idea-to-spec sorts your features, anything that does not serve the core loop goes in section 6 with a reason. If section 5 is longer than section 6, look again.
