# AGENTS.md

This file records project-specific conventions for maintaining `yan`'s homepage.

## Project Overview

- This repo is a simple static homepage.
- Main file: `index.html`
- CV file: `cv.tex`
- Image asset: `images/Photo.jpg`
- Most homepage edits happen directly in `index.html` (single-file style).

## Owner Profile (for content edits)

- Homepage owner: **Yan Ma**
- Research focus: reinforcement learning and foundation models, especially RL-based post-training for vision-language models.
- Affiliation context on homepage: Ph.D. student at Fudan University.

When editing profile text, preserve the existing academic/personal tone unless the user asks for a rewrite.

## Publications Section Architecture (Important)

`Selected Publications` has been refactored into:

- Filter buttons:
  - `First-author / Co-first` (default)
  - `All publications`
- A rendered container:
  - `#publications-rendered`
- A hidden single source of truth:
  - `#publications-templates`
  - each paper is a `<template class="pub-template" ...>`

Do **not** maintain two separate publication lists. Add/update each publication **once** in the template store.

## Publication Template Fields (Required)

Each publication template should include:

- `data-year="YYYY"`
- `data-first-author="true|false"`
  - `true` includes first-author and co-first papers
- `data-sort-date="YYYY-MM-DD"`
  - used for ordering within year (descending)

Example:

```html
<template class="pub-template" data-year="2025" data-first-author="true" data-sort-date="2025-05-18">
  ...
</template>
```

## Publication Sorting Rule (User Preference)

The user wants publication ordering to follow a date inferred from arXiv identifiers in a custom way.

For arXiv IDs like:

- `arXiv:2505.18129`

Use:

- `2025-05-18` as `data-sort-date`

That is, interpret:

- `YYMM` -> year/month
- the first two digits after the dot (`NNNNN`) -> approximate day

Notes:

- This is a **project-specific convention** for sorting, not the official arXiv date encoding.
- If the user provides an exact publication date, prefer that exact date.
- For non-arXiv items (conference/blog/tech report), use a user-provided exact date when available.

## Author Marking Conventions

Follow per-paper conventions exactly as provided by the user.

Examples already used:

- `†` for joint contribution (co-first)
- `*` for joint supervision
- In some papers, other symbols may be used (e.g. `♔` project lead)

Do not normalize symbols across all papers unless the user explicitly requests it.

## ANOLE / ICLR 2025 Blog Track Convention

The publication list treats:

- `ANOLE: ...`

as the primary entry, and folds the ICLR 2025 Blog Track item into the ANOLE entry as an extended blog version.

Do not re-split this into two separate publication entries unless the user asks.

## News Section Conventions

- News items are plain HTML list items under the `News` section.
- New entries should usually be inserted at the top (most recent first).
- Keep the existing tone/style and emoji usage unless the user requests a style change.

## Last Update

- Update the footer `Last Update:` line whenever substantive homepage changes are made, if the user asks for it.
- Use a human-readable English date format (e.g., `February 25, 2026`) to match the current page style.

## Editing Guidance

- Prefer minimal changes outside the target section.
- Keep the page single-file unless the user explicitly requests a refactor.
- Preserve current behavior of the publication filter JS unless intentionally modifying it.

## CV (`cv.tex`) Maintenance Conventions

- `cv.tex` should stay aligned with the homepage profile and publication updates.
- When updating the CV publication list, prioritize:
  - first-author / co-first papers
  - accepted papers (including accepted blog-track items)
- CV publications should be ordered by time (newest first), following the same project-specific sorting preference used on the homepage:
  - if exact dates are available, use them
  - otherwise, infer an approximate date from the arXiv identifier using the local `YYMM.xx -> YYYY-MM-DD` convention (with `xx` mapped to day)
- When homepage publication metadata changes (new papers, updated acceptance status, merged entries like ANOLE + ICLR Blog Track), check whether `cv.tex` should be updated in the same turn.

### CV Publication Formatting (Current Style)

- Keep publication entries in paragraph-style auto-wrap format (not rigid 3-line tabular blocks), to improve one-page density and readability.
- Current macro convention:
  - `\Paper{title+links}{venue_or_arxiv}{authors}`
  - `\PaperTLDR{title+links}{venue_or_arxiv}{authors}{tldr}`
- Author line should be on a separate line in smaller font.
- `\PaperTLDR` should hide the TLDR line when the 4th argument is empty (`{}`), i.e., no dangling `TLDR:` label.
- Use icon links in titles where applicable (e.g., `[\faFilePdf]`, `[\faGithub]`, `[\faGlobe]`) instead of plain `[PDF]` text.

### CV Publication Content Policy

- For preprint/technical-report style entries, show only arXiv ID style info (e.g., `arXiv:2602.01334`) without redundant year text.
- For accepted conference/journal entries, do not append arXiv ID in the venue line unless explicitly requested.
- Keep author lists consistent with `index.html`; fix discrepancies against homepage source of truth when conflicts appear.
- Underline `Yan Ma` where the user explicitly requests it on specific papers; do not globally enforce underlining on all entries unless requested.

### CV Sections and Length

- Keep CV concise (target one page unless user asks otherwise).
- When space is tight, prefer:
  - keeping key first/co-first papers
  - keeping concise experience bullets
  - reducing/removing optional TLDR lines on lower-priority entries

### Chinese CV (`cv_CN.tex`) Conventions

- `cv_CN.tex` should be kept in sync with `cv.tex` structure and key content unless user asks for divergence.
- Keep paper titles and author names in original English by default; translate narrative text (research interests, experience descriptions, TLDR text) to Chinese.
- If using class/template that already loads `hyperref`, avoid option clashes by passing options before class load:
  - use `\PassOptionsToPackage{hidelinks}{hyperref}` before `\documentclass`
  - avoid re-loading `hyperref` with conflicting options later.
