  围绕第一段提出的总问题，我过去主要从多模态智能体的 action side 入手，并以 RL-based post-training 作为主
  要抓手。我最初从 reasoning-centric setting 出发，因为 RL 最早在 foundation models 的推理能力上显示出强
  大潜力，也为研究模型如何基于结果反馈学习行动能力提供了一个相对清晰的起点。在此基础上，我进一步关注，如
  果这条路线只对 reasoning-heavy tasks 有效，它仍不足以支撑更完整的 multimodal action，因为模型若不能稳定
  感知当前状态，后续推理与行动的上限也会受到限制。因此，我开始探索如何在统一的 RL 框架中同时提升
  reasoning 与 perception，并通过严格消融验证联合训练的互补性。更进一步，在 tool-use setting 中，模型的行
  动不再只影响最终输出，还会影响其后续能够获取到的观测信息，因此问题也从“如何提升模型的行动能力”转向“模型
  究竟学会了如何通过行动获取和利用信息”。这促使我进一步研究 vision tool-use RL 中 intrinsic capability
  improvement 与 tool-induced effects 之间的关系。整体来看，这些工作构成了我在 action side 上的一条连续研
  究路径：从建立 reasoning-centric RL 的透明训练与评测基础，到扩展 reasoning 与 perception 的统一学习，再
  到理解更 agentic 的 tool-use setting 下模型究竟学到了什么。

  围绕第一段提出的总问题，我过去主要在 action side 上研究一个更基础的问题：RL-based post-training 究竟如
  何改变 multimodal models。我的相关工作表明，这种改变并不只是最终分数的提升，而会体现在模型能力、训练动
  态和行为机制的多个层面。首先，在 reasoning-centric setting 中，我通过透明的训练与评测框架系统研究了 RL
  如何影响多模态模型的推理行为与泛化能力，并发现其收益不仅体现在性能上，也体现在与长度、反思等训练动态相
  关的行为变化上。随后，我进一步发现，这种由 RL 带来的能力塑造并不局限于 reasoning-heavy tasks，而可以在
  统一框架中同时作用于 reasoning 与 perception，并且二者的联合训练具有明显的互补性。再进一步，在 vision
  tool-use RL 中，我开始研究当模型能够通过行动改变其后续信息获取过程时，RL training 到底学到了什么；相关
  分析表明，当前工具使用 RL 的主要收益更多来自 intrinsic capability improvement 和 tool-induced harm 的降
  低，而不是真正意义上的工具掌握。整体来看，这些工作共同构成了我对 action side 的一个持续判断：RL
  training 不只是提升多模态模型的输出质量，更在逐步重塑其推理、感知与行动方式，而理解这种变化本身，正是我
  后续走向 predictive side 的重要基础。
