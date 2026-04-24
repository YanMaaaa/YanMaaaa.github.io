# Research Talk Base Deck Outline V0

## Goal

- Build a modular base deck for visiting meetings and faculty conversations.
- Default length: 10--12 slides.
- Default duration: 10--15 minutes.
- Main purpose: present a coherent research agenda rather than a paper-by-paper report.

## Core Narrative

- I study multimodal agents in partially observed environments.
- My past work asks how reinforcement learning changes multimodal models.
- This line leads naturally to a broader question: when current observations are not enough, how should agents predict future states and action outcomes?
- My current and future work moves toward predictive multimodal learning from video, with the long-term goal of integrating prediction into multimodal agent systems.

## Suggested Deck Structure

### Slide 1. Title

- Suggested title:
  - `Toward Multimodal Agents that Perceive, Reason, Act, and Predict`
- Content:
  - Name, affiliation, email, homepage
  - One-line summary of research theme
- Visual:
  - clean title slide, or a cropped version of the main agenda figure

### Slide 2. Research Agenda

- Key message:
  - My research is organized around multimodal agents operating in partially observed environments.
- Content:
  - brief definition of the setting
  - mention `perceive / reason / act / predict`
  - mention long-horizon multimodal tasks
- Visual:
  - the current agenda figure from the research statement

### Slide 3. Central Question

- Key message:
  - Long-horizon multimodal tasks require more than acting from current observations.
- Content:
  - examples: computer use, streaming video decision-making, embodied interaction
  - explain why actions change future information
  - motivate prediction of future states and action outcomes
- Visual:
  - task examples, or a simplified version of the agenda figure with emphasis on the transition from current observations to future states

### Slide 4. Past Work Overview

- Key message:
  - My past work studies how RL changes multimodal models under current observations.
- Content:
  - three takeaways:
    - RL reshapes training dynamics and generalization
    - RL can jointly shape reasoning and perception
    - tool-use RL gains do not yet imply true tool mastery
- Visual:
  - three-box overview with paper names in small text only

### Slide 5. RL Reshapes Training Dynamics and Generalization

- Key message:
  - RL changes more than benchmark scores.
- Content:
  - question: what exactly changes during RL training?
  - highlight: response length, reflection behavior, seed sensitivity, generalization over SFT
  - use only one or two result plots
- Visual:
  - one training-dynamics figure
  - one generalization result
- Source:
  - `Rethinking RL Scaling for Vision Language Models`

### Slide 6. RL Can Jointly Shape Reasoning and Perception

- Key message:
  - RL is not limited to reasoning-heavy tasks; it can shape reasoning and perception together.
- Content:
  - introduce the motivation behind V-Triune
  - highlight stable joint training across reasoning and perception tasks
  - emphasize complementary gains
- Visual:
  - one framework diagram
  - one compact table or bar chart
- Source:
  - `One RL to See Them All`

### Slide 7. Tool-Use RL Still Falls Short of True Tool Mastery

- Key message:
  - Current gains in vision tool-use RL mostly come from intrinsic improvement and harm reduction.
- Content:
  - explain the question: what does tool-use RL really learn?
  - highlight the main finding: performance gains do not necessarily mean genuine tool-based correction
  - connect this to the limits of acting only from current observations
- Visual:
  - one decomposition figure or analysis chart
- Source:
  - `What Does Vision Tool-Use Reinforcement Learning Really Learn?`

### Slide 8. Transition: Why Prediction Becomes Necessary

- Key message:
  - These limitations motivate a shift from current-observation competence to predictive multimodal learning.
- Content:
  - summarize the bridge:
    - current observations are often insufficient
    - actions change future information
    - long-horizon tasks require anticipating future states and outcomes
- Visual:
  - a stripped-down transition diagram
  - or the agenda figure with the `Predict` part highlighted

### Slide 9. Current Work: Video Data Foundations for Predictive Multimodal Learning

- Key message:
  - Video is a scalable basis for learning how multimodal environments evolve over time.
- Content:
  - define predictive multimodal learning at a high level
  - explain why video is central
  - introduce the scientific question:
    - how should video data be cleaned, segmented, filtered, annotated, and organized for predictive learning?
- Visual:
  - one conceptual slide on `current observations -> future frames / clips`
  - avoid pipeline details

### Slide 10. Future Program: Integrating Prediction into Multimodal Agent Systems

- Key message:
  - Prediction should improve perception, reasoning, and action, not remain a standalone modeling ability.
- Content:
  - future directions:
    - predictive objectives for multimodal agents
    - longer-horizon multimodal state modeling
    - anticipating action outcomes
    - integrating predictive models into agent systems
- Visual:
  - system-level diagram showing prediction feeding back into the agent loop

### Slide 11. Why This Matters for a Visit

- Key message:
  - A visit would let me connect my RL background with predictive multimodal learning in a stronger collaborative setting.
- Content:
  - what I can bring:
    - RL for multimodal models
    - analysis of training dynamics and behavior
    - data-centric perspective on predictive learning
  - what I hope to explore:
    - prediction-aware multimodal agents
    - video-based predictive learning
    - long-horizon multimodal decision making
- Visual:
  - optional; can be text-only
- Note:
  - this slide can be customized per professor

### Slide 12. Closing

- Key message:
  - My long-term goal is to build multimodal agents that perceive, reason, act, and predict in partially observed environments.
- Content:
  - one-line summary
  - email / homepage
- Visual:
  - reuse the main agenda figure or a simplified closing graphic

## Minimal Version

- If time is short, the minimum viable deck is:
  - Slide 1. Title
  - Slide 2. Research Agenda
  - Slide 4. Past Work Overview
  - Slide 8. Transition
  - Slide 9. Current Work
  - Slide 10. Future Program
  - Slide 12. Closing

## Customization Strategy

- For RL-oriented professors:
  - spend more time on Slides 5--7
  - compress Slides 9--10
- For multimodal foundation model professors:
  - keep Slides 5--6 shorter
  - spend more time on Slides 9--10
- For video / world-model / agent professors:
  - emphasize Slides 8--10
  - use one concrete motivating example such as streaming video decision-making

## Slide Design Notes

- Prefer claim-style slide titles rather than topic-only titles.
- Keep one main point per slide.
- Minimize text; use one result figure or one conceptual graphic per slide.
- Separate `past work` and `current / future work` with distinct color coding.
- Do not turn the talk into a chronological paper list.
- Keep paper titles secondary; foreground the scientific question and takeaway.

## Candidate Asset List

- agenda figure from the research statement
- one result figure from `Rethinking RL Scaling`
- one framework/result figure from `One RL to See Them All`
- one analysis figure from `Med`
- one conceptual figure for video-based predictive multimodal learning

## Next Step

- Turn this outline into an actual slide deck with a first-pass design template.
