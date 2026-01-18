# Second Stage Insights

This document captures the key insights and technical learnings from the second stage of experimentation in the *dGhosts ’n Goblins* project. This stage focused primarily on **reward shaping via emulator memory access** and its impact on agent behavior.

---

## Memory-Based Progress Signal

With the help of the emulator and its memory watch functionality, a critical memory address was identified:

* **Memory address:** `8265370`

This address reliably stores the player’s **progress within the level** and provides a clean, monotonic signal for forward movement.

**Insight:**

* This value is far better suited for reward shaping than raw score.
* It directly encodes level progression, which aligns with the intended objective of the agent.

As a result, this address can be used as the primary signal to reward the agent for moving forward through the level.

---

## Integration into stable-retro

To make use of this new signal, changes were required in the stable-retro configuration:

* The new memory value must be declared as a data source in `data.json`.
* The reward logic referencing this value must be implemented in `scenario.json`.

This integration allows the environment to expose level progress in a structured way and enables reward shaping without modifying the emulator core.

---

## Effects of the New Reward Function

After introducing the progress-based reward and **strongly reducing the influence of score**, the agent’s behavior changed significantly:

* For the first time, the agent actively attempts to progress through the level.
* The agent starts jumping over stone pillars and other early obstacles.
* However, this behavior is not yet consistent and remains unstable.

**Key observation:**
Rewarding level progress successfully shifts the agent’s objective from score farming to actual gameplay progression.

---

## Issues with Score and Life Handling

At this stage, the environment still uses **three lives per episode**.

This leads to an important problem:

* The total reward is effectively aggregated across multiple lives.
* A run consisting of two very short lives and one very long life can yield the same reward as three medium-length lives.

**Insight:**

* This makes the score signal diffuse and hard to interpret.
* It weakens the pressure on the agent to optimize a single, high-quality run.

Additionally, because the episode restarts at the beginning of the level after losing a life, the current episode termination logic does not reflect the true objective of the task.

---

## Conclusion and Next Direction

The introduction of a memory-based progress reward marks a major step forward. However, the current life-based episode structure limits learning efficiency.

**For the next stage:**

* The environment should be restricted to **a single life per episode**.
* Episode termination should occur immediately upon death.
* The agent must therefore learn to maximize **one continuous run** rather than accumulating progress across multiple retries.

This change is expected to encourage deeper, more consistent runs and better align the learning objective with the intended gameplay experience.

---

## Status

This stage represents a clear improvement over score-based reward shaping and provides a strong foundation for further refinement of agent behavior.
