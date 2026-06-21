# Monetization

How indie mobile apps make money in 2026: StoreKit 2 vs RevenueCat, paywall patterns that work, the 15% Small Business Program, and the regulatory picture. Decide this in the spec, not after you build.

## StoreKit 2 vs RevenueCat

**StoreKit 2** is free, modern (async/await Swift), and now genuinely pleasant, including SwiftUI paywall views. It is enough if you want to own everything and avoid a dependency.

**RevenueCat** earns its place when you want any of: cross-platform receipt validation, real-time analytics (MRR, trial-to-paid, churn) beyond what App Store Connect shows, server-side entitlements, or remotely configurable and A/B-testable paywalls that you can change without shipping an app update.

RevenueCat's pricing as of 2026 is free up to $2,500 in Monthly Tracked Revenue (full analytics, webhooks, and experiments included), then 1% of tracked revenue on paid plans. That 1% is on tracked revenue before Apple's commission, so the effective rate against your net is a little higher. Note this is the current model. Older "free up to $10k" numbers you might find are out of date, so do not quote them.

**The indie default:** start on StoreKit 2 if it is a single simple subscription, you are iOS-only, and you do not need much analytics. Reach for RevenueCat the moment you want paywall experimentation or cross-platform support. Its free tier covers you until you are actually making money.

## Paywall patterns that work

- **Free trial with full access** is the proven balance for most consumer subscription apps. A 3 or 7 day full-access trial that auto-renews unless cancelled is one of the highest-converting common patterns, though conversion varies a lot by category and price.
- **Soft paywall** (let users in, gate the premium features) lowers the entry barrier and raises install-to-explore. Good for broad consumer apps.
- **Hard paywall** (pay or start a trial before any use) raises install-to-trial but lowers trial-to-paid. It works for niche or professional tools where intent is already high.
- **Lifetime or one-time tier** alongside subscriptions is a common indie move. It captures subscription-averse buyers, usually offered as a higher-priced option next to the sub rather than instead of it.

The discipline to encode: the first paywall impression and the price anchoring matter more than the exact tier list, and you should test rather than guess. Remotely configurable paywalls (the main reason to use RevenueCat) are what make that testing cheap.

## Apple's cut and the Small Business Program

- Standard commission is 30%. The Small Business Program is 15% on paid apps and in-app purchases.
- Eligibility is up to $1,000,000 in proceeds (net of commission and tax) in the prior calendar year across all your apps. Developers new to the App Store also qualify.
- If you cross $1M mid-year, the standard 30% applies to future sales that year. Drop back below in a later year and you re-qualify for 15% the following year.
- You must enroll. It is not automatic. Nearly every indie qualifies and should be on 15%.

## The regulatory picture (changing, verify before relying on it)

This area is genuinely in flux. Treat the following as "current direction, confirm before you build a business model on it."

- **EU and the Digital Markets Act.** In the EU, Apple now permits alternative app marketplaces, sideloading, and external purchase links, under a restructured and much-revised fee model. As of 2026 it layers a Core Technology Commission (around 5% on digital goods) and tiered Store Services fees (about 10% or 13%) on top of, or in place of, the older per-install Core Technology Fee. Apple said the per-install fee would be phased out in favor of the commission, but that transition has not fully landed and the structure is still being contested with the European Commission. Most relevant if you target EU users, and very much a verify-before-you-rely-on-it area.
- **US external purchase links.** After an April 2025 ruling barred Apple from taking a commission on off-app purchases, a December 2025 appeals decision upheld part of it but reversed the zero-commission remedy and sent it back for a court to set a "reasonable" rate. As of mid-2026 this was still unresolved. So in the US, the rules on external-link purchases are unsettled and changing. Do not assume a fixed number.

For an MVP, the safe assumption remains the default: digital goods and services go through Apple's in-app purchase system. Build on that, and treat external-link strategies as an optimization to revisit once the legal picture settles.

## What this means for your spec

In section 9, write the model, the paywall type and exactly what it gates, the actual price points, and whether you will use StoreKit 2 or RevenueCat. Be honest in the validation goal ([mvp-scope](mvp-scope.md)) about whether an app like yours realistically earns subscription revenue, or whether you are adding a paywall out of habit. If you are not charging in the MVP, say so and cut all of the purchase plumbing from scope.
