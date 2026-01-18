# 👻🎮 Imitation Learning with Ghost n Goblins

> *An experimental Reinforcement Learning project inspired by AI-controlled “ghost” gameplay.*

Insights:
[text](0_initial-insights-stage-0.md)
[text](1_insights-stage-1.md)
[text](2_insights-stage-2.md)

---

## 🚀 Motivation

Sony recently announced a technology concept often referred to as **AI Ghosts**: a mode where an AI can take over gameplay for the player. The idea is that players can switch on a *Ghost Mode* and let the game play itself, helping them through particularly difficult passages.

Around the same time, the **Ghosts ’n Goblins** franchise appeared in the *Stranger Things* series, which sparked renewed interest in the game. Interestingly, this showcase caused some controversy: while *Ghosts ’n Goblins* is suggested, the footage shown is actually **Super Ghouls ’n Ghosts**.

This combination of recent trends and the series showcase directly motivated this project.

As a small nod to that controversy, this repository is intentionally called **Ghosts ’n Goblins**, even though the actual target game is **Super Ghouls ’n Ghosts** on the **Super Nintendo Entertainment System (SNES)**.

---

## Project Idea 💡

The core idea of this project is to build an **AI Ghost** for a classic side‑scrolling action game:

* Train a Reinforcement Learning (RL) agent that can play *Super Ghouls ’n Ghosts*.
* Use the trained agent as an *AI Ghost* rather than a full replacement for the player.
* Allow seamless switching between **human control** and **AI control** during gameplay.

The goal is not just to beat the game automatically, but to create a system that can:

* Step in when a section is too difficult
* Help the player recover from mistakes
* Hand control back to the player at any time

---

## Technical Foundation 🛠️

This project is built on top of the excellent **stable-retro** framework:

* stable-retro provides a Gymnasium-compatible interface for classic console games
* It allows programmatic control of emulators, access to observations, rewards, and actions
* It significantly reduces the boilerplate needed to start Reinforcement Learning experiments on retro games

Using stable-retro made it possible to focus on:

* reward shaping
* agent behavior
* human–AI interaction

instead of emulator internals.

---

## Roadmap 🗺️

### 1. Reinforcement Learning Baseline

* Set up the environment for *Super Ghouls ’n Ghosts* (SNES) 
* Define a meaningful reward function (e.g. survival, progress to the right, checkpoints)
* Train a Reinforcement Learning agent that can reliably play the game
* Evaluate stability and robustness of the learned policy

### 2. Human ↔ AI Switch Mode

* Implement a **dual-control mode** where a human player and an AI agent can alternate control
* Enable the player to press a button that immediately hands control to the AI Ghost
* Ensure the agent can take over from *arbitrary game states*, not only from episode starts
* Allow smooth handover back to the human player at any time

---

## Why This Project

Classic games like *Super Ghouls ’n Ghosts* are notoriously difficult. Instead of reducing difficulty or relying on save states, this project explores a more modern approach:

> *Let an AI become your ghost.*

The long-term vision is an assistive system that respects the player’s agency while providing help exactly when it’s needed.

---

## Real-World Relevance 🌍

Although this project is framed around a retro video game, the underlying concepts translate directly to real-world applications:

* **Human-in-the-loop AI systems**: The switchable control mechanism mirrors assistive AI systems in industrial automation, robotics, and decision-support tools, where humans and AI dynamically share control.
* **Fallback and safety agents**: The AI Ghost acts as a safety or recovery policy, comparable to fallback controllers in autonomous driving, robotics, or medical devices.
* **Policy handover under uncertainty**: Learning to take over from arbitrary states is closely related to real-world problems where systems cannot rely on clean resets.
* **Imitation + Reinforcement Learning workflows**: Combining human demonstrations with reinforcement learning reflects modern training pipelines used in robotics and control.
* **User experience–driven AI design**: The project emphasizes seamless interaction between user and model, a key requirement for deployable AI products.

As such, this repository serves both as a playful experiment and as a compact showcase of techniques relevant to applied AI, reinforcement learning, and interactive systems.

---

## Disclaimer ⚠️

This is a research and hobby project created for educational and experimental purposes. All game assets and trademarks belong to their respective owners.

---

## Status 🚧

Work in progress.

---

## Meta 🤖✨

This README was written with the assistance of **ChatGPT (GPT‑5.2)**.
