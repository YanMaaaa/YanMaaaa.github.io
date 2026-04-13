# 视频生成模型预训练数据处理管线

## 项目认知 (原始版)

首先，predictive multimodal learning，预测什么? 在我看来本质上是预测multimodal tasks/environments的 next state，什么是state？我认为这本身可以有很多表征方式。可以是computer use任务的接受一个click之后的下 一个电脑桌面的样子，可以是streaming videos的下一帧或者下一段video clips，也可以是embodied tasks的下一 段环境的样子。表征既可以是真正的frames（例如video Diffusion Models），也可以是latent（例如JEPA, latent Diffusion MOdels）。但是你会发现，无论绕来绕去，对于multimodal environments的next state，一定绕不开的 东西就是video！因为在我看来，video就可以类比为纯文本的tasks里的text（token sequences）video就会去学习 如何modeling 多模态的next-state predication的语料（对应到文本语料来学习next token prediction）。这就是 我去做我现在这个项目的原因。也许未来去做predictive modeling的算法和范式乃至架构可能会变，但是video作为 核心“食物”的逻辑不会变。因此，去研究video数据的认知是我做现在这个项目的核心。如何定义高质量的video data，如何处理，处理前后的video会对模型训练带来什么影响？（我目前主要针对video generation model）也就 是next state的state是一个显式的frame，但是我不去定义如果predictive modeling的能力要融入到mm agents到底 是应该预测latent还是完整帧，这个我很难预测，但是我做的事情就是围绕如何为predictive modeling的能力带了 更高质量的食物，以及对video数据如何处理，和被训进video generation model as world simulator带来认知平 权

## 项目认知 (阐释版)

我目前更愿意把 predictive multimodal learning 理解为：学习多模态环境如何随时间演化，以及当前上下文和行动会如何影响后续状态。这里的 `state` 不需要被过早固定成某一种表示。在 computer use 中，它可以体现为一次 click 之后的下一个桌面；在 streaming video 中，它可以体现为下一帧、下一段 clip，或更长时间范围内的事件延续；在 embodied tasks 中，它也可以体现为行动后的下一段环境变化。对应地，模型预测的对象既可以是显式的 frame，也可以是更抽象的内部表示。

从这个角度看，video 在 predictive multimodal learning 中具有很特殊的地位。无论未来的算法、训练范式或架构如何变化，只要目标还是学习多模态环境的 next-state prediction，就很难绕开 video，因为 video 是当前最通用、最可扩展的时序多模态经验基础。类似于 text corpora 对 next-token prediction 的作用，video data 为 predictive modeling 提供的是大规模、按时间展开的世界变化样本。

这也是我做当前项目的核心原因。我关心的并不只是如何搭建一个视频处理 pipeline，而是：如果我们希望模型真正学到环境随时间演化的规律，那么什么样的 video data 才是高质量的训练基础？视频应该如何切分、过滤、标注和组织，才能尽可能保留对预测有用的时间结构？这些处理选择在进入训练之后，又会如何影响模型的稳定性、样本效率和最终能力？

在当前阶段，我主要以 video generation model 作为一个具体而可验证的 testbed，在这里 next state 往往被建模为显式的 future frames 或 future clips。但我并不想过早预设，未来 predictive modeling 融入 multimodal agents 时，最终一定应该预测完整帧还是更抽象的内部状态。对我来说，更核心的问题是：如何为 predictive modeling 提供更高质量的 video “食物”，并系统理解不同 video data recipe 会如何影响模型对时间动态、未来结果和行动后果的学习。

因此，这个项目的意义并不只是服务某一个具体的视频生成训练流程，而是在更长远的意义上，为 predictive multimodal learning 建立一套更 data-centric 的研究基础：把 video data 从原始素材变成可验证的训练基础，并研究这些数据处理与组织方式如何影响模型作为 predictive simulator，乃至更广义的 multimodal agent 组成部分的能力边界。

## 一个可选的 formalization

下面这套 formalization 主要用于帮助我自己澄清概念边界，也适合放在内部研究笔记、proposal 或更 technical 的长文里；它默认 **不适合直接放进 research statement**，因为符号会明显增加阅读负担，也会让整段表述过早绑定某一种技术形式。

如果把 predictive multimodal learning 写得更正式一些，我可以把问题定义成部分可观测多模态环境中的状态演化问题：

- `s_t`：时刻 `t` 的真实环境状态（通常不可被模型完整观测）
- `o_t`：时刻 `t` 的多模态观测，例如 video frame、audio chunk、screen state 等
- `a_t`：时刻 `t` 的 action
- `h_t = (o_{1:t}, a_{1:t-1})`：截至时刻 `t` 的交互历史
- `z_t`：模型基于历史形成的 latent belief state，也就是一个对当前环境状态的压缩内部估计

一种比较自然的写法是：

```math
z_t = f_\phi(z_{t-1}, o_t, a_{t-1})
```

其中 `z_t` 用来概括历史观测和动作，并近似表示模型当前对环境的内部状态判断。随后，预测问题可以写成 latent dynamics 与 future observation prediction 的组合：

```math
z_{t+1} \sim p_\theta(z_{t+1} \mid z_t, a_t)
```

```math
o_{t+1} \sim p_\psi(o_{t+1} \mid z_{t+1})
```

如果面向更长时间范围，也可以直接写成 horizon-level prediction：

```math
p_\theta(o_{t+1:t+H} \mid z_t, a_{t:t+H-1})
```

这套写法的核心作用，不是要求未来方法一定预测 latent 而不是 frame，而是把几个层次分开：

- 环境本身如何演化
- 模型如何把历史压缩成内部状态
- 预测目标究竟是 future observations，还是更抽象的 state representations

从这个意义上说，`video generation model` 只是当前一个具体而可验证的 testbed：它通常把未来状态写成显式的 future frames 或 clips；但更广义的 predictive multimodal learning，并不需要预先承诺未来一定只能用 frame 作为唯一表示。

## 项目定位

本仓库聚焦于视频生成预训练数据的 `recipe` 沉淀、资产契约定义与经验验证：不仅要把原始视频处理成可消费的数据集，还要明确每个阶段应该产出什么资产、保留什么元数据、如何通过实验验证这些处理策略是否真的改善训练数据质量。

这意味着本仓库的核心目标不是重复实现一个通用视频处理框架，而是沉淀一套面向视频生成训练的数据生产规范：

- 定义可复用的数据 `recipe`，例如切分、过滤、标注与打包策略。
- 定义跨阶段稳定的数据资产契约，例如 `run_id`、manifest、Parquet schema 和 stage output layout。
- 通过 viewer、summary、抽样检查和后续训练对比，把数据处理假设变成可验证、可复现的经验。

像 NeMo Curator 这样的通用视频 curation 框架，是本仓库的重要参考与对照对象；但本仓库不以某个外部框架的 task model 或 pipeline abstraction 作为系统边界，而以“可交付的训练数据资产”作为主抽象。

## 研究问题与验证清单

本项目的价值不在于“把所有 stage 都实现出来”，而在于把视频生成预训练数据构建过程拆成可验证的模块，并逐步回答每个模块是否真的有必要、带来了什么收益、是否值得它的成本。

后续开发默认围绕下面这些问题展开：

- **Stage 1 / probe**：哪些基础元数据是后续切分、过滤、审计和训练配方所必需的？
- **Stage 1 / screen**：粗粒度筛选能节省多少后续转码与切分成本？又会误伤多少潜在有效样本？
- **Stage 1 / transcode**：统一编码、分辨率和帧率，是否显著提升后续切分稳定性、过滤一致性或训练可用性？
- **Stage 1 / manifest**：哪些字段必须进入 canonical manifest，才能支撑后续 stage、人工审核和训练消费？
- **Stage 2 / segmentation**：`fixed_stride`、`PySceneDetect`、`TransNetV2`、`VLM semantic split` 各自带来什么增益？shot-aware segmentation 是否优于固定时长切分？
- **Stage 2 / clip policy**：`<2s` 丢弃、`2~10s` 保留、`>10s` 等分，以及 `single_shot` / `multi_shot` 策略，是否真的更适合视频生成训练？
- **Stage 3 / filtering**：motion、aesthetic、去重等过滤策略分别提高了什么质量指标？是否损伤了数据多样性？
- **Stage 4 / annotation**：caption、tag、scene/action labels 对采样、检索、训练效果分别有什么实际价值？
- **Stage 5 / packaging**：最终打包格式与 shard 策略，是否影响训练吞吐、采样稳定性和故障恢复成本？

每个新模块在进入仓库前，至少应该能回答下面 3 个问题：

1. 它对应哪一个明确的数据假设或研究问题？
2. 它的收益将通过什么方式验证：viewer 抽查、统计对比、还是下游训练实验？
3. 如果去掉它，数据质量、训练效果或生产成本会发生什么变化？
