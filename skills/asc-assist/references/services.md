# Applicable service checks

Read only the sections matching detected or confirmed services. For each check, record observed evidence, intended configuration, any mismatch, owner, and verification status. Validate current requirements against official sources; do not assume remembered dashboard navigation is current.

## App Store Connect and the existing build

Confirm team, app identity, platform, primary language, editable version and existing build. Check bundle ID, version/build number, processing/eligibility, supported devices and required capabilities. Associate only the confirmed eligible build. Do not compile, sign, archive, or upload by default.

Prepare applicable app/version fields: name, subtitle, description, keywords, promotional text, release notes for updates, support/marketing/privacy URLs, category, copyright and review contact/access notes. Check the current localization scope and limits of each field. Some information is shared at app level rather than version or locale level.

Check age-rating answers, content rights, encryption/export questions, privacy disclosures, availability and pricing where relevant. Derive answers from actual app/backend/SDK behavior and user-confirmed organizational facts. Do not make legal attestations from guesses. Confirm reviewer access for gated features without using a production customer account.

Inspect the current review/release state. Never stage or submit a review item or change release settings. Do not replace a submitted build or withdraw an existing submission.

## RevenueCat and Apple purchases

Confirm whether RevenueCat is active and which SDK/platform/store configuration is used. Map ASC product IDs and subscription groups to RevenueCat products, entitlements, offerings and packages. Check app/bundle identity, free/paid access, restore behavior and sandbox evidence where available.

Distinguish the Apple In-App Purchase `.p8` credential from the ASC API `.p8` credential and RevenueCat SDK/public versus secret/server keys. Check applicable credential validation status without exposing material. Determine shared-secret requirements from the actual StoreKit/SDK setup and current RevenueCat guidance; do not require every historical credential unconditionally.

Check applicable subscription/product localizations, durations, entitlement mappings, disclosure links and approved offer terms. Verify agreements/account readiness through status evidence; the user handles agreement, banking and tax actions. Product/price creation or changes require approved commercial scope. Never submit a purchase or subscription for review.

Sandbox validation can support a readiness check; it does not prove production payment behavior or replace evidence from the targeted build. Do not make real purchases or modify real subscriber entitlements as a test.

## AdMob and mediation

Confirm actual advertising use, app and ad-unit IDs, build environment, formats, mediation partners and relevant regions/audiences. Distinguish app IDs from dashboard credentials. Never click live ads or generate artificial traffic while testing.

Inspect the consent flow and enabled collection/tracking behavior, including applicable UMP, ATT, privacy options and child-directed settings. Do not infer that ATT is always required merely because the SDK is installed. Review Mobile Ads and mediation partner data disclosures for the actual versions and options.

Check the developer website/domain relationship and public `app-ads.txt` when applicable. Detect a launch dependency if a provider requires a live store URL before final linkage; report it as pending rather than claiming it is complete. Do not publish campaigns or change live ad behavior outside authorized scope.

## Firebase

Identify enabled products separately: Analytics, Crashlytics, Authentication, Messaging, Firestore, Storage, Remote Config, Performance, or others. Confirm intended project/app and bundle ID. Determine what the application actually sends or stores, collection defaults/overrides, account deletion, and relevant retention/user-linking behavior.

Use product-specific disclosure documentation together with code and runtime evidence. A privacy manifest does not automatically answer every privacy-label question. Distinguish client configuration from service-account/admin secrets.

Inspect readiness without silently changing production security rules, data retention, analytics collection, messaging, or Remote Config. Such changes can affect live users and require specific scope.

## Other providers

Apply the same evidence-driven process to other purchases, analytics, crash reporting, attribution, login, notifications, backend, AI or content services. Inspect actual modules and configuration, consult their official current docs, identify public/client identifiers versus secrets, and include their effect on privacy, consent, review access and required pages.

Do not install or configure an unused service to satisfy a generic checklist. Unsupported operations receive a precise manual handoff and remain unverified until checked.
