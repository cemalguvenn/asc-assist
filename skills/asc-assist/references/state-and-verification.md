# State, resumption and completion

Keep a local operational checkpoint under the app project's `.asc-assist/`, separate from this public skill package. If that path is unsuitable, agree on a writable local location. Before writing private operational material, ensure it is excluded from Git or use an external private path; confirm with the environment's ignore mechanism. A `.gitignore` pattern does not untrack existing files.

Use a concise structured record such as `state.json` and a human-readable `verification.md`. Do not generate empty files for unused stages. Store metadata drafts, assets and HTML previews in that private workspace, not in the public skill source.

## Minimum checkpoint information

- Target account/team/app/bundle ID/platform/version/build; mode and output language.
- Exact primary and requested locales, device families, active service projects and operation scope.
- Reference document paths/revisions and facts requiring confirmation.
- Per-provider credential-handling choice, authorized operations and opaque secure references; never credential values.
- Approval records: what was approved, user response, revision, locale coverage and when it was given.
- Per-item expected output, current status, observed evidence, source URL/path, observation time, and unresolved blocker/owner.
- Completed remote changes, prior values when available, and the next safe action.

Use these item states consistently:

| State | Meaning |
| --- | --- |
| `unknown` | Required fact or evidence has not been obtained. |
| `drafted` | Local content or asset exists; approval or saving may remain. |
| `approved` | User approved the specific artifact/scope; it may not be saved. |
| `saved` | Remote persistence was reported or observed; full read-back comparison remains. |
| `verified` | The relevant check passed against observed evidence, including remote read-back for saved items. |
| `blocked` | A dependency, decision, permission or capability prevents completion. |
| `not-applicable` | Excluded with an evidence-based reason. |

A user report can be recorded as such but is not agent-observed read-back. Do not promote it to independently verified without sufficient observable evidence. Record manual completion and its evidence source explicitly.

## Resume safely

On resume, read existing state, confirm target identity, and inspect remote changes made since the last checkpoint. Preserve current user edits. Reuse valid approvals and handling choices; do not ask the same questions again solely because the session changed.

Revalidate assumptions affected by a new build, locale, source-document revision, service configuration or changed tool access. Compare uncertain writes before retrying. After a repeated failure with no new evidence or safe alternate path, stop that operation, record the blocker, and continue independent work. Avoid blind polling and repeated mutations.

## Completion criteria

The preparation can be called verified only when:

1. Required preflight facts and pages are verified or explicitly not applicable.
2. Reference facts are established, and reconstructed or materially changed facts have user confirmation.
3. Every requested locale/device/product item is covered; intentional exceptions are visible and accepted.
4. The approved HTML revision corresponds to the final uploaded asset set.
5. Intended remote fields and assets have been read back and compared, including saved screenshot processing/order.
6. The correct existing build is associated and applicable provider checks have evidence.
7. Remaining user-owned final submission is clearly identified, and the observed final review/release state has not been changed by this skill.

If required access is absent, deliver the prepared local package with an incomplete status and a concrete handoff. A completed local package is not completed remote preparation. Pending mandatory decisions remain pending regardless of mode or elapsed time.

In the user's language, deliver a concise result with preparation status, target app/version/build, locale coverage, service outcomes, saved-versus-verified differences, blockers/owners, artifact paths and manual next steps. State that nothing was submitted for review. Do not include secrets or imply guaranteed App Review acceptance.
