# Research Talk Base Deck Outline V1

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

### Slide 2. Past Work Overview

- Key message:
  - My past work studies what RL changes in multimodal models under current observations.
- Content:
  - opening sentence:
    - `So far, my work has focused on what RL changes in multimodal models.`
  - three takeaways:
    - `RL for multimodal reasoning reshapes training behavior and improves generalization.` `[1]`
    - `Unified RL reveals positive transfer between reasoning and perception under matched budgets.` `[2]`
    - `Vision tool-use RL gains mainly come from reducing tool-induced harm.` `[3]`
  - closing sentence:
    - `Taken together, these works study how multimodal models perceive, reason, and act under current observations, which motivates my broader interest in prediction for long-horizon multimodal tasks.`
- Visual:
  - three-box overview or three takeaway cards
  - citations `[1][2][3]` can appear in small text at the bottom

### Slide 3. Why This Leads to Prediction

- Key message:
  - The limits revealed by my past work motivate a shift toward predictive multimodal learning for long-horizon multimodal tasks.
- Content:
  - opening sentence:
    - `My past work mainly studies multimodal competence under current observations, but long-horizon multimodal tasks expose a broader limitation.`
  - three points:
    - `Long-horizon multimodal tasks unfold under partial observation.`
    - `In these tasks, actions have delayed consequences and change future information.`
    - `Agents therefore need models of how environments evolve over time, not only reactions to the present.`
  - representative examples:
    - `interactive computer use across multiple tools and interfaces`
    - `streaming video decision-making`
    - `embodied interaction and control`
  - closing sentence:
    - `This is why I am moving toward predictive multimodal learning, especially from video as a scalable source of experience about how environments evolve over time.`
- Visual:
  - one transition slide or conceptual figure
  - emphasize long-horizon multimodal tasks rather than isolated examples
- Role note:
  - this page is about personal trajectory: why my past work leads to prediction

### Slide 4. Research Agenda

- Key message:
  - My research agenda connects a past RL line with a current and future predictive line.
- Content:
  - top sentence:
    - `I study multimodal agents in partially observed environments through two connected lines: RL under current observations, and predictive multimodal learning for long-horizon tasks.`
  - use this slide as a map rather than another argument slide
  - keep only three short anchors around the figure:
    - `Past: how RL changes multimodal models`
    - `Current: video data foundations for predictive multimodal learning`
    - `Long-term: integrate prediction into multimodal agent systems`
  - bottom segue:
    - `I will start with the first question in this agenda: what RL actually changes in multimodal models, before turning to my current work on predictive multimodal learning from video.`
- Visual:
  - the full agenda figure from the research statement
  - do not repeat all Slide 2 / Slide 3 text on this page
  - use the figure as a global map for the rest of the talk

### Slide 4 Figure Design Notes

- Purpose:
  - show the whole research agenda in one view
  - connect the past RL line and the predictive line without turning the slide into a flowchart full of text
- Recommended layout:
  - center:
    - the main agenda figure
  - top:
    - one short agenda sentence
  - around the figure:
    - three small anchor labels for `Past`, `Current`, and `Long-term`
  - bottom:
    - one short segue sentence
- Figure content:
  - research object:
    - multimodal agents in partially observed environments
  - core loop:
    - perceive / reason / act / predict
  - left branch:
    - past work on RL under current observations
  - right branch:
    - predictive multimodal learning from video
  - final destination:
    - multimodal agents that use prediction to improve perception, reasoning, and action
- Figure style:
  - this should feel like an agenda map, not a paper taxonomy and not a dense box-and-arrow pipeline
  - keep the left side visually associated with past RL work
  - keep the right side visually associated with current and future predictive work
  - avoid adding detailed bullet text inside the figure
  - prefer one memorable visual metaphor over many boxes
- Practical note:
  - if Slide 1 already uses the figure, keep Slide 1 cropped or simplified
  - reserve the full figure for Slide 4 so it still feels like a reveal

### Slide 5. How Can We Make Claims About What RL Changes Trustworthy?

- Key message:
  - this work was less about another final-score gain, and more about making empirical claims in an emerging area transparent and defensible
- Content:
  - field context:
    - early multimodal reasoning RL had many follow-up works, heterogeneous codebases, and evaluation that emphasized final performance tables
  - central move:
    - build a transparent from-scratch RL framework for VLMs
    - evaluate full learning trajectories rather than only final checkpoints
  - one-line slide sentence:
    - `I built a transparent from-scratch RL framework and evaluated full learning trajectories, rather than only final checkpoints.`
- Visual:
  - use a simple contrast figure rather than a dense paper diagram
  - left:
    - fragmented practice: different frameworks, opaque training code, final-table reporting
  - right:
    - my setup: from-scratch framework + repeated checkpoint evaluation + learning curves
  - if needed, the original four-step framework can appear as a simplified inset rather than the main visual
- Source:
  - `Rethinking RL Scaling for Vision Language Models`

### Slide 6. What Does RL Actually Change In Visual Reasoning Models?

- Key message:
  - trajectory-level evaluation reveals both behavioral changes during training and stronger generalization than SFT
- Content:
  - main conclusion:
    - RL changes training behavior during learning, not only final performance
  - empirical findings to emphasize orally:
    - response length and reflection change during training
    - response length is seed-sensitive
    - RL generalizes better than SFT even with high-quality supervision
  - one-line slide sentence:
    - `Trajectory-level evaluation shows that RL reshapes training behavior and generalizes better than SFT, even with high-quality supervision.`
- Visual:
  - one large representative training-dynamics panel
  - one smaller RL-vs-SFT generalization comparison
  - do not paste the full four-panel paper figure unchanged; crop or redraw for presentation clarity
- Source:
  - `Rethinking RL Scaling for Vision Language Models`

### Optional Backup Slide For Paper 1

- Possible title:
  - `Why Look Beyond Final Checkpoints?`
- Use only if the audience wants more detail on methodology
- Content:
  - why final tables are insufficient for RL
  - why seed variance and learning trajectories matter
  - how repeated checkpoint evaluation made the final claims more trustworthy

### Slide 7. Can RL Jointly Shape Perception and Reasoning?

- Key message:
  - unified RL can become a more general post-training method only if it helps not just reasoning-heavy tasks, but also perception-heavy tasks that support grounding and action
- Content:
  - opening framing:
    - `For multimodal agents, better reasoning alone is not enough; they also need stronger perceptual grounding for action and decision making.`
  - one-line slide sentence:
    - `Under matched budgets, unified RL matches or outperforms specialist mixtures across both perception and reasoning.`
  - optional supporting line:
    - `This suggests positive transfer rather than a clear reasoning-perception trade-off.`
- Visual:
  - left:
    - `fair_budget_evidence` task-composition curves
  - right:
    - a simplified benchmark summary rather than the full paper table
  - keep this slide focused on the scientific claim, not the full methodology
- Source:
  - `One RL to See Them All`

### Slide 8. How Did I Make Unified Multimodal RL Possible?

- Key message:
  - unified multimodal RL is not just a matter of mixing tasks; it needs an explicit methodology for heterogeneous rewards, verifiers, and observability
- Content:
  - one-line sentence:
    - `V-Triune organizes unified multimodal RL around reward routing, verifier-level outcome verification, and source-level diagnostics.`
  - three components:
    - reward routing
    - verifier-level outcome verification
    - source-level diagnostics
- Visual:
  - the V-Triune framework figure
  - simplify labels if needed, but keep the three abstractions visible

### Slide 9. What Makes Unified Multimodal RL Stable In Practice?

- Key message:
  - stable unified multimodal RL required better localization rewards, source-level observability, and careful training recipes
- Content:
  - one-line sentence:
    - `Stable unified multimodal RL required better localization rewards, source-level observability, and careful training recipes.`
  - three supporting points:
    - `Dynamic IoU` avoids the ambiguity-versus-sparsity trade-off in localization rewards
    - `Source-level diagnostics` reveal hidden task-specific behaviors and failures during unified training
    - `Training recipes matter`: continuing to update the vision encoder can hurt perception performance
  - note:
    - different response patterns across reasoning and perception tasks can be presented as the most intuitive example of source-level diagnostics
- Visual:
  - use `combined_iou_source_level` as the main figure
  - highlight panels (a), (b), and (c) as one integrated story about stability and observability

### Slide 10. What Does Vision Tool-Use RL Really Learn?

- Key message:
  - this is the first past-work setting where actions can change the visual evidence available to the model
- Content:
  - opening framing:
    - `This is my first setting where actions can change the visual evidence available to the model.`
  - introduce MED as the analysis lens:
    - Measure intrinsic drift versus tool-induced effects
    - Explain gain versus harm
    - Diagnose what changes over training
  - teaser line:
    - `This analysis lets us ask whether tool-use RL mainly improves tool use itself, or mostly changes the model in other ways.`
  - keep the slide focused on the question and the analysis setup
- Visual:
  - use the MED framework figure as the main visual
- Source:
  - `What Does Vision Tool-Use Reinforcement Learning Really Learn?`

### Slide 11. Do Gains Come From Intrinsic Learning or Tool-Induced Effects?

- Key message:
  - most gains come from intrinsic learning, while tool-induced effects contribute much less
- Content:
  - one-line sentence:
    - `Most gains come from intrinsic learning, while tool-induced effects contribute much less.`
  - emphasize:
    - tool-free versus tool-available evaluation
    - intrinsic drift dominates overall improvement
- Visual:
  - use `Exp-I` as the main figure
- Source:
  - `What Does Vision Tool-Use Reinforcement Learning Really Learn?`

### Slide 12. Does Vision Tool-Use RL Expand Gain or Mainly Reduce Harm?

- Key message:
  - tool-use RL mainly reduces tool-induced harm rather than continuously increasing tool-based gain
- Content:
  - one-line sentence:
    - `Tool-use RL mainly reduces tool-induced harm rather than continuously increasing tool-based gain.`
  - emphasize:
    - Gross Gain versus Gross Harm
    - why the net tool gap saturates
- Visual:
  - use `Exp-II` as the main figure
- Source:
  - `What Does Vision Tool-Use Reinforcement Learning Really Learn?`

### Slide 13. Why Does Tool Gain Remain Limited?

- Key message:
  - RL suppresses harmful tool-side behavior more than it improves correction of intrinsically hard failures
- Content:
  - one-line sentence:
    - `RL suppresses harmful tool-side behavior more than it improves correction of intrinsically hard failures.`
  - emphasize:
    - factor decomposition
    - limited improvement on the hardest failure cases
- Visual:
  - use `Exp-III` as the main figure
- Source:
  - `What Does Vision Tool-Use Reinforcement Learning Really Learn?`

### Slide 14. What Do These Results Suggest for Future RL Design?

- Key message:
  - the main value of these extra analyses is not just more evidence, but a clearer design implication for future RL algorithms
- Content:
  - one-line sentence:
    - `These results suggest that future RL should target hard-failure correction more directly, rather than mainly learning safer tool use.`
  - possible supporting elements:
    - rebuttal baselines such as `no-tool RL` and `tool-reward RL`
    - 2--3 crop-and-zoom failure cases
    - one short summary of what current binary outcome reward seems to optimize
  - note:
    - if deck length becomes a problem, this slide can be merged with Slide 13
- Visual:
  - mix one compact baseline comparison with a few qualitative cases

### Slide 15. Why Predictive Multimodal Learning for Long-Horizon Tasks?

- Key message:
  - Many practically important multimodal tasks are long-horizon, partially observed, and interaction-driven, which makes prediction necessary.
- Content:
  - slide-friendly lead-in:
    - `From current-observation competence to long-horizon multimodal tasks`
  - one short core sentence on the slide:
    - `Long-horizon multimodal tasks require anticipating future states and action outcomes.`
  - keep the fuller transition as oral narration rather than slide text
  - representative task labels on the slide:
    - `computer use across tools`
    - `streaming video decision-making`
    - `embodied interaction`
- Visual:
  - a simple bridge layout with the lead-in at top, three task labels, and a prediction-oriented concept graphic
  - avoid project details on this page
- Role note:
  - this page is about task necessity: why long-horizon multimodal tasks need prediction

### Slide 16. Current Project: Video Data Foundations for Predictive Multimodal Learning

- Key message:
  - Video is a scalable basis for learning how multimodal environments evolve over time.
- Content:
  - one-line slide sentence:
    - `I study how video data should be segmented, filtered, annotated, organized, and validated so that models learn useful predictive structure.`
  - three guiding questions:
    - `What temporal structure should video preprocessing preserve?`
    - `What annotations and metadata make predictive learning more effective?`
    - `How do these data choices change what world models actually learn?`
- Visual:
  - recommended structure for this specific page:
    - left: `Raw video`
    - middle: `Segment / Filter / Annotate / Organize / Validate`
    - right: `Predictive models / Video generation / JEPA-like models / Learned predictive structure`
  - bottom line:
    - `Data choices shape what predictive structure models actually learn.`
  - avoid pipeline details

### Slide 17. Future Program: Integrating Prediction into Multimodal Agent Systems

- Key message:
  - Prediction should improve perception, reasoning, and action, not remain a standalone modeling ability.
- Content:
  - bridge from Slide 16:
    - `Video data foundations are my near-term entry point.`
    - `The longer-term goal is to turn predictive models into capabilities that improve how multimodal agents perceive, reason, and act.`
  - one-line slide sentence:
    - `Prediction should feed back into how multimodal agents perceive, reason, and act.`
  - three future questions:
    - `How can anticipating future observations improve perception under partial observation?`
    - `How can longer-horizon multimodal state modeling support reasoning and planning?`
    - `How can action-outcome prediction improve tool use and decision making?`
  - bottom line:
    - `Goal: multimodal agents that act with foresight, not only react to the present.`
- Visual:
  - a clean agent-loop diagram with `Perceive / Reason / Act / Predict`
  - show `Predict` feeding back into the other three capabilities
  - avoid repeating the more data-centric structure from Slide 16

### Slide 18. Why This Direction Matters

- Key message:
  - This direction matters because long-horizon multimodal tasks require agents that can anticipate, not only react.
- Content:
  - three short blocks:
    - `Task Frontier`
      - many practically important multimodal tasks are long-horizon, partially observed, and interaction-driven
    - `Current Gap`
      - current multimodal models are still better at reacting to the present than anticipating what comes next
    - `Research Opportunity`
      - prediction can improve perception, reasoning, and action together
  - bottom line:
    - `The goal is not prediction as a standalone benchmark, but prediction as a core capability of multimodal agents.`
- Visual:
  - simple three-column layout or three labeled cards
  - keep the page significance-oriented rather than project-specific
- Role note:
  - this page is about field significance: why this research direction is worth doing

### Slide 19. Closing

- Key message:
  - My long-term goal is to build multimodal agents that perceive, reason, act, and predict in partially observed environments.
- Content:
  - title:
    - `Toward Multimodal Agents that Perceive, Reason, Act, and Predict`
  - one-line takeaway:
    - `My long-term goal is to build multimodal agents that perceive, reason, act, and predict in partially observed environments.`
  - optional small line:
    - `From current-observation competence to prediction-aware multimodal agents.`
  - footer:
    - email / homepage
- Visual:
  - keep this page minimal
  - optional: a faint version of the agenda figure or a small `Perceive / Reason / Act / Predict` loop
  - do not introduce any new diagram or detail here
- Visual:
  - reuse the main agenda figure or a simplified closing graphic

## Minimal Version

- If time is short, the minimum viable deck is:
  - Slide 1. Title
  - Slide 2. Past Work Overview
  - Slide 3. Why This Leads to Prediction
  - Slide 4. Research Agenda
  - Slide 15. Why Predictive Multimodal Learning
  - Slide 16. Current Project
  - Slide 17. Future Program
  - Slide 19. Closing

## Customization Strategy

- For RL-oriented professors:
  - spend more time on Slides 5--14
  - compress Slides 15--17
- For multimodal foundation model professors:
  - keep Slides 5--14 shorter
  - spend more time on Slides 15--17
- For video / world-model / agent professors:
  - emphasize Slides 3, 15, 16, and 17
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
