# Phase 0 — Orientation (≈ 1 week)

**Goal:** kill the "I don't know where to start" paralysis by shipping a trained model in
your first few days, set up a research environment you'll actually keep, and start the two
habits (a log and reading) that run through every later phase.

You're a strong engineer. The trap at the start isn't capability — it's spending three
weeks "preparing to learn." Don't. The point of this week is *momentum and a working loop*,
not understanding. Understanding comes in Phase 1.

## What "done" looks like
- You trained *something* end-to-end and saw a loss go down — even if you don't fully understand it yet.
- You have a GitHub repo, a research log, and a paper-notes habit started.
- You've joined one community and lurked.

## Do this, in order

1. **Environment (half a day).** Python + PyTorch. A single consumer GPU, or free Colab/Kaggle to start (don't spend money yet). Get `uv` or conda, a notebook + a real editor, and `git`. Confirm `torch.cuda.is_available()` (or MPS on your Mac). Don't over-build the setup — you'll redo it later.
2. **First vertical slice (1–2 days).** Run the **fast.ai Lesson 1** notebook, or train **nanoGPT** on the tiny-shakespeare dataset following the README (nanoGPT is deprecated but frozen — ideal for a first run: it will never change under you). Goal: watch a real training loop run and a loss curve drop. You will not understand most of it. That's fine — you're proving the machine works and that you can drive it.
3. **Create your public scaffolding (half a day):**
   - A GitHub repo, e.g. `learning-ml` — every reproduction and experiment goes here.
   - A **research log** (`LOG.md` or a daily note): what you did, what broke, what you learned, what's next. One entry per session. This is the single highest-ROI habit in the whole roadmap.
   - A **paper-notes** file/folder. You'll add to it from Phase 1 on.
4. **Join one community (1 hour).** The **EleutherAI Discord** (#beginners / #research) is the highest-signal home for independent model researchers. Make an account, read, don't post yet. (Also fine: Hugging Face forums/Discord.)
5. **Set your target (1 hour).** Re-read the Levels table in the README. Write one line in your log: *"My 6-month target is L2 — run a clean extension of a small-models result."* Vague goals produce vague effort.

## The mental model to install this week

A modern language model is, end to end:

```
text ──tokenizer──► token ids ──embeddings──► [ transformer blocks: attention + MLP, repeated ] ──► logits ──► next-token probabilities
                                                                                                              │
                                              trained by: predict-the-next-token on a big corpus (pretraining)
                                              then shaped by: SFT + RL on smaller curated data (post-training)
                                              measured by: evals (which lie in subtle ways)
```

Every phase of this roadmap zooms into one part of that pipeline. Phase 1 = the neural-net
and backprop machinery underneath every box. Phase 2 = the transformer blocks + tokenizer.
Phase 3 = how the pretraining is actually done efficiently. Phase 4 = the post-training and
eval. Phase 5 = making one box better than anyone has, at small scale.

Keep this diagram in your log. You'll understand more of it every week.

## Milestone test (can you do this by end of week?)
- [ ] A loss curve you produced, screenshotted in your repo.
- [ ] First `LOG.md` entry written.
- [ ] First paper skimmed figures-first (try **TinyStories**, arXiv 2305.07759 — short and motivating) with a 3-sentence note.
- [ ] EleutherAI joined.

## Traps
- **Tooling rabbit holes.** Don't spend the week on the perfect dev environment, dotfiles, or a GPU rig. Colab is fine for now.
- **"I need to understand it first."** No. Run it, then understand it. Inversion of the instinct is the whole point of this week.
- **Skipping the log.** The log is not optional busywork — it's your external memory and the raw material of your first writeups. Start it now or you never will.

→ Next: **[phase-1-foundations.md](phase-1-foundations.md)**
