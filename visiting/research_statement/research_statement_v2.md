# Research Statement

## Working Title

Toward Multimodal Agents that Perceive, Reason, Act, and Predict

## Core Paragraph

I view multimodal agents as goal-directed systems that work in partially observed multimodal environments, where they must perceive what is happening, reason about it, act to gather useful information, and predict what will happen next. Such systems are needed to complete long-horizon multi-modal tasks that unfold through interaction, such as multi-step computer use, decision-making from video or audio streams, and embodied tasks like robotics or driving.

A central question motivating my research is how multimodal agents can not only perceive, reason, and act based on current observations, but also predict how the world will evolve after their actions. So far, my work has mainly focused on the first part of this question, using reinforcement learning (RL) to improve reasoning, perception, and tool-use actions in multimodal foundation models. More recently, I have begun to extend this agenda toward the predictive side by learning from large-scale audio-video data to anticipate future observations and longer-term outcomes. In the long run, I hope these two directions will help move multimodal systems beyond passive understanding toward agents that act with foresight, adapt through interaction, and improve over time.

## Third Paragraph Draft (CN)

围绕第一段提出的总问题，我过去主要从多模态模型如何基于当前观测完成感知、推理与行动这一部分入手，研究一个更基础的科学问题：RL 究竟如何改变 multimodal models。我的研究表明，这种改变并不只是 benchmark 分数的提升，而会体现在模型的训练动态、能力协同与行为机制上。

首先，在 reasoning-centric setting 中，我通过从零搭建训练流程并配套标准化评测，系统研究了 RL 如何影响模型的训练动态与泛化行为。相关结果表明，RL 的收益不仅体现在最终性能上，也伴随着长度、反思和泛化行为上的系统性变化；尤其值得注意的是，不同 random seeds 本身就会显著影响这些训练动态，而在视觉数学任务上，RL 相较于高质量监督的 SFT 仍表现出更强的泛化能力。随后，我进一步关注 RL 能否在单一框架下同时作用于 reasoning 与 perception。为此，我们设计了一个联合推理与感知的统一训练框架 V-Triune，用来支持不同类型推理与感知任务的稳定联合训练，并在 8 个任务（4 个推理、4 个感知）上验证了联合训练的互补收益。

更进一步，在 vision tool-use RL 的场景中，模型的行动不再仅仅决定单步输出，而开始影响其后续能够获取到的观测信息。在这个更具 agentic 特征的设定下，我进一步研究模型究竟学到了什么；相关分析表明，当前工具使用 RL 的收益更多来自 intrinsic capability improvement 和 tool-induced harm 的降低，而非真正意义上的工具掌握。

整体来看，这些工作共同构成了我对这一问题的一条持续研究主线：RL 正在逐步重塑多模态模型基于当前观测进行感知、推理与行动的方式。对于我而言，理解这种重塑的机制及其局限，正是进一步从基于当前观测的决策学习走向对未来演化的预测建模的重要起点。
