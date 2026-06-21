# app-idea-to-spec

**Turn a mobile app idea into a build-ready spec for Claude Code. Spec-driven development, made for mobile.**

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Claude Code](https://img.shields.io/badge/Claude%20Code-plugin-d97757)

app-idea-to-spec is a Claude Code plugin. You describe an app idea, it runs a guided interview, and you walk away with a structured spec that Claude Code can actually build from. It is opinionated about mobile on purpose: App Store rules, monetization, data and sync, and the scope discipline that decides whether an app ever ships.

If you know GitHub's Spec Kit, this is that idea aimed squarely at mobile. Generic spec tools leave the platform, the store, and the monetization calls to you. app-idea-to-spec makes them, because those are the decisions that actually sink a first app.

It works whether you have shipped ten apps or none. If you are coming from the web or from vibe-coding, it walks you through the mobile decisions you do not know you need to make yet. If you are an indie iOS dev, it skips the basics and fights your urge to over-scope.

<!-- TODO: add a demo GIF here (idea in, spec out, ~20s). This is the single highest-leverage thing in the README. -->

## Install

The one-line way, through the marketplace:

```
/plugin marketplace add dabodamjan/app-idea-to-spec
/plugin install app-idea-to-spec
```

Or clone it and run it locally, so you can read every file before you enable anything:

```
git clone https://github.com/dabodamjan/app-idea-to-spec.git
claude --plugin-dir ./app-idea-to-spec
```

(If you do not see the `/plugin` command, update Claude Code.)

## Quickstart

```
/app-idea-to-spec:new-spec
```

Or just tell Claude Code you want to spec a mobile app idea, and app-idea-to-spec will offer to start. Either way you answer a few questions, one at a time, and app-idea-to-spec writes `app-spec.md` into your project. Hand that file to Claude Code and start building.

## What's inside

| Command | What it does |
| --- | --- |
| `/app-idea-to-spec:new-spec` | Guided interview that turns your idea into a structured spec |
| `/app-idea-to-spec:refine-spec` | Iterate on an existing spec, challenge scope, fill the gaps |
| `/app-idea-to-spec:reality-check` | Pressure-test the spec against what mobile devs underestimate |
| `/app-idea-to-spec:build-plan` | Turn the spec into an ordered build plan for Claude Code |

## Two ways in

**New to mobile.** You can build a UI, but you have never shipped to the App Store. app-idea-to-spec explains the decisions that bite first-timers: review is a human gate, not a `git push`. Digital purchases have to use Apple's system. Privacy manifests, account-deletion rules, what an app MVP actually includes. You get stronger defaults and more explanation.

**Already shipped apps.** You know the ropes. app-idea-to-spec moves fast, skips the basics, and spends its energy where it matters for a veteran: cutting scope, naming what to defer, and turning the spec into something Claude Code builds cleanly the first time.

## How it works

The slow part of building an app in 2026 is not writing the code. It is deciding what to build, and then not building the other ten things you thought of.

A vague prompt gives you a vague app. app-idea-to-spec front-loads the decisions that a code generator cannot make for you (platform, data model, monetization, the one core loop) into a spec, then hands that spec to Claude Code as the source of truth. The spec is the artifact you keep and edit. The code is the thing it builds.

That is spec-driven development. app-idea-to-spec is the version of it that knows about mobile.

## The knowledge behind it

The [`knowledge/`](knowledge/) folder is a working playbook, not filler. It is what makes app-idea-to-spec opinionated instead of generic, and it is readable on its own:

- [platform-choice](knowledge/platform-choice.md): native Swift vs Expo vs Flutter vs KMP, with a decision framework
- [data-and-sync](knowledge/data-and-sync.md): SwiftData vs Core Data, CloudKit vs Firebase vs a custom backend
- [monetization](knowledge/monetization.md): StoreKit 2, RevenueCat, paywalls, the 15% Small Business Program
- [app-store-reality](knowledge/app-store-reality.md): review, rejections, privacy manifests, the rules that block submission
- [aso-basics](knowledge/aso-basics.md): what actually drives discovery and downloads
- [mvp-scope](knowledge/mvp-scope.md): what an MVP really includes, and the over-scoping traps

## Example

See [`examples/`](examples/) for a full run: a rough idea turned into a finished spec.

## Why I built this

I kept getting the same DM. Some version of "I have an app idea, how do I actually turn it into something I can build?" I have shipped a handful of apps over the years (Itemlist, QRGenie, BarcodeCraft), and the honest answer was never about code. It was about the decisions you make before the code, and the ones you talk yourself out of making.

So I put that conversation into a tool. app-idea-to-spec is the thing I wish I could have sent in reply to every one of those DMs. It is free and open source. If it helps you ship, tell me what worked and what broke.

More of what I build is at [dabo.dev](https://dabo.dev).

## Contributing

Issues and pull requests are welcome, especially corrections to the knowledge docs as the mobile platforms change. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
