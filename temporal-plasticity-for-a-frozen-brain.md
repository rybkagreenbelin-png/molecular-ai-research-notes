# Molecular AI: Temporal Plasticity for a Frozen Brain

### A research programme on what makes a static transformer part of a living cycle

**Status:** research note — an honest fixation of the current state of
an open research programme. Not a product, not a release plan;
negative results count as results here.
**Origin:** the Molecular AI programme; manifesto v0.2 and the
conceptual sessions of April–July 2026.
**Language:** English edition, translated from the Russian original in
this repository. In case of divergence, the original governs.

---

## 1. The metathesis: a process, not an architecture

Molecular AI studies the continuously running learning process as the
living mechanism of intelligence. A static transformer is its frozen
result, not the process itself. We study the unfrozen one.

The programme did not arrive at this wording immediately. The first
version of the manifesto described an alternative paradigm — an
opposition to transformers. An honest inventory showed that **five of
the six properties of living intelligence** we had declared missing
are in fact present in the transformer — implicitly:
**specialisation** (layers emergently divide the work, from morphology
to answer planning), **parallelism** (attention heads), **internal
modulation** (the processing mode shifts with context), **modular
memory** (MLP blocks as associative memory, attention as working
memory), **integration** (the residual stream as a shared
representation flow). One property is missing — **plasticity in
time**: the weights are frozen after training, experience does not
change the system, every session starts from zero.

Hence the positioning: **we are not an alternative to transformers.
We are what makes the frozen result part of a living cycle.** The
formula: the transformer is the brain; Molecular AI is the organism.

The programme's bet points where the mainstream rarely looks. The
industry is busy with the architecture of the processing machine —
attention variants, MoE, state space models — while the learning
algorithm (gradient descent with Adam) has not fundamentally changed
since 2014. The bottleneck may be in the learning process, not in the
machine's internals.

## 2. Six theses

Each is a testable hypothesis, not an axiom.

1. **Specialisation** is already implemented implicitly; we test
   whether it can be made explicit and articulable — via external
   modules with clear interfaces. The gain is explainability and
   independent development of capabilities, not new functionality.
2. **Parallelism** exists at the level of attention heads; we test
   whether it can be extended to processes around the model — a
   background crew, critics, observers. This adds not speed but the
   ability to exist between requests.
3. **Neuromodulation** works inside, but implicitly and
   unpredictably; an explicit layer of salience triggers stabilises
   what is already there.
4. **Modular memory** is present; we add the missing kind — external
   episodic memory that accumulates through use.
5. **Integration** is solved within a single forward pass (the
   residual stream); at the system level an explicit coordination
   mechanism is needed for processes running on different timescales.
6. **Plasticity in time** — the new part, the central contribution:
   multi-level plasticity across timescales (context → external
   memory → consolidation into LoRA), with salience triggers at the
   entrance and consolidation processes during sleep. The hypothesis:
   this brings a static model to life without catastrophic
   forgetting.

## 3. The theoretical anchor: complementary learning systems

The architecture rests on a model from neuroscience — complementary
learning systems. A living brain has two memory systems with different
dynamics: a fast one (the hippocampus) that admits almost everything,
and a slow one (the neocortex) that integrates the verified through
consolidation during sleep. In Molecular AI: the transformer is the
neocortex analogue (changes slowly, through LoRA adapters), the
external graph of knowledge molecules is the hippocampus analogue, and
the sleep cycle is the consolidation process between them.

The key difference from "memory with forgetting": **overload
protection is selectivity at the entrance, not deletion after the
fact.** Most information never enters the system in the first place:
six salience triggers work at the entrance — Valence, Salience,
Novelty, Goal, Confidence and Temporality. The last one classifies
knowledge by decay classes (A/B/C) and carries self-reflection: low
confidence in the classification is itself a signal to handle the
topic under the safe class. When triggers give conflicting directions,
the system does not fan out searches in all directions — it asks the
user a clarifying question.

## 4. The molecule

The unit of external memory is called a molecule not for decoration:
like a molecule of matter, it is atomic in meaning, joins others
through typed bonds, and lives in an environment with processes.

**The form is fact+context with an "NL + structural index" core.** The
core is a single normalised natural-language statement plus an
automatically extracted index (subject, predicate, object, modality,
polarity). The context is a hybrid of typed fields (source, validity
interval, the source's assertion strength) and free text with caveats.
The form was chosen by examining four candidates against 24
constraints: a pure SPO triple is strong inside the archive and weak
at the entrance (and, when honestly optimised, degenerates into
fact+context); the RAG chunk was rejected (10 reservations out of 24);
the form differs from an A-MEM note by the typed graph and the
core/context split, and from a Wikidata triple by a textual rather
than ontological core.

**A molecule is a node of a distributed system, not a record.** Its
attributes are spread across the four layers of the archive: content
(core + context), vector (two embeddings — the primary one over the
core for placement and deduplication, the auxiliary one over
core+context for operative search), graph (typed links: develops,
contradicts, related_by_generality with an optional direction; each
link carries its own classifier-confidence scalar) and metadata.

**Status is a fold over history, not a label.** The metadata layer
holds an immutable event log (17 canonical record types; corrections
are made by compensating records, never by editing). A molecule's
status is a cached fold over this log: ten statuses, from candidate
through maturation to LoRA consolidation and absorption into the base
weights, plus three terminal ones. One of them — **atrophy** — is
honesty about irreversibility: what has been absorbed into the weights
cannot be recalled, but the system can acknowledge that its current
understanding has diverged from what was absorbed.

**Two confidence scalars are never mixed:** the source's assertion
strength (on the core) and the classifier's link confidence (on the
link) are different epistemic objects; consumers use them as
independent filters, never as one composite score.

## 5. The organism of one shelf

Around the transformer kernel there are eight subsystems (the
knowledge archive, the temporal subsystem, salience triggers, the
immune subsystem, intents, operative introspection, consolidation, the
Archivist) and three components (the kernel, the walkers, the
chronicler). Below are the load-bearing mechanics.

**The observer is interoception, not self-report.** Signals about the
kernel's state come from probe classifiers on the mid-layer
activations — not verbalized confidence and not logits. The observer's
contract is a triple of scalars `(gap, uncertainty, relevance)`: a
direct signal of a knowledge gap, a direct signal of uncertainty at
the level of semantic representations, and a predictive signal of the
archive's relevance, which on its own never motivates action.

**The Archivist is an active subject of memory, not a retrieval
service.** Inside: a chief and three workers (the reference clerk, the
placer, the orienteer), plus its own memory (a topology map of the
archive, two calibration states, three temporal queues). It acts on
the principle of motivated action: no intervention into the context
happens without a formal signal from the observer — the motivation
gate turns "no gap and no uncertainty" into automatic
non-intervention. The chief then chooses among four modes:
non-intervention, enrichment, correction (the archive is fresher than
the weights), conflict. Insertion into the context always carries an
explicit source mark: distinguishing "archive versus weights" is an
architectural obligation, because **the archive is a delta from the
weights**, not a full knowledge base.

**At night the placer builds the graph.** For every newly arrived
molecule there is a cheap-to-expensive pipeline: the numeric stage
(candidate selection by the primary embedding within a region hinted
by the topology map, with two proximity thresholds) → metadata (cheap
checks of indices and flags) → semantics (a kernel call within a
budget) → decision. Uncertain pairs go to a re-examination queue,
pairs unprocessed within the budget go to the unplaced queue, disputed
ones go to the chief's escalation queue. A contradiction is a state of
the graph with a resolution attribute, not a flag on a molecule: an
unresolved "contradicts" pair blocks the molecule's path into LoRA and
is handed to the semantic resolver of the intents subsystem.

**The immune subsystem is veto asymmetry.** The input critic (veto on
writing into memory) and the query critic (veto on reaching outward)
may forbid; the adequacy advisor, working after generation, may only
signal. Calibrating the critics is like calibrating an immune system:
too sluggish — inaccuracies; too aggressive — paralysis.

**The single aggregator.** Raw events from all subsystems flow into
one chronometer; subsystems keep no local logs. What they receive back
is not events but autobiography summaries — delayed by one sleep
cycle. The history of an object (a molecule's event log) and the
history of processes (the chronometer) are fundamentally different
channels.

**The sleep cycle: ownership and phases.** Five phases: the day's
summary → intake and revision (input critic → placer → orienteer,
strictly in sequence) → meta-summaries and calibration → LoRA
selection → training and validation (two evaluators: formal and
behavioural). Coordination goes through a system-state variable; no
subsystem calls another directly during sleep. Reversibility is built
in at three levels: admission is never revised retroactively (the
critic adapts by calibration, not by retrospection), consolidation is
rolled back by adapter versioning, and history stays accessible
through a three-tier store with age-based aggregation. And the
sovereignty of decision in time: at the moment of generation the final
token choice belongs to the kernel — it is free not to use the
inserted material; the system corrects for that in the long run,
through sleep.

**Hardware Humble** is a baseline requirement, not a limitation: the
whole organism runs on an ordinary laptop; the GPU is reserved for
dense training operations only.

## 6. The shelves frame: the direction of the next frontier

A late refinement of the programme: everything described above is the
anatomy of **one shelf** — a single-language instance of the system.
Every language is a separate shelf with its own archive, graph and
Archivist; "привет" and "hello" are two different molecules on two
shelves joined by a complementarity bridge — never one molecule with
two representations. The transformer kernel and the LoRA adapters are
shared across shelves. Technical and formal languages (Python,
mathematics) do not form shelves: their static knowledge lives in the
base weights.

Inter-shelf organisation — complementarity, shelf initialisation,
cross-shelf conflict resolution — is the subject of the programme's
next major pass. It is currently blocked, and §8 says so plainly.

## 7. Method and current state

**Discipline.** The programme advances in passes: each pass closes a
cluster of questions and is fixed by a delta; deltas are periodically
assembled into an architecture snapshot. Twelve passes have been
completed (subsystem map → lifecycle → reversibility → consolidation →
the Archivist → the molecule's form), plus the shelves-frame delta.
Priority rules for contradictions between documents are formalised;
hypothesis notes are separated from decisions by an explicit "do not
apply without verification" status.

**The executable specification.** The fixed part of the architecture
has been translated into a typed Python package: a live core (the
molecule, the lifecycle, the event log, the links — validated by tests
and strict typing) and a Protocol skeleton of all subsystems with
`NotImplementedError` bodies. The code is a derived artefact: the
documents govern; ambiguities in the code are marked with a status
legend (DECISION / CONTESTED / HYPOTHESIS / OPEN / EMPIRICAL), and no
numeric thresholds are hard-coded anywhere. The method has already
paid for itself: the mandatory verification of every code claim
against the documents exposed two internal contradictions of the
snapshot that were invisible to linear reading — typing works as a
forced coherence check. A separate methodological note on this is
coming.

**The first experiment (preliminary).** A parallel branch, probe-scan,
tested the extraction of knowledge from a small model's weights by
probing, against an external corpus (Wikipedia, the Solar System). All
numbers below are *preliminary*, pending completion of the manual
validation: an LLM judge (qwen2.5:7b) labelled 1,390 probe-only
clusters; two independent annotations by frontier models agreed on
90.8% of the sample; the judge against their consensus scored 53.2%,
with a systematic bias toward strictness (up to ~70% of its
"contradiction" verdicts are not contradictions). One methodological
lesson is already stable: **an LLM judge is a measuring instrument
with its own systematics**; it must be calibrated and characterised
like any instrument, and its quoted evidence must be checked against
the source, because paraphrase from the weights blends in unnoticed.

**Maturity map.**

| Area | State |
| --- | --- |
| Molecule form, lifecycle, event log | Fixed; encoded in the live core of the specification |
| The Archivist, the link pipeline, the queues | Conceptually fixed; Protocol skeleton |
| Triggers, immune, intents, temporal | Map and boundaries fixed; detailing belongs to future passes |
| Consolidation into LoRA | Mechanics described; not yet tested experimentally |
| The observer (probes on activations) | Contract fixed; probe trainability is an open research risk |
| The shelves frame / inter-shelf layer | Direction adopted; the pass is blocked (§8.1) |
| Difference from neighbours | A-MEM / Zettelkasten-style agents — no typed graph with a lifecycle; MemGPT/Letta — context management, not consolidation into weights; Generative Agents — reflection without a path into the weights; sleep-inspired approaches — without selectivity at the entrance. The combination "triggers at the entrance → typed graph with a lifecycle → consolidation into LoRA → an observer on activations → shelves" has not been met in this completeness |

## 8. Open problems

1. **The blocking question.** A late pivot — "molecules do not merge,
   they group" (the premise of the shelves frame) — contradicts the
   formally retained merge mechanics. The entire merge cluster in the
   specification is marked CONTESTED; the inter-shelf pass stands
   still until this is resolved. We preferred a stop to a silent
   choice.
2. **The observer is the riskiest bet.** Whether probe classifiers
   can be trained to deliver gap/uncertainty signals of the required
   quality, and whether they transfer across kernel versions, is
   open; if this fails, the principle of motivated action loses its
   input.
3. **Consolidation without catastrophic forgetting** — the central
   thesis has not yet met an experiment.
4. **Thresholds and interpretations.** All numeric thresholds are
   calibration state; the rules by which different consumers use the
   two confidence scalars are not fixed.
5. **Scaling in time.** The behaviour of the graph, the queues and
   the topology map over years of continuous operation is unknown.
6. **Concept inflation.** Conceptual work runs ahead of experiment; a
   tower of unverified ideas may crumble at first contact with
   reality. We acknowledge this risk and publish the state before it
   is resolved — that is the point of the research-notes genre.

## 9. What this programme is not

Not a commercial product and not an MVP. Not a competitor to LLM
companies — scaling the current paradigm and studying the living
learning process are different tasks. Not an attempt to build AGI. Not
a claim that transformers are bad. **Not yet another RAG framework**:
the chain "query → embedding → search → LLM" is one utility fragment,
not the essence; the architecture is a multi-process system on
different timescales, and its degeneration into RAG is treated as a
documented failure mode with a dedicated defence discipline. Not a
fast project: the horizon is years.

## 10. Status and invitation

The phase is conceptual design with first empirical probes. The
programme's code & data repository (the executable specification, the
experiment materials) is being prepared for publication. The most
useful thing you can leave here is criticism: an objection to any of
the six theses, a counterexample to the maturity map, a pointer to
work we have missed, or to a contradiction we have missed in
ourselves. The programme has already rewritten its manifesto in
response to critique and is ready to do it again.

---

*Research note · July 2026 · v0.1 (English edition)*

**Authorship note.** This document is a product of dialogic
co-authorship with asymmetric responsibility: the ideas and
formulations that constitute the research programme are the author's;
development, critique, and landscape mapping emerged in dialogue with
an AI assistant (Claude, Anthropic). Responsibility for the content
rests with the human author.
