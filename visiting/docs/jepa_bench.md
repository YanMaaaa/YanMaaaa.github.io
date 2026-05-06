可以用这三个，计算量相对可控：

| 评估目标                           | 推荐 benchmark                                                       | 怎么测                                       |
| ------------------------------ | ------------------------------------------------------------------ | ----------------------------------------- |
| **Action recognition**         | **UCF101**、**HMDB51**；资源多一点再用 **Something-Something V2 subset**    | frozen encoder + linear probe / small MLP |
| **Temporal ordering**          | 自己从 **UCF101 / Something-Something V2 / Kinetics subset** 构造顺序判断任务 | 取同一视频的 2–3 个 clip，判断顺序是否正确                |
| **Object / scene recognition** | **ImageNet-1K subset** 测 object；**Places365 subset** 测 scene       | 抽视频帧或用图像输入，frozen encoder + linear probe  |

最推荐的最小组合：

```text
Action recognition: UCF101
Temporal ordering: 自构造 ordering task
Object/scene recognition: Places365 subset 或 ImageNet subset
```

如果只想用 video benchmark：

```text
Action recognition: UCF101 / HMDB51
Temporal ordering: 自构造
Object/scene recognition: 从视频帧抽 pseudo object/scene labels
```
