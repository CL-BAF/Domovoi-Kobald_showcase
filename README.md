# Kobald + Domovoi

> Local AI development and efficient-model research from Mount Gambier, South Australia.

Kobald and Domovoi are two connected artificial intelligence projects led by Cameron Lonnie.

**Kobald** is the practical software platform. It is used to run AI models locally, give them access to useful tools, and test how well they perform on real tasks.

**Domovoi** is the research project. It investigates whether capable AI models can be designed to use significantly less computer memory and processing power.

Together, the projects aim to answer a simple question:

> **How much useful AI capability can be achieved for each byte of memory, unit of computation and watt of power?**

The long-term research target is to investigate whether AI capability normally associated with much larger models could eventually run within only a few gigabytes of memory.

Sub-1-bit storage remains one experimental direction, but Domovoi is no longer framed as only a "0.5-bit Transformer" project. The broader direction is to reconsider the architecture, memory system, routing, numerical representation and training process together.

This is an active research project. Long-term targets described here are goals being investigated, not claims of results already achieved.

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

Modern artificial intelligence can be extremely capable, but the most capable systems often require expensive hardware, large amounts of memory, and significant computing power.

This creates a barrier for individuals, researchers, small organisations and businesses that want to run AI locally rather than depending entirely on large cloud providers.

Kobald and Domovoi approach that problem from two directions.

**Kobald** provides the practical environment where AI models can be used and tested.

**Domovoi** investigates whether the models themselves can be redesigned to become much more efficient.

The research is not limited to compressing a conventional Transformer. Domovoi will test whether major parts of the current LLM stack can be redesigned together, including model structure, working memory, routing, precision, sparsity, knowledge storage and training objectives.

The projects are designed to support each other:

~~~text
Domovoi develops and tests more efficient AI models
                         ↓
Kobald tests whether those models are useful in practice
                         ↓
Results are measured and compared
                         ↓
Promising ideas are improved and tested again
~~~

The long-term objective is not simply to build another chatbot.

The objective is to investigate whether capable AI can become more practical to run locally, with efficiency measured across memory, computation, bandwidth and energy rather than model size alone.

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

Kobald is a local AI platform.

In simple terms, it is the software environment around an AI model.

A model by itself mainly receives text and produces text.

Kobald is intended to provide the surrounding systems that allow a model to perform more useful work.

This can include:

- research;
- coding;
- data analysis;
- cybersecurity tasks;
- document and knowledge access;
- model testing;
- controlled tool use;
- longer-running AI workflows.

Kobald is designed to work with different AI models rather than being locked to a single provider.

That means established models can be used today while experimental Domovoi models can later be tested in the same environment.

## Why Kobald matters

AI models are often compared using benchmarks.

Benchmarks are useful, but a high benchmark score does not automatically mean a model performs well in real use.

Kobald provides a way to test questions such as:

> Can the model complete a coding task?

> Can it use tools correctly?

> Can it work with documents?

> Can it follow a longer research process?

> Can it operate locally and reliably?

> What changes when a smaller model replaces a much larger one?

This makes Kobald useful as a practical testing environment for Domovoi.

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

The two projects have different roles.

| Project | Role |
|---|---|
| **Domovoi** | Researches more efficient AI model designs |
| **Kobald** | Tests whether those models are practically useful |

The process is:

~~~text
Design an experimental model
            ↓
Train the model
            ↓
Measure its capability
            ↓
Measure memory and computing requirements
            ↓
Compare it with established models
            ↓
Test promising models inside Kobald
            ↓
Improve, replace or reject the idea
~~~

This prevents the research from focusing only on theoretical efficiency.

A model also needs to be useful.

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

Domovoi will use a staged research process.

The current Domovoi implementation will be retained as a baseline rather than discarded. Experimental architecture work can then branch away from that baseline while preserving a known reference for comparison.

The project will not begin by attempting to train an extremely large AI model or by replacing every part of the architecture simultaneously.

New ideas are first tested using relatively small models, with major components changed independently where practical.

For example:

~~~text
Small baseline model
        ↓
Experimental model
        ↓
Compare results
        ↓
If promising, test at a larger scale
        ↓
Repeat
~~~

Potential model sizes may progress from tens of millions of parameters into hundreds of millions and eventually larger systems.

A technique only receives significantly more computing resources if smaller experiments provide evidence that it is worth scaling.

This approach reduces wasted computing time and makes failed experiments useful.

If an idea performs poorly, it can be rejected before large amounts of money or computing power are spent on it.

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

# Current Status

Both projects are actively being developed.

## Kobald

Kobald already exists as an early research and development platform.

Current and ongoing work includes:

- AI model integration;
- local model support;
- knowledge and memory systems;
- testing and evaluation;
- desktop interface development;
- AI tool integration;
- research workflows;
- controlled cybersecurity tooling.

Kobald is not currently presented as a finished commercial product.

It is an evolving platform used for development, experimentation and evaluation.

## Domovoi

Domovoi is currently in the research and experimentation stage.

The first priority is establishing reliable baseline models and repeatable testing.

Experimental architectures can then be compared against those baselines.

This allows results to be measured objectively rather than relying on impressions.

---

# Why Local Research Hardware is Needed

Training AI models requires substantially more computing power than simply using services such as ChatGPT.

Research requires models to be trained repeatedly while different designs are tested.

A single experiment may involve:

~~~text
prepare data
      ↓
train model
      ↓
test model
      ↓
measure results
      ↓
modify architecture
      ↓
train again
~~~

This process may be repeated many times.

The project's current development hardware significantly limits the size and number of experiments that can be performed locally.

A dedicated AI research workstation would allow the project to conduct these experiments without relying entirely on rented cloud computing.

The current target is approximately:

| Component | Target |
|---|---|
| GPU | NVIDIA RTX 5090-class |
| GPU memory | 32 GB |
| System memory | Approximately 96 GB or more |
| Storage | High-speed NVMe storage |
| CPU | High-performance multi-core processor |
| Additional equipment | Backup storage and power protection |

This system would support early and medium-scale research, including:

- training experimental models;
- model benchmarking;
- fine-tuning;
- model distillation;
- local AI testing;
- Kobald development;
- dataset processing;
- storing model checkpoints and research results.

It would not replace the need for large-scale computing if the research eventually reaches much larger model sizes.

If an experimental architecture demonstrates strong results, larger training runs could later use university, industry, sponsored or rented research computing.

---

# Project Roadmap

## Stage 1 — Research foundation

Establish reliable training, benchmarking and comparison systems.

## Stage 2 — Preserve and measure the baseline

Keep the current Domovoi implementation as a reference and establish repeatable capability, memory, speed and compute measurements.

## Stage 3 — Replace individual primitives

Test reusable learned patterns, sparse structures, alternative state mechanisms, routing and adaptive precision separately where possible.

## Stage 4 — Combine successful components

Integrate components that demonstrate measurable improvements into increasingly non-Transformer experimental architectures.

## Stage 5 — Efficiency-aware training

Investigate training objectives that reward capability while penalising unnecessary memory, computation and precision.

## Stage 6 — Extreme memory efficiency

Investigate very low storage requirements, including whether below-one-bit average storage is useful when considered alongside compute and latency.

## Stage 7 — Scaling successful ideas

Increase model size only when earlier experiments show evidence that an approach is worth scaling.

## Stage 8 — Practical testing through Kobald

Integrate successful models into Kobald and compare them with established AI systems on practical work.

## Long-term objective

Investigate whether the practical capability of modern 27B-class or larger AI models can eventually be approached using only a few gigabytes of inference memory.

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

# Sponsorship and Collaboration

Kobald and Domovoi are seeking organisations interested in supporting independent Australian AI research and local technology development.

Potential support may include:

- financial sponsorship;
- AI research hardware;
- computing access;
- university collaboration;
- industry partnerships;
- technical mentorship;
- equipment loans;
- supplier support.

The immediate infrastructure priority is establishing a capable local AI research workstation.

This would allow Domovoi experiments and Kobald development to be conducted repeatedly and locally without depending entirely on external computing services.

Potential sponsors and collaborators can receive appropriate acknowledgement through public project documentation, research updates, presentations, demonstrations and published results.

The project is open to discussions with businesses, universities, researchers, technology companies and community organisations.

---

# Repositories

## Combined Public Showcase

This repository provides the public overview of the combined Kobald and Domovoi research program.

## Kobald

Kobald is the practical local AI platform and model-testing environment.

Public showcase:

https://github.com/CL-BAF/Kobald_Showcase

## Domovoi

Domovoi is the experimental AI model-efficiency research project.

Research information, results and public material will continue to be added as development progresses.

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
