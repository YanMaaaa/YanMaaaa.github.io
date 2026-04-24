# Research Talk Content Notes

This file tracks the agreed slide content before we turn it into the final deck.

## Current Overall Narrative

- Research object:
  - multimodal agents in partially observed multimodal environments
- Past line:
  - how reinforcement learning changes multimodal models
- Transition:
  - acting only from current observations is often not enough for long-horizon multimodal tasks
- Current and future line:
  - predictive multimodal learning from video
- Long-term goal:
  - integrate prediction into multimodal agent systems so that prediction improves perception, reasoning, and action

## Current Recommended Opening Structure

The previous opening was:

- Slide 1: Title
- Slide 2: Research Agenda
- Slide 3: Central Question

This was coherent, but it introduced the agenda before giving a strong enough signal of what has already been done. For a research talk or visiting meeting, the opening should establish credibility earlier.

The recommended opening is now:

- Slide 1: Title
- Slide 2: Past Work Overview
- Slide 3: Why This Leads to Prediction
- Slide 4: Research Agenda

This order is stronger because:

- by Slide 2, the audience already sees what I have actually done
- by Slide 3, prediction is motivated as a limitation revealed by past work
- by Slide 4, the broader agenda feels earned rather than purely aspirational

## Agreed Opening Slides

### Slide 1. Title

- Title:
  - `Toward Multimodal Agents that Perceive, Reason, Act, and Predict`
- Identity block:
  - Yan Ma
  - Fudan University
  - email
  - homepage
- One-line positioning:
  - `Multimodal agents in partially observed environments`
- Visual:
  - place the main agenda figure on the right

### Slide 2. Past Work Overview

- Core message:
  - so far, my work has mainly studied what RL changes in multimodal models under current observations
- Main points:
  - opening sentence:
    - `So far, my work has focused on what RL changes in multimodal models.`
  - three takeaways:
    - `RL for multimodal reasoning reshapes training behavior and improves generalization.` `[1]`
    - `Unified RL reveals positive transfer between reasoning and perception under matched budgets.` `[2]`
    - `Vision tool-use RL gains mainly come from reducing tool-induced harm.` `[3]`
  - closing sentence:
    - `Taken together, these works study how multimodal models perceive, reason, and act under current observations, which motivates my broader interest in prediction for long-horizon multimodal tasks.`
- Visual:
  - three-box takeaway slide
  - citations `[1][2][3]` can appear in smaller text

### Slide 3. Why This Leads to Prediction

- Core message:
  - the RL line naturally exposes why long-horizon multimodal tasks motivate predictive multimodal learning
- Main points:
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

- Core message:
  - my research agenda connects a past RL line with a current and future predictive line
- Main points:
  - top sentence:
    - `I study multimodal agents in partially observed environments through two connected lines: RL under current observations, and predictive multimodal learning for long-horizon tasks.`
  - three short anchors around the figure:
    - `Past: how RL changes multimodal models`
    - `Current: video data foundations for predictive multimodal learning`
    - `Long-term: integrate prediction into multimodal agent systems`
  - bottom segue:
    - `I will start with the first question in this agenda: what RL actually changes in multimodal models, before turning to my current work on predictive multimodal learning from video.`
- Visual:
  - the full agenda figure
  - use it as a global map, not as another dense argument slide
  - avoid repeating all the bullet content from Slides 2 and 3

### Slide 4 Figure Notes

- Function:
  - this slide is the first full reveal of the agenda figure
  - it should orient the audience for the rest of the talk
- Figure should show:
  - multimodal agents in partially observed environments
  - the `perceive / reason / act / predict` loop
  - the left RL line as past work under current observations
  - the right predictive line as current and future work from video
  - the long-term goal of integrating prediction back into the agent system
- Figure should not try to show:
  - all past-work details from Slide 2
  - all motivation details from Slide 3
  - pipeline stages or implementation specifics
- Visual guidance:
  - agenda map rather than pipeline
  - left and right branches should feel distinct but connected
  - keep text inside the figure minimal
  - let the figure carry structure, and let the surrounding labels carry interpretation

## Current Opening Logic in One Line

- Slide 1:
  - what I study
- Slide 2:
  - what I have done so far
- Slide 3:
  - why this naturally leads beyond current observations
- Slide 4:
  - how the full research agenda is organized

## Likely Next Slides

- Slide 5:
  - `How Can We Make Claims About What RL Changes Trustworthy?`
  - this slide should frame the paper as an early attempt to make a noisy area empirically legible
  - not a `new SOTA` slide, but a `why trust the evidence` slide
  - one-line sentence:
    - `I built a transparent from-scratch RL framework and evaluated full learning trajectories, rather than only final checkpoints.`
  - visual:
    - contrast fragmented practice versus transparent framework plus trajectory evaluation

- Slide 6:
  - `What Does RL Actually Change In Visual Reasoning Models?`
  - this slide should carry the main empirical payoff
  - one-line sentence:
    - `Trajectory-level evaluation shows that RL reshapes training behavior and generalizes better than SFT, even with high-quality supervision.`
  - oral emphasis:
    - response length and reflection change during training
    - response length is seed-sensitive
    - RL generalizes better than SFT
  - visual:
    - one representative training-dynamics figure
    - one compact RL-versus-SFT comparison

- Optional backup slide for Paper 1:
  - `Why Look Beyond Final Checkpoints?`
  - use only if the audience wants more methodology detail

- Slide 7:
  - `Can RL Jointly Shape Perception and Reasoning?`
  - this slide should motivate why perception matters for multimodal agents, without turning into a separate motivation slide
  - opening framing:
    - `For multimodal agents, better reasoning alone is not enough; they also need stronger perceptual grounding for action and decision making.`
  - one-line sentence:
    - `Under matched budgets, unified RL matches or outperforms specialist mixtures across both perception and reasoning.`
  - optional supporting line:
    - `This suggests positive transfer rather than a clear reasoning-perception trade-off.`
  - visual:
    - use the fair-budget evidence as the main figure
    - do not make the methodology the focus on this slide
- Slide 8:
  - `How Did I Make Unified Multimodal RL Possible?`
  - this slide should explain why unified multimodal RL is a methodology problem, not just a mixture-design problem
  - one-line sentence:
    - `V-Triune organizes unified multimodal RL around reward routing, verifier-level outcome verification, and source-level diagnostics.`
  - visual:
    - use the V-Triune framework figure as the main visual
    - keep the three abstractions visible
- Slide 9:
  - `What Makes Unified Multimodal RL Stable In Practice?`
  - this slide should present the most interesting concrete findings that support stable unified training
  - one-line sentence:
    - `Stable unified multimodal RL required better localization rewards, source-level observability, and careful training recipes.`
  - three supporting points:
    - Dynamic IoU avoids the ambiguity-versus-sparsity trade-off in localization rewards
    - source-level diagnostics reveal hidden task-specific behaviors and failures
    - continuing to update the vision encoder can hurt perception performance
  - note:
    - different response patterns across task families should be presented as the most intuitive source-level-diagnostics finding
  - visual:
    - use `combined_iou_source_level` as the main figure
- Slide 10:
  - `What Does Vision Tool-Use RL Really Learn?`
  - this should be the first past-work page where actions explicitly change the visual evidence available to the model
  - opening framing:
    - `This is my first setting where actions can change the visual evidence available to the model.`
  - main job:
    - introduce MED so that later experiment figures are readable
  - teaser line:
    - `This analysis lets us ask whether tool-use RL mainly improves tool use itself, or mostly changes the model in other ways.`
  - visual:
    - use the MED framework figure
- Slide 11:
  - `Do Gains Come From Intrinsic Learning or Tool-Induced Effects?`
  - one-line sentence:
    - `Most gains come from intrinsic learning, while tool-induced effects contribute much less.`
  - visual:
    - use `Exp-I`
- Slide 12:
  - `Does Vision Tool-Use RL Expand Gain or Mainly Reduce Harm?`
  - one-line sentence:
    - `Tool-use RL mainly reduces tool-induced harm rather than continuously increasing tool-based gain.`
  - visual:
    - use `Exp-II`
- Slide 13:
  - `Why Does Tool Gain Remain Limited?`
  - one-line sentence:
    - `RL suppresses harmful tool-side behavior more than it improves correction of intrinsically hard failures.`
  - visual:
    - use `Exp-III`
- Slide 14:
  - `What Do These Results Suggest for Future RL Design?`
  - one-line sentence:
    - `These results suggest that future RL should target hard-failure correction more directly, rather than mainly learning safer tool use.`
  - possible elements:
    - rebuttal baselines such as `no-tool RL` and `tool-reward RL`
    - crop-and-zoom failure cases
    - one short summary of what current binary outcome reward seems to optimize
  - note:
    - if deck length becomes a problem, this slide can be merged with Slide 13
- Slide 15:
  - `Why Predictive Multimodal Learning for Long-Horizon Tasks?`
  - role note:
    - this page is about task necessity: why long-horizon multimodal tasks need prediction
  - oral transition from past work:
    - `My past work has mainly studied multimodal competence under current observations. These studies helped me understand how multimodal models can be shaped to reason, perceive, and use tools more effectively. But many multimodal tasks with real practical value are long-horizon, partially observed, and interaction-driven. In those settings, stronger performance on the current observation is not enough; agents also need to anticipate how the environment will evolve and what their actions will change. That is what led me to predictive multimodal learning.`
  - slide text should be much shorter:
    - lead-in:
      - `From current-observation competence to long-horizon multimodal tasks`
    - one core sentence:
      - `Long-horizon multimodal tasks require anticipating future states and action outcomes.`
    - representative task labels:
      - `computer use across tools`
      - `streaming video decision-making`
      - `embodied interaction`
  - visual:
    - a simple bridge layout with the lead-in at top, three task labels, and a prediction-oriented concept graphic
- Slide 16:
  - `Current Project: Video Data Foundations for Predictive Multimodal Learning`
  - this should be the concrete anchor page for the current project
  - one-line sentence:
    - `I study how video data should be segmented, filtered, annotated, organized, and validated so that models learn useful predictive structure.`
  - three guiding questions:
    - `What temporal structure should video preprocessing preserve?`
    - `What annotations and metadata make predictive learning more effective?`
    - `How do these data choices change what world models actually learn?`
  - visual structure:
    - left: `Raw video`
    - middle: `Segment / Filter / Annotate / Organize / Validate`
    - right: `Predictive models / Video generation / JEPA-like models / Learned predictive structure`
  - bottom line:
    - `Data choices shape what predictive structure models actually learn.`
- Slide 17:
  - `Future Program: Integrating Prediction into Multimodal Agent Systems`
  - this page should move from current project to longer-term research program
  - bridge from Slide 16:
    - `Video data foundations are my near-term entry point.`
    - `The longer-term goal is to turn predictive models into capabilities that improve how multimodal agents perceive, reason, and act.`
  - one-line sentence:
    - `Prediction should feed back into how multimodal agents perceive, reason, and act.`
  - three future questions:
    - `How can anticipating future observations improve perception under partial observation?`
    - `How can longer-horizon multimodal state modeling support reasoning and planning?`
    - `How can action-outcome prediction improve tool use and decision making?`
  - bottom line:
    - `Goal: multimodal agents that act with foresight, not only react to the present.`
  - visual:
    - a clean `Perceive / Reason / Act / Predict` loop
    - `Predict` should visibly feed back into the other three
    - do not reuse the data-foundations layout from Slide 16
- Slide 18:
  - `Why This Direction Matters`
  - role note:
    - this page is about field significance: why this research direction is worth doing
  - this should be a significance page, not a visit/application page
  - one-line sentence:
    - `This direction matters because long-horizon multimodal tasks require agents that can anticipate, not only react.`
  - three short blocks:
    - `Task Frontier`
      - many practically important multimodal tasks are long-horizon, partially observed, and interaction-driven
    - `Current Gap`
      - current multimodal models are still better at reacting to the present than anticipating what comes next
    - `Research Opportunity`
      - prediction can improve perception, reasoning, and action together
  - bottom line:
    - `The goal is not prediction as a standalone benchmark, but prediction as a core capability of multimodal agents.`
  - visual:
    - three-column layout or three cards
    - keep it significance-oriented rather than project-specific
- Slide 19:
  - `Toward Multimodal Agents that Perceive, Reason, Act, and Predict`
  - this should be a minimal closing page that echoes the title slide
  - one-line takeaway:
    - `My long-term goal is to build multimodal agents that perceive, reason, act, and predict in partially observed environments.`
  - optional small line:
    - `From current-observation competence to prediction-aware multimodal agents.`
  - footer:
    - email / homepage
  - visual:
    - optional faint agenda figure or a small `Perceive / Reason / Act / Predict` loop
    - no new detail on this page

## Paper 2 Structure

- Slide 7:
  - scientific payoff
- Slide 8:
  - methodology / framework
- Slide 9:
  - concrete stability and diagnostics findings

## Paper 3 Structure

- Slide 10:
  - question plus MED framework
- Slide 11:
  - main answer on intrinsic versus tool-induced effects
- Slide 12:
  - gain versus harm
- Slide 13:
  - diagnosis of why gain remains limited
- Slide 14:
  - extra baselines, failure cases, and future design implications
