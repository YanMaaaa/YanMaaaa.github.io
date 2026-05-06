# AGENTS.md

This file records project-specific conventions for the current `visiting` branch.

# 当前进度

你现在的 visiting 材料已经基本成套。后续上下文优先保留这些最新结论：

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
- 当前统一研究主线：
  - multimodal agents in partially observed environments
  - past line: RL changes multimodal perception, reasoning, and acting through tools under current observations
  - current / future line: video as a scalable foundation for predictive multimodal learning
- research statement 的核心逻辑已经收束为：
  - current observations -> action changes information -> future multimodal states / action outcomes
  - 过去工作围绕 RL 对 perception / reasoning / tool use 的影响
  - 当前工作围绕 video data foundations / video curation for predictive multimodal learning

## 当前 Slides 进度

- 当前正在推进 visiting research talk slides：
  - 内容源文件：
    - `visiting/slides/research_talk_content_notes.md`
    - `visiting/slides/research_talk_base_deck_outline.md`
  - 当前 Beamer 主入口：
    - `visiting/beamer/main.tex`
  - 已拆分出的 Beamer section：
    - `visiting/beamer/opening.tex`
    - `visiting/beamer/past_work.tex`
  - 当前选择：
    - 使用 `moloch` Beamer 模板，而不是先做 PPTX
    - 不运行编译，编译由用户自己执行
    - `main.tex` 保留 preamble、title page、TOC、section inputs
    - 每个主要 section 尽量拆成独立 tex，再由 `main.tex` input
- opening section 已基本完成：
  - `Past Work Overview`
  - `From Multimodal Models to Multimodal Agents`
  - `From Current Observations to Prediction`
  - `Research Agenda`
  - opening 叙事：先建立 past work credibility，再区分 model vs. agent，再解释 prediction 为什么对 long-horizon multimodal agents 必要，最后用 `Main_Figure1.png` 收束 research agenda。
- past work section 已基本完成，文件在 `visiting/beamer/past_work.tex`：
  - Paper 1: visual reasoning RL
    - 核心问题：如何让关于 multimodal reasoning RL 的经验结论更可信？
    - 重点展示 full learning trajectories、training behavior、generalization beyond SFT。
  - Paper 2: unified multimodal RL for perception + reasoning
    - 核心问题：multimodal RL 能否 jointly shape perception and reasoning？
    - 重点展示 matched-budget positive transfer、heterogeneous-task RL framework、Dynamic IoU、ViT freezing、source-level diagnostics、new-domain scaling。
  - Paper 3: vision tool-use RL / MED
    - 核心问题：what does vision tool-use RL really learn?
    - 当前结论：intrinsic drift dominates; tool-use RL mainly reduces tool-induced harm; future tool-use RL should target correction on the moving failure set.
    - Paper 3 main slides 已形成：MED overview、measure intrinsic/tool-induced drift、explain/diagnose term decomposition、gain vs. harm、factor diagnosis、future tool-use RL target。
- 当前 deck 不算 backup 约 27 页；后续可以先完成 full deck，再压缩出 12-14 页和 8-10 页版本。

## 下一步

- 下一步优先进入 current / future work section，而不是继续扩展 past work：
  - 从 past work under current observations 过渡到 long-horizon multimodal agents that require prediction。
  - 设计 current project slide：
    - `Video as a Scalable Foundation for Predictive Multimodal Learning`
    - 项目标题候选：`The Curse of Conventional Wisdom: Which Video Curation Practices Matter for World Model Pretraining?`
    - 科学问题：which video segmentation / filtering / annotation / organization practices affect what world models learn, which capabilities they affect, and how they affect predictive multimodal learning。
  - 设计 future program slide：
    - video data foundations 是近程切入点
    - integrating prediction into multimodal agent systems 是长期目标
  - 设计 final closing / visiting-fit slide：
    - what I bring: RL/post-training empirical analysis, multimodal agent framing, video-data project execution
    - what I seek: video/world-modeling/agent-system collaboration environment, experimental platform, data/model resources

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
