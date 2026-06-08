# Phase 3 — Training & systems (≈ 8–12 weeks)

**Goal:** understand how real models are trained *efficiently* — scaling laws, data,
optimization at scale, GPU systems (kernels, mixed precision, parallelism) — and the
efficiency techniques (quantization, distillation, sparsity) that define small-models work.
Then **reproduce a published result and run one clean ablation.** This is the phase that
takes you from L1 (reproducer) toward L2 (extender), and it's where most of your real
research competence is forged.

**The gap this closes:** Phase 2 taught you what a transformer *is*; this teaches you how
the field actually *builds* them under real constraints — the knowledge that separates
someone who can train a toy from someone who can contribute. It's also where your single-GPU
budget becomes a design constraint you learn to engineer around rather than fight.

## What to learn (in priority order)
1. **Scaling laws** — Chinchilla (compute-optimal ~20 tokens/param), what they predict and where they break. The conceptual basis for "small but well-trained."
2. **Efficiency / GPU systems** — mixed precision (bf16), MFU (model-FLOPs-utilization), memory vs compute, FlashAttention, and at least a reading-level grasp of kernels (Triton) and parallelism (data/tensor/pipeline). You don't need to be a kernel author; you need to know where the time and memory go.
3. **Data** — the biggest lever in practice. Curation, filtering, deduplication; why data quality often beats architecture (TinyStories → Phi → SmolLM lineage).
4. **Optimization at scale** — learning-rate schedules, warmup, the modern optimizer landscape (AdamW, Muon), gradient accumulation, batch-size effects.
5. **The small-models efficiency toolkit** (your niche's core): **quantization** (GPTQ/AWQ/GGUF), **knowledge distillation**, **pruning/sparsity**, efficient architectures. Read enough to run experiments in each.

## Primary path
- **Stanford CS336 — Language Modeling from Scratch (Spring 2026).** The flagship for this phase. Lectures are free on YouTube; assignments are public on GitHub. It deliberately mirrors an OS-from-scratch course: you implement the tokenizer, architecture, and optimizer; profile and optimize attention with a **Triton FlashAttention2**; build distributed training; turn raw Common Crawl into pretraining data (filter + dedup); and do SFT + RL for math reasoning (+ optional DPO). **Do the assignments**, not just the lectures — that's where the systems knowledge sticks.
- **modded-nanogpt** (the speedrun repo + its commit history) — a masterclass in concrete, citable efficiency wins (Muon, value embeddings, QK-norm, sliding-window attention). Read the commit log like a textbook.
- **Foundational papers** (read, don't just cite): Chinchilla scaling laws; the FlashAttention paper; GPTQ + AWQ for quantization; the original distillation paper (Hinton) + sequence-level KD (Kim & Rush). See `resources.md`.

## The project / deliverable (the important one)
**Reproduce a result on one GPU, then run ONE clean ablation.** Concretely, the highest-value
options (all in the on-ramp's project list):
- Reproduce a **single-GPU modded-nanogpt** run, then isolate one trick (e.g. Muon vs AdamW, or with/without value embeddings) with proper seeds, reporting wall-clock + val-loss deltas; **or**
- A **quantization quality ablation** at matched effective bits-per-weight across GPTQ/AWQ/GGUF, with both perplexity *and* a downstream suite; **or**
- A **distillation logit-sparsity study** (how few teacher logits suffice).

Ship: repo + a reproducible eval harness + honest same-size baselines + a clear writeup with a
plot. **This artifact is your L2 credential** — it's the thing that proves you can take real
work and extend it cleanly. Run it through the `../research-buddy` to pressure-test the design first.

## Milestone test (you've finished Phase 3 when you can…)
- [ ] Explain Chinchilla, MFU, and estimate the GPU-hours/cost to train a given model on your hardware (sanity-check against `../research-buddy/.claude/skills/research-buddy/tools/cost_model.py`).
- [ ] Read a profiler trace and say where a training run is bottlenecked (compute vs memory vs IO).
- [ ] Implement or clearly explain FlashAttention's idea and why it saves memory.
- [ ] Reproduce a published result on one GPU and run a controlled ablation with seeds + a same-size baseline.
- [ ] Read a small-models systems paper and identify its key efficiency claim and how it was measured.

## Time & calibration
8–12 weeks at ~10–15 hrs/week — **this is the longest, deepest phase, and the one where your
"massive gap" most closes.** Don't rush it. The reproduction + ablation project alone can take
3–4 weeks and is worth every hour. CS336's assignments are demanding; budget accordingly.

## Traps
- **Lectures without assignments.** CS336's value is in the implementation work. Watching the lectures and skipping the psets gives you the *illusion* of systems knowledge.
- **Chasing the speedrun record.** The 8×H100 leaderboard is a saturated, multi-year competition. Reproduce on one GPU and isolate one trick — don't try to beat the record.
- **Confounded ablations.** This is the #1 way to produce a worthless result: vary two things at once, mismatch the baseline, or run one seed. Read `../research-buddy/.claude/skills/research-buddy/reference/pitfalls.md` *before* you design the experiment.
- **Skipping data.** Data quality is the highest-leverage variable in the field and the least glamorous. Don't under-weight it.

→ Next: **[phase-4-posttraining-and-eval.md](phase-4-posttraining-and-eval.md)**
