# Temporal Plasticity for a Frozen Brain

## A research program on what makes a static transformer part of a living cycle

**Status:** research note — an honest record of the current state of an open research program. Not a product, not a release plan; negative results count as results here.
**Origin:** the Molecular AI program; manifesto v0.2 and conceptual sessions of April–July 2026.
**Language:** English — translation. The Russian original lives in this repository; where the two diverge, the original takes precedence.
**Version history:** v0.1 (July 2026) → v0.2 (October 2026): the "resource envelope" pass — removal of the Hardware Humble requirement, introduction of the judgment layer, multi-level consolidation, ablation discipline, reassessment of the shelf framework. The pass delta is a separate file in the repository.

* * *

## 1. Meta-thesis: process, not architecture

Molecular AI studies the continuously running learning process as the living mechanism of intelligence. The static transformer is its frozen result, not the thing itself. We study the thawed one.

The program did not arrive at this formulation immediately. The first version of the manifesto described an alternative paradigm — an opposition to transformers. An honest inventory showed that **five of the six properties of living intelligence** claimed as missing are in fact present in the transformer — in implicit form: **specialization** (layers emergently divide the work, from morphology to response planning), **parallelism** (attention heads), **internal modulation** (the processing regime shifts with context), **modular memory** (MLP as associative, attention as working), **integration** (the residual stream as a shared flow of representations). One thing is missing — **plasticity in time**: weights are frozen after training, experience does not change the system, every session starts from zero.

Hence the positioning: **we are not an alternative to transformers. We are what makes the frozen result part of a living cycle.** The formula: the transformer is the brain; Molecular AI is the organism.

The program's bet aims where the mainstream rarely looks. The industry is busy with the architecture of the processing machine — attention variants, MoE, state space models — while the learning algorithm (gradient descent with Adam) has not fundamentally changed since 2014. The bottleneck may be in the learning process, not in the machine's design.

A separate v0.2 revision concerns the resource frame. The original Hardware Humble requirement (the whole organism runs on an ordinary laptop) has been removed: on inspection it turned out to be not a property of the program but its hidden limiter. The quality ceiling of the entire system was bound to the judgment quality of one small local model — and that ceiling was measured by the program's own experiment (§7). The resource envelope is reformulated as a parameter, not an identity (§5).

## 2. Six theses

Each is a testable hypothesis, not an axiom.

1. **Specialization** is already implemented implicitly; we test whether it can be made explicit and articulable — through external modules with clear interfaces. The gain is explainability and independent development of abilities, not new functionality.
2. **Parallelism** exists at the level of attention heads; we extend it to processes around the model — a background crew, critics, observers. This adds not speed but the ability to exist between requests. In v0.2 the continuity of background processes stops being a budget question and becomes the norm; the testable hypothesis that remains is their measurable contribution to quality.
3. **Neuromodulation** works inside, but implicitly and unpredictably; an explicit layer of significance triggers stabilizes what is already there.
4. **Modular memory** is present; we add the missing type — external episodic memory accumulated through use.
5. **Integration** is solved within a single forward pass (the residual stream); at the system level an explicit mechanism is needed to reconcile processes running on different time scales.
6. **Plasticity in time** — the new, central contribution: multi-level plasticity across time scales (context → external memory → surgical weight edits → a bank of LoRA adapters → deep consolidation), with significance triggers at the input and consolidation processes during sleep. The hypothesis: this revives a static model without catastrophic forgetting. The hypothesis's status is unchanged in v0.2 — it has not met experiment; the kill experiment is declared priority #1 (§7).

## 3. Theoretical support: complementary learning systems

The architecture rests on a model from neuroscience — complementary learning systems. The living brain has two memory systems with different dynamics: a fast one (the hippocampus) accepts everything indiscriminately, a slow one (the neocortex) embeds what has been validated through consolidation during sleep. In Molecular AI: the transformer is the neocortex analogue (changes slowly, through LoRA adapters), the external graph of knowledge molecules is the hippocampus analogue, the sleep cycle is the consolidation process between them.

The key difference from "memory with forgetting": **overload protection is selectivity at the gate, not deletion after the fact.** Most information never enters the system: six significance triggers operate at the input — Valence, Salience, Novelty, Goal, Confidence, and Temporality. The last classifies knowledge by obsolescence grades (A/B/C) and carries self-reflection: low confidence in the classification is itself a signal to treat the topic under the safe grade. When trigger directives conflict, the system does not run a fan-out search in all directions — it asks a clarifying question.

A v0.2 addition — an honest record of neighborhood. In machine learning, the analogue of sleep consolidation is known as generative replay: the model rehearses its past on self-generated data, which reduces interference during further training. The program directly borrows this apparatus for the deep phase of consolidation (§5). The continual learning community (EWC, replay methods) has been modifying the learning algorithm for a long time; the program's contribution is not the discovery of the problem but linking it with selectivity at the gate and epistemic bookkeeping (§4).

## 4. The molecule

The unit of external memory is called a molecule not for beauty: like a molecule of a substance, it is semantically atomic, connects through typed bonds, and lives in a medium with processes.

**The form — fact+context with an "NL + structural index" core.** The core is one normalized natural-language statement plus an automatically extracted index (subject, predicate, object, modality, polarity). The context is a hybrid of typed fields (source, interval of validity, strength of the source's assertion) and free text with caveats. The form was chosen by iterating four candidates against 24 constraints: a pure SPO triple is strong inside the archive and weak at the input (and under honest optimization degenerates into fact+context); the RAG chunk was rejected (10 caveats out of 24); the form differs from an A-MEM note by its typed graph and the core/context split, from a Wikidata triple by a textual rather than ontological core.

**A molecule is a node of a distributed system, not a record.** Its attributes are spread across four layers of the archive: content (core + context), vector (two embeddings — a primary one over the core for placement and deduplication, an auxiliary one over core+context for operational search), graph (typed links: *develops*, *contradicts*, *related_by_generality* with optional direction; each link carries its own classifier-confidence scalar), and metadata.

**Status is a fold over history, not a label.** Metadata holds an immutable event log (17 canonical record types; a correction is a compensating entry, never an edit). A molecule's status is a cached fold over this journal: ten statuses, from candidate through maturation to fixation in LoRA and absorption into base weights, plus three terminal ones. One of them — **dying-off** — is honesty about irreversibility. In v0.2 its scope is narrowed: knowledge fixed in an additive LoRA adapter is revocable by construction (the adapter is detached, versions are kept); only what is absorbed into base weights during deep consolidation remains irreversible — a rare, explicit, and now voluntary operation (§5). Dying-off records: the system acknowledges that its current understanding has diverged from what was absorbed, without having a mechanism of recall.

**Two confidence scalars are never mixed:** the strength of the source's assertion (on the core) and the link classifier's confidence (on the link) are different epistemic objects; consumers use them as independent filters, never as one composite score.

## 5. The organism of one shelf

Around the transformer core there are eight subsystems (knowledge archive, temporal, significance triggers, immune, intentions, operational introspection, consolidation, archivist) and three components (core, roving workers, chronicler). In v0.2 the roster gains a **judgment layer** — dedicated critic models; it is load-bearing, so it is described first. Below are the load-bearing mechanics.

**The judgment layer — the new load-bearing element of v0.2.** All evaluative work is moved out of the core: the entry critic, the semantic conflict resolver, the link classifier, the content evaluator of consolidation, and the significance triggers are implemented as specialized models distilled from frontier models. The source material already exists: the probe-scan markup by two frontier models (consensus on 90.8% of the sample, §7) is a ready-made training corpus. The principle from §7 is generalized into a norm: **a judge is a measuring instrument with its own systematics**; every critic in the layer ships with its systematics measured and documented, and its verdicts are consumed with a correction for them. This is a direct answer to the measured ceiling of the local judge (53.2% agreement with consensus): the program no longer delegates critical decisions to models whose judgment quality failed its own test.

**The observer — interoception, not self-report.** Signals about the core's state come from probe classifiers on mid-layer activations — not verbalized confidence and not logits. The observer's contract is a triple of scalars `(gap, uncertainty, relevance)`: a direct signal of a knowledge gap, a direct signal of uncertainty at the level of semantic representations, and a predictive signal of archive relevance which alone does not motivate action. In v0.2 the observer gets a proper training base: probes are trained as ensembles on large labeled corpora, with control tasks against spurious correlates; transfer between core versions is a separate measured procedure, not an assumption. The risk remains a research risk (§8), but it turns from a bet into an engineering task.

**The archivist — an active subject of memory, not a retrieval service.** Inside — a chief and three workers (reference clerk, placement clerk, orientation clerk), its own memory (a topology map of the archive, two calibration states, three time queues). It acts on the principle of motivatedness: no intervention into the context happens without a formal observer signal — the motivatedness gate turns "no gap and no uncertainty" into automatic non-intervention. The chief then chooses among four modes: non-intervention, enrichment, correction (the archive is fresher than the weights), conflict. Insertion into the context — only with an explicit source tag: the distinguishability of "archive versus weights" is an architectural commitment, because **the archive is a delta from the weights**, not a full knowledge base.

**At night the placement clerk builds the graph.** For each newly arrived molecule — a "cheap → expensive" pipeline: the numeric stage (candidate selection by primary embedding in the region suggested by the topology map, with two proximity thresholds) → metadata (cheap checks of indexes and flags) → semantics (a call to the judgment layer) → decision. Uncertain pairs go to the re-examination queue, contested ones to the escalation queue for the chief. In v0.2 the queues change meaning: from budget graveyards they become latency buffers; "unprocessed due to budget" is a vanishing regime. Contradiction is a state of the graph with a resolution attribute, not a flag on a molecule: an unresolved "contradicts" pair blocks the molecule's path into LoRA and is passed to the semantic resolver of the judgment layer.

**The immune subsystem — veto asymmetry.** The entry critic (veto on writing to memory) and the request critic (veto on reaching outside) can forbid; the adequacy advisor, working after generation, can only signal. Calibrating critics is like immunity: too sluggish — inaccuracies, too active — paralysis. In v0.2 calibration stops being a metaphor: it is performed against frontier-model markup with the systematics of each critic measured.

**Consolidation — three levels instead of one (reformulated in v0.2).** (1) **Surgical weight edits** (model editing in the spirit of ROME/MEMIT) — a fast layer for individual facts, intermediate between the archive and adapters. (2) **A bank of LoRA adapters with routing and composition** — the main fixation layer; adapters are additive, versioned, and revocable, which narrows the scope of irreversibility (§4). (3) **Deep consolidation** — a rare, explicit operation: merging seasoned adapters into base weights with generative replay (the core rehearses the past on its own generated data, §3) and validation by two evaluators — formal and content.

**A single aggregator.** Raw events from all subsystems flow into one timeline; subsystems keep no local logs. What they get back is not events but autobiography digests — with a delay of one sleep cycle. The history of an object (a molecule's event log) and the history of processes (the timeline) are fundamentally different channels.

**The sleep cycle — ownership and phases.** Five phases: closing the day → intake and review (entry critic → placement clerk → orientation clerk, strictly sequential) → meta-digests and calibration → selection for fixation → training and validation. Coordination is through a system-state variable; during sleep subsystems make no direct calls to each other. In v0.2 the sleep cycle turns from queue orchestration into a real MLOps pipeline: training → validation → versioning → rollback capability. Reversibility is built in, of three types: intake is not revised retroactively (the critic is adapted through calibration, not retrospection), consolidation is rolled back through adapter versioning, history is available through a three-tier store with age aggregation. And sovereignty of the decision in time: at the moment of generation the final choice of tokens belongs to the core — it is entitled not to use inserted material; the system corrects for this in the long run, through sleep.

**The resource envelope — a parameter, not an identity (replaces Hardware Humble in v0.2).** The "whole organism on a laptop" requirement is removed: it constrained the main things — judgment quality, consolidation cadence, probe trainability, and the continuity of background processes. An honest record of what resources buy and what they do not. They buy: quality of the judgment layer, frequency and depth of consolidation, full-fledged probe training, continuity of background work. They do not buy: the answer on catastrophic forgetting (it is empirical, not computational), probe transfer between core versions, falsifiability of the program (it is set by metrics fixed in advance, not by hardware). Removing the ceiling also removes the alibi: failure can no longer be explained by anything except the architecture itself.

**The new price of positioning.** "An organism on a laptop" was a moat separating the program from the industry; without it, the neighborhood with the labs' continual-learning programs becomes direct. The program's answer: the contribution is not scale but process discipline — selectivity at the gate, epistemic bookkeeping (the lifecycle, two independent confidence scalars, the event log), a calibrated judgment layer. Hardware is a commodity; discipline is not.

## 6. The shelf framework: reassessed in v0.2

A later refinement of v0.1: everything described above is the design of **one shelf**, a single-language instance of the system. In v0.2 the shelf framework is moved from the program's identity into **deferred hypotheses**. Two reasons are recorded directly.

The first is internal: the blocking contradiction "molecules do not merge, they group" versus the formally preserved merge mechanics (§8.1 in v0.1) is generated by the framework itself — the non-merge premise is needed precisely for the shelves. That is, the contradiction is partly self-inflicted, and stopping the pass was stopping in front of one's own construction.

The second is external: research on bilingual memory (the revised hierarchical model and the subsequent line of work) and the empirics of multilingual transformers support a single conceptual store with language-specific access; separate per-language archives ("привет" and "hello" as two molecules on two shelves) reproduce the separate-stores model that psycholinguistics has largely rejected. A program that leans on neuroscience in §3 must reckon with it here as well.

The single-language shelf remains the working instance of the system. Inter-shelf organization is a pass closed until new grounds appear; the merge cluster keeps its CONTESTED status until the framework's fate is decided.

## 7. Method and current state

**Discipline.** The program develops in passes: each pass closes a cluster of questions and is recorded as a delta; deltas are periodically assembled into an architecture snapshot. Thirteen passes completed (subsystem map → lifecycle → reversibility → consolidation → archivist → molecule form → … → resource envelope). Priority rules for document contradictions are formalized; hypothesis notes are separated from decisions by the status "do not apply without explicit verification."

**Ablation discipline (new in v0.2).** Every named mechanism of the architecture — triggers, the typed graph, the observer, the judgment layer, the levels of consolidation — must earn its budget: the component is removed, the degradation is measured on benchmarks fixed in advance (LongMemEval, LoCoMo, standard continual-learning protocols), the success threshold is announced before the experiment. A mechanism without measurable contribution is removed from the architecture regardless of conceptual appeal. This is the procedural answer to the concept-inflation risk: item 8.6 from v0.1 has been turned from an admission into a norm.

**Priority #1 — the kill experiment for thesis 6 (new in v0.2).** Before any new conceptual passes: a stream of facts → a comparison of three regimes on one core — (a) pure retrieval, (b) naive consolidation into LoRA, (c) consolidation with triggers at the input. Metrics: retention of prior abilities (a regression suite) and completeness of new-fact recall. If (c) does not differ from (a), the program records degeneration into the documented failure mode (§9) and revises thesis 6. The experiment is cheap and feasible within weeks; its absence after twelve passes is acknowledged as a prioritization error.

**Executable specification.** The fixed part of the architecture has been translated into a typed Python package: a living core (molecule, lifecycle, event log, links — validated by tests and strict typing) and a Protocol skeleton of all subsystems with `NotImplementedError` bodies. Code is a derived artifact: documents are primary; ambiguities in code are marked with a status legend (DECISION / CONTESTED / HYPOTHESIS / OPEN / EMPIRICAL); no numeric thresholds are hard-coded anywhere. The method has already paid off: the mandatory cross-check of every code assertion against the documents exposed two internal contradictions of the snapshot, invisible to linear reading — typing works as an enforced coherence check. A separate methodological note on this is forthcoming.

**The first experiment (preliminary).** A parallel branch, probe-scan, tested extracting knowledge from a small model's weights by probing against an external corpus (Wikipedia, the Solar System). All numbers below are _preliminary_, pending completion of manual validation: an LLM judge (qwen2.5:7b) labeled 1390 probe-only clusters; two independent frontier-model markups agreed on 90.8% of the sample; the judge against their consensus — 53.2%, with a systematic skew toward strictness (up to ~70% of its "contradiction" verdicts are not contradictions). The methodological lesson is already stable: **an LLM judge is a measuring instrument with its own systematics**; it must be calibrated and characterized like any instrument, and its quoted rationales must be checked against the source, because paraphrase from weights gets mixed in unnoticed. In v0.2 this experiment received a second reading: it measured the ceiling of a local model's judgment quality, to which the architecture delegated critical decisions — the direct motive for the "resource envelope" pass. And the frontier-model markup received a second use: the training corpus for the judgment layer (§5).

**Maturity map.**

| Area | State |
| --- | --- |
| Molecule form, lifecycle, event log | Fixed; encoded in the living core of the specification |
| Archivist, link pipeline, queues | Conceptually fixed; Protocol skeleton; queues reframed in v0.2 |
| Judgment layer | Adopted in v0.2; training corpus exists (probe-scan); calibration of systematics — open work |
| Triggers, immune, intentions, temporal | Map and boundaries fixed; detailing — future passes |
| Consolidation | Reformulated as three levels (§5); experimentally untested; kill experiment — priority #1 |
| Observer (probes on activations) | Contract fixed; resource ceiling on training removed; transfer between versions — a measured risk |
| Shelf framework / inter-shelf layer | Moved to deferred hypotheses (§6); pass closed until new grounds |
| Difference from neighbors | A-MEM/Zettelkasten agents — no typed graph with a lifecycle; MemGPT/Letta — context management, not consolidation into weights; Generative Agents — reflection without a path into weights; sleep-inspired approaches — no selectivity at the gate; continual learning (EWC, replay, generative replay) — no epistemic bookkeeping or judgment layer; model editing (ROME/MEMIT) — surgical edits without a lifecycle. The bundle "triggers at the input → typed graph with lifecycle → multi-level consolidation → observer on activations → calibrated judgment layer" has not been seen in this completeness; the measure of the contribution is the ablation discipline, not the uniqueness of the combination |

## 8. Open problems

1. **Thesis 6 has not met experiment.** The kill experiment (§7) is blocking for the entire consolidation vertical; no new conceptual passes are opened until its result.
2. **The observer** — trainability of probe classifiers at the needed quality and their transfer between core versions; the risk is measurable, the measurement procedure is fixed, the result is open. If it fails, the principle of motivated action loses its input.
3. **Calibrating the judgment layer.** The systematics of each critic must be measured and compensated; until then the layer is a carrier of others' biases, not a measuring instrument.
4. **Shelves (deferred).** The merge contradiction is acknowledged as partly self-inflicted (§6); the CONTESTED cluster remains until the framework's fate is decided.
5. **Thresholds and interpretations.** All numeric thresholds are calibration state; the rules for how different consumers use the two confidence scalars are not fixed.
6. **Scaling in time.** The behavior of the graph, queues, and topology map over a horizon of years of continuous operation is unknown.
7. **Concept inflation — residual risk.** The risk has been turned into a procedure (ablation discipline, §7); the residue is that the discipline may not be applied to conceptually beloved mechanisms. The only protection is announcing success thresholds before the experiment.
8. **Absorption by engineering (new in v0.2).** A fleet of models and MLOps pipelines create an operational load capable of pulling resources away from the research question. The antidote is the "kill experiment first" order fixed in §7.

## 9. What the program is not

Not a commercial product and not an MVP. Not a competitor to LLM companies — scaling the current paradigm and investigating the living process of learning are different tasks. Not an attempt to build AGI. Not a claim that transformers are bad. **Not another RAG framework**: the chain "query → embedding → search → LLM" is one utility fragment, not the essence; the architecture is a multi-process system with different time scales, and its degeneration into RAG is considered a documented failure mode, against which a separate protective discipline is built. **Not a bet on compute (new in v0.2)**: resources buy judgment quality and consolidation cadence, not answers; everything the program claims is still tested by experiment. Not a fast project: the horizon is years.

## 10. Status and invitation

The phase is conceptual design with first empirical probes; priority has shifted to the kill experiment for thesis 6. The program's code and data repository (the executable specification, experiment materials) is being prepared for publication. The most useful thing to leave here is criticism: an objection to any of the six theses, a counterexample to the maturity map, a pointer to work we have not noticed, or to a contradiction we have not noticed in ourselves. The program has already rewritten its manifesto in response to criticism; v0.2 is the second such rewriting, and the readiness to repeat this remains.

* * *

_Research note · July 2026 → October 2026 · v0.2 (English translation)_

**A note on authorship.** This document is a product of dialogic co-authorship with asymmetric responsibility: the ideas and formulations constituting the research program are the author's own; the cartography of the surrounding landscape — the AI assistant's.
