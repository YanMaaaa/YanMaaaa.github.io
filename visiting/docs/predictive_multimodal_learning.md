# Video-based Predictive Learning 与 World Model 的关系

## 1. 总览

**Video-based Predictive Learning** 指一类以视频为核心数据来源的预测式学习方法。它的基本思想是：视频包含丰富的空间结构、时间动态、物体交互、物理规律和语义信息。模型通过预测视频中的缺失部分、未来状态或条件指定的内容，可以学习到关于世界结构和动态规律的表示。

一个清晰的划分方式是：

```text id="fo2rqd"
Video-based Predictive Learning
├── Self-supervised Predictive Learning
│   └── 通过预测视频中被遮住或缺失的部分来学习表示
│       例如：V-JEPA2
│
└── Generative Predictive Learning
    └── 通过给定条件生成未来视频、视频延续或时序展开
        例如：video generation / future rollout / simulation models
```

这个划分是按照**学习目标**来区分的。
**Self-supervised Predictive Learning** 更强调从视频自身构造预测任务，从而学习表示。
**Generative Predictive Learning** 更强调在给定条件下生成未来、延续或模拟结果。

**World Model** 可以由上述任一路线实现。判断一个模型是否属于 World Model，关键不在于它使用哪一种训练方式，而在于它是否能够建模世界状态、动态规律、动作后果，并进一步支持规划或控制。

---

## 2. Self-supervised Predictive Learning from Videos

**Self-supervised Predictive Learning** 是指模型不依赖人工标签，而是直接从视频数据自身构造预测任务。常见做法是遮住视频中的一部分内容，让模型根据可见部分预测被遮住的部分。

典型形式是：

```text id="fj6zu1"
视频中的可见部分 → 视频中被遮住或缺失的部分
```

被预测的目标可以处于不同层次：

```text id="qq1g7d"
Self-supervised Predictive Learning
├── Pixel-level prediction
│   └── 预测被遮住的像素、patch 或 video tube
│
├── Feature-level prediction
│   └── 预测视觉特征或 teacher model 产生的特征
│
└── Latent-level prediction
    └── 预测被遮住视频区域的 latent representation
```

在这个意义上，**VideoMAE** 和 **V-JEPA2** 都可以归入广义的 Self-supervised Predictive Learning from Videos。
二者的区别在于预测目标所在的层次不同。

```text id="mnhpoi"
VideoMAE:
根据可见视频内容，重建被 mask 的视频 patch / tube。
它更偏向 pixel-level 或 reconstruction-oriented 的预测。

V-JEPA2:
根据可见视频内容，预测被 mask 区域在 latent representation space 中的表示。
它更偏向 latent-level 或 representation-oriented 的预测。
```

这类方法的主要目标通常不是直接生成逼真的视频，而是学习有用的视觉和时序表示。通过预测视频中缺失的时空区域，模型可以学习物体结构、运动模式、场景关系、时间连续性以及一定程度的物理规律。

因此，Self-supervised Predictive Learning 可以训练出 **world-model-oriented representations**。
V-JEPA2 就是这一方向的代表例子。它通过视频中的自监督预测任务学习抽象表示，这些表示可以服务于对物理世界的理解、预测和后续规划。

---

## 3. Generative Predictive Learning for Videos

**Generative Predictive Learning** 是指模型在给定条件下生成未来视频、视频延续、多模态时序展开或模拟结果。这里的“predictive”强调模型需要预测某种未来或条件指定的结果；“generative”强调模型以生成可观察内容的方式完成预测。

典型形式是：

```text id="juhg8g"
给定条件 → 生成未来视频、视频延续或模拟结果
```

这里的条件可以有多种形式：

```text id="vlieig"
Generative Predictive Learning
├── text → video
├── image / first frame → video
├── past video frames → future video frames
├── video prefix → video continuation
├── action + current observation → future state
└── multimodal condition → video-audio rollout
```

这类模型的输出通常是可观察的生成结果，例如视频帧、音频、轨迹或模拟展开。它不仅学习“识别视频内容”，还学习在给定条件下生成可能发生的后续结果。

因此，Generative Predictive Learning 可以训练出 **generative world simulators**。
如果一个生成式模型能够生成物理一致、时间连贯、对象关系稳定、动作后果合理的未来场景，它就与 World Model 的目标非常接近。

这一类可以包括：

```text id="qwzzqk"
video generation models
future video prediction models
video continuation models
video-audio generation models
simulation-oriented generative models
interactive world simulators
```

---

## 4. World Model 是能力层面的概念

**World Model** 更适合作为一个能力层面的概念，而不是一个单独的训练范式。

一个模型是否可以被称为 World Model，取决于它是否具备对世界运行方式的建模能力。核心能力包括：

```text id="zxmvoo"
World Model
├── 表示 world states
├── 建模 temporal dynamics
├── 预测 future states
├── 预测 action outcomes
├── 支持 planning
└── 支持 control 或 decision-making
```

因此，World Model 可以由 Self-supervised Predictive Learning 路线产生，也可以由 Generative Predictive Learning 路线产生。

```text id="c42bap"
Video-based Predictive Learning
├── Self-supervised Predictive Learning
│   └── 可以训练出 world-model-oriented representations
│       例如：V-JEPA2
│
└── Generative Predictive Learning
    └── 可以训练出 generative world simulators
        例如：video generation / future rollout / simulation models

World Model
= 可能由上述任一路线实现
= 关键看它是否能建模世界状态、动态规律、动作后果、规划或控制
```

这意味着，World Model 不应该被简单等同于 Self-supervised Predictive Learning，也不应该被简单等同于 Generative Predictive Learning。
它是某些模型最终达到的能力状态，而不是某一种固定的训练目标。

---

## 5. 两条路线与 World Model 的关系

Self-supervised Predictive Learning 和 Generative Predictive Learning 的区别在于学习目标不同。

**Self-supervised Predictive Learning** 通常是 representation-oriented。
它通过预测视频中被遮住或缺失的部分，学习对视频和物理世界的抽象表示。

**Generative Predictive Learning** 通常是 simulation-oriented。
它通过生成未来、延续或条件指定的视频内容，学习对可能未来的模拟能力。

二者和 World Model 的关系可以概括如下：

| 类别                                      | 主要目标             | 典型输出                                                    | 与 World Model 的关系                         |
| --------------------------------------- | ---------------- | ------------------------------------------------------- | ----------------------------------------- |
| **Self-supervised Predictive Learning** | 从视频自身学习表示        | masked pixels、features、latent representations           | 可以产生 world-model-oriented representations |
| **Generative Predictive Learning**      | 生成未来或条件指定的视频内容   | future video、video continuation、rollout、simulation      | 可以产生 generative world simulators          |
| **World Model**                         | 建模世界状态、动态规律和动作后果 | internal state、prediction、plan、control signal 或 rollout | 可以由上述任一路线实现                               |

---

## 6. 更完整的术语关系

可以将三者关系表达为：

```text id="ldvsij"
Video-based Predictive Learning
├── Self-supervised Predictive Learning
│   ├── masked video prediction
│   ├── masked feature prediction
│   ├── masked latent prediction
│   └── world-model-oriented representation learning
│
└── Generative Predictive Learning
    ├── future video generation
    ├── video continuation
    ├── video-audio generation
    ├── action-conditioned future rollout
    └── generative world simulation

World Model
├── 可以基于 self-supervised predictive representations
├── 可以基于 generative predictive simulators
└── 由建模世界动态、动作后果、规划和控制的能力来定义
```

在这个框架下，**V-JEPA2** 更适合放在 Self-supervised Predictive Learning 下，因为它通过预测视频中被 mask 的 latent representation 来学习世界表示。
而视频生成、未来帧预测、视频延续和交互式模拟模型更适合放在 Generative Predictive Learning 下，因为它们通过生成未来或条件指定的内容来完成预测。

---

## 7. 总结

**Video-based Predictive Learning** 可以分为两条主要路线。

第一条路线是 **Self-supervised Predictive Learning**。它通过视频内部的预测任务学习表示，例如预测被遮住的像素、特征或 latent representation。V-JEPA2 是这一方向的代表模型之一。它不以生成逼真视频为主要目标，而是通过 latent-level prediction 学习对物理世界有用的抽象表示。因此，它可以被看作一种 world-model-oriented representation learning 方法。

第二条路线是 **Generative Predictive Learning**。它通过给定文本、图像、首帧、视频前缀、动作或其他条件，生成未来视频、视频延续、多模态时序展开或模拟结果。这类方法可以发展为 generative world simulators，尤其是在模型能够生成物理一致、时间连贯、动作后果合理的未来场景时。

**World Model** 不是上述两类中的某一个固定分支，而是一个能力层面的概念。
只要一个模型能够建模世界状态、动态规律、动作后果，并支持规划或控制，它就可以被视为 World Model。
因此，World Model 既可以通过 Self-supervised Predictive Learning 路线实现，也可以通过 Generative Predictive Learning 路线实现。
