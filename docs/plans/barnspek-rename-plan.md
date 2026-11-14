# Barnspek rename — website

**Status (2026-11-14): Local rename, migration, verification and independent review complete; final candidates and publication remain.**

Part of the [coordinated rename](../../../docs/plans/barnspek-rename-plan.md); its checkpoint and publication boundaries apply.
No product behaviour is being added. Preserve unrelated work and historical receipts.

## Starting point

- Branch: `main`; commit: `0f85fea94f8d3e12642879bbff66c09ce114c8bf`.
- Latest local tag: `none`; initial working tree: clean.
- Existing origin: `git@github.com:rogerbarnfather/barn-website.git`. No remote has been changed.
- Version: Documentation-only repository; no package tag.

## Scope

Update current product names, links, shared CSS tokens/header/footer and matching screenshot captions. Retake actual screenshots containing the old name; preserve useful image filenames and historical provenance. Keep shared assets byte-identical across all four sites and verify relative links plus responsive light/dark rendering. Keep existing public site destinations.

Dependencies to check, including development dependencies: Shared website assets and verified Barnspek package/site destinations.

## Baseline and verification

Use the [Stage 1 receipt](../../../docs/plans/barnspek-rename-stage1.md) and its immutable baseline archive.
Compare the relevant CLI/API output, copied specification, generated files and GUI pages;
only the documented identity/path changes are expected. Do not rewrite the old baseline.
Run this repository's configured CI and mutation gates before completion, without lowering
thresholds; documentation-only sites use link, shared-asset and browser checks instead.
Run process/terminal/browser checks where the changed surface warrants them. Rebuild any
changed committed frontend bundle. The coordinated stable archive rehearsal must pass too.

Stop before publication. Obtain the final coordinated release authorisation; preserve all old
tags and histories. Fold this plan into repository history once the rename is complete.
