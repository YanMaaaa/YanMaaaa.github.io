# CV Revision Notes

这份文档整理了当前 `cv.tex` 面向美国高校 `visiting student` 申请时的修改建议，按讨论点逐条记录，后续可以逐项确认后再改正文。

## 1. Research Interests 是否可以写 2025 年经历

可以写。

问题不在于提到 `2025`，而在于当前这段文字放在 `Research Interests` 里时，时间性稍强，同时最后一句容易让人误解你已经完全从 `RL for VLM` 转向别的主题。

当前更合理的策略是：

- 保留 `In 2025, ...` 作为对过去一年研究经历的总结
- 同时把最后一句改成更加连续的表述
- 明确说明你是在原有 `RL-based post-training for VLMs` 主线基础上，进一步扩展到 `multimodal generative model pre-training`

建议改写方向：

```tex
My research lies at the intersection of reinforcement learning and multimodal foundation models. In 2025, I worked extensively on RL-based post-training for vision-language models, including single-visual tasks, multi-visual tasks, and agentic vision tool use. I am currently expanding this line toward pre-training for multimodal generative models, especially large-scale audio-video pre-training.
```

这样可以同时保留：

- 你过去一年的代表性研究轨迹
- 你当前正在做的 `audio-video pre-training`

## 2. 是否应该在对外 CV 中写 submission score / rejection history

当前建议是：

- `5444` 这类 submission score 不建议直接放在对外 CV 中
- `rej -> to COLM` 这类 rejection history 更不建议出现在对外 CV 中

理由不是因为分数不高，而是因为这些信息的信号不够稳定：

- 不同会议和不同 reviewer 的打分尺度差异很大
- 不是所有老师都知道 `5444` 的含义和相对位置
- `rejection history` 是一个低收益且容易产生负面解读的信息
- 会让读者把注意力从论文内容转移到投稿过程

更稳的 CV 信号通常是：

- 已发表 venue
- arXiv
- 一作 / 共一
- 代码
- 研究主题本身

如果确实希望保留一些“质量不错”的信号，建议考虑更中性的表达，例如：

```tex
\textit{arXiv:2505.18129}\tiny[under revision]
```

目前更建议把 `5444` 这类信息留在：

- 套磁邮件中针对个别老师单独提及
- 或者不写

## 3. citation / GitHub stars 应该展示在哪里

这些指标不算炫耀，前提是表达方式足够客观，不做宣传式表述。

推荐的放置位置有两个：

### 方案 A：名字下方加一行 `Selected Impact`

例如：

```tex
Selected Impact: 300+ citations, 500+ GitHub stars across open-source projects.
```

这是最直接也最自然的位置。

### 方案 B：放在 Research Interests 后面

也可以放在研究兴趣段落后单独补一行影响力概览，但整体视觉上不如方案 A 清晰。

当前建议：

- `citation`
- `GitHub stars`

适合放在 CV 里。

`X 平台阅读量 10W+` 不太建议放在 CV 主体中，因为它更像传播指标，不是最标准的学术信号。这个更适合放在：

- homepage
- 套磁邮件
- research summary

## 4. Experience 应该写多细

当前建议是：

- 不要写成长段过程描述
- 也不要只写得非常抽象
- 最合适的粒度是：`作用域 + 技术对象 + 角色`

每一条经历只需要回答三个问题：

- 你在做什么系统 / 问题
- 它服务于什么模型 / 方向
- 你承担什么角色

对当前经历，可以考虑改成下面这种密度：

- `Shanghai Innovation Institute - Intern; leading a large-scale audio-video data pipeline for multimodal generative model pre-training`
- `MiniMax & HailuoAI - Intern; worked on multimodal foundation models and video generation pipelines for M-series and Hailuo models`
- `Shanghai AI Laboratory - Intern; worked on text generation and unified multimodal model training`

这样有几个好处：

- 不会写得失控
- 技术对象更清楚
- 对 visiting 老师来说，信号更强

## 5. Programming Skills 应该如何调整

当前建议：

- 保留 `NeoVim` 和 `Tmux`
- 但不要让它们和核心研究技术栈处在同等权重

更合理的分法是：

- `Languages`
- `ML / Systems`
- `Tools`

建议形式：

```tex
\textbf{Languages}{: Python, Bash, LaTeX, Markdown}
\hfill
\textbf{ML / Systems}{: PyTorch, FSDP, Verl, vLLM, SGLang}
\hfill
\textbf{Tools}{: Git, NeoVim, Tmux}
```

这样既能保留个人习惯，也不会让读者误以为编辑器和终端工具比训练框架更重要。

## 当前不直接改 `cv.tex` 的原因

这份文档先作为讨论底稿，目的是逐条确认方向，再对 `cv.tex` 做实际修改，避免反复调整正文。

后续可以按下面顺序推进：

1. 先确认 `Research Interests` 的最终定位
2. 再决定是否展示 `citation / GitHub stars`
3. 再统一 `Experience`
4. 最后更新 `Programming Skills`
