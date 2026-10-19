# Kobald + Domovoi

> **Two complementary research efforts:** a scientific AI harness and an efficient-language-model research laboratory.

Kobald and Domovoi are independent projects led by Cameron Lonnie in Mount Gambier, South Australia.

**Kobald** is being developed as a **scientific AI orchestration harness**. Its intended focus is AI-assisted physics simulations, numerical scientific computing, chemical data analysis, and eventually properly authorised scientific instrument connectors—not an everyday personal assistant. Evidence handling, model access, human review and desktop interface prototypes exist, but the science-specific adapters are **not yet implemented**.

**Domovoi** is a long-term research effort investigating language-model capability per byte of memory, unit of computation and watt of power. **Domovoi-Labs already has a research pipeline and a conventional Transformer baseline**, with documented training, testing, profiling and experiment tracking. The proposed new Domovoi architecture remains unimplemented and unvalidated.

The two projects are complementary, but neither depends on the other's success. Kobald can work with existing models; future experimental Domovoi models could be evaluated in Kobald on scientific tasks.

> **Build it. Measure it. Challenge it. Improve it.**

The research is early-stage. Proposed capabilities and efficiency targets are aims and hypotheses, not claims that novel AI architecture or lab automation has already been achieved.

---

## Table of Contents

- [Executive Summary](#executive-summary)
- [The Problem](#the-problem)
- [What is Kobald?](#what-is-kobald)
- [What is Domovoi?](#what-is-domovoi)
- [How the Projects Work Together](#how-the-projects-work-together)
- [What Domovoi is Researching](#what-domovoi-is-researching)
- [Clean-Sheet Architecture Direction](#clean-sheet-architecture-direction)
- [Sub-1-Bit Research](#sub-1-bit-research)
- [How the Research is Conducted](#how-the-research-is-conducted)
- [How Results are Measured](#how-results-are-measured)
- [Current Status](#current-status)
- [Why Local Research Hardware is Needed](#why-local-research-hardware-is-needed)
- [Project Roadmap](#project-roadmap)
- [Public Research and Transparency](#public-research-and-transparency)
- [Sponsorship and Collaboration](#sponsorship-and-collaboration)
- [Repositories](#repositories)
- [About the Project Lead](#about-the-project-lead)

---

# Executive Summary

AI can be helpful in scientific research, but a plausible answer is not a verified result. Simulations, chemical analyses and laboratory measurements need specified inputs, units, tools, versioned methods, recorded outputs and independent checks.

**Kobald** aims to supply the research harness around interchangeable AI models: constrained scientific tools, simulation runners, datasets, evidence records and human review. The technical foundation exists in earlier general-purpose prototypes; the new science-first integrations are planned.

**Domovoi** investigates a different foundational problem: whether novel model designs, training methods and memory systems could deliver substantially more useful capability for the same resources. Its private `Domovoi-Labs` repository has a functioning Phase 0 training/evaluation laboratory and a conventional baseline implementation. It has **not** demonstrated a new Domovoi architecture or achieved its long-term efficiency target.

A potential future combination would be:

~~~text
Researcher defines a question
           ↓
Kobald executes an authorised simulation or data analysis
           ↓
Results, assumptions and uncertainty are recorded
           ↓
Researcher independently examines the evidence
           ↓
Experimental Domovoi models, if developed, can be evaluated
           ↓
Findings guide future research on both systems
~~~

Both initiatives are research-first rather than promises of a near-term commercial product.

---

# The Problem

Many modern AI models contain billions of learned values.

Those values must be stored in memory while the model is running.

As models become larger, the amount of memory and computing power they require also increases.

For example, a model containing approximately 27 billion parameters can require tens of gigabytes of memory depending on how it is stored.

That creates several problems:

- powerful local AI hardware becomes expensive;
- organisations become more dependent on cloud services;
- private data may need to leave the user's own systems;
- independent researchers face higher costs;
- larger systems consume more electricity;
- running multiple AI systems at once becomes difficult.

Domovoi investigates whether some of those requirements can be reduced through better model design.

---

# What is Kobald?

Kobald is a proposed **scientific AI harness**, not a new language model or a general daily-life chatbot. The AI model is interchangeable; Kobald is intended to provide the structured, controlled scientific workflows around it.

## Scientific directions

| Domain | Intended workflow | Current maturity |
|---|---|---|
| Physics and engineering | Configure numerical/physics-engine simulations, capture inputs and compare outputs | Proposed |
| Computational chemistry | Analyse chemical datasets and simulation output with reproducible methods | Proposed |
| Mathematics and statistics | Run verifiable calculations, numerical methods and uncertainty analysis | Proposed |
| Biology and environmental science | Process observational data and support evidence-grounded analysis | Proposed |
| Laboratory data and instrumentation | Ingest instrument data using typed, permissioned connectors | Proposed; synthetic/read-only first |
| Evidence and research workflows | Track source provenance, contradictions, reviews and audit records | Early general-purpose prototypes exist; science-specific migration pending |

Kobald would ideally allow a researcher to move from hypothesis to approved tool execution to traceable results—without taking the model's conclusions on faith.

## Example future workflow

~~~text
Researcher poses hypothesis
    → define dataset and experimental conditions
    → verify tool versions, parameters, units and permissions
    → run isolated simulation or read-only scientific analysis
    → store raw outputs, errors, seeds and provenance
    → compare against references or measurements
    → show findings, uncertainties and contradictions
    → researcher approves interpretation or plans next study
~~~

**This is the desired design, not a currently working end-to-end scientific system.**

External laboratory control would require qualified human supervision, device-specific interlocks and separate safety reviews. A generated plan must never count as permission for a physical experiment.

Earlier Kobald work includes model interactions, developing knowledge/evidence foundations, human review, policy/audit concepts and an early Command Centre interface. The [canonical KobaldAi repository](https://github.com/CL-BAF/KobaldAi) is rebuilding that foundation for the science-first direction.

[View the dedicated Kobald scientific-harness showcase](https://github.com/CL-BAF/Kobald_Showcase).

---

# What is Domovoi?

Domovoi is the model-research side of the project.

Its purpose is to investigate whether AI models can be designed from the beginning to use much less memory and computing power.

The goal is not simply to take an existing large model and compress it as much as possible.

Instead, Domovoi asks whether the model itself can be designed differently from the beginning.

The central research question is:

> **Can a language model designed specifically for efficiency approach the useful capability of much larger models while requiring dramatically less memory and computation?**

One long-term research target is to investigate whether capability similar to current 27-billion-parameter-class models could eventually be approached within roughly **4 GB of inference memory**.

That target does not require a specific parameter count or a fixed 0.5-bit format. A design with a higher average bit width may be better if it requires much less computation, while an extremely low-bit model may be a poor result if it needs an enormous network to compensate.

Domovoi therefore treats **capability per byte, capability per operation and capability per watt** as more important than bit width alone.

This target has not been achieved.

It is the research problem Domovoi is intended to investigate.

---

# How the Projects Work Together

These projects address different problems in research.

| Project | Primary question | Relationship |
|---|---|---|
| **Kobald** | How can AI-assisted scientific computing be reproducible, inspectable and subject to researcher control? | Can use established local or cloud models independently |
| **Domovoi** | Can new language-model designs achieve much greater capability per memory, compute and energy? | Can be independently developed and benchmarked before any Kobald integration |

In a possible later stage, Kobald would provide controlled scientific workflows against which *newly developed* Domovoi models could be evaluated. That would supplement, not replace, Domovoi's independent reasoning, language, coding, long-context and resource-use evaluations.

There is no current integration between a novel Domovoi model and Kobald, because the novel architecture does not yet exist.

---

# What Domovoi is Researching

There is unlikely to be one single technique that solves the efficiency problem.

Domovoi therefore investigates several parts of the model together rather than assuming that the existing Transformer stack must remain unchanged.

## Reusable learned computation

Conventional models store huge numbers of separate learned values.

One research direction is whether the model can learn a smaller vocabulary of reusable computational structures or **microcircuits** and reuse them throughout a much larger effective network.

~~~text
Conventional network

unique weight
unique weight
unique weight
unique weight


Possible Domovoi direction

learned pattern A ─┐
learned pattern B ─┼─ reused in many places
learned pattern C ─┘
~~~

The question is whether complex behaviour can emerge from combinations of a much smaller set of learned structures.

## Conditional routing

A conventional model often runs most of its network for every token.

Domovoi is interested in architectures where a learned router selects only the computation needed for the current input.

~~~text
Input
  ↓
Router
  ├── language structure
  ├── reasoning
  ├── mathematics
  ├── retrieval
  └── other learned modules
~~~

The objective is to make total model capacity much larger than the amount of computation activated for any single step.

## Compact working state

Transformer inference normally retains growing token-related state as context length increases.

Domovoi will investigate whether a model can maintain a smaller recurrent or compressed **working state** containing the information currently needed for reasoning, while retrieving older information when required.

The research question is not simply how to make context smaller, but how to teach the model what should be retained, compressed, retrieved or forgotten.

## Adaptive precision

Instead of forcing every connection to use the same number of bits, Domovoi will investigate whether precision itself can become a learned resource.

~~~text
Unnecessary connection  → remove it
Simple relationship     → shared low-bit pattern
Common relationship     → ternary / very-low-bit
Important relationship  → several bits
Critical computation    → higher precision
~~~

The objective is to spend precision only where it produces useful capability.

## Sparsity

If a connection or module is not useful, the model should ideally avoid storing or evaluating it.

Sparse structures may reduce memory traffic, active computation, energy use and latency.

## Separating knowledge from computation

Large language models store both general reasoning behaviour and large amounts of factual information inside their parameters.

Domovoi will investigate whether those roles can be separated more aggressively.

~~~text
                 Model
                /     \
               /       \
        computation    knowledge
        and reasoning   memory
~~~

The model could focus more internal capacity on language, reasoning, planning and information use, while factual or long-term knowledge is retrieved from an external or structured memory system when required.

## Dynamic computation

Not every input requires the same amount of processing.

Domovoi will investigate models that can perform additional computation only when needed.

~~~text
Input
  ↓
Compute
  ↓
Enough information?
  ├── yes → output
  └── no  → compute another cycle
                ↑
                └─────────
~~~

This allows easy tasks to remain cheap while difficult tasks receive additional computation.

## Efficient internal representations

Tokens are useful for language input and output, but they may not be the most efficient representation for every internal operation.

A longer-term direction is investigating whether text can be transformed into richer or more compact internal representations before expensive reasoning occurs, then decoded back into language afterward.

## Efficiency-aware training

If efficiency is a core design goal, training should reward it directly.

A future experimental objective may combine normal prediction quality with penalties for unnecessary memory, computation, active modules or precision.

Conceptually:

~~~text
training objective
=
task / language error
+ memory cost
+ compute cost
+ routing cost
+ precision cost
~~~

The goal would be to teach the model not only **what** to learn, but also **how efficiently** to represent and use what it learns.

---

# Clean-Sheet Architecture Direction

Domovoi's long-term direction is a clean-sheet language architecture rather than assuming that every successful idea must fit inside a conventional Transformer.

A conceptual system could look like:

~~~text
                    INPUT
                      │
                      ▼
             Semantic / Input Encoder
                      │
                      ▼
               Compact Working State
                      │
                      ▼
                    Router
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Pattern Bank   Pattern Bank   Memory Retrieval
        │             │             │
        └─────────────┼─────────────┘
                      │
                      ▼
                  State Update
                      │
                Enough compute?
                 /          \
               no            yes
               │              │
               └──── repeat   ▼
                         Output Decoder
                              │
                              ▼
                            OUTPUT
~~~

Possible properties include:

- reusable learned computational patterns instead of only independent dense weights;
- conditional routing so only relevant computation is activated;
- sparse structures;
- compact recurrent or compressed working state;
- adaptive numerical precision;
- external or structured long-term knowledge;
- dynamic reasoning depth;
- training objectives that explicitly reward efficiency.

This architecture is a research direction, not an implemented or proven model design.

The project will not replace every component at once. Existing Domovoi work will be preserved as a **baseline and reference implementation**, and new components will be introduced experimentally so their effect can be measured.

A radical destination still requires controlled experiments.

---

# Sub-1-Bit Research

One experimental area within Domovoi involves extremely low model-storage requirements.

Sub-1-bit storage is treated as **one possible tool inside the broader architecture**, not the definition of Domovoi itself.

A conventional binary value requires one bit of storage.

Going below an average of one stored bit per effective model weight therefore requires the model to reuse or generate information rather than independently storing every value.

A simplified example is:

~~~text
Traditional approach

stored value → one model weight


Possible structured approach

small amount of stored information
              ↓
reused or generated
              ↓
multiple effective model weights
~~~

One experimental target being considered is approximately **0.5 stored bits per effective weight on average**.

However, the project will not optimise for this number at the expense of overall efficiency. If a model using more than 0.5 bits achieves the same capability with substantially less compute, latency or energy, it may be the better architecture.

This does not mean physically storing half of a bit.

It means attempting to design the model so that the same stored information contributes to multiple parts of the model.

Whether this can preserve strong AI capability is unknown.

That is why it is being treated as an experiment rather than an assumption.

---

# How the Research is Conducted

## Domovoi Labs — Phase 0 already underway

Domovoi's work did begin: its research laboratory is implemented to a meaningful extent. The **existing model is deliberately a conventional Transformer baseline**, not the proposed novel Domovoi architecture.

The private `Domovoi-Labs` repository documents:

- a roughly **41-million-parameter**, pre-layer-normalisation decoder-only Transformer for baseline experiments;
- deterministic data preparation and tokenisation, training, checkpoint/resume and independent generation;
- benchmark evaluation scaffolding, CUDA memory profiling and experiment tracking;
- **75 reported passing tests**, including an offline CPU end-to-end test; these are repository-reported, not an external audit;
- one real GPU run, **DML-0001**, on an RTX 2050, stopped at approximately step **520/3,000** at the operator's request;
- **no completed official benchmark comparison** and **no validated novel-model efficiency result** yet.

The project will not resume local GPU training, download benchmark datasets or change the interrupted run's experiment status without the project lead's explicit approval.

## Next research stages

~~~text
Confirm reproducible baseline measurements
             ↓
Define a falsifiable architectural hypothesis
             ↓
Implement a single controlled experimental change
             ↓
Measure capability, memory, latency, compute and energy
             ↓
Compare with an established baseline and record failures
             ↓
Revise, reject or scale based on evidence
~~~

## Kobald's planned scientific validation

Kobald's first proposed scientific milestone is a small reproducible **offline simulation** against an independently verifiable reference result. Next would come computational science/data analysis, and only later synthetic or read-only measurement connectors. Physical laboratory actuation is not a baseline development milestone.

The research may take years. No particular outcome or timetable is guaranteed.

---

# How Results are Measured

Efficiency alone is not enough.

A very small model is not useful if its capability becomes too limited.

Domovoi therefore measures both efficiency and performance.

Important measurements include:

| Measurement | Why it matters |
|---|---|
| Model capability | Whether the model can actually perform useful tasks |
| Memory use | How much computer memory is required |
| Model size | How much storage is required |
| Processing requirements | How expensive the model is to run |
| Speed | How quickly the model produces results |
| Training cost | How much computing is required to create the model |
| Coding performance | Whether the model can perform software tasks |
| Reasoning performance | How well the model handles complex problems |
| Tool use | Whether the model can reliably interact with other software |
| Failure cases | Where and why the model performs poorly |
| Capability per byte | Whether additional memory is producing useful capability |
| Capability per operation | Whether compute is being used efficiently |
| Capability per watt | Whether efficiency improvements also reduce energy requirements |

The aim is not simply:

> "Make the smallest possible model."

The actual goal is:

> **Achieve the greatest useful capability possible for the available memory, computation and energy.**

---

# Current Status — October 2026

## Kobald

**Existing general AI/evidence prototypes; scientific-harness integrations planned.**

Legacy work includes evidence handling, model interfaces, bounded tool and policy concepts, a research workflow foundation and desktop interface development. The newer canonical `KobaldAi` codebase is at a foundation/migration stage. It has **not** yet integrated physics engines, computational chemistry software or scientific instruments.

## Domovoi

**Phase 0 laboratory partly implemented and tested; novel architecture research not yet begun.**

`Domovoi-Labs` contains the conventional Transformer, training/evaluation pipeline, profiling tools, experiment management and documented tests. The initial real training run was interrupted at the project lead's request, before completion and official benchmark evaluation.

No novel Domovoi architecture has been built or shown to satisfy the target 4 GiB inference and capability constraints. Existing code and small-model training are genuine engineering progress, not evidence of a foundational AI efficiency breakthrough.

## Research integrity

The public descriptions separate **implemented tooling**, **executed experiments**, **reported test coverage**, **proposed hypotheses** and **long-term targets**. Actual benchmark results should be published with matched baselines, measurement conditions and reproducible artifacts, not inferred from test counts or training loss.

---

# Why Computing and Research Infrastructure Matter

Domovoi architecture research requires repeatable model training, comparisons, profiling, ablations and eventual scaling. The existing RTX 2050 has been useful for Phase 0, but it does not provide enough headroom for every future experiment.

Kobald's science-first direction may also need CPU-heavy simulation, data storage, appropriate scientific software, domain expertise, specialist instruments and access to representative research datasets. **Computing hardware alone does not substitute for scientific validation or supervised laboratory access.**

Potential support includes university compute allocations, shared GPU clusters, sponsored workstations, cloud research credits, mentorship, research-software access, and supervised, read-only laboratory-data partnerships. No specific single GPU purchase is assumed to solve the research programme.

Larger training hardware would be compatible with Domovoi's objective: the **4 GiB target is for qualifying model inference**, not a cap on the compute permitted to conduct research.

---

# Project Roadmap

These are **research and engineering stages**, not fixed 90-day deliverables.

## Kobald

1. **Preserve and verify the foundation:** migrate evidence, policy, model-interface and audit concepts from the legacy prototype into the canonical scientific-harness architecture.
2. **First computational experiment:** run a documented physics or mathematical simulation offline with versioned inputs and independently checked outputs.
3. **Scientific data workflows:** integrate numerical and chemical analysis tools under reproducible execution manifests.
4. **Measurement connectors:** develop synthetic and read-only instrument interfaces with explicit scope, data provenance and relevant safety reviews.
5. **Research-grade orchestration:** connect multiple computational studies, report uncertainty and preserve researcher control.

## Domovoi

1. **Phase 0:** complete and assess reproducible baseline training, profiling, evaluation and reporting. The training/evaluation pipeline exists; the first real baseline run is incomplete.
2. **Architecture experiments:** introduce isolated changes to memory, routing, representations or computation and compare against baselines.
3. **Combine promising components:** only where ablation results support it.
4. **Efficiency-aware training:** investigate objectives that trade capability against memory, compute and energy cost.
5. **Scale justified approaches:** seek larger infrastructure only after smaller results warrant it.
6. **Evaluate candidate models:** benchmark directly, then potentially test in Kobald's scientific workflows if such models are developed.

**Long-term Domovoi research target:** investigate whether capability approaching much larger 27B-class models can be delivered within approximately 4 GiB of inference GPU memory, with explicit speed and context constraints. This remains speculative and is not achieved.

---

# Public Research and Transparency

Research does not always produce positive results.

An experiment that demonstrates that an idea does **not** work can still be valuable.

Where practical, this repository will publish information including:

- research methodology;
- model designs;
- benchmark results;
- memory measurements;
- speed measurements;
- comparisons with established models;
- training information;
- limitations;
- unsuccessful approaches;
- practical Kobald testing.

Project information will distinguish between four categories:

| Status | Meaning |
|---|---|
| **Implemented** | Currently exists and can be demonstrated |
| **Experimental** | Currently being researched or tested |
| **Planned** | Intended future work |
| **Long-term target** | A research objective that may or may not ultimately prove achievable |

This distinction is important because Domovoi is intentionally exploring difficult and uncertain research questions.

---

# Research Support and Collaboration

Kobald and Domovoi are looking primarily for **scientific and technical collaboration**, not immediate commercialisation.

Potential support includes academic mentorship, access to scientific software, instrument/data integration expertise, GPU and CPU research computing, reproducible evaluation design, grants or sponsorship appropriate to early-stage independent research, and introductions to experienced researchers.

A useful collaborator might help formulate falsifiable experiments, provide lawful access to suitable datasets, review numerical methods, help define safety boundaries or make compute available for justified studies.

These projects do not claim institutional sponsorship, laboratory partnerships, validated scientific discoveries or commercial readiness merely because discussions with interested people or organisations have occurred.

---

# Repositories

| Repository | Purpose | Access |
|---|---|---|
| [Kobald scientific-harness showcase](https://github.com/CL-BAF/Kobald_Showcase) | Public mission, scientific workflow direction and prototype status | Public |
| [KobaldAi](https://github.com/CL-BAF/KobaldAi) | Canonical source, architecture and migration roadmap | Public |
| [Domovoi-Labs](https://github.com/CL-BAF/Domovoi-Labs) | Actual research laboratory: baseline Transformer, pipeline, tests and partial first experiment | **Private**; access requires authorisation |
| [Kobald + Domovoi](https://github.com/CL-BAF/Domovoi-Kobald_showcase) | Combined public programme and research context | Public |

The public combined showcase describes research goals and documented status. The private laboratory code and complete research artifacts are not automatically accessible to external readers.

---

# About the Project Lead

The projects are led by **Cameron Lonnie**, a student developer and independent AI researcher based in **Mount Gambier, South Australia**.

Kobald originally began as a local AI development project and has since expanded into a broader research program involving AI efficiency, model architecture and practical local AI systems.

The project is currently being developed while Cameron completes secondary school and is intended to continue independently beyond school.

Areas of ongoing interest include artificial intelligence, machine learning, cybersecurity, systems engineering, software development, local computing and robotics.

---

# Project Principle

> **Build it. Measure it. Challenge it. Improve it.**

The purpose of Domovoi is not to claim that extreme AI efficiency has already been solved.

The purpose is to investigate, experimentally and transparently, how far it can actually be pushed.
