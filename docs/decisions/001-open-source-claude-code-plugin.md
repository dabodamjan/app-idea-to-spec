# 001: Open-source Claude Code plugin, not a paid SaaS

## Context

The idea started as a SaaS: a web app that turns a mobile app idea into an MVP spec, with a subscription. On inspection that shape had three structural problems:

- **Retention.** Writing a spec is a once-per-project act. People would spec an app, then leave for months. That does not sustain a subscription.
- **Thin wrapper.** "Paste an idea, get a structured spec" is close to a single good prompt. As a paid product that is a weak moat. As free tooling it is simply the format.
- **Wrong side of the AI wave.** Tools that generate working apps from a prompt are collapsing the spec step. A paid spec-document tool swims against that current.

## Decision

Ship app-idea-to-spec as a free, open-source Claude Code plugin. The spec it produces is the input to AI code generation (Claude Code builds from it), not a document you copy into a separate tool.

## Alternatives considered

- **Paid SaaS web app.** Rejected for the three reasons above.
- **Free web app (no Claude Code).** Lower friction to try, but it would not ride the codegen workflow, and it would compete with general AI chat for the "structure my idea" job without a real edge.
- **A private internal tool.** Rejected because the point is reach and reputation, which require it to be public.

## Consequences

- **Upside.** No retention problem (a free tool does not need you to return), the "it is mostly good prompts and encoded knowledge" property becomes a feature rather than a weakness, and positioning it as the spec layer that feeds Claude Code turns the AI wave into a tailwind. It also serves as top-of-funnel for the author's other work.
- **Cost.** Revenue is indirect (reputation, audience, top-of-funnel), not direct. Success depends on distribution and on the quality of the encoded knowledge, not on a billing relationship.
- **The moat is the knowledge and the author**, not secrecy. That is an accepted trade: the mobile-specific playbook is given away, and the value is being the person who shipped real apps and encoded the playbook.
