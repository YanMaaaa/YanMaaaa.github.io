# Furong Huang, UMD: Outreach Background

Created: 2026-05-08

## Basic Information

- Name: Furong Huang
- Email salutation: `Dear Professor Huang,`
- Institution: University of Maryland, College Park
- Department: Computer Science; affiliated with UMIACS, ECE, Maryland Robotics Center
- Homepage: <https://furong-huang.com/>
- UMD CS page: <https://www.cs.umd.edu/people/furongh>
- Email from public pages:
  - `furongh@cs.umd.edu`
  - course page also lists `furongh@umd.edu`

## User-Provided Recent XHS Note

Professor Huang's 2026-05-08 Xiaohongshu post says she will travel:

- Bay Area: 2026-06-07 to 2026-06-15
- China: 2026-06-16 to 2026-07-05
- Korea / ICML: 2026-07-05 to 2026-07-11

Research phrases from the post:

- "test time compute" should be spent intelligently
- symbolic representation for robotics / "robots growing a brain"
- world models that do not collapse or act blindly
- physical intelligence

This is a strong soft signal that her current interests overlap with:

- world models
- physical intelligence
- symbolic / abstract representations
- efficient test-time reasoning
- agents that act reliably rather than brute-force learning

Yan is open to mentioning the XHS post in the formal email, but it should be brief and secondary. Use official papers/pages as the main formal hook.

## Public Research Fit

Official homepage summary:

- trustworthy machine learning
- sequential decision-making
- generative AI
- foundation models for robotics
- robust, interpretable, aligned AI systems

UMD CS / robotics pages emphasize:

- trustworthy ML
- AI for sequential decision-making
- generative AI
- foundation models for robotics
- perception, planning, and control across robotic platforms
- robust / adaptable / safe systems in dynamic real-world environments

Course signal:

- CMSC848N `Generative AI Agents` covers LLM/VLM agents, RL/RLHF, reasoning models, alignment, self-improvement, agent safety, tool/web/code agents, and world models for web, robotics, and simulation environments.

## Current Fit Assessment

- Overall fit: **high**
- Scientific fit: **high**
- Administrative signal: **medium**
- Robotics risk: **medium**
- Best use: **early main target**

This is much stronger than Yao Qin for Yan's current pitch. The overlap is direct across:

- multimodal agents
- RL post-training / RLHF / alignment
- world models
- video / sequential image reasoning
- physical intelligence / robotics-adjacent foundation models

The main caveat is robotics. Yan does not have real-robot / control / hardware experience, so the email should frame the fit as upstream video/world-model/foundation-model work, not real-robot manipulation or deployment. Yan is comfortable with robotics-adjacent projects as long as the core contribution is video/world-model/foundation-model or multimodal-agent learning rather than hardware/control.

## Soft Information From Yan

User-provided soft information is strongly positive:

- A source who spent PhD + one postdoc year at UMD and collaborated with Furong Huang on multiple projects reported that her knowledge and guidance were helpful.
- Lab environment is described as allowing students to work calmly; she is tenured and not perceived as overly pushy.
- No first-year publication pressure was reported, but students can also build a strong publication profile if self-driven.
- Group has strong compute and enterprise collaborations.
- Internship support is described as strong, with industry connections and recent graduates going to OpenAI, Google, Meta, and other top labs.
- Academic career support also exists; one student reportedly went to Yale as a postdoc.
- Research directions are described as flexible; PhD students can choose topics they are interested in.
- Main downside: group is large, so students need to be self-driven. TA duty may also be a downside.
- Summary from the source: strongly recommended; no obvious negative feedback heard.

Conclusion:

- Advising / lab-risk signal: **low based on available soft information**
- Opportunity signal: **high**
- This is not merely a template warm-up target; it is worth a carefully customized email.

## Best Paper / Project Hooks

### Hook 1: Agentic Critical Training

Project: `Agentic Critical Training`

Why it fits Yan:

- Very recent agent-training work.
- Uses reinforcement learning to train agents to judge action quality rather than merely imitate expert behavior or pre-written reflections.
- Directly connects to Yan's past work on RL post-training for multimodal reasoning and tool-use agents.
- Helps frame a visiting direction around what RL should teach multimodal agents beyond imitation.

Best use in email:

> I was particularly interested in your recent Agentic Critical Training work on training agents to reason about action quality rather than merely imitate expert behavior.

### Hook 2: MomaGraph

Project: `MomaGraph: State-Aware Unified Scene Graphs with Vision-Language Model for Embodied Task Planning`

Why it fits Yan:

- Very recent embodied-agent / VLM / planning work.
- Uses state-aware scene representations and VLMs for embodied task planning.
- Includes RL-trained VLM components and connects structured representations with decision making.
- Aligns with Yan's future direction on predictive / structured representations for multimodal agents in evolving environments.

Risk:

- Robotics-adjacent. Do not write as if Yan wants to do robot control / manipulation.

Best use in email:

> I was also excited by MomaGraph, especially its use of state-aware scene representations for embodied task planning.

### Hook 3: Mementos / TraceGen / Lemon

These are still useful background hooks but should not be the main email hook for the current draft.

Potential use:

- `Mementos`: useful if emphasizing MLLM reasoning over image sequences.
- `TraceGen`: useful if emphasizing structured world models from videos.
- `Lemon`: useful if emphasizing 3D multimodal / spatial understanding.
- `Deliberative Alignment`: less relevant to Yan's main pitch unless focusing on safety / reliability.

## Recommended Email Angle

Best angle:

> multimodal agents that learn from evolving visual inputs, with video/world-model learning as a bridge from MLLM reasoning to physical or real-world decision making.

Suggested professor-specific paragraph:

> I was particularly interested in your recent Agentic Critical Training work on training agents to reason about action quality, and MomaGraph on state-aware scene representations for embodied task planning. These projects connect closely to my interest in how multimodal agents can move beyond single-step visual reasoning toward reasoning and acting in evolving visual environments.

This paragraph avoids claiming real-robot expertise while still showing strong fit.

## Topics to Emphasize

- RL post-training for multimodal perception, reasoning, and tool use.
- Predictive multimodal learning from video.
- Image/video sequences as evolving visual contexts.
- World-model learning with abstract / structured representations.
- Multimodal agents that use prediction for reasoning and decision making.
- Reliability in changing environments, but only as a supporting theme.

## Topics to Avoid or De-Emphasize

- Do not lead with healthcare, fairness, watermarking, or misinformation.
- Do not present Yan as a real-robot / control / hardware student.
- Do not overemphasize pure LLM safety / jailbreak / watermarking.
- Do not mention XHS directly unless intentionally using a lighter personal tone.

## Information Needed From Yan

Before drafting the actual email, clarify:

1. **Willingness**
   - If Professor Huang responds positively, would Yan seriously consider UMD / her group?
   - Is Yan comfortable with a project that is robotics-adjacent but not real-robot-control centered?

2. **Preferred hook**
   - Choose the main email hook:
     - Agentic Critical Training: RL training for agents to reason about action quality
     - MomaGraph: state-aware scene graphs for embodied task planning
     - Mementos / TraceGen / Lemon as backup hooks
   - Current recommendation: use **Agentic Critical Training + MomaGraph** together.

3. **Soft information**
   - Student-feedback signal is strongly positive based on Yan's source.
   - Unknown whether she responds to cold emails.
   - Unknown whether the group accepts visiting Ph.D. students.
   - Unknown funding expectations.

4. **Tone**
   - Should the email mention the XHS post indirectly?
   - Updated recommendation: it is okay to mention the XHS post briefly because it gives a natural meeting context, but the research fit should still rely on official papers/projects.
   - Separate XHS DM can mention that Yan sent an email and would be glad to meet in Shanghai / at ICML if convenient.
   - Yan will attend ICML 2026 in Seoul and present an ICML paper, so ICML meeting can be mentioned in the formal email.
   - Do not invite her to Yan's group on behalf of the advisor/lab in the first email because this has not been confirmed. If needed, say Yan can help connect her with Pengfei Liu only after interest is established.

5. **Funding / logistics**
   - Same default timing:
     - remote collaboration around July-August 2026
     - in-person visit from around September 2026 to February 2027
   - Do not mention personal self-funding in the first email.

## Tentative Decision

Proceed. This is a strong candidate for the second email.

Recommended subject:

> Prospective Visiting PhD Student in Multimodal Agents and World Models

Recommended attachments:

- CV
- research statement

## Contact Strategy

Use two channels with different purposes:

1. Formal email:
   - Main purpose: visiting Ph.D. opportunity + research fit.
   - Tone: professional, concise, research-centered.
   - Mention official work only, especially Agentic Critical Training and MomaGraph.
   - Mention that Yan will attend ICML 2026 in Seoul and would be glad to meet briefly there if convenient.
   - It is acceptable to include one light sentence saying Yan saw her note about the summer trip / ICML schedule.
   - Do not mention inviting her to Yan's group unless the advisor/lab has agreed.

2. Xiaohongshu DM:
   - Main purpose: light nudge and informal meeting possibility.
   - Tone: short, Chinese, casual but respectful.
   - It is okay to mention her public XHS travel note.
   - Mention that Yan has sent a formal email, and if she is in Shanghai or at ICML, Yan would be happy to have a short coffee chat.
   - Do not paste the full email into DM.
