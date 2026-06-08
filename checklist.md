# Checklist — track yourself by artifacts, not hours

Check a box only when you can do it **from a blank file / for real**, not "I watched it."
Progress here = shipped artifacts + capabilities, never "time spent." If a box is unchecked
after weeks, that's the signal of where you actually are — useful, not shameful.

> Rule: every phase must end with a **public artifact** (repo + writeup). No artifact → phase
> not done, regardless of what you've watched.

---

## Phase 0 — Orientation
- [ ] Environment works (`torch` sees your GPU/MPS, or Colab set up)
- [ ] Trained *something* end-to-end; loss curve screenshotted in a repo
- [ ] `LOG.md` started (first dated entry written)
- [ ] First paper skimmed figures-first + 3-sentence note (try TinyStories)
- [ ] EleutherAI joined
- **Artifact:** a public repo with a loss curve and a log. ✅ →

## Phase 1 — Foundations → **Level 1 (Reproducer) begins**
- [ ] Reverse-mode autodiff implemented from a blank file (your own micrograd)
- [ ] Hand-derived one gradient to check it
- [ ] MLP built, trained, and *debugged* without copying (diagnosed a bad LR from the curve)
- [ ] Can explain in your log: cross-entropy, train/val split, overfitting + 3 fixes
- [ ] makemore reimplemented (bigram → MLP char-LM)
- **Artifact:** micrograd + makemore repos + a "what backprop computes" note. ✅ →

## Phase 2 — Transformers & LLMs
- [ ] Multi-head causal self-attention from a blank file, every line explained
- [ ] Can explain why attention needs positional info + how RoPE provides it
- [ ] Built a small BPE tokenizer; can name one way tokenization hurts quality
- [ ] Trained a GPT end-to-end; read its loss/perplexity
- [ ] Reproduced nanochat's full pipeline once
- [ ] Answered one empirical question about your model (a finding, not just a run)
- **Artifact:** a from-scratch GPT repo + a short investigation writeup. ✅ → **Level 1 reached.**

## Phase 3 — Training & systems → **Level 2 (Extender) begins**
- [ ] Can explain Chinchilla, MFU; can estimate train cost on your hardware
- [ ] Can read a profiler trace and locate the bottleneck (compute/memory/IO)
- [ ] Can implement or clearly explain FlashAttention's idea
- [ ] Did the CS336 assignments (not just the lectures)
- [ ] **Reproduced a published result on one GPU**
- [ ] **Ran ONE clean ablation** (≥3 seeds, same-size baseline, one variable)
- [ ] Designed the ablation through the research-buddy + checked the pitfalls list first
- **Artifact:** reproduction + ablation repo with eval harness, baselines, plot, writeup. ✅ → **Your L2 credential.**

## Phase 4 — Post-training & eval
- [ ] Can explain SFT vs DPO vs GRPO — what each optimizes, when to use which
- [ ] Can describe reward hacking with a concrete example
- [ ] Can name ≥3 ways an eval lies
- [ ] Post-trained a small model (SFT+LoRA, then DPO or a small GRPO) with TRL
- [ ] Built an *honest* eval harness with a same-size baseline + a stated metric limitation
- [ ] Critiqued a "small reasoning model" paper's evaluation specifically
- **Artifact:** a post-trained model + honest-eval repo + writeup. ✅ → **Level 2 reached.**

## Phase 5 — Specialization & research → **Levels 3–4**
- [ ] Chose ONE niche and read its on-ramp section + key papers in full
- [ ] Reproduced something in the niche as a launchpad
- [ ] Found an open thread (the unrun ablation / unswept variable) yourself
- [ ] Scoped it with the research-buddy (prior-art + feasibility + confound)
- [ ] Ran it cleanly and **shipped an original result publicly** (weights/code + eval + writeup)
- [ ] Someone you don't know used / cited / built on it
- [ ] Active in a community (asking, answering, collaborating); pursued SOAR or similar
- [ ] You're choosing your own questions, not waiting to be assigned one
- **Artifact:** a public original result. ✅ → **Level 3 reached.** (Level 4 = recognized, self-directed work over years.)

---

## The four weekly habits (tick every week, every phase)
- [ ] Built/reproduced one slice of the current project
- [ ] Read 2–3 papers, figures-first, each with a one-paragraph note
- [ ] Wrote one log entry / note / explainer
- [ ] Engaged once in a community (posted, asked, answered, reviewed)

> If you keep only the weekly habits and lose everything else, you'll still get there. They're
> the engine; the phases are just the route.
