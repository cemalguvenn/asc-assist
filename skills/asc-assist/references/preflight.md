# Preflight and intake

Use this reference when beginning or resuming an app preparation. Discover first, then ask focused questions about missing facts. Do not print secrets while inspecting configuration.

## Intake record

Capture:

- Working project, account/team, bundle ID, ASC app ID, new release or update, editable target version, and existing uploaded build identity.
- Operating mode, communication language, primary store locale, exact target locales, platforms and supported device families.
- Confirmed integrations, each provider's project/app identity, and which service changes are in scope.
- Names/paths/links of reference documents and existing assets.
- Web-page readiness, asset-generation resources, credential-handling choices, and currently known user-presence requirements.

If any target identity is ambiguous, stop its dependent writes and resolve it. Treat SDK presence as evidence of a dependency, not proof that a feature is active in production. Mark unused integrations not applicable with a reason.

## Conditional readiness matrix

| Area | Evidence to obtain | Consequence when unresolved |
| --- | --- | --- |
| Apple access | Correct team/app, role, editable version, account status and applicable agreements | Block affected remote changes; user handles account-holder actions. |
| Existing build | Bundle/version/build match, processing status, platform, device support and eligibility for the selected version | Do not associate an ambiguous or ineligible build; request an existing usable build. |
| Reference facts | Approved source documents or confirmed reconstructed brief | Block final claims that depend on uncertain facts. |
| Privacy | Actual app/backend behavior, enabled SDK modules, consent and tracking configuration | Do not infer disclosure answers from a dependency list alone. |
| Monetization | Paid/free behavior, products, entitlements, restore access, approved commercial choices | Block dependent product and subscription work. |
| Locales | Primary locale, exact variants, number of locales, copy/asset/product scope | Do not generate an assumed locale set. |
| Assets | Authentic UI source, brand resources, generation/rendering capability, device requirements | Prepare supported alternatives; report missing capabilities. |
| Web pages | Actual public URL and relevant content for each applicable page | A draft file does not count as a deployed page. |

## Web-page questions and verification

Ask whether the pages required by this app and its services are already ready, and request their URLs. Determine applicability rather than imposing every page on every app:

- Privacy policy and support/contact destination.
- Marketing/product page when used by the listing or a provider.
- Terms of use or EULA and subscription-related explanations when applicable; distinguish a custom EULA from Apple's standard EULA.
- Account/data deletion instructions and actual in-app deletion flow when account creation or applicable policy requires them. A web page does not replace a required in-app flow.
- Advertising domain and `app-ads.txt` when applicable to the actual AdMob setup; verify the domain relationship and published file using current provider guidance.

Fetch public pages when permitted. Check the final URL, accessibility without login, correct app/developer identity, working contact links, language coverage, and agreement with actual data practices. An HTTP success response alone is insufficient. Distinguish ASC requirements, provider requirements, and recommendations.

If pages are missing, prepare reviewable drafts from verified project facts and ask for unresolved organizational/legal details. Publishing needs deployment scope and available hosting; continue unrelated local work while it is unresolved.

## Presence notice

Explain likely handoffs before work starts. Update the notice when new requirements emerge. Do not demand that the user stay at the computer throughout routine preparation.

Authentication/2FA/CAPTCHA and OS permission prompts are user-controlled. Account-holder agreements, banking/tax and binding legal attestations are user-owned. One-time credential downloads require an agreed safe destination and handling choice. Content questions and HTML preview approval can usually be answered asynchronously.

## Scope boundaries

Inspect code to understand the product. Do not silently rewrite app functionality, install SDKs, change production security rules, compile/sign/upload a build, deploy pages, or alter pricing to make a preflight row pass. Prepare the necessary findings and seek the specific missing scope only when needed.
