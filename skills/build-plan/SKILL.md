---
name: build-plan
description: Turn a finished app spec into an ordered, buildable plan that Claude Code can execute. Use when the spec is solid and the user is ready to start building the actual app.
disable-model-invocation: true
argument-hint: [path to the spec file, defaults to app-spec.md]
---

# app-idea-to-spec: build-plan

You are turning a app-idea-to-spec spec into a build plan that Claude Code (or any capable coding agent) can execute. This is the handoff from "what to build" to "build it."

## How to run this

1. **Read the spec** (default `app-spec.md`). If it is missing, point them to `/app-idea-to-spec:new-spec`. If it is clearly under-specified (no data model, no screens, no platform decision), point them to `/app-idea-to-spec:refine-spec` first. A vague spec produces a vague plan.

2. **Produce an ordered, phased build plan.** Order matters: each phase should leave the app in a runnable state. A sensible default order, adapted to the spec:

   1. **Project setup.** Create the project for the chosen platform (Swift and SwiftUI, Expo, Flutter, etc.), the folder structure, dependencies, and any chosen SDKs (RevenueCat, Firebase) installed but not yet wired.
   2. **Data layer.** The data model and storage from the spec (SwiftData, Core Data, local, or a backend), with the main entities and relationships.
   3. **Core loop.** The screens and navigation that deliver the one core loop, end to end, with real data. Nothing else yet.
   4. **Supporting screens.** Only the MVP features from the spec, in priority order.
   5. **Monetization.** The paywall and purchase flow, if the spec has one. Wire up StoreKit 2 or RevenueCat per the spec.
   6. **Store readiness.** The blockers from the spec: account deletion if there are accounts, a privacy manifest if there are third-party SDKs, a privacy policy, an app icon and screenshots, and a working demo path for review.

3. **For each phase, write:** the goal, the concrete tasks, and what "done" looks like (something the user can run and see). Keep tasks specific to this app, using the real screen names, entities, and decisions from the spec. Reference `${CLAUDE_PLUGIN_ROOT}/knowledge/` docs where a phase depends on a mobile-specific detail.

4. **Keep the cut list visible.** Restate what the spec deliberately left out, so the build does not quietly grow it back.

5. **Write the plan** into the spec's "Build handoff" section, or to a separate `build-plan.md` if the user prefers. Then tell them how to start: open the plan in Claude Code and build phase by phase, checking each phase runs before moving on.

## Tone

Practical and concrete. The output is an execution plan, not advice. Order things so the app is runnable as early and as often as possible.
