# Paper 1 叙事笔记：Multimodal Reasoning RL

对应论文：*Rethinking RL Scaling for Vision Language Models: A Transparent, From-Scratch Framework and Comprehensive Evaluation Scheme*

## 在整套 Talk 里的位置

Opening 已经提出总问题：**What does RL actually change in multimodal models?**

Paper 1 是这个问题的第一个具体回答，范围收窄到 **multimodal reasoning RL / visual reasoning RL**。它不应该被讲成一个单纯的 SOTA 或性能提升工作，而应该被讲成一个方法论起点：如果只看 final score，很难可信地判断 RL 到底改变了模型什么。

## 为什么不额外加 Past Work 背景页

不需要在 Slide 5 前再单独加一页 `Past Work Overview`。

原因是：
- Opening 的 `Research Agenda` 已经讲过 past line 和 current/future line。
- Section page 已经完成了从 agenda 到 past work 的章节切换。
- Paper 1 自己的第一页可以直接承担背景和方法论 framing。
- 如果再加一页 overview，会重复 opening 的信息，拖慢进入第一篇工作的节奏。

口头过渡可以很短：

> I start with my past work on multimodal RL. The first question is not only whether RL improves final scores, but how we can make claims about what RL changes trustworthy.

## 主线拆页

Paper 1 当前建议用 4 页主线：

1. **How Can We Make Claims About Multimodal Reasoning RL Trustworthy?**
2. **What Does RL Change During Multimodal Reasoning Training?**
3. **How Does RL Reshape Training Across Models and Datasets?**
4. **Does RL Generalize Better Than SFT?**

这 4 页分别承担不同职责，避免把所有实验图堆在一页。

## Slide 5：可信评估的 framing

标题：

> How Can We Make Claims About Multimodal Reasoning RL Trustworthy?

这一页的任务不是讲结果，而是解释为什么这篇工作要看 training trajectory。

核心逻辑：
- 当时 multimodal reasoning RL 很热，但不同工作使用不同代码栈和评估方式。
- 只看 final performance table 很难判断 RL 到底改变了什么。
- 因此这篇工作构建 transparent from-scratch VLM-RL framework，并评估 full learning trajectories。

当前 slide 句子：

> Early multimodal RL was hard to interpret from final tables and heterogeneous codebases. I built a transparent from-scratch VLM-RL framework and evaluated full learning trajectories on visual reasoning tasks.

图：
- `eval_scheme.pdf`

底部三个 evidence blocks：
- `Trajectory`: checkpoint-level dynamics
- `Behavior`: length and reflection metrics
- `Generalization`: pass@{1,k} evaluation

这页的 takeaway：

> To answer what RL changes, I first made the evidence more observable: trajectories, behavior, and generalization.

## Slide 6：单个 setting 中，trajectory 揭示了什么

标题：

> What Does RL Change During Multimodal Reasoning Training?

这一页是 Paper 1 对总问题的第一个具体回答。

它不负责证明跨模型/跨数据集的普遍性，也不负责证明 RL 比 SFT 泛化更好。这一页只说明：当我们看完整 trajectory 时，会看到 RL 改变了训练过程和输出行为，而不只是最终准确率。

当前 slide 句子：

> Trajectory-level evaluation reveals that RL changes how VLMs learn and respond, not only where final accuracy lands.

图：
- `qwen2.5_mmmath_training_metrics.pdf`

底部 observation tags：
- `Accuracy improves`
- `Length shifts`
- `Reflection changes`
- `Seeds matter`

这页需要注意：
- 图中没有 baseline，因此不要把这一页讲成 RL 相比 SFT 更好。
- 它能支撑的是：RL training 过程中，accuracy、response length、reflection metrics、seed variance 都有可观测 dynamics。
- 这一页的目标是让观众理解为什么 trajectory-level evaluation 比 final checkpoint 更有信息量。

这页的 takeaway：

> Looking across checkpoints reveals how RL changes learning and response behavior during training.

## Slide 7：跨模型和数据集的 dynamics 不一样

标题：

> How Does RL Reshape Training Across Models and Datasets?

这一页使用 2x2 training metrics 图，展示相同评价框架下，不同 backbone 和 dataset 的 RL-induced dynamics 并不完全一样。

图：
- `qwen2_mmmath_training_metrics.pdf`
- `qwen2.5_mmmath_training_metrics.pdf`
- `qwen2_geo3k_training_metrics.pdf`
- `qwen2.5_geo3k_training_metrics.pdf`

当前 slide 句子：

> The effects of RL are visible in trajectories, but their form depends on both model backbone and dataset.

这页的作用：
- 从 Slide 6 的代表性 setting 推广到 broader observation。
- 强调 RL 对模型行为的“塑造”不是单一模式。
- 支撑为什么不能只看一个 final checkpoint 或一个 setting。

这页的 takeaway：

> RL-induced dynamics vary across settings, so claims about RL should be trajectory-level and setting-aware.

## Slide 8：泛化结果

建议标题：

> Does RL Generalize Better Than SFT?

这一页才负责讲 RL vs SFT。

图：
- `qwen2_rl_sft.pdf`
- `qwen2_5_rl_sft.pdf`

建议句子：

> Compared with SFT on high-quality CoT supervision, RL shows stronger validation/test generalization.

这页和 Slide 6 的区别：
- Slide 6 看 RL training 内部发生了什么。
- Slide 8 比较 RL 和 SFT 的泛化表现。

这页的 takeaway：

> RL not only changes trajectories; it can also generalize better than SFT under the same visual reasoning setup.

## Backup 建议

可以准备两个 backup：

1. **Why Look Beyond Final Checkpoints?**
   - 用来解释 RL evaluation 为什么需要 trajectory。
   - 强调 checkpoints、seeds、behavior metrics 的必要性。

2. **Full Training Dynamics Across Settings**
   - 如果主线 Slide 7 太小，可以在 backup 放更大的 2x2 或逐张图。

## 总结句

Paper 1 最好用一句话收束：

> This work taught me to study multimodal RL not only by final scores, but by how training reshapes model behavior over time.

