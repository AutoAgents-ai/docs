# Documentation Update Standards

This repository uses `AGENTS.md` as the single source of truth for release-note and product-feature documentation updates.

## Scope

- Applies to:
  - Version release notes (currently `changelog`)
  - Product feature documentation (future `guide` content)
- Applies to all supported languages:
  - Simplified Chinese (`zh-hans`)
  - English (`en`)
  - Japanese (`ja-jp`)

## 1) Release Notes Standard (changelog)

### Files

- `zh-hans/changelog/product-updates.mdx`
- `en/changelog/product-updates.mdx`
- `ja-jp/changelog/product-updates.mdx`

### Required synchronization

- Any new version after release (for example `v2.0.3.0`) must be added to all three files in the same change set.
- Do not update only one language first and leave others missing.

### Required structure

For each language file:

1. Add the new version to frontmatter `filters`:
   - `label` and `value` must both use the exact version string.
   - Insert newest version at the top of the filter list.
2. Add a new `<Update ...>` block:
   - Place newest version block at the top (before older versions).
   - Use `tags={["<version>"]}`.
   - Use `rss.title = "Agentify <version>"`.
   - Provide concise `rss.description` in the target language.
3. Keep section taxonomy aligned across languages:
   - New features
   - Enhancements/optimizations
   - Bug fixes
   - Localized headings can differ in wording, but should represent the same meaning.

### Content quality rules

- Language must be natural and user-facing (not raw machine translation).
- Terminology should stay consistent across languages (for example: Agent, Workflow, NL2SQL, Token, Prompt).
- Keep each bullet focused on one change point.
- Prefer user impact wording ("what changed + why it matters").

## 2) Product Feature Documentation Standard (guide, future)

When new product features are introduced and require standalone documentation:

### Language parity

- Create or update all language versions in the same change set whenever possible.
- If one language must be delayed, add a temporary placeholder note and schedule completion immediately (avoid silent omissions).

### Path and naming consistency

- Keep equivalent paths aligned by locale namespace:
  - `zh-hans/...`
  - `en/...`
  - `ja-jp/...`
- Keep slugs and information architecture consistent across locales for discoverability and maintenance.

### Content consistency

- Preserve the same functional scope across languages:
  - Feature purpose
  - Prerequisites/permissions
  - Steps or usage flow
  - Expected behavior/results
  - Limits/caveats if applicable
- Examples can be localized, but behavior descriptions must remain equivalent.

## 3) Delivery Checklist (for every doc PR)

- [ ] New version exists in all changelog locale files.
- [ ] `filters` and `<Update>` are both added and version strings match exactly.
- [ ] Newest entries are ordered at top in all locales.
- [ ] Terminology is consistent across zh-hans / en / ja-jp.
- [ ] No locale is missing required release or feature documentation.
- [ ] Markdown/MDX formatting renders correctly.

## 4) Priority Rule

If there is any conflict between old habits and this file:

- Follow `AGENTS.md`.
- Update `AGENTS.md` first when process changes, then apply the new process in docs updates.
