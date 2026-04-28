# 论文标题

The Curse of Conventional Wisdom: Which Video Curation Practices Matter for World Model Pretraining?

# 仓库指南（Repository Guidelines）

## 项目概览

Video Pretrain Data Pipeline：视频生成模型预训练数据处理管线。将几百万个来自 YouTube 等来源的原始视频，经过标准化、切分、过滤、标注、打包，最终输出可直接用于训练的数据集。

当前仓库的核心定位不是实现另一个通用视频处理框架，而是沉淀面向视频生成预训练的数据 `recipe`、资产契约和经验验证方法。也就是说，仓库不仅负责“把视频处理一遍”，还负责定义每个阶段的正式产物、元数据 schema、`run_id` 版本语义，以及如何通过 viewer / summary / 后续训练实验来验证这些数据处理策略是否有效。

像 NeMo Curator 这类通用视频 curation 框架，是重要的设计对照物和局部实现参考；但本仓库的系统边界不以外部框架的 task model 或 stage abstraction 为核心，而以阶段化数据资产和下游训练可消费的交付物为核心。

管线分为 5 个阶段，顺序执行：

1. **摄入与解码 (Ingestion & Decoding)** — 原始视频 → 标准化 H.265/MP4 (720p, 24fps)
2. **切分与结构化 (Segmentation)** — 长视频 → 2~10 秒场景片段
3. **多维过滤与清洗 (Filtering & Cleaning)** — 美学评分、运动评分、去重
4. **深度标注与对齐 (Deep Annotation & Alignment)** — VLM captioning、标签生成
5. **存储优化 (Storage Optimization)** — 打包为 WebDataset (.tar) 供训练消费

技术栈：

- **离线转码**: FFmpeg + NVDEC/NVENC (GPU 加速)
- **训练时数据加载**: NVIDIA DALI
- **元数据索引**: Parquet (pandas/pyarrow)
- **分布式调度**: Ray / Spark
- **训练数据格式**: WebDataset (.tar)
- **语言**: Python

关键约定：

- 不使用 decord（已停止维护），解码相关用 DALI 或 torchcodec

设计文档：

- 详细的阶段设计文档见 `README.md`

参考文档：

- 详细的背景知识参考文档见 `assets/Report_from_ChatGPT.pdf` 和 `assets/Report_from_Gemini.pdf`

## 项目结构与模块组织

当前仓库以设计文档为主：

- `README.md`: 主设计文档（各 Stage 的详细说明与决策）
- `doc/`: 补充/对照资料（例如 `doc/seedance1.0_data_pipeline.md`）
- `assets/`: PDF 等参考资料

如果引入可执行代码，建议采用稳定结构：

- `video_pretrain/`: 可复用库代码（核心函数、可 import）
- `recipe/`: 流程编排脚本（按 stage/step 组织的 CLI 入口）
- `viewers/`: 人工检查与可视化工具（例如 streamlit）

`video_pretrain/` 子目录语义（一句话）：

- `ingestion/`: Stage 1 摄入阶段的可复用能力，按能力目录组织（如 `probe/`、`screen/`、`transcode/`）。
- `index/`: 样本索引与元数据清单管理（扫描、读写、表结构）。
- `media/`: 与单视频媒体属性直接交互（如 ffprobe/codec 信息）。
- `filters/`: 数据质量与规则过滤逻辑。
- `annotate/`: 文本/标签等标注与对齐逻辑。
- `common/`: 跨模块共享的基础类型、异常与工具。

运行约定（保持抽象且可迁移）：

- 在仓库根目录优先使用可安装包方式运行（推荐 `pip install -e .`）
- 核心逻辑优先沉淀到 `video_pretrain/`，`recipe/` 只做参数编排与调用
- `scripts/` 中的 runner 使用 `VAR="${VAR:-default}"` 提供默认参数，允许本地或 `submit/` 通过环境变量覆盖。
- `submit/` 只负责运行时编排（例如启动 Ray 后再调用 `scripts/`），不重复维护业务参数。

当前实现入口：

- Stage 1 统一入口为 `recipe/stage1_ingestion.py`，配置位于 `configs/stage1_ingestion/`，库代码位于 `video_pretrain/ingestion/{probe,screen,transcode,manifest}/`。
- Stage 2 统一入口为 `recipe/stage2_segmentation.py`，配置位于 `configs/stage2_segmentation/`，库代码位于 `video_pretrain/segmentation/detect/`。
- Stage 2 detect 代码按 `config.py` / `ranges.py` / `worker.py` / `orchestrator.py` 组织；其中 `ranges.py` 负责把单视频 row 与 detector config 转成 `(start_sec, end_sec)` 时间区间。
- 示例 runner 位于 `scripts/stage1_ingestion/` 与 `scripts/stage2_segmentation/`；`submit/` 只负责运行时编排，不重复维护业务参数。
- Viewer 位于 `viewers/`，Stage 1/2 均有统一 Streamlit 入口。

当前进度与关键事实：

- Stage 1 Step 1-4 已完成统一 Hydra 入口、scripts 和 viewer 主链路；`meta/stage1_ingestion/step4_manifest/run_id_...` 是 Stage 1 的正式 metadata 输出，也是 Stage 2 默认输入。
- 公共 Ray 执行器位于 `video_pretrain/common/ray.py`：`run_ray_task_pool()` 用于无状态 CPU task pool，`run_ray_actor_pool()` 用于离线 batch actor 动态派发。
- Stage 1 Step 3 CPU 路径使用 `run_ray_task_pool()`，GPU 路径使用 `run_ray_actor_pool()`；`max_pending_tasks` 统一由 Ray cluster CPU 与每 task CPU 自动计算。
- Stage 2 已拆分为 metadata-only 的 `step1_detect` 与后续 asset-producing 的 `step2_clip`；当前 `step1_detect` 已完成，`step2_clip` 是下一步开发目标。
- Stage 2 Step 1 Detect 默认输入为 `meta/stage1_ingestion/step4_manifest/run_id_...`，默认输出为 `meta/stage2_segmentation/step1_detect/run_id_...`。
- Stage 2 Step 1 Detect 支持 PySceneDetect detectors、TransNetV2 CPU、`uniform` baseline 和 `random` baseline；多 detector 组合通过 `step.detectors=[adaptive,transnetv2]` 这类 Hydra list 表达。
- PySceneDetect `SceneManager.add_detector()` 的组合语义是多个 detector 共享完整 frame stream，各自报 boundary，最终取 boundary 并集；它不是“先 detector A 切分，再在子段内运行 detector B”的级联流程。
- `uniform` 与 `random` 只依赖 `duration_sec`，不解码视频；`uniform` 按固定 `clip_len_sec` 生成等长 segment 并丢弃尾段，`random` 按 `min_scene_len_sec/max_scene_len_sec/scene_len_step_sec/seed` 生成可复现的随机长度连续 segment。
- Stage 2 Step 1 Detect 输出两层 metadata：`segments/segments-*.parquet` 是一行一个 segment 的事实表，`videos/videos-*.parquet` 是视频级浏览索引，包含 `ticks_sec` 与 `segment_shard_paths`。
- Stage 2 viewer 优先读取 `videos` 索引表，并仅在需要 segment 明细时按 `segment_shard_paths` 定位读取相关 shard。
- `scripts/stage2_segmentation/run_step1_detect.sh` 会根据 `DETECTORS` 条件追加 detector 参数：基础路径/Ray/limit 参数总是传入，只有被启用的 detector 才传入对应 `step.detector.<name>.*` override。
- 当前 TransNetV2 只把 CPU 路径作为正式 baseline；`device=cuda` 暂未作为 GPU backend 建模，后续如需 GPU 推理应单独设计 actor/backend。
- 原设计中的 Step 5 不再作为固定 pipeline step 保留；如需迁移、长期存放或训练前复核，应以按需 `verify/audit` 工具单独运行。

数据管理约定（High-level）：

- 原始数据按 `source_batch` 分批快照管理，避免新旧 raw 数据混写。
- 各 stage 产物目录独立，使用 `run_id` 追踪一次完整处理运行。
- `data/` 与 `meta/` 的推荐目录层级统一为：`<stage语义>/<step语义>/run_id_...`。
- 这样既保留 stage 语义，也保留 step 语义，避免同一 stage 下多个产出视频的 step 因共用 `run_id` 而发生目录语义冲突或覆盖。
- 并非每个 step 都必须有 `data/` 目录；只有真正产出新视频资产的 step 才在 `data/` 下落盘。
- metadata 统一使用 Parquet；CSV 仅可用于临时调试，不作为主产物。
- 通过 `sample_id` 贯穿各 stage，保证跨阶段关联与可追溯。
- 完整模板与字段定义见 `README.md` 的“数据资产管理模板（推荐）”章节。

## 常用命令（开发与协作）

目前未内置统一的 build/test 命令，常用协作命令：

- `rg "<关键词>"`: 全仓库快速搜索（优先用于定位文档/代码位置）
- `git log -n 20 --oneline`: 回顾近期设计变更
- `git status`: 提交前检查工作区状态

## 编码风格与命名约定

- 以 Python 为主；4 空格缩进；非平凡逻辑尽量补全类型标注。
- `video_pretrain/` 内部优先使用能力语义命名，而不是 `stageN_stepM` 编号命名；例如目录使用 `probe`、`screen`、`transcode`，类名使用 `ProbeOrchestrator`、`ScreenOrchestrator`、`TranscodeOrchestrator`。
- `recipe/` 与产物目录继续保留 `stage/step` 语义，例如 `recipe/stage1_ingestion.py step=step2_screen` 与 `meta/stage1_ingestion/step2_screen/run_id_...`。
- `stage0` 表示 raw 数据索引与探测等 metadata-only 预处理；从 `stage1` 开始才产出新的标准化视频资产。
- 文件/脚本命名保留 stage/step 语义；统一入口用阶段语义命名（例如 `recipe/stage2_segmentation.py`），具体 runner 用 step 语义命名（例如 `scripts/stage2_segmentation/run_step1_detect.sh`）。
- 产物命名与 `README.md` 保持一致（例如 `metadata.parquet`、`videos/*.mp4`、WebDataset `.tar`）。

## 测试指南

当前未建立测试框架。新增代码建议至少包含：

- 核心逻辑单测（快）
- 小样本端到端 smoke test（少量短视频，验证 CLI 串联）

## 提交与 PR 规范

提交信息保持简短、祈使句风格（历史示例：`add ...`、`update ...`、`init: ...`），可选前缀：`stageN:`。

PR 至少写清：

- 影响的 Stage、改动动机、与文档对应位置（`README.md`/`doc/...`）
- 新增/修改脚本的示例命令与预期输出

## 安全与配置

- 禁止提交数据集、API key、凭据、模型权重。
- 机器相关路径/本地数据进入 `.gitignore`，运行假设写入 `README.md`。
