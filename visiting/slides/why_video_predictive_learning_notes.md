# Why Video for Predictive Multimodal Learning

This note records the current conceptual framing for the Beamer transition page from past multimodal RL work to video-based predictive multimodal learning.

## Slide Role

This page should answer **why video**.

It should not yet explain the current project's full data-foundation design. The next page can explain which video data choices matter, such as segmentation, filtering, annotation, and organization.

The page should function as a compact bridge:

1. Past work: multimodal models at a single or short horizon.
2. Agent setting: long-horizon multimodal tasks unfold as temporal interaction.
3. Prediction: future-state and action-outcome estimates can improve decision making.
4. Video: scalable temporal observations provide a practical entry point for learning how multimodal states evolve.

## Core Distinction

Past work mostly studies current-observation competence:

```tex
o_t
\xrightarrow{\;\text{Model}_{\text{\tiny perceive, reason, act}}\;}
y_t
```

Here, the model receives a multimodal input at a single timestep or short horizon, such as an image, a short video, and/or text instruction, and produces an answer or action.

Long-horizon multimodal agents are different because the system is embedded in an environment over time:

```tex
(o_1, a_1, o_2, a_2, \ldots, o_T)
```

The agent is goal-conditioned and repeatedly observes, reasons, acts, and receives new observations.

Prediction enters as a capability that can support decision making:

```tex
(o_{\le t}, a_t) \mapsto \hat{o}_{t+1:t+H}
```

This should not be stated as "agents must predict before acting." Agents can act reactively. The more defensible claim is that prediction can improve long-horizon decision making by estimating how future states and outcomes may evolve.

## Why Video

Video should not be framed as ordinary supervised learning over context-frame/future-frame pairs on this slide.

A better framing:

```tex
\textbf{Video:}\quad
(o_1, u_1, o_2, u_2, \ldots, o_T),
\quad u_t = \text{unobserved dynamics / implicit action}
```

Video is not a full agent rollout because it usually lacks explicit agent actions, goals, and interventions. However, video is an observation-rich proxy for temporal environment evolution. It contains state transitions driven by latent causes such as human motion, object dynamics, camera motion, scene changes, and implicit interactions.

Thus, video is a scalable entry point for learning predictive multimodal structure:

```tex
\text{video} \approx \text{scalable temporal observations of evolving multimodal states}
```

## `a_t` vs. `u_t`

Use this distinction if needed:

```tex
a_t: \text{explicit agent action}
\qquad
u_t: \text{unobserved dynamics / implicit action}
```

or:

```tex
(o_t, a_t, o_{t+1}) \quad \text{agent rollout}
\qquad
(o_t, u_t, o_{t+1}) \quad \text{video rollout}
```

`a_t` is chosen by the agent. It is an explicit control variable and supports action-conditioned prediction.

`u_t` is an unobserved or implicit factor that explains how one video observation transitions to the next. It may correspond to human actions, camera motion, object motion, physical dynamics, cuts, or other hidden causes. It is inferred rather than commanded. The notation `u_t` is preferred over `z_t` here to avoid confusion with a learned latent state such as `s_t` in world-model methods.

## Recommended Slide Shape

Prefer symbolic structure over many nodes. The page should be readable at a glance.

Possible compact formula layout:

```tex
\[
\begin{aligned}
\textbf{Past work:}\quad
& o_t
  \xrightarrow{\;\text{Model}_{\text{\tiny perceive, reason, act}}\;}
  y_t \\
\textbf{Agent rollout:}\quad
& o_t \xrightarrow{\;a_t\;} o_{t+1},
  \qquad
  (o_1, a_1, o_2, a_2, \ldots, o_T) \\
\textbf{Video rollout:}\quad
& o_t \xrightarrow{\;u_t\;} o_{t+1},
  \qquad
  (o_1, u_1, o_2, u_2, \ldots, o_T) \\
\textbf{Prediction:}\quad
& \text{estimate future observations under transition drivers}
\end{aligned}
\]
```

Bottom message:

```tex
Video is a scalable entry point for learning how multimodal states evolve over time.
```

## Wording Constraints

Avoid:

- "agents must predict before acting"
- "video is supervised learning over context frames to future frames"
- "video is a full multimodal agent rollout"
- introducing a new term such as "predictive agent"

Prefer:

- "prediction can improve long-horizon decision making"
- "video is an observation-rich proxy for temporal environment evolution"
- "video provides scalable temporal observations"
- "learn how multimodal states evolve over time"
