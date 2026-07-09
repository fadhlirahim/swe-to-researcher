# Phase 2 — Transformers & LLMs from scratch (≈ 4–8 weeks)

**Goal:** build and train a GPT-style transformer from a blank file, understand every
component (tokenizer → embeddings → attention → MLP → logits), and run the full small-LLM
pipeline end to end at least once. After this phase, the architecture diagram from Phase 0
has no black boxes left.

**The gap this closes:** this is the core of modern model research. Most people use
transformers as an API; you'll understand them as a mechanism. This is the difference
between "I fine-tuned a model" and "I can reason about *why* it behaves as it does" — the
foundation for every research idea you'll later have.

## What to learn (in priority order)
1. **Self-attention** — queries/keys/values, why it's the key idea, multi-head attention,
   causal masking. Implement it from scratch; this is the centerpiece.
2. **The transformer block** — attention + MLP, residual connections, LayerNorm/RMSNorm, why each is there.
3. **Tokenization** — BPE, why subword, how the tokenizer shapes everything downstream (an underrated source of bugs and quality).
4. **Positional information** — learned vs RoPE; why attention needs it (your milestone question from the README).
5. **The training loop at language scale** — data loading, batching, the optimizer, learning-rate schedule, evaluation by loss/perplexity.
6. **The full pipeline** — pretrain → (optional) mid-train → SFT → eval, so you've seen the whole shape once before Phases 3–4 deepen each part.

## Primary path
- **Karpathy — "Let's build GPT" + nanoGPT.** Build a GPT from a blank file, then study `nanoGPT` as the clean reference implementation — deprecated since Nov 2025 in favor of **nanochat** (below), but still the shortest complete GPT you can hold in your head. Train it on tiny-shakespeare, then on a slightly bigger corpus. This is your attention-from-scratch deliverable.
- **Sebastian Raschka — *Build a Large Language Model (From Scratch)* (book + repo).** The most thorough, code-first walk through every component, including loading real pretrained weights (GPT-2 → Llama). Excellent companion to nanoGPT; use it to go deeper on the parts Karpathy moves quickly through. The repo also has GPT-2→Llama and Qwen-from-scratch conversions.
- **Karpathy — nanochat.** nanoGPT's official successor. Reproduce the *entire* modern stack end-to-end once: tokenizer → pretrain → mid-train → SFT → (optional RL) → eval → a chat UI. The resulting model is weak ("$100 ChatGPT" is marketing), but running the whole pipeline once is the point — it makes Phases 3–4 concrete.
- **Jay Alammar — [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/).** The clearest visual explainer of how attention moves information through the model. Read it alongside the code whenever the mechanism feels abstract.

## Foundational papers (read them, don't just cite them)
- [Attention Is All You Need](https://arxiv.org/abs/1706.03762). The Transformer. The one paper to actually read this phase.
- [GPT-1: Improving Language Understanding by Generative Pre-Training](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf). The generative-pretraining idea (OpenAI report, never put on arXiv).
- [BERT](https://arxiv.org/abs/1810.04805). Bidirectional pre-training, the other 2018 transformer milestone.

## The project / deliverable
**Train a small GPT from a blank file and write up one thing you investigated.** Beyond just
training it: pick one small question and answer it empirically — e.g. "how does final loss
change with model depth at fixed params?" or "what does the attention pattern look like on
a simple input?" Push the repo with a README + a short note. This is your first taste of
*research* (a question → an experiment → a finding), not just implementation.

## Milestone test (you've finished Phase 2 when you can…)
- [ ] Implement multi-head causal self-attention from a blank file and explain every line.
- [ ] Explain why self-attention needs positional information and how RoPE provides it.
- [ ] Describe what a tokenizer does and give one concrete way tokenization can hurt model quality.
- [ ] Train a GPT end-to-end, read its loss/perplexity, and reproduce nanochat's pipeline once.
- [ ] Read a transformer-architecture paper (e.g. an efficient-attention variant) and map every component onto code you've written.

## Time & calibration
4–8 weeks at ~10 hrs/week. Your engineering speed helps a lot here. **Don't rush past
attention** — rebuild it until it's boring. The nanochat end-to-end run can feel slow on one
GPU; rent an 8×H100 node for a few hours if you want to see the full pipeline at speed
(~$40–60), or just run the small/slow version locally.

## Traps
- **Treating attention as a formula to memorize.** Implement it, visualize the attention weights, perturb it. Understand it as a mechanism, not an equation.
- **Skipping the tokenizer.** It's boring and it's where subtle quality bugs live. Build a small BPE once.
- **Stopping at "it trains."** The deliverable is a *question answered*, not just a running loop. That mindset shift — from building to investigating — is what makes this Phase 2 and not Phase 0.

→ Next: **[phase-3-training-and-systems.md](phase-3-training-and-systems.md)**
