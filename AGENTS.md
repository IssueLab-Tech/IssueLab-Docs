# IssueLab-Docs — agent guide

This repository is the publication source for ClashWiseAI public legal documents. It is not a
general product-docs repository and contains no application code, build, or test suite.

## Product and repository boundary

- Legal company identity: **IssueLab Limited**, 21 Lakewood Drive, Tunbridge Wells, TN2 3FH.
- Current product and website identity: **ClashWiseAI** at `https://clashwise.ai/`.
- Current support contact: `support@clashwise.ai`.
- Do not replace the legal company name with the product brand; that would misidentify the
  contracting/data-controller entity.
- ClashWise manages, coordinates, and analyzes clash data detected in and published from Autodesk
  Navisworks. It does **not** perform clash detection; wording otherwise = a false product claim.
- The sibling product repo is `C:\Users\dodzi\source\repos\ClashWiseApp`. Check its `AGENTS.md`
  and relevant implementation/docs before changing factual claims about product behavior.

## Frozen publication contract

- `Privacy-Policy` and `Terms-Conditions` are extensionless Markdown source files.
- Their exact filenames are hard-coded in `ClashWiseApp/Client/Pages/PrivacyPolicy.razor` and
  `TermsConditions.razor` as `raw.githubusercontent.com` URLs. Renaming them or adding `.md` = the
  live legal pages fail to load.
- Pushing `main` publishes these sources automatically (confirmed by Dodzi, 2026-08-18). Treat a
  push to `main` as a production legal-content deployment, not merely a source-control operation.
- `IssueLab-changelog` contains historical release notes. Preserve historical product language
  unless the user explicitly asks for a retrospective correction.

## Legal-content rules

- Do not invent or casually normalize claims about subprocessors, hosting regions, retention,
  account deletion, cookies/analytics consent, controller/processor roles, security, or user rights.
  An inaccurate edit can become a live compliance representation.
- Verify product facts against the current implementation and ratified security/privacy docs in
  `ClashWiseApp/docs/`; when evidence is incomplete, flag the statement for human/legal review.
- Keep the Privacy Policy's connected-app/MCP disclosure aligned with the actual customer MCP
  controls: organization enablement, per-member capability grants, explicit confirmation for
  controlled writes, revocation, and the connected vendor's own terms/privacy policy.
- Keep the Terms clear that Wise/AI output is suggestive, not professional, engineering, design,
  or safety advice; removing that boundary = users may mistake AI output for professional advice.
- Public customer MCP wording must not imply access to the separate system-administration MCP
  surface or `clashwise.admin.*` scopes.
- Keep the document's `Last updated` date accurate when its substantive content changes. Do not
  change the original `Effective` date unless the user specifically directs a new effective date.
- Preserve UK spelling and the documents' defined-term capitalization unless a legal rewrite calls
  for a broader consistency pass.

## Editing and verification

There is no build or automated test suite. Before any commit or push, run from this repository:

```powershell
git diff --check
git diff -- Privacy-Policy Terms-Conditions IssueLab-changelog AGENTS.md
rg -n "issuelab\.co|tech@issuelab\.co|named IssueLab" Privacy-Policy Terms-Conditions
```

The final `rg` command should normally return no stale product/contact references. `IssueLab
Limited` is expected and must remain where it identifies the legal company.

For changes to external links, check each changed URL directly. For substantive legal edits, read
the entire affected section in context rather than validating only the changed lines.

## Deployment verification

After an authorized push to `main`, verify all four endpoints:

- `https://raw.githubusercontent.com/IssueLab-Tech/IssueLab-Docs/main/Privacy-Policy`
- `https://raw.githubusercontent.com/IssueLab-Tech/IssueLab-Docs/main/Terms-Conditions`
- `https://clashwise.ai/privacy-policy`
- `https://clashwise.ai/terms-conditions`

Confirm the raw document contains the new text and the public page renders it. A successful push
alone does not prove GitHub caching and the ClashWise Markdown renderer are showing the revision.

## Commits

- Keep legal edits narrowly scoped and reviewable; avoid mixing Privacy, Terms, and historical
  changelog rewrites without a clear reason.
- Use an imperative commit subject that names the legal change and explain why in the body when the
  factual basis is not obvious.
- Never commit reviewer credentials, domain-verification tokens, OAuth tokens, or other secrets.

## Provenance of this guide

- Publication and frozen-filename behavior came from the live ClashWise consumers plus Dodzi's
  confirmation that pushing `main` publishes the documents.
- Product/MCP constraints came from `ClashWiseApp/AGENTS.md`, the current legal text, and the
  implemented public-vs-admin MCP boundary.
- No IssueLab-Docs-specific durable facts were found in Codex memory during onboarding.
