# Research Statement

## Working Title

Toward Multimodal Agents that Perceive, Reason, Act, and Predict

## Current Draft

I view multimodal agents as goal-directed systems that work in partially observed multimodal environments, where they must perceive what is happening, reason about it, act to gather useful information, and predict what will happen next. Such systems are needed to complete long-horizon multimodal tasks that unfold through interaction, such as multi-step computer use, decision-making from video or audio streams, and embodied tasks like robotics or driving.

A central question motivating my research is how multimodal agents can not only perceive, reason, and act based on current observations, but also predict how the world will evolve after their actions. So far, my work has mainly focused on the first part of this question, using reinforcement learning (RL) to improve reasoning, perception, and tool use in multimodal foundation models. More recently, I have begun to extend this agenda toward predictive multimodal learning by studying how large-scale video data can support the anticipation of future observations and longer-term outcomes.

To study how multimodal agents perceive, reason, and act under current observations, I have mainly approached this question through RL and asked a more basic question: how does RL change multimodal models? My work shows that these changes are not only about higher benchmark scores. They also appear in training dynamics, in the joint improvement of reasoning and perception, and in what models actually learn in tool-use settings.

First, in reasoning-centric settings, I studied how to make empirical claims about multimodal reasoning RL more transparent and reproducible. Using a from-scratch RL framework and trajectory-level evaluation rather than only final checkpoints, I found that RL reshapes response length, reflection, and other training behaviors, and that it generalizes better than high-quality SFT on visual math tasks. I then asked a broader question: if RL mainly helps on reasoning-heavy tasks, can it really become a general training method for multimodal foundation models? To study this, we designed V-Triune, a unified framework for joint reasoning-and-perception training, and validated stable joint training on 8 tasks (4 reasoning and 4 perception). The results show that RL can shape reasoning and perception together, with complementary gains across the two.

I then became interested in what RL learns when actions start to affect how the model gathers information. In vision tool-use RL, our analysis shows that the gains mostly come from intrinsic capability improvement and reduced tool-induced harm, rather than true tool mastery.

Taken together, these works form one basic line of my research on multimodal agents. I first study how models perceive, reason, and act from current observations, and then move to more agentic settings where actions begin to change the information available to the model. These results also suggest that, for long-horizon multimodal tasks that unfold through ongoing interaction, acting only from current observations is often not enough; models also need to anticipate how future states will evolve and what consequences their actions will bring.

To move toward predictive multimodal learning, I am currently studying the video data foundations needed to teach models how multimodal environments evolve over time. I think of predictive multimodal learning as modeling how multimodal environments evolve over time, where the target may range from future observations to more abstract internal states. From this perspective, video is a uniquely important training source because it provides scalable temporal experience. A central question, then, is how video data should be segmented, filtered, annotated, and organized for predictive learning.

In my current work, I use video generation models as a concrete testbed for this question, in which future states are expressed as future frames or clips. This setting allows me to study how data choices shape the temporal structure that models learn. Going forward, I want to study how predictive models can be integrated into multimodal agent systems, so that anticipating future observations and action outcomes can directly improve perception, reasoning, and action in long-horizon multimodal tasks. In the long run, I hope this line of work will help build multimodal agents that not only understand the present, but also act, plan, and adapt by anticipating what may happen next.

## Figure Sketch (Text)

[Long-horizon multimodal tasks:
computer use | streaming video decision-making | embodied tasks]
                                |
[Partially observed multimodal environments]
                                |
[Perceive] -> [Reason] -> [Act] -> [Predict]
     |             |         |          |
     |             |         |          |
[RL under current observations:
training dynamics | joint reasoning+perception | tool use]
                                \
                                 \
                         [Prediction becomes necessary when
                          actions change future information
                          and tasks unfold over time]
                                          |
                         [Video data foundations for
                          predictive multimodal learning]
                                          |
                         [Video as scalable temporal experience]
                                          |
                         [Current testbed:
                          video generation models]
                                          |
                         [Future program:
                          integrate prediction into multimodal agent systems]
                                          |
                         [Goal:
                          agents that act with foresight,
                          plan, and adapt]
