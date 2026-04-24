---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    font-family: "Aptos", "Helvetica Neue", Arial, sans-serif;
    color: #1f2937;
    background: #fbfbf9;
    padding: 44px 56px;
  }
  h1 {
    font-size: 32px;
    line-height: 1.15;
    color: #10243d;
    margin-bottom: 0.35em;
  }
  h2 {
    font-size: 26px;
    line-height: 1.2;
    color: #10243d;
    margin-bottom: 0.45em;
  }
  p, li {
    font-size: 20px;
    line-height: 1.45;
  }
  ul {
    margin-top: 0.35em;
  }
  .muted {
    color: #5b6573;
    font-size: 18px;
  }
  .tagline {
    display: inline-block;
    margin-top: 0.8em;
    padding: 8px 14px;
    border-radius: 999px;
    background: #eef4fb;
    color: #163a63;
    font-size: 17px;
  }
  .small {
    font-size: 16px;
    color: #5b6573;
  }
---

# Toward Multimodal Agents that Perceive, Reason, Act, and Predict

**Yan Ma**  
Fudan University  
<span class="muted">yanma23@m.fudan.edu.cn · yanmaaaa.github.io</span>

<div class="tagline">Multimodal agents in partially observed environments</div>

![bg right:43% contain](../research_statement/Main_Figure1.png)

<!--
Speaker note:
- This talk is about a single long-term goal: building multimodal agents that can operate in partially observed environments.
- My past work mainly studies how RL changes multimodal models.
- My current and future work moves toward predictive multimodal learning from video.
-->

---

## Research Agenda

- I study **multimodal agents** that operate in **partially observed multimodal environments**.
- My main question is how such agents can **perceive, reason, act, and predict** over **long-horizon tasks**.
- My research has two connected lines:
  - **Past work:** how reinforcement learning changes multimodal models
  - **Current and future work:** predictive multimodal learning from video

![bg right:46% contain](../research_statement/Main_Figure1.png)

<!--
Speaker note:
- The agenda figure is the central map for the whole talk.
- On the left is the past RL line under current observations.
- On the right is the predictive line, starting from video data foundations.
-->

---

## Central Question

- Many multimodal tasks unfold through interaction under **partial observation**.
- In these settings, acting only from the current observation is often **not enough**.
- Agents also need to anticipate:
  - **how the environment will evolve**
  - **what consequences their actions will bring**

<div class="small">
Examples: multi-step computer use, streaming video decision-making, and embodied interaction.
</div>

<!--
Speaker note:
- This slide explains why the talk is not only about better multimodal understanding.
- The key transition is from current-observation competence to predictive competence.
- The rest of the talk first summarizes my RL line, then explains why it leads to predictive multimodal learning.
-->
