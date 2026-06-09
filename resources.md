# Resources — master list

The single source of truth for links, so the phase files don't repeat them. Curated, not
exhaustive — **a short list you'll actually use beats a long list you won't.** Each entry
notes which phase it serves. Verified current as of 2026-06.

> Principle: for any given phase, pick **one primary** resource and go deep. The others are
> references for when the primary leaves a gap. Collecting resources is procrastination;
> finishing one is progress.

---

## Hands-on courses & code (the spine — do these)

| Resource | Phase | What it is | Link |
|---|---|---|---|
| **Karpathy — Neural Networks: Zero to Hero** | 1–2 | The canonical from-scratch course: micrograd, makemore, build-GPT. Do the exercises. | karpathy.ai/zero-to-hero.html |
| **3Blue1Brown's Neural Networks series** | 1 | The best visual intuition for nets, gradients, and backprop. Watch when a concept won't click. | [youtube.com](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) |
| **nanoGPT** | 2 | Clean minimal GPT to study + train. | github.com/karpathy/nanoGPT |
| **nanochat** | 2 | The full modern stack end-to-end (tokenizer→pretrain→SFT→eval→UI). | github.com/karpathy/nanochat |
| **The Illustrated Transformer (Jay Alammar)** | 2 | Visual walk through attention; read alongside the code. | jalammar.github.io/illustrated-transformer |
| **Sebastian Raschka — Build an LLM (From Scratch)** | 2 | Thorough code-first book + repo (incl. GPT-2→Llama, Qwen-from-scratch). | github.com/rasbt/LLMs-from-scratch |
| **fast.ai — Practical Deep Learning** | 0–1 | Top-down, build-first DL course. Free. | course.fast.ai |
| **Dive into Deep Learning (d2l.ai)** | 1–3 | Free interactive textbook; use as reference. | d2l.ai |
| **Stanford CS336 — Language Modeling from Scratch (Spring 2026)** | 3–4 | The flagship systems course: tokenizer, FlashAttention2-in-Triton, distributed training, data, SFT+RL. Lectures free on YouTube; assignments on GitHub. | cs336.stanford.edu · github.com/stanford-cs336 |
| **Hugging Face TRL** | 4 | Practical SFT / DPO / GRPO toolkit. | huggingface.co/docs/trl |
| **ARENA** (Callum McDougall) | 5 | Alignment/research-engineering curriculum: DL fundamentals → transformers + mech interp (TransformerLens) → RL. | arena.education |
| **TransformerLens** | 5 (interp) | The mech-interp library (induction heads, IOI in GPT-2 small). | github.com/TransformerLensOrg/TransformerLens |
| **modded-nanogpt** | 3 | Speedrun repo; the commit history is an efficiency masterclass. | github.com/KellerJordan/modded-nanogpt |

## Books & long-form

| Resource | Phase | Note | Link |
|---|---|---|---|
| **The RLHF Book — Nathan Lambert** | 4 | Authoritative post-training/RLHF/RLVR guide. Free online. | rlhfbook.com |
| **Mathematics for Machine Learning — Deisenroth et al.** | 1 | Math *reference* (look up, don't read linearly). Free PDF. | mml-book.github.io |
| **Deep Learning — Goodfellow, Bengio, Courville** | 1–3 | The classic theory reference; dip in, don't read cover-to-cover. | deeplearningbook.org |
| **Andrew Ng — Machine Learning Specialization** | 1 | Gentle, rigorous ML fundamentals if you want more hand-holding. | (Coursera) |

## Canonical papers (read, don't just cite)

| Paper | Phase | Why |
|---|---|---|
| [Attention Is All You Need](https://arxiv.org/abs/1706.03762) | 2 | The transformer. |
| [GPT-1 — Improving Language Understanding by Generative Pre-Training](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf) | 2 | The generative-pretraining lineage (OpenAI report, not on arXiv). |
| [BERT](https://arxiv.org/abs/1810.04805) | 2 | Bidirectional pre-training; the other 2018 transformer milestone. |
| Chinchilla — Training Compute-Optimal LLMs | 3 | Scaling laws; "small but well-trained." |
| FlashAttention | 3 | Memory-efficient attention; the systems mindset. |
| GPTQ / AWQ | 3 | Post-training quantization. |
| Distilling the Knowledge in a Neural Network (Hinton) + Sequence-Level KD (Kim & Rush) | 3 | Distillation foundations. |
| TinyStories → Phi-1.5 → Phi-3 → SmolLM | 3 | The data-quality thread; small-model recipes. |
| InstructGPT / RLHF + DPO + a GRPO/RLVR paper | 4 | The post-training lineage. |
| [DeepSeek-R1](https://arxiv.org/abs/2501.12948) | 4 / RL-3 | RL for reasoning (RLVR); the GRPO breakthrough. |
| Anthropic — Transformer Circuits / induction heads | 5 (interp) | Mech-interp foundations. |

(Find exact links via Semantic Scholar/arXiv — or use the `../research-buddy` `litsearch.py` tool.)

## People / newsletters (signal, low noise)

- **Sebastian Raschka — *Ahead of AI*** (highest signal; annual paper reading lists) — magazine.sebastianraschka.com
- **Lilian Weng** (deep technical explainers) — lilianweng.github.io
- **Nathan Lambert — *Interconnects*** (post-training / RLHF pragmatics)
- **Neel Nanda** (mech interp; "Concrete Steps to Get Started") — neelnanda.io
- **MIT Han Lab** (the academic home of efficiency: AWQ/SmoothQuant/TinyChat)

> Raschka + Han Lab + the Hugging Face science blog cover ~80% of what matters week-to-week.

## Communities, compute, venues

- **EleutherAI** — Discord #research + the **SOAR** mentored program (self-taught researchers welcome; possible publication credit). The highest-ROI single move. eleuther.ai
- **Hugging Face** — models/datasets/Spaces; Daily Papers for visibility. huggingface.co
- **Compute** — free Colab/Kaggle to start; Vast/RunPod community tiers for cheap rentals; granted compute via TPU Research Cloud / EleutherAI / academic credits (competitive, time-bounded).
- **Venues for independents** — ICLR **Blog Posts** track; NeurIPS **ENLSP** workshop; **ML Reproducibility Challenge** (now a NeurIPS track). Not the main-track lottery.

## Your own project assets

- `../advisory/small-models-research-onramp.md` — the specialization + how-to-publish playbook (Phase 5).
- `../advisory/research-buddy-prd.md` — design rationale for the buddy.
- `../research-buddy/` — the skill that scopes/critiques project ideas (Phase 5+).

---

### How to choose (so you don't drown)
- **Phase 1–2:** Karpathy Zero-to-Hero is your primary. Raschka's book is the deeper companion. fast.ai/d2l only to patch gaps.
- **Phase 3:** CS336 is your primary — *do the assignments*. modded-nanogpt + the canonical papers around it.
- **Phase 4:** The RLHF Book + TRL.
- **Phase 5:** the on-ramp + (if interpretability) ARENA.
- **RL branch (separate track):** see [`rl-track.md`](rl-track.md) — Hugging Face Deep RL course → Sutton & Barto + David Silver → Spinning Up + CleanRL + Gymnasium → RLHF Book / GRPO / RLVR. Its own self-contained resource table is in that file. Also worth following: the [RL Field Manual](https://rl.paraz.in/#frontier), an interactive guide to LLM reinforcement learning (good for the RL-3 frontier).

One primary per phase. Everything else is a reference, not a queue.
