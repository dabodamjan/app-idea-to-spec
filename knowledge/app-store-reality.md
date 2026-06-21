# App Store reality

The part web newcomers underestimate most. Review is a human gate, not a deploy, and a handful of rules will block your submission if the spec ignores them. Current as of 2026.

## The process and timeline

Initial review is usually fast now. Most apps are reviewed within roughly a day or two, sometimes longer for a new or complex app. There is no exact guaranteed time, so do not plan around a hard SLA.

If you get rejected, a reply in the Resolution Center typically turns around in about a day or two. Escalating to the App Review Board takes longer, on the order of a week or two.

Expect at least one rejection round on a first app. A large fraction of first submissions get rejected, almost always for something preventable. Plan for it rather than being surprised by it.

## The most common rejection reasons

1. **Crashes and broken functionality.** Dead buttons, blank screens, a feature that does not work on the reviewer's device. The single most common reason, and almost always preventable. Reviewers test on real devices.
2. **Privacy and data transparency.** Inaccurate privacy labels, undisclosed data use, or sharing data with third parties (now explicitly including AI services) without consent.
3. **Privacy manifest or SDK signature failures.** See the hard requirement below. This is the most common binary-level rejection of the current era.
4. **Missing account deletion.** If your app lets users create an account, it must offer in-app account deletion. This has been required since June 30, 2022, and it still trips people up. With Sign in with Apple you must revoke the token through the REST API.
5. **In-app purchase compliance.** Digital goods and services must use Apple's in-app purchase system. You cannot send users to an external site or a third-party processor for digital purchases (subject to the unsettled external-link litigation in [monetization](monetization.md); the default rule still stands).
6. **Minimum functionality and spam (Guideline 4.2).** Thin apps, and web-wrapper-only apps that are "just a website in a shell," get rejected. A frequent newcomer trap.
7. **Design and metadata issues.** Human interface guideline violations, placeholder content, a broken demo account, incomplete metadata.

## Hard requirement: privacy manifests

Since May 1, 2024, new and updated apps that include a third-party SDK on Apple's "commonly used SDKs" list must ship a privacy manifest (`PrivacyInfo.xcprivacy`) and a valid SDK signature, and must declare approved reasons for using certain "required reason" APIs. Apps that do not comply are rejected at submission.

This hits common SDKs like Firebase, analytics, and ad SDKs. If you use Expo, React Native, or Flutter, the plugin ecosystems handle much of this, but you still have to verify each native dependency complies.

## What web and vibe-coding newcomers underestimate

- **Review is a human and device gate, not `git push` to prod.** There is no instant deploy. A rejection can cost days. Hotfixes are not instant either. You can mitigate with over-the-air JavaScript updates (Expo, React Native) or remote config, but native binary changes still go through review.
- **Apple's rules are real product constraints, not suggestions.** Forced in-app purchase for digital goods (and the cut), mandatory account deletion, privacy manifests, App Tracking Transparency.
- **You need real assets and accounts before you can even submit.** Working demo or login credentials for the reviewer, a privacy policy URL, accurate data-collection disclosures, screenshots at the required sizes, a support URL. These block submission.
- **A paid Apple Developer Program membership is required** to ship at all (currently $99 per year).
- "It works on my machine" is not approval. Reviewers test fresh installs, offline states, and edge cases.

## What this means for your spec

Section 11 of the spec exists for exactly this. Walk the list and write down what applies: do you have accounts (then you need deletion), do you use third-party SDKs (then you need a privacy manifest), what is your privacy policy URL, and what demo path lets a reviewer reach the core feature. Catching these in the spec is free. Catching them at submission costs you a rejection round.
