# Phase 4 — Post-training & evaluation (≈ 4–8 weeks)

**Goal:** understand how a raw pretrained model becomes useful — supervised fine-tuning
(SFT), preference/RL methods (RLHF, DPO, GRPO), reward modeling, and **evaluation as a
rigorous discipline** (the part nearly everyone does badly). Post-train a small model
yourself and measure it honestly.

**The gap this closes:** pretraining gets a lot of attention, but most *applied* model
research today is post-training and evaluation. This is also where the small-models field is
hottest (small reasoning models, distilled reasoning, RLVR). And evaluation is the single
most under-respected skill in the field — getting it right is a genuine differentiator and a
recurring source of "results" that turn out to be measurement artifacts.

## What to learn (in priority order)
1. **SFT / instruction tuning** — turning a base model into one that follows instructions; data formats; LoRA/QLoRA for doing it cheaply on one GPU.
2. **Preference & RL methods** — RLHF (the canonical recipe), **DPO** (simpler, no separate reward model), **GRPO / RLVR** (reinforcement learning from *verifiable* rewards — the current frontier for reasoning). Understand what each optimizes and when to use which.
3. **Reward modeling** — what a reward model is, reward hacking, why a verifier with skin in the game can't be a fair verifier.
4. **Evaluation as a discipline** — benchmarks and how they lie: contamination, prompt sensitivity, the gap between a metric and the behavior you care about, why comparative/pairwise judgment beats absolute scoring. **This is the most important sub-topic in the phase.**
5. **Inference-time methods** — sampling, speculative decoding, why decoding choices change measured quality.

## Primary path
- **Nathan Lambert — *The RLHF Book*** (free online at **rlhfbook.com**; also Manning print). The authoritative, current guide to post-training: the canonical RLHF recipe, DPO, the RLVR renaissance, reward modeling, evaluation, and industry post-training tricks. Your spine for this phase.
- **Hugging Face TRL** (library + docs/cookbook) — the practical toolkit for SFT, DPO, and GRPO. Use it to actually post-train a small model.
- **CS336's post-training assignment** (from Phase 3) — SFT + RL for math reasoning + optional DPO, implemented rather than imported. If you did it in Phase 3, deepen it here.
- **Evaluation reading** — find recent work on benchmark contamination and eval pitfalls; treat "how was this measured?" as the first question of every paper you read.
- **Key paper:** [DeepSeek-R1](https://arxiv.org/abs/2501.12948). The RL-for-reasoning (RLVR/GRPO) result that defined the current frontier. Use it as your "small reasoning model" paper for the milestone below.

## The project / deliverable
**Post-train a small model (0.5–1.5B) and evaluate it honestly.** Concretely: take a small
base model, run SFT (LoRA) on a focused dataset, then either DPO or a small GRPO loop with a
*programmatic/verifiable* reward (e.g. a math or formatting task). The research content is in
the **evaluation**: build a clean eval harness, include a same-size baseline, look for the
ways your reward could be gamed, and report what the metric does *not* capture. Ship repo +
eval harness + writeup.

> Honesty note: online GRPO is finicky (KL control, reward hacking, vLLM colocation, wall-clock ≫ GPU-hours). For a first post-training project, SFT + DPO is the safer path; treat GRPO as a stretch. See the RL pitfalls in `../research-buddy/.claude/skills/research-buddy/reference/pitfalls.md`.

## Milestone test (you've finished Phase 4 when you can…)
- [ ] Explain SFT vs DPO vs GRPO — what each optimizes and when you'd reach for it.
- [ ] Describe reward hacking and give a concrete example of a reward your model could game.
- [ ] Name at least three distinct ways an eval can lie (contamination, prompt sensitivity, metric≠behavior, absolute-vs-comparative scoring…).
- [ ] Post-train a small model with TRL and produce an *honest* evaluation, including a same-size baseline and a stated limitation of the metric.
- [ ] Read a "small reasoning model" paper and critique its evaluation specifically.

## Time & calibration
4–8 weeks at ~10 hrs/week. The post-training mechanics are quick to *run* (TRL does the heavy
lifting); the time goes into understanding *why* they work and into doing evaluation
properly. **Spend disproportionate effort on the evaluation half** — it compounds into every
later project and is where you'll out-perform most practitioners.

## Traps
- **Trusting your own numbers.** The default failure mode. Assume your eval is lying until you've checked for contamination, prompt sensitivity, and a missing baseline.
- **Reaching for GRPO first.** It's the exciting frontier and a debugging swamp. Earn it with SFT+DPO first.
- **Self-evaluation.** Don't let the model (or the same prompt) grade its own work — the self-preference bias is real. Separate the worker from the judge (the same lesson as the research-buddy's independent skeptic).
- **Metric tunnel-vision.** A number going up is not a behavior improving. Always ask what the metric fails to capture.

→ Next: **[phase-5-specialization-and-research.md](phase-5-specialization-and-research.md)**
