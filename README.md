# ASC Assist

Prepare your App Store Connect listing with Claude, Codex, or Antigravity—from project checks and localized copy to approved screenshots and final verification.

ASC Assist is an instruction-based agent skill. It guides your agent using the tools and access available in your environment. Its instructions are in English; it communicates in your language and creates listing content in your chosen store locales.

**Review submission always stays with you.** The skill stops before **Add for Review**, review submission, publication, or release, in every mode—even when asked to perform those actions.

## Contents

- [What it does](#what-it-does)
- [Requirements](#requirements)
- [Installation](#installation)
- [First use](#first-use)
- [Choose a mode](#choose-a-mode)
- [Example prompts](#example-prompts)
- [The preparation workflow](#the-preparation-workflow)
- [Credentials and your involvement](#credentials-and-your-involvement)
- [Outputs and verification](#outputs-and-verification)
- [Update or uninstall](#update-or-uninstall)
- [Troubleshooting](#troubleshooting)
- [Repository layout](#repository-layout)
- [Validation and contributions](#validation-and-contributions)
- [License](#license)

## What it does

| Area | Preparation work |
| --- | --- |
| Project readiness | Identify the app, existing build, supported devices, integrations, and missing prerequisites. |
| Web pages | Check applicable privacy, support, marketing, terms, deletion, and advertising-domain resources; draft missing content from verified facts. |
| Reference documents | Read your product and store documents, or reconstruct a brief from the project and ask you to confirm it. |
| Store copy | Prepare metadata that reflects real features, branding, and paid/free boundaries. |
| Assets | Use authentic app UI and available creative tools to prepare assets, then create a localized HTML approval preview. |
| Localization | Track exact locale variants across copy, screenshots, and applicable purchase/subscription fields. |
| Services | Check applicable RevenueCat, AdMob, Firebase, and other provider configuration. Unused services do not require setup. |
| Remote changes | Save authorized preparation changes and associate the correct existing uploaded build. |
| Final verification | Read saved content back from App Store Connect for every requested locale and report mismatches or blockers. |

Version 1 works with an **existing uploaded build**. Compilation, signing, archive creation, and build upload require a separate explicit request and workflow. Website deployment, new business terms, and unrelated production changes also need their own scope.

## Requirements

Start with a supported agent host and access to your app project or relevant documents. You can begin an audit or draft preparation before every integration is connected.

| Capability | When it is needed |
| --- | --- |
| Project/document access | Understand app behavior, dependencies, branding, and store requirements. |
| Web research | Check current Apple/provider requirements and public web pages. |
| Authenticated ASC API, connector, or browser | Inspect, save, and independently verify store data. The account needs suitable permissions for each operation. |
| Provider access | Inspect or change the service projects actually in scope. |
| Image/rendering tools and real UI sources | Produce and visually inspect assets. Existing assets or a file-based handoff can be used when generation tools are unavailable. |
| HTML preview capability | Inspect the localized asset mockup before you approve it. |

Installing the skill does **not** connect accounts, grant permissions, install SDKs, or provide an image-generation service. Missing capabilities lead to a precise manual handoff; they must not be reported as completed automation.

## Installation

The commands below use a POSIX-compatible shell. Install the **entire `skills/asc-assist` folder**, including `references/`. Cloning this repository alone does not install the skill into your app project.

### 1. Download the source

```bash
mkdir -p "$HOME/.local/share"
git clone https://github.com/cemalguvenn/asc-assist.git "$HOME/.local/share/asc-assist"
```

You can also download the repository ZIP from GitHub and copy the skill folder manually.

### 2. Install into your app project

Open a terminal in the root of the **app you want to prepare**, not the downloaded skill repository. These are fresh-install examples; if an `asc-assist` destination already exists, use the [update procedure](#update-or-uninstall) instead of merging copies.

**Claude Code:**

```bash
mkdir -p .claude/skills
cp -R "$HOME/.local/share/asc-assist/skills/asc-assist" .claude/skills/
```

**Codex or Antigravity:**

```bash
mkdir -p .agents/skills
cp -R "$HOME/.local/share/asc-assist/skills/asc-assist" .agents/skills/
```

Codex and Antigravity can use the same project copy. If you also use Claude Code, install its copy separately and keep both copies at the same revision.

For an optional personal installation, copy the complete skill folder to the appropriate location instead:

| Host | Project folder | Personal/global folder |
| --- | --- | --- |
| Claude Code | `.claude/skills/asc-assist/` | `~/.claude/skills/asc-assist/` |
| Codex | `.agents/skills/asc-assist/` | `~/.agents/skills/asc-assist/` |
| Antigravity App / CLI / IDE | `.agents/skills/asc-assist/` | `~/.gemini/config/skills/asc-assist/` |

Local discovery and installation locations are documented by [Claude Code](https://code.claude.com/docs/en/skills), [Codex](https://developers.openai.com/codex/skills/), and [Antigravity](https://antigravity.google/docs/skills). Check your installed surface/version; web and cloud sessions may load skills differently from local hosts.

### 3. Verify discovery

Confirm that the destination contains both `SKILL.md` and `references/`. Open your app project in the agent host and select or mention the skill:

- **Claude Code:** invoke `/asc-assist`.
- **Codex:** select the skill from the available skills UI, or mention `$asc-assist` where skill mentions are supported. In CLI/IDE sessions, `/skills` can help locate it.
- **Antigravity:** mention `asc-assist` by name; App and CLI also support `/asc-assist`. Use the IDE's Customizations menu to inspect active skills.

These invocation methods are described in the [Claude Code](https://code.claude.com/docs/en/skills), [Codex](https://developers.openai.com/codex/skills/), and [Antigravity](https://antigravity.google/docs/skills) guides. If discovery is stale, start a fresh session or use the host's supported reload mechanism.

## First use

Invoke the skill in your app project and describe the release you want to prepare. Write in your preferred language. Have these details ready where known; the skill should inspect available evidence before asking you to repeat information:

- Target app, Apple team/account, editable store version, and existing uploaded build.
- Primary store locale and exact additional locale variants—not only a language count.
- Product/store reference document names, paths, or links. It is fine if these do not exist yet.
- Existing public page URLs, screenshots, logo, fonts, and brand references.
- Active services and their project identities, including individual Firebase products.
- Available asset tools or authorized Codex/Antigravity connections.
- Preferred mode and which remote preparation changes you authorize.

You do not need to supply credentials upfront. The skill must first explain likely user-presence requirements and ask how you want applicable credentials handled.

A first session should establish the target, available capabilities, readiness checks, missing inputs, and the next safe preparation step. If documents are missing, it should inspect the project, draft a requirements brief, and ask you to confirm reconstructed facts.

## Choose a mode

| Mode | How it works | Best fit |
| --- | --- | --- |
| **Collaborative** — default | Work together on the reference brief, source-language copy, localized asset preview, and concrete remote changes. | First-time preparation or close control over positioning and content. |
| **Full-auto** | Agree on the target and scope once. The agent prepares, localizes, saves authorized changes, and reads them back without repeating routine approvals. | A clear brief, known integrations, and an established release process. |
| **Audit-only scope** | Inspect readiness and create local findings without remote writes. | Understanding gaps before committing to preparation. |

Full-auto still waits for your credential-handling choice, confirmation of reconstructed or materially changed facts, approval of the actual localized HTML asset preview, and user-owned actions. It also asks when a new decision falls outside the agreed scope. Existing approval is reused while its target, revision, locales, and operation scope remain valid.

## Example prompts

Use these after selecting the skill, or include the invocation syntax supported by your host. Replace sample identities and paths with your own; do not include secret values.

### Start collaboratively

```text
Use asc-assist in collaborative mode to prepare this app's next App Store version.
Inspect the project first. Explain which steps will require my presence, then
check applicable web pages, integrations, reference documents, and build readiness.
Ask me for the primary store locale and additional locales before creating assets.
```

### Provide documents and locale scope

```text
Use asc-assist for the existing uploaded build of My App, version 1.2.0.
The reference documents are docs/product.md and docs/store-brief.md.
The primary locale is en-US; also prepare Turkish and Arabic (Saudi Arabia).
Confirm their exact current ASC locale codes before generating content.
Include listing copy and screenshots for the app's supported device families.
RevenueCat is active; AdMob and Firebase are not used.
Confirm actual app UI language support before designing localized screenshots.
```

### Run full-auto within an agreed scope

```text
Use asc-assist in full-auto mode for the app, team, version, build, locales,
and service projects already confirmed in this conversation.
I authorize saving the agreed metadata, approved screenshot set, and existing
build association to that version. Keep current product prices and offer terms.
Ask for my credential-handling choice before accessing credential material.
Get my approval of the localized HTML preview before uploading its assets.
Read back every requested locale and report any mismatches. Leave review
staging, submission, publication, and release to me.
```

### Audit or resume

```text
Use asc-assist in audit-only scope. Inspect project and store readiness and list
missing pages, assets, locale coverage, build issues, and applicable service gaps.
Do not change remote state.
```

```text
Resume asc-assist from this app project's .asc-assist checkpoint.
Confirm the target and inspect remote changes before continuing.
Reuse still-valid approvals and preserve unrelated edits made since the last run.
```

## The preparation workflow

1. **Preflight:** discover the app and integrations, check page readiness and access, explain human involvement, and record evidence-backed blockers.
2. **Reference brief:** read supplied documents or reconstruct the relevant facts from the project and obtain your confirmation.
3. **Locale and asset plan:** confirm exact locale variants, actual UI languages, device coverage, creative resources, and asset-generation access.
4. **Prepare:** draft and localize copy/assets, check applicable services, and build an HTML mockup using the proposed files. Obtain your preview approval.
5. **Save:** check the target and current values, then apply only authorized differences and associate the correct existing build. Preserve unrelated content.
6. **Verify and hand off:** read every requested locale back from ASC, compare it with approved artifacts, confirm build/service outcomes, and identify remaining manual work.

The agent can continue independent local work while a dependency is blocked. It must not mark a missing page, unavailable connection, pending decision, or unverified remote change as complete.

## Credentials and your involvement

Choose credential handling separately for each applicable provider:

- **User-managed:** you create, download, store, and enter credentials. The agent guides you and checks non-secret status evidence.
- **Assisted:** authorize specific credential operations, accounts, destinations, storage, and retention through available secure tools. Assistance is limited to that scope.

Mixed choices are supported. For example, you can manage Apple `.p8` files yourself while authorizing non-secret provider configuration checks. Never paste private keys or secret tokens into prompts, issues, previews, or repository files.

Login, 2FA, CAPTCHA, device/Keychain prompts, and certain one-time downloads may require your presence. Agreement acceptance, identity checks, banking/tax submissions, and unresolved legal declarations stay with you. The opening exchange should distinguish steps actually required for your app from merely possible ones.

Review staging/submission and release actions always stay with you, including review submission for in-app purchases, subscriptions, and external TestFlight builds. These boundaries are agent instructions; the package does not install a separate permission-enforcement service.

## Outputs and verification

Operational artifacts belong in the **app project's private workspace**, usually `.asc-assist/`, rather than in this public skill repository. Depending on the task, they include a checkpoint, confirmed brief, localized metadata, source/final assets, the HTML approval preview, and a verification report. File layout may vary; `state.json` and `verification.md` are suggested record names.

Before writing private operational material, the skill checks that it is excluded from Git or chooses an external private location. This repository's `.gitignore` is not automatically installed into your app project. Secrets must remain in secure storage outside the project.

| Item status | What it means |
| --- | --- |
| `drafted` | A local artifact exists. |
| `approved` | You approved the specific revision and scope. |
| `saved` | A remote save was reported or observed; read-back comparison remains. |
| `verified` | Observed evidence confirms the check, including read-back for saved items. |
| `unknown` / `blocked` | Evidence or a dependency is missing. |
| `not-applicable` | The item is excluded with a recorded reason. |

A successful upload or Save is not enough for verification. The agent must inspect saved fields, screenshot processing/order, URLs, and applicable product localizations for **every requested locale**. Listing localization does not imply that the app UI supports the same languages.

The final report should identify the app/version/build, locale coverage, service outcomes, saved-versus-verified differences, blockers and owners, artifact paths, and manual next steps. Its outcome is either **preparation incomplete** or **preparation verified; manual submission remains**. Neither guarantees App Review acceptance.

## Update or uninstall

To download source updates:

```bash
git -C "$HOME/.local/share/asc-assist" pull --ff-only
```

Review the changes, back up any local skill customizations outside host discovery folders, and replace each installed `asc-assist` folder with the latest complete `skills/asc-assist` folder. Avoid copying a new folder inside an old one. Refresh discovery and check that all hosts use the intended revision. Updating the source clone alone does not update installed copies.

To uninstall, remove only the installed `asc-assist` folder from each project/personal location and refresh discovery. App checkpoints and prepared assets are separate; retain or remove those deliberately. Removing the skill does not revoke provider credentials or undo remote store changes.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| Skill does not appear | Correct host location, exact `asc-assist/SKILL.md` nesting, project/workspace root, complete folder copy, and reload/new-session behavior. |
| Agent cannot read a reference | Install the sibling `references/` folder with `SKILL.md`; copying only the entrypoint is insufficient. |
| Different behavior between hosts | Compare installed revisions and available tools. Portable instructions do not imply identical browser/API/image access. |
| No ASC/provider connection | Connect an authorized capability or use a guided manual handoff. Remote work remains unverified without evidence. |
| No Codex/Antigravity generation connection | Use existing assets, available native tools, or a file-based asset brief/handoff. A product name alone is not a connection. |
| Full-auto pauses | Check for a required preview/fact/credential decision, user-owned action, or new scope. Full-auto retains these gates. |
| A locale is missing or shows fallback content | Check exact ASC locale mapping and coverage, then read the saved locale back; do not count silent fallback as completed localization. |
| Build cannot be associated | Check the existing build's identity, processing, eligibility, platform, and target version. Default v1 preparation does not upload a replacement. |
| A resume encounters manual edits | Re-read remote state and reconcile intended changes; preserve unrelated edits and avoid blindly replaying previous writes. |

## Repository layout

```text
asc-assist/
├── LICENSE
├── README.md
├── evaluation-scenarios.md
└── skills/
    └── asc-assist/
        ├── SKILL.md
        └── references/
            ├── preflight.md
            ├── credentials-and-authority.md
            ├── services.md
            ├── assets-and-localization.md
            ├── state-and-verification.md
            └── sources.md
```

The [skill entrypoint](skills/asc-assist/SKILL.md) defines the workflow. References supply stage-specific detail. [Official sources](skills/asc-assist/references/sources.md) identify where runtime requirements must be checked; Apple/provider rules are not frozen to the authoring baseline of 2026-11-17.

## Validation and contributions

Current validation covers skill structure and documentation consistency. Cross-host trials and live browser/API workflows remain pending. The package is a shared instruction set; no bundled API client, installer, or account connector is included.

Use [behavioral evaluation scenarios](evaluation-scenarios.md) for isolated host trials. Run only against permitted fixtures or explicitly authorized sandbox accounts, with no real secrets or review submissions.

For issues or improvements, include the host/version, installation scope, available tools, expected versus observed behavior, and a sanitized reproduction. Remove credentials, private customer data, demo logins, and private operational files before sharing. Keep reusable instructions in English and preserve user-language output, approval gates, and the no-submission boundary.

## License

[MIT](LICENSE). Copyright (c) 2026 cemalguvenn.
