# The RL branch — Reinforcement Learning

A sibling branch to the LLM/small-models track, growing from the **same trunk** (Phase 0–1 +
[`research-method.md`](research-method.md)). If you've done the trunk, you have what RL needs to
*start*; this track adds the RL-specific theory and practice the LLM phases don't teach.

> **Read [`README.md`](README.md) first.** The philosophy is identical — build-first, spiral,
> artifacts over courses, reproduce-before-innovate, learn in public, the L0–L4 levels. This
> file only covers what's *different* for RL. (It's one dense file rather than per-phase files
> because RL is your secondary option, not your primary — say the word and I'll expand it to
> match the LLM track's depth.)

---

## Where RL sits (so you don't repeat the confusion)

ML has three classical paradigms — **supervised**, **self-supervised/unsupervised** (LLM
pretraining is this), and **reinforcement learning** (learn from reward via interaction). RL is
*one branch*, not the root. The root is the trunk: backprop, optimization, neural nets.

**The twist that matters in 2026:** the RL and LLM branches **merge at the frontier.** Modern LLM
post-training — RLHF, and especially **GRPO / RLVR** for reasoning — *is* reinforcement learning
applied to language models. So this track's RL-3 is the same destination as the LLM track's
Phase 4, approached from the RL side.

RL splits into two lanes, and the choice matters for a solo researcher:
- **Classic deep RL** — games, robotics, control. The older lineage. **Harder and less forgiving solo:** sample-inefficient (millions of env steps), compute- and wall-clock-hungry, brittle, with a real reproducibility problem (the field has a famous paper, *"Deep Reinforcement Learning That Matters,"* about exactly this). Pick it for *love of the problem*, not tractability.
- **RL-for-LLMs / RLVR** — reasoning models. The hottest area, most jobs, **and the most tractable for a solo person on one GPU** — it reuses your entire LLM-track skillset. This is the lane I'd steer you toward unless robots/games are the dream.

---

## The honest build-first warning

Even RL veterans call Sutton & Barto a *slog* (500+ pages, tabular-first). **Do not read it
cover-to-cover before touching code.** Ship a working agent early (HF Deep RL course / CleanRL),
hit a wall, then pull the theory in. Same spiral as the trunk. RL punishes the "learn everything
first" instinct harder than any other branch, because the theory only clicks once you've watched
an agent fail to learn.

---

## The phases

Same template as the LLM track: goal → what to learn → primary path → the artifact → milestone → traps.

### RL-0 — Orientation (≈ days)
**Goal:** train one working RL agent end-to-end before you understand it, and pick your lane.
- Do **Hugging Face Deep RL Course, Unit 1** — train an agent on a Gymnasium env with Stable-Baselines3 in an afternoon. Watch a reward curve go up.
- Decide your lane (classic deep RL vs RL-for-LLMs) — write it in your `LOG.md`. For tractability solo, default to the RLVR lane.
- **Milestone:** a trained agent + a reward curve in your repo.
- **Trap:** starting with Sutton & Barto chapter 1. Don't. Train something first.

### RL-1 — RL foundations (≈ 4–6 wk)
**Goal:** understand and implement the core RL machinery from a blank file. This is the "micrograd of RL."
- **Learn:** MDPs (states, actions, rewards, transitions), return + discounting, **value functions** (V, Q), the **Bellman equations**, dynamic programming (policy/value iteration), exploration vs exploitation, and **tabular methods** — Q-learning, SARSA, TD learning.
- **Primary path:** Sutton & Barto **Part I** (tabular) — read *alongside* coding, not before. Supplement with **David Silver's RL lectures** (the canonical course). Theory rigor (optional): Szepesvári's *Algorithms for RL*.
- **The artifact:** implement **tabular Q-learning and SARSA from a blank file** on a gridworld / FrozenLake / Taxi — no library doing the learning for you. Plot the value function; show the policy converging.
- **Milestone:** explain Bellman, value-vs-policy, on- vs off-policy in your own words; implement tabular Q-learning from scratch and debug a non-converging agent.
- **Trap:** jumping to deep RL before tabular intuition. The deep stuff is just function approximation bolted onto these ideas — skip them and nothing later makes sense.

### RL-2 — Deep RL (≈ 8–12 wk) → your L2 credential
**Goal:** the modern algorithms, and a clean reproduction + ablation (the RL equivalent of the LLM track's Phase 3 credential).
- **Learn:** function approximation, **DQN** (value-based, replay buffers, target nets), **policy gradients** (REINFORCE), **actor-critic** (A2C), and **PPO** — the workhorse you must know cold. Then, for continuous control, SAC / DDPG / TD3. Key concepts: GAE, advantage normalization, the bias-variance levers.
- **Primary path:** **OpenAI Spinning Up** (the best practical deep-RL intro) + **CleanRL** (single-file, research-grade implementations — the "nanoGPT of RL"; read and reproduce them) + **Gymnasium** (Farama, the standard env interface) + **Stable-Baselines3** for trusted baselines.
- **The artifact:** **reproduce PPO on classic control with CleanRL** (CartPole → LunarLander), then run **ONE clean ablation** (e.g. GAE on/off, advantage normalization, clip range) with **≥3 seeds** and reported variance. Ship repo + reward curves + writeup. Run the design through the `../research-buddy` first.
- **Milestone:** implement/explain PPO; read a profiler/training trace and explain why an RL run isn't learning; reproduce a result and ablate it cleanly.
- **Traps:** **reproducibility hell** — RL variance is brutal; one seed is a lie, seed everything and report spread. **Compute/wall-clock** — env steps dominate; budget time, not just GPU-$. **Cross-env comparisons** — a win on CartPole says nothing about Atari.

### RL-3 — The LLM intersection: RLHF / GRPO / RLVR (≈ 4–8 wk)
**Goal:** the cheap-compute, high-energy lane — and the point where this branch rejoins the LLM track (this *is* Phase 4).
- **Learn:** reward modeling (+ reward hacking), **PPO-for-LLMs (RLHF)**, **DPO** (no reward model), **GRPO** (DeepSeek — critic-free, group-normalized advantages over 8–64 sampled traces), and **RLVR** (verifiable rewards: math/code where correctness is auto-checkable). The o1 / DeepSeek-R1 / Qwen lineage.
- **Primary path:** **The RLHF Book** ([rlhfbook.com](https://rlhfbook.com), free) + **HF TRL** (SFT/DPO/GRPO toolkit) + CS336's RL assignment + the open frameworks (Open-Reasoner-Zero, DAPO) and the "Post-Training in 2026" landscape.
- **The artifact:** a small **GRPO/RLVR run on a 0.5–1.5B model** with a *programmatic/verifiable* reward (a math or formatting task) + an honest eval with a same-size baseline.
- **Milestone:** explain RLHF vs DPO vs GRPO and what each optimizes; run a small RLVR loop; critique an RL-for-reasoning paper's evaluation.
- **Traps:** GRPO is finicky (KL control, reward hacking, vLLM colocation, wall-clock ≫ GPU-hours) — SFT+DPO is the safer first step. And keep an honest eye on the **RLVR debate**: some 2026 work argues it makes models *faster/sharper at what they already can do*, not fundamentally smarter — don't overclaim your gains.

### RL-4 — Specialization & research (ongoing)
**Goal:** pick a lane and ship an original result. Same `research-method.md`, same L3 bar (a public, reproducible original result others use).
Lanes (depth over breadth — pick one):
- **RL-for-reasoning / RLVR** — most tractable solo; reuses your LLM skills.
- **Small-scale classic deep RL** — control/games on modest envs.
- **Model-based RL**, **offline RL**, **exploration**, or **multi-agent RL (MARL)** — note: *this* is the real "multi-agent RL" (agents learning policies in a shared environment), not the LLM-orchestration "multi-agent" you asked about earlier. Different thing entirely.
- **Reproduction-as-contribution** — given RL's reproducibility crisis, a careful, seeded reproduction of a published RL result is a genuinely valued contribution (ICLR Blog Posts track, MLRC).

---

## Resources (verified current, 2026)

| Resource | Phase | What |
|---|---|---|
| [Hugging Face Deep RL Course](https://huggingface.co/learn/deep-rl-course/) | RL-0 | Hands-on on-ramp (SB3 + Gymnasium). Start here. |
| **Sutton & Barto — Reinforcement Learning: An Introduction** (2nd ed, free PDF) | RL-1 | The bible. Part I (tabular) first; read alongside code. |
| **David Silver — RL Course** (DeepMind/UCL lectures) | RL-1 | The canonical lecture series. |
| Szepesvári — *Algorithms for RL* | RL-1 | Optional theory rigor. |
| [OpenAI Spinning Up](https://spinningup.openai.com) | RL-2 | Best practical deep-RL intro. |
| [CleanRL](https://github.com/vwxyzjn/cleanrl) | RL-2 | Single-file deep-RL implementations (PPO/DQN/SAC/…). Reproduce these. |
| [Gymnasium (Farama)](https://gymnasium.farama.org) | RL-0–2 | Standard env interface (successor to OpenAI Gym). |
| Stable-Baselines3 | RL-0–2 | Trusted PyTorch baselines. |
| [The RLHF Book](https://rlhfbook.com) + HF TRL | RL-3 | The RL/LLM intersection (RLHF/DPO/GRPO/RLVR). |
| Open-Reasoner-Zero · DAPO · "Post-Training 2026" survey | RL-3–4 | Open RLVR frameworks + current landscape. |

---

## The honest bottom line

If your goal is **tractable, impactful research as a solo person on one GPU**, the RL lane to take
is **RL-3 (RLVR/reasoning)** — it's the frontier, it's cheap-ish compute, and it reuses everything
in your LLM track. *Classic* deep RL (RL-1→RL-2 toward robots/games) is a real and worthy path, but
it's the **less forgiving** one — choose it because you can't stop thinking about the control
problem, not because it looks like the shortcut. Either way: same trunk, same method, same "ship the
artifact" discipline. The branch is different; the work is the same.
