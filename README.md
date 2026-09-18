# Kobald + Domovoi

> Local AI development and efficient-model research from Mount Gambier, South Australia.

Kobald and Domovoi are two connected artificial intelligence projects led by Cameron Lonnie.

**Kobald** is the practical software platform. It is used to run AI models locally, give them access to useful tools, and test how well they perform on real tasks.

**Domovoi** is the research project. It investigates whether capable AI models can be designed to use significantly less computer memory and processing power.

Together, the projects aim to answer a simple question:

> **Can useful AI become much more efficient without sacrificing too much capability?**

The long-term research target is to investigate whether AI capability normally associated with much larger models could eventually run within only a few gigabytes of memory.

This is an active research project. Long-term targets described here are goals being investigated, not claims of results already achieved.

---

## Table of Contents

- [Executive Summary](#executive-summary)
- [The Problem](#the-problem)
- [What is Kobald?](#what-is-kobald)
- [What is Domovoi?](#what-is-domovoi)
- [How the Projects Work Together](#how-the-projects-work-together)
- [What Domovoi is Researching](#what-domovoi-is-researching)
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

The objective is to investigate whether capable AI can become more practical to run locally.

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

Instead, Domovoi asks whether the model itself can be designed differently.

The central research question is:

> **Can an AI model designed specifically for efficiency approach the useful capability of much larger models while requiring dramatically less memory?**

One long-term research target is to investigate whether capability similar to current 27-billion-parameter-class models could eventually be approached within roughly **4 GB of inference memory**.

That would be a substantial reduction compared with conventional approaches.

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

Domovoi therefore investigates several approaches.

## Lower-precision model storage

Most AI models store their learned information using numerical values.

Reducing the amount of information needed to store each value can significantly reduce memory requirements.

Domovoi is interested in models designed around low-precision storage from the beginning rather than only reducing precision after training.

## Reusing learned information

Conventional models may store large numbers of separate learned values.

One research direction is whether parts of the model can reuse the same learned information more effectively.

If successful, this could reduce how much information needs to be stored.

## Repeated computation

Instead of storing a very large model, a smaller model may be able to perform several rounds of computation.

The research question is whether repeated use of a smaller structure can sometimes replace part of the capability gained from simply making a model larger.

## Selective computation

Large AI models do not necessarily need every part of the system for every task.

Another research direction is allowing the model to activate only the parts that are useful for the current input.

## More efficient mathematical structures

Large AI models contain very large mathematical structures.

Some of those structures may be representable using smaller components.

Domovoi will investigate whether these approaches can reduce storage while maintaining useful performance.

## Learning from larger models

A larger and more capable AI model can sometimes help train a smaller model.

This process is commonly called **distillation**.

Domovoi may use established models as teachers or reference systems while still training experimental models from scratch.

---

# Sub-1-Bit Research

One experimental area within Domovoi involves extremely low model-storage requirements.

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

This does not mean physically storing half of a bit.

It means attempting to design the model so that the same stored information contributes to multiple parts of the model.

Whether this can preserve strong AI capability is unknown.

That is why it is being treated as an experiment rather than an assumption.

---

# How the Research is Conducted

Domovoi will use a staged research process.

The project will not begin by attempting to train an extremely large AI model.

New ideas are first tested using relatively small models.

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

The aim is not simply:

> "Make the smallest possible model."

The actual goal is:

> **Achieve the greatest useful capability possible for the available memory and computing power.**

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

## Stage 2 — Small efficiency experiments

Test low-precision and alternative model designs using small models where experiments are relatively inexpensive.

## Stage 3 — Structural efficiency

Investigate whether models can reuse information, repeat computation or activate only selected parts of the network.

## Stage 4 — Extreme memory efficiency

Investigate very low storage requirements, including whether below-one-bit average storage is practical.

## Stage 5 — Scaling successful ideas

Increase model size only when earlier experiments show evidence that an approach is worth scaling.

## Stage 6 — Practical testing through Kobald

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
