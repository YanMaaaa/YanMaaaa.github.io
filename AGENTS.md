# AGENTS.md

This file records project-specific conventions for the current `visiting` branch.

# 当前进度

  你现在的 visiting 材料已经基本成套。压缩上下文前，建议优先保留这些最新结论：

  - 当前有效的 research statement 源文件在：
      - `visiting/research_statement/research_statement_v4.tex`
      - 对应 PDF 在 `visiting/official_pdfs/Research_Statement_0416.pdf`
  - 当前有效的 CV 材料在：
      - `cv.tex`
      - `cv_CN.tex`
      - 对应 PDF 在 `visiting/official_pdfs/CV_EN.pdf` 和 `visiting/official_pdfs/CV_CN.pdf`
  - `index.html` 已同步更新：
      - homepage intro-text 已与 research statement 主线对齐
      - profile links 中已加入 `Research Statement`
  - 当前统一的研究主线已经定为：
      - multimodal agents in partially observed environments
      - past line: RL changes multimodal models
      - current / future line: predictive multimodal learning from video
  - research statement 的核心逻辑已经收束为：
      - current observations -> action changes information -> future states / action outcomes
      - 过去工作围绕 RL 对 perception / reasoning / tool use 的影响
      - 当前工作围绕 video data foundations for predictive multimodal learning
  - 当前最值得推进的不是继续重写 statement，而是：
      - final consistency check across CV / homepage / statement
      - cold email template
      - professor-specific fit notes
      - modular 6--8 slide base deck
      - short visiting proposal when needed

## Current Scope

- Active work on this branch is centered on:
  - `visiting/`
  - `cv.tex`
  - `cv_CN.tex`
  - `index.html`
- Do not treat unrelated homepage maintenance, publication filters, news items, or footer updates as active requirements unless the user explicitly asks.

## `visiting/` Folder Purpose

- `visiting/` stores planning and preparation materials for Yan's visiting-student applications.
- Typical contents include:
  - target school / professor lists
  - application material notes
  - progress tracking
  - research statement drafts
  - outreach-related drafts

## Owner Context

- Owner: **Yan Ma**
- Current context: Ph.D. student at Fudan University
- Main research focus:
  - multimodal agents in partially observed environments
  - RL-based post-training for vision-language / multimodal models
  - predictive multimodal learning from video

When editing research or application materials, preserve a direct academic tone unless the user asks for a rewrite.

## CV (`cv.tex`) Conventions

- `cv.tex` is an active document on this branch and should stay aligned with current visiting-application materials.
- Keep the CV concise; default target is one page unless the user asks otherwise.
- Prioritize:
  - first-author / co-first papers
  - accepted papers
  - representative ongoing works when relevant for visiting applications

### CV Publication Formatting

- Keep publication entries in paragraph-style auto-wrap format, not rigid multi-line tabular blocks.
- Current macro convention:
  - `\Paper{title+links}{venue_or_arxiv}{authors}`
  - `\PaperTLDR{title+links}{venue_or_arxiv}{authors}{tldr}`
- Author line should stay on a separate line in smaller font.
- `\PaperTLDR` should hide the TLDR line when the 4th argument is empty (`{}`).
- Use icon links in titles where applicable (e.g. `[\faFilePdf]`, `[\faGithub]`, `[\faGlobe]`).

### CV Content Policy

- For preprint / technical-report style entries, use concise arXiv-style venue lines without redundant year text unless the user asks otherwise.
- For accepted conference / journal entries, do not append arXiv IDs in the venue line unless explicitly requested.
- Underline `Yan Ma` only when the user explicitly requests it on specific entries; do not globally enforce underlining.

### Chinese CV (`cv_CN.tex`) Conventions

- `cv_CN.tex` should generally stay aligned with `cv.tex` in structure and key content unless the user asks for divergence.
- Keep paper titles and author names in original English by default; translate narrative text to Chinese.
- If the class/template already loads `hyperref`, avoid option clashes by passing options before class load:
  - use `\PassOptionsToPackage{hidelinks}{hyperref}` before `\documentclass`
  - avoid re-loading `hyperref` with conflicting options later.

## Writing Guidance for Visiting Materials

- Favor clear, direct academic prose over polished but vague language.
- Prefer defensible claims over broad or fashionable wording.
- When drafting research statements, avoid turning paragraphs into paper lists; organize them around research questions and scientific takeaways.
- Keep terminology consistent across drafts, especially around:
  - multimodal agents
  - multimodal foundation models
  - prediction / world modeling
  - RL / post-training
