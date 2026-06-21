# Example: a habit tracker

A short before-and-after. This is what a `/app-idea-to-spec:new-spec` run does to a typical over-scoped idea: it finds the one core loop and defends it.

## The idea, as it came in

> "I want to build a habit tracker. Users track multiple habits, see streaks, get reminders, compete with friends on leaderboards, earn badges, and there is a premium tier with detailed analytics and custom themes. Sync across devices. iOS and Android."

That is six or seven apps wearing a trench coat. Here is the spec app-idea-to-spec produced after the interview.

## The spec it produced (condensed)

**1. One-liner.** A dead-simple tracker for building one habit at a time, focused on the streak.

**3. Core loop.** Open the app, mark today's habit done, see your streak grow. That is the whole loop, and everything in the MVP serves it.

**4. Platform and tech approach.** iOS only, Swift and SwiftUI. The user knows Swift and wants the fastest path to a polished native feel. Android is deferred until the idea is validated on one platform. Minimum iOS 17.

**5. MVP features.**
- Create a habit (name, optional daily reminder time)
- Mark the habit done for today
- See the current streak and a simple calendar of done days
- One local daily notification

**6. Explicitly cut for later.**
- Multiple habits at once (validate single-habit retention first)
- Friends, leaderboards, badges (a whole social system, not a core loop)
- Custom themes (polish, not value)
- Android (second platform before validating one)
- Detailed analytics (there is nothing to analyze until people stay)

**7. Screens and navigation.** Today (the main screen), Habit setup (a sheet), History (calendar). Navigation stack with one modal sheet.

**8. Data and persistence.** Entities: Habit, Completion. Storage: SwiftData (iOS-only, modern OS floor). Sync: none in the MVP, the data lives fine on one device. Offline: fully offline, no network needed.

**9. Monetization.** Freemium. The MVP ships free to maximize installs and test retention. A soft paywall on long-term history and stats is named for a later version, not built now. No purchase plumbing in the MVP.

**10. Validation goal.** Tests whether a deliberately minimal single-habit tracker retains users. Validated when a meaningful share of installs are still marking the habit done after two weeks.

**11. Store readiness.** No accounts, so no account-deletion requirement. No third-party SDKs, so no privacy manifest needed yet. Needs a privacy policy URL and a reviewer demo path (the app opens straight to the core loop, so this is trivial).

**12. ASO starter.** Working title: "Streak: One Habit Tracker." Subtitle leads with the single-habit angle. Keyword direction around habit, streak, daily, routine.

## The point

The input was a year of work. The spec is a weekend. app-idea-to-spec did not invent anything the user did not want. It made them say out loud which one thing the app is for, then put everything else in section 6 with a reason. That is the job.
