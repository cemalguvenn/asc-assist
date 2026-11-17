# Credentials and authority

Read this before entering credential-bearing pages, reading credential files, creating credentials, or moving keys between systems.

## Ask for a handling choice

For each applicable provider, ask in the user's language whether they prefer:

1. **User-managed:** the user generates, downloads, stores, and enters credentials. Provide exact destination/purpose and verify a non-secret status result afterward. Do not inspect the credential material.
2. **Assisted:** the agent may handle specified credentials through an available authorized browser, API, or secure file reference. Agree on the provider/account, key type, operations, receiving service, safe storage destination, and retention first.

Record the choice per provider and allow mixed choices. An assisted choice is not blanket permission to create every type of key, revoke existing keys, export a password vault, or transfer credentials to another provider. A handling preference alone does not authorize a specific key creation unless its scope was also agreed.

Do not request secrets pasted into chat. Prefer user-selected secure file references, OS credential storage, authorized environment injection, or direct entry into the intended provider. Do not run commands that echo credentials into logs or place them in command-line arguments, HTML, artifacts, commits, screenshots, or checkpoint records.

If a credential would be exposed through a tool transcript, screenshot, or unsafe download location, use a safer mechanism or hand that step to the user. A browser session does not guarantee invisible secret handling. Inspect non-secret status areas rather than capturing credential screens.

## Classify the credential correctly

| Material | Treatment |
| --- | --- |
| Apple `.p8` private keys | Secret. ASC API and In-App Purchase keys serve different purposes despite sharing a file extension. Confirm the requested type, issuer, team, key ID and destination. |
| RevenueCat SDK/public key | Client configuration; use the appropriate platform/app key. Do not substitute a secret server key. |
| RevenueCat secret API key | Server-only secret with scoped permissions. Never embed in the app or preview. |
| AdMob application/ad-unit IDs | App identifiers rather than dashboard OAuth secrets. Verify correct app and environment; do not invent a secret API key requirement. |
| Firebase client config | Distinguish client configuration from admin authority. Inspect product configuration and restrictions; do not equate a client API key with a service-account private key. |
| Service-account keys, OAuth tokens, signing private keys | Secret. Handle only for the agreed operation and destination. Signing work is outside the default v1 scope. |
| App Review demo login | Sensitive access information. Use a restricted test account; keep it out of public previews and public repository files. |

Verify provider requirements in current official docs. Apple credentials may be downloadable only once; agree on secure storage before generating or downloading, and never regenerate or revoke an existing key just because its local copy is missing.

Keep credential material outside the project and public skill repository. Ignore rules are defense in depth, not a substitute for safe storage. Store only opaque secure references and non-secret validation results in local state. If exposure occurs, stop propagating the material, notify the user without reproducing it, and coordinate remediation; do not revoke shared production credentials without authorization.

## Other authority boundaries

Legal acceptance, identity verification, bank/tax submissions, and unresolved privacy/export/rights declarations remain user-owned. Prepare evidence and explain the precise action required; do not click acceptance on their behalf.

Commercial changes require a concrete approved decision: products, IDs, group placement, prices, trial/offer terms, territories and applicability. Full-auto may execute already approved choices. It must not invent business terms. Destructive operations and production configuration changes outside the agreed scope need specific authorization.

Review staging and review submission remain outside this skill regardless of credential access or mode.
