# ASC Assist

Agent skill for preparing App Store Connect listings with a developer. The shared instructions and reusable prompts are in English; conversation follows the user's language and listing content follows the requested store locales.

The package targets Claude, Codex and Antigravity through a portable `SKILL.md` core. Runtime automation depends on the tools, credentials and permissions available in the host. Cross-host execution has not yet been tested.

## Modes

| Mode | Behavior |
| --- | --- |
| Collaborative | Work through meaningful content, preview and store-change decisions together. Default. |
| Full-auto | Execute the initially authorized scope, pausing for required user decisions, credential handling, HTML asset approval and user-owned actions. |
| Audit-only scope | Inspect readiness and report without remote writes. |

Version 1 validates and associates an existing uploaded build. Compilation, signing and build upload require a separate request and workflow. The skill stops before review staging, submission, publication and release, even if asked to perform them.

The workflow covers conditional page/service preflight; source-document discovery or a confirmed reconstructed brief; exact locale coverage; authentic UI-based assets; a localized HTML approval preview; scoped ASC/provider changes; and final per-locale remote read-back.

## Install the skill folder

Copy the complete [`skills/asc-assist`](skills/asc-assist) folder, including its `references/`, into a skill location supported by the target host. Do not copy only `SKILL.md`.

| Host surface | Project installation |
| --- | --- |
| Claude Code | `.claude/skills/asc-assist/` |
| Codex | `.agents/skills/asc-assist/` |
| Antigravity App / CLI / IDE | `.agents/skills/asc-assist/`; verify support for the installed surface/version. |

These locations are documented by [Claude Code](https://code.claude.com/docs/en/skills), [Codex](https://developers.openai.com/codex/skills/) and [Antigravity](https://antigravity.google/docs/skills). Verify current host documentation for personal installs, cloud/web upload, discovery or reload behavior. No host-specific tool permissions or MCP connection is bundled.

## Example requests

```text
Use asc-assist in collaborative mode to prepare this app's next store version.
First inspect the project, explain any steps requiring my presence, and ask
about existing reference documents, web pages and target locales.
```

```text
Use asc-assist in full-auto mode for the app, version, locales and service
scope we have agreed on. Save the authorized preparation changes, obtain
approval for the HTML asset preview, and read back every locale. Leave
review staging and submission to me.
```

## Private operational data

Keep app-specific checkpoints, metadata, screenshots, previews, demo accounts and credential references in the app project's private workspace. Credential material belongs in secure storage outside the public repository. This repository distributes reusable instructions, not app data or credentials.

Official runtime references are listed in [`sources.md`](skills/asc-assist/references/sources.md). The authoring baseline is 2026-11-17; runtime requirements must be rechecked.

## Validation

[`evaluation-scenarios.md`](evaluation-scenarios.md) defines behavioral checks for later host trials. Static skill validation does not prove live browser/API operation. Cross-host trials remain pending.

## License

[MIT](LICENSE). Copyright (c) 2026 cemalguvenn.
