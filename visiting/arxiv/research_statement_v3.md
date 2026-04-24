# Research Statement

## Working Title

Toward Multimodal Agents that Perceive, Reason, Act, and Predict

## Core Paragraph

I view multimodal agents as goal-directed systems that work in partially observed multimodal environments, where they must perceive what is happening, reason about it, act to gather useful information, and predict what will happen next. Such systems are needed to complete long-horizon multi-modal tasks that unfold through interaction, such as multi-step computer use, decision-making from video or audio streams, and embodied tasks like robotics or driving.

A central question motivating my research is how multimodal agents can not only perceive, reason, and act based on current observations, but also predict how the world will evolve after their actions. So far, my work has mainly focused on the first part of this question, using reinforcement learning (RL) to improve reasoning, perception, and tool-use actions in multimodal foundation models. More recently, I have begun to extend this agenda toward the predictive side by learning from large-scale audio-video data to anticipate future observations and longer-term outcomes. In the long run, I hope these two directions will help move multimodal systems beyond passive understanding toward agents that act with foresight, adapt through interaction, and improve over time.

## Third Paragraph Draft (CN)

围绕 multimodal agents 如何在当前观测下完成感知、推理与行动，我过去主要从 RL 这一训练范式切入，追问一个更基础的问题：RL 究竟如何改变 multimodal models。我的研究表明，这种改变并不只是 benchmark 分数的提升，而会体现在模型的训练动态、能力协同与行为机制上。

首先，在 reasoning-centric setting 中，我系统研究了 RL 如何影响模型的训练动态与泛化行为。结果表明，RL 改变的不只是最终性能，还会重塑长度、反思等训练动态，而这些变化本身也对随机种子较为敏感；在视觉数学任务上，它相较于高质量监督的 SFT 仍表现出更强的泛化能力。随后，我进一步追问：如果 RL 的收益主要停留在 reasoning-heavy tasks 上，它能否真正成为塑造 multimodal foundation models 的通用训练范式？为此，我们设计了联合推理与感知的统一训练框架 V-Triune，并在 8 个任务（4 个推理、4 个感知）上验证了稳定联合训练的可行性。结果表明，RL 的能力塑造并不局限于推理，而可以同时作用于 reasoning 与 perception，并带来互补收益。

更进一步，我开始关注当模型的行动开始影响其信息获取过程时，RL 究竟会塑造出怎样的能力。在 vision tool-use RL 的场景中，相关分析表明，当前工具使用 RL 的收益更多来自 intrinsic capability improvement 和 tool-induced harm 的降低，而非真正意义上的工具掌握。

整体来看，这些工作共同构成了我在 multimodal agents agenda 中的一条基础研究主线：我首先关注模型如何基于当前观测完成感知、推理与行动，随后进一步进入行动开始影响信息获取过程的更 agentic setting。这些结果也说明，对于那些通过持续交互逐步展开的 long-horizon multimodal tasks，仅仅基于当前观测进行感知、推理与行动往往还不够；模型还需要预判后续状态如何演化，以及行动将带来什么后果。


## Third Paragraph Draft (EN)

Around the question of how multimodal agents perceive, reason, and act under current observations, I have mainly approached this topic through RL and asked a more basic question: how does RL change multimodal models? My work suggests that these changes are not just about higher benchmark scores. They also appear in training dynamics, in how different abilities work together, and in the behavior the model develops.

First, in reasoning-centric settings, I studied how RL changes training dynamics and generalization. The results show that RL changes more than final performance: it also reshapes response length, reflection, and other training behaviors, and these changes are themselves fairly sensitive to random seeds. On visual math tasks, RL also shows better generalization than high-quality SFT. I then asked a broader question: if the gains from RL mostly stay in reasoning-heavy tasks, can RL really become a general way to shape multimodal foundation models? To study this, we designed V-Triune, a unified framework for joint reasoning-and-perception training, and validated stable joint training on 8 tasks (4 reasoning and 4 perception). The results show that RL does not only shape reasoning. It can also improve reasoning and perception together, with complementary gains across the two.

I then became interested in what RL learns when actions start to affect how the model gathers information. In vision tool-use RL, our analysis shows that the gains from tool-use RL mostly come from intrinsic capability improvement and reduced tool-induced harm, rather than true tool mastery.

Taken together, these works form one basic line of my research on multimodal agents. I first study how models perceive, reason, and act from current observations, and then move to more agentic settings where actions begin to change the information available to the model. These results also suggest that, for long-horizon multimodal tasks that unfold through ongoing interaction, acting only from current observations is often not enough; models also need to anticipate how future states will evolve and what consequences their actions will bring.
