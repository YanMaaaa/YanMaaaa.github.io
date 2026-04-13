# Research Statement

## Working Title

Toward Multimodal Agents that Perceive, Reason, Act, and Predict

## Core Paragraph

A central question motivating my research is how multimodal agents can couple action with prediction, learning not only to act on current observations but also to anticipate how the world evolves after action. So far, my work has mainly focused on the action side of this question, using RL-driven post-training to improve reasoning, perception, and tool use in multimodal foundation models. More recently, I have begun to extend this agenda toward the predictive side by learning from large-scale audio-video data to anticipate future observations and longer-term outcomes. In the long run, I hope these two directions will help move multimodal systems beyond passive understanding toward agents that act with foresight, adapt through interaction, and improve over time.

## Second Paragraph Draft (CN)

围绕第一段提出的总问题，我过去主要在 action side 上研究一个更基础的科学问题：RL-based post-training 究竟如何改变 multimodal models。我的研究表明，这种改变并不只是 benchmark 分数的提升，而会体现在模型的训练动态、能力组织和行为机制上。

首先，在 reasoning-centric setting 中，我通过从零搭建训练流程并配套标准化评测，系统研究了 RL 如何影响模型的训练动态与泛化行为。相关结果表明，RL 的收益不仅体现在最终性能上，也伴随着长度、反思和泛化行为上的系统性变化；尤其在视觉数学任务上，它相较于高质量监督的 SFT 仍表现出更强的泛化能力。随后，我进一步在单一 RL 框架中对 8 个任务（4 个推理、4 个感知）进行统一训练，表明这种能力塑造并不局限于推理任务，而可以同时作用于 reasoning 与 perception，并体现出联合训练的互补收益。

更进一步，在 vision tool-use RL 的场景中，模型的行动不再仅仅决定单步输出，而开始影响其后续能够获取到的观测信息。在这个更具 agentic 特征的设定下，我进一步研究模型究竟学到了什么；相关分析表明，当前工具使用 RL 的收益更多来自 intrinsic capability improvement 和 tool-induced harm 的降低，而非真正意义上的工具掌握。

整体来看，这些工作共同构成了我对 action side 的一个持续判断：RL post-training 正在逐步重塑多模态模型的感知、推理与行动方式。对于我而言，理解这种重塑的机制及其局限，正是进一步走向 predictive side 的重要起点。
