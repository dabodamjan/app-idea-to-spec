# app-idea-to-spec

**Purpose:** an open-source Claude Code plugin that turns a mobile app idea into a build-ready spec, which Claude Code then builds from. Spec-driven development, made for mobile.

## Operating model

app-idea-to-spec is a plugin made of markdown and JSON. There is no build and no runtime. The commands are Skills in `skills/`, the spec structure is `templates/spec-template.md`, and the encoded mobile knowledge is in `knowledge/`. Users install it with `/plugin marketplace add dabodamjan/app-idea-to-spec` or run it locally with `claude --plugin-dir ./app-idea-to-spec`.

## Read first

- [README.md](README.md): what it is and how users install and run it
- [docs/architecture.md](docs/architecture.md): how the pieces fit
- [docs/decisions/](docs/decisions/): why it is built this way
- [knowledge/](knowledge/): the mobile playbook the skills rely on

## Hard rules for this repo

- **No em dashes** in any file. Use periods, commas, or restructure. House style, and it matches the author's voice.
- **No emojis** in docs or knowledge, unless there is a functional reason.
- **Keep it mobile-specific.** Generic spec-driven tooling already exists. app-idea-to-spec earns its place through App Store, StoreKit, SwiftData, ASO, and the rest. Do not dilute that into generic PRD advice.
- **Cut before you add.** New spec sections and commands have a high bar. The tool models scope discipline, so the repo should too.
- **Cite current facts.** No invented numbers, no stale advice as current. If something is unsettled, say so in the doc. The `knowledge/` docs are the part most likely to go stale, so date facts and link primary sources.
- **Public repo hygiene.** This is public. No personal or business content beyond the author's public brand (name, dabo.dev, shipped apps). No personal emails in manifests.

## Testing locally

```
claude --plugin-dir .
```

Then run `/app-idea-to-spec:new-spec` and walk a sample idea through to a spec.
