# AGENTS.md

This file records project-specific conventions for the current `visiting` branch.

# 当前进度

  你现在的进度已经比较清楚了。压缩上下文前，建议你保留这几个最关键的结论，下一轮直接从这里继续：

  - 当前有效稿子在 research_statement_v4.md
  - 这版只保留英文，前三段已经成形
  - 第三段主轴已经定成：
      - 不是论文罗列
      - 而是 RL 如何改变 multimodal models
      - 三个 scientific takeaways：
          - Rethinking: RL 改变训练动态与泛化，不只是分数
          - One RL: RL 可以在统一框架下同时塑造 reasoning 与 perception
          - Tool-Use: 当前收益更多来自 intrinsic improvement 和 harm reduction，而不是真正 tool mastery
  - 第三段结尾已经改成 necessity statement：
      - 对 long-horizon multimodal tasks，单靠当前观测下的 perceive/reason/act 往往不够
      - 需要预测后续状态演化和行动后果

  你下一段要写的是：

  - 我现在正在做什么
  - 并把它自然接到 predictive modeling

  我建议你下一轮继续时，先围绕这两个问题展开：

  1. 你“现在正在做的事情”更准确的上位描述是什么
      - audio-video pretraining
      - multimodal generative modeling
      - future-state prediction
      - world modeling
        这几个词的层级要先理顺
  2. 这一段是要写成
      - current work paragraph
      - 还是 future agenda paragraph
        这会决定语气强弱

  如果你回来继续，我建议我们直接从 research_statement_v4.md 往下写第四段

## Current Scope

- Active work on this branch is centered on:
  - `visiting/`
  - `cv.tex`
  - `cv_CN.tex`
- Do not treat homepage-source conventions for `index.html`, publication filters, news items, or footer updates as active requirements on this branch unless the user explicitly asks.

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
- Main research focus: reinforcement learning and foundation models, especially RL-based post-training for vision-language / multimodal models

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
