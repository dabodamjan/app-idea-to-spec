# Architecture

What app-idea-to-spec is built from and how the pieces fit. There is no runtime and no build step. app-idea-to-spec is a Claude Code plugin made of markdown and JSON.

## Tech stack and why

- **Claude Code plugin format.** The distribution unit is a plugin: `.claude-plugin/plugin.json` is the manifest, and `.claude-plugin/marketplace.json` makes the repo itself an installable marketplace so users can run `/plugin marketplace add dabodamjan/app-idea-to-spec`. Chosen because it is the current, lowest-friction way for people to install and update a Claude Code workflow, and because being plugin-native signals the project is current.
- **Skills, not flat commands.** Each command lives in `skills/<name>/SKILL.md`. In 2026, custom commands merged into Skills, and Skills give us a folder per command (for supporting files), frontmatter invocation control, and progressive disclosure. See [decisions/002-skills-over-flat-commands.md](decisions/002-skills-over-flat-commands.md).
- **Markdown knowledge base.** The `knowledge/` folder is plain markdown so it is both machine-readable (the skills load it) and human-readable (it is browsable on GitHub, which doubles as the project's credibility and its content).
- **No dependencies, no runtime.** Nothing to install, nothing to break on a platform update. The only moving part is the accuracy of the knowledge docs over time, which is why [CONTRIBUTING.md](../CONTRIBUTING.md) makes corrections the headline contribution.

## How the pieces fit

```
user runs /app-idea-to-spec:new-spec
        |
        v
skills/new-spec/SKILL.md   ->   reads templates/spec-template.md (the structure)
        |                        reads knowledge/*.md (the mobile-specific decisions)
        v
writes app-spec.md into the user's project
        |
        v
/app-idea-to-spec:refine-spec  ->  tightens it
/app-idea-to-spec:reality-check ->  pressure-tests it against knowledge/
/app-idea-to-spec:build-plan   ->  turns it into an ordered plan for Claude Code to build
```

The spec is the durable artifact the user keeps and edits. The skills are the interview and the transforms. The knowledge is what makes the output opinionated about mobile rather than generic.

## Paths inside skills

Skills reference sibling files (the template, the knowledge docs) through the plugin root variable `${CLAUDE_PLUGIN_ROOT}`. This keeps paths working whether the plugin is installed through the marketplace or run locally with `--plugin-dir`.

## Env vars

None. app-idea-to-spec makes no network calls of its own and stores no configuration.
