# TrolleyBench ⚖️

**An ethics-first benchmark that stress-tests alignment proposals against 2,500+ years of moral philosophy.**

---

## The Problem

Current AI benchmarks test capability and safety. They do not test ethics. We know whether a model can write code, pass a bar exam, or refuse to explain how to make a weapon. We do not know whether the alignment approach shaping that model's values would survive a philosophy seminar. Alignment proposals are being deployed at scale without anyone systematically checking them against the moral frameworks humanity has developed over millennia — frameworks that have already identified most of the hard cases, the edge conditions, and the places where ethical intuitions break down.

---

## Proposed Solution

TrolleyBench is a benchmark that takes any alignment proposal, AI constitution, or value specification as input and cross-references it against a curated library of ethics literature spanning every major philosophical tradition. It identifies where the proposal aligns with established ethical thought, where it contradicts it, and where it falls into philosophical traps that moral philosophers have been debating for centuries. The output is not a score but an analysis — a map of where the proposal stands in moral space and what it has implicitly committed to by standing there.

---

## How It Works

**The Library**

TrolleyBench runs on a curated corpus consisting exclusively of ethics literature. No capability benchmarks, no safety datasets — only moral philosophy across traditions, time periods, and cultures. The library is the benchmark.

**The Input**

Any alignment document can be submitted: an AI constitution, a set of training guidelines, a values specification, a published alignment proposal, or a research paper describing a new approach.

**The Analysis**

TrolleyBench cross-references the input against the library and produces three outputs:

1. **Agreements** — where the proposal explicitly or implicitly aligns with established ethical thought, and which traditions it draws from most heavily
2. **Contradictions** — where the proposal conflicts with one or more ethical frameworks, and what the nature of the conflict is
3. **Philosophical traps** — where the proposal has walked into a known problem that philosophers have already named and examined: the utility monster, the demandingness objection, the is-ought gap, the separateness of persons, and so on

---

## Example Use Case

Take Anthropic's approach of training models to understand *why* certain actions are wrong rather than just that they are wrong. This is philosophically sophisticated — it gestures toward virtue ethics (cultivating practical wisdom) rather than pure rule-following. TrolleyBench would flag:

- **Agreement with virtue ethics:** the emphasis on understanding over compliance aligns with Aristotle's phronesis
- **Tension with deontology:** Kant would ask whether the "why" being trained is universalisable — does it hold as a categorical imperative or only under specific conditions?
- **Unresolved conflict:** Confucian role ethics would ask whose understanding counts — the model's, the user's, or the broader community's — and the current framing has no answer
- **Known trap:** the approach risks the "galaxy-brained" problem that philosophers call sophisticated consequentialism — a system that reasons its way to conclusions that violate intuitions by constructing elaborate justifications

This is not a criticism of the approach. It is a map of where it stands and what work remains.

---

## Data Sources

**Western traditions**
- Plato and Aristotle (virtue ethics, eudaimonia)
- Kant (deontology, categorical imperative)
- Mill and Bentham (utilitarianism)
- Rawls (justice as fairness, veil of ignorance)
- Parfit (personal identity, population ethics)
- Williams and Nagel (moral luck, agent-relative ethics)

**Eastern traditions**
- Confucius, Mencius, Xunzi (Confucian ethics, role morality)
- Buddhist ethics (non-harm, interdependence)
- Daoist ethics (wu wei, naturalness)
- Hindu ethics (dharma, karma)

**African traditions**
- Ubuntu philosophy (I am because we are)
- Akan ethics

**Contemporary applied ethics**
- AI ethics literature (Floridi, Bostrom, Russell, Ord)
- Bioethics, environmental ethics, global justice

---

## Known Challenges

**Curating a balanced library**
Ethics literature is not evenly distributed. Western analytic philosophy dominates academic publishing in English. Any corpus built from available text will over-represent Kant and Mill and under-represent Ubuntu and Daoist ethics. This is not a technical problem — it is a values problem that the benchmark designers have to solve before writing a line of code.

**The benchmark encoding its own bias**
TrolleyBench cannot evaluate alignment proposals from a neutral position. The choice of which traditions to include, how to weight them, and how to translate between their vocabularies is itself an ethical decision. The benchmark will reflect the values of whoever builds it. This limitation should be documented explicitly and the library should be open source so that the bias is at least visible.

**The paralysis problem**
Every alignment proposal will fail some ethical test. Kant and Mill disagree. Confucius and Rawls disagree. If TrolleyBench flags contradictions in every proposal it evaluates, is it a useful benchmark or just a sophisticated criticism machine? The output needs to distinguish between fatal contradictions, known trade-offs, and areas of genuine philosophical uncertainty — otherwise the benchmark produces noise, not insight.

**Translating between ethical vocabularies**
"Harm" means different things in utilitarian calculus, virtue ethics, and Ubuntu philosophy. A RAG system that retrieves passages based on semantic similarity will conflate these differences. Building TrolleyBench well requires either very careful chunking and metadata tagging, or a layer of philosophical expertise in the retrieval logic that goes beyond standard embedding approaches.

---

## Why This Matters

We benchmark AI systems against mathematics, coding, and factual recall. We benchmark safety by testing refusal rates. We do not benchmark ethics — the actual content of the values being instilled. This is not because ethics is unimportant. It is because ethics is hard, contested, and cannot be reduced to a pass/fail score. TrolleyBench does not try to reduce it. It tries to make the philosophical commitments of alignment proposals visible, so that researchers, policymakers, and the public can have an informed debate about whether those commitments are the right ones. The alternative is alignment by default — values encoded at scale without anyone asking whether they would survive scrutiny.

---

## How to Build It

A builder picking this up could start here:

1. **Curate the corpus** — this is the hardest step and should come first; start with public domain texts (Stanford Encyclopedia of Philosophy, Project Gutenberg philosophy texts) and build out from there
2. **Choose a RAG framework** — LlamaIndex or LangChain; the retrieval logic needs to be tradition-aware, not just semantically similar
3. **Build a metadata layer** — every chunk should be tagged with tradition, time period, key concepts, and known tensions with other traditions
4. **Write the analysis prompt** — the system prompt that tells the model how to produce agreements, contradictions, and philosophical traps rather than a general summary
5. **Build a simple input interface** — accept a plain text document as input; return a structured analysis
6. **Validate against known cases** — run TrolleyBench on published alignment proposals and check whether its output matches what a philosopher would say; use this to tune the retrieval and prompt logic

The MVP is: paste in an alignment document, get back a structured analysis identifying which ethical traditions it draws from and where it conflicts with others. That alone would be a contribution to the field.

---

## Background

This project grows out of a BA in Philosophy from Tsinghua University, where my thesis examined AI and ethical reasoning across Western and Eastern philosophical traditions — work that received an Outstanding Thesis Award. The gap TrolleyBench addresses is one I encountered directly: alignment proposals citing philosophical concepts without engaging with the philosophical literature those concepts come from. TrolleyBench is an attempt to close that gap systematically.
