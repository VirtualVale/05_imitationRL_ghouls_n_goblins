# First Insights

This document summarizes the **initial observations and learnings** from the early experiments in the *dGhosts ’n Goblins* project. The goal is to capture what worked, what did not, and which direction appears most promising going forward.

---

## Baseline Agents

### Random Agent

The random agent serves as a minimal baseline.

**Insight:**

* A purely random policy is incapable of reaching any meaningful long-term goal.
* While it can occasionally trigger short-term events, it has no notion of progression, survival, or planning.

**Conclusion:**
Useful only as a sanity check for the environment and reward signal, not as a serious candidate for gameplay or assistance.

---

### Brute Agent

The Brute approach (as described in the Arcade Learning Environment literature) leverages determinism by learning **action sequences** that yield high rewards.

**Insight:**

* The Brute is conceptually interesting and can achieve surprisingly good results in deterministic settings.
* However, it does not learn a *policy* or *model* of the game.
* Instead, it memorizes or optimizes action sequences starting from a fixed initial state.

**Why this is a problem for this project:**

* The intended AI Ghost must be able to **take over from an arbitrary position and time** in the game.
* A sequence-based approach cannot seamlessly replace or assist a human player mid-game.

**Conclusion:**
The Brute is not suitable for a human ↔ AI switchable control scenario.

---

## PPO as the Primary Candidate

### Proximal Policy Optimization (PPO)

Among the tested approaches, PPO stands out as the most promising.

**Insight:**

* PPO learns a true policy rather than memorized sequences.
* It is well-suited for continuous interaction and generalization across different game states.
* This makes it a strong candidate for an AI Ghost that can take over control dynamically.

**Conclusion:**
PPO should be the **first algorithm to be tested and iterated on seriously** for this project.

---

## Reward Function: First Experiment Results

### Initial Reward Design

In the first experiments, the reward function was based **only on the in-game score**.

**Observed behavior:**

* The agent quickly learns to maximize score rather than progress through the level.
* In the first screen of *Super Ghouls ’n Ghosts*, enemies (ghouls) spawn infinitely.
* This allows the agent to farm score indefinitely without moving forward.

**Result:**

* The agent remains on the first screen.
* No meaningful level progression occurs.

---

## Key Takeaway for the Next Stage

Relying on score alone as a reward signal is insufficient and actively harmful.

**Next steps:**

* Introduce a reward component for **progressing to the right / advancing in the level**.
* Combine progress-based rewards with survival and penalty signals.
* Ensure that standing still and farming enemies is suboptimal compared to moving forward.

This insight directly shapes the next iteration of reward shaping and environment design.