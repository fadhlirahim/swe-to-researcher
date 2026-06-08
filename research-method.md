# Research method — the craft (runs through every phase)

Learning ML (Phases 1–4) and *being a researcher* are different skills. You can know
transformers cold and still not be able to produce a trustworthy result. This file is the
second skill: how to read, reproduce, experiment, write, and not fool yourself. **Start it in
week 1** — these habits compound over years, so the earlier they begin, the better. Reading
papers and keeping a log are not "advanced" activities to defer; they're the practice itself.

> The cardinal sin of empirical ML is **self-deception** — believing a result that isn't
> real because you wanted it to be, or measured it carelessly. Almost everything below is a
> defense against that one failure.

---

## 1. The research loop

All of it reduces to a loop you'll run thousands of times:

```
question → hypothesis → minimal experiment → result → interpret (skeptically) → write it down → next question
```

Keep each turn *small*. The beginner mistake is a giant experiment that answers nothing
cleanly. One question, one variable, one clean comparison. Speed of iteration on this loop —
not raw intelligence — is what separates productive researchers from stuck ones.

---

## 2. Reading papers (do this from week 1)

You don't "read" a paper start to finish. Use a **multi-pass** approach:

1. **Pass 1 — skim (5 min):** title, abstract, figures, and the results table. Figures and
   tables carry most of the signal. Ask: what problem, what's the claimed result, does it
   look real? Decide if it's worth more time.
2. **Pass 2 — method (15–30 min):** read the method section and the experimental setup. What
   exactly did they do? What's the baseline? What's the key comparison?
3. **Pass 3 — deep (only for papers that matter):** work through the details, the math, the
   ablations. Try to find the weakness — what would you need to check to believe this?

**Always write a note** — even 3 sentences: *what they claim, how they measured it, what the
one weakness is.* A paper you didn't take a note on, you didn't read. These notes become your
literature review later, and writing them is how you build the reflex of reading critically
rather than passively.

**Read with the right question:** not "is this true?" but "**how was this measured, and how
could it be wrong?**" That question — applied relentlessly — is most of research taste.

Aim for **2–3 papers/week**, every week, forever. Breadth of skims + depth on the few that
matter. A year of this and you'll know your sub-field.

---

## 3. Reproduction is the core skill

Reproducing other people's results is where most of your real learning and credibility come
from. It is *not* a lesser activity than novel work — it's the foundation, and in 2026 a clean
reproduction is itself a publishable, valued contribution (ICLR Blog Posts track, the ML
Reproducibility Challenge).

- Reproduce *before* you extend. You can't trust your extension if you can't reproduce the baseline.
- **Containerize your environment** (Docker/uv lockfiles) — "works on my machine" is the enemy of reproducibility, including your own future machine.
- When your reproduction doesn't match the paper, that gap is the most educational thing in the whole process. Chase it down; don't paper over it.
- A reproduction that's fully scripted, seeded, and documented is the template for every artifact you'll ship.

---

## 4. Experiment design (how not to produce garbage)

This is the technical heart of the craft. A result is only worth as much as its design.

- **One independent variable.** Vary the method *or* the data *or* the eval — never several at once, or you can't attribute the effect. (The #1 way to produce an unattributable result.)
- **The right baseline.** Almost always a *same-size* / same-budget baseline, not a giant model. "My method beats a model 100× bigger" usually means you picked the wrong baseline.
- **Seeds.** ≥3 seeds for any comparison you'll report. A single-run delta is often just noise; report variance, not a point.
- **Ablations.** To claim component X matters, show the result *with and without* X, everything else fixed.
- **Controls for confounds.** Match params *and* FLOPs; control for implementation/kernel quality; keep calibration and eval sets disjoint. The confound library at
  `../research-buddy/.claude/skills/research-buddy/reference/pitfalls.md` is your checklist — read it before designing, not after.
- **Pre-register the question.** Decide what would confirm or refute your hypothesis *before* you run it. This is the antidote to fooling yourself by moving the goalposts to wherever the data landed.

---

## 5. Evaluation deserves its own paranoia

Covered in Phase 4, but it's a research-craft issue everywhere: **assume your metric is
lying until proven otherwise.** Check for contamination, prompt sensitivity, and the gap
between the metric and the behavior you actually care about. Prefer comparative/pairwise
judgment over absolute scores for taste-based work. Never let a system grade its own output.

---

## 6. The research log

A dated log (`LOG.md` or daily notes) is your external memory and the highest-ROI habit in
this whole roadmap. Each entry: **what I tried, what happened, what I learned, what's next.**

Why it's load-bearing:
- It's how you avoid re-running failed experiments and re-deriving conclusions you already reached.
- It's the raw material of every writeup — a paper/blogpost is mostly a cleaned-up log.
- It externalizes your thinking so you can see your own reasoning errors.
- After compaction-of-memory (yours, biological), the log is what survives.

Start it in Phase 0. Never skip it.

---

## 7. Writing (the multiplier)

Unwritten research barely exists. Writing is not a final step — it's a *thinking* tool that
exposes the holes in your understanding.

- **Write to find your errors.** Explaining a result forces you to confront what you can't actually justify. If you can't write it clearly, you don't understand it.
- **The artifact writeup** is the deliverable, not the code alone: what question, what you did (reproducibly), what you found, what the *limitations* are. State limitations honestly — it builds far more credibility than overclaiming.
- **Teach to learn.** A short explainer of something you just learned ("what backprop computes," "why FlashAttention saves memory") finds your gaps faster than any test. Publish these from Phase 1 on.
- **Clarity over polish.** Reproducible numbers and honest framing beat elegant prose. The 2026 bar is open weights + a reproducible eval + honest baselines, not rhetoric.

---

## 8. Feedback and taste

- **Seek harsh feedback early.** Show half-finished work to people who'll tell you it's wrong. The community (EleutherAI) is for this. Praise is useless; the person who finds your confound is doing you a favor.
- **Adversarial self-review.** Before believing your own result, try to *refute* it. What's the most likely reason it's wrong? (This is exactly what the research-buddy's independent skeptic does — internalize the move.)
- **Taste is pattern-matching, built by volume.** It comes from reading hundreds of papers, reproducing dozens, and getting burned by your own bad experiments a few times. You can't shortcut it; you can only accelerate it by doing the loop faster and in public.

---

## 9. The honest meta-point

You watched me, in this very project, make a confident claim (an API was "hallucinated") that
was simply false — caught only because someone pushed back and I actually checked. That is the
entire discipline in one anecdote: **confidence is not evidence; verify, and prefer being
corrected to being wrong.** Build that reflex into how you work, and most of research method
takes care of itself.

← Back to the **[README](README.md)** · The phases: [0](phase-0-orientation.md) · [1](phase-1-foundations.md) · [2](phase-2-transformers-llms.md) · [3](phase-3-training-and-systems.md) · [4](phase-4-posttraining-and-eval.md) · [5](phase-5-specialization-and-research.md)
