# 002: Skills and plugin packaging, not flat command files

## Context

A Claude Code workflow can be distributed several ways. As of 2026, custom commands have merged into Skills: a file at `.claude/commands/foo.md` and a skill at `.claude/skills/foo/SKILL.md` both create a `/foo` command, but Skills add capabilities, and plugins add distribution.

## Decision

Build each command as a Skill in `skills/<name>/SKILL.md`, and package the whole repo as a Claude Code plugin with `.claude-plugin/plugin.json` plus a `.claude-plugin/marketplace.json` so the repo is directly installable.

`new-spec` stays model-invocable, so describing a mobile app idea in a session can trigger the interview, which suits a tool whose whole point is helping people who do not know where to start. The other three (`refine-spec`, `reality-check`, `build-plan`) set `disable-model-invocation: true`, because they act on an existing spec and should run only when the user asks for them.

## Alternatives considered

- **Flat `.claude/commands/*.md` files.** Still supported, and simpler, but they cannot carry a folder of supporting files, lack frontmatter invocation control, and read as a 2024-era project. Rejected.
- **Skills without plugin packaging (clone only).** Works with `--plugin-dir`, but it loses the one-line marketplace install that adopters now expect, and it cannot be submitted to the community marketplace. We support clone-and-go as a fallback, but plugin packaging is primary.
- **An MCP server.** Overkill. The workflow is prompt-and-knowledge driven, with no external service to broker.

## Consequences

- Users get a one-line install (`/plugin marketplace add dabodamjan/app-idea-to-spec`) and a clone-and-go fallback.
- Each command owns a folder, and shared content lives in `knowledge/` and `templates/`, referenced through `${CLAUDE_PLUGIN_ROOT}`.
- The project can be submitted to the community marketplace and to `awesome-claude-code` for discovery.
- Commands are namespaced as `/app-idea-to-spec:<command>`. That is slightly more to type, but it puts the project name in every invocation, which suits a brand-building tool.
