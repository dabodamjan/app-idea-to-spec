# Contributing to app-idea-to-spec

Thanks for wanting to help. app-idea-to-spec is small on purpose, so contributions that keep it sharp are more useful than ones that make it bigger.

## The most useful contribution

The mobile platforms move fast. The [`knowledge/`](knowledge/) docs are the part most likely to go stale: a framework hits a new major version, Apple changes a rule, a pricing tier shifts. If you spot something out of date, open an issue or a pull request with a source. Corrections with a link to a primary source (official docs, a release note, an Apple developer page) get merged fastest.

## Ground rules

- **Keep it mobile-specific.** Generic spec-driven-development tooling already exists. app-idea-to-spec earns its place by knowing about App Store review, StoreKit, SwiftData, ASO, and the rest. Contributions should deepen that, not dilute it.
- **Cut before you add.** A new spec section or command has a high bar. The default answer to "should this be in the MVP spec" is usually no, and the tool should model that discipline.
- **Cite current facts.** No invented numbers, no stale advice presented as current. If a fact is unsettled or sources disagree, say so in the doc rather than faking precision.
- **No em dashes in docs.** House style. Use periods, commas, or restructure.

## How to propose a change

1. Open an issue describing the change and why it helps.
2. For knowledge corrections, include the source.
3. For new behavior, keep the pull request focused on one thing.

## Local development

Clone the repo and run Claude Code against it directly:

```
git clone https://github.com/dabodamjan/app-idea-to-spec.git
claude --plugin-dir ./app-idea-to-spec
```

The commands live in `skills/`, the spec structure in `templates/spec-template.md`, and the encoded knowledge in `knowledge/`.
