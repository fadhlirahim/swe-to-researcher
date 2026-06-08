# Roadmap to Mastery — ML / LLM / model research

A step-by-step path from "strong software engineer with a massive gap in ML research" to
"independent researcher who produces original, recognized work." Written for **you**: you
can already code, build systems, debug, and ship. That's a real head start — most of this
roadmap targets the gaps that engineering experience *doesn't* close (math intuition,
deep-learning internals, and the craft of research itself).

> **Read this README fully before opening any phase file.** The philosophy below is more
> important than the curriculum. Most people fail this not for lack of resources — there
> are too many — but because they learn in the wrong *shape*.

---

## The honest premise

- **Mastery is years, not months.** Anyone selling you "become an AI researcher in 8 weeks" is selling something. Be suspicious of this roadmap too — it's a map, not a contract.
- **But useful competence is months.** You can reach "can build a GPT from scratch and read most papers" in ~3–6 months of focused part-time work, and "can run a clean extension of a published result" in ~6–12. That's enough to start contributing.
- **"Researcher" is not binary.** It's a ladder (see Levels below). You climb it by shipping artifacts, not by finishing courses.
- **The bottleneck is reps and taste, not information.** Everything you need is free. What's scarce is the discipline to build, reproduce, and write — repeatedly, in public.

---

## Core philosophy (the 5 principles)

1. **Build first, theory just-in-time.** Do NOT spend 6 months on linear algebra before touching a model. Build a working thing, hit a wall, learn exactly the theory that wall requires, continue. This is the fast.ai / Karpathy ethos and it's how working researchers actually learn. The math matters — you pull it in *when a model forces you to*, not preemptively.
2. **Spiral, don't sequence.** The phases are a *competence map*, not a strict order. You'll build a tiny transformer in Phase 2 before you "finish" Phase 1's math — that's correct. You revisit each layer at increasing depth. A vertical slice early beats a perfect horizontal foundation.
3. **Artifacts over courses.** A finished course is worth nothing; a reproduced result with a writeup is worth a lot. Every phase ends in a *shippable artifact* (repo + notes). If you "completed" a phase but have nothing to show, you didn't complete it.
4. **Reproduce before you innovate.** You earn the right to have ideas by first reproducing other people's. Reproduction is where 80% of the real learning lives and where taste is built. Novel ideas come *out of* reproduction, not before it.
5. **Learn in public.** A private learner is an invisible learner with no feedback loop. Push code to GitHub, write short notes, post them, join a community (EleutherAI). This is not vanity — it's the feedback mechanism that makes you improve and the network that gets you collaborators and compute.

---

## The levels (what "researcher" actually means)

Define your target concretely. Each level is a *capability*, reached by a deliverable — not a credential.

| Level | You can… | Rough time* | Reached by |
|---|---|---|---|
| **L0 — Tourist** | run notebooks, call APIs, not explain internals | — | (where most people stop) |
| **L1 — Reproducer** | build + train a small model from a blank file; read most papers; reproduce a simple published result | 3–6 mo | Phases 1–2 |
| **L2 — Extender** | take a paper and run a clean, controlled ablation/extension; know the pretrain→post-train→eval stack; ship a reproducible artifact | 6–12 mo | Phases 3–4 |
| **L3 — Contributor** | produce a small *original* result others use/cite; engaged in a community; a workshop paper or a serious blog-post result | 1–2 yr | Phase 5 |
| **L4 — Independent researcher** | set your own research direction; produce recognized original work | 2–4+ yr | beyond this map |

\* at ~10–15 focused hrs/week. Faster if you go full-time; slower is fine. The levels are the point, not the clock.

**Your near-term target is L2.** Everything here is sequenced to get you to "I can take a published small-models result and run a clean extension of it" — which is exactly what the `../advisory/small-models-research-onramp.md` plan and the `../research-buddy` tool are built to exploit.

---

## The phase map

| Phase | Competence gained | Primary resource | Deliverable | ~Time |
|---|---|---|---|---|
| **[0 — Orientation](phase-0-orientation.md)** | environment, mental model, first vertical slice | — | a trained tiny model, day 1 | 1 wk |
| **[1 — Foundations](phase-1-foundations.md)** | neural nets + backprop + ML from scratch; math-as-needed | Karpathy Zero-to-Hero | micrograd + makemore, reimplemented | 4–8 wk |
| **[2 — Transformers & LLMs](phase-2-transformers-llms.md)** | attention, build+train a GPT, the full small-LLM stack | nanoGPT + Raschka's book + nanochat | a GPT trained from a blank file | 4–8 wk |
| **[3 — Training & systems](phase-3-training-and-systems.md)** | scaling laws, efficiency, kernels, data, reproduce a result | Stanford CS336 (Spring 2026) | one clean reproduction + ablation | 8–12 wk |
| **[4 — Post-training & eval](phase-4-posttraining-and-eval.md)** | SFT, RLHF/DPO/GRPO, evaluation as a discipline | The RLHF Book + TRL | a post-trained small model + honest eval | 4–8 wk |
| **[5 — Specialization & research](phase-5-specialization-and-research.md)** | a niche + your first original result + community + publishing | the on-ramp + ARENA (if interp) | a shipped original artifact | ongoing |

Woven through **all** phases: **[research-method.md](research-method.md)** — the craft of being a
researcher (reading papers, experiment design, the research log, writing). Start it in week 1,
not at the end.

Single source of truth for every link: **[resources.md](resources.md)**.
Track yourself against **[checklist.md](checklist.md)**.

---

## "You are here" — find your entry point

Don't assume you're at zero. Run this self-diagnostic; start at the first one you *can't* confidently do (by *implementing*, not "I've seen it"):

1. Derive backprop for a 2-layer MLP by hand and implement it from a blank file (no autograd). → can't? **Phase 1.**
2. Implement multi-head self-attention from scratch and explain why it's permutation-equivariant without positional encodings. → can't? **Phase 2.**
3. Explain the Chinchilla scaling law, what MFU is, and roughly what it costs to train a 1B model on one GPU. → can't? **Phase 3.**
4. Explain the difference between SFT, DPO, and GRPO, and name two ways an eval can lie to you. → can't? **Phase 4.**
5. Take a recent small-models paper, identify its baseline + the one confound that would invalidate it, and design a controlled extension. → can't? **Phase 5 / the research-buddy.**

Most strong engineers with "a massive gap" land at **Phase 1**, move through it fast (you already code), and slow down at Phases 3–4 where the field-specific depth lives.

---

## The weekly cadence (the habit engine)

The compounding habit matters more than any single course. Aim for a sustainable weekly loop:

- **Build / reproduce** one slice of the current phase's project (the core — most of your hours).
- **Read 2–3 papers**, figures-first, each with a one-paragraph note (see research-method.md).
- **Write one note** — a log entry, a "what I learned / got stuck on," or a short explainer.
- **Engage once** — post a result, ask/answer in a community, read someone else's work.

Four habits, every week. Miss the courses, keep the loop.

---

## Anti-patterns (how strong engineers waste months here)

- **Math-first paralysis** — "I'll learn all the linear algebra/probability first." You won't, and you don't need to. Pull math in when a model demands it.
- **Tutorial hell / course collecting** — finishing lectures feels like progress and isn't. If you can't implement it from a blank file, you don't know it. Watched ≠ can-build.
- **Skipping reproduction** — chasing "novel" before you can reproduce. You'll generate confident nonsense (you've seen me do it). Reproduce first.
- **Learning in private** — no public repo, no notes, no community. Invisible, and no feedback loop. Fix this in week 1.
- **Perfecting the plan** — re-reading roadmaps, re-sequencing, optimizing your setup. This doc included: read it once, start Phase 0 today, deviate freely.
- **Over-respecting the phases** — they're a spiral, not a gate. Build the tiny transformer before you "finish" the math.

---

## How this connects to your other work

- This roadmap is the **learning superset** — it builds the competence.
- `../advisory/small-models-research-onramp.md` is the **applied specialization** (Phase 5) plus how-to-get-visible-and-publish. It's the capstone this roadmap delivers you into.
- `../research-buddy/` is the **tool** you use once you're at Phase 5 — generating and pressure-testing project ideas. Useless before then (you can't critique ideas you can't yet have); essential after.

Sequence: **learn (this roadmap) → specialize (on-ramp) → ideate + scope (research-buddy) → ship.**

---

## Start now

Open **[phase-0-orientation.md](phase-0-orientation.md)** and do the week-1 vertical slice today.
Not tomorrow, after more reading. Today. The roadmap works only if the first artifact exists by the end of this week.
