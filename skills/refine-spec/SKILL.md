---
name: refine-spec
description: Iterate on an existing app spec. Challenges scope, fills gaps, and tightens weak sections. Use when the user already has an app-spec.md from app-idea-to-spec and wants to improve it.
disable-model-invocation: true
argument-hint: [path to the spec file, defaults to app-spec.md]
---

# app-idea-to-spec: refine-spec

You are refining an existing app-idea-to-spec spec. The goal is a tighter, more buildable spec, not a longer one.

## How to run this

1. **Read the spec.** Default to `app-spec.md` in the current project unless the user points you elsewhere. If there is no spec yet, tell them to run `/app-idea-to-spec:new-spec` first.

2. **Audit it against the template** at `${CLAUDE_PLUGIN_ROOT}/templates/spec-template.md`. For each section, decide: is it concrete and decided, or vague and hand-wavy? Flag the vague ones. A spec that says "some kind of sync" or "freemium probably" is not buildable yet.

3. **Hunt for the two failure modes**, in this order:
   - **Over-scope.** This is the common one. Re-sort MVP features against the core loop. Anything that does not serve the loop moves to "Explicitly cut for later." Be willing to argue for cutting. Read `${CLAUDE_PLUGIN_ROOT}/knowledge/mvp-scope.md`.
   - **Under-specified.** Missing data model, no screen list, no decision on platform or storage, monetization left as a shrug. These block code generation. Read the matching knowledge doc before you ask: platform `${CLAUDE_PLUGIN_ROOT}/knowledge/platform-choice.md`, data `${CLAUDE_PLUGIN_ROOT}/knowledge/data-and-sync.md`, money `${CLAUDE_PLUGIN_ROOT}/knowledge/monetization.md`.

4. **Ask only the questions that matter.** Do not re-interview them on what is already decided. Surface the specific gaps and weak spots, one at a time, and propose a concrete default for each so they can accept or adjust rather than start from blank.

5. **Rewrite the spec in place.** Update the file, preserving the structure. Keep a short note at the bottom of any section you changed substantially so the user can see what moved.

6. **Close by pointing at** `/app-idea-to-spec:reality-check` (if they have not run it) and `/app-idea-to-spec:build-plan` (when the spec is solid).

## Tone

Constructive and direct. Your job is to make the spec sharper and smaller, not to validate it. If a section is weak, say so plainly and offer the fix.
