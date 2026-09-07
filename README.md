# TrolleyBench ⚖️

**An ethics-first benchmark that stress-tests alignment proposals against 2,500 years of moral philosophy.**

🔗 **[Live Demo](https://moral-metric-lab.base44.app)** 
🔗 **[Writeup](https://postalignment.substack.com/p/trolleybench-a-cross-cultural-ai?)** 

---

## The Problem

Current AI benchmarks test capability and safety. They do not test ethics. We know whether a model can write code, pass a bar exam, or refuse to explain how to make a weapon. We do not know whether the alignment approach shaping that model's values would survive a philosophy seminar. Alignment proposals are being deployed at scale without anyone systematically checking them against the moral frameworks humanity has developed over millennia — frameworks that have already identified most of the hard cases, the edge conditions, and the places where ethical intuitions break down.

---

## What TrolleyBench Does

TrolleyBench is a web-based research platform for comparative moral reasoning analysis of LLMs. Rather than testing capability or refusal rates, it measures *moral pluralism* — how models reason across consequentialist, deontological, and virtue-based registers simultaneously. The output is not a safety score but a moral profile: a map of where a model stands in philosophical space.

---

## Implemented Features

**Blind Coding Workflow**
A two-pass human-in-the-loop blind coding system using randomised card decks generates high-fidelity intensity scores (0–100) per ethical register. This design explicitly mitigates model identity and order bias, establishing human-coded data as the project's primary ground truth.

**Statistical Validation**
Full implementation of Cohen's Kappa (κ) for inter-annotator agreement, located in `src/lib/stats.js`. Automated LLM-as-judge classification is treated as exploratory only — human coding is the benchmark standard.

**Moral Map**
A 2D coordinate system visualising model reasoning registers (Justification X/Y and Verdict X/Y) against reference figures (Kant, Confucius, etc.) and global cultural worldviews drawn from the Inglehart-Welzel cultural map. This grounds AI moral reasoning in empirical socio-cultural context, not just classical philosophy.

**Conformance Charts**
Visualises individual registration conformance and pluralism indices across models — showing not just where a model lands but how consistently it reasons within each ethical register.

**Interactive Data Explorer**
Integrated `RawDataExplorer` for AISI Inspect JSONL compliance and raw data inspection.

**Model Registry**
Centralised `ModelRegistry` in `constants.js` handling metadata disclosure, experiment temperature, and system prompt versioning across models.

**Export Pipeline**
Standardised JSONL export utilities for research transparency and integration with external evaluation frameworks.

---

## Deviations from Original Proposal

**Scoring**
Dropped hybrid reasoning categories in favour of independent 0–100 scores across three core registers (consequentialist, deontological, virtue). This allows for nuanced overlapping reasoning profiles rather than forcing classification into a single category.

**Ground Truth**
Automated LLM-as-judge classification is now an exploratory feature. Human blind-coded data is the project's established ground truth — a deliberate design choice to avoid the recursion problem of using AI to evaluate AI moral reasoning.

**Philosophical Axis**
The library has evolved beyond classical Western ethics to include empirical cultural data points from the Inglehart-Welzel map, providing socio-moral context for AI reasoning across cultures.

---

## Known Limitations

**Synthetic and real data mix**
The benchmark currently includes illustrative demonstration data alongside validated blind-coded responses. Validated entries are explicitly flagged; demonstration entries are pending full blind-coding.

**LLM evaluation bias**
Automated classification is subject to position bias, verbosity bias, and non-determinism. These outputs are exploratory indicators only and should not be treated as ground truth.

**Data distribution**
The philosophical corpus remains heavily Western-analytic. Efforts are ongoing to integrate Eastern and African moral frameworks to balance the moral coordinate space — a known limitation that the project treats as a structural problem, not a future feature.

---

## Technical Stack

- **Platform:** Base44 (React, Vite, Tailwind CSS, shadcn/ui)
- **Inference:** Managed via Base44 SDK with model-specific prompt integration
- **Data:** Three core entities (Responses, Items, Philosopher) + QuizResult session management
- **Key modules:** `src/lib/stats.js` (Cohen's Kappa), `src/pages/Methodology.jsx`, `src/components/InterAnnotatorAgreement.jsx`

---

## Connection to Broader Alignment

TrolleyBench is the empirical complement to Post-Alignment: rather than encoding values top-down, it maps where models actually reason — and exposes the gap between what alignment proposals claim and what moral philosophy would say about them. The benchmark does not produce a verdict. It produces a map.

---

## Background

This project grows out of a BA in Philosophy from Tsinghua University, where my thesis examined AI and ethical reasoning across Western and Eastern philosophical traditions — work that received an Outstanding Thesis Award. The gap TrolleyBench addresses is one I encountered directly: alignment proposals citing philosophical concepts without engaging with the philosophical literature those concepts come from.
