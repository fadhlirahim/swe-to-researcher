# Phase 1 — Foundations (≈ 4–8 weeks)

**Goal:** understand and *implement from a blank file* the machinery under every model:
gradient descent, backpropagation, a neural net, and the core ML concepts (loss,
generalization, overfitting). Pull in exactly the math each step requires — no more.

**The gap this closes (for a strong engineer):** you can already write code; what you lack
is the *intuition* for why neural nets train, what a gradient is doing, and the ML concepts
(bias/variance, regularization, optimization) that make experiments interpretable. This
phase converts "I can call `.backward()`" into "I know exactly what `.backward()` computes
and could write it myself."

## What to learn (in priority order)
1. **Backpropagation** — the chain rule applied to a computation graph. The single most
   important thing in this phase. If you can implement reverse-mode autodiff, most of deep
   learning stops being magic.
2. **Gradient descent & optimizers** — SGD, momentum, Adam; learning rate, why it matters most.
3. **A neural net from scratch** — MLP, activations, initialization, why depth helps.
4. **Core ML** — loss functions (cross-entropy especially), train/val/test, overfitting,
   regularization, the bias–variance tradeoff. The grammar of every experiment you'll run.
5. **Math, just-in-time:** linear algebra (matmuls, what a matrix *does* to a vector),
   calculus (partial derivatives, the chain rule), probability (distributions, expectation,
   cross-entropy/KL). Learn each *when the model above forces you to*, from the reference below.

## Primary path (use these, not ten others)
- **Karpathy — Neural Networks: Zero to Hero** (the spine of this phase). **Do the exercises; don't just watch.** Specifically build:
  - **micrograd** — a tiny reverse-mode autodiff engine + an MLP, from a blank file. This *is* backprop. If you build one thing in Phase 1, build this.
  - **makemore** — a character-level language model, taken from a bigram count model up through an MLP. Bridges ML basics → language modeling and sets up Phase 2.
- **One breadth source, as reference (not cover-to-cover):** **fast.ai Practical Deep Learning** (top-down, build-first) *or* **d2l.ai** (interactive textbook). Use to fill gaps Karpathy doesn't cover. Andrew Ng's ML Specialization is a fine, gentler alternative if you want more hand-holding on the ML fundamentals.
- **Math reference (look up, don't read linearly):** *Mathematics for Machine Learning* (Deisenroth et al., free PDF). Open it only when a concept above is fuzzy.

## The project / deliverable
**Reimplement micrograd and makemore yourself, from scratch, in your repo** — not by copying,
but by watching a segment, closing it, and rebuilding from memory + first principles. Push
both with a README explaining what each does. Bonus: write a short blog-style note "what
backprop actually computes" — teaching it is how you find the holes in your understanding.

## Milestone test (you've finished Phase 1 when you can…)
- [ ] Implement reverse-mode autodiff for a small expression graph from a blank file, and hand-derive the gradient for one node to check it.
- [ ] Build, train, and debug an MLP on a toy dataset *without* copying — including diagnosing a too-high learning rate from the loss curve.
- [ ] Explain, in your own words in your log: cross-entropy loss, why we hold out a validation set, what overfitting looks like and three ways to fight it.
- [ ] Read an empirical ML paper and follow its training setup without getting lost.

## Time & calibration
4–8 weeks at ~10 hrs/week. **A strong engineer can move fast here** — the coding is easy
for you; spend your saved time on the *math intuition* and on rebuilding from memory rather
than copying. If micrograd clicks in week 1, don't pad — move toward Phase 2.

## Traps
- **Watching instead of building.** Karpathy makes it look easy; that's the danger. Close the video and rebuild from a blank file. The gap between "followed along" and "can implement" is the entire point.
- **Math-first detour.** Do not stop to "finish" a linear algebra course. Look math up when micrograd/makemore forces the question, then return.
- **Copy-paste completion.** Copying his code and running it teaches almost nothing. Type it from understanding, or rebuild from memory.

→ Next: **[phase-2-transformers-llms.md](phase-2-transformers-llms.md)**
