# Third Stage Insights

This document summarizes the observations and conclusions from the third stage of experimentation in the *Ghosts ’n Goblins* project. At this stage, the focus was on **agent behavior stability**, **environment complexity**, and identifying limitations of the current training setup.

---

## Improved Performance on Early Obstacles

After several hours of training with the revised reward function and single-life episode structure, the agent shows clear improvements:

* The stone pillar section at the beginning of the level is now traversed consistently.
* The agent demonstrates stable timing and movement patterns in this part of the level.

**Insight:**
This indicates that the reward shaping and episode design are sufficient for learning repetitive and well-structured obstacles.

---

## Emergence of a Hard Decision Point

The next section of the level introduces a more complex challenge:

* The agent can choose between two routes: going **over a hill** or **under the hill**.
* Both routes are viable, but they differ significantly in difficulty and required precision.

In this section, the agent’s performance degrades noticeably.

---

## Human Inspection of the Level Design

To better understand the agent’s failure mode, the level was played manually.

This revealed a critical detail:

* When taking the route **over the hill**, the player must perform a **very precise jump** shortly after the hill.
* Small deviations in timing or position lead to failure.

**Insight:**
The agent’s difficulties are not due to random behavior but are a direct consequence of a highly sensitive gameplay mechanic that requires precise control.

---

## Implications for Training Strategy

Reaching this level of precision highlights the limitations of the current training setup.

Two main paths forward are identified:

* **Significantly longer training times**, allowing the agent to eventually discover and refine the required behavior through exploration.
* **More sophisticated training strategies**, reducing the search space and improving learning efficiency.

---

## Identified Areas for Improvement

Based on these observations, the following improvements are considered necessary for the next stage:

* **Enhanced reward monitoring** to better analyze where and why the agent fails.
* **Improved data preprocessing**, tailored specifically to the structure and mechanics of *Super Ghouls ’n Ghosts*.
* Better alignment between observations, rewards, and critical gameplay events.

These changes aim to support learning in sections that require high precision rather than simple forward progression.

---

## Conclusion

The third stage confirms that the current approach is capable of learning stable behaviors for simpler sections of the game. However, more complex level design elements expose the need for deeper instrumentation and more informed training strategies.

This stage serves as a transition point from basic reward shaping toward more advanced reinforcement learning techniques.

---

## Status

The agent is partially successful and demonstrates consistent progress, but further refinement is required to handle precision-critical sections of the level.
