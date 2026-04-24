# 为什么 long-horizon tasks 需要 predictive multimodal learning

## 核心判断

- 不是所有多模态任务都强依赖 prediction。
- 但对于 **long-horizon multimodal tasks**，prediction 会变得尤其重要。
- 更准确地说，**predictive multimodal learning is especially valuable when tasks are long-horizon, partially observed, and interaction-driven.**

## 这句话背后的逻辑

### 1. 长程任务的难点，不只是理解当前，而是管理未来轨迹

- 在短任务里，模型往往只需要：
  - 理解当前 observation
  - 给出当前最合适的 action
- 但在长程任务里，一个 action 的价值通常不由“现在立刻有没有收益”决定，而由它是否会让未来任务更容易完成决定。
- 所以任务 horizon 一长，agent 的核心困难就从“识别当前”转向了“建模演化”。

### 2. long-horizon multimodal tasks 往往同时具备三个结构特征

#### 第一，当前观测通常不够

- 当前 screen、当前 frame、当前 observation 往往只暴露了任务状态的一部分。
- 因此模型不仅要理解“现在看到了什么”，还要推断：
  - 之前发生了什么
  - 当前处于什么更高层状态
  - 接下来最可能往哪里发展

#### 第二，动作的后果经常是延迟显现的

- 某个 action 的好坏不一定立刻显现。
- 它可能通过影响未来几步甚至十几步后的状态才体现出来。
- 这意味着 agent 需要某种对 **action outcomes** 的 anticipation。

#### 第三，动作还会改变未来可获得的信息

- 很多长任务里，动作不只是改变环境，还会改变：
  - 下一步会看到什么
  - 哪些信息会暴露出来
  - 哪些任务分支会被打开或关闭
- 所以 agent 不只是要预测“世界状态”，还要预测：
  - `if I do this, what information will become available next?`

## 为什么这在 multimodal 里尤其重要

- 多模态环境的状态变化，往往不是通过一个已经抽象好的 symbolic state 给出的，而是通过：
  - video / frames
  - audio streams
  - UI states
  - sensor observations
  - text + visual context together
- 也就是说，多模态环境的“演化”通常是通过 **可观测流** 呈现出来的。
- 因而问题不只是预测一个 neat 的 symbolic state，而是从复杂、部分可观测、随时间展开的多模态经验流里学到环境如何变化。

## 为什么不是简单地“用文本来预测”

### 1. 文本 prediction 当然有用

- 文本 prediction 很适合预测：
  - 高层计划
  - 子目标
  - 语言化的状态摘要
  - action rationale
  - abstract decision branches

### 2. 但 text-only prediction 有很强的前提

- 它默认环境状态可以被无损或近无损地压缩成语言。
- 这在很多 multimodal tasks 里并不成立。
- 很多关键的 future information 本来就是：
  - 视觉的
  - 空间的
  - 时间连续的
  - interaction-dependent

### 3. 所以关键区别是

- **Text prediction** 更适合高层 planning / reasoning。
- **Predictive multimodal learning** 更适合建模 grounded environment dynamics。

一句压缩版可以写成：

- **Text can predict plans; predictive multimodal learning models grounded environment dynamics.**

## 这些例子和 long-horizon multimodal tasks 的关系

- `interactive computer use across multiple tools and interfaces`
- `streaming video decision-making`
- `embodied interaction and control`

这些并不是彼此分散的例子，而是 **long-horizon multimodal tasks** 的不同实例。

它们共享的共同结构是：

- 任务随时间展开
- 当前观测不完整
- 行动会改变未来状态与未来信息

因此，predictive multimodal learning 的价值不是在所有任务上平均分布的，而是在这类任务上最自然、最有必要地体现出来。

## 最稳的表述方式

不建议写成：

- `all multimodal tasks require prediction`
- `only long-horizon tasks need prediction`

更稳的说法是：

- **Predictive multimodal learning is especially valuable for long-horizon multimodal tasks.**
- **Prediction becomes especially important when multimodal tasks are long-horizon, partially observed, and interaction-driven.**

## 对 slide 的启发

如果后面写 `Why This Leads to Prediction` 这一页，逻辑最好不是简单地说：

- `prediction is important`

而是清楚地说：

1. Long-horizon multimodal tasks unfold under partial observation.
2. Actions have delayed consequences and change future information.
3. Agents therefore need models of how environments evolve over time.

## 最后一句总结

- 长程多模态智能体的能力，本质上不只是识别当前状态，而是管理未来轨迹。
- 因此，predictive multimodal learning 的意义不只是生成未来，而是帮助 agent 建模环境演化与行动后果，从而更好地支持 perception, reasoning, and action.
