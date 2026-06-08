# Phase 5 — Specialization & doing research (ongoing)

**Goal:** stop following a curriculum and start *doing research* — pick a niche, produce
your first **original** result (however small), engage a community, and ship it publicly.
This phase has no end; it's the transition from "learning the field" (L1→L2) to "contributing
to it" (L2→L3→L4). The earlier phases were scaffolding for this.

**The shift:** in Phases 1–4 someone else defined the task. Here *you* do — first by
extending published work, then, eventually, by setting your own direction. That's the whole
definition of a researcher.

## Step 1 — Pick a niche (and go deep, not wide)
Generalists don't contribute; specialists do. Choose **one** sub-area where you can build a
real result on one GPU. Strong options for a small-models researcher:

- **Efficiency** — quantization, distillation, pruning, efficient architectures. (Highest leverage-per-dollar; your `cost_model` reality applies.)
- **Mechanistic interpretability** — small models are *interpretable*; the community rewards small clean results from unknowns. The on-ramp's induction-head / GPT-2-small project lives here.
- **Data curation / synthetic data** — the TinyStories lineage; often the highest-leverage variable.
- **Small reasoning models / post-training** — distilled reasoning, RLVR at small scale.

Use **`../advisory/small-models-research-onramp.md`** — it's the detailed specialization guide
(scoped projects, the field map, precedents, and the full how-to-get-visible-and-publish
playbook). This phase and that document are the same destination from two angles; read it now
in full.

## Step 2 — Produce your first original result
This is where the `../research-buddy` skill earns its place. The loop:

1. **Reproduce** something in your niche (you've been doing this since Phase 3 — now it's the launchpad, not the goal).
2. **Find the open thread** — the cheap ablation the paper didn't run, the variable nobody swept. Reading deeply *is* idea generation; the act of reproducing surfaces these.
3. **Scope it** with the research-buddy: prior-art check (is it done?), feasibility (one GPU?), confound check (is the comparison clean?). Get a tight, controlled plan.
4. **Run it.** Fix one model family, one dataset, vary one axis, ≥3 seeds, same-size baseline.
5. **Ship the artifact** — open weights/code + a reproducible eval harness + honest baselines + a clear writeup. This is your L3 credential.

Specialization resources (pick per niche, see `resources.md`): **ARENA** (the mech-interp /
alignment-engineering curriculum, with TransformerLens) if you go the interpretability route;
the efficiency papers and the modded-nanogpt ecosystem if you go efficiency.

## Step 3 — Do research as a practice (forever)
This is the craft, covered in depth in **[research-method.md](research-method.md)**: read the
frontier continuously, keep a research log, design controlled experiments, write clearly,
seek harsh feedback, build taste. The phases end; this doesn't.

## Step 4 — Get visible and find your people
You cannot do research alone and invisibly. From the on-ramp's playbook:
- **Ship in public** — open-source-as-research is the modern credential. Weights + eval + writeup beats a clever-sounding paper with no artifact.
- **EleutherAI** (#research, and the **SOAR** mentored program) is the highest-ROI single move — it solves collaborators, granted compute, and the arXiv-endorsement gate simultaneously.
- **Realistic venues:** the ICLR Blog Posts track, NeurIPS ENLSP workshop, the ML Reproducibility Challenge. Not the main-track lottery.
- **The credibility loop:** artifact → tight writeup with reproducible numbers → share → community → collaborators. Twitter/X is the funnel; Discord is where collaboration happens.

## Milestone test (you're operating as a researcher — L3 — when…)
- [ ] You've shipped at least one *original* result (an extension or a small novel finding) with open code + honest eval, publicly.
- [ ] Someone you didn't know has used, cited, or built on it.
- [ ] You're an active member of a research community (asking, answering, collaborating).
- [ ] You can read a frontier paper in your niche and immediately see the next experiment.
- [ ] You're choosing your own questions, not waiting to be assigned one.

## Time & calibration
Ongoing — this is the rest of your research life. The first original artifact typically lands
**1–2 years** in (L3); setting your own recognized research direction (L4) is **2–4+ years**.
Mastery is asymptotic; stop measuring it and measure shipped artifacts instead.

## Traps
- **Niche-hopping.** Depth compounds; breadth doesn't. Stay in one sub-area long enough to develop taste before switching.
- **Reaching for novelty too early.** Your first "original" result should be a clean extension of existing work, not an invented direction. Earn novelty.
- **Building tools instead of doing research.** (Yes — this includes over-investing in the research-buddy. It's an aid, not the work.) Ship results, not infrastructure.
- **Isolation.** The single biggest accelerator available to you is a community that grants compute, gives feedback, and co-authors. Use it.

← The phases end here. **[research-method.md](research-method.md)** is the craft that runs forever.
